# ⚖️ Projet : Convertisseur d’Unités (HTML + CSS + JavaScript)

## 🎯 Objectif
Créer une application web simple qui permet de **convertir des unités de mesure** (longueur, poids, température, etc.) avec une interface claire et réactive.

---

## 🚀 Fonctionnalités principales
- Sélectionner un **type de conversion** (longueur, poids, température)
- Entrer une **valeur à convertir**
- Choisir **l’unité source** et **l’unité cible**
- Afficher le **résultat instantanément**
- Interface responsive et lisible

---

## 💡 Exemples de conversions
| Type         | De → Vers                   |
|---------------|-----------------------------|
| Longueur      | m ↔ cm ↔ km ↔ pouces ↔ pieds |
| Poids         | kg ↔ g ↔ lb ↔ oz            |
| Température   | °C ↔ °F ↔ K                 |

---

## 🌱 Philosophie de développement
- Simplicité d’usage : **une page, tout-en-un**
- Conversion en temps réel (sans rechargement)
- Design minimaliste, professionnel
- Code clair et commenté
- Possibilité d’extension future (autres unités)

---

## 🛠️ Étapes de développement

### Phase 1 : Structure de base
- Créer un fichier `index.html`  
- Ajouter les éléments :
  - Champ de saisie de la valeur  
  - Deux menus déroulants (unité source / unité cible)  
  - Sélecteur du type d’unité (longueur, poids, température)  
  - Zone d’affichage du résultat  

### Phase 2 : Logique de conversion
- Utiliser JavaScript pour :
  - Récupérer les valeurs des champs
  - Appliquer la formule de conversion appropriée
  - Afficher automatiquement le résultat à chaque saisie  

### Phase 3 : Design & ergonomie
- Centrer les éléments avec **Flexbox**
- Appliquer un **thème clair et moderne**
- Ajouter des effets de hover sur les boutons et menus

---

## 💬 Prompts & consignes

### Prompt 1 :
*Crée un convertisseur d’unités en HTML + CSS + JS qui permet de convertir des longueurs (m, cm, km, pouces, pieds). Le résultat doit s’afficher instantanément lorsqu’on modifie la valeur ou l’unité.*

### Prompt 2 :
*Compléter le projet pour inclure la température (°C ↔ °F ↔ K) et le poids (kg ↔ lb ↔ oz). ajouter un menu déroulant pour choisir le type de conversion.*

---

## ✅ Résultat attendu
Une page web **intuitive et réactive**, permettant :
- De choisir un type d’unité
- De saisir une valeur
- D’obtenir instantanément la conversion
- D’utiliser une interface agréable sur mobile et desktop

---

## 🧩 Structure du projet

```bash
convertisseur-unite/
├── index.html
├── style.css
└── script.js

```
---

## 💡 Bonus possibles

- 🌓 Ajouter un mode sombre
- 🧮 Historique des conversions récentes
- 🔄 Bouton pour inverser les unités
- 🌐 Conversion automatique selon la langue du navigateur

