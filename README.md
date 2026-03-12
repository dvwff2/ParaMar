<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Para Mar 🌊</title>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=Space+Mono:ital@0;1&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --deep: #0a0e1a;
      --ocean: #0d2137;
      --blue: #1a4a6e;
      --glow: #4fc3f7;
      --soft: #a8d8ea;
      --white: #e8f4f8;
      --gold: #c9a96e;
      --dim: rgba(79,195,247,0.12);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--deep);
      color: var(--white);
      font-family: 'Cormorant Garamond', serif;
      min-height: 100vh;
      overflow-x: hidden;
      cursor: crosshair;
    }

    /* Starfield */
    .stars {
      position: fixed;
      inset: 0;
      z-index: 0;
      pointer-events: none;
    }
    .star {
      position: absolute;
      border-radius: 50%;
      background: white;
      animation: twinkle var(--d) ease-in-out infinite alternate;
    }
    @keyframes twinkle {
      from { opacity: 0.1; transform: scale(1); }
      to   { opacity: 0.9; transform: scale(1.4); }
    }

    /* Floating pixels (Minecraft reference) */
    .pixels {
      position: fixed;
      inset: 0;
      z-index: 0;
      pointer-events: none;
    }
    .pixel {
      position: absolute;
      width: 6px;
      height: 6px;
      background: var(--glow);
      opacity: 0;
      animation: floatPixel var(--d) ease-in-out infinite;
      animation-delay: var(--delay);
      image-rendering: pixelated;
    }
    @keyframes floatPixel {
      0%   { opacity: 0; transform: translateY(0) rotate(0deg); }
      20%  { opacity: 0.5; }
      80%  { opacity: 0.3; }
      100% { opacity: 0; transform: translateY(-120px) rotate(90deg); }
    }

    /* Main wrapper */
    .container {
      position: relative;
      z-index: 1;
      max-width: 680px;
      margin: 0 auto;
      padding: 80px 32px 120px;
    }

    /* Header */
    .header {
      text-align: center;
      margin-bottom: 80px;
      opacity: 0;
      animation: fadeUp 1.2s ease forwards 0.3s;
    }
    .header .eyebrow {
      font-family: 'Space Mono', monospace;
      font-size: 0.7rem;
      letter-spacing: 0.3em;
      color: var(--glow);
      text-transform: uppercase;
      margin-bottom: 20px;
    }
    .header h1 {
      font-size: clamp(3.5rem, 10vw, 6rem);
      font-weight: 300;
      font-style: italic;
      line-height: 0.9;
      letter-spacing: -0.02em;
      color: var(--white);
    }
    .header h1 span {
      color: var(--glow);
      display: block;
    }
    .header .subtitle {
      margin-top: 24px;
      font-size: 1rem;
      font-style: italic;
      color: var(--soft);
      opacity: 0.7;
      letter-spacing: 0.05em;
    }

    /* Divider */
    .divider {
      display: flex;
      align-items: center;
      gap: 16px;
      margin: 48px 0;
      opacity: 0;
      animation: fadeUp 1s ease forwards;
    }
    .divider::before, .divider::after {
      content: '';
      flex: 1;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--glow), transparent);
    }
    .divider-icon {
      font-size: 1rem;
      color: var(--gold);
    }

    /* Sections */
    .section {
      margin-bottom: 64px;
      opacity: 0;
      animation: fadeUp 1s ease forwards;
    }
    .section:nth-child(2) { animation-delay: 0.6s; }
    .section:nth-child(3) { animation-delay: 0.9s; }
    .section:nth-child(4) { animation-delay: 1.2s; }
    .section:nth-child(5) { animation-delay: 1.5s; }
    .section:nth-child(6) { animation-delay: 1.8s; }

    .section-label {
      font-family: 'Space Mono', monospace;
      font-size: 0.6rem;
      letter-spacing: 0.35em;
      text-transform: uppercase;
      color: var(--glow);
      margin-bottom: 16px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .section-label::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--dim);
      max-width: 60px;
    }

    .section p {
      font-size: 1.25rem;
      font-weight: 300;
      line-height: 1.9;
      color: var(--white);
      opacity: 0.9;
    }
    .section p em {
      font-style: italic;
      color: var(--soft);
    }
    .section p strong {
      font-weight: 400;
      color: var(--glow);
    }

    /* Quote block */
    .quote-block {
      border-left: 2px solid var(--gold);
      padding: 24px 32px;
      margin: 48px 0;
      background: rgba(201, 169, 110, 0.04);
      opacity: 0;
      animation: fadeUp 1s ease forwards 1.4s;
    }
    .quote-block p {
      font-size: 1.4rem;
      font-style: italic;
      font-weight: 300;
      line-height: 1.7;
      color: var(--gold);
    }
    .quote-block cite {
      display: block;
      margin-top: 12px;
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      letter-spacing: 0.2em;
      color: var(--soft);
      opacity: 0.5;
    }

    /* Minecraft block */
    .minecraft-block {
      display: flex;
      align-items: center;
      gap: 20px;
      padding: 28px;
      border: 1px solid rgba(79,195,247,0.15);
      background: rgba(13,33,55,0.6);
      margin: 48px 0;
      opacity: 0;
      animation: fadeUp 1s ease forwards 1.6s;
    }
    .mc-icon {
      font-size: 2.5rem;
      flex-shrink: 0;
      image-rendering: pixelated;
      filter: drop-shadow(0 0 12px var(--glow));
    }
    .mc-text {
      font-family: 'Space Mono', monospace;
      font-size: 0.75rem;
      line-height: 1.8;
      color: var(--soft);
      opacity: 0.8;
    }
    .mc-text strong {
      color: var(--glow);
      display: block;
      font-size: 0.8rem;
      margin-bottom: 4px;
    }

    /* Final */
    .final {
      text-align: center;
      padding: 64px 0 32px;
      opacity: 0;
      animation: fadeUp 1.2s ease forwards 2.1s;
    }
    .final .big-text {
      font-size: clamp(2rem, 7vw, 3.5rem);
      font-weight: 300;
      font-style: italic;
      line-height: 1.2;
      color: var(--white);
      margin-bottom: 32px;
    }
    .final .big-text strong {
      color: var(--glow);
      font-weight: 300;
    }
    .final .signature {
      font-family: 'Space Mono', monospace;
      font-size: 0.7rem;
      letter-spacing: 0.3em;
      color: var(--gold);
      opacity: 0.6;
      text-transform: uppercase;
    }

    /* Glow orb */
    .orb {
      position: fixed;
      width: 400px;
      height: 400px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(79,195,247,0.08) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      animation: pulse 6s ease-in-out infinite;
    }
    @keyframes pulse {
      0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 0.6; }
      50%       { transform: translate(-50%, -50%) scale(1.3); opacity: 1; }
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    /* Heart cursor trail */
    .heart-trail {
      position: fixed;
      pointer-events: none;
      z-index: 999;
      font-size: 14px;
      animation: heartFade 1s ease forwards;
    }
    @keyframes heartFade {
      0%   { opacity: 0.9; transform: translateY(0) scale(1); }
      100% { opacity: 0; transform: translateY(-40px) scale(0.5); }
    }
  </style>
</head>
<body>

<div class="stars" id="stars"></div>
<div class="pixels" id="pixels"></div>
<div class="orb"></div>

<div class="container">

  <div class="header">
    <p class="eyebrow">una carta para</p>
    <h1>para<span>Mar.</span></h1>
    <p class="subtitle">escrita desde el lugar más honesto que tengo</p>
  </div>

  <div class="section">
    <p class="section-label">01 — la verdad</p>
    <p>
      Te fallé. No hay forma más simple ni más honesta de decirlo. 
      Tomé decisiones que te lastimaron, y no puedo borrarlas, 
      no puedo deshacer lo que hice. Pero sí puedo estar aquí, 
      sin excusas, <strong>diciéndote que lo siento con cada parte de mí.</strong>
    </p>
  </div>

  <div class="divider" style="animation-delay: 0.8s"><span class="divider-icon">✦</span></div>

  <div class="section">
    <p class="section-label">02 — lo que siento</p>
    <p>
      Hubo cosas que no supe manejar, situaciones que me atraparon 
      y en las que tomé el camino equivocado. Eso no te lo mereces. 
      <em>Tú te mereces a alguien que te elija siempre, incluso cuando es difícil.</em>
      Y quiero ser esa persona. Quiero aprender a serlo.
    </p>
  </div>

  <div class="minecraft-block">
    <span class="mc-icon">⛏️</span>
    <div class="mc-text">
      <strong>[ primer encuentro — servidor de Minecraft ]</strong>
      desde ese mundo de bloques y píxeles, sin saber que te estaba encontrando a ti.
      que ese juego nos haya cruzado sigue siendo una de las cosas más bonitas que me han pasado.
    </div>
  </div>

  <div class="section">
    <p class="section-label">03 — lo que eres para mí</p>
    <p>
      Eres la persona con quien quiero construir cosas. 
      No sé si en un servidor de Minecraft o en la vida real, 
      pero quiero construir <strong>contigo.</strong> 
      Quiero seguir descubriendo canciones juntos, 
      quiero estar cuando estés bien y cuando no estés tan bien. 
      <em>Quiero ser tuyo, Mar, de verdad.</em>
    </p>
  </div>

  <div class="quote-block">
    <p>"we used to be closer than this"</p>
    <cite>— Twenty One Pilots, Formidable</cite>
  </div>

  <div class="section">
    <p class="section-label">04 — lo que pido</p>
    <p>
      No te pido que olvides. Te pido que me dejes 
      <strong>demostrarte</strong> que puedo ser mejor. 
      Que lo que siento por ti es más grande que mis errores. 
      Que el resto de mis días tiene mucho más sentido 
      si los vivo a tu lado.
    </p>
  </div>

  <div class="final">
    <p class="big-text">
      quiero estar contigo<br/>
      <strong>el resto de mis días.</strong>
    </p>
    <p class="signature">con todo lo que soy — para Mar 🌊</p>
  </div>

</div>

<script>
  // Generate stars
  const starsEl = document.getElementById('stars');
  for (let i = 0; i < 120; i++) {
    const s = document.createElement('div');
    s.className = 'star';
    const size = Math.random() * 2.5 + 0.5;
    s.style.cssText = `
      width: ${size}px; height: ${size}px;
      top: ${Math.random() * 100}%;
      left: ${Math.random() * 100}%;
      --d: ${2 + Math.random() * 4}s;
      animation-delay: ${Math.random() * 4}s;
    `;
    starsEl.appendChild(s);
  }

  // Floating pixels
  const pixelsEl = document.getElementById('pixels');
  for (let i = 0; i < 30; i++) {
    const p = document.createElement('div');
    p.className = 'pixel';
    p.style.cssText = `
      bottom: ${Math.random() * 30}%;
      left: ${Math.random() * 100}%;
      --d: ${4 + Math.random() * 6}s;
      --delay: ${Math.random() * 6}s;
    `;
    pixelsEl.appendChild(p);
  }

  // Heart cursor trail
  document.addEventListener('mousemove', (e) => {
    if (Math.random() > 0.85) {
      const heart = document.createElement('div');
      heart.className = 'heart-trail';
      heart.textContent = ['💙','🌊','✦','⛏️'][Math.floor(Math.random()*4)];
      heart.style.left = e.clientX + 'px';
      heart.style.top  = e.clientY + 'px';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 1000);
    }
  });
</script>
</body>
</html>
