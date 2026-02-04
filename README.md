<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Valentine 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

<style>
@import url('https://fonts.googleapis.com/css2?family=Pacifico&family=Poppins:wght@300;500&display=swap');

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  height: 100vh;
  background: radial-gradient(circle at top, #2b0a3d, #0b0210);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: 'Poppins', sans-serif;
  overflow: hidden;
  color: white;
}

.container {
  text-align: center;
  padding: 2.5rem 1.5rem;
  width: 90%;
  max-width: 360px;
  background: rgba(255,255,255,0.1);
  backdrop-filter: blur(14px);
  border-radius: 22px;
  box-shadow: 0 0 35px rgba(255, 80, 150, 0.4);
  animation: fadeIn 2s ease;
}

h1 {
  font-family: 'Pacifico', cursive;
  font-size: 2.2rem;
  margin-bottom: 0.8rem;
  color: #ffb3c6;
}

.name {
  font-size: 1.1rem;
  margin-bottom: 1.8rem;
  opacity: 0.9;
}

.buttons {
  display: flex;
  justify-content: center;
  gap: 1.2rem;
}

button {
  padding: 0.7rem 1.8rem;
  font-size: 1rem;
  border-radius: 25px;
  border: none;
  cursor: pointer;
}

#yes {
  background: linear-gradient(135deg, #ff4d6d, #ff8fa3);
  color: white;
  box-shadow: 0 0 20px rgba(255,77,109,0.8);
}

#no {
  background: rgba(255,255,255,0.2);
  color: white;
  position: relative;
}

.message {
  margin-top: 1.8rem;
  font-size: 1.3rem;
  color: #ffd6e0;
  display: none;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(40px); }
  to { opacity: 1; transform: translateY(0); }
}

/* floating hearts */
.heart {
  position: absolute;
  color: pink;
  font-size: 18px;
  animation: floatUp 6s linear infinite;
}

@keyframes floatUp {
  from { transform: translateY(100vh); opacity: 1; }
  to { transform: translateY(-10vh); opacity: 0; }
}

canvas {
  position: fixed;
  inset: 0;
  pointer-events: none;
}
</style>
</head>

<body>

<audio autoplay loop>
  <source src="https://cdn.pixabay.com/audio/2023/02/14/audio_5c63f0c6a1.mp3" type="audio/mpeg">
</audio>

<canvas id="fireworks"></canvas>

<div class="container">
  <h1>Will you be my Valentine? 💖</h1>
  <div class="name">Poorna Sri Rasinti</div>

  <div class="buttons">
    <button id="yes">Yes ❤️</button>
    <button id="no">No 💔</button>
  </div>

  <div class="message" id="msg">
    You just made my heart yours 💕✨
  </div>
</div>

<script>
/* No button escape */
const noBtn = document.getElementById("no");
noBtn.addEventListener("mouseover", () => {
  const x = Math.random() * 150 - 75;
  const y = Math.random() * 150 - 75;
  noBtn.style.transform = `translate(${x}px, ${y}px)`;
});

/* Hearts animation */
setInterval(() => {
  const heart = document.createElement("div");
  heart.className = "heart";
  heart.innerHTML = "❤️";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.fontSize = Math.random() * 20 + 12 + "px";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 6000);
}, 500);

/* Fireworks */
const canvas = document.getElementById("fireworks");
const ctx = canvas.getContext("2d");
canvas.width = innerWidth;
canvas.height = innerHeight;

function firework() {
  for (let i = 0; i < 100; i++) {
    ctx.fillStyle = `hsl(${Math.random()*360},100%,70%)`;
    ctx.beginPath();
    ctx.arc(
      Math.random() * canvas.width,
      Math.random() * canvas.height,
      Math.random() * 3,
      0,
      Math.PI * 2
    );
    ctx.fill();
  }
}

document.getElementById("yes").onclick = () => {
  document.getElementById("msg").style.display = "block";
  firework();
};
</script>

</body>
</html>
