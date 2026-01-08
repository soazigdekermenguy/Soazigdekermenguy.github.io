<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <title>Soazig de Kermenguy - Portfolio</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />

  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

    :root {
      --bg-primary: #f8faff;
      --bg-secondary: #fdfbff;
      --accent-blue: #c1dbfc;
      --accent-pink: #f5d7e3;
      --accent-blue-dark: #9bb8d8;
      --accent-pink-dark: #e2b3c9;
      --text-primary: #1a202c;
      --text-secondary: #4a5568;
      --white: #ffffff;
      --shadow: 0 20px 40px rgba(0,0,0,0.08);
      --shadow-hover: 0 25px 50px rgba(0,0,0,0.12);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--bg-primary);
      color: var(--text-primary);
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* HEADER */
    .header {
      position: fixed;
      top: 0;
      width: 100%;
      background: rgba(248, 250, 255, 0.95);
      backdrop-filter: blur(20px);
      z-index: 1000;
      padding: 1rem 0;
      border-bottom: 1px solid rgba(193, 219, 252, 0.3);
      box-shadow: 0 2px 20px rgba(0,0,0,0.05);
    }

    .nav-container {
      max-width: 1400px;
      margin: 0 auto;
      padding: 0 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .logo {
      font-size: 1.8rem;
      font-weight: 700;
      background: linear-gradient(135deg, var(--accent-blue-dark), var(--accent-pink-dark));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .nav {
      display: flex;
      gap: 2.5rem;
      list-style: none;
    }

    .nav-link {
      color: var(--text-secondary);
      text-decoration: none;
      font-weight: 500;
      font-size: 0.95rem;
      padding: 0.5rem 0;
      position: relative;
      transition: all 0.3s ease;
    }

    .nav-link::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 0;
      height: 2px;
      background: linear-gradient(135deg, var(--accent-blue-dark), var(--accent-pink-dark));
      transition: width 0.3s ease;
      border-radius: 1px;
    }

    .nav-link:hover::after,
    .nav-link.active::after {
      width: 100%;
    }

    .nav-link:hover,
    .nav-link.active {
      color: var(--text-primary);
    }

    /* HERO */
    .hero {
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      position: relative;
      background: linear-gradient(135deg, var(--bg-primary) 0%, var(--bg-secondary) 100%);
    }

    .hero-content {
      max-width: 800px;
      padding: 0 2rem;
    }

    .hero-badge {
      display: inline-block;
      background: linear-gradient(135deg, var(--accent-blue), var(--accent-pink));
      color: var(--text-primary);
      backdrop-filter: blur(10px);
      padding: 0.75rem 2rem;
      border-radius: 50px;
      font-size: 0.9rem;
      font-weight: 600;
      letter-spacing: 0.1em;
      margin-bottom: 2rem;
      box-shadow: 0 8px 25px rgba(193,219,252,0.3);
    }

    .hero-title {
      font-size: clamp(3.5rem, 8vw, 6rem);
      font-weight: 800;
      line-height: 0.9;
      margin-bottom: 1.5rem;
      background: linear-gradient(135deg, var(--accent-blue-dark), var(--accent-pink-dark));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .hero-subtitle {
      font-size: 1.3rem;
      color: var(--text-secondary);
      margin-bottom: 3rem;
      font-weight: 400;
    }

    .hero-locations {
      display: flex;
      justify-content: center;
      gap: 2.5rem;
      margin-bottom: 3rem;
      font-size: 1.2rem;
      font-weight: 500;
    }

    .location {
      color: var(--text-secondary);
      background: rgba(245, 215, 227, 0.3);
      padding: 0.5rem 1.5rem;
      border-radius: 25px;
      backdrop-filter: blur(10px);
    }

    .cta-buttons {
      display: flex;
      gap: 1.5rem;
      justify-content: center;
      flex-wrap: wrap;
    }

    .btn {
      padding: 1rem 2.5rem;
      border-radius: 50px;
      font-weight: 600;
      text-decoration: none;
      transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
      font-size: 1rem;
      position: relative;
      overflow: hidden;
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      border: 1px solid transparent;
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--accent-blue-dark), var(--accent-pink-dark));
      color: var(--text-primary);
      box-shadow: 0 8px 25px rgba(193,219,252,0.3);
    }

    .btn-primary:hover {
      transform: translateY(-3px);
      box-shadow: 0 15px 35px rgba(193,219,252,0.4);
    }

    .btn-secondary {
      background: rgba(255,255,255,0.8);
      color: var(--text-primary);
      box-shadow: 0 5px 15px rgba(0,0,0,0.05);
    }

    .btn-secondary:hover {
      background: var(--white);
      transform: translateY(-3px);
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    }

    /* SECTIONS */
    .section {
      padding: 120px 0;
      max-width: 1400px;
      margin: 0 auto;
      padding-left: 2rem;
      padding-right: 2rem;
    }

    .section-header {
      text-align: center;
      margin-bottom: 5rem;
    }

    .section-title {
      font-size: clamp(2.5rem, 5vw, 4rem);
      font-weight: 700;
      margin-bottom: 1rem;
      background: linear-gradient(135deg, var(--accent-blue-dark), var(--accent-pink-dark));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .section-subtitle {
      font-size: 1.2rem;
      color: var(--text-secondary);
      max-width: 600px;
      margin: 0 auto;
    }

    /* GALLERY */
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
      gap: 2rem;
    }

    .gallery-item {
      position: relative;
      height: 500px;
      border-radius: 24px;
      overflow: hidden;
      cursor: pointer;
      background: var(--white);
      border: 1px solid rgba(193,219,252,0.3);
      transition: all 0.4s ease;
      box-shadow: 0 10px 30px rgba(0,0,0,0.05);
    }

    .gallery-item:hover {
      transform: translateY(-10px);
      box-shadow: var(--shadow-hover);
      border-color: rgba(245,215,227,0.5);
    }

    .gallery-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.4s ease;
      border-radius: 22px;
    }

    .gallery-item:hover img {
      transform: scale(1.05);
    }

    .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(transparent, rgba(26,32,44,0.85));
      padding: 2rem;
      transform: translateY(100%);
      transition: transform 0.4s ease;
    }

    .gallery-item:hover .gallery-overlay {
      transform: translateY(0);
    }

    .gallery-title {
      font-size: 1.5rem;
      font-weight: 600;
      margin-bottom: 0.5rem;
      color: var(--white);
    }

    .gallery-meta {
      color: rgba(255,255,255,0.9);
      font-size: 0.95rem;
    }

    /* ABOUT */
    .about-content {
      max-width: 800px;
      margin: 0 auto;
      text-align: center;
      background: rgba(255,255,255,0.6);
      backdrop-filter: blur(20px);
      border: 1px solid rgba(193,219,252,0.4);
      border-radius: 24px;
      padding: 4rem 2rem;
      box-shadow: 0 20px 40px rgba(0,0,0,0.06);
    }

    .about-text {
      font-size: 1.2rem;
      line-height: 1.8;
      margin-bottom: 3rem;
      color: var(--text-primary);
    }

    .skills {
      display: flex;
      gap: 1.5rem;
      justify-content: center;
      flex-wrap: wrap;
    }

    .skill-tag {
      background: linear-gradient(135deg, var(--accent-blue), var(--accent-pink));
      color: var(--text-primary);
      padding: 0.75rem 1.5rem;
      border-radius: 50px;
      font-size: 0.9rem;
      font-weight: 500;
      box-shadow: 0 5px 15px rgba(193,219,252,0.3);
    }

    /* CONTACT */
    .contact-content {
      max-width: 600px;
      margin: 0 auto;
      text-align: center;
      background: rgba(255,255,255,0.6);
      backdrop-filter: blur(20px);
      border: 1px solid rgba(193,219,252,0.4);
      border-radius: 24px;
      padding: 4rem 2rem;
      box-shadow: 0 20px 40px rgba(0,0,0,0.06);
    }

    .contact-email {
      font-size: 1.5rem;
      font-weight: 600;
      margin: 2rem 0;
      word-break: break-all;
    }

    .contact-email a {
      color: var(--text-primary);
      text-decoration: none;
      font-weight: 600;
    }

    /* FOOTER */
    .footer {
      padding: 4rem 2rem 2rem;
      text-align: center;
      border-top: 1px solid rgba(193,219,252,0.3);
      color: var(--text-secondary);
    }

    .social-links {
      display: flex;
      justify-content: center;
      gap: 2rem;
      margin: 2rem 0;
      flex-wrap: wrap;
    }

    .social-link {
      color: var(--text-secondary);
      text-decoration: none;
      font-size: 1.1rem;
      padding: 1rem 1.5rem;
      border-radius: 16px;
      border: 1px solid rgba(193,219,252,0.3);
      transition: all 0.3s ease;
      background: rgba(255,255,255,0.5);
    }

    .social-link:hover {
      background: linear-gradient(135deg, var(--accent-blue), var(--accent-pink));
      color: var(--text-primary);
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(193,219,252,0.3);
    }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      .nav {
        display: none;
      }

      .hero-locations {
        flex-direction: column;
        gap: 1rem;
      }

      .cta-buttons {
        flex-direction: column;
        align-items: center;
      }

      .btn {
        width: 100%;
        max-width: 300px;
      }

      .gallery {
        grid-template-columns: 1fr;
        gap: 1.5rem;
      }

      .section {
        padding-left: 1.5rem;
        padding-right: 1.5rem;
      }
    }

    /* Lightbox */
    .lightbox {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(248, 250, 255, 0.95);
      z-index: 2000;
      display: none;
      align-items: center;
      justify-content: center;
      backdrop-filter: blur(10px);
    }

    .lightbox.active {
      display: flex;
    }

    .lightbox img {
      max-width: 90vw;
      max-height: 90vh;
      object-fit: contain;
      border-radius: 20px;
      box-shadow: 0 20px 60px rgba(0,0,0,0.15);
    }
  </style>
</head>
<body>
  <header class="header">
    <nav class="nav-container">
      <div class="logo">S2K</div>
      <ul class="nav">
        <li><a href="#home" class="nav-link active">Accueil</a></li>
        <li><a href="#portfolio" class="nav-link">Portfolio</a></li>
        <li><a href="#about" class="nav-link">À propos</a></li>
        <li><a href="#contact" class="nav-link">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <!-- HERO -->
    <section id="home" class="hero">
      <div class="hero-content">
        <div class="hero-badge">Saison 2026 complète</div>
        <h1 class="hero-title">Soazig de Kermenguy</h1>
        <div class="hero-subtitle">Photographe de mariages</div>
        <div class="hero-locations">
          <div class="location">Brest</div>
          <div class="location">La Roche-sur-Yon</div>
        </div>
        <div class="hero-subtitle">ETN Photo • Scouts d'Europe</div>
        <div class="cta-buttons">
          <a href="#portfolio" class="btn btn-primary">Voir le portfolio</a>
          <a href="#contact" class="btn btn-secondary">Me contacter</a>
        </div>
      </div>
    </section>

    <!-- PORTFOLIO -->
    <section id="portfolio" class="section">
      <div class="section-header">
        <h2 class="section-title">Portfolio</h2>
        <p class="section-subtitle">Mariages</p>
      </div>
      <div class="gallery">
        <div class="gallery-item" data-full="https://images.unsplash.com/photo-1511285560929-80b456fea0bc?w=1400">
          <img src="https://images.unsplash.com/photo-1511285560929-80b456fea0bc?w=500&q=85" alt="Cérémonie">
          <div class="gallery-overlay">
            <h3 class="gallery-title">Cérémonie</h3>
            <p class="gallery-meta">Mariage • 2025</p>
          </div>
        </div>
        <div class="gallery-item" data-full="https://images.unsplash.com/photo-1571896349840-0d2d1ba8f7bf?w=1400">
          <img src="https://images.unsplash.com/photo-1571896349840-0d2d1ba8f7bf?w=500&q=85" alt="Baiser">
          <div class="gallery-overlay">
            <h3 class="gallery-title">Premier baiser</h3>
            <p class="gallery-meta">Mariage • 2025</p>
          </div>
        </div>
        <div class="gallery-item" data-full="https://images.unsplash.com/photo-1515934751635-c81c6bc9a2d8?w=1400">
          <img src="https://images.unsplash.com/photo-1515934751635-c81c6bc9a2d8?w=500&q=85" alt="Alliances">
          <div class="gallery-overlay">
            <h3 class="gallery-title">Échange d'alliances</h3>
            <p class="gallery-meta">Mariage • 2024</p>
          </div>
        </div>
        <div class="gallery-item" data-full="https://images.unsplash.com/photo-1569016602078-f2c0bd3e1f37?w=1400">
          <img src="https://images.unsplash.com/photo-1569016602078-f2c0bd3e1f37?w=500&q=85" alt="Réception">
          <div class="gallery-overlay">
            <h3 class="gallery-title">Réception</h3>
            <p class="gallery-meta">Mariage • 2025</p>
          </div>
        </div>
        <div class="gallery-item" data-full="https://images.unsplash.com/photo-1517443440416-9ca7853223e3?w=1400">
          <img src="https://images.unsplash.com/photo-1517443440416-9ca7853223e3?w=500&q=85" alt="Danse">
          <div class="gallery-overlay">
            <h3 class="gallery-title">Ouverture de bal</h3>
            <p class="gallery-meta">Mariage • 2024</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ABOUT -->
    <section id="about" class="section">
      <div class="about-content">
        <h2 class="section-title" style="margin-bottom: 2rem;">À propos</h2>
        <p class="about-text">
          J'ai 19 ans et je capture les moments uniques avec émotion et authenticité. 
          Spécialisée dans les mariages, les couples et les portraits familiaux.
        </p>
        <div class="skills">
          <span class="skill-tag">Mariages</span>
          <span class="skill-tag">Couples</span>
          <span class="skill-tag">Famille</span>
          <span class="skill-tag">Scouts</span>
          <span class="skill-tag">Nature</span>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="section">
      <div class="contact-content">
        <h2 class="section-title" style="margin-bottom: 2rem;">Contact</h2>
        <p style="font-size: 1.3rem; margin-bottom: 2rem; color: var(--text-secondary);">
          Prêt à capturer vos plus beaux moments ?
        </p>
        <p class="contact-email">
          <a href="mailto:soazigdekermenguy@gmail.com">soazigdekermenguy@gmail.com</a>
        </p>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="social-links">
      <a href="https://instagram.com/s2k__photos" class="social-link" target="_blank">Instagram</a>
      <a href="#" class="social-link" target="_blank">Pinterest</a>
      <a href="#" class="social-link" target="_blank">TikTok</a>
    </div>
    <p>© 2026 Soazig de Kermenguy. Tous droits réservés.</p>
    <p style="margin-top: 1rem; font-size: 0.9rem; color: var(--text-secondary);">Design par Wandrille.Fernex.de.Mongex</p>
  </footer>

  <script>
    // Smooth scroll navigation
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
          target.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
          });
          
          document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('active'));
          this.classList.add('active');
        }
      });
    });

    // Update active nav on scroll
    window.addEventListener('scroll', () => {
      const sections = document.querySelectorAll('section');
      const scrollPos = window.scrollY + 100;

      sections.forEach(section => {
        if (section.offsetTop <= scrollPos && scrollPos < section.offsetTop + section.offsetHeight) {
          const id = section.getAttribute('id');
          document.querySelectorAll('.nav-link').forEach(link => {
            link.classList.remove('active');
            if (link.getAttribute('href') === `#${id}`) {
              link.classList.add('active');
            }
          });
        }
      });
    });

    // Gallery lightbox
    document.querySelectorAll('.gallery-item').forEach(item => {
      item.addEventListener('click', () => {
        const imgSrc = item.dataset.full || item.querySelector('img').src;
        const lightbox = document.createElement('div');
        lightbox.className = 'lightbox active';
        lightbox.innerHTML = `
          <div class="lightbox-content">
            <img src="${imgSrc}" alt="Portfolio">
            <button class="lightbox-close">&times;</button>
          </div>
        `;
        document.body.appendChild(lightbox);
        document.body.style.overflow = 'hidden';

        lightbox.querySelector('.lightbox-close').onclick = () => {
          document.body.removeChild(lightbox);
          document.body.style.overflow = '';
        };
        
        lightbox.onclick = (e) => {
          if (e.target === lightbox) {
            document.body.removeChild(lightbox);
            document.body.style.overflow = '';
          }
        };
      });
    });
  </script>
</body>
</html>
