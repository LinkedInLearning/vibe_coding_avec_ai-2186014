# Projet : Application Checklist (⚛️ React)

## 🎯 Objectif
Créer une application **Checklist** pour ajouter, cocher/décocher et supprimer des tâches, avec une sauvegarde locale.

---

## 🚀 Fonctionnalités principales
- ➕ Ajouter une tâche avec date automatique
- ❌ Supprimer une note   
- ✅ Cocher/décocher une tâche 
- (Bonus) Sauvegarde automatique dans `localStorage` 
- (Bonus) Filtrer les tâches (Toutes / Actives / Terminées)  
- (Bonus) Réorganiser l’ordre des tâches par drag & drop
- (Bonus) Attribuer une priorité (basse, normale, haute)  
- (Bonus) Choisir une couleur (ex : jaune, vert, bleu, rouge)  
- (Bonus) Bouton pour "Tout effacer" 
- (Bonus) Sauvegarde dans `localStorage`  
 
---

## 🌱 Philosophie de développement

- Commencer simple (**MVP first**)  
- Interface minimaliste et claire  
- Tester les fonctions principales (start, pause, reset) 
- Ajouter les fonctionnalités progressivement avec l'assistance de l'IA
- Tester manuellement chaque étape avant de passer à la suivante  

---

## 🛠️ Phase 1 : Configuration
- Créer une app React (Vite ou CRA)  
- Ouvrir composant `App` avec le titre "Checklist"   

## 📋 Phase 2 : Gestion des Tâches
**But : Avoir une liste de tâches dynamique**

- Champ texte + bouton **Ajouter**  
- Afficher toutes les tâches dans une liste  
- Cocher/décocher une tâche (toggle)  
- Supprimer une tâche  

## 🎨 Phase 3 : Style & Couleurs
- Tâches cochées → texte barré + grisé  
- Tâches actives → texte normal  
- Mise en page simple et responsive  

## 🧪 Phase 4 : Tests
- Vérifier l’ajout de tâche  
- Vérifier la suppression  
- Vérifier le toggle (cocher/décocher)  

---

### 💬 Prompts et consignes

- **Prompt 1 :**
Crée une application React avec Vite avec titre "Checklist", avec les fonctionnalités : ajouter une note avec texte et date automatique, et supprimer une note.
- ajouter un champ texte et un bouton 'Ajouter' qui permet d’ajouter une tâche dans un state React."  
- afficher la liste des tâches avec une checkbox pour les cocher/décocher.  
- ajouter un bouton 'supprimer' à côté de chaque tâche.  
- mettre à jour le state quand une tâche est cochée/décochée. 

- **Prompt 2 :**
- ajouter du avec CSS :
  - pour une tâche est cochée (supprimée), barrer le texte et change la couleur en gris 
- ajouter un style hover pour les boutons pour les rendre plus interactifs  

- **Prompt 3 :**
Crée un timer en JavaScript pur avec un champ de saisie au format HH:MM.
Le temps doit s’afficher en grand, centré sur la page.
La couleur du texte change selon l’état :
- 🟢 vert = en cours
- 🟠 orange = en pause
- 🔴 rouge = terminé
Plus, sauvegarder les notes dans localStorage.
Fournis un seul fichier HTML complet (HTML + CSS + JS intégrés), sans dépendance externe.

---

## ✅ Résultat attendu
Une application **Checklist** :  
- Simple et intuitive  
- Avec ajout, suppression, et marquage des tâches  
- Responsive et agréable à utiliser  
- Persistance locale pour garder les données  
