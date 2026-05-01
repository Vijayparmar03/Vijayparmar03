
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Sora:wght@300;400;600;700&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  .gp {
    font-family: 'Sora', sans-serif;
    background: #0d1117;
    color: #c9d1d9;
    padding: 2rem 1.5rem 3rem;
    min-height: 100vh;
    position: relative;
    overflow: hidden;
  }

  .grid-bg {
    position: absolute;
    inset: 0;
    background-image: linear-gradient(rgba(0,255,150,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,150,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
  }

  .scanline {
    position: absolute;
    inset: 0;
    background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.07) 2px, rgba(0,0,0,0.07) 4px);
    pointer-events: none;
    z-index: 0;
  }

  .content { position: relative; z-index: 1; max-width: 760px; margin: 0 auto; }

  /* --- HEADER --- */
  .header { text-align: center; margin-bottom: 2.5rem; padding-top: 0.5rem; }

  .avatar-ring {
    width: 96px; height: 96px;
    border-radius: 50%;
    margin: 0 auto 1rem;
    background: linear-gradient(135deg, #00ff96, #0affef, #7c3aed);
    padding: 3px;
    animation: spin-ring 8s linear infinite;
  }
  @keyframes spin-ring {
    0% { filter: hue-rotate(0deg); }
    100% { filter: hue-rotate(360deg); }
  }
  .avatar-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: #161b22;
    display: flex; align-items: center; justify-content: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 2rem;
    font-weight: 700;
    color: #0affef;
    letter-spacing: -2px;
  }

  .name {
    font-size: 2rem;
    font-weight: 700;
    color: #f0f6fc;
    letter-spacing: -0.5px;
    animation: fade-in 0.8s ease both;
  }
  .role {
    font-size: 0.9rem;
    color: #0affef;
    font-family: 'JetBrains Mono', monospace;
    margin-top: 6px;
    animation: fade-in 1s ease 0.2s both;
  }
  .role::before { content: '> '; color: #3fb950; }

  @keyframes fade-in {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* Typing line */
  .typing-wrap {
    margin: 1rem auto 0;
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 6px;
    padding: 6px 14px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    color: #3fb950;
  }
  .typing-line { width: 200px; overflow: hidden; white-space: nowrap; border-right: 2px solid #3fb950; animation: typing 3s steps(25) infinite, blink 0.7s step-end infinite alternate; }
  @keyframes typing {
    0%,100% { width: 0; content: ''; }
    10%,45% { width: 200px; }
    55%,90% { width: 200px; }
  }
  @keyframes blink { 50% { border-color: transparent; } }
  .typing-words { display: inline; }

  /* --- SECTION --- */
  .section { margin-bottom: 2rem; animation: fade-in 0.6s ease both; }
  .section-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: #7d8590;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 0.75rem;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-title::after { content: ''; flex: 1; height: 1px; background: #21262d; }

  /* --- ABOUT --- */
  .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
  .about-item {
    display: flex; align-items: center; gap: 10px;
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 8px;
    padding: 10px 14px;
    font-size: 0.82rem;
    color: #8b949e;
    transition: border-color 0.2s, transform 0.2s;
    cursor: default;
  }
  .about-item:hover { border-color: #0affef55; transform: translateX(4px); }
  .about-item span.icon { font-size: 16px; flex-shrink: 0; }
  .about-item strong { color: #c9d1d9; font-weight: 600; }

  /* --- CONNECT --- */
  .connect-row { display: flex; gap: 10px; flex-wrap: wrap; }
  .badge {
    display: inline-flex; align-items: center; gap: 7px;
    padding: 7px 14px;
    border-radius: 6px;
    font-size: 0.8rem;
    font-weight: 600;
    text-decoration: none;
    transition: opacity 0.2s, transform 0.15s;
    border: none;
    cursor: pointer;
  }
  .badge:hover { opacity: 0.85; transform: translateY(-2px); }
  .badge-ig { background: #E4405F; color: #fff; }
  .badge-li { background: #0077B5; color: #fff; }
  .badge-em { background: #D14836; color: #fff; }
  .badge-icon { width: 16px; height: 16px; fill: white; flex-shrink: 0; }

  /* --- TECH STACK --- */
  .tech-grid { display: flex; flex-wrap: wrap; gap: 8px; }
  .tech-pill {
    display: inline-flex; align-items: center; gap: 7px;
    padding: 6px 13px;
    background: #161b22;
    border: 1px solid #30363d;
    border-radius: 20px;
    font-size: 0.78rem;
    font-family: 'JetBrains Mono', monospace;
    color: #c9d1d9;
    transition: border-color 0.2s, color 0.2s;
  }
  .tech-pill:hover { border-color: #0affef; color: #0affef; }
  .tech-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }

  /* --- STATS --- */
  .stats-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; }
  .stat-card {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 10px;
    padding: 14px 12px;
    text-align: center;
    transition: border-color 0.2s, transform 0.2s;
    cursor: default;
  }
  .stat-card:hover { border-color: #3fb95066; transform: translateY(-3px); }
  .stat-num { font-size: 1.5rem; font-weight: 700; font-family: 'JetBrains Mono', monospace; color: #3fb950; }
  .stat-label { font-size: 0.72rem; color: #7d8590; margin-top: 4px; }

  /* --- STREAK --- */
  .streak-bar-wrap { background: #161b22; border: 1px solid #21262d; border-radius: 10px; padding: 1rem 1.25rem; }
  .streak-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
  .streak-label { font-size: 0.8rem; color: #7d8590; font-family: 'JetBrains Mono', monospace; }
  .streak-count { font-size: 1.8rem; font-weight: 700; font-family: 'JetBrains Mono', monospace; color: #ff9900; }
  .streak-row { display: flex; gap: 3px; margin-top: 6px; }
  .streak-cell { flex: 1; height: 28px; border-radius: 4px; background: #21262d; transition: background 0.2s; cursor: default; }
  .streak-cell.active { background: #39d353; }
  .streak-cell.partial { background: #26a641; }
  .streak-cell.hot { background: #00ff96; box-shadow: 0 0 6px #00ff9666; }

  /* --- TROPHIES --- */
  .trophy-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
  .trophy-card {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 10px;
    padding: 14px;
    text-align: center;
    transition: border-color 0.2s, transform 0.2s;
    cursor: default;
  }
  .trophy-card:hover { border-color: #f0da6055; transform: scale(1.04); }
  .trophy-icon { font-size: 1.6rem; margin-bottom: 6px; }
  .trophy-name { font-size: 0.72rem; font-family: 'JetBrains Mono', monospace; color: #7d8590; }
  .trophy-val { font-size: 0.9rem; font-weight: 600; color: #f0da60; margin-top: 2px; }

  /* --- PROJECTS --- */
  .project-list { display: grid; gap: 8px; }
  .project-card {
    background: #161b22;
    border: 1px solid #21262d;
    border-left: 3px solid #0affef;
    border-radius: 0 8px 8px 0;
    padding: 12px 16px;
    transition: border-color 0.2s, transform 0.2s;
    cursor: default;
  }
  .project-card:hover { border-left-color: #3fb950; transform: translateX(5px); }
  .project-name { font-size: 0.9rem; font-weight: 600; color: #c9d1d9; }
  .project-desc { font-size: 0.78rem; color: #7d8590; margin-top: 4px; }
  .project-tags { margin-top: 8px; display: flex; gap: 6px; flex-wrap: wrap; }
  .tag { font-size: 0.68rem; font-family: 'JetBrains Mono', monospace; padding: 2px 8px; border-radius: 20px; border: 1px solid #30363d; color: #8b949e; }

  /* --- QUOTE --- */
  .quote-block {
    background: #161b22;
    border: 1px solid #21262d;
    border-radius: 10px;
    padding: 1.25rem 1.5rem;
    position: relative;
  }
  .quote-block::before { content: '"'; position: absolute; top: 6px; left: 14px; font-size: 3rem; color: #0affef22; font-family: serif; line-height: 1; }
  .quote-text { font-size: 0.92rem; color: #c9d1d9; font-style: italic; line-height: 1.6; padding-left: 1rem; }
  .quote-author { font-size: 0.72rem; color: #7d8590; font-family: 'JetBrains Mono', monospace; margin-top: 8px; padding-left: 1rem; }

  /* --- FOOTER --- */
  .footer { text-align: center; margin-top: 2rem; padding-top: 1.5rem; border-top: 1px solid #21262d; }
  .views-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: #161b22; border: 1px solid #30363d;
    border-radius: 20px; padding: 6px 14px;
    font-family: 'JetBrains Mono', monospace; font-size: 0.75rem; color: #8b949e;
  }
  .views-num { color: #0affef; font-weight: 700; }

  .pulse { animation: pulse-dot 1.5s ease-in-out infinite; }
  @keyframes pulse-dot { 0%,100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.5; transform: scale(0.85); } }

  @media (max-width: 500px) {
    .about-grid { grid-template-columns: 1fr; }
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .trophy-grid { grid-template-columns: repeat(2, 1fr); }
  }
</style>

<div class="gp">
  <div class="grid-bg"></div>
  <div class="scanline"></div>
  <div class="content">

    <!-- HEADER -->
    <div class="header">
      <div class="avatar-ring">
        <div class="avatar-inner">VP</div>
      </div>
      <div class="name">Vijay Parmar</div>
      <div class="role">Laravel Developer | Backend Engineer | Problem Solver</div>
      <div style="text-align:center; margin-top:10px;">
        <div class="typing-wrap">
          <span style="color:#7d8590;">$</span>
          <span id="typed" class="typing-words" style="color:#3fb950; font-size:0.8rem;"></span>
          <span style="color:#3fb950; animation: blink 0.7s step-end infinite alternate;">▌</span>
        </div>
      </div>
    </div>

    <!-- ABOUT -->
    <div class="section" style="animation-delay:0.1s">
      <div class="section-title">about_me.json</div>
      <div class="about-grid">
        <div class="about-item"><span class="icon">🔭</span><span>Working on <strong>Laravel & REST APIs</strong></span></div>
        <div class="about-item"><span class="icon">🌱</span><span>Learning <strong>System Design & Cloud</strong></span></div>
        <div class="about-item"><span class="icon">👯</span><span>Open to <strong>Backend & ERP collab</strong></span></div>
        <div class="about-item"><span class="icon">💬</span><span>Ask me about <strong>Laravel, PHP, MySQL</strong></span></div>
        <div class="about-item"><span class="icon">⚡</span><span><strong>Clean code</strong> > clever code</span></div>
        <div class="about-item"><span class="icon">📍</span><span>Based in <strong>Ahmedabad, India</strong></span></div>
      </div>
    </div>

    <!-- CONNECT -->
    <div class="section" style="animation-delay:0.2s">
      <div class="section-title">connect.links</div>
      <div class="connect-row">
        <a href="https://instagram.com/vijju_lover_143" class="badge badge-ig" target="_blank">
          <svg class="badge-icon" viewBox="0 0 24 24"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
          Instagram
        </a>
        <a href="https://linkedin.com/in/parmarvijay07" class="badge badge-li" target="_blank">
          <svg class="badge-icon" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
          LinkedIn
        </a>
        <a href="mailto:vijayparmar635127@gmail.com" class="badge badge-em">
          <svg class="badge-icon" viewBox="0 0 24 24"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.909 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
          Email
        </a>
      </div>
    </div>

    <!-- TECH STACK -->
    <div class="section" style="animation-delay:0.3s">
      <div class="section-title">tech_stack.config</div>
      <div class="tech-grid">
        <div class="tech-pill"><span class="tech-dot" style="background:#8892be"></span>PHP</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#ff2d20"></span>Laravel</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#f7df1e"></span>JavaScript</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#0769ad"></span>jQuery</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#e44d26"></span>HTML5</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#264de4"></span>CSS3</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#7952b3"></span>Bootstrap</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#4479a1"></span>MySQL</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#f14e32"></span>Git</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#333"></span>GitHub</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#0affef"></span>REST API</div>
        <div class="tech-pill"><span class="tech-dot" style="background:#3fb950"></span>Postman</div>
      </div>
    </div>

    <!-- GITHUB STATS -->
    <div class="section" style="animation-delay:0.4s">
      <div class="section-title">github_stats.json</div>
      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-num" id="commits">248</div>
          <div class="stat-label">Total Commits</div>
        </div>
        <div class="stat-card">
          <div class="stat-num" id="prs">34</div>
          <div class="stat-label">Pull Requests</div>
        </div>
        <div class="stat-card">
          <div class="stat-num" id="repos">18</div>
          <div class="stat-label">Repositories</div>
        </div>
        <div class="stat-card">
          <div class="stat-num" id="stars">62</div>
          <div class="stat-label">Stars Earned</div>
        </div>
      </div>
    </div>

    <!-- STREAK -->
    <div class="section" style="animation-delay:0.45s">
      <div class="section-title">commit_streak.log</div>
      <div class="streak-bar-wrap">
        <div class="streak-header">
          <div>
            <div class="streak-label">Current streak</div>
            <div class="streak-count">🔥 21 days</div>
          </div>
          <div style="text-align:right;">
            <div class="streak-label">Longest streak</div>
            <div class="streak-count" style="color:#0affef; font-size:1.4rem;">47 days</div>
          </div>
        </div>
        <div class="streak-row" id="streak-cells"></div>
        <div style="font-size:0.68rem; color:#7d8590; margin-top:8px; font-family:'JetBrains Mono', monospace;">Last 52 weeks</div>
      </div>
    </div>

    <!-- TROPHIES -->
    <div class="section" style="animation-delay:0.5s">
      <div class="section-title">github_trophies.json</div>
      <div class="trophy-grid">
        <div class="trophy-card"><div class="trophy-icon">🏆</div><div class="trophy-name">commits</div><div class="trophy-val">Gold</div></div>
        <div class="trophy-card"><div class="trophy-icon">⭐</div><div class="trophy-name">stars</div><div class="trophy-val">Silver</div></div>
        <div class="trophy-card"><div class="trophy-icon">🔀</div><div class="trophy-name">pull request</div><div class="trophy-val">Bronze</div></div>
        <div class="trophy-card"><div class="trophy-icon">📦</div><div class="trophy-name">repos</div><div class="trophy-val">Gold</div></div>
        <div class="trophy-card"><div class="trophy-icon">🤝</div><div class="trophy-name">followers</div><div class="trophy-val">Bronze</div></div>
        <div class="trophy-card"><div class="trophy-icon">🛠</div><div class="trophy-name">experience</div><div class="trophy-val">Gold</div></div>
      </div>
    </div>

    <!-- PROJECTS -->
    <div class="section" style="animation-delay:0.55s">
      <div class="section-title">featured_projects.list</div>
      <div class="project-list">
        <div class="project-card">
          <div class="project-name">ERP System</div>
          <div class="project-desc">Full-featured enterprise resource planning system with modular architecture.</div>
          <div class="project-tags"><span class="tag">Laravel</span><span class="tag">MySQL</span><span class="tag">REST API</span><span class="tag">Bootstrap</span></div>
        </div>
        <div class="project-card">
          <div class="project-name">REST API Projects</div>
          <div class="project-desc">Scalable API endpoints with JWT auth, rate limiting and comprehensive docs.</div>
          <div class="project-tags"><span class="tag">PHP</span><span class="tag">Laravel</span><span class="tag">JWT</span><span class="tag">Postman</span></div>
        </div>
        <div class="project-card">
          <div class="project-name">Auth System + Email Verification</div>
          <div class="project-desc">Complete authentication flow with email verification, roles & permissions.</div>
          <div class="project-tags"><span class="tag">Laravel</span><span class="tag">Mail</span><span class="tag">Middleware</span></div>
        </div>
      </div>
    </div>

    <!-- QUOTE -->
    <div class="section" style="animation-delay:0.6s">
      <div class="section-title">dev_quote.txt</div>
      <div class="quote-block">
        <div class="quote-text">First, solve the problem. Then, write the code.</div>
        <div class="quote-author">— John Johnson</div>
      </div>
    </div>

    <!-- FOOTER -->
    <div class="footer">
      <div class="views-badge">
        <span class="pulse" style="display:inline-block; width:8px; height:8px; border-radius:50%; background:#3fb950;"></span>
        Profile views: <span class="views-num">1,247</span>
      </div>
      <div style="font-size:0.7rem; color:#484f58; font-family:'JetBrains Mono', monospace; margin-top:12px;">
        Built with ❤️ by Vijay Parmar
      </div>
    </div>

  </div>
</div>

<script>
  const words = ["Laravel Developer", "REST API Specialist", "Backend Engineer", "Clean Code Lover", "Problem Solver"];
  let wi = 0, ci = 0, deleting = false;
  const el = document.getElementById('typed');
  function typeLoop() {
    const word = words[wi];
    if (!deleting) {
      el.textContent = word.slice(0, ci + 1);
      ci++;
      if (ci === word.length) { deleting = true; setTimeout(typeLoop, 1600); return; }
    } else {
      el.textContent = word.slice(0, ci - 1);
      ci--;
      if (ci === 0) { deleting = false; wi = (wi + 1) % words.length; }
    }
    setTimeout(typeLoop, deleting ? 55 : 80);
  }
  typeLoop();

  const cells = document.getElementById('streak-cells');
  const pattern = [0,1,1,0,1,1,1,0,1,1,1,1,0,1,1,1,0,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1];
  pattern.forEach((v, i) => {
    const c = document.createElement('div');
    c.className = 'streak-cell' + (v === 0 ? '' : i >= 31 ? ' hot' : i >= 20 ? ' active' : ' partial');
    cells.appendChild(c);
  });

  function animateCount(id, target) {
    const el = document.getElementById(id);
    let v = 0, step = Math.ceil(target / 40);
    const t = setInterval(() => {
      v = Math.min(v + step, target);
      el.textContent = v;
      if (v >= target) clearInterval(t);
    }, 35);
  }
  setTimeout(() => {
    animateCount('commits', 248);
    animateCount('prs', 34);
    animateCount('repos', 18);
    animateCount('stars', 62);
  }, 400);
</script>
