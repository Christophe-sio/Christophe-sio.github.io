<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Christophe Zhou — Portfolio</title>
<style>
:root{
  --paper:#F1EEE7;
  --ink:#181510;
  --line:#D9D3C4;
  --blue:#2A3FE0;
  --green:#3E6B4F;
  --muted:#55503F;
  --paper-dark:#15140F;
  --ink-dark:#F6F3EA;
  --line-dark:#3E3A2F;
  padding-top:env(safe-area-inset-top,0px);
  padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){--paper:var(--paper-dark);--ink:var(--ink-dark);--line:var(--line-dark);--blue:#93A0FF;--green:#8FDCAB;--muted:#D8D3C4;}
}
:root[data-theme="dark"]{--paper:var(--paper-dark);--ink:var(--ink-dark);--line:var(--line-dark);--blue:#93A0FF;--green:#8FDCAB;--muted:#D8D3C4;}
*{box-sizing:border-box;}
html{scroll-behavior:smooth;scroll-padding-top:env(safe-area-inset-top,0px);}
body{
  margin:0;background:var(--paper);color:var(--ink);
  font-family:'Aptos','Aptos Display','Segoe UI',system-ui,-apple-system,sans-serif;
  font-size:16.5px;line-height:1.65;
}
h1,h2,.serif{font-family:'Aptos Display','Aptos','Segoe UI',system-ui,-apple-system,sans-serif;}
a{color:var(--blue);text-decoration:none;}
a:hover{text-decoration:underline;}
::selection{background:var(--blue);color:var(--paper);}

.layout{display:flex;min-height:100vh;}

/* --- Sidebar (file explorer) --- */
.sidebar{
  width:240px;flex-shrink:0;border-right:1px solid var(--line);
  padding:28px 20px;position:sticky;top:0;height:100vh;
  display:flex;flex-direction:column;justify-content:space-between;
}
.brand{margin-bottom:36px;}
.brand .dir{color:var(--muted);font-size:13px;}
.brand .name{font-family:inherit;font-weight:600;font-size:23px;margin-top:4px;}
nav.tree ul{list-style:none;margin:0;padding:0;}
nav.tree li{margin-bottom:2px;}
nav.tree a{
  display:flex;align-items:center;gap:8px;color:var(--ink);
  padding:7px 8px;border-radius:4px;font-size:14.5px;
}
nav.tree a::before{content:'›';color:var(--muted);width:10px;}
nav.tree a:hover,nav.tree a.active{background:var(--line);text-decoration:none;color:var(--blue);}
.sidebar-footer{font-size:12.5px;color:var(--muted);}
.theme-toggle{
  background:none;border:1px solid var(--line);color:var(--ink);
  font-family:inherit;font-size:12px;padding:7px 10px;border-radius:4px;cursor:pointer;margin-top:14px;
}
.theme-toggle:hover{border-color:var(--blue);}

/* --- Mobile top bar --- */
.topbar{display:none;position:sticky;top:0;z-index:20;background:var(--paper);border-bottom:1px solid var(--line);padding:14px 18px;align-items:center;justify-content:space-between;padding-top:calc(14px + env(safe-area-inset-top,0px));}
.topbar .name{font-family:inherit;font-weight:600;font-size:19px;}
.burger{background:none;border:1px solid var(--line);color:var(--ink);padding:7px 11px;border-radius:4px;font-family:inherit;font-size:14px;}
.mobile-nav{display:none;flex-direction:column;background:var(--paper);border-bottom:1px solid var(--line);padding:8px 18px 16px;}
.mobile-nav a{padding:9px 0;color:var(--ink);font-size:15px;border-bottom:1px dashed var(--line);}
.mobile-nav.open{display:flex;}

/* --- Main --- */
main{flex:1;min-width:0;}
.pane{border-bottom:1px solid var(--line);}
.pane-head{
  display:flex;align-items:center;gap:8px;padding:10px 40px;
  font-size:13px;color:var(--muted);border-bottom:1px solid var(--line);
  position:sticky;top:0;background:var(--paper);z-index:5;
}
.pane-head .dot{width:7px;height:7px;border-radius:50%;background:var(--line);}
.pane-body{padding:56px 40px;max-width:720px;}

/* Hero */
#home .pane-body{padding-top:72px;padding-bottom:64px;}
.eyebrow-line{color:var(--muted);font-size:14.5px;margin-bottom:18px;}
h1.hero-title{font-size:clamp(32px,5vw,52px);font-weight:600;line-height:1.08;margin:0 0 20px;}
h1.hero-title .accent{color:var(--blue);font-style:italic;}
.hero-desc{font-size:17px;max-width:54ch;color:var(--ink);margin-bottom:28px;}
.hero-links{display:flex;flex-wrap:wrap;gap:10px;}
.btn{
  border:1px solid var(--ink);padding:10px 17px;border-radius:4px;font-size:14.5px;color:var(--ink);
}
.btn.primary{background:var(--blue);border-color:var(--blue);color:var(--paper);}
.btn:hover{text-decoration:none;background:var(--line);}
.btn.primary:hover{opacity:.88;background:var(--blue);}

/* Entries (formation / expérience) */
.entry-list{display:flex;flex-direction:column;gap:16px;}
.entry-card{border:1px solid var(--line);border-radius:6px;padding:20px 22px;}
.entry-card .etitle{font-family:inherit;font-size:20px;font-weight:600;margin:0 0 5px;}
.entry-card .emeta{font-size:13.5px;color:var(--muted);margin-bottom:10px;}
.entry-card p{margin:0;font-size:15.5px;}

/* Skills */
.skills-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:14px;}
.skill-card{border:1px solid var(--line);border-radius:6px;padding:16px;}
.skill-card .lang{font-family:inherit;font-size:19px;font-weight:600;margin-bottom:6px;}
.skill-card .level-label{font-size:13px;color:var(--muted);}

/* Projet */
.project-card{border:1px solid var(--line);border-radius:6px;overflow:hidden;}
.project-top{padding:22px 22px 0;}
.project-top .ptitle{font-family:inherit;font-size:22px;font-weight:600;margin:0 0 6px;}
.project-top .pmeta{font-size:13.5px;color:var(--muted);margin-bottom:14px;}
.project-body{padding:0 22px 22px;}
.stack{display:flex;gap:8px;flex-wrap:wrap;margin:14px 0 0;}
.chip{border:1px solid var(--line);border-radius:20px;padding:5px 12px;font-size:13px;color:var(--muted);}

/* Contact */
.contact-box{border:1px solid var(--line);border-radius:6px;padding:26px;max-width:520px;}
.contact-box a{display:block;margin:6px 0;font-size:16px;}
footer{padding:30px 40px 60px;font-size:13px;color:var(--muted);}

@media (max-width:860px){
  .sidebar{display:none;}
  .topbar{display:flex;}
  .pane-body{padding:36px 20px;}
  .pane-head{padding:10px 20px;}
  footer{padding:24px 20px 48px;}
}
</style>
</head>
<body>

<div class="topbar">
  <div class="name">Christophe Zhou</div>
  <button class="burger" id="burgerBtn" aria-label="Ouvrir le menu">menu</button>
</div>
<div class="mobile-nav" id="mobileNav">
  <a href="#home">accueil</a>
  <a href="#formation">formation</a>
  <a href="#experience">expérience</a>
  <a href="#skills">compétences</a>
  <a href="#projet">projet</a>
  <a href="#contact">contact</a>
</div>

<div class="layout">
  <aside class="sidebar">
    <div>
      <div class="brand">
        <div class="dir">~/portfolio</div>
        <div class="name">Christophe Zhou</div>
      </div>
      <nav class="tree" aria-label="Navigation principale">
        <ul>
          <li><a href="#home">accueil</a></li>
          <li><a href="#formation">formation</a></li>
          <li><a href="#experience">expérience</a></li>
          <li><a href="#skills">compétences</a></li>
          <li><a href="#projet">projet</a></li>
          <li><a href="#contact">contact</a></li>
        </ul>
      </nav>
    </div>
    <div class="sidebar-footer">
      BTS SIO — 2e année<br>
      <button class="theme-toggle" id="themeBtn">mode clair/sombre</button>
    </div>
  </aside>

  <main>
    <section class="pane" id="home">
      <div class="pane-head"><span class="dot"></span> accueil</div>
      <div class="pane-body">
        <div class="eyebrow-line">Étudiant en BTS SIO, 2e année</div>
        <h1 class="hero-title">Christophe Zhou</h1>
        <p class="hero-desc">Je développe des sites et petits outils en Python, Java, HTML et CSS. Actuellement en 2e année de BTS Services Informatiques aux Organisations.</p>
        <div class="hero-links">
          <a class="btn primary" href="#projet">Voir le projet</a>
          <a class="btn" href="#contact">Me contacter</a>
        </div>
      </div>
    </section>

    <section class="pane" id="formation">
      <div class="pane-head"><span class="dot"></span> formation</div>
      <div class="pane-body">
        <h2 class="serif" style="font-size:27px;margin-top:0;">Formation</h2>
        <div class="entry-list">
          <div class="entry-card">
            <div class="etitle">BTS Services Informatiques aux Organisations (SIO)</div>
            <div class="emeta">2e année — en cours</div>
            <p>Formation orientée développement et gestion de projets informatiques, incluant la programmation (Python, Java), le développement web (HTML, CSS) et la gestion de services numériques.</p>
          </div>
        </div>
      </div>
    </section>

    <section class="pane" id="experience">
      <div class="pane-head"><span class="dot"></span> expérience</div>
      <div class="pane-body">
        <h2 class="serif" style="font-size:27px;margin-top:0;">Expérience</h2>
        <div class="entry-list">
          <div class="entry-card">
            <div class="etitle">Stage Erasmus en Irlande</div>
            <div class="emeta">27 avril – 26 juin 2026</div>
            <p>Stage effectué en Irlande dans le cadre du programme Erasmus, permettant de développer mon autonomie, mon adaptabilité et ma pratique de l'anglais en contexte professionnel. J'y ai aussi appris à utiliser des outils tels que Power Apps et Power Automate.</p>
          </div>
          <div class="entry-card">
            <div class="etitle">Expérience en restauration / commerce</div>
            <div class="emeta">Depuis août — expérience professionnelle</div>
            <p>Expérience dans un bar-tabac durant les vacances d'été. Cette expérience en restauration a renforcé mon sens du travail d'équipe, ma gestion du rythme sous pression et mon relationnel avec la clientèle.</p>
          </div>
        </div>
      </div>
    </section>

    <section class="pane" id="skills">
      <div class="pane-head"><span class="dot"></span> compétences</div>
      <div class="pane-body">
        <h2 class="serif" style="font-size:27px;margin-top:0;">Compétences</h2>
        <div class="skills-grid">
          <div class="skill-card">
            <div class="lang">Python</div>
            <div class="level-label">Débutant</div>
          </div>
          <div class="skill-card">
            <div class="lang">Java</div>
            <div class="level-label">Débutant</div>
          </div>
          <div class="skill-card">
            <div class="lang">HTML</div>
            <div class="level-label">Débutant</div>
          </div>
          <div class="skill-card">
            <div class="lang">CSS</div>
            <div class="level-label">Débutant</div>
          </div>
          <div class="skill-card">
            <div class="lang">Anglais</div>
            <div class="level-label">Intermédiaire<br>B1-B2</div>
          </div>
        </div>
      </div>
    </section>

    <section class="pane" id="projet">
      <div class="pane-head"><span class="dot"></span> projet</div>
      <div class="pane-body">
        <h2 class="serif" style="font-size:27px;margin-top:0;">Projet</h2>
        <div class="project-card">
          <div class="project-top">
            <div class="ptitle">Site web en HTML / CSS</div>
            <div class="pmeta">Projet personnel — BTS SIO, 2e année</div>
          </div>
          <div class="project-body">
            <p style="margin:0;">Conception et intégration d'un site web réalisé entièrement en HTML et CSS.</p>
            <div class="stack">
              <span class="chip">HTML</span>
              <span class="chip">CSS</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="pane" id="contact">
      <div class="pane-head"><span class="dot"></span> contact</div>
      <div class="pane-body">
        <h2 class="serif" style="font-size:27px;margin-top:0;">Contact</h2>
        <div class="contact-box">
          <a href="mailto:czhou@lerebours.fr">czhou@lerebours.fr</a>
        </div>
      </div>
    </section>

    <footer>Christophe Zhou — BTS SIO, 2e année</footer>
  </main>
</div>

<script>
(function(){
  var burger=document.getElementById('burgerBtn');
  var nav=document.getElementById('mobileNav');
  burger.addEventListener('click',function(){nav.classList.toggle('open');});
  nav.querySelectorAll('a').forEach(function(a){a.addEventListener('click',function(){nav.classList.remove('open');});});

  var themeBtn=document.getElementById('themeBtn');
  themeBtn.addEventListener('click',function(){
    var root=document.documentElement;
    var current=root.getAttribute('data-theme');
    root.setAttribute('data-theme', current==='dark' ? 'light' : 'dark');
  });

  var sections=document.querySelectorAll('main section');
  function onScroll(){
    var pos=window.scrollY+120;
    var atBottom=(window.innerHeight+window.scrollY)>=(document.body.scrollHeight-2);
    var current=sections[0];
    sections.forEach(function(sec){
      if(sec.offsetTop<=pos){current=sec;}
    });
    if(atBottom){current=sections[sections.length-1];}
    sections.forEach(function(sec){
      var id=sec.getAttribute('id');
      var link=document.querySelector('nav.tree a[href="#'+id+'"]');
      if(!link)return;
      link.classList.toggle('active', sec===current);
    });
  }
  window.addEventListener('scroll',onScroll);
  window.addEventListener('resize',onScroll);
  onScroll();
})();
</script>
</body>
</html>
