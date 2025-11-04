<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PhiloFacile - Comprendre la philosophie autrement</title>
    
    <!-- Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    
    <!-- Icons -->
    <link rel="stylesheet" href="https://unpkg.com/lucide@latest/font/lucide.min.css">
    
    <!-- Swiper CSS -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.css"/>
    
    <!-- Plyr CSS -->
    <link rel="stylesheet" href="https://cdn.plyr.io/3.7.8/plyr.css"/>
    
    <style>
        :root {
            --beige: #F5F1E6;
            --navy: #0B1F3B;
            --gold: #C9A14E;
            --white: #FFFFFF;
            --gray: #6B7280;
            --light-gray: #F9FAFB;
            --dark-gray: #374151;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            color: var(--navy);
            background-color: var(--beige);
        }

        h1, h2, h3 {
            font-family: 'Playfair Display', serif;
        }

        .container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Navigation */
        nav {
            background: var(--white);
            box-shadow: 0 2px 10px rgba(11, 31, 59, 0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--navy);
            text-decoration: none;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--navy);
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: var(--gold);
        }

        .theme-toggle {
            background: none;
            border: 2px solid var(--navy);
            border-radius: 20px;
            padding: 0.5rem 1rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.3s;
        }

        .theme-toggle:hover {
            background: var(--navy);
            color: var(--white);
        }

        /* Hero Section */
        .hero {
            min-height: 70vh;
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, var(--beige) 0%, var(--white) 100%);
            position: relative;
            overflow: hidden;
        }

        .hero-content {
            flex: 1;
            z-index: 2;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            animation: fadeUp 0.8s ease-out;
        }

        .hero p {
            font-size: 1.2rem;
            color: var(--gray);
            margin-bottom: 2rem;
            animation: fadeUp 0.8s ease-out 0.2s both;
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            animation: fadeUp 0.8s ease-out 0.4s both;
        }

        .btn {
            padding: 0.75rem 2rem;
            border: none;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--gold) 0%, var(--navy) 100%);
            color: var(--white);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(201, 161, 78, 0.3);
        }

        .btn-secondary {
            background: transparent;
            color: var(--navy);
            border: 2px solid var(--navy);
        }

        .btn-secondary:hover {
            background: var(--navy);
            color: var(--white);
        }

        .hero-illustration {
            position: absolute;
            right: 10%;
            top: 20%;
            width: 300px;
            height: 300px;
            opacity: 0.1;
        }

        /* Features Section */
        .features {
            padding: 4rem 0;
            background: var(--white);
        }

        .features h2 {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .feature-card {
            background: var(--light-gray);
            padding: 2rem;
            border-radius: 12px;
            text-align: center;
            transition: transform 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 3rem;
            color: var(--gold);
            margin-bottom: 1rem;
        }

        /* Courses Section */
        .courses {
            padding: 4rem 0;
        }

        .courses h2 {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
        }

        .swiper {
            width: 100%;
            padding-top: 50px;
            padding-bottom: 50px;
        }

        .swiper-slide {
            background-position: center;
            background-size: cover;
            width: 300px;
            height: 400px;
        }

        .course-card {
            background: var(--white);
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(11, 31, 59, 0.1);
            height: 100%;
            display: flex;
            flex-direction: column;
        }

        .course-image {
            height: 200px;
            background: linear-gradient(135deg, var(--gold) 0%, var(--navy) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: var(--white);
        }

        .course-content {
            padding: 1.5rem;
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .course-title {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }

        .course-description {
            color: var(--gray);
            margin-bottom: 1rem;
            flex: 1;
        }

        .course-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.9rem;
            color: var(--gray);
        }

        /* Quote Section */
        .quote-section {
            padding: 4rem 0;
            background: var(--navy);
            color: var(--white);
            text-align: center;
        }

        .quote-container {
            max-width: 800px;
            margin: 0 auto;
        }

        .quote-text {
            font-size: 1.5rem;
            font-style: italic;
            margin-bottom: 1rem;
        }

        .quote-author {
            font-size: 1.1rem;
            color: var(--gold);
        }

        .quote-button {
            margin-top: 2rem;
            background: var(--gold);
            color: var(--navy);
        }

        /* Newsletter */
        .newsletter {
            padding: 4rem 0;
            background: var(--white);
        }

        .newsletter-container {
            max-width: 600px;
            margin: 0 auto;
            text-align: center;
        }

        .newsletter h2 {
            font-size: 2rem;
            margin-bottom: 1rem;
        }

        .newsletter-form {
            display: flex;
            gap: 1rem;
            margin-top: 2rem;
        }

        .newsletter input {
            flex: 1;
            padding: 0.75rem 1rem;
            border: 2px solid var(--navy);
            border-radius: 12px;
            font-size: 1rem;
        }

        /* Footer */
        footer {
            background: var(--navy);
            color: var(--white);
            padding: 3rem 0;
            text-align: center;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 2rem;
        }

        .social-links {
            display: flex;
            gap: 1rem;
        }

        .social-links a {
            color: var(--white);
            font-size: 1.5rem;
            transition: color 0.3s;
        }

        .social-links a:hover {
            color: var(--gold);
        }

        /* Animations */
        @keyframes fadeUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero h1 {
                font-size: 2rem;
            }

            .hero p {
                font-size: 1rem;
            }

            .cta-buttons {
                flex-direction: column;
            }

            .features-grid {
                grid-template-columns: 1fr;
            }

            .newsletter-form {
                flex-direction: column;
            }

            .footer-content {
                flex-direction: column;
                text-align: center;
            }
        }

        /* Dark mode */
        body.dark {
            background-color: var(--navy);
            color: var(--white);
        }

        body.dark nav {
            background: var(--dark-gray);
        }

        body.dark .hero {
            background: linear-gradient(135deg, var(--navy) 0%, var(--dark-gray) 100%);
        }

        body.dark .feature-card,
        body.dark .course-card,
        body.dark .newsletter-container {
            background: var(--dark-gray);
        }

        body.dark h1,
        body.dark h2,
        body.dark h3 {
            color: var(--white);
        }

        body.dark .newsletter input {
            background: var(--navy);
            color: var(--white);
            border-color: var(--gold);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="container">
            <div class="nav-container">
                <a href="#" class="logo">PhiloFacile</a>
                <ul class="nav-links">
                    <li><a href="#cours">Cours</a></li>
                    <li><a href="#quiz">Quiz</a></li>
                    <li><a href="#citations">Citations</a></li>
                    <li><a href="#ressources">Ressources</a></li>
                    <li><a href="#profil">Mon Profil</a></li>
                    <li><button class="theme-toggle" onclick="toggleTheme()">
                        <i data-lucide="sun"></i>
                        <span>Thème</span>
                    </button></li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Penser, c'est exister. Commence ici ton voyage philosophique.</h1>
                <p>Cours clairs, quiz ludiques et citations inspirantes pour comprendre la philo autrement.</p>
                <div class="cta-buttons">
                    <a href="#cours" class="btn btn-primary">Commencer à apprendre</a>
                    <button class="btn btn-secondary" onclick="showDemo()">Voir une démo</button>
                </div>
            </div>
        </div>
        <div class="hero-illustration">
            <i data-lucide="brain" style="width: 100%; height: 100%;"></i>
        </div>
    </section>

    <!-- Features Section -->
    <section class="features">
        <div class="container">
            <h2>Pourquoi PhiloFacile ?</h2>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">
                        <i data-lucide="book-open"></i>
                    </div>
                    <h3>Zero jargon</h3>
                    <p>Nous traduisons les concepts complexes en langage clair.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i data-lucide="target"></i>
                    </div>
                    <h3>Progression ludique</h3>
                    <p>Gagne des badges et suis ton avancement.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">
                        <i data-lucide="users"></i>
                    </div>
                    <h3>Communauté bienveillante</h3>
                    <p>Échange dans un espace modéré avec d'autres curieux.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Courses Section -->
    <section class="courses" id="cours">
        <div class="container">
            <h2>Aperçu des cours</h2>
            <div class="swiper mySwiper">
                <div class="swiper-wrapper">
                    <div class="swiper-slide">
                        <div class="course-card">
                            <div class="course-image">
                                <i data-lucide="columns"></i>
                            </div>
                            <div class="course-content">
                                <h3 class="course-title">Philosophie antique</h3>
                                <p class="course-description">Platon, Aristote et les origines de la pensée occidentale.</p>
                                <div class="course-meta">
                                    <span>8 leçons</span>
                                    <span>45 min</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="swiper-slide">
                        <div class="course-card">
                            <div class="course-image">
                                <i data-lucide="lightbulb"></i>
                            </div>
                            <div class="course-content">
                                <h3 class="course-title">Philosophie moderne</h3>
                                <p class="course-description">Descartes, Kant et les Lumières.</p>
                                <div class="course-meta">
                                    <span>10 leçons</span>
                                    <span>60 min</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="swiper-slide">
                        <div class="course-card">
                            <div class="course-image">
                                <i data-lucide="globe"></i>
                            </div>
                            <div class="course-content">
                                <h3 class="course-title">Philosophie africaine</h3>
                                <p class="course-description">Sagesse traditionnelle et penseurs contemporains.</p>
                                <div class="course-meta">
                                    <span>6 leçons</span>
                                    <span>30 min</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="swiper-slide">
                        <div class="course-card">
                            <div class="course-image">
                                <i data-lucide="scale"></i>
                            </div>
                            <div class="course-content">
                                <h3 class="course-title">Morale & Politique</h3>
                                <p class="course-description">Justice, devoir et société.</p>
                                <div class="course-meta">
                                    <span>7 leçons</span>
                                    <span>40 min</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="swiper-slide">
                        <div class="course-card">
                            <div class="course-image">
                                <i data-lucide="palette"></i>
                            </div>
                            <div class="course-content">
                                <h3 class="course-title">Esthétique & Art</h3>
                                <p class="course-description">La beauté et la création artistique.</p>
                                <div class="course-meta">
                                    <span>5 leçons</span>
                                    <span>25 min</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="swiper-pagination"></div>
            </div>
        </div>
    </section>

    <!-- Quote Section -->
    <section class="quote-section" id="citations">
        <div class="container">
            <div class="quote-container">
                <blockquote class="quote-text" id="quote">"La philosophie commence dans l'étonnement."</blockquote>
                <cite class="quote-author" id="quote-author">Platon</cite>
                <button class="btn quote-button" onclick="newQuote()">Nouvelle pensée</button>
            </div>
        </div>
    </section>

    <!-- Newsletter -->
    <section class="newsletter">
        <div class="container">
            <div class="newsletter-container">
                <h2>Recevez une citation philosophique chaque jour</h2>
                <p>Enrichissez votre réflexion avec notre newsletter quotidienne.</p>
                <form class="newsletter-form" onsubmit="subscribeNewsletter(event)">
                    <input type="email" placeholder="Votre adresse email" required>
                    <button type="submit" class="btn btn-primary">S'inscrire</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div>
                    <h3>PhiloFacile</h3>
                    <p>Comprendre la philosophie autrement</p>
                </div>
                <div class="social-links">
                    <a href="#"><i data-lucide="twitter"></i></a>
                    <a href="#"><i data-lucide="instagram"></i></a>
                    <a href="#"><i data-lucide="facebook"></i></a>
                </div>
                <div>
                    <p>&copy; 2025 PhiloFacile. Tous droits réservés.</p>
                </div>
            </div>
        </div>
    </footer>

    <!-- Scripts -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <script src="https://cdn.jsdelivr.net/npm/swiper@10/swiper-bundle.min.js"></script>
    <script src="https://cdn.plyr.io/3.7.8/plyr.polyfilled.js"></script>
    
    <script>
        // Initialize Lucide icons
        lucide.createIcons();

        // Initialize Swiper
        const swiper = new Swiper('.mySwiper', {
            effect: 'coverflow',
            grabCursor: true,
            centeredSlides: true,
            slidesPerView: 'auto',
            coverflowEffect: {
                rotate: 50,
                stretch: 0,
                depth: 100,
                modifier: 1,
                slideShadows: true,
            },
            pagination: {
                el: '.swiper-pagination',
                clickable: true,
            },
            autoplay: {
                delay: 5000,
                disableOnInteraction: false,
            },
        });

        // Theme toggle
        function toggleTheme() {
            document.body.classList.toggle('dark');
            localStorage.setItem('theme', document.body.classList.contains('dark') ? 'dark' : 'light');
        }

        // Load saved theme
        if (localStorage.getItem('theme') === 'dark') {
            document.body.classList.add('dark');
        }

        // Quotes
        const quotes = [
            { text: "La philosophie commence dans l'étonnement.", author: "Platon" },
            { text: "Je pense, donc je suis.", author: "Descartes" },
            { text: "L'homme est né libre, et partout il est dans les fers.", author: "Rousseau" },
            { text: "Le langage est la maison de l'être.", author: "Heidegger" },
            { text: "La vie n'est pas un problème à résoudre, mais une réalité à expérimenter.", author: "Søren Kierkegaard" },
            { text: "On ne naît pas femme, on le devient.", author: "Simone de Beauvoir" },
            { text: "L'enfer, c'est les autres.", author: "Jean-Paul Sartre" },
            { text: "La liberté est ce que vous faites avec ce qui a été fait de vous.", author: "Jean-Paul Sartre" }
        ];

        function newQuote() {
            const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
            document.getElementById('quote').textContent = "${randomQuote.text}";
            document.getElementById('quote-author').textContent = randomQuote.author;
        }

        // Newsletter
        function subscribeNewsletter(event) {
            event.preventDefault();
            alert('Merci pour votre inscription ! Vous recevrez bientôt vos premières citations philosophiques.');
            event.target.reset();
        }

        // Demo
        function showDemo() {
            alert('Bientôt disponible : une vidéo de démonstration vous présentera toutes les fonctionnalités de PhiloFacile !');
        }

        // Smooth scrolling
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

        // Progress tracking (simple version)
        function trackProgress(courseId) {
            let progress = JSON.parse(localStorage.getItem('progress') || '{}');
            progress[courseId] = (progress[courseId] || 0) + 1;
            localStorage.setItem('progress', JSON.stringify(progress));
        }

        // Add interactive hover effects
        document.querySelectorAll('.course-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-10px)';
                this.style.transition = 'transform 0.3s ease';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0)';
            });
        });

        // Simulate course completion
        function completeCourse(courseId) {
            trackProgress(courseId);
            alert('Félicitations ! Vous avez terminé ce cours.');
            // Add completion styling
            const card = document.querySelector([data-course="${courseId}"]);
            if (card) {
                card.classList.add('completed');
            }
        }

        // Initialize Plyr for videos (when implemented)
        // const player = new Plyr('#player');
    </script>
</body>
</html>
