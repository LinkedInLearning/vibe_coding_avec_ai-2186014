## 🎮 Projet : Jeu 2D Brick Breaker 

## Solution:

L’interface de jeu est maintenant colorée :

* Palette rouge, balle jaune, et briques en dégradés de couleurs.

* Le score et les vies s’affichent en blanc en haut à droite.

* Le message “GAME OVER” apparaît au centre avec une police plus grande après trois échecs.
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
      --brick1:linear-gradient(90deg,#ef4444,#f97316);
      --brick2:linear-gradient(90deg,#f59e0b,#84cc16);
      --brick3:linear-gradient(90deg,#10b981,#3b82f6);
      --paddle:#dc2626; /* rouge */
      --ball:#fde047; /* jaune */
    }
    html,body{height:100%;margin:0;font-family:Inter,system-ui,Arial;background:linear-gradient(180deg,var(--bg),#071024);color:#fff;overflow:hidden}
    .wrap{display:flex;align-items:center;justify-content:center;height:100%;padding:20px;box-sizing:border-box}
    .game-container{position:relative;width:900px;max-width:96vw;border-radius:12px;padding:12px;box-shadow:0 8px 30px rgba(2,6,23,0.7);background:linear-gradient(180deg,rgba(255,255,255,0.05),rgba(0,0,0,0.3));}
    header{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px}
    header h1{font-size:16px;margin:0}
    .scoreboard{position:absolute;top:15px;right:25px;font-size:16px;color:#fff;font-weight:600;text-shadow:0 0 5px rgba(255,255,255,0.4)}
    canvas{display:block;background:linear-gradient(180deg,#071029 0%, #07162a 100%);border-radius:8px;width:100%;height:600px}
    #game-over{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);color:white;font-size:28px;font-weight:bold;text-shadow:0 0 15px rgba(255,255,255,0.6);display:none;}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="game-container">
      <div class="scoreboard">
        <span id="score">Score: 0</span>&nbsp;&nbsp;|&nbsp;&nbsp;<span id="lives">Vies: 3</span>
      </div>
      <canvas id="game" width="900" height="600"></canvas>
      <div id="game-over">GAME OVER</div>
    </div>
  </div>

  <script>
  (function(){
    const canvas = document.getElementById('game');
    const ctx = canvas.getContext('2d');
    const W = canvas.width;
    const H = canvas.height;

    let running = false;
    let score = 0;
    let lives = 3;

    const paddle = { w:120, h:14, x:(W-120)/2, y:H-40, speed:8 };
    const ball = { r:8, x:W/2, y:H-60, vx:4, vy:-4 };

    const brick = {cols:10, rows:3, w:72, h:24, padding:12, offsetTop:40, offsetLeft:22};
    const bricks = [];

    function createBricks(){
      bricks.length=0;
      for(let r=0;r<brick.rows;r++){
        for(let c=0;c<brick.cols;c++){
          const x = brick.offsetLeft + c*(brick.w+brick.padding);
          const y = brick.offsetTop + r*(brick.h+brick.padding);
          bricks.push({x,y,w:brick.w,h:brick.h,alive:true,row:r});
        }
      }
    }

    createBricks();

    const keys={left:false,right:false};
    window.addEventListener('keydown',e=>{
      if(e.code==='ArrowLeft')keys.left=true;
      if(e.code==='ArrowRight')keys.right=true;
      if(e.code==='Space'){
        if(!running){
          if(lives>0)start();
          else reset();
        }
      }
    });
    window.addEventListener('keyup',e=>{
      if(e.code==='ArrowLeft')keys.left=false;
      if(e.code==='ArrowRight')keys.right=false;
    });

    function start(){
      running=true;
      document.getElementById('game-over').style.display='none';
      loop();
    }

    function reset(){
      score=0; lives=3; running=false;
      document.getElementById('score').textContent='Score: '+score;
      document.getElementById('lives').textContent='Vies: '+lives;
      document.getElementById('game-over').style.display='none';
      createBricks();
      paddle.x=(W-paddle.w)/2;
      ball.x=W/2; ball.y=paddle.y-20; ball.vx=4; ball.vy=-4;
      draw();
    }

    function loseLife(){
      lives--;
      score = Math.max(0, score - 1);
      document.getElementById('score').textContent='Score: '+score;
      document.getElementById('lives').textContent='Vies: '+lives;
      if(lives<=0){
        running=false;
        document.getElementById('game-over').style.display='block';
      }else{
        running=false;
        ball.x=W/2; ball.y=paddle.y-20; ball.vx=4; ball.vy=-4;
      }
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
      ctx.clearRect(0,0,W,H);

      // Briques avec dégradé par rangée
      for(const b of bricks){
        if(!b.alive) continue;
        let grad = ctx.createLinearGradient(b.x,b.y,b.x+b.w,b.y);
        if(b.row===0){ grad.addColorStop(0,'#ef4444'); grad.addColorStop(1,'#f97316'); }
        else if(b.row===1){ grad.addColorStop(0,'#f59e0b'); grad.addColorStop(1,'#84cc16'); }
        else { grad.addColorStop(0,'#10b981'); grad.addColorStop(1,'#3b82f6'); }
        ctx.fillStyle=grad;
        drawRoundedRect(b.x,b.y,b.w,b.h,5);
      }

      // Palette rouge
      ctx.fillStyle='var(--paddle)';
      drawRoundedRect(paddle.x,paddle.y,paddle.w,paddle.h,6);

      // Balle jaune
      ctx.beginPath();
      ctx.fillStyle='var(--ball)';
      ctx.arc(ball.x,ball.y,ball.r,0,Math.PI*2);
      ctx.fill();
    }

    function update(){
      if(keys.left)paddle.x-=paddle.speed;
      if(keys.right)paddle.x+=paddle.speed;
      paddle.x=Math.max(0,Math.min(W-paddle.w,paddle.x));

      if(!running)return;

      ball.x+=ball.vx;
      ball.y+=ball.vy;

      if(ball.x-ball.r<0||ball.x+ball.r>W)ball.vx*=-1;
      if(ball.y-ball.r<0)ball.vy*=-1;

      // collision palette
      if(ball.y+ball.r>=paddle.y&&ball.x>paddle.x&&ball.x<paddle.x+paddle.w){
        ball.vy*=-1;
        ball.y=paddle.y-ball.r;
      }

      // collision briques
      for(const b of bricks){
        if(!b.alive)continue;
        if(ball.x> b.x && ball.x < b.x+b.w && ball.y> b.y && ball.y < b.y+b.h){
          b.alive=false;
          ball.vy*=-1;
          score++;
          document.getElementById('score').textContent='Score: '+score;
          break;
        }
      }

      if(ball.y-ball.r>H){ loseLife(); }
    }

    function loop(){
      update();
      draw();
      if(running)requestAnimationFrame(loop);
    }

    draw();
  })();
  </script>
</body>
</html>


```