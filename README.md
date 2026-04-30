
import os

html_content = open('/tmp/jawwad-github-profile.html', 'w') if False else None

content = '''<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Jawad Ahmed Khan — GitHub Profile</title>
  <link href="https://api.fontshare.com/v2/css?f[]=cabinet-grotesk@400,500,700,800&f[]=satoshi@400,500,700&display=swap" rel="stylesheet">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    :root {
      --font-display: "Cabinet Grotesk", "Inter", sans-serif;
      --font-body:    "Satoshi", "Inter", sans-serif;
      --font-mono:    "JetBrains Mono", monospace;
      --text-xs:   clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
      --text-sm:   clamp(0.875rem, 0.8rem + 0.35vw, 1rem);
      --text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
      --text-lg:   clamp(1.125rem, 1rem + 0.75vw, 1.5rem);
      --text-xl:   clamp(1.5rem, 1.2rem + 1.25vw, 2.25rem);
      --text-2xl:  clamp(2rem, 1.2rem + 2.5vw, 3.5rem);
      --space-1:0.25rem;--space-2:0.5rem;--space-3:0.75rem;--space-4:1rem;
      --space-5:1.25rem;--space-6:1.5rem;--space-8:2rem;--space-10:2.5rem;
      --space-12:3rem;--space-16:4rem;
      --radius-sm:0.375rem;--radius-md:0.5rem;--radius-lg:0.75rem;
      --radius-xl:1rem;--radius-full:9999px;
      --transition:180ms cubic-bezier(0.16,1,0.3,1);
    }
    [data-theme="dark"] {
      --bg:#0d1117;--surface:#161b22;--surface-2:#1c2128;
      --border:#30363d;--divider:#21262d;
      --text:#e6edf3;--text-muted:#8b949e;--text-faint:#484f58;
      --primary:#58a6ff;--primary-hover:#1f6feb;--primary-glow:rgba(88,166,255,0.15);
      --accent-green:#3fb950;--accent-orange:#e3b341;--accent-purple:#bc8cff;--accent-pink:#f778ba;
      --shadow-sm:0 1px 3px rgba(0,0,0,0.4);--shadow-md:0 4px 16px rgba(0,0,0,0.5);--shadow-lg:0 12px 40px rgba(0,0,0,0.6);
    }
    [data-theme="light"] {
      --bg:#f6f8fa;--surface:#ffffff;--surface-2:#f0f2f5;
      --border:#d0d7de;--divider:#e1e4e8;
      --text:#1f2328;--text-muted:#636c76;--text-faint:#9da5af;
      --primary:#0969da;--primary-hover:#0550ae;--primary-glow:rgba(9,105,218,0.12);
      --accent-green:#1a7f37;--accent-orange:#9a6700;--accent-purple:#8250df;--accent-pink:#bf3989;
      --shadow-sm:0 1px 3px rgba(31,35,40,0.08);--shadow-md:0 4px 16px rgba(31,35,40,0.1);--shadow-lg:0 12px 40px rgba(31,35,40,0.14);
    }
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
    html{scroll-behavior:smooth;-webkit-font-smoothing:antialiased;}
    body{font-family:var(--font-body);font-size:var(--text-base);color:var(--text);background:var(--bg);line-height:1.6;min-height:100dvh;transition:background var(--transition),color var(--transition);}
    img{display:block;max-width:100%;}
    a{color:var(--primary);text-decoration:none;transition:color var(--transition);}
    a:hover{color:var(--primary-hover);}
    .page-wrapper{max-width:900px;margin-inline:auto;padding:var(--space-8) var(--space-4);}
    .theme-toggle{position:fixed;top:var(--space-4);right:var(--space-4);z-index:100;width:40px;height:40px;border-radius:var(--radius-full);background:var(--surface);border:1px solid var(--border);display:flex;align-items:center;justify-content:center;cursor:pointer;box-shadow:var(--shadow-sm);transition:background var(--transition),border-color var(--transition),box-shadow var(--transition);color:var(--text-muted);}
    .theme-toggle:hover{background:var(--surface-2);box-shadow:var(--shadow-md);color:var(--text);}
    .hero{padding:var(--space-12) var(--space-6);background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-xl);position:relative;overflow:hidden;margin-bottom:var(--space-6);box-shadow:var(--shadow-md);}
    .hero::before{content:"";position:absolute;inset:0;background:radial-gradient(ellipse 70% 60% at 70% 0%,var(--primary-glow),transparent 65%),radial-gradient(ellipse 40% 50% at 10% 100%,rgba(188,140,255,0.08),transparent 55%);pointer-events:none;}
    .hero-top{display:flex;align-items:center;gap:var(--space-6);flex-wrap:wrap;position:relative;}
    .avatar-wrap{position:relative;flex-shrink:0;}
    .avatar{width:90px;height:90px;border-radius:var(--radius-full);border:3px solid var(--primary);box-shadow:0 0 0 5px var(--primary-glow);object-fit:cover;background:var(--surface-2);}
    .avatar-status{position:absolute;bottom:4px;right:4px;width:14px;height:14px;border-radius:var(--radius-full);background:var(--accent-green);border:2px solid var(--surface);}
    .hero-info{flex:1;min-width:200px;}
    .hero-name{font-family:var(--font-display);font-size:var(--text-2xl);font-weight:800;line-height:1.1;letter-spacing:-0.03em;color:var(--text);}
    .hero-title{margin-top:var(--space-2);font-size:var(--text-sm);color:var(--text-muted);display:flex;align-items:center;gap:var(--space-2);flex-wrap:wrap;}
    .pill{display:inline-flex;align-items:center;gap:var(--space-1);padding:2px var(--space-3);border-radius:var(--radius-full);font-size:var(--text-xs);font-weight:500;border:1px solid transparent;}
    .pill-blue{background:rgba(88,166,255,0.12);color:var(--primary);border-color:rgba(88,166,255,0.25);}
    .pill-green{background:rgba(63,185,80,0.12);color:var(--accent-green);border-color:rgba(63,185,80,0.25);}
    .pill-purple{background:rgba(188,140,255,0.12);color:var(--accent-purple);border-color:rgba(188,140,255,0.25);}
    [data-theme="light"] .pill-blue{background:rgba(9,105,218,0.08);color:var(--primary);border-color:rgba(9,105,218,0.2);}
    [data-theme="light"] .pill-green{background:rgba(26,127,55,0.08);color:var(--accent-green);border-color:rgba(26,127,55,0.2);}
    [data-theme="light"] .pill-purple{background:rgba(130,80,223,0.08);color:var(--accent-purple);border-color:rgba(130,80,223,0.2);}
    .hero-bio{margin-top:var(--space-5);font-size:var(--text-base);color:var(--text-muted);max-width:62ch;line-height:1.7;position:relative;}
    .section-card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius-xl);padding:var(--space-6);margin-bottom:var(--space-5);box-shadow:var(--shadow-sm);transition:box-shadow var(--transition);}
    .section-card:hover{box-shadow:var(--shadow-md);}
    .section-title{font-family:var(--font-display);font-size:var(--text-lg);font-weight:700;color:var(--text);display:flex;align-items:center;gap:var(--space-2);margin-bottom:var(--space-4);padding-bottom:var(--space-3);border-bottom:1px solid var(--divider);}
    .what-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(min(240px,100%),1fr));gap:var(--space-3);}
    .what-item{background:var(--surface-2);border:1px solid var(--border);border-radius:var(--radius-lg);padding:var(--space-4);transition:border-color var(--transition),box-shadow var(--transition);}
    .what-item:hover{border-color:var(--primary);box-shadow:0 0 0 3px var(--primary-glow);}
    .what-item-icon{font-size:1.5rem;margin-bottom:var(--space-2);}
    .what-item h3{font-family:var(--font-display);font-size:var(--text-sm);font-weight:700;color:var(--text);margin-bottom:var(--space-1);}
    .what-item p{font-size:var(--text-xs);color:var(--text-muted);line-height:1.5;}
    .tech-grid{display:flex;flex-wrap:wrap;gap:var(--space-2);}
    .tech-badge{display:inline-flex;align-items:center;gap:var(--space-1);padding:var(--space-1) var(--space-3);background:var(--surface-2);border:1px solid var(--border);border-radius:var(--radius-full);font-family:var(--font-mono);font-size:var(--text-xs);color:var(--text-muted);transition:border-color var(--transition),color var(--transition),background var(--transition);cursor:default;}
    .tech-badge:hover{border-color:var(--primary);color:var(--text);background:var(--primary-glow);}
    .tech-category{font-family:var(--font-display);font-size:var(--text-xs);font-weight:700;text-transform:uppercase;letter-spacing:0.08em;color:var(--text-faint);width:100%;margin-top:var(--space-3);margin-bottom:var(--space-1);}
    .tech-category:first-child{margin-top:0;}
    .stats-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(min(280px,100%),1fr));gap:var(--space-4);}
    .stats-img{width:100%;border-radius:var(--radius-lg);border:1px solid var(--border);}
    .socials-row{display:flex;flex-wrap:wrap;gap:var(--space-3);}
    .social-link{display:inline-flex;align-items:center;gap:var(--space-2);padding:var(--space-2) var(--space-4);border-radius:var(--radius-lg);border:1px solid var(--border);background:var(--surface-2);font-size:var(--text-sm);font-weight:500;color:var(--text-muted);transition:all var(--transition);text-decoration:none;}
    .social-link:hover{color:var(--text);border-color:var(--primary);background:var(--primary-glow);transform:translateY(-1px);box-shadow:var(--shadow-sm);}
    .social-icon{width:18px;height:18px;border-radius:3px;}
    .availability{background:linear-gradient(135deg,rgba(63,185,80,0.08) 0%,rgba(88,166,255,0.08) 100%);border:1px solid rgba(63,185,80,0.25);border-radius:var(--radius-xl);padding:var(--space-5) var(--space-6);display:flex;align-items:center;gap:var(--space-4);flex-wrap:wrap;}
    [data-theme="light"] .availability{background:linear-gradient(135deg,rgba(26,127,55,0.06) 0%,rgba(9,105,218,0.06) 100%);border-color:rgba(26,127,55,0.2);}
    .avail-dot{width:10px;height:10px;border-radius:var(--radius-full);background:var(--accent-green);box-shadow:0 0 8px rgba(63,185,80,0.6);flex-shrink:0;animation:pulse-dot 2s ease-in-out infinite;}
    @keyframes pulse-dot{0%,100%{box-shadow:0 0 6px rgba(63,185,80,0.5);}50%{box-shadow:0 0 14px rgba(63,185,80,0.9);}}
    .avail-text{flex:1;}
    .avail-text h3{font-family:var(--font-display);font-size:var(--text-base);font-weight:700;color:var(--text);}
    .avail-text p{font-size:var(--text-sm);color:var(--text-muted);margin-top:2px;}
    .avail-services{display:flex;flex-wrap:wrap;gap:var(--space-2);margin-top:var(--space-2);}
    .footer{text-align:center;padding:var(--space-6) 0 var(--space-4);font-size:var(--text-xs);color:var(--text-faint);border-top:1px solid var(--divider);margin-top:var(--space-6);}
    .footer a{color:var(--text-faint);}
    .footer a:hover{color:var(--primary);}
    .visitor-wrap{display:flex;justify-content:center;margin-top:var(--space-4);}
    @keyframes fade-up{from{opacity:0;transform:translateY(16px);}to{opacity:1;transform:translateY(0);}}
    .fade-up{animation:fade-up 0.55s cubic-bezier(0.16,1,0.3,1) both;}
    .delay-1{animation-delay:0.08s;}.delay-2{animation-delay:0.16s;}.delay-3{animation-delay:0.24s;}
    .delay-4{animation-delay:0.32s;}.delay-5{animation-delay:0.40s;}
    @media (prefers-reduced-motion: reduce){.fade-up{animation:none;}}
    @media (max-width: 640px){
      .hero{padding:var(--space-8) var(--space-4);}
      .hero-top{gap:var(--space-4);}
      .avatar{width:72px;height:72px;}
      .stats-grid{grid-template-columns:1fr;}
    }
  </style>
</head>
<body>
<button class="theme-toggle" data-theme-toggle aria-label="Switch to light mode">
  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
</button>
<div class="page-wrapper">
  <section class="hero fade-up">
    <div class="hero-top">
      <div class="avatar-wrap">
        <img class="avatar" src="https://avatars.githubusercontent.com/jawwadahmedkhan?v=4" onerror="this.src=\'https://ui-avatars.com/api/?name=JAK&background=1f6feb&color=fff&size=90\'" alt="Jawad Ahmed Khan" width="90" height="90" loading="eager">
        <div class="avatar-status" title="Available for work"></div>
      </div>
      <div class="hero-info">
        <h1 class="hero-name">Jawad Ahmed Khan</h1>
        <div class="hero-title">
          <span class="pill pill-blue">💻 Frontend Developer</span>
          <span class="pill pill-green">🔍 SEO Specialist</span>
          <span class="pill pill-purple">🤖 Prompt Engineer</span>
        </div>
      </div>
    </div>
    <p class="hero-bio">Passionate developer &amp; digital marketing professional building beautiful, optimized web experiences. I blend technical precision with SEO expertise to craft high-performing digital products.</p>
  </section>

  <section class="section-card fade-up delay-1">
    <h2 class="section-title"><span>🚀</span> What I Do</h2>
    <div class="what-grid">
      <div class="what-item"><div class="what-item-icon">💻</div><h3>Frontend Development</h3><p>Crafting responsive, pixel-perfect web interfaces with modern HTML, CSS, JS &amp; React.</p></div>
      <div class="what-item"><div class="what-item-icon">🔍</div><h3>SEO Optimization</h3><p>Driving organic traffic through on-page, off-page &amp; technical SEO strategies.</p></div>
      <div class="what-item"><div class="what-item-icon">🤖</div><h3>Prompt Engineering</h3><p>Leveraging AI tools like ChatGPT &amp; Perplexity to solve complex problems efficiently.</p></div>
    </div>
  </section>

  <section class="section-card fade-up delay-2">
    <h2 class="section-title"><span>🛠️</span> Tech Stack &amp; Skills</h2>
    <div class="tech-grid">
      <div class="tech-category">Frontend</div>
      <span class="tech-badge">HTML5</span><span class="tech-badge">CSS3 / SASS</span><span class="tech-badge">JavaScript</span><span class="tech-badge">React</span><span class="tech-badge">React Native</span><span class="tech-badge">Next.js</span><span class="tech-badge">Angular</span><span class="tech-badge">Bootstrap</span>
      <div class="tech-category">Backend &amp; Cloud</div>
      <span class="tech-badge">Node.js</span><span class="tech-badge">NestJS</span><span class="tech-badge">Django</span><span class="tech-badge">Firebase</span><span class="tech-badge">MongoDB</span><span class="tech-badge">MySQL</span><span class="tech-badge">Google Cloud</span><span class="tech-badge">Vercel</span><span class="tech-badge">Netlify</span><span class="tech-badge">Docker</span>
      <div class="tech-category">Languages</div>
      <span class="tech-badge">Python</span><span class="tech-badge">Java</span><span class="tech-badge">TypeScript</span><span class="tech-badge">.NET</span><span class="tech-badge">Web3.js</span><span class="tech-badge">GraphQL</span>
      <div class="tech-category">SEO &amp; Analytics</div>
      <span class="tech-badge">Google Analytics</span><span class="tech-badge">Search Console</span><span class="tech-badge">Keyword Research</span><span class="tech-badge">Technical SEO</span>
      <div class="tech-category">Design &amp; Tools</div>
      <span class="tech-badge">Figma</span><span class="tech-badge">Canva</span><span class="tech-badge">Adobe</span><span class="tech-badge">Git</span><span class="tech-badge">VS Code</span><span class="tech-badge">Jira</span>
    </div>
  </section>

  <section class="section-card fade-up delay-3">
    <h2 class="section-title"><span>📊</span> GitHub Stats</h2>
    <div class="stats-grid">
      <img class="stats-img" src="https://github-readme-stats.vercel.app/api?username=jawwadahmedkhan&theme=dark&hide_border=true&include_all_commits=false&count_private=false&bg_color=161b22&title_color=58a6ff&text_color=8b949e&icon_color=3fb950" alt="GitHub Stats" loading="lazy" width="495" height="195">
      <img class="stats-img" src="https://nirzak-streak-stats.vercel.app/?user=jawwadahmedkhan&theme=dark&hide_border=true&background=161b22&stroke=30363d&ring=58a6ff&fire=e3b341&currStreakLabel=58a6ff" alt="GitHub Streak" loading="lazy" width="495" height="195">
    </div>
    <div style="margin-top:1rem;">
      <img class="stats-img" src="https://github-readme-stats.vercel.app/api/top-langs/?username=jawwadahmedkhan&theme=dark&hide_border=true&include_all_commits=false&count_private=false&layout=compact&bg_color=161b22&title_color=58a6ff&text_color=8b949e" alt="Top Languages" loading="lazy" width="400" height="165" style="max-width:420px;">
    </div>
  </section>

  <section class="section-card fade-up delay-4">
    <h2 class="section-title"><span>📫</span> Connect With Me</h2>
    <div class="socials-row">
      <a href="https://www.linkedin.com/in/jawad-ahmed-khan-seo-services/" target="_blank" rel="noopener noreferrer" class="social-link"><img class="social-icon" src="https://cdn.simpleicons.org/linkedin/0A66C2" alt="" width="18" height="18" loading="lazy"> LinkedIn</a>
      <a href="https://www.upwork.com/freelancers/~01449dba2630d968e7" target="_blank" rel="noopener noreferrer" class="social-link"><img class="social-icon" src="https://cdn.simpleicons.org/upwork/6FDA44" alt="" width="18" height="18" loading="lazy"> Upwork</a>
      <a href="https://www.instagram.com/jawwad_ahmed_khan93/" target="_blank" rel="noopener noreferrer" class="social-link"><img class="social-icon" src="https://cdn.simpleicons.org/instagram/E4405F" alt="" width="18" height="18" loading="lazy"> Instagram</a>
      <a href="https://www.pinterest.com/SEO_Specialist93/" target="_blank" rel="noopener noreferrer" class="social-link"><img class="social-icon" src="https://cdn.simpleicons.org/pinterest/BD081C" alt="" width="18" height="18" loading="lazy"> Pinterest</a>
      <a href="https://www.reddit.com/user/Sensitive-Lab-9325/" target="_blank" rel="noopener noreferrer" class="social-link"><img class="social-icon" src="https://cdn.simpleicons.org/reddit/FF4500" alt="" width="18" height="18" loading="lazy"> Reddit</a>
      <a href="https://github.com/jawwadahmedkhan" target="_blank" rel="noopener noreferrer" class="social-link"><img class="social-icon" src="https://cdn.simpleicons.org/github/ffffff" alt="" width="18" height="18" loading="lazy"> GitHub</a>
    </div>
  </section>

  <div class="availability fade-up delay-5">
    <div class="avail-dot"></div>
    <div class="avail-text">
      <h3>💼 Available for Freelance Projects</h3>
      <p>Open to interesting collaborations and custom projects. Let\'s build something great together.</p>
      <div class="avail-services">
        <span class="pill pill-green">Custom Website Dev</span>
        <span class="pill pill-blue">SEO Optimization</span>
        <span class="pill pill-purple">AI-Powered Solutions</span>
      </div>
    </div>
  </div>

  <div class="visitor-wrap fade-up delay-5" style="margin-top:1.5rem;">
    <a href="https://visitcount.itsvg.in" target="_blank" rel="noopener noreferrer">
      <img src="https://visitcount.itsvg.in/api?id=jawwadahmedkhan&icon=6&color=1" alt="Visitor Count" loading="lazy" height="28">
    </a>
  </div>

  <footer class="footer">
    <p>⭐️ From <a href="https://github.com/jawwadahmedkhan" target="_blank" rel="noopener noreferrer">jawwadahmedkhan</a> &nbsp;·&nbsp; Built with ❤️ and clean code</p>
  </footer>
</div>
<script>
(function(){
  const t=document.querySelector("[data-theme-toggle]"),r=document.documentElement;
  let d=matchMedia("(prefers-color-scheme: dark)").matches?"dark":"light";
  r.setAttribute("data-theme",d);
  const sun=\'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="5"/><path d="M12 1v2M12 21v2M4.22 4.22l1.42 1.42M18.36 18.36l1.42 1.42M1 12h2M21 12h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42"/></svg>\';
  const moon=\'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>\';
  const upd=()=>{t.innerHTML=d==="dark"?sun:moon;t.setAttribute("aria-label","Switch to "+(d==="dark"?"light":"dark")+" mode");};
  upd();
  t&&t.addEventListener("click",()=>{d=d==="dark"?"light":"dark";r.setAttribute("data-theme",d);upd();});
})();
</script>
</body>
</html>'''

os.makedirs('output', exist_ok=True)
with open('output/jawwad-github-profile.html', 'w') as f:
    f.write(content)
print("Written:", os.path.getsize('output/jawwad-github-profile.html'), "bytes")
