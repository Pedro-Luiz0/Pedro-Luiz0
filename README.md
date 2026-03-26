<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pedro Luiz — GitHub README</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&display=swap');

  :root {
    --green: #00FF41;
    --green-dim: #00cc33;
    --green-glow: rgba(0, 255, 65, 0.4);
    --green-faint: rgba(0, 255, 65, 0.08);
    --bg: #020c06;
    --bg2: #041008;
    --surface: #061a0a;
    --border: rgba(0,255,65,0.18);
    --text: #b0ffb8;
    --dim: #3a5c40;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Share Tech Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* scanline effect */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.08) 2px,
      rgba(0,0,0,0.08) 4px
    );
    pointer-events: none;
    z-index: 100;
  }

  /* noise texture */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 99;
    opacity: 0.6;
  }

  .container {
    max-width: 820px;
    margin: 0 auto;
    padding: 40px 24px 80px;
    position: relative;
  }

  /* ===== HEADER ===== */
  .header {
    text-align: center;
    padding: 48px 0 40px;
    position: relative;
  }

  .boot-label {
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 4px;
    text-transform: uppercase;
    margin-bottom: 20px;
    animation: blink-in 0.6s ease both;
  }

  .name-wrap {
    position: relative;
    display: inline-block;
    margin-bottom: 12px;
  }

  .name {
    font-family: 'Orbitron', monospace;
    font-size: clamp(2rem, 8vw, 4rem);
    font-weight: 900;
    color: var(--green);
    text-shadow:
      0 0 10px var(--green),
      0 0 30px var(--green-glow),
      0 0 60px rgba(0,255,65,0.2);
    letter-spacing: 6px;
    animation: flicker 8s infinite;
  }

  .name-glitch {
    position: absolute;
    inset: 0;
    font-family: 'Orbitron', monospace;
    font-size: clamp(2rem, 8vw, 4rem);
    font-weight: 900;
    color: #00ffff;
    opacity: 0;
    letter-spacing: 6px;
    clip-path: inset(40% 0 50% 0);
    animation: glitch 7s infinite;
  }

  .tagline {
    font-size: 13px;
    color: var(--dim);
    letter-spacing: 3px;
    margin-top: 8px;
  }

  .tagline span {
    color: var(--green);
    animation: cursor-blink 1s step-end infinite;
  }

  .divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--green), transparent);
    margin: 36px 0;
    box-shadow: 0 0 8px var(--green-glow);
  }

  /* ===== TYPING INTRO ===== */
  .terminal-block {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 24px 28px;
    margin-bottom: 32px;
    position: relative;
    box-shadow: 0 0 20px rgba(0,255,65,0.05), inset 0 0 30px rgba(0,0,0,0.4);
  }

  .terminal-block::before {
    content: '● ● ●';
    position: absolute;
    top: 10px;
    left: 16px;
    font-size: 10px;
    color: var(--dim);
    letter-spacing: 4px;
  }

  .terminal-block .prompt {
    color: var(--green);
    font-size: 13px;
    line-height: 2;
  }

  .terminal-block .prompt::before {
    content: '> ';
    color: var(--dim);
  }

  .terminal-block .output {
    color: var(--text);
    font-size: 13px;
    line-height: 1.9;
    padding-left: 14px;
    border-left: 2px solid var(--border);
    margin: 6px 0 12px;
  }

  .highlight { color: var(--green); }

  /* ===== SECTION TITLES ===== */
  .section-title {
    font-family: 'Orbitron', monospace;
    font-size: 12px;
    font-weight: 700;
    color: var(--green);
    letter-spacing: 5px;
    text-transform: uppercase;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ===== STATS GRID ===== */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 14px;
    margin-bottom: 32px;
  }

  .stat-card {
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 18px 16px;
    background: var(--green-faint);
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, box-shadow 0.3s;
  }

  .stat-card:hover {
    border-color: var(--green);
    box-shadow: 0 0 18px var(--green-glow), inset 0 0 18px rgba(0,255,65,0.05);
  }

  .stat-card::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle, rgba(0,255,65,0.04), transparent 60%);
  }

  .stat-value {
    font-family: 'Orbitron', monospace;
    font-size: 22px;
    font-weight: 700;
    color: var(--green);
    text-shadow: 0 0 12px var(--green-glow);
    display: block;
  }

  .stat-label {
    font-size: 10px;
    color: var(--dim);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-top: 4px;
    display: block;
  }

  /* ===== SKILLS ===== */
  .skills-wrap {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 32px;
  }

  .skill-tag {
    border: 1px solid var(--border);
    border-radius: 3px;
    padding: 6px 14px;
    font-size: 12px;
    color: var(--green-dim);
    letter-spacing: 1.5px;
    background: var(--green-faint);
    transition: all 0.25s;
    cursor: default;
  }

  .skill-tag:hover {
    color: var(--green);
    border-color: var(--green);
    box-shadow: 0 0 12px var(--green-glow);
    background: rgba(0,255,65,0.12);
  }

  .skill-tag.main {
    border-color: rgba(0,255,65,0.35);
    color: var(--green);
  }

  /* ===== PROGRESS BARS ===== */
  .progress-list {
    display: flex;
    flex-direction: column;
    gap: 14px;
    margin-bottom: 32px;
  }

  .progress-item {
    display: grid;
    grid-template-columns: 130px 1fr 36px;
    align-items: center;
    gap: 14px;
  }

  .progress-name {
    font-size: 12px;
    color: var(--text);
    letter-spacing: 1px;
  }

  .bar-track {
    height: 6px;
    background: rgba(0,255,65,0.08);
    border: 1px solid var(--border);
    border-radius: 2px;
    overflow: hidden;
  }

  .bar-fill {
    height: 100%;
    background: linear-gradient(90deg, var(--green-dim), var(--green));
    box-shadow: 0 0 6px var(--green-glow);
    border-radius: 2px;
    transition: width 1s ease;
    animation: bar-grow 1.5s ease both;
  }

  .bar-pct {
    font-size: 11px;
    color: var(--dim);
    text-align: right;
  }

  /* ===== CONTACT ===== */
  .contact-row {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-bottom: 32px;
  }

  .contact-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 10px 18px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 12px;
    color: var(--green-dim);
    background: var(--green-faint);
    text-decoration: none;
    letter-spacing: 2px;
    transition: all 0.25s;
  }

  .contact-btn:hover {
    color: var(--green);
    border-color: var(--green);
    box-shadow: 0 0 14px var(--green-glow);
  }

  /* ===== FOOTER ===== */
  .footer {
    text-align: center;
    padding-top: 32px;
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 2px;
  }

  .footer em {
    color: var(--green);
    font-style: normal;
  }

  /* ===== ANIMATIONS ===== */
  @keyframes flicker {
    0%, 95%, 100% { opacity: 1; }
    96% { opacity: 0.85; }
    97% { opacity: 1; }
    98% { opacity: 0.7; }
    99% { opacity: 1; }
  }

  @keyframes glitch {
    0%, 90%, 100% { opacity: 0; transform: translateX(0); }
    91% { opacity: 0.6; transform: translateX(-4px); clip-path: inset(20% 0 70% 0); }
    92% { opacity: 0.4; transform: translateX(4px); clip-path: inset(65% 0 10% 0); }
    93% { opacity: 0; }
  }

  @keyframes cursor-blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  @keyframes bar-grow {
    from { width: 0 !important; }
  }

  @keyframes blink-in {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  /* ===== MARKDOWN EXPORT AREA ===== */
  .md-section {
    margin-top: 56px;
    border-top: 1px solid var(--border);
    padding-top: 32px;
  }

  .md-label {
    font-size: 11px;
    color: var(--dim);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .md-box {
    background: #000;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 20px;
    font-size: 12px;
    color: #5a9960;
    line-height: 1.8;
    white-space: pre-wrap;
    word-break: break-word;
    max-height: 340px;
    overflow-y: auto;
  }

  .copy-btn {
    margin-top: 12px;
    background: var(--green-faint);
    border: 1px solid var(--border);
    color: var(--green);
    font-family: 'Share Tech Mono', monospace;
    font-size: 12px;
    letter-spacing: 2px;
    padding: 10px 24px;
    border-radius: 3px;
    cursor: pointer;
    transition: all 0.2s;
  }

  .copy-btn:hover {
    background: rgba(0,255,65,0.15);
    box-shadow: 0 0 12px var(--green-glow);
  }
</style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <div class="header">
    <div class="boot-label">// github profile · v2.0.26</div>
    <div class="name-wrap">
      <div class="name">PEDRO LUIZ</div>
      <div class="name-glitch">PEDRO LUIZ</div>
    </div>
    <div class="tagline">
      DESENVOLVEDOR EM FORMAÇÃO &nbsp;<span>_</span>
    </div>
  </div>

  <div class="divider"></div>

  <!-- TERMINAL INTRO -->
  <div class="terminal-block">
    <div class="prompt">whoami</div>
    <div class="output">
      Olá, sou o <span class="highlight">Pedro Luiz</span> — estudante apaixonado por tecnologia<br>
      e em constante evolução no mundo do desenvolvimento.
    </div>
    <div class="prompt">cat mission.txt</div>
    <div class="output">
      Aprender · Construir · Melhorar · Repetir.<br>
      Cada linha de código é um passo a mais.
    </div>
    <div class="prompt">status --current<span style="animation: cursor-blink 1s step-end infinite; color: var(--green);">█</span></div>
    <div class="output">
      <span class="highlight">[ONLINE]</span> Estudando e desenvolvendo projetos pessoais.
    </div>
  </div>

  <!-- SOBRE -->
  <div class="section-title">// sobre.init</div>
  <div class="stats-grid">
    <div class="stat-card">
      <span class="stat-value">🎓</span>
      <span class="stat-label">Estudando</span>
    </div>
    <div class="stat-card">
      <span class="stat-value">🇧🇷</span>
      <span class="stat-label">Brasil</span>
    </div>
    <div class="stat-card">
      <span class="stat-value">∞</span>
      <span class="stat-label">Curiosidade</span>
    </div>
    <div class="stat-card">
      <span class="stat-value">⚡</span>
      <span class="stat-label">Sempre online</span>
    </div>
  </div>

  <!-- STACK -->
  <div class="section-title">// stack.log</div>
  <div class="skills-wrap">
    <span class="skill-tag main">Python</span>
    <span class="skill-tag main">JavaScript</span>
    <span class="skill-tag main">HTML / CSS</span>
    <span class="skill-tag">Git</span>
    <span class="skill-tag">Linux</span>
    <span class="skill-tag">VS Code</span>
    <span class="skill-tag">SQL</span>
    <span class="skill-tag">Node.js</span>
    <span class="skill-tag">React</span>
    <span class="skill-tag">C</span>
  </div>

  <!-- PROGRESSO -->
  <div class="section-title">// skills.progress</div>
  <div class="progress-list">
    <div class="progress-item">
      <span class="progress-name">Lógica / Algoritmos</span>
      <div class="bar-track"><div class="bar-fill" style="width:78%"></div></div>
      <span class="bar-pct">78%</span>
    </div>
    <div class="progress-item">
      <span class="progress-name">Python</span>
      <div class="bar-track"><div class="bar-fill" style="width:65%"></div></div>
      <span class="bar-pct">65%</span>
    </div>
    <div class="progress-item">
      <span class="progress-name">Web (HTML/CSS/JS)</span>
      <div class="bar-track"><div class="bar-fill" style="width:55%"></div></div>
      <span class="bar-pct">55%</span>
    </div>
    <div class="progress-item">
      <span class="progress-name">Git & Versionamento</span>
      <div class="bar-track"><div class="bar-fill" style="width:60%"></div></div>
      <span class="bar-pct">60%</span>
    </div>
    <div class="progress-item">
      <span class="progress-name">Banco de Dados</span>
      <div class="bar-track"><div class="bar-fill" style="width:40%"></div></div>
      <span class="bar-pct">40%</span>
    </div>
  </div>

  <!-- CONTATO -->
  <div class="section-title">// connect.sh</div>
  <div class="contact-row">
    <a class="contact-btn" href="#">⬡ GitHub</a>
    <a class="contact-btn" href="#">✉ Email</a>
    <a class="contact-btn" href="#">in LinkedIn</a>
  </div>

  <div class="divider"></div>

  <!-- FOOTER -->
  <div class="footer">
    <em>"The quieter you become, the more you can hear."</em><br><br>
    // Pedro Luiz · README.md · gerado com 💚
  </div>

  <!-- MARKDOWN EXPORT -->
  <div class="md-section">
    <div class="md-label">// copie o README.md para seu GitHub</div>
    <div class="md-box" id="mdContent">
<!-- PEDRO LUIZ — GitHub Profile README -->

<div align="center">

```
██████╗ ███████╗██████╗ ██████╗  ██████╗
██╔══██╗██╔════╝██╔══██╗██╔══██╗██╔═══██╗
██████╔╝█████╗  ██║  ██║██████╔╝██║   ██║
██╔═══╝ ██╔══╝  ██║  ██║██╔══██╗██║   ██║
██║     ███████╗██████╔╝██║  ██║╚██████╔╝
╚═╝     ╚══════╝╚═════╝ ╚═╝  ╚═╝ ╚═════╝
```

### `> Olá, eu sou Pedro Luiz_`

*Desenvolvedor em formação · Apaixonado por tecnologia · Brasil 🇧🇷*

</div>

---

## 💻 `whoami`

```bash
$ cat sobre.txt
```

> Estudante de desenvolvimento de software em constante evolução.
> Acredito que cada linha de código é uma oportunidade de aprender algo novo.
> **Status:** 🟢 Online — estudando e construindo projetos.

---

## ⚡ `stack.log`

![Python](https://img.shields.io/badge/Python-00FF41?style=for-the-badge&logo=python&logoColor=black)
![JavaScript](https://img.shields.io/badge/JavaScript-00FF41?style=for-the-badge&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/HTML5-00FF41?style=for-the-badge&logo=html5&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-00FF41?style=for-the-badge&logo=css3&logoColor=black)
![Git](https://img.shields.io/badge/Git-00FF41?style=for-the-badge&logo=git&logoColor=black)
![Linux](https://img.shields.io/badge/Linux-00FF41?style=for-the-badge&logo=linux&logoColor=black)
![VS Code](https://img.shields.io/badge/VSCode-00FF41?style=for-the-badge&logo=visualstudiocode&logoColor=black)

---

## 📊 `skills.progress`

```
Lógica / Algoritmos  ████████████████░░░░  78%
Python               █████████████░░░░░░░  65%
Web (HTML/CSS/JS)    ███████████░░░░░░░░░  55%
Git & Versionamento  ████████████░░░░░░░░  60%
Banco de Dados       ████████░░░░░░░░░░░░  40%
```

---

## 📈 `github.stats`

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=SEU_USERNAME&show_icons=true&theme=chartreuse-dark&bg_color=020c06&title_color=00FF41&text_color=b0ffb8&icon_color=00FF41&border_color=00FF41)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SEU_USERNAME&layout=compact&theme=chartreuse-dark&bg_color=020c06&title_color=00FF41&text_color=b0ffb8&border_color=00FF41)

</div>

---

## 📡 `connect.sh`

[![GitHub](https://img.shields.io/badge/GitHub-00FF41?style=for-the-badge&logo=github&logoColor=black)](https://github.com/SEU_USERNAME)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-00FF41?style=for-the-badge&logo=linkedin&logoColor=black)](https://linkedin.com/in/SEU_USUARIO)
[![Email](https://img.shields.io/badge/Email-00FF41?style=for-the-badge&logo=gmail&logoColor=black)](mailto:SEU_EMAIL)

---

<div align="center">

*"The quieter you become, the more you can hear."*

`// Pedro Luiz · README.md`

</div>
    </div>
    <button class="copy-btn" onclick="copyMD()">[ COPIAR README.md ]</button>
  </div>

</div>

<script>
function copyMD() {
  const text = document.getElementById('mdContent').innerText;
  navigator.clipboard.writeText(text).then(() => {
    const btn = document.querySelector('.copy-btn');
    btn.textContent = '[ COPIADO ✓ ]';
    setTimeout(() => btn.textContent = '[ COPIAR README.md ]', 2000);
  });
}
</script>
</body>
</html>
