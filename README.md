<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Dr. McHenry's Favorite Plant</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@600;800&family=Atkinson+Hyperlegible:wght@400;700&display=swap">
<style>
:root{
  --bg:#eaf6dc; --paper:#fffdf5; --ink:#1f3320; --muted:#4d6a4f; --leaf:#3f9d3a; --leaf-d:#23662a;
  --trap:#d8433b; --sun:#ffc531; --sky:#cfeefc; --soil:#7a4e2d; --line:#b9d6a6; --good:#2f9e48; --bad:#c9443a;
  --display:"Baloo 2","Trebuchet MS",sans-serif; --body:"Atkinson Hyperlegible",system-ui,sans-serif;
  color-scheme:light;
}
*{box-sizing:border-box}
[hidden]{display:none!important}
html,body{background:var(--bg);color:var(--ink);font-family:var(--body);font-size:17px}
body{padding-inline:16px;padding-block:14px}
.wrap{max-width:1000px;margin:0 auto;display:flex;flex-direction:column;gap:14px}
header{display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;gap:8px 16px}
h1{font-family:var(--display);font-weight:800;font-size:clamp(28px,5vw,44px);margin:0;line-height:1;color:var(--leaf-d)}
h1 span{color:var(--trap)}
.steps{display:flex;gap:6px;flex-wrap:wrap}
.steps i{font-style:normal;font-family:var(--display);font-weight:800;font-size:13px;padding:4px 10px;border-radius:99px;background:#fff;border:2px solid var(--line);color:var(--muted)}
.steps i.on{background:var(--sun);border-color:#d79a00;color:var(--ink)}
.steps i.done{background:var(--leaf);border-color:var(--leaf-d);color:#fff}
.card{background:var(--paper);border:3px solid var(--line);border-radius:22px;padding:14px}
.stage{position:relative;padding:8px}
.stage svg{display:block;width:100%;height:auto;max-height:62vh}
.tag{font-family:var(--display);font-weight:800;font-size:13px;letter-spacing:.06em;text-transform:uppercase;color:var(--trap);margin:0 0 4px}
h2{font-family:var(--display);font-weight:800;font-size:clamp(22px,3.4vw,30px);margin:0 0 6px;line-height:1.1;text-wrap:balance}
p{margin:0 0 8px;line-height:1.5;max-width:70ch}
.panel{display:grid;grid-template-columns:minmax(0,1.2fr) minmax(0,1fr);gap:14px;align-items:start}
@media (max-width:760px){.panel{grid-template-columns:minmax(0,1fr)}}
.tray{display:flex;flex-wrap:wrap;gap:8px}
.item{font-family:var(--display);font-weight:800;font-size:17px;display:flex;align-items:center;gap:8px;padding:8px 14px 8px 8px;border-radius:16px;background:#fff;border:3px solid var(--line);cursor:pointer;color:var(--ink);box-shadow:0 4px 0 var(--line)}
.item svg{width:38px;height:38px}
.item.sel{border-color:#d79a00;background:#fff4c4;box-shadow:0 4px 0 #d79a00;transform:translateY(-2px)}
.item.used{opacity:.35;pointer-events:none;box-shadow:none}
.item:focus-visible,.btn:focus-visible,.chip:focus-visible,.opt:focus-visible{outline:3px solid var(--trap);outline-offset:2px}
.hint{font-size:15px;color:var(--muted)}
.fb{min-height:1.5em;font-weight:700}
.fb.good{color:var(--good)} .fb.bad{color:var(--bad)}
.btn{font-family:var(--display);font-weight:800;font-size:19px;padding:10px 22px;border-radius:16px;border:3px solid var(--leaf-d);background:var(--leaf);color:#fff;cursor:pointer;box-shadow:0 5px 0 var(--leaf-d)}
.btn:active{transform:translateY(4px);box-shadow:0 1px 0 var(--leaf-d)}
.btn.sun{background:var(--sun);border-color:#d79a00;color:var(--ink);box-shadow:0 5px 0 #d79a00}
.target{cursor:pointer}
.target .ring{fill:rgba(255,197,49,.18);stroke:#d79a00;stroke-width:4;stroke-dasharray:10 7}
.armed .target .ring{animation:pulse 1s ease-in-out infinite alternate}
.target.filled .ring{fill:rgba(47,158,72,.15);stroke:var(--good);stroke-dasharray:none}
.target text{font-family:var(--display);font-weight:800;font-size:15px;fill:var(--ink);paint-order:stroke;stroke:#fff;stroke-width:5px;stroke-linejoin:round}
@keyframes pulse{from{stroke-width:3}to{stroke-width:7}}
.eq{display:flex;flex-wrap:wrap;gap:8px;align-items:center;font-family:var(--display);font-weight:800;font-size:20px;margin:6px 0 10px}
.blank{min-width:120px;min-height:46px;padding:6px 12px;border-radius:12px;border:3px dashed #d79a00;background:#fff8dc;display:flex;align-items:center;justify-content:center;cursor:pointer}
.blank.ok{border-style:solid;border-color:var(--good);background:#e5f6e2}
.chips{display:flex;flex-wrap:wrap;gap:8px}
.chip{font-family:var(--display);font-weight:800;font-size:17px;padding:8px 14px;border-radius:99px;border:3px solid var(--line);background:#fff;cursor:pointer;color:var(--ink)}
.chip.sel{border-color:#d79a00;background:#fff4c4}
.chip.used{opacity:.35;pointer-events:none}
.opts{display:flex;flex-direction:column;gap:8px}
.opt{font-family:var(--body);font-size:17px;text-align:left;padding:10px 14px;border-radius:14px;border:3px solid var(--line);background:#fff;cursor:pointer;color:var(--ink)}
.opt.right{border-color:var(--good);background:#e5f6e2}
.opt.wrong{border-color:var(--bad);background:#fbe4e1}
.shake{animation:shake .35s}
@keyframes shake{25%{transform:translateX(-6px)}75%{transform:translateX(6px)}}
.gallery{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}
@media (max-width:620px){.gallery{grid-template-columns:minmax(0,1fr)}}
.photo{background:#fff;border:3px solid var(--line);border-radius:18px;padding:8px 8px 10px;transform:rotate(-1deg)}
.photo:nth-child(2n){transform:rotate(1.2deg)}
.photo svg{display:block;width:100%;height:auto;border-radius:12px}
.photo b{display:block;font-family:var(--display);font-size:18px;text-align:center;margin-top:6px}
.code{font-family:var(--display);font-weight:800;font-size:clamp(30px,7vw,48px);letter-spacing:.04em;text-align:center;color:var(--leaf-d);background:#fff8dc;border:4px dashed var(--trap);border-radius:18px;padding:8px 12px;user-select:all}
.row{display:flex;flex-wrap:wrap;gap:10px;align-items:center}
.std{font-size:14px;color:var(--muted)}
.float{animation:float 2.4s ease-in-out infinite}
@keyframes float{50%{transform:translateY(-8px)}}
@media (prefers-reduced-motion:reduce){*{animation:none!important}}
</style>
</head>
<body>
<div class="wrap">
  <header>
    <h1>Dr. McHenry's <span>Favorite Plant</span></h1>
    <div class="steps" id="steps"></div>
  </header>
  <div class="card stage" id="stage"></div>
  <div class="card" id="panel"></div>
</div>

<script>
(function(){
const $=s=>document.querySelector(s);
const stage=$('#stage'), panel=$('#panel');
let sound=true, ac=null;
function tone(f,d,type='triangle',v=.07,delay=0){if(!sound)return;try{ac=ac||new (window.AudioContext||window.webkitAudioContext)();const t=ac.currentTime+delay,o=ac.createOscillator(),g=ac.createGain();o.type=type;o.frequency.value=f;g.gain.setValueAtTime(v,t);g.gain.exponentialRampToValueAtTime(.0001,t+d);o.connect(g).connect(ac.destination);o.start(t);o.stop(t+d);}catch(e){}}
const yay=()=>{tone(660,.15);tone(880,.2,'triangle',.07,.12)}, nope=()=>tone(180,.25,'sawtooth',.04), chomp=()=>{tone(300,.08,'square',.06);tone(160,.12,'square',.06,.08)};

/* ---------- art ---------- */
const ICON={
 water:`<svg viewBox="0 0 40 40"><path d="M20 4 C12 16 9 21 9 26 a11 11 0 0 0 22 0 c0-5-3-10-11-22z" fill="#4fb3f0" stroke="#1e6fa8" stroke-width="2.5"/><ellipse cx="15" cy="25" rx="3" ry="5" fill="#bfe6ff"/></svg>`,
 minerals:`<svg viewBox="0 0 40 40"><path d="M8 16 h24 l-3 20 h-18z" fill="#c99a62" stroke="#7a4e2d" stroke-width="2.5"/><path d="M8 16 q12 -8 24 0" fill="#e1b98a" stroke="#7a4e2d" stroke-width="2.5"/><circle cx="15" cy="26" r="3" fill="#8b6ad6"/><circle cx="22" cy="29" r="2.5" fill="#3fa7a0"/><circle cx="25" cy="23" r="2.5" fill="#e0a12e"/></svg>`,
 bug:`<svg viewBox="0 0 40 40"><ellipse cx="13" cy="15" rx="8" ry="5" fill="#d9f1ff" stroke="#6aa0c4" stroke-width="2" transform="rotate(-25 13 15)"/><ellipse cx="27" cy="15" rx="8" ry="5" fill="#d9f1ff" stroke="#6aa0c4" stroke-width="2" transform="rotate(25 27 15)"/><ellipse cx="20" cy="24" rx="6" ry="9" fill="#3b3b3b"/><circle cx="20" cy="14" r="5" fill="#3b3b3b"/><circle cx="18" cy="13" r="1.8" fill="#c0392b"/><circle cx="22" cy="13" r="1.8" fill="#c0392b"/></svg>`,
 sun:`<svg viewBox="0 0 40 40"><g stroke="#e8a400" stroke-width="3" stroke-linecap="round">${[0,45,90,135,180,225,270,315].map(a=>`<line x1="20" y1="3" x2="20" y2="8" transform="rotate(${a} 20 20)"/>`).join('')}</g><circle cx="20" cy="20" r="10" fill="#ffc531" stroke="#e8a400" stroke-width="2.5"/></svg>`,
 co2:`<svg viewBox="0 0 40 40"><path d="M9 28 a7 7 0 0 1 1-14 a9 9 0 0 1 17-2 a7 7 0 0 1 4 16z" fill="#e3e9ef" stroke="#7c8b99" stroke-width="2.5"/><text x="20" y="25" text-anchor="middle" font-family="Baloo 2,sans-serif" font-weight="800" font-size="11" fill="#4b5966">CO₂</text></svg>`,
 o2:`<svg viewBox="0 0 40 40"><circle cx="20" cy="20" r="14" fill="#dff4ff" stroke="#3b9bd6" stroke-width="2.5"/><text x="20" y="25" text-anchor="middle" font-family="Baloo 2,sans-serif" font-weight="800" font-size="13" fill="#1e6fa8">O₂</text></svg>`,
 food:`<svg viewBox="0 0 40 40"><path d="M6 18 q14 -14 28 0 z" fill="#e8b46a" stroke="#9a6a2c" stroke-width="2"/><rect x="6" y="18" width="28" height="4" fill="#5fbf4a"/><rect x="6" y="22" width="28" height="4" fill="#d9534f"/><rect x="6" y="26" width="28" height="4" fill="#ffd84d"/><path d="M6 30 h28 q0 5 -6 5 h-16 q-6 0 -6 -5z" fill="#e8b46a" stroke="#9a6a2c" stroke-width="2"/></svg>`,
 sugar:`<svg viewBox="0 0 40 40"><rect x="9" y="9" width="10" height="10" rx="2" fill="#fff" stroke="#c07a2e" stroke-width="2.5"/><rect x="21" y="13" width="10" height="10" rx="2" fill="#fff" stroke="#c07a2e" stroke-width="2.5"/><rect x="14" y="22" width="10" height="10" rx="2" fill="#fff" stroke="#c07a2e" stroke-width="2.5"/></svg>`,
 energy:`<svg viewBox="0 0 40 40"><polygon points="23,3 9,23 19,23 15,37 31,15 21,15" fill="#ffc531" stroke="#c98a00" stroke-width="2.5" stroke-linejoin="round"/></svg>`,
 breathe:`<svg viewBox="0 0 40 40"><path d="M4 16 h20 a5 5 0 1 0 -5 -5 M4 23 h28 a5 5 0 1 1 -5 5 M4 30 h14" fill="none" stroke="#3b9bd6" stroke-width="3" stroke-linecap="round"/></svg>`
};

function trap(x,y,s,rot,shut){
  const teeth=(dir)=>Array.from({length:7},(_,k)=>{const tx=-26+k*8.6;return `<line x1="${tx}" y1="0" x2="${tx+dir*2}" y2="${dir*-12}" stroke="#bfe28a" stroke-width="2.4" stroke-linecap="round"/>`}).join('');
  const open=shut?6:28;
  return `<g transform="translate(${x} ${y}) rotate(${rot}) scale(${s})">
   <g transform="rotate(${-open})"><path d="M-30 0 Q0 -30 30 0 Z" fill="#7cc04a" stroke="#2f7a2a" stroke-width="3"/><path d="M-24 -1 Q0 -20 24 -1 Z" fill="#e5483f"/><g transform="translate(0 -1)">${teeth(1)}</g></g>
   <g transform="rotate(${open})"><path d="M-30 0 Q0 30 30 0 Z" fill="#7cc04a" stroke="#2f7a2a" stroke-width="3"/><path d="M-24 1 Q0 20 24 1 Z" fill="#c9332c"/><g transform="translate(0 1)">${teeth(-1)}</g></g>
  </g>`;
}
function flytrap(cx,base,s=1,happy=true){
  const leaf=(ang,len)=>{const a=ang*Math.PI/180,ex=cx+Math.cos(a)*len*s,ey=base-6-Math.sin(a)*len*s;
    return `<path d="M${cx} ${base-6} Q${(cx+ex)/2} ${(base-6+ey)/2-14*s} ${ex} ${ey}" stroke="#3f9d3a" stroke-width="${7*s}" fill="none" stroke-linecap="round"/>`+trap(ex+Math.cos(a)*24*s,ey-Math.sin(a)*24*s,s,-ang,false)};
  let g=leaf(155,70)+leaf(118,95)+leaf(62,95)+leaf(25,70)+leaf(90,110);
  g+=`<path d="M${cx-48*s} ${base} h${96*s} l${-10*s} ${58*s} h${-76*s}z" fill="#d9784a" stroke="#8a4524" stroke-width="${3*s}"/><rect x="${cx-54*s}" y="${base-8*s}" width="${108*s}" height="${14*s}" rx="${4*s}" fill="#e88a5a" stroke="#8a4524" stroke-width="${3*s}"/>`;
  if(happy) g+=`<g transform="translate(${cx} ${base+30*s})">${face(0,0,s*1.3)}</g>`;
  return g;
}
function face(x,y,s){return `<circle cx="${x-7*s}" cy="${y-3*s}" r="${3*s}" fill="#1f3320"/><circle cx="${x+7*s}" cy="${y-3*s}" r="${3*s}" fill="#1f3320"/><path d="M${x-7*s} ${y+5*s} q${7*s} ${7*s} ${14*s} 0" stroke="#1f3320" stroke-width="${2.4*s}" fill="none" stroke-linecap="round"/>`}

function drm(x,y,s=1,pose='stand'){
  const S=v=>v*s;
  const armL = pose==='wave' ? `<path d="M${x-S(34)} ${y-S(150)} q${S(-30)} ${S(-30)} ${S(-20)} ${S(-70)}" stroke="#f4f6f8" stroke-width="${S(18)}" fill="none" stroke-linecap="round"/><circle cx="${x-S(52)}" cy="${y-S(222)}" r="${S(10)}" fill="#7a4a2a"/>`
    : pose==='drive'||pose==='sit' ? `<path d="M${x-S(30)} ${y-S(150)} q${S(10)} ${S(40)} ${S(46)} ${S(36)}" stroke="#f4f6f8" stroke-width="${S(18)}" fill="none" stroke-linecap="round"/><circle cx="${x+S(20)}" cy="${y-S(112)}" r="${S(9)}" fill="#7a4a2a"/>`
    : pose==='throw' ? `<path d="M${x+S(34)} ${y-S(150)} q${S(34)} ${S(-20)} ${S(40)} ${S(-62)}" stroke="#f4f6f8" stroke-width="${S(18)}" fill="none" stroke-linecap="round"/><circle cx="${x+S(76)}" cy="${y-S(214)}" r="${S(10)}" fill="#7a4a2a"/>`
    : `<path d="M${x-S(34)} ${y-S(150)} q${S(-14)} ${S(30)} ${S(-10)} ${S(62)}" stroke="#f4f6f8" stroke-width="${S(18)}" fill="none" stroke-linecap="round"/><circle cx="${x-S(44)}" cy="${y-S(84)}" r="${S(9)}" fill="#7a4a2a"/>`;
  const armR = pose==='throw' ? `<path d="M${x-S(34)} ${y-S(150)} q${S(-24)} ${S(26)} ${S(-16)} ${S(60)}" stroke="#f4f6f8" stroke-width="${S(18)}" fill="none" stroke-linecap="round"/>`
    : pose==='cart' ? `<path d="M${x+S(34)} ${y-S(150)} q${S(24)} ${S(30)} ${S(50)} ${S(40)}" stroke="#f4f6f8" stroke-width="${S(18)}" fill="none" stroke-linecap="round"/><circle cx="${x+S(86)}" cy="${y-S(110)}" r="${S(9)}" fill="#7a4a2a"/>`
    : `<path d="M${x+S(34)} ${y-S(150)} q${S(14)} ${S(30)} ${S(10)} ${S(62)}" stroke="#f4f6f8" stroke-width="${S(18)}" fill="none" stroke-linecap="round"/><circle cx="${x+S(44)}" cy="${y-S(84)}" r="${S(9)}" fill="#7a4a2a"/>`;
  const legs = (pose==='drive'||pose==='sit') ? '' : `<rect x="${x-S(26)}" y="${y-S(70)}" width="${S(20)}" height="${S(66)}" rx="${S(6)}" fill="#2d3e66"/><rect x="${x+S(6)}" y="${y-S(70)}" width="${S(20)}" height="${S(66)}" rx="${S(6)}" fill="#2d3e66"/><ellipse cx="${x-S(18)}" cy="${y-S(2)}" rx="${S(15)}" ry="${S(6)}" fill="#3b2416"/><ellipse cx="${x+S(18)}" cy="${y-S(2)}" rx="${S(15)}" ry="${S(6)}" fill="#3b2416"/>`;
  return `<g>
   ${legs}
   <path d="M${x-S(40)} ${y-S(160)} q${S(40)} ${S(-14)} ${S(80)} 0 l${S(8)} ${S(100)} h${S(-96)} z" fill="#f4f6f8" stroke="#aab4be" stroke-width="${S(3)}"/>
   <path d="M${x-S(14)} ${y-S(162)} l${S(14)} ${S(22)} l${S(14)} ${S(-22)}" fill="#7a3e9d"/>
   <line x1="${x}" y1="${y-S(140)}" x2="${x}" y2="${y-S(62)}" stroke="#aab4be" stroke-width="${S(2)}"/>
   <rect x="${x+S(10)}" y="${y-S(128)}" width="${S(18)}" height="${S(14)}" rx="${S(2)}" fill="#dfe6ec" stroke="#aab4be" stroke-width="${S(2)}"/><line x1="${x+S(14)}" y1="${y-S(132)}" x2="${x+S(14)}" y2="${y-S(118)}" stroke="#3b6fd6" stroke-width="${S(2.5)}"/>
   ${armL}${armR}
   <rect x="${x-S(9)}" y="${y-S(178)}" width="${S(18)}" height="${S(20)}" fill="#7a4a2a"/>
   <circle cx="${x}" cy="${y-S(222)}" r="${S(58)}" fill="#2a1a12"/>
   ${Array.from({length:18},(_,k)=>{const a=k/18*Math.PI*2;return `<circle cx="${x+Math.cos(a)*S(54)}" cy="${y-S(226)+Math.sin(a)*S(50)}" r="${S(16)}" fill="#2a1a12"/>`}).join('')}
   <ellipse cx="${x}" cy="${y-S(204)}" rx="${S(30)}" ry="${S(35)}" fill="#7a4a2a"/>
   <circle cx="${x-S(30)}" cy="${y-S(204)}" r="${S(7)}" fill="#6b3f23"/><circle cx="${x+S(30)}" cy="${y-S(204)}" r="${S(7)}" fill="#6b3f23"/>
   <circle cx="${x-S(32)}" cy="${y-S(196)}" r="${S(4)}" fill="#ffc531"/><circle cx="${x+S(32)}" cy="${y-S(196)}" r="${S(4)}" fill="#ffc531"/>
   <circle cx="${x-S(12)}" cy="${y-S(208)}" r="${S(11)}" fill="#ffffff" fill-opacity=".35" stroke="#1d1d1d" stroke-width="${S(3)}"/>
   <circle cx="${x+S(12)}" cy="${y-S(208)}" r="${S(11)}" fill="#ffffff" fill-opacity=".35" stroke="#1d1d1d" stroke-width="${S(3)}"/>
   <line x1="${x-S(1)}" y1="${y-S(209)}" x2="${x+S(1)}" y2="${y-S(209)}" stroke="#1d1d1d" stroke-width="${S(3)}"/>
   <circle cx="${x-S(12)}" cy="${y-S(207)}" r="${S(4)}" fill="#3b2314"/><circle cx="${x+S(12)}" cy="${y-S(207)}" r="${S(4)}" fill="#3b2314"/>
   <circle cx="${x-S(13)}" cy="${y-S(208.5)}" r="${S(1.3)}" fill="#fff"/><circle cx="${x+S(11)}" cy="${y-S(208.5)}" r="${S(1.3)}" fill="#fff"/>
   <path d="M${x-S(11)} ${y-S(188)} q${S(11)} ${S(10)} ${S(22)} 0" stroke="#5a1f1f" stroke-width="${S(3)}" fill="#fff" stroke-linecap="round"/>
  </g>`;
}

function targetG(id,cx,cy,rx,ry,label,lx,ly){return `<g class="target" data-t="${id}" tabindex="0" role="button" aria-label="${label}"><ellipse class="ring" cx="${cx}" cy="${cy}" rx="${rx}" ry="${ry}"/><text x="${lx??cx}" y="${ly??(cy+ry+18)}" text-anchor="middle">${label}</text></g>`}

function plantScene(extra=''){
  return `<svg viewBox="0 0 640 380" role="img" aria-label="A Venus flytrap in a pot, cut away to show the roots">
   <rect width="640" height="380" fill="#cfeefc"/><rect y="300" width="640" height="80" fill="#9fd36d"/>
   <circle cx="560" cy="64" r="36" fill="#ffe27a" opacity=".6"/>
   <g transform="translate(0 -10)">${flytrap(320,250,1.05,true)}</g>
   <g><rect x="270" y="252" width="100" height="44" rx="6" fill="#6b4226"/>
     <path d="M320 252 q-4 16 -26 34 M320 252 q2 20 -4 40 M320 252 q10 18 30 30 M310 262 q-14 4 -24 2 M332 262 q12 6 22 2" stroke="#f0d7a8" stroke-width="3.5" fill="none" stroke-linecap="round"/>
     <text x="320" y="312" text-anchor="middle" font-family="Baloo 2" font-weight="800" font-size="12" fill="#6b4226">pot cut open</text></g>
   ${extra}</svg>`;
}
function personScene(extra=''){
  return `<svg viewBox="0 0 640 380" role="img" aria-label="Dr. McHenry with her lungs, stomach and a body cell shown">
   <rect width="640" height="380" fill="#f3ecff"/><rect y="330" width="640" height="50" fill="#d9cdf2"/>
   ${drm(250,340,1.25)}
   <g opacity=".9"><path d="M222 168 q-14 4 -16 34 q2 22 14 22 q10 -2 12 -16 v-36z" fill="#f08aa0" stroke="#b44a62" stroke-width="2.5"/><path d="M278 168 q14 4 16 34 q-2 22 -14 22 q-10 -2 -12 -16 v-36z" fill="#f08aa0" stroke="#b44a62" stroke-width="2.5"/><line x1="250" y1="150" x2="250" y2="172" stroke="#b44a62" stroke-width="4"/></g>
   <path d="M256 236 q24 -4 26 14 q-2 18 -24 16 q-12 -2 -10 -14z" fill="#f2b05e" stroke="#b47424" stroke-width="2.5" opacity=".95"/>
   <g transform="translate(470 150)"><circle r="78" fill="#fff" stroke="#9b7ad6" stroke-width="4"/><circle r="70" fill="#ffe3ec"/><circle cx="-18" cy="-8" r="16" fill="#9b6bff"/>
    <g transform="translate(26 22) rotate(-20)"><ellipse rx="24" ry="12" fill="#ff9a5c" stroke="#c4581f" stroke-width="2.5"/><path d="M-16 0 q4 -7 8 0 t8 0 t8 0 t8 0" stroke="#c4581f" stroke-width="2" fill="none"/></g>
    <text y="-86" text-anchor="middle" font-family="Baloo 2" font-weight="800" font-size="15" fill="#5b3fa0">Her body cell, zoomed in</text></g>
   <line x1="290" y1="200" x2="394" y2="160" stroke="#9b7ad6" stroke-width="2.5" stroke-dasharray="6 5"/>
   ${extra}</svg>`;
}

/* ---------- game script ---------- */
const PARTS=['Meet','Feed the Plant','Plant Recipe','Fuel Dr. McHenry','Body Recipe','Big Cycle','Adventures'];
function steps(n){$('#steps').innerHTML=PARTS.map((p,k)=>`<i class="${k<n?'done':k===n?'on':''}">${p}</i>`).join('');}

function intro(){
  steps(0);
  stage.innerHTML=`<svg viewBox="0 0 640 380" role="img" aria-label="Dr. McHenry waving next to her Venus flytrap"><rect width="640" height="380" fill="#cfeefc"/><rect y="320" width="640" height="60" fill="#9fd36d"/>
   <g fill="#fff" opacity=".9"><circle cx="90" cy="70" r="26"/><circle cx="120" cy="60" r="32"/><circle cx="150" cy="72" r="24"/></g>
   ${drm(220,330,1.15,'wave')}
   <rect x="330" y="300" width="220" height="24" rx="6" fill="#b5835a" stroke="#7a4e2d" stroke-width="3"/>
   <g class="float">${flytrap(440,236,.95,true)}</g>
   <g transform="translate(470 66)"><rect x="-90" y="-26" width="180" height="46" rx="16" fill="#fff" stroke="#3f9d3a" stroke-width="3"/><text text-anchor="middle" y="5" font-family="Baloo 2" font-weight="800" font-size="20" fill="#23662a">Meet Snapper!</text></g></svg>`;
  panel.innerHTML=`<div class="panel"><div><div class="tag">Mission</div><h2>Help me take care of Snapper, my Venus flytrap!</h2>
   <p>Hi, scientists! Snapper is my favorite plant. Plants make their own food through <b>photosynthesis</b>. People get energy from food through <b>respiration</b>.</p>
   <p>First you will give Snapper what it needs. Then you will do the same for me! Finish every part to unlock our adventure photos and your secret code.</p>
   <p class="std">Standards: 4-LS1-1 (plant and animal structures), 5-LS1-1 (plants get what they need from air and water), MS-LS1-6 and MS-LS1-7 (photosynthesis and respiration, introduced).</p></div>
   <div class="row" style="align-self:center"><button class="btn sun" id="go">Start the mission</button><button class="btn" id="snd" aria-pressed="true" style="background:#fff;color:var(--ink);border-color:var(--line);box-shadow:0 5px 0 var(--line)">Sound on</button></div></div>`;
  $('#go').onclick=()=>{tone(523,.1);feedPlant();};
  $('#snd').onclick=e=>{sound=!sound;e.target.textContent=sound?'Sound on':'Sound off';e.target.setAttribute('aria-pressed',sound);};
}

function station({n,title,intro,sceneFn,targets,items,done}){
  steps(n);
  const placed={}; let sel=null;
  const draw=(extra='')=>{stage.innerHTML=sceneFn(targets.map(t=>targetG(...t)).join('')+extra);stage.classList.toggle('armed',!!sel);
    stage.querySelectorAll('.target').forEach(g=>{const id=g.dataset.t;if(Object.values(placed).includes(id))g.classList.add('filled');
      g.onclick=()=>drop(id);g.onkeydown=e=>{if(e.key==='Enter'||e.key===' '){e.preventDefault();drop(id);}};});
    Object.entries(placed).forEach(([it,tid])=>{const t=targets.find(x=>x[0]===tid);const svg=stage.querySelector('svg');
      const g=document.createElementNS('http://www.w3.org/2000/svg','g');g.setAttribute('pointer-events','none');const n=Object.entries(placed).filter(([a,b])=>b===tid).findIndex(([a])=>a===it);
      g.setAttribute('transform',`translate(${t[1]-20+(n-0.5)*30} ${t[2]-20}) scale(1)`);g.innerHTML=ICON[items.find(i=>i.id===it).icon].replace('<svg viewBox="0 0 40 40">','<g>').replace('</svg>','</g>');svg.appendChild(g);});
  };
  panel.innerHTML=`<div class="panel"><div><div class="tag">${title}</div>${intro}<p class="fb" id="fb" aria-live="polite"></p></div>
   <div><div class="hint">Tap a supply, then tap where it goes in the picture.</div><div class="tray" id="tray">${items.map(i=>`<button class="item" data-i="${i.id}">${ICON[i.icon]}${i.name}</button>`).join('')}</div>
   <div class="row" style="margin-top:12px"><button class="btn" id="next" hidden>Next</button></div></div></div>`;
  const fb=$('#fb');
  panel.querySelectorAll('.item').forEach(b=>b.onclick=()=>{panel.querySelectorAll('.item').forEach(x=>x.classList.remove('sel'));sel=b.dataset.i;b.classList.add('sel');stage.classList.add('armed');fb.className='fb';fb.textContent='Now tap where '+items.find(i=>i.id===sel).name.toLowerCase()+' should go.';});
  function drop(tid){
    if(!sel){fb.className='fb';fb.textContent='Pick a supply first.';return;}
    const it=items.find(i=>i.id===sel);
    if(it.to===tid){placed[sel]=tid;yay();if(it.chomp)chomp();fb.className='fb good';fb.innerHTML='Yes! '+it.why;
      panel.querySelector(`[data-i="${sel}"]`).classList.add('used');sel=null;draw(it.after||'');stage.classList.remove('armed');
      if(Object.keys(placed).length===items.length){const nx=$('#next');nx.hidden=false;nx.focus();nx.onclick=done;}}
    else{nope();fb.className='fb bad';fb.innerHTML='Not there. '+(it.hint||'Think about which part uses it.');stage.classList.remove('shake');void stage.offsetWidth;stage.classList.add('shake');}
  }
  draw();
}

function feedPlant(){
  station({n:1,title:'Part 1 · Feed the Plant',sceneFn:plantScene,
   intro:`<h2>What does Snapper need to make food?</h2><p>Give Snapper water, minerals, bugs, sunlight and air. Each supply goes to the plant part that takes it in.</p>`,
   targets:[['roots',320,270,62,28,'Roots',320,226],['leaves',190,150,70,40,'Leaves'],['trap',452,92,52,34,'Trap',452,52]],
   items:[
    {id:'water',icon:'water',name:'Water',to:'roots',why:'<b>Roots</b> soak up water from the soil. Water travels up the stem to the leaves.',hint:'Water is soaked up from the soil.'},
    {id:'min',icon:'minerals',name:'Minerals',to:'roots',why:'Most plants take in <b>nutrients and minerals</b> from the soil through their <b>roots</b>. Snapper grows in a swampy bog where the soil has very few nutrients...',hint:'Minerals are in the soil.'},
    {id:'bug',icon:'bug',name:'Bug',to:'trap',chomp:true,why:'SNAP! ...so Snapper gets extra <b>nutrients</b> by catching bugs in its <b>trap</b>. The bug is like a vitamin. Snapper still makes its own food from sunlight!',hint:'Which part snaps shut?'},
    {id:'sun',icon:'sun',name:'Sunlight',to:'leaves',why:'<b>Leaves</b> catch sunlight. Light is the energy that powers photosynthesis.',hint:'The flat green parts catch light.'},
    {id:'co2',icon:'co2',name:'Air (carbon dioxide)',to:'leaves',why:'<b>Leaves</b> take in carbon dioxide from the air through tiny holes.',hint:'Air goes in through tiny holes in the green parts.'}],
   done:plantRecipe});
}

function recipe({n,title,head,text,sceneHTML,slots,chips,done,doneMsg}){
  steps(n); stage.innerHTML=sceneHTML;
  let sel=null; const filled={};
  panel.innerHTML=`<div><div class="tag">${title}</div><h2>${head}</h2><p>${text}</p>
   <div class="eq" id="eq">${slots.map((s,k)=>s.op?`<span>${s.op}</span>`:`<button class="blank" data-k="${k}" aria-label="Empty blank">?</button>`).join('')}</div>
   <div class="hint">Tap a word, then tap a blank.</div><div class="chips">${chips.map(c=>`<button class="chip" data-c="${c}">${c}</button>`).join('')}</div>
   <p class="fb" id="fb" aria-live="polite"></p><button class="btn" id="next" hidden>Next</button></div>`;
  const fb=$('#fb');
  panel.querySelectorAll('.chip').forEach(c=>c.onclick=()=>{panel.querySelectorAll('.chip').forEach(x=>x.classList.remove('sel'));sel=c.dataset.c;c.classList.add('sel');});
  panel.querySelectorAll('.blank').forEach(b=>b.onclick=()=>{
    if(b.classList.contains('ok'))return; if(!sel){fb.className='fb';fb.textContent='Pick a word first.';return;}
    const k=+b.dataset.k, need=slots[k];
    const okSet=need.any||[need.a];
    const usedElsewhere=Object.values(filled).includes(sel);
    if(okSet.includes(sel)&&!usedElsewhere){filled[k]=sel;b.textContent=sel;b.classList.add('ok');yay();panel.querySelector(`.chip[data-c="${sel}"]`).classList.add('used');sel=null;fb.className='fb good';fb.textContent='Correct!';
      if(Object.keys(filled).length===slots.filter(s=>!s.op).length){fb.innerHTML=doneMsg;const nx=$('#next');nx.hidden=false;nx.focus();nx.onclick=done;}}
    else{nope();fb.className='fb bad';fb.textContent=need.tip||'Not that one. Try another blank or word.';b.classList.remove('shake');void b.offsetWidth;b.classList.add('shake');}
  });
}

function plantRecipe(){
  const sc=plantScene(`<g transform="translate(70 60)">${ICON.sun.replace('<svg viewBox="0 0 40 40">','<g transform="scale(2)">').replace('</svg>','</g>')}</g>
    <g class="float"><g transform="translate(520 120)">${ICON.o2.replace('<svg viewBox="0 0 40 40">','<g transform="scale(1.6)">').replace('</svg>','</g>')}</g><g transform="translate(560 190)">${ICON.o2.replace('<svg viewBox="0 0 40 40">','<g transform="scale(1.2)">').replace('</svg>','</g>')}</g></g>
    <g transform="translate(130 250)">${ICON.sugar.replace('<svg viewBox="0 0 40 40">','<g transform="scale(1.6)">').replace('</svg>','</g>')}</g><text x="162" y="330" text-anchor="middle" font-family="Baloo 2" font-weight="800" font-size="15" fill="#23662a">sugar = plant food</text>`);
  recipe({n:2,title:'Part 2 · Snapper\'s Food Recipe',sceneHTML:sc,head:'Photosynthesis: how a plant makes its own food',
   text:'Inside the leaves, the plant uses <b>sunlight</b> to turn <b>water</b> and <b>carbon dioxide</b> into <b>sugar</b> (its food) and <b>oxygen</b>. Fill in the recipe.',
   slots:[{any:['sunlight','water','carbon dioxide'],tip:'These blanks are what goes IN.'},{op:'+'},{any:['sunlight','water','carbon dioxide'],tip:'These blanks are what goes IN.'},{op:'+'},{any:['sunlight','water','carbon dioxide'],tip:'These blanks are what goes IN.'},{op:'→'},{any:['sugar','oxygen'],tip:'These blanks are what the plant MAKES.'},{op:'+'},{any:['sugar','oxygen'],tip:'These blanks are what the plant MAKES.'}],
   chips:['oxygen','water','sugar','sunlight','carbon dioxide'],
   doneMsg:'You did it! <b>Sunlight + water + carbon dioxide → sugar + oxygen.</b> Snapper keeps the sugar for energy and growth, and lets the oxygen out into the air. Bugs give extra nutrients, but the food comes from photosynthesis!',
   done:fuelMe});
}

function fuelMe(){
  station({n:3,title:'Part 3 · Fuel Dr. McHenry',sceneFn:personScene,
   intro:`<h2>Now it's my turn! I can't make food from sunlight.</h2><p>People and animals have to <b>eat</b> food and <b>breathe</b> oxygen. Give my body what it needs, and send it to the right place.</p>`,
   targets:[['stomach',270,250,38,28,'Stomach',270,300],['lungs',250,196,56,40,'Lungs',178,198],['cell',470,150,80,80,'Her cells',470,256]],
   items:[
    {id:'food',icon:'food',name:'Food',to:'stomach',why:'My <b>stomach</b> breaks food down into tiny pieces, including <b>sugar</b>. Did you know? All food energy started as sunlight caught by a plant!',hint:'Where does food go after you swallow it?'},
    {id:'o2',icon:'o2',name:'Oxygen',to:'lungs',why:'I breathe in air, and my <b>lungs</b> pass the <b>oxygen</b> into my blood.',hint:'You breathe it in.'},
    {id:'sugar',icon:'sugar',name:'Sugar from food',to:'cell',why:'My <b>blood</b> carries the sugar to every one of my <b>cells</b>.',hint:'Blood delivers this to every tiny part of the body.'},
    {id:'o2b',icon:'o2',name:'Oxygen in my blood',to:'cell',why:'My blood brings the oxygen to my <b>cells</b> too. Now my cells have sugar AND oxygen!',hint:'Blood delivers this to every tiny part of the body.'}],
   done:bodyRecipe});
}

function bodyRecipe(){
  const sc=personScene(`<g class="float"><g transform="translate(585 236)">${ICON.energy.replace('<svg viewBox="0 0 40 40">','<g transform="scale(1.7)">').replace('</svg>','</g>')}</g></g>
   <g transform="translate(400 262)">${ICON.co2.replace('<svg viewBox="0 0 40 40">','<g transform="scale(1.4)">').replace('</svg>','</g>')}</g>`);
  recipe({n:4,title:'Part 4 · Dr. McHenry\'s Energy Recipe',sceneHTML:sc,head:'Respiration: how my cells get energy from food',
   text:'Inside my cells, tiny power plants called <b>mitochondria</b> use <b>oxygen</b> to break down <b>sugar</b>. That releases <b>energy</b> so I can walk, think and teach! It also makes <b>carbon dioxide</b> and <b>water</b>. Fill in the recipe.',
   slots:[{any:['sugar','oxygen'],tip:'These blanks are what my cells USE.'},{op:'+'},{any:['sugar','oxygen'],tip:'These blanks are what my cells USE.'},{op:'→'},{any:['energy','carbon dioxide','water'],tip:'These blanks are what my cells MAKE.'},{op:'+'},{any:['energy','carbon dioxide','water'],tip:'These blanks are what my cells MAKE.'},{op:'+'},{any:['energy','carbon dioxide','water'],tip:'These blanks are what my cells MAKE.'}],
   chips:['carbon dioxide','sugar','energy','sunlight','water','oxygen'],
   doneMsg:'Great job! <b>Sugar + oxygen → energy + carbon dioxide + water.</b> Notice: sunlight is not in MY recipe. My energy came from the sun only because a plant caught it first.',
   done:cycle});
}

function cycle(){
  station({n:5,title:'Part 5 · The Big Cycle',
   sceneFn:extra=>`<svg viewBox="0 0 640 380" role="img" aria-label="Dr. McHenry and Snapper trading gases"><rect width="640" height="380" fill="#e4f6ff"/><rect y="320" width="640" height="60" fill="#9fd36d"/>
     ${drm(170,330,1.1)}<g>${flytrap(470,250,.9,true)}</g>
     <path d="M250 110 Q340 50 420 110" stroke="#3b9bd6" stroke-width="4" fill="none" stroke-dasharray="8 6"/><polygon points="420,110 404,96 400,114" fill="#3b9bd6"/>
     <path d="M420 200 Q340 260 250 200" stroke="#7c8b99" stroke-width="4" fill="none" stroke-dasharray="8 6"/><polygon points="250,200 266,188 268,206" fill="#7c8b99"/>${extra}</svg>`,
   intro:`<h2>Snapper and I help each other!</h2><p>What I breathe out, Snapper uses. What Snapper lets out, I breathe in. Send each gas to the one who needs it.</p>`,
   targets:[['plant',470,150,70,60,'Snapper\'s leaves',470,62],['me',170,205,52,40,'Dr. McHenry\'s lungs',170,268]],
   items:[
    {id:'co2',icon:'co2',name:'Carbon dioxide I breathe out',to:'plant',why:'Snapper\'s leaves use my carbon dioxide for photosynthesis.',hint:'Which one USES carbon dioxide to make food?'},
    {id:'o2',icon:'o2',name:'Oxygen Snapper lets out',to:'me',why:'I breathe in the oxygen Snapper made. We need each other!',hint:'Who breathes oxygen in?'}],
   done:()=>quiz(0)});
}

const Q=[
 {q:'Where does a plant\'s FOOD come from?',o:['The soil','Bugs it eats','It makes sugar in its leaves using sunlight (photosynthesis)','Rain'],a:2,why:'Plants make their own food. Snapper catches bugs only for extra nutrients.'},
 {q:'Why does a Venus flytrap catch bugs?',o:['Its bog soil has few nutrients, so bugs give it extra nutrients','It has no leaves','It cannot use sunlight','To get water'],a:0,why:'Most plants get nutrients from the soil. Flytraps live where the soil is poor, so bugs fill the gap.'},
 {q:'What do Dr. McHenry\'s cells need to release energy?',o:['Sunlight and water','Sugar and oxygen','Carbon dioxide only','Bugs'],a:1,why:'Respiration: sugar + oxygen → energy + carbon dioxide + water.'},
 {q:'Which plant part takes in water?',o:['Trap','Flower','Roots','Leaves'],a:2,why:'Roots soak up water and minerals from the soil.'}];
function quiz(i=0){
  steps(5); if(i===0)stage.innerHTML=`<svg viewBox="0 0 640 260" role="img" aria-label="Dr. McHenry and Snapper"><rect width="640" height="260" fill="#fff6d6"/>${drm(200,250,.85,'wave')}<g>${flytrap(430,160,.7,true)}</g><text x="320" y="40" text-anchor="middle" font-family="Baloo 2" font-weight="800" font-size="24" fill="#23662a">Final check before our adventure!</text></svg>`;
  const it=Q[i];
  panel.innerHTML=`<div><div class="tag">Question ${i+1} of ${Q.length}</div><h2>${it.q}</h2><div class="opts">${it.o.map((o,k)=>`<button class="opt" data-k="${k}">${o}</button>`).join('')}</div><p class="fb" id="fb" aria-live="polite"></p><button class="btn" id="next" hidden>${i<Q.length-1?'Next question':'See our adventures!'}</button></div>`;
  panel.querySelectorAll('.opt').forEach(b=>b.onclick=()=>{const fb=$('#fb');
    if(+b.dataset.k===it.a){b.classList.add('right');yay();panel.querySelectorAll('.opt').forEach(x=>x.disabled=true);fb.className='fb good';fb.textContent='Correct! '+it.why;const nx=$('#next');nx.hidden=false;nx.focus();nx.onclick=()=>i<Q.length-1?quiz(i+1):finale();}
    else{b.classList.add('wrong');b.disabled=true;nope();fb.className='fb bad';fb.textContent='Not quite. Try again!';}});
}

/* ---------- finale ---------- */
const scenes={
 drive:()=>`<svg viewBox="0 0 400 260" role="img" aria-label="Dr. McHenry driving with Snapper buckled in"><rect width="400" height="260" fill="#bfe6fb"/><rect y="200" width="400" height="60" fill="#6c6f7a"/><g stroke="#fff" stroke-width="5" stroke-dasharray="26 18"><line x1="0" y1="232" x2="400" y2="232"/></g>
   <g fill="#8fd16a"><circle cx="40" cy="190" r="26"/><circle cx="360" cy="186" r="30"/></g>
   <path d="M40 190 Q60 120 140 110 L280 110 Q330 112 352 150 L370 190 Z" fill="#d8433b" stroke="#8c2620" stroke-width="4"/>
   <path d="M120 120 L160 120 L160 168 L80 168 Q92 132 120 120Z" fill="#dff4ff" stroke="#8c2620" stroke-width="3"/><path d="M170 120 L270 120 Q300 124 316 168 L170 168Z" fill="#dff4ff" stroke="#8c2620" stroke-width="3"/>
   <clipPath id="w1"><path d="M170 120 L270 120 Q300 124 316 168 L170 168Z"/></clipPath><g clip-path="url(#w1)">${drm(232,236,.42,'drive')}</g>
   <clipPath id="w2"><path d="M120 120 L160 120 L160 168 L80 168 Q92 132 120 120Z"/></clipPath><g clip-path="url(#w2)">${flytrap(130,160,.3,true)}<line x1="100" y1="132" x2="158" y2="166" stroke="#2d3e66" stroke-width="5"/></g>
   <circle cx="110" cy="196" r="24" fill="#222"/><circle cx="110" cy="196" r="10" fill="#aaa"/><circle cx="310" cy="196" r="24" fill="#222"/><circle cx="310" cy="196" r="10" fill="#aaa"/></svg>`,
 movies:()=>`<svg viewBox="0 0 400 260" role="img" aria-label="Dr. McHenry and Snapper watching a movie with popcorn"><rect width="400" height="260" fill="#241a38"/><rect x="40" y="20" width="320" height="110" rx="6" fill="#fff6c8"/><text x="200" y="84" text-anchor="middle" font-family="Baloo 2" font-weight="800" font-size="26" fill="#23662a">THE PLANT WHO SNAPPED</text>
   <polygon points="40,130 360,130 400,180 0,180" fill="#fff6c8" opacity=".12"/>
   <rect x="0" y="180" width="400" height="80" fill="#7a2335"/><g fill="#9b2c44"><rect x="60" y="170" width="110" height="80" rx="16"/><rect x="230" y="170" width="110" height="80" rx="16"/></g>
   <clipPath id="m1"><rect x="0" y="0" width="400" height="215"/></clipPath><g clip-path="url(#m1)">${drm(115,330,.62,'sit')}</g>
   ${flytrap(285,178,.42,true)}
   <g transform="translate(180 168)"><path d="M0 0 h26 l-4 34 h-18z" fill="#fff" stroke="#d8433b" stroke-width="3"/><line x1="8" y1="2" x2="6" y2="32" stroke="#d8433b" stroke-width="3"/><line x1="18" y1="2" x2="20" y2="32" stroke="#d8433b" stroke-width="3"/>${[0,8,16,24,4,12,20].map((x,k)=>`<circle cx="${x+1}" cy="${-4-(k>3?6:0)}" r="5" fill="#fff4b0"/>`).join('')}</g></svg>`,
 shop:()=>`<svg viewBox="0 0 400 260" role="img" aria-label="Dr. McHenry grocery shopping with Snapper in the cart"><rect width="400" height="260" fill="#f4f0e6"/><rect y="220" width="400" height="40" fill="#d9cdb8"/>
   <g>${[0,1,2].map(r=>`<rect x="10" y="${30+r*55}" width="160" height="10" fill="#b49a78"/>`).join('')}${['#d8433b','#ffc531','#3f9d3a','#4fb3f0','#f08aa0','#e88a5a'].map((c,k)=>`<rect x="${18+k*25}" y="12" width="18" height="18" rx="3" fill="${c}"/><circle cx="${27+k*25}" cy="72" r="9" fill="${c}"/><rect x="${18+k*25}" y="120" width="18" height="20" rx="4" fill="${c}"/>`).join('')}</g>
   <text x="90" y="170" text-anchor="middle" font-family="Baloo 2" font-weight="800" font-size="16" fill="#7a4e2d">PRODUCE</text>
   ${drm(200,236,.78,'cart')}
   <g><path d="M262 150 h110 l-12 50 h-86z" fill="none" stroke="#7c8b99" stroke-width="5"/><g stroke="#7c8b99" stroke-width="2">${[0,1,2,3,4].map(k=>`<line x1="${276+k*20}" y1="150" x2="${280+k*16}" y2="200"/>`).join('')}</g><line x1="262" y1="150" x2="252" y2="132" stroke="#7c8b99" stroke-width="5"/><circle cx="286" cy="214" r="9" fill="#333"/><circle cx="352" cy="214" r="9" fill="#333"/>
   ${flytrap(320,150,.32,true)}</g></svg>`,
 catch:()=>`<svg viewBox="0 0 400 260" role="img" aria-label="Dr. McHenry playing catch with Snapper in the park"><rect width="400" height="260" fill="#bfe6fb"/><circle cx="350" cy="44" r="26" fill="#ffc531"/><rect y="200" width="400" height="60" fill="#8fd16a"/>
   <g fill="#5fae45"><circle cx="40" cy="150" r="40"/><rect x="34" y="170" width="12" height="40" fill="#7a4e2d"/></g>
   ${drm(120,236,.78,'throw')}
   <path d="M190 70 Q250 20 300 98" stroke="#fff" stroke-width="3" fill="none" stroke-dasharray="6 6"/><circle cx="290" cy="82" r="10" fill="#ffd84d" stroke="#d79a00" stroke-width="2.5"/>
   ${flytrap(310,186,.55,true)}</svg>`
};
function finale(){
  steps(6);
  stage.innerHTML=`<div class="tag">Part 6 · Adventures</div><h2 style="margin-bottom:10px">Snapper and I go everywhere together!</h2>
   <div class="gallery">
    <div class="photo">${scenes.drive()}<b>Road trip! Snapper is buckled in.</b></div>
    <div class="photo">${scenes.movies()}<b>Movie night with popcorn</b></div>
    <div class="photo">${scenes.shop()}<b>Grocery shopping</b></div>
    <div class="photo">${scenes.catch()}<b>Playing catch in the park</b></div>
   </div>`;
  const code=String.fromCharCode(86,101,110,117,115,102,108,121,116,114,97,112);
  panel.innerHTML=`<div class="panel"><div><div class="tag">Mission complete</div><h2>Thank you for taking care of us, scientist!</h2>
   <p>You showed how a plant makes food with <b>photosynthesis</b> and how my body gets energy with <b>respiration</b>. Your secret code is:</p></div>
   <div><div class="code" id="code">${code}</div><div class="row" style="margin-top:10px"><button class="btn sun" id="cp">Copy code</button><button class="btn" id="again">Play again</button></div><p class="fb" id="fb" aria-live="polite"></p></div></div>`;
  [523,659,784,1047].forEach((f,k)=>tone(f,.25,'triangle',.07,k*.1));
  $('#cp').onclick=()=>{const fb=$('#fb');navigator.clipboard.writeText(code).then(()=>{fb.className='fb good';fb.textContent='Copied! Type it where your teacher asked.';}).catch(()=>{const r=document.createRange();r.selectNodeContents($('#code'));const s=getSelection();s.removeAllRanges();s.addRange(r);fb.className='fb';fb.textContent='Code selected. Copy it or write it down.';});};
  $('#again').onclick=()=>intro();
}
intro();
})();
</script>
</body>
</html>
