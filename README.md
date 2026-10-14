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
.photo:nth-child(2n){transform:rotat
