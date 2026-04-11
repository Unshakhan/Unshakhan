<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Unsha | Frontend Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;700;800&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Syne', sans-serif;
    background: #f5f4f1;
    color: #1a1a1a;
    min-height: 100vh;
    padding: 2rem 1rem;
  }

  .readme-wrap {
    max-width: 860px;
    margin: 0 auto;
    padding: 2rem 1.5rem 3rem;
  }

  /* === Animations === */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }
  @keyframes slideRight {
    from { opacity: 0; transform: translateX(-20px); }
    to   { opacity: 1; transform: translateX(0); }
  }
  @keyframes popIn {
    from { opacity: 0; transform: scale(0.8); }
    to   { opacity: 1; transform: scale(1); }
  }
  @keyframes float {
    0%,100% { transform: translateY(0px); }
    50%     { transform: translateY(-6px); }
  }
  @keyframes shimmer {
    0%   { background-position: -200% center; }
    100% { background-position:  200% center; }
  }
  @keyframes blink {
    0%,100% { opacity: 1; }
    50%     { opacity: 0; }
  }
  @keyframes pulse {
    0%,100% { transform: scale(1); }
    50%     { transform: scale(1.08); }
  }

  .fade-up { opacity: 0; animation: fadeUp 0.6s ease forwards; }
  .d1 { animation-delay: 0.1s; }
  .d2 { animation-delay: 0.3s; }
  .d3 { animation-delay: 0.5s; }
  .d4 { animation-delay: 0.7s; }
  .d5 { animation-delay: 0.9s; }

  /* === Hero === */
  .hero {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    align-items: center;
    margin-bottom: 2.5rem;
    background: #ffffff;
    border: 0.5px solid #ddd;
    border-radius: 16px;
    padding: 2rem;
  }

  .avatar-row {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 1.2rem;
  }

  .avatar-wrap { position: relative; }

  .avatar {
    width: 54px;
    height: 54px;
    border-radius: 50%;
    background: #EEEDFE;
    border: 2px solid #AFA9EC;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 800;
    font-size: 18px;
    color: #3C3489;
    animation: float 3s ease-in-out infinite;
  }

  .status-dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: #1D9E75;
    border: 2px solid #ffffff;
    position: absolute;
    bottom: 2px;
    right: 2px;
    animation: pulse 2s ease-in-out infinite;
  }

  .hero-name {
    font-size: 34px;
    font-weight: 800;
    line-height: 1.1;
    margin-bottom: 4px;
    background: linear-gradient(90deg, #534AB7, #7F77DD, #534AB7);
    background-size: 200% auto;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: shimmer 3s linear infinite;
  }

  .handle {
    font-size: 13px;
    color: #888;
    font-family: 'DM Mono', monospace;
  }

  /* === Typewriter === */
  .typewriter-wrap {
    display: flex;
    align-items: center;
    gap: 0;
    font-family: 'DM Mono', monospace;
    font-size: 14px;
    color: #534AB7;
    min-height: 22px;
    margin-bottom: 1.4rem;
    background: #EEEDFE;
    border: 0.5px solid #AFA9EC;
    border-radius: 8px;
    padding: 6px 12px;
    width: fit-content;
  }

  .prefix {
    color: #888;
    margin-right: 6px;
    font-size: 13px;
  }

  #typed-text {
    color: #534AB7;
    font-weight: 500;
  }

  .cursor {
    display: inline-block;
    width: 2px;
    height: 15px;
    background: #534AB7;
    margin-left: 2px;
    vertical-align: middle;
    animation: blink 0.8s step-end infinite;
  }

  /* === Info list === */
  .info-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .info-list li {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    font-size: 14px;
    opacity: 0;
    animation: slideRight 0.5s ease forwards;
  }
  .info-list li:nth-child(1) { animation-delay: 1.2s; }
  .info-list li:nth-child(2) { animation-delay: 1.4s; }
  .info-list li:nth-child(3) { animation-delay: 1.6s; }

  .info-icon {
    width: 28px;
    height: 28px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 14px;
    flex-shrink: 0;
    background: #f5f4f1;
    border: 0.5px solid #ddd;
  }

  /* === GIF side === */
  .hero-gif {
    border-radius: 14px;
    overflow: hidden;
    border: 0.5px solid #ddd;
    opacity: 0;
    animation: fadeIn 1s ease 0.3s forwards;
  }
  .hero-gif img { width: 100%; display: block; }

  /* === Badge row === */
  .badge-row {
    display: flex;
    gap: 8px;
    margin-bottom: 1rem;
    flex-wrap: wrap;
  }
  .badge {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 100px;
    background: #EEEDFE;
    color: #3C3489;
    border: 0.5px solid #AFA9EC;
    opacity: 0;
    animation: fadeIn 0.4s ease forwards;
  }
  .badge:nth-child(1) { animation-delay: 0.5s; }
  .badge:nth-child(2) { animation-delay: 0.7s; }

  /* === Section === */
  .section { margin-bottom: 2.5rem; }

  .section-label {
    font-size: 11px;
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.1em;
    color: #999;
    text-transform: uppercase;
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 0.5px;
    background: #ddd;
  }

  /* === Connect buttons === */
  .connect-row { display: flex; gap: 10px; flex-wrap: wrap; }

  .connect-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 16px;
    border-radius: 8px;
    background: #fff;
    border: 0.5px solid #ccc;
    font-size: 13px;
    font-weight: 500;
    color: #1a1a1a;
    text-decoration: none;
    font-family: 'Syne', sans-serif;
    transition: transform 0.2s ease, border-color 0.2s ease;
  }
  .connect-btn:hover { transform: translateY(-2px); border-color: #7F77DD; }
  .connect-btn svg { width: 16px; height: 16px; flex-shrink: 0; }

  /* === Skill bars === */
  .skill-bar-item { margin-bottom: 14px; }

  .skill-bar-label {
    display: flex;
    justify-content: space-between;
    font-size: 13px;
    margin-bottom: 6px;
    font-family: 'DM Mono', monospace;
    color: #555;
  }

  .skill-bar-track {
    height: 6px;
    background: #eee;
    border-radius: 100px;
    overflow: hidden;
    border: 0.5px solid #ddd;
  }

  .skill-bar-fill {
    height: 100%;
    border-radius: 100px;
    width: 0%;
    transition: width 1.4s cubic-bezier(0.4, 0, 0.2, 1);
  }

  /* === Tools grid === */
  .tools-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(96px, 1fr));
    gap: 10px;
  }

  .tool-card {
    background: #fff;
    border: 0.5px solid #ddd;
    border-radius: 10px;
    padding: 14px 10px 12px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    text-align: center;
    opacity: 0;
    transform: scale(0.85);
    transition: transform 0.2s ease, border-color 0.2s ease;
    cursor: default;
  }
  .tool-card.visible { animation: popIn 0.4s ease forwards; }
  .tool-card:hover { transform: scale(1.06) translateY(-3px); border-color: #7F77DD; }
  .tool-card img { width: 36px; height: 36px; object-fit: contain; }
  .tool-card span { font-size: 11px; font-family: 'DM Mono', monospace; color: #777; }

  /* === Fun fact === */
  .fun-fact {
    background: #EEEDFE;
    border: 0.5px solid #AFA9EC;
    border-radius: 14px;
    padding: 1rem 1.25rem;
    font-size: 14px;
    color: #3C3489;
    display: flex;
    align-items: center;
    gap: 10px;
    opacity: 0;
    animation: fadeUp 0.6s ease 2s forwards;
  }

  @media (max-width: 580px) {
    .hero { grid-template-columns: 1fr; }
    .hero-gif { display: none; }
    .hero-name { font-size: 26px; }
  }
</style>
</head>
<body>

<div class="readme-wrap">

  <!-- Hero -->
  <div class="hero fade-up d1">
    <div>
      <div class="badge-row">
        <span class="badge">frontend dev</span>
        <span class="badge">🇵🇰 pakistan</span>
      </div>

      <div class="avatar-row">
        <div class="avatar-wrap">
          <div class="avatar">US</div>
          <div class="status-dot"></div>
        </div>
        <div>
          <div class="hero-name">Hi, I'm Unsha 👋</div>
          <div class="handle">@unshakhan</div>
        </div>
      </div>

      <!-- Typewriter -->
      <div class="typewriter-wrap">
        <span class="prefix">I am a</span>
        <span id="typed-text"></span>
        <span class="cursor"></span>
      </div>

      <ul class="info-list">
        <li>
          <div class="info-icon">🌱</div>
          <span style="padding-top:4px;">Learning <strong>Web & App Dev</strong> at SMIT</span>
        </li>
        <li>
          <div class="info-icon">📫</div>
          <span style="padding-top:4px;color:#534AB7;">unshak08@gmail.com</span>
        </li>
        <li>
          <div class="info-icon">⚡</div>
          <span style="padding-top:4px;">I think I am funny 😎</span>
        </li>
      </ul>
    </div>

    <div class="hero-gif">
      <img src="https://mir-s3-cdn-cf.behance.net/project_modules/max_1200/81bb4b165684019.640b6038d133e.gif" alt="coding animation" />
    </div>
  </div>

  <!-- Connect -->
  <div class="section fade-up d2">
    <div class="section-label">connect with me</div>
    <div class="connect-row">
      <a class="connect-btn" href="https://linkedin.com/in/unsha-sattar-b544b8365" target="_blank">
        <svg viewBox="0 0 24 24" fill="#0077B5"><path d="M20.45 20.45h-3.56v-5.57c0-1.33-.03-3.04-1.85-3.04-1.85 0-2.13 1.45-2.13 2.94v5.67H9.35V9h3.41v1.56h.05c.48-.91 1.64-1.86 3.37-1.86 3.6 0 4.27 2.37 4.27 5.46v6.29zM5.34 7.43a2.07 2.07 0 1 1 0-4.14 2.07 2.07 0 0 1 0 4.14zM7.12 20.45H3.55V9h3.57v11.45zM22.22 0H1.77C.79 0 0 .77 0 1.72v20.56C0 23.23.79 24 1.77 24h20.45C23.21 24 24 23.23 24 22.28V1.72C24 .77 23.21 0 22.22 0z"/></svg>
        LinkedIn
      </a>
      <a class="connect-btn" href="mailto:unshak08@gmail.com">
        <svg viewBox="0 0 24 24" fill="#EA4335"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
        Email
      </a>
    </div>
  </div>

  <!-- Skills -->
  <div class="section fade-up d3">
    <div class="section-label">skill levels</div>
    <div id="skill-bars">
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>HTML5</span><span>90%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-w="90" style="background:#E24B4A;"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>CSS3</span><span>85%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-w="85" style="background:#185FA5;"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>JavaScript</span><span>70%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-w="70" style="background:#EF9F27;"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>Flutter / Dart</span><span>60%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-w="60" style="background:#5DCAA5;"></div></div>
      </div>
      <div class="skill-bar-item">
        <div class="skill-bar-label"><span>Photoshop</span><span>65%</span></div>
        <div class="skill-bar-track"><div class="skill-bar-fill" data-w="65" style="background:#534AB7;"></div></div>
      </div>
    </div>
  </div>

  <!-- Tools -->
  <div class="section fade-up d4">
    <div class="section-label">languages & tools</div>
    <div class="tools-grid" id="tools-grid">
      <div class="tool-card">
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="HTML5" />
        <span>HTML5</span>
      </div>
      <div class="tool-card">
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="CSS3" />
        <span>CSS3</span>
      </div>
      <div class="tool-card">
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="JavaScript" />
        <span>JavaScript</span>
      </div>
      <div class="tool-card">
        <img src="https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg" alt="Flutter" />
        <span>Flutter</span>
      </div>
      <div class="tool-card">
        <img src="https://www.vectorlogo.zone/logos/dartlang/dartlang-icon.svg" alt="Dart" />
        <span>Dart</span>
      </div>
      <div class="tool-card">
        <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/photoshop/photoshop-line.svg" alt="Photoshop" />
        <span>Photoshop</span>
      </div>
    </div>
  </div>

  <!-- Fun fact -->
  <div class="fun-fact">
    <span style="font-size:20px;">⚡</span>
    <span><strong>Fun fact:</strong> I think I am funny 😎</span>
  </div>

</div>

<script>
  /* ---- Typewriter cycling effect ---- */
  var roles = [
    "Developer",
    "UI Designer",
    "Flutter Dev",
    "Teacher",
    "Problem Solver",
    "Creative Coder"
  ];

  var el = document.getElementById('typed-text');
  var roleIndex = 0;
  var charIndex = 0;
  var isDeleting = false;
  var typeSpeed = 100;

  function type() {
    var current = roles[roleIndex];

    if (isDeleting) {
      el.textContent = current.substring(0, charIndex - 1);
      charIndex--;
    } else {
      el.textContent = current.substring(0, charIndex + 1);
      charIndex++;
    }

    var delay = isDeleting ? 60 : typeSpeed;

    if (!isDeleting && charIndex === current.length) {
      delay = 1400;
      isDeleting = true;
    } else if (isDeleting && charIndex === 0) {
      isDeleting = false;
      roleIndex = (roleIndex + 1) % roles.length;
      delay = 300;
    }

    setTimeout(type, delay);
  }

  setTimeout(type, 800);

  /* ---- Skill bars ---- */
  setTimeout(function () {
    document.querySelectorAll('.skill-bar-fill').forEach(function (bar) {
      bar.style.width = bar.getAttribute('data-w') + '%';
    });
  }, 900);

  /* ---- Tool cards pop-in ---- */
  setTimeout(function () {
    document.querySelectorAll('.tool-card').forEach(function (card, i) {
      setTimeout(function () {
        card.classList.add('visible');
      }, i * 100);
    });
  }, 1000);
</script>
</body>
</html>
