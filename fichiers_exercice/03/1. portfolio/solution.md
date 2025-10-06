# 🌐 Projet : Page Portfolio (HTML + CSS)

## Solution:

> Un exemple de page portfolio complète (HTML + CSS pur) conforme aux specs précédentes, avecun rendu est moderne, minimaliste, responsive, et parfaitement adapté à un usage en portfolio professionnel.
Aucune dépendance externe. Tout tient dans un seul fichier.

```bash
portfolio/
├── index.html
├── style.css
├── /images
│   ├── profile.jpg
│   └── project1.jpg
└── /assets
    └── icons/
    
```

```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Portfolio – Mon Profil</title>
  <style>
    :root {
      --bg: #f9fafb;
      --text: #1f2937;
      --accent: #2563eb;
      --card-bg: #ffffff;
      --border: #e5e7eb;
    }

    body {
      font-family: "Inter", system-ui, sans-serif;
      background-color: var(--bg);
      color: var(--text);
      margin: 0;
      line-height: 1.6;
    }

    header {
      background: var(--card-bg);
      border-bottom: 1px solid var(--border);
      padding: 1.5rem 2rem;
      text-align: center;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    header h1 {
      margin: 0;
      font-size: 1.8rem;
      color: var(--accent);
    }

    nav {
      margin-top: 0.5rem;
    }

    nav a {
      margin: 0 1rem;
      text-decoration: none;
      color: var(--text);
      font-weight: 500;
    }

    nav a:hover {
      color: var(--accent);
    }

    main {
      max-width: 1000px;
      margin: 2rem auto;
      padding: 0 1.5rem;
    }

    section {
      margin-bottom: 4rem;
    }

    h2 {
      font-size: 1.6rem;
      color: var(--accent);
      border-left: 4px solid var(--accent);
      padding-left: 0.6rem;
      margin-bottom: 1rem;
    }

    /* Profil */
    #about {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
    }

    #about img {
      width: 140px;
      height: 140px;
      border-radius: 50%;
      object-fit: cover;
      margin-bottom: 1rem;
      border: 3px solid var(--accent);
    }

    #about p {
      max-width: 600px;
      font-size: 1rem;
      color: #4b5563;
    }

    /* Projets */
    .projects {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.5rem;
    }

    .card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 12px;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
      overflow: hidden;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
    }

    .card img {
      width: 100%;
      height: 160px;
      object-fit: cover;
    }

    .card-content {
      padding: 1rem;
    }

    .card-content h3 {
      margin: 0.3rem 0;
      font-size: 1.1rem;
      color: var(--text);
    }

    .card-content p {
      font-size: 0.95rem;
      color: #6b7280;
    }

    .card-content a {
      display: inline-block;
      margin-top: 0.8rem;
      color: var(--accent);
      text-decoration: none;
      font-weight: 600;
      transition: color 0.2s ease;
    }

    .card-content a:hover {
      color: #1d4ed8;
    }

    /* Contact */
    form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      max-width: 500px;
      margin: 0 auto;
    }

    input, textarea {
      width: 100%;
      padding: 0.8rem 1rem;
      border: 1px solid var(--border);
      border-radius: 8px;
      font-family: inherit;
      font-size: 1rem;
    }

    button {
      background: var(--accent);
      color: white;
      border: none;
      padding: 0.9rem;
      font-size: 1rem;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background: #1d4ed8;
    }

    footer {
      text-align: center;
      padding: 2rem 1rem;
      font-size: 0.9rem;
      color: #6b7280;
      border-top: 1px solid var(--border);
      background: var(--card-bg);
    }

    /* Responsive */
    @media (max-width: 700px) {
      nav a {
        margin: 0 0.5rem;
      }

      #about img {
        width: 120px;
        height: 120px;
      }

      .card img {
        height: 140px;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Mon Portfolio</h1>
    <nav>
      <a href="#about">Profil</a>
      <a href="#projects">Projets</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <!-- Profil -->
    <section id="about">
      <img src="images/profile.jpg" alt="Photo de profil">
      <h2>👋 À propos de moi</h2>
      <p>
        Je suis un développeur passionné par la création d’expériences web modernes et performantes. 
        J’aime concevoir des interfaces claires, accessibles et centrées sur l’utilisateur.
      </p>
    </section>

    <!-- Projets -->
    <section id="projects">
      <h2>💼 Mes projets</h2>
      <div class="projects">
        <div class="card">
          <img src="images/project1.jpg" alt="Projet 1">
          <div class="card-content">
            <h3>Application Checklist</h3>
            <p>Une application React simple pour gérer ses tâches avec persistance locale.</p>
            <a href="#">Voir le projet →</a>
          </div>
        </div>
        <div class="card">
          <img src="images/project2.jpg" alt="Projet 2">
          <div class="card-content">
            <h3>Timer JS</h3>
            <p>Un minuteur en JavaScript pur avec changement de couleur selon l’état.</p>
            <a href="#">Voir le projet →</a>
          </div>
        </div>
        <div class="card">
          <img src="images/project3.jpg" alt="Projet 3">
          <div class="card-content">
            <h3>Portfolio Personnel</h3>
            <p>Une page vitrine responsive codée en HTML et CSS sans dépendances.</p>
            <a href="#">Voir le projet →</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section id="contact">
      <h2>📬 Me contacter</h2>
      <form>
        <input type="text" name="name" placeholder="Votre nom" required />
        <input type="email" name="email" placeholder="Votre email" required />
        <textarea name="message" rows="5" placeholder="Votre message..." required></textarea>
        <button type="submit">Envoyer</button>
      </form>
    </section>
  </main>

  <footer>
    © 2025 Mon Portfolio – Développé en HTML & CSS pur 🌿
  </footer>
</body>
</html>

```