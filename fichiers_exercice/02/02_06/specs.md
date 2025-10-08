# Projet : Application Compte à Rebours (Timer)

## 🎯 Objectif
Créer une application **Timer** en **JavaScript pur (sans framework)** 
Projet simple dans une version minimale, idéal pour débuter avec JavaScript et le DOM.
Les fonctionnalités seront de pouvoir : 
- saisir un temps de départ, 
- lancer le compte à rebours avec un click, 
- mettre en pause, 
- réinitialiser et reprendre.
---
## ⚙️ Outils pour démarrer :
- Installer l'extension de navigateur (Chrome, Firefox ou Safari) [Markdown Viewer](https://chromewebstore.google.com/detail/markdown-viewer/ckkdlimhmcjmikdlpkmbgfkaikojcbjk?hl=en)
- Ouvrir le *Code Playground* [ici](https://platform.openai.com/chat)
- Pour tester le code en ligne: 
 * *JSfiddle* [jsfiddle.net](https://jsfiddle.net/) pour tester le code en ligne
 * *CodePen* [https://codepen.io](https://codepen.io/) pour tester le code en ligne
 * *Playcode.io* [https://playcode.io/react](https://playcode.io/react)

--- 

## 🌱 Philosophie de développement
- Commencer simple (**MVP first**), avec :  
- une interface minimaliste et claire 
- les fonctions principales (start, pause, reset) 
---

## 🚀 Fonctionnalités principales
- Définir un temps de départ (minutes/secondes)  
- Lancer le compte à rebours  
- Afficher le temps restant au format `MM:SS`
- Mettre en pause et reprendre le timer  
- Réinitialiser le timer  
- (Bonus) Sonnerie ou alerte quand le timer atteint zéro  
- (Bonus) Sauvegarde du dernier temps choisi dans `localStorage`  
- (Bonus) Animation visuelle à la fin du timer  

*tester manuellement chaque étape avant de passer à la suivante et ajouter des  progressivement avec l'assistance de l'IA*

---
## ⏱️ Phase 1 : MVP (les fonctionnalités principales)
- 💬 Prompt : *créer un timer ultra-minimaliste en JavaScript pur (sans framework) en 30 lignes de code, avec les fonctionalités pour : afficher le temps restant sous format `MM:SS`, démarrer, mettre en pause et se réinitialiser, déclencher une alerte à la fin.
Fournir un seul fichier HTML complet, avec le JavaScript inclus dans une balise `<script>`*

---

## ⏱️ Phase 2 : Gestion du Timer
Champs de saisie pour minutes et secondes  
- 💬 Prompt : *ajouter un champs texte pour saisir le temps à écouler au format `MM:SS`*

---

## 🎨 Phase 3 : Style & Couleurs
- Afficher le temps en grand et centré sur l'écran 
- Style : Changer la couleur du texte selon l’état :  
  - 🟢 Vert = en cours  
  - 🟠 Orange = en pause  
  - 🔴 Rouge = terminé  

### Prompts & Consignes
- 💬 Prompt : *ajouter du CSS pour centrer le timer et afficher le texte en grand.*  
- 💬 Prompt : *changer dynamiquement la couleur du texte avec `element.style.color` selon l’état du timer. (🟢 vert = en cours, 🟠 orange = en pause, 🔴 rouge = terminé)*  

---

## 🧪 Phase 4 : Tests utilisateur
- Vérifier le démarrage et la décrémentation  
- Vérifier la pause  
- Vérifier la réinitialisation  


## ✅ Résultat attendu
Une application **Timer** en JavaScript pur :  
- affichage simple et coloré (optionnel) 
- gèrer les fonctions essentielles (démarrer, pause, réinitialiser)  
- Bonus : ajouter des alertes visuelles ou audio, des animations, sauvegarde locale `localStorage` 

---

## 🌟 Bonus
- 💬 Prompt : *ajouter de l'audio ou une alerte avec `alert()` ou `Audio()` quand le timer arrive à zéro.*  
- 💬 Prompt: *utiliser `localStorage` pour sauvegarder les dernières valeurs saisies*  
💬 Prompt : *ajouter une animation CSS (changement de couleur ou vibration) à la fin du décompte.*  

---

## 📚 Ressources : apprendre JavaScript (pour les débutants)

- **MDN Web Docs (Mozilla)** — [https://developer.mozilla.org/fr/docs/Web/JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript)  
- **JavaScript.info** — [https://fr.javascript.info](https://fr.javascript.info)  
- **FreeCodeCamp** — [https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures)  
- **W3Schools** — [https://www.w3schools.com/js/](https://www.w3schools.com/js/)  
- **OpenClassrooms - Apprenez à coder avec JavaScript** — [https://openclassrooms.com/fr/courses/6175841-apprenez-a-coder-avec-javascript](https://openclassrooms.com/f)
