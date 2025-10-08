## 🎮 Projet : Jeu 2D Brick Breaker (⚛️ React)

## 🎯 Objectif
Créer un **jeu 2D inspiré du jeu classique *Brick Breaker***. 
Le jeu comporte trois rangées de briques positionnées en haut de l’écran, une balle qui rebondit et une palette mobile contrôlée par le joueur. 
**L’objectif** est de faire naviguer la palette mobile pour détruire toutes les briques en renvoyant la balle avec la palette pour accumuler des points. Si la balle tombe et sort du champs de l'écran, les points sont perdus et la partie terminée au bout de 3 échecs.

---

## 🚀 Fonctionnalités principales
- 🎯 Mouvement fluide de la palette (touches ← et → ou souris)  
- 🟡 Balle rebondissante (rebonds sur murs, palette et briques)  
- 🧱 Trois rangées de briques destructibles  
- 💯 Système de score dynamique  
- ❤️ Gestion des vies (3 tentatives par partie)  
- 🔁 Réinitialisation automatique après *Game Over*  
- 💥 (Bonus) Effets sonores à chaque collision  
- ⚡ (Bonus) Difficulté progressive (vitesse de la balle augmentant)  
- 🏆 (Bonus) Affichage du meilleur score (stocké dans `localStorage`)

---


## 🛠️ Phases de développement

### Phase 1 : Configuration du projet
- Créer une app React (Vite recommandé)  
- Mettre en place la structure du composant `Game` avec un canvas ou un conteneur principal  
💬 Prompt : *Créer une application React avec Vite, avec un composant `Game` affichant une balle, une palette, et trois rangées de briques.*

### Phase 2 : Mécaniques de base
- Générer et afficher la balle, la palette et les briques  
- Gérer le déplacement de la palette via les touches du clavier  
- Implémenter les rebonds de la balle sur les murs et la palette  
💬 Prompt : *Ajouter la gestion du clavier pour déplacer la palette.*

### Phase 3 : Collision et score
- Détecter les collisions balle/brique  
- Supprimer la brique au contact et incrémenter le score  
- Réinitialiser la balle en cas de perte  
💬 Prompt :*Gérer les collisions balle/brique et incrémenter un score.*

### Phase 4 : Interface et feedback visuel
- Ajouter le score et le nombre de vies à l’écran  
- Intégrer des effets (couleurs, sons, animations)  
- Ajouter un bouton **Rejouer** ou **Start Game**
💬 Prompts : 
  - *Ajouter un système de vies et un message *Game Over*.*
  - *Styliser le jeu avec CSS (couleurs, effets de rebond, transitions).*

## 🧪 Tests utilisateurs
- Vérifier le mouvement de la palette  
- Vérifier les rebonds et collisions  
- Vérifier la suppression correcte des briques  
- Vérifier le score et le compteur de vies  
- Tester le redémarrage du jeu après *Game Over*   

---

## 🧱 Stack technique
- ⚛️ **React** — Structure et composants  
- 💻 **JavaScript (ES6+)** — Logique du jeu et collisions  
- 🎨 **CSS / Tailwind (optionnel)** — Style et animations  
- 💾 **localStorage** — Sauvegarde du meilleur score  