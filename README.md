<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>ARISE Robotics Club</title>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;500;600;700&family=Exo+2:ital,wght@0,300;0,400;0,600;0,900;1,400&display=swap" rel="stylesheet"/>
<style>
  :root {
  --bg: #0f1835;
  --bg2: #182449;
  --card: #22315f;

  --accent: #F5B041;
  --accent2: #D89B2D;
  --accent3: #FFCA66;

  --text: #F8F8F8;
  --muted: #BFC7D9;

  --border: rgba(245,176,65,0.18);
  --glow: 0 0 24px rgba(245,176,65,0.35);
}

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Exo 2', sans-serif;
    overflow-x: hidden;
  }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 5px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 3px; }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 9999; opacity: 0.4;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 5vw;
    height: 64px;
    background: rgba(11, 17, 30, 0.85);
    backdrop-filter: blur(14px);
    border-bottom: 1px solid var(--border);
    transition: all 0.3s ease;
    
  nav.scrolled {
  box-shadow: 0 4px 40px rgba(245,176,65,0.2);
}

  .nav-logo {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700;
    font-size: 1.6rem;
    letter-spacing: 3px;
    color: var(--accent);
    text-shadow: var(--glow);
    cursor: pointer;
  }
  .nav-logo span { color: var(--accent2); }

  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    text-decoration: none;
    color: var(--muted);
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    letter-spacing: 1px;
    font-size: 0.95rem;
    text-transform: uppercase;
    position: relative;
    transition: color 0.3s;
  }
  .nav-links a::after {
    content: '';
    position: absolute; bottom: -4px; left: 0; right: 0;
    height: 2px; background: var(--accent);
    transform: scaleX(0); transition: transform 0.3s ease;
    transform-origin: center;
  }
  .nav-links a:hover { color: var(--accent); }
  .nav-links a:hover::after { transform: scaleX(1); }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center; justify-content: center;
    position: relative; overflow: hidden;
    padding-top: 64px;
  }

  .hero-grid {
    position: absolute; inset: 0;
    background-image:
     linear-gradient(rgba(245,176,65,0.08) 1px, transparent 1px),
linear-gradient(90deg, rgba(245,176,65,0.08) 1px, transparent 1px);
    background-size: 60px 60px;
    animation: gridPulse 8s ease-in-out infinite;
  }
  @keyframes gridPulse {
    0%,100% { opacity: 0.4; }
    50% { opacity: 0.8; }
  }

  .hero-glow {
    position: absolute;
    width: 700px; height: 700px;
    background: radial-gradient(circle,
rgba(245,176,65,0.15) 0%, transparent 70%);
    top: 50%; left: 50%; transform: translate(-50%,-50%);
    animation: glowPulse 5s ease-in-out infinite;
  }
  @keyframes glowPulse {
    0%,100% { transform: translate(-50%,-50%) scale(1); opacity: 0.6; }
    50% { transform: translate(-50%,-50%) scale(1.15); opacity: 1; }
  }

  .hero-content {
    position: relative; z-index: 2;
    text-align: center; max-width: 900px; padding: 0 2rem;
  }

  .hero-tag {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(243, 169, 59, 0.08);
    border: 1px solid var(--border);
    border-radius: 100px;
    padding: 6px 18px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.8rem;
    letter-spacing: 2px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 2rem;
    animation: fadeUp 0.6s ease both;
  }
  .hero-tag::before {
    content: '';
    width: 6px; height: 6px;
    background: var(--accent);
    border-radius: 50%;
    box-shadow: 0 0 8px var(--accent);
    animation: blink 1.5s ease-in-out infinite;
  }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  .hero-title {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700;
    font-size: clamp(3.5rem, 10vw, 7rem);
    line-height: 0.95;
    letter-spacing: -2px;
    color: var(--text);
    animation: fadeUp 0.6s 0.1s ease both;
  }
  .hero-title .glow-text {
    color: var(--accent);
    text-shadow:
0 0 30px rgba(245,176,65,0.6),
0 0 60px rgba(245,176,65,0.3);
  .hero-title .white-text { color: var(--accent2); }

  .hero-sub {
    margin-top: 1.5rem;
    font-size: 1.15rem;
    color: var(--muted);
    line-height: 1.7;
    max-width: 580px; margin-left: auto; margin-right: auto;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .hero-btns {
    margin-top: 2.5rem;
    display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 14px 32px;
    border-radius: 4px;
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700;
    font-size: 1rem;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    text-decoration: none;
    cursor: pointer;
    border: none;
    transition: all 0.3s ease;
    position: relative; overflow: hidden;
  }
  .btn-primary {
    background: var(--accent);
    color: var(--bg);
    box-shadow: 0 0 20px rgba(245,176,65,0.4); 
  }
  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 30px rgba(0,229,255,0.6);
  }
  .btn-outline {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-outline:hover {
    border-color: var(--accent);
    color: var(--accent);
    transform: translateY(-3px);
    box-shadow: 0 4px 20px rgba(243, 169, 59, 0.15);
  }

  .hero-stats {
    margin-top: 4rem;
    display: flex; gap: 3rem; justify-content: center; flex-wrap: wrap;
    animation: fadeUp 0.6s 0.4s ease both;
  }
  .stat { text-align: center; }
  .stat-num {
    font-family: 'Rajdhani', sans-serif;
    font-size: 2.2rem; font-weight: 700;
    color: var(--accent);
    text-shadow: 0 0 20px rgba(243, 169, 59, 0.4);
  }
  .stat-label {
    font-size: 0.8rem; color: var(--muted);
    letter-spacing: 1px; text-transform: uppercase;
    margin-top: 2px;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ── SECTION BASE ── */
  section {
    padding: 100px 5vw;
    position: relative;
  }

  .section-label {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.75rem;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 0.8rem;
    display: flex; align-items: center; gap: 10px;
  }
  .section-label::before {
    content: ''; width: 30px; height: 1px;
    background: var(--accent);
  }

  .section-title {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700;
    font-size: clamp(2rem, 5vw, 3.2rem);
    line-height: 1.1;
    margin-bottom: 1.5rem;
  }

  .section-desc {
    color: var(--muted);
    font-size: 1.05rem;
    line-height: 1.8;
    max-width: 600px;
  }

  /* ── ABOUT ── */
  #about { background: var(--bg2); }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5rem;
    align-items: center;
    max-width: 1200px; margin: 0 auto;
  }

  .about-visual {
    position: relative;
    height: 420px;
  }
  .about-box {
    position: absolute;
    border: 1px solid var(--border);
    border-radius: 8px;
    background: var(--card);
    display: flex; align-items: center; justify-content: center;
    font-size: 2.5rem;
    box-shadow: 0 0 30px rgba(245,176,65,0.08);
    transition: all 0.5s ease;
  }
  .about-box:hover {
    border-color: var(--accent);
    box-shadow: var(--glow);
    transform: scale(1.05);
  }
  .ab1 { width: 200px; height: 200px; top: 0; left: 0; }
  .ab2 { width: 160px; height: 160px; top: 60px; right: 0; border-color: rgba(255,255,255,0.2); }
  .ab3 { width: 130px; height: 130px; bottom: 0; left: 40px; border-color: rgba(243, 169, 59,0.3); }
  .ab4 { width: 110px; height: 110px; bottom: 40px; right: 60px; }

  .about-line {
    position: absolute;
    background: linear-gradient(90deg, var(--accent), transparent);
    height: 1px; opacity: 0.4;
  }
  .al1 { width: 80px; top: 100px; left: 200px; }
  .al2 { width: 60px; top: 150px; right: 160px; transform: rotate(-30deg); }

  .timeline { margin-top: 2.5rem; }
  .timeline-item {
    display: flex; gap: 1.2rem;
    padding: 1rem 0;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    cursor: default;
    transition: all 0.3s;
  }
  .timeline-item:hover { padding-left: 8px; }
  .t-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 8px var(--accent);
    flex-shrink: 0; margin-top: 6px;
    transition: transform 0.3s;
  }
  .timeline-item:hover .t-dot { transform: scale(1.5); }
  .t-year {
    font-family: 'Rajdhani', sans-serif;
    color: var(--accent); font-weight: 700;
    font-size: 0.85rem; letter-spacing: 1px;
  }
  .t-text { font-size: 0.95rem; line-height: 1.6; }
  .t-title { font-weight: 600; color: var(--text); }
  .t-desc { color: var(--muted); font-size: 0.88rem; margin-top: 2px; }

  /* ── ROBOTS ── */
  #robots { background: var(--bg); }

  .robots-header {
    text-align: center; margin-bottom: 4rem;
    max-width: 700px; margin-left: auto; margin-right: auto;
  }
  .robots-header .section-label { justify-content: center; }
  .robots-header .section-label::before { display: none; }

  .robots-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
    max-width: 1200px; margin: 0 auto;
  }

  .robot-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.4s ease;
    position: relative;
  }
  .robot-card:hover {
    border-color: var(--accent);
    transform: translateY(-8px);
    box-shadow: 0 20px 60px rgba(0,0,0,0.4), var(--glow);
  }

  .robot-visual {
    height: 200px;
    display: flex; align-items: center; justify-content: center;
    position: relative; overflow: hidden;
    font-size: 5rem;
    background: linear-gradient(135deg,rgba(245,176,65,0.12),transparent);
  }
  .robot-visual::before {
    content: '';
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(245,176,65,0.08) 1px, transparent 1px),
      linear-gradient(90deg, rgba(245,176,65,0.08) 1px, transparent 1px);
    background-size: 30px 30px;
  }
  .robot-emoji {
    position: relative; z-index: 1;
    transition: transform 0.4s ease;
    filter: drop-shadow(0 0 20px rgba(245,176,65,0.4));
  }
  .robot-card:hover .robot-emoji { transform: scale(1.15) rotate(-5deg); }

  .robot-badge {
    position: absolute; top: 12px; right: 12px;
    background: rgba(243, 169, 59, 0.1);
    border: 1px solid var(--border);
    border-radius: 100px;
    padding: 3px 10px;
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.7rem;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--accent);
  }

  .robot-body { padding: 1.5rem; }
  .robot-name {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700; font-size: 1.4rem;
    letter-spacing: 1px; margin-bottom: 0.5rem;
  }
  .robot-desc { color: var(--muted); font-size: 0.9rem; line-height: 1.6; }

  .robot-tags {
    display: flex; flex-wrap: wrap; gap: 6px; margin-top: 1rem;
  }
  .robot-tag {
    background: rgba(243, 169, 59, 0.1);
    border: 1px solid rgba(243, 169, 59, 0.25);
    border-radius: 4px;
    padding: 2px 10px;
    font-size: 0.75rem;
    color: var(--accent);
    font-family: 'Rajdhani', sans-serif;
    letter-spacing: 0.5px;
  }

  .robot-footer {
    margin-top: 1.2rem;
    padding-top: 1rem;
    border-top: 1px solid rgba(255,255,255,0.05);
    display: flex; align-items: center; justify-content: space-between;
  }
  .robot-status {
    display: flex; align-items: center; gap: 6px;
    font-size: 0.8rem; color: #f3a93b;
    font-family: 'Rajdhani', sans-serif; letter-spacing: 1px;
  }
  .status-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: #f3a93b;
    box-shadow: 0 0 6px #f3a93b;
    animation: blink 2s ease-in-out infinite;
  }
  .robot-arrow {
    color: var(--accent); font-size: 1.2rem;
    transition: transform 0.3s;
  }
  .robot-card:hover .robot-arrow { transform: translateX(6px); }

  /* ── COMPETITIONS ── */
  #competitions { background: var(--bg2); }

  .comp-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
    max-width: 1200px; margin: 3rem auto 0;
  }

  .comp-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 2rem;
    transition: all 0.4s ease;
    position: relative; overflow: hidden;
    cursor: default;
  }
  .comp-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    transform: scaleX(0); transition: transform 0.4s ease;
    transform-origin: left;
  }
  .comp-card:hover::before { transform: scaleX(1); }
  .comp-card:hover {
    border-color: rgba(243, 169, 59, 0.3);
    transform: translateY(-5px);
    box-shadow: 0 15px 40px rgba(0,0,0,0.3);
  }

  .comp-icon { font-size: 2.5rem; margin-bottom: 1rem; }
  .comp-name {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700; font-size: 1.25rem;
    letter-spacing: 0.5px; margin-bottom: 0.5rem;
  }
  .comp-desc { color: var(--muted); font-size: 0.88rem; line-height: 1.6; }

  /* ── MEMBERS ── */
  #team { background: var(--bg); }

  .team-header { text-align: center; margin-bottom: 3rem; }
  .team-header .section-label { justify-content: center; }
  .team-header .section-label::before { display: none; }

  .team-grid {
    display: flex; flex-wrap: wrap; gap: 1.5rem;
    justify-content: center;
    max-width: 1200px; margin: 0 auto;
  }

  .member-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 2rem 1.5rem;
    text-align: center;
    width: 200px;
    transition: all 0.4s ease;
    cursor: default;
  }
  .member-card:hover {
    border-color: var(--accent);
    transform: translateY(-6px);
    box-shadow: var(--glow);
  }

  .member-avatar {
    width: 72px; height: 72px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--card));
    display: flex; align-items: center; justify-content: center;
    font-size: 1.8rem;
    margin: 0 auto 1rem;
    border: 2px solid var(--border);
    transition: all 0.3s;
  }
  .member-card:hover .member-avatar {
    border-color: var(--accent);
    box-shadow: 0 0 20px rgba(243, 169, 59, 0.4);
    transform: scale(1.08);
  }
  .member-name {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700; font-size: 1rem;
    letter-spacing: 0.5px;
  }
  .member-role {
    font-size: 0.78rem; color: var(--accent);
    font-family: 'Rajdhani', sans-serif;
    letter-spacing: 1px; text-transform: uppercase;
    margin-top: 4px;
  }

  /* ── JOIN ── */
  #join {
    background: var(--bg2);
    text-align: center;
  }
  .join-inner {
    max-width: 700px; margin: 0 auto;
    position: relative;
  }
  .join-glow {
    position: absolute;
    width: 500px; height: 300px;
    background: radial-gradient(ellipse,rgba(245,176,65,0.12) 0%,transparent 70%);
    top: 50%; left: 50%;
    transform: translate(-50%,-50%);
    pointer-events: none;
  }
  .join-inner > * { position: relative; z-index: 1; }
  .join-title {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700;
    font-size: clamp(2rem, 5vw, 3rem);
    margin-bottom: 1rem;
  }
  .join-sub { color: var(--muted); font-size: 1rem; line-height: 1.7; margin-bottom: 2.5rem; }

  /* ── FOOTER ── */
  footer {
    background: var(--bg);
    border-top: 1px solid var(--border);
    padding: 2.5rem 5vw;
    display: flex; align-items: center; justify-content: space-between;
    flex-wrap: wrap; gap: 1rem;
  }
  .footer-logo {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700; font-size: 1.3rem;
    letter-spacing: 3px;
    color: var(--accent);
  }
  .footer-copy { color: var(--muted); font-size: 0.82rem; }

  /* ── MODAL ── */
  .modal-overlay {
    position: fixed; inset: 0;
    background: rgba(11, 17, 30, 0.85);
    backdrop-filter: blur(8px);
    z-index: 200;
    display: flex; align-items: center; justify-content: center;
    padding: 1rem;
    opacity: 0; pointer-events: none;
    transition: opacity 0.3s ease;
  }
  .modal-overlay.open { opacity: 1; pointer-events: all; }

  .modal {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    width: 100%; max-width: 520px;
    padding: 2.5rem;
    position: relative;
    transform: translateY(20px) scale(0.97);
    transition: all 0.3s ease;
    box-shadow: 0 30px 80px rgba(0,0,0,0.5), var(--glow);
  }
  .modal-overlay.open .modal { transform: translateY(0) scale(1); }

  .modal-close {
    position: absolute; top: 1rem; right: 1rem;
    background: none; border: none; color: var(--muted);
    font-size: 1.5rem; cursor: pointer;
    transition: color 0.2s;
  }
  .modal-close:hover { color: var(--text); }

  .modal-icon { font-size: 3.5rem; margin-bottom: 1rem; text-align: center; }
  .modal-name {
    font-family: 'Rajdhani', sans-serif;
    font-weight: 700; font-size: 1.8rem;
    text-align: center; margin-bottom: 0.5rem;
  }
  .modal-badge {
    display: block; text-align: center;
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.8rem; letter-spacing: 2px; text-transform: uppercase;
    color: var(--accent); margin-bottom: 1.5rem;
  }
  .modal-desc {
    color: var(--muted); font-size: 0.95rem; line-height: 1.8;
    margin-bottom: 1.5rem;
  }
  .modal-specs {
    border-top: 1px solid var(--border); padding-top: 1.2rem;
  }
  .spec-row {
    display: flex; justify-content: space-between;
    padding: 0.5rem 0;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    font-size: 0.88rem;
  }
  .spec-key { color: var(--muted); }
  .spec-val { color: var(--text); font-family: 'Rajdhani', sans-serif; font-weight: 600; }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    .about-grid { grid-template-columns: 1fr; }
    .about-visual { display: none; }
    .nav-links { gap: 1rem; }
    .hero-stats { gap: 1.5rem; }
  }

  /* ── REVEAL ANIMATION ── */
  .reveal {
    opacity: 0; transform: translateY(40px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }
</style>
</head>
<body>

<!-- NAV -->
<nav id="navbar">
  <div class="nav-logo">A<span>R</span>ISE</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#robots">Robots</a></li>
    <li><a href="#competitions">Events</a></li>
    <li><a href="#team">Team</a></li>
    <li><a href="#join">Join</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-grid"></div>
  <div class="hero-glow"></div>
  <div class="hero-content">
    <div class="hero-tag">Robotics Club &bull; Est. 2022</div>
    <h1 class="hero-title">
      <span class="glow-text">ARISE</span><br>
      <span>Robotics</span> <span class="white-text">Club</span>
    </h1>
    <p class="hero-sub">Where innovation meets engineering. We design, build, and battle robots — from sumo warriors to precision line tracers.</p>
    <div class="hero-btns">
      <a href="#robots" class="btn btn-primary">⚙ Explore Robots</a>
      <a href="#about" class="btn btn-outline">Our Story</a>
    </div>
    <div class="hero-stats">
      <div class="stat">
        <div class="stat-num">3+</div>
        <div class="stat-label">Robot Types</div>
      </div>
      <div class="stat">
        <div class="stat-num">20+</div>
        <div class="stat-label">Members</div>
      </div>
      <div class="stat">
        <div class="stat-num">5+</div>
        <div class="stat-label">Competitions</div>
      </div>
      <div class="stat">
        <div class="stat-num">∞</div>
        <div class="stat-label">Ideas</div>
      </div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="about-grid">
    <div>
      <div class="section-label reveal">Our Story</div>
      <h2 class="section-title reveal reveal-delay-1">Born from a passion<br>for <span style="color:var(--accent)">building</span> things.</h2>
      <p class="section-desc reveal reveal-delay-2">ARISE was founded by a small group of students who believed that engineering wasn't just a subject — it was a mindset. We built our first robot with spare parts and a whole lot of determination, and we haven't stopped since.</p>
      <div class="timeline reveal reveal-delay-3">
        <div class="timeline-item">
          <div class="t-dot"></div>
          <div>
            <div class="t-year">2022</div>
            <div class="t-title">Club Founded</div>
            <div class="t-desc">ARISE was established with 8 founding members and a shared dream.</div>
          </div>
        </div>
        <div class="timeline-item">
          <div class="t-dot"></div>
          <div>
            <div class="t-year">2023</div>
            <div class="t-title">First Competition</div>
            <div class="t-desc">We entered our first Sumo Bot competition and placed in the top 5.</div>
          </div>
        </div>
        <div class="timeline-item">
          <div class="t-dot"></div>
          <div>
            <div class="t-year">2024</div>
            <div class="t-title">Expanding the Fleet</div>
            <div class="t-desc">Added line tracing and innovation projects to our growing roster.</div>
          </div>
        </div>
        <div class="timeline-item">
          <div class="t-dot"></div>
          <div>
            <div class="t-year">2025</div>
            <div class="t-title">Growing Strong</div>
            <div class="t-desc">20+ active members, multiple medals, and bigger dreams ahead.</div>
          </div>
        </div>
      </div>
    </div>
    <div class="about-visual reveal">
      <div class="about-box ab1">🤖</div>
      <div class="about-box ab2">⚡</div>
      <div class="about-box ab3">🏆</div>
      <div class="about-box ab4">🔧</div>
      <div class="about-line al1"></div>
      <div class="about-line al2"></div>
    </div>
  </div>
</section>

<!-- ROBOTS -->
<section id="robots">
  <div class="robots-header">
    <div class="section-label reveal">Our Fleet</div>
    <h2 class="section-title reveal reveal-delay-1">Meet the <span style="color:var(--accent)">Robots</span></h2>
    <p class="section-desc reveal reveal-delay-2" style="margin:0 auto;text-align:center;">Each robot is designed, built, and programmed by our members. Click on any robot to learn more.</p>
  </div>

  <div class="robots-grid">
    <div class="robot-card reveal" onclick="openModal('sumo')">
      <div class="robot-visual">
        <div class="robot-badge">Combat</div>
        <span class="robot-emoji">🥊</span>
      </div>
      <div class="robot-body">
        <div class="robot-name">TITAN-X</div>
        <div class="robot-desc">Our heavyweight sumo bot built for pushing power and edge detection. Designed to dominate the ring.</div>
        <div class="robot-tags">
          <span class="robot-tag">Sumo Bot</span>
          <span class="robot-tag">IR Sensors</span>
          <span class="robot-tag">High Torque</span>
        </div>
        <div class="robot-footer">
          <div class="robot-status"><div class="status-dot"></div>Competition Ready</div>
          <div class="robot-arrow">→</div>
        </div>
      </div>
    </div>

    <div class="robot-card reveal reveal-delay-1" onclick="openModal('line')">
      <div class="robot-visual">
        <div class="robot-badge">Precision</div>
        <span class="robot-emoji">🏎️</span>
      </div>
      <div class="robot-body">
        <div class="robot-name">SWIFT-7</div>
        <div class="robot-desc">A lightning-fast line follower that navigates complex tracks using PID-tuned algorithms and array sensors.</div>
        <div class="robot-tags">
          <span class="robot-tag">Line Tracer</span>
          <span class="robot-tag">PID Control</span>
          <span class="robot-tag">Speed Tuned</span>
        </div>
        <div class="robot-footer">
          <div class="robot-status"><div class="status-dot"></div>Active Build</div>
          <div class="robot-arrow">→</div>
        </div>
      </div>
    </div>

    <div class="robot-card reveal reveal-delay-2" onclick="openModal('innovation')">
      <div class="robot-visual">
        <div class="robot-badge">Innovation</div>
        <span class="robot-emoji">🔬</span>
      </div>
      <div class="robot-body">
        <div class="robot-name">NEXUS-1</div>
        <div class="robot-desc">Our flagship innovation project — an autonomous robot exploring real-world problem solving using sensors and AI logic.</div>
        <div class="robot-tags">
          <span class="robot-tag">Autonomous</span>
          <span class="robot-tag">Sensor Fusion</span>
          <span class="robot-tag">Innovation</span>
        </div>
        <div class="robot-footer">
          <div class="robot-status"><div class="status-dot"></div>In Development</div>
          <div class="robot-arrow">→</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- COMPETITIONS -->
<section id="competitions">
  <div class="section-label reveal">What We Do</div>
  <h2 class="section-title reveal reveal-delay-1">Competitions &amp; <span style="color:var(--accent)">Events</span></h2>
  <p class="section-desc reveal reveal-delay-2">We compete across multiple robotics disciplines, pushing our skills further with every event.</p>

  <div class="comp-grid">
    <div class="comp-card reveal">
      <div class="comp-icon">⚔️</div>
      <div class="comp-name">Sumo Bot</div>
      <div class="comp-desc">Head-to-head battles where robots push each other out of a circular ring. Strength, strategy, and sensor speed.</div>
    </div>
    <div class="comp-card reveal reveal-delay-1">
      <div class="comp-icon">〰️</div>
      <div class="comp-name">Line Tracing</div>
      <div class="comp-desc">Race through winding tracks following a black line as fast and as precisely as possible. Every millisecond counts.</div>
    </div>
    <div class="comp-card reveal reveal-delay-2">
      <div class="comp-icon">💡</div>
      <div class="comp-name">Innovation Challenge</div>
      <div class="comp-desc">Design a robot that solves a real-world problem. Judged on creativity, functionality, and presentation.</div>
    </div>
    <div class="comp-card reveal reveal-delay-3">
      <div class="comp-icon">🛠️</div>
      <div class="comp-name">Build Workshops</div>
      <div class="comp-desc">Regular internal sessions where members learn new skills — soldering, coding, mechanical design, and more.</div>
    </div>
  </div>
</section>

<!-- TEAM -->
<section id="team">
  <div class="team-header">
    <div class="section-label reveal">The People</div>
    <h2 class="section-title reveal reveal-delay-1">Our <span style="color:var(--accent)">Team</span></h2>
    <p class="section-desc reveal reveal-delay-2" style="margin:0 auto;text-align:center;">Every great robot starts with great people.</p>
  </div>
  <div class="team-grid">
    <div class="member-card reveal">
      <div class="member-avatar">👾</div>
      <div class="member-name">Club President</div>
      <div class="member-role">Leadership</div>
    </div>
    <div class="member-card reveal reveal-delay-1">
      <div class="member-avatar">🔧</div>
      <div class="member-name">Head Engineer</div>
      <div class="member-role">Hardware</div>
    </div>
    <div class="member-card reveal reveal-delay-2">
      <div class="member-avatar">💻</div>
      <div class="member-name">Lead Programmer</div>
      <div class="member-role">Software</div>
    </div>
    <div class="member-card reveal reveal-delay-3">
      <div class="member-avatar">📐</div>
      <div class="member-name">Design Lead</div>
      <div class="member-role">Mechanical</div>
    </div>
    <div class="member-card reveal">
      <div class="member-avatar">📡</div>
      <div class="member-name">Electronics Lead</div>
      <div class="member-role">Circuits & PCB</div>
    </div>
  </div>
</section>

<!-- JOIN -->
<section id="join">
  <div class="join-inner">
    <div class="join-glow"></div>
    <div class="section-label reveal" style="justify-content:center">
      <span style="display:inline-flex;align-items:center;gap:10px">Get Involved</span>
    </div>
    <h2 class="join-title reveal reveal-delay-1">Ready to <span style="color:var(--accent)">ARISE</span>?</h2>
    <p class="join-sub reveal reveal-delay-2">Whether you're into coding, building, or just want to see robots fight — there's a place for you in ARISE. Come join the team and build something incredible.</p>
    <div class="reveal reveal-delay-3">
      <a href="mailto:arise.robotics@email.com" class="btn btn-primary" style="margin-right:1rem">✉ Get In Touch</a>
      <a href="#robots" class="btn btn-outline">⚙ See Our Robots</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">ARISE</div>
  <div class="footer-copy">© 2025 ARISE Robotics Club. Built by engineers, for engineers.</div>
</footer>

<!-- ROBOT MODAL -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
  <div class="modal" id="modal">
    <button class="modal-close" onclick="closeModalBtn()">✕</button>
    <div id="modal-content"></div>
  </div>
</div>

<script>
  // ── NAV SCROLL ──
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 40);
  });

  // ── REVEAL ON SCROLL ──
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); }
    });
  }, { threshold: 0.12 });
  reveals.forEach(r => observer.observe(r));

  // ── MODAL DATA ──
  const robots = {
    sumo: {
      icon: '🥊',
      name: 'TITAN-X',
      badge: 'Sumo Bot · Combat Division',
      desc: 'TITAN-X is our premier combat robot built for sumo competitions. Its low center of gravity and high-torque motors deliver maximum pushing force, while IR sensors detect the ring edges to prevent accidental exit. The wedge design forces opponents upward and out of the ring.',
      specs: [
        ['Weight Class', 'Lightweight (500g)'],
        ['Drive System', 'Differential Drive'],
        ['Sensors', 'IR Edge Detection x4'],
        ['Microcontroller', 'Arduino Nano'],
        ['Top Speed', '0.8 m/s'],
        ['Material', 'ABS + Aluminum Frame'],
      ]
    },
    line: {
      icon: '🏎️',
      name: 'SWIFT-7',
      badge: 'Line Follower · Precision Division',
      desc: 'SWIFT-7 is engineered for speed and precision. It uses a 5-sensor array to read the track and a PID control loop to make real-time micro-corrections. Tuned for tight curves and straight-line bursts, SWIFT-7 consistently ranks among the fastest entries in competitions.',
      specs: [
        ['Sensor Array', '5-Channel IR Reflective'],
        ['Control Algorithm', 'PID (Kp, Ki, Kd tuned)'],
        ['Motors', 'N20 Gear Motors 1000RPM'],
        ['Microcontroller', 'STM32 / Arduino'],
        ['Track Width', '150mm wheelbase'],
        ['Battery', 'LiPo 7.4V 800mAh'],
      ]
    },
    innovation: {
      icon: '🔬',
      name: 'NEXUS-1',
      badge: 'Innovation Project · R&D Division',
      desc: 'NEXUS-1 is our most ambitious project yet — an autonomous robot designed to solve a real-world challenge. It combines ultrasonic, infrared, and environmental sensors with a custom logic system to navigate and make decisions independently. Currently in active development by the club.',
      specs: [
        ['Project Type', 'Autonomous Navigation'],
        ['Sensors', 'Ultrasonic + IR + Env.'],
        ['Microcontroller', 'ESP32 (Wi-Fi enabled)'],
        ['Status', 'In Development 🔨'],
        ['Target Event', 'Innovation Challenge 2026'],
        ['Team Size', '6 Members'],
      ]
    }
  };

  function openModal(id) {
    const r = robots[id];
    const specs = r.specs.map(([k,v]) => `
      <div class="spec-row">
        <span class="spec-key">${k}</span>
        <span class="spec-val">${v}</span>
      </div>`).join('');

    document.getElementById('modal-content').innerHTML = `
      <div class="modal-icon">${r.icon}</div>
      <div class="modal-name">${r.name}</div>
      <span class="modal-badge">${r.badge}</span>
      <div class="modal-desc">${r.desc}</div>
      <div class="modal-specs">${specs}</div>
    `;
    document.getElementById('modalOverlay').classList.add('open');
    document.body.style.overflow = 'hidden';
  }

  function closeModal(e) {
    if (e.target === document.getElementById('modalOverlay')) closeModalBtn();
  }
  function closeModalBtn() {
    document.getElementById('modalOverlay').classList.remove('open');
    document.body.style.overflow = '';
  }
  document.addEventListener('keydown', e => {
    if (e.key === 'Escape') closeModalBtn();
  });
</script>
</body>
</html>
