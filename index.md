<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Mining — Coming Soon</title>
  <style>
    /* --------- Page reset & base --------- */
    :root{
      --bg: #000000;
      --text: #ffffff;
      --gold: #ffd700;
      --gear: #ff7a00;
      --muted: rgba(255,255,255,0.78);
      --card-bg: rgba(0,0,0,0.0);
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      background:var(--bg);
      color:var(--text);
      font-family:Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:28px;
      overflow:hidden;
    }

    /* --------- Animated tiny gold circles (background bubbles) --------- */
    .bg-bubbles{
      position:fixed;
      inset:0;
      z-index:0;
      pointer-events:none;
      overflow:hidden;
    }
    .bubble{
      position:absolute;
      border-radius:50%;
      background: var(--gold);
      box-shadow: 0 0 6px rgba(255,215,0,0.45), inset 0 0 3px rgba(255,255,255,0.18);
      mix-blend-mode: screen;
      opacity:.95;
      will-change: transform, opacity;
    }
    /* fast subtle float */
    @keyframes floatYFast {
      0% { transform: translate3d(0,0,0) scale(1); opacity:.9; }
      50% { transform: translate3d(0,-12px,0) scale(1.05); opacity:1; }
      100% { transform: translate3d(0,0,0) scale(1); opacity:.9; }
    }
    @keyframes driftXFast {
      0% { transform: translate3d(0,0,0); }
      50% { transform: translate3d(8px,0,0); }
      100% { transform: translate3d(0,0,0); }
    }

    /* --------- Central content card --------- */
    .wrap{
      position:relative;
      z-index:2;
      width:min(1100px, 96vw);
      max-width:1100px;
      display:flex;
      align-items:center;
      justify-content:center;
      min-height:60vh;
    }
    .card {
      width:100%;
      background:var(--card-bg); /* transparent black */
      border-radius:14px;
      padding:48px 36px;
      text-align:center;
      color:var(--text);
      border: 1px solid rgba(255,215,0,0.03);
      box-shadow: 0 12px 40px rgba(0,0,0,0.6);
    }

    /* --------- Headline --------- */
    .headline {
      font-weight:900;
      font-size:clamp(36px, 7.5vw, 84px); /* large & responsive */
      line-height:1.02;
      margin:0 0 20px 0;
      color:var(--text);
      letter-spacing:-0.02em;
      text-transform:uppercase;
    }
    .sub {
      font-size:16px;
      color:var(--muted);
      margin-bottom:32px;
    }

    /* --------- Gears (SVG) and layout --------- */
    .gears {
      display:flex;
      gap:36px;
      align-items:center;
      justify-content:center;
      margin:6px 0 28px;
      flex-wrap:wrap;
    }

    .gear-wrap{
      width:140px;
      height:140px;
      display:flex;
      align-items:center;
      justify-content:center;
    }
    /* make gears slightly different sizes */
    .gear-wrap.small { width:110px; height:110px; }
    .gear-wrap.large { width:170px; height:170px; }

    /* slow rotation animations */
    @keyframes spin-slow {
      from { transform: rotate(0deg); }
      to   { transform: rotate(360deg); }
    }
    .gear-svg {
      width:100%;
      height:100%;
      display:block;
      transform-origin:center center;
      /* animated; duration differs per gear via inline style or classes */
    }

    /* --------- Counters row --------- */
    .counters {
      display:flex;
      gap:24px;
      justify-content:center;
      align-items:flex-start;
      margin-top:8px;
      flex-wrap:wrap;
    }
    .counter {
      min-width:180px;
      padding:12px 16px;
      border-radius:10px;
      background:rgba(255,255,255,0.02);
      border:1px solid rgba(255,255,255,0.02);
      text-align:center;
    }
    .counter .value{
      font-weight:800;
      font-size:clamp(20px,4.2vw,32px);
      color:var(--text);
      margin-bottom:6px;
      letter-spacing:0.01em;
    }
    .counter .label{
      font-size:13px;
      color:var(--muted);
    }

    /* small screens */
    @media (max-width:520px){
      .gear-wrap { width:92px; height:92px; }
      .gear-wrap.large { width:124px; height:124px; }
      .counter { min-width:140px; padding:10px; }
      .headline { font-size:28px; }
    }

    /* Respect reduced motion */
    @media (prefers-reduced-motion: reduce) {
      .bubble { animation: none !important; }
      .gear-svg { animation: none !important; }
    }
  </style>
</head>
<body>
  <!-- Animated tiny gold dots in the background -->
  <div class="bg-bubbles" id="bg-bubbles" aria-hidden="true"></div>

  <!-- Main central card -->
  <div class="wrap" role="main">
    <div class="card" aria-labelledby="headline">
      <h1 id="headline" class="headline">Mining — Coming Soon</h1>
      <p class="sub">Get ready. Rewards, airdrops and game mining will be distributed to active participants.</p>

      <!-- Gears row -->
      <div class="gears" aria-hidden="false" role="img" aria-label="Rotating gears animation">
        <!-- Left gear (rotates counterclockwise slowly) -->
        <div class="gear-wrap small">
          <svg class="gear-svg" viewBox="0 0 100 100" aria-hidden="true"
               style="animation: spin-slow 60s linear infinite; transform-origin:50% 50%;">
            <g transform="translate(50,50)">
              <!-- simple gear path (stylized) -->
              <path d="M0 -28 L6 -24 L12 -28 L18 -20 L26 -18 L28 -10 L36 -6 L36 6 L28 10 L26 18 L18 20 L12 28 L6 24 L0 28 L-6 24 L-12 28 L-18 20 L-26 18 L-28 10 L-36 6 L-36 -6 L-28 -10 L-26 -18 L-18 -20 L-12 -28 L-6 -24 Z"
                    fill="none" stroke="none" />
              <!-- center circular gear using stroke to mimic teeth -->
              <circle r="28" fill="none" stroke="none"></circle>
              <!-- actual visible gear: create toothed effect by repeating small rectangles -->
              <g fill="var(--gear)" stroke="none">
                <!-- inner circle -->
                <circle r="22" fill="var(--gear)" opacity="0.95"></circle>
              </g>
              <!-- central hole -->
              <circle r="6" fill="#000"></circle>
            </g>
          </svg>
        </div>

        <!-- Middle gear (largest, rotates clockwise very slowly) -->
        <div class="gear-wrap large">
          <svg class="gear-svg" viewBox="0 0 120 120" aria-hidden="true"
               style="animation: spin-slow 90s linear infinite; transform-origin:50% 50%; filter: drop-shadow(0 6px 12px rgba(255,122,0,0.08));">
            <g transform="translate(60,60)">
              <circle r="40" fill="var(--gear)" opacity="0.96"></circle>
              <circle r="11" fill="#000"></circle>
            </g>
          </svg>
        </div>

        <!-- Right gear (medium, rotates counter to middle) -->
        <div class="gear-wrap">
          <svg class="gear-svg" viewBox="0 0 100 100" aria-hidden="true"
               style="animation: spin-slow 48s linear infinite reverse; transform-origin:50% 50%;">
            <g transform="translate(50,50)">
              <circle r="30" fill="var(--gear)" opacity="0.95"></circle>
              <circle r="7" fill="#000"></circle>
            </g>
          </svg>
        </div>
      </div>

      <!-- Counters -->
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
    /* ---------------- Background tiny gold circles ----------------
       - small filled circles (4-10px), slightly faster motion and subtle drift
       - COUNT is moderate to keep effect light on performance
    -----------------------------------------------------------------*/
    (function createBubbles(){
      const container = document.getElementById('bg-bubbles');
      const COUNT = 48; // adjust for density
      const minSize = 4, maxSize = 10;

      for (let i=0;i<COUNT;i++){
        const el = document.createElement('div');
        el.className = 'bubble';
        const size = Math.floor(Math.random() * (maxSize - minSize + 1)) + minSize;
        el.style.width = size + 'px';
        el.style.height = size + 'px';

        // random position across viewport; bias slightly away from center
        const left = Math.random() * 100;
        const top = Math.random() * 100;
        el.style.left = left + 'vw';
        el.style.top = top + 'vh';

        // animation timings: faster and varied
        const durY = (1.6 + Math.random()*2.4).toFixed(2); // 1.6 - 4.0s
        const durX = (2.0 + Math.random()*3.0).toFixed(2); // 2.0 - 5.0s
        const delay = (Math.random()*1.2).toFixed(2);

        el.style.animation = `floatYFast ${durY}s ease-in-out ${delay}s infinite alternate, driftXFast ${durX}s ease-in-out ${delay/2}s infinite alternate`;
        el.style.opacity = (0.7 + Math.random()*0.3).toFixed(2);

        container.appendChild(el);
      }
      // simple responsive nudge, not full regen
      let t;
      window.addEventListener('resize', ()=> {
        clearTimeout(t);
        t = setTimeout(()=> {
          const nodes = container.children;
          for (let i=0;i<nodes.length;i++){
            const n = nodes[i];
            const left = Math.min(98, Math.max(2, parseFloat(n.style.left || '50') + (Math.random()*8-4)));
            const top  = Math.min(98, Math.max(2, parseFloat(n.style.top  || '50') + (Math.random()*8-4)));
            n.style.left = left + 'vw';
            n.style.top  = top  + 'vh';
          }
        }, 200);
      }, { passive:true });
    })();

    /* ---------------- Rotating gears detail (optional enhancement) -------------
       The SVG shapes are simple filled circles to represent gears; rotation is handled
       in CSS via animation durations set inline above. If you want more realistic
       toothed gears, replace the SVG content with a detailed gear path.
    ---------------------------------------------------------------------------*/

    /* ---------------- Slow counters ----------------
       - Targets set below; change constants to desired final values.
       - Duration is long to produce "very slow" counting effect.
       - Uses requestAnimationFrame for smooth increments with easing.
    ---------------------------------------------------------------------------*/
    (function slowCounters(){
      // Edit targets here as needed
      const TARGETS = {
        playbnb: 20000000000,   // 20,000,000,000
        bnb: 25000,             // 25,000
        usd: 12345678           // 12,345,678
      };

      // Very slow duration (ms). Increase to slow more.
      const DURATION_MS = 5 * 60 * 1000; // 5 minutes = 300000ms (very slow)
      // You can change DURATION_MS to 600000 (10 minutes) etc.

      // Easing function (easeOutCubic)
      function easeOutCubic(t){ return 1 - Math.pow(1 - t, 3); }

      function animateValue(element, start, end, duration){
        const startTime = performance.now();
        function frame(now){
          const elapsed = now - startTime;
          const t = Math.min(1, elapsed / duration);
          const eased = easeOutCubic(t);
          const current = Math.floor(start + (end - start) * eased);
          element.textContent = formatNumber(current);
          if (t < 1){
            requestAnimationFrame(frame);
          } else {
            element.textContent = formatNumber(end);
          }
        }
        requestAnimationFrame(frame);
      }

      // formatting with commas and preserving integer part; if you want decimals, adjust.
      function formatNumber(n){
        return n.toLocaleString('en-US');
      }

      // start from zero (or small numbers if desired)
      const playEl = document.getElementById('playbnbValue');
      const bnbEl  = document.getElementById('bnbValue');
      const usdEl  = document.getElementById('usdValue');

      // Kick off animations slightly staggered for visual interest
      setTimeout(()=> animateValue(playEl, 0, TARGETS.playbnb, DURATION_MS), 400);
      setTimeout(()=> animateValue(bnbEl, 0, TARGETS.bnb, DURATION_MS + 8000), 800);
      setTimeout(()=> animateValue(usdEl, 0, TARGETS.usd, DURATION_MS + 16000), 1200);
    })();
  </script>
</body>
</html>
