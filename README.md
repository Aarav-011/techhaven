# techhaven
🌐 Aarav's interactive portfolio features a dark mode toggle, animated sections, and a multilingual welcome modal with speech synthesis. It showcases projects like a periodic table game and a reminder box, and includes a contact form and social media links—all styled with smooth transitions and a modern UI.

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>🌟 Aarav's Portfolio</title>
  <link rel="icon" href="https://cdn-icons-png.flaticon.com/512/3135/3135715.png" type="image/png">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" integrity="sha512-b7Hz3...x" crossorigin="anonymous" referrerpolicy="no-referrer" />
  <style>
    /* Add your existing styles here */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
    scroll-behavior: smooth;
    }


    body {
      font-family: 'Segoe UI', sans-serif;
      color: #333;
      transition: background-color 0.4s, color 0.4s;
      position: relative;
      background-color: #fff;
      overflow-x: hidden;
    }

    body::before {
      content: '';
      position: fixed;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle at 30% 30%, rgba(255, 99, 71, 0.4), transparent 70%),
                  radial-gradient(circle at 70% 70%, rgba(255, 165, 0, 0.3), transparent 70%);
      animation: moveBlur 20s infinite linear;
      z-index: -1;
      filter: blur(80px);
    }

    @keyframes moveBlur {
      0% { transform: translate(0, 0); }
      50% { transform: translate(50px, -50px); }
      100% { transform: translate(0, 0); }
    }

    body.dark-mode {
      background-color: #121212;
      color: #e0e0e0;
    }

    body.dark-mode::before {
      background: radial-gradient(circle at 30% 30%, rgba(0, 128, 255, 0.25), transparent 70%),
                  radial-gradient(circle at 70% 70%, rgba(138, 43, 226, 0.2), transparent 70%);
    }

    .dark-mode-toggle {
    position: fixed;
    top: 20px;
    right: 20px;
    padding: 10px 20px;
    background: #ff6347;
    color: white;
    border-radius: 8px;
    cursor: pointer;
    font-weight: bold;
    z-index: 10;
    box-shadow: 0 0 12px rgba(255, 99, 71, 0.5);
    user-select: none;
    }

    .dark-mode-toggle:hover {
    transform: scale(1.08);
    background: #ff826e;
    box-shadow: 0 0 20px rgba(255, 99, 71, 0.8);
    }


    header {
      height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
    }

    header h1 {
      font-size: 3rem;
      text-shadow: 2px 2px 10px rgba(0,0,0,0.5);
    }

    header p {
      font-size: 1.5rem;
      margin: 20px 0;
    }

    .hero-btn {
      padding: 12px 24px;
      background: #ff6347;
      border: none;
      color: white;
      font-size: 1rem;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.4s ease-in-out;
      box-shadow: 0 0 12px rgba(255, 99, 71, 0.5);
    }

    .hero-btn:hover {
      transform: scale(1.08);
      background: #ff826e;
      box-shadow: 0 0 20px rgba(255, 99, 71, 0.8);
    }

    section {
      padding: 60px 20px;
      text-align: center;
    }

    section h1 {
      font-size: 2rem;
      margin-bottom: 20px;
    }

    section p {
      max-width: 800px;
      margin: auto;
      line-height: 1.8;
      font-size: 1.1rem;
    }

    .projects-container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      margin-top: 40px;
    }

    .project-card {
      background: rgba(255, 255, 255, 0.8);
      padding: 20px;
      width: 320px;
      border-radius: 12px;
      box-shadow: 0 4px 16px rgba(0,0,0,0.1);
      transition: all 0.3s ease;
      backdrop-filter: blur(10px);
    }

    .project-card:hover {
      transform: translateY(-10px) scale(1.05);
      box-shadow: 0 0 20px rgba(255, 99, 71, 0.6);
    }

    .project-card img {
      max-width: 100%;
      border-radius: 8px;
    }

    .project-card h3 {
      margin: 10px 0;
    }

    .project-card a {
      color: #ff6347;
      text-decoration: none;
      font-weight: bold;
      display: inline-block;
      margin-top: 10px;
    }

    form {
      max-width: 600px;
      margin: auto;
      display: flex;
      flex-direction: column;
      gap: 15px;
    }

    input, textarea {
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 1rem;
    }

    form button {
      padding: 12px;
      background: #ff6347;
      color: white;
      border: none;
      border-radius: 6px;
      font-size: 1rem;
      cursor: pointer;
    }

    footer {
      background: #333;
      color: white;
      text-align: center;
      padding: 20px 0;
      font-size: 0.9rem;
    }

    footer .social-icons {
      margin-top: 10px;
    }

    footer .social-icons a {
      color: #ff6347;
      margin: 0 10px;
      font-size: 1.4rem;
      text-decoration: none;
    }

    .hidden-section {
      opacity: 0;
      transform: translateY(50px);
      transition: opacity 0.6s ease-out, transform 0.6s ease-out;
    }

    .white-link {
    color: red;
    }

    .visible-section {
      opacity: 1;
      transform: translateY(0);
    }
    #welcomeModal {
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100vw;
    background: rgba(0,0,0,0.6);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
    }

    .modal-content {
    background: #fff;
    padding: 30px;
    border-radius: 12px;
    text-align: center;
    max-width: 400px;
    width: 90%;
    box-shadow: 0 0 20px rgba(0,0,0,0.3);
    }

    .modal-content input,
    .modal-content select,
    .modal-content button {
    width: 100%;
    padding: 10px;
    margin: 12px 0;
    font-size: 1rem;
    }


    /* Dark mode styles */
    body.dark-mode header,
    body.dark-mode section,
    body.dark-mode form,
    body.dark-mode .project-card {
      background-color: rgba(30, 30, 30, 0.6);
      color: #e0e0e0;
    }

    body.dark-mode footer {
      background-color: #0d0d0d;
      color: #aaa;
    }

    body.dark-mode .project-card {
      background: rgba(40, 40, 40, 0.85);
      border: 1px solid #444;
    }

    body.dark-mode input,
    body.dark-mode textarea {
      background-color: #1f1f1f;
      color: #eee;
      border: 1px solid #555;
    }

    body.dark-mode .hero-btn,
    body.dark-mode .dark-mode-toggle,
    body.dark-mode form button {
      background: #1a73e8;
      box-shadow: 0 0 12px rgba(26, 115, 232, 0.6);
    }

    body.dark-mode .hero-btn:hover,
    body.dark-mode .dark-mode-toggle:hover,
    body.dark-mode form button:hover {
      background: #4285f4;
      box-shadow: 0 0 20px rgba(66, 133, 244, 0.8);
    }
  </style>
</head>
<body>

    <span class="dark-mode-toggle" onclick="toggleDarkMode()">🌙 Dark Mode</span>

  <header>
    <h1><i class="fas fa-laptop-code"></i> Welcome to My Portfolio</h1>
    <p><i class="fas fa-user-astronaut"></i> I'm a passionate Developer and Designer</p>
    <a href="#about" class="hero-btn">Explore More</a>
  </header>

  <section id="about" class="hidden-section">
    <h1><i class="fas fa-info-circle"></i> About Me</h1>
    <p>
      I'm a passionate and creative web developer dedicated to crafting seamless, user-friendly digital experiences. With a strong foundation in front-end technologies like HTML, CSS, and JavaScript, I specialize in building visually compelling and highly interactive web applications. My work combines clean code with thoughtful design, ensuring responsive and accessible interfaces across all devices. I also enjoy sharing my knowledge and creativity through <a href="https://www.youtube.com/@aaravrughani9641" target="_blank" rel="noopener noreferrer" class="white-link">My YouTube Channel</a>, where I post tutorials, coding projects, and tech-related content to help and inspire others. Whether it's developing educational games, portfolio sites, or real-world applications, I thrive on turning ideas into engaging digital solutions.
    </p>
  </section>

  <section id="projects" class="hidden-section">
    <h1><i class="fas fa-folder-open"></i> My Projects</h1>
    <div class="projects-container">
      <div class="project-card">
        <img src="https://via.placeholder.com/300" alt="Reminder Box">
        <h3>Reminder Box</h3>
        <p>Hardware system reminding users to take medicine or drink water on time.</p>
        <!-- <a href="#"><i class="fas fa-microchip"></i> View Project</a> -->
        <a>Upcoming</a>
      </div>

      <div class="project-card">
        <img src="https://via.placeholder.com/300" alt="Periodic Table Game">
        <h3>Periodic Table Game</h3>
        <p>Drag-and-drop game for placing elements in correct boxes. Educational & fun.</p>
        <a href="#"><i class="fas fa-atom"></i> Play Game</a>
      </div>

      <div class="project-card">
        <img src="https://via.placeholder.com/300" alt="Hangman Game">
        <h3>Hangman Game</h3>
        <p>Guess the word in 6 attempts. Boost your vocabulary in a fun way.</p>
        <a href="#"><i class="fas fa-gamepad"></i> Play Game</a>
      </div>
    </div>
  </section>

  <section id="contact" class="hidden-section">
    <h1><i class="fas fa-envelope"></i> Contact Me</h1>
    <form>
      <input type="text" name="name" placeholder="Your Name" required>
      <input type="email" name="email" placeholder="Your Email" required>
      <textarea rows="4" name="message" placeholder="Your Message" required></textarea>
      <button type="submit"><i class="fas fa-paper-plane"></i> Send Message</button>
    </form>
  </section>

  <footer>
    <p>&copy; 2025 Aarav Rughani. All rights reserved.</p>
    <div class="social-icons">
      <a href="#"><i class="fab fa-github"></i></a>
      <a href="#"><i class="fab fa-linkedin"></i></a>
      <a href="#"><i class="fab fa-twitter"></i></a>
    </div>
  </footer>

  <!-- 🔻 Welcome Modal (outside the project section) -->
  <div id="welcomeModal" style="display: flex;">
    <div class="modal-content">
      <h2>Welcome!</h2>
      <label for="username">Your Name:</label>
      <input type="text" id="username" placeholder="Enter your name" required>
      <label for="language">Preferred Language:</label>
      <select id="language">
        <option value="en-US">English</option>
        <option value="hi-IN">Hindi</option>
        <option value="es-ES">Spanish</option>
        <option value="fr-FR">French</option>
        <option value="de-DE">German</option>
      </select>
      <button onclick="submitWelcome()">Continue</button>
    </div>
  </div>

  <!-- 🔻 JavaScript -->
  <script>
    const greetings = {
    "en-US": "Good {time}, {name}! Welcome to my portfolio.",
    "hi-IN": "नमस्ते {name}! मेरे पोर्टफोलियो में आपका स्वागत है।",
    "es-ES": "¡Buen{time}, {name}! Bienvenido a mi portafolio.",
    "fr-FR": "Bonjour {name} ! Bon{time} et bienvenue sur mon portfolio.",
    "de-DE": "Guten {time}, {name}! Willkommen in meinem Portfolio."
    };


    function getTimeOfDay() {
      const hour = new Date().getHours();
      if (hour < 12) return "morning";
      if (hour < 18) return "afternoon";
      return "evening";
    }

    function speakGreeting(name, lang) {
      const time = getTimeOfDay();
      const greetingTemplate = greetings[lang] || greetings["en-US"];
      const message = greetingTemplate.replace("{name}", name).replace("{time}", time);
      const utterance = new SpeechSynthesisUtterance(message);
      utterance.lang = lang;
      speechSynthesis.speak(utterance);
    }

    function submitWelcome() {
      const name = document.getElementById("username").value || "Friend";
      const lang = document.getElementById("language").value || "en-US";
      sessionStorage.setItem("userName", name);
      sessionStorage.setItem("userLang", lang);
      document.getElementById("welcomeModal").style.display = "none";
      speakGreeting(name, lang);
    }

    window.addEventListener("DOMContentLoaded", () => {
      // Always show modal on new visit
      document.getElementById("welcomeModal").style.display = "flex";
    });

    window.addEventListener("beforeunload", () => {
      const goodbye = new SpeechSynthesisUtterance("Goodbye, thanks for visiting!");
      speechSynthesis.speak(goodbye);
    });

    function toggleDarkMode() {
    document.body.classList.toggle('dark-mode');
    const toggle = document.querySelector('.dark-mode-toggle');
    const isDark = document.body.classList.contains('dark-mode');
    toggle.textContent = isDark ? '☀️ Light Mode' : '🌙 Dark Mode';
    }


    document.querySelector(".hero-btn").addEventListener("click", function () {
      document.querySelector("#about").scrollIntoView({ behavior: "smooth" });
    });

    const sections = document.querySelectorAll(".hidden-section");
    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add("visible-section");
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1 });

    sections.forEach(section => observer.observe(section));
  </script>
</body>
</html>
