<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Personal Branding Website</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #0a0f2c, #001f3f, #004080);
      color: #fff;
      scroll-behavior: smooth;
    }

    header {
      position: fixed;
      top: 0;
      width: 100%;
      background: rgba(0, 0, 0, 0.85);
      padding: 15px 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 1000;
    }

    header h1 {
      font-size: 1.2rem;
      color: #4da6ff;
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 20px;
    }

    nav a {
      text-decoration: none;
      color: #fff;
      font-weight: 500;
      transition: color 0.3s;
    }

    nav a:hover {
      color: #4da6ff;
    }

    section {
      padding: 100px 20px 60px;
      text-align: center;
    }

    h2 {
      font-size: 2rem;
      margin-bottom: 30px;
      color: #4da6ff;
    }

    /* ABOUT */
    .profile-card {
      width: 200px;
      height: 200px;
      margin: 0 auto;
      border-radius: 70%;
      overflow: hidden;
      border: 3px solid #4da6ff;
      transition: transform 0.4s, box-shadow 0.4s;
    }

    .profile-card img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .profile-card:hover {
      transform: scale(1.08);
      box-shadow: 0 0 25px #4da6ff;
    }

    .typing {
      margin: 40px 0;
      font-size: 1.3rem;
      color: #4da6ff;
      min-height: 30px;
    }

    .about-desc {
      max-width: 600px;
      margin: 20px auto;
      font-size: 1rem;
      line-height: 1.5;
    }

    /* SKILLS */
    .skills {
      max-width: 700px;
      margin: auto;
      display: flex;
      flex-direction: column;
      gap: 60px;
    }

    .skill-card {
      background: rgba(255,255,255,0.05);
      border-radius: 20px;
      padding: 30px;
      border: 2px solid transparent;
      transition: 0.4s;
    }

    .skill-card:hover {
      border-color: #4da6ff;
      box-shadow: 0 0 20px #4da6ff55;
    }

    .skill-card h3 {
      margin-bottom: 20px;
    }

    .progress-bar {
      background: #111;
      border-radius: 10px;
      height: 14px;
      overflow: hidden;
      margin-bottom: 10px;
    }

    .progress {
      height: 100%;
      background: linear-gradient(90deg, #1e90ff, #00bfff);
      width: 0;
      transition: width 1.2s;
    }

    .skill-desc {
      display: none;
      font-size: 0.9rem;
    }

    .skill-card:hover .skill-desc {
      display: block;
    }

    /* PORTOFOLIO */
    .portofolio {
      display: flex;
      justify-content: center;
      gap: 30px;
      flex-wrap: wrap;
    }

    .portofolio-card {
      width: 300px;
      height: 400px;
      background: rgba(255,255,255,0.05);
      border-radius: 22px;
      overflow: hidden;
      position: relative;
      border: 2px solid transparent;
      transition: 0.4s;
    }

    .portofolio-card img {
      width: 75%;
      height: 75%;
      object-fit: cover;
      transition: opacity 0.4s;
    }

    .portofolio-card:hover {
      border-color: #4da6ff;
      box-shadow: 0 0 20px #4da6ff55;
    }

    .portofolio-card:hover img {
      opacity: 0.4;
    }

    .portofolio-desc {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      opacity: 0;
      transition: 0.4s;
      color: #fff;
      font-size: 3rem;
      text-align: center;
      padding: 10px;
    }

    .portofolio-card:hover .portofolio-desc {
      opacity: 1;
    }

    /* CONTACT */
    .contact-desc {
      margin-bottom: 60px;
    }

    .social-icons {
      display: flex;
      justify-content: center;
      gap: 40px;
    }

    .social-icons a {
      font-size: 3rem;
      color: #fff;
      transition: transform 0.3s, filter 0.3s;
      position: relative;
    }

    .social-icons a:hover {
      transform: scale(1.2);
      filter: brightness(60%);
    }

    .social-icons a span {
      position: absolute;
      bottom: 70px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 0.9rem;
      background: rgba(0,0,0,0.7);
      padding: 4px 8px;
      border-radius: 6px;
      opacity: 0;
      transition: opacity 0.3s;
      color: #4da6ff;
      white-space: nowrap;
    }

    .social-icons a:hover span {
      opacity: 1;
    }

    /* MOBILE MENU */
    .menu-toggle {
      display: none;
      flex-direction: column;
      cursor: pointer;
    }

    .menu-toggle span {
      background: #fff;
      margin: 4px 0;
      width: 25px;
      height: 3px;
    }

    @media (max-width: 768px) {
      nav ul {
        display: none;
        flex-direction: column;
        position: absolute;
        top: 70px;
        right: 60px;
        background: rgba(0,0,0,0.9);
        padding: 20px;
        border-radius: 8px;
      }

      nav ul.active {
        display: flex;
      }

      .menu-toggle {
        display: flex;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>My Profile</h1>
    <div class="menu-toggle" id="menu-toggle">
      <span></span><span></span><span></span>
    </div>
    <nav>
      <ul id="nav-links">
        <li><a href="#about">About Me</a></li>
        <li><a href="#skills">My Skills</a></li>
        <li><a href="#portofolio">Portofolio</a></li>
        <li><a href="#contact">Contact Me</a></li>
      </ul>
    </nav>
  </header>

  <!-- ABOUT -->
  <section id="about">
    <h2>ABOUT ME</h2>
    <div class="profile-card">
      <img src="Profil.jpg" alt="Profile">
    </div>
    <div class="typing" id="typing"></div>
    <p class="about-desc">Halo, saya Luthfi permata ulya seorang siswa SMK yang tertarik dan sedang menekuni bidang desain grafis dan pemrograman.</p>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <h2>MY SKILLS</h2>
    <div class="skills">
      <div class="skill-card">
        <h3>Desainer Grafis (85%)</h3>
        <div class="progress-bar"><div class="progress" style="width:85%"></div></div>
        <p class="skill-desc">Membuat poster di Canva, poster publik, dan infografis.</p>
      </div>
      <div class="skill-card">
        <h3>Flat Designer (70%)</h3>
        <div class="progress-bar"><div class="progress" style="width:70%"></div></div>
        <p class="skill-desc">Membuat karakter dan elemen sederhana.</p>
      </div>
    </div>
  </section>

  <!-- PORTOFOLIO -->
  <section id="portofolio">
    <h2>PORTOFOLIO</h2>
    <div class="portofolio">
      <div class="portofolio-card">
        <img src= "Poster publik.jpg"
        alt="Poster publik">
        <class="portofolio-desc">
        <p>Peringkat 50 besar poster publik dalam event OU Festival</p>
      </div>
      <div class="portofolio-card">
        <img src="Infografis.jpg"
        alt="Poster infografis">
        <class="portofolio-desc">
        <p>Juara terfavorit dalam lomba poster infografis</p>
      </div>
    </div>
  </section>
  
  <!-- CONTACT -->
<section id="contact">
  <h2>CONTACT ME</h2>
  <p class="contact-desc">Ingin kerja sama dan kolaborasi? atau memiliki kritik dan saran. Hubungi saya melalui media sosial berikut:</p>
  <div class="social-icons">
    <a href="javascript:void(0)"><i class="fab fa-tiktok"></i><span>@permataulya_</span></a>
    <a href="javascript:void(0)"><i class="fab fa-instagram"></i><span>@permataulya_</span></a>
    <a href="javascript:void(0)"><i class="fab fa-whatsapp"></i><span>+62-896-3093-8863</span></a>
  </div>
</section>

  <script>
    // Typing animation
    const texts = ["Student", "Desainer Grafis", "Flat Designer"];
    let index = 0;
    let charIndex = 0;
    const typingEl = document.getElementById("typing");

    function type() {
      if (charIndex < texts[index].length) {
        typingEl.innerHTML += texts[index].charAt(charIndex);
        charIndex++;
        setTimeout(type, 100);
      } else {
        setTimeout(erase, 2000);
      }
    }

    function erase() {
      if (charIndex > 0) {
        typingEl.innerHTML = texts[index].substring(0, charIndex - 1);
        charIndex--;
        setTimeout(erase, 50);
      } else {
        index = (index + 1) % texts.length;
        setTimeout(type, 500);
      }
    }

    document.addEventListener("DOMContentLoaded", () => {
      type();
    });

    // Mobile menu
    const menuToggle = document.getElementById("menu-toggle");
    const navLinks = document.getElementById("nav-links");
    menuToggle.addEventListener("click", () => {
      navLinks.classList.toggle("active");
    });
  </script>
</body>
</html>
