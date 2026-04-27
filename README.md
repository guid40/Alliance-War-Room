[index.html.html](https://github.com/user-attachments/files/27111493/index.html.html)
# Alliance-War-Room<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Alliance War Room — Rankings</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;500;600;700&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
  :root {
    --red: #c0392b;
    --red-dark: #96281b;
    --gold: #f39c12;
    --silver: #95a5a6;
    --bronze: #a04000;
    --green: #27ae60;
    --blue: #2980b9;
    --bg: #0d1117;
    --bg2: #161b22;
    --bg3: #21262d;
    --border: #30363d;
    --text: #e6edf3;
    --muted: #8b949e;
    --dim: #484f58;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Rajdhani', sans-serif;
    min-height: 100vh;
    padding-bottom: 40px;
  }

  header {
    background: var(--bg2);
    border-bottom: 1px solid var(--border);
    padding: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
    position: sticky;
    top: 0;
    z-index: 10;
  }

  .skull {
    width: 36px; height: 36px;
    background: var(--red);
    clip-path: polygon(50% 0%,80% 20%,100% 50%,80% 80%,60% 100%,40% 100%,20% 80%,0% 50%,20% 20%);
    flex-shrink: 0;
  }

  .header-text h1 {
    font-size: 18px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: #f0f6fc;
  }

  .header-text p {
    font-size: 11px;
    color: var(--muted);
    font-family: 'Share Tech Mono', monospace;
    letter-spacing: 1px;
  }

  .badge {
    margin-left: auto;
    background: var(--red);
    color: #ffe;
    font-size: 10px;
    font-weight: 700;
    padding: 4px 10px;
    border-radius: 4px;
    letter-spacing: 1px;
    text-transform: uppercase;
    flex-shrink: 0;
  }

  .tabs {
    display: flex;
    background: var(--bg2);
    border-bottom: 1px solid var(--border);
    padding: 0 16px;
  }

  .tab {
    flex: 1;
    padding: 12px 0;
    text-align: center;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--muted);
    cursor: pointer;
    border-bottom: 2px solid transparent;
    transition: color 0.2s, border-color 0.2s;
  }

  .tab.active { color: var(--red); border-bottom-color: var(--red); }

  .legend {
    display: flex;
    gap: 14px;
    padding: 10px 16px;
    flex-wrap: wrap;
    background: var(--bg2);
    border-bottom: 1px solid var(--border);
  }

  .legend span {
    display: flex;
    align-items: center;
    gap: 5px;
    font-size: 11px;
    color: var(--muted);
    font-family: 'Share Tech Mono', monospace;
  }

  .dot {
    width: 8px; height: 8px;
    border-radius: 2px;
    display: inline-block;
  }

  .list { padding: 12px 16px; display: flex; flex-direction: column; gap: 8px; }

  .panel { display: none; }
  .panel.active { display: block; }

  .card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px;
    display: flex;
    align-items: center;
    gap: 10px;
    animation: fadeUp 0.3s ease both;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(6px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .card:nth-child(1)  { animation-delay: 0.02s; }
  .card:nth-child(2)  { animation-delay: 0.05s; }
  .card:nth-child(3)  { animation-delay: 0.08s; }
  .card:nth-child(4)  { animation-delay: 0.11s; }
  .card:nth-child(5)  { animation-delay: 0.14s; }
  .card:nth-child(6)  { animation-delay: 0.17s; }
  .card:nth-child(7)  { animation-delay: 0.20s; }
  .card:nth-child(8)  { animation-delay: 0.23s; }
  .card:nth-child(9)  { animation-delay: 0.26s; }
  .card:nth-child(10) { animation-delay: 0.29s; }

  .card.top1 { border-color: #f39c12; }
  .card.top2 { border-color: #7f8c8d; }
  .card.top3 { border-color: #a04000; }

  .rank-num {
    font-size: 15px;
    font-weight: 700;
    min-width: 26px;
    text-align: center;
    font-family: 'Share Tech Mono', monospace;
    color: var(--dim);
  }

  .rank-num.gold   { color: var(--gold); }
  .rank-num.silver { color: var(--silver); }
  .rank-num.bronze { color: var(--bronze); }

  .info { flex: 1; min-width: 0; }

  .name {
    font-size: 15px;
    font-weight: 600;
    color: #f0f6fc;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    margin-bottom: 7px;
  }

  .bars { display: flex; flex-direction: column; gap: 4px; }

  .bar-row {
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .bar-lbl {
    font-size: 10px;
    color: var(--dim);
    font-family: 'Share Tech Mono', monospace;
    width: 48px;
    flex-shrink: 0;
  }

  .bar-track {
    flex: 1;
    height: 5px;
    border-radius: 3px;
    background: var(--bg3);
    overflow: hidden;
  }

  .bar-fill {
    height: 100%;
    border-radius: 3px;
    transition: width 0.8s cubic-bezier(0.4,0,0.2,1);
  }

  .bar-val {
    font-size: 10px;
    color: var(--muted);
    font-family: 'Share Tech Mono', monospace;
    width: 38px;
    text-align: right;
    flex-shrink: 0;
  }

  .score {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-width: 42px;
    padding: 6px 4px;
    border-radius: 8px;
    font-family: 'Share Tech Mono', monospace;
  }

  .score-num {
    font-size: 18px;
    font-weight: 700;
    line-height: 1;
  }

  .score-lbl {
    font-size: 9px;
    margin-top: 2px;
    opacity: 0.7;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .score.high { background: #0d2016; color: #3fb950; }
  .score.low  { background: #1e0a0a; color: #f85149; }

  .section-title {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    font-family: 'Share Tech Mono', monospace;
    padding: 14px 16px 2px;
  }

  .section-desc {
    font-size: 12px;
    color: var(--dim);
    padding: 2px 16px 8px;
    font-family: 'Share Tech Mono', monospace;
  }

  .formula {
    margin: 8px 16px 0;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 10px 14px;
    font-size: 12px;
    color: var(--muted);
    font-family: 'Share Tech Mono', monospace;
    line-height: 1.7;
  }

  .formula strong { color: var(--text); }
</style>
</head>
<body>

<header>
  <div class="skull"></div>
  <div class="header-text">
    <h1>Alliance War Room</h1>
    <p>Dark War: Survival · Member Rankings</p>
  </div>
  <div class="badge">R4 CMD</div>
</header>

<div class="tabs">
  <div class="tab active" onclick="showTab('top')">Top 10</div>
  <div class="tab" onclick="showTab('bot')">Bottom 10</div>
  <div class="tab" onclick="showTab('info')">Score Info</div>
</div>

<div class="legend">
  <span><span class="dot" style="background:#378ADD"></span>Power</span>
  <span><span class="dot" style="background:#E24B4A"></span>Kills</span>
  <span><span class="dot" style="background:#1D9E75"></span>Contrib.</span>
</div>

<div id="panel-top" class="panel active">
  <div class="section-title">Top 10 — best performers</div>
  <div class="section-desc">Ranked by combined score (power + kills + contribution)</div>
  <div class="list" id="top-list"></div>
</div>

<div id="panel-bot" class="panel">
  <div class="section-title">Bottom 10 — lowest engagement</div>
  <div class="section-desc">Members who need to step up their activity</div>
  <div class="list" id="bot-list"></div>
</div>

<div id="panel-info" class="panel">
  <div class="section-title">How scores are calculated</div>
  <div class="formula">
    <strong>Score = Power×40% + Kills×40% + Contribution×20%</strong><br><br>
    Each metric is normalized against the top member in that category (0–100%).<br><br>
    <strong>Power</strong> — total battle power (BP)<br>
    <strong>Kills</strong> — total kills (Abates)<br>
    <strong>Contribution</strong> — weekly alliance contribution<br><br>
    Data snapshot: April 26, 2026<br>
    Total members ranked: 100
  </div>
</div>

<script>
const raw = [
  {name:"Timmŷ",power:1234870872,resources:89260,kills:24403437},
  {name:"LũNaTiC",power:1097924792,resources:79900,kills:31203430},
  {name:"P4nti3R41dr",power:1073039571,resources:74920,kills:42549400},
  {name:"• Sarah • 2",power:1063383409,resources:74020,kills:24359561},
  {name:"CoverednBlood",power:1005908440,resources:58070,kills:14659463},
  {name:"¥Mythic¥",power:942527302,resources:72940,kills:21911147},
  {name:"H4rl3ysb0x",power:938882412,resources:52050,kills:11636777},
  {name:"• Sarah •",power:902443630,resources:63580,kills:4906670},
  {name:"ChristIsK1ng",power:899627560,resources:65620,kills:7817691},
  {name:"Rage2334",power:879396236,resources:59170,kills:4103893},
  {name:"SN4KEPRINCESS",power:854399430,resources:88900,kills:4246501},
  {name:"Do0fy",power:853745111,resources:52300,kills:1109536},
  {name:"Aevrax",power:836570681,resources:57640,kills:6738728},
  {name:"Guidao",power:830218283,resources:86080,kills:4746278},
  {name:"XabstractX",power:809867281,resources:70480,kills:6983552},
  {name:"yupp4nti3s",power:809657201,resources:65180,kills:7618332},
  {name:"BADBOY-007",power:796567799,resources:77630,kills:2372626},
  {name:"BLACKBEARD",power:794346549,resources:83280,kills:3196944},
  {name:"SUN G0D NIKA",power:789299031,resources:92620,kills:5949101},
  {name:"Randomie",power:786417980,resources:84160,kills:1404561},
  {name:"-Mana-",power:771912794,resources:85720,kills:2429294},
  {name:"Ticklēmētimmŷ",power:766230103,resources:70180,kills:1582688},
  {name:"Gadik13",power:752795921,resources:88760,kills:970465},
  {name:"LATENIGHTSHADOW",power:752662487,resources:15320,kills:10469615},
  {name:"Mermaid55",power:752303040,resources:82960,kills:7303401},
  {name:"Deemac2",power:747357891,resources:23080,kills:414622},
  {name:"Ch££sE",power:740479250,resources:42070,kills:7408945},
  {name:"Marzann",power:732201791,resources:20280,kills:1453529},
  {name:"Fido dog",power:721757837,resources:36050,kills:524504},
  {name:"greypansies-OLAF",power:717503017,resources:26460,kills:868175},
  {name:"Roubax",power:716149301,resources:56620,kills:3184173},
  {name:"P1lus",power:713906647,resources:84040,kills:334202},
  {name:"MoHAMMeD",power:712290166,resources:69360,kills:3709580},
  {name:"bienmary",power:709907672,resources:51350,kills:2371955},
  {name:"9Kaos9",power:709228628,resources:58420,kills:1651045},
  {name:"Happy Vales",power:707266495,resources:54420,kills:22908},
  {name:"P4nt1Dropper",power:704680506,resources:45650,kills:1985960},
  {name:"--pepper--",power:702273884,resources:68440,kills:1012944},
  {name:"Bleu Mage",power:699222532,resources:55780,kills:2439354},
  {name:"P4nti3Jinx3r",power:698036945,resources:8510,kills:5891198},
  {name:"Saikotsu",power:692175370,resources:89380,kills:1035930},
  {name:"marybien",power:690198060,resources:54160,kills:1167307},
  {name:"Oblivion",power:682591931,resources:68540,kills:2079470},
  {name:"Z M A N",power:672237365,resources:82000,kills:5640676},
  {name:"TheWeirdStar",power:664156472,resources:9440,kills:774861},
  {name:"ReApR",power:662633979,resources:45670,kills:2410136},
  {name:"TheGodfath3r",power:655676502,resources:61610,kills:1912039},
  {name:"AuroraBrooke",power:654368159,resources:21800,kills:59662},
  {name:"Petros K",power:654140023,resources:65620,kills:1630852},
  {name:"OG22202",power:651749830,resources:59010,kills:699100},
  {name:"Sk3ll13sG1rl",power:650031628,resources:19400,kills:779140},
  {name:"Samanouske",power:648683467,resources:28050,kills:171108},
  {name:"Tainted Jesus",power:637877209,resources:12500,kills:1168978},
  {name:"P4nti3squid",power:632863281,resources:31510,kills:7090284},
  {name:"BittencourtM",power:628449771,resources:60580,kills:5394882},
  {name:"MED GHOST",power:626052967,resources:86200,kills:1360756},
  {name:"Shawaal",power:621601361,resources:38750,kills:991536},
  {name:"PoppySia",power:614461498,resources:33870,kills:286805},
  {name:"TheHeroSB",power:613642008,resources:84700,kills:4617419},
  {name:"Alice doCAPS",power:613408807,resources:15980,kills:2738904},
  {name:"Awaryjny",power:608654770,resources:47260,kills:587984},
  {name:"Qereq",power:606749175,resources:68990,kills:555337},
  {name:"P4nt13-Royal",power:605979076,resources:11410,kills:714321},
  {name:"Haryana Boy",power:605928825,resources:83180,kills:468908},
  {name:"DamageVA",power:604887682,resources:55240,kills:714728},
  {name:"Aphröditēēē",power:599075070,resources:30050,kills:1291571},
  {name:"roma2706",power:596511777,resources:28920,kills:563568},
  {name:"Nick'",power:592264407,resources:46930,kills:961959},
  {name:"mohammed RM",power:585026729,resources:48050,kills:686587},
  {name:"mikhto",power:585024599,resources:54170,kills:1996700},
  {name:"°Ishaan°",power:582796961,resources:68090,kills:2823262},
  {name:"Miingau",power:569237848,resources:72880,kills:2000916},
  {name:"JabberWocky9",power:567628086,resources:6120,kills:308868},
  {name:"PelicanEcho",power:566644614,resources:43720,kills:175194},
  {name:"Azooz97",power:550768948,resources:18770,kills:2162227},
  {name:"Claayyy-",power:539667053,resources:15090,kills:1271396},
  {name:"GaryMichael",power:533580862,resources:80860,kills:517560},
  {name:"Og Yocs",power:527287749,resources:21640,kills:5442980},
  {name:"QdMn",power:524166438,resources:45780,kills:224338},
  {name:"adøre",power:521339483,resources:67150,kills:195433},
  {name:"Frankiejay",power:511570520,resources:37100,kills:165824},
  {name:"• AAAA • TH • •",power:511071257,resources:59930,kills:1737291},
  {name:"TheRealK1ng",power:478258866,resources:4450,kills:348840},
  {name:"• BOB • P4NTIE •",power:475799498,resources:0,kills:1553084},
  {name:"GREM",power:470934339,resources:0,kills:1611811},
  {name:"The MaReSiA",power:466682497,resources:34720,kills:1329283},
  {name:"Mark",power:461678544,resources:5350,kills:410217},
  {name:"DJAVU",power:455878223,resources:50490,kills:550032},
  {name:"Juliasj",power:454873879,resources:23700,kills:224490},
  {name:"Kilr0y",power:450459646,resources:47010,kills:42749},
  {name:"P4nti3Sl4yeR",power:444918244,resources:12810,kills:404872},
  {name:"Yumena",power:429136842,resources:33360,kills:1302284},
  {name:"lilyrosee",power:405242927,resources:66220,kills:838665},
  {name:"The volibear",power:394793051,resources:13140,kills:901835},
  {name:"El VooDooDaddy",power:389303910,resources:2300,kills:960770},
  {name:"presidentebender",power:324413960,resources:0,kills:1893004},
  {name:"Don Richard",power:321357163,resources:0,kills:173173},
  {name:"P4nt135hr3k",power:313853196,resources:90,kills:649932},
  {name:"obaethis",power:298218735,resources:0,kills:554933},
  {name:"Mysticfox420",power:256486398,resources:0,kills:707562}
];

const maxP = Math.max(...raw.map(d=>d.power));
const maxK = Math.max(...raw.map(d=>d.kills));
const maxR = Math.max(...raw.map(d=>d.resources));

function fmt(n) {
  if(n>=1e9) return (n/1e9).toFixed(1)+'B';
  if(n>=1e6) return (n/1e6).toFixed(1)+'M';
  if(n>=1e3) return (n/1e3).toFixed(0)+'K';
  return n.toString();
}

const scored = raw.map(d => {
  const sp = d.power/maxP;
  const sk = d.kills/maxK;
  const sr = d.resources/maxR;
  const score = Math.round((sp*0.4+sk*0.4+sr*0.2)*100);
  return {...d, score, sp, sk, sr};
}).sort((a,b)=>b.score-a.score);

const top10 = scored.slice(0,10);
const bot10 = scored.slice(-10).reverse();

function card(m, rank, isTop) {
  const rc = rank===1?'gold':rank===2?'silver':rank===3?'bronze':'';
  const cardCls = rank===1?'top1':rank===2?'top2':rank===3?'top3':'';
  const scoreCls = isTop?'high':'low';
  const pct = v => Math.round(v*100);
  return `<div class="card ${cardCls}">
    <div class="rank-num ${rc}">#${rank}</div>
    <div class="info">
      <div class="name">${m.name}</div>
      <div class="bars">
        <div class="bar-row">
          <div class="bar-lbl">Power</div>
          <div class="bar-track"><div class="bar-fill" style="width:${pct(m.sp)}%;background:#378ADD"></div></div>
          <div class="bar-val">${fmt(m.power)}</div>
        </div>
        <div class="bar-row">
          <div class="bar-lbl">Kills</div>
          <div class="bar-track"><div class="bar-fill" style="width:${pct(m.sk)}%;background:#E24B4A"></div></div>
          <div class="bar-val">${fmt(m.kills)}</div>
        </div>
        <div class="bar-row">
          <div class="bar-lbl">Contrib.</div>
          <div class="bar-track"><div class="bar-fill" style="width:${pct(m.sr)}%;background:#1D9E75"></div></div>
          <div class="bar-val">${fmt(m.resources)}</div>
        </div>
      </div>
    </div>
    <div class="score ${scoreCls}">
      <div class="score-num">${m.score}</div>
      <div class="score-lbl">score</div>
    </div>
  </div>`;
}

document.getElementById('top-list').innerHTML = top10.map((m,i)=>card(m,i+1,true)).join('');
document.getElementById('bot-list').innerHTML = bot10.map((m,i)=>card(m,scored.length-i,false)).join('');

function showTab(name) {
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
  document.getElementById('panel-'+name).classList.add('active');
  event.target.classList.add('active');
}
</script>
</body>
</html>
