<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>XxGamingxXyt12 — Official Site</title>
  <meta name="description" content="XxGamingxXyt12 — Gaming videos, livestreams & merch" />

  <style>
    :root{
      --bg:#07080b;
      --panel:#0f1318;
      --accent:#00e0ff;
      --accent-2:#7b3cff;
      --muted:#9aa3ad;
      --glass: rgba(255,255,255,0.03);
      --card: rgba(255,255,255,0.02);
      --accent-glow: 0 0 18px rgba(0,224,255,0.15), 0 0 40px rgba(123,60,255,0.05);
    }
    html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;}
    body{
      background: linear-gradient(180deg,#02040a 0%, #070912 100%);
      color:#e6eef6;
      -webkit-font-smoothing:antialiased;
      overflow-x:hidden;
    }

    /* animated canvas sits behind page content */
    #bgCanvas{
      position:fixed;left:0;top:0;width:100%;height:100%;z-index:0;
      filter: drop-shadow(0 0 20px rgba(0,224,255,0.06));
    }

    /* page container */
    .site{
      position:relative;z-index:5;max-width:1200px;margin:0 auto;padding:28px;
    }

    /* header */
    header{
      display:flex;align-items:center;gap:18px;padding:18px 8px;border-radius:12px;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      box-shadow: 0 6px 30px rgba(2,6,12,0.6);
      margin-top:18px;
    }
    .logo {
      display:flex;align-items:center;gap:12px;
    }
    .logo img{
      width:88px;height:88px;object-fit:cover;border-radius:10px;border:2px solid rgba(0,224,255,0.2);
      box-shadow: 0 6px 30px rgba(0,0,0,0.6), 0 0 22px rgba(0,224,255,0.06) inset;
    }
    .brand {
      line-height:1;
    }
    .brand h1{font-size:20px;margin:0;color:var(--accent);text-shadow:0 0 12px rgba(0,224,255,0.12);}
    .brand p{margin:2px 0 0 0;color:var(--muted);font-size:13px}

    nav {margin-left:auto;display:flex;gap:10px;align-items:center;}
    nav a{ color:var(--accent); text-decoration:none;padding:8px 12px;border-radius:8px;font-weight:600;
          background:transparent;border:1px solid rgba(255,255,255,0.02); transition: all .18s ease;}
    nav a:hover{ transform:translateY(-2px); box-shadow: var(--accent-glow); color:#fff; }

    /* hero */
    .hero{
      margin-top:26px;padding:28px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.015));
      display:grid;grid-template-columns: 1fr 360px;gap:18px;align-items:center;
    }
    .hero-left h2{font-size:34px;margin:0 0 10px;color:var(--accent)}
    .hero-left p{margin:0 0 18px;color:var(--muted);font-size:15px}
    .cta-row{display:flex;gap:12px;flex-wrap:wrap}
    .btn {
      padding:12px 18px;border-radius:10px;background:linear-gradient(90deg,var(--accent),var(--accent-2));
      color:#03121a;text-decoration:none;font-weight:700;box-shadow:var(--accent-glow);
    }
    .btn.secondary{background:transparent;border:1px solid rgba(255,255,255,0.03);color:var(--accent);}

    .hero-right{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:10px;padding:18px;text-align:center;
    }
    .hero-right img{width:100%;height:220px;object-fit:cover;border-radius:8px;border:1px solid rgba(255,255,255,0.03)}

    /* sections */
    section{margin-top:18px;padding:18px;border-radius:12px;background:var(--panel);box-shadow: 0 10px 40px rgba(2,6,12,0.6);}

    .section-title{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:10px}
    .section-title h3{margin:0;color:var(--accent)}
    .flex-row{display:flex;gap:18px;flex-wrap:wrap;align-items:flex-start}

    /* videos */
    .videos-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:12px}
    .video-card{background:var(--card);border-radius:8px;padding:8px}
    .video-card iframe{width:100%;height:160px;border-radius:6px;border:0;display:block}

    /* merch */
    .shop-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(210px,1fr));gap:12px}
    .product{background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.005));padding:12px;border-radius:10px;text-align:center}
    .product img{width:100%;height:230px;object-fit:cover;border-radius:8px;border:1px solid rgba(255,255,255,0.03)}
    .product h4{margin:10px 0 6px 0}
    .price{font-weight:800;color:var(--accent);margin-bottom:8px}
    .add-btn{background:var(--accent);border:none;padding:10px 12px;border-radius:8px;color:#02121a;font-weight:700;cursor:pointer}
    .add-btn.small{padding:8px 10px;font-size:14px}

    /* cart panel */
    .cart-btn{position:fixed;right:18px;bottom:18px;background:linear-gradient(90deg,var(--accent),var(--accent-2));border:none;color:#02121a;padding:12px 14px;border-radius:999px;box-shadow:var(--accent-glow);cursor:pointer;z-index:10}
    .cart-count{background:#02121a;color:var(--accent);padding:3px 8px;border-radius:999px;font-weight:700;margin-left:8px;border:1px solid rgba(255,255,255,0.03)}

    /* cart modal */
    .modal{
      position:fixed;right:18px;bottom:70px;width:360px;max-width:94%;z-index:40;
      background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:12px;padding:12px;box-shadow:0 20px 60px rgba(2,6,12,0.6);
      display:none;flex-direction:column;gap:12px;
    }
    .cart-item{display:flex;gap:12px;align-items:center}
    .cart-item img{width:64px;height:64px;object-fit:cover;border-radius:6px}
    .cart-footer{display:flex;justify-content:space-between;align-items:center;margin-top:8px}
    .checkout-btn{background:var(--accent-2);color:#fff;padding:10px 12px;border-radius:10px;border:none;cursor:pointer;font-weight:800}
    .small-muted{color:var(--muted);font-size:13px}

    /* footer */
    footer{margin-top:28px;padding:18px;text-align:center;color:var(--muted);font-size:14px;border-radius:8px}

    /* responsive adjustments */
    @media (max-width:880px){
      .hero{grid-template-columns:1fr}
      .hero-right img{height:180px}
    }
  </style>
</head>
<body>

<!-- animated background canvas -->
<canvas id="bgCanvas"></canvas>

<div class="site">

  <!-- Header -->
  <header>
    <div class="logo">
      <!-- *** REPLACE IMAGE PATH if you host elsewhere *** -->
      <img src="/mnt/data/263C0503-F0FC-4788-917E-7E3AABAF094A.png" alt="XxGamingxXyt12 logo" id="siteLogo">
      <div class="brand">
        <h1>XxGamingxXyt12</h1>
        <p>Gaming • Streams • Merch</p>
      </div>
    </div>

    <nav>
      <a href="#about">About</a>
      <a href="#videos">Videos</a>
      <a href="#merch">Merch</a>
      <a href="#socials">Socials</a>
      <a href="#contact" class="secondary">Contact</a>
    </nav>
  </header>

  <!-- HERO -->
  <div class="hero" role="region" aria-label="Hero">
    <div class="hero-left">
      <h2>Welcome to XxGamingxXyt12</h2>
      <p>Gameplay, highlights, livestreams and exclusive merch drops. New videos every week — hit subscribe and support the channel!</p>
      <div class="cta-row">
        <a class="btn" href="https://www.youtube.com" target="_blank" id="visitChannel">Visit Channel</a>
        <a class="btn secondary" href="#merch">Shop Merch</a>
      </div>

      <div style="margin-top:16px;color:var(--muted);font-size:14px">
        <strong>Tip:</strong> Click any merch item to add to cart. Checkout uses PayPal placeholders — I'll help wire a real payment method when you choose one.
      </div>
    </div>

    <div class="hero-right">
      <!-- featured artwork uses same uploaded image, feel free to replace -->
      <img src="/mnt/data/263C0503-F0FC-4788-917E-7E3AABAF094A.png" alt="Featured artwork">
      <div style="margin-top:10px;color:var(--muted);font-size:13px">Official channel artwork</div>
    </div>
  </div>

  <!-- About -->
  <section id="about">
    <div class="section-title">
      <h3>About</h3>
      <div class="small-muted">XxGamingxXyt12 — Gamer & Content Creator</div>
    </div>
    <p style="color:var(--muted)">Welcome — I play a mix of competitive & chill games, post montages, full gameplay walkthroughs, and stream weekly. Join the community and grab exclusive merch to support the channel!</p>
  </section>

  <!-- Videos -->
  <section id="videos">
    <div class="section-title">
      <h3>Latest Videos</h3>
      <div class="small-muted">Embedded previews — replace the IDs with your own</div>
    </div>

    <div class="videos-grid">
      <!-- Replace `VIDEO_ID` with your YouTube video IDs -->
      <div class="video-card">
        <iframe src="https://www.youtube.com/embed/VIDEO_ID_1" title="Video 1" allowfullscreen></iframe>
        <div style="padding:8px;color:var(--muted)"><strong>Video Title 1</strong><div style="font-size:13px">Short description or timestamp</div></div>
      </div>

      <div class="video-card">
        <iframe src="https://www.youtube.com/embed/VIDEO_ID_2" title="Video 2" allowfullscreen></iframe>
        <div style="padding:8px;color:var(--muted)"><strong>Video Title 2</strong><div style="font-size:13px">Short description</div></div>
      </div>

      <div class="video-card">
        <iframe src="https://www.youtube.com/embed/VIDEO_ID_3" title="Video 3" allowfullscreen></iframe>
        <div style="padding:8px;color:var(--muted)"><strong>Video Title 3</strong><div style="font-size:13px">Short description</div></div>
      </div>
    </div>
  </section>

  <!-- Merch -->
  <section id="merch">
    <div class="section-title">
      <h3>Merch Shop</h3>
      <div class="small-muted">Exclusive designs — click an item to add to cart</div>
    </div>

    <div class="shop-grid" id="shopGrid">
      <!-- Products are injected by JavaScript. Default examples below -->
      <!-- You can replace images and prices in the `products` array in the JS -->
    </div>
  </section>

  <!-- Socials / Contact -->
  <section id="socials" style="display:flex;flex-direction:column;gap:12px">
    <div class="section-title">
      <h3>Follow / Contact</h3>
      <div class="small-muted">Stay connected</div>
    </div>

    <div style="display:flex;gap:10px;flex-wrap:wrap">
      <a class="btn" href="https://www.youtube.com" target="_blank">YouTube</a>
      <a class="btn" href="#" target="_blank">TikTok</a>
      <a class="btn" href="#" target="_blank">Instagram</a>
      <a class="btn" href="#" id="discordBtn">Discord</a>
    </div>

    <div style="margin-top:8px;color:var(--muted)">Business / collabs: <a href="mailto:your-email-here@example.com" style="color:var(--accent);text-decoration:none">your-email-here@example.com</a></div>
  </section>

  <footer>
    © <span id="year"></span> XxGamingxXyt12 — Built with love. Replace video IDs and product links to publish.
  </footer>

</div>

<!-- Cart UI -->
<button class="cart-btn" id="openCart">
  Cart <span class="cart-count" id="cartCount">0</span>
</button>

<div class="modal" id="cartModal" role="dialog" aria-label="Shopping cart">
  <div style="display:flex;justify-content:space-between;align-items:center">
    <strong>Your Cart</strong>
    <button id="closeCart" style="background:transparent;border:0;color:var(--muted);cursor:pointer">✕</button>
  </div>
  <div id="cartItems" style="display:flex;flex-direction:column;gap:8px;max-height:300px;overflow:auto"></div>
  <div class="cart-footer">
    <div>
      <div class="small-muted">Total</div>
      <div id="cartTotal" style="font-size:18px;font-weight:800;color:var(--accent)">£0.00</div>
    </div>
    <div>
      <!-- Placeholder PayPal button: integrate real PayPal/Stripe as needed -->
      <button class="checkout-btn" id="checkoutBtn">Checkout (PayPal)</button>
    </div>
  </div>
  <div style="font-size:12px;color:var(--muted);margin-top:8px">This demo uses a client-side cart. To accept real payments, connect PayPal/Stripe or a store platform (I can set that up).</div>
</div>

<script>
  // small helpers
  const $ = sel => document.querySelector(sel);
  const $$ = sel => document.querySelectorAll(sel);

  // set year
  document.getElementById('year').textContent = new Date().getFullYear();

  // PRODUCTS (customize this array: image paths, names, prices)
  const products = [
    {
      id: 'hoodie-001',
      name: 'XxGamingxXyt12 - Neon Hoodie',
      price: 29.99,
      img: '/mnt/data/263C0503-F0FC-4788-917E-7E3AABAF094A.png',
      desc: 'Premium hoodie with printed neon logo.'
    },
    {
      id: 'shirt-001',
      name: 'XxGamingxXyt12 - Logo Tee',
      price: 14.99,
      img: '/mnt/data/263C0503-F0FC-4788-917E-7E3AABAF094A.png',
      desc: 'Soft cotton tee, multiple sizes.'
    },
    {
      id: 'mug-001',
      name: 'XxGamingxXyt12 - Gamer Mug',
      price: 9.99,
      img: '/mnt/data/263C0503-F0FC-4788-917E-7E3AABAF094A.png',
      desc: '11oz ceramic mug with glossy print.'
    }
  ];

  // render products
  const shopGrid = document.getElementById('shopGrid');
  function renderProducts(){
    shopGrid.innerHTML = '';
    products.forEach(p=>{
      const div = document.createElement('div');
      div.className = 'product';
      div.innerHTML = `
        <img src="${p.img}" alt="${p.name}">
        <h4>${p.name}</h4>
        <div class="price">£${p.price.toFixed(2)}</div>
        <div style="color:var(--muted);font-size:13px;margin-bottom:8px">${p.desc}</div>
        <button class="add-btn" data-id="${p.id}">Add to cart</button>
      `;
      shopGrid.appendChild(div);
    });
  }
  renderProducts();

  // CART (client-side using localStorage)
  let cart = JSON.parse(localStorage.getItem('xg_cart')||'[]');
  function saveCart(){ localStorage.setItem('xg_cart', JSON.stringify(cart)); updateCartUI(); }
  function addToCart(id){
    const prod = products.find(p=>p.id===id);
    if(!prod) return;
    const existing = cart.find(i=>i.id===id);
    if(existing) existing.qty++;
    else cart.push({id:prod.id, name:prod.name, price:prod.price, img:prod.img, qty:1});
    saveCart();
    pulseCart();
  }
  function removeFromCart(id){
    cart = cart.filter(i=>i.id!==id);
    saveCart();
  }
  function changeQty(id, qty){
    const it = cart.find(i=>i.id===id);
    if(!it) return;
    it.qty = Math.max(1, qty);
    saveCart();
  }

  function cartTotal(){
    return cart.reduce((s,i)=>s + i.price * i.qty, 0);
  }

  function updateCartUI(){
    $('#cartCount').textContent = cart.reduce((s,i)=>s+i.qty,0);
    $('#cartTotal').textContent = '£' + cartTotal().toFixed(2);
    const list = $('#cartItems');
    list.innerHTML = '';
    if(cart.length===0){
      list.innerHTML = '<div style="color:var(--muted)">Your cart is empty.</div>';
      return;
    }
    cart.forEach(item=>{
      const row = document.createElement('div');
      row.className = 'cart-item';
      row.innerHTML = `
        <img src="${item.img}" alt="${item.name}">
        <div style="flex:1">
          <div style="font-weight:700">${item.name}</div>
          <div style="color:var(--muted);font-size:13px">£${item.price.toFixed(2)} • x<input style="width:44px;margin-left:6px;padding:3px;border-radius:6px;border:1px solid rgba(255,255,255,0.04)" type="number" min="1" value="${item.qty}" data-id="${item.id}" class="qtyInput"></div>
        </div>
        <div style="display:flex;flex-direction:column;gap:6px">
          <button style="background:transparent;border:0;color:var(--muted);cursor:pointer" data-remove="${item.id}">Remove</button>
          <div style="font-weight:700;color:var(--accent)">£${(item.price*item.qty).toFixed(2)}</div>
        </div>
      `;
      list.appendChild(row);
    });

    // attach listeners to qty and remove
    document.querySelectorAll('.qtyInput').forEach(input=>{
      input.addEventListener('change', e=>{
        const id = e.target.dataset.id;
        const val = parseInt(e.target.value) || 1;
        changeQty(id, val);
      });
    });
    document.querySelectorAll('[data-remove]').forEach(btn=>{
      btn.addEventListener('click', e=>{
        const id = e.target.dataset.remove;
        removeFromCart(id);
      });
    });
  }

  // buttons for add-to-cart
  document.addEventListener('click', e=>{
    const add = e.target.closest('[data-id]');
    if(add && add.classList.contains('add-btn')){
      const id = add.dataset.id;
      addToCart(id);
    }
  });

  // open/close cart
  const cartModal = $('#cartModal');
  $('#openCart').addEventListener('click', ()=> { cartModal.style.display = 'flex'; });
  $('#closeCart').addEventListener('click', ()=> { cartModal.style.display = 'none'; });

  function pulseCart(){
    const el = $('#openCart');
    el.animate([{transform:'scale(1)'},{transform:'scale(1.08)'},{transform:'scale(1)'}], {duration:400});
  }

  // checkout (placeholder)
  $('#checkoutBtn').addEventListener('click', ()=>{
    if(cart.length===0){ alert('Your cart is empty. Add something first.'); return; }
    // Simple demonstration: create a pseudo order summary and open PayPal checkout placeholder
    const summary = cart.map(i=>`${i.qty}x ${i.name} (£${i.price.toFixed(2)})`).join('\\n');
    if(confirm(`Proceed to PayPal checkout?\\n\\n${summary}\\n\\nTotal: £${cartTotal().toFixed(2)}`)){
      // In production: redirect to server-side create-paypal-order or to your PayPal product page
      window.open('https://www.paypal.com/gb/home', '_blank');
      // optional: clear cart (comment out if you prefer leaving it)
      cart = [];
      saveCart();
      cartModal.style.display = 'none';
      alert('This demo redirects to PayPal homepage. To accept payments you must integrate your PayPal/Shopify/Stripe account — I can help set that up.');
    }
  });

  // init cart UI
  updateCartUI();

  // quick demo: wire product injection click handlers
  document.getElementById('visitChannel').addEventListener('click', e=>{
    // If you want it to go to your channel directly, replace href above or change to your channel link
  });

  // --- Animated background: particle field with neon lines ---
  (function(){
    const canvas = document.getElementById('bgCanvas');
    const ctx = canvas.getContext('2d');
    let width = canvas.width = innerWidth;
    let height = canvas.height = innerHeight;
    const mouse = {x: width/2, y: height/2};

    addEventListener('resize', ()=>{
      width = canvas.width = innerWidth;
      height = canvas.height = innerHeight;
    });
    addEventListener('mousemove', (e)=>{ mouse.x = e.clientX; mouse.y = e.clientY; });

    // particles
    const COUNT = Math.floor(Math.max(30, Math.min(120, width/12)));
    const pts = [];
    for(let i=0;i<COUNT;i++){
      pts.push({
        x: Math.random()*width,
        y: Math.random()*height,
        vx:(Math.random()-0.5)*0.6,
        vy:(Math.random()-0.5)*0.6,
        r: Math.random()*1.6 + 0.6
      });
    }

    function step(){
      ctx.clearRect(0,0,width,height);

      // gradient overlay (subtle)
      const g = ctx.createLinearGradient(0,0,width,height);
      g.addColorStop(0,"rgba(10,12,20,0.18)");
      g.addColorStop(1,"rgba(3,6,12,0.18)");
      ctx.fillStyle = g;
      ctx.fillRect(0,0,width,height);

      // draw connections
      for(let i=0;i<pts.length;i++){
        const a = pts[i];
        for(let j=i+1;j<pts.length;j++){
          const b = pts[j];
          const dx = a.x-b.x, dy=a.y-b.y;
          const d = Math.sqrt(dx*dx+dy*dy);
          if(d < 140){
            const alpha = 1 - d/140;
            ctx.strokeStyle = `rgba(0,224,255,${0.06*alpha})`;
            ctx.lineWidth = 1;
            ctx.beginPath();
            ctx.moveTo(a.x,a.y);
            ctx.lineTo(b.x,b.y);
            ctx.stroke();
          }
        }
      }

      // draw points
      for(let p of pts){
        p.x += p.vx; p.y += p.vy;
        // drift back if near edges
        if(p.x < -20) p.x = width+20;
        if(p.x > width+20) p.x = -20;
        if(p.y < -20) p.y = height+20;
        if(p.y > height+20) p.y = -20;

        // mouse attraction
        const mdx = p.x - mouse.x, mdy = p.y - mouse.y;
        const md = Math.sqrt(mdx*mdx+mdy*mdy);
        if(md < 120){
          p.x += (mdx / md) * 0.6;
          p.y += (mdy / md) * 0.6;
        }

        ctx.beginPath();
        const gradient = ctx.createRadialGradient(p.x,p.y,0,p.x,p.y,p.r*6);
        gradient.addColorStop(0, 'rgba(0,224,255,0.9)');
        gradient.addColorStop(0.5, 'rgba(123,60,255,0.15)');
        gradient.addColorStop(1, 'rgba(0,0,0,0)');
        ctx.fillStyle = gradient;
        ctx.arc(p.x,p.y,p.r*3,0,Math.PI*2);
        ctx.fill();
      }

      requestAnimationFrame(step);
    }
    requestAnimationFrame(step);
  })();

  // small UX: close cart on outside click
  document.addEventListener('click', (e)=>{
    const modal = document.getElementById('cartModal');
    if(modal.style.display === 'flex'){
      if(!modal.contains(e.target) && !e.target.closest('#openCart')) {
        modal.style.display = 'none';
      }
    }
  });

  // helpful console logs for customizing
  console.log('Site ready — replace VIDEO_ID_* with your YouTube video IDs in the Videos section. Replace product images & prices in the `products` array in the script.');

</script>

</body>
</html>
