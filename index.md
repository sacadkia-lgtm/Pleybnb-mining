
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>COMING SOON — Mining</title>
  <style>
    :root{
      --bg: #000000;
      --text: #ffffff;
      --gold: #ffd700;
      --gear: #ff7a00;
      --muted: rgba(255,255,255,0.78);
    }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html,body { height: 100%; }
    body {
      background: var(--bg);
      color: var(--text);
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px;
    }

    /* Background tiny solid gold circles */
    .bg-bubbles {
      position: fixed;
      inset: 0;
      z-index: 0;
      pointer-events: none;
      overflow: hidden;
    }
    .bubble {
      position: absolute;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--gold);
      box-shadow: 0 0 6px rgba(255,215,0,0.45), inset 0 0 2px rgba(255,255,255,0.08);
      opacity: 0.95;
      will-change: transform, opacity;
      mix-blend-mode: screen;
    }
    @keyframes floatFastY { 0% { transform: translateY(0); } 50% { transform: translateY(-10px); } 100% { transform: translateY(0); } }
    @keyframes driftFastX { 0% { transform: translateX(0); } 50% { transform: translateX(6px); } 100% { transform: translateX(0); } }

    /* Card/center */
    .wrap {
      position: relative;
      z-index: 2;
      width: min(1200px, 96vw);
      display: flex;
      align-items: center;
      justify-content: center;
      min-height: 70vh;
    }
    .card {
      width: 100%;
      background: rgba(0,0,0,0.0);
      border-radius: 16px;
      padding: 54px 36px;
      text-align: center;
      color: var(--text);
      border: 1px solid rgba(255,255,255,0.03);
      box-shadow: 0 18px 60px rgba(0,0,0,0.65);
    }

    /* Headline very large */
    .headline {
      font-weight: 900;
      font-size: clamp(84px, 12vw, 200px); /* much larger */
      line-height: 1.02;
      margin: 0 0 20px;
      letter-spacing: -0.02em;
      text-transform: uppercase;
      color: var(--text);
    }
    .sub {
      font-size: clamp(14px, 2.2vw, 18px);
      color: var(--muted);
      margin-bottom: 28px;
    }

    /* Gears row - enlarged and shaped like gears */
    .gears {
      display: flex;
      gap: 40px;
      align-items: center;
      justify-content: center;
      margin: 8px 0 26px;
      flex-wrap: nowrap;
    }
    .gear-wrap { display:flex; align-items:center; justify-content:center; }

    /* sizes for gears (bigger as requested) */
    .gear-wrap.left  { width: 300px; height: 300px; }
    .gear-wrap.mid   { width: 420px; height: 420px; }
    .gear-wrap.right { width: 300px; height: 300px; }

    /* CSS rotation for gears - very slow */
    @keyframes spin-ccw { from { transform: rotate(0deg); } to { transform: rotate(-360deg); } }
    @keyframes spin-cw  { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }

    /* apply slow durations */
    .gear-svg.left  { animation: spin-ccw 180s linear infinite; transform-origin:50% 50%; }
    .gear-svg.mid   { animation: spin-cw 240s linear infinite;  transform-origin:50% 50%; }
    .gear-svg.right { animation: spin-ccw 150s linear infinite; transform-origin:50% 50%; }

    /* Counters */
    .counters {
      display:flex;
      gap: 22px;
      justify-content: center;
      align-items: flex-start;
      margin-top: 10px;
      flex-wrap: wrap;
    }
    .counter {
      min-width: 200px;
      padding: 14px 18px;
      border-radius: 12px;
      background: rgba(255,255,255,0.02);
      border: 1px solid rgba(255,255,255,0.03);
      text-align: center;
    }
    .counter .value {
      font-weight: 900;
      font-size: clamp(20px, 4.5vw, 44px);
      color: var(--text);
      margin-bottom: 8px;
      letter-spacing: 0.01em;
    }
    .counter .label { font-size: 13px; color: var(--muted); }

    @media (max-width: 820px) {
      .gears { gap: 18px; }
      .gear-wrap.mid { width: 320px; height: 320px; }
      .gear-wrap.left, .gear-wrap.right { width: 240px; height: 240px; }
      .headline { font-size: clamp(64px, 18vw, 120px); }
    }

    /* reduced motion */
    @media (prefers-reduced-motion: reduce) {
      .bubble { animation: none !important; }
      .gear-svg { animation: none !important; }
    }
  </style>
</head>
<body>
  <div class="bg-bubbles" id="bg-bubbles" aria-hidden="true"></div>

  <div class="wrap" role="main">
    <div class="card" aria-labelledby="headline">
      <h1 id="headline" class="headline">COMING SOON</h1>
      <p class="sub">Mining, rewards and airdrops for active players — prepare to participate.</p>

      <div class="gears" role="img" aria-label="Three rotating gears">
        <!-- LEFT GEAR (toothed SVG) -->
        <div class="gear-wrap left" aria-hidden="true">
          <svg class="gear-svg left" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
            <defs>
              <filter id="gShadow" x="-50%" y="-50%" width="200%" height="200%">
                <feDropShadow dx="0" dy="6" stdDeviation="10" flood-color="#ff7a00" flood-opacity="0.08"/>
              </filter>
            </defs>
            <g transform="translate(100,100)">
              <g fill="var(--gear)">
                <!-- 16 teeth -->
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(0)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(22.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(45)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(67.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(90)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(112.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(135)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(157.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(180)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(202.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(225)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(247.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(270)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(292.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(315)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(337.5)"></rect>
              </g>
              <circle r="72" fill="var(--gear)" style="filter:url(#gShadow)" opacity="0.98"></circle>
              <circle r="44" fill="#000"></circle>
              <circle r="12" fill="var(--gold)"></circle>
            </g>
          </svg>
        </div>

        <!-- MIDDLE GEAR (largest, toothed) -->
        <div class="gear-wrap mid" aria-hidden="true">
          <svg class="gear-svg mid" viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
            <defs>
              <filter id="gShadow2" x="-50%" y="-50%" width="200%" height="200%">
                <feDropShadow dx="0" dy="10" stdDeviation="18" flood-color="#ff7a00" flood-opacity="0.06"/>
              </filter>
            </defs>
            <g transform="translate(150,150)">
              <g fill="var(--gear)">
                <!-- 20 teeth -->
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(0)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(18)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(36)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(54)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(72)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(90)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(108)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(126)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(144)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(162)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(180)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(198)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(216)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(234)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(252)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(270)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(288)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(306)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(324)"></rect>
                <rect x="-8" y="-130" width="16" height="36" rx="3" transform="rotate(342)"></rect>
              </g>
              <circle r="120" fill="var(--gear)" style="filter:url(#gShadow2)" opacity="0.98"></circle>
              <circle r="68" fill="#000"></circle>
              <circle r="18" fill="var(--gold)"></circle>
            </g>
          </svg>
        </div>

        <!-- RIGHT GEAR (toothed) -->
        <div class="gear-wrap right" aria-hidden="true">
          <svg class="gear-svg right" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
            <g transform="translate(100,100)">
              <g fill="var(--gear)">
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(0)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(22.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(45)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(67.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(90)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(112.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(135)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(157.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(180)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(202.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(225)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(247.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(270)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(292.5)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(315)"></rect>
                <rect x="-6" y="-92" width="12" height="28" rx="3" transform="rotate(337.5)"></rect>
              </g>
              <circle r="72" fill="var(--gear)" opacity="0.98"></circle>
              <circle r="44" fill="#000"></circle>
              <circle r="12" fill="var(--gold)"></circle>
            </g>
          </svg>
        </div>
      </div>

      <!-- Counters row -->
      <div class="counters" role="status" aria-live="polite" aria-atomic="true">
        <div class="counter" aria-label="Play BNB supply">
          <div id="playbnbValue" class="value">0</div>
          <div class="label">PLAY BNB</div>
        </div>

        <div class="counter" aria-label="BNB amount">
          <div id="bnbValue" class="value">0.000000</div>
          <div class="label">BNB</div>
        </div>

        <div class="counter" aria-label="USD value">
          <div id="usdValue" class="value">0.00</div>
          <div class="label">USD</div>
        </div>
      </div>

    </div>
  </div>

  <script>
    /* ---------------- create many tiny filled gold bubbles ---------------- */
    (function createBubbles(){
      const container = document.getElementById('bg-bubbles');
      const COUNT = 60;
      const minSize = 4, maxSize = 8;
      for (let i=0;i<COUNT;i++){
        const n = document.createElement('div');
        n.className = 'bubble';
        const s = Math.floor(Math.random()*(maxSize-minSize+1))+minSize;
        n.style.width = s + 'px';
        n.style.height = s + 'px';
        n.style.left = (Math.random() * 100) + 'vw';
        n.style.top  = (Math.random() * 100) + 'vh';
        const durY = (1.2 + Math.random()*2.2).toFixed(2);
        const durX = (1.6 + Math.random()*2.8).toFixed(2);
        const delay = (Math.random()*1.2).toFixed(2);
        n.style.animation = `floatFastY ${durY}s ease-in-out ${delay}s infinite alternate, driftFastX ${durX}s ease-in-out ${delay/2}s infinite alternate`;
        n.style.opacity = (0.6 + Math.random()*0.4).toFixed(2);
        container.appendChild(n);
      }
      let t;
      window.addEventListener('resize', function(){
        clearTimeout(t);
        t = setTimeout(()=> {
          const children = container.children;
          for (let i=0;i<children.length;i++){
            const el = children[i];
            const left = Math.min(98, Math.max(2, parseFloat(el.style.left || '50') + (Math.random()*6-3)));
            const top  = Math.min(98, Math.max(2, parseFloat(el.style.top  || '50') + (Math.random()*6-3)));
            el.style.left = left + 'vw';
            el.style.top = top + 'vh';
          }
        }, 180);
      }, { passive: true });
    })();

    /* ----------------- Very slow counters using setInterval (24 hours) ------------------
       - Play BNB target: 890,000,000
       - BNB target: 1 (shown with 6 decimals while counting)
       - USD = BNB * 890 (shown with 2 decimals)
       - DURATION_MS currently 24 hours. Change if you want slower/faster.
    ---------------------------------------------------------------------------------------*/
    (function slowCounters(){
      const TARGETS = {
        playbnb: 890000000, // 890,000,000
        bnb: 1.0,           // 1 BNB
        pricePerBnb: 890.0  // 890 USD per BNB
      };

      const DURATION_MS = 24 * 60 * 60 * 1000; // 24 hours
      const TICK_MS = 1000; // update every second
      const steps = Math.max(1, Math.ceil(DURATION_MS / TICK_MS));

      // increments per tick
      const playIncrement = TARGETS.playbnb / steps;
      const bnbIncrement  = TARGETS.bnb / steps;

      // DOM
      const playEl = document.getElementById('playbnbValue');
      const bnbEl  = document.getElementById('bnbValue');
      const usdEl  = document.getElementById('usdValue');

      let playAcc = 0;
      let bnbAcc = 0;
      let step = 0;

      // update display every tick (1s). using setInterval to be CPU-friendly.
      const timer = setInterval(() => {
        step++;
        if (step >= steps) {
          // ensure final precise values
          playAcc = TARGETS.playbnb;
          bnbAcc  = TARGETS.bnb;
          const usd = bnbAcc * TARGETS.pricePerBnb;
          playEl.textContent = formatInt(playAcc);
          bnbEl.textContent  = formatFloat(bnbAcc, 6);
          usdEl.textContent  = formatFloat(usd, 2);
          clearInterval(timer);
          return;
        }

        // accumulate
        playAcc += playIncrement;
        bnbAcc  += bnbIncrement;

        // compute USD from current BNB
        const usd = bnbAcc * TARGETS.pricePerBnb;

        // render: playbnb as integer, bnb with 6 decimals, usd with 2 decimals
        playEl.textContent = formatInt(Math.floor(playAcc));
        bnbEl.textContent  = formatFloat(bnbAcc, 6);
        usdEl.textContent  = formatFloat(usd, 2);

      }, TICK_MS);

      // formatter helpers
      function formatInt(n){
        return Math.floor(n).toLocaleString('en-US');
      }
      function formatFloat(v, decimals){
        return Number(v).toFixed(decimals).replace(/\B(?=(\d{3})+(?!\d))/g, ",");
      }
    })();
  </script>
</body>
</html>
