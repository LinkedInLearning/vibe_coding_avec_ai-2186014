# 🌐 Projet : Page Portfolio (HTML + CSS)

## Solution:

Un exemple de page portfolio complète (HTML + CSS pur) conforme aux specs précédentes, avecun rendu est moderne, minimaliste, responsive, et parfaitement adapté à un usage en portfolio professionnel.
Aucune dépendance externe. Tout tient dans un seul fichier.
---

```bash
portfolio/
├── index.html
├── style.css
```
lien [CodePen](https://codepen.io/SandyL/pen/JoGNjzx)
```html
<body>
    <header>
        <h1>Portfolio</h1>
        <h2>Artiste & Vibe Coder</h2>
    </header>

    <main>
        <section id="profil">
            <h2>Profil</h2>
            <div class="profile-content">
                <div class="profile-image">👨‍💻</div>
                <div class="profile-text">
                    <p>Passionné par l'art du code et la créativité numérique, je transforme des idées en expériences digitales uniques.</p>
                    <p>Chaque projet est une opportunité d'explorer de nouvelles technologies et de repousser les limites du possible.</p>
                </div>
            </div>
        </section>

        <section id="biographie">
            <h2>Biographie</h2>
            <div class="bio-content">
                <p>
                    Développeur créatif et artiste numérique, je navigue entre le monde du code et celui de l'expression artistique. 
                    Mon parcours est guidé par une passion pour l'innovation et un désir constant d'apprendre.
                </p>
                <p>
                    Je crois fermement que la technologie et l'art ne sont pas des domaines séparés, mais plutôt des langages 
                    complémentaires qui peuvent s'enrichir mutuellement pour créer des expériences mémorables.
                </p>
                <p>
                    Mon approche minimaliste et fonctionnelle me permet de concevoir des solutions élégantes qui répondent 
                    aux besoins tout en conservant une esthétique soignée et intemporelle.
                </p>
            </div>

            <div class="projects-grid">
                <div class="project-card">
                    <h3>⏱️ Timer</h3>
                    <p>
                        Une application de gestion du temps élégante et intuitive. Conçue pour améliorer la productivité 
                        avec des fonctionnalités de minuterie personnalisables et une interface épurée qui facilite la 
                        concentration sur l'essentiel.
                    </p>
                </div>

                <div class="project-card">
                    <h3>✅ Checklist</h3>
                    <p>
                        Un gestionnaire de tâches minimaliste pour organiser votre quotidien. Ajoutez, modifiez et complétez 
                        vos tâches en toute simplicité grâce à une interface claire et responsive qui s'adapte à tous vos appareils.
                    </p>
                </div>
            </div>
        </section>

        <section id="contact">
            <h2>Contact</h2>
            <div class="social-links">
                <a href="https://github.com" class="social-link" target="_blank">
                    <span>🐙</span> GitHub
                </a>
                <a href="https://linkedin.com" class="social-link" target="_blank">
                    <span>💼</span> LinkedIn
                </a>
                <a href="https://twitter.com" class="social-link" target="_blank">
                    <span>🐦</span> Twitter
                </a>
                <a href="mailto:contact@example.com" class="social-link">
                    <span>📧</span> Email
                </a>
            </div>
        </section>
    </main>

    <footer>
        <p>&copy; 2025 Artiste et Vibe Coder. Tous droits réservés.</p>
    </footer>
</body>
</html>

```
```css
@import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@300..700&display=swap');
* {
          margin: 0;
          padding: 0;
          box-sizing: border-box;
      }

      :root {
          --bg-primary: #f5f5f5;
          --bg-secondary: #ffffff;
          --text-primary: #2c2c2c;
          --text-secondary: #666666;
          --accent: #4a4a4a;
          --shadow: rgba(0, 0, 0, 0.1);
          --transition: all 0.3s ease;
      }

      body {
/*           font-family: 'Segoe UI', Tahoma, Geneva, Verdana,  */
          font-family: "Quicksand", sans-serif;sans-serif;
          line-height: 1.6;
          font-size : 18px;
          color: var(--text-primary);
          background-color: var(--bg-primary);
      }

      header {
          background-color: var(--bg-secondary);
          padding: 3rem 2rem;
          text-align: center;
          box-shadow: 0 2px 10px var(--shadow);
      }

      header h1 {
          font-size: 2.5rem;
          margin-bottom: 0.5rem;
          font-weight: 300;
          letter-spacing: 2px;
      }

      header p {
          color: var(--text-secondary);
          font-size: 1.2rem;
          font-weight: 300;
      }

      main {
          max-width: 1200px;
          margin: 0 auto;
          padding: 3rem 2rem;
      }

      section {
          margin-bottom: 4rem;
      }

      h2 {
          font-size: 2rem;
          margin-bottom: 2rem;
          font-weight: 300;
          text-align: center;
          position: relative;
      }

      h2::after {
          content: '';
          display: block;
          width: 60px;
          height: 2px;
          background-color: var(--accent);
          margin: 1rem auto 0;
      }

      .profile-content {
          display: flex;
          justify-content: center;
          align-items: center;
          gap: 3rem;
          flex-wrap: wrap;
      }

      .profile-image {
          width: 200px;
          height: 200px;
          border-radius: 50%;
          background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
          display: flex;
          align-items: center;
          justify-content: center;
          font-size: 4rem;
          color: white;
          box-shadow: 0 4px 15px var(--shadow);
      }

      .profile-text {
          max-width: 500px;
      }

      .profile-text p {
          color: var(--text-secondary);
          margin-bottom: 1rem;
      }

      .bio-content {
          max-width: 800px;
          margin: 0 auto;
          background-color: var(--bg-secondary);
          padding: 2.5rem;
          border-radius: 8px;
          box-shadow: 0 2px 10px var(--shadow);
      }

      .bio-content p {
          color: var(--text-secondary);
          margin-bottom: 1.5rem;
          text-align: justify;
      }

      .projects-grid {
          display: grid;
          grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
          gap: 2rem;
          margin-top: 2rem;
      }

      .project-card {
          background-color: var(--bg-secondary);
          padding: 2rem;
          border-radius: 8px;
          box-shadow: 0 2px 10px var(--shadow);
          transition: var(--transition);
          cursor: pointer;
      }

      .project-card:hover {
          transform: translateY(-8px);
          box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
      }

      .project-card h3 {
          font-size: 1.5rem;
          margin-bottom: 1rem;
          font-weight: 400;
      }

      .project-card p {
          color: var(--text-secondary);
          line-height: 1.8;
      }

      footer {
          background-color: var(--bg-secondary);
          padding: 3rem 2rem;
          text-align: center;
          box-shadow: 0 -2px 10px var(--shadow);
      }

      .social-links {
          display: flex;
          justify-content: center;
          gap: 2rem;
          margin-top: 2rem;
          flex-wrap: wrap;
      }

      .social-link {
          display: inline-flex;
          align-items: center;
          gap: 0.5rem;
          padding: 0.8rem 1.5rem;
          background-color: var(--accent);
          color: white;
          text-decoration: none;
          border-radius: 50px;
          transition: var(--transition);
          font-size: 0.95rem;
      }

      .social-link:hover {
          background-color: var(--text-primary);
          transform: scale(1.05);
      }

      @media (max-width: 768px) {
          header h1 {
              font-size: 2rem;
          }

          header p {
              font-size: 1rem;
          }

          h2 {
              font-size: 1.5rem;
          }

          .profile-content {
              gap: 2rem;
          }

          .profile-image {
              width: 150px;
              height: 150px;
              font-size: 3rem;
          }

          .bio-content {
              padding: 1.5rem;
          }

          .projects-grid {
              grid-template-columns: 1fr;
          }

          .social-links {
              gap: 1rem;
          }

          .social-link {
              padding: 0.7rem 1.2rem;
              font-size: 0.9rem;
          }
      }
```