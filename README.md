[einheitenkonverter-adsense.html](https://github.com/user-attachments/files/28458266/einheitenkonverter-adsense.html)
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Einheitenkonverter – Alle Einheiten kostenlos umrechnen</title>
<meta name="description" content="Kostenloser Einheitenkonverter mit über 200 Einheiten: Länge, Gewicht, Temperatur, Fläche, Volumen, Energie, Druck, Datenmenge und mehr.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg:       #F4F3F0;
  --surface:  #FFFFFF;
  --surface2: #EDECEA;
  --ink:      #18181B;
  --muted:    #71717A;
  --faint:    #D4D4D8;
  --border:   #E4E4E7;
  --accent:   #18181B;
  --accent-light: #F4F3F0;
  --green:    #166534;
  --green-bg: #F0FDF4;
  --mono:     'JetBrains Mono', monospace;
  --sans:     'Inter', system-ui, sans-serif;
  --sidebar:  220px;
}

html, body { height: 100%; }
body {
  font-family: var(--sans);
  background: var(--bg);
  color: var(--ink);
  font-size: 14px;
  line-height: 1.5;
  display: flex;
  flex-direction: column;
  height: 100vh;
  overflow: hidden;
}

/* ── Top bar ── */
.topbar {
  height: 48px;
  background: var(--surface);
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  padding: 0 1.5rem;
  gap: 2rem;
  flex-shrink: 0;
}
.brand {
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.01em;
  color: var(--ink);
  white-space: nowrap;
}
.brand-sub {
  font-size: 12px;
  color: var(--muted);
  font-family: var(--mono);
}
/* ── Body layout ── */
.layout {
  display: flex;
  flex: 1;
  overflow: hidden;
}

/* ── Sidebar ── */
.sidebar {
  width: var(--sidebar);
  background: var(--surface);
  border-right: 1px solid var(--border);
  overflow-y: auto;
  flex-shrink: 0;
  padding: 1rem 0;
}
.sidebar-section {
  padding: 0 0.75rem;
  margin-bottom: 0.25rem;
}
.sidebar-label {
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--faint);
  padding: 0.5rem 0.5rem 0.3rem;
  display: block;
}
.cat-btn {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  padding: 0.45rem 0.65rem;
  border: none;
  background: none;
  cursor: pointer;
  text-align: left;
  color: var(--muted);
  font-family: var(--sans);
  font-size: 13px;
  border-radius: 5px;
  transition: all 0.1s;
  gap: 0.5rem;
}
.cat-btn:hover { background: var(--surface2); color: var(--ink); }
.cat-btn.active { background: var(--ink); color: #fff; }
.cat-btn.active .cat-n { color: #fff; }
.cat-n { flex: 1; }
.cat-c {
  font-family: var(--mono);
  font-size: 10px;
  color: var(--faint);
  background: var(--surface2);
  padding: 1px 5px;
  border-radius: 3px;
  flex-shrink: 0;
}
.cat-btn.active .cat-c { background: rgba(255,255,255,0.15); color: rgba(255,255,255,0.6); }

/* ── Main ── */
.main {
  flex: 1;
  overflow-y: auto;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

/* ── Main grid ── */
.content-grid {
  display: grid;
  grid-template-columns: 1fr 200px;
  gap: 1rem;
  align-items: start;
}
@media (max-width: 860px) { .content-grid { grid-template-columns: 1fr; } }

/* ── Card ── */
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  overflow: visible;
}

/* ── Card header ── */
.card-head {
  padding: 1rem 1.25rem 0.875rem;
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: baseline;
  gap: 0.75rem;
}
.card-title { font-size: 15px; font-weight: 500; }
.card-meta {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--muted);
}

/* ── Unit selectors ── */
.selectors {
  display: grid;
  grid-template-columns: 1fr 44px 1fr;
  gap: 0;
  border-bottom: 1px solid var(--border);
}
@media (max-width: 560px) { .selectors { grid-template-columns: 1fr; } }

.sel-col {
  padding: 1rem 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
.sel-col:first-child { border-right: 1px solid var(--border); }
.sel-col:last-child  { border-left: 1px solid var(--border); }

.sel-label {
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--muted);
}

.search-wrap { position: relative; }
.sel-input {
  width: 100%;
  padding: 0.5rem 0.75rem;
  border: 1px solid var(--border);
  border-radius: 5px;
  background: var(--bg);
  font-family: var(--sans);
  font-size: 13px;
  color: var(--ink);
  outline: none;
  transition: border-color 0.12s;
}
.sel-input:focus { border-color: var(--ink); }

.dropdown {
  position: absolute;
  top: calc(100% + 3px);
  left: 0; right: 0;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 6px;
  box-shadow: 0 8px 24px rgba(0,0,0,0.08);
  max-height: 220px;
  overflow-y: auto;
  display: none;
  z-index: 100;
}
.dropdown.open { display: block; }

.dd-group-label {
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.07em;
  text-transform: uppercase;
  color: var(--faint);
  padding: 0.5rem 0.75rem 0.25rem;
  border-top: 1px solid var(--border);
}
.dd-group-label:first-child { border-top: none; }

.dd-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.45rem 0.75rem;
  cursor: pointer;
  font-size: 13px;
  gap: 0.5rem;
  transition: background 0.08s;
}
.dd-item:hover, .dd-item.sel { background: var(--surface2); }
.dd-item.sel { font-weight: 500; color: var(--ink); }
.dd-sym {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--faint);
  flex-shrink: 0;
}
.dd-item.sel .dd-sym { color: var(--muted); }
.dd-empty {
  padding: 0.6rem 0.75rem;
  font-size: 12px;
  color: var(--muted);
  font-style: italic;
}

/* Swap button column */
.swap-col {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  padding-bottom: 1.05rem;
}
.swap-btn {
  width: 32px; height: 32px;
  border: 1px solid var(--border);
  border-radius: 50%;
  background: var(--surface);
  cursor: pointer;
  font-size: 14px;
  color: var(--muted);
  display: flex; align-items: center; justify-content: center;
  transition: all 0.15s;
  font-family: var(--mono);
}
.swap-btn:hover { border-color: var(--ink); color: var(--ink); }

/* ── Value row ── */
.values {
  display: grid;
  grid-template-columns: 1fr 32px 1fr;
  gap: 0;
  padding: 1.25rem;
  align-items: center;
  border-bottom: 1px solid var(--border);
}
@media (max-width: 560px) { .values { grid-template-columns: 1fr; gap: 0.5rem; } }

.val-wrap { display: flex; flex-direction: column; gap: 0.3rem; }
.val-lbl {
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.07em;
  text-transform: uppercase;
  color: var(--muted);
  font-family: var(--mono);
}
.val-input {
  width: 100%;
  padding: 0.6rem 0.85rem;
  border: 1px solid var(--border);
  border-radius: 5px;
  background: var(--bg);
  font-family: var(--mono);
  font-size: 20px;
  font-weight: 500;
  color: var(--ink);
  outline: none;
  transition: border-color 0.12s;
}
.val-input:focus { border-color: var(--ink); }
.val-result {
  width: 100%;
  padding: 0.6rem 0.85rem;
  border: 1px solid var(--green-bg);
  border-radius: 5px;
  background: var(--green-bg);
  font-family: var(--mono);
  font-size: 20px;
  font-weight: 500;
  color: var(--green);
  outline: none;
  cursor: default;
}
.eq-sign {
  text-align: center;
  font-family: var(--mono);
  font-size: 18px;
  color: var(--faint);
  line-height: 1;
  padding-top: 20px;
}
@media (max-width: 560px) { .eq-sign { display: none; } }

/* ── Formula ── */
.formula {
  padding: 0.65rem 1.25rem;
  font-family: var(--mono);
  font-size: 12px;
  color: var(--muted);
  border-bottom: 1px solid var(--border);
  min-height: 38px;
  display: flex;
  align-items: center;
}

/* ── Quick refs ── */
.quick {
  padding: 1rem 1.25rem;
}
.quick-head {
  font-size: 10px;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--faint);
  margin-bottom: 0.6rem;
}
.quick-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
  gap: 4px;
}
.quick-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.35rem 0.6rem;
  border-radius: 4px;
  cursor: pointer;
  background: var(--bg);
  transition: background 0.1s;
  gap: 0.5rem;
}
.quick-item:hover { background: var(--surface2); }
.q-from { font-family: var(--mono); font-size: 11px; color: var(--muted); }
.q-to   { font-family: var(--mono); font-size: 11px; color: var(--green); font-weight: 500; }

/* ── Right sidebar ── */
.right-col { display: flex; flex-direction: column; gap: 1rem; }
.info-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 1rem;
}
.info-card h3 { font-size: 12px; font-weight: 500; margin-bottom: 0.4rem; }
.info-card p  { font-size: 12px; color: var(--muted); line-height: 1.6; }

/* ── Footer ── */
.footer {
  background: var(--surface);
  border-top: 1px solid var(--border);
  padding: 0.6rem 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 11px;
  color: var(--muted);
  flex-shrink: 0;
}
.footer a { color: var(--muted); text-decoration: none; }
.footer a:hover { color: var(--ink); }

/* ── Mobile sidebar collapse ── */
@media (max-width: 700px) {
  .sidebar { width: 140px; }
  .cat-c   { display: none; }
}
@media (max-width: 520px) {
  .sidebar { display: none; }
}
</style>
</head>
<body>

<!-- Top bar -->
<div class="topbar">
  <span class="brand">Einheitenkonverter</span>
  <span class="brand-sub">220+ Einheiten · 15 Kategorien</span>
</div>

<div class="layout">

  <!-- Sidebar -->
  <nav class="sidebar">
    <div class="sidebar-section">
      <span class="sidebar-label">Grundmaße</span>
      <button class="cat-btn active" data-cat="laenge"><span class="cat-n">Länge</span><span class="cat-c">30</span></button>
      <button class="cat-btn" data-cat="masse"><span class="cat-n">Masse</span><span class="cat-c">24</span></button>
      <button class="cat-btn" data-cat="volumen"><span class="cat-n">Volumen</span><span class="cat-c">28</span></button>
      <button class="cat-btn" data-cat="flaeche"><span class="cat-n">Fläche</span><span class="cat-c">20</span></button>
      <button class="cat-btn" data-cat="temperatur"><span class="cat-n">Temperatur</span><span class="cat-c">4</span></button>
      <button class="cat-btn" data-cat="zeit"><span class="cat-n">Zeit</span><span class="cat-c">16</span></button>
    </div>
    <div class="sidebar-section">
      <span class="sidebar-label">Mechanik</span>
      <button class="cat-btn" data-cat="geschwindigkeit"><span class="cat-n">Geschwindigkeit</span><span class="cat-c">14</span></button>
      <button class="cat-btn" data-cat="beschleunigung"><span class="cat-n">Beschleunigung</span><span class="cat-c">8</span></button>
      <button class="cat-btn" data-cat="kraft"><span class="cat-n">Kraft</span><span class="cat-c">12</span></button>
      <button class="cat-btn" data-cat="druck"><span class="cat-n">Druck</span><span class="cat-c">16</span></button>
      <button class="cat-btn" data-cat="energie"><span class="cat-n">Energie</span><span class="cat-c">18</span></button>
      <button class="cat-btn" data-cat="leistung"><span class="cat-n">Leistung / PS</span><span class="cat-c">10</span></button>
    </div>
    <div class="sidebar-section">
      <span class="sidebar-label">Digital & Winkel</span>
      <button class="cat-btn" data-cat="datenmenge"><span class="cat-n">Datenmenge</span><span class="cat-c">16</span></button>
      <button class="cat-btn" data-cat="winkel"><span class="cat-n">Winkel</span><span class="cat-c">8</span></button>
      <button class="cat-btn" data-cat="frequenz"><span class="cat-n">Frequenz</span><span class="cat-c">10</span></button>
    </div>
  </nav>

  <!-- Main content -->
  <main class="main">

    <div class="content-grid">

      <!-- Converter -->
      <div class="card">

        <!-- Header -->
        <div class="card-head">
          <span class="card-title" id="cat-title">Länge</span>
          <span class="card-meta" id="cat-meta">30 Einheiten verfügbar</span>
        </div>

        <!-- Unit selectors -->
        <div class="selectors">
          <div class="sel-col">
            <span class="sel-label">Von</span>
            <div class="search-wrap" id="wrap-from">
              <input class="sel-input" id="srch-from" placeholder="Einheit suchen …" autocomplete="off">
              <div class="dropdown" id="drop-from"></div>
            </div>
          </div>
          <div class="swap-col">
            <button class="swap-btn" id="swap-btn" title="Tauschen">⇄</button>
          </div>
          <div class="sel-col">
            <span class="sel-label">In</span>
            <div class="search-wrap" id="wrap-to">
              <input class="sel-input" id="srch-to" placeholder="Einheit suchen …" autocomplete="off">
              <div class="dropdown" id="drop-to"></div>
            </div>
          </div>
        </div>

        <!-- Values -->
        <div class="values">
          <div class="val-wrap">
            <span class="val-lbl" id="lbl-from">Meter</span>
            <input class="val-input" id="val-from" type="number" value="1">
          </div>
          <div class="eq-sign">=</div>
          <div class="val-wrap">
            <span class="val-lbl" id="lbl-to">Zoll</span>
            <input class="val-result" id="val-to" readonly>
          </div>
        </div>

        <!-- Formula -->
        <div class="formula" id="formula"></div>

        <!-- Quick refs -->
        <div class="quick">
          <div class="quick-head">Schnell-Referenz</div>
          <div class="quick-grid" id="quick-grid"></div>
        </div>

      </div><!-- /card -->

      <!-- Right column -->
      <div class="right-col">
        <div class="info-card">
          <h3 id="info-title">Länge umrechnen</h3>
          <p id="info-text">Alle gängigen Längenmaße auf einen Blick – von Angström bis Lichtjahr. Besonders gesucht: Zoll in cm für Bildschirmgrößen und Meilen in Kilometer.</p>
        </div>
      </div>

    </div><!-- /content-grid -->
  </main>

</div><!-- /layout -->

<div class="footer">
  <span>© 2025 Einheitenkonverter · Alle Angaben ohne Gewähr</span>
  <span><a href="#">Impressum</a> · <a href="#">Datenschutz</a></span>
</div>

<script>
// ═══════════════════════════════════════════════════
// DATA
// ═══════════════════════════════════════════════════
const CATS = {
  laenge: {
    title:"Länge", info:"Alle gängigen Längenmaße – von Angström bis Lichtjahr. Besonders gesucht: Zoll in cm für Bildschirmgrößen und Meilen in Kilometer.",
    base:"m",
    quick:[["1","in","cm"],["1","ft","cm"],["1","mi","km"],["1","yd","m"],["100","m","ft"],["1","nmi","km"]],
    groups:[
      { label:"Metrisch", units:[
        {k:"m",    n:"Meter",               s:"m",     f:1},
        {k:"km",   n:"Kilometer",           s:"km",    f:1e3},
        {k:"dm",   n:"Dezimeter",           s:"dm",    f:0.1},
        {k:"cm",   n:"Zentimeter",          s:"cm",    f:0.01},
        {k:"mm",   n:"Millimeter",          s:"mm",    f:1e-3},
        {k:"um",   n:"Mikrometer",          s:"μm",    f:1e-6},
        {k:"nm",   n:"Nanometer",           s:"nm",    f:1e-9},
        {k:"pm",   n:"Pikometer",           s:"pm",    f:1e-12},
        {k:"ang",  n:"Angström",            s:"Å",     f:1e-10},
      ]},
      { label:"Imperial / US", units:[
        {k:"in",   n:"Zoll (Inch)",         s:"in",    f:0.0254},
        {k:"ft",   n:"Fuß (Foot)",          s:"ft",    f:0.3048},
        {k:"yd",   n:"Yard",                s:"yd",    f:0.9144},
        {k:"mi",   n:"Meile (Mile)",        s:"mi",    f:1609.344},
        {k:"nmi",  n:"Seemeile",            s:"nmi",   f:1852},
        {k:"fur",  n:"Furlong",             s:"fur",   f:201.168},
        {k:"fath", n:"Faden (Fathom)",      s:"ftm",   f:1.8288},
        {k:"rod",  n:"Rod (Rute)",          s:"rd",    f:5.0292},
        {k:"ch",   n:"Chain",               s:"ch",    f:20.1168},
        {k:"lea",  n:"League",              s:"lea",   f:4828.032},
        {k:"hand", n:"Hand (Pferdemaß)",    s:"hand",  f:0.1016},
      ]},
      { label:"Astronomisch", units:[
        {k:"au",   n:"Astronomische Einheit",s:"AU",   f:1.496e11},
        {k:"ly",   n:"Lichtjahr",           s:"ly",    f:9.461e15},
        {k:"pc",   n:"Parsec",              s:"pc",    f:3.086e16},
      ]},
      { label:"Typografie", units:[
        {k:"pt",   n:"Punkt",               s:"pt",    f:0.000352778},
        {k:"pica", n:"Pica",                s:"pica",  f:0.00423333},
      ]},
      { label:"Historisch", units:[
        {k:"elle", n:"Elle (dt., ca.)",     s:"Elle",  f:0.6},
        {k:"cubit",n:"Cubit (Ellenbogen)",  s:"cubit", f:0.4572},
        {k:"span", n:"Span (Handspanne)",   s:"span",  f:0.2286},
        {k:"li",   n:"Li (chinesisch)",     s:"里",     f:500},
      ]},
    ]
  },

  masse: {
    title:"Masse / Gewicht", info:"Von Mikrogramm bis Tonne – alle Gewichtseinheiten weltweit. Besonders gesucht: Pfund in Kilogramm und Karat für Edelsteine.",
    base:"kg",
    quick:[["1","lb","kg"],["1","oz","g"],["1","st","kg"],["1","t","kg"],["100","kg","lb"],["1","ct","g"]],
    groups:[
      { label:"Metrisch", units:[
        {k:"kg",   n:"Kilogramm",           s:"kg",    f:1},
        {k:"g",    n:"Gramm",               s:"g",     f:1e-3},
        {k:"mg",   n:"Milligramm",          s:"mg",    f:1e-6},
        {k:"ug",   n:"Mikrogramm",          s:"μg",    f:1e-9},
        {k:"ng",   n:"Nanogramm",           s:"ng",    f:1e-12},
        {k:"t",    n:"Tonne (metrisch)",    s:"t",     f:1000},
        {k:"kt",   n:"Kilotonne",           s:"kt",    f:1e6},
        {k:"q",    n:"Quintal (metrisch)",  s:"q",     f:100},
      ]},
      { label:"Imperial / US", units:[
        {k:"lb",   n:"Pfund (Pound)",       s:"lb",    f:0.453592},
        {k:"oz",   n:"Unze (Ounce)",        s:"oz",    f:0.028349523},
        {k:"st",   n:"Stone (brit.)",       s:"st",    f:6.35029},
        {k:"lt",   n:"Long Ton (brit.)",    s:"lt",    f:1016.047},
        {k:"sh_t", n:"Short Ton (US)",      s:"sh t",  f:907.185},
        {k:"gr",   n:"Grain",               s:"gr",    f:6.47989e-5},
        {k:"dram", n:"Dram",                s:"dr",    f:1.7718e-3},
        {k:"pdl",  n:"Poundal",             s:"pdl",   f:0.138255},
      ]},
      { label:"Edelmetalle", units:[
        {k:"ct",   n:"Karat (Edelstein)",   s:"ct",    f:2e-4},
        {k:"ozt",  n:"Feinunze (Troy oz)",  s:"oz t",  f:0.031103},
        {k:"lbt",  n:"Troy Pound",          s:"lb t",  f:0.373242},
        {k:"dwt",  n:"Pennyweight",         s:"dwt",   f:1.5552e-3},
      ]},
      { label:"Historisch", units:[
        {k:"pfund",n:"Pfund (dt. alt)",     s:"Pfd.",  f:0.5},
        {k:"lot",  n:"Lot (dt. alt)",       s:"Lot",   f:0.015},
        {k:"atom", n:"Atomare Masseeinheit",s:"u",     f:1.66054e-27},
      ]},
    ]
  },

  volumen: {
    title:"Volumen", info:"Flüssigkeitsmaße für Kochen, Chemie und Technik. Gallone und Cup für US-Rezepte – Kubikmeter für Bau und Industrie.",
    base:"l",
    quick:[["1","gal_us","l"],["1","cup_us","ml"],["1","pt_us","l"],["1","fl_oz","ml"],["1","tbsp","ml"],["1","bbl","l"]],
    groups:[
      { label:"Metrisch", units:[
        {k:"l",    n:"Liter",               s:"l",     f:1},
        {k:"ml",   n:"Milliliter",          s:"ml",    f:1e-3},
        {k:"ul",   n:"Mikroliter",          s:"μl",    f:1e-6},
        {k:"cl",   n:"Centiliter",          s:"cl",    f:0.01},
        {k:"dl",   n:"Deziliter",           s:"dl",    f:0.1},
        {k:"hl",   n:"Hektoliter",          s:"hl",    f:100},
        {k:"m3",   n:"Kubikmeter",          s:"m³",    f:1000},
        {k:"cm3",  n:"Kubikzentimeter",     s:"cm³",   f:1e-3},
        {k:"mm3",  n:"Kubikmillimeter",     s:"mm³",   f:1e-6},
      ]},
      { label:"US-Maße", units:[
        {k:"gal_us",n:"Gallone (US)",       s:"gal",   f:3.78541},
        {k:"qt_us", n:"Quart (US)",         s:"qt",    f:0.946353},
        {k:"pt_us", n:"Pint (US)",          s:"pt",    f:0.473176},
        {k:"cup_us",n:"Cup (US)",           s:"cup",   f:0.236588},
        {k:"fl_oz", n:"Fluid Ounce (US)",   s:"fl oz", f:0.029574},
        {k:"tbsp",  n:"Esslöffel (US)",     s:"EL",    f:0.014787},
        {k:"tsp",   n:"Teelöffel (US)",     s:"TL",    f:0.004929},
        {k:"bbl",   n:"Barrel (Öl, US)",    s:"bbl",   f:158.987},
      ]},
      { label:"Britisch", units:[
        {k:"gal_uk",n:"Gallone (UK)",       s:"gal UK",f:4.54609},
        {k:"qt_uk", n:"Quart (UK)",         s:"qt UK", f:1.13652},
        {k:"pt_uk", n:"Pint (UK)",          s:"pt UK", f:0.568261},
        {k:"cup_uk",n:"Cup (UK)",           s:"cup UK",f:0.284131},
        {k:"fl_oz_uk",n:"Fluid Ounce (UK)", s:"fl oz UK",f:0.028413},
      ]},
      { label:"Imperial", units:[
        {k:"ft3",  n:"Kubikfuß",            s:"ft³",   f:28.3168},
        {k:"in3",  n:"Kubikzoll",           s:"in³",   f:0.016387},
        {k:"yd3",  n:"Kubikyard",           s:"yd³",   f:764.555},
      ]},
      { label:"Sonstige", units:[
        {k:"shot", n:"Shot (Schnaps, 4 cl)",s:"shot",  f:0.04},
        {k:"cord", n:"Cord (Holzmaß)",      s:"cord",  f:3624.56},
      ]},
    ]
  },

  flaeche: {
    title:"Fläche", info:"Flächenmaße für Grundstücke und Landkarten. Hektar und Morgen für Agrar- und Immobilienflächen, Acre für internationale Vergleiche.",
    base:"m2",
    quick:[["1","ha","m2"],["1","acre","m2"],["1","km2","ha"],["1","ft2","m2"],["1","morgen","ha"],["1","mi2","km2"]],
    groups:[
      { label:"Metrisch", units:[
        {k:"m2",  n:"Quadratmeter",         s:"m²",    f:1},
        {k:"km2", n:"Quadratkilometer",     s:"km²",   f:1e6},
        {k:"dm2", n:"Quadratdezimeter",     s:"dm²",   f:0.01},
        {k:"cm2", n:"Quadratzentimeter",    s:"cm²",   f:1e-4},
        {k:"mm2", n:"Quadratmillimeter",    s:"mm²",   f:1e-6},
        {k:"ha",  n:"Hektar",              s:"ha",    f:1e4},
        {k:"a",   n:"Ar",                  s:"a",     f:100},
      ]},
      { label:"Agrar (deutsch)", units:[
        {k:"morgen",n:"Morgen (dt.)",       s:"Morgen",f:2500},
        {k:"joch", n:"Joch (österr.)",      s:"Joch",  f:5754.64},
        {k:"tagw", n:"Tagwerk (bay.)",      s:"Tagw.", f:3407.23},
      ]},
      { label:"Imperial / US", units:[
        {k:"acre", n:"Acre",               s:"ac",    f:4046.86},
        {k:"ft2",  n:"Quadratfuß",         s:"ft²",   f:0.092903},
        {k:"in2",  n:"Quadratzoll",        s:"in²",   f:6.4516e-4},
        {k:"yd2",  n:"Quadratyard",        s:"yd²",   f:0.836127},
        {k:"mi2",  n:"Quadratmeile",       s:"mi²",   f:2.58999e6},
        {k:"rod2", n:"Quadrat-Rod",        s:"rd²",   f:25.2929},
      ]},
      { label:"Asiatisch", units:[
        {k:"tsu",  n:"Tsubo (Japan)",       s:"坪",     f:3.30579},
        {k:"tatami",n:"Tatami-Matte",       s:"畳",     f:1.6529},
        {k:"mu",   n:"Mu (China)",          s:"亩",     f:666.667},
      ]},
      { label:"Physik", units:[
        {k:"barn", n:"Barn (Kernphysik)",   s:"b",     f:1e-28},
      ]},
    ]
  },

  temperatur: {
    title:"Temperatur", info:"Celsius, Fahrenheit, Kelvin und Rankine. Wichtig: 0 °C = 32 °F = 273,15 K. Körpertemperatur = 37 °C = 98,6 °F.",
    isTemp:true,
    quick:[["100","C","F"],["37","C","F"],["0","C","F"],["-40","C","F"],["0","K","C"],["72","F","C"]],
    groups:[
      { label:"Alle Skalen", units:[
        {k:"C",  n:"Celsius",               s:"°C"},
        {k:"F",  n:"Fahrenheit",            s:"°F"},
        {k:"K",  n:"Kelvin",                s:"K"},
        {k:"R",  n:"Rankine",               s:"°R"},
      ]},
    ]
  },

  zeit: {
    title:"Zeit", info:"Von Nanosekunden bis Jahrtausenden. Nützlich für Physik, Projektplanung und Astronomie.",
    base:"s",
    quick:[["1","h","min"],["1","d","h"],["1","wk","d"],["1","yr","d"],["1","min","s"],["1","decade","yr"]],
    groups:[
      { label:"Klein", units:[
        {k:"ns",   n:"Nanosekunde",          s:"ns",    f:1e-9},
        {k:"us",   n:"Mikrosekunde",         s:"μs",    f:1e-6},
        {k:"ms",   n:"Millisekunde",         s:"ms",    f:1e-3},
        {k:"s",    n:"Sekunde",              s:"s",     f:1},
        {k:"min",  n:"Minute",               s:"min",   f:60},
        {k:"h",    n:"Stunde",               s:"h",     f:3600},
      ]},
      { label:"Groß", units:[
        {k:"d",    n:"Tag",                  s:"d",     f:86400},
        {k:"wk",   n:"Woche",               s:"Wo.",   f:604800},
        {k:"fn",   n:"Fortnight (2 Wochen)", s:"fn",    f:1209600},
        {k:"mo",   n:"Monat (Ø 30,44 Tage)",s:"Mo.",   f:2629800},
        {k:"yr",   n:"Jahr (365,25 Tage)",   s:"a",     f:31557600},
        {k:"decade",n:"Jahrzehnt",           s:"Dez.",  f:315576000},
        {k:"cent", n:"Jahrhundert",          s:"Jh.",   f:3155760000},
        {k:"millennium",n:"Jahrtausend",     s:"Jt.",   f:31557600000},
      ]},
      { label:"Physik", units:[
        {k:"shake",n:"Shake (Kernphysik)",   s:"shake", f:1e-8},
        {k:"jiffy",n:"Jiffy (Elektronik)",   s:"jiffy", f:0.01667},
      ]},
    ]
  },

  geschwindigkeit: {
    title:"Geschwindigkeit", info:"Von km/h und mph bis Mach und Lichtgeschwindigkeit. Wichtig für Reisen, Physik und Nautik.",
    base:"ms",
    quick:[["100","kmh","mph"],["60","mph","kmh"],["1","mach","kmh"],["30","kn","kmh"],["1","c","kmh"],["10","ms","kmh"]],
    groups:[
      { label:"Alltäglich", units:[
        {k:"ms",   n:"Meter pro Sekunde",    s:"m/s",   f:1},
        {k:"kmh",  n:"Kilometer pro Stunde", s:"km/h",  f:1/3.6},
        {k:"mph",  n:"Meilen pro Stunde",    s:"mph",   f:0.44704},
        {k:"fps",  n:"Fuß pro Sekunde",      s:"ft/s",  f:0.3048},
        {k:"fpm",  n:"Fuß pro Minute",       s:"ft/min",f:0.00508},
        {k:"kn",   n:"Knoten (Nautik)",      s:"kn",    f:0.51444},
        {k:"cms",  n:"Zentimeter pro Sekunde",s:"cm/s", f:0.01},
      ]},
      { label:"Physik", units:[
        {k:"mach", n:"Mach (Schall, 20 °C)", s:"Mach",  f:343},
        {k:"mach_h",n:"Mach (Schall, Höhe)", s:"Mach↑", f:295},
        {k:"c",    n:"Lichtgeschwindigkeit", s:"c",     f:299792458},
        {k:"kmmin",n:"Kilometer pro Minute", s:"km/min",f:16.6667},
        {k:"mps",  n:"Meile pro Sekunde",    s:"mi/s",  f:1609.344},
        {k:"ips",  n:"Inch pro Sekunde",     s:"in/s",  f:0.0254},
        {k:"mimin",n:"Meile pro Minute",     s:"mi/min",f:26.8224},
      ]},
    ]
  },

  beschleunigung: {
    title:"Beschleunigung", info:"Beschleunigungseinheiten für Physik und Luft- und Raumfahrt. 1 g = 9,80665 m/s² = Erdbeschleunigung.",
    base:"ms2",
    quick:[["1","g","ms2"],["9.81","ms2","g"],["1","gal","ms2"],["100","cms2","ms2"],["1","fts2","ms2"],["1","g","fts2"]],
    groups:[
      { label:"Alle", units:[
        {k:"ms2",  n:"Meter pro Sekunde²",   s:"m/s²",  f:1},
        {k:"cms2", n:"Zentimeter pro Sek.²", s:"cm/s²", f:0.01},
        {k:"fts2", n:"Fuß pro Sekunde²",     s:"ft/s²", f:0.3048},
        {k:"ins2", n:"Inch pro Sekunde²",    s:"in/s²", f:0.0254},
        {k:"g",    n:"g (Erdbeschleunigung)",s:"g",     f:9.80665},
        {k:"gal",  n:"Gal (Geodäsie)",       s:"Gal",   f:0.01},
        {k:"mgal", n:"Milligal",             s:"mGal",  f:1e-5},
        {k:"mph_s",n:"mph pro Sekunde",      s:"mph/s", f:0.44704},
      ]},
    ]
  },

  kraft: {
    title:"Kraft", info:"Krafteinheiten für Physik und Technik. Newton ist die SI-Einheit. Kilopond war in Deutschland bis 1977 gebräuchlich.",
    base:"N",
    quick:[["1","kN","N"],["1","lbf","N"],["1","kgf","N"],["100","N","kgf"],["1","dyn","N"],["1","MN","kN"]],
    groups:[
      { label:"Metrisch / SI", units:[
        {k:"N",    n:"Newton",               s:"N",     f:1},
        {k:"kN",   n:"Kilonewton",           s:"kN",    f:1000},
        {k:"MN",   n:"Meganewton",           s:"MN",    f:1e6},
        {k:"mN",   n:"Millinewton",          s:"mN",    f:1e-3},
        {k:"uN",   n:"Mikronewton",          s:"μN",    f:1e-6},
        {k:"kgf",  n:"Kilopond (kp)",        s:"kp",    f:9.80665},
        {k:"gf",   n:"Gramm-Kraft",          s:"gf",    f:0.00980665},
        {k:"tf",   n:"Tonnen-Kraft",         s:"tf",    f:9806.65},
      ]},
      { label:"Imperial / CGS", units:[
        {k:"lbf",  n:"Pound-Force",          s:"lbf",   f:4.44822},
        {k:"ozf",  n:"Ounce-Force",          s:"ozf",   f:0.278014},
        {k:"pdl",  n:"Poundal",              s:"pdl",   f:0.138255},
        {k:"dyn",  n:"Dyn (CGS)",            s:"dyn",   f:1e-5},
      ]},
    ]
  },

  druck: {
    title:"Druck", info:"Druckeinheiten für Technik, Meteorologie und Medizin. Bar und Pascal sind die gängigsten Einheiten in Europa.",
    base:"Pa",
    quick:[["1","bar","Pa"],["1","atm","bar"],["1","psi","bar"],["1013.25","hPa","atm"],["1","torr","Pa"],["1","mmhg","Pa"]],
    groups:[
      { label:"SI / Metrisch", units:[
        {k:"Pa",   n:"Pascal",               s:"Pa",    f:1},
        {k:"hPa",  n:"Hektopascal",          s:"hPa",   f:100},
        {k:"kPa",  n:"Kilopascal",           s:"kPa",   f:1000},
        {k:"MPa",  n:"Megapascal",           s:"MPa",   f:1e6},
        {k:"GPa",  n:"Gigapascal",           s:"GPa",   f:1e9},
        {k:"bar",  n:"Bar",                  s:"bar",   f:1e5},
        {k:"mbar", n:"Millibar",             s:"mbar",  f:100},
      ]},
      { label:"Technisch", units:[
        {k:"atm",  n:"Atmosphäre (atm)",     s:"atm",   f:101325},
        {k:"at",   n:"Techn. Atmosphäre",    s:"at",    f:98066.5},
        {k:"torr", n:"Torr",                 s:"Torr",  f:133.322},
        {k:"mmhg", n:"Millimeter Quecksilber",s:"mmHg", f:133.322},
        {k:"cmhg", n:"Zentimeter Hg",        s:"cmHg",  f:1333.22},
        {k:"inhg", n:"Inch Quecksilber",     s:"inHg",  f:3386.39},
        {k:"mmh2o",n:"Millimeter Wassersäule",s:"mmH₂O",f:9.80665},
      ]},
      { label:"US / Imperial", units:[
        {k:"psi",  n:"Pound pro Inch² (PSI)",s:"psi",   f:6894.76},
        {k:"ksi",  n:"Kilopound pro Inch²",  s:"ksi",   f:6894757},
      ]},
    ]
  },

  energie: {
    title:"Energie / Arbeit", info:"Energieeinheiten für Physik, Ernährung und Elektrizität. 1 kcal = 4,184 kJ – wichtig für Kalorienberechnungen.",
    base:"J",
    quick:[["1","kcal","kJ"],["1","kWh","MJ"],["1","eV","J"],["1","BTU","J"],["1","Wh","kJ"],["1","MJ","kWh"]],
    groups:[
      { label:"SI", units:[
        {k:"J",    n:"Joule",                s:"J",     f:1},
        {k:"kJ",   n:"Kilojoule",            s:"kJ",    f:1000},
        {k:"MJ",   n:"Megajoule",            s:"MJ",    f:1e6},
        {k:"GJ",   n:"Gigajoule",            s:"GJ",    f:1e9},
        {k:"mJ",   n:"Millijoule",           s:"mJ",    f:1e-3},
      ]},
      { label:"Elektrisch", units:[
        {k:"Wh",   n:"Wattstunde",           s:"Wh",    f:3600},
        {k:"kWh",  n:"Kilowattstunde",       s:"kWh",   f:3.6e6},
        {k:"MWh",  n:"Megawattstunde",       s:"MWh",   f:3.6e9},
        {k:"GWh",  n:"Gigawattstunde",       s:"GWh",   f:3.6e12},
      ]},
      { label:"Wärme / Ernährung", units:[
        {k:"cal",  n:"Kalorie (Physik)",     s:"cal",   f:4.1868},
        {k:"kcal", n:"Kilokalorie (kcal)",   s:"kcal",  f:4186.8},
        {k:"BTU",  n:"British Thermal Unit", s:"BTU",   f:1055.06},
        {k:"therm",n:"Therm (US)",           s:"therm", f:1.0551e8},
      ]},
      { label:"Physik", units:[
        {k:"eV",   n:"Elektronenvolt",       s:"eV",    f:1.60218e-19},
        {k:"keV",  n:"Kiloelektronenvolt",   s:"keV",   f:1.60218e-16},
        {k:"MeV",  n:"Megaelektronenvolt",   s:"MeV",   f:1.60218e-13},
        {k:"erg",  n:"Erg (CGS)",            s:"erg",   f:1e-7},
        {k:"ftlb", n:"Foot-Pound",           s:"ft·lbf",f:1.35582},
        {k:"tnt",  n:"Tonne TNT",            s:"t TNT", f:4.184e9},
      ]},
    ]
  },

  leistung: {
    title:"Leistung / PS", info:"PS in kW und zurück – am häufigsten für Motorleistungen gesucht. 1 PS = 0,7355 kW. 100 PS ≈ 73,6 kW.",
    base:"W",
    quick:[["100","PS","kW"],["200","PS","kW"],["75","kW","PS"],["1","hp","W"],["1","kW","PS"],["1","MW","PS"]],
    groups:[
      { label:"SI", units:[
        {k:"W",    n:"Watt",                 s:"W",     f:1},
        {k:"kW",   n:"Kilowatt",             s:"kW",    f:1000},
        {k:"MW",   n:"Megawatt",             s:"MW",    f:1e6},
        {k:"GW",   n:"Gigawatt",             s:"GW",    f:1e9},
        {k:"mW",   n:"Milliwatt",            s:"mW",    f:0.001},
      ]},
      { label:"Pferdestärken", units:[
        {k:"PS",   n:"Pferdestärke (PS)",    s:"PS",    f:735.499},
        {k:"hp",   n:"Horsepower (hp)",      s:"hp",    f:745.700},
        {k:"hp_e", n:"Elektrische HP",       s:"hp(E)", f:746},
        {k:"hp_b", n:"Boiler HP",            s:"hp(B)", f:9810.66},
      ]},
      { label:"Wärme", units:[
        {k:"BTUh", n:"BTU pro Stunde",       s:"BTU/h", f:0.293071},
        {k:"kcalh",n:"kcal pro Stunde",      s:"kcal/h",f:1.163},
      ]},
    ]
  },

  datenmenge: {
    title:"Datenmenge", info:"Byte, Kilobyte, Megabyte und mehr. Hinweis: 1 KB = 1000 Byte (SI/dezimal) vs. 1 KiB = 1024 Byte (binär).",
    base:"B",
    quick:[["1","GB","MB"],["1","TB","GB"],["1","GiB","GB"],["500","MB","GB"],["1","Mbit","MB"],["1","GB","Gbit"]],
    groups:[
      { label:"Dezimal (SI)", units:[
        {k:"B",    n:"Byte",                 s:"B",     f:1},
        {k:"KB",   n:"Kilobyte (1 000 B)",   s:"KB",    f:1e3},
        {k:"MB",   n:"Megabyte",             s:"MB",    f:1e6},
        {k:"GB",   n:"Gigabyte",             s:"GB",    f:1e9},
        {k:"TB",   n:"Terabyte",             s:"TB",    f:1e12},
        {k:"PB",   n:"Petabyte",             s:"PB",    f:1e15},
        {k:"EB",   n:"Exabyte",              s:"EB",    f:1e18},
      ]},
      { label:"Binär (IEC)", units:[
        {k:"KiB",  n:"Kibibyte (1 024 B)",   s:"KiB",   f:1024},
        {k:"MiB",  n:"Mebibyte",             s:"MiB",   f:1048576},
        {k:"GiB",  n:"Gibibyte",             s:"GiB",   f:1073741824},
        {k:"TiB",  n:"Tebibyte",             s:"TiB",   f:1.09951e12},
        {k:"PiB",  n:"Pebibyte",             s:"PiB",   f:1.12590e15},
      ]},
      { label:"Bits", units:[
        {k:"bit",  n:"Bit",                  s:"bit",   f:0.125},
        {k:"Kbit", n:"Kilobit",              s:"Kbit",  f:125},
        {k:"Mbit", n:"Megabit",              s:"Mbit",  f:125000},
        {k:"Gbit", n:"Gigabit",              s:"Gbit",  f:1.25e8},
        {k:"Tbit", n:"Terabit",              s:"Tbit",  f:1.25e11},
      ]},
    ]
  },

  winkel: {
    title:"Winkel", info:"Winkeleinheiten für Mathematik, Technik und Navigation. Radiant ist die SI-Einheit, Grad die alltägliche.",
    base:"deg",
    quick:[["180","deg","rad"],["1","rad","deg"],["360","deg","grad"],["1","rev","deg"],["90","deg","rad"],["1","arcmin","deg"]],
    groups:[
      { label:"Alle", units:[
        {k:"deg",   n:"Grad (°)",             s:"°",     f:1},
        {k:"rad",   n:"Radiant",              s:"rad",   f:180/Math.PI},
        {k:"grad",  n:"Gon / Neugrad",        s:"gon",   f:0.9},
        {k:"rev",   n:"Umdrehung (voll)",     s:"rev",   f:360},
        {k:"arcmin",n:"Bogenminute",          s:"'",     f:1/60},
        {k:"arcsec",n:"Bogensekunde",         s:"\"",    f:1/3600},
        {k:"mil",   n:"Artillerie-Mil",       s:"mil",   f:0.05625},
        {k:"brad",  n:"Binärgrad (256/Kreis)",s:"brad",  f:360/256},
      ]},
    ]
  },

  frequenz: {
    title:"Frequenz", info:"Frequenzeinheiten für Elektronik, Akustik und Physik. Hertz = Schwingungen pro Sekunde.",
    base:"Hz",
    quick:[["1","kHz","Hz"],["1","MHz","kHz"],["1","GHz","MHz"],["50","Hz","rpm"],["1","rpm","Hz"],["1","THz","GHz"]],
    groups:[
      { label:"Hertz", units:[
        {k:"uHz",  n:"Mikrohertz",            s:"μHz",   f:1e-6},
        {k:"mHz",  n:"Millihertz",            s:"mHz",   f:1e-3},
        {k:"Hz",   n:"Hertz",                 s:"Hz",    f:1},
        {k:"kHz",  n:"Kilohertz",             s:"kHz",   f:1e3},
        {k:"MHz",  n:"Megahertz",             s:"MHz",   f:1e6},
        {k:"GHz",  n:"Gigahertz",             s:"GHz",   f:1e9},
        {k:"THz",  n:"Terahertz",             s:"THz",   f:1e12},
      ]},
      { label:"Rotation", units:[
        {k:"rpm",  n:"Umdrehungen pro Minute",s:"rpm",   f:1/60},
        {k:"rps",  n:"Umdrehungen pro Sekunde",s:"rps",  f:1},
        {k:"rad_s",n:"Radiant pro Sekunde",   s:"rad/s", f:1/(2*Math.PI)},
      ]},
    ]
  },
};

// ═══════════════════════════════════════════════════
// STATE
// ═══════════════════════════════════════════════════
let cat    = "laenge";
let kFrom  = "m";
let kTo    = "in";

// ═══════════════════════════════════════════════════
// HELPERS
// ═══════════════════════════════════════════════════
function allUnits(c) {
  return c.groups.flatMap(g => g.units);
}
function findUnit(c, k) {
  return allUnits(c).find(u => u.k === k);
}

function convertTemp(v, f, t) {
  let c = f==="C"?v : f==="F"?(v-32)*5/9 : f==="K"?v-273.15 : v*5/9-273.15;
  return t==="C"?c : t==="F"?c*9/5+32 : t==="K"?c+273.15 : (c+273.15)*9/5;
}

function calc(v, f, t) {
  const c = CATS[cat];
  if (c.isTemp) return convertTemp(v, f, t);
  const uf = findUnit(c, f), ut = findUnit(c, t);
  if (!uf || !ut) return NaN;
  return v * uf.f / ut.f;
}

function fmt(n) {
  if (!isFinite(n)) return "—";
  if (n === 0) return "0";
  const a = Math.abs(n);
  if (a < 1e-9 || a >= 1e15) return n.toExponential(4);
  const dec = a >= 1e6 ? 2 : a >= 100 ? 3 : a >= 1 ? 5 : 7;
  let s = n.toLocaleString("de-DE", {maximumFractionDigits: dec});
  if (s.includes(",")) s = s.replace(/,?0+$/, "");
  return s;
}

// ═══════════════════════════════════════════════════
// CATEGORY
// ═══════════════════════════════════════════════════
function setCat(id) {
  cat = id;
  const c = CATS[id];
  const all = allUnits(c);

  document.querySelectorAll(".cat-btn").forEach(b =>
    b.classList.toggle("active", b.dataset.cat === id));

  document.getElementById("cat-title").textContent = c.title;
  document.getElementById("cat-meta").textContent  = all.length + " Einheiten verfügbar";
  document.getElementById("info-title").textContent = c.title + " umrechnen";
  document.getElementById("info-text").textContent  = c.info;

  kFrom = all[0].k;
  kTo   = all[1]?.k ?? all[0].k;
  refreshLabels();
  doConvert();
  buildQuick();
}

// ═══════════════════════════════════════════════════
// DROPDOWNS
// ═══════════════════════════════════════════════════
function buildDrop(side) {
  const q    = document.getElementById("srch-" + side).value.toLowerCase();
  const drop = document.getElementById("drop-" + side);
  const c    = CATS[cat];
  const sel  = side === "from" ? kFrom : kTo;
  drop.innerHTML = "";

  c.groups.forEach(g => {
    const matches = g.units.filter(u =>
      u.n.toLowerCase().includes(q) || u.s.toLowerCase().includes(q) || u.k.toLowerCase().includes(q)
    );
    if (!matches.length) return;

    const lbl = document.createElement("div");
    lbl.className = "dd-group-label";
    lbl.textContent = g.label;
    drop.appendChild(lbl);

    matches.forEach(u => {
      const div = document.createElement("div");
      div.className = "dd-item" + (u.k === sel ? " sel" : "");
      div.innerHTML = `<span>${u.n}</span><span class="dd-sym">${u.s}</span>`;
      div.onmousedown = e => { e.preventDefault(); pickUnit(side, u.k); };
      drop.appendChild(div);
    });
  });

  if (!drop.children.length) {
    drop.innerHTML = `<div class="dd-empty">Keine Treffer für „${q}"</div>`;
  }
}

function openDrop(side) {
  document.getElementById("drop-" + side).classList.add("open");
  document.getElementById("srch-" + side).select();
  buildDrop(side);
}
function closeDrop(side) {
  document.getElementById("drop-" + side).classList.remove("open");
  refreshLabels();
}

function pickUnit(side, k) {
  if (side === "from") kFrom = k; else kTo = k;
  document.getElementById("drop-" + side).classList.remove("open");
  refreshLabels();
  doConvert();
  buildQuick();
}

function refreshLabels() {
  const c  = CATS[cat];
  const uf = findUnit(c, kFrom);
  const ut = findUnit(c, kTo);
  document.getElementById("srch-from").value = uf ? uf.n : kFrom;
  document.getElementById("srch-to").value   = ut ? ut.n : kTo;
  document.getElementById("lbl-from").textContent = uf ? `${uf.n} (${uf.s})` : kFrom;
  document.getElementById("lbl-to").textContent   = ut ? `${ut.n} (${ut.s})` : kTo;
}

// Close on outside click
document.addEventListener("mousedown", e => {
  ["from","to"].forEach(side => {
    if (!document.getElementById("wrap-" + side).contains(e.target))
      document.getElementById("drop-" + side).classList.remove("open");
  });
});

// ═══════════════════════════════════════════════════
// CONVERT
// ═══════════════════════════════════════════════════
function doConvert() {
  const val = parseFloat(document.getElementById("val-from").value);
  if (isNaN(val)) {
    document.getElementById("val-to").value = "";
    document.getElementById("formula").textContent = "";
    return;
  }
  const res = calc(val, kFrom, kTo);
  document.getElementById("val-to").value = fmt(res);

  const c  = CATS[cat];
  const uf = findUnit(c, kFrom);
  const ut = findUnit(c, kTo);
  if (uf && ut)
    document.getElementById("formula").textContent =
      `${fmt(val)} ${uf.s}  =  ${fmt(res)} ${ut.s}`;
}

// ═══════════════════════════════════════════════════
// QUICK GRID
// ═══════════════════════════════════════════════════
function buildQuick() {
  const c = CATS[cat];
  const grid = document.getElementById("quick-grid");
  grid.innerHTML = "";

  c.quick.forEach(([val, f, t]) => {
    const v   = parseFloat(val);
    const res = calc(v, f, t);
    const uf  = findUnit(c, f);
    const ut  = findUnit(c, t);
    if (!uf || !ut) return;

    const div = document.createElement("div");
    div.className = "quick-item";
    div.innerHTML =
      `<span class="q-from">${fmt(v)} ${uf.s} &rarr;</span>` +
      `<span class="q-to">${fmt(res)} ${ut.s}</span>`;
    div.onclick = () => {
      kFrom = f; kTo = t;
      document.getElementById("val-from").value = val;
      refreshLabels();
      doConvert();
    };
    grid.appendChild(div);
  });
}

// ═══════════════════════════════════════════════════
// SWAP
// ═══════════════════════════════════════════════════
document.getElementById("swap-btn").onclick = () => {
  const oldResult = document.getElementById("val-to").value;
  [kFrom, kTo] = [kTo, kFrom];
  document.getElementById("val-from").value = oldResult || document.getElementById("val-from").value;
  refreshLabels();
  doConvert();
  buildQuick();
};

// ═══════════════════════════════════════════════════
// SEARCH INPUTS
// ═══════════════════════════════════════════════════
["from","to"].forEach(side => {
  const inp = document.getElementById("srch-" + side);
  inp.addEventListener("focus", () => openDrop(side));
  inp.addEventListener("blur",  () => setTimeout(() => closeDrop(side), 120));
  inp.addEventListener("input", () => buildDrop(side));
});

document.getElementById("val-from").addEventListener("input", doConvert);

// ═══════════════════════════════════════════════════
// SIDEBAR BUTTONS
// ═══════════════════════════════════════════════════
document.querySelectorAll(".cat-btn").forEach(btn => {
  btn.addEventListener("click", () => setCat(btn.dataset.cat));
});

// ═══════════════════════════════════════════════════
// BOOT
// ═══════════════════════════════════════════════════
setCat("laenge");
</script>
</body>
</html>
