<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Hồng Quân – Giải Bài Tập Tin</title>
<meta name="theme-color" content="#070a1a">
<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>📘</text></svg>">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;600;700;800;900&family=JetBrains+Mono:wght@500;700&display=swap" rel="stylesheet">
<style>
/* ============ RESET & BIẾN ============ */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --bg:#05070f;
  --cyan:#22d3ee;--blue:#3b82f6;--purple:#a855f7;--pink:#ec4899;
  --text:#eef2ff;--text-dim:#a5b0d4;
  --glass:rgba(15,20,45,.55);
  --glass-brd:rgba(140,160,255,.18);
  --glass-brd-hi:rgba(140,160,255,.4);
  --ok:#10b981;--err:#f43f5e;
  --grad-main:linear-gradient(135deg,#22d3ee 0%,#3b82f6 45%,#a855f7 75%,#ec4899 100%);
  --grad-btn:linear-gradient(135deg,#22d3ee,#3b82f6);
  --grad-btn2:linear-gradient(135deg,#a855f7,#ec4899);
  --shadow-soft:0 8px 32px rgba(0,0,0,.35);
  --shadow-glow-cyan:0 0 30px rgba(34,211,238,.35),0 0 60px rgba(34,211,238,.15);
  --shadow-glow-pink:0 0 30px rgba(236,72,153,.35),0 0 60px rgba(168,85,247,.15);
  --radius:20px;
}
html{scroll-behavior:smooth}
body{
  font-family:"Be Vietnam Pro",system-ui,-apple-system,sans-serif;
  color:var(--text);background:var(--bg);min-height:100vh;
  overflow-x:hidden;line-height:1.65;letter-spacing:.15px;
  -webkit-font-smoothing:antialiased;position:relative;
  background:
    radial-gradient(1400px 900px at 10% -20%, rgba(34,211,238,.22), transparent 55%),
    radial-gradient(1200px 800px at 110% 15%, rgba(168,85,247,.25), transparent 55%),
    radial-gradient(1000px 700px at 50% 130%, rgba(236,72,153,.18), transparent 55%),
    linear-gradient(180deg,#05070f 0%,#0a0f24 50%,#05070f 100%);
}

/* ============ NỀN ĐỘNG ============ */
.bg-orbs{position:fixed;inset:0;z-index:0;overflow:hidden;pointer-events:none}
.orb{position:absolute;border-radius:50%;filter:blur(80px);opacity:.5;mix-blend-mode:screen;animation:orbFloat 20s ease-in-out infinite}
.orb:nth-child(1){width:500px;height:500px;background:#22d3ee;top:-100px;left:-100px;animation-delay:0s}
.orb:nth-child(2){width:600px;height:600px;background:#a855f7;top:20%;right:-200px;animation-delay:-7s}
.orb:nth-child(3){width:450px;height:450px;background:#ec4899;bottom:-150px;left:30%;animation-delay:-14s}
@keyframes orbFloat{
  0%,100%{transform:translate(0,0) scale(1)}
  33%{transform:translate(60px,-40px) scale(1.1)}
  66%{transform:translate(-40px,60px) scale(.95)}
}

.bg-grid{position:fixed;inset:0;z-index:0;pointer-events:none;opacity:.4;
  background-image:
    linear-gradient(rgba(120,150,255,.08) 1px,transparent 1px),
    linear-gradient(90deg,rgba(120,150,255,.08) 1px,transparent 1px);
  background-size:60px 60px;
  mask-image:radial-gradient(ellipse at center,black 30%,transparent 80%);
  -webkit-mask-image:radial-gradient(ellipse at center,black 30%,transparent 80%);
}

.bg-noise{position:fixed;inset:0;z-index:1;pointer-events:none;opacity:.03;
  background-image:url("data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' width='200' height='200'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='.9'/></filter><rect width='200' height='200' filter='url(%23n)'/></svg>")}

/* Ký hiệu bay */
.symbols-layer{position:fixed;inset:0;z-index:2;pointer-events:none;overflow:hidden}
.symbol{position:absolute;font-size:20px;color:rgba(180,220,255,.3);
  text-shadow:0 0 14px rgba(34,211,238,.5),0 0 26px rgba(168,85,247,.3);
  animation:symbolFloat linear infinite;user-select:none;font-weight:700;will-change:transform}
@keyframes symbolFloat{
  0%{transform:translate3d(0,110vh,0) rotate(0) scale(.85);opacity:0}
  8%{opacity:.7}92%{opacity:.7}
  100%{transform:translate3d(var(--drift,60px),-10vh,0) rotate(360deg) scale(1.1);opacity:0}
}

/* ============ HEADER ============ */
.site-header{
  position:sticky;top:0;z-index:100;
  display:flex;align-items:center;justify-content:space-between;gap:16px;
  padding:14px clamp(16px,4vw,48px);
  background:rgba(8,12,28,.65);
  backdrop-filter:blur(20px) saturate(180%);
  -webkit-backdrop-filter:blur(20px) saturate(180%);
  border-bottom:1px solid rgba(140,160,255,.12);
  box-shadow:0 4px 30px rgba(0,0,0,.3);
}
.brand{display:flex;align-items:center;gap:14px}
.logo{
  width:50px;height:50px;display:grid;place-items:center;
  background:linear-gradient(135deg,rgba(34,211,238,.15),rgba(168,85,247,.15));
  border:1px solid rgba(140,160,255,.3);border-radius:14px;
  box-shadow:0 0 20px rgba(34,211,238,.35);
  transition:.3s;
}
.logo:hover{transform:rotate(-8deg) scale(1.08);box-shadow:0 0 30px rgba(34,211,238,.6)}
.logo svg{width:30px;height:30px;filter:drop-shadow(0 0 6px rgba(34,211,238,.7))}
.brand-text h1{
  font-size:clamp(19px,2.6vw,24px);font-weight:900;letter-spacing:.3px;
  line-height:1.1;
  background:var(--grad-main);
  -webkit-background-clip:text;background-clip:text;color:transparent;
  background-size:200% 200%;animation:gradShift 6s ease infinite;
}
@keyframes gradShift{0%,100%{background-position:0% 50%}50%{background-position:100% 50%}}
.brand-text span{
  display:block;font-size:11.5px;letter-spacing:2.8px;text-transform:uppercase;
  color:var(--text-dim);margin-top:4px;font-weight:600;
}

/* ============ MUSIC PLAYER ============ */
.music-player{
  display:flex;align-items:center;gap:8px;
  padding:6px 8px 6px 16px;border-radius:999px;
  background:rgba(15,20,45,.7);backdrop-filter:blur(12px);
  border:1px solid rgba(140,160,255,.25);
  transition:.3s;max-width:340px;
}
.music-player:hover{border-color:rgba(34,211,238,.5);box-shadow:var(--shadow-glow-cyan)}
.music-player.playing{
  background:linear-gradient(135deg,rgba(34,211,238,.2),rgba(168,85,247,.25));
  border-color:rgba(34,211,238,.55);box-shadow:var(--shadow-glow-cyan);
}
.music-ctrl{
  width:36px;height:36px;border-radius:50%;border:none;cursor:pointer;
  background:rgba(8,12,28,.6);color:var(--cyan);font-size:14px;
  display:grid;place-items:center;transition:.25s;flex-shrink:0;
}
.music-ctrl:hover{background:rgba(34,211,238,.25);transform:scale(1.12)}
.music-info{flex:1;min-width:0;overflow:hidden}
.music-title{font-size:12.5px;font-weight:700;color:var(--text);
  white-space:nowrap;overflow:hidden;text-overflow:ellipsis;display:block;line-height:1.3}
.music-title .dot{
  display:inline-block;width:6px;height:6px;border-radius:50%;
  background:var(--cyan);margin-right:6px;box-shadow:0 0 10px var(--cyan);
  vertical-align:middle;opacity:0;animation:pulse 1.2s ease-in-out infinite;
}
.music-player.playing .music-title .dot{opacity:1}
@keyframes pulse{0%,100%{transform:scale(1);opacity:1}50%{transform:scale(.55);opacity:.6}}
.music-toggle{
  width:40px;height:40px;border-radius:50%;border:none;cursor:pointer;
  background:var(--grad-btn);color:#04121a;font-size:15px;font-weight:900;
  display:grid;place-items:center;transition:.3s;flex-shrink:0;
  box-shadow:0 0 16px rgba(34,211,238,.55);
}
.music-toggle:hover{transform:scale(1.12);box-shadow:0 0 26px rgba(34,211,238,.9)}

/* ============ LAYOUT ============ */
main{position:relative;z-index:10;max-width:1200px;margin:0 auto;
  padding:clamp(30px,5vw,64px) clamp(16px,4vw,40px) 80px}

/* ============ HERO ============ */
.hero{text-align:center;padding:30px 0 60px}
.hero-badge{
  display:inline-flex;align-items:center;gap:8px;
  padding:9px 22px;margin-bottom:26px;border-radius:999px;
  font-size:13.5px;font-weight:600;color:#ffe4f0;
  background:linear-gradient(135deg,rgba(34,211,238,.15),rgba(236,72,153,.15));
  border:1px solid rgba(236,72,153,.4);
  box-shadow:0 0 24px rgba(236,72,153,.25);
  backdrop-filter:blur(10px);
}
.hero-badge::before{content:"●";color:var(--ok);font-size:10px;animation:pulse 2s infinite}
.hero-title{
  font-size:clamp(34px,7vw,68px);font-weight:900;line-height:1.05;
  letter-spacing:-1.2px;text-shadow:0 6px 32px rgba(0,0,0,.5);
}
.grad{
  display:block;margin-top:8px;
  background:var(--grad-main);
  background-size:200% 200%;animation:gradShift 6s ease infinite;
  -webkit-background-clip:text;background-clip:text;color:transparent;
  filter:drop-shadow(0 0 30px rgba(168,85,247,.5));
}
.hero-desc{max-width:680px;margin:26px auto 0;color:var(--text-dim);
  font-size:clamp(15px,1.8vw,17px);font-weight:500;line-height:1.7}
.hero-desc strong{color:var(--cyan);font-weight:700;text-shadow:0 0 12px rgba(34,211,238,.5)}
.hero-actions{display:flex;flex-wrap:wrap;justify-content:center;gap:14px;margin-top:38px}
.hero-stats{
  display:grid;gap:16px;margin-top:52px;
  grid-template-columns:repeat(auto-fit,minmax(160px,1fr));
  max-width:760px;margin-left:auto;margin-right:auto;
}
.hero-stats li{
  padding:20px 16px;border-radius:16px;text-align:center;list-style:none;
  background:var(--glass);backdrop-filter:blur(16px);
  border:1px solid var(--glass-brd);transition:.35s;cursor:default;
}
.hero-stats li:hover{
  transform:translateY(-6px);border-color:rgba(34,211,238,.5);
  box-shadow:var(--shadow-glow-cyan);
}
.hero-stats strong{
  display:block;font-size:22px;color:var(--cyan);font-weight:900;
  letter-spacing:.5px;text-shadow:0 0 18px rgba(34,211,238,.7);
}
.hero-stats span{font-size:12.5px;color:var(--text-dim);font-weight:500;margin-top:6px;display:block}

/* ============ BUTTONS ============ */
.btn{
  position:relative;display:inline-flex;align-items:center;justify-content:center;
  gap:10px;padding:15px 32px;border:none;border-radius:14px;
  font-family:inherit;font-size:15.5px;font-weight:800;letter-spacing:.4px;
  cursor:pointer;text-decoration:none;transition:.3s;white-space:nowrap;
  overflow:hidden;
}
.btn::before{
  content:"";position:absolute;top:0;left:-100%;width:100%;height:100%;
  background:linear-gradient(90deg,transparent,rgba(255,255,255,.25),transparent);
  transition:.6s;
}
.btn:hover::before{left:100%}
.btn-primary{
  color:#04121a;background:var(--grad-btn);
  box-shadow:0 8px 28px rgba(34,211,238,.45);
}
.btn-primary:hover{transform:translateY(-3px);box-shadow:0 12px 38px rgba(34,211,238,.7)}
.btn-purple{
  color:#fff;background:var(--grad-btn2);
  box-shadow:0 8px 28px rgba(168,85,247,.45);
}
.btn-purple:hover{transform:translateY(-3px);box-shadow:0 12px 38px rgba(168,85,247,.7)}
.btn-ghost{
  color:var(--text);background:rgba(140,160,255,.08);
  border:1px solid rgba(140,160,255,.35);backdrop-filter:blur(10px);
}
.btn-ghost:hover{transform:translateY(-3px);border-color:var(--cyan);background:rgba(34,211,238,.12)}
.btn-block{width:100%;margin-top:8px}
.btn:disabled{opacity:.55;cursor:not-allowed;transform:none!important}

/* ============ FORMS GRID ============ */
.forms-grid{
  display:grid;gap:28px;
  grid-template-columns:repeat(auto-fit,minmax(360px,1fr));
}

/* ============ PANEL (glassmorphism) ============ */
.panel{
  position:relative;padding:clamp(24px,3vw,36px);
  border-radius:var(--radius);overflow:hidden;
  background:var(--glass);backdrop-filter:blur(24px) saturate(180%);
  -webkit-backdrop-filter:blur(24px) saturate(180%);
  border:1px solid var(--glass-brd);
  box-shadow:var(--shadow-soft);
  transition:.35s;
}
.panel:hover{border-color:var(--glass-brd-hi);box-shadow:0 12px 48px rgba(0,0,0,.5)}
.panel::before{
  content:"";position:absolute;top:0;left:0;right:0;height:4px;
  background:var(--grad-main);background-size:200% 100%;
  animation:gradShift 6s ease infinite;
}
.panel::after{
  content:"";position:absolute;top:-50%;right:-50%;width:200%;height:200%;
  background:radial-gradient(circle,rgba(34,211,238,.06),transparent 60%);
  pointer-events:none;opacity:0;transition:.5s;
}
.panel:hover::after{opacity:1}

.panel-head{margin-bottom:28px;position:relative;z-index:1}
.panel-head h3{
  font-size:clamp(20px,2.6vw,24px);font-weight:900;margin-bottom:10px;
  background:var(--grad-main);background-size:200% 200%;
  animation:gradShift 6s ease infinite;
  -webkit-background-clip:text;background-clip:text;color:transparent;
  letter-spacing:-.3px;display:flex;align-items:center;gap:10px;
}
.panel-head p{font-size:14px;color:var(--text-dim);font-weight:500;line-height:1.65}

/* ============ FIELD ============ */
.field{margin-bottom:18px;position:relative;z-index:1}
.field label{
  display:block;font-size:13.5px;font-weight:700;color:#d5ddf5;
  margin-bottom:8px;letter-spacing:.3px;text-transform:uppercase;
}
.req{color:var(--pink);font-weight:900}
.grid-2{display:grid;gap:16px;grid-template-columns:1fr 1fr}
input,select,textarea{
  width:100%;padding:14px 18px;font-family:inherit;
  font-size:14.5px;font-weight:500;color:var(--text);
  background:rgba(5,8,20,.6);
  border:1.5px solid rgba(140,160,255,.22);border-radius:12px;
  transition:.25s;outline:none;letter-spacing:.15px;
  backdrop-filter:blur(8px);
}
input::placeholder,textarea::placeholder{color:#7a86ad;font-weight:400}
input:hover,select:hover,textarea:hover{border-color:rgba(140,160,255,.4)}
input:focus,select:focus,textarea:focus{
  border-color:var(--cyan);background:rgba(5,8,20,.85);
  box-shadow:0 0 0 4px rgba(34,211,238,.15),0 0 24px rgba(34,211,238,.25);
}
textarea{resize:vertical;min-height:130px;line-height:1.7;font-family:inherit}
select{
  cursor:pointer;appearance:none;
  background-image:url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%2322d3ee' stroke-width='3' stroke-linecap='round'><polyline points='6 9 12 15 18 9'/></svg>");
  background-repeat:no-repeat;background-position:right 16px center;padding-right:44px;
}
select option{background:#0a0f24;color:var(--text);font-family:inherit;padding:12px}
.form-status{
  margin-top:16px;font-size:13.5px;font-weight:700;
  min-height:22px;text-align:center;letter-spacing:.3px;
  transition:.3s;
}
.form-status.ok{color:var(--ok);text-shadow:0 0 12px rgba(16,185,129,.5)}
.form-status.err{color:var(--err);text-shadow:0 0 12px rgba(244,63,94,.5)}
.form-status.loading{color:var(--cyan);text-shadow:0 0 12px rgba(34,211,238,.5)}

/* ============ KEY INFO ============ */
.key-info{margin-top:72px;text-align:center}
.section-title{
  font-size:clamp(24px,3.4vw,34px);font-weight:900;
  margin-bottom:32px;letter-spacing:-.5px;
}
.key-grid{
  display:grid;gap:20px;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
}
.key-card{
  padding:28px 24px;border-radius:16px;text-align:left;
  background:var(--glass);backdrop-filter:blur(16px);
  border:1px solid var(--glass-brd);transition:.35s;position:relative;overflow:hidden;
}
.key-card::before{
  content:"";position:absolute;top:0;left:0;width:100%;height:3px;
  background:var(--grad-btn);opacity:0;transition:.3s;
}
.key-card:hover{
  transform:translateY(-6px);border-color:rgba(34,211,238,.55);
  box-shadow:var(--shadow-glow-cyan);
}
.key-card:hover::before{opacity:1}
.key-card h4{
  font-size:18px;margin-bottom:10px;color:var(--cyan);font-weight:900;
  letter-spacing:.3px;text-shadow:0 0 14px rgba(34,211,238,.5);
}
.key-card p{font-size:13.5px;color:var(--text-dim);line-height:1.65;font-weight:500}
.key-card--vip{background:linear-gradient(180deg,rgba(236,72,153,.1),rgba(168,85,247,.08))}
.key-card--vip::before{background:var(--grad-btn2);opacity:1}
.key-card--vip h4{color:var(--pink);text-shadow:0 0 14px rgba(236,72,153,.6)}
.key-card--vip:hover{border-color:rgba(236,72,153,.55);box-shadow:var(--shadow-glow-pink)}
.key-note{
  margin-top:30px;font-size:13.5px;color:var(--text-dim);
  max-width:820px;margin-left:auto;margin-right:auto;line-height:1.75;font-weight:500;
  padding:18px 24px;border-radius:14px;
  background:rgba(140,160,255,.06);border:1px dashed rgba(140,160,255,.25);
}
.key-note strong{color:var(--cyan);font-weight:700}

/* ============ FOOTER ============ */
.site-footer{
  position:relative;z-index:10;text-align:center;
  padding:32px 20px 40px;
  border-top:1px solid rgba(140,160,255,.12);
  font-size:13.5px;color:var(--text-dim);font-weight:500;
  background:rgba(5,8,20,.5);backdrop-filter:blur(10px);
}
.site-footer strong{
  background:var(--grad-main);background-size:200% 200%;
  animation:gradShift 6s ease infinite;
  -webkit-background-clip:text;background-clip:text;color:transparent;
  font-weight:800;
}

/* ============ TOAST ============ */
.toast-wrap{
  position:fixed;bottom:24px;right:24px;z-index:9999;
  display:flex;flex-direction:column;gap:12px;max-width:360px;
}
.toast{
  padding:16px 22px;border-radius:14px;font-size:14px;font-weight:600;
  color:#fff;background:rgba(15,20,45,.95);backdrop-filter:blur(20px);
  border:1px solid rgba(140,160,255,.25);
  border-left:4px solid var(--cyan);
  box-shadow:0 16px 48px rgba(0,0,0,.6);
  animation:toastIn .4s cubic-bezier(.16,1,.3,1);line-height:1.55;
}
.toast.ok{border-left-color:var(--ok)}
.toast.err{border-left-color:var(--err)}
@keyframes toastIn{from{transform:translateX(120%);opacity:0}to{transform:translateX(0);opacity:1}}
.toast.hide{animation:toastOut .35s forwards}
@keyframes toastOut{to{transform:translateX(120%);opacity:0}}

/* ============ RESPONSIVE ============ */
@media(max-width:780px){
  .site-header{flex-wrap:wrap;justify-content:center;padding:12px 16px}
  .brand{flex:1 1 100%;justify-content:center}
  .music-player{max-width:none;width:100%;order:2}
  .grid-2{grid-template-columns:1fr}
  .brand-text span{letter-spacing:2px;font-size:11px}
  .toast-wrap{left:16px;right:16px;max-width:none}
  .hero{padding:20px 0 40px}
}
@media(prefers-reduced-motion:reduce){
  *,*::before,*::after{animation-duration:.01ms!important;transition-duration:.01ms!important}
}
</style>
</head>
<body>

<!-- NỀN ĐỘNG -->
<div class="bg-orbs">
  <div class="orb"></div>
  <div class="orb"></div>
  <div class="orb"></div>
</div>
<div class="bg-grid"></div>
<div class="bg-noise"></div>
<div class="symbols-layer" id="symbolsLayer"></div>

<!-- HEADER -->
<header class="site-header">
  <div class="brand">
    <div class="logo">
      <svg viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <linearGradient id="g" x1="0" y1="0" x2="1" y2="1">
            <stop offset="0%" stop-color="#22d3ee"/>
            <stop offset="100%" stop-color="#a855f7"/>
          </linearGradient>
        </defs>
        <path d="M32 17c-5-4.5-12.5-6.5-21-6.5v35c8.5 0 16 2 21 6.5 5-4.5 12.5-6.5 21-6.5v-35C44.5 10.5 37 12.5 32 17z"
              stroke="url(#g)" stroke-width="2.6" stroke-linejoin="round"
              fill="rgba(34,211,238,0.1)"/>
        <path d="M32 17v35" stroke="url(#g)" stroke-width="2.6" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="brand-text">
      <h1>Hồng Quân</h1>
      <span>Giải Bài Tập Tin</span>
    </div>
  </div>
  <div class="music-player" id="musicPlayer">
    <button class="music-ctrl" id="musicPrev" title="Bài trước">⏮</button>
    <div class="music-info">
      <span class="music-title" id="musicTitle"><span class="dot"></span>Nhấn ▶ để bật nhạc</span>
    </div>
    <button class="music-ctrl" id="musicNext" title="Bài kế">⏭</button>
    <button class="music-toggle" id="musicToggle" title="Bật nhạc">▶</button>
  </div>
  <audio id="bgMusic" preload="none"></audio>
</header>

<main>
  <!-- HERO -->
  <section class="hero">
    <p class="hero-badge">Nền tảng hỗ trợ học Tin học</p>
    <h2 class="hero-title">
      Giải Bài Tập Tin
      <span class="grad">Nhanh – Chuẩn – Tận Tâm</span>
    </h2>
    <p class="hero-desc">
      Gửi bài tập cho <strong>Hồng Quân</strong> chỉ trong vài giây.
      Điền biểu mẫu bên dưới, hệ thống sẽ chuyển thông tin trực tiếp tới quản trị viên.
    </p>
    <div class="hero-actions">
      <a href="#gui-bai-tap" class="btn btn-primary">📝 Gửi bài tập</a>
      <a href="#mua-key" class="btn btn-ghost">🔑 Mua KEY</a>
    </div>
    <ul class="hero-stats">
      <li><strong>24/7</strong><span>Nhận bài mọi lúc</span></li>
      <li><strong>M1·M2·M3</strong><span>Nhiều loại KEY</span></li>
      <li><strong>Bảo mật</strong><span>Thông tin riêng tư</span></li>
    </ul>
  </section>

  <!-- 2 FORM -->
  <div class="forms-grid">
    <section class="panel" id="gui-bai-tap">
      <div class="panel-head">
        <h3>📝 Gửi bài tập cần giải</h3>
        <p>Điền đầy đủ các ô có dấu <span class="req">*</span> rồi bấm <em>Gửi bài tập</em>.</p>
      </div>
      <form id="homeworkForm">
        <div class="field">
          <label for="hwName">Họ và tên học sinh <span class="req">*</span></label>
          <input id="hwName" type="text" placeholder="Ví dụ: Nguyễn Văn A" required maxlength="80">
        </div>
        <div class="grid-2">
          <div class="field">
            <label for="hwClass">Lớp <span class="req">*</span></label>
            <input id="hwClass" type="text" placeholder="Ví dụ: 11A1" required maxlength="30">
          </div>
          <div class="field">
            <label for="hwKey">KEY sử dụng <span class="req">*</span></label>
            <input id="hwKey" type="text" placeholder="Ví dụ: HQ-M1-1234" required maxlength="60">
          </div>
        </div>
        <div class="field">
          <label for="hwLesson">Tên bài học <span class="req">*</span></label>
          <input id="hwLesson" type="text" placeholder="Ví dụ: Bài 12 – Mảng một chiều" required maxlength="120">
        </div>
        <div class="field">
          <label for="hwContent">Nội dung bài tập <span class="req">*</span></label>
          <textarea id="hwContent" rows="6" placeholder="Dán đề bài hoặc mô tả chi tiết yêu cầu cần giải..." required maxlength="5000"></textarea>
        </div>
        <button type="submit" class="btn btn-primary btn-block" id="hwSubmit">🚀 Gửi bài tập</button>
        <p class="form-status" id="hwStatus"></p>
      </form>
    </section>

    <section class="panel" id="mua-key">
      <div class="panel-head">
        <h3>🔑 Đăng ký mua KEY</h3>
        <p>Gửi yêu cầu, quản trị viên sẽ liên hệ xác nhận và cấp KEY cho bạn.</p>
      </div>
      <form id="keyForm">
        <div class="field">
          <label for="keyName">Tên người mua <span class="req">*</span></label>
          <input id="keyName" type="text" placeholder="Ví dụ: Trần Thị B" required maxlength="80">
        </div>
        <div class="field">
          <label for="keyContact">Email hoặc liên hệ khác <span class="req">*</span></label>
          <input id="keyContact" type="text" placeholder="email@gmail.com hoặc Zalo 09xxxxxxxx" required maxlength="120">
        </div>
        <div class="grid-2">
          <div class="field">
            <label for="keyType">Loại KEY <span class="req">*</span></label>
            <select id="keyType" required>
              <option value="" disabled selected>-- Chọn --</option>
              <option value="M1">KEY M1</option>
              <option value="M2">KEY M2</option>
              <option value="M3">KEY M3</option>
              <option value="Vĩnh viễn">KEY Vĩnh viễn</option>
            </select>
          </div>
          <div class="field">
            <label for="keyQty">Số lượng <span class="req">*</span></label>
            <input id="keyQty" type="number" min="1" max="100" value="1" required>
          </div>
        </div>
        <div class="field">
          <label for="keyPay">Phương thức thanh toán <span class="req">*</span></label>
          <select id="keyPay" required>
            <option value="" disabled selected>-- Chọn --</option>
            <option value="Chuyển khoản ngân hàng">Chuyển khoản ngân hàng</option>
            <option value="Ví MoMo">Ví MoMo</option>
            <option value="ZaloPay">ZaloPay</option>
            <option value="Thẻ cào điện thoại">Thẻ cào điện thoại</option>
            <option value="Khác">Khác</option>
          </select>
        </div>
        <button type="submit" class="btn btn-purple btn-block" id="keySubmit">💳 Gửi yêu cầu mua KEY</button>
        <p class="form-status" id="keyStatus"></p>
      </form>
    </section>
  </div>

  <!-- KEY INFO -->
  <section class="key-info">
    <h3 class="section-title">Các loại <span class="grad" style="display:inline">KEY</span> đang cung cấp</h3>
    <div class="key-grid">
      <article class="key-card">
        <h4>KEY M1</h4>
        <p>Gói cơ bản, phù hợp nhu cầu giải bài tập ngắn hạn.</p>
      </article>
      <article class="key-card">
        <h4>KEY M2</h4>
        <p>Gói mở rộng, thời hạn dài hơn và nhiều lượt sử dụng hơn.</p>
      </article>
      <article class="key-card">
        <h4>KEY M3</h4>
        <p>Gói nâng cao, ưu tiên xử lý và hỗ trợ chi tiết hơn.</p>
      </article>
      <article class="key-card key-card--vip">
        <h4>KEY Vĩnh viễn</h4>
        <p>Sử dụng lâu dài, không giới hạn thời gian.</p>
      </article>
    </div>
    <p class="key-note">
      ℹ️ Giá và quyền lợi cụ thể sẽ do quản trị viên xác nhận qua liên hệ bạn cung cấp.
      Website <strong>không tự động</strong> cấp KEY.
    </p>
  </section>
</main>

<footer class="site-footer">
  <p>© <span id="year">2025</span> <strong>Hồng Quân – Giải Bài Tập Tin</strong>. Made with 💙</p>
</footer>

<div class="toast-wrap" id="toastWrap"></div>

<script>
(function(){
"use strict";

/* ⚠️ DÁN URL APPS SCRIPT CỦA BẠN VÀO ĐÂY */
var APPS_SCRIPT_URL = "https://script.google.com/macros/s/XXXXXXXXXXXXXXXXXXXXXXXX/exec";

var PLAYLIST=[
  {title:"FUNK MANDALA — DJ Samir",src:"music/funk-mandala.mp3"},
  {title:"MALE MANDALA FUNK — Nulteex",src:"music/male-mandala-funk.mp3"},
  {title:"FUNK MANDALA (SLOWED)",src:"music/funk-mandala-slowed.mp3"},
  {title:"Remix Sôi Động #1",src:"music/bai1.mp3"},
  {title:"Remix Bass Mạnh #2",src:"music/bai2.mp3"}
];

var $=function(s,r){return (r||document).querySelector(s)};

function showToast(m,t){
  var w=$("#toastWrap"),d=document.createElement("div");
  d.className="toast "+(t||"");d.innerHTML=m;w.appendChild(d);
  setTimeout(function(){d.classList.add("hide");setTimeout(function(){d.remove()},350)},4500);
}
function setStatus(el,m,t){el.textContent=m||"";el.className="form-status"+(t?" "+t:"")}

/* Ký hiệu bay */
function initSymbols(){
  var layer=$("#symbolsLayer");if(!layer)return;
  var icons=["📘","📗","📙","📕","✏️","📐","📏","🔬","🧮","∑","√","∫","π","∞","{}","</>","#","@","α","β","Δ","λ","💡","⚡"];
  var count=window.innerWidth<640?16:32,frag=document.createDocumentFragment();
  for(var i=0;i<count;i++){
    var s=document.createElement("span");s.className="symbol";
    s.textContent=icons[Math.floor(Math.random()*icons.length)];
    s.style.left=Math.random()*100+"%";
    s.style.fontSize=(14+Math.random()*18)+"px";
    var dur=(14+Math.random()*12).toFixed(1);
    s.style.animationDuration=dur+"s";
    s.style.animationDelay=(-Math.random()*dur)+"s";
    s.style.setProperty("--drift",(Math.random()*100-50).toFixed(0)+"px");
    s.style.opacity=(0.2+Math.random()*0.35).toFixed(2);
    frag.appendChild(s);
  }
  layer.appendChild(frag);
}

/* Nhạc */
function initMusic(){
  var audio=$("#bgMusic"),player=$("#musicPlayer"),toggle=$("#musicToggle");
  var prevBtn=$("#musicPrev"),nextBtn=$("#musicNext"),titleEl=$("#musicTitle");
  if(!audio||!toggle)return;
  var current=0,isPlaying=false;
  if(!PLAYLIST.length){player.style.display="none";return}
  audio.volume=0.55;
  function updateUI(){
    player.classList.toggle("playing",isPlaying);
    toggle.textContent=isPlaying?"❚❚":"▶";
    toggle.title=isPlaying?"Tạm dừng":"Bật nhạc";
    if(isPlaying||audio.currentTime>0){
      titleEl.innerHTML='<span class="dot"></span>Bài '+(current+1)+'/'+PLAYLIST.length+' — '+PLAYLIST[current].title;
    } else {
      titleEl.innerHTML='<span class="dot"></span>Nhấn ▶ để bật nhạc';
    }
  }
  function loadTrack(i){current=(i+PLAYLIST.length)%PLAYLIST.length;audio.src=PLAYLIST[current].src;audio.load();updateUI()}
  function play(){
    var p=audio.play();
    if(p&&p.catch){
      p.then(function(){isPlaying=true;updateUI()})
       .catch(function(){
         isPlaying=false;updateUI();
         showToast("⚠️ Không phát được: <b>"+PLAYLIST[current].src+"</b>","err");
       });
    } else {isPlaying=true;updateUI()}
  }
  function pause(){audio.pause();isPlaying=false;updateUI()}
  toggle.addEventListener("click",function(){if(audio.paused){if(!audio.src)loadTrack(0);play()}else pause()});
  nextBtn.addEventListener("click",function(){var w=!audio.paused;loadTrack(current+1);if(w)play();else updateUI()});
  prevBtn.addEventListener("click",function(){var w=!audio.paused;loadTrack(current-1);if(w)play();else updateUI()});
  audio.addEventListener("ended",function(){loadTrack(current+1);play()});
  audio.addEventListener("play",function(){isPlaying=true;updateUI()});
  audio.addEventListener("pause",function(){isPlaying=false;updateUI()});
  loadTrack(0);
}

/* Gửi Apps Script */
function sendToAppsScript(payload){
  return fetch(APPS_SCRIPT_URL,{
    method:"POST",mode:"no-cors",
    headers:{"Content-Type":"text/plain;charset=utf-8"},
    body:JSON.stringify(payload)
  });
}

/* Form bài tập */
function initHomeworkForm(){
  var form=$("#homeworkForm"),btn=$("#hwSubmit"),status=$("#hwStatus");
  if(!form)return;
  form.addEventListener("submit",function(e){
    e.preventDefault();
    if(!form.checkValidity()){form.reportValidity();return}
    var payload={
      type:"BAITAP",
      hoTen:$("#hwName").value.trim(),
      lop:$("#hwClass").value.trim(),
      keySuDung:$("#hwKey").value.trim(),
      tenBaiHoc:$("#hwLesson").value.trim(),
      noiDung:$("#hwContent").value.trim(),
      thoiGian:new Date().toLocaleString("vi-VN")
    };
    btn.disabled=true;btn.textContent="⏳ Đang gửi...";
    setStatus(status,"Đang gửi bài tập, vui lòng chờ...","loading");
    sendToAppsScript(payload).then(function(){
      setStatus(status,"✅ Gửi bài tập thành công! Quản trị viên sẽ phản hồi sớm.","ok");
      showToast("✅ <b>Gửi bài tập thành công!</b><br>Vui lòng chờ phản hồi.","ok");
      form.reset();
    }).catch(function(err){
      console.error(err);
      setStatus(status,"❌ Gửi thất bại. Kiểm tra kết nối và thử lại.","err");
      showToast("❌ <b>Không gửi được bài tập.</b>","err");
    }).finally(function(){
      btn.disabled=false;btn.textContent="🚀 Gửi bài tập";
    });
  });
}

/* Form mua KEY */
function initKeyForm(){
  var form=$("#keyForm"),btn=$("#keySubmit"),status=$("#keyStatus");
  if(!form)return;
  form.addEventListener("submit",function(e){
    e.preventDefault();
    if(!form.checkValidity()){form.reportValidity();return}
    var payload={
      type:"MUKEY",
      tenNguoiMua:$("#keyName").value.trim(),
      lienHe:$("#keyContact").value.trim(),
      loaiKey:$("#keyType").value,
      soLuong:$("#keyQty").value,
      phuongThuc:$("#keyPay").value,
      thoiGian:new Date().toLocaleString("vi-VN")
    };
    btn.disabled=true;btn.textContent="⏳ Đang gửi...";
    setStatus(status,"Đang gửi yêu cầu mua KEY...","loading");
    sendToAppsScript(payload).then(function(){
      setStatus(status,"✅ Đã gửi yêu cầu! Quản trị viên sẽ liên hệ xác nhận.","ok");
      showToast("✅ <b>Yêu cầu mua KEY đã gửi!</b><br>Chờ quản trị viên xác nhận.","ok");
      form.reset();$("#keyQty").value=1;
    }).catch(function(err){
      console.error(err);
      setStatus(status,"❌ Gửi thất bại. Kiểm tra kết nối và thử lại.","err");
      showToast("❌ <b>Không gửi được yêu cầu mua KEY.</b>","err");
    }).finally(function(){
      btn.disabled=false;btn.textContent="💳 Gửi yêu cầu mua KEY";
    });
  });
}

/* Khởi tạo */
function init(){
  var y=$("#year");if(y)y.textContent=new Date().getFullYear();
  initSymbols();
  initMusic();
  initHomeworkForm();
  initKeyForm();
  if(APPS_SCRIPT_URL.indexOf("XXXX")!==-1){
    console.warn("[Hồng Quân] Chưa cấu hình APPS_SCRIPT_URL!");
  }
}
if(document.readyState==="loading"){document.addEventListener("DOMContentLoaded",init)}else{init()}
})();
</script>
</body>
</html>
