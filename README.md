<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NEXCODE - Agence de Développement Web</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Space+Mono:wght@400;700&display=swap"              rel="stylesheet">
    <style>
        :root {
            --primary: #00ff88;
            --secondary: #00d4ff;
            --dark: #0a0e27;
            --darker: #050816;
            --accent: #ff0080;
            --text: #e0e0e0;
        }

        {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Space Mono', monospace;
            background: var(--darker);
            color: var(--text);
            overflow-x: hidden;
            cursor: none;
        }

        /* Custom Cursor */
        .cursor {
            width: 20px;
            height: 20px;
            border: 2px solid var(--primary);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 9999;
            transition: 0.1s;
            mix-blend-mode: difference;
        }

        .cursor-follower {
            width: 40px;
            height: 40px;
            border: 1px solid var(--secondary);
            border-radius: 50%;
            position: fixed;
            pointer-events: none;
            z-index: 9998;
            transition: 0.3s;
            opacity: 0.5;
        }

        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            opacity: 0.05;
        }

        .bg-animation span {
            position: absolute;
            width: 2px;
            height: 2px;
            background: var(--primary);
            box-shadow: 0 0 10px var(--primary);
            animation: float 15s infinite;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0) translateX(0);
                opacity: 0;
            }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% {
                transform: translateY(-100vh) translateX(100px);
                opacity: 0;
            }
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 20px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            background: rgba(5, 8, 22, 0.8);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(0, 255, 136, 0.1);
        }

        .logo {
            font-family: 'Orbitron', sans-serif;
            font-size: 28px;
            font-weight: 900;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 30px rgba(0, 255, 136, 0.5);
            animation: pulse 3s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { filter: brightness(1); }
            50% { filter: brightness(1.3); }
        }

        nav {
            display: flex;
            gap: 40px;
        }

        nav a {
            color: var(--text);
            text-decoration: none;
            font-size: 14px;
            letter-spacing: 2px;
            text-transform: uppercase;
            position: relative;
            transition: color 0.3s;
        }

        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            transition: width 0.3s;
        }

        nav a:hover {
            color: var(--primary);
        }

        nav a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            position: relative;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            overflow: hidden;
        }

        .hero-content {
            position: relative;
            z-index: 1;
            animation: fadeInUp 1s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 80px;
            font-weight: 900;
            margin-bottom: 20px;
            background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: fadeInUp 1s ease-out 0.2s both;
        }

        .glitch {
            position: relative;
        }

        .glitch::before,
        .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--darker);
        }

        .glitch::before {
            animation: glitch 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) infinite;
            color: var(--primary);
            z-index: -1;
        }

        .glitch::after {
            animation: glitch 0.3s cubic-bezier(0.25, 0.46, 0.45, 0.94) reverse infinite;
            color: var(--accent);
            z-index: -2;
        }

        @keyframes glitch {
            0% {
                transform: translate(0);
            }
            20% {
                transform: translate(-2px, 2px);
            }
            40% {
                transform: translate(-2px, -2px);
            }
            60% {
                transform: translate(2px, 2px);
            }
            80% {
                transform: translate(2px, -2px);
            }
            100% {
                transform: translate(0);
            }
        }

        .hero p {
            font-size: 20px;
            margin-bottom: 40px;
            color: var(--text);
            letter-spacing: 3px;
            animation: fadeInUp 1s ease-out 0.4s both;
        }

        .cta-button {
            display: inline-block;
            padding: 18px 40px;
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
            text-decoration: none;
            font-size: 16px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            animation: fadeInUp 1s ease-out 0.6s both;
        }

        .cta-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: var(--primary);
            transition: left 0.3s;
            z-index: -1;
        }

        .cta-button:hover {
            color: var(--dark);
            box-shadow: 0 0 30px var(--primary);
        }

        .cta-button:hover::before {
            left: 0;
        }

        /* Geometric Shapes */
        .shape {
            position: absolute;
            border: 2px solid var(--primary);
            opacity: 0.1;
            animation: rotate 20s linear infinite;
        }

        .shape-1 {
            width: 300px;
            height: 300px;
            top: 10%;
            right: 10%;
            transform: rotate(45deg);
        }

        .shape-2 {
            width: 200px;
            height: 200px;
            bottom: 15%;
            left: 10%;
            border-radius: 50%;
        }

        .shape-3 {
            width: 150px;
            height: 150px;
            top: 60%;
            right: 20%;
            clip-path: polygon(50% 0%, 100% 100%, 0% 100%);
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        /* Services Section */
        .services {
            padding: 100px 50px;
            position: relative;
            z-index: 1;
        }

        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 50px;
            font-weight: 900;
            text-align: center;
            margin-bottom: 80px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .service-card {
            background: rgba(10, 14, 39, 0.6);
            border: 1px solid rgba(0, 255, 136, 0.2);
            padding: 40px;
            border-radius: 10px;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            cursor: pointer;
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 136, 0.1), transparent);
            transform: rotate(45deg);
            transition: all 0.5s;
        }

        .service-card:hover::before {
            animation: shimmer 1.5s infinite;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }

        .service-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
            box-shadow: 0 10px 40px rgba(0, 255, 136, 0.3);
        }

        .service-icon {
            font-size: 50px;
            margin-bottom: 20px;
            display: inline-block;
            animation: float-icon 3s ease-in-out infinite;
        }

        @keyframes float-icon {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .service-card h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 24px;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .service-card p {
            font-size: 14px;
            line-height: 1.8;
            color: var(--text);
        }

        /* Tech Stack */
        .tech-stack {
            padding: 100px 50px;
            background: linear-gradient(180deg, var(--darker) 0%, var(--dark) 100%);
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 30px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .tech-item {
            background: rgba(0, 255, 136, 0.05);
            padding: 30px;
            border-radius: 10px;
            text-align: center;
            border: 1px solid rgba(0, 255, 136, 0.1);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .tech-item::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: radial-gradient(circle, rgba(0, 255, 136, 0.3), transparent);
            transform: translate(-50%, -50%);
            transition: width 0.3s, height 0.3s;
            border-radius: 50%;
        }

        .tech-item:hover::after {
            width: 300px;
            height: 300px;
        }

        .tech-item:hover {
            transform: scale(1.1);
            border-color: var(--primary);
        }

        .tech-item span {
            font-size: 18px;
            font-weight: 700;
            position: relative;
            z-index: 1;
        }

        /* Contact Section */
        .contact {
            padding: 100px 50px;
            position: relative;
        }

        .contact-container {
            max-width: 800px;
            margin: 0 auto;
            background: rgba(10, 14, 39, 0.6);
            padding: 60px;
            border-radius: 20px;
            border: 1px solid rgba(0, 255, 136, 0.2);
        }

        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .form-group {
            position: relative;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 15px;
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(0, 255, 136, 0.3);
            color: var(--text);
            font-family: 'Space Mono', monospace;
            font-size: 14px;
            border-radius: 5px;
            transition: all 0.3s;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 20px rgba(0, 255, 136, 0.3);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 150px;
        }

        .submit-button {
            padding: 18px 40px;
            background: var(--primary);
            border: none;
            color: var(--dark);
            font-size: 16px;
            font-weight: 700;
            letter-spacing: 2px;
            text-transform: uppercase;
            cursor: pointer;
            border-radius: 5px;
            transition: all 0.3s;
            font-family: 'Space Mono', monospace;
        }

        .submit-button:hover {
            background: var(--secondary);
            box-shadow: 0 10px 40px rgba(0, 212, 255, 0.4);
            transform: translateY(-3px);
        }

        /* Footer */
        footer {
            padding: 40px 50px;
            text-align: center;
            border-top: 1px solid rgba(0, 255, 136, 0.1);
            background: var(--darker);
        }

        footer p {
            font-size: 14px;
            color: var(--text);
            opacity: 0.7;
        }

        /* Scroll Indicator */
        .scroll-indicator {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            width: 30px;
            height: 50px;
            border: 2px solid var(--primary);
            border-radius: 20px;
            display: flex;
            justify-content: center;
            padding-top: 10px;
            animation: fadeOut 1s ease-out 3s forwards;
            z-index: 10;
        }

        @keyframes fadeOut {
            to {
                opacity: 0;
                visibility: hidden;
            }
        }

        .scroll-indicator::before {
            content: '';
            width: 6px;
            height: 10px;
            background: var(--primary);
            border-radius: 10px;
            animation: scroll 2s infinite;
        }

        @keyframes scroll {
            0% {
                transform: translateY(0);
                opacity: 1;
            }
            100% {
                transform: translateY(20px);
                opacity: 0;
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 40px;
            }

            .hero p {
                font-size: 16px;
            }

            nav {
                display: none;
            }

            .services-grid,
            .tech-grid {
                grid-template-columns: 1fr;
            }

            header {
                padding: 20px;
            }

            .services,
            .tech-stack,
            .contact {
                padding: 50px 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Custom Cursor -->
    <div class="cursor"></div>
    <div class="cursor-follower"></div>

    <!-- Background Animation -->
    <div class="bg-animation" id="bgAnimation"></div>

    <!-- Header -->
    <header>
        <div class="logo">NEXCODE</div>
        <nav>
            <a href="#services">Services</a>
            <a href="#tech">Technos</a>
            <a href="#contact">Contact</a>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="shape shape-1"></div>
        <div class="shape shape-2"></div>
        <div class="shape shape-3"></div>
        
        <div class="hero-content">
            <h1 class="glitch" data-text="CODE THE FUTURE">CODE THE FUTURE</h1>
            <p>AGENCE DE DÉVELOPPEMENT WEB NOUVELLE GÉNÉRATION</p>
            <a href="#contact" class="cta-button">Démarrer un projet</a>
        </div>

        <div class="scroll-indicator"></div>
    </section>

    <!-- Services Section -->
    <section class="services" id="services">
        <h2 class="section-title">NOS SERVICES</h2>
        <div class="services-grid">
            <div class="service-card">
                <div class="service-icon">⚡</div>
                <h3>Développement Web</h3>
                <p>Applications web performantes et modernes avec les dernières technologies. React, Vue, Node.js et plus encore.</p>
            </div>
            <div class="service-card">
                <div class="service-icon">📱</div>
                <h3>Applications Mobile</h3>
                <p>Solutions mobiles natives et cross-platform pour iOS et Android. Une expérience utilisateur fluide et intuitive.</p>
            </div>
            <div class="service-card">
                <div class="service-icon">🎨</div>
                <h3>UI/UX Design</h3>
                <p>Interfaces utilisateur élégantes et ergonomiques. Design thinking et prototypage rapide pour des expériences mémorables.</p>
            </div>
            <div class="service-card">
                <div class="service-icon">🚀</div>
                <h3>DevOps & Cloud</h3>
                <p>Infrastructure cloud scalable et automatisation CI/CD. Déploiement continu et monitoring en temps réel.</p>
            </div>
            <div class="service-card">
                <div class="service-icon">🔒</div>
                <h3>Cybersécurité</h3>
                <p>Protection de vos données et applications. Audits de sécurité, tests de pénétration et conformité RGPD.</p>
            </div>
            <div class="service-card">
                <div class="service-icon">🤖</div>
                <h3>Intelligence Artificielle</h3>
                <p>Intégration d'IA et Machine Learning. Chatbots intelligents, analyses prédictives et automatisation.</p>
            </div>
        </div>
    </section>

    <!-- Tech Stack Section -->
    <section class="tech-stack" id="tech">
        <h2 class="section-title">TECHNOLOGIES</h2>
        <div class="tech-grid">
            <div class="tech-item"><span>React</span></div>
            <div class="tech-item"><span>Vue.js</span></div>
            <div class="tech-item"><span>Node.js</span></div>
            <div class="tech-item"><span>Python</span></div>
            <div class="tech-item"><span>Docker</span></div>
            <div class="tech-item"><span>AWS</span></div>
            <div class="tech-item"><span>MongoDB</span></div>
            <div class="tech-item"><span>PostgreSQL</span></div>
            <div class="tech-item"><span>GraphQL</span></div>
            <div class="tech-item"><span>TypeScript</span></div>
            <div class="tech-item"><span>Next.js</span></div>
            <div class="tech-item"><span>TailwindCSS</span></div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <h2 class="section-title">CONTACTEZ-NOUS</h2>
        <div class="contact-container">
            <form class="contact-form">
                <div class="form-group">
                    <input type="text" placeholder="Votre nom" required>
                </div>
                <div class="form-group">
                    <input type="email" placeholder="Votre email" required>
                </div>
                <div class="form-group">
                    <input type="text" placeholder="Sujet">
                </div>
                <div class="form-group">
                    <textarea placeholder="Votre message" required></textarea>
                </div>
                <button type="submit" class="submit-button">Envoyer</button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 NEXCODE. Tous droits réservés. Codé avec ❤️ et ☕</p>
    </footer>

    <script>
        // Custom Cursor
        const cursor = document.querySelector('.cursor');
        const cursorFollower = document.querySelector('.cursor-follower');

        document.addEventListener('mousemove', (e) => {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
            
            setTimeout(() => {
                cursorFollower.style.left = e.clientX + 'px';
                cursorFollower.style.top = e.clientY + 'px';
            }, 100);
        });

        // Background Animation
        const bgAnimation = document.getElementById('bgAnimation');
        for (let i = 0; i < 50; i++) {
            const span = document.createElement('span');
            span.style.left = Math.random() * 100 + '%';
            span.style.animationDelay = Math.random() * 15 + 's';
            span.style.animationDuration = (Math.random() * 10 + 10) + 's';
            bgAnimation.appendChild(span);
        }

        // Smooth Scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Parallax Effect on Scroll
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const shapes = document.querySelectorAll('.shape');
            shapes.forEach((shape, index) => {
                const speed = (index + 1) * 0.5;
                shape.style.transform = `translateY(${scrolled * speed}px) rotate(${scrolled * 0.1}deg)`;
            });
        });

        // Service Cards Animation on Scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animation = 'fadeInUp 0.6s ease-out forwards';
                }
            });
        }, observerOptions);

        document.querySelectorAll('.service-card, .tech-item').forEach(card => {
            observer.observe(card);
        });

        // Form Submission
        document.querySelector('.contact-form').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Merci pour votre message ! Nous vous répondrons dans les plus brefs délais.');
            e.target.reset();
        });

        // Glitch Effect on Hover
        const glitchText = document.querySelector('.glitch');
        glitchText.addEventListener('mouseenter', () => {
            glitchText.style.animation = 'none';
            setTimeout(() => {
                glitchText.style.animation = '';
            }, 10);
        });
    </script>
</body>
</html>
