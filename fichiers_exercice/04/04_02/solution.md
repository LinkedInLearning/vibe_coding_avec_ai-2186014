## 🎮 Projet : Jeu 2D Brick Breaker 

## Solution:

Interface du jeu de brique avec contrôles rapides : 
* les flèches pour naviguer : gauche/droite ou la souris 
* la touche Espace pour déplacer la palette, pour démarreret recommencer.
---

```html
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Jeu : Balle, Palette et Briques</title>
  <style>
    :root{
      --bg:#0f1724;
      --accent:#60a5fa;
      --brick1:#ef4444; /* rouge */
      --brick2:#f59e0b; /* orange */
      --brick3:#10b981; /* vert */
      --paddle:#e2e8f0;
      --ball:#fff;
    }
    html,body{height:100%;margin:0;font-family:Inter,system-ui,Arial;background:linear-gradient(180deg,var(--bg),#071024);color:#d1d5db}
    .wrap{display:flex;align-items:center;justify-content:center;height:100%;padding:20px;box-sizing:border-box}
    .game-container{width:900px;max-width:96vw;background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(0,0,0,0.15));border-radius:12px;padding:12px;box-shadow:0 8px 30px rgba(2,6,23,0.7);}
    header{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px}
    header h1{font-size:16px;margin:0}
    .controls{font-size:13px;opacity:0.85}
    canvas{display:block;background:linear-gradient(180deg,#071029 0%, #07162a 100%);border-radius:8px;width:100%;height:600px}
    footer{display:flex;justify-content:space-between;margin-top:8px;font-size:13px;color:#9ca3af}
    .status{font-weight:600}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="game-container">
      <header>
        <h1>Breakout minimal — flèches ou souris pour déplacer la palette</h1>
        <div class="controls">Espace: démarrer / recommencer</div>
      </header>

      <canvas id="game" width="900" height="600" aria-label="Zone de jeu"></canvas>

      <footer>
        <div class="status" id="status">Prêt</div>
        <div id="score">Score: 0</div>
      </footer>
    </div>
  </div>

  <script>
  (function(){
    const canvas = document.getElementById('game');
    const ctx = canvas.getContext('2d');
    const W = canvas.width;
    const H = canvas.height;

    // Game state
    let running = false;
    let score = 0;

    // Paddle
    const paddle = {
      w: 120,
      h: 14,
      x: (W - 120) / 2,
      y: H - 40,
      speed: 8,
      vx: 0
    };

    // Ball
    const ball = {
      r: 8,
      x: W/2,
      y: paddle.y - 8 - 1,
      vx: 4 * (Math.random() > 0.5 ? 1 : -1),
      vy: -4
    };

    // Bricks
    const brick = {cols: 10, rows: 3, w: 72, h: 24, padding: 12, offsetTop: 40, offsetLeft: 22};
    const bricks = [];

    function createBricks(){
      bricks.length = 0;
      for(let r=0;r<brick.rows;r++){
        for(let c=0;c<brick.cols;c++){
          const x = brick.offsetLeft + c*(brick.w + brick.padding);
          const y = brick.offsetTop + r*(brick.h + brick.padding);
          bricks.push({x,y,w:brick.w,h:brick.h,alive:true,row:r,col:c});
        }
      }
    }

    createBricks();

    // Input
    const keys = {left:false,right:false};
    window.addEventListener('keydown',e=>{
      if(e.code === 'ArrowLeft') keys.left = true;
      if(e.code === 'ArrowRight') keys.right = true;
      if(e.code === 'Space'){
        if(!running) start();
        else reset();
      }
    });
    window.addEventListener('keyup',e=>{
      if(e.code === 'ArrowLeft') keys.left = false;
      if(e.code === 'ArrowRight') keys.right = false;
    });

    // Mouse: move paddle
    canvas.addEventListener('mousemove',e=>{
      const rect = canvas.getBoundingClientRect();
      const mx = (e.clientX - rect.left) * (canvas.width / rect.width);
      paddle.x = Math.max(0, Math.min(W - paddle.w, mx - paddle.w/2));
    });

    canvas.addEventListener('click',()=>{
      if(!running) start();
    });

    function start(){
      running = true;
      document.getElementById('status').textContent = 'En jeu';
      // if ball stuck on paddle, give it some random vx
      if(Math.abs(ball.vx) < 0.1){ ball.vx = 4 * (Math.random() > 0.5 ? 1 : -1); ball.vy = -4 }
      loop();
    }

    function reset(){
      running = false;
      score = 0;
      document.getElementById('score').textContent = 'Score: 0';
      document.getElementById('status').textContent = 'Prêt';
      paddle.x = (W - paddle.w)/2;
      ball.x = W/2;
      ball.y = paddle.y - ball.r - 1;
      ball.vx = 4 * (Math.random() > 0.5 ? 1 : -1);
      ball.vy = -4;
      createBricks();
      draw();
    }

    function drawRoundedRect(x,y,w,h,r){
      ctx.beginPath();
      ctx.moveTo(x+r,y);
      ctx.arcTo(x+w,y,x+w,y+h,r);
      ctx.arcTo(x+w,y+h,x,y+h,r);
      ctx.arcTo(x,y+h,x,y,r);
      ctx.arcTo(x,y,x+w,y,r);
      ctx.closePath();
      ctx.fill();
    }

    function draw(){
      // clear
      ctx.clearRect(0,0,W,H);

      // background subtle grid
      ctx.save();
      ctx.globalAlpha = 0.06;
      ctx.fillStyle = '#9ca3af';
      for(let gx=0;gx<W;gx+=40){ ctx.fillRect(gx,0,1,H) }
      for(let gy=0;gy<H;gy+=40){ ctx.fillRect(0,gy,W,1) }
      ctx.restore();

      // bricks
      for(const b of bricks){
        if(!b.alive) continue;
        let color = b.row === 0 ? 'var(--brick1)' : (b.row === 1 ? 'var(--brick2)' : 'var(--brick3)');
        ctx.fillStyle = getComputedStyle(document.documentElement).getPropertyValue(color) || (b.row===0? '#ef4444': b.row===1? '#f59e0b':'#10b981');
        ctx.save();
        drawRoundedRect(b.x, b.y, b.w, b.h, 6);
        ctx.restore();
        ctx.strokeStyle = 'rgba(255,255,255,0.06)';
        ctx.strokeRect(b.x, b.y, b.w, b.h);
      }

      // paddle
      ctx.fillStyle = 'var(--paddle)';
      drawRoundedRect(paddle.x, paddle.y, paddle.w, paddle.h, 6);

      // ball
      ctx.beginPath();
      ctx.fillStyle = 'var(--ball)';
      ctx.arc(ball.x, ball.y, ball.r, 0, Math.PI*2);
      ctx.fill();

      // top UI glow
      ctx.fillStyle = 'rgba(96,165,250,0.035)';
      ctx.fillRect(0,0,W,40);

    }

    function update(){
      // move paddle from keys
      if(keys.left) paddle.x -= paddle.speed;
      if(keys.right) paddle.x += paddle.speed;
      paddle.x = Math.max(0, Math.min(W - paddle.w, paddle.x));

      if(!running) return;

      // move ball
      ball.x += ball.vx;
      ball.y += ball.vy;

      // wall collisions
      if(ball.x - ball.r <= 0){ ball.x = ball.r; ball.vx *= -1 }
      if(ball.x + ball.r >= W){ ball.x = W - ball.r; ball.vx *= -1 }
      if(ball.y - ball.r <= 0){ ball.y = ball.r; ball.vy *= -1 }

      // paddle collision
      if(ball.y + ball.r >= paddle.y && ball.y + ball.r <= paddle.y + paddle.h
         && ball.x >= paddle.x && ball.x <= paddle.x + paddle.w){
        // place ball above paddle
        ball.y = paddle.y - ball.r - 0.1;
        // reflect Y
        ball.vy *= -1;
        // change vx depending on where it hits the paddle
        const hitPos = (ball.x - (paddle.x + paddle.w/2)) / (paddle.w/2); // -1..1
        ball.vx += hitPos * 2; // add some horizontal momentum
        // cap speed
        const maxSpeed = 9;
        const minSpeed = 3;
        const speed = Math.sqrt(ball.vx*ball.vx + ball.vy*ball.vy);
        if(speed > maxSpeed){ ball.vx *= maxSpeed / speed; ball.vy *= maxSpeed / speed }
        if(speed < minSpeed){ ball.vx *= minSpeed / speed; ball.vy *= minSpeed / speed }
      }

      // brick collisions (simple AABB check)
      for(const b of bricks){
        if(!b.alive) continue;
        if(ball.x + ball.r > b.x && ball.x - ball.r < b.x + b.w && ball.y + ball.r > b.y && ball.y - ball.r < b.y + b.h){
          // kill brick
          b.alive = false;
          score += 10;
          document.getElementById('score').textContent = 'Score: ' + score;

          // reflect ball depending on side
          // compute penetration depths
          const overlapLeft = (ball.x + ball.r) - b.x;
          const overlapRight = (b.x + b.w) - (ball.x - ball.r);
          const overlapTop = (ball.y + ball.r) - b.y;
          const overlapBottom = (b.y + b.h) - (ball.y - ball.r);
          const minOverlap = Math.min(overlapLeft, overlapRight, overlapTop, overlapBottom);
          if(minOverlap === overlapLeft || minOverlap === overlapRight){
            ball.vx *= -1;
          } else {
            ball.vy *= -1;
          }
          break; // handle one brick per frame
        }
      }

      // lose condition
      if(ball.y - ball.r > H){
        running = false;
        document.getElementById('status').textContent = 'Perdu — appuyez sur Espace pour recommencer';
      }

      // win condition
      const remaining = bricks.filter(b => b.alive).length;
      if(remaining === 0){
        running = false;
        document.getElementById('status').textContent = 'Gagné ! Appuyez sur Espace pour rejouer';
      }
    }

    // main loop
    function loop(){
      update();
      draw();
      if(running) requestAnimationFrame(loop);
    }

    // initial draw
    draw();

    // expose reset to global for debugging
    window.resetGame = reset;

  })();
  </script>
</body>
</html>


```