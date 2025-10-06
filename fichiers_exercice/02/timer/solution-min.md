# Solution — Projet : Timer en JavaScript Pur

> Version ultra minimale

```html

<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Timer minimal en JavaScript</title>
</head>
<body>
  <h1>⏱️ Timer</h1>
  <p id="display">00:10</p>

  <button onclick="startTimer()">Démarrer</button>
  <button onclick="pauseTimer()">Pause</button>
  <button onclick="resetTimer()">Reset</button>

  <script>
    let duration = 10; // durée en secondes
    let remaining = duration;
    let intervalId = null;

    function updateDisplay() {
      const minutes = String(Math.floor(remaining / 60)).padStart(2, '0');
      const seconds = String(remaining % 60).padStart(2, '0');
      document.getElementById('display').textContent = `${minutes}:${seconds}`;
    }

    function startTimer() {
      if (intervalId) return; // déjà en cours
      intervalId = setInterval(() => {
        remaining--;
        updateDisplay();
        if (remaining <= 0) {
          clearInterval(intervalId);
          intervalId = null;
          alert('⏰ Temps écoulé !');
        }
      }, 1000);
    }

    function pauseTimer() {
      clearInterval(intervalId);
      intervalId = null;
    }

    function resetTimer() {
      pauseTimer();
      remaining = duration;
      updateDisplay();
    }

    updateDisplay(); // initialisation
  </script>
</body>
</html>


```