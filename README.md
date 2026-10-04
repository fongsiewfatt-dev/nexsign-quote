<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
  <!-- 📱 手机APP全屏模式 -->
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-title" content="NEXSIGN" />
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
  <meta name="theme-color" content="#FF7A00" />
  <title>NEXSIGN — 全屋报价系统</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: system-ui, -apple-system, sans-serif; }
    :root { --blue: #0A2351; --orange: #FF7A00; --red: #E6212A; --green: #22c55e; --bg: #f7f8fa; }
    .hidden { display: none !important; }

    .login-wrap {
      min-height: 100vh; display: flex; align-items: center; justify-content: center;
      background: linear-gradient(135deg, #0A2351 0%, #16213e 100%); padding: 20px;
    }
    .login-card {
      background: #fff; border-radius: 20px; padding: 36px 24px; width: 100%; max-width: 420px;
    }
    .logo-text { font-size: 32px; font-weight: 800; color: var(--blue); text-align: center; }
    .logo-text span { color: var(--orange); }
    .logo-zh { font-size: 22px; font-weight: 700; color: var(--red); text-align: center; margin: 6px 0 24px; }
    input { width: 100%; padding: 12px 14px; margin-bottom: 10px; border: 1px solid #e2e2e2; border-radius: 10px; font-size: 15px; }
    input:focus { outline: none; border-color: var(--orange); box-shadow: 0 0 0 3px rgba(255,122,0,0.15); }
    .btn-login { width: 100%; padding: 14px; background: var(--orange); border: none; border-radius: 12px; font-size: 17px; font-weight: 700; cursor: pointer; margin-top: 8px; }
    .error { color: var(--red); text-align: center; margin-top: 12px; display: none; }
    .error.show { display: block; }
    .tip { text-align: center; margin-top: 16px; font-size: 13px; color: #999; }

    .top-nav { background: #fff; border-bottom: 1px solid #eee; padding: 12px 16px; position: sticky; top: 0; z-index: 100; }
    .nav-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
    .brand { font-weight: 700; font-size: 16px; color: var(--blue); }
    .brand span { color: var(--orange); }
    .btn-logout { border: none; background: #f5f5f5; padding: 8px 12px; border-radius: 8px; cursor: pointer; }
    .nav-tabs { display: flex; gap: 6px; overflow-x: auto; }
    .tab { padding: 10px 14px; border-radius: 10px; background: #f5f5f5; cursor: pointer; white-space: nowrap; }
    .tab.active { background: var(--orange); font-weight: 600; }

    .container { padding: 16px; }
    .card { background: #fff; border-radius: 16px; padding: 20px; margin-bottom: 16px; }
    .search-input { width: 100%; padding: 12px; border: 1px solid #e5e7eb; border-radius: 10px; margin-bottom: 16px; }
    .cat-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(80px, 1fr)); gap: 10px; margin-bottom: 20px; }
    .cat-item { padding: 10px; text-align: center; background: #f9fafb; border-radius: 10px; cursor: pointer; border: 2px solid transparent; }
    .cat-item.active { background: #fff9f0; border-color: var(--orange); }
    table { width: 100%; border-collapse: collapse; font-size: 13px; }
    th { background: #f9fafb; padding: 10px; text-align: left; border-bottom: 1px solid #eee; }
    td { padding: 8px; border-bottom: 1px solid #f3f4f6; }
    td input { padding: 6px; border: 1px solid #ddd; border-radius: 4px; margin: 0; }
    .text-right { text-align: right; }
    .btn-bar { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 16px; }
    .btn { flex: 1; min-width: 100px; padding: 12px; border: none; border-radius: 10px; font-weight: 600; cursor: pointer; }
    .btn-o { background: var(--orange); color: #000; }
    .btn-b { background: var(--blue); color: #fff; }
    .btn-g { background: #f0f0f0; color: #333; }
    
    /* ✅ 修复：项目名称输入框样式 */
    .proj-block { background: #fff; border-radius: 16px; margin-bottom: 16px; overflow: hidden; }
    .proj-header { 
      background: linear-gradient(to right, #fff9f0, #fff); padding: 14px; 
      display: flex; align-items: center; gap: 10px; flex-wrap: wrap; 
    }
    .proj-num { 
      background: var(--orange); width: 32px; height: 32px; border-radius: 50%; 
      display: flex; align-items: center; justify-content: center; font-weight: 700; flex-shrink: 0; 
    }
    .proj-name { 
      flex: 1; min-width: 150px; border: 1px solid transparent; 
      font-size: 16px; font-weight: 700; background: transparent; padding: 6px 8px; border-radius: 6px;
      transition: border 0.2s;
    }
    .proj-name:focus { border-color: var(--orange); outline: none; background: #fff; }
    .proj-total { color: var(--orange); font-weight: 700; font-size: 18px; white-space: nowrap; }
    .proj-del { border: none; background: none; color: var(--red); font-size: 20px; cursor: pointer; padding: 4px 8px; }
    
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
    <div id="page-ratelib" class="page">
      <div class="card">
        <h2 style="margin-bottom:16px;">📋 费率库（含柜体基础价）</h2>
        <input type="text" class="search-input" id="searchInput" placeholder="搜索项目..." oninput="renderItems()" />
        <div class="cat-grid" id="catGrid"></div>
        <table>
          <thead><tr>
            <th>分类</th><th>编号</th><th>项目名称</th><th>单位</th><th class="text-right">单价(RM)</th><th>说明</th><th></th>
          </tr></thead>
          <tbody id="itemBody"></tbody>
        </table>
        <div class="btn-bar">
          <button class="btn btn-o" onclick="addItem()">➕ 添加项目</button>
          <button class="btn btn-g" onclick="resetLib()">↩️ 恢复默认</button>
          <button class="btn btn-b" onclick="goPage('quote')">→ 报价</button>
        </div>
      </div>
    </div>

    <div id="page-quote" class="page hidden">
      <div class="card">
        <h3>客户信息</h3>
        <div style="display:grid; gap:10px; margin-top:12px;">
          <div><label>姓名</label><input type="text" id="cname" /></div>
          <div><label>日期</label><input type="date" id="qdate" /></div>
        </div>
      </div>
      <div id="projContainer"></div>
      <div class="btn-bar">
        <button class="btn btn-o" onclick="addProj()">➕ 添加项目</button>
        <button class="btn btn-b" onclick="goPage('ratelib')">📋 费率库</button>
      </div>
      <div class="grand-total">
        <div>最终报价总额（含+50%）</div>
        <div class="grand-value">RM <span id="finalTotal">0.00</span></div>
      </div>
    </div>
  </div>
</div>

<script>
const USER = "admin", PASS = "admin123";
const MARKUP = 1.5; // 自动+50%

const categories = [
  {id:"all",name:"全部"},
  {id:"cabinet",name:"柜体"},
  {id:"base",name:"地柜"},
  {id:"wall",name:"吊柜"},
  {id:"material",name:"材料"},
  {id:"sink",name:"水盆"},
  {id:"other",name:"其他"}
];

// ✅ 完整柜体基础价
const defaultData = [
  {uid:1,cat:"base",code:"B001",name:"Melamine E0 地柜基础",unit:"ft",price:400,desc:"Supply & Install +50%"},
  {uid:2,cat:"base",code:"B002",name:"Melamine E1 地柜基础",unit:"ft",price:360,desc:"Supply & Install +50%"},
  {uid:3,cat:"wall",code:"W001",name:"吊柜 700mm高",unit:"ft",price:420,desc:"Supply & Install +50%"},
  {uid:4,cat:"wall",code:"W002",name:"吊柜 800mm高",unit:"ft",price:460,desc:"Supply & Install +50%"},
  {uid:5,cat:"wall",code:"W003",name:"吊柜 900mm高",unit:"ft",price:500,desc:"Supply & Install +50%"},
  {uid:6,cat:"cabinet",code:"C001",name:"标准柜体 melamine",unit:"sqft",price:95,desc:"E1级 不含保修"},
  {uid:7,cat:"cabinet",code:"C002",name:"加厚柜体 melamine E0",unit:"sqft",price:115,desc:"E0级 不含保修"},
  {uid:8,cat:"sink",code:"S001",name:"不锈钢洗菜盆 SUS304",unit:"个",price:850,desc:"含安装辅材"},
  {uid:9,cat:"sink",code:"S002",name:"SORENTO单槽套装",unit:"套",price:2300,desc:"含龙头安装"}
];

let items = [], activeCat = "all", projects = [], pidCounter = 0;

// ===== 登录 =====
function doLogin() {
  const u = document.getElementById("username").value.trim();
  const p = document.getElementById("password").value;
  if(u === USER && p === PASS) {
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
  if(localStorage.getItem("nexsign_user") === USER) {
    document.getElementById("loginPage").classList.add("hidden");
    document.getElementById("mainPage").classList.remove("hidden");
    init();
  }
  document.addEventListener("keydown", e => e.key === "Enter" && doLogin());
};

// ===== 初始化 =====
function init() {
  const saved = localStorage.getItem("nexsign_items");
  items = saved ? JSON.parse(saved) : [...defaultData];
  // 确保每个项目有uid（旧数据修复）
  items = items.map((it, idx) => ({...it, uid: it.uid || idx+1}));
  document.getElementById("qdate").valueAsDate = new Date();
  renderCats();
  renderItems();
  if(projects.length === 0) addProj();
}

// ===== 页面切换 =====
function goPage(pageId) {
  document.querySelectorAll(".tab").forEach(t => t.classList.toggle("active", t.dataset.page === pageId));
  document.querySelectorAll(".page").forEach(x => x.classList.toggle("hidden", x.id !== `page-${pageId}`));
  if(pageId === "ratelib") { renderCats(); renderItems(); }
}

// ===== 费率库 =====
function renderCats() {
  document.getElementById("catGrid").innerHTML = categories.map(c => `
    <div class="cat-item ${activeCat === c.id ? 'active' : ''}" 
         onclick="activeCat='${c.id}'; renderItems();">
      ${c.name}<br><small>${activeCat==='all'?items.length:items.filter(i=>i.cat===c.id).length}</small>
    </div>`).join("");
}

function renderItems() {
  let list = [...items];
  if(activeCat !== "all") list = list.filter(i => i.cat === activeCat);
  const kw = document.getElementById("searchInput")?.value.toLowerCase() || "";
  if(kw) list = list.filter(i => 
    i.name.toLowerCase().includes(kw) || i.code.toLowerCase().includes(kw)
  );
  
  document.getElementById("itemBody").innerHTML = list.map(it => `
    <tr>
      <td>${categories.find(c => c.id === it.cat)?.name || it.cat}</td>
      <td>${it.code}</td>
      <td><input value="${it.name}" onchange="updateItem(${it.uid}, 'name', this.value)" /></td>
      <td><input value="${it.unit}" style="width:70px;" onchange="updateItem(${it.uid}, 'unit', this.value)" /></td>
      <td class="text-right"><input type="number" value="${it.price}" style="width:100px;" onchange="updateItem(${it.uid}, 'price', +this.value)" /></td>
      <td><input value="${it.desc || ''}" onchange="updateItem(${it.uid}, 'desc', this.value)" /></td>
      <td><button style="border:none;background:none;color:red;cursor:pointer;" onclick="deleteItem(${it.uid})">×</button></td>
    </tr>`).join("");
  saveItems();
}

function saveItems() { localStorage.setItem("nexsign_items", JSON.stringify(items)); }
function updateItem(uid, field, val) {
  const x = items.find(i => i.uid === uid);
  if(x) { x[field] = val; saveItems(); calcTotal(); }
}
function deleteItem(uid) {
  if(confirm("确定删除？")) {
    items = items.filter(i => i.uid !== uid);
    saveItems(); renderItems();
  }
}
function addItem() {
  const newUid = items.length ? Math.max(...items.map(i => i.uid)) + 1 : 1;
  items.unshift({uid: newUid, cat: "base", code:`N${newUid}`, name:"新项目", unit:"ft", price:0, desc:""});
  saveItems(); renderItems();
}
function resetLib() {
  if(confirm("恢复默认？自定义项目会保留，基础价全部恢复！")) {
    localStorage.removeItem("nexsign_items");
    items = [...defaultData];
    saveItems(); renderItems();
  }
}

// ===== ✅ 报价单 - 修复项目名称修改 =====
function addProj() {
  pidCounter++;
  projects.push({
    id: pidCounter,
    name: `项目${projects.length + 1}`, // 默认名
    list: []
  });
  renderProjects();
}

function deleteProject(pid) {
  if(confirm("确定删除此项目？")) {
    projects = projects.filter(p => p.id !== pid);
    renderProjects();
  }
}

// ✅ 关键修复：专门处理项目名称更新
function updateProjectName(pid, newName) {
  const proj = projects.find(p => p.id === pid);
  if(proj) {
    proj.name = newName;
    // 不重新render整页，避免输入框失去焦点
    calcTotal();
  }
}

function addRow(pid) {
  const proj = projects.find(p => p.id === pid);
  if(!proj) return;
  proj.list.push({name:"", unit:"ft", price:0, qty:1});
  renderProjects();
}

function updateRow(pid, idx, field, val) {
  const proj = projects.find(p => p.id === pid);
  if(!proj) return;
  proj.list[idx][field] = val;
  calcTotal();
}

function deleteRow(pid, idx) {
  projects.find(p => p.id === pid)?.list.splice(idx, 1);
  renderProjects();
}

function renderProjects() {
  document.getElementById("projContainer").innerHTML = projects.map((proj, pIdx) => {
    const subtotal = proj.list.reduce((s, r) => s + (r.price || 0) * (r.qty || 0), 0);
    const totalWithMarkup = subtotal * MARKUP;
    return `
      <div class="proj-block">
        <div class="proj-header">
          <span class="proj-num">${pIdx + 1}</span>
          <!-- ✅ 修复：oninput 实时保存，不会改不了 -->
          <input type="text" class="proj-name" 
                 value="${proj.name}" 
                 oninput="updateProjectName(${proj.id}, this.value)"
                 placeholder="输入项目名称" />
          <span class="proj-total">RM ${totalWithMarkup.toFixed(2)}</span>
          <button class="proj-del" onclick="deleteProject(${proj.id})">×</button>
        </div>
        <div style="padding:14px;">
          <table style="width:100%;">
            <thead>
              <tr>
                <th style="width:35%;">项目名称</th>
                <th style="width:15%;">单位</th>
                <th style="width:15%;text-align:right;">单价(RM)</th>
                <th style="width:10%;text-align:right;">数量</th>
                <th style="width:20%;text-align:right;">金额(含+50%)</th>
                <th style="width:5%;"></th>
              </tr>
            </thead>
            <tbody>
              ${proj.list.map((row, rIdx) => {
                const amount = ((row.price || 0) * (row.qty || 0) * MARKUP).toFixed(2);
                return `
                  <tr>
                    <td><input value="${row.name}" 
                           oninput="updateRow(${proj.id}, ${rIdx}, 'name', this.value)" /></td>
                    <td><input value="${row.unit}" style="width:60px;" 
                           oninput="updateRow(${proj.id}, ${rIdx}, 'unit', this.value)" /></td>
                    <td class="text-right"><input type="number" value="${row.price}" style="width:80px;" 
                           oninput="updateRow(${proj.id}, ${rIdx}, 'price', +this.value||0)" /></td>
                    <td class="text-right"><input type="number" value="${row.qty}" style="width:60px;" 
                           oninput="updateRow(${proj.id}, ${rIdx}, 'qty', +this.value||0)" /></td>
                    <td class="text-right" style="color:var(--orange);font-weight:bold;">${amount}</td>
                    <td><button style="border:none;background:none;color:red;cursor:pointer;" 
                           onclick="deleteRow(${proj.id}, ${rIdx})">×</button></td>
                  </tr>`;
              }).join("")}
            </tbody>
          </table>
          <div class="btn-bar" style="margin-top:10px;">
            <button class="btn btn-g" style="flex:none;padding:8px 12px;" 
                    onclick="addRow(${proj.id})">➕ 添加行</button>
            <button class="btn btn-g" style="flex:none;padding:8px 12px;" 
                    onclick="goPage('ratelib'); alert('去费率库复制项目名称和单价回来')">📋 从费率库选</button>
          </div>
        </div>
      </div>`;
  }).join("");
  calcTotal();
}

function calcTotal() {
  const grandTotal = projects.reduce((sum, p) => 
    sum + p.list.reduce((s, r) => s + (r.price || 0) * (r.qty || 0), 0), 0
  ) * MARKUP;
  document.getElementById("finalTotal").textContent = grandTotal.toFixed(2);
}
</script>
</body>
</html>
