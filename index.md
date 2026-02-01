<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>PlayBNB — Coming Soon</title>

<style>
:root{
  --bg:#000000;
  --white:#ffffff;
  --muted:rgba(255,255,255,.75);
}

*{box-sizing:border-box}
html,body{height:100%}

body{
  margin:0;
  background:var(--bg);
  color:var(--white);
  font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,Arial;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:28px;
  overflow:hidden;
}

.wrap{
  position:relative;
  z-index:2;
  width:min(1100px,96vw);
}

.card{
  text-align:center;
}

/* -------- TEXT -------- */
.brand{
  font-size:clamp(56px,10vw,120px);
  font-weight:900;
  color:#FFFFFF;
  letter-spacing:-0.03em;
  margin:0;
}

.coming{
  font-size:clamp(42px,7vw,88px);
  font-weight:800;
  margin:10px 0 22px;
  text-transform:uppercase;
}

/* -------- GEARS -------- */
.gears{
  display:flex;
  justify-content:center;
  gap:44px;
  margin:20px 0 34px;
}

.gear{
  width:190px;
  height:190px;
  animation:spin 120s linear infinite;
}

.gear.mid{
  width:230px;
  height:230px;
  animation-duration:180s;
}

.gear.rev{
  animation-direction:reverse;
  animation-duration:150s;
}

@keyframes spin{
  from{transform:rotate(0)}
  to{transform:rotate(360deg)}
}

/* -------- COUNTERS -------- */
.counters{
  display:flex;
  gap:26px;
  justify-content:center;
  flex-wrap:wrap;
}

.counter .value{
  font-size:32px;
  font-weight:800;
}

.counter .label{
  font-size:13px;
  color:var(--muted);
}
</style>
</head>

<body>

<div class="wrap">
  <div class="card">

    <!-- TEXT -->
    <h1 class="brand">PlayBNB</h1>
    <div class="coming">COMING SOON</div>

    <!-- GEARS (WEB3 STYLE SVG) -->
    <div class="gears">
      <svg class="gear rev" viewBox="0 0 200 200">
        <defs>
          <linearGradient id="g1" x1="0" y1="0" x2="1" y2="1">
            <stop offset="0%" stop-color="#7C7CFF"/>
            <stop offset="100%" stop-color="#00E5FF"/>
          </linearGradient>
        </defs>
        <circle cx="100" cy="100" r="70" fill="url(#g1)"/>
        <circle cx="100" cy="100" r="18" fill="#000"/>
      </svg>

      <svg class="gear mid" viewBox="0 0 200 200">
        <defs>
          <linearGradient id="g2" x1="1" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#FFD54F"/>
            <stop offset="100%" stop-color="#FF9100"/>
          </linearGradient>
        </defs>
        <circle cx="100" cy="100" r="85" fill="url(#g2)"/>
        <circle cx="100" cy="100" r="22" fill="#000"/>
      </svg>

      <svg class="gear" viewBox="0 0 200 200">
        <defs>
          <linearGradient id="g3" x1="0" y1="1" x2="1" y2="0">
            <stop offset="0%" stop-color="#00FFA3"/>
            <stop offset="100%" stop-color="#00C853"/>
          </linearGradient>
        </defs>
        <circle cx="100" cy="100" r="70" fill="url(#g3)"/>
        <circle cx="100" cy="100" r="18" fill="#000"/>
      </svg>
    </div>

    <!-- COUNTERS -->
    <div class="counters">
      <div class="counter">
        <div id="playbnb" class="value">0</div>
        <div class="label">PLAY BNB</div>
      </div>
      <div class="counter">
        <div id="bnb" class="value">0</div>
        <div class="label">BNB</div>
      </div>
      <div class="counter">
        <div id="usd" class="value">0</div>
        <div class="label">USD</div>
      </div>
    </div>

  </div>
</div>

<script>
/* VERY VERY SLOW COUNTERS */
const TARGET={playbnb:20000000000,bnb:25000,usd:12345678};
const DURATION=15*60*1000; // 15 minutes

function animate(el,end){
  const start=performance.now();
  function step(t){
    let p=Math.min((t-start)/DURATION,1);
    el.textContent=Math.floor(end*p).toLocaleString();
    if(p<1)requestAnimationFrame(step);
  }
  requestAnimationFrame(step);
}

animate(document.getElementById("playbnb"),TARGET.playbnb);
animate(document.getElementById("bnb"),TARGET.bnb);
animate(document.getElementById("usd"),TARGET.usd);
</script>

</body>
</html>
