# Custom-liquid-block---Featured-product-crousel
custom liquid code for the featured crousel section - with bg color and and in bottom - layered 


<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;1,400&family=Jost:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
/* full-bleed breakout */
.jfs { font-family:'Jost',sans-serif; width:100vw; max-width:100vw; margin-left:calc(50% - 50vw); overflow-x:hidden; }
.jfs * { box-sizing:border-box; margin:0; padding:0; }

/* NEW ARRIVALS */
.jfs-na {
  background:#ffc152; padding:64px 0 0;
  position:relative; overflow:hidden;
}
.jfs-na-orb {
  position:absolute; width:600px; height:600px; border-radius:50%;
  background:radial-gradient(circle,rgba(255,255,255,0.18) 0%,transparent 65%);
  top:-200px; right:-150px; pointer-events:none;
}
.jfs-na-header {
  padding:0 max(64px, calc(50vw - 800px)); display:flex; align-items:flex-end;
  justify-content:space-between; gap:24px; margin-bottom:32px; position:relative; z-index:2;
}
.jfs-eyebrow-na {
  font-size:10px; font-weight:700; letter-spacing:0.28em; text-transform:uppercase;
  color:rgba(0,0,0,0.45); display:flex; align-items:center; gap:10px; margin-bottom:12px;
}
.jfs-eyebrow-na::before { content:''; width:20px; height:1px; background:rgba(0,0,0,0.3); display:block; }
.jfs-na-title { font-family:'Playfair Display',serif; font-size:clamp(28px,3.5vw,52px); font-weight:400; color:#1a1a1a; line-height:1.1; }
.jfs-na-title em { font-style:italic; color:#fff; }
.jfs-na-sub { font-size:13px; color:rgba(0,0,0,0.5); line-height:1.8; margin-top:8px; }
.jfs-btn-na {
  flex-shrink:0; display:inline-flex; align-items:center; gap:8px;
  font-size:10px; font-weight:700; letter-spacing:0.16em; text-transform:uppercase;
  color:#fff !important; background:#3c6447; text-decoration:none !important;
  padding:13px 28px; border-radius:2px; white-space:nowrap; transition:background 0.2s;
}
.jfs-btn-na:hover { background:#2e4e36; }
.jfs-btn-na svg { width:11px; height:11px; }

/* BEST SELLERS */
.jfs-bs {
  background:#fffbf5; padding:24px 0 64px;
  position:relative; overflow:hidden;
}
.jfs-bs-orb {
  position:absolute; width:500px; height:500px; border-radius:50%;
  background:radial-gradient(circle,rgba(255,193,82,0.1) 0%,transparent 65%);
  bottom:-160px; right:-100px; pointer-events:none;
}
.jfs-bs-header {
  padding:0 max(64px, calc(50vw - 800px)); display:flex; align-items:flex-end;
  justify-content:space-between; gap:24px; margin-bottom:32px; position:relative; z-index:2;
}
.jfs-eyebrow-bs {
  font-size:10px; font-weight:700; letter-spacing:0.28em; text-transform:uppercase;
  color:#3c6447; display:flex; align-items:center; gap:10px; margin-bottom:12px;
}
.jfs-eyebrow-bs::before { content:''; width:20px; height:1px; background:#3c6447; display:block; }
.jfs-bs-title { font-family:'Playfair Display',serif; font-size:clamp(28px,3.5vw,52px); font-weight:400; color:#1a1a1a; line-height:1.1; }
.jfs-bs-title em { font-style:italic; color:#3c6447; }
.jfs-bs-sub { font-size:13px; font-weight:300; color:#9a8878; line-height:1.8; margin-top:8px; }
.jfs-btn-bs {
  flex-shrink:0; display:inline-flex; align-items:center; gap:8px;
  font-size:10px; font-weight:700; letter-spacing:0.16em; text-transform:uppercase;
  color:#1a1a1a !important; background:#ffc152; text-decoration:none !important;
  padding:13px 28px; border-radius:2px; white-space:nowrap; transition:background 0.2s;
}
.jfs-btn-bs:hover { background:#f0b040; }
.jfs-btn-bs svg { width:11px; height:11px; }

/* STRIP */
.jfs-strip-wrap { position:relative; z-index:2; overflow:hidden; }
.jfs-strip-wrap::before, .jfs-strip-wrap::after {
  content:''; position:absolute; top:0; bottom:0; width:64px; z-index:3; pointer-events:none;
}
.jfs-na .jfs-strip-wrap::before { left:0; background:linear-gradient(to right,#ffc152,transparent); }
.jfs-na .jfs-strip-wrap::after  { right:0; background:linear-gradient(to left,#ffc152,transparent); }
.jfs-bs .jfs-strip-wrap::before { left:0; background:linear-gradient(to right,#fffbf5,transparent); }
.jfs-bs .jfs-strip-wrap::after  { right:0; background:linear-gradient(to left,#fffbf5,transparent); }

.jfs-strip {
  display:flex; gap:16px; overflow-x:auto; overflow-y:visible;
  -webkit-overflow-scrolling:touch; scrollbar-width:none; padding:4px max(64px, calc(50vw - 800px)) 20px;
}
.jfs-na .jfs-strip { padding-bottom:88px; }
.jfs-strip::-webkit-scrollbar { display:none; }

/* CARD — matches Impact theme card style */
.jfs-card {
  flex-shrink:0; width:220px;
  text-decoration:none !important; color:inherit !important; display:block;
}
.jfs-img-wrap {
  position:relative; overflow:hidden; border-radius:4px;
  aspect-ratio:3/4; background:#f0ebe3; margin-bottom:12px;
  transition:box-shadow 0.3s ease;
}
.jfs-na .jfs-img-wrap { background:rgba(0,0,0,0.08); }
.jfs-card:hover .jfs-img-wrap { box-shadow:0 8px 28px rgba(0,0,0,0.12); }
.jfs-img { width:100%; height:100%; object-fit:cover; object-position:top; display:block; transition:transform 0.5s ease; }
.jfs-card:hover .jfs-img { transform:scale(1.03); }

/* Badge bottom of image — not covering face */
.jfs-badge {
  position:absolute; bottom:10px; left:10px; z-index:2;
  font-size:9px; font-weight:700; letter-spacing:0.1em; text-transform:uppercase;
  padding:4px 8px; border-radius:2px;
}
.jfs-na .jfs-badge { background:rgba(0,0,0,0.55); color:#fff; }
.jfs-bs .jfs-badge { background:#ffc152; color:#1a1a1a; }
.jfs-badge-sale { background:#3c6447 !important; color:#fff !important; }

/* Title — matches Impact exactly: Jost, 14px, normal weight, dark */
.jfs-title {
  display:block; font-family:'Jost',sans-serif;
  font-size:14px; font-weight:400; color:#1a1a1a;
  line-height:1.4; margin-bottom:4px;
  text-decoration:none !important;
}
/* Price — matches Impact: 14px, regular weight */
.jfs-price { font-family:'Jost',sans-serif; font-size:14px; color:#1a1a1a; }
.jfs-compare { font-size:13px; color:#9a8878; text-decoration:line-through; margin-right:5px; }
.jfs-current { color:#1a1a1a; }
.jfs-sale-price { color:#1a1a1a; }

/* Target the actual custom element the snippet outputs — fixed width so cards never sprawl on wide screens */
.jfs-strip product-card {
  flex-shrink:0 !important;
  width:260px !important;
  min-width:260px !important;
  max-width:260px !important;
  display:block !important;
}
/* Also target any wrapper around it */
.jfs-strip > *,
.jfs-strip .card-wrapper,
.jfs-strip .product-card-wrapper,
.jfs-strip li {
  flex-shrink:0 !important;
  width:260px !important;
  min-width:260px !important;
  max-width:260px !important;
  list-style:none !important;
  padding:0 !important;
}

/* WAVE */
.jfs-wave { display:block; line-height:0; margin-top:-2px; }

@media (max-width:768px) {
  .jfs-na { padding:44px 0 0; }
  .jfs-bs { padding:16px 0 48px; }
  .jfs-na-header, .jfs-bs-header { padding:0 16px; flex-direction:column; align-items:flex-start; gap:14px; margin-bottom:20px; }
  .jfs-strip { padding:4px 16px 16px; gap:10px; }
  .jfs-na .jfs-strip { padding-bottom:52px; }
  .jfs-strip-wrap::before, .jfs-strip-wrap::after { width:16px; }
  .jfs-card { width:calc((100vw - 54px) / 3); min-width:96px; }
  .jfs-strip product-card,
  .jfs-strip > *,
  .jfs-strip .card-wrapper,
  .jfs-strip .product-card-wrapper,
  .jfs-strip li {
    width:calc((100vw - 48px) / 2.3) !important;
    min-width:calc((100vw - 48px) / 2.3) !important;
    max-width:calc((100vw - 48px) / 2.3) !important;
  }
  .jfs-na-title, .jfs-bs-title { font-size:24px; }
  .jfs-btn-na, .jfs-btn-bs { padding:10px 16px; font-size:9px; }
  .jfs-title { font-size:11px; }
  .jfs-price { font-size:12px; }
}
</style>

<div class="jfs">

<section class="jfs-na">
  <div class="jfs-na-orb"></div>
  <div class="jfs-na-header">
    <div>
      <div class="jfs-eyebrow-na">Just dropped</div>
      <h2 class="jfs-na-title">Fresh off the <em>runway.</em></h2>
      <p class="jfs-na-sub">New designs every week — pure cotton, made in Jaipur.</p>
    </div>
    <a href="/collections/new-arrivals" class="jfs-btn-na">
      Shop New Arrivals
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
    </a>
  </div>
  <div class="jfs-strip-wrap">
    <div class="jfs-strip">
      {% assign na_col = collections['new-arrivals'] %}
      {% for product in na_col.products limit: 8 %}
        {% render 'product-card',
          product: product,
          product_card: product,
          show_rating: true,
          media_aspect_ratio: 'portrait',
          stacked: true,
          card_index: forloop.index
        %}
      {% endfor %}
    </div>
  </div>
</section>

<svg class="jfs-wave" viewBox="0 0 1440 80" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none" style="display:block;width:100%;height:80px;">
  <rect width="1440" height="80" fill="#ffc152"/>
  <path d="M0,25 C200,70 400,5 600,38 C800,72 1000,8 1200,40 C1320,60 1400,20 1440,32 L1440,80 L0,80 Z" fill="#fffbf5"/>
</svg>

<section class="jfs-bs">
  <div class="jfs-bs-orb"></div>
  <div class="jfs-bs-header">
    <div>
      <div class="jfs-eyebrow-bs">Customer favourites</div>
      <h2 class="jfs-bs-title">Seasonal <em>favourites.</em></h2>
      <p class="jfs-bs-sub">The pieces women keep coming back for, season after season.</p>
    </div>
    <a href="/collections/best-sellers" class="jfs-btn-bs">
      Shop All
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>
    </a>
  </div>
  <div class="jfs-strip-wrap">
    <div class="jfs-strip">
      {% assign bs_col = collections['best-sellers'] %}
      {% for product in bs_col.products limit: 8 %}
        {% render 'product-card',
          product: product,
          product_card: product,
          show_rating: true,
          media_aspect_ratio: 'portrait',
          stacked: true,
          card_index: forloop.index
        %}
      {% endfor %}
    </div>
  </div>
</section>

</div>

<script>
(function() {
  function fixCards() {
    var isMobile = window.innerWidth <= 768;
    var W = isMobile
      ? Math.floor((window.innerWidth - 48) / 2.3) + 'px'
      : '260px';
    var selectors = '.jfs-strip product-card, .jfs-strip > *';
    document.querySelectorAll(selectors).forEach(function(el) {
      // Remove inline style that the snippet injects (the calc max-width)
      el.style.removeProperty('max-width');
      el.style.removeProperty('width');
      // Now set our values
      el.style.setProperty('flex-shrink', '0', 'important');
      el.style.setProperty('width', W, 'important');
      el.style.setProperty('min-width', W, 'important');
      el.style.setProperty('max-width', W, 'important');
      el.style.setProperty('list-style', 'none', 'important');
    });
  }
  // Run immediately and again after a small delay for any deferred rendering
  fixCards();
  setTimeout(fixCards, 300);
  window.addEventListener('resize', fixCards);
})();
</script>
