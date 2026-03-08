<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Maksudul Islam — ML Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --card: #16161f;
    --border: #1e1e2e;
    --accent: #7c6af7;
    --accent2: #f06e9b;
    --accent3: #4ecdc4;
    --text: #e8e8f0;
    --muted: #6b6b80;
    --glow: rgba(124,106,247,0.15);
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem;
  }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  .card {
    position: relative;
    z-index: 1;
    width: 100%;
    max-width: 680px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 0 60px rgba(124,106,247,0.08), 0 40px 80px rgba(0,0,0,0.6);
    animation: fadeUp 0.8s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Top accent stripe */
  .stripe {
    height: 3px;
    background: linear-gradient(90deg, var(--accent), var(--accent2), var(--accent3));
  }

  .body { padding: 2.5rem; }

  /* Header */
  .header {
    display: flex;
    align-items: flex-start;
    gap: 1.5rem;
    margin-bottom: 2rem;
  }

  .avatar {
    width: 72px;
    height: 72px;
    border-radius: 16px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    flex-shrink: 0;
    box-shadow: 0 0 24px var(--glow);
  }

  .name-block h1 {
    font-size: 1.7rem;
    font-weight: 800;
    letter-spacing: -0.03em;
    line-height: 1.1;
    background: linear-gradient(135deg, #fff 40%, var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .name-block .role {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    margin-top: 0.4rem;
    letter-spacing: 0.08em;
  }

  .name-block .bio {
    font-size: 0.85rem;
    color: var(--muted);
    margin-top: 0.6rem;
    line-height: 1.6;
    font-weight: 400;
  }

  /* Section label */
  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 0.9rem;
  }

  /* Divider */
  .divider {
    height: 1px;
    background: var(--border);
    margin: 1.8rem 0;
  }

  /* Skills */
  .skills-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .skill-chip {
    display: flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.35rem 0.75rem;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    font-size: 0.78rem;
    font-weight: 600;
    color: var(--text);
    transition: border-color 0.2s, box-shadow 0.2s, transform 0.2s;
    cursor: default;
    animation: fadeUp 0.8s ease both;
  }

  .skill-chip:hover {
    border-color: var(--accent);
    box-shadow: 0 0 12px var(--glow);
    transform: translateY(-2px);
  }

  .skill-chip img {
    width: 16px;
    height: 16px;
  }

  /* Stagger chips */
  .skill-chip:nth-child(1)  { animation-delay: 0.05s; }
  .skill-chip:nth-child(2)  { animation-delay: 0.10s; }
  .skill-chip:nth-child(3)  { animation-delay: 0.15s; }
  .skill-chip:nth-child(4)  { animation-delay: 0.20s; }
  .skill-chip:nth-child(5)  { animation-delay: 0.25s; }
  .skill-chip:nth-child(6)  { animation-delay: 0.30s; }
  .skill-chip:nth-child(7)  { animation-delay: 0.35s; }
  .skill-chip:nth-child(8)  { animation-delay: 0.40s; }
  .skill-chip:nth-child(9)  { animation-delay: 0.45s; }
  .skill-chip:nth-child(10) { animation-delay: 0.50s; }

  /* Links */
  .links {
    display: flex;
    flex-wrap: wrap;
    gap: 0.6rem;
  }

  .link-btn {
    display: flex;
    align-items: center;
    gap: 0.45rem;
    padding: 0.45rem 1rem;
    border-radius: 9px;
    font-size: 0.78rem;
    font-weight: 700;
    text-decoration: none;
    border: 1px solid var(--border);
    transition: all 0.2s;
    letter-spacing: 0.02em;
  }

  .link-btn:hover { transform: translateY(-2px); box-shadow: 0 4px 20px rgba(0,0,0,0.4); }

  .link-btn.github   { background: #181717; color: #fff; border-color: #2d2d2d; }
  .link-btn.linkedin { background: #0a66c2; color: #fff; border-color: #0a66c2; }
  .link-btn.cf       { background: #1f8acb; color: #fff; border-color: #1f8acb; }
  .link-btn.lc       { background: #ffa116; color: #1a1a1a; border-color: #ffa116; }
  .link-btn.gmail    { background: #d14836; color: #fff; border-color: #d14836; }
  .link-btn.fb       { background: #1877f2; color: #fff; border-color: #1877f2; }

  .link-btn svg { width: 14px; height: 14px; fill: currentColor; }

  /* Stats row */
  .stats-row {
    display: flex;
    gap: 1rem;
    margin-bottom: 1.8rem;
  }

  .stat-card {
    flex: 1;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1rem;
    text-align: center;
  }

  .stat-card .num {
    font-size: 1.4rem;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .stat-card .lbl {
    font-family: 'DM Mono', monospace;
    font-size: 0.65rem;
    color: var(--muted);
    margin-top: 0.2rem;
    letter-spacing: 0.06em;
  }
</style>
</head>
<body>

<div class="card">
  <div class="stripe"></div>
  <div class="body">

    <!-- Header -->
    <div class="header">
      <div class="avatar">🤖</div>
      <div class="name-block">
        <h1>Maksudul Islam</h1>
        <div class="role">// Aspiring ML Engineer · AI Enthusiast</div>
        <div class="bio">Strong foundations in Python, data analysis & core ML algorithms. Passionate about building data-driven solutions and real-world AI projects.</div>
      </div>
    </div>

    <!-- Stats -->
    <div class="stats-row">
      <div class="stat-card">
        <div class="num">Python</div>
        <div class="lbl">Primary Lang</div>
      </div>
      <div class="stat-card">
        <div class="num">ML / AI</div>
        <div class="lbl">Focus Area</div>
      </div>
      <div class="stat-card">
        <div class="num">Open</div>
        <div class="lbl">to Opportunities</div>
      </div>
    </div>

    <!-- Tools -->
    <div class="section-label">⚙ Stack & Tools</div>
    <div class="skills-grid">
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg"/>Python</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tensorflow/tensorflow-original.svg"/>TensorFlow</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/numpy/numpy-original.svg"/>NumPy</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pandas/pandas-original.svg"/>Pandas</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jupyter/jupyter-original.svg"/>Jupyter</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/fastapi/fastapi-original.svg"/>FastAPI</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg"/>Docker</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg"/>MySQL</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg"/>Git</div>
      <div class="skill-chip"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kaggle/kaggle-original.svg"/>Kaggle</div>
    </div>

    <div class="divider"></div>

    <!-- Links -->
    <div class="section-label">🔗 Find me on</div>
    <div class="links">
      <a class="link-btn github" href="https://github.com/iammaksud" target="_blank">
        <svg viewBox="0 0 24 24"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.44 9.8 8.2 11.38.6.11.82-.26.82-.58v-2.03c-3.34.73-4.04-1.61-4.04-1.61-.54-1.38-1.33-1.74-1.33-1.74-1.09-.74.08-.73.08-.73 1.2.08 1.84 1.24 1.84 1.24 1.07 1.83 2.8 1.3 3.49 1 .1-.78.42-1.3.76-1.6-2.67-.3-5.47-1.33-5.47-5.93 0-1.31.47-2.38 1.24-3.22-.13-.3-.54-1.52.12-3.17 0 0 1.01-.32 3.3 1.23a11.5 11.5 0 0 1 3-.4c1.02 0 2.04.13 3 .4 2.28-1.55 3.3-1.23 3.3-1.23.66 1.65.25 2.87.12 3.17.77.84 1.24 1.91 1.24 3.22 0 4.61-2.81 5.63-5.48 5.92.43.37.81 1.1.81 2.22v3.29c0 .32.22.7.83.58C20.56 21.8 24 17.3 24 12c0-6.63-5.37-12-12-12z"/></svg>
        GitHub
      </a>
      <a class="link-btn linkedin" href="https://www.linkedin.com/in/maksudul-islam-ab913b2b5/" target="_blank">
        <svg viewBox="0 0 24 24"><path d="M20.45 20.45h-3.55v-5.57c0-1.33-.03-3.04-1.85-3.04-1.85 0-2.14 1.45-2.14 2.94v5.67H9.36V9h3.41v1.56h.05c.47-.9 1.63-1.85 3.35-1.85 3.59 0 4.25 2.36 4.25 5.43v6.31zM5.34 7.43a2.06 2.06 0 1 1 0-4.12 2.06 2.06 0 0 1 0 4.12zM7.12 20.45H3.55V9h3.57v11.45zM22.23 0H1.77C.79 0 0 .77 0 1.73v20.54C0 23.23.79 24 1.77 24h20.46C23.2 24 24 23.23 24 22.27V1.73C24 .77 23.2 0 22.23 0z"/></svg>
        LinkedIn
      </a>
      <a class="link-btn cf" href="https://codeforces.com/profile/maksud04" target="_blank">
        <svg viewBox="0 0 24 24"><path d="M4.5 7.5A1.5 1.5 0 0 1 6 9v10.5A1.5 1.5 0 0 1 4.5 21h-3A1.5 1.5 0 0 1 0 19.5V9A1.5 1.5 0 0 1 1.5 7.5h3zm9-4.5A1.5 1.5 0 0 1 15 4.5v15A1.5 1.5 0 0 1 13.5 21h-3A1.5 1.5 0 0 1 9 19.5v-15A1.5 1.5 0 0 1 10.5 3h3zm9 7.5A1.5 1.5 0 0 1 24 12v7.5A1.5 1.5 0 0 1 22.5 21h-3A1.5 1.5 0 0 1 18 19.5V12a1.5 1.5 0 0 1 1.5-1.5h3z"/></svg>
        Codeforces
      </a>
      <a class="link-btn lc" href="https://leetcode.com/u/Maksud27/" target="_blank">
        <svg viewBox="0 0 24 24"><path d="M13.483 0a1.374 1.374 0 0 0-.961.438L7.116 6.226l-3.854 4.126a5.266 5.266 0 0 0-1.209 2.104 5.35 5.35 0 0 0-.125.513 5.527 5.527 0 0 0 .062 2.362 5.83 5.83 0 0 0 .349 1.017 5.938 5.938 0 0 0 1.271 1.818l4.277 4.193.039.038c2.248 2.165 5.852 2.133 8.063-.074l2.396-2.392c.54-.54.54-1.414.003-1.955a1.378 1.378 0 0 0-1.951-.003l-2.396 2.392a3.021 3.021 0 0 1-4.205.038l-.02-.019-4.276-4.193c-.652-.64-.972-1.469-.948-2.263a2.68 2.68 0 0 1 .066-.523 2.545 2.545 0 0 1 .619-1.164L9.13 8.114c1.058-1.134 3.204-1.27 4.43-.278l3.501 2.831c.593.48 1.461.387 1.94-.207a1.384 1.384 0 0 0-.207-1.943l-3.5-2.831c-.8-.647-1.766-1.045-2.774-1.202l2.015-2.158A1.384 1.384 0 0 0 13.483 0zm-2.866 12.815a1.38 1.38 0 0 0-1.38 1.382 1.38 1.38 0 0 0 1.38 1.382H20.79a1.38 1.38 0 0 0 1.38-1.382 1.38 1.38 0 0 0-1.38-1.382z"/></svg>
        LeetCode
      </a>
      <a class="link-btn gmail" href="mailto:maksudulislam2004@gmail.com" target="_blank">
        <svg viewBox="0 0 24 24"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
        Gmail
      </a>
    </div>

  </div>
</div>

</body>
</html>
