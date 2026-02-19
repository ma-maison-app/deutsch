<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Deutsch — My Study Space</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Work+Sans:wght@300;400;500&family=Allura&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
:root {
  --ink: #0f0e0c; --paper: #f5f0e8; --gold: #b8913f; --gold-light: #d4a853;
  --muted: #7a7168; --border: rgba(184,145,63,0.25); --radius: 3px;
  --shadow: 0 4px 24px rgba(15,14,12,0.07); --shadow-deep: 0 8px 48px rgba(15,14,12,0.13);
  --m: #4a6fa5; --f: #a54a6f; --n: #4a8f6f;
}
html { scroll-behavior: smooth; }
body {
  background: var(--paper); color: var(--ink);
  font-family: 'Work Sans', sans-serif; font-weight: 300; min-height: 100vh;
  background-image: radial-gradient(ellipse at 15% 0%,rgba(184,145,63,.08) 0%,transparent 55%),
                    radial-gradient(ellipse at 85% 100%,rgba(184,145,63,.05) 0%,transparent 50%);
}

/* ── HEADER ── */
header { text-align:center; padding:2.5rem 2rem 1.5rem; position:relative; }
header::after { content:''; display:block; width:60px; height:1px; background:linear-gradient(90deg,transparent,var(--gold),transparent); margin:1.2rem auto 0; }
.site-script { font-family:'Allura',cursive; font-size:clamp(2.8rem,7vw,5rem); color:var(--gold); line-height:1; }
.site-sub { font-family:'Cormorant Garamond',serif; font-size:0.76rem; letter-spacing:.4em; text-transform:uppercase; color:var(--muted); margin-top:.25rem; }
.user-bar { position:absolute; right:1.5rem; top:1.5rem; display:flex; align-items:center; gap:.6rem; }
.user-email { font-size:.65rem; letter-spacing:.12em; color:var(--muted); }
.sync-status { font-size:.6rem; letter-spacing:.1em; color:var(--n); }
.sync-status.err { color:var(--f); }

/* ── AUTH SCREEN ── */
#auth-screen {
  display:flex; align-items:center; justify-content:center;
  min-height:calc(100vh - 140px); padding:2rem;
}
.auth-box {
  background:rgba(255,255,255,.68); border:1px solid var(--border);
  border-radius:var(--radius); box-shadow:var(--shadow-deep);
  padding:2.5rem 2.5rem 2rem; width:100%; max-width:400px; backdrop-filter:blur(4px);
}
.auth-tabs { display:flex; gap:0; margin-bottom:2rem; border-bottom:1px solid var(--border); }
.auth-tab { font-family:'Work Sans',sans-serif; font-size:.68rem; font-weight:500; letter-spacing:.2em; text-transform:uppercase; color:var(--muted); background:none; border:none; border-bottom:2px solid transparent; padding:.5rem 1.2rem .6rem; cursor:pointer; margin-bottom:-1px; transition:all .2s; }
.auth-tab.active { color:var(--gold); border-bottom-color:var(--gold); }
.auth-form { display:none; }
.auth-form.active { display:block; }
.auth-form .fg { margin-bottom:.9rem; }
.auth-err { font-size:.75rem; color:var(--f); margin-top:.8rem; min-height:1.1rem; font-family:'Cormorant Garamond',serif; font-style:italic; }
.auth-note { font-size:.72rem; color:var(--muted); margin-top:.75rem; font-family:'Cormorant Garamond',serif; font-style:italic; text-align:center; }

/* ── NAV ── */
nav { display:flex; justify-content:center; padding:0 2rem 2rem; border-bottom:1px solid var(--border); }
.tab-btn { font-family:'Work Sans',sans-serif; font-size:.68rem; font-weight:500; letter-spacing:.22em; text-transform:uppercase; color:var(--muted); background:none; border:1px solid transparent; padding:.55rem 1.8rem; cursor:pointer; transition:all .2s; }
.tab-btn.active { color:var(--gold); border-color:var(--border); background:rgba(184,145,63,.05); }
.tab-btn:hover:not(.active) { color:var(--ink); }

/* ── LAYOUT ── */
main { max-width:1100px; margin:0 auto; padding:2.5rem 1.5rem 6rem; }
.panel { display:none; }
.panel.active { display:block; animation:fadeUp .3s ease; }
@keyframes fadeUp { from{opacity:0;transform:translateY(8px)} to{opacity:1;transform:translateY(0)} }

/* ── STATS ── */
.stats-row { display:flex; margin-bottom:2rem; background:rgba(255,255,255,.5); border:1px solid var(--border); border-radius:var(--radius); overflow:hidden; }
.stat { flex:1; padding:.9rem 1rem; text-align:center; border-right:1px solid var(--border); }
.stat:last-child { border-right:none; }
.stat-num { font-family:'Cormorant Garamond',serif; font-size:1.8rem; font-weight:300; color:var(--gold); line-height:1; }
.stat-num.m{color:var(--m)} .stat-num.f{color:var(--f)} .stat-num.n{color:var(--n)}
.stat-label { font-size:.57rem; letter-spacing:.18em; text-transform:uppercase; color:var(--muted); margin-top:.2rem; }

/* ── ADD CARD ── */
.add-card { background:rgba(255,255,255,.65); border:1px solid var(--border); border-radius:var(--radius); box-shadow:var(--shadow); margin-bottom:2.5rem; overflow:hidden; }
.add-card-header { padding:1.2rem 1.8rem; border-bottom:1px solid transparent; display:flex; align-items:center; justify-content:space-between; cursor:pointer; user-select:none; transition:border-color .2s; }
.add-card.open .add-card-header { border-bottom-color:var(--border); }
.add-card-title { font-family:'Cormorant Garamond',serif; font-size:1.05rem; font-style:italic; display:flex; align-items:center; gap:.6rem; }
.add-icon { display:inline-flex; width:20px; height:20px; background:var(--gold); color:white; border-radius:50%; align-items:center; justify-content:center; font-size:.95rem; font-style:normal; font-family:'Work Sans',sans-serif; flex-shrink:0; transition:transform .25s; }
.add-card.open .add-icon { transform:rotate(45deg); }
.add-card-hint { font-size:.6rem; letter-spacing:.14em; text-transform:uppercase; color:var(--muted); }
.add-card-body { display:none; padding:1.8rem 2rem 2rem; }
.add-card.open .add-card-body { display:block; }

/* ── WORD HERO INPUTS ── */
.word-hero { display:grid; grid-template-columns:120px 1fr 1fr; border:1px solid var(--border); border-radius:var(--radius); overflow:hidden; margin-bottom:1.4rem; background:rgba(245,240,232,.6); }
.wh-cell { padding:1rem 1.2rem; display:flex; flex-direction:column; gap:.25rem; border-right:1px solid var(--border); }
.wh-cell:last-child { border-right:none; }
.wh-label { font-size:.57rem; letter-spacing:.18em; text-transform:uppercase; color:var(--muted); }
.wh-cell select, .wh-cell input { font-family:'Cormorant Garamond',serif; font-size:1.55rem; font-weight:400; background:transparent; border:none; border-bottom:1.5px solid rgba(184,145,63,.2); border-radius:0; padding:.15rem 0; color:var(--ink); width:100%; transition:border-color .2s; }
.wh-cell select { font-size:1.1rem; cursor:pointer; }
.wh-cell select:focus, .wh-cell input:focus { outline:none; border-bottom-color:var(--gold); background:transparent; }
.wh-cell input::placeholder { color:rgba(15,14,12,.2); font-style:italic; }
#v-translation, #edit-translation { font-style:italic; color:var(--muted); }

/* ── CHIPS ── */
.chips-label { font-size:.6rem; letter-spacing:.18em; text-transform:uppercase; color:var(--muted); margin-bottom:.45rem; }
.chips { display:flex; flex-wrap:wrap; gap:.35rem; margin-bottom:1.3rem; }
.chip { font-size:.62rem; letter-spacing:.1em; text-transform:uppercase; padding:.28rem .7rem; border-radius:20px; border:1px solid var(--border); color:var(--muted); background:transparent; cursor:pointer; transition:all .15s; font-family:'Work Sans',sans-serif; font-weight:400; }
.chip.on { background:var(--gold); border-color:var(--gold); color:white; }
.chip:hover:not(.on) { border-color:var(--gold); color:var(--gold); }

/* ── FORM FIELDS ── */
.dg { display:grid; grid-template-columns:repeat(auto-fill,minmax(155px,1fr)); gap:.75rem; margin-bottom:.75rem; }
.fg { display:flex; flex-direction:column; gap:.22rem; }
.fg.full { grid-column:1/-1; }
.fg label { font-size:.58rem; letter-spacing:.16em; text-transform:uppercase; color:var(--muted); }
.fg input, .fg select, .fg textarea { font-family:'Work Sans',sans-serif; font-weight:300; font-size:.83rem; background:rgba(245,240,232,.75); border:1px solid rgba(184,145,63,.2); border-radius:var(--radius); padding:.48rem .72rem; color:var(--ink); transition:border-color .2s; width:100%; }
.fg input:focus,.fg select:focus,.fg textarea:focus { outline:none; border-color:var(--gold); background:rgba(255,255,255,.9); }
.fg textarea { resize:vertical; min-height:56px; }

/* ── BUTTONS ── */
.btn { font-family:'Work Sans',sans-serif; font-size:.64rem; font-weight:500; letter-spacing:.2em; text-transform:uppercase; padding:.58rem 1.4rem; border:1px solid var(--gold); border-radius:var(--radius); background:var(--gold); color:var(--paper); cursor:pointer; transition:all .2s; }
.btn:hover { background:var(--gold-light); border-color:var(--gold-light); }
.btn:disabled { opacity:.5; cursor:not-allowed; }
.btn.sec { background:transparent; color:var(--gold); }
.btn.sec:hover { background:rgba(184,145,63,.08); }
.btn.sm { padding:.32rem .7rem; font-size:.58rem; }
.btn.danger { border-color:rgba(165,74,111,.35); color:#a54a6f; background:transparent; }
.btn.danger:hover { background:rgba(165,74,111,.07); }
.btn-row { display:flex; gap:.6rem; align-items:center; flex-wrap:wrap; margin-top:1rem; }

/* ── FILTER BAR ── */
.filter-bar { display:flex; gap:.55rem; margin-bottom:1.5rem; flex-wrap:wrap; align-items:center; }
.filter-bar input, .filter-bar select { font-family:'Work Sans',sans-serif; font-weight:300; font-size:.81rem; background:rgba(255,255,255,.58); border:1px solid var(--border); border-radius:var(--radius); padding:.46rem .72rem; color:var(--ink); transition:border-color .2s; min-width:100px; }
.filter-bar input:focus,.filter-bar select:focus { outline:none; border-color:var(--gold); }
.filter-bar input { flex:1; min-width:130px; max-width:240px; }
.count-badge { font-size:.62rem; letter-spacing:.1em; color:var(--muted); margin-left:auto; }
.csv-btns { display:flex; gap:.35rem; }
#csv-import-input { display:none; }

/* ── VOCAB CARDS ── */
.vocab-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(285px,1fr)); gap:1rem; }
.vocab-card { background:rgba(255,255,255,.62); border:1px solid var(--border); border-radius:var(--radius); padding:1.15rem 1.35rem .9rem; box-shadow:var(--shadow); transition:box-shadow .2s,transform .2s; position:relative; overflow:hidden; }
.vocab-card:hover { box-shadow:var(--shadow-deep); transform:translateY(-2px); }
.vocab-card::before { content:''; position:absolute; left:0;top:0;bottom:0; width:3px; }
.vocab-card[data-gender="der"]::before{background:var(--m)}
.vocab-card[data-gender="die"]::before{background:var(--f)}
.vocab-card[data-gender="das"]::before{background:var(--n)}
.vocab-card[data-gender=""]::before{background:var(--gold)}
.vc-word { font-family:'Cormorant Garamond',serif; font-size:1.4rem; font-weight:500; line-height:1.1; }
.vc-art { font-size:.66rem; letter-spacing:.12em; text-transform:uppercase; margin-right:.2rem; font-family:'Work Sans',sans-serif; }
.vc-art.der{color:var(--m)} .vc-art.die{color:var(--f)} .vc-art.das{color:var(--n)}
.vc-trans { font-family:'Cormorant Garamond',serif; font-style:italic; font-size:.95rem; color:var(--muted); margin:.15rem 0 .65rem; }
.vc-tags { display:flex; flex-wrap:wrap; gap:.3rem; margin-bottom:.65rem; }
.tag { font-size:.56rem; letter-spacing:.1em; text-transform:uppercase; padding:.12rem .45rem; border-radius:20px; border:1px solid var(--border); color:var(--muted); }
.tag.topic { color:var(--gold); border-color:rgba(184,145,63,.4); }
.vc-extra { font-size:.77rem; color:#4a4540; line-height:1.55; border-top:1px solid rgba(184,145,63,.12); padding-top:.6rem; margin-top:.3rem; }
.vc-el { font-size:.58rem; letter-spacing:.12em; text-transform:uppercase; color:var(--muted); display:block; margin-top:.35rem; margin-bottom:.1rem; }
.vc-el:first-child{margin-top:0}
.vc-ctx { font-family:'Cormorant Garamond',serif; font-style:italic; font-size:.88rem; border-left:2px solid var(--border); padding-left:.55rem; }
.card-actions { display:flex; gap:.3rem; justify-content:flex-end; margin-top:.7rem; }

/* ── NOTES ── */
.notes-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(280px,1fr)); gap:1rem; }
.note-card { background:rgba(255,255,255,.62); border:1px solid var(--border); border-radius:var(--radius); padding:1.15rem 1.35rem; box-shadow:var(--shadow); transition:box-shadow .2s; }
.note-card:hover { box-shadow:var(--shadow-deep); }
.note-type { font-size:.57rem; letter-spacing:.18em; text-transform:uppercase; color:var(--gold); margin-bottom:.35rem; }
.note-title { font-family:'Cormorant Garamond',serif; font-size:1.1rem; font-weight:500; margin-bottom:.35rem; }
.note-body { font-size:.8rem; line-height:1.65; color:#4a4540; white-space:pre-wrap; word-break:break-word; }
.note-link { display:inline-block; margin-top:.5rem; font-size:.7rem; color:var(--gold); text-decoration:none; border-bottom:1px solid var(--border); transition:border-color .2s; word-break:break-all; }
.note-link:hover { border-color:var(--gold); }

/* ── EMPTY ── */
.empty-state { text-align:center; padding:4rem 2rem; color:var(--muted); grid-column:1/-1; }
.empty-script { font-family:'Allura',cursive; font-size:3rem; color:rgba(184,145,63,.22); margin-bottom:.5rem; }
.empty-state p { font-family:'Cormorant Garamond',serif; font-style:italic; }

/* ── MODAL ── */
.modal-overlay { display:none; position:fixed; inset:0; background:rgba(15,14,12,.55); backdrop-filter:blur(4px); z-index:100; align-items:center; justify-content:center; padding:1rem; }
.modal-overlay.open { display:flex; }
.modal { background:var(--paper); border:1px solid var(--border); border-radius:var(--radius); padding:2rem; max-width:540px; width:100%; max-height:90vh; overflow-y:auto; box-shadow:var(--shadow-deep); animation:fadeUp .22s ease; }
.modal-title { font-family:'Cormorant Garamond',serif; font-size:1.3rem; font-style:italic; margin-bottom:1.2rem; padding-bottom:.75rem; border-bottom:1px solid var(--border); }

/* ── TOAST ── */
.toast { position:fixed; bottom:2rem; right:2rem; background:var(--ink); color:var(--paper); font-size:.7rem; letter-spacing:.1em; padding:.6rem 1.2rem; border-radius:var(--radius); opacity:0; transform:translateY(6px); transition:all .25s; pointer-events:none; z-index:200; }
.toast.show { opacity:1; transform:translateY(0); }
.toast.ok { background:var(--n); }
.toast.err { background:var(--f); }

/* ── DICT LINKS ── */
.dict-bar { display:flex; flex-wrap:wrap; gap:.45rem; margin-bottom:2rem; padding:.9rem 1.1rem; background:rgba(255,255,255,.5); border:1px solid var(--border); border-radius:var(--radius); align-items:center; }
.dict-label { font-size:.56rem; letter-spacing:.18em; text-transform:uppercase; color:var(--muted); margin-right:.3rem; flex-shrink:0; }
.dict-link { font-size:.67rem; font-weight:400; letter-spacing:.08em; padding:.26rem .7rem; border:1px solid var(--border); border-radius:20px; color:var(--muted); text-decoration:none; transition:all .18s; background:transparent; white-space:nowrap; }
.dict-link:hover { color:var(--gold); border-color:var(--gold); background:rgba(184,145,63,.05); }
.dict-link .di { font-size:.55rem; opacity:.6; margin-left:.25rem; }

/* ── LOOKUP LINK ON CARDS ── */
.vc-lookup { display:inline-flex; gap:.25rem; margin-top:.35rem; flex-wrap:wrap; }
.vc-lookup a { font-size:.56rem; letter-spacing:.1em; text-transform:uppercase; color:var(--muted); text-decoration:none; border-bottom:1px dotted rgba(184,145,63,.35); transition:color .15s; }
.vc-lookup a:hover { color:var(--gold); }

/* ── HEATMAP ── */
.heatmap-section { margin-bottom:2.5rem; }
.heatmap-title { font-family:'Cormorant Garamond',serif; font-size:1.05rem; font-style:italic; color:var(--ink); margin-bottom:.5rem; }
.heatmap-subtitle { font-size:.62rem; letter-spacing:.14em; text-transform:uppercase; color:var(--muted); margin-bottom:1.2rem; }
.heatmap-wrap { background:rgba(255,255,255,.5); border:1px solid var(--border); border-radius:var(--radius); padding:1.4rem 1.6rem 1.2rem; overflow-x:auto; }
.heatmap-months { display:flex; gap:0; margin-bottom:.35rem; padding-left:28px; }
.hm-month-label { font-size:.57rem; letter-spacing:.1em; text-transform:uppercase; color:var(--muted); flex:0 0 auto; }
.heatmap-grid { display:flex; gap:3px; }
.hm-day-labels { display:flex; flex-direction:column; gap:3px; margin-right:5px; }
.hm-day-label { font-size:.52rem; color:var(--muted); height:12px; line-height:12px; width:22px; text-align:right; }
.hm-weeks { display:flex; gap:3px; }
.hm-week { display:flex; flex-direction:column; gap:3px; }
.hm-day { width:12px; height:12px; border-radius:2px; background:rgba(184,145,63,.08); border:1px solid rgba(184,145,63,.1); cursor:default; transition:transform .1s; flex-shrink:0; }
.hm-day:hover { transform:scale(1.3); z-index:1; }
.hm-day.l1 { background:rgba(184,145,63,.25); border-color:rgba(184,145,63,.3); }
.hm-day.l2 { background:rgba(184,145,63,.5); border-color:rgba(184,145,63,.5); }
.hm-day.l3 { background:rgba(184,145,63,.75); border-color:rgba(184,145,63,.7); }
.hm-day.l4 { background:var(--gold); border-color:var(--gold-light); }
.hm-day.future { background:transparent; border-color:transparent; }
.heatmap-legend { display:flex; align-items:center; gap:.4rem; margin-top:.9rem; justify-content:flex-end; }
.hm-leg-label { font-size:.56rem; letter-spacing:.08em; color:var(--muted); }
.hm-leg-swatch { width:11px; height:11px; border-radius:2px; border:1px solid rgba(184,145,63,.2); }
.heatmap-tooltip { position:fixed; background:var(--ink); color:var(--paper); font-size:.65rem; padding:.3rem .6rem; border-radius:2px; pointer-events:none; z-index:300; display:none; letter-spacing:.04em; }

/* ── MONTHLY BARS ── */
.monthly-bars { display:grid; grid-template-columns:repeat(auto-fill,minmax(60px,1fr)); gap:.6rem; margin-top:1rem; }
.mbar-item { display:flex; flex-direction:column; align-items:center; gap:.3rem; }
.mbar-track { width:100%; height:60px; background:rgba(184,145,63,.07); border-radius:2px; display:flex; align-items:flex-end; border:1px solid var(--border); overflow:hidden; }
.mbar-fill { width:100%; background:linear-gradient(180deg,var(--gold-light),var(--gold)); border-radius:2px 2px 0 0; transition:height .4s ease; }
.mbar-label { font-size:.56rem; letter-spacing:.1em; text-transform:uppercase; color:var(--muted); }
.mbar-count { font-family:'Cormorant Garamond',serif; font-size:.9rem; color:var(--gold); }

/* ── PROGRESS STATS ── */
.prog-cards { display:grid; grid-template-columns:repeat(auto-fill,minmax(140px,1fr)); gap:.75rem; margin-bottom:2rem; }
.prog-card { background:rgba(255,255,255,.55); border:1px solid var(--border); border-radius:var(--radius); padding:1rem 1.2rem; text-align:center; }
.prog-num { font-family:'Cormorant Garamond',serif; font-size:2rem; color:var(--gold); line-height:1; }
.prog-desc { font-size:.58rem; letter-spacing:.14em; text-transform:uppercase; color:var(--muted); margin-top:.25rem; }
.prog-sub { font-size:.7rem; font-family:'Cormorant Garamond',serif; font-style:italic; color:var(--muted); margin-top:.15rem; }
.streak-flame { font-size:1.1rem; }

@media(max-width:600px){
  .word-hero{grid-template-columns:1fr}
  .wh-cell{border-right:none;border-bottom:1px solid var(--border)}
  .wh-cell:last-child{border-bottom:none}
  .vocab-grid{grid-template-columns:1fr}
  .user-bar{position:static;justify-content:center;padding:.5rem 0 0}
  .heatmap-wrap{padding:.9rem .7rem}
}
</style>
</head>
<body>

<header>
  <div class="user-bar" id="user-bar" style="display:none">
    <span class="user-email" id="user-email"></span>
    <span class="sync-status" id="sync-status"></span>
    <button class="btn sm sec" onclick="signOut()">Sign out</button>
  </div>
  <div class="site-script">Deutsch</div>
  <div class="site-sub">my study space</div>
</header>

<!-- ══════════════════════════════════════════
     AUTH SCREEN
══════════════════════════════════════════ -->
<div id="auth-screen">
  <div class="auth-box">
    <div class="auth-tabs">
      <button class="auth-tab active" onclick="showAuthTab('login',this)">Sign in</button>
      <button class="auth-tab" onclick="showAuthTab('signup',this)">Create account</button>
    </div>

    <div class="auth-form active" id="form-login">
      <div class="fg"><label>Email</label><input type="email" id="login-email" placeholder="you@example.com" onkeydown="if(event.key==='Enter')g('login-pass').focus()"></div>
      <div class="fg"><label>Password</label><input type="password" id="login-pass" placeholder="••••••••" onkeydown="if(event.key==='Enter')handleLogin()"></div>
      <div class="btn-row"><button class="btn" id="login-btn" onclick="handleLogin()">Sign in</button></div>
      <div class="auth-err" id="login-err"></div>
    </div>

    <div class="auth-form" id="form-signup">
      <div class="fg"><label>Email</label><input type="email" id="signup-email" placeholder="you@example.com" onkeydown="if(event.key==='Enter')g('signup-pass').focus()"></div>
      <div class="fg"><label>Password</label><input type="password" id="signup-pass" placeholder="min. 6 characters" onkeydown="if(event.key==='Enter')handleSignup()"></div>
      <div class="btn-row"><button class="btn" id="signup-btn" onclick="handleSignup()">Create account</button></div>
      <div class="auth-err" id="signup-err"></div>
      <div class="auth-note">Your data syncs to the cloud — access it from any device.</div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════
     APP
══════════════════════════════════════════ -->
<div id="app" style="display:none">
  <nav>
    <button class="tab-btn active" onclick="switchTab('vocab',this)">Vocabulary</button>
    <button class="tab-btn" onclick="switchTab('notes',this)">Notes &amp; Resources</button>
    <button class="tab-btn" onclick="switchTab('progress',this);renderProgress()">Progress</button>
  </nav>

  <main>

    <!-- VOCAB -->
    <div id="panel-vocab" class="panel active">

      <div class="dict-bar">
        <span class="dict-label">Dictionaries</span>
        <a class="dict-link" href="https://www.dict.cc" target="_blank" rel="noopener">dict.cc <span class="di">↗</span></a>
        <a class="dict-link" href="https://www.linguee.com/german-english" target="_blank" rel="noopener">Linguee <span class="di">↗</span></a>
        <a class="dict-link" href="https://www.pons.com/translate/german-english" target="_blank" rel="noopener">PONS <span class="di">↗</span></a>
        <a class="dict-link" href="https://www.duden.de/suchen/dudenonline" target="_blank" rel="noopener">Duden <span class="di">↗</span></a>
        <a class="dict-link" href="https://www.deepl.com/translator#de/en/" target="_blank" rel="noopener">DeepL <span class="di">↗</span></a>
        <a class="dict-link" href="https://context.reverso.net/translation/german-english" target="_blank" rel="noopener">Reverso Context <span class="di">↗</span></a>
        <a class="dict-link" href="https://de.wiktionary.org" target="_blank" rel="noopener">Wiktionary DE <span class="di">↗</span></a>
      </div>

      <div id="stats-row" class="stats-row"></div>

      <div class="add-card" id="add-card">
        <div class="add-card-header" onclick="toggleCard('add-card','add-hint','add word')">
          <div class="add-card-title"><span class="add-icon">+</span>Add a new word</div>
          <span class="add-card-hint" id="add-hint">add word</span>
        </div>
        <div class="add-card-body">
          <div class="word-hero">
            <div class="wh-cell">
              <span class="wh-label">Article</span>
              <select id="v-gender">
                <option value="">—</option>
                <option value="der">der</option>
                <option value="die">die</option>
                <option value="das">das</option>
              </select>
            </div>
            <div class="wh-cell">
              <span class="wh-label">German word</span>
              <input type="text" id="v-word" placeholder="Fernweh" autocomplete="off"
                onkeydown="if(event.key==='Enter')g('v-translation').focus()">
            </div>
            <div class="wh-cell">
              <span class="wh-label">Translation</span>
              <input type="text" id="v-translation" placeholder="wanderlust" autocomplete="off"
                onkeydown="if(event.key==='Enter')addWord()">
            </div>
          </div>

          <div class="chips-label">Topic</div>
          <div class="chips" id="chips-add"></div>

          <div class="dg">
            <div class="fg"><label>Week</label><input type="number" id="v-week" placeholder="3" min="1"></div>
            <div class="fg"><label>Quarter</label>
              <select id="v-quarter"><option value="">—</option><option value="Q1">Q1</option><option value="Q2">Q2</option><option value="Q3">Q3</option><option value="Q4">Q4</option></select>
            </div>
            <div class="fg"><label>Year</label><input type="number" id="v-year" value="2026"></div>
            <div class="fg"><label>Cases / Conjugation</label><input type="text" id="v-cases" placeholder="den Fernweh · läuft, lief"></div>
            <div class="fg full"><label>Context sentence</label><input type="text" id="v-context" placeholder="Ich habe Fernweh nach Wien."></div>
          </div>
          <div class="btn-row">
            <button class="btn" onclick="addWord()">Save word</button>
            <button class="btn sec" onclick="clearVocabForm()">Clear</button>
          </div>
        </div>
      </div>

      <div class="filter-bar">
        <input type="text" id="search-input" placeholder="Search…" oninput="renderVocab()">
        <select id="filter-gender" onchange="renderVocab()">
          <option value="">All genders</option>
          <option value="der">der</option><option value="die">die</option><option value="das">das</option>
        </select>
        <select id="filter-topic" onchange="renderVocab()"><option value="">All topics</option></select>
        <select id="filter-quarter" onchange="renderVocab()">
          <option value="">All quarters</option>
          <option value="Q1">Q1</option><option value="Q2">Q2</option><option value="Q3">Q3</option><option value="Q4">Q4</option>
        </select>
        <select id="sort-select" onchange="renderVocab()">
          <option value="newest">Newest first</option>
          <option value="alpha">A → Z</option>
          <option value="week">By week</option>
        </select>
        <div class="csv-btns">
          <button class="btn sec sm" onclick="exportCSV()">↓ CSV</button>
          <button class="btn sec sm" onclick="g('csv-import-input').click()">↑ Import</button>
          <input type="file" id="csv-import-input" accept=".csv" onchange="importCSV(event)">
        </div>
        <span class="count-badge" id="vocab-count"></span>
      </div>

      <div class="vocab-grid" id="vocab-grid"></div>
    </div>

    <!-- NOTES -->
    <div id="panel-notes" class="panel">

      <div class="dict-bar">
        <span class="dict-label">Grammar help</span>
        <a class="dict-link" href="https://www.germanveryeasy.com" target="_blank" rel="noopener">German Very Easy <span class="di">↗</span></a>
        <a class="dict-link" href="https://www.dartmouth.edu/~deutsch/Grammatik/Grammatik.html" target="_blank" rel="noopener">Dartmouth Grammar <span class="di">↗</span></a>
        <a class="dict-link" href="https://www.germanpod101.com" target="_blank" rel="noopener">GermanPod101 <span class="di">↗</span></a>
        <a class="dict-link" href="https://www.youtube.com/@EasyGerman" target="_blank" rel="noopener">Easy German YT <span class="di">↗</span></a>
        <a class="dict-link" href="https://ankiweb.net/decks" target="_blank" rel="noopener">Anki Decks <span class="di">↗</span></a>
      </div>

      <div class="add-card" id="note-card">
        <div class="add-card-header" onclick="toggleCard('note-card','note-hint','add note')">
          <div class="add-card-title"><span class="add-icon">+</span>Add a note or resource</div>
          <span class="add-card-hint" id="note-hint">add note</span>
        </div>
        <div class="add-card-body">
          <div class="dg">
            <div class="fg"><label>Type</label>
              <select id="n-type" onchange="toggleLink()">
                <option value="note">Note</option>
                <option value="grammar">Grammar rule</option>
                <option value="resource">Resource / Link</option>
                <option value="tip">Study tip</option>
                <option value="phrase">Useful phrase</option>
              </select>
            </div>
            <div class="fg" style="flex:2;min-width:200px"><label>Title</label><input type="text" id="n-title" placeholder="e.g. Dative after 'mit'"></div>
            <div class="fg full" id="n-link-wrap" style="display:none"><label>URL</label><input type="url" id="n-link" placeholder="https://…"></div>
            <div class="fg full"><label>Content</label><textarea id="n-body" rows="3" placeholder="Rules, mnemonics, observations…"></textarea></div>
          </div>
          <div class="btn-row">
            <button class="btn" onclick="addNote()">Save</button>
            <button class="btn sec" onclick="clearNoteForm()">Clear</button>
          </div>
        </div>
      </div>

      <div class="filter-bar">
        <input type="text" id="note-search" placeholder="Search notes…" oninput="renderNotes()">
        <select id="note-type-filter" onchange="renderNotes()">
          <option value="">All types</option>
          <option value="note">Notes</option><option value="grammar">Grammar</option>
          <option value="resource">Resources</option><option value="tip">Tips</option>
          <option value="phrase">Phrases</option>
        </select>
        <span class="count-badge" id="note-count"></span>
      </div>

      <div class="notes-grid" id="notes-grid"></div>
    </div>

    <!-- PROGRESS -->
    <div id="panel-progress" class="panel">
      <div class="prog-cards" id="prog-cards"></div>
      <div class="heatmap-section">
        <div class="heatmap-title">Word additions — past year</div>
        <div class="heatmap-subtitle">Each square is one day</div>
        <div class="heatmap-wrap">
          <div class="heatmap-months" id="hm-month-labels"></div>
          <div class="heatmap-grid">
            <div class="hm-day-labels">
              <div class="hm-day-label" style="margin-top:0">Mon</div>
              <div class="hm-day-label" style="margin-top:12px">Wed</div>
              <div class="hm-day-label" style="margin-top:12px">Fri</div>
            </div>
            <div class="hm-weeks" id="hm-weeks"></div>
          </div>
          <div class="heatmap-legend">
            <span class="hm-leg-label">Less</span>
            <div class="hm-leg-swatch" style="background:rgba(184,145,63,.08)"></div>
            <div class="hm-leg-swatch" style="background:rgba(184,145,63,.25)"></div>
            <div class="hm-leg-swatch" style="background:rgba(184,145,63,.5)"></div>
            <div class="hm-leg-swatch" style="background:rgba(184,145,63,.75)"></div>
            <div class="hm-leg-swatch" style="background:var(--gold)"></div>
            <span class="hm-leg-label">More</span>
          </div>
        </div>
      </div>
      <div class="heatmap-section">
        <div class="heatmap-title">Words per month</div>
        <div class="heatmap-subtitle">How many new words you added each month</div>
        <div class="heatmap-wrap">
          <div class="monthly-bars" id="monthly-bars"></div>
        </div>
      </div>
    </div>

  </main>
</div>

<!-- Edit Modal -->
<div class="modal-overlay" id="edit-modal">
  <div class="modal">
    <div class="modal-title">Edit word</div>
    <input type="hidden" id="edit-id">
    <div class="word-hero" style="margin-bottom:1.2rem">
      <div class="wh-cell"><span class="wh-label">Article</span>
        <select id="edit-gender"><option value="">—</option><option value="der">der</option><option value="die">die</option><option value="das">das</option></select>
      </div>
      <div class="wh-cell"><span class="wh-label">German word</span><input type="text" id="edit-word"></div>
      <div class="wh-cell"><span class="wh-label">Translation</span><input type="text" id="edit-translation"></div>
    </div>
    <div class="chips-label">Topic</div>
    <div class="chips" id="chips-edit" style="margin-bottom:1.2rem"></div>
    <div class="dg">
      <div class="fg"><label>Week</label><input type="number" id="edit-week"></div>
      <div class="fg"><label>Quarter</label>
        <select id="edit-quarter"><option value="">—</option><option value="Q1">Q1</option><option value="Q2">Q2</option><option value="Q3">Q3</option><option value="Q4">Q4</option></select>
      </div>
      <div class="fg"><label>Year</label><input type="number" id="edit-year"></div>
      <div class="fg"><label>Cases / Conjugation</label><input type="text" id="edit-cases"></div>
      <div class="fg full"><label>Context sentence</label><input type="text" id="edit-context"></div>
    </div>
    <div class="btn-row">
      <button class="btn" onclick="saveEdit()">Save changes</button>
      <button class="btn sec" onclick="closeModal()">Cancel</button>
    </div>
  </div>
</div>

<div class="heatmap-tooltip" id="hm-tooltip"></div>
<div class="toast" id="toast"></div>

<script>
// ══════════════════════════════════════════════════════════
// SUPABASE CONFIG  (same REST pattern as your CBT app)
// ══════════════════════════════════════════════════════════
const SB = {
  url: 'https://cjjutbqvkcqqzxduqipe.supabase.co',
  key: 'sb_publishable_jgqgGhV9DyWJ3sTJVUISwg_8yUR1Lt6',
  user: null,

  headers(extra={}) {
    const h = { 'Content-Type':'application/json', 'apikey': this.key, ...extra };
    if (this.user?.token) h['Authorization'] = `Bearer ${this.user.token}`;
    return h;
  },

  async signUp(email, password) {
    const r = await fetch(`${this.url}/auth/v1/signup`, {
      method:'POST', headers: this.headers(),
      body: JSON.stringify({ email, password })
    });
    const d = await r.json();
    if (d.error || d.msg) throw new Error(d.error_description || d.msg || d.error);
    if (!d.access_token) throw new Error('Check your email to confirm your account, then sign in.');
    this.user = { uid:d.user.id, email:d.user.email, token:d.access_token, refresh:d.refresh_token };
    await this._persist();
    return this.user;
  },

  async signIn(email, password) {
    const r = await fetch(`${this.url}/auth/v1/token?grant_type=password`, {
      method:'POST', headers: this.headers(),
      body: JSON.stringify({ email, password })
    });
    const d = await r.json();
    if (d.error || d.error_description) throw new Error(d.error_description || d.error);
    this.user = { uid:d.user.id, email:d.user.email, token:d.access_token, refresh:d.refresh_token };
    await this._persist();
    return this.user;
  },

  async signOut() {
    try {
      await fetch(`${this.url}/auth/v1/logout`, { method:'POST', headers: this.headers() });
    } catch(e){}
    this.user = null;
    try { localStorage.removeItem('sb_user'); } catch(e){}
  },

  async refreshToken() {
    if (!this.user?.refresh) return;
    try {
      const r = await fetch(`${this.url}/auth/v1/token?grant_type=refresh_token`, {
        method:'POST', headers: this.headers(),
        body: JSON.stringify({ refresh_token: this.user.refresh })
      });
      const d = await r.json();
      if (d.access_token) {
        this.user.token = d.access_token;
        this.user.refresh = d.refresh_token;
        await this._persist();
      }
    } catch(e){}
  },

  // Store all vocab+notes as JSON in a single row per user
  async saveData(vocab, notes) {
    const body = { user_id: this.user.uid, vocab: JSON.stringify(vocab), notes: JSON.stringify(notes) };
    const r = await fetch(`${this.url}/rest/v1/deutsch_data?on_conflict=user_id`, {
      method:'POST',
      headers: this.headers({ 'Prefer':'return=minimal,resolution=merge-duplicates' }),
      body: JSON.stringify(body)
    });
    if (!r.ok) {
      let msg = r.statusText;
      try { const e=await r.json(); msg=e.message||e.hint||JSON.stringify(e); } catch(ex){}
      throw new Error(msg);
    }
    return true;
  },

  async loadData() {
    const r = await fetch(`${this.url}/rest/v1/deutsch_data?user_id=eq.${this.user.uid}&select=*`, {
      headers: this.headers()
    });
    const d = await r.json();
    if (!r.ok) throw new Error(d.message||JSON.stringify(d));
    if (!d || !d.length) return { vocab:[], notes:[] };
    return {
      vocab: JSON.parse(d[0].vocab || '[]'),
      notes: JSON.parse(d[0].notes || '[]')
    };
  },

  // IndexedDB persistence for session (mirrors your CBT app)
  _dbName:'DeutschDB', _store:'auth',
  async _getDB() {
    return new Promise((res,rej)=>{
      const req = indexedDB.open(this._dbName,1);
      req.onerror = ()=>rej(req.error);
      req.onsuccess = ()=>res(req.result);
      req.onupgradeneeded = e=>{ const db=e.target.result; if(!db.objectStoreNames.contains(this._store)) db.createObjectStore(this._store); };
    });
  },
  async _persist() {
    const data = { ...this.user, ts: Date.now() };
    try { localStorage.setItem('sb_user', JSON.stringify(data)); } catch(e){}
    try { const db=await this._getDB(); db.transaction([this._store],'readwrite').objectStore(this._store).put(data,'u'); } catch(e){}
  },
  async restoreSession() {
    // try memory then localStorage then IndexedDB
    let u = null;
    try { u = JSON.parse(localStorage.getItem('sb_user')); } catch(e){}
    if (!u) {
      try {
        const db = await this._getDB();
        u = await new Promise((res,rej)=>{ const t=db.transaction([this._store],'readonly'); const req=t.objectStore(this._store).get('u'); req.onsuccess=()=>res(req.result); req.onerror=()=>rej(); });
      } catch(e){}
    }
    if (u?.token) { this.user = u; await this.refreshToken(); }
    return this.user;
  }
};

// ══════════════════════════════════════════════════════════
// DATA
// ══════════════════════════════════════════════════════════
const TOPICS = ['Daily Life','Food & Drink','Travel','Work & Study','People & Social','Time & Dates','Nature','Body & Health','Grammar','Expressions','Numbers','Other'];
let vocab=[], notes=[], topicAdd='', topicEdit='';
let saveTimer=null;

const g = id => document.getElementById(id);
const esc = s => (s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');

function toast(msg, type='ok') {
  const t=g('toast'); t.textContent=msg; t.className='toast show '+(type||'');
  clearTimeout(t._t); t._t=setTimeout(()=>t.classList.remove('show'),2500);
}

// Debounced cloud save
function scheduleSave() {
  clearTimeout(saveTimer);
  setSyncStatus('saving…', '');
  saveTimer = setTimeout(async()=>{
    try { await SB.saveData(vocab,notes); setSyncStatus('synced ✓','ok'); }
    catch(e){ setSyncStatus('sync failed','err'); }
  }, 1200);
}
function setSyncStatus(msg, cls) {
  const el=g('sync-status'); el.textContent=msg; el.className='sync-status '+(cls||'');
}

// ══════════════════════════════════════════════════════════
// AUTH
// ══════════════════════════════════════════════════════════
function showAuthTab(tab, btn) {
  document.querySelectorAll('.auth-tab').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.auth-form').forEach(f=>f.classList.remove('active'));
  btn.classList.add('active');
  g('form-'+tab).classList.add('active');
}

async function handleLogin() {
  const email=g('login-email').value.trim(), pass=g('login-pass').value;
  g('login-err').textContent=''; g('login-btn').disabled=true; g('login-btn').textContent='Signing in…';
  try {
    await SB.signIn(email, pass);
    await bootApp();
  } catch(e) {
    g('login-err').textContent=e.message;
  } finally { g('login-btn').disabled=false; g('login-btn').textContent='Sign in'; }
}

async function handleSignup() {
  const email=g('signup-email').value.trim(), pass=g('signup-pass').value;
  g('signup-err').textContent=''; g('signup-btn').disabled=true; g('signup-btn').textContent='Creating…';
  try {
    await SB.signUp(email, pass);
    await bootApp();
  } catch(e) {
    g('signup-err').textContent=e.message;
  } finally { g('signup-btn').disabled=false; g('signup-btn').textContent='Create account'; }
}

async function signOut() {
  await SB.signOut();
  vocab=[]; notes=[];
  g('app').style.display='none';
  g('auth-screen').style.display='flex';
  g('user-bar').style.display='none';
}

// ══════════════════════════════════════════════════════════
// BOOT
// ══════════════════════════════════════════════════════════
async function bootApp() {
  g('auth-screen').style.display='none';
  g('app').style.display='block';
  g('user-bar').style.display='flex';
  g('user-email').textContent=SB.user.email;
  setSyncStatus('loading…','');

  try {
    const data = await SB.loadData();
    vocab = data.vocab; notes = data.notes;
    setSyncStatus('synced ✓','ok');
  } catch(e) {
    setSyncStatus('load failed','err');
    toast('Could not load cloud data: '+e.message,'err');
  }

  drawChips('chips-add','','toggleChipAdd');
  drawChips('chips-edit','','toggleChipEdit');
  updateTopicDrop(); renderVocab(); renderNotes();
}

// ══════════════════════════════════════════════════════════
// UI HELPERS
// ══════════════════════════════════════════════════════════
function switchTab(tab,btn){
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  g('panel-'+tab).classList.add('active'); btn.classList.add('active');
}
function toggleCard(id,hintId,label){
  const c=g(id); c.classList.toggle('open');
  g(hintId).textContent=c.classList.contains('open')?'collapse':label;
}

// CHIPS
function drawChips(containerId, sel, fn) {
  g(containerId).innerHTML = TOPICS.map(t=>`<button class="chip${sel===t?' on':''}" onclick="${fn}('${t}')">${t}</button>`).join('');
}
function toggleChipAdd(t){ topicAdd=topicAdd===t?'':t; drawChips('chips-add',topicAdd,'toggleChipAdd'); }
function toggleChipEdit(t){ topicEdit=topicEdit===t?'':t; drawChips('chips-edit',topicEdit,'toggleChipEdit'); }

// TOPIC DROPDOWN
function updateTopicDrop(){
  const sel=g('filter-topic'), cur=sel.value;
  const used=[...new Set(vocab.map(v=>v.topic).filter(Boolean))].sort();
  sel.innerHTML=`<option value="">All topics</option>`+used.map(t=>`<option value="${esc(t)}"${cur===t?' selected':''}>${esc(t)}</option>`).join('');
}

// ══════════════════════════════════════════════════════════
// VOCAB CRUD
// ══════════════════════════════════════════════════════════
function addWord(){
  const word=g('v-word').value.trim(), translation=g('v-translation').value.trim();
  if(!word||!translation){toast('Word and translation required.','err');return;}
  vocab.unshift({id:Date.now(),gender:g('v-gender').value,word,translation,topic:topicAdd,
    week:g('v-week').value,quarter:g('v-quarter').value,year:g('v-year').value||2026,
    cases:g('v-cases').value.trim(),context:g('v-context').value.trim(),added:Date.now()});
  clearVocabForm(); updateTopicDrop(); renderVocab();
  toggleCard('add-card','add-hint','add word');
  scheduleSave();
}
function clearVocabForm(){
  ['v-word','v-translation','v-week','v-cases','v-context'].forEach(id=>g(id).value='');
  g('v-gender').value=''; g('v-quarter').value=''; g('v-year').value=2026;
  topicAdd=''; drawChips('chips-add','','toggleChipAdd');
}
function deleteWord(id){
  if(!confirm('Delete this word?'))return;
  vocab=vocab.filter(v=>v.id!==id); renderVocab(); scheduleSave();
}
function openEdit(id){
  const v=vocab.find(x=>x.id===id); if(!v)return;
  ['gender','word','translation','week','quarter','year','cases','context'].forEach(f=>g('edit-'+f).value=v[f]||'');
  g('edit-id').value=id; topicEdit=v.topic||'';
  drawChips('chips-edit',topicEdit,'toggleChipEdit');
  g('edit-modal').classList.add('open');
}
function saveEdit(){
  const id=parseInt(g('edit-id').value), idx=vocab.findIndex(x=>x.id===id); if(idx===-1)return;
  vocab[idx]={...vocab[idx],gender:g('edit-gender').value,word:g('edit-word').value.trim(),
    translation:g('edit-translation').value.trim(),topic:topicEdit,week:g('edit-week').value,
    quarter:g('edit-quarter').value,year:g('edit-year').value,
    cases:g('edit-cases').value.trim(),context:g('edit-context').value.trim()};
  closeModal(); updateTopicDrop(); renderVocab(); scheduleSave();
}
function closeModal(){g('edit-modal').classList.remove('open');}
g('edit-modal').addEventListener('click',e=>{if(e.target===g('edit-modal'))closeModal();});

// RENDER VOCAB
function renderVocab(){
  const sq=g('search-input').value.toLowerCase(),
        fg=g('filter-gender').value, fq=g('filter-quarter').value,
        ft=g('filter-topic').value, sort=g('sort-select').value;
  let list=vocab.filter(v=>{
    const ms=!sq||[v.word,v.translation,v.context,v.cases].some(s=>(s||'').toLowerCase().includes(sq));
    return ms&&(!fg||v.gender===fg)&&(!fq||v.quarter===fq)&&(!ft||v.topic===ft);
  });
  if(sort==='alpha') list.sort((a,b)=>a.word.localeCompare(b.word));
  else if(sort==='week') list.sort((a,b)=>(a.week||0)-(b.week||0));

  g('vocab-count').textContent=list.length+' word'+(list.length!==1?'s':'');

  const tot=vocab.length, der=vocab.filter(v=>v.gender==='der').length,
        die=vocab.filter(v=>v.gender==='die').length, das=vocab.filter(v=>v.gender==='das').length;
  g('stats-row').innerHTML=`
    <div class="stat"><div class="stat-num">${tot}</div><div class="stat-label">Total</div></div>
    <div class="stat"><div class="stat-num m">${der}</div><div class="stat-label">der</div></div>
    <div class="stat"><div class="stat-num f">${die}</div><div class="stat-label">die</div></div>
    <div class="stat"><div class="stat-num n">${das}</div><div class="stat-label">das</div></div>
    <div class="stat"><div class="stat-num" style="font-size:1.3rem">${tot-der-die-das}</div><div class="stat-label">verbs/phrases</div></div>`;

  if(!list.length){
    g('vocab-grid').innerHTML=`<div class="empty-state"><div class="empty-script">leer</div><p>No words yet — or nothing matches.</p></div>`;
    return;
  }
  g('vocab-grid').innerHTML=list.map(v=>`
    <div class="vocab-card" data-gender="${esc(v.gender)}">
      <div class="vc-word">${v.gender?`<span class="vc-art ${v.gender}">${esc(v.gender)}</span>`:''}${esc(v.word)}</div>
      <div class="vc-trans">${esc(v.translation)}</div>
      <div class="vc-tags">
        ${v.topic?`<span class="tag topic">${esc(v.topic)}</span>`:''}
        ${v.week?`<span class="tag">Wk ${esc(v.week)}</span>`:''}
        ${v.quarter?`<span class="tag">${esc(v.quarter)}</span>`:''}
        ${v.year?`<span class="tag">${esc(v.year)}</span>`:''}
      </div>
      ${v.cases||v.context?`<div class="vc-extra">
        ${v.cases?`<span class="vc-el">Cases / Conj.</span>${esc(v.cases)}`:''}
        ${v.context?`<span class="vc-el">Context</span><div class="vc-ctx">${esc(v.context)}</div>`:''}
      </div>`:''}
      <div class="vc-lookup">
        <a href="https://www.dict.cc/?s=${encodeURIComponent(v.word)}" target="_blank" rel="noopener">dict.cc</a>
        <a href="https://www.linguee.com/german-english/search?query=${encodeURIComponent(v.word)}" target="_blank" rel="noopener">Linguee</a>
        <a href="https://www.duden.de/suchen/dudenonline/${encodeURIComponent(v.word)}" target="_blank" rel="noopener">Duden</a>
      </div>
      <div class="card-actions">
        <button class="btn sec sm" onclick="openEdit(${v.id})">Edit</button>
        <button class="btn sm danger" onclick="deleteWord(${v.id})">Delete</button>
      </div>
    </div>`).join('');
}

// ══════════════════════════════════════════════════════════
// CSV
// ══════════════════════════════════════════════════════════
function exportCSV(){
  if(!vocab.length){toast('No words to export.','err');return;}
  const h=['gender','word','translation','topic','week','quarter','year','cases','context'];
  const rows=vocab.map(v=>h.map(k=>`"${(v[k]||'').toString().replace(/"/g,'""')}"`).join(','));
  const blob=new Blob([[h.join(','),...rows].join('\n')],{type:'text/csv;charset=utf-8;'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='deutsch_vocab_'+new Date().toISOString().slice(0,10)+'.csv';
  a.click();
}
function importCSV(event){
  const file=event.target.files[0]; if(!file)return;
  const r=new FileReader();
  r.onload=e=>{
    const lines=e.target.result.trim().split('\n');
    const headers=parseRow(lines[0]);
    let added=0,skipped=0;
    for(let i=1;i<lines.length;i++){
      const vals=parseRow(lines[i]), obj={};
      headers.forEach((h,idx)=>obj[h.trim()]=(vals[idx]||'').trim());
      if(!obj.word||!obj.translation){skipped++;continue;}
      if(vocab.some(v=>v.word===obj.word&&v.translation===obj.translation)){skipped++;continue;}
      vocab.push({id:Date.now()+i,...obj,added:Date.now()}); added++;
    }
    updateTopicDrop(); renderVocab(); scheduleSave();
    toast(`Imported ${added} word(s).${skipped?` Skipped ${skipped}.`:''}`);
  };
  r.readAsText(file); event.target.value='';
}
function parseRow(row){
  const res=[]; let cur='',inQ=false;
  for(let i=0;i<row.length;i++){
    const c=row[i];
    if(c==='"'){if(inQ&&row[i+1]==='"'){cur+='"';i++;}else inQ=!inQ;}
    else if(c===','&&!inQ){res.push(cur);cur='';}
    else cur+=c;
  }
  res.push(cur); return res;
}

// ══════════════════════════════════════════════════════════
// NOTES CRUD
// ══════════════════════════════════════════════════════════
function toggleLink(){g('n-link-wrap').style.display=g('n-type').value==='resource'?'block':'none';}
function addNote(){
  const title=g('n-title').value.trim(); if(!title){toast('Title required.','err');return;}
  notes.unshift({id:Date.now(),type:g('n-type').value,title,body:g('n-body').value.trim(),link:g('n-link').value.trim(),added:Date.now()});
  clearNoteForm(); renderNotes(); scheduleSave();
}
function clearNoteForm(){['n-title','n-body','n-link'].forEach(id=>g(id).value='');g('n-type').value='note';toggleLink();}
function deleteNote(id){if(!confirm('Delete?'))return;notes=notes.filter(n=>n.id!==id);renderNotes();scheduleSave();}
const TLABELS={note:'Note',grammar:'Grammar',resource:'Resource',tip:'Study Tip',phrase:'Phrase'};
function renderNotes(){
  const sq=g('note-search').value.toLowerCase(), ft=g('note-type-filter').value;
  let list=notes.filter(n=>{
    const ms=!sq||[n.title,n.body].some(s=>(s||'').toLowerCase().includes(sq));
    return ms&&(!ft||n.type===ft);
  });
  g('note-count').textContent=list.length+' item'+(list.length!==1?'s':'');
  if(!list.length){g('notes-grid').innerHTML=`<div class="empty-state" style="grid-column:1/-1"><div class="empty-script">leer</div><p>No notes yet.</p></div>`;return;}
  g('notes-grid').innerHTML=list.map(n=>`
    <div class="note-card">
      <div class="note-type">${TLABELS[n.type]||n.type}</div>
      <div class="note-title">${esc(n.title)}</div>
      ${n.body?`<div class="note-body">${esc(n.body)}</div>`:''}
      ${n.link?`<a href="${esc(n.link)}" target="_blank" rel="noopener" class="note-link">${esc(n.link)}</a>`:''}
      <div class="card-actions"><button class="btn sm danger" onclick="deleteNote(${n.id})">Delete</button></div>
    </div>`).join('');
}

// ══════════════════════════════════════════════════════════
// PROGRESS & HEATMAP
// ══════════════════════════════════════════════════════════
function renderProgress() {
  // ── Stats cards ──
  const total = vocab.length;
  const today = new Date(); today.setHours(0,0,0,0);
  const todayStr = today.toDateString();
  const todayCount = vocab.filter(v=>new Date(v.added).toDateString()===todayStr).length;

  // streak
  let streak=0, d=new Date(today);
  while(true){
    const ds=d.toDateString();
    if(vocab.some(v=>new Date(v.added).toDateString()===ds)){streak++;d.setDate(d.getDate()-1);}
    else break;
  }

  // best day
  const dayMap={};
  vocab.forEach(v=>{const k=new Date(v.added).toDateString();dayMap[k]=(dayMap[k]||0)+1;});
  const bestDay=Object.values(dayMap).length?Math.max(...Object.values(dayMap)):0;

  // this week
  const weekStart=new Date(today); weekStart.setDate(today.getDate()-today.getDay());
  const thisWeek=vocab.filter(v=>new Date(v.added)>=weekStart).length;

  g('prog-cards').innerHTML=`
    <div class="prog-card"><div class="prog-num">${total}</div><div class="prog-desc">Total words</div></div>
    <div class="prog-card"><div class="prog-num">${todayCount}</div><div class="prog-desc">Added today</div></div>
    <div class="prog-card"><div class="prog-num"><span class="streak-flame">🔥</span>${streak}</div><div class="prog-desc">Day streak</div><div class="prog-sub">consecutive days</div></div>
    <div class="prog-card"><div class="prog-num">${thisWeek}</div><div class="prog-desc">This week</div></div>
    <div class="prog-card"><div class="prog-num">${bestDay}</div><div class="prog-desc">Best day</div><div class="prog-sub">words in one day</div></div>
  `;

  // ── Heatmap ──
  // Start from Monday 52 weeks ago
  const end = new Date(today);
  // go to next Saturday so we complete the week
  const endDay = end.getDay(); // 0=Sun
  end.setDate(end.getDate() + (6-endDay));
  const start = new Date(end);
  start.setDate(end.getDate() - 52*7 + 1);
  // align to Monday
  while(start.getDay()!==1) start.setDate(start.getDate()-1);

  // Build month labels
  const weeksEl=g('hm-weeks'); weeksEl.innerHTML='';
  const monthLabelsEl=g('hm-month-labels'); monthLabelsEl.innerHTML='';

  let cur=new Date(start), weeks=[], weekDays=[], prevMonth=-1, monthWidths=[];
  let curMonthWeeks=0;
  while(cur<=end){
    if(weekDays.length===7){ weeks.push(weekDays); weekDays=[]; curMonthWeeks++; }
    const isToday=cur.toDateString()===todayStr;
    const isFuture=cur>today;
    const count=dayMap[cur.toDateString()]||0;
    let lvl='';
    if(!isFuture&&count>0){lvl=count>=5?'l4':count>=3?'l3':count>=2?'l2':'l1';}
    const dateStr=cur.toLocaleDateString('en-GB',{day:'numeric',month:'short',year:'numeric'});
    const label=count>0?`${count} word${count!==1?'s':''} · ${dateStr}`:dateStr;
    weekDays.push({lvl,future:isFuture,today:isToday,label});

    // month label
    const m=cur.getMonth();
    if(m!==prevMonth){
      if(prevMonth!==-1) monthWidths.push({month:new Date(cur.getFullYear(),prevMonth,1).toLocaleString('default',{month:'short'}),weeks:curMonthWeeks});
      curMonthWeeks=0; prevMonth=m;
    }
    cur.setDate(cur.getDate()+1);
  }
  if(weekDays.length) weeks.push(weekDays);
  monthWidths.push({month:new Date(today.getFullYear(),prevMonth,1).toLocaleString('default',{month:'short'}),weeks:curMonthWeeks+1});

  // Render month labels
  monthLabelsEl.innerHTML=monthWidths.map(mw=>`<div class="hm-month-label" style="width:${mw.weeks*15}px">${mw.month}</div>`).join('');

  // Render weeks
  const tip=g('hm-tooltip');
  weeksEl.innerHTML=weeks.map(wk=>`<div class="hm-week">${wk.map(day=>`<div class="hm-day${day.lvl?' '+day.lvl:''}${day.future?' future':''}${day.today?' today':''}" data-tip="${day.label}"></div>`).join('')}</div>`).join('');

  // Tooltip events
  weeksEl.querySelectorAll('.hm-day:not(.future)').forEach(el=>{
    el.addEventListener('mouseenter',e=>{
      tip.textContent=el.dataset.tip; tip.style.display='block';
    });
    el.addEventListener('mousemove',e=>{
      tip.style.left=(e.clientX+12)+'px'; tip.style.top=(e.clientY-28)+'px';
    });
    el.addEventListener('mouseleave',()=>{ tip.style.display='none'; });
  });

  // ── Monthly bars ──
  const months=[];
  for(let i=11;i>=0;i--){
    const d=new Date(today.getFullYear(),today.getMonth()-i,1);
    const key=`${d.getFullYear()}-${d.getMonth()}`;
    const count=vocab.filter(v=>{const a=new Date(v.added);return a.getFullYear()===d.getFullYear()&&a.getMonth()===d.getMonth();}).length;
    months.push({label:d.toLocaleString('default',{month:'short'}),year:d.getFullYear(),count});
  }
  const maxCount=Math.max(...months.map(m=>m.count),1);
  g('monthly-bars').innerHTML=months.map(m=>`
    <div class="mbar-item">
      <div class="mbar-count">${m.count||''}</div>
      <div class="mbar-track"><div class="mbar-fill" style="height:${Math.round((m.count/maxCount)*100)}%"></div></div>
      <div class="mbar-label">${m.label}</div>
    </div>`).join('');
}


(async()=>{
  const user = await SB.restoreSession();
  if (user) {
    await bootApp();
  }
})();
</script>
</body>
</html>
