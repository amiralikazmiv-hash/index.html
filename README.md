
# index.html
<!doctype html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>فروشگاه آنلاین</title>
  <style>
    :root{
      --bg:#f5f5f5;
      --card:#ffffff;
      --text:#111;
      --muted:#666;
      --border:#e6e6e6;
      --shadow:0 10px 30px rgba(0,0,0,.06);
      --radius:18px;
      --red:#ef4056; /* نزدیک به دیجی‌کالا */
    }
    *{box-sizing:border-box}
    body{margin:0;font-family:Tahoma, Arial;background:var(--bg);color:var(--text)}
    a{color:inherit;text-decoration:none}
    .container{max-width:1200px;margin:0 auto;padding:12px}

    /* Header */
    .header{
      position:sticky; top:0; z-index:10;
      background:#fff; border-bottom:1px solid var(--border);
    }
    .headerRow{
      display:flex; gap:10px; align-items:center; justify-content:space-between;
      padding:10px 12px;
      max-width:1200px; margin:0 auto;
    }
    .brand{
      display:flex; align-items:center; gap:10px;
      font-weight:900; letter-spacing:-.5px;
    }
    .logo{
      width:36px;height:36px;border-radius:12px;
      background:var(--red);
      display:grid; place-items:center;
      color:#fff; font-weight:900;
    }
    .searchWrap{flex:1; display:flex; gap:10px; align-items:center}
    .search{
      width:100%;
      border:1px solid var(--border);
      border-radius:16px;
      padding:12px 14px;
      outline:none;
      background:#fafafa;
      font-family:Tahoma;
    }
    .btn{
      border:0; cursor:pointer;
      border-radius:16px;
      padding:11px 12px;
      font-family:Tahoma;
      font-weight:800;
    }
    .btnRed{background:var(--red); color:#fff}
    .btnWhite{background:#fff; border:1px solid var(--border)}
    .pill{
      background:#f1f1f1; border-radius:999px;
      padding:6px 10px; font-size:12px; color:#222;
    }

    /* Layout */
    .layout{display:grid; grid-template-columns:320px 1fr; gap:12px; margin-top:12px}
    @media(max-width:900px){ .layout{grid-template-columns:1fr} }

    /* Sidebar */
    .card{
      background:var(--card);
      border:1px solid var(--border);
      border-radius:var(--radius);
      box-shadow:var(--shadow);
      padding:14px;
    }
    .sectionTitle{font-weight:900; font-size:15px; margin-bottom:10px}
    .muted{color:var(--muted); font-size:13px}

    .catList{display:flex; flex-wrap:wrap; gap:8px}
    .catBtn{
      border:1px solid var(--border);
      background:#fff;
      padding:8px 10px;
      border-radius:999px;
      cursor:pointer;
      font-size:13px;
      font-family:Tahoma;
    }
    .catBtn.active{
      border-color:var(--red);
      color:var(--red);
      font-weight:900;
    }

    .row{display:flex; gap:10px; align-items:center; justify-content:space-between}
    .input, select, textarea{
      width:100%;
      padding:11px 12px;
      border-radius:16px;
      border:1px solid var(--border);
      outline:none;
      font-family:Tahoma;
      background:#fff;
    }
    textarea{min-height:80px; resize:vertical}

    /* Products */
    .productsTop{display:flex; gap:10px; align-items:center; justify-content:space-between; margin-bottom:10px}
    .grid{display:grid; grid-template-columns:repeat(4,1fr); gap:12px}
    @media(max-width:1100px){ .grid{grid-template-columns:repeat(3,1fr)} }
    @media(max-width:800px){ .grid{grid-template-columns:repeat(2,1fr)} }
    @media(max-width:420px){ .grid{grid-template-columns:1fr} }

    .pCard{
      background:#fff;
      border:1px solid var(--border);
      border-radius:22px;
      box-shadow:var(--shadow);
      overflow:hidden;
      display:flex;
      flex-direction:column;
      min-height:360px;
    }
    .pImg{
      height:170px;
      background:#fafafa;
      border-bottom:1px solid var(--border);
      overflow:hidden;
    }
    .pImg img{width:100%; height:100%; object-fit:cover; display:block}
    .pBody{padding:12px; display:flex; flex-direction:column; gap:8px; flex:1}
    .pName{font-weight:900; font-size:14px; line-height:1.5}
    .pMeta{display:flex; gap:8px; flex-wrap:wrap}
    .pPrice{margin-top:auto; display:flex; justify-content:space-between; align-items:center; gap:10px}
    .price{font-weight:900}
    .tiny{font-size:12px; color:var(--muted)}

    .pActions{display:flex; gap:8px; margin-top:6px}
    .btnFull{width:100%}

    /* Modal */
    .modalBg{
      position:fixed; inset:0;
      background:rgba(0,0,0,.45);
      display:none;
      align-items:center;
      justify-content:center;
      padding:14px;
      z-index:50;
    }
    .modal{
      width:min(920px, 100%);
      background:#fff;
      border-radius:24px;
      overflow:hidden;
      border:1px solid var(--border);
      box-shadow:0 30px 80px rgba(0,0,0,.25);
    }
    .modalGrid{display:grid; grid-template-columns:1fr 1fr}
    @media(max-width:900px){ .modalGrid{grid-template-columns:1fr} }
    .modalImg{height:360px;background:#f7f7f7}
    .modalImg img{width:100%;height:100%;object-fit:cover}
    .modalBody{padding:14px}
    .closeX{
      position:absolute;
      top:14px; left:14px;
      background:#fff;
      border:1px solid var(--border);
      border-radius:999px;
      width:44px;height:44px;
      cursor:pointer;
      font-size:18px;
    }

    /* Cart Drawer */
    .drawerBg{
      position:fixed; inset:0;
      background:rgba(0,0,0,.35);
      display:none;
      z-index:60;
    }
    .drawer{
      position:fixed; top:0; bottom:0;
      right:0;
      width:min(420px, 92vw);
      background:#fff;
      border-left:1px solid var(--border);
      box-shadow:-20px 0 60px rgba(0,0,0,.15);
      transform:translateX(110%);
      transition:.25s;
      z-index:70;
      display:flex;
      flex-direction:column;
    }
    .drawer.open{transform:translateX(0)}
    .drawerHead{
      padding:12px;
      border-bottom:1px solid var(--border);
      display:flex; align-items:center; justify-content:space-between; gap:10px;
    }
    .drawerBody{padding:12px; overflow:auto; flex:1}
    .cartItem{
      border:1px solid var(--border);
      border-radius:18px;
      padding:10px;
      margin-bottom:10px;
      display:flex;
      gap:10px;
      align-items:flex-start;
    }
    .cartThumb{
      width:64px;height:64px;border-radius:14px;
      background:#f3f3f3; overflow:hidden; flex:0 0 auto;
      border:1px solid var(--border);
    }
    .cartThumb img{width:100%;height:100%;object-fit:cover}
    .cartInfo{flex:1}
    .qtyRow{display:flex; gap:8px; align-items:center; margin-top:8px}
    .qtyBtn{
      width:36px;height:36px;border-radius:14px;
      border:1px solid var(--border);
      background:#fff; cursor:pointer;
      font-size:18px;
    }
    .drawerFoot{
      padding:12px;
      border-top:1px solid var(--border);
      background:#fff;
    }
    .totalRow{display:flex; justify-content:space-between; align-items:center; gap:10px}
    .danger{background:#fff; border:1px solid #fca5a5; color:#991b1b}
  </style>
</head>
<body>

  <div class="header">
    <div class="headerRow">
      <div class="brand">
        <div class="logo">DK</div>
        <div>فروشگاه من</div>
      </div>

      <div class="searchWrap">
        <input id="search" class="search" placeholder="جستجو در محصولات..." oninput="render()" />
      </div>

      <button class="btn btnRed" onclick="openCart()">
        سبد خرید <span class="pill" id="cartCount">0</span>
      </button>
    </div>
  </div>

  <div class="container">
    <div class="layout">

      <!-- Sidebar -->
      <div class="card">
        <div class="sectionTitle">دسته‌بندی‌ها</div>
        <div class="catList" id="cats"></div>

        <div style="height:12px"></div>

        <div class="sectionTitle">مرتب‌سازی</div>
        <select id="sort" onchange="render()">
          <option value="popular">پیشنهادی</option>
          <option value="cheap">ارزان‌ترین</option>
          <option value="expensive">گران‌ترین</option>
          <option value="new">جدیدترین</option>
        </select>

        <div style="height:12px"></div>

        <div class="sectionTitle">فیلتر قیمت (تومان)</div>
        <div class="muted">حداکثر قیمت:</div>
        <input class="input" id="maxPrice" type="number" placeholder="مثلاً 500000" oninput="render()" />

        <div style="height:12px"></div>

        <div class="sectionTitle">سفارش</div>
        <div class="muted">برای ثبت سفارش، سبد خرید را باز کن.</div>

        <div style="height:12px"></div>

        <div class="sectionTitle">افزودن محصول (مدیریت ساده)</div>
        <input class="input" id="newName" placeholder="نام محصول" />
        <div style="height:8px"></div>
        <input class="input" id="newPrice" type="number" placeholder="قیمت (تومان)" />
        <div style="height:8px"></div>
        <input class="input" id="newCat" placeholder="دسته‌بندی (مثلاً لبنیات)" />
        <div style="height:8px"></div>
        <input class="input" id="newImg" placeholder="لینک عکس (اختیاری)" />
        <div style="height:10px"></div>
        <button class="btn btnWhite btnFull" onclick="addProduct()">افزودن</button>
        <div class="muted" style="margin-top:10px">
          نکته: این محصولات در همین گوشی ذخیره می‌شن (localStorage).
        </div>
      </div>

      <!-- Products -->
      <div>
        <div class="productsTop">
          <div class="sectionTitle" style="margin:0">محصولات</div>
          <div class="muted" id="resultCount"></div>
        </div>

        <div class="grid" id="grid"></div>
      </div>

    </div>
  </div>

  <!-- Modal -->
  <div class="modalBg" id="modalBg" onclick="closeModal(event)">
    <div class="modal" onclick="event.stopPropagation()">
      <button class="closeX" onclick="hideModal()">✕</button>
      <div class="modalGrid">
        <div class="modalImg"><img id="mImg" src="" alt=""></div>
        <div class="modalBody">
          <div class="pName" id="mName" style="font-size:18px"></div>
          <div class="pMeta" style="margin-top:10px">
            <span class="pill" id="mCat"></span>
            <span class="pill" id="mBadge"></span>
          </div>
          <div style="height:12px"></div>
          <div class="muted">توضیحات</div>
          <div id="mDesc" style="margin-top:6px; line-height:1.9"></div>

          <div style="height:14px"></div>

          <div class="row">
            <div class="price" id="mPrice" style="font-size:18px"></div>
            <div class="tiny">ارسال با پیک</div>
          </div>

          <div class="pActions" style="margin-top:14px">
            <button class="btn btnRed btnFull" onclick="modalAddToCart()">افزودن به سبد خرید</button>
            <button class="btn btnWhite" onclick="hideModal()">بستن</button>
          </div>

          <div class="muted" style="margin-top:10px">
            این نسخه کوچک است ولی شبیه فروشگاه‌های بزرگ طراحی شده.
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Drawer -->
  <div class="drawerBg" id="drawerBg" onclick="closeCart()"></div>
  <div class="drawer" id="drawer">
    <div class="drawerHead">
      <div style="font-weight:900">سبد خرید</div>
      <button class="btn btnWhite" onclick="closeCart()">بستن</button>
    </div>

    <div class="drawerBody">
      <div id="cartList"></div>

      <div class="card" style="box-shadow:none">
        <div class="sectionTitle">اطلاعات مشتری</div>
        <input class="input" id="cName" placeholder="نام و نام خانوادگی" />
        <div style="height:8px"></div>
        <input class="input" id="cPhone" placeholder="شماره موبایل" />
        <div style="height:8px"></div>
        <textarea id="cAddr" placeholder="آدرس کامل"></textarea>
        <div class="muted" style="margin-top:8px">بعد از ثبت، واتساپ باز می‌شود.</div>
      </div>
    </div>

    <div class="drawerFoot">
      <div class="totalRow">
        <div style="font-weight:900">مجموع</div>
        <div class="pill" id="total">0 تومان</div>
      </div>
      <div style="height:10px"></div>
      <button class="btn btnRed btnFull" onclick="submitOrder()">ثبت سفارش و ارسال به واتساپ</button>
      <div style="height:8px"></div>
      <button class="btn btnWhite btnFull danger" onclick="clearCart()">خالی کردن سبد خرید</button>
    </div>
  </div>

<script>
  // شماره واتساپ خودت (بدون +)
  const WHATSAPP_NUMBER = "989000000000";

  // محصولات پیشفرض (عکس‌ها را بهتر است از GitHub خودت بزاری)
  const DEFAULT_PRODUCTS = [
    {id: 1, name:"برنج ایرانی ۱۰ کیلویی", price:1250000, category:"غلات", image:"images/rice.jpg", badge:"پرفروش", desc:"برنج ایرانی خوش‌عطر، مناسب مهمانی و مصرف روزانه."},
    {id: 2, name:"روغن ۱.۵ لیتری", price:185000, category:"روغن", image:"images/oil.jpg", badge:"اقتصادی", desc:"روغن مناسب پخت‌وپز و سرخ‌کردنی."},
    {id: 3, name:"خرما درجه یک", price:210000, category:"خشکبار", image:"images/date.jpg", badge:"ویژه", desc:"خرمای تازه و نرم، مناسب افطار و پذیرایی."},
    {id: 4, name:"رب گوجه ۸۰۰ گرمی", price:98000, category:"کنسروی", image:"images/tomato.jpg", badge:"جدید", desc:"رب غلیظ و خوش‌رنگ، مناسب خورشت و غذا."},
    {id: 5, name:"چای ایرانی ۵۰۰ گرمی", price:240000, category:"چای", image:"images/tea.jpg", badge:"پیشنهاد", desc:"چای ایرانی با رنگ و عطر عالی."},
    {id: 6, name:"عسل طبیعی", price:480000, category:"خوراکی", image:"images/honey.jpg", badge:"کیفیت بالا", desc:"عسل طبیعی مناسب صبحانه و تقویت بدن."},
    {id: 7, name:"شکر ۱ کیلویی", price:55000, category:"سوپرمارکتی", image:"images/sugar.jpg", badge:"روزانه", desc:"شکر سفید مناسب مصرف روزانه."},
    {id: 8, name:"ماکارونی ۵۰۰ گرمی", price:65000, category:"سوپرمارکتی", image:"images/pasta.jpg", badge:"ارزان", desc:"ماکارونی باکیفیت مناسب غذاهای سریع."},
  ];

  // --- Storage ---
  function loadProducts(){
    const saved = localStorage.getItem("products_v1");
    if(saved){
      try { return JSON.parse(saved); } catch(e){ return [...DEFAULT_PRODUCTS]; }
    }
    return [...DEFAULT_PRODUCTS];
  }
  function saveProducts(list){ localStorage.setItem("products_v1", JSON.stringify(list)); }

  function loadCart(){
    const saved = localStorage.getItem("cart_v1");
    if(saved){
      try { return JSON.parse(saved); } catch(e){ return []; }
    }
    return [];
  }
  function saveCart(){ localStorage.setItem("cart_v1", JSON.stringify(cart)); }

  let products = loadProducts();
  let cart = loadCart();

  // --- UI state ---
  let activeCategory = "همه";
  let modalProductId = null;

  // --- Utils ---
  function toman(n){ return n.toLocaleString("fa-IR") + " تومان"; }
  function safeImg(src){
    // اگر عکس نبود، جایگزین
    return src && src.trim() ? src : "images/placeholder.jpg";
  }

  // --- Categories ---
  function categories(){
    const set = new Set(products.map(p=>p.category));
    return ["همه", ...Array.from(set)];
  }

  function renderCats(){
    const box = document.getElementById("cats");
    box.innerHTML = "";
    categories().forEach(cat=>{
      const btn = document.createElement("button");
      btn.className = "catBtn" + (cat===activeCategory ? " active" : "");
      btn.innerText = cat;
      btn.onclick = ()=>{
        activeCategory = cat;
        renderCats();
        render();
      };
      box.appendChild(btn);
    });
  }

  // --- Product list ---
  function filteredProducts(){
    const q = (document.getElementById("search").value || "").trim().toLowerCase();
    const maxP = parseInt((document.getElementById("maxPrice").value || "").trim());
    const sort = document.getElementById("sort").value;

    let list = [...products];

    if(activeCategory !== "همه"){
      list = list.filter(p=>p.category===activeCategory);
    }
    if(q){
      list = list.filter(p=>p.name.toLowerCase().includes(q));
    }
    if(!isNaN(maxP) && maxP > 0){
      list = list.filter(p=>p.price <= maxP);
    }

    if(sort==="cheap") list.sort((a,b)=>a.price-b.price);
    if(sort==="expensive") list.sort((a,b)=>b.price-a.price);
    if(sort==="new") list.sort((a,b)=>b.id-a.id);
    // popular = پیشفرض

    return list;
  }

  function render(){
    const list = filteredProducts();
    document.getElementById("resultCount").innerText = list.length + " کالا";

    const grid = document.getElementById("grid");
    grid.innerHTML = "";

    list.forEach(p=>{
      const div = document.createElement("div");
      div.className = "pCard";
      div.innerHTML = `
        <div class="pImg">
          <img src="${safeImg(p.image)}" alt="${p.name}" onerror="this.src='images/placeholder.jpg'">
        </div>
        <div class="pBody">
          <div class="pName">${p.name}</div>
          <div class="pMeta">
            <span class="pill">${p.category}</span>
            <span class="pill">${p.badge || "موجود"}</span>
          </div>
          <div class="pPrice">
            <div class="price">${toman(p.price)}</div>
            <div class="tiny">ارسال امروز</div>
          </div>
          <div class="pActions">
            <button class="btn btnWhite btnFull">مشاهده</button>
            <button class="btn btnRed">+</button>
          </div>
        </div>
      `;

      div.querySelectorAll("button")[0].onclick = ()=> showModal(p.id);
      div.querySelectorAll("button")[1].onclick = ()=> addToCart(p.id);

      grid.appendChild(div);
    });

    updateCartUI();
  }

  // --- Modal ---
  function showModal(id){
    const p = products.find(x=>x.id===id);
    if(!p) return;
    modalProductId = id;

    document.getElementById("mImg").src = safeImg(p.image);
    document.getElementById("mName").innerText = p.name;
    document.getElementById("mCat").innerText = p.category;
    document.getElementById("mBadge").innerText = p.badge || "موجود";
    document.getElementById("mDesc").innerText = p.desc || "بدون توضیحات";
    document.getElementById("mPrice").innerText = toman(p.price);

    document.getElementById("modalBg").style.display = "flex";
  }
  function hideModal(){ document.getElementById("modalBg").style.display = "none"; }
  function closeModal(e){ if(e.target.id==="modalBg") hideModal(); }
  function modalAddToCart(){
    if(modalProductId) addToCart(modalProductId);
  }

  // --- Cart ---
  function addToCart(id){
    const p = products.find(x=>x.id===id);
    if(!p) return;
    const x = cart.find(i=>i.id===id);
    if(x) x.qty++;
    else cart.push({id:p.id, name:p.name, price:p.price, image:p.image, qty:1});
    saveCart();
    updateCartUI();
  }
  function decQty(id){
    const x = cart.find(i=>i.id===id);
    if(!x) return;
    x.qty--;
    if(x.qty<=0) cart = cart.filter(i=>i.id!==id);
    saveCart();
    updateCartUI();
    renderCart();
  }
  function incQty(id){
    const x = cart.find(i=>i.id===id);
    if(!x) return;
    x.qty++;
    saveCart();
    updateCartUI();
    renderCart();
  }
  function removeItem(id){
    cart = cart.filter(i=>i.id!==id);
    saveCart();
    updateCartUI();
    renderCart();
  }
  function clearCart(){
    cart = [];
    saveCart();
    updateCartUI();
    renderCart();
    alert("سبد خرید خالی شد");
  }

  function cartTotal(){
    return cart.reduce((s,x)=>s + x.price*x.qty, 0);
  }

  function updateCartUI(){
    document.getElementById("cartCount").innerText = cart.reduce((s,x)=>s+x.qty,0);
    document.getElementById("total").innerText = toman(cartTotal());
  }

  function openCart(){
    document.getElementById("drawerBg").style.display = "block";
    document.getElementById("drawer").classList.add("open");
    renderCart();
  }
  function closeCart(){
    document.getElementById("drawerBg").style.display = "none";
    document.getElementById("drawer").classList.remove("open");
  }

  function renderCart(){
    const box = document.getElementById("cartList");
    box.innerHTML = "";

    if(cart.length===0){
      box.innerHTML = `<div class="card" style="box-shadow:none">سبد خرید خالی است.</div>`;
      return;
    }

    cart.forEach(i=>{
      const div = document.createElement("div");
      div.className = "cartItem";
      div.innerHTML = `
        <div class="cartThumb">
          <img src="${safeImg(i.image)}" onerror="th
