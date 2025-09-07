# my-website-<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Charity: Water – Lead the Future</title>
  <meta name="theme-color" content="#77A8BB" />

  <style>
    :root{
      /* requested palette */
      --primary-color: #77A8BB;
      --accent-color: #FED8C1;
      --dark-color: #BF6C46;
      --light-bg: #f9f9f9;

      /* supporting tokens */
      --muted: #55646a;
      --radius: 12px;
      --shadow-strong: 0 18px 48px rgba(17,24,28,0.12);
      --shadow-soft: 0 8px 28px rgba(17,24,28,0.06);
      --max-content-width: 1100px;
      --glass: rgba(255,255,255,0.9);

      /* button sizing tokens */
      --btn-min-touch: 44px;      /* recommended touch target */
      --btn-min-width: 140px;    /* comfortable min width on desktop */
      --btn-gap: .85rem;
    }

    /* Reset / base */
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      font-family:Inter, "Proxima Nova", "Helvetica Neue", Arial, sans-serif;
      line-height:1.6;
      background: var(--light-bg);
      color: var(--dark-color);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
    }

    /* Accessibility */
    .skip-link{
      position:absolute;left:-999px;top:auto;width:1px;height:1px;overflow:hidden;
    }
    .skip-link:focus{
      left:1rem;top:1rem;width:auto;height:auto;padding:.5rem .75rem;background:#fff;border-radius:6px;box-shadow:var(--shadow-soft);color:var(--primary-color);z-index:9999;
    }
    :focus-visible{ outline: 3px solid rgba(119,168,187,0.22); outline-offset:3px; border-radius:8px; }

    /* Header */
    header{
      position:sticky;
      top:0;
      background: linear-gradient(180deg, rgba(255,255,255,0.95), rgba(255,255,255,0.9));
      padding:1rem 1.25rem;
      box-shadow:var(--shadow-soft);
      z-index:1000;
    }
    .header-inner{
      width:100%;
      max-width:var(--max-content-width);
      margin:0 auto;
      padding:0 1.25rem;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:.5rem;
    }
    .logo{
      font-weight:800;
      font-size:1.25rem;
      color:var(--primary-color);
      letter-spacing:0.2px;
    }
    nav{ display:flex; gap:.75rem; align-items:center; justify-content:flex-end; flex:1 1 auto; }
    nav a{
      text-decoration:none;
      color:var(--dark-color);
      font-weight:700;
      padding:.45rem .6rem;
      border-radius:10px;
      transition: transform .16s ease, background .18s ease, color .18s ease;
    }
    nav a:hover, nav a:focus{
      transform: translateY(-2px);
      color: white;
      background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
      box-shadow: 0 12px 30px rgba(119,168,187,0.12);
    }

    .container{ width:100%; max-width:var(--max-content-width); margin:0 auto; padding:0 1.25rem; }

    /* HERO */
    .hero{
      padding:5rem 0;
      display:flex;
      align-items:center;
      justify-content:center;
      background:
        radial-gradient(800px 360px at 8% 12%, rgba(119,168,187,0.06), transparent 12%),
        radial-gradient(700px 300px at 92% 88%, rgba(254,216,193,0.045), transparent 12%),
        var(--light-bg);
    }

    .hero-card{
      width:100%;
      max-width:1100px;
      background: linear-gradient(180deg, var(--glass), rgba(255,255,255,0.95));
      border-radius: var(--radius);
      box-shadow: var(--shadow-strong);
      padding:2.25rem;
      display:grid;
      grid-template-columns: 1fr 420px;
      gap:1.5rem;
      align-items:center;
      overflow:visible;
    }

    .hero-content h1{
      font-size: clamp(1.9rem, 4.2vw, 3rem);
      line-height:1.02;
      font-weight:900;
      margin-bottom:.5rem;
      /* gradient clipped text using same palette */
      background: linear-gradient(90deg, #5aa6b6 0%, var(--primary-color) 45%, var(--accent-color) 100%);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 0 10px 30px rgba(119,168,187,0.06);
    }

    .hero-underline{
      width:72px;height:8px;border-radius:8px;
      background: linear-gradient(90deg, rgba(119,168,187,0.95), rgba(254,216,193,0.95));
      margin-top:.9rem;margin-bottom:1rem;
      box-shadow: 0 10px 30px rgba(119,168,187,0.06);
      transform-origin:left center;
      animation: grow 700ms cubic-bezier(.2,.9,.2,1) both;
    }
    @keyframes grow{ from{ transform:scaleX(0); opacity:0 } to{ transform:scaleX(1); opacity:1 } }

    .hero-content p{
      font-size:1.05rem;
      color:var(--muted);
      margin-bottom:1.25rem;
      max-width:44rem;
    }

    /*
      Responsive buttons
      - Desktop: buttons have a comfortable min width and sit inline
      - Medium screens: buttons flex and can shrink
      - Small screens: buttons stack and stretch to full width for easy tapping
    */
    .cta-buttons{
      display:flex;
      gap: var(--btn-gap);
      flex-wrap:wrap;
      align-items:center;
    }

    .btn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      padding: calc(var(--btn-min-touch) / 3) 1.05rem;
      border-radius:12px;
      font-weight:800;
      cursor:pointer;
      border:none;
      transition: transform .16s ease, box-shadow .18s ease;
      box-shadow: 0 8px 28px rgba(17,24,28,0.06);
      min-width: var(--btn-min-width);
      min-height: var(--btn-min-touch);
      gap: .5rem;
      white-space:nowrap;
      flex: 0 1 auto; /* allow shrinking on narrower widths */
    }

    .btn-primary{
      background: linear-gradient(90deg, var(--accent-color), #ffe7cf);
      color: var(--dark-color);
    }
    .btn-primary:hover{ transform: translateY(-3px); box-shadow: 0 20px 60px rgba(191,108,70,0.12) }
    .btn-primary:focus{ box-shadow: 0 0 0 6px rgba(191,108,70,0.08); outline:none; }

    .btn-secondary{
      background: linear-gradient(90deg, rgba(119,168,187,0.12), rgba(119,168,187,0.06));
      color: var(--primary-color);
    }
    .btn-secondary:hover{ transform: translateY(-3px); box-shadow: 0 20px 50px rgba(119,168,187,0.08); }

    /*
      Make CTA buttons fluid on small screens:
      - Buttons become flex:1 1 0 so they'll share a row evenly
      - Under 560px we'll stack them vertically and stretch full width
    */
    @media (max-width:900px){
      .btn{ min-width: 120px; padding: .6rem 1rem; }
      .cta-buttons { gap: .6rem; }
    }

    @media (max-width:560px){
      .cta-buttons{
        flex-direction:column;
        align-items:stretch;
      }
      .btn{
        flex: 1 1 auto;
        width:100%;
        min-width: 0;
        padding: .9rem 1rem;
      }
      /* make secondary subdued but full width too */
      .btn-secondary{ order: 2; }
      .btn-primary{ order: 1; }
    }

    /* hero media */
    .hero-media{ display:flex; align-items:center; justify-content:center; position:relative; }
    .hero-media img{
      width:100%; height:auto; border-radius:12px; display:block;
      box-shadow: 0 24px 64px rgba(17,24,28,0.10);
      filter: saturate(1.08) contrast(1.05) brightness(1.02);
      transition: transform .36s ease, filter .2s ease;
    }
    .hero-media img:hover{ transform: translateY(-6px) scale(1.02); filter: saturate(1.12) contrast(1.07) }

    /* Content section */
    section.content{ padding:3rem 0; }
    .content-text{ display:block; max-width:860px; margin:0 auto; padding:0 1.25rem; text-align:center; }
    .content-text h2{ margin-bottom:.6rem; color:var(--primary-color); font-weight:800; font-size:1.35rem; }
    .content-text p{ color:var(--muted); font-size:1.05rem; line-height:1.65; }

    /* Donate card and amount buttons responsiveness */
    .donate{ padding:2rem; background: linear-gradient(180deg, white, #fffaf7); border-radius:12px; box-shadow:var(--shadow-soft); margin-top:1.5rem; }
    .donate-form{ display:grid; gap:.75rem; max-width:640px; margin-top:.5rem; }

    .amounts{
      display:flex;
      gap:.5rem;
      flex-wrap:wrap;
      align-items:center;
    }
    .amount-btn{
      padding:.45rem .75rem;
      border-radius:10px;
      background:#fff;
      border:1px solid #eee;
      min-height: var(--btn-min-touch);
      cursor:pointer;
      flex: 0 1 auto;
    }
    .amount-btn.selected{
      background: linear-gradient(90deg, var(--accent-color), #ffe7cf);
      color: var(--dark-color);
    }
    /* On small screens make the custom input and amount buttons more comfortable */
    @media (max-width:560px){
      .amounts{ gap:.5rem; justify-content:center; }
      .amount-btn{ flex: 1 1 28%; min-width: 0; }
      #amount-custom{ flex: 1 1 32%; min-width: 0; width: auto; }
      .donate-form{ gap:.6rem; }
    }

    /* Footer */
    footer{ background: linear-gradient(90deg,#6e4f3a,#4e382d); color:white; text-align:center; padding:2rem 0; margin-top:2rem; }

    /* Responsive layout adjustments below 980px */
    @media (max-width:980px){
      .header-inner{ flex-direction:column; align-items:center; gap:.5rem; }
      nav{ width:100%; justify-content:center; gap:.5rem; flex-wrap:wrap; }
      .hero-card{ grid-template-columns:1fr; padding:1.5rem; gap:1rem; }
      .hero-media{ order:-1; margin-bottom:.75rem; }
      .hero-content h1{ font-size: clamp(1.6rem, 5vw, 2.2rem); }
      .content-text{ padding:0 1rem; text-align:center; }
    }

    @media (prefers-reduced-motion: reduce){
      *{ animation:none!important; transition:none!important; scroll-behavior:auto!important; }
    }
  </style>
</head>
<body>
  <a href="#main" class="skip-link">Skip to content</a>

  <header role="banner" aria-label="Site header">
    <div class="header-inner">
      <div class="logo">Charity: Water</div>

      <nav role="navigation" aria-label="Main Navigation">
        <a href="#about">About</a>
        <a href="#projects">Projects</a>
        <a href="#involved">Get Involved</a>
        <a href="#donate">Donate</a>
      </nav>
    </div>
  </header>

  <main id="main" class="hero" role="main">
    <div class="hero-card container" aria-labelledby="hero-heading">
      <div class="hero-content">
        <h1 id="hero-heading">Lead the Future. Start with Clean Water</h1>
        <div class="hero-underline" aria-hidden="true"></div>

        <p>Support clean water today — it's the foundation for health, learning, and leadership. Your contributions help create resilient communities and inspire tomorrow's leaders.</p>

        <div class="cta-buttons" role="group" aria-label="Primary calls to action">
          <a href="#donate" class="btn btn-primary" role="button">Donate now</a>
          <a href="#projects" class="btn btn-secondary" role="button">See our work</a>
        </div>
      </div>

      <div class="hero-media" aria-hidden="false">
        <picture>
          <source type="image/webp"
            srcset="assets/two-glasses-water-320.webp 320w, assets/two-glasses-water-640.webp 640w, assets/two-glasses-water-1200.webp 1200w"
            sizes="(max-width:980px) 90vw, 420px">
          <source type="image/jpeg"
            srcset="assets/two-glasses-water-320.jpg 320w, assets/two-glasses-water-640.jpg 640w, assets/two-glasses-water-1200.jpg 1200w"
            sizes="(max-width:980px) 90vw, 420px">
          <img src="assets/two-glasses-water-640.jpg"
               alt="Two small glasses on a wooden surface; the left glass contains cloudy water and the right glass contains clear water, illustrating clean vs. contaminated water."
               loading="eager" width="420" height="320">
        </picture>
      </div>
    </div>
  </main>

  <section id="about" class="content">
    <div class="content-text container" aria-labelledby="why-heading">
      <h2 id="why-heading">Why Clean Water Matters</h2>
      <p>Clean water is the foundation of health, education, and opportunity. When communities gain access to safe water, children stay in school, families prosper, and leaders emerge. Every contribution builds both a better world and stronger leaders for the future.</p>
    </div>

    <div id="donate" class="donate container" aria-labelledby="donate-heading" style="margin-top:2rem">
      <h3 id="donate-heading">Donate — support clean water</h3>
      <p class="lead">Choose an amount and frequency. For production, integrate Stripe/PayPal or your preferred payment provider. This demo shows a lightweight client-side flow and analytics hooks.</p>

      <form id="donate-form" class="donate-form" action="/donate" method="POST" aria-describedby="donate-note" novalidate>
        <div>
          <label for="donor-email">Email</label><br />
          <input id="donor-email" name="email" type="email" autocomplete="email" required placeholder="you@example.com" style="padding:.6rem .7rem;border-radius:8px;border:1px solid #e6e6e6;width:100%" />
        </div>

        <div>
          <label>Amount</label>
          <div class="amounts" role="radiogroup" aria-label="Donation amounts" style="margin-top:.5rem">
            <button type="button" class="amount-btn" data-amount="10" aria-pressed="false">$10</button>
            <button type="button" class="amount-btn" data-amount="25" aria-pressed="false">$25</button>
            <button type="button" class="amount-btn" data-amount="50" aria-pressed="false">$50</button>
            <button type="button" class="amount-btn" data-amount="100" aria-pressed="false">$100</button>
            <input aria-label="Custom amount" id="amount-custom" name="amount" type="number" min="1" placeholder="Custom" style="width:120px;padding:.5rem;border-radius:8px;border:1px solid #e6e6e6" />
          </div>
        </div>

        <div style="margin-top:.5rem">
          <label for="frequency">Frequency</label><br />
          <select id="frequency" name="frequency" aria-label="Donation frequency" style="padding:.6rem .7rem;border-radius:8px;border:1px solid #e6e6e6">
            <option value="one_time">One-time</option>
            <option value="monthly">Monthly</option>
          </select>
        </div>

        <div class="donate-actions" style="display:flex;gap:.75rem;align-items:center;margin-top:.75rem;flex-wrap:wrap">
          <button id="donate-submit" type="submit" class="btn btn-primary" aria-live="polite" style="min-width:160px">Donate now</button>
          <div id="donate-status" class="msg" role="status" aria-live="polite" style="color:var(--muted)"></div>
        </div>

        <p id="donate-note" style="font-size:.85rem;color:#666;margin-top:.5rem">Security note: This demo form does not process cards. Replace the client handling with your payment provider's secure integration (Stripe Elements, Stripe Checkout, PayPal, etc.).</p>
      </form>
    </div>
  </section>

  <footer role="contentinfo">
    <div class="container">
      <p>© 2025 Charity: Water – All rights reserved.</p>
      <p style="font-size:.9rem;opacity:.95">Made with care · Accessible · Responsive</p>
    </div>
  </footer>

  <script>
    // Simple amount button interactions and responsive niceties.
    (function(){
      const amountButtons = Array.from(document.querySelectorAll('.amount-btn'));
      const amountCustom = document.getElementById('amount-custom');

      function clearSelected(){
        amountButtons.forEach(b => {
          b.classList.remove('selected');
          b.setAttribute('aria-pressed','false');
          b.style.background = '';
          b.style.color = '';
        });
      }
      amountButtons.forEach(btn => {
        btn.addEventListener('click', () => {
          clearSelected();
          btn.classList.add('selected');
          btn.setAttribute('aria-pressed','true');
          // use the palette gradient for selected state
          btn.style.background = 'linear-gradient(90deg, var(--accent-color), #ffe7cf)';
          btn.style.color = 'var(--dark-color)';
          amountCustom.value = btn.getAttribute('data-amount');
        });
      });

      // Respect prefers-reduced-motion: avoid tilt animations
      const prefersReduced = window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches;
      const imgWrap = document.querySelector('.hero-media');
      const img = imgWrap ? imgWrap.querySelector('img') : null;
      if (img && !prefersReduced) {
        imgWrap.addEventListener('pointermove', (e) => {
          const rect = imgWrap.getBoundingClientRect();
          const cx = rect.left + rect.width/2;
          const cy = rect.top + rect.height/2;
          const dx = e.clientX - cx;
          const dy = e.clientY - cy;
          const rx = (dy / rect.height) * 6; // rotateX
          const ry = -(dx / rect.width) * 6;  // rotateY
          img.style.transform = `perspective(900px) rotateX(${rx}deg) rotateY(${ry}deg) translateZ(6px)`;
        });
        imgWrap.addEventListener('pointerleave', () => { img.style.transform = ''; });
      }
    })();
  </script>
</body>
</html>
