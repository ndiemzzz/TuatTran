<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Bạn có phải là chó không?</title>
<style>
  :root {
    box-sizing: border-box;
    padding-top: env(safe-area-inset-top, 0px);
    padding-bottom: env(safe-area-inset-bottom, 0px);
    --bg: #fff4e0;
    --card: #ffffff;
    --text: #3b2a1a;
    --yes: #2e9e5b;
    --no: #d64545;
    --rain: #e0457b;
  }
  @media (prefers-color-scheme: dark) {
    :root:not([data-theme="light"]) {
      --bg: #1c1612; --card: #2a211a; --text: #f6e9d8; --rain: #ff7aa8;
    }
  }
  :root[data-theme="dark"] {
    --bg: #1c1612; --card: #2a211a; --text: #f6e9d8; --rain: #ff7aa8;
  }
  html { height: 100%; }
  * { box-sizing: border-box; }
  body {
    margin: 0;
    min-height: 100%;
    background: var(--bg);
    color: var(--text);
    font-family: "Segoe UI", system-ui, -apple-system, Roboto, sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }
  .card {
    position: relative;
    z-index: 2;
    background: var(--card);
    border-radius: 24px;
    padding: 32px 24px;
    width: min(92vw, 460px);
    text-align: center;
    box-shadow: 0 10px 30px rgba(0,0,0,.18);
  }
  .emoji { font-size: 64px; line-height: 1; }
  h1 { margin: 12px 0 6px; font-size: 1.6rem; }
  .sub { margin: 0 0 24px; opacity: .75; min-height: 1.4em; }
  .buttons {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }
  button {
    border: 0;
    border-radius: 14px;
    color: #fff;
    font-weight: 700;
    cursor: pointer;
    transition: font-size .25s ease, padding .25s ease, transform .1s ease;
  }
  button:active { transform: scale(.95); }
  #yes { background: var(--yes); font-size: 18px; padding: 12px 24px; }
  #no  { background: var(--no);  font-size: 18px; padding: 12px 24px; }
  .avatar { width: 140px; height: 140px; border-radius: 50%; object-fit: cover; border: 4px solid var(--rain); box-shadow: 0 4px 14px rgba(0,0,0,.3); }
  .hidden { display: none !important; }

  /* Mưa chữ */
  #rain { position: fixed; inset: 0; z-index: 3; pointer-events: none; overflow: hidden; }
  .drop {
    position: absolute;
    top: -10vh;
    color: var(--rain);
    font-weight: 800;
    white-space: nowrap;
    text-shadow: 0 2px 6px rgba(0,0,0,.2);
    animation-name: fall;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
  }
  @keyframes fall {
    0%   { transform: translateY(0) rotate(var(--rot)); opacity: 0; }
    10%  { opacity: 1; }
    100% { transform: translateY(115vh) rotate(var(--rot)); opacity: .9; }
  }
  @media (prefers-reduced-motion: reduce) {
    .drop { animation-duration: 12s !important; }
  }
</style>
</head>
<body>
  <div id="rain"></div>

  <main class="card">
    <div class="emoji" id="emoji">🐶</div>
    <h1 id="title">Bạn có phải là chó không?</h1>
    <p class="sub" id="sub">Vui lòng xác nhận danh tính.</p>
    <div class="buttons">
      <button id="yes">Yes</button>
      <button id="no">No</button>
    </div>
  </main>

<script>
  const yes = document.getElementById('yes');
  const no = document.getElementById('no');
  const sub = document.getElementById('sub');
  const title = document.getElementById('title');
  const emoji = document.getElementById('emoji');
  const rain = document.getElementById('rain');

  const lines = [
    "Chắc chưa?",
    "Nghĩ lại đi...",
    "Nút Yes đang to ra kìa 👀",
    "Còn bấm No nữa thì...",
    ""
  ];
  let count = 0;

  no.addEventListener('click', () => {
    count++;
    if (count < 5) {
      // Nút Yes to dần
      const size = 18 + count * 12;
      yes.style.fontSize = size + 'px';
      yes.style.padding = (12 + count * 8) + 'px ' + (24 + count * 14) + 'px';
      sub.textContent = lines[count - 1];
    } else {
      startRain();
    }
  });

  yes.addEventListener('click', () => {
    emoji.textContent = '🐕';
    title.textContent = 'Biết ngay mà! Gâu gâu!';
    sub.textContent = 'Xác nhận thành công: bạn là chó 🦴';
    no.classList.add('hidden');
    yes.classList.add('hidden');
  });

  function startRain() {
    no.classList.add('hidden');
    emoji.innerHTML = '<img class="avatar" alt="Tuất" src="data:image/jpeg;base64,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">';
    title.textContent = 'Bạn là 1 con Tuất';
    sub.textContent = '';
    for (let i = 0; i < 60; i++) {
      const d = document.createElement('span');
      d.className = 'drop';
      d.textContent = 'Tuất Huyền Trân';
      d.style.color = 'hsl(' + Math.floor(Math.random() * 360) + ', 85%, 58%)';
      d.style.left = Math.random() * 100 + 'vw';
      d.style.fontSize = (14 + Math.random() * 22) + 'px';
      d.style.animationDuration = (4 + Math.random() * 6) + 's';
      d.style.animationDelay = (-Math.random() * 10) + 's';
      d.style.setProperty('--rot', (Math.random() * 20 - 10) + 'deg');
      rain.appendChild(d);
    }
  }
</script>
</body>
</html>
