# ⚖️ Projet : Convertisseur d’Unités (HTML + CSS + JavaScript)

## Solution:
Excellent exercice pour apprendre les interactions temps réel sans frameworks.
Ce projet permet de manipuler :
- Les événements du DOM
- Les structures de données dynamiques
- Les formules de conversion en JavaScript
- Le design réactif avec CSS

---
## 📄 `index.html`
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Convertisseur d'Unités</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>⚖️ Convertisseur d’Unités</h1>

    <label for="type">Type d’unité :</label>
    <select id="type">
      <option value="length">Longueur</option>
      <option value="weight">Poids</option>
      <option value="temperature">Température</option>
    </select>

    <input type="number" id="inputValue" placeholder="Entrez une valeur" />

    <div class="selectors">
      <select id="fromUnit"></select>
      <span>→</span>
      <select id="toUnit"></select>
    </div>

    <div id="result">Résultat : —</div>
  </div>

  <script src="script.js"></script>
</body>
</html>


```

## 🎨 style.css

```css
body {
  margin: 0;
  background: #f9fafb;
  color: #1f2937;
  font-family: "Inter", system-ui, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  background: white;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 300px;
}

h1 {
  color: #2563eb;
  margin-bottom: 1.5rem;
}

select, input {
  width: 100%;
  padding: 0.7rem;
  margin: 0.5rem 0;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  font-size: 1rem;
}

button, select:hover {
  cursor: pointer;
}

#result {
  margin-top: 1rem;
  font-weight: bold;
  font-size: 1.1rem;
  color: #111827;
}

```

## ⚙️ script.js

```js
const typeSelect = document.getElementById("type");
const fromUnit = document.getElementById("fromUnit");
const toUnit = document.getElementById("toUnit");
const inputValue = document.getElementById("inputValue");
const result = document.getElementById("result");

const units = {
  length: ["m", "cm", "km", "pouces", "pieds"],
  weight: ["kg", "g", "lb", "oz"],
  temperature: ["°C", "°F", "K"],
};

typeSelect.addEventListener("change", updateUnits);
inputValue.addEventListener("input", convert);
fromUnit.addEventListener("change", convert);
toUnit.addEventListener("change", convert);

function updateUnits() {
  const type = typeSelect.value;
  fromUnit.innerHTML = "";
  toUnit.innerHTML = "";
  units[type].forEach((u) => {
    fromUnit.add(new Option(u, u));
    toUnit.add(new Option(u, u));
  });
  convert();
}

function convert() {
  const type = typeSelect.value;
  const value = parseFloat(inputValue.value);
  if (isNaN(value)) {
    result.textContent = "Résultat : —";
    return;
  }
  const from = fromUnit.value;
  const to = toUnit.value;
  let output;

  if (type === "length") {
    output = convertLength(value, from, to);
  } else if (type === "weight") {
    output = convertWeight(value, from, to);
  } else {
    output = convertTemperature(value, from, to);
  }

  result.textContent = `Résultat : ${output.toFixed(2)} ${to}`;
}

function convertLength(v, from, to) {
  const rates = { m: 1, cm: 100, km: 0.001, pouces: 39.37, pieds: 3.281 };
  return (v / rates[from]) * rates[to];
}

function convertWeight(v, from, to) {
  const rates = { kg: 1, g: 1000, lb: 2.205, oz: 35.274 };
  return (v / rates[from]) * rates[to];
}

function convertTemperature(v, from, to) {
  if (from === to) return v;
  if (from === "°C" && to === "°F") return (v * 9) / 5 + 32;
  if (from === "°F" && to === "°C") return ((v - 32) * 5) / 9;
  if (from === "°C" && to === "K") return v + 273.15;
  if (from === "K" && to === "°C") return v - 273.15;
  if (from === "°F" && to === "K") return ((v - 32) * 5) / 9 + 273.15;
  if (from === "K" && to === "°F") return ((v - 273.15) * 9) / 5 + 32;
}

updateUnits();

```