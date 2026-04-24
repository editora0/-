<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>editor_a0</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary-color: #6a11cb;
      --secondary-color: #2575fc;
      --accent-color: #ff4d4d;
      --dark-color: #1a1a2e;
      --light-color: #f8f9fa;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background: linear-gradient(135deg, var(--dark-color), #16213e);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      color: var(--light-color);
      overflow-x: hidden;
    }

    .container {
      width: 90%;
      max-width: 1200px;
      position: relative;
      z-index: 1;
    }

    .glass-panel {
      background: rgba(255, 255, 255, .05);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(15px);
      border-radius: 20px;
      border: 1px solid rgba(255, 255, 255, .1);
      box-shadow: 0 25px 45px rgba(0, 0, 0, .2);
      padding: 40px;
      position: relative;
      overflow: hidden;
    }

    .glass-panel::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: linear-gradient(to bottom right, rgba(106, 17, 203, .1), rgba(37, 117, 252, .1), rgba(255, 77, 77, .1));
      transform: rotate(30deg);
      z-index: -1;
      animation: shine 8s infinite linear;
    }

    @keyframes shine {
      0% { transform: rotate(30deg) translate(-10%, -10%); }
      50% { transform: rotate(30deg) translate(10%, 10%); }
      100% { transform: rotate(30deg) translate(-10%, -10%); }
    }

    .header {
      text-align: center;
      margin-bottom: 50px;
      position: relative;
    }

    .logo {
      width: 150px;
      height: 150px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 0 auto 20px;
      box-shadow: 0 10px 30px rgba(106, 17, 203, .5);
      border: 3px solid rgba(255, 255, 255, .2);
      position: relative;
      overflow: hidden;
      background-color: transparent;
    }

    .logo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 50%;
    }

    .logo::after {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: linear-gradient(to bottom right, transparent, rgba(255, 255, 255, .2), transparent);
      transform: rotate(30deg);
      animation: shineLogo 6s infinite linear;
    }

    @keyframes shineLogo {
      0% { transform: rotate(30deg) translate(-30%, -30%); }
      100% { transform: rotate(30deg) translate(30%, 30%); }
    }

    .header h1 {
      font-size: 2.5rem;
      margin-bottom: 10px;
      background: linear-gradient(to right, #fff, #ccc);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 0 2px 10px rgba(0, 0, 0, .2);
    }

    .social-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 25px;
      margin-bottom: 40px;
    }

    .social-card {
      background: rgba(255, 255, 255, .05);
      border-radius: 15px;
      padding: 25px;
      text-align: center;
      transition: all .3s ease;
      border: 1px solid rgba(255, 255, 255, .1);
      position: relative;
      overflow: hidden;
      cursor: pointer;
    }

    .social-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 15px 30px rgba(0, 0, 0, .3);
      background: rgba(255, 255, 255, .1);
      border-color: rgba(255, 255, 255, .3);
    }

    .social-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 5px;
      background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
    }

    .social-card i {
      font-size: 2.5rem;
      margin-bottom: 15px;
      background: linear-gradient(to bottom right, var(--primary-color), var(--secondary-color));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .social-card h3 {
      font-size: 1.3rem;
      margin-bottom: 10px;
    }

    .channel-card {
      background: linear-gradient(to right, rgba(106, 17, 203, .2), rgba(37, 117, 252, .2));
      border: 2px solid rgba(255, 255, 255, .3);
    }

    .particles {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      overflow: hidden;
    }

    .particle {
      position: absolute;
      background: rgba(255, 255, 255, .5);
      border-radius: 50%;
      animation: float linear infinite;
    }

    @keyframes float {
      0% { transform: translateY(0) rotate(0); }
      100% { transform: translateY(-1000px) rotate(720deg); }
    }

    @media (max-width: 768px) {
      .glass-panel { padding: 25px; }
      .header h1 { font-size: 2rem; }
      .social-grid { grid-template-columns: 1fr; }
    }

    .notification {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background: rgba(0, 0, 0, .7);
      color: #fff;
      padding: 15px 25px;
      border-radius: 10px;
      z-index: 1000;
      display: none;
      animation: fadeIn .5s;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .ad-popup {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.8);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
    }

    .ad-popup.active {
      opacity: 1;
      visibility: visible;
    }

    .ad-content {
      background: linear-gradient(145deg, rgba(106, 17, 203, 0.7), rgba(37, 117, 252, 0.7));
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border-radius: 20px;
      padding: 2rem;
      width: 90%;
      max-width: 400px;
      text-align: center;
      position: relative;
      box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5), 0 0 20px rgba(106, 17, 203, 0.5), inset 0 0 30px rgba(255, 255, 255, 0.1);
      border: 2px solid rgba(255, 255, 255, 0.2);
    }

    .ad-close {
      position: absolute;
      top: 10px;
      left: 10px;
      background: #ff4d4d;
      color: white;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      font-weight: bold;
      opacity: 0.7;
      transition: opacity 0.3s;
    }

    .ad-close:hover {
      opacity: 1;
    }

    .ad-image {
      width: 100%;
      border-radius: 10px;
      margin: 15px 0;
      max-height: 200px;
      object-fit: cover;
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    .ad-btn {
      background: linear-gradient(145deg, var(--primary-color), var(--secondary-color));
      color: #fff;
      border: none;
      padding: 12px 25px;
      border-radius: 15px;
      cursor: pointer;
      font-family: inherit;
      font-weight: 700;
      font-size: 1rem;
      transition: all .3s ease;
      margin-top: 15px;
      display: inline-flex;
      align-items: center;
      gap: 10px;
      box-shadow: 0 8px 25px rgba(106, 17, 203, 0.5), inset 0 0 15px rgba(255, 255, 255, 0.1);
      border: 2px solid rgba(255, 255, 255, 0.2);
      letter-spacing: 1px;
    }

    .ad-btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 12px 35px rgba(106, 17, 203, 0.7), 0 0 20px rgba(37, 117, 252, 0.5), inset 0 0 15px rgba(255, 255, 255, 0.1);
    }
  </style>
</head>
<body>
  <div class="ad-popup" id="adPopup">
    <div class="ad-content">
      <div class="ad-close" id="adClose">✕</div>
      <h2>تبلیغ شما</h2>
      <img src="https://i.supaimg.com/993c43ad-19ad-46fd-bb62-4673f3dd5a80.jpg" alt="1000043218" class="ad-image" />
      <p>توضیحات تبلیغ شما</p>
      <button class="ad-btn" id="viewTelegramBtn">
        <i class="fab fa-telegram"></i> ثبت تبلیغ 
      </button>
    </div>
  </div>

  <div class="particles" id="particles"></div>
  <div class="notification" id="notification"></div>
  <div class="container">
    <div class="glass-panel">
      <div class="header">
        <div class="logo"><img src="https://i.ibb.co/7xZF6pGq/profile-pic.jpg" alt="پروفایل editor_a0"></div>
        <h1>editor_a0</h1>
      </div>
      <div class="social-grid">
        <div class="social-card channel-card" onclick='window.open("https://t.me/editor_a0","_blank")'>
          <i class="fab fa-telegram"></i>
          <h3>چنل اصلی</h3>
          <p>Telegram Channel</p>
        </div>
        <div class="social-card" onclick='window.open("https://www.tiktok.com/@editor_a0_tiktok?_t=ZS-8z7ZOItCCMq&_r=1","_blank")'>
          <i class="fab fa-tiktok"></i>
          <h3>TikTok</h3>
          <p>تمپلیت ها</p>
        </div>
        <div class="social-card" onclick='window.open("https://www.instagram.com/editor_a0.official?igsh=MWRib2c4aHFpN2Jtdg==","_blank")'>
          <i class="fab fa-instagram"></i>
          <h3>Instagram</h3>
          <p>صفحه رسمی</p>
        </div>
        <div class="social-card" onclick='window.open("https://youtube.com/@editor_a0-e7f?si=WEEIaFtOm00vZUlh","_blank")'>
          <i class="fab fa-youtube"></i>
          <h3>YouTube</h3>
          <p>کانال رسمی</p>
        </div>
        <div class="social-card" onclick='window.open("https://www.twitch.tv/editor_a0","_blank")'>
          <i class="fab fa-twitch"></i>
          <h3>Twitch</h3>
          <p>استریم روم‌ها</p>
        </div>
        <div class="social-card" onclick='window.open("https://t.me/NetliVPN","_blank")'>
          <i class="fas fa-shield-alt"></i>
          <h3>چنل VPN</h3>
          <p>NetliVPN</p>
        </div>
        <div class="social-card" onclick='window.open("https://pubg-id.netlify.app","_blank")'>
          <i class="fas fa-gamepad"></i>
          <h3>PUBG ID</h3>
          <p>آیدی پابجی من</p>
        </div>
      </div>
    </div>
  </div>
  <script>
    function showAdPopup() {
      const adPopup = document.getElementById('adPopup');
      adPopup.classList.add('active');
    }

    function closeAdPopup() {
      const adPopup = document.getElementById('adPopup');
      adPopup.classList.remove('active');
    }

    document.getElementById('adClose').addEventListener('click', closeAdPopup);
    document.getElementById('viewTelegramBtn').addEventListener('click', () => {
      window.open('https://t.me/editor_a0_ADM', '_blank');
      closeAdPopup();
    });

    function createParticles() {
      const particlesContainer = document.getElementById('particles');
      const particleCount = 30;
      
      for (let i = 0; i < particleCount; i++) {
        const particle = document.createElement('div');
        particle.classList.add('particle');
        
        const size = Math.random() * 2 + 1;
        particle.style.width = `${size}px`;
        particle.style.height = `${size}px`;
        
        particle.style.left = `${Math.random() * 100}%`;
        particle.style.top = `${Math.random() * 100}%`;
        
        particle.style.opacity = Math.random() * 0.5 + 0.1;
        
        const duration = Math.random() * 20 + 10;
        particle.style.animationDuration = `${duration}s`;
        
        particle.style.animationDelay = `${Math.random() * 10}s`;
        
        particlesContainer.appendChild(particle);
      }
    }

    function showNotification(message) {
      const notification = document.getElementById('notification');
      notification.textContent = message;
      notification.style.display = 'block';
      setTimeout(() => {
        notification.style.display = 'none';
      }, 3000);
    }

    window.addEventListener('load', () => {
      createParticles();
      showNotification('روی کارت مربوط به هر پلتفرم کلیک کنید');
      setTimeout(showAdPopup, 1000);
    });
  </script>
</body>
</html>
