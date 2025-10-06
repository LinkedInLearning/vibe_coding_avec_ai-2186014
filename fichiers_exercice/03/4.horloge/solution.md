# Projet : Application Palette de Couleurs en React

## Solution:

un exemple de code fonctionnel avec génération aléatoire, affichage des couleurs, copie au clic et palette responsive

```bash
horloge/
├── index.html
├── package.json
├── vite.config.js
├── src/
│   ├── App.jsx
│   ├── App.css
│   ├── main.jsx
└── public/
    
```

1. ** ⏱️ Phase 1 : Gestion de l’horloge**
Ouvrir `App.jsx` et remplacer le contenu initial par le squelette de l’application :

App.jsx: 

🎯 Objectif : Afficher une horloge fonctionnelle qui met à jour l’heure chaque seconde et affiche aussi la date du jour.


```jsx
import { useState, useEffect } from "react";
import "./App.css";

export default function App() {
  const [time, setTime] = useState(new Date());
  const [is24h, setIs24h] = useState(true);

  useEffect(() => {
    const interval = setInterval(() => {
      setTime(new Date());
    }, 1000);
    return () => clearInterval(interval);
  }, []);

  const formatTime = () => {
    let hours = time.getHours();
    let minutes = time.getMinutes();
    let seconds = time.getSeconds();

    if (!is24h) {
      const ampm = hours >= 12 ? "PM" : "AM";
      hours = hours % 12 || 12;
      return `${pad(hours)}:${pad(minutes)}:${pad(seconds)} ${ampm}`;
    }
    return `${pad(hours)}:${pad(minutes)}:${pad(seconds)}`;
  };

  const pad = (n) => String(n).padStart(2, "0");

  const formatDate = () => {
    const options = { weekday: "long", year: "numeric", month: "long", day: "numeric" };
    return time.toLocaleDateString("fr-FR", options);
  };

  return (
    <div className="container">
      <h1>🕒 Horloge</h1>
      <div className="clock">{formatTime()}</div>
      <div className="date">{formatDate()}</div>
      <button onClick={() => setIs24h(!is24h)}>
        Basculer en format {is24h ? "12h" : "24h"}
      </button>
    </div>
  );
}

export default function App() {
  return (
    <div>
      <h1>Horloge</h1>
    </div>
  );
}
```

2. **🎨 Phase 3 : Style & design (App.css)**

App.css

```css

body {
  margin: 0;
  background: #f9fafb;
  color: #1f2937;
  font-family: "Inter", system-ui, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

.container {
  text-align: center;
  padding: 2rem;
  background: white;
  border-radius: 16px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #2563eb;
  margin-bottom: 1rem;
}

.clock {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.date {
  font-size: 1.1rem;
  color: #4b5563;
  margin-bottom: 1.5rem;
}

button {
  background: #2563eb;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1rem;
  transition: background 0.3s ease;
}

button:hover {
  background: #1d4ed8;
}


```