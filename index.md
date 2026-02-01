<!doctype html>
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

    /* Headline large */
    .headline {
      font-weight: 900;
      font-size: clamp(48px, 10vw, 130px); /* very large */
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
    .gear-wrap.left  { width: 260px; height: 260px; }
    .gear-wrap.mid   { width: 360px; height: 360px; }
    .gear-wrap.right { width: 260px; height: 260px; }

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
      font-size: clamp(20px, 4.5vw, 34px);
      color: var(--text);
      margin-bottom: 8px;
      letter-spacing: 0.01em;
    }
    .counter .label { font-size: 13px; color: var(--muted); }

    @media (max-width: 820px) {
      .gears { gap: 18px; }
      .gear-wrap.mid { width: 300px; height: 300px; }
      .gear-wrap.left, .gear-wrap.right { width: 220px; height: 220px; }
      .headline { font-size: clamp(42px, 12vw, 72px); }
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
              <!-- teeth: 16 rectangles rotated -->
              <g fill="none" stroke="none">
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
              </g>

              <!-- main gear body -->
              <circle r="72" fill="var(--gear)" style="filter:url(#gShadow)" opacity="0.98"></circle>
              <!-- inner ring to suggest depth -->
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
              <!-- teeth: 20 rectangles rotated -->
              <g fill="var(--gear)">
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

              <!-- main gear body large -->
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
          <div id="bnbValue" class="value">0</div>
          <div class="label">BNB</div>
        </div>

        <div class="counter" aria-label="USD value">
          <div id="usdValue" class="value">0</div>
          <div class="label">USD</div>
        </div>
      </div>

    </div>
  </div>

  <script>
    /* ---------------- create many tiny filled gold bubbles ---------------- */
    (function createBubbles(){
      const container = document.getElementById('bg-bubbles');
      const COUNT = 60; // density
      const minSize = 4, maxSize = 8;
      for (let i=0;i<COUNT;i++){
        const n = document.createElement('div');
        n.className = 'bubble';
        const s = Math.floor(Math.random()*(maxSize-minSize+1))+minSize;
        n.style.width = s + 'px';
        n.style.height = s + 'px';
        // randomized positions, avoid exact center concentration
        const left = Math.random() * 100;
        const top = Math.random() * 100;
        n.style.left = left + 'vw';
        n.style.top = top + 'vh';
        // faster subtle motions
        const durY = (1.2 + Math.random()*2.2).toFixed(2); // 1.2 - 3.4s
        const durX = (1.6 + Math.random()*2.8).toFixed(2); // 1.6 - 4.4s
        const delay = (Math.random()*1.2).toFixed(2);
        n.style.animation = `floatFastY ${durY}s ease-in-out ${delay}s infinite alternate, driftFastX ${durX}s ease-in-out ${delay/2}s infinite alternate`;
        n.style.opacity = (0.6 + Math.random()*0.4).toFixed(2);
        container.appendChild(n);
      }

      // nudge positions on resize to keep scattered look
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

    /* ----------------- Very slow counters ------------------
       User requested: "very very very slow". Set a long duration.
       Change DURATION_MS to adjust speed:
       - Current value = 4 hours (14400000 ms) which is extremely slow.
       - Feel free to reduce if needed.
    ---------------------------------------------------------*/
    (function slowCounters(){
      const TARGETS = {
        playbnb: 20000000000,   // 20,000,000,000
        bnb: 25000,             // 25,000
        usd: 12345678           // 12,345,678
      };

      const DURATION_MS = 4 * 60 * 60 * 1000; // 4 hours

      function easeOutCubic(t){ return 1 - Math.pow(1 - t, 3); }

      function animateValue(element, start, end, duration){
        const startTime = performance.now();
        function frame(now){
          const elapsed = now - startTime;
          const t = Math.min(1, elapsed / duration);
          const eased = easeOutCubic(t);
          const current = Math.floor(start + (end - start) * eased);
          element.textContent = formatNumber(current);
          if (t < 1) requestAnimationFrame(frame);
          else element.textContent = formatNumber(end);
        }
        requestAnimationFrame(frame);
      }

      function formatNumber(n){
        return n.toLocaleString('en-US');
      }

      const playEl = document.getElementById('playbnbValue');
      const bnbEl  = document.getElementById('bnbValue');
      const usdEl  = document.getElementById('usdValue');

      // Start animations with little stagger, all extremely long
      setTimeout(()=> animateValue(playEl, 0, TARGETS.playbnb, DURATION_MS), 200);
      setTimeout(()=> animateValue(bnbEl, 0, TARGETS.bnb, DURATION_MS + 12000), 800);
      setTimeout(()=> animateValue(usdEl, 0, TARGETS.usd, DURATION_MS + 24000), 1400);
    })();
  </script>
</body>
</html>
