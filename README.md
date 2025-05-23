# <div align="center">🎮✨ Hi there! I'm **YUM YUM** ✨🎮</div>

<div align="center">
  
  ![Typing SVG](https://readme-typing-svg.herokuapp.com?font=Orbitron&size=35&duration=2000&pause=500&color=00D4FF&center=true&vCenter=true&width=800&lines=3D+Developer+%F0%9F%8C%8C;Game+Creator+%F0%9F%8E%AE;WebGL+Master+%F0%9F%94%A5;Interactive+Experiences+%E2%9C%A8;Welcome+to+my+3D+World!+%F0%9F%9A%80)
  
</div>

---

## 🎮 **Interactive 3D Portfolio**

<div align="center">

### 🌟 **Play My Mini Game!** 🌟
*Click and drag to control!*

```html
<div style="width: 100%; height: 400px; background: linear-gradient(45deg, #000428, #004e92); border-radius: 20px; display: flex; align-items: center; justify-content: center; position: relative; overflow: hidden;">
  <canvas id="gameCanvas" width="800" height="400" style="border-radius: 15px; cursor: pointer;"></canvas>
  <div style="position: absolute; top: 20px; left: 20px; color: #00D4FF; font-family: 'Courier New'; font-size: 18px; text-shadow: 0 0 10px #00D4FF;">
    🎮 3D Cube Game - Score: <span id="score">0</span>
  </div>
</div>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
let score = 0;
let mouseX = 400, mouseY = 200;
let cubes = [];
let particles = [];

// Initialize cubes
for(let i = 0; i < 5; i++) {
  cubes.push({
    x: Math.random() * 800,
    y: Math.random() * 400,
    z: Math.random() * 100,
    vx: (Math.random() - 0.5) * 4,
    vy: (Math.random() - 0.5) * 4,
    rotation: 0,
    color: `hsl(${Math.random() * 360}, 70%, 60%)`
  });
}

canvas.addEventListener('mousemove', (e) => {
  const rect = canvas.getBoundingClientRect();
  mouseX = e.clientX - rect.left;
  mouseY = e.clientY - rect.top;
});

canvas.addEventListener('click', (e) => {
  // Create particle explosion
  for(let i = 0; i < 20; i++) {
    particles.push({
      x: mouseX,
      y: mouseY,
      vx: (Math.random() - 0.5) * 10,
      vy: (Math.random() - 0.5) * 10,
      life: 60,
      color: `hsl(${Math.random() * 360}, 100%, 50%)`
    });
  }
  score += 10;
  document.getElementById('score').textContent = score;
});

function drawCube(x, y, size, rotation, color) {
  ctx.save();
  ctx.translate(x, y);
  ctx.rotate(rotation);
  
  // 3D effect
  ctx.fillStyle = color;
  ctx.fillRect(-size/2, -size/2, size, size);
  
  // Lighter top face
  ctx.fillStyle = `${color}DD`;
  ctx.fillRect(-size/2 - 5, -size/2 - 5, size, size);
  
  // Shadow
  ctx.fillStyle = 'rgba(0,0,0,0.3)';
  ctx.fillRect(-size/2 + 3, -size/2 + 3, size, size);
  
  ctx.restore();
}

function animate() {
  // Clear canvas with trail effect
  ctx.fillStyle = 'rgba(0, 20, 40, 0.1)';
  ctx.fillRect(0, 0, 800, 400);
  
  // Update and draw cubes
  cubes.forEach(cube => {
    cube.x += cube.vx;
    cube.y += cube.vy;
    cube.rotation += 0.02;
    
    // Bounce off walls
    if(cube.x <= 0 || cube.x >= 800) cube.vx *= -1;
    if(cube.y <= 0 || cube.y >= 400) cube.vy *= -1;
    
    // Attraction to mouse
    const dx = mouseX - cube.x;
    const dy = mouseY - cube.y;
    const distance = Math.sqrt(dx * dx + dy * dy);
    
    if(distance < 100) {
      cube.vx += dx * 0.0001;
      cube.vy += dy * 0.0001;
    }
    
    drawCube(cube.x, cube.y, 30 + cube.z * 0.3, cube.rotation, cube.color);
  });
  
  // Update and draw particles
  particles = particles.filter(particle => {
    particle.x += particle.vx;
    particle.y += particle.vy;
    particle.vy += 0.1; // gravity
    particle.life--;
    
    if(particle.life > 0) {
      ctx.fillStyle = particle.color;
      ctx.globalAlpha = particle.life / 60;
      ctx.fillRect(particle.x - 2, particle.y - 2, 4, 4);
      ctx.globalAlpha = 1;
      return true;
    }
    return false;
  });
  
  requestAnimationFrame(animate);
}

animate();
</script>
```

</div>

---

## 🌌 **3D About Me**

<div align="center">

### 🚀 **Rotating 3D Developer Card** 🚀

```html
<div style="perspective: 1000px; display: flex; justify-content: center; margin: 50px 0;">
  <div style="
    width: 300px; 
    height: 200px; 
    transform-style: preserve-3d; 
    animation: rotate3d 10s infinite linear;
    position: relative;
  ">
    <div style="
      position: absolute;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      border-radius: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      transform: rotateY(0deg) translateZ(100px);
      color: white;
      font-family: 'Courier New';
      text-align: center;
    ">
      <div>
        <h3>🎮 YUM YUM</h3>
        <p>3D Developer</p>
      </div>
    </div>
    <div style="
      position: absolute;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
      border-radius: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      transform: rotateY(90deg) translateZ(100px);
      color: white;
      font-family: 'Courier New';
      text-align: center;
    ">
      <div>
        <h3>⚡ Skills</h3>
        <p>WebGL | Three.js</p>
      </div>
    </div>
    <div style="
      position: absolute;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
      border-radius: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      transform: rotateY(180deg) translateZ(100px);
      color: white;
      font-family: 'Courier New';
      text-align: center;
    ">
      <div>
        <h3>🎯 Focus</h3>
        <p>Interactive Experiences</p>
      </div>
    </div>
    <div style="
      position: absolute;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
      border-radius: 15px;
      display: flex;
      align-items: center;
      justify-content: center;
      transform: rotateY(270deg) translateZ(100px);
      color: white;
      font-family: 'Courier New';
      text-align: center;
    ">
      <div>
        <h3>🚀 Goal</h3>
        <p>Next-Gen Web</p>
      </div>
    </div>
  </div>
</div>

<style>
@keyframes rotate3d {
  0% { transform: rotateY(0deg); }
  100% { transform: rotateY(360deg); }
}
</style>
```

</div>

<img align="right" height="250" src="https://media.tenor.com/nb_83xDs3ekAAAAM/aespa-karina.gif" />

```javascript
const yumyum = {
    code: ["JavaScript", "TypeScript", "Python", "Go", "GLSL"],
    technologies: {
        frontEnd: ["React", "Three.js", "WebGL", "Canvas API"],
        backEnd: ["Node.js", "Express", "WebRTC"],
        databases: ["MongoDB", "MySQL", "PostgreSQL"],
        gameEngine: ["Unity", "Unreal Engine", "Custom WebGL"],
        3D: ["Blender", "Maya", "3ds Max"]
    },
    currentFocus: "Building immersive 3D web experiences",
    funFact: "I render 60fps dreams in real-time! 🎮✨"
};
```

---

## 🎮 **Gaming Zone**

<div align="center">

### 🕹️ **Snake Game 3D Style** 🕹️
*Use WASD or Arrow Keys*

```html
<div style="width: 100%; max-width: 600px; margin: 0 auto; background: #000; border-radius: 15px; padding: 20px;">
  <div style="display: flex; justify-content: space-between; color: #00ff00; font-family: 'Courier New'; margin-bottom: 10px;">
    <span>Score: <span id="snakeScore">0</span></span>
    <span>High Score: <span id="highScore">0</span></span>
  </div>
  <canvas id="snakeGame" width="560" height="400" style="border: 2px solid #00ff00; background: linear-gradient(45deg, #001100, #003300);"></canvas>
  <div style="text-align: center; color: #00ff00; font-family: 'Courier New'; margin-top: 10px;">
    Press SPACE to start/restart
  </div>
</div>

<script>
const snakeCanvas = document.getElementById('snakeGame');
const snakeCtx = snakeCanvas.getContext('2d');
const gridSize = 20;
const tileCount = snakeCanvas.width / gridSize;

let snake = [{x: 10, y: 10}];
let food = {};
let dx = 0, dy = 0;
let snakeScore = 0;
let gameRunning = false;

function randomFood() {
  food = {
    x: Math.floor(Math.random() * tileCount),
    y: Math.floor(Math.random() * tileCount)
  };
}

function drawGame() {
  // Clear canvas
  snakeCtx.fillStyle = 'rgba(0, 20, 0, 0.2)';
  snakeCtx.fillRect(0, 0, snakeCanvas.width, snakeCanvas.height);
  
  // Draw snake with 3D effect
  snake.forEach((segment, index) => {
    const brightness = 1 - (index * 0.1);
    snakeCtx.fillStyle = `hsl(120, 100%, ${50 + brightness * 20}%)`;
    snakeCtx.fillRect(segment.x * gridSize + 2, segment.y * gridSize + 2, gridSize - 4, gridSize - 4);
    
    // 3D shadow effect
    snakeCtx.fillStyle = 'rgba(0, 255, 0, 0.3)';
    snakeCtx.fillRect(segment.x * gridSize, segment.y * gridSize, gridSize - 2, gridSize - 2);
  });
  
  // Draw food with glow effect
  snakeCtx.shadowColor = '#ff0080';
  snakeCtx.shadowBlur = 20;
  snakeCtx.fillStyle = '#ff0080';
  snakeCtx.fillRect(food.x * gridSize + 4, food.y * gridSize + 4, gridSize - 8, gridSize - 8);
  snakeCtx.shadowBlur = 0;
}

function updateGame() {
  if (!gameRunning) return;
  
  const head = {x: snake[0].x + dx, y: snake[0].y + dy};
  
  // Check wall collision
  if (head.x < 0 || head.x >= tileCount || head.y < 0 || head.y >= tileCount) {
    gameRunning = false;
    return;
  }
  
  // Check self collision
  if (snake.some(segment => segment.x === head.x && segment.y === head.y)) {
    gameRunning = false;
    return;
  }
  
  snake.unshift(head);
  
  // Check food collision
  if (head.x === food.x && head.y === food.y) {
    snakeScore += 10;
    document.getElementById('snakeScore').textContent = snakeScore;
    randomFood();
  } else {
    snake.pop();
  }
}

function gameLoop() {
  updateGame();
  drawGame();
  setTimeout(gameLoop, 150);
}

document.addEventListener('keydown', (e) => {
  if (e.code === 'Space') {
    gameRunning = !gameRunning;
    if (gameRunning && snake.length === 1) {
      snakeScore = 0;
      snake = [{x: 10, y: 10}];
      randomFood();
    }
  }
  
  if (!gameRunning) return;
  
  switch(e.key) {
    case 'ArrowUp':
    case 'w':
    case 'W':
      if (dy === 0) { dx = 0; dy = -1; }
      break;
    case 'ArrowDown':
    case 's':
    case 'S':
      if (dy === 0) { dx = 0; dy = 1; }
      break;
    case 'ArrowLeft':
    case 'a':
    case 'A':
      if (dx === 0) { dx = -1; dy = 0; }
      break;
    case 'ArrowRight':
    case 'd':
    case 'D':
      if (dx === 0) { dx = 1; dy = 0; }
      break;
  }
});

randomFood();
gameLoop();
</script>
```

</div>

---

## 📊 **3D GitHub Analytics**

<div align="center">
  
### 🌟 **Holographic Stats** 🌟

```html
<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap; margin: 30px 0;">
  <div style="
    width: 250px;
    height: 150px;
    background: linear-gradient(45deg, rgba(0,212,255,0.1), rgba(255,0,128,0.1));
    border: 1px solid rgba(0,212,255,0.3);
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(10px);
    box-shadow: 0 8px 32px rgba(0,212,255,0.2);
    animation: float 3s ease-in-out infinite;
  ">
    <h3 style="color: #00D4FF; margin: 0; text-shadow: 0 0 10px #00D4FF;">🚀 Commits</h3>
    <h2 style="color: #fff; margin: 5px 0; font-size: 2em; text-shadow: 0 0 20px #00D4FF;">1,337+</h2>
    <p style="color: #aaa; margin: 0;">This year</p>
  </div>
  
  <div style="
    width: 250px;
    height: 150px;
    background: linear-gradient(45deg, rgba(255,0,128,0.1), rgba(128,0,255,0.1));
    border: 1px solid rgba(255,0,128,0.3);
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(10px);
    box-shadow: 0 8px 32px rgba(255,0,128,0.2);
    animation: float 3s ease-in-out infinite 0.5s;
  ">
    <h3 style="color: #ff0080; margin: 0; text-shadow: 0 0 10px #ff0080;">⭐ Stars</h3>
    <h2 style="color: #fff; margin: 5px 0; font-size: 2em; text-shadow: 0 0 20px #ff0080;">420+</h2>
    <p style="color: #aaa; margin: 0;">Earned</p>
  </div>
  
  <div style="
    width: 250px;
    height: 150px;
    background: linear-gradient(45deg, rgba(128,255,0,0.1), rgba(0,255,128,0.1));
    border: 1px solid rgba(128,255,0,0.3);
    border-radius: 15px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(10px);
    box-shadow: 0 8px 32px rgba(128,255,0,0.2);
    animation: float 3s ease-in-out infinite 1s;
  ">
    <h3 style="color: #80ff00; margin: 0; text-shadow: 0 0 10px #80ff00;">🔥 Streak</h3>
    <h2 style="color: #fff; margin: 5px 0; font-size: 2em; text-shadow: 0 0 20px #80ff00;">69</h2>
    <p style="color: #aaa; margin: 0;">Days</p>
  </div>
</div>

<style>
@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}
</style>
```

<img src="https://streak-stats.demolab.com?user=fathuur7&theme=neon&hide_border=true&background=000000&stroke=00D4FF&ring=FF0080&fire=80FF00&currStreakLabel=FFFFFF" height="200"/>

</div>

---

## 🛠️ **3D Tech Arsenal**

<div align="center">

### 🌈 **Animated Tech Stack** 🌈

```html
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap: 20px; max-width: 800px; margin: 0 auto; padding: 20px;">
  <div style="text-align: center; animation: techFloat 2s ease-in-out infinite;">
    <div style="width: 80px; height: 80px; margin: 0 auto 10px; background: linear-gradient(45deg, #F7DF1E, #FFD700); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 30px; box-shadow: 0 10px 30px rgba(247,223,30,0.3); transform-style: preserve-3d;">
      <span style="transform: translateZ(20px);">JS</span>
    </div>
    <p style="color: #F7DF1E; font-weight: bold; text-shadow: 0 0 10px #F7DF1E;">JavaScript</p>
  </div>
  
  <div style="text-align: center; animation: techFloat 2s ease-in-out infinite 0.2s;">
    <div style="width: 80px; height: 80px; margin: 0 auto 10px; background: linear-gradient(45deg, #007ACC, #0099FF); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 30px; box-shadow: 0 10px 30px rgba(0,122,204,0.3);">
      <span style="transform: translateZ(20px);">TS</span>
    </div>
    <p style="color: #007ACC; font-weight: bold; text-shadow: 0 0 10px #007ACC;">TypeScript</p>
  </div>
  
  <div style="text-align: center; animation: techFloat 2s ease-in-out infinite 0.4s;">
    <div style="width: 80px; height: 80px; margin: 0 auto 10px; background: linear-gradient(45deg, #61DAFB, #00D8FF); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 30px; box-shadow: 0 10px 30px rgba(97,218,251,0.3);">
      <span style="transform: translateZ(20px);">⚛️</span>
    </div>
    <p style="color: #61DAFB; font-weight: bold; text-shadow: 0 0 10px #61DAFB;">React</p>
  </div>
  
  <div style="text-align: center; animation: techFloat 2s ease-in-out infinite 0.6s;">
    <div style="width: 80px; height: 80px; margin: 0 auto 10px; background: linear-gradient(45deg, #000000, #333333); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 25px; box-shadow: 0 10px 30px rgba(255,255,255,0.1); border: 2px solid #fff;">
      <span style="transform: translateZ(20px); color: white;">3JS</span>
    </div>
    <p style="color: #ffffff; font-weight: bold; text-shadow: 0 0 10px #ffffff;">Three.js</p>
  </div>
  
  <div style="text-align: center; animation: techFloat 2s ease-in-out infinite 0.8s;">
    <div style="width: 80px; height: 80px; margin: 0 auto 10px; background: linear-gradient(45deg, #FF6B6B, #FF8E8E); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 25px; box-shadow: 0 10px 30px rgba(255,107,107,0.3);">
      <span style="transform: translateZ(20px);">GL</span>
    </div>
    <p style="color: #FF6B6B; font-weight: bold; text-shadow: 0 0 10px #FF6B6B;">WebGL</p>
  </div>
  
  <div style="text-align: center; animation: techFloat 2s ease-in-out infinite 1s;">
    <div style="width: 80px; height: 80px; margin: 0 auto 10px; background: linear-gradient(45deg, #4CAF50, #66BB6A); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 25px; box-shadow: 0 10px 30px rgba(76,175,80,0.3);">
      <span style="transform: translateZ(20px);">🎮</span>
    </div>
    <p style="color: #4CAF50; font-weight: bold; text-shadow: 0 0 10px #4CAF50;">Unity</p>
  </div>
</div>

<style>
@keyframes techFloat {
  0%, 100% { transform: translateY(0px) rotateY(0deg); }
  25% { transform: translateY(-5px) rotateY(90deg); }
  50% { transform: translateY(-10px) rotateY(180deg); }
  75% { transform: translateY(-5px) rotateY(270deg); }
}
</style>
```

</div>

---

## 🎯 **Epic Projects Showcase**

<div align="center">

### 🚀 **3D Project Gallery** 🚀

```html
<div style="display: flex; justify-content: center; gap: 30px; flex-wrap: wrap; margin: 40px 0;">
  <div style="
    width: 300px;
    height: 200px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 20px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 15px 35px rgba(102, 126, 234, 0.3);
  " onmouseover="this.style.transform='scale(1.05) rotateX(5deg)'" onmouseout="this.style.transform='scale(1) rotateX(0deg)'">
    <div style="position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.3); display: flex; flex-direction: column; justify-content: center; align-items: center; color: white; text-align: center; padding: 20px;">
      <h3 style="margin: 0 0 10px 0; font-size: 1.5em;">🌌 3D Space Explorer</h3>
      <p style="margin: 0 0 15px 0; opacity: 0.9;">Interactive solar system with WebGL</p>
      <div style="background: rgba(255,255,255,0.2); padding: 5px 15px; border-radius: 20px; font-size: 0.9em;">Three.js • WebGL • Physics</div>
    </div>
  </div>
  
  <div style="
    width: 300px;
    height: 200px;
    background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
    border-radius: 20px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 15px 35px rgba(240, 147, 251, 0.3);
  " onmouseover="this.style.transform='scale(1.05) rotateX(5deg)'" onmouseout="this.style.transform='scale(1) rotateX(0deg)'">
    <div style="position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.3); display: flex; flex-direction: column; justify-content: center; align-items: center; color: white; text-align: center; padding: 20px;">
      <h3 style="margin: 0 0 10px 0; font-size: 1.5em;">🎮 Neon Racer</h3>
      <p style="margin: 0 0 15px 0; opacity: 0.9;">High-speed 3D racing game</p>
      <div style="background: rgba(255,255,255,0.2); padding: 5px 15px; border-radius: 20px; font-size: 0.9em;">Unity • C# • Multiplayer</div>
    </div>
  </div>
  
  <div style="
    width: 300px;
    height: 200px;
    background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
    border-radius: 20px;
    position: relative;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 15px 35px rgba(79, 172, 254, 0.3);
  " onmouseover="this.style.transform='scale(1.05) rotateX(5deg)'" onmouseout="this.style.transform='scale(1) rotateX(0deg)'">
    <div style="position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: rgba(0,0,0,0.3); display: flex; flex-direction: column; justify-content: center; align-items: center; color: white; text-align: center; padding: 20px;">
      <h3 style="margin: 0 0 10px 0; font-size: 1.5em;">🏗️ VR Builder</h3>
      <p style="margin: 0 0 15px 0; opacity: 0.9;">Virtual reality construction simulator</p>
      <div style="background: rgba(255,255,255,0.2); padding: 5px 15px; border-radius: 20px; font-size: 0.9em;">WebXR • A-Frame • VR</div>
    </div>
  </div>
</div>
```

</div>

---

## 📈 **Holographic Contribution Graph**

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=fathuur7&theme=react-dark&bg_color=000000&hide_border=true&line=00D4FF&point=FF0080&color=FFFFFF" width="100%"/>
</div>

---

## 🏆 **Achievement Unlocked**

<div align="center">

### 🎯 **Gaming Trophies** 🎯

```html
<div style="display: flex; justify-content: center; gap: 20px; flex-wrap: wrap; margin: 30px 0;">
  <div style="
    width: 120px;
    height: 120px;
    background: radial-gradient(circle, #FFD700, #FFA500);
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    box-shadow: 0 0 30px rgba(255, 215, 0, 0.5);
    animation: trophy-glow 2s ease-in-out infinite alternate;
    position: relative;
  ">
    <div style="font-size: 40px; margin-bottom: 5px;">🏆</div>
    <div style="font-size: 12px; font-weight: bold; color: #8B4513;">LEGENDARY</div>
    <div style="font-size: 10px; color: #8B4513;">CODER</div>
  </div>
  
  <div style="
    width: 120px;
    height: 120px;
    background: radial-gradient(circle, #C0C0C0, #A0A0A0);
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    box-shadow: 0 0 20px rgba(192, 192, 192, 0.5);
    animation: trophy-glow 2s ease-in-out infinite alternate 0.5s;
  ">
    <div style="font-size: 40px; margin-bottom: 5px;">🥈</div>
    <div style="font-size: 12px; font-weight: bold; color: #4A4A4A;">EPIC</div>
    <div style="font-size: 10px; color: #4A4A4A;">DEVELOPER</div>
  </div>
  
  <div style="
    width: 120px;
    height: 120px;
    background: radial-gradient(circle, #CD7F32, #B8860B);
    border-radius: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    box-shadow: 0 0 15px rgba(205, 127, 50, 0.5);
    animation: trophy-glow 2s ease-in-out infinite alternate 1s;
  ">
    <div style="font-size: 40px; margin-bottom: 5px;">🥉</div>
    <div style="font-size: 12px; font-weight: bold; color: #654321;">RARE</div>
    <div style="font-size: 10px; color: #654321;">CREATOR</div>
  </div>
</div>

<style>
@keyframes trophy-glow {
  0% { transform: scale(1) rotateY(0deg); box-shadow: 0 0 20px rgba(255, 215, 0, 0.3); }
  100% { transform: scale(1.05) rotateY(10deg); box-shadow: 0 0 40px rgba(255, 215, 0, 0.8); }
}
</style>
```

<img src="https://github-profile-trophy.vercel.app/?username=fathuur7&theme=radical&no-frame=true&no-bg=true&margin-w=4&row=2"/>

</div>

---

## 🌌 **3D Particle System**

<div align="center">

### ✨ **Interactive Cosmic Background** ✨

```html
<div style="width: 100%; height: 300px; background: linear-gradient(135deg, #000428, #004e92); border-radius: 20px; position: relative; overflow: hidden; margin: 30px 0;">
  <canvas id="particleCanvas" width="800" height="300" style="width: 100%; height: 100%; border-radius: 20px; cursor: crosshair;"></canvas>
  <div style="position: absolute; top: 20px; left: 20px; color: #00D4FF; font-family: 'Orbitron', monospace; font-size: 18px; text-shadow: 0 0 10px #00D4FF;">
    🌌 Cosmic Code Universe - Move your mouse!
  </div>
</div>

<script>
const particleCanvas = document.getElementById('particleCanvas');
const pCtx = particleCanvas.getContext('2d');
let particles = [];
let mousePos = { x: 400, y: 150 };

class Particle {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.vx = (Math.random() - 0.5) * 2;
    this.vy = (Math.random() - 0.5) * 2;
    this.life = Math.random() * 100 + 50;
    this.maxLife = this.life;
    this.size = Math.random() * 3 + 1;
    this.color = `hsl(${180 + Math.random() * 60}, 100%, ${50 + Math.random() * 30}%)`;
  }
  
  update() {
    // Attraction to mouse
    const dx = mousePos.x - this.x;
    const dy = mousePos.y - this.y;
    const distance = Math.sqrt(dx * dx + dy * dy);
    
    if (distance < 100) {
      this.vx += dx * 0.0005;
      this.vy += dy * 0.0005;
    }
    
    this.x += this.vx;
    this.y += this.vy;
    this.life--;
    
    // Wrap around edges
    if (this.x < 0) this.x = particleCanvas.width;
    if (this.x > particleCanvas.width) this.x = 0;
    if (this.y < 0) this.y = particleCanvas.height;
    if (this.y > particleCanvas.height) this.y = 0;
  }
  
  draw() {
    const alpha = this.life / this.maxLife;
    pCtx.save();
    pCtx.globalAlpha = alpha;
    pCtx.fillStyle = this.color;
    pCtx.shadowColor = this.color;
    pCtx.shadowBlur = 10;
    pCtx.beginPath();
    pCtx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
    pCtx.fill();
    pCtx.restore();
  }
}

// Initialize particles
for (let i = 0; i < 150; i++) {
  particles.push(new Particle(
    Math.random() * particleCanvas.width,
    Math.random() * particleCanvas.height
  ));
}

particleCanvas.addEventListener('mousemove', (e) => {
  const rect = particleCanvas.getBoundingClientRect();
  mousePos.x = (e.clientX - rect.left) * (particleCanvas.width / rect.width);
  mousePos.y = (e.clientY - rect.top) * (particleCanvas.height / rect.height);
});

function animateParticles() {
  pCtx.fillStyle = 'rgba(0, 4, 40, 0.1)';
  pCtx.fillRect(0, 0, particleCanvas.width, particleCanvas.height);
  
  // Update and draw particles
  particles = particles.filter(particle => {
    particle.update();
    particle.draw();
    return particle.life > 0;
  });
  
  // Add new particles
  while (particles.length < 150) {
    particles.push(new Particle(
      Math.random() * particleCanvas.width,
      Math.random() * particleCanvas.height
    ));
  }
  
  // Draw connections
  pCtx.strokeStyle = 'rgba(0, 212, 255, 0.1)';
  pCtx.lineWidth = 1;
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const distance = Math.sqrt(dx * dx + dy * dy);
      
      if (distance < 80) {
        pCtx.beginPath();
        pCtx.moveTo(particles[i].x, particles[i].y);
        pCtx.lineTo(particles[j].x, particles[j].y);
        pCtx.stroke();
      }
    }
  }
  
  requestAnimationFrame(animateParticles);
}

animateParticles();
</script>
```

</div>

---

## 🎵 **Audio Visualizer**

<div align="center">

### 🎶 **Music-Reactive Animation** 🎶

```html
<div style="width: 100%; max-width: 600px; margin: 0 auto; background: #000; border-radius: 15px; padding: 20px;">
  <div style="text-align: center; color: #00ff88; font-family: 'Orbitron'; margin-bottom: 15px;">
    🎵 Audio Spectrum Visualizer 🎵
  </div>
  <canvas id="audioCanvas" width="560" height="200" style="width: 100%; background: linear-gradient(90deg, #000, #001a1a, #000); border-radius: 10px;"></canvas>
  <div style="text-align: center; margin-top: 15px;">
    <button onclick="toggleAudio()" style="
      background: linear-gradient(45deg, #00ff88, #00cc66);
      border: none;
      color: #000;
      padding: 10px 20px;
      border-radius: 25px;
      font-weight: bold;
      cursor: pointer;
      font-family: 'Orbitron';
    ">🎵 Start Audio Viz</button>
  </div>
</div>

<script>
const audioCanvas = document.getElementById('audioCanvas');
const aCtx = audioCanvas.getContext('2d');
let audioRunning = false;
let bars = [];

// Initialize bars
for (let i = 0; i < 64; i++) {
  bars.push({
    height: Math.random() * 100 + 10,
    targetHeight: Math.random() * 150 + 20,
    color: `hsl(${i * 5 + 120}, 100%, 60%)`
  });
}

function toggleAudio() {
  audioRunning = !audioRunning;
  if (audioRunning) {
    animateAudio();
  }
}

function animateAudio() {
  if (!audioRunning) return;
  
  aCtx.fillStyle = 'rgba(0, 0, 0, 0.3)';
  aCtx.fillRect(0, 0, audioCanvas.width, audioCanvas.height);
  
  const barWidth = audioCanvas.width / bars.length;
  
  bars.forEach((bar, index) => {
    // Simulate audio data
    bar.targetHeight = Math.random() * 150 + 20 + Math.sin(Date.now() * 0.01 + index * 0.1) * 30;
    bar.height += (bar.targetHeight - bar.height) * 0.1;
    
    // Draw bar with glow effect
    aCtx.shadowColor = bar.color;
    aCtx.shadowBlur = 20;
    aCtx.fillStyle = bar.color;
    aCtx.fillRect(
      index * barWidth + 2, 
      audioCanvas.height - bar.height, 
      barWidth - 4, 
      bar.height
    );
    
    // Add top glow
    aCtx.shadowBlur = 5;
    aCtx.fillStyle = `${bar.color}88`;
    aCtx.fillRect(
      index * barWidth + 2, 
      audioCanvas.height - bar.height - 10, 
      barWidth - 4, 
      10
    );
  });
  
  aCtx.shadowBlur = 0;
  requestAnimationFrame(animateAudio);
}
</script>
```

</div>

---

## 🌐 **Connect With Me**

<div align="center">

### 🚀 **Social Media Portal** 🚀

```html
<div style="display: flex; justify-content: center; gap: 25px; flex-wrap: wrap; margin: 40px 0;">
  <a href="https://discord.gg/yourdiscord" style="text-decoration: none;">
    <div style="
      width: 120px;
      height: 120px;
      background: linear-gradient(135deg, #7289DA, #5B6EAE);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: white;
      transition: all 0.3s ease;
      box-shadow: 0 10px 30px rgba(114, 137, 218, 0.3);
      cursor: pointer;
    " onmouseover="this.style.transform='scale(1.1) rotateY(15deg)'; this.style.boxShadow='0 20px 40px rgba(114, 137, 218, 0.6)'" onmouseout="this.style.transform='scale(1) rotateY(0deg)'; this.style.boxShadow='0 10px 30px rgba(114, 137, 218, 0.3)'">
      <div style="font-size: 40px;">💬</div>
      <div style="font-size: 12px; font-weight: bold;">DISCORD</div>
    </div>
  </a>
  
  <a href="https://youtube.com/@yourchannel" style="text-decoration: none;">
    <div style="
      width: 120px;
      height: 120px;
      background: linear-gradient(135deg, #FF0000, #CC0000);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: white;
      transition: all 0.3s ease;
      box-shadow: 0 10px 30px rgba(255, 0, 0, 0.3);
      cursor: pointer;
    " onmouseover="this.style.transform='scale(1.1) rotateY(15deg)'; this.style.boxShadow='0 20px 40px rgba(255, 0, 0, 0.6)'" onmouseout="this.style.transform='scale(1) rotateY(0deg)'; this.style.boxShadow='0 10px 30px rgba(255, 0, 0, 0.3)'">
      <div style="font-size: 40px;">📺</div>
      <div style="font-size: 12px; font-weight: bold;">YOUTUBE</div>
    </div>
  </a>
  
  <a href="https://instagram.com/yourhandle" style="text-decoration: none;">
    <div style="
      width: 120px;
      height: 120px;
      background: linear-gradient(135deg, #E4405F, #C13584, #833AB4);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: white;
      transition: all 0.3s ease;
      box-shadow: 0 10px 30px rgba(228, 64, 95, 0.3);
      cursor: pointer;
    " onmouseover="this.style.transform='scale(1.1) rotateY(15deg)'; this.style.boxShadow='0 20px 40px rgba(228, 64, 95, 0.6)'" onmouseout="this.style.transform='scale(1) rotateY(0deg)'; this.style.boxShadow='0 10px 30px rgba(228, 64, 95, 0.3)'">
      <div style="font-size: 40px;">📷</div>
      <div style="font-size: 12px; font-weight: bold;">INSTAGRAM</div>
    </div>
  </a>
  
  <a href="https://t.me/yourusername" style="text-decoration: none;">
    <div style="
      width: 120px;
      height: 120px;
      background: linear-gradient(135deg, #2CA5E0, #1E88E5);
      border-radius: 50%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: white;
      transition: all 0.3s ease;
      box-shadow: 0 10px 30px rgba(44, 165, 224, 0.3);
      cursor: pointer;
    " onmouseover="this.style.transform='scale(1.1) rotateY(15deg)'; this.style.boxShadow='0 20px 40px rgba(44, 165, 224, 0.6)'" onmouseout="this.style.transform='scale(1) rotateY(0deg)'; this.style.boxShadow='0 10px 30px rgba(44, 165, 224, 0.3)'">
      <div style="font-size: 40px;">✈️</div>
      <div style="font-size: 12px; font-weight: bold;">TELEGRAM</div>
    </div>
  </a>
</div>
```

</div>

---

## 💭 **Matrix Code Rain**

<div align="center">

### 🔢 **Digital Rain Effect** 🔢

```html
<div style="width: 100%; height: 250px; background: #000; border-radius: 15px; position: relative; overflow: hidden; margin: 30px 0;">
  <canvas id="matrixCanvas" width="800" height="250" style="width: 100%; height: 100%; border-radius: 15px;"></canvas>
  <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); color: #00ff00; font-family: 'Courier New'; font-size: 24px; text-shadow: 0 0 20px #00ff00; z-index: 10; text-align: center;">
    <div>WELCOME TO THE MATRIX</div>
    <div style="font-size: 16px; margin-top: 10px; opacity: 0.8;">~ YUM YUM's Code Realm ~</div>
  </div>
</div>

<script>
const matrixCanvas = document.getElementById('matrixCanvas');
const mCtx = matrixCanvas.getContext('2d');

const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
const charArray = chars.split('');
const fontSize = 14;
const columns = matrixCanvas.width / fontSize;
const drops = Array(Math.floor(columns)).fill(1);

function drawMatrix() {
  mCtx.fillStyle = 'rgba(0, 0, 0, 0.05)';
  mCtx.fillRect(0, 0, matrixCanvas.width, matrixCanvas.height);
  
  mCtx.fillStyle = '#00ff00';
  mCtx.font = `${fontSize}px courier`;
  
  for (let i = 0; i < drops.length; i++) {
    const text = charArray[Math.floor(Math.random() * charArray.length)];
    mCtx.fillText(text, i * fontSize, drops[i] * fontSize);
    
    if (drops[i] * fontSize > matrixCanvas.height && Math.random() > 0.975) {
      drops[i] = 0;
    }
    drops[i]++;
  }
}

setInterval(drawMatrix, 50);
</script>
```

</div>

---

## 📊 **Epic Stats Dashboard**

<div align="center">
  
### 🌟 **Real-time Analytics** 🌟

![Profile Views](https://komarev.com/ghpvc/?username=fathuur7&color=brightgreen&style=for-the-badge&label=PROFILE+VIEWS)

```html
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; max-width: 800px; margin: 30px auto; padding: 20px;">
  <div style="background: linear-gradient(135deg, #667eea, #764ba2); padding: 20px; border-radius: 15px; text-align: center; color: white; box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);">
    <h3 style="margin: 0; font-size: 2em;">⚡</h3>
    <h2 style="margin: 10px 0; font-size: 2.5em;">99%</h2>
    <p style="margin: 0; opacity: 0.9;">Code Quality</p>
  </div>
  
  <div style="background: linear-gradient(135deg, #f093fb, #f5576c); padding: 20px; border-radius: 15px; text-align: center; color: white; box-shadow: 0 10px 30px rgba(240, 147, 251, 0.3);">
    <h3 style="margin: 0; font-size: 2em;">🚀</h3>
    <h2 style="margin: 10px 0; font-size: 2.5em;">24/7</h2>
    <p style="margin: 0; opacity: 0.9;">Coding Mode</p>
  </div>
  
  <div style="background: linear-gradient(135deg, #4facfe, #00f2fe); padding: 20px; border-radius: 15px; text-align: center; color: white; box-shadow: 0 10px 30px rgba(79, 172, 254, 0.3);">
    <h3 style="margin: 0; font-size: 2em;">🎮</h3>
    <h2 style="margin: 10px 0; font-size: 2.5em;">∞</h2>
    <p style="margin: 0; opacity: 0.9;">Fun Level</p>
  </div>
  
  <div style="background: linear-gradient(135deg, #43e97b, #38f9d7); padding: 20px; border-radius: 15px; text-align: center; color: white; box-shadow: 0 10px 30px rgba(67, 233, 123, 0.3);">
    <h3 style="margin: 0; font-size: 2em;">🌟</h3>
    <h2 style="margin: 10px 0; font-size: 2.5em;">MAX</h2>
    <p style="margin: 0; opacity: 0.9;">Creativity</p>
  </div>
</div>
```

</div>

---

<div align="center">
  
### 🎯 **"The best way to predict the future is to create it."** – Alan Kay

### ⭐ **Thanks for visiting my 3D coding universe!** ⭐

```html
<div style="margin: 50px 0; text-align: center;">
  <div style="
    display: inline-block;
    padding: 20px 40px;
    background: linear-gradient(45deg, #ff006e, #8338ec, #3a86ff);
    border-radius: 50px;
    color: white;
    font-family: 'Orbitron', monospace;
    font-size: 18px;
    font-weight: bold;
    text-shadow: 0 0 10px rgba(255,255,255,0.5);
    box-shadow: 0 10px 30px rgba(255, 0, 110, 0.3);
    animation: final-glow 3s ease-in-out infinite alternate;
  ">
    🚀 Ready to build the future together? 🚀
  </div>
</div>

<style>
@keyframes final-glow {
  0% { 
    box-shadow: 0 10px 30px rgba(255, 0, 110, 0.3);
    transform: scale(1);
  }
  100% { 
    box-shadow: 0 20px 60px rgba(255, 0, 110, 0.6);
    transform: scale(1.05);
  }
}
</style>
```

<img src="https://raw.githubusercontent.com/fathuur7/fathuur7/output/snake.svg" alt="Snake animation" />

</div>

---

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=120&section=footer&text=See%20You%20in%20the%20Metaverse!&fontSize=24&fontColor=fff&animation=twinkling"/>
</div>
