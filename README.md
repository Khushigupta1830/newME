<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Khushi Gupta</title>
  <meta name="description" content="Computer Software Engineer | Delhi, India"/>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    /* ══════════════════════════════════════
       THEMES
    ══════════════════════════════════════ */
    [data-theme="dark"] {
      --bg: #0d0d0f;
      --bg2: #13131a;
      --card: #17171f;
      --border: rgba(255,255,255,0.07);
      --accent: #c8a96e;
      --accent2: #e8c98d;
      --accent-rgb: 200,169,110;
      --text: #f0ede6;
      --muted: #8a8799;
      --nav-bg: rgba(13,13,15,0.88);
      --btn-primary-text: #0d0d0f;
      --h1-grad: linear-gradient(135deg, #f0ede6 30%, #e8c98d 80%);
    }
    [data-theme="light"] {
      --bg: #f7f5f0;
      --bg2: #eceae3;
      --card: #ffffff;
      --border: rgba(0,0,0,0.09);
      --accent: #8b6914;
      --accent2: #b8891a;
      --accent-rgb: 139,105,20;
      --text: #1a1810;
      --muted: #6b6456;
      --nav-bg: rgba(247,245,240,0.93);
      --btn-primary-text: #ffffff;
      --h1-grad: linear-gradient(135deg, #1a1810 30%, #8b6914 80%);
    }
    [data-theme="pink"] {
      --bg: #1a0d14;
      --bg2: #200f18;
      --card: #27121e;
      --border: rgba(255,150,180,0.1);
      --accent: #f472b6;
      --accent2: #fb7cc4;
      --accent-rgb: 244,114,182;
      --text: #fce7f3;
      --muted: #c084a0;
      --nav-bg: rgba(26,13,20,0.88);
      --btn-primary-text: #1a0d14;
      --h1-grad: linear-gradient(135deg, #fce7f3 30%, #f472b6 80%);
    }
    [data-theme="blue"] {
      --bg: #080d1a;
      --bg2: #0c1220;
      --card: #101828;
      --border: rgba(100,160,255,0.1);
      --accent: #60a5fa;
      --accent2: #93c5fd;
      --accent-rgb: 96,165,250;
      --text: #e8f0fe;
      --muted: #7a9bbf;
      --nav-bg: rgba(8,13,26,0.88);
      --btn-primary-text: #080d1a;
      --h1-grad: linear-gradient(135deg, #e8f0fe 30%, #93c5fd 80%);
    }

    :root { --radius: 16px; }

    html { scroll-behavior: smooth; }
    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      line-height: 1.7;
      overflow-x: hidden;
      transition: background 0.4s, color 0.4s;
    }

    /* ══ THEME SWITCHER ══ */
    .theme-switcher {
      display: flex;
      align-items: center;
      gap: 7px;
    }
    .theme-label {
      font-size: 0.68rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--muted);
      margin-right: 2px;
      transition: color 0.4s;
    }
    .theme-btn {
      width: 26px; height: 26px;
      border-radius: 50%;
      border: 2.5px solid transparent;
      cursor: pointer;
      transition: transform 0.2s, border-color 0.2s, box-shadow 0.2s;
      outline: none;
      position: relative;
    }
    .theme-btn:hover { transform: scale(1.18); }
    .theme-btn.active {
      border-color: var(--accent);
      box-shadow: 0 0 0 3px rgba(var(--accent-rgb), 0.25);
      transform: scale(1.15);
    }
    .theme-btn[data-mode="dark"]  { background: radial-gradient(circle at 35% 35%, #3a3a4a, #0d0d0f); }
    .theme-btn[data-mode="light"] { background: radial-gradient(circle at 35% 35%, #fff8e8, #c4b57a); }
    .theme-btn[data-mode="pink"]  { background: radial-gradient(circle at 35% 35%, #ff8ec4, #9b1d5c); }
    .theme-btn[data-mode="blue"]  { background: radial-gradient(circle at 35% 35%, #93c5fd, #1e3a7a); }
    /* tooltip */
    .theme-btn::after {
      content: attr(title);
      position: absolute;
      bottom: -28px; left: 50%;
      transform: translateX(-50%);
      background: var(--card);
      color: var(--text);
      font-size: 0.65rem;
      white-space: nowrap;
      padding: 3px 7px;
      border-radius: 6px;
      border: 1px solid var(--border);
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.2s;
    }
    .theme-btn:hover::after { opacity: 1; }

    /* ══ NAV ══ */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; justify-content: space-between; align-items: center;
      padding: 16px 48px;
      background: var(--nav-bg);
      backdrop-filter: blur(18px);
      border-bottom: 1px solid var(--border);
      transition: background 0.4s, border-color 0.4s;
    }
    .nav-left { display: flex; align-items: center; gap: 36px; }
    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      color: var(--accent);
      letter-spacing: 0.04em;
      transition: color 0.4s;
    }
    .nav-links { display: flex; gap: 28px; }
    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 0.85rem;
      font-weight: 500;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--accent); }

    /* ══ HERO ══ */
    .hero {
      min-height: 100vh;
      display: flex; flex-direction: column;
      justify-content: center; align-items: center;
      text-align: center;
      padding: 120px 24px 80px;
      position: relative; overflow: hidden;
    }
    .hero::before {
      content: '';
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse 60% 50% at 50% 20%, rgba(var(--accent-rgb),0.13) 0%, transparent 70%),
        radial-gradient(ellipse 40% 40% at 80% 80%, rgba(var(--accent-rgb),0.06) 0%, transparent 60%);
      pointer-events: none;
    }
    .hero-eyebrow {
      font-size: 0.78rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 20px; font-weight: 500;
      transition: color 0.4s;
    }
    .hero h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(3.5rem, 9vw, 7.5rem);
      font-weight: 900; line-height: 1.0;
      letter-spacing: -0.02em; margin-bottom: 24px;
      background: var(--h1-grad);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .hero-sub {
      font-size: 1.1rem; color: var(--muted);
      max-width: 460px; margin-bottom: 44px; font-weight: 300;
      transition: color 0.4s;
    }
    .hero-btns { display: flex; gap: 16px; flex-wrap: wrap; justify-content: center; }
    .btn {
      display: inline-flex; align-items: center; gap: 8px;
      padding: 14px 28px; border-radius: 40px;
      font-size: 0.88rem; font-weight: 600;
      letter-spacing: 0.04em; text-decoration: none;
      transition: all 0.25s; cursor: pointer; border: none;
    }
    .btn-primary { background: var(--accent); color: var(--btn-primary-text); }
    .btn-primary:hover { background: var(--accent2); transform: translateY(-2px); }
    .btn-ghost { background: transparent; color: var(--text); border: 1px solid var(--border); }
    .btn-ghost:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

    .scroll-hint {
      margin-top: 72px;
      display: flex; flex-direction: column; align-items: center; gap: 8px;
      color: var(--muted); font-size: 0.75rem; letter-spacing: 0.1em;
      text-transform: uppercase; animation: bounce 2s infinite;
      transition: color 0.4s;
    }
    .scroll-hint span { width: 1px; height: 40px; background: var(--accent); opacity: 0.5; transition: background 0.4s; }
    @keyframes bounce { 0%,100%{transform:translateY(0)} 50%{transform:translateY(6px)} }

    /* ══ SECTIONS ══ */
    section { padding: 100px 24px; max-width: 1100px; margin: 0 auto; }
    .section-label {
      font-size: 0.75rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: var(--accent); margin-bottom: 12px; font-weight: 500; transition: color 0.4s;
    }
    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 700; line-height: 1.15; margin-bottom: 48px;
    }

    /* ABOUT */
    .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 64px; align-items: start; }
    .about-text p { color: var(--muted); margin-bottom: 20px; font-size: 1.02rem; font-weight: 300; transition: color 0.4s; }
    .about-facts { display: flex; flex-direction: column; gap: 16px; margin-top: 36px; }
    .fact {
      display: flex; gap: 16px; align-items: flex-start;
      padding: 16px 20px; background: var(--card);
      border: 1px solid var(--border); border-radius: var(--radius);
      transition: background 0.4s, border-color 0.4s;
    }
    .fact-icon { color: var(--accent); font-size: 1.2rem; margin-top: 2px; transition: color 0.4s; }
    .fact-label { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--muted); transition: color 0.4s; }
    .fact-value { font-weight: 500; font-size: 0.95rem; }

    /* SKILLS */
    .skills-section { background: var(--bg2); padding: 100px 0; transition: background 0.4s; }
    .skills-inner { max-width: 1100px; margin: 0 auto; padding: 0 24px; }
    .skills-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; }
    .skill-card {
      background: var(--card); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 32px;
      transition: border-color 0.25s, transform 0.25s, background 0.4s;
    }
    .skill-card:hover { border-color: var(--accent); transform: translateY(-4px); }
    .skill-icon {
      width: 48px; height: 48px; border-radius: 12px;
      background: rgba(var(--accent-rgb), 0.12);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.4rem; margin-bottom: 20px; transition: background 0.4s;
    }
    .skill-card h3 { font-size: 1.05rem; font-weight: 600; margin-bottom: 8px; }
    .skill-card p { color: var(--muted); font-size: 0.9rem; font-weight: 300; transition: color 0.4s; }

    /* EXPERTISE */
    .expertise-list { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 16px; }
    .expertise-item {
      padding: 24px 28px; background: var(--card);
      border: 1px solid var(--border); border-radius: var(--radius);
      border-left: 3px solid var(--accent);
      transition: background 0.4s, border-color 0.4s;
    }
    .expertise-item h4 { font-size: 0.95rem; font-weight: 600; margin-bottom: 6px; }
    .expertise-item p { color: var(--muted); font-size: 0.86rem; font-weight: 300; transition: color 0.4s; }

    /* PROCESS */
    .process-section { background: var(--bg2); padding: 100px 0; transition: background 0.4s; }
    .process-inner { max-width: 1100px; margin: 0 auto; padding: 0 24px; }
    .process-steps {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 0; position: relative;
    }
    .process-steps::before {
      content: ''; position: absolute;
      top: 28px; left: 10%; right: 10%; height: 1px;
      background: linear-gradient(90deg, transparent, var(--accent), transparent);
      opacity: 0.4;
    }
    .step { text-align: center; padding: 0 20px; position: relative; }
    .step-num {
      width: 56px; height: 56px; border-radius: 50%;
      background: var(--card); border: 2px solid var(--accent);
      display: flex; align-items: center; justify-content: center;
      font-family: 'Playfair Display', serif; font-size: 1.1rem; font-weight: 700;
      color: var(--accent); margin: 0 auto 20px; position: relative; z-index: 1;
      transition: background 0.4s, border-color 0.4s, color 0.4s;
    }
    .step h4 { font-size: 0.95rem; font-weight: 600; margin-bottom: 8px; }
    .step p { color: var(--muted); font-size: 0.85rem; font-weight: 300; transition: color 0.4s; }

    /* BRING */
    .bring-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 24px; margin-bottom: 60px; }
    .bring-card {
      background: var(--card); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 36px;
      transition: background 0.4s, border-color 0.4s;
    }
    .bring-card h3 { font-size: 1.1rem; font-weight: 600; margin-bottom: 12px; color: var(--accent2); transition: color 0.4s; }
    .bring-card p { color: var(--muted); font-size: 0.92rem; font-weight: 300; transition: color 0.4s; }

    .interests { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 20px; }
    .interest-card {
      background: linear-gradient(135deg, var(--card), rgba(var(--accent-rgb), 0.05));
      border: 1px solid var(--border); border-radius: var(--radius); padding: 28px;
      transition: border-color 0.25s, background 0.4s;
    }
    .interest-card:hover { border-color: rgba(var(--accent-rgb), 0.4); }
    .interest-card .ic-icon { font-size: 1.8rem; margin-bottom: 16px; }
    .interest-card h4 { font-size: 1rem; font-weight: 600; margin-bottom: 8px; }
    .interest-card p { color: var(--muted); font-size: 0.88rem; font-weight: 300; transition: color 0.4s; }

    /* EDUCATION */
    .edu-card {
      background: var(--card); border: 1px solid var(--border);
      border-radius: var(--radius); padding: 40px;
      display: flex; gap: 32px; align-items: flex-start;
      transition: background 0.4s, border-color 0.4s;
    }
    .edu-num {
      font-family: 'Playfair Display', serif; font-size: 3rem; font-weight: 900;
      color: rgba(var(--accent-rgb), 0.2); line-height: 1; flex-shrink: 0; transition: color 0.4s;
    }
    .edu-info h3 { font-size: 1.2rem; font-weight: 700; margin-bottom: 6px; }
    .edu-info .degree { color: var(--accent); font-weight: 500; margin-bottom: 4px; font-size: 0.95rem; transition: color 0.4s; }
    .edu-info .field { color: var(--muted); font-size: 0.9rem; transition: color 0.4s; }
    .edu-info .location { color: var(--muted); font-size: 0.85rem; margin-top: 8px; display: flex; align-items: center; gap: 6px; transition: color 0.4s; }

    /* CONTACT */
    .contact-section { background: var(--bg2); padding: 100px 0; transition: background 0.4s; }
    .contact-inner { max-width: 1100px; margin: 0 auto; padding: 0 24px; }
    .contact-grid { display: grid; grid-template-columns: 1.2fr 1fr; gap: 60px; align-items: start; }
    .contact-text p { color: var(--muted); font-size: 1rem; font-weight: 300; margin-bottom: 36px; transition: color 0.4s; }
    .contact-methods { display: flex; flex-direction: column; gap: 16px; }
    .contact-method {
      display: flex; gap: 16px; align-items: center;
      padding: 20px 24px; background: var(--card);
      border: 1px solid var(--border); border-radius: var(--radius);
      text-decoration: none; color: var(--text);
      transition: border-color 0.25s, transform 0.2s, background 0.4s;
    }
    .contact-method:hover { border-color: var(--accent); transform: translateX(4px); }
    .contact-method-icon { font-size: 1.3rem; }
    .contact-method-label { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.1em; color: var(--muted); transition: color 0.4s; }
    .contact-method-value { font-weight: 500; font-size: 0.92rem; }

    .ready-card {
      background: linear-gradient(135deg, rgba(var(--accent-rgb),0.1), rgba(var(--accent-rgb),0.03));
      border: 1px solid rgba(var(--accent-rgb),0.25);
      border-radius: var(--radius); padding: 36px;
      transition: background 0.4s, border-color 0.4s;
    }
    .ready-card p { color: var(--muted); font-size: 0.92rem; font-weight: 300; margin-bottom: 28px; transition: color 0.4s; }
    .ready-card .btns { display: flex; flex-direction: column; gap: 12px; }
    .ready-card .btns .btn { justify-content: center; }

    /* FOOTER */
    footer {
      text-align: center; padding: 32px;
      border-top: 1px solid var(--border); color: var(--muted); font-size: 0.82rem;
      transition: border-color 0.4s, color 0.4s;
    }

    /* FADE IN */
    .fade-in { opacity: 0; transform: translateY(24px); transition: opacity 0.7s ease, transform 0.7s ease; }
    .fade-in.visible { opacity: 1; transform: translateY(0); }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      nav { padding: 14px 16px; }
      .nav-links { display: none; }
      .about-grid, .contact-grid { grid-template-columns: 1fr; }
      .process-steps::before { display: none; }
      .edu-card { flex-direction: column; gap: 16px; }
      section { padding: 70px 20px; }
      .theme-label { display: none; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-left">
    <div class="nav-logo">KG</div>
    <div class="nav-links">
      <a href="#about">About</a>
      <a href="#skills">Skills</a>
      <a href="#education">Education</a>
      <a href="#contact">Contact</a>
    </div>
  </div>
  <div style="display:flex;align-items:center;gap:20px;">
    <a href="https://github.com/Khushigupta1830" target="_blank" style="color:var(--muted);text-decoration:none;font-size:0.85rem;font-weight:500;letter-spacing:0.06em;text-transform:uppercase;transition:color 0.2s;" onmouseover="this.style.color='var(--accent)'" onmouseout="this.style.color='var(--muted)'">⌥ GitHub</a>
    <div class="theme-switcher">
      <span class="theme-label">Theme</span>
      <button class="theme-btn active" data-mode="dark"  title="Dark"></button>
      <button class="theme-btn"        data-mode="light" title="Light"></button>
      <button class="theme-btn"        data-mode="pink"  title="Pink"></button>
      <button class="theme-btn"        data-mode="blue"  title="Blue"></button>
    </div>
  </div>
</nav>

<!-- HERO -->
<div class="hero">
  <p class="hero-eyebrow">Portfolio</p>
  <h1>Khushi Gupta</h1>
  <p class="hero-sub">Computer Software Engineer &nbsp;·&nbsp; Delhi, India</p>
  <div class="hero-btns">
    <button onclick="copyEmail()" class="btn btn-primary">✉ Get In Touch</button>
    <a href="https://www.linkedin.com/in/khushi-gupta-288208335" target="_blank" class="btn btn-ghost">↗ LinkedIn</a>
    <a href="https://github.com/Khushigupta1830" target="_blank" class="btn btn-ghost">⌥ GitHub</a>
  </div>
  <div class="scroll-hint">scroll<span></span></div>
</div>

<!-- ABOUT -->
<section id="about">
  <p class="section-label">Who I Am</p>
  <h2 class="section-title">About Me</h2>
  <div class="about-grid fade-in">
    <div class="about-text">
      <p>I am a Computer Software Engineering graduate from Guru Gobind Singh Indraprastha University, passionate about creating innovative software solutions.</p>
      <p>With a strong foundation in Java and software development principles, I am eager to contribute to challenging projects and continue growing as a developer.</p>
      <p>My academic background has equipped me with the technical skills and problem-solving mindset necessary for modern software development. I am committed to writing clean, efficient code and continuously expanding my knowledge.</p>
    </div>
    <div class="about-facts">
      <div class="fact">
        <div class="fact-icon">📍</div>
        <div><div class="fact-label">Location</div><div class="fact-value">Delhi, India</div></div>
      </div>
      <div class="fact">
        <div class="fact-icon">🎓</div>
        <div><div class="fact-label">Degree</div><div class="fact-value">Bachelor of Technology</div></div>
      </div>
      <div class="fact">
        <div class="fact-icon">💻</div>
        <div><div class="fact-label">Field</div><div class="fact-value">Computer Software Engineering</div></div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<div class="skills-section" id="skills">
  <div class="skills-inner">
    <p class="section-label">Capabilities</p>
    <h2 class="section-title">Core Skills</h2>
    <div class="skills-grid fade-in">
      <div class="skill-card">
        <div class="skill-icon">☕</div>
        <h3>Java</h3>
        <p>Strong foundation in object-oriented programming, data structures, and algorithm implementation.</p>
      </div>
      <div class="skill-card">
        <div class="skill-icon">🛠</div>
        <h3>Software Development</h3>
        <p>Understanding of software engineering principles and development methodologies.</p>
      </div>
      <div class="skill-card">
        <div class="skill-icon">🧩</div>
        <h3>Problem Solving</h3>
        <p>Analytical approach to debugging and creating efficient, optimised solutions.</p>
      </div>
    </div>
    <div style="margin-top:60px;">
      <h3 style="font-family:'Playfair Display',serif;font-size:1.5rem;margin-bottom:28px;">Technical Expertise</h3>
      <div class="expertise-list fade-in">
        <div class="expertise-item">
          <h4>Programming Languages</h4>
          <p>Java for application development and problem-solving</p>
        </div>
        <div class="expertise-item">
          <h4>Software Engineering</h4>
          <p>Principles of software design, testing, and maintenance</p>
        </div>
        <div class="expertise-item">
          <h4>Data Structures</h4>
          <p>Implementation of fundamental data structures and algorithms</p>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- PROCESS -->
<div class="process-section">
  <div class="process-inner">
    <p class="section-label">How I Work</p>
    <h2 class="section-title">Professional Approach</h2>
    <div class="process-steps fade-in">
      <div class="step">
        <div class="step-num">01</div>
        <h4>Analyse Requirements</h4>
        <p>Understand project goals and technical specifications</p>
      </div>
      <div class="step">
        <div class="step-num">02</div>
        <h4>Design Solutions</h4>
        <p>Create efficient architecture and implementation plans</p>
      </div>
      <div class="step">
        <div class="step-num">03</div>
        <h4>Develop Code</h4>
        <p>Write clean, maintainable, and well-documented code</p>
      </div>
      <div class="step">
        <div class="step-num">04</div>
        <h4>Test &amp; Refine</h4>
        <p>Ensure quality through testing and continuous improvement</p>
      </div>
    </div>
  </div>
</div>

<!-- WHAT I BRING -->
<section>
  <p class="section-label">Value</p>
  <h2 class="section-title">What I Bring to Your Team</h2>
  <div class="bring-grid fade-in">
    <div class="bring-card">
      <h3>Technical Foundation</h3>
      <p>Strong understanding of computer science fundamentals and software engineering principles from a reputable university programme.</p>
    </div>
    <div class="bring-card">
      <h3>Learning Mindset</h3>
      <p>Committed to continuous learning and adapting to new technologies and industry best practices.</p>
    </div>
  </div>
  <h3 style="font-family:'Playfair Display',serif;font-size:1.5rem;margin-bottom:28px;">Areas of Interest</h3>
  <div class="interests fade-in">
    <div class="interest-card">
      <div class="ic-icon">⚙️</div>
      <h4>Backend Development</h4>
      <p>Building robust server-side applications and APIs using Java and related technologies.</p>
    </div>
    <div class="interest-card">
      <div class="ic-icon">🏗️</div>
      <h4>Software Architecture</h4>
      <p>Designing scalable and maintainable software systems with clean code practices.</p>
    </div>
    <div class="interest-card">
      <div class="ic-icon">🔍</div>
      <h4>Problem Solving</h4>
      <p>Tackling complex technical challenges with analytical thinking and creative solutions.</p>
    </div>
  </div>
</section>

<!-- EDUCATION -->
<section id="education" style="padding-top:0;">
  <p class="section-label">Background</p>
  <h2 class="section-title">Education</h2>
  <div class="edu-card fade-in">
    <div class="edu-num">1</div>
    <div class="edu-info">
      <h3>Guru Gobind Singh Indraprastha University</h3>
      <div class="degree">Bachelor of Technology — BTech</div>
      <div class="field">Computer Software Engineering</div>
      <div class="location">📍 Delhi, India</div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<div class="contact-section" id="contact">
  <div class="contact-inner">
    <p class="section-label">Get In Touch</p>
    <h2 class="section-title">Let's Connect</h2>
    <div class="contact-grid fade-in">
      <div class="contact-text">
        <p>I am always interested in discussing new opportunities, collaborations, and learning experiences. Whether you have a project in mind or simply want to exchange ideas about software development, I would love to hear from you.</p>
        <div class="contact-methods">
          <div class="contact-method" onclick="copyEmail()" style="cursor:pointer;">
            <div class="contact-method-icon">✉️</div>
            <div style="flex:1;">
              <div class="contact-method-label">Email — Click to Copy</div>
              <div class="contact-method-value">Khushigupta1830@gmail.com</div>
            </div>
            <div id="copy-badge" style="font-size:0.75rem;background:var(--accent);color:var(--btn-primary-text);padding:4px 10px;border-radius:20px;opacity:0;transition:opacity 0.3s;white-space:nowrap;">Copied! ✓</div>
          </div>
          <a href="https://www.linkedin.com/in/khushi-gupta-288208335" target="_blank" class="contact-method">
            <div class="contact-method-icon">🔗</div>
            <div>
              <div class="contact-method-label">LinkedIn</div>
              <div class="contact-method-value">linkedin.com/in/khushi-gupta-288208335</div>
            </div>
          </a>
          <a href="https://github.com/Khushigupta1830" target="_blank" class="contact-method">
            <div class="contact-method-icon">🐙</div>
            <div>
              <div class="contact-method-label">GitHub</div>
              <div class="contact-method-value">github.com/Khushigupta1830</div>
            </div>
          </a>
        </div>
      </div>
      <div class="ready-card">
        <h3 style="font-family:'Playfair Display',serif;font-size:1.4rem;margin-bottom:16px;">Ready to Contribute</h3>
        <p>As a recent Computer Software Engineering graduate with a strong foundation in Java and software development principles, I am excited to begin my career. I bring fresh perspectives, dedication to quality, and a genuine passion for creating software solutions.</p>
        <div class="btns">
          <button onclick="copyEmail()" class="btn btn-primary">✉ Copy Email</button>
          <a href="https://www.linkedin.com/in/khushi-gupta-288208335" target="_blank" class="btn btn-ghost">↗ LinkedIn</a>
          <a href="https://github.com/Khushigupta1830" target="_blank" class="btn btn-ghost">⌥ GitHub</a>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <p>© 2024 Khushi Gupta &nbsp;·&nbsp; Computer Software Engineer &nbsp;·&nbsp; Delhi, India</p>
  <p style="margin-top:10px;display:flex;justify-content:center;gap:24px;flex-wrap:wrap;">
    <a onclick="copyEmail()" style="color:var(--accent);text-decoration:none;cursor:pointer;">✉ Copy Email</a>
    <a href="https://www.linkedin.com/in/khushi-gupta-288208335" target="_blank" style="color:var(--accent);text-decoration:none;">🔗 LinkedIn</a>
    <a href="https://github.com/Khushigupta1830" target="_blank" style="color:var(--accent);text-decoration:none;">🐙 GitHub</a>
  </p>
</footer>

<script>
  // Copy Email
  function copyEmail() {
    navigator.clipboard.writeText('Khushigupta1830@gmail.com').then(() => {
      const badge = document.getElementById('copy-badge');
      if (badge) {
        badge.style.opacity = '1';
        setTimeout(() => badge.style.opacity = '0', 2500);
      }
      // Also show alert as backup
      const btn = event && event.target;
      const original = btn ? btn.textContent : '';
      if (btn && btn.textContent) {
        btn.textContent = '✓ Copied!';
        setTimeout(() => btn.textContent = original, 2000);
      }
    }).catch(() => {
      prompt('Copy this email:', 'Khushigupta1830@gmail.com');
    });
  }

  // Scroll fade-in
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); }
    });
  }, { threshold: 0.12 });
  document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

  // Theme switcher
  const html = document.documentElement;
  const btns = document.querySelectorAll('.theme-btn');

  function setTheme(mode) {
    html.setAttribute('data-theme', mode);
    btns.forEach(b => b.classList.toggle('active', b.dataset.mode === mode));
    try { localStorage.setItem('kg-theme', mode); } catch(e) {}
  }

  btns.forEach(btn => btn.addEventListener('click', () => setTheme(btn.dataset.mode)));

  // Restore saved theme on load
  try {
    const saved = localStorage.getItem('kg-theme');
    if (saved) setTheme(saved);
  } catch(e) {}
</script>
</body>
</html>