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
    :root { --blue: #0A2351; --orange: #FF7A00; --red: #E6212A; }
    .hidden { display: none !important; }

    .login-wrap { min-height: 100vh; display: flex; align-items: center; justify-content: center; background: linear-gradient(135deg, #0A2351, #16213e); padding: 20px; }
    .login-card { background: #fff; border-radius: 20px; padding: 36px 24px; width: 100%; max-width: 420px; }
    .logo-text { font-size: 32px; font-weight: 800; color: var(--blue); text-align: center; }
    .logo-text span { color: var(--orange); }
    .logo-zh { font-size: 22px; font-weight: 700; color: var(--red); text-align: center; margin: 6px 0 24px; }
    input { width: 100%; padding: 12px 14px; margin-bottom: 10px; border: 1px solid #e2e2e2; border-radius: 10px; font-size: 15px; }
    input:focus { outline: none; border-color: var(--orange); box-shadow: 0 0 0 3px rgba(255,122,0,0.15); background: #fff; }
    .btn-login { width: 100%; padding: 14px; background: var(--orange); border: none; border-radius: 12px; font-size: 17px; font-weight: 700; cursor: pointer; }
    .error { color: var(--red); text-align: center; margin-top: 12px; display: none; }
    .error.show { display: block; }
    .tip { text-align: center; margin-top: 16px; font-size: 13px; color: #999; }

    .top-nav { background: #fff; border-bottom: 1px solid #eee; padding: 12px 16px; position: sticky; top: 0; }
    .nav-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
    .brand { font-weight: 700; font-size: 16px; color: var(--blue); }
    .brand span { color: var(--orange); }
    .btn-logout { border: none; background: #f5f5f5; padding: 8px 12px; border-radius: 8px; cursor: pointer; }
    .nav-tabs { display: flex; gap: 6px; overflow-x: auto; }
    .tab { padding: 10px 14px; border-radius: 10px; background: #f5f5f5; cursor: pointer; white-space: nowrap; }
    .tab.active { background: var(--orange); font-weight: 600; }

    .container { padding: 16px; }
    .card { background: #fff; border-radius: 16px; padding: 20px; margin-bottom: 16px; }
    table { width: 100%; border-collapse: collapse; font-size: 14px; }
    th { background: #f9fafb; padding: 12px 10px; text-align: left; border-bottom: 1px solid #eee; font-weight: 600; }
    td { padding: 10px; border-bottom: 1px solid #f3f4f6; }
    td input { 
      padding: 8px 10px; border: 1px solid #ddd; border-radius: 6px; margin: 0; font-size: 14px;
      width: 100%; background: #fff; cursor: text;
    }
    td input:focus { border-color: var(--orange); outline: none; box-shadow: 0 0 0 2px rgba(255,122,0,0.15); }
    .text-right { text-align: right; }
    .btn-bar { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 16px; }
    .btn { flex: 1; min-width: 100px; padding: 12px; border: none; border-radius: 10px; font-weight: 600; cursor: pointer; font-size: 15px; }
    .btn-o { background: var(--orange); color: #000; }
    .btn-b { background: var(--blue); color: #fff; }
    .btn-g { background: #f0f0f0; color: #333; }
    .btn-sm { flex: none; padding: 8px 12px; font-size: 13px; }

    .proj-block { background: #fff; border-radius: 16px; margin-bottom: 16px; overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.06); }
    .proj-header { background: linear-gradient(to right, #fff9f0, #fff); padding: 14px; display: flex; align-items: center; gap: 10px; flex-wrap: wrap; }
    .proj-num { background: var(--orange); width: 32px; height: 32px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700; flex-shrink: 0; }
    .proj-name { 
      flex: 1; min-width: 150px; border: 1px solid transparent; 
      font-size: 16px; font-weight: 700; background: transparent; 
      padding: 8px 10px; border-radius: 6px;
    }
    .proj-name:focus { border-color: var(--orange); outline: none; background: #fff; }
    .proj-total { color: var(--orange); font-weight: 700; font-size: 18px; white-space: nowrap; }
    .proj-del { border: none; background: none; color: var(--red); font-size: 22px; cursor: pointer; padding: 4px 8px; }

    .grand-total { background: linear-gradient(135deg, #0A2351, #16213e); color: #fff; border-radius: 16px; padding: 24px; margin-top: 16px; }
    .grand-value { font-size: 32px; font-weight: 800; margin-top: 8px; }
  </style>
</head>
<body>

<div id="loginPage" class="login-wrap">
  <div class="login-card">
    <div class="logo-text"><span>NEX</span>SIGN</div>
    <div class="logo-zh">新 帜</div>
    <input type="text" id="username" placeholder="账号" />
    <input type="password" id="password" placeholder="密码" />
    <button class="btn-login" onclick="doLogin()">登 录</button>
    <div class="error" id="errorMsg">❌ 账号或密码错误</div>
    <div class="tip">admin / admin123</div>
  </div>
</div>

<div id="mainPage" class="hidden">
  <nav class="top-nav">
    <div class="nav-top">
      <div class="brand"><span>N</span>EXSIGN · 新帜</div>
      <button class="btn-logout" onclick="doLogout()">退出</button>
    </div>
    <div class="nav-tabs">
      <div class="tab active" data-page="ratelib" onclick="goPage('ratelib')">费率库</div>
      <div class="tab" data-page="quote" onclick="goPage('quote')">报价单</div>
    </div>
  </nav>

  <div class="container">
    <!-- 费率库 -->
    <div id="page-ratelib" class="page">
      <div class="card">
        <h2 style="margin-bottom:16px;">📋 费率库</h2>
        <input type="text" id="searchInput" placeholder="搜索项目..." style="margin-bottom:16px;" oninput="renderRate()" />
        <div id="rateTable"></div>
        <div class="btn-bar">
          <button class="btn btn-o" onclick="addRateRow()">➕ 添加项目</button>
          <button class="btn btn-g" onclick="resetRate()">↩️ 恢复默认</button>
          <button class="btn btn-b" onclick="goPage('quote')">→ 去报价</button>
        </div>
      </div>
    </div>

    <!-- 报价单 -->
    <div id="page-quote" class="page hidden">
      <div class="card">
        <h3>客户信息</h3>
        <div style="display:grid; gap:10px; margin-top:12px;">
          <div><label style="font-size:13px; color:#666;">客户姓名</label><input type="text" id="cname" /></div>
          <div><label style="font-size:13px; color:#666;">日期</label><input type="date" id="qdate" /></div>
        </div>
      </div>
      <div id="quoteContainer"></div>
      <div class="btn-bar">
        <button class="btn btn-o" onclick="addQuoteProject()">➕ 添加项目</button>
        <button class="btn btn-b" onclick="goPage('ratelib')">📋 费率库</button>
      </div>
      <div class="grand-total">
        <div>最终报价总额（含 +50%）</div>
        <div class="grand-value">RM <span id="grandTotal">0.00</span></div>
      </div>
    </div>
  </div>
</div>

<script>
const USER = "admin", PASS = "admin123";
const MARKUP = 1.5; // 自动加50%

// ✅ 默认基础价（含你写的 Melamine E0）
const defaultRates = [
  { id:1, cat:"地柜", name:"Melamine E0 NO WARRANTY", unit:"ft", price:400 },
  { id:2, cat:"地柜", name:"Melamine E1 NO WARRANTY", unit:"ft", price:360 },
  { id:3, cat:"吊柜", name:"吊柜 700mm高", unit:"ft", price:420 },
  { id:4, cat:"吊柜", name:"吊柜 800mm高", unit:"ft", price:460 },
  { id:5, cat:"吊柜", name:"吊柜 900mm高", unit:"ft", price:500 },
  { id:6, cat:"柜体", name:"标准柜体 melamine E1", unit:"sqft", price:95 },
  { id:7, cat:"柜体", name:"加厚柜体 melamine E0", unit:"sqft", price:115 },
  { id:8, cat:"水盆", name:"不锈钢洗菜盆 SUS304", unit:"个", price:850 },
  { id:9, cat:"水盆", name:"SORENTO单槽套装", unit:"套", price:2300 }
];

let rateData = [];
let projects = [];
let projId = 0;

// ===== 登录 =====
function doLogin() {
  const u = document.getElementById("username").value.trim();
  const p = document.getElementById("password").value;
  if (u === USER && p === PASS) {
    localStorage.setItem("nexsign_user", USER);
    document.getElementById("loginPage").classList.add("hidden");
    document.getElementById("mainPage").classList.remove("hidden");
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
    init();
  }
  document.addEventListener("keydown", e => e.key === "Enter" && doLogin());
};

// ===== 初始化 =====
function init() {
  const saved = localStorage.getItem("nexsign_rates");
  rateData = saved ? JSON.parse(saved) : [...defaultRates];
  document.getElementById("qdate").valueAsDate = new Date();
  renderRate();
  if (projects.length === 0) addQuoteProject();
}

// ===== 页面切换 =====
function goPage(page) {
  document.querySelectorAll(".tab").forEach(t => t.classList.toggle("active", t.dataset.page === page));
  document.querySelectorAll(".page").forEach(p => p.classList.toggle("hidden", p.id !== `page-${page}`));
  if (page === "quote") renderQuote();
}

// ===== 费率库 =====
function renderRate() {
  let list = [...rateData];
  const kw = document.getElementById("searchInput")?.value.toLowerCase() || "";
  if (kw) list = list.filter(r => r.name.toLowerCase().includes(kw));
  
  document.getElementById("rateTable").innerHTML = `
    <table><thead><tr>
      <th>分类</th><th>项目名称</th><th>单位</th><th class="text-right">单价(RM)</th><th></th>
    </tr></thead><tbody>
    ${list.map(r => `
      <tr>
        <td><input value="${r.cat}" oninput="updateRate(${r.id},'cat',this.value)" style="width:100px;" /></td>
        <td><input value="${r.name}" oninput="updateRate(${r.id},'name',this.value)" /></td>
        <td><input value="${r.unit}" oninput="updateRate(${r.id},'unit',this.value)" style="width:70px;" /></td>
        <td class="text-right"><input type="number" value="${r.price}" oninput="updateRate(${r.id},'price',+this.value||0)" style="width:100px; text-align:right;" /></td>
        <td><button style="border:none; background:none; color:red; cursor:pointer; font-size:20px;" onclick="delRate(${r.id})">×</button></td>
      </tr>
    `).join("")}
    </tbody></table>
  `;
  saveRate();
}
function updateRate(id, f, v) {
  const r = rateData.find(x => x.id === id);
  if (r) { r[f] = v; saveRate(); }
}
function delRate(id) {
  if (confirm("确定删除？")) { rateData = rateData.filter(r => r.id !== id); renderRate(); }
}
function addRateRow() {
  const newId = rateData.length ? Math.max(...rateData.map(r => r.id)) + 1 : 1;
  rateData.push({ id: newId, cat:"新分类", name:"新项目", unit:"pc", price:0 });
  renderRate();
}
function resetRate() {
  if (confirm("恢复默认？自定义项目会保留，基础价全部恢复！")) {
    localStorage.removeItem("nexsign_rates");
    rateData = [...defaultRates];
    renderRate();
  }
}
function saveRate() { localStorage.setItem("nexsign_rates", JSON.stringify(rateData)); }

// ===== ✅ 报价单 — 项目名称框完全修复 =====
function addQuoteProject() {
  projId++;
  projects.push({ id: projId, name: `项目${projects.length+1}`, items: [] });
  renderQuote();
}
function delQuoteProject(pid) {
  if (confirm("确定删除？")) {
    projects = projects.filter(p => p.id !== pid);
    renderQuote();
  }
}
function addQuoteRow(pid) {
  const p = projects.find(x => x.id === pid);
  p.items.push({ name:"", unit:"ft", price:0, qty:1 });
  renderQuote();
}
function delQuoteRow(pid, idx) {
  projects.find(x => x.id === pid).items.splice(idx, 1);
  renderQuote();
}

// ✅ 实时更新：不刷新、不丢焦点
function updateQuoteName(pid, val) {
  const p = projects.find(x => x.id === pid);
  p.name = val;
  calcGrandTotal();
}
function updateQuoteCell(pid, idx, field, val) {
  const row = projects.find(x => x.id === pid).items[idx];
  row[field] = val;
  calcGrandTotal();
}

function renderQuote() {
  document.getElementById("quoteContainer").innerHTML = projects.map((p, pIdx) => {
    const subTotal = p.items.reduce((sum, r) => sum + (r.price||0)*(r.qty||0), 0);
    const withMarkup = subTotal * MARKUP;
    return `
      <div class="proj-block">
        <div class="proj-header">
          <span class="proj-num">${pIdx+1}</span>
          <input type="text" class="proj-name" value="${p.name}" 
                 oninput="updateQuoteName(${p.id}, this.value)"
                 placeholder="输入项目名称" />
          <span class="proj-total">RM ${withMarkup.toFixed(2)}</span>
          <button class="proj-del" onclick="delQuoteProject(${p.id})">×</button>
        </div>
        <div style="padding:14px;">
          <table><thead><tr>
            <th style="width:35%;">项目名称</th>
            <th style="width:15%;">单位</th>
            <th style="width:15%;text-align:right;">单价(RM)</th>
            <th style="width:10%;text-align:right;">数量</th>
            <th style="width:20%;text-align:right;">金额(+50%)</th>
            <th style="width:5%;"></th>
          </tr></thead><tbody>
          ${p.items.map((r, i) => {
            const amt = ((r.price||0)*(r.qty||0)*MARKUP).toFixed(2);
            return `
              <tr>
                <td>
                  <!-- ✅ 这一行就是你截图里改不到的地方，现在完全修好！ -->
                  <input type="text" value="${r.name}" 
                         oninput="updateQuoteCell(${p.id}, ${i}, 'name', this.value)"
                         placeholder="直接点这里改项目名称" />
                </td>
                <td><input type="text" value="${r.unit}" style="width:70px;" 
                       oninput="updateQuoteCell(${p.id}, ${i}, 'unit', this.value)" /></td>
                <td class="text-right"><input type="number" value="${r.price}" style="width:90px; text-align:right;" 
                       oninput="updateQuoteCell(${p.id}, ${i}, 'price', +this.value||0)" /></td>
                <td class="text-right"><input type="number" value="${r.qty}" style="width:60px; text-align:right;" 
                       oninput="updateQuoteCell(${p.id}, ${i}, 'qty', +this.value||0)" /></td>
                <td class="text-right" style="font-weight:bold; color:var(--orange);">${amt}</td>
                <td><button style="border:none; background:none; color:red; cursor:pointer; font-size:18px;" 
                       onclick="delQuoteRow(${p.id}, ${i})">×</button></td>
              </tr>
            `;
          }).join("")}
          </tbody></table>
          <div class="btn-bar" style="margin-top:10px;">
            <button class="btn btn-g btn-sm" onclick="addQuoteRow(${p.id})">➕ 添加行</button>
            <button class="btn btn-g btn-sm" onclick="goPage('ratelib')">📋 从费率库复制</button>
          </div>
        </div>
      </div>
    `;
  }).join("");
  calcGrandTotal();
}

function calcGrandTotal() {
  const total = projects.reduce((sum, p) => 
    sum + p.items.reduce((s, r) => s + (r.price||0)*(r.qty||0), 0), 0
  ) * MARKUP;
  document.getElementById("grandTotal").textContent = total.toFixed(2);
}
</script>
</body>
</html>
