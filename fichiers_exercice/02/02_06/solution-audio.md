# Solution 
## Projet : Timer en JavaScript Pur avec alerte audio 🔔
Timer avec alerte audio. le code source (HTML + CSS + JS) se trouve sur le même fichier `index.html`.

---

## 🧩 index.html

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Timer avec alerte audio</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #f7f9fb;
      padding-top: 100px;
    }
    #timer {
      font-size: 3em;
      margin-bottom: 20px;
    }
    button {
      padding: 10px 20px;
      font-size: 1em;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>⏱️ Timer avec Alerte Audio</h1>
  <div id="timer">10</div>
  <button id="start">Démarrer</button>

  <audio id="alertSound" src="https://cdn.pixabay.com/audio/2022/03/15/audio_143039.mp3" preload="auto"></audio>

  <script>
    const timerDisplay = document.getElementById('timer');
    const startButton = document.getElementById('start');
    const alertSound = document.getElementById('alertSound');
    let countdown;

    startButton.addEventListener('click', () => {
      let timeLeft = 10; // durée du timer en secondes
      timerDisplay.textContent = timeLeft;
      startButton.disabled = true;

      countdown = setInterval(() => {
        timeLeft--;
        timerDisplay.textContent = timeLeft;

        if (timeLeft <= 0) {
          clearInterval(countdown);
          alertSound.play(); // 🔔 lecture du son d’alerte
          timerDisplay.textContent = "⏰ Temps écoulé !";
          startButton.disabled = false;
        }
      }, 1000);
    });
  </script>
</body>
</html>
```
