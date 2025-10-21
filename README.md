<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HOME - Luxury Real Estate Reimagined</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@200;300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-black: #0a0a0a;
            --secondary-black: #1a1a1a;
            --gold: #d4af37;
            --gold-light: #f0d98f;
            --white: #ffffff;
            --gray: #8a8a8a;
            --gray-light: #e5e5e5;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--primary-black);
            color: var(--white);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav.scrolled {
            background: rgba(10, 10, 10, 0.85);
            backdrop-filter: blur(20px);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 200;
            letter-spacing: 0.3em;
            color: var(--gold);
            text-decoration: none;
        }

        .nav-links {
            display: flex;
            gap: 3rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--white);
            text-decoration: none;
            font-weight: 300;
            font-size: 0.95rem;
            letter-spacing: 0.05em;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--gold);
        }

        .burger {
            display: none;
            flex-direction: column;
            cursor: pointer;
            gap: 6px;
        }

        .burger span {
            width: 28px;
            height: 2px;
            background: var(--gold);
            transition: all 0.3s ease;
        }

        .mobile-menu {
            position: fixed;
            top: 0;
            right: -100%;
            width: 300px;
            height: 100vh;
            background: rgba(26, 26, 26, 0.98);
            backdrop-filter: blur(20px);
            transition: right 0.4s ease;
            padding: 6rem 2rem;
            z-index: 999;
        }

        .mobile-menu.active {
            right: 0;
        }

        .mobile-menu a {
            display: block;
            color: var(--white);
            text-decoration: none;
            padding: 1rem 0;
            font-size: 1.2rem;
            font-weight: 300;
            letter-spacing: 0.05em;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            transition: color 0.3s ease;
        }

        .mobile-menu a:hover {
            color: var(--gold);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, var(--primary-black) 0%, var(--secondary-black) 100%);
        }

        .hero-content {
            text-align: center;
            z-index: 2;
            max-width: 900px;
            padding: 0 2rem;
            opacity: 0;
            animation: fadeUp 1s ease forwards 0.3s;
        }

        @keyframes fadeUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
            from {
                opacity: 0;
                transform: translateY(30px);
            }
        }

        .hero h1 {
            font-size: clamp(3rem, 7vw, 6rem);
            font-weight: 200;
            letter-spacing: 0.02em;
            margin-bottom: 1.5rem;
            background: linear-gradient(135deg, var(--white) 0%, var(--gold-light) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero p {
            font-size: 1.3rem;
            font-weight: 300;
            color: var(--gray);
            margin-bottom: 3rem;
            letter-spacing: 0.03em;
        }

        .cta-buttons {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn {
            padding: 1rem 2.5rem;
            font-size: 1rem;
            font-weight: 400;
            letter-spacing: 0.05em;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
            position: relative;
            overflow: hidden;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 100%);
            color: var(--primary-black);
            box-shadow: 0 10px 30px rgba(212, 175, 55, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 40px rgba(212, 175, 55, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: var(--white);
            border: 2px solid var(--gold);
        }

        .btn-secondary:hover {
            background: var(--gold);
            color: var(--primary-black);
        }

        /* Section Styling */
        section {
            padding: 8rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .section-header {
            text-align: center;
            margin-bottom: 5rem;
        }

        .section-header h2 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 200;
            letter-spacing: 0.02em;
            margin-bottom: 1rem;
            color: var(--gold);
        }

        .section-header p {
            font-size: 1.2rem;
            color: var(--gray);
            font-weight: 300;
        }

        /* Featured Properties */
        .properties-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2.5rem;
        }

        .property-card {
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            transition: all 0.4s ease;
            border: 1px solid rgba(212, 175, 55, 0.1);
        }

        .property-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 60px rgba(212, 175, 55, 0.2);
            border-color: rgba(212, 175, 55, 0.3);
        }

        .property-image {
            width: 100%;
            height: 280px;
            background: linear-gradient(135deg, var(--secondary-black) 0%, var(--gold) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: var(--white);
            opacity: 0.3;
        }

        .property-content {
            padding: 2rem;
        }

        .property-content h3 {
            font-size: 1.5rem;
            font-weight: 400;
            margin-bottom: 0.5rem;
            color: var(--gold);
        }

        .property-content .location {
            color: var(--gray);
            font-size: 0.95rem;
            margin-bottom: 1rem;
        }

        .property-content .price {
            font-size: 1.8rem;
            font-weight: 300;
            margin-bottom: 1rem;
        }

        .property-features {
            display: flex;
            gap: 1.5rem;
            font-size: 0.9rem;
            color: var(--gray);
        }

        /* Testimonials */
        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
        }

        .testimonial-card {
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            padding: 2.5rem;
            border-radius: 20px;
            border: 1px solid rgba(212, 175, 55, 0.1);
            transition: all 0.4s ease;
        }

        .testimonial-card:hover {
            border-color: rgba(212, 175, 55, 0.3);
            transform: translateY(-5px);
        }

        .testimonial-text {
            font-size: 1.1rem;
            font-weight: 300;
            line-height: 1.8;
            margin-bottom: 2rem;
            color: var(--gray-light);
        }

        .testimonial-author {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .author-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 500;
            font-size: 1.2rem;
            color: var(--primary-black);
        }

        .author-info h4 {
            font-weight: 400;
            margin-bottom: 0.2rem;
        }

        .author-info p {
            color: var(--gray);
            font-size: 0.9rem;
        }

        /* How It Works */
        .steps-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
            margin-top: 4rem;
        }

        .step {
            text-align: center;
            position: relative;
        }

        .step-number {
            width: 80px;
            height: 80px;
            margin: 0 auto 2rem;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            font-weight: 300;
            color: var(--primary-black);
            box-shadow: 0 10px 30px rgba(212, 175, 55, 0.3);
        }

        .step h3 {
            font-size: 1.5rem;
            font-weight: 400;
            margin-bottom: 1rem;
            color: var(--gold);
        }

        .step p {
            color: var(--gray);
            font-weight: 300;
        }

        /* Features */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2.5rem;
        }

        .feature-card {
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            padding: 2.5rem;
            border-radius: 20px;
            border: 1px solid rgba(212, 175, 55, 0.1);
            transition: all 0.4s ease;
        }

        .feature-card:hover {
            border-color: rgba(212, 175, 55, 0.3);
            transform: translateY(-5px);
        }

        .feature-icon {
            font-size: 3rem;
            margin-bottom: 1.5rem;
        }

        .feature-card h3 {
            font-size: 1.3rem;
            font-weight: 400;
            margin-bottom: 1rem;
            color: var(--gold);
        }

        .feature-card p {
            color: var(--gray);
            font-weight: 300;
            line-height: 1.8;
        }

        /* Mission */
        .mission-content {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }

        .mission-content p {
            font-size: 1.3rem;
            font-weight: 300;
            line-height: 2;
            color: var(--gray-light);
            margin-bottom: 2rem;
        }

        /* Pricing */
        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
            margin-top: 4rem;
        }

        .pricing-card {
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            padding: 3rem 2.5rem;
            border-radius: 20px;
            border: 1px solid rgba(212, 175, 55, 0.1);
            text-align: center;
            transition: all 0.4s ease;
        }

        .pricing-card.featured {
            border-color: var(--gold);
            transform: scale(1.05);
            background: rgba(212, 175, 55, 0.1);
        }

        .pricing-card:hover {
            transform: translateY(-10px) scale(1.02);
            border-color: rgba(212, 175, 55, 0.3);
        }

        .pricing-card h3 {
            font-size: 1.8rem;
            font-weight: 300;
            margin-bottom: 1rem;
            color: var(--gold);
        }

        .pricing-card .price {
            font-size: 3rem;
            font-weight: 200;
            margin-bottom: 0.5rem;
        }

        .pricing-card .period {
            color: var(--gray);
            margin-bottom: 2rem;
        }

        .pricing-features {
            list-style: none;
            margin-bottom: 2rem;
            text-align: left;
        }

        .pricing-features li {
            padding: 0.8rem 0;
            color: var(--gray-light);
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            font-weight: 300;
        }

        /* FAQ */
        .faq-container {
            max-width: 800px;
            margin: 0 auto;
        }

        .faq-item {
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            margin-bottom: 1.5rem;
            border: 1px solid rgba(212, 175, 55, 0.1);
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .faq-question {
            padding: 1.5rem 2rem;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 400;
            font-size: 1.1rem;
            transition: all 0.3s ease;
        }

        .faq-question:hover {
            color: var(--gold);
        }

        .faq-toggle {
            font-size: 1.5rem;
            transition: transform 0.3s ease;
        }

        .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
            padding: 0 2rem;
        }

        .faq-answer p {
            padding-bottom: 1.5rem;
            color: var(--gray);
            font-weight: 300;
            line-height: 1.8;
        }

        .faq-item.active .faq-answer {
            max-height: 500px;
        }

        .faq-item.active .faq-toggle {
            transform: rotate(180deg);
        }

        /* Footer */
        footer {
            background: var(--secondary-black);
            padding: 4rem 2rem 2rem;
            border-top: 1px solid rgba(212, 175, 55, 0.2);
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
            margin-bottom: 3rem;
        }

        .footer-section h3 {
            color: var(--gold);
            font-weight: 400;
            margin-bottom: 1.5rem;
            font-size: 1.2rem;
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section ul li {
            margin-bottom: 0.8rem;
        }

        .footer-section a {
            color: var(--gray);
            text-decoration: none;
            font-weight: 300;
            transition: color 0.3s ease;
        }

        .footer-section a:hover {
            color: var(--gold);
        }

        .footer-bottom {
            text-align: center;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--gray);
            font-weight: 300;
        }

        /* Page Content */
        .page-content {
            min-height: 100vh;
            padding: 10rem 2rem 5rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .page-content h1 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: 200;
            margin-bottom: 2rem;
            color: var(--gold);
        }

        .page-content h2 {
            font-size: 2rem;
            font-weight: 300;
            margin: 3rem 0 1.5rem;
            color: var(--gold);
        }

        .page-content p {
            font-size: 1.1rem;
            font-weight: 300;
            line-height: 1.8;
            color: var(--gray-light);
            margin-bottom: 1.5rem;
        }

        /* Blog Grid */
        .blog-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
            margin-top: 3rem;
        }

        .blog-card {
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid rgba(212, 175, 55, 0.1);
            transition: all 0.4s ease;
            cursor: pointer;
        }

        .blog-card:hover {
            transform: translateY(-10px);
            border-color: rgba(212, 175, 55, 0.3);
        }

        .blog-image {
            width: 100%;
            height: 220px;
            background: linear-gradient(135deg, var(--secondary-black) 0%, var(--gold) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            opacity: 0.3;
        }

        .blog-content {
            padding: 2rem;
        }

        .blog-date {
            color: var(--gray);
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
        }

        .blog-content h3 {
            font-size: 1.5rem;
            font-weight: 400;
            margin-bottom: 1rem;
            color: var(--gold);
        }

        .blog-excerpt {
            color: var(--gray);
            font-weight: 300;
            line-height: 1.6;
        }

        /* Contact Form */
        .contact-form {
            max-width: 600px;
            margin: 3rem auto;
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            padding: 3rem;
            border-radius: 20px;
            border: 1px solid rgba(212, 175, 55, 0.1);
        }

        .form-group {
            margin-bottom: 2rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--gold);
            font-weight: 300;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            background: rgba(10, 10, 10, 0.5);
            border: 1px solid rgba(212, 175, 55, 0.2);
            border-radius: 10px;
            color: var(--white);
            font-family: 'Inter', sans-serif;
            font-weight: 300;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--gold);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 150px;
        }

        /* Chatbot */
        .chatbot-container {
            max-width: 900px;
            margin: 3rem auto;
            background: rgba(26, 26, 26, 0.6);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            border: 1px solid rgba(212, 175, 55, 0.1);
            overflow: hidden;
            height: 600px;
            display: flex;
            flex-direction: column;
        }

        .chat-messages {
            flex: 1;
            padding: 2rem;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
        }

        .message {
            display: flex;
            gap: 1rem;
            align-items: flex-start;
            animation: fadeUp 0.3s ease;
        }

        .message.user {
            flex-direction: row-reverse;
        }

        .message-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 500;
            color: var(--primary-black);
            flex-shrink: 0;
        }

        .message.user .message-avatar {
            background: rgba(255, 255, 255, 0.1);
            color: var(--white);
        }

        .message-content {
            background: rgba(10, 10, 10, 0.5);
            padding: 1rem 1.5rem;
            border-radius: 15px;
            max-width: 70%;
            font-weight: 300;
            line-height: 1.6;
        }

        .message.user .message-content {
            background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 100%);
            color: var(--primary-black);
        }

        .chat-input-container {
            padding: 2rem;
            border-top: 1px solid rgba(212, 175, 55, 0.1);
            display: flex;
            gap: 1rem;
        }

        .chat-input {
            flex: 1;
            padding: 1rem;
            background: rgba(10, 10, 10, 0.5);
            border: 1px solid rgba(212, 175, 55, 0.2);
            border-radius: 25px;
            color: var(--white);
            font-family: 'Inter', sans-serif;
            font-weight: 300;
        }

        .chat-input:focus {
            outline: none;
            border-color: var(--gold);
        }

        .chat-send {
            padding: 1rem 2rem;
            background: linear-gradient(135deg, var(--gold) 0%, var(--gold-light) 100%);
            border: none;
            border-radius: 25px;
            color: var(--primary-black);
            font-weight: 500;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .chat-send:hover {
            transform: scale(1.05);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .burger {
                display: flex;
            }

            .properties-grid,
            .testimonials-grid,
            .features-grid,
            .pricing-grid {
                grid-template-columns: 1fr;
            }

            .hero h1 {
                font-size: 3rem;
            }

            .hero p {
                font-size: 1.1rem;
            }

            .cta-buttons {
                flex-direction: column;
            }

            section {
                padding: 5rem 1.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav id="navbar">
        <div class="nav-container">
            <a href="#" class="logo" data-page="home">HOME</a>
            <ul class="nav-links">
                <li><a href="#featured">Properties</a></li>
                <li><a href="#" data-page="about">About</a></li>
                <li><a href="#" data-page="blog">Blog</a></li>
                <li><a href="#" data-page="contact">Contact</a></li>
                <li><a href="#" data-page="chat">AI Assistant</a></li>
            </ul>
            <div class="burger" id="burger">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <!-- Mobile Menu -->
    <div class="mobile-menu" id="mobileMenu">
        <a href="#featured">Properties</a>
        <a href="#" data-page="about">About</a>
        <a href="#" data-page="blog">Blog</a>
        <a href="#" data-page="contact">Contact</a>
        <a href="#" data-page="chat">AI Assistant</a>
    </div>

    <!-- Main Content Container -->
    <div id="mainContent">
        <!-- Home Page -->
        <div id="homePage">
            <!-- Hero Section -->
            <section class="hero">
                <div class="hero-content">
                    <h1>Luxury Living<br>Redefined</h1>
                    <p>Discover extraordinary properties in the world's most coveted locations</p>
                    <div class="cta-buttons">
                        <a href="#featured" class="btn btn-primary">Explore Properties</a>
                        <a href="#" class="btn btn-secondary" data-page="contact">Schedule Viewing</a>
                    </div>
                </div>
            </section>

            <!-- Featured Properties -->
            <section id="featured">
                <div class="section-header">
                    <h2>Featured Properties</h2>
                    <p>Handpicked selection of premium estates</p>
                </div>
                <div class="properties-grid">
                    <div class="property-card">
                        <div class="property-image">🏛️</div>
                        <div class="property-content">
                            <h3>Skyline Penthouse</h3>
                            <p class="location">Manhattan, New York</p>
                            <p class="price">$12,500,000</p>
                            <div class="property-features">
                                <span>4 Beds</span>
                                <span>5 Baths</span>
                                <span>4,500 sqft</span>
                            </div>
                        </div>
                    </div>
                    <div class="property-card">
                        <div class="property-image">🏖️</div>
                        <div class="property-content">
                            <h3>Oceanfront Villa</h3>
                            <p class="location">Malibu, California</p>
                            <p class="price">$18,900,000</p>
                            <div class="property-features">
                                <span>6 Beds</span>
                                <span>7 Baths</span>
                                <span>8,200 sqft</span>
                            </div>
                        </div>
                    </div>
                    <div class="property-card">
                        <div class="property-image">🏰</div>
                        <div class="property-content">
                            <h3>Historic Estate</h3>
                            <p class="location">Beverly Hills, California</p>
                            <p class="price">$24,750,000</p>
                            <div class="property-features">
                                <span>8 Beds</span>
                                <span>10 Baths</span>
                                <span>12,000 sqft</span>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Testimonials -->
            <section id="testimonials">
                <div class="section-header">
                    <h2>Client Stories</h2>
                    <p>What our clients say about their HOME experience</p>
                </div>
                <div class="testimonials-grid">
                    <div class="testimonial-card">
                        <p class="testimonial-text">"The level of service and attention to detail was exceptional. They found us the perfect family home that exceeded all our expectations."</p>
                        <div class="testimonial-author">
                            <div class="author-avatar">JD</div>
                            <div class="author-info">
                                <h4>Jennifer Davis</h4>
                                <p>Tech Executive</p>
                            </div>
                        </div>
                    </div>
                    <div class="testimonial-card">
                        <p class="testimonial-text">"Professional, knowledgeable, and always available. The entire process was seamless from start to finish. Highly recommend HOME."</p>
                        <div class="testimonial-author">
                            <div class="author-avatar">MC</div>
                            <div class="author-info">
                                <h4>Michael Chen</h4>
                                <p>Investment Banker</p>
                            </div>
                        </div>
                    </div>
                    <div class="testimonial-card">
                        <p class="testimonial-text">"They understood exactly what we were looking for and delivered beyond our wildest dreams. Our new home is absolutely perfect."</p>
                        <div class="testimonial-author">
                            <div class="author-avatar">SR</div>
                            <div class="author-info">
                                <h4>Sarah Rodriguez</h4>
                                <p>Entrepreneur</p>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- How It Works -->
            <section id="how-it-works">
                <div class="section-header">
                    <h2>How It Works</h2>
                    <p>Your journey to luxury living in three simple steps</p>
                </div>
                <div class="steps-container">
                    <div class="step">
                        <div class="step-number">1</div>
                        <h3>Discover</h3>
                        <p>Browse our curated collection of exceptional properties or let our AI assistant help you find the perfect match based on your preferences.</p>
                    </div>
                    <div class="step">
                        <div class="step-number">2</div>
                        <h3>Experience</h3>
                        <p>Schedule private viewings and virtual tours. Our expert agents provide comprehensive insights into each property and neighborhood.</p>
                    </div>
                    <div class="step">
                        <div class="step-number">3</div>
                        <h3>Secure</h3>
                        <p>We handle all negotiations, paperwork, and closing details, ensuring a smooth and stress-free transaction from offer to keys.</p>
                    </div>
                </div>
            </section>

            <!-- Features -->
            <section id="features">
                <div class="section-header">
                    <h2>Why Choose HOME</h2>
                    <p>Elevating the real estate experience</p>
                </div>
                <div class="features-grid">
                    <div class="feature-card">
                        <div class="feature-icon">🤖</div>
                        <h3>AI-Powered Search</h3>
                        <p>Our intelligent assistant learns your preferences and delivers personalized property recommendations that match your lifestyle.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🌟</div>
                        <h3>Exclusive Access</h3>
                        <p>Get early access to off-market properties and exclusive listings before they reach the public market.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🔒</div>
                        <h3>White Glove Service</h3>
                        <p>From initial search to final closing, experience concierge-level service tailored to your unique needs.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">📊</div>
                        <h3>Market Intelligence</h3>
                        <p>Access comprehensive market analytics and insights to make informed decisions with confidence.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">🌍</div>
                        <h3>Global Network</h3>
                        <p>Leverage our worldwide network of luxury real estate professionals and exclusive partnerships.</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">💎</div>
                        <h3>Luxury Portfolio</h3>
                        <p>Curated selection of the finest properties in the most prestigious locations around the world.</p>
                    </div>
                </div>
            </section>

            <!-- Mission -->
            <section id="mission">
                <div class="section-header">
                    <h2>Our Mission</h2>
                </div>
                <div class="mission-content">
                    <p>At HOME, we believe that finding the perfect property should be as exceptional as the property itself. Our mission is to revolutionize luxury real estate by combining cutting-edge technology with unparalleled personal service.</p>
                    <p>We're not just about transactions; we're about transformations. Every property we represent tells a story, and every client we serve embarks on a journey. Our commitment is to make that journey extraordinary.</p>
                    <p>Through innovation, integrity, and an unwavering dedication to excellence, we're redefining what it means to find home in the luxury market.</p>
                </div>
            </section>

            <!-- Pricing -->
            <section id="pricing">
                <div class="section-header">
                    <h2>Membership Tiers</h2>
                    <p>Choose the level of service that matches your needs</p>
                </div>
                <div class="pricing-grid">
                    <div class="pricing-card">
                        <h3>Explorer</h3>
                        <div class="price">Free</div>
                        <p class="period">Always</p>
                        <ul class="pricing-features">
                            <li>Browse all properties</li>
                            <li>Save favorites</li>
                            <li>Property alerts</li>
                            <li>Basic AI assistance</li>
                            <li>Market reports</li>
                        </ul>
                        <a href="#" class="btn btn-secondary" style="width: 100%;">Get Started</a>
                    </div>
                    <div class="pricing-card featured">
                        <h3>Connoisseur</h3>
                        <div class="price">$2,500</div>
                        <p class="period">per year</p>
                        <ul class="pricing-features">
                            <li>Everything in Explorer</li>
                            <li>Early access to listings</li>
                            <li>Dedicated agent</li>
                            <li>Advanced AI insights</li>
                            <li>Private viewings</li>
                            <li>Investment analysis</li>
                        </ul>
                        <a href="#" class="btn btn-primary" style="width: 100%;">Join Now</a>
                    </div>
                    <div class="pricing-card">
                        <h3>Elite</h3>
                        <div class="price">$10,000</div>
                        <p class="period">per year</p>
                        <ul class="pricing-features">
                            <li>Everything in Connoisseur</li>
                            <li>Off-market exclusives</li>
                            <li>Concierge service 24/7</li>
                            <li>Global property access</li>
                            <li>Helicopter tours</li>
                            <li>Personal shopper</li>
                            <li>Priority closing</li>
                        </ul>
                        <a href="#" class="btn btn-secondary" style="width: 100%;">Contact Us</a>
                    </div>
                </div>
            </section>

            <!-- FAQ -->
            <section id="faq">
                <div class="section-header">
                    <h2>Frequently Asked Questions</h2>
                    <p>Everything you need to know</p>
                </div>
                <div class="faq-container">
                    <div class="faq-item">
                        <div class="faq-question">
                            <span>What areas do you serve?</span>
                            <span class="faq-toggle">▼</span>
                        </div>
                        <div class="faq-answer">
                            <p>We serve luxury markets worldwide, with primary focus on major metropolitan areas including New York, Los Angeles, Miami, San Francisco, London, Paris, and Dubai. Our global network allows us to assist clients anywhere in the world.</p>
                        </div>
                    </div>
                    <div class="faq-item">
                        <div class="faq-question">
                            <span>How does the AI assistant work?</span>
                            <span class="faq-toggle">▼</span>
                        </div>
                        <div class="faq-answer">
                            <p>Our AI assistant learns your preferences through conversations and browsing behavior, then provides personalized property recommendations. It can answer questions about listings, neighborhoods, pricing trends, and more, available 24/7.</p>
                        </div>
                    </div>
                    <div class="faq-item">
                        <div class="faq-question">
                            <span>What is your commission structure?</span>
                            <span class="faq-toggle">▼</span>
                        </div>
                        <div class="faq-answer">
                            <p>Our commission structure varies based on property value and membership tier. Explorer members pay standard rates, while Connoisseur and Elite members receive discounted commissions. Contact us for a detailed breakdown tailored to your situation.</p>
                        </div>
                    </div>
                    <div class="faq-item">
                        <div class="faq-question">
                            <span>Can I schedule virtual property tours?</span>
                            <span class="faq-toggle">▼</span>
                        </div>
                        <div class="faq-answer">
                            <p>Absolutely! We offer high-definition virtual tours, 3D walkthroughs, and live video tours with our agents. This is perfect for international clients or initial property screening before in-person visits.</p>
                        </div>
                    </div>
                    <div class="faq-item">
                        <div class="faq-question">
                            <span>Do you assist with international purchases?</span>
                            <span class="faq-toggle">▼</span>
                        </div>
                        <div class="faq-answer">
                            <p>Yes, we specialize in international transactions. Our team includes experts in cross-border regulations, currency exchange, tax implications, and legal requirements for property purchases in multiple countries.</p>
                        </div>
                    </div>
                </div>
            </section>
        </div>

        <!-- About Page -->
        <div id="aboutPage" class="page-content" style="display: none;">
            <h1>About HOME</h1>
            <p>Founded in 2020, HOME was born from a simple belief: that finding the perfect luxury property should be as remarkable as the property itself. We saw an industry ripe for innovation, where technology and personal touch could come together to create something truly exceptional.</p>
            
            <h2>Our Story</h2>
            <p>Our founders, veterans of both Silicon Valley and luxury real estate, recognized that high-net-worth individuals deserved a more sophisticated approach to property search and acquisition. They envisioned a platform that would combine artificial intelligence, comprehensive market data, and white-glove service to deliver an unmatched experience.</p>
            
            <p>Today, HOME represents the pinnacle of luxury real estate service. We've facilitated over $2 billion in transactions, served clients across 40 countries, and maintained a 98% client satisfaction rate. Our success is built on a foundation of trust, expertise, and an unwavering commitment to excellence.</p>
            
            <h2>Our Values</h2>
            <p><strong>Excellence:</strong> We set the highest standards in everything we do, from property curation to client service.</p>
            <p><strong>Innovation:</strong> We continuously push boundaries, leveraging technology to enhance the human experience.</p>
            <p><strong>Integrity:</strong> We operate with transparency, honesty, and an ethical approach in every transaction.</p>
            <p><strong>Discretion:</strong> We understand the importance of privacy and confidentiality in luxury real estate.</p>
            
            <h2>Our Team</h2>
            <p>Our team consists of seasoned real estate professionals, data scientists, and customer experience specialists. Each member brings unique expertise, unified by a passion for helping clients find their perfect home. With an average of 15 years of luxury market experience, our agents are true experts in their fields.</p>
        </div>

        <!-- Blog Page -->
        <div id="blogPage" class="page-content" style="display: none;">
            <h1>Insights & Trends</h1>
            <p>Stay informed with the latest luxury real estate market insights, trends, and expert analysis.</p>
            
            <div class="blog-grid">
                <div class="blog-card" data-article="1">
                    <div class="blog-image">📈</div>
                    <div class="blog-content">
                        <p class="blog-date">October 15, 2025</p>
                        <h3>2025 Luxury Market Outlook</h3>
                        <p class="blog-excerpt">An in-depth analysis of emerging trends shaping the luxury real estate market this year, from sustainable architecture to smart home integration.</p>
                    </div>
                </div>
                <div class="blog-card" data-article="2">
                    <div class="blog-image">🏗️</div>
                    <div class="blog-content">
                        <p class="blog-date">October 8, 2025</p>
                        <h3>The Rise of Wellness Estates</h3>
                        <p class="blog-excerpt">How health-focused amenities are becoming essential in luxury properties, from spa facilities to meditation gardens and fitness centers.</p>
                    </div>
                </div>
                <div class="blog-card" data-article="3">
                    <div class="blog-image">🌴</div>
                    <div class="blog-content">
                        <p class="blog-date">September 30, 2025</p>
                        <h3>Top 10 Emerging Luxury Markets</h3>
                        <p class="blog-excerpt">Discover the next generation of prestigious locations attracting discerning buyers, from coastal paradises to mountain retreats.</p>
                    </div>
                </div>
                <div class="blog-card" data-article="4">
                    <div class="blog-image">💡</div>
                    <div class="blog-content">
                        <p class="blog-date">September 22, 2025</p>
                        <h3>Smart Home Technology in Luxury Properties</h3>
                        <p class="blog-excerpt">Exploring how cutting-edge technology is transforming the luxury living experience, from AI-powered systems to sustainable energy solutions.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Individual Blog Articles -->
        <div id="article1" class="page-content" style="display: none;">
            <h1>2025 Luxury Market Outlook</h1>
            <p class="blog-date">October 15, 2025</p>
            <p>The luxury real estate market is experiencing a fascinating evolution in 2025, driven by changing buyer priorities, technological advancements, and global economic shifts. As we analyze current trends and forecast future developments, several key themes emerge that are reshaping how high-net-worth individuals approach property acquisition.</p>
            
            <h2>Sustainability Takes Center Stage</h2>
            <p>Today's luxury buyers are increasingly environmentally conscious. Sustainable architecture, renewable energy systems, and eco-friendly materials are no longer optional features—they're expected standards. Properties with LEED certification or similar sustainability credentials command premium prices and sell faster than conventional luxury homes.</p>
            
            <h2>The Hybrid Lifestyle Revolution</h2>
            <p>The pandemic permanently altered how we think about home and work. Luxury properties now must accommodate sophisticated home office setups, high-speed connectivity, and versatile spaces that serve multiple functions. Properties with dedicated office wings, video conference rooms, and soundproof work environments are particularly sought after.</p>
            
            <h2>Market Performance and Predictions</h2>
            <p>Despite economic uncertainties, the luxury segment shows remarkable resilience. Prime urban markets have stabilized after the pandemic-era exodus, while prestigious secondary markets continue to appreciate. We predict continued strong performance in waterfront properties, mountain retreats, and urban penthouses in gateway cities.</p>
            
            <p><a href="#" data-page="blog" style="color: var(--gold);">← Back to Blog</a></p>
        </div>

        <div id="article2" class="page-content" style="display: none;">
            <h1>The Rise of Wellness Estates</h1>
            <p class="blog-date">October 8, 2025</p>
            <p>The concept of home as a wellness sanctuary has moved from trendy feature to fundamental requirement in luxury real estate. Today's discerning buyers view their residence as an investment in their health, longevity, and quality of life.</p>
            
            <h2>Essential Wellness Amenities</h2>
            <p>Modern wellness estates go far beyond basic gym facilities. We're seeing dedicated yoga studios with custom lighting and acoustics, infrared saunas, cold plunge pools, meditation gardens, and even on-site massage rooms. Air and water purification systems are becoming standard, as are circadian lighting systems that adjust throughout the day.</p>
            
            <h2>Design for Well-being</h2>
            <p>Wellness-focused design considers everything from room orientation for optimal natural light to the use of non-toxic building materials. Biophilic design principles—incorporating natural elements throughout the home—create spaces that actively support mental and physical health.</p>
            
            <h2>The Investment Case</h2>
            <p>Properties with comprehensive wellness features not only provide lifestyle benefits but also demonstrate superior value retention and appreciation. As health consciousness continues to grow among affluent buyers, wellness estates are proving to be excellent long-term investments.</p>
            
            <p><a href="#" data-page="blog" style="color: var(--gold);">← Back to Blog</a></p>
        </div>

        <div id="article3" class="page-content" style="display: none;">
            <h1>Top 10 Emerging Luxury Markets</h1>
            <p class="blog-date">September 30, 2025</p>
            <p>While traditional luxury markets like New York, London, and Paris remain strong, savvy investors are increasingly looking to emerging markets that offer exceptional value, lifestyle appeal, and appreciation potential.</p>
            
            <h2>The New Luxury Destinations</h2>
            <p>Our analysis identifies several markets poised for significant growth. Coastal Portugal, particularly the Algarve region, combines stunning natural beauty with favorable tax policies. Jackson Hole, Wyoming, offers unparalleled outdoor recreation while maintaining exclusivity. The Texas Hill Country near Austin provides a unique blend of natural beauty, cultural amenities, and business opportunities.</p>
            
            <h2>What Makes a Market Emerge</h2>
            <p>Several factors contribute to a luxury market's emergence: improved infrastructure and connectivity, arrival of high-end amenities and services, growing community of affluent residents, favorable regulatory or tax environment, and unique lifestyle offerings that can't be replicated elsewhere.</p>
            
            <h2>Investment Timing</h2>
            <p>The key to capitalizing on emerging markets is identifying them before they reach peak prices while ensuring fundamental infrastructure and amenities are already in place. Our research suggests that the markets highlighted here are in the ideal sweet spot for entry.</p>
            
            <p><a href="#" data-page="blog" style="color: var(--gold);">← Back to Blog</a></p>
        </div>

        <div id="article4" class="page-content" style="display: none;">
            <h1>Smart Home Technology in Luxury Properties</h1>
            <p class="blog-date">September 22, 2025</p>
            <p>The integration of sophisticated technology into luxury homes has evolved from novelty to necessity. Today's smart homes offer unprecedented levels of convenience, security, efficiency, and personalization.</p>
            
            <h2>Integrated Home Systems</h2>
            <p>Modern luxury properties feature fully integrated systems that control lighting, climate, security, entertainment, and more through unified interfaces. Voice-activated controls, smartphone apps, and AI-driven automation create seamless living experiences. These systems learn resident preferences and automatically adjust settings for optimal comfort.</p>
            
            <h2>Security and Privacy</h2>
            <p>Advanced security systems combine multiple technologies: facial recognition, biometric access, AI-powered surveillance, and sophisticated alarm systems. Privacy concerns are addressed through encrypted networks, secure cloud storage, and systems designed to operate without compromising personal data.</p>
            
            <h2>Energy Management</h2>
            <p>Smart homes optimize energy consumption through intelligent systems that monitor and adjust usage in real-time. Solar panels paired with battery storage, smart HVAC systems, and automated window treatments work together to minimize energy costs while reducing environmental impact.</p>
            
            <h2>Future-Proofing</h2>
            <p>The best smart home installations are designed with upgradeability in mind. Modular systems and robust infrastructure ensure that homes can incorporate new technologies as they emerge, protecting property values and maintaining cutting-edge functionality.</p>
            
            <p><a href="#" data-page="blog" style="color: var(--gold);">← Back to Blog</a></p>
        </div>

        <!-- Contact Page -->
        <div id="contactPage" class="page-content" style="display: none;">
            <h1>Get In Touch</h1>
            <p>Whether you're ready to begin your property search or have questions about our services, we're here to help. Our team typically responds within 24 hours.</p>
            
            <div class="contact-form">
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">Full Name</label>
                        <input type="text" id="name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email Address</label>
                        <input type="email" id="email" required>
                    </div>
                    <div class="form-group">
                        <label for="phone">Phone Number</label>
                        <input type="tel" id="phone">
                    </div>
                    <div class="form-group">
                        <label for="interest">I'm Interested In</label>
                        <input type="text" id="interest" placeholder="e.g., Manhattan penthouses, Malibu beachfront">
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" required></textarea>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Send Message</button>
                </form>
            </div>
        </div>

        <!-- Chat Page -->
        <div id="chatPage" class="page-content" style="display: none;">
            <h1>AI Property Assistant</h1>
            <p>Chat with our intelligent assistant to find properties that match your preferences, get market insights, or ask any questions about luxury real estate.</p>
            
            <div class="chatbot-container">
                <div class="chat-messages" id="chatMessages">
                    <div class="message">
                        <div class="message-avatar">AI</div>
                        <div class="message-content">
                            Hello! I'm your HOME AI assistant. I can help you discover luxury properties, answer questions about neighborhoods, provide market insights, and more. What are you looking for today?
                        </div>
                    </div>
                </div>
                <div class="chat-input-container">
                    <input type="text" class="chat-input" id="chatInput" placeholder="Type your message...">
                    <button class="chat-send" id="chatSend">Send</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h3>HOME</h3>
                <p style="color: var(--gray); font-weight: 300; line-height: 1.8;">Redefining luxury real estate through innovation, expertise, and exceptional service.</p>
            </div>
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul>
                    <li><a href="#featured">Properties</a></li>
                    <li><a href="#" data-page="about">About Us</a></li>
                    <li><a href="#" data-page="blog">Blog</a></li>
                    <li><a href="#" data-page="contact">Contact</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Services</h3>
                <ul>
                    <li><a href="#">Buy</a></li>
                    <li><a href="#">Sell</a></li>
                    <li><a href="#">Rent</a></li>
                    <li><a href="#">Investment</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Connect</h3>
                <ul>
                    <li><a href="#">Instagram</a></li>
                    <li><a href="#">LinkedIn</a></li>
                    <li><a href="#">Twitter</a></li>
                    <li><a href="#">Facebook</a></li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2025 HOME Luxury Real Estate. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // Smooth scroll reveal animation
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('section').forEach(section => {
            observer.observe(section);
        });

        // Sticky navigation with blur effect
        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 100) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Mobile menu toggle
        const burger = document.getElementById('burger');
        const mobileMenu = document.getElementById('mobileMenu');

        burger.addEventListener('click', () => {
            mobileMenu.classList.toggle('active');
        });

        // Close mobile menu when clicking outside
        document.addEventListener('click', (e) => {
            if (!burger.contains(e.target) && !mobileMenu.contains(e.target)) {
                mobileMenu.classList.remove('active');
            }
        });

        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                const href = this.getAttribute('href');
                if (href !== '#' && !this.hasAttribute('data-page')) {
                    e.preventDefault();
                    const target = document.querySelector(href);
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth',
                            block: 'start'
                        });
                        mobileMenu.classList.remove('active');
                    }
                }
            });
        });

        // FAQ accordion
        document.querySelectorAll('.faq-question').forEach(question => {
            question.addEventListener('click', () => {
                const faqItem = question.parentElement;
                const isActive = faqItem.classList.contains('active');
                
                // Close all FAQ items
                document.querySelectorAll('.faq-item').forEach(item => {
                    item.classList.remove('active');
                });
                
                // Open clicked item if it wasn't active
                if (!isActive) {
                    faqItem.classList.add('active');
                }
            });
        });

        // Page navigation system
        const pages = {
            home: 'homePage',
            about: 'aboutPage',
            blog: 'blogPage',
            contact: 'contactPage',
            chat: 'chatPage',
            article1: 'article1',
            article2: 'article2',
            article3: 'article3',
            article4: 'article4'
        };

        function showPage(pageName) {
            // Hide all pages
            Object.values(pages).forEach(pageId => {
                document.getElementById(pageId).style.display = 'none';
            });
            
            // Show requested page
            const pageId = pages[pageName];
            if (pageId) {
                document.getElementById(pageId).style.display = 'block';
                window.scrollTo({ top: 0, behavior: 'smooth' });
                mobileMenu.classList.remove('active');
            }
        }

        // Page navigation click handlers
        document.querySelectorAll('[data-page]').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const page = link.getAttribute('data-page');
                showPage(page);
            });
        });

        // Blog card click handlers
        document.querySelectorAll('.blog-card').forEach(card => {
            card.addEventListener('click', () => {
                const articleNum = card.getAttribute('data-article');
                showPage('article' + articleNum);
            });
        });

        // Contact form submission
        document.getElementById('contactForm')?.addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Thank you for your message! Our team will contact you within 24 hours.');
            e.target.reset();
        });

        // Chatbot functionality
        const chatMessages = document.getElementById('chatMessages');
        const chatInput = document.getElementById('chatInput');
        const chatSend = document.getElementById('chatSend');

        const botResponses = {
            default: "I'd be happy to help you with that. Could you provide more details about what you're looking for?",
            greeting: ["hello", "hi", "hey"],
            greetingResponse: "Hello! How can I assist you with your luxury property search today?",
            properties: ["properties", "listings", "homes", "houses"],
            propertiesResponse: "We have an exceptional collection of luxury properties. Are you interested in a specific location? For example, urban penthouses, beachfront estates, or mountain retreats?",
            price: ["price", "cost", "budget", "expensive"],
            priceResponse: "Our properties range from $5M to $50M+, with most listings between $10M-$25M. What's your ideal price range? I can show you properties that match your budget.",
            location: ["new york", "manhattan", "malibu", "beverly hills", "miami"],
            locationResponse: "Excellent choice! That's one of our premier markets. We have several stunning properties in that area. Would you like to see penthouses, estates, or waterfront properties?",
            features: ["features", "amenities", "bedrooms", "bathrooms"],
            featuresResponse: "Our luxury properties typically include: spacious layouts (4-10+ bedrooms), resort-style amenities, smart home technology, private pools, home theaters, wine cellars, and stunning views. What features are most important to you?",
            schedule: ["schedule", "viewing", "tour", "visit"],
            scheduleResponse: "I can help you schedule a private viewing! We offer both in-person tours and virtual walkthroughs. Would you prefer to schedule a specific date, or would you like me to connect you with one of our agents?",
            contact: ["contact", "call", "email", "speak"],
            contactResponse: "You can reach our team at: Phone: 1-800-LUXURY-HOME or Email: concierge@homeluxury.com. We're available 24/7. Would you like me to have an agent contact you directly?"
        };

        function addMessage(content, isUser = false) {
            const messageDiv = document.createElement('div');
            messageDiv.className = 'message' + (isUser ? ' user' : '');
            messageDiv.innerHTML = `
                <div class="message-avatar">${isUser ? 'You' : 'AI'}</div>
                <div class="message-content">${content}</div>
            `;
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }

        function getBotResponse(userMessage) {
            const message = userMessage.toLowerCase();
            
            // Check for greetings
            if (botResponses.greeting.some(word => message.includes(word))) {
                return botResponses.greetingResponse;
            }
            
            // Check for property inquiries
            if (botResponses.properties.some(word => message.includes(word))) {
                return botResponses.propertiesResponse;
            }
            
            // Check for price inquiries
            if (botResponses.price.some(word => message.includes(word))) {
                return botResponses.priceResponse;
            }
            
            // Check for location inquiries
            if (botResponses.location.some(word => message.includes(word))) {
                return botResponses.locationResponse;
            }
            
            // Check for features inquiries
            if (botResponses.features.some(word => message.includes(word))) {
                return botResponses.featuresResponse;
            }
            
            // Check for scheduling inquiries
            if (botResponses.schedule.some(word => message.includes(word))) {
                return botResponses.scheduleResponse;
            }
            
            // Check for contact inquiries
            if (botResponses.contact.some(word => message.includes(word))) {
                return botResponses.contactResponse;
            }
            
            return botResponses.default;
        }

        function sendMessage() {
            const message = chatInput.value.trim();
            if (message) {
                addMessage(message, true);
                chatInput.value = '';
                
                // Simulate bot typing delay
                setTimeout(() => {
                    const response = getBotResponse(message);
                    addMessage(response);
                }, 1000);
            }
        }

        chatSend?.addEventListener('click', sendMessage);
        chatInput?.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });

        // Initialize: Show home page and make first section visible
        showPage('home');
        
        // Trigger initial animations
        setTimeout(() => {
            document.querySelectorAll('section').forEach((section, index) => {
                if (index === 0) {
                    section.classList.add('visible');
                }
            });
        }, 100);
    </script>
</body>
</html>
