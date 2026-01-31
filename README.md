<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>kataX | Digital Excellence Studio</title>

  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Outfit:wght@300;400;700&display=swap" rel="stylesheet">

  <style>
    :root {
      --lila: #9b5cff;
      --rosa: #ff4fa3;
      --negro-ebano: #030305;
      --negro-card: #08080c;
      --border: rgba(255, 255, 255, 0.06);
      --text-gray: #a1a1aa;
      --gradient: linear-gradient(135deg, var(--lila) 0%, var(--rosa) 100%);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; scroll-behavior: smooth; }

    body {
      background-color: var(--negro-ebano);
      color: #ffffff;
      font-family: 'Plus Jakarta Sans', sans-serif;
      overflow-x: hidden;
    }

    /* BACKGROUND EFECTOS */
    .bg-main {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      z-index: -1;
      background-image: 
        radial-gradient(circle at 20% 30%, rgba(155, 92, 255, 0.07) 0%, transparent 40%),
        radial-gradient(circle at 80% 70%, rgba(255, 79, 163, 0.07) 0%, transparent 40%);
    }

    /* HEADER */
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 25px 8%;
      backdrop-filter: blur(20px);
      position: fixed;
      width: 100%;
      top: 0;
      z-index: 1000;
      border-bottom: 1px solid var(--border);
    }

    .logo {
      font-size: 1.8rem;
      font-weight: 800;
      letter-spacing: -2px;
      background: var(--gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      font-family: 'Outfit', sans-serif;
    }

    nav ul { display: flex; list-style: none; gap: 40px; }
    nav a { 
      text-decoration: none; color: #fff; font-size: 0.9rem; 
      font-weight: 500; opacity: 0.5; transition: 0.4s;
    }
    nav a:hover { opacity: 1; color: var(--rosa); text-shadow: 0 0 10px rgba(255,79,163,0.3); }

    /* SECCIONES ANIMADAS */
    section { padding: 120px 8%; opacity: 0; transform: translateY(40px); transition: 1.2s cubic-bezier(0.22, 1, 0.36, 1); }
    section.visible { opacity: 1; transform: translateY(0); }

    /* HERO SECTION */
    .hero {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
    }

    .hero-badge {
      background: rgba(155, 92, 255, 0.1);
      border: 1px solid rgba(155, 92, 255, 0.2);
      padding: 8px 20px;
      border-radius: 100px;
      font-size: 0.8rem;
      color: var(--lila);
      margin-bottom: 25px;
      font-weight: 600;
      letter-spacing: 1px;
    }

    .hero h1 { 
      font-family: 'Outfit', sans-serif;
      font-size: clamp(3rem, 10vw, 6.5rem); 
      font-weight: 700; 
      line-height: 0.95; 
      margin-bottom: 30px; 
    }

    .hero p { 
      max-width: 700px; 
      font-size: 1.2rem; 
      color: var(--text-gray); 
      margin-bottom: 45px; 
      line-height: 1.6;
    }

    .btn {
      padding: 20px 50px;
      border-radius: 16px;
      font-weight: 700;
      font-size: 1.1rem;
      text-decoration: none;
      transition: 0.5s;
      border: none;
      cursor: pointer;
    }

    .btn-glow {
      background: var(--gradient);
      color: #fff;
      box-shadow: 0 10px 40px rgba(155, 92, 255, 0.4);
    }

    .btn-glow:hover { transform: scale(1.05); box-shadow: 0 20px 60px rgba(255, 79, 163, 0.6); }

    /* QUIÉNES SOMOS */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: center;
    }

    .about-text h2 { font-size: 3rem; margin-bottom: 30px; font-family: 'Outfit', sans-serif; }
    .about-text span { background: var(--gradient); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
    .about-text p { font-size: 1.1rem; color: var(--text-gray); margin-bottom: 20px; line-height: 1.8; }

    .stat-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 40px; }
    .stat-card { background: var(--negro-card); padding: 25px; border-radius: 20px; border: 1px solid var(--border); }
    .stat-card h4 { font-size: 2rem; color: var(--rosa); margin-bottom: 5px; }
    .stat-card p { font-size: 0.9rem; margin-bottom: 0; }

    /* TRABAJOS */
    .work-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 30px; margin-top: 50px; }
    .work-item {
      position: relative;
      height: 450px;
      border-radius: 30px;
      overflow: hidden;
      background: var(--negro-card);
      border: 1px solid var(--border);
      transition: 0.5s;
    }

    .work-item:hover { border-color: var(--lila); transform: scale(1.02); }
    .work-content {
      position: absolute;
      bottom: 0; left: 0; width: 100%;
      padding: 40px;
      background: linear-gradient(to top, var(--negro-ebano), transparent);
    }

    /* PRECIOS */
    .price-section { text-align: center; }
    .price-box {
      max-width: 500px;
      margin: 60px auto;
      background: linear-gradient(145deg, #0a0a0f 0%, #030305 100%);
      padding: 60px;
      border-radius: 40px;
      border: 1px solid var(--lila);
      position: relative;
    }

    .price-box::after {
      content: 'OFERTA DE LANZAMIENTO';
      position: absolute;
      top: -15px; left: 50%;
      transform: translateX(-50%);
      background: var(--gradient);
      padding: 5px 20px;
      border-radius: 50px;
      font-size: 0.7rem;
      font-weight: 800;
    }

    .price-amount { font-size: 5rem; font-weight: 800; line-height: 1; margin: 30px 0; font-family: 'Outfit'; }
    .price-amount span { font-size: 1.5rem; color: var(--text-gray); }

    .features-list { list-style: none; margin-bottom: 40px; text-align: left; }
    .features-list li { margin-bottom: 15px; display: flex; align-items: center; gap: 10px; color: var(--text-gray); }
    .features-list li::before { content: '✦'; color: var(--rosa); font-weight: bold; }

    /* CONTACTO */
    .contact-area { text-align: center; padding: 150px 8%; }
    .contact-area h2 { font-size: 4rem; margin-bottom: 20px; font-family: 'Outfit'; }
    .contact-link { 
      font-size: clamp(1.5rem, 5vw, 3.5rem); 
      color: #fff; text-decoration: none; 
      font-weight: 800; transition: 0.4s;
    }
    .contact-link:hover { color: var(--lila); letter-spacing: 2px; }

    footer {
      padding: 60px 8%;
      border-top: 1px solid var(--border);
      display: flex;
      justify-content: space-between;
      align-items: center;
      opacity: 0.5;
      font-size: 0.9rem;
    }

    @media (max-width: 900px) {
      .about-grid { grid-template-columns: 1fr; }
      nav ul { display: none; }
      .hero h1 { font-size: 4rem; }
    }
  </style>
</head>
<body>

  <div class="bg-main"></div>

  <header>
    <div class="logo">kataX</div>
    <nav>
      <ul>
        <li><a href="#about">Nosotros</a></li>
        <li><a href="#work">Trabajos</a></li>
        <li><a href="#prices">Precios</a></li>
        <li><a href="#contact">Contacto</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section id="hero" class="hero visible">
      <div class="hero-badge">FRONTEND WEB'S & MORE</div>
      <h1>Creamos el <br><span>Futuro Digital.</span></h1>
      <p>No somos una agencia convencional. Somos un estudio boutique que fusiona el diseño de autor con la potencia de la Inteligencia Artificial para marcas que exigen excelencia.</p>
      <a href="#contact" class="btn btn-glow">Reservar Consultoría</a>
    </section>

    <section id="about">
      <div class="about-grid">
        <div class="about-text">
          <h2>Una nueva era de <span>Emprendimiento.</span></h2>
          <p>En <strong>kataX</strong>, la juventud no es una falta de experiencia, sino nuestra mayor ventaja. Nacimos en la era de la IA y el código fluido.</p>
          <p>Somos dos mentes emprendedoras dedicadas a transformar ideas complejas en interfaces minimalistas. Creemos en la elegancia del negro, la fuerza del lila y la precisión de cada píxel.</p>
          
          <div class="stat-grid">
            <div class="stat-card"><h4>∞</h4><p>Pasión por el código</p></div>
            <div class="stat-card"><h4>AI</h4><p>Flujo de trabajo moderno</p></div>
          </div>
        </div>
        <div class="about-visual">
          <div style="width: 100%; height: 400px; background: linear-gradient(45deg, #08080c, #1a1a2e); border-radius: 40px; border: 1px solid var(--lila); display: flex; align-items: center; justify-content: center; font-size: 4rem;">X</div>
        </div>
      </div>
    </section>

    <section id="work">
      <h2 style="font-size: 3rem; margin-bottom: 50px; text-align: center;">Proyectos <span>Destacados</span></h2>
      <div class="work-grid">
        <div class="work-item">
          <div class="work-content">
            <h3>CalendAxel</h3>
            <p>Sistema de gestión inteligente con arquitectura React.</p>
          </div>
        </div>
        <div class="work-item">
          <div class="work-content">
            <h3>Fisiolución</h3>
            <p>Landing page emocional con optimización de conversión.</p>
          </div>
        </div>
        <div class="work-item">
          <div class="work-content">
            <h3>NoxLabs V1</h3>
            <p>Ecosistema digital para creadores de tecnología.</p>
          </div>
        </div>
      </div>
    </section>

    <section id="prices" class="price-section">
      <h2>Inversión <span>Transparente</span></h2>
      <p style="color: var(--text-gray); margin-top: 15px;">Calidad premium a precio de lanzamiento.</p>
      
      <div class="price-box">
        <h3>Web Profesional Full-Service</h3>
        <div class="price-amount">50€<span>/mes</span></div>
        <ul class="features-list">
          <li>Diseño exclusivo kataX (Sin plantillas)</li>
          <li>Desarrollo con React & Tailwind CSS</li>
          <li>Mantenimiento técnico y actualizaciones</li>
          <li>Optimización SEO y Velocidad Google Core</li>
          <li>Integración de herramientas de IA</li>
          <li>Soporte directo con los fundadores</li>
        </ul>
        <a href="#contact" class="btn btn-glow" style="display: block;">Quiero mi Web Ahora</a>
      </div>
    </section>

    <section id="contact" class="contact-area">
      <h2>¿Hablamos de tu <span>Idea?</span></h2>
      <p style="color: var(--text-gray); margin-bottom: 50px; font-size: 1.3rem;">Estamos listos para dar vida a tu próximo gran proyecto.</p>
      <a href="mailto:hola@katax.com" class="contact-link">hola@katax.com</a>
      <div style="margin-top: 40px; font-weight: 700; color: var(--text-gray);">MEX · +52 999 528 9854</div>
    </section>
  </main>

  <footer>
    <div>© 2026 kataX Studio · Crafted with Precision.</div>
    <div class="logo" style="font-size: 1rem;">kataX</div>
  </footer>

  <script>
    // Script mejorado para revelación de secciones
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) entry.target.classList.add('visible');
      });
    }, { threshold: 0.15 });

    document.querySelectorAll('section').forEach(section => observer.observe(section));
  </script>

</body>
</html>


