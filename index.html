<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Warehouse Dashboard</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>

    <style>
        :root {
            --bg: #0f172a;
            --sidebar: #020617;
            --card: #111827;
            --accent: #22c55e;
            --warning: #f59e0b;
            --text: #e5e7eb;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Inter, sans-serif;
        }

        body {
            background: var(--bg);
            color: var(--text);
        }

        .hidden {
            display: none !important
        }

        .app {
            display: grid;
            grid-template-columns: 240px 1fr;
            min-height: 100vh
        }

        .sidebar {
            background: var(--sidebar);
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 20px
        }

        .sidebar h2 {
            color: var(--accent)
        }

        .sidebar a {
            color: var(--text);
            text-decoration: none;
            padding: 10px;
            border-radius: 8px
        }

        .sidebar a:hover {
            background: #111827
        }

        .main {
            padding: 20px
        }

        .card {
            background: var(--card);
            border-radius: 16px;
            padding: 18px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, .35)
        }

        .kpis {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 16px
        }

        .kpi {
            background: #020617;
            padding: 18px;
            border-radius: 14px;
            text-align: center;
            cursor: pointer
        }

        .kpi .value {
            font-size: 32px;
            font-weight: 700;
            margin-top: 6px
        }

        .success {
            color: var(--accent)
        }

        .warning {
            color: var(--warning);
            text-align: center;
            margin-top: 16px;
            font-style: oblique;
        }

        input,
        button {
            padding: 8px;
            border-radius: 8px;
            border: none;
            background: #020617;
            color: white
        }

        button {
            cursor: pointer
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 12px
        }

        th,
        td {
            border: 1px solid #333;
            padding: 8px;
            text-align: center
        }

        th {
            background: #111827;
            color: var(--accent)
        }

        .warehouse-card {
            background: #020617;
            padding: 14px;
            border-radius: 14px;
            margin-bottom: 12px
        }

        #loginContainer {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;

        }

        #orderDetails {
            position: fixed;
            inset: 0;
            background: rgba(0, 0, 0, .6);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 999
        }

        #orderDetails .card {
            width: 90%;
            max-width: 800px;
            max-height: 85vh;
            overflow: auto
        }

        .warehouse-container {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-top: 40px
        }

        .warehouse-container .card {
            flex: 1
        }

        a {
            color: white;
            text-decoration: none
        }

        .sales-order {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        .two-columns {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            align-items: flex-start;
        }

        /* Input أجمل */
        .search-input {
            width: 100%;
            padding: 10px;
            margin-bottom: 12px;
            border-radius: 10px;
            background: #020617;
            border: 1px solid #1f2937;
        }

        /* Responsive للموبايل */
        @media (max-width: 1024px) {
            .two-columns {
                grid-template-columns: 1fr;
            }
        }

        /* LOGIN BACKGROUND */
        .login-wrapper {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background:
                radial-gradient(circle at top, #22c55e22, transparent 40%),
                radial-gradient(circle at bottom, #0ea5e922, transparent 40%),
                var(--bg);
        }

        /* LOGIN CARD */
        .login-card {
            width: 360px;
            background: rgba(2, 6, 23, 0.9);
            backdrop-filter: blur(10px);
            padding: 30px 26px;
            border-radius: 18px;
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.6);
            animation: fadeIn 0.6s ease;
        }

        /* TITLE */
        .login-title {
            text-align: center;
            font-size: 28px;
            margin-bottom: 24px;
            color: white;
        }

        .login-title span {
            color: var(--accent);
        }

        /* INPUT GROUP */
        .input-group {
            position: relative;
            margin-bottom: 16px;
        }

        .input-group i {
            position: absolute;
            top: 50%;
            left: 14px;
            transform: translateY(-50%);
            color: #9ca3af;
        }

        .input-group input {
            width: 100%;
            padding: 12px 14px 12px 42px;
            border-radius: 12px;
            background: #020617;
            border: 1px solid #1f2937;
            color: white;
            font-size: 14px;
        }

        .input-group input:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 2px #22c55e33;
        }

        /* BUTTON */
        .login-btn {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border-radius: 14px;
            font-weight: 600;
            background: linear-gradient(135deg, #22c55e, #16a34a);
            color: #020617;
            cursor: pointer;
            transition: transform 0.15s ease, box-shadow 0.15s ease;
        }

        .login-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 30px #22c55e55;
        }

        /* ERROR */
        .login-error {
            margin-top: 14px;
            text-align: center;
            color: #ef4444;
            font-size: 14px;
        }

        /* ANIMATION */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(10px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* LOADING OVERLAY */
        .loading-overlay {
            position: fixed;
            inset: 0;
            background: rgba(2, 6, 23, 0.95);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
        }

        .loading-card {
            text-align: center;
            animation: fadeIn 0.4s ease;
        }

        .loading-card h2 {
            margin-top: 18px;
            font-size: 26px;
            color: white;
        }

        .loading-card h2 span {
            color: var(--accent);
        }

        .loading-card p {
            margin-top: 6px;
            color: #9ca3af;
            font-size: 14px;
        }

        /* SPINNER */
        .spinner {
            width: 64px;
            height: 64px;
            border: 5px solid #1f2937;
            border-top: 5px solid var(--accent);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }

        .menu-item>a {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .submenu,
        .subsubmenu {
            display: none;
            margin-top: 6px;
            margin-left: 10px;
        }

        .submenu a,
        .subsubmenu a {
            display: block;
            padding: 8px 12px;
            border-radius: 8px;
            font-size: 14px;
        }

        .submenu a:hover,
        .subsubmenu a:hover {
            background: #111827;
        }

        .subsubmenu {
            margin-left: 14px;
            border-left: 2px solid #1f2937;
            padding-left: 10px;
        }

        .arrow {
            font-size: 12px;
            transition: transform 0.2s ease;
        }

        .menu-open>a .arrow {
            transform: rotate(180deg);
        }
    </style>

</head>

<body>

    <div id="loginContainer" class="login-wrapper">
        <form id="loginForm" class="login-card">
            <h2 class="login-title">
                <span>MY</span>HOLDAL
            </h2>

            <div class="input-group">
                <i class="fa-solid fa-user"></i>
                <input id="username" placeholder="Username" required>
            </div>

            <div class="input-group">
                <i class="fa-solid fa-lock"></i>
                <input id="password" type="password" placeholder="Password" required>
            </div>

            <button class="login-btn">
                <i class="fa-solid fa-right-to-bracket"></i> Login
            </button>

            <p id="loginError" class="login-error hidden">
                <i class="fa-solid fa-circle-exclamation"></i>
                Incorrect username or password
            </p>
        </form>
    </div>

    <div id="dashboard" class="hidden app">
        <aside class="sidebar">
            <h2><i class="fa-solid fa-warehouse"></i>Warehouse Management System</h2>
            <a href="#">Dashboard</a>
            <div class="menu-item">
                <a href="#" onclick="toggleMenu('warehousesMenu')">
                    <i class="fa-solid fa-boxes-stacked"></i> Warehouses
                    <i class="fa-solid fa-chevron-down arrow"></i>
                </a>

                <div id="warehousesMenu" class="submenu">

                    <!-- P&C -->
                    <div class="submenu-item">
                        <a href="#" onclick="toggleMenu('pcMenu')">P&amp;C</a>
                        <div id="pcMenu" class="subsubmenu">
                            <a href="./p&c.html">MyHoldal</a>
                            <a href="#">Return</a>
                            <a href="#">KPI</a>
                        </div>
                    </div>

                    <!-- Pharma -->
                    <div class="submenu-item">
                        <a href="#" onclick="toggleMenu('pharmaMenu')">Pharma</a>
                        <div id="pharmaMenu" class="subsubmenu">
                            <a href="#">MyHoldal</a>
                            <a href="#">Return</a>
                            <a href="#">KPI</a>
                        </div>
                    </div>

                    <!-- Retail -->
                    <div class="submenu-item">
                        <a href="#" onclick="toggleMenu('retailMenu')">Retail</a>
                        <div id="retailMenu" class="subsubmenu">
                            <a href="#">MyHoldal</a>
                            <a href="#">Return</a>
                            <a href="#">KPI</a>
                        </div>
                    </div>

                    <!-- LOREAL -->
                    <div class="submenu-item">
                        <a href="#" onclick="toggleMenu('lorealMenu')">L’Oréal Lux</a>
                        <div id="lorealMenu" class="subsubmenu">
                            <a href="#">MyHoldal</a>
                            <a href="#">Return</a>
                            <a href="#">KPI</a>
                        </div>
                    </div>

                    <!-- BEESLINE -->
                    <div class="submenu-item">
                        <a href="#" onclick="toggleMenu('beeslineMenu')">Beesline</a>
                        <div id="beeslineMenu" class="subsubmenu">
                            <a href="#">MyHoldal</a>
                            <a href="#">Return</a>
                            <a href="#">KPI</a>
                        </div>
                    </div>

                </div>
            </div>
            <a href="#" onclick="signOut()" style="color:#ef4444">Logout</a>
        </aside>

        <main class="main">
            <header style="margin-bottom:20px;display:flex;justify-content:space-between;align-items:center">
                <h3><B style="font-style: 26px;">My</B>Holdal</h3>
                <div style="display:flex;gap:10px;align-items:center">
                    <button type="button" id="toggleToDate" style="padding:4px 8px; font-size:12px;"> from</button>

                    <input type="date" id="dateFrom" onchange="updateDashboard()">

                    <button type="button" id="toggleToDate" style="padding:4px 8px; font-size:12px;"> to</button>

                    <input type="date" id="dateTo" onchange="updateDashboard()">
                </div>
            </header>

            <div class="kpis">
                <div class="kpi" onclick="showOrderDetails('total')">
                    <div>Total Orders</div>
                    <div id="total" class="value">0</div>
                </div>
                <div class="kpi" onclick="showOrderDetails('completed')">
                    <div>In-Packing</div>
                    <div id="completed" class="value success">0</div>
                </div>
                <div class="kpi" onclick="showOrderDetails('pending')">
                    <div>Pending</div>
                    <div id="pending" class="value warning">0</div>
                </div>
                <div class="kpi" onclick="showOrderDetails('distributed')">
                    <div>Distributed</div>
                    <div id="distributed" class="value success">0</div>
                </div>
            </div>

            <div class="warehouse-container">


                <div class="card">
                    <h3 style="color:var(--accent)">Multi-Warehouse Orders</h3>
                    <div id="multiWHTable"></div>
                </div>

                <div class="card">
                    <h3 style="color:var(--accent)">Single-Warehouse Orders</h3>
                    <div id="singleWHTable"></div>
                </div>
            </div>
            <div class="sales-order two-columns">

                <div class="card">
                    <h3 style="color:var(--accent)">Sales order details</h3>
                    <div id="warehouseBreakdownTable"></div>
                </div>

                <div class="card">
                    <h3 style="color:var(--accent)">Tracking</h3>

                    <input type="text" id="orderSearch" placeholder="Search Order #" class="search-input"
                        oninput="updateSearch()">

                    <div id="searchResultsCard" style="display:none">
                        <div id="searchResultsTable"></div>
                    </div>
                </div>

            </div>
    </div>

    </div>
    </main>
    </div>

    <div id="orderDetails" class="hidden">
        <div class="card">
            <button onclick="closeOrderDetails()" style="float:right;background:#ef4444">Close</button>
            <button onclick="exportOrderDetailsToExcel()" style="float:right;margin-right:8px;background:#22c55e">Export
                to Excel</button>
            <h3 style="color:var(--accent)" id="orderDetailsTitle">Order Details</h3>
            <div id="orderList"></div>
        </div>
    </div>

    <!-- LOADING OVERLAY -->
    <div id="loadingOverlay" class="loading-overlay hidden">
        <div class="loading-card">
            <div class="spinner"></div>
            <h2><span>MY</span> HOLDAL</h2>
            <p>Loading Dashboard...</p>
        </div>
    </div>

</body>
<script>
    const users = [{ username: "manager", password: "123456" }];
    const sheetURL = "https://docs.google.com/spreadsheets/d/e/2PACX-1vSmcU44IrVbsgFcrMJ1TxA0xnjwBQa9cD6NKPf-jmVaDNIMaNOMa14pU0eRSh9QLw/pub?output=csv";
    let allOrders = [];
    let lastDisplayedOrders = [];

    function updateSearch() {
        const query = document.getElementById("orderSearch").value.trim().toLowerCase();
        const resultsDiv = document.getElementById("searchResultsCard");
        const tableDiv = document.getElementById("searchResultsTable");

        if (!query) {
            resultsDiv.style.display = "none";
            return;
        }

        const filtered = allOrders.filter(o =>
            o.orderNo.toLowerCase().includes(query)
        );

        if (!filtered.length) {
            tableDiv.innerHTML =
                "<p style='color:var(--warning)'>No matching orders found.</p>";
            resultsDiv.style.display = "block";
            return;
        }

        tableDiv.innerHTML = `
<table>
    <tr>
        <th>Order #</th>
        <th>Warehouse</th>
        <th>Status</th>
        <th>Note</th>
    </tr>

    ${filtered.map(o =>
            o.warehouses.map(w => {

                /* STATUS فقط Pending أو In-Packing */
                const status = w.packed ? "In-Packing" : "Pending";
                const time = formatDateForInput(w["Snapshot_Date"]);
                return `
                <tr>
                    <td>${o.orderNo}</td>
                    <td>${w.base}</td>
                    <td>${status}</td>
                    <td>${w.comment || ""}</td>
                </tr>

                ${(
                        o.status === "distributed" &&
                        w.distributed &&
                        o.distributor
                    ) ? `
                <tr style="background:#020617;color:#22c55e;font-weight:600">
                    <td colspan="4">
                        <i class="fa-solid fa-truck"></i>
                        Distributed    to: ${o.distributor} ? <span style="margin-left:12px; color:#9ca3af"><i class="fa-regular fa-clock"></i>${o.distributedTime}</span>
                    </td>
                </tr>
                ` : ""}
            `;
            }).join("")
        ).join("")}
</table>
`;

        resultsDiv.style.display = "block";
    }
    // LOGIN
    loginForm.onsubmit = e => {
        e.preventDefault();

        const u = users.find(
            x => x.username === username.value && x.password === password.value
        );

        if (!u) {
            loginError.classList.remove("hidden");
            return;
        }

        loginError.classList.add("hidden");

        loginContainer.style.display = "none";
        loadingOverlay.classList.remove("hidden"); // 👈 Loading ON

        loadData(); // 👈 تحميل حقيقي
    };
    // FORMAT DATE
    function formatDateForInput(d) {
        if (!d || !d.includes("/")) return "";
        const p = d.split("/");
        return `${p[2]}-${p[1].padStart(2, '0')}-${p[0].padStart(2, '0')}`;
    }

    function loadData() {
        fetch(sheetURL)
            .then(r => r.text())
            .then(csv => {
                const rows = Papa.parse(csv, {
                    header: true,
                    skipEmptyLines: true
                }).data;

                const map = {};

                rows.forEach(r => {
                    const id = r["#M Order"];
                    if (!id) return;

                    if (!map[id]) {
                        map[id] = {
                            orderNo: id,
                            date: formatDateForInput(r["Snapshot_Date"]),
                            wh: {}
                        };
                    }

                    let wh = (r["Warehouse Name"] || "").toLowerCase();
                    let base = wh.replace(/---pack/g, "").replace(/\s*wh/g, "").trim();

                    if (!map[id].wh[base]) {
                        map[id].wh[base] = {
                            base,
                            packed: false,
                            distributed: false,
                            distributor: null,
                            comment: ""
                        };
                    }

                    if (r["comment"]) {
                        map[id].wh[base].comment = r["comment"];
                    }

                    if (wh.includes("pack")) {
                        map[id].wh[base].packed = true;
                    }

                    const d = (r["Distribution"] || "").toUpperCase();
                    if (["LMD", "WAKILNI", "EMPLOYEE"].includes(d)) {
                        map[id].wh[base].distributed = true;
                        map[id].wh[base].distributor = d;

                        map[id].wh[base].distributedTime = r["Order Received in WH"]
                    }
                });

                allOrders = Object.values(map).map(o => {
                    const warehouses = Object.values(o.wh);
                    const packedCount = warehouses.filter(w => w.packed).length;
                    const isDistributed = warehouses.some(w => w.distributed);

                    let status = "pending";
                    if (isDistributed) status = "distributed";
                    else if (packedCount === warehouses.length) status = "completed";
                    else if (packedCount > 0) status = "partial";

                    const distWH = warehouses.find(w => w.distributed);
                    const distributor = distWH ? distWH.distributor : null;
                    const distributedTime = distWH ? distWH.distributedTime : null
                    warehouses.forEach(w => w.distributed = false);
                    if (distWH) distWH.distributed = true;

                    return {
                        ...o,
                        status,
                        warehouses,
                        warehouseCount: warehouses.length,
                        distributor,
                        distributedTime
                    };
                });

                initDate();
                updateDashboard();

                loadingOverlay.classList.add("hidden");
                dashboard.classList.remove("hidden");
            })
            .catch(err => {
                loadingOverlay.innerHTML = `
                <div class="loading-card">
                    <h2 style="color:#ef4444">MY HOLDAL</h2>
                    <p>Failed to load data</p>
                </div>
            `;
                console.error(err);
            });
    }

    // INIT DATE FILTER
    function initDate() {
        const dates = [...new Set(allOrders.map(o => o.date))].filter(Boolean).sort();
        if (!dates.length) return;

        dateFrom.value = dates[0];                 // أول تاريخ
        dateTo.value = dates[dates.length - 1];    // آخر تاريخ
    }

    // APPLY DATE FILTER
    function applyFilters() {
        const from = dateFrom.value ? new Date(dateFrom.value) : null;
        const to = dateTo.value ? new Date(dateTo.value) : null;

        return allOrders.filter(o => {
            if (!o.date) return false;

            const orderDate = new Date(o.date);

            if (from && orderDate < from) return false;
            if (to && orderDate > to) return false;

            return true;
        });
    }

    // UPDATE DASHBOARD KPIS
    function updateDashboard() {
        const o = applyFilters();
        total.textContent = o.length;
        completed.textContent = o.filter(x => x.status === "completed").length;

        // Pending KPI only counts non-distributed pending/partial orders
        pending.textContent = o.filter(x => (x.status === "pending" || x.status === "partial") && !x.distributor).length;

        distributed.textContent = o.filter(x => x.status === "distributed").length;

        renderWarehouseBreakdown(o);
        renderMultiWHOrders(o);
        renderSingleWHOrders(o);
    }

    // WAREHOUSE BREAKDOWN
    function renderWarehouseBreakdown(orders) {
        const m = {};
        let grandTotal = { t: 0, c: 0, p: 0, d: 0 }; // Total counters

        orders.forEach(o => {
            o.warehouses.forEach(w => {
                if (!m[w.base]) m[w.base] = { t: 0, c: 0, p: 0, d: 0 };

                // Increment totals per warehouse
                m[w.base].t++;
                if (o.status === "distributed") m[w.base].d++;
                else if (!o.distributor && w.packed) m[w.base].c++;
                else if (!o.distributor && !w.packed) m[w.base].p++;

                // Increment grand totals
                grandTotal.t++;
                if (o.status === "distributed") grandTotal.d++;
                else if (!o.distributor && w.packed) grandTotal.c++;
                else if (!o.distributor && !w.packed) grandTotal.p++;
            });
        });

        warehouseBreakdownTable.innerHTML = `
<table>
<tr>
 <th>Warehouse</th>
 <th>Total</th>
 <th>In-Packing</th>
 <th>Pending</th>
 <th>Delivered</th>
</tr>

${Object.entries(m).map(([k, v]) => `
<tr>
 <td>${k}</td>
<td><a href="#" onclick="showWarehouseOrders('${k}','total')">${v.t}</a></td>
<td><a href="#" onclick="showWarehouseOrders('${k}','completed')">${v.c}</a></td>
 <td><a href="#" onclick="showWarehouseOrders('${k}','pending')">${v.p}</a></td>
 <td><a href="#" onclick="showWarehouseOrders('${k}','distributed')">${v.d}</a></td>
</tr>`).join("")}

<tr style="font-weight:bold;background:#020617;color:#22c55e">
 <td>TOTAL</td>
 <td>${grandTotal.t}</td>
 <td>${grandTotal.c}</td>
 <td>${grandTotal.p}</td>
 <td>${grandTotal.d}</td>
</tr>
</table>`;
    }


    // MULTI-WAREHOUSE ORDERS
    function renderMultiWHOrders(orders) {
        const m = orders.filter(x => x.warehouseCount > 1);
        multiWHTable.innerHTML = `
<table>
<tr><th>Type</th><th>Orders</th></tr>
<tr><td>Total</td><td><a href="#" onclick="showMultiWHOrders('total')">${m.length}</a></td></tr>
<tr><td>In-Packing</td><td><a href="#" onclick="showMultiWHOrders('completed')">${m.filter(x => x.status === "completed").length}</a></td></tr>
<tr><td>Pending / partial </td><td><a href="#" onclick="showMultiWHOrders('pending')">${m.filter(x => (x.status === "pending" || x.status === "partial") && !x.distributor).length}</a></td></tr>
<tr><td>Distributed</td><td><a href="#" onclick="showMultiWHOrders('distributed')">${m.filter(x => x.status === "distributed").length}</a></td></tr>
</table>`;
    }

    // SINGLE-WAREHOUSE ORDERS
    function renderSingleWHOrders(orders) {
        const s = orders.filter(x => x.warehouseCount === 1);
        singleWHTable.innerHTML = `
<table>
<tr><th>Type</th><th>Orders</th></tr>
<tr><td>Total</td><td><a href="#" onclick="showSingleWHOrders('total')">${s.length}</a></td></tr>
<tr><td>In-Packing</td><td><a href="#" onclick="showSingleWHOrders('completed')">${s.filter(x => x.status === "completed").length}</a></td></tr>
<tr><td>Pending</td><td><a href="#" onclick="showSingleWHOrders('pending')">${s.filter(x => (x.status === "pending" || x.status === "partial") && !x.distributor).length}</a></td></tr>
<tr><td>Distributed</td><td><a href="#" onclick="showSingleWHOrders('distributed')">${s.filter(x => x.status === "distributed").length}</a></td></tr>
</table>`;
    }

    // SHOW ORDER DETAILS
    function showOrderDetails(type) {
        let o = applyFilters();
        if (type === "completed") o = o.filter(x => x.status === "completed");
        if (type === "pending") o = o.filter(x => (x.status === "pending" || x.status === "partial") && !x.distributor);
        if (type === "distributed") o = o.filter(x => x.status === "distributed");
        displayOrders(o);
    }

    // SHOW WAREHOUSE ORDERS
   function showWarehouseOrders(warehouse, type) {
    let o = applyFilters();

    if (warehouse !== 'all') {
        o = o.filter(order =>
            order.warehouses.some(w => w.base === warehouse)
        );
    }

    if (type === "completed") o = o.filter(x => x.status === "completed");
    if (type === "pending") o = o.filter(x => (x.status === "pending" || x.status === "partial") && !x.distributor);
    if (type === "distributed") o = o.filter(x => x.status === "distributed");
    if (type === "total") o = o; // all filtered orders

    displayOrders(o, warehouse === 'all' ? 'All Warehouses' : `Warehouse: ${warehouse}`);
}

    // SHOW MULTI/SINGLE-WAREHOUSE ORDERS
    function showMultiWHOrders(type) {
        let o = applyFilters().filter(x => x.warehouseCount > 1);
        if (type === "completed") o = o.filter(x => x.status === "completed");
        if (type === "pending") o = o.filter(x => (x.status === "pending" || x.status === "partial") && !x.distributor);
        if (type === "distributed") o = o.filter(x => x.status === "distributed");
        displayOrders(o, "Multi-Warehouse Orders");
    }

    function showSingleWHOrders(type) {
        let o = applyFilters().filter(x => x.warehouseCount === 1);
        if (type === "completed") o = o.filter(x => x.status === "completed");
        if (type === "pending") o = o.filter(x => (x.status === "pending" || x.status === "partial") && !x.distributor);
        if (type === "distributed") o = o.filter(x => x.status === "distributed");
        displayOrders(o, "Single-Warehouse Orders");
    }

    // DISPLAY ORDERS MODAL
    function displayOrders(o, title = null) {
        lastDisplayedOrders = o;
        orderList.innerHTML = "";
        orderDetailsTitle.textContent = title ? `Order Details - ${title}` : "Order Details";

        o.forEach(x => {
            orderList.innerHTML += `
<div class="warehouse-card">
 <b>Order:</b> ${x.orderNo} - ${x.status}
 <ul>${x.warehouses.map(w => `<li>${w.base} - ${w.packed ? "In-Packing" : "Pending"}</li>`).join("")}</ul>
</div>`;
        });

        orderDetails.classList.remove("hidden");
    }
    function toggleMenu(id) {
        const menu = document.getElementById(id);
        if (!menu) return;

        const parent = menu.parentElement;
        parent.classList.toggle("menu-open");

        menu.style.display =
            menu.style.display === "block" ? "none" : "block";
    }

    const toggleToDateBtn = document.getElementById("toggleToDate");
    const dateToInput = document.getElementById("dateTo");

    // toggleToDateBtn.addEventListener("click", () => {
    //     if (dateToInput.style.display === "none") {
    //         dateToInput.style.display = "inline-block";
    //         toggleToDateBtn.textContent = "− Range"; // تغيير الزر
    //     } else {
    //         dateToInput.style.display = "none";
    //         toggleToDateBtn.textContent = "+ Range";
    //         dateToInput.value = ""; // مسح القيمة عند الإخفاء
    //         updateDashboard(); // إعادة حساب الفلترة
    //     }
    // });

    // CLOSE MODAL
    function closeOrderDetails() { orderDetails.classList.add("hidden"); }

    // EXPORT TO EXCEL
    function exportOrderDetailsToExcel() {
        if (!lastDisplayedOrders.length) {
            alert("No orders to export!");
            return;
        }

        const headers = ["Order", "Status", "Warehouses", "Distributor"];

        const rows = lastDisplayedOrders.map(o => {
            const whs = o.warehouses.map(w => {
                let status = w.packed ? "In-Packing" : "Pending";
                if (w.distributed) status = "Distributed";
                return `${w.base}`;
            }).join(" | ");

            return [
                o.orderNo,
                o.status,
                whs,
                o.distributor || ""
            ];
        });

        // CSV with proper escaping
        const csv = [
            headers.join(","),
            ...rows.map(r =>
                r.map(v => `"${String(v).replace(/"/g, '""')}"`).join(",")
            )
        ].join("\r\n");

        // Use Blob (Excel-safe)
        const blob = new Blob([csv], { type: "text/csv;charset=utf-8;" });
        const url = URL.createObjectURL(blob);

        const link = document.createElement("a");
        link.href = url;
        link.download = "order_details.csv";
        document.body.appendChild(link);
        link.click();

        document.body.removeChild(link);
        URL.revokeObjectURL(url);
    }

    // SHOW WAREHOUSES PAGE
    function showWarehouses() { }

    // SIGN OUT
    function signOut() { dashboard.classList.add("hidden"); loginContainer.style.display = "flex"; }



</script>
</body>

</html>
