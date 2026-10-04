<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
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
    .proj-block { background: #fff; border-radius: 16px; margin-bottom: 16px; overflow: hidden; }
    .proj-header { background: linear-gradient(to right, #fff9f0, #fff); padding: 14px; display: flex; align-items: center; gap: 10px; }
    .proj-num { background: var(--orange); width: 32px; height: 32px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700; }
    .proj-name { flex: 1; border: none; font-size: 16px; font-weight: 700; background: transparent; }
    .proj-total { color: var(--orange); font-weight: 700; font-size: 18px; }
    .proj-del { border: none; background: none; color: var(--red); font-size: 20px; cursor: pointer; }
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
        <div>最终报价总额</div>
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

// ✅ 已包含你说的柜体基础价
const defaultData = [
  // 柜体基础
  {cat:"base",code:"B001",name:"Melamine E0 地柜基础",unit:"ft",price:400,desc:"Supply & Install +50%"},
  {cat:"base",code:"B002",name:"Melamine E1 地柜基础",unit:"ft",price:360,desc:"Supply & Install +50%"},
  {cat:"wall",code:"W001",name:"吊柜 700mm高",unit:"ft",price:420,desc:"Supply & Install +50%"},
  {cat:"wall",code:"W002",name:"吊柜 800mm高",unit:"ft",price:460,desc:"Supply & Install +50%"},
  {cat:"wall",code:"W003",name:"吊柜 900mm高",unit:"ft",price:500,desc:"Supply & Install +50%"},
  {cat:"cabinet",code:"C001",name:"标准柜体 melamine",unit:"sqft",price:95,desc:"E1级 不含保修"},
  {cat:"cabinet",code:"C002",name:"加厚柜体 melamine E0",unit:"sqft",price:115,desc:"E0级 不含保修"},
  // 水盆
  {cat:"sink",code:"S001",name:"不锈钢洗菜盆 SUS304",unit:"个",price:850,desc:"含安装辅材"},
  {cat:"sink",code:"S002",name:"SORENTO单槽套装",unit:"套",price:2300,desc:"含龙头安装"}
];

let items = [], activeCat = "all", projects = [], pid = 0;

function doLogin() {
  if(document.getElementById("username").value.trim()===USER && document.getElementById("password").value===PASS) {
    localStorage.setItem("nexsign_user",USER);
    document.getElementById("loginPage").classList.add("hidden");
    document.getElementById("mainPage").classList.remove("hidden");
    init();
  } else { document.getElementById("errorMsg").classList.add("show"); }
}
function doLogout() { localStorage.removeItem("nexsign_user"); location.reload(); }
window.onload = ()=>{ if(localStorage.getItem("nexsign_user")===USER) {document.getElementById("loginPage").classList.add("hidden");document.getElementById("mainPage").classList.remove("hidden");init();} };

function init() {
  const saved = localStorage.getItem("nexsign_items");
  items = saved ? JSON.parse(saved) : [...defaultData];
  document.getElementById("qdate").valueAsDate = new Date();
  renderCats(); renderItems(); addProj();
}

function goPage(p) {
  document.querySelectorAll(".tab").forEach(t=>t.classList.toggle("active",t.dataset.page===p));
  document.querySelectorAll(".page").forEach(x=>x.classList.toggle("hidden",x.id!==`page-${p}`));
  if(p==="ratelib") {renderCats(); renderItems();}
}

function renderCats() {
  document.getElementById("catGrid").innerHTML = categories.map(c=>`
    <div class="cat-item ${activeCat===c.id?'active':''}" onclick="activeCat='${c.id}';renderItems();">
      ${c.name}<br><small>${activeCat==='all'?items.length:items.filter(i=>i.cat===c.id).length}</small>
    </div>`).join("");
}

function renderItems() {
  let list = [...items];
  if(activeCat!=="all") list = list.filter(i=>i.cat===activeCat);
  const kw = document.getElementById("searchInput")?.value.toLowerCase()||"";
  if(kw) list = list.filter(i=>i.name.toLowerCase().includes(kw)||i.code.toLowerCase().includes(kw));
  
  document.getElementById("itemBody").innerHTML = list.map(it=>`
    <tr>
      <td>${categories.find(c=>c.id===it.cat)?.name||it.cat}</td>
      <td>${it.code}</td>
      <td><input value="${it.name}" onchange="upd(${it.uid},'name',this.value)" /></td>
      <td><input value="${it.unit}" style="width:70px;" onchange="upd(${it.uid},'unit',this.value)" /></td>
      <td class="text-right"><input type="number" value="${it.price}" style="width:100px;" onchange="upd(${it.uid},'price',+this.value)" /></td>
      <td><input value="${it.desc||''}" onchange="upd(${it.uid},'desc',this.value)" /></td>
      <td><button style="border:none;background:none;color:red;" onclick="del(${it.uid})">×</button></td>
    </tr>`).join("");
  save();
}

function save() { localStorage.setItem("nexsign_items",JSON.stringify(items)); }
function upd(uid,f,v) { const x=items.find(i=>i.uid===uid); if(x){x[f]=v;save();calc();} }
function del(uid) { if(confirm("确定删除？")){items=items.filter(i=>i.uid!==uid);save();renderItems();} }
function addItem() {
  const nid=items.length?Math.max(...items.map(i=>i.uid))+1:1;
  items.unshift({uid:nid,cat:"base",code:`N${nid}`,name:"新项目",unit:"ft",price:0,desc:""});
  save();renderItems();
}
function resetLib() {
  if(confirm("恢复默认？自定义项目会保留，基础价全部恢复！")) {
    localStorage.removeItem("nexsign_items");
    items = [...defaultData];
    save();renderItems();
  }
}

function addProj() {
  pid++; projects.push({id:pid,name:`项目${projects.length+1}`,list:[]}); renderProj();
}
function delProj(id) { if(confirm("确定？")){projects=projects.filter(p=>p.id!==id);renderProj();} }
function addRow(pid) { const p=projects.find(x=>x.id===pid);p.list.push({name:"",unit:"ft",price:0,qty:1});renderProj(); }
function updRow(pid,idx,f,v) { const p=projects.find(x=>x.id===pid);p.list[idx][f]=v;renderProj(); }
function delRow(pid,idx) { projects.find(x=>x.id===pid).list.splice(idx,1);renderProj(); }

function renderProj() {
  document.getElementById("projContainer").innerHTML = projects.map((p,pi)=>{
    const sub = p.list.reduce((s,r)=>s+(r.price||0)*(r.qty||0),0);
    return `<div class="proj-block">
      <div class="proj-header">
        <span class="proj-num">${pi+1}</span>
        <input class="proj-name" value="${p.name}" onchange="p.name=this.value" />
        <span class="proj-total">RM ${(sub*MARKUP).toFixed(2)}</span>
        <button class="proj-del" onclick="delProj(${p.id})">×</button>
      </div>
      <div style="padding:14px;">
        <table><thead><tr>
          <th>项目</th><th>单位</th><th class="text-right">单价</th><th class="text-right">数量</th><th class="text-right">金额(含+50%)</th><th></th>
        </tr></thead><tbody>
        ${p.list.map((r,i)=>{
          const amt = ((r.price||0)*(r.qty||0)*MARKUP).toFixed(2);
          return `<tr>
            <td><input value="${r.name}" onchange="updRow(${p.id},${i},'name',this.value)" /></td>
            <td><input value="${r.unit}" style="width:60px;" onchange="updRow(${p.id},${i},'unit',this.value)" /></td>
            <td class="text-right"><input type="number" value="${r.price}" style="width:80px;" oninput="updRow(${p.id},${i},'price',+this.value||0)" /></td>
            <td class="text-right"><input type="number" value="${r.qty}" style="width:60px;" oninput="updRow(${p.id},${i},'qty',+this.value||0)" /></td>
            <td class="text-right" style="color:var(--orange);font-weight:bold;">${amt}</td>
            <td><button style="border:none;background:none;color:red;" onclick="delRow(${p.id},${i})">×</button></td>
          </tr>`;
        }).join("")}
        </tbody></table>
        <div class="btn-bar" style="margin-top:10px;">
          <button class="btn btn-g" style="flex:none;padding:8px 12px;" onclick="addRow(${p.id})">➕ 加行</button>
          <button class="btn btn-g" style="flex:none;padding:8px 12px;" onclick="goPage('ratelib')">📋 从费率库复制</button>
        </div>
      </div>
    </div>`;
  }).join("");
  calc();
}

function calc() {
  const total = projects.reduce((sum,p)=>sum+p.list.reduce((s,r)=>s+(r.price||0)*(r.qty||0),0),0)*MARKUP;
  document.getElementById("finalTotal").textContent = total.toFixed(2);
}
</script>
</body>
</html>
