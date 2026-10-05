<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-title" content="NEXSIGN" />
  <meta name="theme-color" content="#FF7A00" />
  <title>NEXSIGN — 全屋报价系统</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: system-ui, -apple-system, sans-serif; }
    :root { --blue: #0A2351; --orange: #FF7A00; --red: #E6212A; --gray: #666; --light-gray: #f5f5f5; --border: #e5e5e5; }
    .hidden { display: none !important; }

    /* 登录页 */
    .login-wrap { min-height: 100vh; display: flex; align-items: center; justify-content: center; background: linear-gradient(135deg, #0A2351, #16213e); padding: 20px; }
    .login-card { background: #fff; border-radius: 20px; padding: 36px 24px; width: 100%; max-width: 420px; }
    .login-logo { text-align: center; margin-bottom: 24px; }
    .login-logo img { height: 100px; object-fit: contain; }
    .logo-text { font-size: 32px; font-weight: 800; color: var(--blue); text-align: center; }
    .logo-text span { color: var(--orange); }
    .logo-zh { font-size: 22px; font-weight: 700; color: var(--red); text-align: center; margin: 6px 0 24px; }
    input, button { font-size: 15px; }
    input { 
      width: 100%; padding: 10px 12px; border: 1px solid var(--border); border-radius: 4px;
      background: #fff; color: #000;
    }
    input:focus { outline: 2px solid var(--orange); border-color: var(--orange); }
    .btn-login { width: 100%; padding: 14px; background: var(--orange); border: none; border-radius: 8px; font-size: 17px; font-weight: 700; cursor: pointer; margin-top: 8px; }
    .error { color: var(--red); text-align: center; margin-top: 12px; display: none; }
    .error.show { display: block; }
    .tip { text-align: center; margin-top: 16px; font-size: 13px; color: #999; }

    /* 顶部导航栏 */
    .top-nav { 
      background: #fff; border-bottom: 1px solid var(--border); 
      padding: 0 16px; height: 56px; line-height: 56px;
      display: flex; align-items: center; justify-content: space-between;
      position: sticky; top: 0; z-index: 100; box-shadow: 0 1px 3px rgba(0,0,0,0.05);
    }
    .nav-left { display: flex; align-items: center; gap: 4px; }
    .nav-logo { height: 36px; margin-right: 8px; }
    .nav-logo img { height: 100%; object-fit: contain; }
    .nav-tab { 
      padding: 0 20px; height: 56px; line-height: 56px; cursor: pointer;
      font-size: 14px; color: #555; border-bottom: 3px solid transparent;
      transition: all 0.2s;
    }
    .nav-tab:hover { background: #fafafa; color: #333; }
    .nav-tab.active { 
      background: #fff; border-bottom: 3px solid var(--orange); 
      color: var(--orange); font-weight: 600;
    }
    .nav-tab.locked { position: relative; }
    .nav-tab.locked::after {
      content: "🔒"; position: absolute; right: 6px; top: 4px; font-size: 12px;
    }
    .nav-tab.active.locked { padding-right: 28px; }
    
    .nav-right { display: flex; align-items: center; gap: 12px; }
    .lang-btn { 
      padding: 4px 10px; border: 1px solid #ddd; border-radius: 4px; 
      background: #fff; cursor: pointer; font-size: 13px; color: #555;
    }
    .lang-btn:hover { border-color: var(--orange); color: var(--orange); }
    .user-name { font-size: 14px; color: #333; padding: 0 8px; }
    .nav-btn { 
      padding: 6px 14px; border: none; border-radius: 4px; cursor: pointer;
      font-size: 13px; font-weight: 500;
    }
    .btn-pwd { background: #f0f0f0; color: #333; }
    .btn-logout { background: var(--red); color: #fff; }

    .container { padding: 20px; max-width: 1280px; margin: 0 auto; }
    .card { background: #fff; border-radius: 8px; padding: 20px; margin-bottom: 16px; border: 1px solid var(--border); }
    table { width: 100%; border-collapse: collapse; font-size: 14px; }
    th { background: #f9fafb; padding: 10px 8px; text-align: left; border-bottom: 1px solid var(--border); font-weight: 600; color: #333; white-space: nowrap; }
    td { padding: 8px; border-bottom: 1px solid #f0f0f0; vertical-align: middle; }
    td input { padding: 6px 8px; border-radius: 4px; margin: 0; font-size: 14px; border: 1px solid #ddd; }
    td input:focus { border-color: var(--orange); outline: 2px solid rgba(255,122,0,0.2); }
    .text-right { text-align: right; }
    .text-center { text-align: center; }
    .btn-bar { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 16px; }
    .btn { padding: 10px 16px; border: none; border-radius: 6px; font-weight: 600; cursor: pointer; font-size: 14px; }
    .btn-o { background: var(--orange); color: #000; }
    .btn-b { background: var(--blue); color: #fff; }
    .btn-g { background: var(--light-gray); color: #333; border: 1px solid var(--border); }
    .btn-sm { padding: 6px 12px; font-size: 13px; cursor: pointer; position: relative; z-index: 10; }
    .btn-xs { padding: 4px 8px; font-size: 12px; cursor: pointer; position: relative; z-index: 10; }
    .btn-del { background: none; border: none; color: var(--red); cursor: pointer; font-size: 18px; position: relative; z-index: 10; }

    /* 照片/PDF上传 */
    .media-cell { width: 80px; }
    .upload-wrap { position: relative; }
    .upload-btn { 
      width: 50px; height: 50px; border-radius: 6px; border: 1px dashed #ccc; 
      background: #fafafa; cursor: pointer; display: flex; flex-direction: column;
      align-items: center; justify-content: center; font-size: 16px; color: #999;
      gap: 2px;
    }
    .upload-btn:hover { border-color: var(--orange); color: var(--orange); }
    .upload-btn span { font-size: 9px; }
    .media-preview { width: 50px; height: 50px; object-fit: cover; border-radius: 6px; cursor: pointer; }
    .pdf-icon { 
      width: 50px; height: 50px; border-radius: 6px; background: #fef0f0; 
      display: flex; flex-direction: column; align-items: center; justify-content: center;
      color: var(--red); font-size: 20px; cursor: pointer;
    }
    .pdf-icon span { font-size: 8px; color: #c00; margin-top: 2px; }
    input[type="file"] { display: none; }
    .media-actions { display: flex; gap: 4px; margin-top: 2px; }
    .media-actions button { padding: 2px 6px; font-size: 10px; border: none; border-radius: 3px; cursor: pointer; }
    .btn-view { background: #e8f0fe; color: #1a73e8; }
    .btn-remove { background: #fee; color: #c00; }

    /* 区块样式 */
    .block-card { background: #fff; border-radius: 8px; margin-bottom: 20px; border: 1px solid var(--border); overflow: hidden; }
    .block-header { padding: 12px 16px; border-bottom: 1px solid var(--border); display: flex; align-items: center; gap: 10px; background: #fafafa; }
    .block-name { flex: 1; font-size: 15px; font-weight: 600; border: 1px solid transparent; background: transparent; padding: 4px 8px; border-radius: 4px; }
    .block-name:focus { border-color: var(--orange); background: #fff; outline: none; }
    .block-del { margin-left: auto; }
    .block-body { padding: 16px; }
    .block-actions { margin: 12px 0; display: flex; gap: 10px; }
    .add-block-area { border: 2px dashed #ddd; border-radius: 8px; padding: 20px; text-align: center; cursor: pointer; color: #999; margin: 10px 0; }
    .add-block-area:hover { border-color: var(--orange); color: var(--orange); }
    .subtotal-row { text-align: right; padding: 10px 16px; font-weight: 600; border-top: 1px solid #f0f0f0; }

    /* 底部汇总 */
    .summary-box { background: #fff; border-radius: 8px; padding: 20px; margin-top: 16px; border: 1px solid var(--border); }
    .summary-inner { display: flex; flex-wrap: wrap; gap: 20px; }
    .summary-left { flex: 1; min-width: 280px; }
    .summary-right { flex: 1; min-width: 280px; }
    .check-row { display: flex; align-items: center; gap: 8px; margin: 10px 0; }
    .check-row input[type="checkbox"] { width: auto; margin: 0; cursor: pointer; }
    .check-row label { font-size: 14px; cursor: pointer; }
    .input-inline { display: flex; align-items: center; gap: 6px; margin: 6px 0 6px 24px; }
    .input-inline input { width: 80px; padding: 6px; }
    .total-row { display: flex; justify-content: space-between; padding: 8px 0; font-size: 14px; }
    .total-row.border-top { border-top: 1px solid #eee; margin-top: 8px; padding-top: 12px; }
    .total-row.final { font-size: 18px; font-weight: 700; color: var(--orange); padding-top: 12px; border-top: 2px solid #f0f0f0; margin-top: 4px; }
    .total-label { color: #333; }
    .total-value { font-weight: 600; }
    
    .bottom-actions { margin-top: 24px; display: flex; gap: 10px; flex-wrap: wrap; }
    .btn-save { background: #222; color: #fff; }
    .btn-pdf { background: var(--orange); color: #000; }

    /* 费率库图标分类 */
    .rate-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px; }
    .rate-title { font-size: 18px; font-weight: 700; color: #333; }
    .rate-search { width: 260px; }

    .icon-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(76px, 1fr)); gap: 12px; margin-bottom: 24px; }
    .icon-item { 
      display: flex; flex-direction: column; align-items: center; justify-content: center;
      gap: 6px; padding: 12px 8px; border-radius: 8px; background: #fafafa;
      cursor: pointer; transition: 0.2s; border: 1px solid transparent;
    }
    .icon-item:hover { background: #fff; border-color: var(--orange); }
    .icon-item.active { background: #fff; border-color: var(--orange); box-shadow: 0 2px 8px rgba(255,122,0,0.15); }
    .icon-circle { 
      width: 48px; height: 48px; border-radius: 12px; background: #f5f5f5;
      display: flex; align-items: center; justify-content: center; font-size: 24px;
    }
    .icon-item.active .icon-circle { background: var(--orange); color: #fff; }
    .icon-label { font-size: 12px; color: #555; text-align: center; }
    .icon-item.active .icon-label { color: var(--orange); font-weight: 600; }

    .rate-table-section { margin-top: 16px; }
    .rate-table-title { font-size: 16px; font-weight: 600; margin-bottom: 12px; color: #333; }
  </style>
</head>
<body>

<div id="loginPage" class="login-wrap">
  <div class="login-card">
    <div class="login-logo">
      <!-- 把 logo.png 换成你上传的 Logo 文件名 -->
      <img src="logo.png" alt="NEXSIGN 新帜" />
    </div>
    <input type="text" id="username" placeholder="账号" />
    <input type="password" id="password" placeholder="密码" />
    <button class="btn-login" onclick="doLogin()">登 录</button>
    <div class="error" id="errorMsg">❌ 账号或密码错误</div>
    <div class="tip">admin / admin123</div>
  </div>
</div>

<div id="mainPage" class="hidden">
  <!-- 顶部导航栏 -->
  <nav class="top-nav">
    <div class="nav-left">
      <div class="nav-logo">
        <!-- 把 logo.png 换成你上传的 Logo 文件名 -->
        <img src="logo.png" alt="NEXSIGN 新帜" />
      </div>
      <div class="nav-tab active" data-page="newquote" onclick="goPage('newquote')">新建报价</div>
      <div class="nav-tab" data-page="history" onclick="goPage('history')">历史报价 (1)</div>
      <div class="nav-tab locked" data-page="ratelib" onclick="goPage('ratelib')">费率库</div>
      <div class="nav-tab" data-page="progress" onclick="goPage('progress')">项目进度</div>
      <div class="nav-tab" data-page="expense" onclick="goPage('expense')">我的报销</div>
    </div>
    <div class="nav-right">
      <button class="lang-btn" onclick="toggleLang()">EN</button>
      <span class="user-name" id="userDisplay">销售 · Jasper Fong</span>
      <button class="nav-btn btn-pwd" onclick="alert('改密码功能')">改密码</button>
      <button class="nav-btn btn-logout" onclick="doLogout()">退出</button>
    </div>
  </nav>

  <div class="container">
    <!-- 新建报价（主页面） -->
    <div id="page-newquote" class="page">
      <div class="card">
        <h3 style="margin-bottom:16px;">客户信息</h3>
        <div style="display:grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap:12px;">
          <div><label style="font-size:13px; color:#666;">客户姓名</label><input type="text" id="cname" /></div>
          <div><label style="font-size:13px; color:#666;">日期</label><input type="date" id="qdate" /></div>
        </div>
      </div>

      <div id="blocksContainer"></div>

      <div class="add-block-area" onclick="addBlock()">+ 加区块</div>

      <div class="summary-box">
        <div class="summary-inner">
          <div class="summary-left">
            <div class="check-row">
              <input type="checkbox" id="chkServiceFee" onchange="calcAll()" checked />
              <label for="chkServiceFee">收综合服务费 (10%)</label>
            </div>
            <div class="check-row">
              <input type="checkbox" id="chkSST" onchange="calcAll()" checked />
              <label for="chkSST">收服务税 SST</label>
            </div>
            <div class="input-inline">
              <span>税率</span>
              <input type="number" id="sstRate" value="6" oninput="calcAll()" />
              <span>%</span>
            </div>
            <div class="check-row">
              <input type="checkbox" id="chkDesignFee" onchange="calcAll()" checked />
              <label for="chkDesignFee">收设计费</label>
            </div>
            <div class="input-inline">
              <span>设计费单价 (RM/sqft)</span>
              <input type="number" id="designPrice" value="55" oninput="calcAll()" />
            </div>
            <div class="input-inline">
              <span>面积 (sqft)</span>
              <input type="number" id="designArea" value="" placeholder="填面积" oninput="calcAll()" />
            </div>
          </div>
          <div class="summary-right">
            <div class="total-row">
              <span class="total-label">工程直接费合计</span>
              <span class="total-value">RM <span id="baseTotal">0.00</span></span>
            </div>
            <div class="total-row" id="rowServiceFee">
              <span class="total-label">综合服务费 (10%)</span>
              <span class="total-value">RM <span id="serviceFeeAmt">0.00</span></span>
            </div>
            <div class="total-row" id="rowSST">
              <span class="total-label">服务税 SST (<span id="sstLabel">6</span>%)</span>
              <span class="total-value">RM <span id="sstAmt">0.00</span></span>
            </div>
            <div class="total-row border-top">
              <span class="total-label">总造价</span>
              <span class="total-value">RM <span id="subTotal">0.00</span></span>
            </div>
            <div class="total-row" id="rowDesignFee">
              <span class="total-label">设计费</span>
              <span class="total-value">RM <span id="designFeeAmt">0.00</span></span>
            </div>
            <div class="total-row final">
              <span class="total-label">总计 (含设计费)</span>
              <span class="total-value">RM <span id="grandTotal">0.00</span></span>
            </div>
          </div>
        </div>
        <div class="bottom-actions">
          <button class="btn btn-save" onclick="saveQuote()">保存</button>
          <button class="btn btn-pdf" onclick="exportPDF()">导出/打印 PDF</button>
          <button class="btn btn-g" onclick="clearAll()">清空重开</button>
        </div>
      </div>
    </div>

    <!-- 费率库 → 图标分类版 -->
    <div id="page-ratelib" class="page hidden">
      <div class="card">
        <div class="rate-header">
          <h3 class="rate-title">费率库</h3>
          <input type="text" id="searchInput" class="rate-search" placeholder="搜索项目名称..." oninput="renderRate()" />
        </div>

        <!-- 图标分类 -->
        <div class="icon-grid" id="iconGrid"></div>

        <!-- 费率表格 -->
        <div class="rate-table-section">
          <div class="rate-table-title" id="categoryTitle">全部项目</div>
          <div id="rateTable"></div>
        </div>

        <div class="btn-bar">
          <button class="btn btn-o" onclick="addRateRow()">➕ 添加项目</button>
          <button class="btn btn-g" onclick="resetRate()">↩️ 恢复默认</button>
          <button class="btn btn-b" onclick="goPage('newquote')">→ 去报价单</button>
        </div>
      </div>
    </div>

    <!-- 其他页面占位 -->
    <div id="page-history" class="page hidden">
      <div class="card"><h3>📄 历史报价</h3><p style="padding:20px; color:#888;">暂无历史记录</p></div>
    </div>
    <div id="page-progress" class="page hidden">
      <div class="card"><h3>📊 项目进度</h3><p style="padding:20px; color:#888;">开发中...</p></div>
    </div>
    <div id="page-expense" class="page hidden">
      <div class="card"><h3>💰 我的报销</h3><p style="padding:20px; color:#888;">开发中...</p></div>
    </div>
  </div>
</div>

<script>
localStorage.removeItem("nexsign_rates");

const USER = "admin", PASS = "admin123";
const USER_NAME = "销售 · Jasper Fong";
const MARKUP = 1.5;
let langEN = false;

// 分类图标
const categories = [
  { id: "all", name: "全部", icon: "📋" },
  { id: "sink", name: "Sink", icon: "🚰" },
  { id: "cabinet", name: "柜子", icon: "🗄️" },
  { id: "door", name: "门", icon: "🚪" },
  { id: "window", name: "窗", icon: "🪟" },
  { id: "floor", name: "地板", icon: "🧱" },
  { id: "wall", name: "墙面", icon: "🏗️" },
  { id: "ceiling", name: "吊顶", icon: "🔲" },
  { id: "light", name: "灯具", icon: "💡" },
  { id: "sanitary", name: "卫浴", icon: "🚿" },
  { id: "hardware", name: "五金", icon: "🔩" },
  { id: "paint", name: "油漆", icon: "🎨" },
  { id: "tile", name: "瓷砖", icon: "🧱" },
  { id: "stone", name: "石材", icon: "🪨" },
  { id: "glass", name: "玻璃", icon: "🥛" },
  { id: "aluminium", name: "铝材", icon: "🔧" },
  { id: "accessory", name: "配件", icon: "🧩" }
];

let activeCategory = "all";

const defaultRates = [
  { id:1, cat:"sink", name:"不锈钢洗菜盆", unit:"个", price:850, code:"XCP-001", desc:" SUS304, 600x450mm 600x450mm 人工, 辅材" },
  { id:2, cat:"sink", name:"水龙头无铅水嘴", unit:"个", price:250, code:"XCP-003", desc:" SUS304, 600x450mm 600x450mm 人工, 辅材" },
  { id:3, cat:"sink", name:"SORENTO 不锈钢单槽套装", unit:"套", price:2300, code:"XCP-002", desc:" SUS304, 600x450mm 600x450mm 人工, 辅材" },
  { id:4, cat:"sink", name:"不锈钢洗菜盆", unit:"个", price:450, code:"XCP-002", desc:" SUS304, 600x450mm 600x450mm 人工, 辅材" },
  { id:5, cat:"cabinet", name:"Melamine E0 NO WARRANTY", unit:"ft", price:400 },
  { id:6, cat:"cabinet", name:"Melamine E1 NO WARRANTY", unit:"ft", price:360 },
  { id:7, cat:"cabinet", name:"吊柜 700mm高", unit:"ft", price:420 },
  { id:8, cat:"cabinet", name:"吊柜 800mm高", unit:"ft", price:460 },
  { id:9, cat:"cabinet", name:"吊柜 900mm高", unit:"ft", price:500 },
  { id:10, cat:"cabinet", name:"标准柜体 melamine E1", unit:"sqft", price:95 },
  { id:11, cat:"cabinet", name:"加厚柜体 melamine E0", unit:"sqft", price:115 }
];

let rateData = [];
let blocks = [];
let blockId = 0;

function doLogin() {
  const u = document.getElementById("username").value.trim();
  const p = document.getElementById("password").value;
  if (u === USER && p === PASS) {
    localStorage.setItem("nexsign_user", USER);
    document.getElementById("loginPage").classList.add("hidden");
    document.getElementById("mainPage").classList.remove("hidden");
    document.getElementById("userDisplay").textContent = USER_NAME;
    init();
  } else {
    document.getElementById("errorMsg").classList.add("show");
  }
}
function doLogout() { localStorage.removeItem("nexsign_user"); location.reload(); }
window.onload = () => {
  if (localStorage.getItem("nexsign_user") === USER) {
    document.getElementById("loginPage").classList.add("hidden");
    document.getElementById("mainPage").classList.remove("hidden");
    document.getElementById("userDisplay").textContent = USER_NAME;
    init();
  }
};

function toggleLang() {
  langEN = !langEN;
  alert(langEN ? "已切换到英文" : "已切换到中文");
}

function init() {
  rateData = [...defaultRates];
  document.getElementById("qdate").valueAsDate = new Date();
  renderIcons();
  renderRate();
  if (blocks.length === 0) addBlock();
}

function goPage(page) {
  document.querySelectorAll(".nav-tab").forEach(t => t.classList.toggle("active", t.dataset.page === page));
  document.querySelectorAll(".page").forEach(p => p.classList.toggle("hidden", p.id !== `page-${page}`));
  if (page === "newquote") renderQuote();
  if (page === "ratelib") { renderIcons(); renderRate(); }
}

// 渲染分类图标
function renderIcons() {
  document.getElementById("iconGrid").innerHTML = categories.map(c => `
    <div class="icon-item ${activeCategory === c.id ? "active" : ""}" onclick="setCategory('${c.id}')">
      <div class="icon-circle">${c.icon}</div>
      <div class="icon-label">${c.name}</div>
    </div>
  `).join("");
}

function setCategory(catId) {
  activeCategory = catId;
  renderIcons();
  renderRate();
}

// 费率库表格
function renderRate() {
  let list = [...rateData];
  const kw = document.getElementById("searchInput")?.value.toLowerCase() || "";

  if (activeCategory !== "all") {
    list = list.filter(r => r.cat === activeCategory);
  }

  if (kw) {
    list = list.filter(r => r.name.toLowerCase().includes(kw) || (r.code && r.code.toLowerCase().includes(kw)));
  }

  const catName = categories.find(c => c.id === activeCategory)?.name || "全部";
  document.getElementById("categoryTitle").textContent = catName + "项目";

  document.getElementById("rateTable").innerHTML = `
    <table><thead><tr>
      <th>编号</th>
      <th>项目名称</th>
      <th>分类</th>
      <th>单位</th>
      <th class="text-right">单价(RM)</th>
      <th>工艺做法及材料说明</th>
      <th style="width:90px;" class="text-center">操作</th>
    </tr></thead><tbody>
    ${list.map(r => `
      <tr>
        <td>${r.code || "-"}</td>
        <td><input type="text" value="${r.name}" oninput="updateRate(${r.id},'name',this.value)" /></td>
        <td>
          <select onchange="updateRate(${r.id},'cat',this.value)" style="padding:4px; border-radius:4px; border:1px solid #ddd;">
            ${categories.map(c => `<option value="${c.id}" ${r.cat === c.id ? "selected" : ""}>${c.name}</option>`).join("")}
          </select>
        </td>
        <td><input type="text" value="${r.unit}" oninput="updateRate(${r.id},'unit',this.value)" style="width:70px;" /></td>
        <td class="text-right"><input type="number" value="${r.price}" oninput="updateRate(${r.id},'price',+this.value||0)" style="width:100px; text-align:right;" /></td>
        <td><input type="text" value="${r.desc || ""}" oninput="updateRate(${r.id},'desc',this.value)" placeholder="说明..." /></td>
        <td class="text-center"><button class="btn btn-sm btn-o" onclick="selectRate(${r.id})">选择</button></td>
      </tr>
    `).join("")}
    </tbody></table>
  `;
}

function updateRate(id, f, v) {
  const r = rateData.find(x => x.id === id);
  if (r) { r[f] = v; }
}

function addRateRow() {
  const newId = rateData.length ? Math.max(...rateData.map(r => r.id)) + 1 : 1;
  rateData.push({ id: newId, cat: activeCategory === "all" ? "cabinet" : activeCategory, name:"新项目", unit:"pc", price:0, code:"", desc:"" });
  renderRate();
}

function resetRate() {
  if (confirm("恢复默认费率库？")) {
    rateData = [...defaultRates];
    activeCategory = "all";
    renderIcons();
    renderRate();
  }
}

function selectRate(rid) {
  const r = rateData.find(x => x.id === rid);
  if (!r) return;
  if (blocks.length === 0) { addBlock(); }
  const lastBlock = blocks[blocks.length - 1];
  lastBlock.items.push({ name: r.name, unit: r.unit, price: r.price, qty:1, mediaData:"", mediaType:"", code: r.code || "", desc: r.desc || "" });
  renderQuote();
  alert(`✅ 已添加：${r.name}`);
}

// 区块
function addBlock() {
  blockId++;
  blocks.push({ id:blockId, name:"定制项目", items:[] });
  renderQuote();
}
function delBlock(bid) {
  if (confirm("删除此区块？")) {
    blocks = blocks.filter(b => b.id !== bid);
    renderQuote();
  }
}
function addItemRow(bid) {
  const b = blocks.find(x => x.id === bid);
  b.items.push({ name:"", unit:"ft", price:0, qty:1, mediaData:"", mediaType:"", code:"", desc:"" });
  renderQuote();
}
function delItemRow(bid, idx) {
  blocks.find(x => x.id === bid).items.splice(idx, 1);
  renderQuote();
}

// 照片/PDF上传
function handleMediaUpload(bid, idx, input) {
  const file = input.files[0];
  if (!file) return;
  
  const isImage = file.type.startsWith("image/");
  const isPDF = file.type === "application/pdf";
  
  if (!isImage && !isPDF) {
    alert("❌ 只支持图片或PDF文件");
    return;
  }
  
  const reader = new FileReader();
  reader.onload = function(e) {
    const b = blocks.find(x => x.id === bid);
    if (b && b.items[idx]) {
      b.items[idx].mediaData = e.target.result;
      b.items[idx].mediaType = isPDF ? "pdf" : "image";
      b.items[idx].mediaName = file.name;
      renderQuote();
    }
  };
  reader.readAsDataURL(file);
}

function viewMedia(bid, idx) {
  const b = blocks.find(x => x.id === bid);
  if (!b || !b.items[idx]) return;
  const item = b.items[idx];
  if (!item.mediaData) return;
  
  const w = window.open();
  w.document.write(`<html><body style="margin:0;"><embed src="${item.mediaData}" width="100%" height="100%" type="${item.mediaType === 'pdf' ? 'application/pdf' : ''}" /></body></html>`);
}

function removeMedia(bid, idx) {
  const b = blocks.find(x => x.id === bid);
  if (!b || !b.items[idx]) return;
  b.items[idx].mediaData = "";
  b.items[idx].mediaType = "";
  b.items[idx].mediaName = "";
  renderQuote();
}

// 渲染报价单
function renderQuote() {
  document.getElementById("blocksContainer").innerHTML = blocks.map((b, bIdx) => {
    const blockSubtotal = b.items.reduce((s, r) => s + (r.price||0)*(r.qty||0)*MARKUP, 0);
    return `
      <div class="block-card">
        <div class="block-header">
          <span style="color:#999; font-size:13px;">区块名称</span>
          <input type="text" class="block-name" value="${b.name}" 
                 oninput="updateBlockName(${b.id}, this.value)" />
          <button class="btn-del block-del" onclick="delBlock(${b.id})">×</button>
        </div>
        <div class="block-body">
          <table>
            <thead>
              <tr>
                <th style="width:50px;" class="text-center">序号</th>
                <th style="width:80px;" class="text-center">附件</th>
                <th style="width:80px;">编号</th>
                <th>项目名称</th>
                <th style="width:70px;">单位</th>
                <th style="width:100px;" class="text-right">单价(RM)</th>
                <th style="width:70px;" class="text-right">数量</th>
                <th style="width:110px;" class="text-right">金额(RM)</th>
                <th style="width:180px;">工艺做法及材料说明</th>
                <th style="width:40px;"></th>
              </tr>
            </thead>
            <tbody>
              ${b.items.map((r, i) => {
                const amt = ((r.price||0)*(r.qty||0)*MARKUP).toFixed(2);
                return `
                  <tr>
                    <td class="text-center">${i+1}</td>
                    <td class="media-cell text-center">
                      ${!r.mediaData 
                        ? `<label class="upload-btn">+<span>图/PDF</span><input type="file" accept="image/*,.pdf" onchange="handleMediaUpload(${b.id}, ${i}, this)" /></label>`
                        : `<div class="upload-wrap">
                            ${r.mediaType === "pdf" 
                              ? `<div class="pdf-icon" onclick="viewMedia(${b.id},${i})">📄<span>PDF</span></div>`
                              : `<img src="${r.mediaData}" class="media-preview" onclick="viewMedia(${b.id},${i})" alt="预览" />`
                            }
                            <div class="media-actions">
                              <button class="btn-view" onclick="viewMedia(${b.id},${i})">查看</button>
                              <button class="btn-remove" onclick="removeMedia(${b.id},${i})">删除</button>
                            </div>
                          </div>`
                      }
                    </td>
                    <td><input type="text" value="${r.code || ""}" placeholder="编号" oninput="updateItem(${b.id}, ${i}, 'code', this.value)" /></td>
                    <td><input type="text" value="${r.name}" 
                           oninput="updateItem(${b.id}, ${i}, 'name', this.value)" /></td>
                    <td><input type="text" value="${r.unit}" 
                           oninput="updateItem(${b.id}, ${i}, 'unit', this.value)" /></td>
                    <td class="text-right"><input type="number" value="${r.price}" 
                           oninput="updateItem(${b.id}, ${i}, 'price', +this.value||0)" 
                           style="width:90px; text-align:right;" /></td>
                    <td class="text-right"><input type="number" value="${r.qty}" 
                           oninput="updateItem(${b.id}, ${i}, 'qty', +this.value||0)" 
                           style="width:50px; text-align:right;" /></td>
                    <td class="text-right" style="font-weight:600; color:var(--orange);">${amt}</td>
                    <td><input type="text" value="${r.desc || ""}" placeholder="说明..." 
                           oninput="updateItem(${b.id}, ${i}, 'desc', this.value||'')" /></td>
                    <td><button class="btn-del" onclick="delItemRow(${b.id}, ${i})">×</button></td>
                  </tr>
                `;
              }).join("")}
            </tbody>
          </table>
          <div class="block-actions">
            <button class="btn btn-sm btn-g" onclick="addItemRow(${b.id})">+ 加项目</button>
            <button class="btn btn-sm btn-o" onclick="goPage('ratelib')">从费率库选</button>
          </div>
          <div class="subtotal-row">小计：RM ${blockSubtotal.toFixed(2)}</div>
        </div>
      </div>
    `;
  }).join("");
  calcAll();
}

function updateBlockName(bid, val) {
  const b = blocks.find(x => x.id === bid);
  b.name = val;
}
function updateItem(bid, idx, field, val) {
  const b = blocks.find(x => x.id === bid);
  if (!b.items[idx]) b.items[idx] = { name:"", unit:"", price:0, qty:1, mediaData:"", mediaType:"", code:"", desc:"" };
  b.items[idx][field] = val;
  calcAll();
}

// 计算
function calcAll() {
  const baseSum = blocks.reduce((sum, b) => 
    sum + b.items.reduce((s, r) => s + (r.price||0)*(r.qty||0), 0), 0
  );
  const directTotal = baseSum * MARKUP;

  const serviceFeeEnabled = document.getElementById("chkServiceFee").checked;
  const serviceFee = serviceFeeEnabled ? directTotal * 0.10 : 0;
  document.getElementById("rowServiceFee").style.display = serviceFeeEnabled ? "flex" : "none";

  const sstEnabled = document.getElementById("chkSST").checked;
  const sstRateVal = +document.getElementById("sstRate").value / 100 || 0.06;
  document.getElementById("sstLabel").textContent = Math.round(sstRateVal*100);
  const afterService = directTotal + serviceFee;
  const sstAmt = sstEnabled ? afterService * sstRateVal : 0;
  document.getElementById("rowSST").style.display = sstEnabled ? "flex" : "none";

  const subTotal = afterService + sstAmt;

  const designEnabled = document.getElementById("chkDesignFee").checked;
  const dPrice = +document.getElementById("designPrice").value || 0;
  const dArea = +document.getElementById("designArea").value || 0;
  const designFee = designEnabled ? dPrice * dArea : 0;
  document.getElementById("rowDesignFee").style.display = designEnabled ? "flex" : "none";

  const grandTotal = subTotal + designFee;

  document.getElementById("baseTotal").textContent = directTotal.toFixed(2);
  document.getElementById("serviceFeeAmt").textContent = serviceFee.toFixed(2);
  document.getElementById("sstAmt").textContent = sstAmt.toFixed(2);
  document.getElementById("subTotal").textContent = subTotal.toFixed(2);
  document.getElementById("designFeeAmt").textContent = designFee.toFixed(2);
  document.getElementById("grandTotal").textContent = grandTotal.toFixed(2);
}

function saveQuote() {
  localStorage.setItem("nexsign_blocks", JSON.stringify(blocks));
  alert("✅ 保存成功！");
}
function exportPDF() {
  window.print();
}
function clearAll() {
  if (confirm("确定清空所有内容？")) {
    blocks = [];
    localStorage.removeItem("nexsign_blocks");
    addBlock();
  }
}
</script>
</body>
</html>
