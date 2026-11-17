<!DOCTYPE html>
<html lang="ru" data-theme="dark">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>CodePath — Гайды по языкам программирования</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet" />
<style>
:root{--radius:20px;--radius-sm:12px;--transition:0.35s cubic-bezier(0.4,0,0.2,1);}
[data-theme="dark"]{--bg:#0b0d17;--bg-soft:#12152a;--card:rgba(255,255,255,0.04);--border:rgba(255,255,255,0.08);--text:#eef0f8;--text-soft:#a7adc4;--accent:#7c5cff;--accent-2:#22d3ee;--accent-3:#f472b6;--shadow:0 20px 60px rgba(0,0,0,0.5);--glow:rgba(124,92,255,0.35);--header-bg:rgba(11,13,23,0.7);--gold:#fbbf24;}
[data-theme="light"]{--bg:#f6f7fb;--bg-soft:#fff;--card:rgba(255,255,255,0.75);--border:rgba(15,20,50,0.08);--text:#131729;--text-soft:#5a6078;--accent:#6248ff;--accent-2:#0891b2;--accent-3:#db2777;--shadow:0 20px 60px rgba(20,30,80,0.12);--glow:rgba(98,72,255,0.25);--header-bg:rgba(246,247,251,0.75);--gold:#d97706;}
*{margin:0;padding:0;box-sizing:border-box}html{scroll-behavior:smooth}
body{font-family:'Inter',system-ui,sans-serif;background:var(--bg);color:var(--text);line-height:1.6;overflow-x:hidden;transition:background var(--transition),color var(--transition)}
.container{max-width:1180px;margin:0 auto;padding:0 24px}
.gradient-text{background:linear-gradient(135deg,var(--accent),var(--accent-2) 60%,var(--accent-3));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.bg-blobs{position:fixed;inset:0;z-index:-1;overflow:hidden;pointer-events:none}
.blob{position:absolute;border-radius:50%;filter:blur(90px);opacity:.5;animation:float 18s ease-in-out infinite}
.blob-1{width:420px;height:420px;background:var(--accent);top:-100px;left:-100px}
.blob-2{width:380px;height:380px;background:var(--accent-2);top:40%;right:-120px;animation-delay:-6s}
.blob-3{width:340px;height:340px;background:var(--accent-3);bottom:-100px;left:30%;animation-delay:-12s}
[data-theme="light"] .blob{opacity:.25}
@keyframes float{0%,100%{transform:translate(0,0) scale(1)}33%{transform:translate(40px,-30px) scale(1.1)}66%{transform:translate(-30px,30px) scale(.95)}}
.header{position:sticky;top:0;z-index:100;backdrop-filter:blur(18px);-webkit-backdrop-filter:blur(18px);background:var(--header-bg);border-bottom:1px solid var(--border);transition:background var(--transition),border-color var(--transition)}
.header-inner{display:flex;align-items:center;gap:14px;height:72px}
.logo{display:flex;align-items:center;gap:10px;text-decoration:none;color:var(--text);font-weight:800;font-size:20px;letter-spacing:-.5px;flex-shrink:0}
.logo-mark{font-family:'JetBrains Mono',monospace;color:var(--accent);font-size:22px}
.search-wrap{flex:1;max-width:420px;margin:0 auto;position:relative;display:flex;align-items:center;transition:opacity var(--transition),transform var(--transition)}
.search-wrap.hidden{opacity:0;transform:translateY(-8px);pointer-events:none;position:absolute}
.search-icon{position:absolute;left:14px;width:18px;height:18px;color:var(--text-soft);pointer-events:none}
.search-input{width:100%;height:44px;padding:0 42px;border-radius:100px;border:1px solid var(--border);background:var(--card);color:var(--text);font-family:inherit;font-size:14.5px;backdrop-filter:blur(10px);transition:all var(--transition)}
.search-input::placeholder{color:var(--text-soft)}
.search-input:focus{outline:none;border-color:var(--accent);box-shadow:0 0 0 4px var(--glow)}
.search-clear{position:absolute;right:10px;width:26px;height:26px;border-radius:50%;border:none;background:var(--border);color:var(--text-soft);cursor:pointer;font-size:11px;display:none;place-items:center;transition:all var(--transition)}
.search-clear.show{display:grid}
.search-clear:hover{background:var(--accent);color:#fff}
.breadcrumbs{flex:1;display:flex;align-items:center}
.back-btn{display:inline-flex;align-items:center;gap:8px;padding:9px 18px;border-radius:100px;border:1px solid var(--border);background:var(--card);color:var(--text);cursor:pointer;font-family:inherit;font-size:14px;font-weight:500;transition:all var(--transition)}
.back-btn svg{width:16px;height:16px;transition:transform var(--transition)}
.back-btn:hover{border-color:var(--accent);transform:translateX(-3px)}
.back-btn:hover svg{transform:translateX(-3px)}
.saved-btn{position:relative;width:44px;height:44px;flex-shrink:0;border-radius:50%;border:1px solid var(--border);background:var(--card);color:var(--text);cursor:pointer;display:grid;place-items:center;transition:all var(--transition)}
.saved-btn:hover{border-color:var(--gold);color:var(--gold);transform:scale(1.08)}
.saved-btn svg{width:18px;height:18px}
.saved-count{position:absolute;top:-6px;right:-6px;min-width:20px;height:20px;padding:0 5px;border-radius:10px;background:linear-gradient(135deg,var(--accent),var(--accent-2));color:#fff;font-size:11px;font-weight:700;display:none;place-items:center;box-shadow:0 2px 8px var(--glow)}
.saved-count.show{display:grid}
.theme-toggle{width:44px;height:44px;flex-shrink:0;border-radius:50%;border:1px solid var(--border);background:var(--card);color:var(--text);cursor:pointer;display:grid;place-items:center;transition:all var(--transition)}
.theme-toggle:hover{transform:rotate(20deg) scale(1.08);border-color:var(--accent);box-shadow:0 0 24px var(--glow)}
.theme-toggle svg{width:20px;height:20px}
.theme-toggle .icon-moon{display:none}
[data-theme="light"] .theme-toggle .icon-moon{display:block}
[data-theme="light"] .theme-toggle .icon-sun{display:none}
.view{display:none;animation:viewIn .5s cubic-bezier(0.4,0,0.2,1)}
.view.active{display:block}
@keyframes viewIn{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.hero{padding:80px 24px 60px;text-align:center;display:flex;flex-direction:column;align-items:center}
.hero-badge{display:inline-flex;align-items:center;gap:8px;padding:8px 18px;border-radius:100px;background:var(--card);border:1px solid var(--border);font-size:14px;color:var(--text-soft);margin-bottom:24px;backdrop-filter:blur(10px)}
.hero-title{font-size:clamp(34px,6vw,62px);font-weight:800;line-height:1.1;letter-spacing:-2px;margin-bottom:20px}
.hero-sub{max-width:600px;font-size:17px;color:var(--text-soft);margin-bottom:34px}
.my-progress{width:100%;max-width:620px;background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:22px 26px;margin-top:8px;backdrop-filter:blur(12px);text-align:left;display:none}
.my-progress.show{display:block}
.my-progress-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px}
.my-progress-head h3{font-size:16px;font-weight:700}
.my-progress-pct{font-family:'JetBrains Mono',monospace;font-weight:700;font-size:15px;background:linear-gradient(135deg,var(--accent),var(--accent-2));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.progress-track{height:10px;background:var(--border);border-radius:100px;overflow:hidden;margin-bottom:10px}
.progress-fill{height:100%;width:0;background:linear-gradient(90deg,var(--accent),var(--accent-2),var(--accent-3));border-radius:100px;transition:width .6s cubic-bezier(0.4,0,0.2,1)}
.my-progress-sub{font-size:13px;color:var(--text-soft)}
.hero-stats{display:flex;gap:52px;margin-top:44px;flex-wrap:wrap;justify-content:center}
.stat{display:flex;flex-direction:column;align-items:center}
.stat strong{font-size:38px;font-weight:800;background:linear-gradient(135deg,var(--accent),var(--accent-2));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.stat span{font-size:14px;color:var(--text-soft)}
.section{padding:70px 24px}
.section-head{text-align:center;margin-bottom:40px}
.section-head h2{font-size:clamp(28px,4vw,42px);font-weight:800;letter-spacing:-1px;margin-bottom:12px}
.section-head p{color:var(--text-soft);font-size:16px}
.filters{display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-bottom:36px}
.chip{padding:9px 20px;border-radius:100px;border:1px solid var(--border);background:var(--card);color:var(--text-soft);font-family:inherit;font-size:14px;font-weight:500;cursor:pointer;transition:all var(--transition);backdrop-filter:blur(10px)}
.chip:hover{border-color:var(--accent);color:var(--text);transform:translateY(-2px)}
.chip.active{background:linear-gradient(135deg,var(--accent),var(--accent-2));border-color:transparent;color:#fff;box-shadow:0 6px 20px var(--glow)}
.lang-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:22px}
.lang-card{position:relative;background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:26px;cursor:pointer;overflow:hidden;backdrop-filter:blur(12px);transition:transform var(--transition),border-color var(--transition),box-shadow var(--transition),background var(--transition);opacity:0;transform:translateY(30px)}
.lang-card.visible{opacity:1;transform:translateY(0)}
.lang-card.hide{display:none}
.lang-card::before{content:'';position:absolute;inset:0;background:radial-gradient(600px circle at var(--mx,50%) var(--my,50%),color-mix(in srgb,var(--accent) 18%,transparent),transparent 40%);opacity:0;transition:opacity var(--transition);pointer-events:none}
.lang-card:hover::before{opacity:1}
.lang-card:hover{transform:translateY(-8px);border-color:color-mix(in srgb,var(--accent) 50%,var(--border));box-shadow:var(--shadow)}
.card-actions{position:absolute;top:14px;right:14px;display:flex;gap:6px;z-index:2}
.icon-btn{width:32px;height:32px;border-radius:50%;border:1px solid var(--border);background:var(--bg-soft);color:var(--text-soft);cursor:pointer;display:grid;place-items:center;transition:all var(--transition);font-size:14px;padding:0}
.icon-btn:hover{transform:scale(1.15);border-color:var(--accent)}
.icon-btn.active-star{background:var(--gold);border-color:var(--gold);color:#fff}
.icon-btn.active-wish{background:var(--accent-3);border-color:var(--accent-3);color:#fff}
.icon-btn svg{width:16px;height:16px}
.lang-icon{width:54px;height:54px;border-radius:16px;display:grid;place-items:center;font-size:24px;font-weight:800;margin-bottom:16px;color:#fff;transition:transform var(--transition)}
.lang-card:hover .lang-icon{transform:scale(1.1) rotate(-6deg)}
.lang-name{font-size:20px;font-weight:700;margin-bottom:6px}
.lang-tag{font-size:13px;color:var(--text-soft);margin-bottom:16px}
.card-progress{display:none;margin-bottom:12px}
.card-progress.show{display:block}
.card-progress-label{display:flex;justify-content:space-between;font-size:11.5px;color:var(--text-soft);margin-bottom:5px;font-family:'JetBrains Mono',monospace}
.card-progress .progress-track{height:6px;margin-bottom:0}
.lang-meta{display:flex;justify-content:space-between;align-items:center;font-size:13px;color:var(--text-soft);padding-top:14px;border-top:1px solid var(--border)}
.lang-level{padding:4px 12px;border-radius:100px;font-weight:600;font-size:12px}
.level-easy{background:rgba(34,197,94,0.15);color:#22c55e}
.level-medium{background:rgba(234,179,8,0.15);color:#eab308}
.level-hard{background:rgba(239,68,68,0.15);color:#ef4444}
.empty-state{text-align:center;padding:60px 20px;animation:viewIn .4s ease}
.empty-state.small{padding:30px 20px}
.empty-icon{font-size:52px;margin-bottom:16px}
.empty-state.small .empty-icon{font-size:34px;margin-bottom:10px}
.empty-state h3{font-size:22px;margin-bottom:8px}
.empty-state p{color:var(--text-soft);margin-bottom:24px}
.empty-state.small p{margin-bottom:0;font-size:14px}
.lang-page{padding:48px 24px 60px}
.lang-hero{display:flex;align-items:center;gap:24px;margin-bottom:32px;flex-wrap:wrap;padding-bottom:32px;border-bottom:1px solid var(--border);animation:viewIn .5s ease}
.lang-hero-icon{width:84px;height:84px;border-radius:24px;display:grid;place-items:center;font-size:34px;font-weight:800;color:#fff;flex-shrink:0;box-shadow:0 12px 40px rgba(0,0,0,0.3)}
.lang-hero-info{flex:1}
.lang-hero-info h1{font-size:clamp(28px,4vw,40px);font-weight:800;letter-spacing:-1px;margin-bottom:6px}
.lang-hero-info .lang-tag{font-size:15px;margin-bottom:12px}
.lang-hero-meta{display:flex;gap:10px;flex-wrap:wrap}
.meta-pill{padding:6px 14px;border-radius:100px;background:var(--card);border:1px solid var(--border);font-size:13px;color:var(--text-soft);display:inline-flex;align-items:center;gap:6px}
.lang-hero-actions{display:flex;gap:10px;flex-wrap:wrap;margin-top:16px}
.action-btn{display:inline-flex;align-items:center;gap:8px;padding:10px 18px;border-radius:100px;border:1px solid var(--border);background:var(--card);color:var(--text);font-family:inherit;font-size:14px;font-weight:500;cursor:pointer;transition:all var(--transition)}
.action-btn:hover{border-color:var(--accent);transform:translateY(-2px)}
.action-btn svg{width:16px;height:16px}
.action-btn.active-star{background:var(--gold);border-color:var(--gold);color:#fff}
.action-btn.active-wish{background:var(--accent-3);border-color:var(--accent-3);color:#fff}
.lang-progress-box{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:22px 26px;margin-bottom:32px;backdrop-filter:blur(12px);animation:viewIn .55s ease}
.lang-progress-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px}
.lang-progress-head h3{font-size:16px;font-weight:700}
.lang-progress-pct{font-family:'JetBrains Mono',monospace;font-weight:700;font-size:18px;background:linear-gradient(135deg,var(--accent),var(--accent-2));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.lang-progress-sub{font-size:13px;color:var(--text-soft);margin-top:10px}
.lang-intro{font-size:16.5px;color:var(--text-soft);margin-bottom:32px;max-width:760px;animation:viewIn .6s ease}
.stages-tabs{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:28px;padding-bottom:4px}
.stage-tab{padding:9px 18px;border-radius:100px;border:1px solid var(--border);background:var(--card);color:var(--text-soft);font-family:inherit;font-size:13.5px;font-weight:500;cursor:pointer;transition:all var(--transition);white-space:nowrap}
.stage-tab:hover{color:var(--text);border-color:var(--accent)}
.stage-tab.active{background:linear-gradient(135deg,var(--accent),var(--accent-2));border-color:transparent;color:#fff}
.stages-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(290px,1fr));gap:20px}
.stage-card{background:var(--card);border:1px solid var(--border);border-radius:var(--radius-sm);padding:22px;backdrop-filter:blur(12px);transition:all var(--transition);animation:viewIn .4s ease backwards;position:relative;overflow:hidden}
.stage-card:hover{transform:translateY(-5px);border-color:var(--accent);box-shadow:var(--shadow)}
.stage-card.done{border-color:rgba(34,197,94,0.4);background:color-mix(in srgb,rgba(34,197,94,0.06) 100%,var(--card))}
.stage-card.done .stage-num{background:linear-gradient(135deg,#22c55e,#16a34a)}
.stage-head{display:flex;align-items:flex-start;gap:12px;margin-bottom:14px}
.stage-num{width:36px;height:36px;border-radius:50%;background:linear-gradient(135deg,var(--accent),var(--accent-2));color:#fff;display:grid;place-items:center;font-size:14px;font-weight:700;flex-shrink:0}
.stage-title-wrap{flex:1}
.stage-card h3{font-size:16.5px;font-weight:700;line-height:1.3}
.stage-check{width:28px;height:28px;border-radius:50%;border:2px solid var(--border);background:transparent;cursor:pointer;display:grid;place-items:center;flex-shrink:0;transition:all var(--transition);padding:0;color:transparent}
.stage-check:hover{border-color:var(--accent);transform:scale(1.1)}
.stage-check.checked{background:linear-gradient(135deg,#22c55e,#16a34a);border-color:#22c55e;color:#fff}
.stage-check svg{width:14px;height:14px;stroke-width:3}
.stage-card p{font-size:14px;color:var(--text-soft);margin-bottom:14px;line-height:1.55}
.stage-card.done p{text-decoration:line-through;opacity:.6}
.tags{display:flex;flex-wrap:wrap;gap:7px}
.tag{font-size:11.5px;padding:4px 11px;border-radius:100px;background:color-mix(in srgb,var(--accent) 10%,transparent);border:1px solid var(--border);color:var(--text-soft);font-family:'JetBrains Mono',monospace;transition:all var(--transition)}
.tag:hover{border-color:var(--accent);color:var(--text)}
.stage-link{display:inline-flex;align-items:center;gap:6px;margin-top:14px;padding:7px 14px;border-radius:100px;background:color-mix(in srgb,var(--accent) 12%,transparent);border:1px solid color-mix(in srgb,var(--accent) 30%,var(--border));color:var(--accent);font-size:12.5px;font-weight:600;text-decoration:none;transition:all var(--transition)}
.stage-link:hover{background:var(--accent);color:#fff;border-color:var(--accent);transform:translateY(-2px)}
.stage-link svg{width:12px;height:12px}
.more-langs{margin-top:50px;padding-top:32px;border-top:1px solid var(--border)}
.more-langs h3{font-size:18px;margin-bottom:20px}
.more-langs-row{display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:14px}
.mini-lang{display:flex;align-items:center;gap:12px;padding:14px 16px;background:var(--card);border:1px solid var(--border);border-radius:var(--radius-sm);cursor:pointer;transition:all var(--transition);backdrop-filter:blur(10px);font-family:inherit;color:var(--text);text-align:left}
.mini-lang:hover{border-color:var(--accent);transform:translateY(-3px)}
.mini-lang-icon{width:36px;height:36px;border-radius:10px;display:grid;place-items:center;font-size:14px;font-weight:800;color:#fff;flex-shrink:0}
.mini-lang-name{font-size:14px;font-weight:600}
.saved-subtitle{font-size:20px;font-weight:700;margin-bottom:20px;letter-spacing:-.5px}
.steps{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:22px}
.step{background:var(--card);border:1px solid var(--border);border-radius:var(--radius);padding:28px;backdrop-filter:blur(12px);transition:all var(--transition)}
.step:hover{transform:translateY(-6px);border-color:var(--accent);box-shadow:var(--shadow)}
.step-num{font-size:40px;font-weight:800;font-family:'JetBrains Mono',monospace;background:linear-gradient(135deg,var(--accent),var(--accent-2));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;margin-bottom:12px}
.step h3{font-size:18px;margin-bottom:10px}
.step p{color:var(--text-soft);font-size:14px}
.footer{text-align:center;padding:36px 24px;color:var(--text-soft);font-size:14px;border-top:1px solid var(--border)}
.reveal{opacity:0;transform:translateY(30px);transition:opacity .7s ease,transform .7s cubic-bezier(0.4,0,0.2,1)}
.reveal.visible{opacity:1;transform:translateY(0)}
@media (max-width:820px){.search-wrap{max-width:none}.logo-text{display:none}.saved-btn{width:40px;height:40px}}
@media (max-width:620px){.hero{padding:50px 24px 30px}.hero-stats{gap:26px;margin-top:34px}.stat strong{font-size:28px}.section{padding:50px 20px}.lang-hero{flex-direction:column;align-items:flex-start}.lang-hero-icon{width:68px;height:68px;font-size:28px}.header-inner{height:64px;gap:8px}.search-input{font-size:14px;padding-left:38px}.search-icon{left:12px;width:16px}.lang-page{padding:32px 20px 40px}.icon-btn{width:28px;height:28px}.card-actions{top:10px;right:10px;gap:4px}}
@media (prefers-reduced-motion:reduce){*,*::before,*::after{animation-duration:.01ms !important;transition-duration:.01ms !important}}
</style>
</head>
<body>

<div class="bg-blobs" aria-hidden="true">
  <div class="blob blob-1"></div>
  <div class="blob blob-2"></div>
  <div class="blob blob-3"></div>
</div>

<header class="header">
  <div class="container header-inner">
    <a href="#" class="logo" data-route="home">
      <span class="logo-mark">{ }</span>
      <span class="logo-text">CodePath</span>
    </a>
    <div class="search-wrap" id="searchWrap">
      <svg class="search-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="7"/><path d="m21 21-4.3-4.3"/></svg>
      <input type="text" id="searchInput" class="search-input" placeholder="Поиск языка… (Python, Go, SQL)" autocomplete="off" />
      <button class="search-clear" id="searchClear" aria-label="Очистить">✕</button>
    </div>
    <nav class="breadcrumbs" id="breadcrumbs" hidden>
      <button class="back-btn" data-route="home">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M19 12H5M12 19l-7-7 7-7"/></svg>
        <span>Все языки</span>
      </button>
    </nav>
    <button class="saved-btn" id="savedBtn" aria-label="Избранное">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M19 21l-7-5-7 5V5a2 2 0 0 1 2-2h10a2 2 0 0 1 2 2z"/></svg>
      <span class="saved-count" id="savedCount">0</span>
    </button>
    <button class="theme-toggle" id="themeToggle" aria-label="Переключить тему">
      <svg class="icon-sun" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M6.34 17.66l-1.41 1.41M19.07 4.93l-1.41 1.41"/></svg>
      <svg class="icon-moon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/></svg>
    </button>
  </div>
</header>

<main id="viewHome" class="view active">
  <section class="hero container">
    <div class="hero-badge reveal">🚀 Путь в IT начинается здесь</div>
    <h1 class="hero-title reveal">Научись программировать <br /><span class="gradient-text">с полного нуля</span></h1>
    <p class="hero-sub reveal">Пошаговые дорожные карты. Каждый этап — со ссылкой на бесплатный текстовый туториал или справочник. Читай и практикуйся в своём темпе.</p>
    <div class="my-progress reveal" id="myProgress"></div>
    <div class="hero-stats reveal">
      <div class="stat"><strong data-count="12">0</strong><span>языков</span></div>
      <div class="stat"><strong data-count="180">0</strong><span>уроков</span></div>
      <div class="stat"><strong data-count="45">0</strong><span>проектов</span></div>
    </div>
  </section>

  <section id="languages" class="section container">
    <div class="section-head">
      <h2 class="reveal">Выбери свой <span class="gradient-text">язык</span></h2>
      <p class="reveal">Нажми на карточку — откроется полная дорожная карта обучения.</p>
    </div>
    <div class="filters" id="filters">
      <button class="chip active" data-filter="all">Все</button>
      <button class="chip" data-filter="easy">Легко</button>
      <button class="chip" data-filter="medium">Средне</button>
      <button class="chip" data-filter="hard">Сложно</button>
      <button class="chip" data-filter="saved">★ Избранное</button>
      <button class="chip" data-filter="wishlist">💭 Хочу изучить</button>
    </div>
    <div class="lang-grid" id="langGrid"></div>
    <div class="empty-state" id="emptyState" hidden>
      <div class="empty-icon">🔍</div>
      <h3>Ничего не найдено</h3>
      <p>Попробуй другой запрос или сбрось фильтры.</p>
      <button class="btn btn-primary" id="resetBtn" style="padding:14px 28px;border-radius:100px;background:linear-gradient(135deg,var(--accent),var(--accent-2));color:#fff;border:none;font-weight:600;cursor:pointer;font-family:inherit;font-size:16px;">Сбросить</button>
    </div>
  </section>

  <section class="section container">
    <div class="section-head">
      <h2 class="reveal">Как учиться <span class="gradient-text">правильно</span></h2>
      <p class="reveal">Методика, которая работает для любого языка.</p>
    </div>
    <div class="steps">
      <div class="step reveal"><div class="step-num">01</div><h3>Основы синтаксиса</h3><p>Переменные, типы данных, условия и циклы. Пиши простые программы каждый день.</p></div>
      <div class="step reveal"><div class="step-num">02</div><h3>Структуры данных</h3><p>Массивы, списки, словари. Учись решать задачи на LeetCode / Codewars.</p></div>
      <div class="step reveal"><div class="step-num">03</div><h3>Функции и ООП</h3><p>Разбивай код на функции, изучай модули, классы и архитектуру.</p></div>
      <div class="step reveal"><div class="step-num">04</div><h3>Первый проект</h3><p>Сделай что-то реальное: бот, парсер, сайт, игру. Это закрепляет знания.</p></div>
    </div>
  </section>
  <footer class="footer container"><p>© 2025 CodePath — учись кодить с удовольствием 💜</p></footer>
</main>

<main id="viewLang" class="view">
  <section class="lang-page container" id="langPage"></section>
  <footer class="footer container"><p>© 2025 CodePath — учись кодить с удовольствием 💜</p></footer>
</main>

<main id="viewSaved" class="view">
  <section class="section container">
    <div class="section-head" style="text-align:left;margin-bottom:32px;">
      <button class="back-btn" data-route="home" style="margin-bottom:20px;">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M19 12H5M12 19l-7-7 7-7"/></svg>
        <span>Все языки</span>
      </button>
      <h2>⭐ Избранное и <span class="gradient-text">планы</span></h2>
      <p>Языки, которые ты сохранил, и те, что хочешь изучить.</p>
    </div>
    <div class="saved-section">
      <h3 class="saved-subtitle">⭐ Избранное</h3>
      <div class="lang-grid" id="savedGrid"></div>
      <div class="empty-state small" id="savedEmpty" hidden><div class="empty-icon">⭐</div><p>Пока пусто. Нажми на звёздочку на карточке языка.</p></div>
    </div>
    <div class="saved-section" style="margin-top:48px;">
      <h3 class="saved-subtitle">💭 Хочу изучить</h3>
      <div class="lang-grid" id="wishlistGrid"></div>
      <div class="empty-state small" id="wishlistEmpty" hidden><div class="empty-icon">💭</div><p>Список пуст. Добавь языки, которые хочешь освоить.</p></div>
    </div>
    <div class="saved-section" style="margin-top:48px;">
      <h3 class="saved-subtitle">📊 В процессе изучения</h3>
      <div class="lang-grid" id="progressGrid"></div>
      <div class="empty-state small" id="progressEmpty" hidden><div class="empty-icon">📊</div><p>Пока нет прогресса. Отметь первый этап на странице языка.</p></div>
    </div>
  </section>
</main>

<script>
const LANGUAGES=[
{id:'python',name:'Python',tag:'Универсальный · для новичков',icon:'Py',color:'linear-gradient(135deg,#3776ab,#ffd43b)',level:'easy',levelText:'Легко',time:'3–4 мес',desc:'Самый дружелюбный язык для старта. Используется в вебе, анализе данных, ML и автоматизации. Отличный первый язык — синтаксис читается почти как английский.',steps:[
{title:'Установка и среда',desc:'Python + VS Code. Первый скрипт "Hello, World!".',tags:['setup','print'],url:'https://docs.python.org/3/tutorial/'},
{title:'Переменные и типы',desc:'int, float, str, bool. Ввод/вывод через input().',tags:['types','input'],url:'https://docs.python.org/3/tutorial/introduction.html'},
{title:'Условия и циклы',desc:'if/elif/else, for, while, range().',tags:['if','for','while'],url:'https://docs.python.org/3/tutorial/controlflow.html'},
{title:'Структуры данных',desc:'Списки, кортежи, словари, множества.',tags:['list','dict','set'],url:'https://docs.python.org/3/tutorial/datastructures.html'},
{title:'Функции',desc:'def, аргументы, return, области видимости.',tags:['def','scope'],url:'https://docs.python.org/3/tutorial/controlflow.html#defining-functions'},
{title:'ООП',desc:'Классы, объекты, наследование, магические методы.',tags:['class','OOP'],url:'https://docs.python.org/3/tutorial/classes.html'},
{title:'Модули и библиотеки',desc:'import, pip, работа с файлами, json, requests.',tags:['pip','requests'],url:'https://docs.python.org/3/tutorial/modules.html'},
{title:'Первый проект',desc:'Telegram-бот или парсер сайта на BeautifulSoup.',tags:['bot','parsing'],url:'https://realpython.com/'}]},
{id:'javascript',name:'JavaScript',tag:'Язык веба',icon:'JS',color:'linear-gradient(135deg,#f7df1e,#f0a500)',level:'easy',levelText:'Легко',time:'3–4 мес',desc:'Единственный язык, который работает в браузере. Основа любого современного сайта.',steps:[
{title:'Основы и DOM',desc:'Переменные, функции, работа с HTML через querySelector.',tags:['let','const','DOM'],url:'https://learn.javascript.ru/'},
{title:'События',desc:'addEventListener, клики, формы, ввод.',tags:['events','click'],url:'https://learn.javascript.ru/'},
{title:'Массивы и объекты',desc:'map, filter, reduce, деструктуризация.',tags:['array','object'],url:'https://learn.javascript.ru/'},
{title:'Асинхронность',desc:'Callback → Promise → async/await, fetch API.',tags:['promise','fetch'],url:'https://learn.javascript.ru/'},
{title:'ES6+ и модули',desc:'Стрелочные функции, import/export, spread.',tags:['ES6','modules'],url:'https://learn.javascript.ru/'},
{title:'Работа с API',desc:'Запросы к серверу, обработка JSON.',tags:['API','JSON'],url:'https://learn.javascript.ru/'},
{title:'Фреймворк',desc:'React или Vue — компоненты и состояние.',tags:['React','Vue'],url:'https://react.dev/learn'},
{title:'Проект',desc:'TODO-приложение или погодный виджет с API.',tags:['project'],url:'https://learn.javascript.ru/'}]},
{id:'java',name:'Java',tag:'Корпоративный стандарт',icon:'Jv',color:'linear-gradient(135deg,#f89820,#5382a1)',level:'medium',levelText:'Средне',time:'5–6 мес',desc:'Мощный ООП-язык для Android, бэкенда и крупных enterprise-систем.',steps:[
{title:'JDK и IDE',desc:'Установка JDK, IntelliJ IDEA, первая программа.',tags:['JDK','IntelliJ'],url:'https://dev.java/learn/'},
{title:'Синтаксис',desc:'Типы, операторы, условия, циклы.',tags:['syntax'],url:'https://dev.java/learn/'},
{title:'ООП',desc:'Классы, интерфейсы, наследование, полиморфизм.',tags:['class','interface'],url:'https://dev.java/learn/'},
{title:'Коллекции',desc:'List, Map, Set, итераторы.',tags:['List','Map'],url:'https://dev.java/learn/'},
{title:'Исключения',desc:'try/catch, свои исключения.',tags:['try','throw'],url:'https://dev.java/learn/'},
{title:'Generics и Streams',desc:'Обобщения и функциональная обработка коллекций.',tags:['generics','stream'],url:'https://dev.java/learn/'},
{title:'Maven/Gradle',desc:'Сборка проекта и зависимости.',tags:['maven','gradle'],url:'https://dev.java/learn/'},
{title:'Spring Boot',desc:'Первый REST API на Spring.',tags:['Spring','REST'],url:'https://spring.io/guides'}]},
{id:'cpp',name:'C++',tag:'Производительность',icon:'C++',color:'linear-gradient(135deg,#00599c,#004482)',level:'hard',levelText:'Сложно',time:'6–8 мес',desc:'Язык игр, системного ПО и высоконагруженных приложений.',steps:[
{title:'Компилятор',desc:'g++/clang, CMake, первая программа.',tags:['g++','cmake'],url:'https://www.learncpp.com/'},
{title:'Синтаксис и типы',desc:'Переменные, указатели, ссылки.',tags:['pointers'],url:'https://www.learncpp.com/'},
{title:'Управление памятью',desc:'new/delete, стек и куча, RAII.',tags:['memory','RAII'],url:'https://www.learncpp.com/'},
{title:'STL',desc:'vector, map, string, алгоритмы.',tags:['STL','vector'],url:'https://www.learncpp.com/'},
{title:'ООП',desc:'Классы, наследование, виртуальные функции.',tags:['class','virtual'],url:'https://www.learncpp.com/'},
{title:'Шаблоны',desc:'template-функции и классы.',tags:['template'],url:'https://www.learncpp.com/'},
{title:'Умные указатели',desc:'unique_ptr, shared_ptr, move-семантика.',tags:['smart_ptr','move'],url:'https://www.learncpp.com/'},
{title:'Проект',desc:'Консольная игра или мини-движок.',tags:['game','project'],url:'https://www.learncpp.com/'}]},
{id:'csharp',name:'C#',tag:'Игры и .NET',icon:'C#',color:'linear-gradient(135deg,#9b4f96,#68217a)',level:'medium',levelText:'Средне',time:'4–5 мес',desc:'Язык Unity и экосистемы .NET. Отличный выбор для игр и Windows-приложений.',steps:[
{title:'Установка',desc:'.NET SDK + Visual Studio.',tags:['.NET','VS'],url:'https://learn.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/'},
{title:'Основы',desc:'Типы, условия, циклы, массивы.',tags:['syntax'],url:'https://learn.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/'},
{title:'ООП',desc:'Классы, свойства, интерфейсы.',tags:['class','property'],url:'https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/'},
{title:'LINQ',desc:'Запросы к коллекциям в одну строку.',tags:['LINQ'],url:'https://learn.microsoft.com/en-us/dotnet/csharp/linq/'},
{title:'Async/await',desc:'Асинхронные операции.',tags:['async'],url:'https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/'},
{title:'Unity',desc:'Сцены, компоненты, физика.',tags:['Unity'],url:'https://learn.unity.com/'},
{title:'Первый проект',desc:'2D-платформер на Unity.',tags:['game'],url:'https://learn.unity.com/'}]},
{id:'go',name:'Go',tag:'Для бэкенда',icon:'Go',color:'linear-gradient(135deg,#00add8,#007d9c)',level:'medium',levelText:'Средне',time:'3–4 мес',desc:'Простой и быстрый язык от Google. Идеален для микросервисов.',steps:[
{title:'Установка Go',desc:'GOPATH, go mod, первая программа.',tags:['setup','go mod'],url:'https://go.dev/tour/'},
{title:'Синтаксис',desc:'Переменные, условия, циклы, массивы.',tags:['syntax'],url:'https://go.dev/tour/'},
{title:'Функции и структуры',desc:'Множественный возврат, struct, методы.',tags:['struct'],url:'https://gobyexample.com/'},
{title:'Интерфейсы',desc:'Неявная реализация, пустой интерфейс.',tags:['interface'],url:'https://gobyexample.com/'},
{title:'Горутины',desc:'Каналы, select, sync.',tags:['goroutine','channel'],url:'https://gobyexample.com/'},
{title:'HTTP-сервер',desc:'net/http, роутинг, JSON-API.',tags:['http','API'],url:'https://gobyexample.com/'},
{title:'Проект',desc:'REST API для TODO-списка.',tags:['project'],url:'https://go.dev/doc/tutorial/'}]},
{id:'rust',name:'Rust',tag:'Безопасность и скорость',icon:'Rs',color:'linear-gradient(135deg,#dea584,#ce422b)',level:'hard',levelText:'Сложно',time:'6–8 мес',desc:'Современный системный язык без сборщика мусора.',steps:[
{title:'Cargo и rustc',desc:'Установка, создание проекта, сборка.',tags:['cargo'],url:'https://doc.rust-lang.org/book/'},
{title:'Владение',desc:'Ownership, borrowing, lifetimes — сердце Rust.',tags:['ownership'],url:'https://doc.rust-lang.org/book/'},
{title:'Структуры и enum',desc:'Struct, enum, pattern matching.',tags:['struct','match'],url:'https://doc.rust-lang.org/book/'},
{title:'Обработка ошибок',desc:'Result, Option, оператор ?.',tags:['Result','Option'],url:'https://doc.rust-lang.org/book/'},
{title:'Трейты',desc:'Аналог интерфейсов, дженерики.',tags:['trait'],url:'https://doc.rust-lang.org/book/'},
{title:'Concurrency',desc:'Потоки, каналы, Mutex.',tags:['thread','Mutex'],url:'https://doc.rust-lang.org/book/'},
{title:'Проект',desc:'CLI-утилита или веб-сервер на Actix.',tags:['CLI','Actix'],url:'https://doc.rust-lang.org/book/'}]},
{id:'php',name:'PHP',tag:'Веб-бэкенд',icon:'PHP',color:'linear-gradient(135deg,#8892bf,#4f5b93)',level:'easy',levelText:'Легко',time:'3–4 мес',desc:'Рабочая лошадка веба. На нём работает WordPress и миллионы сайтов.',steps:[
{title:'Установка',desc:'XAMPP / Laragon, первый PHP-файл.',tags:['XAMPP'],url:'https://www.php.net/manual/en/tutorial.php'},
{title:'Синтаксис',desc:'Переменные, echo, условия, циклы.',tags:['syntax'],url:'https://www.php.net/manual/en/language.basic-syntax.php'},
{title:'Формы и GET/POST',desc:'Обработка данных от пользователя.',tags:['form','POST'],url:'https://www.php.net/manual/en/tutorial.forms.php'},
{title:'Массивы',desc:'Индексированные, ассоциативные, функции.',tags:['array'],url:'https://www.php.net/manual/en/language.types.array.php'},
{title:'Работа с БД',desc:'MySQL, PDO, подготовленные запросы.',tags:['MySQL','PDO'],url:'https://www.php.net/manual/en/book.pdo.php'},
{title:'ООП',desc:'Классы, наследование, трейты.',tags:['class'],url:'https://www.php.net/manual/en/language.oop5.php'},
{title:'Laravel',desc:'Первый проект на популярном фреймворке.',tags:['Laravel'],url:'https://laravel.com/docs'}]},
{id:'typescript',name:'TypeScript',tag:'JS с типами',icon:'TS',color:'linear-gradient(135deg,#3178c6,#235a97)',level:'medium',levelText:'Средне',time:'4–5 мес',desc:'Надстройка над JavaScript с типами. Стандарт в крупных проектах.',steps:[
{title:'Основы JS',desc:'Сначала уверенный JavaScript.',tags:['JS'],url:'https://learn.javascript.ru/'},
{title:'Типы',desc:'string, number, boolean, any, unknown.',tags:['types'],url:'https://www.typescriptlang.org/docs/handbook/2/everyday-types.html'},
{title:'Интерфейсы',desc:'interface, type, объединения.',tags:['interface','union'],url:'https://www.typescriptlang.org/docs/handbook/2/objects.html'},
{title:'Дженерики',desc:'Обобщённый код без потери типов.',tags:['generics'],url:'https://www.typescriptlang.org/docs/handbook/2/generics.html'},
{title:'Утилитарные типы',desc:'Partial, Pick, Omit, Record.',tags:['utility'],url:'https://www.typescriptlang.org/docs/handbook/utility-types.html'},
{title:'React + TS',desc:'Типизация компонентов и пропсов.',tags:['React'],url:'https://react.dev/learn/typescript'},
{title:'Проект',desc:'Типизированное SPA.',tags:['project'],url:'https://www.typescriptlang.org/docs/'}]},
{id:'sql',name:'SQL',tag:'Базы данных',icon:'SQL',color:'linear-gradient(135deg,#00758f,#f29111)',level:'easy',levelText:'Легко',time:'1–2 мес',desc:'Язык запросов к базам данных. Обязателен для любого бэкенд-разработчика.',steps:[
{title:'Установка',desc:'PostgreSQL или MySQL, клиент DBeaver.',tags:['PostgreSQL'],url:'https://www.postgresqltutorial.com/'},
{title:'SELECT',desc:'Выборка данных, WHERE, ORDER BY.',tags:['SELECT'],url:'https://www.postgresqltutorial.com/'},
{title:'Фильтры',desc:'AND, OR, IN, LIKE, BETWEEN.',tags:['WHERE'],url:'https://www.postgresqltutorial.com/'},
{title:'JOIN',desc:'INNER, LEFT, RIGHT — связь таблиц.',tags:['JOIN'],url:'https://www.postgresqltutorial.com/'},
{title:'Агрегации',desc:'COUNT, SUM, GROUP BY, HAVING.',tags:['GROUP BY'],url:'https://www.postgresqltutorial.com/'},
{title:'Изменение данных',desc:'INSERT, UPDATE, DELETE.',tags:['INSERT'],url:'https://www.postgresqltutorial.com/'},
{title:'Проектирование',desc:'Нормализация, индексы, внешние ключи.',tags:['index','FK'],url:'https://www.postgresqltutorial.com/'}]},
{id:'kotlin',name:'Kotlin',tag:'Android',icon:'Kt',color:'linear-gradient(135deg,#7f52ff,#c711e1)',level:'medium',levelText:'Средне',time:'4–5 мес',desc:'Современный язык для Android-разработки. Лаконичнее Java.',steps:[
{title:'Установка',desc:'Android Studio, эмулятор.',tags:['Android Studio'],url:'https://kotlinlang.org/docs/home.html'},
{title:'Синтаксис',desc:'val/var, типы, строки, функции.',tags:['val','var'],url:'https://kotlinlang.org/docs/home.html'},
{title:'Условия и циклы',desc:'if, when, for, while.',tags:['when'],url:'https://kotlinlang.org/docs/home.html'},
{title:'Классы',desc:'data class, наследование, companion object.',tags:['data class'],url:'https://kotlinlang.org/docs/home.html'},
{title:'Коллекции',desc:'map, filter, лямбды.',tags:['lambda'],url:'https://kotlinlang.org/docs/home.html'},
{title:'Coroutines',desc:'Асинхронность без боли.',tags:['coroutines'],url:'https://kotlinlang.org/docs/coroutines-overview.html'},
{title:'Первый экран',desc:'UI на Jetpack Compose.',tags:['Compose'],url:'https://developer.android.com/jetpack/compose'}]},
{id:'swift',name:'Swift',tag:'iOS / macOS',icon:'Sw',color:'linear-gradient(135deg,#fa7343,#f05138)',level:'medium',levelText:'Средне',time:'4–5 мес',desc:'Язык Apple для iOS, macOS, watchOS.',steps:[
{title:'Xcode',desc:'Установка, первый проект.',tags:['Xcode'],url:'https://www.swift.org/documentation/'},
{title:'Основы',desc:'let/var, типы, строки, опционалы.',tags:['let','var'],url:'https://docs.swift.org/swift-book/documentation/the-swift-programming-language/'},
{title:'Управление потоком',desc:'if, switch, циклы.',tags:['switch'],url:'https://docs.swift.org/swift-book/documentation/the-swift-programming-language/'},
{title:'Функции и замыкания',desc:'Closures, аргументы по умолчанию.',tags:['closure'],url:'https://docs.swift.org/swift-book/documentation/the-swift-programming-language/'},
{title:'Структуры и классы',desc:'struct vs class, протоколы.',tags:['struct','protocol'],url:'https://docs.swift.org/swift-book/documentation/the-swift-programming-language/'},
{title:'SwiftUI',desc:'Декларативный UI для Apple.',tags:['SwiftUI'],url:'https://developer.apple.com/tutorials/swiftui'},
{title:'Проект',desc:'Простое iOS-приложение.',tags:['iOS'],url:'https://developer.apple.com/tutorials/swiftui'}]}
];

const $=(s,c=document)=>c.querySelector(s);
const $$=(s,c=document)=>[...c.querySelectorAll(s)];
const STORE_KEY='codepath';
function loadStore(){try{const r=localStorage.getItem(STORE_KEY);if(r)return JSON.parse(r)}catch(e){}return{progress:{},saved:[],wishlist:[]}}
function saveStore(){try{localStorage.setItem(STORE_KEY,JSON.stringify(store))}catch(e){}}
const store=loadStore();
if(!store.progress)store.progress={};
if(!Array.isArray(store.saved))store.saved=[];
if(!Array.isArray(store.wishlist))store.wishlist=[];
function isSaved(id){return store.saved.includes(id)}
function isWished(id){return store.wishlist.includes(id)}
function getDoneSteps(id){return Array.isArray(store.progress[id])?store.progress[id]:[]}
function isStepDone(id,i){return getDoneSteps(id).includes(i)}
function toggleSaved(id){const x=store.saved.indexOf(id);if(x>=0)store.saved.splice(x,1);else store.saved.push(id);saveStore()}
function toggleWished(id){const x=store.wishlist.indexOf(id);if(x>=0)store.wishlist.splice(x,1);else store.wishlist.push(id);saveStore()}
function toggleStep(id,i){if(!store.progress[id])store.progress[id]=[];const a=store.progress[id];const x=a.indexOf(i);if(x>=0)a.splice(x,1);else a.push(i);saveStore()}
function progressPct(lang){return Math.round((getDoneSteps(lang.id).length/lang.steps.length)*100)}

const root=document.documentElement;
root.setAttribute('data-theme',localStorage.getItem('theme')||'dark');
$('#themeToggle').addEventListener('click',()=>{const n=root.getAttribute('data-theme')==='dark'?'light':'dark';root.setAttribute('data-theme',n);localStorage.setItem('theme',n)});

const state={query:'',filter:'all',currentLangId:null};
const grid=$('#langGrid');const emptyState=$('#emptyState');
const viewHome=$('#viewHome');const viewLang=$('#viewLang');const viewSaved=$('#viewSaved');
const searchWrap=$('#searchWrap');const breadcrumbs=$('#breadcrumbs');
const searchInput=$('#searchInput');const searchClear=$('#searchClear');

function cardTemplate(lang,i){
  const done=getDoneSteps(lang.id).length,total=lang.steps.length,pct=progressPct(lang);
  const star=isSaved(lang.id),wish=isWished(lang.id),showProgress=done>0;
  return `<article class="lang-card" data-id="${lang.id}" style="transition-delay:${i*50}ms">
    <div class="card-actions">
      <button class="icon-btn ${star?'active-star':''}" data-action="star" data-id="${lang.id}" title="${star?'Убрать из избранного':'В избранное'}">
        <svg viewBox="0 0 24 24" fill="${star?'currentColor':'none'}" stroke="currentColor" stroke-width="2"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14l-5-4.87 6.91-1.01z"/></svg>
      </button>
      <button class="icon-btn ${wish?'active-wish':''}" data-action="wish" data-id="${lang.id}" title="${wish?'Убрать из планов':'Хочу изучить'}">
        <svg viewBox="0 0 24 24" fill="${wish?'currentColor':'none'}" stroke="currentColor" stroke-width="2"><path d="M12 21s-7-4.35-9.33-8.5C.86 8.9 2.66 5 6.5 5c2.04 0 3.54 1.15 4.5 2.5C11.96 6.15 13.46 5 15.5 5c3.84 0 5.64 3.9 3.83 7.5C19 16.65 12 21 12 21z"/></svg>
      </button>
    </div>
    <div class="lang-icon" style="background:${lang.color}">${lang.icon}</div>
    <h3 class="lang-name">${lang.name}</h3>
    <p class="lang-tag">${lang.tag}</p>
    <div class="card-progress ${showProgress?'show':''}">
      <div class="card-progress-label"><span>Прогресс</span><span>${done}/${total} · ${pct}%</span></div>
      <div class="progress-track"><div class="progress-fill" style="width:${pct}%"></div></div>
    </div>
    <div class="lang-meta"><span>⏱ ${lang.time}</span><span class="lang-level level-${lang.level}">${lang.levelText}</span></div>
  </article>`;
}

function renderCards(list,targetGrid=grid){
  targetGrid.innerHTML=list.map((l,i)=>cardTemplate(l,i)).join('');
  if(targetGrid===grid)emptyState.hidden=list.length>0;
  $$('.lang-card',targetGrid).forEach(card=>{
    card.addEventListener('mousemove',e=>{const r=card.getBoundingClientRect();card.style.setProperty('--mx',`${e.clientX-r.left}px`);card.style.setProperty('--my',`${e.clientY-r.top}px`)});
    card.addEventListener('click',e=>{if(e.target.closest('[data-action]'))return;goToLang(card.dataset.id)});
  });
  $$('[data-action]',targetGrid).forEach(btn=>{
    btn.addEventListener('click',e=>{e.stopPropagation();const id=btn.dataset.id,a=btn.dataset.action;if(a==='star')toggleSaved(id);else if(a==='wish')toggleWished(id);refreshUI()});
  });
  requestAnimationFrame(()=>{$$('.lang-card',targetGrid).forEach(c=>c.classList.add('visible'))});
}

function refreshUI(){
  const total=store.saved.length+store.wishlist.length;
  const sc=$('#savedCount');sc.textContent=total;sc.classList.toggle('show',total>0);
  if(viewHome.classList.contains('active')){applyFilters();renderMyProgress()}
  if(viewLang.classList.contains('active')&&state.currentLangId){const l=LANGUAGES.find(x=>x.id===state.currentLangId);if(l)renderLangPage(l,true)}
  if(viewSaved.classList.contains('active'))renderSavedView();
}

function getFiltered(){
  return LANGUAGES.filter(lang=>{
    const q=state.query.trim().toLowerCase();
    const mq=!q||lang.name.toLowerCase().includes(q)||lang.tag.toLowerCase().includes(q)||lang.desc.toLowerCase().includes(q)||lang.steps.some(s=>s.title.toLowerCase().includes(q)||s.tags.some(t=>t.toLowerCase().includes(q)));
    let mf=true;
    if(state.filter==='saved')mf=isSaved(lang.id);
    else if(state.filter==='wishlist')mf=isWished(lang.id);
    else if(state.filter!=='all')mf=lang.level===state.filter;
    return mq&&mf;
  });
}
function applyFilters(){renderCards(getFiltered())}

searchInput.addEventListener('input',e=>{
  state.query=e.target.value;searchClear.classList.toggle('show',state.query.length>0);
  if(state.currentLangId||viewSaved.classList.contains('active'))showHome();
  else applyFilters();
});
searchClear.addEventListener('click',()=>{searchInput.value='';state.query='';searchClear.classList.remove('show');searchInput.focus();applyFilters()});
$$('.chip').forEach(chip=>chip.addEventListener('click',()=>{
  $$('.chip').forEach(c=>c.classList.remove('active'));chip.classList.add('active');state.filter=chip.dataset.filter;
  if(state.currentLangId||viewSaved.classList.contains('active'))showHome();
  else applyFilters();
}));
$('#resetBtn').addEventListener('click',()=>{
  state.query='';state.filter='all';searchInput.value='';searchClear.classList.remove('show');
  $$('.chip').forEach(c=>c.classList.toggle('active',c.dataset.filter==='all'));applyFilters();
});

function renderMyProgress(){
  const box=$('#myProgress');
  const totalSteps=Object.values(store.progress).reduce((s,a)=>s+a.length,0);
  if(totalSteps===0){box.classList.remove('show');return}
  box.classList.add('show');
  const totalAll=LANGUAGES.reduce((s,l)=>s+l.steps.length,0);
  const pct=Math.round((totalSteps/totalAll)*100);
  const inProg=LANGUAGES.filter(l=>getDoneSteps(l.id).length>0);
  box.innerHTML=`<div class="my-progress-head"><h3>📊 Твой прогресс</h3><span class="my-progress-pct">${pct}%</span></div>
  <div class="progress-track"><div class="progress-fill" style="width:${pct}%"></div></div>
  <p class="my-progress-sub">${totalSteps} из ${totalAll} этапов пройдено · ${inProg.length} языков в процессе</p>`;
}

function hideAllViews(){viewHome.classList.remove('active');viewLang.classList.remove('active');viewSaved.classList.remove('active')}
function showHome(){
  hideAllViews();viewHome.classList.add('active');
  searchWrap.classList.remove('hidden');breadcrumbs.hidden=true;state.currentLangId=null;
  window.scrollTo({top:0,behavior:'smooth'});
  history.pushState({page:'home'},'','#');
  requestAnimationFrame(()=>{applyFilters();renderMyProgress()});
}
function goToLang(id){
  const lang=LANGUAGES.find(l=>l.id===id);if(!lang)return;
  state.currentLangId=id;hideAllViews();viewLang.classList.add('active');
  searchWrap.classList.add('hidden');breadcrumbs.hidden=false;
  renderLangPage(lang);
  window.scrollTo({top:0,behavior:'auto'});
  history.pushState({page:'lang',id},'','#'+id);
}
function showSaved(){
  hideAllViews();viewSaved.classList.add('active');
  searchWrap.classList.remove('hidden');breadcrumbs.hidden=true;state.currentLangId=null;
  renderSavedView();
  window.scrollTo({top:0,behavior:'smooth'});
  history.pushState({page:'saved'},'','#saved');
}
$('#savedBtn').addEventListener('click',showSaved);

function renderLangPage(lang,keepScroll=false){
  const page=$('#langPage');const oldScroll=window.scrollY;
  const done=getDoneSteps(lang.id).length,total=lang.steps.length,pct=Math.round((done/total)*100);
  const star=isSaved(lang.id),wish=isWished(lang.id);
  const others=LANGUAGES.filter(l=>l.id!==lang.id).slice(0,4);
  page.innerHTML=`<div class="lang-hero">
    <div class="lang-hero-icon" style="background:${lang.color}">${lang.icon}</div>
    <div class="lang-hero-info">
      <h1>${lang.name}</h1><p class="lang-tag">${lang.tag}</p>
      <div class="lang-hero-meta">
        <span class="meta-pill">⏱ ${lang.time}</span>
        <span class="meta-pill level-${lang.level}">${lang.levelText}</span>
        <span class="meta-pill">📚 ${total} этапов</span>
      </div>
      <div class="lang-hero-actions">
        <button class="action-btn ${star?'active-star':''}" data-action="star" data-id="${lang.id}">
          <svg viewBox="0 0 24 24" fill="${star?'currentColor':'none'}" stroke="currentColor" stroke-width="2"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14l-5-4.87 6.91-1.01z"/></svg>
          ${star?'В избранном':'В избранное'}
        </button>
        <button class="action-btn ${wish?'active-wish':''}" data-action="wish" data-id="${lang.id}">
          <svg viewBox="0 0 24 24" fill="${wish?'currentColor':'none'}" stroke="currentColor" stroke-width="2"><path d="M12 21s-7-4.35-9.33-8.5C.86 8.9 2.66 5 6.5 5c2.04 0 3.54 1.15 4.5 2.5C11.96 6.15 13.46 5 15.5 5c3.84 0 5.64 3.9 3.83 7.5C19 16.65 12 21 12 21z"/></svg>
          ${wish?'В планах':'Хочу изучить'}
        </button>
      </div>
    </div>
  </div>
  <div class="lang-progress-box">
    <div class="lang-progress-head"><h3>📊 Прогресс изучения</h3><span class="lang-progress-pct">${pct}%</span></div>
    <div class="progress-track"><div class="progress-fill" style="width:${pct}%"></div></div>
    <p class="lang-progress-sub">${done} из ${total} этапов пройдено${done===total?' — поздравляем, курс завершён! 🎉':''}</p>
  </div>
  <p class="lang-intro">${lang.desc}</p>
  <div class="stages-tabs" id="stagesTabs">
    <button class="stage-tab active" data-stage="all">Все этапы</button>
    ${lang.steps.map((s,i)=>`<button class="stage-tab" data-stage="${i}">${i+1}. ${s.title.split(' ')[0]}</button>`).join('')}
  </div>
  <div class="stages-grid" id="stagesGrid">
    ${lang.steps.map((s,i)=>stageTemplate(s,i,isStepDone(lang.id,i))).join('')}
  </div>
  <div class="more-langs"><h3>Другие языки</h3>
    <div class="more-langs-row">
      ${others.map(l=>`<button class="mini-lang" data-goto="${l.id}"><div class="mini-lang-icon" style="background:${l.color}">${l.icon}</div><span class="mini-lang-name">${l.name}</span></button>`).join('')}
    </div>
  </div>`;

  $$('[data-action]',page).forEach(btn=>btn.addEventListener('click',()=>{
    const a=btn.dataset.action;if(a==='star')toggleSaved(lang.id);else if(a==='wish')toggleWished(lang.id);refreshUI();
  }));
  $$('.stage-check',page).forEach(btn=>btn.addEventListener('click',e=>{
    e.stopPropagation();const idx=+btn.dataset.step;toggleStep(lang.id,idx);
    const card=btn.closest('.stage-card');const isDone=isStepDone(lang.id,idx);
    card.classList.toggle('done',isDone);btn.classList.toggle('checked',isDone);
    updateLangProgress(lang);
  }));
  const tabs=$$('#stagesTabs .stage-tab',page);
  tabs.forEach(tab=>tab.addEventListener('click',()=>{
    tabs.forEach(t=>t.classList.remove('active'));tab.classList.add('active');
    const v=tab.dataset.stage;const cards=$$('#stagesGrid .stage-card',page);
    cards.forEach((c,i)=>c.style.display=(v==='all'||+v===i)?'':'none');
  }));
  $$('.mini-lang',page).forEach(b=>b.addEventListener('click',()=>goToLang(b.dataset.goto)));
  if(keepScroll)requestAnimationFrame(()=>window.scrollTo({top:oldScroll,behavior:'auto'}));
}

function updateLangProgress(lang){
  const done=getDoneSteps(lang.id).length,total=lang.steps.length,pct=Math.round((done/total)*100);
  const p=$('.lang-progress-pct'),f=$('.lang-progress-box .progress-fill'),s=$('.lang-progress-sub');
  if(p)p.textContent=pct+'%';if(f)f.style.width=pct+'%';
  if(s)s.innerHTML=`${done} из ${total} этапов пройдено${done===total?' — поздравляем, курс завершён! 🎉':''}`;
}
function stageTemplate(step,i,isDone){
  return `<div class="stage-card ${isDone?'done':''}" style="animation-delay:${i*50}ms">
    <div class="stage-head">
      <div class="stage-num">${i+1}</div>
      <div class="stage-title-wrap"><h3>${step.title}</h3></div>
      <button class="stage-check ${isDone?'checked':''}" data-step="${i}" title="${isDone?'Снять отметку':'Отметить'}">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6L9 17l-5-5"/></svg>
      </button>
    </div>
    <p>${step.desc}</p>
    <div class="tags">${step.tags.map(t=>`<span class="tag">${t}</span>`).join('')}</div>
    ${step.url?`<a class="stage-link" href="${step.url}" target="_blank" rel="noopener">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
      Читать
    </a>`:''}
  </div>`;
}

function renderSavedView(){
  const savedL=LANGUAGES.filter(l=>isSaved(l.id));
  const wishL=LANGUAGES.filter(l=>isWished(l.id));
  const inProg=LANGUAGES.filter(l=>getDoneSteps(l.id).length>0&&!isSaved(l.id)&&!isWished(l.id));
  renderCards(savedL,$('#savedGrid'));$('#savedEmpty').hidden=savedL.length>0;
  renderCards(wishL,$('#wishlistGrid'));$('#wishlistEmpty').hidden=wishL.length>0;
  renderCards(inProg,$('#progressGrid'));$('#progressEmpty').hidden=inProg.length>0;
}

document.addEventListener('click',e=>{
  const b=e.target.closest('[data-route="home"]');
  if(b){e.preventDefault();showHome()}
});

window.addEventListener('popstate',()=>{
  const h=location.hash.slice(1);
  if(h==='saved')showSaved();
  else if(h&&LANGUAGES.some(l=>l.id===h))goToLang(h);
  else showHome();
});

const io=new IntersectionObserver(entries=>{
  entries.forEach(en=>{if(en.isIntersecting){en.target.classList.add('visible');io.unobserve(en.target)}});
},{threshold:0.12});
function observeReveals(){$$('.reveal').forEach(el=>io.observe(el))}

function animateCounters(){
  $$('[data-count]').forEach(el=>{
    const t=+el.dataset.count;let c=0;const step=Math.ceil(t/60);
    const timer=setInterval(()=>{c+=step;if(c>=t){c=t;clearInterval(timer)}el.textContent=c},20);
  });
}

document.addEventListener('DOMContentLoaded',()=>{
  const total=store.saved.length+store.wishlist.length;
  const sc=$('#savedCount');sc.textContent=total;sc.classList.toggle('show',total>0);
  applyFilters();renderMyProgress();observeReveals();setTimeout(animateCounters,400);
  const h=location.hash.slice(1);
  if(h==='saved')showSaved();
  else if(h&&LANGUAGES.some(l=>l.id===h))goToLang(h);
});
</script>
</body>
</html>
