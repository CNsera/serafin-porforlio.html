<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Serafin II T Cuizon — Web Developer & Automation Freelancer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700;800&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #F5FBF8;
    --panel: #FFFFFF;
    --ink: #10241E;
    --ink-soft: #4B665C;
    --line: #DCEBE3;
    --lime: #22C55E;
    --lime-tint: #E7F9EE;
    --violet: #7C3AED;
    --violet-tint: #F2EBFF;
    --amber: #F59E0B;
    --amber-tint: #FFF4E0;
    --display: 'Sora', sans-serif;
    --sans: 'Inter', system-ui, sans-serif;
    --mono: 'JetBrains Mono', ui-monospace, monospace;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{margin:0; background:var(--bg); color:var(--ink); font-family:var(--sans); line-height:1.55;}
  ::selection{background:var(--lime); color:#fff;}
  a{color:inherit;}
  section{padding:96px 24px; max-width:1040px; margin:0 auto;}
  @media(max-width:640px){ section{padding:64px 18px;} }

  /* ---------- Nav ---------- */
  .nav{
    position:sticky; top:0; z-index:50;
    display:flex; align-items:center; justify-content:space-between;
    padding:16px 32px; background:rgba(245,251,248,.85); backdrop-filter:blur(8px);
    border-bottom:1px solid var(--line);
  }
  .nav .logo{font-family:var(--mono); font-weight:700; font-size:15px;}
  .nav .logo span{color:var(--lime);}
  .navlinks{display:flex; gap:26px; list-style:none; margin:0; padding:0;}
  .navlinks a{
    font-family:var(--sans); font-size:14px; font-weight:600; text-decoration:none; color:var(--ink-soft);
    transition:color .15s ease;
  }
  .navlinks a:hover{color:var(--ink);}
  @media(max-width:640px){ .navlinks{gap:14px;} .navlinks a{font-size:12.5px;} }

  /* ---------- Hero ---------- */
  .hero{padding-top:70px; padding-bottom:60px; position:relative;}
  .badge{
    display:inline-flex; align-items:center; gap:8px;
    font-family:var(--mono); font-size:12px; font-weight:600; color:#0B8A3F;
    background:var(--lime-tint); border:1px solid #BEEBCF; padding:6px 14px; border-radius:999px;
  }
  .badge .pulse{width:7px; height:7px; border-radius:50%; background:var(--lime); animation:pulse 1.6s ease-in-out infinite;}
  @keyframes pulse{0%,100%{opacity:1; transform:scale(1);} 50%{opacity:.4; transform:scale(1.4);}}
  @media (prefers-reduced-motion: reduce){ .badge .pulse{animation:none;} }

  .hero h1{
    font-family:var(--display); font-weight:800; font-size:52px; letter-spacing:-0.02em;
    margin:22px 0 10px; line-height:1.08;
  }
  @media(max-width:640px){ .hero h1{font-size:34px;} }
  .hero h1 .accent{color:var(--lime);}
  .hero p.tagline{font-size:18px; color:var(--ink-soft); max-width:560px; margin:0 0 30px;}

  .hero-cta{display:flex; gap:12px; flex-wrap:wrap;}
  .btn{
    font-family:var(--sans); font-weight:700; font-size:14px;
    padding:13px 24px; border-radius:10px; text-decoration:none; border:1px solid transparent;
    transition:transform .15s ease, box-shadow .15s ease;
  }
  .btn:hover{transform:translateY(-2px);}
  .btn-primary{background:var(--ink); color:#fff;}
  .btn-primary:hover{box-shadow:0 12px 26px -14px rgba(16,36,30,.55);}
  .btn-ghost{background:var(--panel); color:var(--ink); border-color:var(--line);}

  /* automation flow diagram */
  .flow{
    margin-top:56px; background:var(--panel); border:1px solid var(--line); border-radius:16px;
    padding:28px 26px; display:flex; align-items:center; justify-content:space-between; gap:8px;
    overflow-x:auto;
  }
  .flow-node{
    display:flex; flex-direction:column; align-items:center; gap:8px; min-width:120px; text-align:center;
  }
  .flow-node .chip{
    width:52px; height:52px; border-radius:14px; display:flex; align-items:center; justify-content:center;
    font-family:var(--mono); font-weight:700; font-size:18px;
  }
  .flow-node .label{font-family:var(--mono); font-size:11.5px; font-weight:600; color:var(--ink-soft);}
  .flow-line{
    flex:1; height:2px; background:repeating-linear-gradient(90deg, var(--line) 0 6px, transparent 6px 12px);
    position:relative; min-width:30px;
  }
  .flow-line .dot{
    position:absolute; top:-3px; width:8px; height:8px; border-radius:50%; background:var(--lime);
    animation:travel 3s linear infinite;
  }
  @keyframes travel{0%{left:0%; opacity:0;} 10%{opacity:1;} 90%{opacity:1;} 100%{left:100%; opacity:0;}}
  @media (prefers-reduced-motion: reduce){ .flow-line .dot{animation:none; left:50%;} }
  @media(max-width:760px){ .flow{flex-direction:column;} .flow-line{width:2px; height:30px; min-width:0;} .flow-line .dot{animation:none; display:none;} }

  /* ---------- reveal ---------- */
  .reveal{opacity:0; transform:translateY(16px); transition:opacity .6s ease, transform .6s ease;}
  .reveal.in{opacity:1; transform:translateY(0);}
  @media (prefers-reduced-motion: reduce){ .reveal{opacity:1; transform:none; transition:none;} }

  .eyebrow{
    font-family:var(--mono); font-size:12px; font-weight:600; color:var(--lime);
    text-transform:uppercase; letter-spacing:.08em; margin-bottom:12px;
  }
  .eyebrow::before{content:'▹ '; }
  h2.sec-title{font-family:var(--display); font-size:32px; font-weight:800; margin:0 0 30px; letter-spacing:-0.01em;}

  /* ---------- About ---------- */
  .about-grid{display:grid; grid-template-columns:1fr 1fr; gap:44px; align-items:start;}
  @media(max-width:760px){ .about-grid{grid-template-columns:1fr;} }
  .about-grid p{color:var(--ink-soft); font-size:15.5px;}
  .facts{display:grid; grid-template-columns:1fr 1fr; gap:14px;}
  .fact{
    background:var(--panel); border:1px solid var(--line); border-radius:12px; padding:16px 18px;
  }
  .fact .k{font-family:var(--mono); font-size:11px; color:var(--ink-soft); text-transform:uppercase; letter-spacing:.05em;}
  .fact .v{font-family:var(--sans); font-size:16px; font-weight:700; margin-top:4px;}

  /* ---------- Skills ---------- */
  .skill-cols{display:grid; grid-template-columns:repeat(3,1fr); gap:20px;}
  @media(max-width:760px){ .skill-cols{grid-template-columns:1fr;} }
  .skill-card{
    background:var(--panel); border:1px solid var(--line); border-radius:14px; padding:22px;
    transition:transform .2s ease, box-shadow .2s ease;
  }
  .skill-card:hover{transform:translateY(-4px); box-shadow:0 16px 34px -20px rgba(16,36,30,.25);}
  .skill-card .icon{
    width:44px; height:44px; border-radius:12px; display:flex; align-items:center; justify-content:center;
    font-family:var(--mono); font-weight:700; font-size:18px; margin-bottom:14px;
  }
  .skill-card h3{font-family:var(--display); font-size:18px; margin:0 0 8px;}
  .skill-card ul{margin:0; padding-left:18px; color:var(--ink-soft); font-size:14px;}
  .skill-card li{margin-bottom:6px;}

  /* ---------- Services ---------- */
  .services{display:grid; grid-template-columns:repeat(3,1fr); gap:20px;}
  @media(max-width:760px){ .services{grid-template-columns:1fr;} }
  .service-card{
    border:1px solid var(--line); border-radius:14px; padding:24px; background:var(--panel);
  }
  .service-card .num{font-family:var(--mono); font-size:12px; color:var(--ink-soft); margin-bottom:10px;}
  .service-card h3{font-family:var(--display); font-size:17px; margin:0 0 8px;}
  .service-card p{color:var(--ink-soft); font-size:14px; margin:0;}

  /* ---------- Projects ---------- */
  .projects{display:grid; grid-template-columns:repeat(2,1fr); gap:20px;}
  @media(max-width:760px){ .projects{grid-template-columns:1fr;} }
  .pcard{
    background:var(--panel); border:1px solid var(--line); border-radius:14px; padding:24px;
    display:flex; flex-direction:column; height:100%; transition:transform .2s ease, box-shadow .2s ease;
  }
  .pcard:hover{transform:translateY(-4px); box-shadow:0 16px 34px -20px rgba(16,36,30,.25);}
  .pcard h3{font-family:var(--display); font-size:18px; margin:0 0 8px;}
  .pcard p{color:var(--ink-soft); font-size:14px; margin:0 0 16px;}
  .tagrow{display:flex; flex-wrap:wrap; gap:6px; margin-top:auto; margin-bottom:14px;}
  .tagrow span{font-family:var(--mono); font-size:11px; font-weight:700; padding:4px 9px; border-radius:6px;}
  .pcard .links{font-family:var(--mono); font-size:13px; font-weight:600;}
  .pcard .links a{color:var(--lime); text-decoration:none; border-bottom:1px solid currentColor;}

  /* ---------- Contact ---------- */
  .contact-box{
    background:var(--ink); color:#fff; border-radius:18px; padding:48px;
    display:flex; flex-wrap:wrap; justify-content:space-between; align-items:center; gap:24px;
  }
  .contact-box h2{font-family:var(--display); font-size:28px; margin:0;}
  .contact-box p{color:#B9D6C8; margin:8px 0 0;}
  .contact-links{display:flex; gap:12px; flex-wrap:wrap;}
  .contact-links a{
    font-family:var(--mono); font-size:13px; font-weight:600; color:#fff;
    border:1px solid rgba(255,255,255,.22); padding:10px 18px; border-radius:9px; text-decoration:none;
    transition:background .15s ease;
  }
  .contact-links a:hover{background:rgba(255,255,255,.12);}

  footer{text-align:center; padding:30px 24px 46px; font-family:var(--mono); font-size:12px; color:var(--ink-soft);}

  :focus-visible{outline:2px solid var(--lime); outline-offset:2px;}
</style>
</head>
<body>

<nav class="nav">
  <div class="logo">serafin<span>.</span>dev</div>
  <ul class="navlinks">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="top">
  <span class="badge"><span class="pulse"></span> Open to freelance & full-time work</span>
  <h1>Hi, I'm Serafin II T Cuizon —<br>I build <span class="accent">websites</span> and <span class="accent">automations</span> that save people time.</h1>
  <p class="tagline">18-year-old freelance web developer focused on clean, functional builds and automating the repetitive parts of work so people don't have to.</p>
  <div class="hero-cta">
    <a class="btn btn-primary" href="#projects">View my work</a>
    <a class="btn btn-ghost" href="#contact">Hire me</a>
  </div>

  <div class="flow reveal">
    <div class="flow-node">
      <div class="chip" style="background:var(--violet-tint); color:var(--violet);">IN</div>
      <div class="label">Manual task</div>
    </div>
    <div class="flow-line"><div class="dot"></div></div>
    <div class="flow-node">
      <div class="chip" style="background:var(--lime-tint); color:var(--lime);">⚙</div>
      <div class="label">Automate it</div>
    </div>
    <div class="flow-line"><div class="dot" style="animation-delay:1.5s;"></div></div>
    <div class="flow-node">
      <div class="chip" style="background:var(--amber-tint); color:var(--amber);">OUT</div>
      <div class="label">Time saved</div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="eyebrow">About</div>
  <h2 class="sec-title">A little about me</h2>
  <div class="about-grid">
    <div class="reveal">
      <p>I'm a web developer, freelancer and virtual assistant, i can offer my skills and talents to you but not for free i am 18yrs old.</p>
      <p>I'm currently between formal jobs and focused on freelance projects, so I have the time and energy to take on new work and learn fast.</p>
    </div>
    <div class="facts reveal">
      <div class="fact"><div class="k">Name</div><div class="v">Serafin II T Cuizon</div></div>
      <div class="fact"><div class="k">Age</div><div class="v">18 years old</div></div>
      <div class="fact"><div class="k">Status</div><div class="v">Grade 12 Student</div></div>
      <div class="fact"><div class="k">Focus</div><div class="v">Automation and Web development</div></div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="eyebrow">Skills</div>
  <h2 class="sec-title">What I'm good at</h2>
  <div class="skill-cols">
    <div class="skill-card reveal">
      <div class="icon" style="background:var(--lime-tint); color:var(--lime);">{ }</div>
      <h3>Web Development</h3>
      <ul>
        <li>HTML, CSS & JavaScript</li>
        <li>Responsive, mobile-first layouts</li>
        <li>Building sites from scratch or templates</li>
      </ul>
    </div>
    <div class="skill-card reveal">
      <div class="icon" style="background:var(--violet-tint); color:var(--violet);">⚙</div>
      <h3>Automation</h3>
      <ul>
        <li>Scripting repetitive tasks</li>
        <li>Workflow tools (Zapier, Make, etc.)</li>
        <li>Data entry & file-handling automation</li>
      </ul>
    </div>
    <div class="skill-card reveal">
      <div class="icon" style="background:var(--amber-tint); color:var(--amber);">$</div>
      <h3>Freelancing</h3>
      <ul>
        <li>Client communication</li>
        <li>Scoping & delivering on deadlines</li>
        <li>Managing multiple small projects</li>
      </ul>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="eyebrow">Services</div>
  <h2 class="sec-title">How I can help</h2>
  <div class="services">
    <div class="service-card reveal">
      <div class="num">01</div>
      <h3>Website Development</h3>
      <p>Simple, fast, good-looking websites for individuals, small businesses, or portfolios.</p>
    </div>
    <div class="service-card reveal">
      <div class="num">02</div>
      <h3>Task Automation</h3>
      <p>Turning repetitive manual work into scripts or workflows that run on their own.</p>
    </div>
    <div class="service-card reveal">
      <div class="num">03</div>
      <h3>Freelance Projects</h3>
      <p>Open to short-term gigs, ongoing contracts, or one-off builds — flexible and reliable.</p>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="eyebrow">Projects</div>
  <h2 class="sec-title">Some things I've built</h2>
  <div class="projects">
    <div class="pcard reveal">
      <h3>Project Name One</h3>
      <p>A short description of this project — what it does and the problem it solves. Replace with your real project.</p>
      <div class="tagrow">
        <span style="background:var(--lime-tint); color:var(--lime);">HTML/CSS</span>
        <span style="background:var(--violet-tint); color:var(--violet);">JavaScript</span>
      </div>
      <div class="links"><a href="#">View project →</a></div>
    </div>
    <div class="pcard reveal">
      <h3>Project Name Two</h3>
      <p>A short description of this project — what it does and the problem it solves. Replace with your real project.</p>
      <div class="tagrow">
        <span style="background:var(--amber-tint); color:var(--amber);">Python</span>
        <span style="background:var(--violet-tint); color:var(--violet);">Automation</span>
      </div>
      <div class="links"><a href="#">View project →</a></div>
    </div>
    <div class="pcard reveal">
      <h3>Project Name Three</h3>
      <p>A short description of this project — what it does and the problem it solves. Replace with your real project.</p>
      <div class="tagrow">
        <span style="background:var(--lime-tint); color:var(--lime);">Web App</span>
      </div>
      <div class="links"><a href="#">View project →</a></div>
    </div>
    <div class="pcard reveal">
      <h3>Project Name Four</h3>
      <p>A short description of this project — what it does and the problem it solves. Replace with your real project.</p>
      <div class="tagrow">
        <span style="background:var(--amber-tint); color:var(--amber);">Script</span>
      </div>
      <div class="links"><a href="#">View project →</a></div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="eyebrow">Contact</div>
  <div class="contact-box reveal">
    <div>
      <h2>Let's work together.</h2>
      <p>Open to freelance gigs, small business sites, and automation projects.</p>
    </div>
    <div class="contact-links">
      <a href="mailto: seracuizon245@gmail.com">Email me</a>
      <a href="https://www.instagram.com/_c0ok1esndcr3am?igsh=enZhcnd6eHNvbjR3">Instagram</a>
      <a href="https://vt.tiktok.com/ZSXd5aLHg/">TikTok</a>
      <a href="https://www.facebook.com/kaoruu159">Facebook</a>
    </div>
  </div>
</section>

<footer>© 2026 Serafin II T Cuizon — built with HTML, CSS & a little automation</footer>

<script>
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); } });
  }, {threshold:0.15});
  document.querySelectorAll('.reveal').forEach(el=>io.observe(el));
</script>

</body>
</html>
