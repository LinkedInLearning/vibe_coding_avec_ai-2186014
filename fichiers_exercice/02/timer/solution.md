# Solution — Projet : Timer en JavaScript Pur

Ce document présente une **solution complète en JavaScript pur** (HTML + CSS + JS) pour créer un **compte à rebours simple et fonctionnel**, basée sur les spécifications du projet.

---

## 🧱 Structure du projet

```bash
timer-js/
├── index.html
├── style.css
└── script.js
```

---

## 🧩 index.html

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Timer</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="container">
    <h1>⏱️ Timer</h1>

    <div class="inputs">
      <input type="number" id="minutes" placeholder="Minutes" min="0" />
      <input type="number" id="seconds" placeholder="Secondes" min="0" max="59" />
    </div>

    <div id="display">00:00</div>

    <div class="buttons">
      <button id="start">Démarrer</button>
      <button id="pause">Pause</button>
      <button id="reset">Réinitialiser</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>


## 🎨 style.css

```css

body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  background: #f4f4f9;
}

.container {
  text-align: center;
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

h1 {
  margin-bottom: 20px;
  color: #333;
}

.inputs {
  margin-bottom: 15px;
}

.inputs input {
  width: 80px;
  padding: 5px;
  margin: 0 5px;
  text-align: center;
  border-radius: 5px;
  border: 1px solid #ccc;
}

#display {
  font-size: 3em;
  margin: 20px 0;
  font-weight: bold;
  color: #28a745; /* vert par défaut */
}

.buttons button {
  margin: 5px;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1em;
  color: white;
  background-color: #007bff;
  transition: background 0.2s;
}

.buttons button:hover {
  background-color: #0056b3;
}

#pause.active {
  background-color: #ff9800; /* orange en pause */
}

.finished {
  color: #d32f2f !important; /* rouge quand terminé */
}

```


## ⚙️ script.js

```js

let timerInterval;
let totalSeconds = 0;
let remainingSeconds = 0;
let isRunning = false;

const display = document.getElementById('display');
const startBtn = document.getElementById('start');
const pauseBtn = document.getElementById('pause');
const resetBtn = document.getElementById('reset');

startBtn.addEventListener('click', startTimer);
pauseBtn.addEventListener('click', togglePause);
resetBtn.addEventListener('click', resetTimer);

function startTimer() {
  const minutes = parseInt(document.getElementById('minutes').value) || 0;
  const seconds = parseInt(document.getElementById('seconds').value) || 0;
  totalSeconds = minutes * 60 + seconds;
  if (totalSeconds <= 0) return;

  remainingSeconds = totalSeconds;
  isRunning = true;
  pauseBtn.textContent = 'Pause';
  updateDisplay();
  display.style.color = '#28a745'; // vert

  timerInterval = setInterval(() => {
    if (remainingSeconds > 0) {
      remainingSeconds--;
      updateDisplay();
    } else {
      clearInterval(timerInterval);
      isRunning = false;
      display.classList.add('finished');
      display.style.color = '#d32f2f'; // rouge
      alert('⏰ Temps écoulé !');
    }
  }, 1000);
}

function togglePause() {
  if (!isRunning && remainingSeconds > 0) {
    // Reprendre
    isRunning = true;
    pauseBtn.textContent = 'Pause';
    display.style.color = '#28a745';
    timerInterval = setInterval(() => {
      if (remainingSeconds > 0) {
        remainingSeconds--;
        updateDisplay();
      } else {
        clearInterval(timerInterval);
        isRunning = false;
        display.classList.add('finished');
        display.style.color = '#d32f2f';
        alert('⏰ Temps écoulé !');
      }
    }, 1000);
  } else if (isRunning) {
    // Pause
    clearInterval(timerInterval);
    isRunning = false;
    pauseBtn.textContent = 'Reprendre';
    display.style.color = '#ff9800'; // orange
  }
}

function resetTimer() {
  clearInterval(timerInterval);
  isRunning = false;
  remainingSeconds = 0;
  totalSeconds = 0;
  document.getElementById('minutes').value = '';
  document.getElementById('seconds').value = '';
  updateDisplay();
  display.style.color = '#28a745';
  pauseBtn.textContent = 'Pause';
}

function updateDisplay() {
  const min = Math.floor(remainingSeconds / 60)
    .toString()
    .padStart(2, '0');
  const sec = (remainingSeconds % 60).toString().padStart(2, '0');
  display.textContent = `${min}:${sec}`;
}

```