<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#f5f2e9">
  <title>Urban Brew Café — Coffee, at your own pace</title>
  <style>
    :root {
      color-scheme: light;
      --ink: #20362e;
      --muted: #6f786e;
      --paper: #f5f2e9;
      --card: #fffdf8;
      --green: #28483b;
      --green-dark: #1d352c;
      --line: #e8e3d8;
      --accent: #bd8054;
      --serif: Georgia, "Times New Roman", serif;
      --sans: "Segoe UI", -apple-system, BlinkMacSystemFont, Roboto, sans-serif;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      background: var(--paper);
      color: var(--ink);
      font-family: var(--sans);
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    a { color: inherit; }
    .page-shell { width: min(1120px, calc(100% - 64px)); margin: 0 auto; }

    .topbar {
      min-height: 86px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid rgba(32, 54, 46, .13);
    }
    .brand {
      display: inline-flex;
      align-items: center;
      gap: 12px;
      color: var(--ink);
      font-family: var(--serif);
      font-size: 1.16rem;
      font-weight: 700;
      letter-spacing: -.03em;
      text-decoration: none;
    }
    .brand-mark {
      width: 34px;
      height: 34px;
      display: grid;
      place-items: center;
      border: 1px solid rgba(40, 72, 59, .25);
      border-radius: 50%;
      color: var(--green);
    }
    .brand-mark svg { width: 18px; height: 18px; }
    .nav-links { display: flex; align-items: center; gap: 34px; }
    .nav-links a {
      color: #535e55;
      font-size: .79rem;
      font-weight: 600;
      letter-spacing: .06em;
      text-decoration: none;
      text-transform: uppercase;
      transition: color .2s ease;
    }
    .nav-links a:hover { color: var(--accent); }
    .nav-links .nav-visit {
      padding: 11px 18px;
      border: 1px solid rgba(32, 54, 46, .35);
      border-radius: 3px;
      color: var(--ink);
    }
    .nav-links .nav-visit:hover { border-color: var(--green); color: var(--green); }

    .hero {
      min-height: 440px;
      display: grid;
      grid-template-columns: 1.08fr .92fr;
      align-items: center;
      gap: 56px;
      padding: 58px 0 62px;
    }
    .eyebrow {
      display: flex;
      align-items: center;
      gap: 10px;
      margin: 0 0 19px;
      color: #876442;
      font-size: .7rem;
      font-weight: 700;
      letter-spacing: .18em;
      text-transform: uppercase;
    }
    .eyebrow::before { width: 25px; height: 1px; background: var(--accent); content: ""; }
    h1, h2, p { margin-top: 0; }
    h1 {
      max-width: 560px;
      margin-bottom: 21px;
      color: var(--green-dark);
      font-family: var(--serif);
      font-size: clamp(3.2rem, 6.6vw, 5.55rem);
      font-weight: 400;
      letter-spacing: -.065em;
      line-height: .99;
    }
    h1 em { color: var(--accent); font-weight: 400; }
    .hero-copy {
      max-width: 420px;
      margin-bottom: 29px;
      color: var(--muted);
      font-size: .98rem;
      line-height: 1.8;
    }
    .primary-link {
      display: inline-flex;
      align-items: center;
      gap: 14px;
      min-height: 48px;
      padding: 0 19px;
      background: var(--green);
      border-radius: 3px;
      color: #fffdf8;
      font-size: .76rem;
      font-weight: 700;
      letter-spacing: .08em;
      text-decoration: none;
      text-transform: uppercase;
      transition: background .2s ease, transform .2s ease;
    }
    .primary-link:hover { background: var(--green-dark); transform: translateY(-2px); }
    .primary-link svg { width: 15px; height: 15px; }

    .hero-art {
      position: relative;
      min-height: 330px;
      overflow: hidden;
      display: grid;
      place-items: center;
      background:
        radial-gradient(ellipse at 68% 32%, rgba(219, 174, 124, .62), transparent 34%),
        radial-gradient(ellipse at 27% 82%, rgba(110, 132, 105, .68), transparent 40%),
        linear-gradient(140deg, #d9c8a9, #b5a27e 48%, #687b69);
      border-radius: 47% 47% 3px 3px / 39% 39% 3px 3px;
    }
    .hero-art::before, .hero-art::after {
      position: absolute;
      border: 1px solid rgba(255, 253, 248, .42);
      border-radius: 50%;
      content: "";
    }
    .hero-art::before { width: 275px; height: 275px; }
    .hero-art::after { width: 220px; height: 220px; }
    .cup {
      position: relative;
      z-index: 1;
      width: 146px;
      height: 112px;
      margin-top: 25px;
      border-radius: 8px 8px 48px 48px;
      background: linear-gradient(100deg, #fffdf8, #e9e1d1);
      box-shadow: 15px 19px 35px rgba(36, 44, 34, .2);
      transform: rotate(-8deg);
    }
    .cup::before {
      position: absolute;
      top: 16px;
      right: -39px;
      width: 45px;
      height: 51px;
      border: 10px solid #eee7d9;
      border-left: 0;
      border-radius: 0 50% 50% 0;
      content: "";
    }
    .cup::after {
      position: absolute;
      top: 8px;
      left: 0;
      width: 100%;
      height: 16px;
      border-radius: 50%;
      background: #593c2b;
      box-shadow: 0 3px 0 rgba(85, 57, 40, .15);
      content: "";
    }
    .art-caption {
      position: absolute;
      right: 22px;
      bottom: 20px;
      z-index: 1;
      color: rgba(255, 253, 248, .92);
      font-family: var(--serif);
      font-size: .9rem;
      font-style: italic;
    }

    .details {
      display: grid;
      grid-template-columns: 1.15fr .85fr;
      gap: 70px;
      padding: 42px 0 70px;
      border-top: 1px solid rgba(32, 54, 46, .13);
    }
    .section-label {
      margin-bottom: 9px;
      color: #987452;
      font-size: .66rem;
      font-weight: 700;
      letter-spacing: .17em;
      text-transform: uppercase;
    }
    h2 {
      margin-bottom: 22px;
      color: var(--green-dark);
      font-family: var(--serif);
      font-size: 2rem;
      font-weight: 400;
      letter-spacing: -.04em;
      line-height: 1.15;
    }
    .menu-list { margin: 0; padding: 0; border-top: 1px solid var(--line); list-style: none; }
    .menu-item {
      min-height: 66px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      border-bottom: 1px solid var(--line);
    }
    .menu-item span:first-child { font-family: var(--serif); font-size: 1.08rem; }
    .price { color: #866344; font-size: .88rem; font-weight: 600; }

    .visit-card {
      align-self: start;
      padding: 29px 30px 27px;
      background: var(--green);
      color: #f8f4eb;
      border-radius: 3px;
    }
    .visit-card .section-label { color: #d7b18b; }
    .visit-card h2 { margin-bottom: 23px; color: #fffaf0; }
    .visit-row {
      display: grid;
      grid-template-columns: 76px 1fr;
      gap: 12px;
      padding: 13px 0;
      border-top: 1px solid rgba(255, 250, 240, .2);
      font-size: .84rem;
    }
    .visit-row strong {
      color: #d7b18b;
      font-size: .68rem;
      letter-spacing: .11em;
      text-transform: uppercase;
    }
    .visit-row span { color: rgba(255, 250, 240, .88); }
    footer {
      display: flex;
      justify-content: space-between;
      gap: 20px;
      padding: 22px 0 27px;
      border-top: 1px solid rgba(32, 54, 46, .13);
      color: var(--muted);
      font-size: .72rem;
    }
    footer p { margin: 0; }
    footer .footer-note { color: #8a7259; font-family: var(--serif); font-style: italic; }

    @media (max-width: 720px) {
      .page-shell { width: min(100% - 40px, 560px); }
      .topbar { min-height: 72px; }
      .nav-links { gap: 18px; }
      .nav-links a { font-size: .68rem; }
      .nav-links .nav-visit { padding: 9px 12px; }
      .hero { min-height: 0; grid-template-columns: 1fr; gap: 35px; padding: 56px 0 45px; }
      h1 { max-width: 540px; font-size: clamp(3.4rem, 12vw, 5rem); }
      .hero-art { min-height: 290px; }
      .details { grid-template-columns: 1fr; gap: 38px; padding: 34px 0 48px; }
      .visit-card { max-width: none; }
    }
    @media (max-width: 420px) {
      .page-shell { width: calc(100% - 32px); }
      .brand { gap: 8px; font-size: 1rem; }
      .brand-mark { width: 30px; height: 30px; }
      .nav-links { gap: 12px; }
      .nav-links a { font-size: .62rem; letter-spacing: .035em; }
      .nav-links .nav-visit { padding: 8px 9px; }
      .hero { padding-top: 44px; }
      .hero-art { min-height: 245px; }
      .cup { transform: scale(.82) rotate(-8deg); }
      .details { gap: 30px; }
      .visit-card { padding: 25px 22px; }
      footer { flex-direction: column; gap: 5px; }
    }
    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }
      *, *::before, *::after { transition-duration: .01ms !important; }
    }
  </style>
</head>
<body>
  <div class="page-shell">
    <header class="topbar">
      <a class="brand" href="#" aria-label="Urban Brew Café home">
        <span class="brand-mark" aria-hidden="true">
          <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 3.5c4.4 0 7.5 3.3 7.5 7.8 0 5.3-3.8 9.2-8.2 9.2-3.8 0-6.8-3.2-6.8-7.5 0-5.3 3.2-9.5 7.5-9.5Z" stroke="currentColor" stroke-width="1.5"/>
            <path d="M15.9 5.4c-4.1 3.3-6.6 7.7-7.4 13" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          </svg>
        </span>
        Urban Brew Café
      </a>
      <nav class="nav-links" aria-label="Main navigation">
        <a href="#menu">Menu</a>
        <a class="nav-visit" href="#visit">Find us</a>
      </nav>
    </header>

    <main>
      <section class="hero" aria-labelledby="hero-title">
        <div>
          <p class="eyebrow">Coffee, at your own pace</p>
          <h1 id="hero-title">A little pause.<br>A <em>better</em> day.</h1>
          <p class="hero-copy">Freshly brewed coffee and handmade pastries daily. Find your favorite corner, settle in, and stay a while.</p>
          <a class="primary-link" href="#menu">
            Explore the menu
            <svg viewBox="0 0 20 20" fill="none" aria-hidden="true">
              <path d="M3.5 10h12m-5-5 5 5-5 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
        </div>
        <div class="hero-art" role="img" aria-label="Illustration of a warm cup of coffee">
          <div class="cup" aria-hidden="true"></div>
          <span class="art-caption">Made for slow mornings</span>
        </div>
      </section>

      <div class="details">
        <section id="menu" aria-labelledby="menu-title">
          <p class="section-label">A few favorites</p>
          <h2 id="menu-title">On the menu</h2>
          <ul class="menu-list">
            <li class="menu-item"><span>Espresso</span><span class="price">$3.50</span></li>
            <li class="menu-item"><span>Cold Brew</span><span class="price">$4.50</span></li>
            <li class="menu-item"><span>Avocado Toast</span><span class="price">$7.00</span></li>
          </ul>
        </section>

        <section class="visit-card" id="visit" aria-labelledby="visit-title">
          <p class="section-label">Come on in</p>
          <h2 id="visit-title">Make yourself at home.</h2>
          <div class="visit-row">
            <strong>Find us</strong>
            <span>123 Main Street</span>
          </div>
          <div class="visit-row">
            <strong>Hours</strong>
            <span>Open daily<br>7:00 AM – 6:00 PM</span>
          </div>
        </section>
      </div>
    </main>

    <footer>
      <p>© 2026 Urban Brew Café. All rights reserved.</p>
      <p class="footer-note">Freshly brewed, always.</p>
    </footer>
  </div>
</body>
</html>
