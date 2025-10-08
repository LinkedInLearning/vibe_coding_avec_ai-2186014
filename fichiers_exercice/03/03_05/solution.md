# Projet : Application Palette de Couleurs en React

## Solution:

un exemple de code fonctionnel avec génération aléatoire, affichage des couleurs, copie au clic et palette responsive

```jsx

import { useState } from "react";

export default function ColorPalette() {
  const [colors, setColors] = useState([]);

  // Fonction pour générer une couleur HEX aléatoire
  const generateColor = () => {
    const hex = `#${Math.floor(Math.random() * 0xffffff)
      .toString(16)
      .padStart(6, "0")}`;
    setColors([hex, ...colors]);
  };

  // Fonction pour copier une couleur dans le presse-papiers
  const copyColor = (color) => {
    navigator.clipboard.writeText(color);
    alert(`Couleur ${color} copiée !`);
  };

  // Fonction pour supprimer une couleur de la palette
  const removeColor = (index) => {
    const newColors = colors.filter((_, i) => i !== index);
    setColors(newColors);
  };

  return (
    <div className="p-6 max-w-3xl mx-auto">
      <h1 className="text-3xl font-bold mb-4 text-center">🎨 Palette de Couleurs</h1>

      <div className="text-center mb-6">
        <button
          onClick={generateColor}
          className="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600 transition"
        >
          Générer une couleur
        </button>
      </div>

      <div className="grid grid-cols-2 sm:grid-cols-4 md:grid-cols-6 gap-4">
        {colors.map((color, index) => (
          <div
            key={index}
            style={{ backgroundColor: color }}
            className="relative h-24 rounded-lg cursor-pointer flex items-center justify-center text-white font-bold shadow-md hover:scale-105 transition"
            onClick={() => copyColor(color)}
          >
            <span className="absolute bottom-1 text-sm">{color}</span>
            <button
              onClick={(e) => {
                e.stopPropagation(); // Empêche la copie au clic sur le bouton
                removeColor(index);
              }}
              className="absolute top-1 right-1 bg-white text-black px-1 rounded text-xs hover:bg-gray-200"
            >
              ✕
            </button>
          </div>
        ))}
      </div>
    </div>
  );
}


```