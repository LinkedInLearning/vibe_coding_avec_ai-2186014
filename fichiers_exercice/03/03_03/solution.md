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
import React, { useState, useEffect } from 'react';


function Clock() {
  // State pour stocker date et heure actuelles
  const [dateTime, setDateTime] = useState(getCurrentDateTime());

  // Fonction pour récupérer la date et l'heure actuelles formatées
  function getCurrentDateTime() {
    const now = new Date();

    // Heure formatée HH:MM:SS
    const hours = String(now.getHours()).padStart(2, "0");
    const minutes = String(now.getMinutes()).padStart(2, "0");
    const seconds = String(now.getSeconds()).padStart(2, "0");

    // Liste des jours et mois en français
    const daysOfWeek = ["Dimanche", "Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi"];
    const months = [
      "Janvier", "Février", "Mars", "Avril", "Mai", "Juin",
      "Juillet", "Août", "Septembre", "Octobre", "Novembre", "Décembre"
    ];

    const dayName = daysOfWeek[now.getDay()]; // nom du jour
    const day = now.getDate();               // jour du mois
    const monthName = months[now.getMonth()]; // nom du mois
    const year = now.getFullYear();          // année

    return {
      time: `${hours}:${minutes}:${seconds}`,
      date: `${dayName} ${day} ${monthName} ${year}`,
    };
  }

  // useEffect pour mettre à jour date et heure chaque seconde
  useEffect(() => {
    const interval = setInterval(() => {
      setDateTime(getCurrentDateTime());
    }, 1000);

    // Nettoyage de l'intervalle à la destruction du composant
    return () => clearInterval(interval);
  }, []);

  return (
    <div style={{ textAlign: "center", marginTop: "50px" }}>
      <h1>Horloge</h1>
      <p style={{ fontSize: "2rem", fontFamily: "monospace" }}>{dateTime.time}</p>
      <p style={{ fontSize: "1.5rem" }}>{dateTime.date}</p>
    </div>
  );
}

export default App;


export function App(props) {
  return <Clock />;
}

// Log to console
console.log('Hello console');

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