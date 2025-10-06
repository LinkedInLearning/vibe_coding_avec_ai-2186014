# Bloc Notes (Minimal Version) - Spécifications Techniques

## 1. Aperçu du projet
Une application React monopage permettant aux utilisateurs de créer, modifier, supprimer et organiser des notes.  
Les notes sont persistées dans `localStorage`, colorées pour une meilleure organisation, et filtrables via une recherche.  

---

## 2. Fonctionnalités principales (30 minutes de build)

### 2.1 Ajout de notes (5 minutes)
#### Interface de base
- **Bouton "Nouvelle note"** visible en haut
- **Création immédiate** d’une note vide avec un champ de texte éditable
- **Modèle de données** :
  ```javascript
  { id, contenu, couleur, épinglée, dateCréation }
  ```
- **Stockage initial** : état React (array de notes)

---

### 2.2 Édition de notes (5 minutes)
- Modification inline : clic sur la note → champ de texte éditable
- Sauvegarde automatique après chaque frappe (`onChange`)
- Pas de bouton "sauvegarder" (UX simplifiée)

---

### 2.3 Suppression de notes (3 minutes)
- Icône (🗑️) dans le coin supérieur droit de chaque note
- Confirmation avant suppression définitive
- Mise à jour immédiate du `localStorage`

---

### 2.4 Sauvegarde locale (3 minutes)
- `localStorage` utilisé pour persister toutes les notes
- Récupération automatique au chargement de l’app
- Synchronisation automatique après chaque ajout, édition ou suppression

---

### 2.5 Couleurs personnalisées (5 minutes)
- Menu déroulant ou bouton sur chaque note pour choisir une couleur
- Options : Jaune, Vert, Bleu, Rouge
- La couleur est stockée dans l’objet note
- Styles appliqués via classes CSS

---

### 2.6 Recherche (5 minutes)
- Barre de recherche globale en haut
- Filtrage en direct des notes affichées (par contenu ou couleur)
- Sensible à la casse ignorée (case-insensitive)

---

### 2.7 Épinglage (bonus 3 minutes)
- Icône (📌) sur chaque note
- Notes épinglées affichées en haut de la grille
- Persistance via `localStorage`

---

### 2.8 Tout effacer (bonus 3 minutes)
- Bouton "Effacer toutes les notes"
- Confirmation requise
- Réinitialise le `localStorage`

---

## 3. Implémentation technique

### 3.1 Dépendances minimales
```json
{
  "dependencies": {
    "react": "^18.0.0"
  },
  "devDependencies": {
    "@testing-library/react": "^14.0.0",
    "jest": "^29.0.0"
  }
}
```

### 3.2 Structure des composants
```
src/
├── App.jsx                 # Point d’entrée principal
├── components/
│   ├── Note.jsx           # Composant individuel de note
│   ├── NoteList.jsx       # Affiche toutes les notes
│   ├── SearchBar.jsx      # Barre de recherche
│   ├── Toolbar.jsx        # Boutons principaux (nouvelle note, tout effacer)
└── utils/
    ├── storage.js         # Gestion du localStorage
    └── helpers.js         # Génération d’ID, tri par épinglage
```

### 3.3 Structure d’état
```javascript
const [state, setState] = useState({
  notes: [],          // toutes les notes
  searchQuery: "",    // recherche active
});
```

---

## 4. Étapes d’implémentation (30 minutes)

### Étape 1 : Setup (5 min)
- Initialiser l’app avec Vite
- Ajouter App.jsx et affichage du titre
- Configurer TailwindCSS pour les styles

### Étape 2 : Notes CRUD (10 min)
- Créer composant `Note`
- Ajouter/supprimer/éditer une note
- Mettre à jour état + `localStorage`

### Étape 3 : Couleurs et organisation (5 min)
- Ajouter option de couleur
- Grille responsive avec CSS Grid
- Support épinglage (notes en haut)

### Étape 4 : Recherche (5 min)
- Ajouter `SearchBar` filtrant la liste des notes
- Mise à jour en direct des résultats

### Étape 5 : Finitions (5 min)
- Ajouter bouton “Tout effacer”
- Tests unitaires simples : ajout, suppression, recherche
- Vérification du responsive

---

## 5. Guidelines de style (CSS minimal)

### 5.1 Layout
- Grille responsive avec `grid-template-columns: repeat(auto-fill, minmax(200px, 1fr))`
- Espacement uniforme avec `gap: 1rem`

### 5.2 Couleurs des notes
```css
.note-yellow { background: #FFF9C4; }  /* Jaune */
.note-green { background: #C8E6C9; }   /* Vert */
.note-blue { background: #BBDEFB; }    /* Bleu */
.note-red { background: #FFCDD2; }     /* Rouge */
```

### 5.3 Effets
- Animation légère sur ajout/suppression
- Hover sur boutons (légère ombre portée)

---

## 6. Flux de données
1. L’utilisateur ajoute/édite/supprime une note
2. État React mis à jour (`notes`)
3. Sauvegarde immédiate dans `localStorage`
4. Au rechargement, l’app recharge depuis `localStorage`
5. Recherche → filtre les notes affichées sans toucher aux données brutes

---

## 7. Cas particuliers à gérer

### 7.1 Obligatoires
- Notes vides → empêcher la sauvegarde
- Tentative de tout effacer → demander confirmation
- `localStorage` plein ou non disponible → message d’erreur


---

## 8. Checklist de test rapide
1. ✓ Ajouter une note fonctionne
2. ✓ Édition inline sauvegarde automatiquement
3. ✓ Suppression avec confirmation fonctionne
4. ✓ Les notes persistent après rechargement
5. ✓ Recherche filtre correctement
6. ✓ Épinglage remonte les notes
7. ✓ “Tout effacer” supprime bien toutes les notes

---

## 9. Bonus : Extensions possibles
### 9.1 Quick wins
- Exporter toutes les notes en `.json`
- Trier les notes par date ou couleur
- Mode sombre

### 9.2 Améliorations UX
- Drag-and-drop pour réorganiser les notes
- Support Markdown dans le contenu
- Tags/catégories de notes
- Synchronisation cloud

---
