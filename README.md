<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-title" content="NEXSIGN 新帜" />
  <meta name="theme-color" content="#FF7A00" />
  <title>NEXSIGN 新帜 — 橱柜智能报价系统</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
    :root {
      --blue: #0A2351;
      --orange: #FF7A00;
      --red: #E6212A;
      --green: #22c55e;
      --bg: #f7f8fa;
      --font-family: system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
      --font-size-base: 16px;
    }
    body { 
      font-family: var(--font-family); 
      font-size: var(--font-size-base);
      background: var(--bg); color: #1a1a1a; line-height: 1.5; 
    }

    .login-wrap {
      min-height: 100vh; display: flex; align-items: center; justify-content: center;
      background: linear-gradient(135deg, #0A2351 0%, #16213e 100%); padding: 20px;
    }
    .login-card {
      background: #fff; border-radius: 20px; padding: 36px 24px; width: 100%; max-width: 400px;
      box-shadow: 0 8px 32px rgba(0,0,0,0.15);
    }
    .logo-text { font-size: 32px; font-weight: 800; color: var(--blue); text-align: center; letter-spacing: 1px; }
    .logo-text span { color: var(--orange); }
    .logo-zh { font-size: 22px; font-weight: 700; color: var(--red); text-align: center; margin: 6px 0 8px; }
    .logo-tag { font-size: 12px; color: #888; text-align: center; margin-bottom: 28px; line-height: 1.6; }
    input, select {
      width: 100%; padding: 12px 14px; margin-bottom: 10px;
      border: 1px solid #e2e2e2; border-radius: 10px; font-size: 15px;
      -webkit-appearance: none; transition: border-color 0.2s, box-shadow 0.2s;
    }
    input:focus, select:focus { 
      outline: none; border-color: var(--orange); 
      box-shadow: 0 0 0 3px rgba(255, 122, 0, 0.15);
    }
    .btn-primary {
      width: 100%; padding: 14px; background: var(--orange); color: #000;
      border: none; border-radius: 12px; font-size: 17px; font-weight: 700; cursor: pointer;
      transition: transform 0.2s, box-shadow 0.2s;
    }
    .btn-primary:active { transform: scale(0.98); }
    .tip { margin-top: 16px; font-size: 13px; color: #999; text-align: center; }
    .error { color: var(--red); margin-top: 10px; text-align: center; min-height: 20px; }
    .hidden { display: none !important; }

    .top-nav {
      background: #fff; border-bottom: 1px solid #eee; padding: 12px 16px; position: sticky; top: 0; z-index: 100;
    }
    .nav-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
    .brand { font-weight: 700; font-size: 16px; color: var(--blue); }
    .brand span { color: var(--orange); }
    .btn-logout { border: none; background: #f5f5f5; padding: 8px 12px; border-radius: 8px; cursor: pointer; font-size: 14px; transition: background 0.2s; }
    .btn-logout:hover { background: #e8e8e8; }
    .nav-tabs { display: flex; gap: 6px; overflow-x: auto; padding-bottom: 4px; }
    .tab { padding: 10px 14px; border-radius: 10px; background: #f5f5f5; cursor: pointer; font-size: 14px; white-space: nowrap; transition: all 0.2s; }
    .tab.active { background: var(--orange); font-weight: 600; }
    
    .container { padding: 16px; padding-bottom: 40px; }
    .card { background: #fff; border-radius: 16px; padding: 20px; margin-bottom: 16px; box-shadow: 0 2px 8px rgba(0,0,0,0.04); }
    .title { font-size: 17px; font-weight: 700; margin-bottom: 18px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; }
    .grid { display: grid; gap: 14px; }
    label { display: block; font-size: 14px; color: #666; margin-bottom: 6px; }
    .phone-link { display: inline-block; margin-top: 8px; padding: 8px 14px; background: #fff4e8; color: var(--orange); text-decoration: none; border-radius: 8px; font-weight: 600; }
    .search { width: 100%; padding: 12px 16px; border: 1px solid #e5e5e5; border-radius: 12px; margin-bottom: 16px; font-size: 16px; }
    .table-wrap { overflow-x: auto; -webkit-overflow-scrolling: touch; margin: 0 -4px; }
    table { width: 100%; border-collapse: collapse; font-size: 13px; min-width: 700px; }
    th { background: #f8f9fa; padding: 12px 8px; text-align: left; font-size: 12px; color: #555; border-bottom: 1px solid #eee; white-space: nowrap; }
    td { padding: 10px 8px; border-bottom: 1px solid #f0f0f0; vertical-align: middle; }
    td input { padding: 8px 6px; font-size: 14px; border: 1px solid #ddd; border-radius: 6px; width: 100%; margin: 0; }
    td input[readonly] { background: #f9f9f9; color: #666; border-color: transparent; }
    .text-right { text-align: right; }
    .total { text-align: right; padding: 18px 10px; font-weight: 700; font-size: 17px; }
    .total span { color: var(--orange); font-size: 24px; font-weight: 800; }
    .btn-bar { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 18px; }
    .btn { flex: 1; min-width: 100px; padding: 13px; border: none; border-radius: 10px; font-size: 15px; font-weight: 600; cursor: pointer; text-align: center; transition: all 0.2s; }
    .btn:active { transform: scale(0.97); }
    .btn-o { background: var(--orange); color: #000; }
    .btn-b { background: var(--blue); color: #fff; }
    .btn-g { background: #f0f0f0; color: #333; }
    .btn-sm { flex: none; padding: 9px 14px; font-size: 13px; }
    .btn-use { padding: 8px 14px; background: var(--green); border: none; border-radius: 7px; font-weight: 600; cursor: pointer; font-size: 13px; color: #fff; white-space: nowrap; transition: background 0.2s; }
    .btn-use:hover { background: #28d06a; }
    .btn-del { border: none; background: none; color: var(--red); font-size: 20px; cursor: pointer; padding: 4px 8px; transition: transform 0.2s; }
    .btn-del:hover { transform: scale(1.2); }
    .item-row { transition: background 0.2s; }
    .item-row:hover { background: #fafafa; }

    /* ========== 全新升级：添加新项目区域 ========== */
    .add-box { 
      background: linear-gradient(135deg, #fff9f0 0%, #fff 100%); 
      border: 2px solid var(--orange); 
      border-radius: 16px; 
      padding: 22px 20px; 
      margin-bottom: 24px;
      box-shadow: 0 4px 12px rgba(255, 122, 0, 0.08);
    }
    .add-box__header {
      display: flex; align-items: center; gap: 10px; margin-bottom: 16px;
    }
    .add-box__icon {
      width: 36px; height: 36px; border-radius: 10px; background: var(--orange); color: #fff;
      display: flex; align-items: center; justify-content: center; font-size: 20px; font-weight: bold;
    }
    .add-box__title { font-weight: 700; font-size: 16px; color: var(--blue); }
    .add-box__desc { font-size: 12px; color: #888; margin-top: 2px; }
    .add-box__grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 14px; align-items: flex-end;
    }
    .add-box__field label { font-size: 13px; color: #555; font-weight: 500; }
    .add-box__field input, .add-box__field select { margin-bottom: 0; }
    .add-box__btn-wrap { margin-top: 16px; display: flex; gap: 10px; flex-wrap: wrap; }
    .add-box__hint {
      margin-top: 12px; padding: 10px 14px; background: #f5f5f5; border-radius: 8px; font-size: 12px; color: #666;
      line-height: 1.6;
    }
    .add-box__hint strong { color: var(--orange); }

    .setup-box { background: #fff9f0; border: 2px solid var(--orange); border-radius: 16px; padding: 20px; }
    .setup-row { display: flex; align-items: center; gap: 12px; margin-bottom: 16px; flex-wrap: wrap; }
    .setup-row label { margin-bottom: 0; white-space: nowrap; }
    .copyright { text-align: center; margin-top: 30px; font-size: 12px; color: #aaa; line-height: 1.6; }
    @media print {
      .top-nav, .btn-bar, .login-wrap, .add-box { display: none !important; }
      .page { display: block !important; }
      body { background: #fff; }
    }
  </style>
</head>
<body>
  <!-- 登录页 -->
  <div id="loginPage" class="login-wrap">
    <div class="login-card">
      <div class="logo-text"><span>NEX</span>SIGN</div>
      <div class="logo-zh">新 帜</div>
      <div class="logo-tag">携手新帜，定义未来标杆<br/>完整报价体系 · 可编辑 · 自定义加价</div>
      <input type="text" id="u" placeholder="账号" autocomplete="username" />
      <input type="password" id="p" placeholder="密码" autocomplete="current-password" />
      <button class="btn-primary" onclick="checkLogin()">登录系统</button>
      <div class="error" id="err"></div>
      <div class="tip">账号：admin / 密码：admin123</div>
    </div>
  </div>

  <!-- 主系统 -->
  <div id="mainPage" class="hidden">
    <nav class="top-nav">
      <div class="nav-top">
        <div class="brand"><span>N</span>EXSIGN · 新帜</div>
        <button class="btn-logout" onclick="logout()">退出</button>
      </div>
      <div class="nav-tabs">
        <div class="tab active" data-page="quote">新建报价</div>
        <div class="tab" data-page="stock">材料库 ✏️可改</div>
        <div class="tab" data-page="settings">设置</div>
      </div>
    </nav>

    <div class="container">
      <!-- 报价页 -->
      <div id="page-quote" class="page">
        <div class="card">
          <div class="title">客户信息</div>
          <div class="grid">
            <div>
              <label>客户姓名</label>
              <input type="text" id="cname" placeholder="填写姓名" />
            </div>
            <div>
              <label>联系电话</label>
              <input type="tel" id="cphone" placeholder="012-345 6789" oninput="showTel()" />
              <div id="telLink"></div>
            </div>
            <div>
              <label>日期</label>
              <input type="date" id="qdate" />
            </div>
            <div>
              <label>报价编号</label>
              <input type="text" id="qno" readonly style="background:#f9f9f9;" placeholder="保存后生成" />
            </div>
            <div>
              <label>业务员</label>
              <input type="text" id="sales" readonly style="background:#f9f9f9;" />
            </div>
            <div>
              <label>备注</label>
              <input type="text" id="remark" placeholder="可选填写" />
            </div>
          </div>
        </div>

        <div class="card">
          <div class="title">报价明细 <button class="btn btn-sm btn-g" onclick="clearAll()">清空</button></div>
          <div class="table-wrap">
            <table>
              <thead>
                <tr>
                  <th>#</th>
                  <th>项目名称</th>
                  <th>单位</th>
                  <th class="text-right">单价 (RM)</th>
                  <th class="text-right">数量</th>
                  <th class="text-right">金额 (RM)</th>
                  <th></th>
                </tr>
              </thead>
              <tbody id="list"></tbody>
              <tfoot>
                <tr>
                  <td colspan="5" class="total">报价总额：<span id="total">0.00</span></td>
                </tr>
              </tfoot>
            </table>
          </div>
          <div class="btn-bar">
            <button class="btn btn-sm btn-b" onclick="goPage('stock')">+ 从材料库选择</button>
            <button class="btn btn-sm btn-g" onclick="addRow()">手动添加</button>
          </div>
        </div>

        <div class="btn-bar">
          <button class="btn btn-b" onclick="saveQuote()">保存报价</button>
          <button class="btn btn-o" onclick="window.print()">打印 / 导出PDF</button>
        </div>
      </div>

      <!-- 材料库 — 升级版添加区域 -->
      <div id="page-stock" class="page hidden">
        <div class="card">
          <div class="title">
            完整材料库（直接改 → 自动保存）
            <span style="font-size:12px;color:#888;font-weight:normal;">Supply & Install 为基础价 × 倍率 = 报价</span>
          </div>
          
          <!-- ✨ 全新升级：添加新项目区域 -->
          <div class="add-box">
            <div class="add-box__header">
              <div class="add-box__icon">+</div>
              <div>
                <div class="add-box__title">添加新项目到材料库</div>
                <div class="add-box__desc">自定义项目 · 永久保存 · 随时调用</div>
              </div>
            </div>
            
            <div class="add-box__grid">
              <div class="add-box__field">
                <label>所属分类</label>
                <select id="newCat">
                  <option value="MATERIAL">📋 材质板材</option>
                  <option value="KITCHEN">🍳 厨房</option>
                  <option value="BEDROOM">🛏️ 卧房</option>
                  <option value="DRESSING">💄 梳妆/书房</option>
                  <option value="LIVING">🛋️ 客厅</option>
                  <option value="FOYER">🚪 玄关</option>
                  <option value="ACCESSORY">🔧 配件</option>
                </select>
              </div>
              <div class="add-box__field">
                <label>项目名称</label>
                <input type="text" id="newName" placeholder="如：定制转角柜" />
              </div>
              <div class="add-box__field">
                <label>计量单位</label>
                <input type="text" id="newUnit" placeholder="ft" value="ft" />
              </div>
              <div class="add-box__field">
                <label>基础单价 (RM)</label>
                <input type="number" id="newPrice" placeholder="400" min="1" step="1" />
              </div>
            </div>
            
            <div class="add-box__btn-wrap">
              <button class="btn btn-o" onclick="addStockItem()" style="flex:1;">✅ 添加并保存</button>
              <button class="btn btn-g" onclick="clearNewForm()">🔄 清空重填</button>
            </div>
            
            <div class="add-box__hint">
              💡 <strong>自动计算报价 = 基础价 × 加价倍率</strong>（当前：×<span id="hintRate">1.50</span>）<br/>
              添加后直接点「选用」即可加入报价单；已添加项目可随时改价/改名/删项
            </div>
          </div>

          <input type="text" class="search" id="search" placeholder="🔍 搜索项目名称…" oninput="renderStock()" />
          
          <div class="table-wrap">
            <table>
              <thead>
                <tr>
                  <th>分类</th>
                  <th>项目名称（可改）</th>
                  <th>单位</th>
                  <th class="text-right">基础价 (RM)</th>
                  <th class="text-right">你的报价</th>
                  <th>选用/删除</th>
                </tr>
              </thead>
              <tbody id="stockList"></tbody>
            </table>
          </div>
          
          <div class="btn-bar" style="margin-top:20px;">
            <button class="btn btn-g" onclick="resetStock()">↩️ 恢复原始清单</button>
            <button class="btn btn-b" onclick="goPage('quote')">← 返回报价单</button>
          </div>
        </div>
      </div>

      <!-- 设置页 -->
      <div id="page-settings" class="page hidden">
        <div class="card setup-box">
          <div class="title">⚙️ 系统设置</div>
          
          <div class="setup-row">
            <label style="min-width:120px;">加价比例：</label>
            <input type="number" id="markupPercent" value="50" style="max-width:100px;" />
            <span>% → 倍率：<strong id="rateDisplay">×1.50</strong></span>
          </div>
          <button class="btn btn-o" onclick="saveMarkup()" style="margin-bottom:24px;">💾 保存加价比例</button>

          <div class="setup-row">
            <label style="min-width:120px;">字体样式：</label>
            <select id="fontFamily" onchange="applyFont()">
              <option value="system-ui, -apple-system, BlinkMacSystemFont, sans-serif">默认 (清晰)</option>
              <option value="'Microsoft YaHei', 'Segoe UI', sans-serif">微软雅黑</option>
              <option value="'PingFang SC', 'Hiragino Sans GB', sans-serif">苹方/黑体</option>
              <option value="Georgia, 'Times New Roman', serif">宋体/正式</option>
              <option value="Arial, Helvetica, sans-serif">Arial</option>
            </select>
          </div>
          
          <div class="setup-row">
            <label style="min-width:120px;">字体大小：</label>
            <select id="fontSize" onchange="applyFont()">
              <option value="14px">小 - 14px</option>
              <option value="16px" selected>中 - 16px</option>
              <option value="18px">大 - 18px</option>
              <option value="20px">超大 - 20px</option>
            </select>
          </div>
          <button class="btn btn-o" onclick="saveFont()">💾 保存字体设置</button>
          
          <p style="margin-top:16px;font-size:12px;color:#888;">
            💡 直接改材料库 → 自动保存；加价只影响新项目；报价单单价可直接改
          </p>
        </div>
      </div>

      <div class="copyright">
        © 2026 NEXSIGN 新帜<br/>
        Designer Price List · Supply & Install
      </div>
    </div>
  </div>

  <script>
    // 登录账号
    const accounts = { admin: "admin123" };
    
    // 默认加价比例
    let markupPercent = parseInt(localStorage.getItem("markupPercent")) || 50;
    
    // ========== NEXSIGN 完整报价清单 ==========
    const originalStock = [
      // ===== 材质板材 =====
      { cat: "MATERIAL", name: "Melamine E0 NO WARRANTY", unit: "ft", original: 400 },
      { cat: "MATERIAL", name: "Melamine E1 NO WARRANTY", unit: "ft", original: 350 },
      { cat: "MATERIAL", name: "Melamine E0 WITH WARRANTY", unit: "ft", original: 450 },
      { cat: "MATERIAL", name: "Melamine E1 WITH WARRANTY", unit: "ft", original: 400 },
      { cat: "MATERIAL", name: "Plywood E0", unit: "ft", original: 480 },
      { cat: "MATERIAL", name: "Plywood E1", unit: "ft", original: 420 },
      { cat: "MATERIAL", name: "PVC Foamboard", unit: "ft", original: 380 },
      
      // ===== 厨房 =====
      { cat: "KITCHEN", name: "Base Unit 700mm (Supply & Install)", unit: "ft", original: 400 },
      { cat: "KITCHEN", name: "Base Unit 800mm (Supply & Install)", unit: "ft", original: 420 },
      { cat: "KITCHEN", name: "Base Unit 900mm (Supply & Install)", unit: "ft", original: 450 },
      { cat: "KITCHEN", name: "Base Cabinet Standard 860mmH × 600mmD", unit: "ft", original: 270 },
      { cat: "KITCHEN", name: "Base Island Cabinet 1000mmH × 600mmD", unit: "ft", original: 285 },
      { cat: "KITCHEN", name: "Tall Cabinet / Pantry 8ft", unit: "ft", original: 420 },
      { cat: "KITCHEN", name: "Tall Cabinet / Pantry 9ft", unit: "ft", original: 440 },
      { cat: "KITCHEN", name: "Tall Cabinet / Pantry 10ft", unit: "ft", original: 450 },
      { cat: "KITCHEN", name: "Wall Cabinet 700mmH × 350mmD", unit: "ft", original: 220 },
      { cat: "KITCHEN", name: "Wall Cabinet 800mmH × 350mmD", unit: "ft", original: 230 },
      { cat: "KITCHEN", name: "Wall Cabinet 900mmH × 370mmD", unit: "ft", original: 240 },
      { cat: "KITCHEN", name: "Wall Cabinet 1200mmH × 370mmD", unit: "ft", original: 255 },
      { cat: "KITCHEN", name: "Wall Cabinet 1500mmH × 370mmD", unit: "ft", original: 270 },
      { cat: "KITCHEN", name: "Fridge Enclosure Cabinet", unit: "ft", original: 300 },
      { cat: "KITCHEN", name: "Sink Base Cabinet", unit: "ft", original: 280 },
      { cat: "KITCHEN", name: "Corner Base Cabinet L-Shape", unit: "pcs", original: 550 },
      
      // ===== 卧房 =====
      { cat: "BEDROOM", name: "Swing Door Wardrobe 8ft Height", unit: "ft", original: 450 },
      { cat: "BEDROOM", name: "Swing Door Wardrobe 9ft Height", unit: "ft", original: 480 },
      { cat: "BEDROOM", name: "Swing Door Wardrobe 10ft Height", unit: "ft", original: 525 },
      { cat: "BEDROOM", name: "Sliding Door Wardrobe 8ft Height", unit: "ft", original: 580 },
      { cat: "BEDROOM", name: "Sliding Door Wardrobe 9ft Height", unit: "ft", original: 630 },
      { cat: "BEDROOM", name: "Sliding Door Wardrobe 10ft Height", unit: "ft", original: 675 },
      { cat: "BEDROOM", name: "Full Colour Carcass Upgrade + Swing", unit: "ft", original: 225 },
      { cat: "BEDROOM", name: "Full Colour Carcass Upgrade + Sliding", unit: "ft", original: 225 },
      { cat: "BEDROOM", name: "Tatami Bed Platform 300mmH", unit: "psf", original: 57 },
      { cat: "BEDROOM", name: "Tatami Bed Platform 400mmH", unit: "psf", original: 65 },
      { cat: "BEDROOM", name: "Bedhead Partition / Feature Wall", unit: "psf", original: 33 },
      { cat: "BEDROOM", name: "Under-mount Drawer Wardrobe", unit: "pcs", original: 128 },
      { cat: "BEDROOM", name: "Hanging Side Table w/ Drawer", unit: "pcs", original: 300 },
      { cat: "BEDROOM", name: "Wardrobe Internal Shelf", unit: "ft", original: 45 },
      { cat: "BEDROOM", name: "Wardrobe Hanging Rod", unit: "ft", original: 25 },
      
      // ===== 梳妆台/书房 =====
      { cat: "DRESSING", name: "Dressing Table Top 50mm", unit: "ft", original: 85 },
      { cat: "DRESSING", name: "Dressing Table Cabinet Set", unit: "ft", original: 233 },
      { cat: "DRESSING", name: "Study Desk Top 50mm", unit: "ft", original: 80 },
      { cat: "DRESSING", name: "Study Cabinet / Bookshelf", unit: "ft", original: 380 },
      { cat: "DRESSING", name: "Glass Door Upgrade M4", unit: "psf", original: 68 },
      { cat: "DRESSING", name: "Glass Door Upgrade M4 Meru", unit: "psf", original: 75 },
      { cat: "DRESSING", name: "Mirror Cabinet", unit: "ft", original: 260 },
      
      // ===== 客厅 =====
      { cat: "LIVING", name: "TV Console / TV Ledge", unit: "ft", original: 225 },
      { cat: "LIVING", name: "Display Cabinet 8ft Height", unit: "ft", original: 400 },
      { cat: "LIVING", name: "Display Cabinet 9ft Height", unit: "ft", original: 425 },
      { cat: "LIVING", name: "Display Cabinet 10ft Height", unit: "ft", original: 450 },
      { cat: "LIVING", name: "Display Cabinet Full Colour Carcass", unit: "ft", original: 638 },
      { cat: "LIVING", name: "Hidden Swing Door", unit: "psf", original: 120 },
      { cat: "LIVING", name: "Hidden Sliding Door", unit: "psf", original: 128 },
      { cat: "LIVING", name: "Partition Wall 50mm 2-Side Colour", unit: "psf", original: 48 },
      { cat: "LIVING", name: "Partition Wall 100mm 2-Side Colour", unit: "psf", original: 55 },
      { cat: "LIVING", name: "Partition Wall 1-Side Colour", unit: "psf", original: 33 },
      { cat: "LIVING", name: "Fluted Panel Feature", unit: "psf", original: 41 },
      
      // ===== 玄关 =====
      { cat: "FOYER", name: "Shoe Cabinet 8ft Height", unit: "ft", original: 420 },
      { cat: "FOYER", name: "Shoe Cabinet 9ft Height", unit: "ft", original: 450 },
      { cat: "FOYER", name: "Shoe Cabinet 10ft Height", unit: "ft", original: 480 },
      { cat: "FOYER", name: "Shoe Bench / Sitting Area", unit: "ft", original: 240 },
      { cat: "FOYER", name: "Shoe Cabinet Sliding Door", unit: "ft", original: 520 },
      
      // ===== 配件 =====
      { cat: "ACCESSORY", name: "Floating Shelf 32mm Thick", unit: "ft", original: 60 },
      { cat: "ACCESSORY", name: "Floating Shelf 50mm Thick", unit: "ft", original: 75 },
      { cat: "ACCESSORY", name: "LED COB Strip Light + Driver + Housing", unit: "pcs", original: 150 },
      { cat: "ACCESSORY", name: "Pantry Pull-out Basket", unit: "pcs", original: 180 },
      { cat: "ACCESSORY", name: "Soft Close Hinge Upgrade", unit: "pcs", original: 12 },
      { cat: "ACCESSORY", name: "Door Handle / Pull", unit: "pcs", original: 8 },
      { cat: "ACCESSORY", name: "Aluminium J-Profile / Handle", unit: "ft", original: 12 },
      { cat: "ACCESSORY", name: "Curve End Panel 900mmH", unit: "pcs", original: 525 },
      { cat: "ACCESSORY", name: "Curve End Panel 1500mmH", unit: "pcs", original: 1275 },
      { cat: "ACCESSORY", name: "Curve End Panel 2400mmH", unit: "pcs", original: 2475 },
      { cat: "ACCESSORY", name: "Hood Installation Service", unit: "pcs", original: 225 },
      { cat: "ACCESSORY", name: "Oven / Microwave Installation", unit: "pcs", original: 180 },
      { cat: "ACCESSORY", name: "Dismantle Old Cabinet", unit: "pcs", original: 750 },
      { cat: "ACCESSORY", name: "Site Measurement & Design Fee", unit: "lot", original: 150 },
      { cat: "ACCESSORY", name: "Delivery & Transportation", unit: "lot", original: 200 }
    ];

    // 加载用户修改后的材料库
    let priceList = [];
    function loadStock() {
      const saved = localStorage.getItem("nexsignStock");
      if (saved) {
        priceList = JSON.parse(saved);
      } else {
        priceList = JSON.parse(JSON.stringify(originalStock));
      }
    }
    function saveStock() {
      localStorage.setItem("nexsignStock", JSON.stringify(priceList));
    }
    function resetStock() {
      if (confirm("⚠️ 确定恢复原始清单？你添加的自定义项目会被清空！")) {
        localStorage.removeItem("nexsignStock");
        priceList = JSON.parse(JSON.stringify(originalStock));
        renderStock();
        alert("✅ 已恢复原始清单！");
      }
    }

    let rowId = 0;

    // 获取当前倍率
    function getRate() { return 1 + markupPercent / 100; }
    
    // 更新提示里的倍率
    function updateHintRate() {
      document.getElementById("hintRate").textContent = getRate().toFixed(2);
    }

    // 登录
    function checkLogin() {
      const u = document.getElementById("u").value.trim();
      const p = document.getElementById("p").value;
      if (accounts[u] && accounts[u] === p) {
        localStorage.setItem("user", u);
        loadStock();
        enterMain(u);
      } else {
        document.getElementById("err").textContent = "账号或密码错误";
      }
    }
    function enterMain(name) {
      document.getElementById("loginPage").classList.add("hidden");
      document.getElementById("mainPage").classList.remove("hidden");
      document.getElementById("sales").value = name;
      document.getElementById("qdate").valueAsDate = new Date();
      
      // 加载设置
      document.getElementById("markupPercent").value = markupPercent;
      updateRateDisplay();
      updateHintRate();
      loadFontSettings();
      
      bindTab();
    }
    function logout() {
      localStorage.removeItem("user");
      location.reload();
    }

    // 记住登录
    const savedUser = localStorage.getItem("user");
    if (savedUser) { loadStock(); enterMain(savedUser); }

    // 页面切换
    function bindTab() {
      document.querySelectorAll(".tab").forEach(tab => {
        tab.addEventListener("click", () => {
          const pg = tab.dataset.page;
          document.querySelectorAll(".tab").forEach(t => t.classList.toggle("active", t.dataset.page === pg));
          document.querySelectorAll(".page").forEach(p => p.classList.toggle("hidden", p.id !== `page-${pg}`));
          if (pg === "stock") {
            renderStock();
            updateHintRate();
          }
        });
      });
    }
    function goPage(pg) {
      document.querySelectorAll(".tab").forEach(t => t.classList.toggle("active", t.dataset.page === pg));
      document.querySelectorAll(".page").forEach(p => p.classList.toggle("hidden", p.id !== `page-${pg}`));
      if (pg === "stock") {
        renderStock();
        updateHintRate();
      }
    }

    // 加价设置
    function updateRateDisplay() {
      const rate = getRate();
      document.getElementById("rateDisplay").textContent = "×" + rate.toFixed(2);
    }
    function saveMarkup() {
      const val = parseInt(document.getElementById("markupPercent").value);
      if (val >= 0 && val <= 300) {
        markupPercent = val;
        localStorage.setItem("markupPercent", val);
        updateRateDisplay();
        updateHintRate();
        renderStock();
        alert("✅ 加价已保存：+" + val + "%\n⚠️ 只影响新项目，已添加到报价的可直接改单价");
      } else {
        alert("⚠️ 请输入 0–300 之间的数字");
      }
    }

    // 字体设置
    function applyFont() {
      const font = document.getElementById("fontFamily").value;
      const size = document.getElementById("fontSize").value;
      document.documentElement.style.setProperty("--font-family", font);
      document.documentElement.style.setProperty("--font-size-base", size);
    }
    function saveFont() {
      applyFont();
      localStorage.setItem("fontFamily", document.getElementById("fontFamily").value);
      localStorage.setItem("fontSize", document.getElementById("fontSize").value);
      alert("✅ 字体设置已保存！");
    }
    function loadFontSettings() {
      const savedFont = localStorage.getItem("fontFamily");
      const savedSize = localStorage.getItem("fontSize");
      if (savedFont) { document.getElementById("fontFamily").value = savedFont; applyFont(); }
      if (savedSize) { document.getElementById("fontSize").value = savedSize; applyFont(); }
    }

    // 一键拨号
    function showTel() {
      const num = document.getElementById("cphone").value.replace(/\D/g, "");
      const box = document.getElementById("telLink");
      box.innerHTML = num.length >= 8 ? `<a href="tel:${num}" class="phone-link">📞 点击拨打</a>` : "";
    }

    // 清空新增表单
    function clearNewForm() {
      document.getElementById("newName").value = "";
      document.getElementById("newUnit").value = "ft";
      document.getElementById("newPrice").value = "";
      document.getElementById("newCat").selectedIndex = 0;
    }

    // 添加新项目到材料库
    function addStockItem() {
      const cat = document.getElementById("newCat").value;
      const name = document.getElementById("newName").value.trim();
      const unit = document.getElementById("newUnit").value.trim() || "ft";
      const price = parseFloat(document.getElementById("newPrice").value);
      
      if (!name) { alert("⚠️ 请填写项目名称！"); document.getElementById("newName").focus(); return; }
      if (!price || price <= 0) { alert("⚠️ 请填写正确的基础价！"); document.getElementById("newPrice").focus(); return; }
      
      priceList.push({ cat, name, unit, original: price });
      saveStock();
      
      // 清空表单
      clearNewForm();
      
      renderStock();
      alert("✅ 添加成功！已保存到材料库");
    }

    // 删除材料库项目
    function deleteStockItem(idx) {
      if (confirm("确定删除这个项目？")) {
        priceList.splice(idx, 1);
        saveStock();
        renderStock();
      }
    }

    // 材料库渲染
    function renderStock() {
      let list = priceList;
      const kw = document.getElementById("search")?.value.trim().toLowerCase() || "";
      if (kw) {
        list = priceList.filter(r => r.name.toLowerCase().includes(kw));
      }
      
      let html = "";
      list.forEach((r, displayIdx) => {
        const realIdx = priceList.indexOf(r);
        const quotePrice = (r.original * getRate()).toFixed(2);
        
        html += `
          <tr class="item-row">
            <td>
              <select onchange="updateStockField(${realIdx}, 'cat', this.value)">
                <option value="MATERIAL" ${r.cat==='MATERIAL'?'selected':''}>材质</option>
                <option value="KITCHEN" ${r.cat==='KITCHEN'?'selected':''}>厨房</option>
                <option value="BEDROOM" ${r.cat==='BEDROOM'?'selected':''}>卧房</option>
                <option value="DRESSING" ${r.cat==='DRESSING'?'selected':''}>梳妆</option>
                <option value="LIVING" ${r.cat==='LIVING'?'selected':''}>客厅</option>
                <option value="FOYER" ${r.cat==='FOYER'?'selected':''}>玄关</option>
                <option value="ACCESSORY" ${r.cat==='ACCESSORY'?'selected':''}>配件</option>
              </select>
            </td>
            <td><input type="text" value="${r.name}" onchange="updateStockField(${realIdx}, 'name', this.value)" style="min-width:240px;" /></td>
            <td><input type="text" value="${r.unit}" onchange="updateStockField(${realIdx}, 'unit', this.value)" style="max-width:70px;" /></td>
            <td class="text-right"><input type="number" value="${r.original}" step="1" onchange="updateStockField(${realIdx}, 'original', parseFloat(this.value))" style="max-width:100px;" /></td>
            <td class="text-right" style="font-weight:700;color:var(--orange);">RM ${quotePrice}</td>
            <td style="white-space:nowrap;">
              <button class="btn-use" onclick="pick(${realIdx})">选用</button>
              <button class="btn-del" onclick="deleteStockItem(${realIdx})" style="display:inline-block;margin-left:4px;">🗑️</button>
            </td>
          </tr>
        `;
      });
      document.getElementById("stockList").innerHTML = html;
    }

    // 更新材料库字段并自动保存
    function updateStockField(idx, field, value) {
      if (priceList[idx]) {
        priceList[idx][field] = value;
        saveStock();
        renderStock();
      }
    }

    // 选用项目到报价单
    function pick(i) {
      const r = priceList[i];
      const price = +(r.original * getRate()).toFixed(2);
      addRowData({ name: r.name, unit: r.unit, price: price });
      goPage('quote');
    }

    // 报价行管理
    function addRowData(d) {
      rowId++;
      const tr = document.createElement("tr");
      tr.id = `r${rowId}`;
      tr.innerHTML = `
        <td>${rowId}</td>
        <td><input type="text" value="${d?.name||''}" readonly /></td>
        <td><input type="text" value="${d?.unit||'ft'}" readonly /></td>
        <td class="text-right"><input type="number" value="${d?.price||0}" oninput="calc()" step="0.01" /></td>
        <td class="text-right"><input type="number" value="1" oninput="calc()" step="0.01" /></td>
        <td class="text-right" style="font-weight:700;color:var(--orange);">0.00</td>
        <td><button class="btn-del" onclick="del(${rowId})">×</button></td>
      `;
      document.getElementById("list").appendChild(tr);
      calc();
    }
    function addRow() { addRowData(null); }
    function del(id) { document.getElementById(`r${id}`)?.remove(); reNum(); calc(); }
    function reNum() { document.querySelectorAll("#list tr").forEach((r,i)=>r.querySelector("td:first-child").textContent=i+1); }
    function clearAll() { if(confirm("确定清空所有项目？")){document.getElementById("list").innerHTML="";rowId=0;} }

    // 自动计算
    function calc() {
      let sum = 0;
      document.querySelectorAll("#list tr").forEach(row => {
        const p = parseFloat(row.querySelector("td:nth-child(4) input").value) || 0;
        const q = parseFloat(row.querySelector("td:nth-child(5) input").value) || 0;
        const amt = p * q;
        row.querySelector("td:nth-child(6)").textContent = amt.toFixed(2);
        sum += amt;
      });
      document.getElementById("total").textContent = sum.toFixed(2);
    }

    // 保存报价
    function saveQuote() {
      const no = "NX-" + new Date().toISOString().slice(0,10).replace(/-/g,"") + "-" + Math.floor(Math.random()*900+100);
      document.getElementById("qno").value = no;
      alert("✅ 保存成功！编号：" + no);
    }
  </script>
</body>
</html>
