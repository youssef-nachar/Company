<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Warehouse Dashboard Enhanced</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
<script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>

<style>
:root{
 --bg:#020617; --card:#111827; --accent:#22c55e;
 --warning:#f59e0b; --text:#e5e7eb; --muted:#94a3b8;
}
*{box-sizing:border-box;margin:0;padding:0;font-family:Inter,sans-serif;}
body{background:#0f172a;color:var(--text);}
.hidden{display:none;}
header{display:flex;align-items:center;padding:14px 22px;background:#111827;border-bottom:1px solid #1f2937;}
header h1{color:var(--accent);font-size:22px}
.container{padding:20px;display:grid;gap:20px}
.card{background:var(--card);border-radius:16px;padding:18px;box-shadow:0 6px 25px rgba(0,0,0,.35);}
.kpis{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:15px;text-align:center;}
.kpi{cursor:pointer}
.kpi .value{font-size:30px;font-weight:700;}
.success{color:var(--accent);}
.warning{color:var(--warning);}
.insights{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:15px;margin-top:15px;}
.insight{background:#020617;padding:14px;border-radius:14px;}
.insight h4{font-size:14px;color:var(--muted);}
.insight p{font-size:22px;font-weight:700;margin-top:5px;}
.pending-card{background:#020617;padding:14px;border-radius:14px;margin-bottom:10px;}
.pending-card h3{color:var(--accent)}
select,input,button{padding:6px;border-radius:6px;border:none;background:#020617;color:white;cursor:pointer}
</style>
</head>

<body>

<!-- LOGIN -->
<div id="loginContainer" style="height:100vh;display:flex;align-items:center;justify-content:center">
<form id="loginForm" class="card" style="width:320px">
 <h2 style="text-align:center;color:var(--accent)">Login</h2>
 <input id="username" placeholder="Username" required style="width:100%;padding:10px;margin:10px 0">
 <input id="password" type="password" placeholder="Password" required style="width:100%;padding:10px">
 <button style="margin-top:12px;width:100%;padding:10px;background:var(--accent);border:none;font-weight:700">Login</button>
 <p id="loginError" class="warning hidden">Invalid credentials</p>
</form>
</div>

<!-- DASHBOARD -->
<div id="dashboard" class="hidden">
<header style="justify-content:space-between;position:relative">
 <h1><i class="fa-solid fa-warehouse"></i> My Holdal</h1>
 <div style="position:relative">
   <button id="menuBtn" style="background:none;border:none;color:var(--accent);font-weight:700;cursor:pointer">
     Menu <i class="fa-solid fa-caret-down"></i>
   </button>
   <div id="menuDropdown" style="display:none;position:absolute;right:0;top:30px;background:var(--card);border-radius:8px;box-shadow:0 6px 15px rgba(0,0,0,0.3);">
     <button onclick="showReturns()" style="display:block;padding:10px 15px;width:100%;text-align:left;border:none;background:none;color:var(--text);cursor:pointer">Returns</button>
     <button onclick="signOut()" style="display:block;padding:10px 15px;width:100%;text-align:left;border:none;background:none;color:var(--text);cursor:pointer">Sign Out</button>
   </div>
 </div>
</header>

<div class="container">

<!-- FILTERS -->
<div class="card" style="display:flex;gap:15px;flex-wrap:wrap">
 <div>
  <label style="color:var(--muted)">Date</label><br>
  <input type="date" id="dateFilter" onchange="updateDashboard()">
 </div>
 <div>
  <label style="color:var(--muted)">Distribution</label><br>
  <select id="distributionFilter" onchange="updateDashboard()">
   <option value="all">All</option>
   <option value="LMD">LMD</option>
   <option value="Wakilni">Wakilni</option>
   <option value="Employee">Employee</option>
  </select>
 </div>
</div>

<!-- KPIS -->
<div class="card">
<h2 style="color:var(--accent)">Report Summary</h2>

<div class="kpis">
 <div class="kpi" onclick="showOrderDetails('total')">
  <div>Total</div><div id="total" class="value">0</div>
 </div>
 <div class="kpi" onclick="showOrderDetails('completed')">
  <div>Completed</div><div id="completed" class="value success">0</div>
 </div>
 <div class="kpi" onclick="showOrderDetails('pending')">
  <div>Pending</div><div id="pending" class="value warning">0</div>
 </div>
</div>

<div class="insights">
 <div class="insight"><h4>Completion Rate</h4><p id="performance">-</p></div>
 <div class="insight"><h4>Oldest Pending</h4><p id="oldest">-</p></div>
</div>
</div>

<!-- DISTRIBUTION BREAKDOWN -->
<div class="card" id="distributionBreakdown" style="display:none">
 <h2 style="color:var(--accent)">Distribution Breakdown</h2>
 <div id="distributionCards" class="insights"></div>
</div>

<!-- ORDER DETAILS -->
<div id="orderDetails" class="card hidden"
style="position:fixed;top:40px;left:50%;transform:translateX(-50%);
width:90%;max-width:700px;max-height:80vh;overflow:auto;z-index:200;">
<button onclick="closeOrderDetails()" style="float:right;background:#ef4444;color:#fff;padding:6px 10px;border:none;border-radius:6px;">Close</button>
<h3 style="color:var(--accent)">Order Details</h3>
<div id="orderList"></div>
</div>

</div>
</div>

<script>
// DOM Elements
const loginForm = document.getElementById("loginForm");
const username = document.getElementById("username");
const password = document.getElementById("password");
const loginError = document.getElementById("loginError");
const loginContainer = document.getElementById("loginContainer");
const dashboard = document.getElementById("dashboard");

const dateFilter = document.getElementById("dateFilter");
const distributionFilter = document.getElementById("distributionFilter");

const total = document.getElementById("total");
const completed = document.getElementById("completed");
const pending = document.getElementById("pending");
const performance = document.getElementById("performance");
const oldest = document.getElementById("oldest");

const distributionBreakdown = document.getElementById("distributionBreakdown");
const distributionCards = document.getElementById("distributionCards");
const orderDetails = document.getElementById("orderDetails");
const orderList = document.getElementById("orderList");

// USERS
const users=[
 {username:"pncUser",password:"123456",warehouse:"p&c---pack",role:"user"},
 {username:"pharmaUser",password:"123456",warehouse:"pharma---pack",role:"user"},
 {username:"lorealUser",password:"123456",warehouse:"loreal---pack",role:"user"},
 {username:"manager",password:"123456",warehouse:"all",role:"manager"}
];

let currentUser=null, allOrders=[];
const sheetURL="https://docs.google.com/spreadsheets/d/1BbhpLwCeajK7GFKHvf_iVu9I4LC65PoPKb-gHUJIiOI/export?format=csv";

// LOGIN
loginForm.onsubmit=e=>{
 e.preventDefault();
 const u=users.find(x=>x.username===username.value && x.password===password.value);
 if(!u) return loginError.classList.remove("hidden");
 currentUser=u;
 loginContainer.style.display="none";
 dashboard.classList.remove("hidden");
 loadData();
};

// NORMALIZE DISTRIBUTION
function normalize(v){return v?.trim().toLowerCase();}
function normalizeDistribution(v){
 if(!v) return "Other";
 v=v.toLowerCase();
 if(v.includes("lmd")) return "LMD";
 if(v.includes("wakilni")) return "Wakilni";
 if(v.includes("employee")) return "Employee";
 return "Other";
}

// تحويل تاريخ الشيت من DD/MM/YYYY HH:MM إلى YYYY-MM-DD
function formatDateForInput(d) {
  const parts = d.split(" ")[0].split("/"); // ["30","12","2025"]
  return `${parts[2]}-${parts[1].padStart(2,'0')}-${parts[0].padStart(2,'0')}`;
}

// LOAD DATA
function loadData(){
 fetch(sheetURL).then(r=>r.text()).then(csv=>{
  const data=Papa.parse(csv,{header:true,skipEmptyLines:true}).data;
  allOrders=data.map(r=>{
   const distribution=normalizeDistribution(r["Distribution"]);
   const status=(distribution==="LMD"||distribution==="Wakilni"||distribution==="Employee")?"completed":"pending";
   return{
    warehouse:normalize(r["Warehouse Name"]),
    distribution,
    status,
    date: r["Snapshot_Date"] ? formatDateForInput(r["Snapshot_Date"]) : "",
    raw:r
   };
  });
  initDate();
  updateDashboard();
 });
}

// INIT DATE
function initDate(){
 if(!dateFilter.value){
  const d=[...new Set(allOrders.map(o=>o.date).filter(Boolean))].sort();
  dateFilter.value=d[d.length-1];
 }
}

// APPLY FILTERS
function applyFilters(){
 let orders=allOrders;
 if(dateFilter.value) orders=orders.filter(o=>o.date===dateFilter.value);
 if(currentUser.warehouse!=="all")
  orders=orders.filter(o=>o.warehouse===normalize(currentUser.warehouse));
 if(distributionFilter.value!=="all")
  orders=orders.filter(o=>o.distribution===distributionFilter.value);
 return orders;
}

// UPDATE DASHBOARD
function updateDashboard(){
 const orders=applyFilters();
 total.textContent=orders.length;
 completed.textContent=orders.filter(o=>o.status==="completed").length;
 pending.textContent=orders.filter(o=>o.status==="pending").length;
 performance.textContent=orders.length
  ?Math.round((completed.textContent/orders.length)*100)+"%"
  :"0%";

 // Show oldest pending order number
 const pendingOrders = orders
   .filter(o => o.status === "pending" && o.date)
   .sort((a,b) => new Date(a.date) - new Date(b.date));
 oldest.textContent = pendingOrders.length ? pendingOrders[0].raw["#M Order"] : "-";

 if(currentUser.role==="manager") renderDistributionBreakdown(orders);
}

// DISTRIBUTION BREAKDOWN
function renderDistributionBreakdown(orders){
 distributionBreakdown.style.display="block";
 const map={};
 orders.forEach(o=>map[o.distribution]=(map[o.distribution]||0)+1);
 distributionCards.innerHTML=Object.entries(map).map(([d,v])=>
  `<div class="insight"><h4>${d}</h4><p>${v}</p></div>`
 ).join('');
}

// ORDER DETAILS
function showOrderDetails(type){
 let orders=applyFilters();
 if(type!=="total") orders=orders.filter(o=>o.status===type);
 orderList.innerHTML=orders.map(o=>`
 <div class="pending-card">
  <h3>${o.raw["#M Order"]||"-"}</h3>
  <p>Warehouse: ${o.raw["Warehouse Name"]}</p>
  <p>Distribution: <b>${o.distribution}</b></p>
  <p>Status: ${o.status}</p>
 </div>`).join('');
 orderDetails.classList.remove("hidden");
}
function closeOrderDetails(){orderDetails.classList.add("hidden");}

// MENU DROPDOWN
const menuBtn = document.getElementById("menuBtn");
const menuDropdown = document.getElementById("menuDropdown");
menuBtn.addEventListener("click", ()=>{
 menuDropdown.style.display = menuDropdown.style.display==="block" ? "none" : "block";
});
window.addEventListener("click", function(e){
 if(!menuBtn.contains(e.target) && !menuDropdown.contains(e.target)){
   menuDropdown.style.display = "none";
 }
});
function showReturns(){ alert("سيتم عرض Returns هنا (يمكن عمل popup أو صفحة لاحقًا)"); }
function signOut(){
 dashboard.classList.add("hidden");
 loginContainer.style.display="flex";
}
</script>

</body>
</html>
