# Einkaufsliste-
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#b4472b">
<title>Unterschlupf – Einkaufsliste</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Rubik+Dirt&display=swap">
<style>
:root{
  --bg:#f7f5f0;--card:#fff;--tx:#201d18;--mu:#7a7468;--bd:#ddd8cc;
  --ac:#b4472b;--ac-tx:#fff;--ok:#2e7d4f;--dg:#c62828;
  --ease:cubic-bezier(.32,.72,0,1);
}
@media (prefers-color-scheme:dark){
  :root:not([data-theme="light"]){
    color-scheme:dark;--bg:#171512;--card:#211e1a;--tx:#efeae0;--mu:#a39c8e;
    --bd:#3a352d;--ac:#e0704f;--ac-tx:#1a0f0a;--ok:#5fbf86;--dg:#ef6a6a;
  }
}
:root[data-theme="dark"]{
  color-scheme:dark;--bg:#171512;--card:#211e1a;--tx:#efeae0;--mu:#a39c8e;
  --bd:#3a352d;--ac:#e0704f;--ac-tx:#1a0f0a;--ok:#5fbf86;--dg:#ef6a6a;
}
html{scroll-padding-top:env(safe-area-inset-top,0px);scroll-behavior:smooth;-webkit-text-size-adjust:100%}
*,*::before,*::after{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
[hidden]{display:none!important}
body{
  margin:0;background:var(--bg);color:var(--tx);
  font:17px/1.4 system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;
  padding:calc(16px + env(safe-area-inset-top,0px)) 16px calc(24px + env(safe-area-inset-bottom,0px));
  min-height:100dvh;
}
#bg,#bgi{position:fixed;inset:0;width:100%;height:100%;z-index:-1;pointer-events:none}
#bgi{background:center/cover no-repeat;opacity:0;transition:opacity .6s var(--ease)}
#bg{transition:opacity .6s var(--ease),filter .6s var(--ease)}
body[data-bg="nacht"] #bg{filter:brightness(.45) hue-rotate(190deg) saturate(1.2)}
body[data-bg="schlicht"] #bg,body[data-bg="eigen"] #bg{opacity:0}
body[data-bg="eigen"] #bgi{opacity:1}

main{max-width:560px;margin:0 auto}
h1{font-size:1.4rem;margin:0}
h2{font-size:.8rem;color:var(--mu);font-weight:600;text-transform:uppercase;letter-spacing:.05em;margin:0 0 10px}

.top{display:flex;align-items:center;gap:10px;background:var(--card);border:1px solid var(--bd);border-radius:14px;padding:8px 12px;margin-bottom:14px}
.top h1{flex:1;word-break:break-word}
#mb,#bk{font-size:1.3rem;padding:8px 14px}

.card{background:var(--card);border:1px solid var(--bd);border-radius:14px;padding:14px;margin-bottom:14px}
.add{border:2px solid var(--ac)}
form{display:flex;gap:8px}
input[type=text]{flex:1;min-width:0;font:inherit;color:var(--tx);background:var(--bg);border:1px solid var(--bd);border-radius:10px;padding:12px}
input[type=text]:focus{outline:none;border-color:var(--ac)}
button{
  font:inherit;border:0;border-radius:10px;padding:12px 16px;cursor:pointer;
  background:var(--ac);color:var(--ac-tx);font-weight:600;
  transition:transform .2s var(--ease),opacity .2s,background-color .25s;
}
button:active{transform:scale(.96);opacity:.85}
button.sec{background:var(--bg);color:var(--tx);border:1px solid var(--bd);font-weight:400}

.chips{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px}
.chips button{padding:8px 12px;font-size:.92rem}

.lst{
  display:flex;align-items:center;justify-content:space-between;gap:10px;width:100%;
  text-align:left;background:var(--card);color:var(--tx);border:1px solid var(--bd);
  border-radius:14px;padding:16px;margin-bottom:10px;font-weight:600;
}
.lst:active{transform:scale(.985)}
.lst small{color:var(--mu);font-weight:400}

.item{
  display:flex;align-items:center;gap:12px;padding:10px 0;border-top:1px solid var(--bd);
  max-height:240px;overflow:hidden;
  transition:max-height .3s var(--ease),opacity .25s,transform .3s var(--ease),padding .3s var(--ease);
}
.item:first-child{border-top:0}
.item input{flex:none;width:24px;height:24px;accent-color:var(--ok);cursor:pointer}
.item span{
  flex:1;word-break:break-word;
  text-decoration:line-through;text-decoration-color:transparent;
  transition:color .3s,text-decoration-color .3s;
}
.item.done span{text-decoration-color:currentColor;color:var(--mu)}
.item .x{background:none;color:var(--mu);padding:4px 10px;font-size:1.3rem;font-weight:400}
.item.rm{max-height:0;opacity:0;transform:translateX(30px);padding-top:0;padding-bottom:0;pointer-events:none}

.empty{color:var(--mu)}
.foot{display:flex;justify-content:space-between;align-items:center;margin-top:10px;color:var(--mu);font-size:.9rem;gap:8px}
.note{color:var(--mu);font-size:.8rem;margin:8px 0 0}

.menu{
  display:flex;flex-direction:column;gap:4px;background:var(--card);
  border:1px solid var(--bd);border-radius:14px;padding:10px;margin:-6px 0 14px;
  transform-origin:top left;animation:fade .2s;
}
.menu>button{background:none;color:var(--tx);text-align:left;font-weight:400;padding:12px}
.menu>h2{margin:8px 12px 2px}
.sub{display:flex;gap:8px;padding:0 4px 6px}
.menu .bk{color:var(--mu)}
.menu .plus{font-weight:600;color:var(--ac)}
.menu .txt{padding:6px 12px;font-size:.9rem;color:var(--mu)}
.menu textarea{
  font:inherit;color:var(--tx);background:var(--bg);border:1px solid var(--bd);
  border-radius:10px;padding:10px;min-height:90px;width:100%;resize:vertical;margin:4px 0;
}
.menu.pop{animation:pop .3s var(--ease)}
.menu.closing{animation:none;opacity:0;transform:translateY(-8px) scale(.97);transition:opacity .2s,transform .2s var(--ease)}

.addl{
  width:100%;background:var(--card);color:var(--ac);border:1px dashed var(--bd);
  font-size:1.6rem;line-height:1;padding:8px;margin-bottom:10px;font-weight:400;
}
.top form{min-width:0;align-items:center}
.top form input{padding:8px 10px}
.top form button{padding:8px 14px;white-space:nowrap}

@keyframes enter{from{opacity:0;transform:translateY(12px)}to{opacity:1;transform:none}}
#app.enter{animation:enter .45s var(--ease)}
@keyframes fade{from{opacity:.4}to{opacity:1}}
@keyframes pop{from{opacity:0;transform:translateY(-8px) scale(.97)}to{opacity:1;transform:none}}
@keyframes itemIn{from{opacity:0;transform:translateY(-10px)}to{opacity:1;transform:none}}
.item.new{animation:itemIn .45s var(--ease)}

#sg{display:grid;grid-template-rows:0fr;opacity:0;transition:grid-template-rows .4s var(--ease),opacity .3s;pointer-events:none}
#sg.open{grid-template-rows:1fr;opacity:1;pointer-events:auto}
#sg>div{overflow:hidden;min-height:0}

#skd,#wtd,#cld{opacity:0;transition:opacity .6s var(--ease)}
#strp,#sunh{transition:opacity .6s var(--ease)}
#sun{transition:transform .6s var(--ease),fill .6s}
body[data-bg="tag"] #skd,body[data-bg="tag"] #wtd{opacity:1}
body[data-bg="tag"] #cld{opacity:.9}
body[data-bg="tag"] #strp,body[data-bg="tag"] #sunh{opacity:0}
body[data-bg="tag"] #sun{fill:#fffbe6;transform:translateY(-34px)}

.top.cave{background:linear-gradient(135deg,#6a635a,#3d3833);border-color:#2a2622}
.top.cave h1{
  font-family:"Rubik Dirt",Impact,"Arial Black",sans-serif;font-weight:400;
  font-size:1.7rem;letter-spacing:.05em;color:#e6dfd0;
  filter:url(#rough) drop-shadow(0 2px 0 #1d1a17);
}
.top.cave .sec{background:#4d473f;color:#e6dfd0;border-color:#2a2622}

@media (prefers-reduced-motion:reduce){
  *,*::before,*::after{animation:none!important;transition:none!important}
}
</style>
</head>
<body data-bg="wald">
<svg width="0" height="0" style="position:absolute" aria-hidden="true">
  <filter id="rough">
    <feTurbulence type="fractalNoise" baseFrequency=".05" numOctaves="2" result="n"/>
    <feDisplacementMap in="SourceGraphic" in2="n" scale="2.5"/>
  </filter>
</svg>

<svg id="bg" viewBox="0 0 400 225" preserveAspectRatio="xMidYMid slice" shape-rendering="crispEdges" aria-hidden="true">
  <defs>
    <linearGradient id="sk" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#d4896f"/><stop offset=".55" stop-color="#eebb98"/><stop offset="1" stop-color="#f6d9ba"/></linearGradient>
    <linearGradient id="skday" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#5fa8dc"/><stop offset="1" stop-color="#c4e6f3"/></linearGradient>
    <linearGradient id="wtday" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#b0dbe8"/><stop offset="1" stop-color="#4d8896"/></linearGradient>
    <linearGradient id="wt" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#dcbd9d"/><stop offset="1" stop-color="#6f8d8c"/></linearGradient>
    <path id="p" d="M0-60L12-38H6L16-20H9L20 0H-20L-9-20H-16L-6-38H-12Z M-2 0h4v8h-4Z"/>
  </defs>
  <rect width="400" height="152" fill="url(#sk)"/>
  <rect id="skd" width="400" height="152" fill="url(#skday)"/>
  <circle id="sunh" cx="200" cy="108" r="72" fill="#f6d3b0" opacity=".3"/>
  <circle id="sun" cx="200" cy="108" r="42" fill="#f8e6cf"/>
  <g id="cld" fill="#fff"><rect x="60" y="40" width="64" height="8"/><rect x="72" y="32" width="36" height="8"/><rect x="270" y="58" width="72" height="8"/><rect x="284" y="50" width="40" height="8"/></g>
  <g id="strp"><rect x="90" y="62" width="50" height="4" fill="#f4cfae" opacity=".7"/><rect x="270" y="48" width="60" height="4" fill="#f4cfae" opacity=".7"/><rect x="30" y="30" width="70" height="4" fill="#e2a07f" opacity=".7"/></g>
  <g fill="#a9bbab" opacity=".8"><use href="#p" transform="translate(40 152) scale(.55)"/><use href="#p" transform="translate(75 152) scale(.7)"/><use href="#p" transform="translate(110 152) scale(.5)"/><use href="#p" transform="translate(150 152) scale(.65)"/><use href="#p" transform="translate(250 152) scale(.7)"/><use href="#p" transform="translate(290 152) scale(.55)"/><use href="#p" transform="translate(325 152) scale(.75)"/><use href="#p" transform="translate(365 152) scale(.5)"/></g>
  <g fill="#6b8c83"><use href="#p" transform="translate(20 158) scale(1)"/><use href="#p" transform="translate(95 158) scale(.85)"/><use href="#p" transform="translate(135 158) scale(1.05)"/><use href="#p" transform="translate(268 158) scale(.95)"/><use href="#p" transform="translate(312 158) scale(1.1)"/><use href="#p" transform="translate(380 158) scale(.9)"/></g>
  <rect y="152" width="400" height="73" fill="url(#wt)"/>
  <rect id="wtd" y="152" width="400" height="73" fill="url(#wtday)"/>
  <rect x="182" y="158" width="36" height="6" fill="#f5dcc0" opacity=".7"/><rect x="188" y="170" width="24" height="5" fill="#f5dcc0" opacity=".55"/><rect x="192" y="182" width="16" height="4" fill="#f5dcc0" opacity=".4"/>
  <g fill="#4a3438"><rect x="6" y="0" width="11" height="225"/><rect x="30" y="0" width="6" height="225"/><rect x="372" y="0" width="12" height="225"/><rect x="352" y="0" width="6" height="225"/></g>
  <g fill="#2c4642"><use href="#p" transform="translate(20 70) scale(1.6)"/><use href="#p" transform="translate(12 135) scale(1.9)"/><use href="#p" transform="translate(385 60) scale(1.7)"/><use href="#p" transform="translate(370 130) scale(2)"/></g>
  <g fill="#556a45"><ellipse cx="35" cy="224" rx="60" ry="14"/><ellipse cx="365" cy="224" rx="60" ry="14"/></g>
</svg>

<div id="bgi"></div>
<input type="file" accept="image/*" id="fg" hidden>
<input type="file" accept="image/*" id="fc" capture="environment" hidden>
<main id="app"></main>

<script>
(function () {
  const KEY = 'einkaufsliste-v2';
  const OLD = 'einkaufsliste-v1';
  const BGK = 'einkaufsliste-bg';
  const VK = 'einkaufsliste-view';
  const IMGK = 'einkaufsliste-bgimg';
  const FBK = 'einkaufsliste-feedback';

  const QUICK = [
    'Rohmilch', 'Rohmilchbutter', 'Rohe Sahne', 'Eier (bio)',
    'Rinderhack', 'Leber', 'Fisch', 'Roher Honig',
    'Obst', 'Gemüse', 'Kokosnuss', 'Avocado'
  ];
  const BGS = {
    wald: 'Wald (Abend)',
    tag: 'Wald (Tag)',
    nacht: 'Wald (Nacht)',
    schlicht: 'Einfarbig'
  };

  let S = { lists: [] };
  let view = null;
  let bg = 'wald';
  let ms = null;
  let ren = false;
  let delId = '';
  let sgY = 0;
  let sgT = 0;
  let sgo = false;
  let animNext = true;
  let menuIn = false;
  let adding = false;
  let newId = '';
  let img = '';
  let closeTimer = null;
  let removingIds = new Set();

  const $ = (id) => document.getElementById(id);
  const app = $('app');

  function esc(s) {
    const d = document.createElement('div');
    d.textContent = String(s ?? '');
    return d.innerHTML;
  }

  function uid() {
    return `${Date.now()}-${Math.floor(Math.random() * 10000)}`;
  }

  function cur() {
    return S.lists.find((l) => l.id === view) || null;
  }

  function store() {
    try {
      localStorage.setItem(KEY, JSON.stringify(S));
    } catch (_) {}
  }

  function load() {
    try {
      const raw = localStorage.getItem(KEY);
      if (raw) {
        S = JSON.parse(raw);
      } else {
        const oldRaw = localStorage.getItem(OLD);
        const parsedOld = oldRaw ? JSON.parse(oldRaw) : [];
        const items = Array.isArray(parsedOld)
          ? parsedOld.map((i) => ({
              id: String(i.id ?? uid()),
              t: String(i.t ?? i.text ?? ''),
              d: Boolean(i.d ?? i.done)
            })).filter((i) => i.t)
          : [];
        S = { lists: [{ id: uid(), name: 'Meine Liste 1', items }] };
      }
    } catch (_) {
      S = { lists: [] };
    }

    if (!S || !Array.isArray(S.lists)) S = { lists: [] };
    S.lists = S.lists.map((l) => ({
      id: String(l.id || uid()),
      name: String(l.name || 'Unbenannte Liste'),
      items: Array.isArray(l.items) ? l.items : []
    }));
    if (!S.lists.length) {
      S.lists.push({ id: uid(), name: 'Meine Liste 1', items: [] });
    }

    try {
      const savedBg = localStorage.getItem(BGK);
      if (savedBg && (BGS[savedBg] || savedBg === 'eigen')) bg = savedBg;
      img = localStorage.getItem(IMGK) || '';
    } catch (_) {}

    if (bg === 'eigen' && !img) bg = 'wald';
    if (img) $('bgi').style.backgroundImage = `url("${img.replace(/"/g, '%22')}")`;
    document.body.setAttribute('data-bg', bg);

    try {
      const savedView = localStorage.getItem(VK);
      if (savedView && S.lists.some((x) => x.id === savedView)) {
        view = savedView;
      }
    } catch (_) {}
  }

  function setBg(k) {
    if (!BGS[k] && k !== 'eigen') return;
    bg = k;
    document.body.setAttribute('data-bg', bg);
    try {
      localStorage.setItem(BGK, bg);
    } catch (_) {}
  }

  function pick(file) {
    if (!file) return;
    const reader = new FileReader();
    reader.onload = () => {
      const im = new Image();
      im.onload = () => {
        const scale = Math.min(1, 1280 / Math.max(im.width, im.height));
        const canvas = document.createElement('canvas');
        canvas.width = Math.round(im.width * scale);
        canvas.height = Math.round(im.height * scale);
        const ctx = canvas.getContext('2d');
        ctx.drawImage(im, 0, 0, canvas.width, canvas.height);
        img = canvas.toDataURL('image/jpeg', 0.8);
        try {
          localStorage.setItem(IMGK, img);
        } catch (_) {}
        $('bgi').style.backgroundImage = `url("${img}")`;
        setBg('eigen');
        closeMenu();
      };
      im.src = reader.result;
    };
    reader.readAsDataURL(file);
  }

  function menu(inListView) {
    const pop = menuIn;
    menuIn = false;
    const bk = (to) => `<button type="button" class="bk" data-ms="${to}">‹ Zurück</button>`;
    let body = '';

    if (ms === 'main') {
      if (inListView) {
        body += `<button type="button" data-ms="name">Name der Liste</button>`;
        body += `<button type="button" data-m="back">Alle Listen</button>`;
      }
      body += `<button type="button" data-ms="bg">Hintergrund ›</button>`;
      body += `<button type="button" data-ms="imp">Impressum</button>`;
      body += `<button type="button" data-ms="fb">Feedback geben</button>`;
      body += `<button type="button" data-ms="del" style="color:var(--dg)">Liste löschen</button>`;
    } else if (ms === 'name') {
      body += `${bk('main')}<div class="sub"><input type="text" id="rni" autocomplete="off"><button type="button" id="rns">OK</button></div>`;
    } else if (ms === 'new') {
      body += `${bk('main')}<form id="nf" class="sub"><input type="text" id="nn" placeholder="Name der Liste …" autocomplete="off"><button type="submit">OK</button></form>`;
    } else if (ms === 'bg') {
      body += bk('main');
      body += Object.keys(BGS)
        .map((k) => `<button type="button" data-bg="${k}">${bg === k ? '✓ ' : ''}${esc(BGS[k])}</button>`)
        .join('');
      if (img) {
        body += `<button type="button" data-bg="eigen">${bg === 'eigen' ? '✓ ' : ''}Eigenes Foto</button>`;
      }
      body += `<button type="button" class="plus" data-ms="add">+ Foto hinzufügen</button>`;
    } else if (ms === 'add') {
      body += `${bk('bg')}<h2>Foto hinzufügen</h2><button type="button" data-m="gal">Aus Galerie auswählen</button><button type="button" data-m="cam">Kamera öffnen</button>`;
    } else if (ms === 'imp') {
      body += `${bk('main')}<h2>Impressum</h2><div class="txt">Unterschlupf – Einkaufsliste<br>Max Mustermann<br>Musterstraße 1<br>12345 Musterstadt<br>kontakt@unterschlupf.example<br><br>Platzhalter, keine rechtlich gültige Angabe.</div>`;
    } else if (ms === 'fb') {
      body += `${bk('main')}<h2>Verbesserungsvorschläge</h2><textarea id="fbt" placeholder="Was soll besser werden?"></textarea><button type="button" id="fbs" style="background:var(--ac);color:var(--ac-tx);text-align:center;font-weight:600">Senden</button>`;
    } else if (ms === 'fbok') {
      body += `${bk('main')}<h2>Danke!</h2><div class="txt">Dein Feedback wurde lokal gespeichert.</div>`;
    } else if (ms === 'del') {
      body += `${bk('main')}<h2>Welche Liste löschen?</h2>`;
      body += S.lists
        .map((x) => `<button type="button" data-dl="${esc(x.id)}">${esc(x.name)}</button>`)
        .join('');
    } else if (ms === 'delc') {
      const target = S.lists.find((x) => x.id === delId);
      body += `${bk('del')}<h2>Liste löschen</h2><div style="padding:6px 12px">„${esc(target ? target.name : '')}“ wirklich löschen?</div><button type="button" data-dc="${esc(delId)}" style="color:var(--dg);font-weight:600">Ja, löschen</button>`;
    }

    return `<div class="menu${pop ? ' pop' : ''}" id="mn"${ms ? '' : ' hidden'}>${body}</div>`;
  }

  function closeMenu(fn) {
    clearTimeout(closeTimer);
    const m = $('mn');
    const done = () => {
      ms = null;
      if (typeof fn === 'function') fn();
      render();
    };
    if (m && ms) {
      m.classList.add('closing');
      closeTimer = setTimeout(done, 190);
    } else {
      done();
    }
  }

  function sgSet(open) {
    const el = $('sg');
    if (el) el.classList.toggle('open', Boolean(open));
  }

  function updFoot(l) {
    const openCount = l.items.filter((i) => !i.d).length;
    const el = document.querySelector('.foot span');
    if (el) el.textContent = `${openCount} offen · ${l.items.length - openCount} erledigt`;
  }

  function sg() {
    const inp = $('in');
    const chipsEl = $('ch');
    if (!inp || !chipsEl) return;
    const q = inp.value.trim().toLowerCase();
    chipsEl.innerHTML = QUICK
      .filter((item) => item.toLowerCase().includes(q))
      .map((item) => `<button type="button" class="sec" data-q="${esc(item)}">+ ${esc(item)}</button>`)
      .join('');
  }

  function add(text) {
    const l = cur();
    const clean = String(text || '').trim();
    if (!l || !clean) return;
    const item = { id: uid(), t: clean, d: false };
    l.items.unshift(item);
    newId = item.id;
    store();
    render();
    newId = '';
  }

  function home() {
    sgo = false;
    ren = false;
    let h = `<div class="top cave"><button type="button" class="sec" id="mb" aria-label="Menü">☰</button><h1>Unterschlupf</h1></div>${menu(false)}`;
    h += adding
      ? `<form id="nf" class="card" style="display:flex;gap:8px;padding:10px"><input type="text" id="nn" placeholder="Name der Liste …" autocomplete="off"><button type="submit">OK</button></form>`
      : `<button type="button" class="addl" id="pl" aria-label="Neue Liste">+</button>`;
    h += S.lists
      .map((l) => {
        const openCount = l.items.filter((i) => !i.d).length;
        return `<button type="button" class="lst" data-open="${esc(l.id)}"><span>${esc(l.name)}</span><small>${openCount} offen ›</small></button>`;
      })
      .join('');
    app.innerHTML = h;
  }

  function listView() {
    const l = cur();
    if (!l) {
      view = null;
      return home();
    }

    const visibleItems = l.items.filter((i) => !removingIds.has(i.id));
    let h = `<div class="top"><button type="button" class="sec" id="bk" data-m="back" aria-label="Zurück">‹</button><button type="button" class="sec" id="mb" aria-label="Menü">☰</button>`;
    h += ren
      ? `<form id="rf" class="sub" style="flex:1;padding:0"><input type="text" id="rt" autocomplete="off"><button type="submit">OK</button></form>`
      : `<h1 id="tt" style="cursor:pointer" title="Tippen zum Umbenennen">${esc(l.name)}</h1>`;
    h += `</div>${menu(true)}`;

    h += `<div class="card add"><h2>Produkte hinzufügen</h2><form id="f"><input type="text" id="in" placeholder="Suchen oder hinzufügen …" autocomplete="off" enterkeyhint="done"><button type="submit" aria-label="Hinzufügen">+</button></form>`;
    h += `<div id="sg"><div><div class="chips" id="ch"></div><p class="note">Grundlebensmittel der Primal Diet. Bei rohen tierischen Produkten auf Frische und Herkunft achten.</p></div></div></div>`;

    h += `<div class="card"><h2>Auf der Liste</h2>`;
    h += visibleItems.length
      ? visibleItems
          .map(
            (i) =>
              `<div class="item${i.d ? ' done' : ''}${i.id === newId ? ' new' : ''}" data-row="${esc(i.id)}"><input type="checkbox" data-c="${esc(i.id)}"${i.d ? ' checked' : ''}><span>${esc(i.t)}</span><button type="button" class="x" data-x="${esc(i.id)}" aria-label="Löschen">×</button></div>`
          )
          .join('')
      : `<div class="empty">Noch nichts auf der Liste.</div>`;

    const openCount = l.items.filter((i) => !i.d).length;
    h += `<div class="foot"><span>${openCount} offen · ${l.items.length - openCount} erledigt</span><button type="button" class="sec" id="clr">Erledigte löschen</button></div></div>`;

    app.innerHTML = h;
    if ($('rni')) $('rni').value = l.name;
    if ($('rt')) {
      $('rt').value = l.name;
      $('rt').focus();
    }
    if (sgo) {
      sg();
      sgSet(true);
    }
  }

  function render() {
    clearTimeout(closeTimer);
    if (view) listView();
    else home();

    try {
      localStorage.setItem(VK, view || '');
    } catch (_) {}

    if (animNext) {
      animNext = false;
      app.classList.remove('enter');
      void app.offsetWidth;
      app.classList.add('enter');
    }
  }

  app.addEventListener('focusin', (e) => {
    if (e.target.id === 'in') {
      sgo = true;
      sgY = window.scrollY;
      sgT = Date.now();
      sg();
      sgSet(true);
    }
  });

  window.addEventListener(
    'scroll',
    () => {
      if (!sgo || Date.now() - sgT < 500 || Math.abs(window.scrollY - sgY) < 30) return;
      sgo = false;
      sgSet(false);
      const active = document.activeElement;
      if (active && active.id === 'in') active.blur();
    },
    { passive: true }
  );

  app.addEventListener('input', (e) => {
    if (e.target.id === 'in') sg();
  });

  app.addEventListener('submit', (e) => {
    e.preventDefault();
    if (e.target.id === 'f') {
      const inp = $('in');
      if (inp) {
        add(inp.value);
        const nextInp = $('in');
        if (nextInp) nextInp.focus();
      }
      return;
    }
    if (e.target.id === 'rf') {
      const l2 = cur();
      const n2 = $('rt').value.trim();
      if (l2 && n2) {
        l2.name = n2;
        store();
      }
      ren = false;
      render();
      return;
    }
    if (e.target.id === 'nf') {
      const nameVal = $('nn').value.trim() || `Meine Liste ${S.lists.length + 1}`;
      const created = { id: uid(), name: nameVal, items: [] };
      S.lists.push(created);
      store();
      view = created.id;
      adding = false;
      animNext = true;
      closeMenu();
    }
  });

  app.addEventListener('click', (e) => {
    const t = e.target;
    const l = cur();

    if (t.id === 'pl') {
      adding = true;
      ms = null;
      render();
      const n0 = $('nn');
      if (n0) n0.focus();
      return;
    }
    if (adding && !view && !t.closest('#nf')) {
      adding = false;
      render();
    }
    if (t.closest('#tt')) {
      ren = true;
      ms = null;
      render();
      return;
    }
    if (ren && !t.closest('#rf')) {
      ren = false;
      render();
    }
    if (l && !t.closest('.add')) {
      sgo = false;
      sgSet(false);
    }

    const ds = t.closest('[data-ms]');
    if (ds) {
      ms = ds.getAttribute('data-ms');
      render();
      const focusTarget = $('rni') || $('nn') || $('fbt');
      if (focusTarget) focusTarget.focus();
      return;
    }

    const bt = t.closest('button[data-bg]');
    if (bt) {
      setBg(bt.getAttribute('data-bg'));
      closeMenu();
      return;
    }

    const dl = t.closest('[data-dl]');
    if (dl) {
      delId = dl.getAttribute('data-dl');
      ms = 'delc';
      render();
      return;
    }

    const dc = t.closest('[data-dc]');
    if (dc) {
      const did = dc.getAttribute('data-dc');
      S.lists = S.lists.filter((z) => z.id !== did);
      if (!S.lists.length) {
        S.lists.push({ id: uid(), name: 'Meine Liste 1', items: [] });
      }
      if (view === did) {
        view = null;
        animNext = true;
      }
      store();
      closeMenu();
      return;
    }

    const op = t.closest('[data-open]');
    if (op) {
      view = op.getAttribute('data-open');
      ms = null;
      animNext = true;
      render();
      return;
    }

    if (t.id === 'mb') {
      if (ms) closeMenu();
      else {
        ms = 'main';
        menuIn = true;
        render();
      }
      return;
    }

    if (t.id === 'fbs') {
      const tx = $('fbt').value.trim();
      if (tx) {
        try {
          const fa = JSON.parse(localStorage.getItem(FBK) || '[]');
          fa.push({ t: tx, d: new Date().toISOString() });
          localStorage.setItem(FBK, JSON.stringify(fa));
        } catch (_) {}
        ms = 'fbok';
        render();
      }
      return;
    }

    const mEl = t.closest('[data-m]');
    const m = mEl ? mEl.getAttribute('data-m') : null;
    if (m === 'gal') {
      $('fg').click();
      return;
    }
    if (m === 'cam') {
      $('fc').click();
      return;
    }
    if (m === 'back') {
      view = null;
      ms = null;
      animNext = true;
      render();
      return;
    }

    if (!l) return;

    if (t.id === 'rns') {
      const nn = $('rni').value.trim();
      if (nn) {
        l.name = nn;
        store();
        closeMenu();
      }
      return;
    }

    if (t.id === 'clr') {
      const doneIds = l.items.filter((i) => i.d).map((i) => i.id);
      if (!doneIds.length) return;
      doneIds.forEach((id) => {
        removingIds.add(id);
        const row = app.querySelector(`[data-row="${CSS.escape(id)}"]`);
        if (row) row.classList.add('rm');
      });
      l.items = l.items.filter((i) => !i.d);
      store();
      updFoot(l);
      setTimeout(() => {
        doneIds.forEach((id) => removingIds.delete(id));
        if (cur()?.id === l.id) render();
      }, 320);
      return;
    }

    const qEl = t.closest('[data-q]');
    if (qEl) {
      add(qEl.getAttribute('data-q'));
      return;
    }

    const cEl = t.closest('[data-c]');
    if (cEl) {
      const cid = cEl.getAttribute('data-c');
      let nowDone = false;
      l.items.forEach((item) => {
        if (item.id === cid) {
          item.d = !item.d;
          nowDone = item.d;
        }
      });
      store();
      const row = t.closest('.item');
      if (row) row.classList.toggle('done', nowDone);
      updFoot(l);
      return;
    }

    const xEl = t.closest('[data-x]');
    if (xEl) {
      const xid = xEl.getAttribute('data-x');
      removingIds.add(xid);
      const rw = t.closest('.item');
      if (rw) rw.classList.add('rm');
      l.items = l.items.filter((item) => item.id !== xid);
      store();
      updFoot(l);
      setTimeout(() => {
        removingIds.delete(xid);
        if (cur()?.id === l.id) render();
      }, 320);
    }
  });

  $('fg').onchange = $('fc').onchange = function () {
    pick(this.files[0]);
    this.value = '';
  };

  load();
  render();
})();
</script>
</body>
</html>
