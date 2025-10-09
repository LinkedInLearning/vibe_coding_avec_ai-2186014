## 🎮 Projet : Jeu 2D Brick Breaker 

![Texte alternatif](./ChatGPT%20Image%208%20oct.%202025,%2016_11_19.png "2D Brick Breaker")
image générée par l'IA

## 🎯 Objectif
Dans ce projet, vous allez apprendre à créer un **jeu 2D inspiré du jeu classique *Brick Breaker***, où le joueur contrôle une raquette pour faire rebondir une balle et détruire des briques.
L’objectif est simple : faire disparaître toutes les briques sans laisser la balle tomber !
 
---

## 🚀 Fonctionnalités du jeu 
- Mouvement fluide de la palette (touches ← et → ou souris)  
- Balle rebondissante (rebonds sur murs, palette et briques)  
- Trois rangées de briques destructibles  
- Système de score dynamique  
- Gestion des vies (3 tentatives par partie)  
- Réinitialisation automatique après *Game Over*  
- (Bonus) Effets sonores à chaque collision  
- (Bonus) Difficulté progressive (vitesse de la balle augmentant)  
- (Bonus) Affichage du meilleur score 🏆 (stocké dans `localStorage`)
---

## 🛠️ Phases de développement

### Phase 1 : Configuration du projet
L'objectif: créer l'interface et le canvas de jeu en HTML et CSS
💬 Prompt : *Créer l'interface de jeu (HTML et CSS) affichant une balle qui rebondit, palette mobile contrôlée par le joueur, et trois rangées de briques positionnées en haut de l’écran*


### Phase 2 : Mécaniques de base
L'objectif: Ajouter la gestion du clavier pour déplacer la palette de gauche à droite.
- Générer et afficher la balle, la palette et les briques  
- Gérer le déplacement de la palette via les touches du clavier  
- Implémenter les rebonds de la balle sur les murs et la palette  
💬 Prompt : **
*L’objectif est de faire naviguer la palette mobile de gauche à droite pour faire rebodir la balle et détruire toutes les briques. À chaque brique touchée, le joueur accumule des points (+1). Si la balle tombe et sort du champs de l'écran, les points sont perdus (-1) et la partie terminée au bout de 3 échecs.*

### Phase 3 : Collision et score
L'objectif : Gérer et détecter les collisions entre la balle et les briques 
- Supprimer la brique au contact de la balle 
- Réinitialiser la balle en cas de perte  
- Arrêter le jeu si la balle sort du champs
💬 Prompt :*Gérer les collisions balle/brique et incrémenter un score.*

### Phase 4 : Interface et feedback visuel
L'objectif : Incrémenter/Décrémenter le score
- Ajouter le score et le nombre de vies à l’écran avec un message *Game Over* après 3 échecs
- Intégrer des effets (couleurs et animations) et ajouter le style avec CSS (couleurs, effets de rebond, transitions)
- Ajouter un bouton **Rejouer** ou **Start Game**
- utiliser une couleur différente pour chaque rangée de brique

---

## 🧪 Tests utilisateurs
- Vérifier le mouvement de la palette  
- Vérifier les rebonds et collisions  
- Vérifier la suppression correcte des briques  
- Vérifier le score et le compteur de vies  
- Tester le redémarrage du jeu après *Game Over*   

---
