# STICKY-SELLER<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>STICKY SELLER - Online Shopping</title>
  <meta name="description" content="Sticky Seller – Flipkart-style online shopping for Men & Women. Fashion, shoes, accessories and more." />
  <style>
    :root{
      --brand:#2874f0; --brand-dark:#0f5cd8; --bg:#f1f3f6; --text:#202124; --muted:#5f6368; --card:#fff; --ok:#1aa34a; --danger:#d93025;
    }
    *{box-sizing:border-box}
    body { margin: 0; font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, sans-serif; background: var(--bg); color: var(--text); }
    /* Header */
    header { position: sticky; top: 0; z-index: 40; background: var(--brand); color: white; padding: 10px 16px; display: grid; grid-template-columns: 220px 1fr auto; gap: 12px; align-items: center; box-shadow: 0 2px 8px rgba(0,0,0,.15); }
    .logo { display:flex; align-items:center; gap:10px; font-weight: 800; letter-spacing:.3px; }
    .logo svg{ width:36px; height:36px; }
    .search { display:flex; gap:8px; align-items:center; }
    .search input { width: 100%; padding: 10px 12px; border: none; border-radius: 4px; outline: none; }
    nav { display: flex; gap: 14px; align-items: center; }
    nav a { color: white; text-decoration: none; font-weight: 600; padding:8px 10px; border-radius:8px }
    nav a:hover{ background: rgba(255,255,255,.15) }
    .cart-btn { display:flex; align-items:center; gap:8px; background: rgba(255,255,255,.15); padding:8px 10px; border-radius: 8px; cursor: pointer; border:0; color:#fff; font-weight:700 }
    .pill{ background:#fff; color: var(--brand); font-weight: 800; padding: 0 8px; border-radius: 999px; min-width: 24px; height: 24px; display: grid; place-items: center; }

    /* Sections */
    main{ padding: 16px; }
    .section { margin: 0 auto 22px; max-width: 1200px; }
    .section h2 { margin: 0 0 12px; font-size: 22px; }

    /* Banners */
    .banner{ display:grid; grid-template-columns: 1fr 1fr; gap:16px; margin:0 auto 18px; max-width:1200px }
    .banner .card{ background:linear-gradient(135deg,#e9f0ff,#dce8ff); border:1px solid #d2defa; border-radius:12px; padding:16px }
    .banner .card.women{ background:linear-gradient(135deg,#ffe9f1,#ffddec); border-color:#ffd0e3 }

    /* Product grid */
    .products { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 14px; }
    .product { background: var(--card); border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.08); padding: 10px; display:flex; flex-direction:column; }
    .product img { width: 100%; height: 180px; object-fit: cover; border-radius: 6px; background:#eee }
    .product h3 { font-size: 15px; margin: 8px 0 4px; }
    .product .brand { color: var(--muted); font-size: 12px; }
    .price-row{ display:flex; align-items:center; gap:8px; margin-top:6px }
    .price { color: var(--brand); font-weight: 800; }
    .mrp{ text-decoration: line-through; color:#888; font-size:12px }
    .off{ color: var(--ok); font-weight: 700; font-size:12px }
    .actions{ margin-top:auto; display:flex; gap:8px }
    .btn{ flex:1; background: var(--brand); color:#fff; border:0; padding:8px 10px; border-radius:6px; cursor:pointer; font-weight:700 }
    .btn.ghost{ background:#eef3ff; color: var(--brand); }

    /* Cart drawer */
    .drawer{ position: fixed; top:0; right:-420px; width: 360px; max-width: 90vw; height: 100dvh; background:#fff; box-shadow: -8px 0 24px rgba(0,0,0,.2); transition: right .25s ease; z-index:60; display:flex; flex-direction:column }
    .drawer.open{ right:0 }
    .drawer header{ background:#fff; color:#111; padding:14px 16px; box-shadow: 0 1px 0 rgba(0,0,0,.08); display:flex; align-items:center; justify-content:space-between }
    .drawer .items{ padding: 10px; overflow:auto; flex:1; display:grid; gap:10px }
    .cart-item{ display:grid; grid-template-columns: 72px 1fr auto; gap:10px; background:#f8f9fb; border:1px solid #e6e8ef; border-radius:10px; padding:8px }
    .cart-item img{ width:72px; height:72px; object-fit:cover; border-radius:8px }
    .qty{ display:flex; align-items:center; gap:6px }
    .qty button{ width:26px; height:26px; border-radius:6px; border:1px solid #d0d7e2; background:#fff; cursor:pointer; font-weight:800 }
    .totals{ padding: 12px 16px; border-top:1px solid #eceff5; }
    .row{ display:flex; justify-content:space-between; margin:6px 0 }
    .checkout-btn{ width:100%; background:var(--ok); color:#fff; border:0; padding:12px; border-radius:8px; font-weight:900; cursor:pointer }

    /* Checkout modal */
    .modal{ position:fixed; inset:0; background:rgba(0,0,0,.55); display:none; align-items:center; justify-content:center; z-index:70 }
    .modal.open{ display:flex }
    .modal .sheet{ width: min(720px, 92vw); background:#fff; border-radius:12px; padding:16px; display:grid; grid-template-columns: 1fr 1fr; gap:14px }
    .sheet h3{ grid-column:1 / -1; margin:6px 0 10px }
    .field{ display:grid; gap:6px }
    .field input, .field select{ padding:10px; border-radius:8px; border:1px solid #d0d7e2 }
    .pay{ grid-column:1 / -1; display:flex; gap:10px; }
    .place{ background:var(--brand); color:#fff; border:0; padding:12px 14px; border-radius:8px; font-weight:900; cursor:pointer }

    /* Footer */
    footer { background: #172337; color: white; padding: 20px; text-align: center; margin-top: 24px; }

    /* Responsive */
    @media (max-width: 840px){
      header{ grid-template-columns: 1fr auto; }
      .logo span{ display:none }
    }
    @media (max-width: 680px){
      .modal .sheet{ grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
  <header>
    <a class="logo" href="#home" aria-label="Sticky Seller home">
      <!-- SVG LOGO -->
      <svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Sticky Seller logo"><defs><linearGradient id="g" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#fff"/><stop offset="1" stop-color="#dce8ff"/></linearGradient></defs><rect x="2" y="2" width="60" height="60" rx="12" fill="url(#g)"/><rect x="2" y="2" width="60" height="60" rx="12" fill="none" stroke="#ffffff55"/><path d="M16 38c0-6 8-6 12-8s2-6-4-6-9 3-9 3" stroke="#2874f0" stroke-width="4" fill="none" stroke-linecap="round"/><path d="M48 26c0 6-8 6-12 8s-2 6 4 6 9-3 9-3" stroke="#0f5cd8" stroke-width="4" fill="none" stroke-linecap="round"/></svg>
      <span>STICKY SELLER</span>
    </a>
    <div class="search"><input id="search" type="search" placeholder="Search for products, brands and more" /></div>
    <nav>
      <a href="#men">Men</a>
      <a href="#women">Women</a>
      <button class="cart-btn" id="openCart" aria-label="Open cart">Cart <span class="pill" id="pill">0</span></button>
    </nav>
  </header>

  <main id="home">
    <div class="banner">
      <div class="card">
        <h3>Men's Deals</h3>
        <p class="muted">Tees, shoes & accessories</p>
      </div>
      <div class="card women">
        <h3>Women’s Picks</h3>
        <p class="muted">Dresses, handbags & heels</p>
      </div>
    </div>

    <section class="section" id="men">
      <h2>Men's Section</h2>
      <div class="products" id="menGrid"></div>
    </section>

    <section class="section" id="women">
      <h2>Women's Section</h2>
      <div class="products" id="womenGrid"></div>
    </section>
  </main>

  <!-- Cart Drawer -->
  <aside class="drawer" id="drawer" aria-label="Shopping cart">
    <header>
      <strong>Cart</strong>
      <button id="closeCart" class="cart-btn" style="background:#eef3ff; color:var(--brand)">Close</button>
    </header>
    <div class="items" id="cartItems"></div>
    <div class="totals">
      <div class="row"><span>Subtotal</span><strong id="subtotal">₹0</strong></div>
      <div class="row" style="font-size:12px; color:#4a4f55"><span>Shipping</span><span>Calculated at checkout</span></div>
      <button class="checkout-btn" id="checkoutBtn">Proceed to Checkout</button>
    </div>
  </aside>

  <!-- Checkout Modal -->
  <div class="modal" id="checkoutModal" role="dialog" aria-modal="true">
    <div class="sheet">
      <h3>Checkout</h3>
      <div class="field"><label>Full Name<input id="cName" placeholder="Your name" required></label></div>
      <div class="field"><label>Email<input id="cEmail" type="email" placeholder="you@example.com" required></label></div>
      <div class="field"><label>Phone<input id="cPhone" placeholder="+91" required></label></div>
      <div class="field"><label>Address<input id="cAddr" placeholder="Street, City, PIN" required></label></div>
      <div class="field"><label>Payment<select id="cPay"><option>Cash on Delivery</option><option>UPI</option><option>Card</option></select></label></div>
      <div class="pay">
        <button class="place" id="placeOrder">Place Order</button>
        <button class="btn ghost" id="cancelCheckout" type="button">Cancel</button>
      </div>
      <p id="thankyou" style="display:none; grid-column:1 / -1; color:var(--ok); font-weight:800">Thank you! Your order request has been captured (demo). We will contact you soon.</p>
    </div>
  </div>

  <footer>
    <p>© <span id="year"></span> STICKY SELLER. All Rights Reserved.</p>
  </footer>

  <script>
    document.getElementById('year').textContent = new Date().getFullYear();

    // --- Simple Catalog ---
    const catalog = [
      // Men
      { id:'m1', gender:'men', name:'Casual Shirt', brand:'Sticky Apparel', price:999, mrp:1499, off:33, img:'https://images.unsplash.com/photo-1521335629791-ce4aec67dd47?w=800' },
      { id:'m2', gender:'men', name:'Running Shoes', brand:'RunMax', price:1999, mrp:2799, off:29, img:'https://images.unsplash.com/photo-1512436991641-6745cdb1723f?w=800' },
      { id:'m3', gender:'men', name:'Analog Watch', brand:'Tempo', price:1499, mrp:2199, off:32, img:'https://images.unsplash.com/photo-1528701800489-20be0e0b3481?w=800' },
      { id:'m4', gender:'men', name:'Denim Jacket', brand:'NorthMill', price:2299, mrp:3299, off:30, img:'https://images.unsplash.com/photo-1520975916090-3105956dac38?w=800' },
      // Women
      { id:'w1', gender:'women', name:'Summer Dress', brand:'Lumi', price:1299, mrp:1999, off:35, img:'https://images.unsplash.com/photo-1520962918287-7448c2878f65?w=800' },
      { id:'w2', gender:'women', name:'Handbag', brand:'CityTote', price:1799, mrp:2599, off:31, img:'https://images.unsplash.com/photo-1519744346361-1a3d8e6f1f6b?w=800' },
      { id:'w3', gender:'women', name:'High Heels', brand:'Elle', price:1599, mrp:2399, off:33, img:'https://images.unsplash.com/photo-1522337660859-02fbefca4702?w=800' },
      { id:'w4', gender:'women', name:'Hoodie', brand:'Cozy', price:1399, mrp:1999, off:30, img:'https://images.unsplash.com/photo-1520975916090-3105956dac38?w=800' },
    ];

    // Render products
    const INR = v => new Intl.NumberFormat('en-IN', { style:'currency', currency:'INR', maximumFractionDigits:0 }).format(v);
    const card = p => `
      <article class="product" data-id="${p.id}">
        <img src="${p.img}" alt="${p.name}" loading="lazy"/>
        <h3>${p.name}</h3>
        <div class="brand">${p.brand}</div>
        <div class="price-row"><span class="price">${INR(p.price)}</span> <span class="mrp">${INR(p.mrp)}</span> <span class="off">${p.off}% off</span></div>
        <div class="actions">
          <button class="btn add" data-id="${p.id}">Add to Cart</button>
          <button class="btn ghost buy" data-id="${p.id}">Buy Now</button>
        </div>
      </article>`;

    const menGrid = document.getElementById('menGrid');
    const womenGrid = document.getElementById('womenGrid');
    menGrid.innerHTML = catalog.filter(x=>x.gender==='men').map(card).join('');
    womenGrid.innerHTML = catalog.filter(x=>x.gender==='women').map(card).join('');

    // --- Cart (localStorage demo) ---
    const CART_KEY = 'ss_cart_v2';
    const pill = document.getElementById('pill');
    const drawer = document.getElementById('drawer');
    const itemsEl = document.getElementById('cartItems');
    const subtotalEl = document.getElementById('subtotal');

    const getCart = () => { try{return JSON.parse(localStorage.getItem(CART_KEY)) || {};}catch{return{}} };
    const setCart = (c) => localStorage.setItem(CART_KEY, JSON.stringify(c));
    const totalCount = (c) => Object.values(c).reduce((a,b)=>a+b,0);

    function renderCart(){
      const cart = getCart();
      const ids = Object.keys(cart);
      if(ids.length===0){ itemsEl.innerHTML = '<p>Your cart is empty.</p>'; subtotalEl.textContent = INR(0); pill.textContent='0'; return; }
      let html = '';
      let sum = 0;
      ids.forEach(id=>{
        const p = catalog.find(x=>x.id===id);
        if(!p) return;
        const qty = cart[id];
        sum += p.price * qty;
        html += `
          <div class="cart-item" data-id="${id}">
            <img src="${p.img}" alt="${p.name}">
            <div>
              <strong>${p.name}</strong>
              <div style="font-size:12px; color:#5f6368">${p.brand}</div>
              <div class="price-row"><span class="price">${INR(p.price)}</span></div>
              <div class="qty">
                <button class="dec">−</button>
                <span>${qty}</span>
                <button class="inc">+</button>
                <button class="rem" style="margin-left:auto; border:1px solid #e3e7ef; background:#fff; border-radius:6px; padding:4px 8px; cursor:pointer">Remove</button>
              </div>
            </div>
            <div style="font-weight:800">${INR(p.price*qty)}</div>
          </div>`;
      });
      itemsEl.innerHTML = html;
      subtotalEl.textContent = INR(sum);
      pill.textContent = totalCount(cart);
    }

    function add(id, q=1){ const c=getCart(); c[id]=(c[id]||0)+q; setCart(c); renderCart(); }
    function dec(id){ const c=getCart(); if(c[id]){ c[id]--; if(c[id]<=0) delete c[id]; setCart(c); renderCart(); } }
    function rem(id){ const c=getCart(); delete c[id]; setCart(c); renderCart(); }

    document.body.addEventListener('click', (e)=>{
      const addBtn = e.target.closest('.add');
      const buyBtn = e.target.closest('.buy');
      if(addBtn){ add(addBtn.dataset.id); drawer.classList.add('open'); }
      if(buyBtn){ add(buyBtn.dataset.id); drawer.classList.add('open'); }

      const item = e.target.closest('.cart-item');
      if(item){
        if(e.target.classList.contains('inc')) add(item.dataset.id);
        if(e.target.classList.contains('dec')) dec(item.dataset.id);
        if(e.target.classList.contains('rem')) rem(item.dataset.id);
      }
    });

    document.getElementById('openCart').addEventListener('click',()=>{ drawer.classList.add('open'); renderCart(); });
    document.getElementById('closeCart').addEventListener('click',()=> drawer.classList.remove('open'));

    renderCart();

    // Search (filters both grids)
    document.getElementById('search').addEventListener('input', (e)=>{
      const q = e.target.value.toLowerCase();
      const show = p => p.name.toLowerCase().includes(q) || p.brand.toLowerCase().includes(q);
      menGrid.innerHTML = catalog.filter(x=>x.gender==='men' && show(x)).map(card).join('');
      womenGrid.innerHTML = catalog.filter(x=>x.gender==='women' && show(x)).map(card).join('');
    });

    // Checkout flow (demo)
    const checkoutBtn = document.getElementById('checkoutBtn');
    const checkoutModal = document.getElementById('checkoutModal');
    const cancelCheckout = document.getElementById('cancelCheckout');
    const placeOrder = document.getElementById('placeOrder');
    const thankyou = document.getElementById('thankyou');

    checkoutBtn.addEventListener('click', ()=>{
      if(totalCount(getCart())===0){ alert('Your cart is empty.'); return; }
      checkoutModal.classList.add('open');
    });
    cancelCheckout.addEventListener('click', ()=> checkoutModal.classList.remove('open'));

    placeOrder.addEventListener('click', ()=>{
      // Basic validation (demo)
      const name = document.getElementById('cName').value.trim();
      const email = document.getElementById('cEmail').value.trim();
      const addr = document.getElementById('cAddr').value.trim();
      if(!name || !email || !addr){ alert('Please fill name, email and address.'); return; }
      // In a real app: send to backend/Google Sheet/WhatsApp/Payment gateway
      localStorage.removeItem(CART_KEY);
      renderCart();
      thankyou.style.display='block';
      setTimeout(()=>{ checkoutModal.classList.remove('open'); thankyou.style.display='none'; }, 1600);
    });
  </script>
</body>
</html>
