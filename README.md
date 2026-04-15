[index.html](https://github.com/user-attachments/files/26763706/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Consumer Insights & Analytics | Carlson School of Management</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Source+Sans+3:wght@300;400;600;700&display=swap" rel="stylesheet" />
  <style>
    :root {
      --maroon: #7b0000;
      --maroon-dark: #5a0000;
      --gold: #f0b90b;
      --gold-light: #f5cc4a;
      --cream: #f5f0e8;
      --white: #ffffff;
      --text-dark: #1a0a0a;
      --text-muted: #6b4545;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Source Sans 3', sans-serif; color: var(--text-dark); background: var(--white); }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 200;
      background: var(--maroon-dark);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 48px; height: 64px;
      box-shadow: 0 2px 16px rgba(0,0,0,0.25);
    }
    .nav-brand {
      font-family: 'Playfair Display', serif;
      color: var(--gold); font-size: 1.1rem; font-weight: 700;
      cursor: pointer; user-select: none; white-space: nowrap;
    }
    .nav-links { display: flex; align-items: center; gap: 4px; }
    .nav-tab {
      color: rgba(240,185,11,0.75); font-size: 0.92rem; font-weight: 600;
      padding: 8px 16px; border-radius: 6px; cursor: pointer;
      transition: color 0.2s, background 0.2s; border: none; background: transparent;
      font-family: 'Source Sans 3', sans-serif;
    }
    .nav-tab:hover { color: var(--gold); background: rgba(255,255,255,0.07); }
    .nav-tab.active { color: var(--gold); background: rgba(255,255,255,0.12); }
    .nav-tab.apply-btn {
      background: var(--gold); color: var(--maroon-dark) !important;
      font-weight: 700; margin-left: 8px;
    }
    .nav-tab.apply-btn:hover { background: var(--gold-light); }
    .nav-tab.apply-btn.active { background: var(--gold-light); color: var(--maroon-dark) !important; }

    /* PAGES */
    .page { display: none; padding-top: 64px; min-height: 100vh; }
    .page.active { display: block; animation: fadeIn 0.35s ease both; }

    @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes fadeUp  { from { opacity: 0; transform: translateY(22px); } to { opacity: 1; transform: translateY(0); } }

    /* ── HOME ── */
    .hero {
      position: relative; height: calc(100vh - 64px);
      display: flex; align-items: center; justify-content: center; text-align: center;
      overflow: hidden;
    }
    .hero-bg {
      position: absolute; inset: 0;
      background: url('https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=1600&q=80') center/cover no-repeat;
    }
    .hero-overlay {
      position: absolute; inset: 0;
      background: linear-gradient(135deg, rgba(90,0,0,0.88) 0%, rgba(123,0,0,0.80) 100%);
    }
    .hero-content { position: relative; z-index: 2; max-width: 760px; padding: 0 24px; }
    .hero-content h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.8rem, 6vw, 4.5rem);
      color: var(--white); line-height: 1.1; margin-bottom: 8px;
      animation: fadeUp 0.7s ease both;
    }
    .hero-content h1 span { color: var(--gold); display: block; }
    .hero-content p {
      font-size: 1.15rem; color: rgba(255,255,255,0.88);
      margin: 24px auto 40px; max-width: 560px; line-height: 1.7;
      animation: fadeUp 0.7s 0.12s ease both;
    }
    .hero-btns { display: flex; gap: 16px; justify-content: center; flex-wrap: wrap; animation: fadeUp 0.7s 0.24s ease both; }
    .btn-gold {
      background: var(--gold); color: var(--maroon-dark);
      padding: 14px 32px; border-radius: 8px; font-weight: 700; font-size: 1rem;
      cursor: pointer; border: none; font-family: 'Source Sans 3', sans-serif;
      transition: background 0.2s, transform 0.2s;
    }
    .btn-gold:hover { background: var(--gold-light); transform: translateY(-2px); }
    .btn-outline {
      background: rgba(255,255,255,0.12); color: var(--white);
      padding: 14px 32px; border-radius: 8px; font-weight: 700; font-size: 1rem;
      cursor: pointer; border: 2px solid rgba(255,255,255,0.55);
      font-family: 'Source Sans 3', sans-serif;
      transition: background 0.2s, transform 0.2s;
    }
    .btn-outline:hover { background: rgba(255,255,255,0.22); transform: translateY(-2px); }

    .why-section { background: var(--cream); padding: 88px 48px; text-align: center; }
    .sec-title { font-family: 'Playfair Display', serif; font-size: clamp(1.9rem, 4vw, 2.7rem); color: var(--maroon-dark); margin-bottom: 12px; }
    .sec-sub { font-size: 1.05rem; color: var(--text-muted); max-width: 540px; margin: 0 auto 52px; line-height: 1.6; }
    .grid-4 { display: grid; grid-template-columns: repeat(auto-fit, minmax(230px, 1fr)); gap: 22px; max-width: 1100px; margin: 0 auto; }
    .card {
      background: var(--white); border-radius: 12px; padding: 30px 26px; text-align: left;
      box-shadow: 0 2px 12px rgba(123,0,0,0.07); transition: transform 0.25s, box-shadow 0.25s;
    }
    .card:hover { transform: translateY(-4px); box-shadow: 0 8px 28px rgba(123,0,0,0.13); }
    .card-icon { width: 48px; height: 48px; border-radius: 10px; background: #fdf5d3; display: flex; align-items: center; justify-content: center; margin-bottom: 18px; font-size: 1.4rem; }
    .card h3 { font-size: 1.05rem; font-weight: 700; margin-bottom: 10px; }
    .card p { font-size: 0.93rem; color: var(--text-muted); line-height: 1.6; }

    .cta-strip { background: linear-gradient(135deg, var(--maroon-dark) 0%, var(--maroon) 100%); padding: 80px 48px; text-align: center; }
    .cta-strip h2 { font-family: 'Playfair Display', serif; font-size: clamp(1.9rem, 4vw, 2.7rem); color: var(--white); margin-bottom: 14px; }
    .cta-strip p { font-size: 1.05rem; color: var(--gold-light); margin-bottom: 36px; max-width: 440px; margin-left: auto; margin-right: auto; line-height: 1.6; }

    /* ── PAGE HERO ── */
    .page-hero { background: linear-gradient(135deg, var(--maroon-dark) 0%, var(--maroon) 100%); padding: 72px 48px; text-align: center; }
    .page-hero h2 { font-family: 'Playfair Display', serif; font-size: clamp(2rem, 5vw, 3rem); color: var(--white); margin-bottom: 14px; }
    .page-hero p { font-size: 1.05rem; color: rgba(245,240,232,0.82); max-width: 580px; margin: 0 auto; line-height: 1.65; }

    /* ── ABOUT ── */
    .two-col { max-width: 1100px; margin: 0 auto; padding: 72px 48px; display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
    .two-col h3 { font-family: 'Playfair Display', serif; font-size: 1.75rem; margin-bottom: 22px; color: var(--text-dark); }
    .two-col p { font-size: 1rem; color: var(--text-muted); line-height: 1.75; margin-bottom: 16px; }
    .about-img { width: 100%; border-radius: 12px; box-shadow: 0 12px 40px rgba(123,0,0,0.15); }

    .learn-section { background: var(--cream); padding: 80px 48px; text-align: center; }
    .grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(270px, 1fr)); gap: 22px; max-width: 1050px; margin: 0 auto; }
    .learn-card { background: var(--white); border-radius: 12px; padding: 32px 26px; text-align: left; border-top: 4px solid var(--gold); box-shadow: 0 2px 12px rgba(123,0,0,0.06); transition: transform 0.25s; }
    .learn-card:hover { transform: translateY(-4px); }
    .learn-dot { width: 13px; height: 13px; border-radius: 50%; background: var(--gold); margin-bottom: 18px; }
    .learn-card h3 { font-size: 1.05rem; font-weight: 700; margin-bottom: 10px; }
    .learn-card p { font-size: 0.93rem; color: var(--text-muted); line-height: 1.65; }

    /* ── EXPERIENCE ── */
    .exp-body { max-width: 1100px; margin: 0 auto; padding: 72px 48px; display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }
    .exp-card { display: flex; gap: 18px; padding: 26px; border-radius: 12px; border: 1px solid #ede0d0; transition: box-shadow 0.25s; }
    .exp-card:hover { box-shadow: 0 6px 24px rgba(123,0,0,0.1); }
    .exp-icon { flex-shrink: 0; width: 46px; height: 46px; border-radius: 10px; background: #fdf5d3; display: flex; align-items: center; justify-content: center; font-size: 1.25rem; }
    .exp-card h3 { font-size: 1.02rem; font-weight: 700; margin-bottom: 7px; }
    .exp-card p { font-size: 0.91rem; color: var(--text-muted); line-height: 1.65; }

    .timeline-section { background: var(--cream); padding: 80px 48px; }
    .timeline-section h2 { font-family: 'Playfair Display', serif; font-size: clamp(1.8rem, 4vw, 2.5rem); color: var(--maroon-dark); text-align: center; margin-bottom: 56px; }
    .timeline { max-width: 660px; margin: 0 auto; position: relative; }
    .timeline::before { content: ''; position: absolute; left: 19px; top: 0; bottom: 0; width: 2px; background: #ddd; }
    .tl-item { display: flex; gap: 26px; margin-bottom: 44px; }
    .tl-dot { flex-shrink: 0; width: 38px; height: 38px; border-radius: 50%; background: var(--gold); border: 4px solid var(--maroon-dark); position: relative; z-index: 1; }
    .tl-label { font-size: 0.82rem; font-weight: 700; color: var(--maroon); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 3px; margin-top: 6px; }
    .tl-content h3 { font-size: 1.15rem; font-weight: 700; margin-bottom: 7px; }
    .tl-content p { font-size: 0.93rem; color: var(--text-muted); line-height: 1.65; }

    /* ── CONTACT ── */
    .contact-body { max-width: 1100px; margin: 0 auto; padding: 72px 48px; display: grid; grid-template-columns: 1.3fr 1fr; gap: 64px; }
    .contact-form h3 { font-size: 1.45rem; font-weight: 700; margin-bottom: 26px; }
    .field { margin-bottom: 18px; }
    .field label { display: block; font-size: 0.88rem; font-weight: 600; margin-bottom: 5px; }
    .field input, .field textarea { width: 100%; padding: 11px 14px; border: 1.5px solid #ddd; border-radius: 8px; font-size: 0.93rem; font-family: 'Source Sans 3', sans-serif; color: var(--text-dark); background: #fafafa; transition: border-color 0.2s; }
    .field input:focus, .field textarea:focus { outline: none; border-color: var(--maroon); background: #fff; }
    .field textarea { height: 128px; resize: vertical; }
    .btn-submit { background: var(--maroon); color: var(--white); padding: 13px 30px; border-radius: 8px; font-size: 0.97rem; font-weight: 700; font-family: 'Source Sans 3', sans-serif; border: none; cursor: pointer; transition: background 0.2s, transform 0.2s; }
    .btn-submit:hover { background: var(--maroon-dark); transform: translateY(-2px); }
    .contact-info { display: flex; flex-direction: column; gap: 26px; padding-top: 56px; }
    .info-item { display: flex; gap: 15px; align-items: flex-start; }
    .info-icon { flex-shrink: 0; width: 42px; height: 42px; border-radius: 10px; background: #fdf5d3; display: flex; align-items: center; justify-content: center; font-size: 1.15rem; }
    .info-item h4 { font-size: 0.97rem; font-weight: 700; margin-bottom: 3px; }
    .info-item p { font-size: 0.9rem; color: var(--text-muted); line-height: 1.55; }

    /* ── APPLY ── */
    .apply-page { background: var(--cream); }
    .apply-body { max-width: 780px; margin: 0 auto; padding: 64px 48px 96px; }
    .apply-intro { text-align: center; margin-bottom: 44px; }
    .apply-intro h3 { font-family: 'Playfair Display', serif; font-size: 1.6rem; color: var(--maroon-dark); margin-bottom: 12px; }
    .apply-intro p { font-size: 1rem; color: var(--text-muted); line-height: 1.7; max-width: 500px; margin: 0 auto; }
    .apply-form { background: var(--white); border-radius: 16px; padding: 44px 40px; box-shadow: 0 4px 24px rgba(123,0,0,0.08); }
    .apply-form h3 { font-size: 1.2rem; font-weight: 700; margin-bottom: 26px; color: var(--maroon-dark); border-bottom: 2px solid var(--cream); padding-bottom: 14px; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; }
    .apply-field { margin-bottom: 20px; }
    .apply-field label { display: block; font-size: 0.87rem; font-weight: 600; margin-bottom: 5px; }
    .apply-field input, .apply-field select, .apply-field textarea { width: 100%; padding: 11px 14px; border: 1.5px solid #ddd; border-radius: 8px; font-size: 0.93rem; font-family: 'Source Sans 3', sans-serif; color: var(--text-dark); background: #fafafa; transition: border-color 0.2s; appearance: none; }
    .apply-field input:focus, .apply-field select:focus, .apply-field textarea:focus { outline: none; border-color: var(--maroon); background: #fff; }
    .apply-field textarea { height: 110px; resize: vertical; }
    .apply-field select { background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath fill='%237b0000' d='M6 8L0 0h12z'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 14px center; }
    .apply-divider { font-size: 0.83rem; font-weight: 700; color: var(--maroon); text-transform: uppercase; letter-spacing: 0.07em; margin: 26px 0 20px; border-top: 1px solid var(--cream); padding-top: 22px; }
    .btn-apply-submit { width: 100%; background: var(--maroon); color: var(--white); padding: 15px; border-radius: 10px; font-size: 1rem; font-weight: 700; font-family: 'Source Sans 3', sans-serif; border: none; cursor: pointer; margin-top: 8px; transition: background 0.2s, transform 0.2s; letter-spacing: 0.02em; }
    .btn-apply-submit:hover { background: var(--maroon-dark); transform: translateY(-2px); }
    .apply-note { text-align: center; font-size: 0.83rem; color: var(--text-muted); margin-top: 14px; }

    /* FOOTER */
    footer { background: var(--maroon-dark); padding: 60px 48px 28px; }
    .footer-grid { display: grid; grid-template-columns: 1.5fr 1fr 1fr; gap: 44px; max-width: 1100px; margin: 0 auto 44px; }
    .footer-brand { font-family: 'Playfair Display', serif; font-size: 1.15rem; color: var(--gold); font-weight: 700; margin-bottom: 14px; }
    .footer-addr { font-size: 0.9rem; color: rgba(245,240,232,0.65); line-height: 1.85; }
    .footer-col h4 { font-size: 0.97rem; font-weight: 700; color: var(--gold); margin-bottom: 14px; }
    .footer-col a { display: block; font-size: 0.9rem; color: rgba(245,240,232,0.65); text-decoration: none; margin-bottom: 9px; cursor: pointer; transition: color 0.2s; }
    .footer-col a:hover { color: var(--white); }
    .footer-col p { font-size: 0.9rem; color: rgba(245,240,232,0.65); line-height: 1.75; }
    .footer-bottom { border-top: 1px solid rgba(255,255,255,0.1); padding-top: 24px; text-align: center; font-size: 0.85rem; color: rgba(245,240,232,0.4); }

    /* RESPONSIVE */
    @media (max-width: 820px) {
      nav { padding: 0 16px; }
      .nav-brand { font-size: 0.88rem; }
      .nav-tab { padding: 7px 9px; font-size: 0.8rem; }
      .two-col, .exp-body, .contact-body { grid-template-columns: 1fr; gap: 32px; }
      .form-row { grid-template-columns: 1fr; }
      .footer-grid { grid-template-columns: 1fr; gap: 28px; }
      .why-section, .learn-section, .timeline-section, .cta-strip { padding: 56px 24px; }
      .two-col, .exp-body { padding: 44px 24px; }
      .contact-body, .apply-body { padding: 44px 24px; }
      .apply-form { padding: 28px 20px; }
      footer { padding: 44px 24px 22px; }
      .page-hero { padding: 52px 24px; }
    }
  </style>
</head>
<body>

  <!-- NAV -->
  <nav>
    <div class="nav-brand" onclick="showTab('home')">Consumer Insights & Analytics</div>
    <div class="nav-links">
      <button class="nav-tab active" data-tab="home"    onclick="showTab('home')">Home</button>
      <button class="nav-tab"        data-tab="about"   onclick="showTab('about')">About</button>
      <button class="nav-tab"        data-tab="exp"     onclick="showTab('exp')">Experience</button>
      <button class="nav-tab"        data-tab="contact" onclick="showTab('contact')">Contact Us</button>
      <button class="nav-tab apply-btn" data-tab="apply" onclick="showTab('apply')">Apply Now</button>
    </div>
  </nav>

  <!-- ═══ HOME ═══ -->
  <div class="page active" id="page-home">
    <div class="hero">
      <div class="hero-bg"></div>
      <div class="hero-overlay"></div>
      <div class="hero-content">
        <h1>Consumer Insights <span>& Analytics</span></h1>
        <p>An experiential learning program at the Carlson School of Management that bridges the gap between consumer research and business strategy.</p>
        <div class="hero-btns">
          <button class="btn-gold" onclick="showTab('apply')">Apply Now</button>
          <button class="btn-outline" onclick="showTab('about')">Learn More</button>
        </div>
      </div>
    </div>

    <div class="why-section">
      <h2 class="sec-title">Why CIA?</h2>
      <p class="sec-sub">Our program equips students with the skills to understand consumers and drive business impact.</p>
      <div class="grid-4">
        <div class="card"><div class="card-icon">📊</div><h3>Data-Driven Insights</h3><p>Learn to transform raw consumer data into actionable business strategies using cutting-edge analytics tools.</p></div>
        <div class="card"><div class="card-icon">👥</div><h3>Real Client Projects</h3><p>Work directly with Fortune 500 companies on live consumer research and analytics challenges.</p></div>
        <div class="card"><div class="card-icon">📈</div><h3>Career Advancement</h3><p>Graduates land roles at top firms including General Mills, Target, 3M, and leading agencies.</p></div>
        <div class="card"><div class="card-icon">💡</div><h3>Innovation Focus</h3><p>Explore emerging methodologies in behavioral analytics, AI-driven insights, and market research.</p></div>
      </div>
    </div>

    <div class="cta-strip">
      <h2>Ready to Get Started?</h2>
      <p>Applications are now open. Join a community of driven students passionate about consumer insights.</p>
      <button class="btn-gold" onclick="showTab('apply')">Apply Now</button>
    </div>

    <footer>
      <div class="footer-grid">
        <div><div class="footer-brand">Consumer Insights & Analytics</div><div class="footer-addr">Carlson School of Management<br>University of Minnesota<br>321 19th Ave S, Minneapolis, MN 55455</div></div>
        <div class="footer-col"><h4>Quick Links</h4><a onclick="showTab('about')">About the Program</a><a onclick="showTab('exp')">Experience</a><a onclick="showTab('apply')">Apply Now</a><a onclick="showTab('contact')">Contact Us</a></div>
        <div class="footer-col"><h4>Connect</h4><p>Email: cia@umn.edu<br>Phone: (612) 625-0027</p></div>
      </div>
      <div class="footer-bottom">© 2026 Regents of the University of Minnesota. All rights reserved.</div>
    </footer>
  </div>

  <!-- ═══ ABOUT ═══ -->
  <div class="page" id="page-about">
    <div class="page-hero">
      <h2>About the Program</h2>
      <p>Discover how the Consumer Insights & Analytics program prepares students for impactful careers.</p>
    </div>

    <div class="two-col">
      <div>
        <h3>Our Mission</h3>
        <p>The Consumer Insights & Analytics (CIA) program at the Carlson School of Management is a premier experiential learning opportunity that connects undergraduate students with real-world consumer research challenges.</p>
        <p>Students work in teams on semester-long projects with corporate partners, applying research methodologies, data analysis, and strategic thinking to deliver actionable insights.</p>
        <p>Since its founding, the program has partnered with industry leaders including General Mills, Target, Best Buy, 3M, Land O'Lakes, and many more. Our alumni network spans top consumer packaged goods companies, consulting firms, and tech organizations.</p>
      </div>
      <div>
        <img class="about-img" src="https://images.unsplash.com/photo-1509062522246-3755977927d7?w=800&q=80" alt="Carlson School campus" />
      </div>
    </div>

    <div class="learn-section">
      <h2 class="sec-title">What You'll Learn</h2>
      <p class="sec-sub" style="margin-bottom:44px;">Core competencies you'll develop throughout the program.</p>
      <div class="grid-3">
        <div class="learn-card"><div class="learn-dot"></div><h3>Research Design</h3><p>Design and execute qualitative and quantitative consumer research studies from inception to delivery.</p></div>
        <div class="learn-card"><div class="learn-dot"></div><h3>Analytics & Tools</h3><p>Master tools like SPSS, Qualtrics, Tableau, and Python to analyze consumer behavior data.</p></div>
        <div class="learn-card"><div class="learn-dot"></div><h3>Strategic Presentation</h3><p>Translate data findings into compelling narratives and present to C-suite executives.</p></div>
      </div>
    </div>

    <footer>
      <div class="footer-grid">
        <div><div class="footer-brand">Consumer Insights & Analytics</div><div class="footer-addr">Carlson School of Management<br>University of Minnesota<br>321 19th Ave S, Minneapolis, MN 55455</div></div>
        <div class="footer-col"><h4>Quick Links</h4><a onclick="showTab('about')">About the Program</a><a onclick="showTab('exp')">Experience</a><a onclick="showTab('apply')">Apply Now</a><a onclick="showTab('contact')">Contact Us</a></div>
        <div class="footer-col"><h4>Connect</h4><p>Email: cia@umn.edu<br>Phone: (612) 625-0027</p></div>
      </div>
      <div class="footer-bottom">© 2026 Regents of the University of Minnesota. All rights reserved.</div>
    </footer>
  </div>

  <!-- ═══ EXPERIENCE ═══ -->
  <div class="page" id="page-exp">
    <div class="page-hero">
      <h2>The CIA Experience</h2>
      <p>A hands-on, semester-long engagement that transforms students into consumer insights professionals.</p>
    </div>

    <div class="exp-body">
      <div class="exp-card"><div class="exp-icon">📋</div><div><h3>Corporate Partnerships</h3><p>Each semester, CIA partners with leading companies to solve real consumer challenges. Past partners include General Mills, Target, Best Buy, 3M, and Land O'Lakes.</p></div></div>
      <div class="exp-card"><div class="exp-icon">🖥️</div><div><h3>Client Presentations</h3><p>Teams present their findings and strategic recommendations directly to senior marketing executives and brand managers.</p></div></div>
      <div class="exp-card"><div class="exp-icon">👤</div><div><h3>Team Collaboration</h3><p>Work in diverse, cross-functional teams of 4–6 students, replicating the dynamics of a professional consulting engagement.</p></div></div>
      <div class="exp-card"><div class="exp-icon">🏆</div><div><h3>Professional Development</h3><p>Build your portfolio with real projects, develop presentation skills, and network with industry professionals throughout the semester.</p></div></div>
    </div>

    <div class="timeline-section">
      <h2>Semester Timeline</h2>
      <div class="timeline">
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-content"><div class="tl-label">Weeks 1–2</div><h3>Project Kickoff</h3><p>Meet your client, understand the business challenge, and define research objectives.</p></div></div>
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-content"><div class="tl-label">Weeks 3–5</div><h3>Research Design</h3><p>Design surveys, interview guides, and research methodologies tailored to the project.</p></div></div>
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-content"><div class="tl-label">Weeks 6–10</div><h3>Data Collection & Analysis</h3><p>Collect data, run analyses, and identify key consumer insights and patterns.</p></div></div>
        <div class="tl-item"><div class="tl-dot"></div><div class="tl-content"><div class="tl-label">Weeks 11–14</div><h3>Strategy & Presentation</h3><p>Develop strategic recommendations and deliver a final presentation to the client.</p></div></div>
      </div>
    </div>

    <footer>
      <div class="footer-grid">
        <div><div class="footer-brand">Consumer Insights & Analytics</div><div class="footer-addr">Carlson School of Management<br>University of Minnesota<br>321 19th Ave S, Minneapolis, MN 55455</div></div>
        <div class="footer-col"><h4>Quick Links</h4><a onclick="showTab('about')">About the Program</a><a onclick="showTab('exp')">Experience</a><a onclick="showTab('apply')">Apply Now</a><a onclick="showTab('contact')">Contact Us</a></div>
        <div class="footer-col"><h4>Connect</h4><p>Email: cia@umn.edu<br>Phone: (612) 625-0027</p></div>
      </div>
      <div class="footer-bottom">© 2026 Regents of the University of Minnesota. All rights reserved.</div>
    </footer>
  </div>

  <!-- ═══ CONTACT ═══ -->
  <div class="page" id="page-contact">
    <div class="page-hero">
      <h2>Contact Us</h2>
      <p>Have questions about the program? We'd love to hear from you.</p>
    </div>

    <div class="contact-body">
      <div class="contact-form">
        <h3>Get in Touch</h3>
        <div class="field"><label>Name</label><input type="text" placeholder="Your full name" /></div>
        <div class="field"><label>Email</label><input type="email" placeholder="you@umn.edu" /></div>
        <div class="field"><label>Message</label><textarea placeholder="Tell us about your interest in the program..."></textarea></div>
        <button class="btn-submit">Send Message</button>
      </div>
      <div class="contact-info">
        <div class="info-item"><div class="info-icon">📍</div><div><h4>Address</h4><p>Carlson School of Management<br>321 19th Ave S<br>Minneapolis, MN 55455</p></div></div>
        <div class="info-item"><div class="info-icon">✉️</div><div><h4>Email</h4><p>cia@umn.edu</p></div></div>
        <div class="info-item"><div class="info-icon">📞</div><div><h4>Phone</h4><p>(612) 625-0027</p></div></div>
      </div>
    </div>

    <footer>
      <div class="footer-grid">
        <div><div class="footer-brand">Consumer Insights & Analytics</div><div class="footer-addr">Carlson School of Management<br>University of Minnesota<br>321 19th Ave S, Minneapolis, MN 55455</div></div>
        <div class="footer-col"><h4>Quick Links</h4><a onclick="showTab('about')">About the Program</a><a onclick="showTab('exp')">Experience</a><a onclick="showTab('apply')">Apply Now</a><a onclick="showTab('contact')">Contact Us</a></div>
        <div class="footer-col"><h4>Connect</h4><p>Email: cia@umn.edu<br>Phone: (612) 625-0027</p></div>
      </div>
      <div class="footer-bottom">© 2026 Regents of the University of Minnesota. All rights reserved.</div>
    </footer>
  </div>

  <!-- ═══ APPLY NOW ═══ -->
  <div class="page apply-page" id="page-apply">
    <div class="page-hero">
      <h2>Apply Now</h2>
      <p>Take the first step toward an unforgettable experiential learning opportunity at Carlson.</p>
    </div>

    <div class="apply-body">
      <div class="apply-intro">
        <h3>Applications Are Open</h3>
        <p>Join a community of driven students passionate about consumer insights. Complete the form below and our team will follow up within 3–5 business days.</p>
      </div>

      <div class="apply-form">
        <h3>Personal Information</h3>
        <div class="form-row">
          <div class="apply-field"><label>First Name</label><input type="text" placeholder="Jane" /></div>
          <div class="apply-field"><label>Last Name</label><input type="text" placeholder="Doe" /></div>
        </div>
        <div class="form-row">
          <div class="apply-field"><label>Email Address</label><input type="email" placeholder="you@umn.edu" /></div>
          <div class="apply-field"><label>Phone Number</label><input type="tel" placeholder="(612) 000-0000" /></div>
        </div>

        <div class="apply-divider">Academic Information</div>
        <div class="form-row">
          <div class="apply-field">
            <label>Year in School</label>
            <select><option value="">Select year…</option><option>Freshman</option><option>Sophomore</option><option>Junior</option><option>Senior</option></select>
          </div>
          <div class="apply-field"><label>Major / Area of Study</label><input type="text" placeholder="e.g. Marketing, Economics" /></div>
        </div>
        <div class="form-row">
          <div class="apply-field"><label>GPA (optional)</label><input type="text" placeholder="e.g. 3.5" /></div>
          <div class="apply-field"><label>Expected Graduation</label><input type="text" placeholder="e.g. May 2027" /></div>
        </div>

        <div class="apply-divider">Statement of Interest</div>
        <div class="apply-field"><label>Why do you want to join CIA?</label><textarea placeholder="Tell us about your interest in consumer research and what you hope to gain from the program..."></textarea></div>
        <div class="apply-field"><label>Relevant Experience (optional)</label><textarea placeholder="Describe any coursework, internships, or projects related to research or analytics..."></textarea></div>

        <button class="btn-apply-submit">Submit Application</button>
        <p class="apply-note">By submitting, you agree to be contacted by the CIA program team regarding your application.</p>
      </div>
    </div>

    <footer>
      <div class="footer-grid">
        <div><div class="footer-brand">Consumer Insights & Analytics</div><div class="footer-addr">Carlson School of Management<br>University of Minnesota<br>321 19th Ave S, Minneapolis, MN 55455</div></div>
        <div class="footer-col"><h4>Quick Links</h4><a onclick="showTab('about')">About the Program</a><a onclick="showTab('exp')">Experience</a><a onclick="showTab('apply')">Apply Now</a><a onclick="showTab('contact')">Contact Us</a></div>
        <div class="footer-col"><h4>Connect</h4><p>Email: cia@umn.edu<br>Phone: (612) 625-0027</p></div>
      </div>
      <div class="footer-bottom">© 2026 Regents of the University of Minnesota. All rights reserved.</div>
    </footer>
  </div>

  <script>
    function showTab(tab) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
      document.getElementById('page-' + tab).classList.add('active');
      document.querySelector('[data-tab="' + tab + '"]').classList.add('active');
      window.scrollTo({ top: 0, behavior: 'instant' });
    }
  </script>
</body>
</html>
