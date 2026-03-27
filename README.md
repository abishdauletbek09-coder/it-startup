!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Manrope:wght@300;400;500;700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --bg: #050a0f;
    --bg2: #0a1520;
    --bg3: #0f1e2d;
    --accent: #00d4ff;
    --accent2: #00ff88;
    --text: #e8f4ff;
    --muted: #6a8aaa;
    --border: rgba(0,212,255,0.15);
    --card-bg: rgba(10,21,32,0.8);
  }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'Manrope', sans-serif;
    background: var(--bg);
    color: var(--text);
    overflow-x: hidden;
  }
  /* NAV */
  nav {
    position: fixed; top: 0; width: 100%; z-index: 100;
    padding: 1.2rem 3rem;
    display: flex; align-items: center; justify-content: space-between;
    background: rgba(5,10,15,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }
  .logo {
    font-family: 'Space Mono', monospace;
    font-size: 1.3rem; font-weight: 700;
    color: var(--accent);
    letter-spacing: -0.02em;
  }
  .logo span { color: var(--accent2); }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    text-decoration: none; color: var(--muted);
    font-size: 0.85rem; font-weight: 500; letter-spacing: 0.05em;
    text-transform: uppercase; transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--accent); }
  .nav-cta {
    background: transparent; border: 1px solid var(--accent);
    color: var(--accent); padding: 0.5rem 1.4rem;
    border-radius: 4px; cursor: pointer; font-family: 'Space Mono', monospace;
    font-size: 0.8rem; transition: all 0.2s;
  }
  .nav-cta:hover { background: var(--accent); color: var(--bg); }

 
  .hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 8rem 3rem 4rem;
    position: relative; overflow: hidden;
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 40%, transparent 100%);
  }
  .hero-glow {
    position: absolute; top: 10%; right: -5%;
    width: 600px; height: 600px; border-radius: 50%;
    background: radial-gradient(circle, rgba(0,212,255,0.06) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-glow2 {
    position: absolute; bottom: 5%; left: -10%;
    width: 400px; height: 400px; border-radius: 50%;
    background: radial-gradient(circle, rgba(0,255,136,0.05) 0%, transparent 70%);
  }
  .hero-content { position: relative; max-width: 760px; }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(0,212,255,0.08); border: 1px solid rgba(0,212,255,0.2);
    border-radius: 100px; padding: 0.4rem 1rem;
    font-size: 0.78rem; color: var(--accent); margin-bottom: 2rem;
    font-family: 'Space Mono', monospace;
  }
  .hero-badge::before { content: ''; width: 6px; height: 6px; background: var(--accent2); border-radius: 50%; animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.5;transform:scale(1.3)} }
  .hero h1 {
    font-size: clamp(2.8rem, 6vw, 5rem);
    font-weight: 800; line-height: 1.05;
    letter-spacing: -0.03em; margin-bottom: 1.5rem;
  }
  .hero h1 .line2 { color: var(--accent); }
  .hero p {
    font-size: 1.15rem; color: var(--muted); line-height: 1.7;
    max-width: 560px; margin-bottom: 2.5rem; font-weight: 300;
  }
  .hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; }
  .btn-primary {
    background: var(--accent); color: var(--bg);
    border: none; padding: 0.9rem 2rem;
    border-radius: 4px; cursor: pointer;
    font-family: 'Space Mono', monospace; font-size: 0.85rem; font-weight: 700;
    transition: all 0.2s; letter-spacing: 0.03em;
  }
  .btn-primary:hover { background: var(--accent2); transform: translateY(-2px); }
  .btn-outline {
    background: transparent; color: var(--text);
    border: 1px solid rgba(255,255,255,0.2); padding: 0.9rem 2rem;
    border-radius: 4px; cursor: pointer;
    font-family: 'Space Mono', monospace; font-size: 0.85rem;
    transition: all 0.2s;
  }
  .btn-outline:hover { border-color: var(--accent); color: var(--accent); }
  .hero-stats {
    display: flex; gap: 3rem; margin-top: 4rem;
    padding-top: 2rem; border-top: 1px solid var(--border);
  }
  .stat-val { font-family: 'Space Mono', monospace; font-size: 2rem; font-weight: 700; color: var(--accent); }
  .stat-lbl { font-size: 0.8rem; color: var(--muted); margin-top: 4px; }

  section { padding: 5rem 3rem; }
  .section-label {
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    color: var(--accent); letter-spacing: 0.15em; text-transform: uppercase;
    margin-bottom: 1rem;
  }
  .section-title {
    font-size: clamp(1.8rem, 3.5vw, 2.8rem); font-weight: 800;
    line-height: 1.1; letter-spacing: -0.02em; margin-bottom: 1rem;
  }
  .section-sub { font-size: 1rem; color: var(--muted); max-width: 500px; line-height: 1.7; }

  
  .services { background: var(--bg2); }
  .services-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5px; margin-top: 3rem;
    border: 1.5px solid var(--border); border-radius: 12px; overflow: hidden;
  }
  .service-card {
    background: var(--card-bg); padding: 2rem;
    transition: background 0.2s; cursor: pointer; position: relative;
  }
  .service-card:hover { background: rgba(0,212,255,0.06); }
  .service-icon {
    width: 44px; height: 44px; border-radius: 8px;
    background: rgba(0,212,255,0.1); border: 1px solid rgba(0,212,255,0.2);
    display: flex; align-items: center; justify-content: center;
    margin-bottom: 1.2rem; font-size: 1.2rem;
  }
  .service-card h3 { font-size: 1rem; font-weight: 700; margin-bottom: 0.6rem; }
  .service-card p { font-size: 0.85rem; color: var(--muted); line-height: 1.6; }
  .service-arrow {
    position: absolute; top: 1.5rem; right: 1.5rem;
    color: var(--border); font-size: 1.2rem; transition: color 0.2s, transform 0.2s;
  }
  .service-card:hover .service-arrow { color: var(--accent); transform: translate(3px,-3px); }

  
  .how { background: var(--bg); }
  .steps { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 2rem; margin-top: 3rem; }
  .step { position: relative; }
  .step-num {
    font-family: 'Space Mono', monospace; font-size: 3.5rem; font-weight: 700;
    color: rgba(0,212,255,0.1); line-height: 1; margin-bottom: 1rem;
  }
  .step h3 { font-size: 1rem; font-weight: 700; margin-bottom: 0.5rem; }
  .step p { font-size: 0.85rem; color: var(--muted); line-height: 1.6; }
  .step-line {
    position: absolute; top: 2rem; right: -1rem; width: 2rem;
    border-top: 1px dashed rgba(0,212,255,0.3);
  }

 
  .pricing { background: var(--bg3); }
  .pricing-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 1.5rem; margin-top: 3rem; }
  .price-card {
    background: var(--card-bg); border: 1px solid var(--border);
    border-radius: 12px; padding: 2rem; transition: border-color 0.2s;
  }
  .price-card.featured { border-color: var(--accent); position: relative; }
  .price-card.featured::before {
    content: 'Популярный';
    position: absolute; top: -12px; left: 50%; transform: translateX(-50%);
    background: var(--accent); color: var(--bg);
    font-family: 'Space Mono', monospace; font-size: 0.7rem;
    padding: 3px 12px; border-radius: 100px;
  }
  .price-plan { font-size: 0.75rem; color: var(--accent); font-family: 'Space Mono', monospace; letter-spacing: 0.1em; margin-bottom: 1rem; }
  .price-val { font-size: 2.5rem; font-weight: 800; letter-spacing: -0.03em; }
  .price-val span { font-size: 1rem; font-weight: 400; color: var(--muted); }
  .price-desc { font-size: 0.85rem; color: var(--muted); margin: 0.5rem 0 1.5rem; line-height: 1.5; }
  .price-features { list-style: none; display: flex; flex-direction: column; gap: 0.6rem; margin-bottom: 2rem; }
  .price-features li { font-size: 0.85rem; display: flex; align-items: center; gap: 8px; }
  .price-features li::before { content: ''; width: 5px; height: 5px; background: var(--accent2); border-radius: 50%; flex-shrink: 0; }
  .price-btn {
    width: 100%; padding: 0.75rem; border-radius: 4px; cursor: pointer;
    font-family: 'Space Mono', monospace; font-size: 0.8rem; font-weight: 700;
    border: 1px solid var(--accent); background: transparent; color: var(--accent);
    transition: all 0.2s;
  }
  .price-card.featured .price-btn { background: var(--accent); color: var(--bg); }
  .price-btn:hover { background: var(--accent); color: var(--bg); }

 
  .contact { background: var(--bg2); }
  .contact-wrap { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start; }
  .contact-info h2 { font-size: 2.2rem; font-weight: 800; margin-bottom: 1rem; }
  .contact-info p { color: var(--muted); line-height: 1.7; margin-bottom: 2rem; }
  .contact-links { display: flex; flex-direction: column; gap: 1rem; }
  .contact-link { display: flex; align-items: center; gap: 12px; font-size: 0.9rem; color: var(--muted); text-decoration: none; }
  .contact-link:hover { color: var(--accent); }
  .clink-icon { width: 36px; height: 36px; border-radius: 8px; background: rgba(0,212,255,0.08); border: 1px solid var(--border); display: flex; align-items: center; justify-content: center; font-size: 1rem; }
  .form-group { margin-bottom: 1.2rem; }
  .form-label { font-size: 0.78rem; color: var(--muted); display: block; margin-bottom: 0.4rem; font-family: 'Space Mono', monospace; letter-spacing: 0.05em; }
  .form-input {
    width: 100%; background: rgba(255,255,255,0.04); border: 1px solid var(--border);
    color: var(--text); padding: 0.75rem 1rem; border-radius: 6px;
    font-family: 'Manrope', sans-serif; font-size: 0.9rem;
    transition: border-color 0.2s; outline: none;
  }
  .form-input:focus { border-color: var(--accent); }
  .form-input::placeholder { color: var(--muted); }
  textarea.form-input { resize: vertical; min-height: 100px; }

  /* FOOTER */
  footer {
    background: var(--bg); padding: 2rem 3rem;
    border-top: 1px solid var(--border);
    display: flex; align-items: center; justify-content: space-between;
    font-size: 0.8rem; color: var(--muted);
  }
  .footer-logo { font-family: 'Space Mono', monospace; color: var(--accent); font-size: 1rem; }
  .footer-logo span { color: var(--accent2); }

  @media (max-width: 768px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { display: none; }
    section, .hero { padding: 4rem 1.5rem; }
    .hero-stats { gap: 2rem; }
    .contact-wrap { grid-template-columns: 1fr; }
    footer { flex-direction: column; gap: 1rem; text-align: center; }
  }
</style>
</head>
<body>

<nav>
  <div class="logo">Koshe<span>Web</span></div>
  <ul class="nav-links">
    <li><a href="#services">Услуги</a></li>
    <li><a href="#how">Как работаем</a></li>
    <li><a href="#pricing">Цены</a></li>
    <li><a href="#contact">Контакты</a></li>
  </ul>
  <button class="nav-cta">Обсудить проект</button>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-grid"></div>
  <div class="hero-glow"></div>
  <div class="hero-glow2"></div>
  <div class="hero-content">
    <div class="hero-badge">Работаем по всему Казахстану</div>
    <h1>
      Цифровые решения<br>
      <span class="line2">для вашего бизнеса</span>
    </h1>
    <p>Создаём сайты, лендинги и цифровую инфраструктуру для бизнеса любого масштаба — от стартапов до крупных компаний.</p>
    <div class="hero-btns">
      <button class="btn-primary" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Получить консультацию</button>
      <button class="btn-outline" onclick="document.getElementById('services').scrollIntoView({behavior:'smooth'})">Наши услуги →</button>
    </div>
    <div class="hero-stats">
      <div><div class="stat-val">50+</div><div class="stat-lbl">Проектов сдано</div></div>
      <div><div class="stat-val">3 дня</div><div class="stat-lbl">Старт проекта</div></div>
      <div><div class="stat-val">100%</div><div class="stat-lbl">Поддержка после сдачи</div></div>
    </div>
  </div>
</section>

<!-- SERVICES -->
<section class="services" id="services">
  <div class="section-label">// Что мы делаем</div>
  <h2 class="section-title">Полный спектр<br>IT-услуг</h2>
  <p class="section-sub">От простого лендинга до корпоративного портала — реализуем проект под ключ.</p>
  <div class="services-grid">
    <div class="service-card">
      <div class="service-icon">🌐</div>
      <h3>Корпоративные сайты</h3>
      <p>Многостраничные сайты с CMS, оптимизированные для поиска и конверсий.</p>
      <span class="service-arrow">↗</span>
    </div>
    <div class="service-card">
      <div class="service-icon">⚡</div>
      <h3>Лендинги и промо</h3>
      <p>Продающие одностраничники для акций, продуктов и рекламных кампаний.</p>
      <span class="service-arrow">↗</span>
    </div>
    <div class="service-card">
      <div class="service-icon">🛒</div>
      <h3>Интернет-магазины</h3>
      <p>E-commerce решения с корзиной, оплатой и управлением каталогом.</p>
      <span class="service-arrow">↗</span>
    </div>
    <div class="service-card">
      <div class="service-icon">📱</div>
      <h3>Мобильная адаптация</h3>
      <p>Сайты, идеально работающие на любых устройствах и браузерах.</p>
      <span class="service-arrow">↗</span>
    </div>
    <div class="service-card">
      <div class="service-icon">🔍</div>
      <h3>SEO-продвижение</h3>
      <p>Оптимизация под поисковики — больше органического трафика и клиентов.</p>
      <span class="service-arrow">↗</span>
    </div>
    <div class="service-card">
      <div class="service-icon">🛠</div>
      <h3>Поддержка и доработки</h3>
      <p>Техническое сопровождение, обновления и развитие вашего сайта.</p>
      <span class="service-arrow">↗</span>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="how" id="how">
  <div class="section-label">// Как мы работаем</div>
  <h2 class="section-title">Просто и прозрачно</h2>
  <div class="steps">
    <div class="step">
      <div class="step-num">01</div>
      <h3>Бриф</h3>
      <p>Обсуждаем цели, аудиторию и пожелания к проекту.</p>
      <div class="step-line"></div>
    </div>
    <div class="step">
      <div class="step-num">02</div>
      <h3>Дизайн</h3>
      <p>Создаём макет и согласовываем каждый экран с вами.</p>
      <div class="step-line"></div>
    </div>
    <div class="step">
      <div class="step-num">03</div>
      <h3>Разработка</h3>
      <p>Верстаем и программируем — чисто, быстро, надёжно.</p>
      <div class="step-line"></div>
    </div>
    <div class="step">
      <div class="step-num">04</div>
      <h3>Запуск</h3>
      <p>Размещаем сайт и передаём управление вам.</p>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing" id="pricing">
  <div class="section-label">// Стоимость</div>
  <h2 class="section-title">Прозрачные цены</h2>
  <p class="section-sub">Фиксированная стоимость без скрытых платежей.</p>
  <div class="pricing-grid">
    <div class="price-card">
      <div class="price-plan">СТАРТ</div>
      <div class="price-val">от 50 000 <span>₸</span></div>
      <div class="price-desc">Для частных лиц и малого бизнеса</div>
      <ul class="price-features">
        <li>Лендинг до 5 секций</li>
        <li>Мобильная адаптация</li>
        <li>Форма обратной связи</li>
        <li>Базовый SEO</li>
        <li>1 месяц поддержки от узбеков</li>
      </ul>
      <button class="price-btn">Выбрать</button>
    </div>
    <div class="price-card featured">
      <div class="price-plan">БИЗНЕС</div>
      <div class="price-val">от 150 000 <span>₸</span></div>
      <div class="price-desc">Для среднего бизнеса и стартапов</div>
      <ul class="price-features">
        <li>Многостраничный сайт</li>
        <li>CMS для управления</li>
        <li>Интеграция с соцсетями</li>
        <li>Аналитика и SEO</li>
        <li>3 месяца поддержки</li>
      </ul>
      <button class="price-btn">Выбрать</button>
    </div>
    <div class="price-card">
      <div class="price-plan">КОРПОРАТ</div>
      <div class="price-val">по запросу</div>
      <div class="price-desc">Для крупных компаний и сложных задач</div>
      <ul class="price-features">
        <li>Индивидуальная разработка</li>
        <li>Интернет-магазин / портал</li>
        <li>API-интеграции</li>
        <li>Выделенный менеджер</li>
        <li>6+ месяцев поддержки</li>
      </ul>
      <button class="price-btn">Обсудить</button>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="contact-wrap">
    <div class="contact-info">
      <div class="section-label">// Свяжитесь с нами</div>
      <h2>Начнём проект<br>вместе?</h2>
      <p>Расскажите о вашей задаче — ответим в течение 2 часов и предложим решение.А если не ответим то я занят</p>
      <div class="contact-links">
        <a href="#" class="contact-link"><div class="clink-icon">✉</div> info@kosheweb.kz</a>
        <a href="#" class="contact-link"><div class="clink-icon">📞</div> +7 (700) 000-00-00</a>
        <a href="#" class="contact-link"><div class="clink-icon">📍</div> Казахстан, работаем удалённо</a>
      </div>
    </div>
   <div class="contact-form">

  <form id="contactForm">

    <div class="form-group">
      <label class="form-label">Ваше имя</label>
      <input type="text" name="name" class="form-input" placeholder="Қалихан">
    </div>

    <div class="form-group">
      <label class="form-label">Телефон или WhatsApp</label>
      <input type="text" name="phone" class="form-input" placeholder="+7 (___) ___-__-__">
    </div>

    <div class="form-group">
      <label class="form-label">Расскажите о проекте</label>
      <textarea class="form-input" name="message" placeholder="Нужен лендинг для нашего магазина..."></textarea>
    </div>

    <button type="submit" class="btn-primary" style="width:100%">
      Отправить заявку →
    </button>

  </form>

</div>
</section>

<footer>
  <div class="footer-logo">Koshe<span>Web</span></div>
  <div>© 2025 KosheWeb. Все права защищены.</div>
  <div>Казахстан · IT-услуги</div>
</footer>
<script>
document.getElementById("contactForm").addEventListener("submit", function(e) {
  e.preventDefault(); // ❗ отменяет переход

  let formData = new FormData(this);

  fetch("send.php", {
    method: "POST",
    body: formData
  })
  .then(response => response.text())
  .then(data => {
    alert("Заявка отправлена ✅");
  })
  .catch(error => {
    alert("Ошибка ❌");
  });
});
</script>
</body>
</html>
