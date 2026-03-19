
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Para Mar 🌸</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=Montserrat:wght@300;400&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #fdf6f0;
    --blush: #e8b4b8;
    --rose: #c2606a;
    --burgundy: #7a2634;
    --gold: #c9a96e;
    --dark: #2a1a1f;
    --text: #3d2028;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--cream);
    color: var(--text);
    font-family: 'Cormorant Garamond', serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Petals */
  .petal {
    position: fixed;
    top: -20px;
    pointer-events: none;
    font-size: 1.2rem;
    animation: fall linear infinite;
    opacity: 0.6;
    z-index: 0;
  }
  @keyframes fall {
    0%   { transform: translateY(-20px) rotate(0deg); opacity: 0; }
    10%  { opacity: 0.6; }
    90%  { opacity: 0.4; }
    100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
  }

  /* HERO */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 60px 20px;
    background:
      radial-gradient(ellipse at 20% 30%, rgba(232,180,184,0.18) 0%, transparent 60%),
      radial-gradient(ellipse at 80% 70%, rgba(194,96,106,0.12) 0%, transparent 55%),
      var(--cream);
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      radial-gradient(circle, rgba(201,169,110,0.08) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
  }

  .ornament {
    font-size: 1.6rem;
    color: var(--gold);
    letter-spacing: 12px;
    margin-bottom: 24px;
    animation: fadeUp 1.2s ease both;
  }

  .hero-eyebrow {
    font-family: 'Montserrat', sans-serif;
    font-weight: 300;
    font-size: 0.75rem;
    letter-spacing: 6px;
    text-transform: uppercase;
    color: var(--rose);
    margin-bottom: 16px;
    animation: fadeUp 1.4s ease both;
  }

  .hero-name {
    font-size: clamp(4rem, 14vw, 9rem);
    font-weight: 300;
    font-style: italic;
    line-height: 1;
    color: var(--dark);
    margin-bottom: 8px;
    animation: fadeUp 1.6s ease both;
  }

  .hero-name span {
    color: var(--rose);
  }

  .hero-subtitle {
    font-size: clamp(1rem, 3vw, 1.5rem);
    font-weight: 300;
    font-style: italic;
    color: var(--burgundy);
    margin-bottom: 40px;
    animation: fadeUp 1.8s ease both;
  }

  .divider {
    display: flex;
    align-items: center;
    gap: 16px;
    margin: 32px auto;
    width: fit-content;
    animation: fadeUp 2s ease both;
  }
  .divider::before, .divider::after {
    content: '';
    width: 80px;
    height: 1px;
    background: linear-gradient(to right, transparent, var(--gold));
  }
  .divider::after { background: linear-gradient(to left, transparent, var(--gold)); }
  .divider-heart { color: var(--rose); font-size: 1rem; }

  /* PHOTOS SECTION */
  .photos-section {
    padding: 80px 20px;
    max-width: 1000px;
    margin: 0 auto;
    text-align: center;
  }

  .section-label {
    font-family: 'Montserrat', sans-serif;
    font-weight: 300;
    font-size: 0.7rem;
    letter-spacing: 5px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 12px;
  }

  .section-title {
    font-size: clamp(2rem, 5vw, 3.2rem);
    font-weight: 300;
    font-style: italic;
    color: var(--dark);
    margin-bottom: 48px;
  }

  .photos-grid {
    display: grid;
    grid-template-columns: 1fr 1.3fr 1fr;
    grid-template-rows: auto auto;
    gap: 16px;
    margin-bottom: 48px;
  }

  .photo-slot {
    position: relative;
    background: linear-gradient(135deg, #f5e6e8, #fdf0f2);
    border: 1px solid rgba(201,169,110,0.3);
    border-radius: 4px;
    overflow: hidden;
    cursor: pointer;
    transition: transform 0.4s ease, box-shadow 0.4s ease;
  }

  .photo-slot:hover {
    transform: translateY(-6px) scale(1.02);
    box-shadow: 0 20px 50px rgba(122,38,52,0.12);
  }

  .photo-slot:nth-child(1) { grid-column: 1; grid-row: 1; aspect-ratio: 3/4; }
  .photo-slot:nth-child(2) { grid-column: 2; grid-row: 1 / 3; aspect-ratio: 2/3; }
  .photo-slot:nth-child(3) { grid-column: 3; grid-row: 1; aspect-ratio: 3/4; }
  .photo-slot:nth-child(4) { grid-column: 1; grid-row: 2; aspect-ratio: 4/3; }
  .photo-slot:nth-child(5) { grid-column: 3; grid-row: 2; aspect-ratio: 4/3; }

  .photo-slot input[type="file"] {
    position: absolute;
    inset: 0;
    opacity: 0;
    cursor: pointer;
    width: 100%;
    height: 100%;
    z-index: 2;
  }

  .photo-placeholder {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 8px;
    color: var(--blush);
    transition: opacity 0.3s;
  }

  .photo-placeholder .icon { font-size: 2rem; }
  .photo-placeholder p {
    font-family: 'Montserrat', sans-serif;
    font-size: 0.65rem;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--rose);
    opacity: 0.6;
  }

  .photo-slot img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: none;
  }

  /* MESSAGE */
  .message-section {
    background: linear-gradient(135deg, var(--burgundy), #5a1a22);
    padding: 80px 40px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .message-section::before {
    content: '❝';
    position: absolute;
    top: -20px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 8rem;
    color: rgba(255,255,255,0.04);
    font-family: serif;
    line-height: 1;
  }

  .message-text {
    max-width: 680px;
    margin: 0 auto;
    font-size: clamp(1.3rem, 3vw, 1.8rem);
    font-weight: 300;
    font-style: italic;
    line-height: 1.9;
    color: #fce8ea;
    position: relative;
    z-index: 1;
  }

  .message-text em {
    color: var(--blush);
    font-style: normal;
    font-weight: 400;
  }

  /* QUESTION */
  .question-section {
    padding: 100px 20px;
    text-align: center;
    background:
      radial-gradient(ellipse at 50% 0%, rgba(232,180,184,0.2) 0%, transparent 60%),
      var(--cream);
  }

  .question-text {
    font-size: clamp(2.5rem, 7vw, 5.5rem);
    font-weight: 300;
    font-style: italic;
    color: var(--dark);
    margin-bottom: 16px;
    line-height: 1.1;
  }

  .question-sub {
    font-family: 'Montserrat', sans-serif;
    font-weight: 300;
    font-size: 0.85rem;
    letter-spacing: 4px;
    text-transform: uppercase;
    color: var(--rose);
    margin-bottom: 60px;
  }

  .buttons {
    display: flex;
    gap: 20px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .btn-yes {
    background: linear-gradient(135deg, var(--rose), var(--burgundy));
    color: white;
    border: none;
    padding: 18px 56px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.4rem;
    font-style: italic;
    cursor: pointer;
    border-radius: 2px;
    letter-spacing: 2px;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    box-shadow: 0 8px 30px rgba(122,38,52,0.2);
  }

  .btn-yes:hover {
    transform: translateY(-3px) scale(1.04);
    box-shadow: 0 16px 40px rgba(122,38,52,0.35);
  }

  .btn-no {
    background: transparent;
    color: var(--rose);
    border: 1px solid var(--blush);
    padding: 18px 40px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.1rem;
    font-style: italic;
    cursor: pointer;
    border-radius: 2px;
    letter-spacing: 1px;
    transition: all 0.3s ease;
    position: relative;
  }

  /* YES SCREEN */
  .yes-screen {
    display: none;
    position: fixed;
    inset: 0;
    background: linear-gradient(135deg, #fdf0f2, #fce8ea, #f5d5d8);
    z-index: 100;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 40px;
    animation: fadeIn 0.8s ease;
  }

  .yes-screen.active { display: flex; }

  .yes-heart {
    font-size: 6rem;
    animation: heartbeat 1s ease infinite;
    margin-bottom: 24px;
  }

  @keyframes heartbeat {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.15); }
  }

  .yes-title {
    font-size: clamp(3rem, 9vw, 7rem);
    font-weight: 300;
    font-style: italic;
    color: var(--burgundy);
    margin-bottom: 16px;
  }

  .yes-sub {
    font-family: 'Montserrat', sans-serif;
    font-weight: 300;
    font-size: 0.85rem;
    letter-spacing: 5px;
    text-transform: uppercase;
    color: var(--rose);
  }

  .confetti-piece {
    position: fixed;
    top: -10px;
    pointer-events: none;
    font-size: 1.4rem;
    animation: confetti-fall 3s linear infinite;
    z-index: 101;
  }

  @keyframes confetti-fall {
    0%   { transform: translateY(-10px) rotate(0deg); opacity: 1; }
    100% { transform: translateY(105vh) rotate(720deg); opacity: 0; }
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(30px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }

  /* FOOTER */
  footer {
    text-align: center;
    padding: 40px;
    font-style: italic;
    font-size: 0.9rem;
    color: var(--blush);
  }

  @media (max-width: 600px) {
    .photos-grid {
      grid-template-columns: 1fr 1fr;
      grid-template-rows: auto;
    }
    .photo-slot:nth-child(1) { grid-column: 1; grid-row: 1; aspect-ratio: 1; }
    .photo-slot:nth-child(2) { grid-column: 2; grid-row: 1 / 3; aspect-ratio: 2/3; }
    .photo-slot:nth-child(3) { grid-column: 1; grid-row: 2; aspect-ratio: 1; }
    .photo-slot:nth-child(4) { grid-column: 1; grid-row: 3; aspect-ratio: 4/3; }
    .photo-slot:nth-child(5) { grid-column: 2; grid-row: 3; aspect-ratio: 4/3; }
  }
</style>
</head>
<body>

<!-- Falling petals -->
<div id="petals"></div>

<!-- HERO -->
<section class="hero">
  <div class="ornament">✦ ✦ ✦</div>
  <p class="hero-eyebrow">Hoy es un día especial para ambos...</p>
  <h1 class="hero-name"><span>M</span>ar</h1>
  <p class="hero-subtitle"></p>
  <div class="divider"><span class="divider-heart">♥</span></div>
  <p style="font-size:1.15rem; font-style:italic; color:var(--burgundy); max-width:400px; line-height:1.8; animation: fadeUp 2.2s ease both;">
    Desde el primer momento contigo,<br>supe que eras algo diferente, algo que me gustaba pero que no podía explicar,
    algo que simplemente me encantaba, me encantaba/encanta estár contigo, a cada momento, a cada hora, a cada segundo,
    cada momento contigo me gusta demasiado. .
  </p>
</section>

<!-- PHOTOS -->
<section class="photos-section">
  <p class="section-label">Nuestros momentos</p>
  <h2 class="section-title">Los recuerdos que atesoro</h2>

  <div class="photos-grid">
    <div class="photo-slot" title="Agregar foto">
      <input type="file" accept="image/*" onchange="loadPhoto(this)">
      <div class="photo-placeholder">
        <span class="icon">🌸</span>
        <p>Agregar foto</p>
      </div>
      <img>
    </div>
    <div class="photo-slot" title="Agregar foto">
      <input type="file" accept="image/*" onchange="loadPhoto(this)">
      <div class="photo-placeholder">
        <span class="icon">🌸</span>
        <p>Agregar foto</p>
      </div>
      <img>
    </div>
    <div class="photo-slot" title="Agregar foto">
      <input type="file" accept="image/*" onchange="loadPhoto(this)">
      <div class="photo-placeholder">
        <span class="icon">🌸</span>
        <p>Agregar foto</p>
      </div>
      <img>
    </div>
    <div class="photo-slot" title="Agregar foto">
      <input type="file" accept="image/*" onchange="loadPhoto(this)">
      <div class="photo-placeholder">
        <span class="icon">🌸</span>
        <p>Agregar foto</p>
      </div>
      <img>
    </div>
    <div class="photo-slot" title="Agregar foto">
      <input type="file" accept="image/*" onchange="loadPhoto(this)">
      <div class="photo-placeholder">
        <span class="icon">🌸</span>
        <p>Agregar foto</p>
      </div>
      <img>
    </div>
  </div>
</section>

<!-- MESSAGE -->
<section class="message-section">
  <p class="message-text">
    Cada vez que estamos juntos, el mundo se vuelve
    <em> más bonito</em>.<br><br>
    Me haces reír cuando menos lo espero,
    me das calma cuando todo se siente difícil.<br><br>
    Contigo, todo simplemente <em>tiene más sentido</em>.
  </p>
</section>

<!-- QUESTION -->
<section class="question-section">
  <div class="divider" style="margin-bottom:40px;"><span class="divider-heart">♥</span></div>
  <h2 class="question-text">Y con la mano en el corazón, me gustaría preguntarte
  ¿Puedo ser tu novio?</h2>
  <p class="question-sub">Mar · con todo mi corazón</p>
  <div class="buttons">
    <button class="btn-yes" onclick="sayYes()">Sí, quiero 💕</button>
    <button class="btn-no" id="noBtn" onmouseover="moveNo()" ontouchstart="moveNo()">Mmm...</button>
  </div>
</section>

<footer>hecho con amor, solo para ti ♥</footer>

<!-- YES SCREEN -->
<div class="yes-screen" id="yesScreen">
  <div class="yes-heart">💖</div>
  <h2 class="yes-title">¡Qué felicidad!</h2>
  <p style="font-size:1.4rem; font-style:italic; color:var(--burgundy); margin: 16px 0 24px;">
    Eres oficialmente mi novia 🌹
  </p>
  <p class="yes-sub">Te quiero muchísimo, Mar</p>
</div>

<script>
  // Petals
  const petalEmojis = ['🌸','🌹','✿','❀','🌺'];
  const container = document.getElementById('petals');
  for (let i = 0; i < 18; i++) {
    const p = document.createElement('div');
    p.className = 'petal';
    p.textContent = petalEmojis[Math.floor(Math.random() * petalEmojis.length)];
    p.style.left = Math.random() * 100 + 'vw';
    p.style.animationDuration = (6 + Math.random() * 8) + 's';
    p.style.animationDelay = (-Math.random() * 10) + 's';
    p.style.fontSize = (0.8 + Math.random() * 0.8) + 'rem';
    container.appendChild(p);
  }

  // Load photos
  function loadPhoto(input) {
    const slot = input.closest('.photo-slot');
    const img = slot.querySelector('img');
    const placeholder = slot.querySelector('.photo-placeholder');
    const file = input.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = e => {
      img.src = e.target.result;
      img.style.display = 'block';
      placeholder.style.opacity = '0';
    };
    reader.readAsDataURL(file);
  }

  // No button runs away
  function moveNo() {
    const btn = document.getElementById('noBtn');
    const vw = window.innerWidth - 150;
    const vh = window.innerHeight - 60;
    const x = Math.floor(Math.random() * vw);
    const y = Math.floor(Math.random() * vh);
    btn.style.position = 'fixed';
    btn.style.left = x + 'px';
    btn.style.top = y + 'px';
    btn.style.zIndex = '50';
  }

  // Say yes
  function sayYes() {
    const screen = document.getElementById('yesScreen');
    screen.classList.add('active');
    // Confetti
    const emojis = ['🌸','💕','🌹','✨','💖','🎀','🌺'];
    for (let i = 0; i < 30; i++) {
      const c = document.createElement('div');
      c.className = 'confetti-piece';
      c.textContent = emojis[Math.floor(Math.random() * emojis.length)];
      c.style.left = Math.random() * 100 + 'vw';
      c.style.animationDuration = (2 + Math.random() * 2) + 's';
      c.style.animationDelay = (Math.random() * 2) + 's';
      document.body.appendChild(c);
    }
  }
</script>
</body>
</html>
