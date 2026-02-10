<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gardens - Sustainable Gardening Boxes & Expert Advice</title>
    <meta name="description" content="Gardens offers curated gardening boxes, expert advice, and a community for beginners and keen gardeners across Europe, Asia, and New Zealand.">
    <style>
        /* =====================
           CSS VARIABLES & RESET
        ===================== */
        :root {
            --primary-green: #2d5016;
            --secondary-green: #4a7c2c;
            --accent-terra: #c67b5c;
            --accent-sage: #9cad8c;
            --cream: #f8f4ed;
            --off-white: #fefdfb;
            --dark-soil: #3a2a1a;
            --light-sage: #dce5d3;
            --shadow: rgba(45, 80, 22, 0.12);
            --text-primary: #3a2a1a;
            --text-secondary: #5a4a3a;
            --bg-primary: #fefdfb;
            --bg-secondary: #f8f4ed;
            --card-bg: #ffffff;
        }

        [data-theme="dark"] {
            --primary-green: #6fb33f;
            --secondary-green: #8fd158;
            --accent-terra: #ff9b7a;
            --accent-sage: #b8d1a3;
            --cream: #2a2520;
            --off-white: #1a1816;
            --dark-soil: #e8e4dc;
            --light-sage: #3a4432;
            --shadow: rgba(0, 0, 0, 0.3);
            --text-primary: #e8e4dc;
            --text-secondary: #c8c4bc;
            --bg-primary: #1a1816;
            --bg-secondary: #2a2520;
            --card-bg: #2f2b26;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Karla', sans-serif;
            color: var(--text-primary);
            background: var(--bg-primary);
            line-height: 1.7;
            overflow-x: hidden;
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        @import url('https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,600;0,9..144,700;1,9..144,300&family=Karla:wght@300;400;500;600&display=swap');

        /* =====================
           ANIMATIONS
        ===================== */
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

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) scale(1); }
            50% { transform: translate(-30px, -30px) scale(1.1); }
        }

        @keyframes fadeOut {
            from { opacity: 1; transform: translate(-50%, -50%); }
            to { opacity: 0; transform: translate(-50%, -60%); }
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        /* =====================
           THEME TOGGLE
        ===================== */
        .theme-toggle {
            position: fixed;
            top: 100px;
            right: 30px;
            z-index: 1000;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--primary-green);
            border: 3px solid var(--accent-sage);
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            transition: all 0.3s ease;
            box-shadow: 0 4px 20px var(--shadow);
        }

        .theme-toggle:hover {
            transform: scale(1.1) rotate(15deg);
            box-shadow: 0 6px 30px var(--shadow);
        }

        .theme-toggle .sun-icon,
        .theme-toggle .moon-icon {
            position: absolute;
            transition: all 0.3s ease;
        }

        .theme-toggle .sun-icon {
            opacity: 1;
            transform: rotate(0deg) scale(1);
        }

        .theme-toggle .moon-icon {
            opacity: 0;
            transform: rotate(180deg) scale(0);
        }

        [data-theme="dark"] .theme-toggle .sun-icon {
            opacity: 0;
            transform: rotate(-180deg) scale(0);
        }

        [data-theme="dark"] .theme-toggle .moon-icon {
            opacity: 1;
            transform: rotate(0deg) scale(1);
        }

        /* =====================
           ACCESSIBILITY
        ===================== */
        .skip-link {
            position: absolute;
            top: -40px;
            left: 0;
            background: var(--primary-green);
            color: white;
            padding: 8px 16px;
            text-decoration: none;
            z-index: 100;
        }

        .skip-link:focus {
            top: 0;
        }

        /* =====================
           HEADER & NAVIGATION
        ===================== */
        header {
            background: var(--bg-secondary);
            border-bottom: 1px solid var(--light-sage);
            position: sticky;
            top: 0;
            z-index: 50;
            backdrop-filter: blur(10px);
            transition: background-color 0.3s ease;
        }

        nav {
            max-width: 1400px;
            margin: 0 auto;
            padding: 1.5rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 2rem;
        }

        .logo {
            font-family: 'Fraunces', serif;
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary-green);
            text-decoration: none;
            letter-spacing: -0.02em;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            transition: color 0.3s ease;
        }

        .logo::before {
            content: '🌱';
            font-size: 1.8rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2.5rem;
            align-items: center;
        }

        .nav-links a {
            color: var(--text-primary);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -4px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent-terra);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after,
        .nav-links a:focus::after {
            width: 100%;
        }

        .nav-links a:hover,
        .nav-links a:focus {
            color: var(--primary-green);
        }

        .cta-button {
            background: var(--primary-green);
            color: white !important;
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            transition: all 0.3s ease;
            border: 2px solid var(--primary-green);
        }

        .cta-button::after {
            display: none;
        }

        .cta-button:hover,
        .cta-button:focus {
            background: var(--secondary-green);
            border-color: var(--secondary-green);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px var(--shadow);
        }

        .menu-toggle {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--primary-green);
            padding: 0.5rem;
        }

        /* =====================
           HERO SECTION
        ===================== */
        .hero {
            background: linear-gradient(135deg, var(--light-sage) 0%, var(--bg-secondary) 100%);
            padding: 6rem 2rem;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -10%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, var(--accent-sage) 0%, transparent 70%);
            border-radius: 50%;
            animation: float 20s ease-in-out infinite;
            opacity: 0.3;
        }

        .hero-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
            position: relative;
            z-index: 1;
        }

        .hero-text h1 {
            font-family: 'Fraunces', serif;
            font-size: 3.5rem;
            line-height: 1.1;
            margin-bottom: 1.5rem;
            color: var(--primary-green);
            font-weight: 700;
            animation: fadeInUp 0.8s ease-out;
        }

        .hero-text p {
            font-size: 1.25rem;
            margin-bottom: 2rem;
            color: var(--text-secondary);
            animation: fadeInUp 0.8s ease-out 0.2s backwards;
        }

        .hero-buttons {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
            animation: fadeInUp 0.8s ease-out 0.4s backwards;
        }

        .btn-primary,
        .btn-secondary {
            padding: 1rem 2rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            display: inline-block;
            border: 2px solid;
        }

        .btn-primary {
            background: var(--primary-green);
            color: white;
            border-color: var(--primary-green);
        }

        .btn-primary:hover,
        .btn-primary:focus {
            background: var(--secondary-green);
            border-color: var(--secondary-green);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px var(--shadow);
        }

        .btn-secondary {
            background: transparent;
            color: var(--primary-green);
            border-color: var(--primary-green);
        }

        .btn-secondary:hover,
        .btn-secondary:focus {
            background: var(--primary-green);
            color: white;
            transform: translateY(-3px);
        }

        .hero-image {
            position: relative;
            animation: fadeIn 1s ease-out 0.3s backwards;
        }

        .hero-image img {
            width: 100%;
            height: 500px;
            object-fit: cover;
            border-radius: 20px;
            box-shadow: 0 20px 60px var(--shadow);
        }

        /* =====================
           GENERAL SECTION STYLES
        ===================== */
        section {
            padding: 5rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-header {
            text-align: center;
            margin-bottom: 4rem;
        }

        .section-header h2 {
            font-family: 'Fraunces', serif;
            font-size: 2.75rem;
            color: var(--primary-green);
            margin-bottom: 1rem;
            font-weight: 700;
        }

        .section-header p {
            font-size: 1.2rem;
            color: var(--text-secondary);
            max-width: 700px;
            margin: 0 auto;
        }

        /* =====================
           FEATURES
        ===================== */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2.5rem;
            margin-top: 3rem;
        }

        .feature {
            text-align: center;
            transition: transform 0.3s ease;
        }

        .feature:hover {
            transform: translateY(-10px);
        }

        .feature-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, var(--accent-sage), var(--secondary-green));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 1.5rem;
            font-size: 2.5rem;
            box-shadow: 0 4px 15px var(--shadow);
        }

        .feature h3 {
            font-family: 'Fraunces', serif;
            font-size: 1.4rem;
            color: var(--primary-green);
            margin-bottom: 0.75rem;
        }

        .feature p {
            color: var(--text-secondary);
        }

        /* =====================
           QUICK LINKS
        ===================== */
        .quick-links {
            background: var(--bg-secondary);
        }

        .quick-links-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .quick-link-card {
            background: var(--card-bg);
            padding: 3rem 2rem;
            border-radius: 16px;
            text-align: center;
            text-decoration: none;
            color: var(--text-primary);
            transition: all 0.3s ease;
            border: 2px solid transparent;
            position: relative;
            overflow: hidden;
        }

        .quick-link-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, var(--accent-sage), transparent);
            transition: left 0.5s ease;
            opacity: 0.3;
        }

        .quick-link-card:hover::before {
            left: 100%;
        }

        .quick-link-card:hover {
            transform: translateY(-8px);
            border-color: var(--primary-green);
            box-shadow: 0 12px 40px var(--shadow);
        }

        .quick-link-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
        }

        .quick-link-card h3 {
            font-family: 'Fraunces', serif;
            font-size: 1.8rem;
            color: var(--primary-green);
            margin-bottom: 0.5rem;
        }

        .quick-link-card p {
            color: var(--text-secondary);
            margin-bottom: 1rem;
        }

        .link-arrow {
            display: inline-block;
            font-size: 1.5rem;
            color: var(--accent-terra);
            transition: transform 0.3s ease;
        }

        .quick-link-card:hover .link-arrow {
            transform: translateX(10px);
        }

        /* =====================
           TESTIMONIALS
        ===================== */
        .testimonials-preview {
            background: var(--light-sage);
        }

        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .testimonial-card {
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 16px;
            box-shadow: 0 4px 20px var(--shadow);
            transition: transform 0.3s ease;
        }

        .testimonial-card:hover {
            transform: translateY(-5px);
        }

        .testimonial-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .testimonial-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--accent-sage);
        }

        .testimonial-info h4 {
            font-family: 'Fraunces', serif;
            color: var(--primary-green);
            margin-bottom: 0.2rem;
        }

        .testimonial-location {
            font-size: 0.9rem;
            color: var(--text-secondary);
        }

        .testimonial-text {
            font-style: italic;
            color: var(--text-primary);
            line-height: 1.8;
            margin-bottom: 1rem;
        }

        .rating {
            color: var(--accent-terra);
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }

        /* =====================
           PAGE HERO (OTHER PAGES)
        ===================== */
        .page-hero {
            background: linear-gradient(135deg, var(--primary-green) 0%, var(--secondary-green) 100%);
            color: white;
            padding: 6rem 2rem 4rem;
            text-align: center;
        }

        .page-hero-content h1 {
            font-family: 'Fraunces', serif;
            font-size: 3.5rem;
            margin-bottom: 1rem;
            animation: fadeInUp 0.8s ease-out;
        }

        .page-hero-content p {
            font-size: 1.3rem;
            max-width: 800px;
            margin: 0 auto;
            opacity: 0.95;
        }

        /* =====================
           BOXES PAGE
        ===================== */
        .boxes-section {
            padding: 4rem 2rem;
        }

        .boxes-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
            margin-bottom: 4rem;
        }

        .box-card {
            background: var(--card-bg);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 4px 20px var(--shadow);
            transition: all 0.4s ease;
            border: 2px solid transparent;
        }

        .box-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 12px 40px var(--shadow);
            border-color: var(--light-sage);
        }

        .box-image {
            width: 100%;
            height: 220px;
            object-fit: cover;
        }

        .box-content {
            padding: 2rem;
        }

        .box-icon {
            font-size: 2.5rem;
            display: block;
            margin-bottom: 1rem;
        }

        .box-card h3 {
            font-family: 'Fraunces', serif;
            font-size: 1.75rem;
            color: var(--primary-green);
            margin-bottom: 1rem;
        }

        .box-card ul {
            list-style: none;
            margin: 1.5rem 0;
        }

        .box-card li {
            padding: 0.5rem 0;
            padding-left: 1.5rem;
            position: relative;
            color: var(--text-primary);
        }

        .box-card li::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: var(--secondary-green);
            font-weight: bold;
        }

        .box-price {
            font-size: 1.1rem;
            color: var(--accent-terra);
            font-weight: 600;
            margin: 1.5rem 0;
        }

        .subscribe-btn {
            width: 100%;
            padding: 1rem;
            background: var(--primary-green);
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .subscribe-btn:hover {
            background: var(--secondary-green);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px var(--shadow);
        }

        .custom-box {
            background: linear-gradient(135deg, var(--primary-green) 0%, var(--secondary-green) 100%);
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 3rem 2rem;
        }

        .custom-box h3,
        .custom-box p {
            color: white;
        }

        .custom-box .box-icon {
            font-size: 4rem;
        }

        .comparison-section {
            margin-top: 5rem;
            padding: 3rem;
            background: var(--bg-secondary);
            border-radius: 16px;
        }

        .comparison-section h2 {
            font-family: 'Fraunces', serif;
            font-size: 2.5rem;
            color: var(--primary-green);
            text-align: center;
            margin-bottom: 2rem;
        }

        .comparison-table {
            overflow-x: auto;
        }

        .comparison-table table {
            width: 100%;
            border-collapse: collapse;
            background: var(--card-bg);
            border-radius: 12px;
            overflow: hidden;
        }

        .comparison-table th,
        .comparison-table td {
            padding: 1.5rem;
            text-align: left;
            border-bottom: 1px solid var(--light-sage);
        }

        .comparison-table th {
            background: var(--primary-green);
            color: white;
            font-weight: 600;
        }

        .comparison-table tr:last-child td {
            border-bottom: none;
        }

        .comparison-table tr:hover {
            background: var(--light-sage);
        }

        /* =====================
           ACTIVITIES PAGE
        ===================== */
        .activities-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            padding: 2rem 0;
        }

        .activity-card {
            background: var(--card-bg);
            border-radius: 12px;
            overflow: hidden;
            transition: all 0.3s ease;
            border: 1px solid var(--light-sage);
            cursor: pointer;
        }

        .activity-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px var(--shadow);
        }

        .activity-image {
            width: 100%;
            height: 180px;
            object-fit: cover;
        }

        .activity-content {
            padding: 1.5rem;
            text-align: center;
        }

        .activity-icon {
            font-size: 2rem;
            margin-bottom: 0.5rem;
        }

        .activity-card h3 {
            font-family: 'Fraunces', serif;
            font-size: 1.3rem;
            color: var(--primary-green);
            margin-bottom: 0.5rem;
        }

        /* =====================
           GALLERY PAGE
        ===================== */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            padding: 2rem 0;
        }

        .gallery-item {
            position: relative;
            overflow: hidden;
            border-radius: 12px;
            aspect-ratio: 4/3;
            cursor: pointer;
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .gallery-item:hover img {
            transform: scale(1.1);
        }

        .gallery-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(to top, rgba(0,0,0,0.8), transparent);
            color: white;
            padding: 1.5rem;
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }

        .gallery-item:hover .gallery-overlay {
            transform: translateY(0);
        }

        .gallery-overlay h4 {
            font-family: 'Fraunces', serif;
            font-size: 1.2rem;
            margin-bottom: 0.3rem;
        }

        /* =====================
           CONTACT PAGE
        ===================== */
        .contact-content {
            max-width: 800px;
            margin: 0 auto;
            padding: 2rem;
        }

        .contact-form {
            display: grid;
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            margin-bottom: 0.5rem;
            font-weight: 500;
            color: var(--text-primary);
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            padding: 1rem;
            border: 2px solid var(--light-sage);
            border-radius: 8px;
            font-family: 'Karla', sans-serif;
            font-size: 1rem;
            background: var(--card-bg);
            color: var(--text-primary);
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            outline: none;
            border-color: var(--primary-green);
        }

        .form-group textarea {
            min-height: 150px;
            resize: vertical;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        .submit-btn {
            background: var(--primary-green);
            color: white;
            padding: 1.2rem 3rem;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            font-family: 'Karla', sans-serif;
            justify-self: center;
            margin-top: 1rem;
        }

        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px var(--shadow);
            background: var(--secondary-green);
        }

        /* =====================
           DETAILED PAGES STYLES
        ===================== */
        .detailed-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 3rem 2rem;
        }

        .content-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: start;
            margin-top: 3rem;
        }

        .content-image {
            width: 100%;
            height: 400px;
            object-fit: cover;
            border-radius: 16px;
            box-shadow: 0 8px 30px var(--shadow);
        }

        .content-text {
            animation: slideInRight 0.8s ease-out;
        }

        .content-text h2 {
            font-family: 'Fraunces', serif;
            font-size: 2.5rem;
            color: var(--primary-green);
            margin-bottom: 1.5rem;
        }

        .content-text h3 {
            font-family: 'Fraunces', serif;
            font-size: 1.8rem;
            color: var(--secondary-green);
            margin: 2rem 0 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid var(--light-sage);
        }

        .content-text p {
            color: var(--text-primary);
            line-height: 1.8;
            margin-bottom: 1.5rem;
        }

        .content-text ul,
        .content-text ol {
            margin: 1.5rem 0 1.5rem 2rem;
            color: var(--text-primary);
        }

        .content-text li {
            margin-bottom: 0.75rem;
            line-height: 1.8;
        }

        .back-button {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: var(--primary-green);
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            margin-top: 3rem;
            transition: all 0.3s ease;
        }

        .back-button:hover {
            background: var(--secondary-green);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px var(--shadow);
        }

        /* =====================
           DELIVERY INFO SPECIFIC
        ===================== */
        .delivery-process {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .process-step {
            background: var(--bg-secondary);
            padding: 2rem;
            border-radius: 12px;
            text-align: center;
            border: 2px solid var(--light-sage);
        }

        .process-number {
            width: 60px;
            height: 60px;
            background: var(--primary-green);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
            margin: 0 auto 1rem;
        }

        .process-step h4 {
            color: var(--primary-green);
            margin: 1rem 0 0.5rem;
        }

        .delivery-illustration {
            max-width: 600px;
            margin: 3rem auto;
            text-align: center;
        }

        .delivery-illustration img {
            width: 100%;
            border-radius: 16px;
            box-shadow: 0 8px 30px var(--shadow);
        }

        /* =====================
           CHECKLIST STYLES
        ===================== */
        .month-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }

        .month-card {
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 12px;
            border: 2px solid var(--light-sage);
            transition: all 0.3s ease;
        }

        .month-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px var(--shadow);
        }

        .month-card h3 {
            font-family: 'Fraunces', serif;
            color: var(--primary-green);
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .month-card ul {
            list-style: none;
            margin: 1rem 0;
        }

        .month-card li {
            padding: 0.5rem 0;
            padding-left: 1.5rem;
            position: relative;
        }

        .month-card li::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: var(--secondary-green);
            font-weight: bold;
        }

        /* =====================
           FAQ STYLES
        ===================== */
        .faq-grid {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            margin: 3rem 0;
        }

        .faq-item {
            background: var(--card-bg);
            border-radius: 12px;
            border: 2px solid var(--light-sage);
            overflow: hidden;
        }

        .faq-question {
            padding: 1.5rem;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-family: 'Fraunces', serif;
            color: var(--primary-green);
            font-size: 1.2rem;
        }

        .faq-answer {
            padding: 0 1.5rem 1.5rem;
            color: var(--text-primary);
            line-height: 1.8;
            display: none;
        }

        .faq-item.active .faq-answer {
            display: block;
        }

        .faq-toggle {
            font-size: 1.5rem;
            transition: transform 0.3s ease;
        }

        .faq-item.active .faq-toggle {
            transform: rotate(45deg);
        }

        /* =====================
           FOOTER
        ===================== */
        footer {
            background: var(--dark-soil);
            color: var(--cream);
            padding: 3rem 2rem 1.5rem;
        }

        [data-theme="dark"] footer {
            background: #0f0d0b;
        }

        .footer-content {
            max-width: 1400px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 3rem;
            margin-bottom: 2rem;
        }

        .footer-section h3 {
            font-family: 'Fraunces', serif;
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--accent-sage);
        }

        .footer-section ul {
            list-style: none;
        }

        .footer-section ul li {
            margin-bottom: 0.5rem;
        }

        .footer-section a {
            color: var(--cream);
            text-decoration: none;
            opacity: 0.8;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }

        .footer-section a:hover,
        .footer-section a:focus {
            opacity: 1;
            color: var(--accent-sage);
            transform: translateX(5px);
        }

        .footer-section a::before {
            content: '→';
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .footer-section a:hover::before {
            opacity: 1;
        }

        .footer-bottom {
            max-width: 1400px;
            margin: 0 auto;
            padding-top: 2rem;
            border-top: 1px solid rgba(255,255,255,0.1);
            text-align: center;
            opacity: 0.7;
            font-size: 0.9rem;
        }

        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-links a {
            width: 40px;
            height: 40px;
            background: rgba(255,255,255,0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            transition: all 0.3s ease;
        }

        .social-links a:hover,
        .social-links a:focus {
            background: var(--accent-sage);
            transform: translateY(-3px);
        }

        /* =====================
           ACTIVE NAV LINK
        ===================== */
        .nav-links a.active {
            color: var(--primary-green);
            font-weight: 600;
        }

        .nav-links a.active::after {
            width: 100%;
        }

        /* =====================
           MODAL STYLES
        ===================== */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 10000;
            animation: fadeIn 0.3s ease;
        }

        .modal-overlay.active {
            display: flex;
        }

        .modal-content {
            background: var(--card-bg);
            border-radius: 16px;
            max-width: 900px;
            max-height: 90vh;
            overflow-y: auto;
            padding: 3rem;
            position: relative;
            animation: fadeInUp 0.5s ease-out;
            margin: 2rem;
        }

        .modal-close {
            position: absolute;
            top: 1.5rem;
            right: 1.5rem;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--text-primary);
            cursor: pointer;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            transition: all 0.3s ease;
        }

        .modal-close:hover {
            background: var(--light-sage);
            transform: rotate(90deg);
        }

        .modal-image {
            width: 100%;
            height: 400px;
            object-fit: cover;
            border-radius: 12px;
            margin-bottom: 2rem;
        }

        /* =====================
           RESPONSIVE DESIGN
        ===================== */
        @media (max-width: 968px) {
            .nav-links {
                position: fixed;
                top: 0;
                left: -100%;
                width: 100%;
                height: 100vh;
                background: var(--bg-secondary);
                flex-direction: column;
                justify-content: center;
                align-items: center;
                transition: left 0.3s ease;
                gap: 2rem;
            }

            .nav-links.active {
                left: 0;
            }

            .menu-toggle {
                display: block;
            }

            .hero-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .hero-text h1 {
                font-size: 2.5rem;
            }

            .hero-image img {
                height: 350px;
            }

            .section-header h2 {
                font-size: 2rem;
            }

            .theme-toggle {
                top: 90px;
                right: 20px;
                width: 50px;
                height: 50px;
            }

            .page-hero-content h1 {
                font-size: 2.5rem;
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .comparison-table {
                font-size: 0.9rem;
            }

            .comparison-table th,
            .comparison-table td {
                padding: 1rem;
            }

            .content-grid {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .content-image {
                height: 300px;
            }

            .modal-content {
                padding: 2rem;
                margin: 1rem;
            }

            .modal-image {
                height: 250px;
            }
        }

        @media (max-width: 640px) {
            nav {
                padding: 1rem;
            }

            .logo {
                font-size: 1.5rem;
            }

            .hero {
                padding: 3rem 1rem;
            }

            .hero-text h1 {
                font-size: 2rem;
            }

            .hero-text p {
                font-size: 1.1rem;
            }

            section {
                padding: 3rem 1rem;
            }

            .quick-links-grid {
                grid-template-columns: 1fr;
            }

            .content-text h2 {
                font-size: 2rem;
            }

            .content-text h3 {
                font-size: 1.5rem;
            }
        }

        :focus {
            outline: 3px solid var(--accent-terra);
            outline-offset: 2px;
        }

        @media (prefers-reduced-motion: reduce) {
            *,
            *::before,
            *::after {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
            }
        }
    </style>
</head>
<body>
    <!-- Theme Toggle Button -->
    <button class="theme-toggle" id="themeToggle" aria-label="Toggle dark mode">
        <span class="sun-icon">☀️</span>
        <span class="moon-icon">🌙</span>
    </button>

    <!-- Skip to main content for accessibility -->
    <a href="#main-content" class="skip-link">Skip to main content</a>

    <!-- Header & Navigation -->
    <header>
        <nav aria-label="Main navigation">
            <a href="#" class="logo" aria-label="Gardens Home" onclick="showPage('home')">Gardens</a>
            <button class="menu-toggle" aria-label="Toggle menu" aria-expanded="false">
                ☰
            </button>
            <ul class="nav-links" role="list">
                <li><a href="#" onclick="showPage('home')" class="active">Home</a></li>
                <li><a href="#" onclick="showPage('boxes')">Our Boxes</a></li>
                <li><a href="#" onclick="showPage('activities')">Activities</a></li>
                <li><a href="#" onclick="showPage('gallery')">Gallery</a></li>
                <li><a href="#" onclick="showPage('about')">About Us</a></li>
                <li><a href="#" onclick="showPage('contact')" class="cta-button">Get in Touch</a></li>
            </ul>
        </nav>
    </header>

    <!-- Main Content -->
    <main id="main-content">
        <!-- HOME PAGE -->
        <section id="home-page" class="page-content">
            <section class="hero">
                <div class="hero-content">
                    <div class="hero-text">
                        <h1>Grow Your Garden, Nurture Your Soul</h1>
                        <p>From wonky vegetables to wild flower meadows, discover curated gardening boxes and expert advice for every gardener across Europe, Asia, and New Zealand.</p>
                        <div class="hero-buttons">
                            <a href="#" onclick="showPage('boxes')" class="btn-primary">Explore Our Boxes</a>
                            <a href="#" onclick="showPage('activities')" class="btn-secondary">Get Advice</a>
                        </div>
                    </div>
                    <div class="hero-image">
                        <img src="https://images.unsplash.com/photo-1416879595882-3373a0480b5b?w=800&h=500&fit=crop" 
                             alt="Beautiful organic garden with fresh vegetables and flowers" 
                             loading="eager">
                    </div>
                </div>
            </section>

            <!-- Features Preview -->
            <section class="features-preview">
                <div class="section-header">
                    <h2>Why Choose Gardens?</h2>
                    <p>We're passionate about making gardening accessible, sustainable, and rewarding for everyone.</p>
                </div>
                <div class="features-grid">
                    <article class="feature">
                        <div class="feature-icon" aria-hidden="true">🌍</div>
                        <h3>Sustainable Practices</h3>
                        <p>From wonky vegetable rescue to eco-friendly packaging, sustainability is at our core.</p>
                    </article>

                    <article class="feature">
                        <div class="feature-icon" aria-hidden="true">👥</div>
                        <h3>Expert Community</h3>
                        <p>Access professional advice and connect with passionate gardeners across three continents.</p>
                    </article>

                    <article class="feature">
                        <div class="feature-icon" aria-hidden="true">📦</div>
                        <h3>Curated Quality</h3>
                        <p>Every box is thoughtfully designed with premium seeds, tools, and materials.</p>
                    </article>

                    <article class="feature">
                        <div class="feature-icon" aria-hidden="true">🎓</div>
                        <h3>Learn & Grow</h3>
                        <p>Beginner or expert, access resources to enhance your gardening journey.</p>
                    </article>
                </div>
            </section>

            <!-- Quick Links -->
            <section class="quick-links">
                <div class="section-header">
                    <h2>Explore Our Offerings</h2>
                </div>
                <div class="quick-links-grid">
                    <a href="#" onclick="showPage('boxes')" class="quick-link-card">
                        <div class="quick-link-icon">🥕</div>
                        <h3>Subscription Boxes</h3>
                        <p>Discover our curated garden boxes</p>
                        <span class="link-arrow">→</span>
                    </a>
                    <a href="#" onclick="showPage('activities')" class="quick-link-card">
                        <div class="quick-link-icon">📅</div>
                        <h3>Expert Activities</h3>
                        <p>Join workshops and get advice</p>
                        <span class="link-arrow">→</span>
                    </a>
                    <a href="#" onclick="showPage('gallery')" class="quick-link-card">
                        <div class="quick-link-icon">📸</div>
                        <h3>Community Gallery</h3>
                        <p>Get inspired by member gardens</p>
                        <span class="link-arrow">→</span>
                    </a>
                </div>
            </section>

            <!-- Testimonials Preview -->
            <section class="testimonials-preview">
                <div class="section-header">
                    <h2>What Our Members Say</h2>
                </div>
                <div class="testimonials-grid">
                    <article class="testimonial-card">
                        <div class="rating">★★★★★</div>
                        <p class="testimonial-text">"The Flourish box got me started on my gardening journey. The quality of seeds and the step-by-step guides made it so easy!"</p>
                        <div class="testimonial-header">
                            <img src="https://i.pravatar.cc/150?img=1" alt="Sophie" class="testimonial-avatar">
                            <div class="testimonial-info">
                                <h4>Sophie Martinez</h4>
                                <p class="testimonial-location">Barcelona, Spain</p>
                            </div>
                        </div>
                    </article>

                    <article class="testimonial-card">
                        <div class="rating">★★★★★</div>
                        <p class="testimonial-text">"I love the Oddbox! Not only am I reducing food waste, but the vegetables are incredibly fresh."</p>
                        <div class="testimonial-header">
                            <img src="https://i.pravatar.cc/150?img=5" alt="James" class="testimonial-avatar">
                            <div class="testimonial-info">
                                <h4>James Chen</h4>
                                <p class="testimonial-location">Auckland, New Zealand</p>
                            </div>
                        </div>
                    </article>
                </div>
            </section>
        </section>

        <!-- BOXES PAGE -->
        <section id="boxes-page" class="page-content" style="display: none;">
            <div class="page-hero">
                <div class="page-hero-content">
                    <h1>Our Curated Garden Boxes</h1>
                    <p>Thoughtfully designed boxes delivered to your doorstep, complete with everything you need to grow and thrive.</p>
                </div>
            </div>

            <section class="boxes-section">
                <div class="boxes-grid">
                    <article class="box-card">
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQimy-9jkOJrsZa6xdSc3bfNv9_o8wlmZR6zA&s" alt="Oddbox" class="box-image">
                        <div class="box-content">
                            <span class="box-icon">🥕</span>
                            <h3>Oddbox</h3>
                            <p>Celebrate imperfection with wonky vegetables rejected by supermarkets. Reduce waste, enjoy fresh produce.</p>
                            <ul>
                                <li>Wonky but wonderful vegetables</li>
                                <li>Weekly deliveries</li>
                                <li>Exclusive blog access</li>
                                <li>Quality vegetable seeds included</li>
                            </ul>
                            <p class="box-price">Weekly subscription</p>
                            <button class="subscribe-btn">Subscribe Now</button>
                        </div>
                    </article>

                    <article class="box-card">
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTcrCo3cF2djJ2au1-o6aCoP912nqnPDv_3nw&s" alt="Flourish" class="box-image">
                        <div class="box-content">
                            <span class="box-icon">🌿</span>
                            <h3>Flourish</h3>
                            <p>Perfect for beginners wanting to grow their own. Four seasonal boxes delivered throughout the year.</p>
                            <ul>
                                <li>Four boxes per year</li>
                                <li>Seeds with premium seed trays</li>
                                <li>Quality watering can</li>
                                <li>Handmade cruelty-free soap</li>
                            </ul>
                            <p class="box-price">Quarterly subscription</p>
                            <button class="subscribe-btn">Subscribe Now</button>
                        </div>
                    </article>

                    <article class="box-card">
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRoET-TBW1tMIzJMFNWpPTdypjiCw4-VuiiMQ&s" alt="Cottage" class="box-image">
                        <div class="box-content">
                            <span class="box-icon">🌸</span>
                            <h3>Cottage</h3>
                            <p>Create your wildflower haven with monthly curated selections and everything to help them flourish.</p>
                            <ul>
                                <li>Monthly box delivery</li>
                                <li>Wild flower seed varieties</li>
                                <li>Educational fact cards</li>
                                <li>Seed markers and twine</li>
                            </ul>
                            <p class="box-price">Monthly subscription</p>
                            <button class="subscribe-btn">Subscribe Now</button>
                        </div>
                    </article>

                    <article class="box-card custom-box">
                        <span class="box-icon">🎁</span>
                        <h3>Custom Boxes</h3>
                        <p>Looking for corporate gifts or bespoke subscriptions? We create personalized boxes tailored to your specific needs and preferences.</p>
                        <a href="#" onclick="showPage('contact')" class="btn-secondary">Contact Us</a>
                    </article>
                </div>

                <div class="comparison-section">
                    <h2>Compare Our Boxes</h2>
                    <div class="comparison-table">
                        <table>
                            <thead>
                                <tr>
                                    <th>Feature</th>
                                    <th>Oddbox</th>
                                    <th>Flourish</th>
                                    <th>Cottage</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Delivery Frequency</td>
                                    <td>Weekly</td>
                                    <td>Quarterly</td>
                                    <td>Monthly</td>
                                </tr>
                                <tr>
                                    <td>Best For</td>
                                    <td>Sustainability</td>
                                    <td>Beginners</td>
                                    <td>Flower Lovers</td>
                                </tr>
                                <tr>
                                    <td>Seeds Included</td>
                                    <td>✓</td>
                                    <td>✓</td>
                                    <td>✓</td>
                                </tr>
                                <tr>
                                    <td>Tools Included</td>
                                    <td>-</td>
                                    <td>✓</td>
                                    <td>✓</td>
                                </tr>
                                <tr>
                                    <td>Educational Content</td>
                                    <td>Blog Access</td>
                                    <td>Guides</td>
                                    <td>Fact Cards</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>
        </section>

        <!-- ACTIVITIES PAGE -->
        <section id="activities-page" class="page-content" style="display: none;">
            <div class="page-hero">
                <div class="page-hero-content">
                    <h1>Expert Advice & Activities</h1>
                    <p>Join our community and access professional gardening guidance, seasonal tips, and engaging activities.</p>
                </div>
            </div>

            <section class="activities-section" style="padding: 4rem 2rem; max-width: 1400px; margin: 0 auto;">
                <div class="activities-grid">
                    <article class="activity-card" onclick="showModal('open-gardens')">
                        <img src="https://images.unsplash.com/photo-1558904541-efa843a96f01?w=400&h=180&fit=crop" alt="Open Gardens" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">🏡</div>
                            <h3>Open Gardens</h3>
                            <p>Visit and explore beautiful member gardens for inspiration and ideas</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('monthly-checklist')">
                        <img src="https://images.unsplash.com/photo-1484480974693-6ca0a78fb36b?w=400&h=180&fit=crop" alt="Monthly Checklist" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">📅</div>
                            <h3>Monthly Checklist</h3>
                            <p>Stay on track with seasonal tasks and monthly gardening to-dos</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('greenhouse-tips')">
                        <img src="https://images.unsplash.com/photo-1530836369250-ef72a3f5cda8?w=400&h=180&fit=crop" alt="Greenhouse Tips" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">🏠</div>
                            <h3>Greenhouse Tips</h3>
                            <p>Expert advice for maximizing your greenhouse potential year-round</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('maintenance-advice')">
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSDZNFiXi6Z-d_SrkjBAVVd9__-bctMGDCbmw&s" alt="Maintenance Advice" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">🔧</div>
                            <h3>Maintenance Advice</h3>
                            <p>Keep your garden healthy with professional maintenance guidance</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('allotment-jobs')">
                        <img src="https://images.unsplash.com/photo-1466692476868-aef1dfb1e735?w=400&h=180&fit=crop" alt="Allotment Jobs" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">🌾</div>
                            <h3>Allotment Jobs</h3>
                            <p>Practical tips for maintaining productive allotment spaces</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('plant-diary')">
                        <img src="https://images.unsplash.com/photo-1455659817273-f96807779a8a?w=400&h=180&fit=crop" alt="Plant Diary" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">📔</div>
                            <h3>Plant Diary</h3>
                            <p>Track growth and progress with our digital plant journal</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('photo-competitions')">
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSo6TAItljN06ZYSH4nj46wvu3GD1qOFF59dA&s" alt="Photo Competitions" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">📸</div>
                            <h3>Photo Competitions</h3>
                            <p>Share your garden beauty and win prizes in seasonal contests</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('seasonal-surveys')">
                        <img src="https://images.unsplash.com/photo-1542601906990-b4d3fb778b09?w=400&h=180&fit=crop" alt="Seasonal Surveys" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">📊</div>
                            <h3>Seasonal Surveys</h3>
                            <p>Contribute to our community knowledge base with your experiences</p>
                        </div>
                    </article>

                    <article class="activity-card" onclick="showModal('advice-talks')">
                        <img src="https://goglobal.com/wp-content/uploads/2025/01/Success-in-Africa.png" alt="Online Advice Talks" class="activity-image">
                        <div class="activity-content">
                            <div class="activity-icon">💬</div>
                            <h3>Online Advice Talks</h3>
                            <p>Join live sessions with gardening experts and community members</p>
                        </div>
                    </article>
                </div>
            </section>
        </section>

        <!-- GALLERY PAGE -->
        <section id="gallery-page" class="page-content" style="display: none;">
            <div class="page-hero">
                <div class="page-hero-content">
                    <h1>Our Garden Community</h1>
                    <p>Be inspired by the incredible gardens our members have created with Gardens boxes.</p>
                </div>
            </div>
            <section style="padding: 4rem 2rem; max-width: 1400px; margin: 0 auto;">
                <div class="gallery-grid">
                    <div class="gallery-item" onclick="showModal('emma-garden')">
                        <img src="https://images.unsplash.com/photo-1585320806297-9794b3e4eeae?w=500&h=400&fit=crop" alt="Kitchen Garden">
                        <div class="gallery-overlay">
                            <h4>Emma's Kitchen Garden</h4>
                            <p>New Zealand</p>
                        </div>
                    </div>
                    <div class="gallery-item" onclick="showModal('sarah-garden')">
                        <img src="https://images.unsplash.com/photo-1591857177580-dc82b9ac4e1e?w=500&h=400&fit=crop" alt="Cottage Garden">
                        <div class="gallery-overlay">
                            <h4>Sarah's Cottage Garden</h4>
                            <p>United Kingdom</p>
                        </div>
                    </div>
                    <div class="gallery-item" onclick="showModal('marco-garden')">
                        <img src="https://images.unsplash.com/photo-1588964895597-cfccd6e2dbf9?w=500&h=400&fit=crop" alt="Herb Garden">
                        <div class="gallery-overlay">
                            <h4>Marco's Herb Paradise</h4>
                            <p>Italy</p>
                        </div>
                    </div>
                    <div class="gallery-item" onclick="showModal('yuki-garden')">
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT0OmL7W6IcRtgT_E083G-cSVnNNtMOO3Ldrg&s" alt="Urban Garden">
                        <div class="gallery-overlay">
                            <h4>Yuki's Urban Oasis</h4>
                            <p>Japan</p>
                        </div>
                    </div>
                    <div class="gallery-item" onclick="showModal('anna-garden')">
                        <img src="https://images.unsplash.com/photo-1523348837708-15d4a09cfac2?w=500&h=400&fit=crop" alt="Wildflower Meadow">
                        <div class="gallery-overlay">
                            <h4>Anna's Wildflower Meadow</h4>
                            <p>Sweden</p>
                        </div>
                    </div>
                    <div class="gallery-item" onclick="showModal('chen-garden')">
                        <img src="https://images.unsplash.com/photo-1592729645009-b96d1e63d14b?w=500&h=400&fit=crop" alt="Raised Beds">
                        <div class="gallery-overlay">
                            <h4>Chen's Raised Beds</h4>
                            <p>Singapore</p>
                        </div>
                    </div>
                </div>
            </section>
        </section>

        <!-- ABOUT PAGE -->
        <section id="about-page" class="page-content" style="display: none;">
            <div class="page-hero">
                <div class="page-hero-content">
                    <h1>Why Choose Gardens?</h1>
                    <p>We're passionate about making gardening accessible, sustainable, and rewarding for everyone.</p>
                </div>
            </div>
            
            <section style="padding: 4rem 2rem; max-width: 1400px; margin: 0 auto;">
                <div class="features-grid">
                    <article class="feature">
                        <div class="feature-icon">🌍</div>
                        <h3>Sustainable Practices</h3>
                        <p>From wonky vegetable rescue to eco-friendly packaging, sustainability is at our core.</p>
                    </article>
                    <article class="feature">
                        <div class="feature-icon">👥</div>
                        <h3>Expert Community</h3>
                        <p>Access professional advice and connect with passionate gardeners across three continents.</p>
                    </article>
                    <article class="feature">
                        <div class="feature-icon">📦</div>
                        <h3>Curated Quality</h3>
                        <p>Every box is thoughtfully designed with premium seeds, tools, and materials.</p>
                    </article>
                    <article class="feature">
                        <div class="feature-icon">🎓</div>
                        <h3>Learn & Grow</h3>
                        <p>Beginner or expert, access resources to enhance your gardening journey.</p>
                    </article>
                </div>
            </section>
        </section>

        <!-- CONTACT PAGE -->
        <section id="contact-page" class="page-content" style="display: none;">
            <div class="page-hero">
                <div class="page-hero-content">
                    <h1>Get in Touch</h1>
                    <p>Have questions? Want to arrange a custom box? We'd love to hear from you!</p>
                </div>
            </div>
            <section class="contact-content">
                <form class="contact-form">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="name">Your Name *</label>
                            <input type="text" id="name" name="name" required placeholder="John Smith">
                        </div>
                        <div class="form-group">
                            <label for="email">Email Address *</label>
                            <input type="email" id="email" name="email" required placeholder="john@example.com">
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="subject">Subject *</label>
                        <select id="subject" name="subject" required>
                            <option value="">Select a topic...</option>
                            <option value="custom-box">Custom Box Inquiry</option>
                            <option value="corporate">Corporate Subscription</option>
                            <option value="general">General Question</option>
                            <option value="support">Customer Support</option>
                            <option value="feedback">Feedback</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="message">Your Message *</label>
                        <textarea id="message" name="message" required placeholder="Tell us about your gardening needs..."></textarea>
                    </div>
                    <button type="submit" class="submit-btn">Send Message</button>
                </form>
            </section>
        </section>
    </main>

    <!-- Modal Overlay -->
    <div class="modal-overlay" id="modalOverlay">
        <div class="modal-content">
            <button class="modal-close" onclick="closeModal()">×</button>
            <div id="modalContent"></div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h3>Gardens</h3>
                <p>Cultivating sustainable gardening communities across Europe, Asia, and New Zealand.</p>
                <div class="social-links">
                    <a href="https://facebook.com" aria-label="Facebook" target="_blank">📘</a>
                    <a href="https://instagram.com" aria-label="Instagram" target="_blank">📷</a>
                    <a href="https://twitter.com" aria-label="Twitter" target="_blank">🐦</a>
                    <a href="https://pinterest.com" aria-label="Pinterest" target="_blank">📌</a>
                </div>
            </div>
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul>
                    <li><a href="#" onclick="showPage('home')">Home</a></li>
                    <li><a href="#" onclick="showPage('boxes')">Our Boxes</a></li>
                    <li><a href="#" onclick="showPage('activities')">Activities</a></li>
                    <li><a href="#" onclick="showPage('gallery')">Gallery</a></li>
                    <li><a href="#" onclick="showPage('about')">About Us</a></li>
                    <li><a href="#" onclick="showPage('contact')">Contact</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Resources</h3>
                <ul>
                    <li><a href="#" onclick="showModal('monthly-checklist')">Monthly Checklist</a></li>
                    <li><a href="#" onclick="showModal('plant-diary')">Plant Diary</a></li>
                    <li><a href="#" onclick="showModal('blog')">Blog</a></li>
                    <li><a href="#" onclick="showModal('faq')">FAQ</a></li>
                    <li><a href="#" onclick="showModal('delivery-info')">Delivery Info</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Legal</h3>
                <ul>
                    <li><a href="#" onclick="showModal('privacy-policy')">Privacy Policy</a></li>
                    <li><a href="#" onclick="showModal('terms-of-service')">Terms of Service</a></li>
                    <li><a href="#" onclick="showModal('shipping-policy')">Shipping Policy</a></li>
                    <li><a href="#" onclick="showModal('accessibility')">Accessibility</a></li>
                    <li><a href="#" onclick="showModal('cookie-policy')">Cookie Policy</a></li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>&copy; 2026 Gardens. All rights reserved. Growing sustainable futures together.</p>
        </div>
    </footer>

    <script>
        // Theme Toggle Functionality
        const themeToggle = document.getElementById('themeToggle');
        const htmlElement = document.documentElement;

        // Check for saved theme preference or default to 'light'
        const currentTheme = localStorage.getItem('theme') || 'light';
        htmlElement.setAttribute('data-theme', currentTheme);

        // Theme toggle event listener
        if (themeToggle) {
            themeToggle.addEventListener('click', () => {
                const currentTheme = htmlElement.getAttribute('data-theme');
                const newTheme = currentTheme === 'light' ? 'dark' : 'light';
                
                htmlElement.setAttribute('data-theme', newTheme);
                localStorage.setItem('theme', newTheme);
                
                // Add a little animation
                themeToggle.style.transform = 'rotate(360deg)';
                setTimeout(() => {
                    themeToggle.style.transform = 'rotate(0deg)';
                }, 300);
            });
        }

        // Mobile Menu Toggle
        const menuToggle = document.querySelector('.menu-toggle');
        const navLinks = document.querySelector('.nav-links');

        if (menuToggle) {
            menuToggle.addEventListener('click', () => {
                navLinks.classList.toggle('active');
                const isExpanded = menuToggle.getAttribute('aria-expanded') === 'true';
                menuToggle.setAttribute('aria-expanded', !isExpanded);
                menuToggle.textContent = navLinks.classList.contains('active') ? '✕' : '☰';
            });

            // Close mobile menu when clicking a link
            document.querySelectorAll('.nav-links a').forEach(link => {
                link.addEventListener('click', () => {
                    navLinks.classList.remove('active');
                    menuToggle.setAttribute('aria-expanded', 'false');
                    menuToggle.textContent = '☰';
                });
            });

            // Close menu when clicking outside
            document.addEventListener('click', (e) => {
                if (!navLinks.contains(e.target) && !menuToggle.contains(e.target)) {
                    navLinks.classList.remove('active');
                    menuToggle.setAttribute('aria-expanded', 'false');
                    menuToggle.textContent = '☰';
                }
            });
        }

        // Smooth Scrolling for Anchor Links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                const href = this.getAttribute('href');
                if (href !== '#' && href.length > 1) {
                    e.preventDefault();
                    
                    // Smooth scroll to top
                    window.scrollTo({
                        top: 0,
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Function to show a specific page and hide others
        function showPage(pageId) {
            // Hide all pages
            document.querySelectorAll('.page-content').forEach(page => {
                page.style.display = 'none';
            });
            
            // Show the selected page
            const targetPage = document.getElementById(`${pageId}-page`);
            if (targetPage) {
                targetPage.style.display = 'block';
            }
            
            // Update active nav link
            document.querySelectorAll('.nav-links a').forEach(link => {
                link.classList.remove('active');
                if (link.textContent.includes(pageId.charAt(0).toUpperCase() + pageId.slice(1)) || 
                    (pageId === 'home' && link.textContent === 'Home')) {
                    link.classList.add('active');
                }
            });
            
            // Update page title
            const titles = {
                'home': 'Gardens - Sustainable Gardening Boxes & Expert Advice',
                'boxes': 'Our Boxes - Gardens',
                'activities': 'Activities & Expert Advice - Gardens',
                'gallery': 'Community Gallery - Gardens',
                'about': 'About Us - Gardens',
                'contact': 'Contact Us - Gardens'
            };
            
            document.title = titles[pageId] || 'Gardens';
            
            // Smooth scroll to top
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        }

        // Modal functionality
        const modalOverlay = document.getElementById('modalOverlay');
        const modalContent = document.getElementById('modalContent');

        function showModal(modalType) {
            let content = '';
            
            switch(modalType) {
                // GALLERY MODALS
                case 'emma-garden':
                    content = `
                        <img src="https://images.unsplash.com/photo-1585320806297-9794b3e4eeae?w=800&h=500&fit=crop" alt="Emma's Kitchen Garden" class="modal-image">
                        <div class="content-text">
                            <h2>Emma's Kitchen Garden</h2>
                            <p><strong>Location:</strong> Auckland, New Zealand</p>
                            <p><strong>Garden Type:</strong> Urban kitchen garden</p>
                            <p><strong>Size:</strong> 25 square meters</p>
                            <h3>About This Garden</h3>
                            <p>Emma transformed her small urban backyard into a productive kitchen garden using our Flourish subscription box. What started as a few herbs has grown into a year-round food source featuring:</p>
                            <ul>
                                <li>Raised beds made from reclaimed timber</li>
                                <li>Companion planting to maximize space</li>
                                <li>Vertical growing structures for climbing plants</li>
                                <li>Rainwater harvesting system</li>
                            </ul>
                            <h3>What's Growing</h3>
                            <p>Tomatoes, peppers, kale, spinach, carrots, radishes, herbs (basil, rosemary, thyme), strawberries, and edible flowers.</p>
                        </div>
                    `;
                    break;
                    
                case 'sarah-garden':
                    content = `
                        <img src="https://images.unsplash.com/photo-1591857177580-dc82b9ac4e1e?w=800&h=500&fit=crop" alt="Sarah's Cottage Garden" class="modal-image">
                        <div class="content-text">
                            <h2>Sarah's Cottage Garden</h2>
                            <p><strong>Location:</strong> Cotswolds, United Kingdom</p>
                            <p><strong>Garden Type:</strong> Traditional cottage garden</p>
                            <p><strong>Size:</strong> 150 square meters</p>
                            <h3>About This Garden</h3>
                            <p>Sarah's cottage garden is a quintessential English country garden created using our Cottage subscription box. The garden features:</p>
                            <ul>
                                <li>Informal planting style with curved beds</li>
                                <li>Mix of ornamental and edible plants</li>
                                <li>Vintage garden furniture and features</li>
                                <li>Bee-friendly planting throughout</li>
                            </ul>
                            <h3>Seasonal Highlights</h3>
                            <p>Spring: Daffodils, tulips, and flowering fruit trees. Summer: Roses, lavender, and hollyhocks. Autumn: Dahlias, asters, and ornamental grasses.</p>
                        </div>
                    `;
                    break;
                    
                case 'marco-garden':
                    content = `
                        <img src="https://images.unsplash.com/photo-1588964895597-cfccd6e2dbf9?w=800&h=500&fit=crop" alt="Marco's Herb Paradise" class="modal-image">
                        <div class="content-text">
                            <h2>Marco's Herb Paradise</h2>
                            <p><strong>Location:</strong> Tuscany, Italy</p>
                            <p><strong>Garden Type:</strong> Mediterranean herb garden</p>
                            <p><strong>Size:</strong> 40 square meters</p>
                            <h3>About This Garden</h3>
                            <p>Marco created this aromatic herb garden on his Tuscan hillside using plants from our Oddbox and Cottage subscriptions. Features include:</p>
                            <ul>
                                <li>Terracotta pots and traditional Italian containers</li>
                                <li>Gravel pathways for drainage and Mediterranean aesthetic</li>
                                <li>Herbs organized by culinary use and growing requirements</li>
                                <li>Solar-powered lighting for evening enjoyment</li>
                            </ul>
                            <h3>Herb Collection</h3>
                            <p>Basil (4 varieties), rosemary, oregano, thyme, sage, mint, parsley, chives, bay laurel, and lavender for both culinary and decorative purposes.</p>
                        </div>
                    `;
                    break;

                case 'yuki-garden':
                    content = `
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT0OmL7W6IcRtgT_E083G-cSVnNNtMOO3Ldrg&s" alt="Yuki's Urban Oasis" class="modal-image">
                        <div class="content-text">
                            <h2>Yuki's Urban Oasis</h2>
                            <p><strong>Location:</strong> Tokyo, Japan</p>
                            <p><strong>Garden Type:</strong> Urban balcony garden</p>
                            <p><strong>Size:</strong> 8 square meters (balcony)</p>
                            <h3>About This Garden</h3>
                            <p>Yuki transformed a small Tokyo balcony into a lush oasis using our Cottage subscription box. This space-efficient garden demonstrates what's possible in urban environments:</p>
                            <ul>
                                <li>Vertical wall planters for maximum space use</li>
                                <li>Japanese-inspired design with bonsai elements</li>
                                <li>Drip irrigation system for easy maintenance</li>
                                <li>Night lighting for evening enjoyment</li>
                            </ul>
                            <h3>Featured Plants</h3>
                            <p>Japanese maple (bonsai), bamboo, ferns, mosses, miniature hostas, and seasonal flowering plants arranged in traditional Japanese garden style.</p>
                        </div>
                    `;
                    break;

                case 'anna-garden':
                    content = `
                        <img src="https://images.unsplash.com/photo-1523348837708-15d4a09cfac2?w=800&h=500&fit=crop" alt="Anna's Wildflower Meadow" class="modal-image">
                        <div class="content-text">
                            <h2>Anna's Wildflower Meadow</h2>
                            <p><strong>Location:</strong> Stockholm, Sweden</p>
                            <p><strong>Garden Type:</strong> Wildflower meadow</p>
                            <p><strong>Size:</strong> 200 square meters</p>
                            <h3>About This Garden</h3>
                            <p>Anna converted part of her country property into a thriving wildflower meadow using seeds from our Cottage subscription box. The meadow supports local biodiversity and provides year-round beauty:</p>
                            <ul>
                                <li>Native Swedish wildflower species</li>
                                <li>Bee and butterfly-friendly planting</li>
                                <li>Naturalistic design that requires minimal maintenance</li>
                                <li>Educational area for local school visits</li>
                            </ul>
                            <h3>Wildflower Species</h3>
                            <p>Cornflowers, poppies, oxeye daisies, red clover, yarrow, knapweed, and various native grasses that create a changing display through the seasons.</p>
                        </div>
                    `;
                    break;

                case 'chen-garden':
                    content = `
                        <img src="https://images.unsplash.com/photo-1592729645009-b96d1e63d14b?w=800&h=500&fit=crop" alt="Chen's Raised Beds" class="modal-image">
                        <div class="content-text">
                            <h2>Chen's Raised Beds</h2>
                            <p><strong>Location:</strong> Singapore</p>
                            <p><strong>Garden Type:</strong> Raised bed vegetable garden</p>
                            <p><strong>Size:</strong> 15 square meters</p>
                            <h3>About This Garden</h3>
                            <p>Chen created this productive raised bed garden in a Singapore condominium using our Oddbox subscription. Despite the tropical climate and limited space, he grows an impressive variety of vegetables:</p>
                            <ul>
                                <li>Custom-built raised beds with proper drainage</li>
                                <li>Shade cloth for sun protection</li>
                                <li>Drip irrigation with timer system</li>
                                <li>Composting system for organic waste</li>
                            </ul>
                            <h3>Year-Round Production</h3>
                            <p>Lettuces, spinach, bok choy, cherry tomatoes, chili peppers, herbs, and Asian vegetables suited to Singapore's tropical climate, providing fresh produce year-round.</p>
                        </div>
                    `;
                    break;

                // ACTIVITIES MODALS
                case 'open-gardens':
                    content = `
                        <img src="https://images.unsplash.com/photo-1558904541-efa843a96f01?w=800&h=500&fit=crop" alt="Open Gardens Event" class="modal-image">
                        <div class="content-text">
                            <h2>Open Gardens</h2>
                            <p>Visit and explore beautiful member gardens for inspiration and ideas</p>
                            
                            <h3>What are Open Gardens?</h3>
                            <p>Our Open Gardens program allows members to visit each other's gardens, share ideas, and get inspired. These events are organized seasonally and feature gardens of all sizes and styles.</p>
                            
                            <h3>Upcoming Events</h3>
                            <ul>
                                <li><strong>Spring Garden Tour:</strong> April 15-30, 2026</li>
                                <li><strong>Summer Showcase:</strong> July 10-25, 2026</li>
                                <li><strong>Autumn Harvest Tour:</strong> September 5-20, 2026</li>
                                <li><strong>Winter Structure Tour:</strong> January 15-30, 2027</li>
                            </ul>
                            
                            <h3>How to Participate</h3>
                            <ul>
                                <li><strong>As a Visitor:</strong> Register online for scheduled tours</li>
                                <li><strong>As a Host:</strong> Submit your garden for consideration</li>
                                <li><strong>Virtual Tours:</strong> Available for international members</li>
                                <li><strong>Group Visits:</strong> Organized for local gardening clubs</li>
                            </ul>
                            
                            <h3>What You'll Experience</h3>
                            <ul>
                                <li>Guided tours by garden owners</li>
                                <li>Q&A sessions with experienced gardeners</li>
                                <li>Plant identification and care tips</li>
                                <li>Design inspiration for your own space</li>
                                <li>Seed and plant swaps</li>
                            </ul>
                            
                            <h3>Registration Information</h3>
                            <p>Open Gardens events are free for all Gardens members. Non-members can purchase day passes. All tours include detailed information packets and refreshments.</p>
                        </div>
                    `;
                    break;
                    
                case 'monthly-checklist':
                    content = `
                        <img src="https://images.unsplash.com/photo-1484480974693-6ca0a78fb36b?w=800&h=500&fit=crop" alt="Monthly Gardening Checklist" class="modal-image">
                        <div class="content-text">
                            <h2>Monthly Gardening Checklist</h2>
                            <p>Stay organized and never miss an important gardening task with our comprehensive monthly guides.</p>
                            
                            <div class="month-grid">
                                <div class="month-card">
                                    <h3>🌱 Spring (March-May)</h3>
                                    <ul>
                                        <li>Prepare soil and add compost</li>
                                        <li>Sow summer vegetables indoors</li>
                                        <li>Prune winter-flowering shrubs</li>
                                        <li>Divide perennials</li>
                                        <li>Start lawn care routine</li>
                                    </ul>
                                </div>
                                
                                <div class="month-card">
                                    <h3>☀️ Summer (June-August)</h3>
                                    <ul>
                                        <li>Plant out summer bedding</li>
                                        <li>Water deeply during dry spells</li>
                                        <li>Harvest vegetables regularly</li>
                                        <li>Deadhead flowers</li>
                                        <li>Control pests naturally</li>
                                    </ul>
                                </div>
                                
                                <div class="month-card">
                                    <h3>🍂 Autumn (September-November)</h3>
                                    <ul>
                                        <li>Plant spring bulbs</li>
                                        <li>Harvest remaining crops</li>
                                        <li>Collect seeds for next year</li>
                                        <li>Prepare garden for winter</li>
                                        <li>Plant trees and shrubs</li>
                                    </ul>
                                </div>
                                
                                <div class="month-card">
                                    <h3>❄️ Winter (December-February)</h3>
                                    <ul>
                                        <li>Plan next year's garden</li>
                                        <li>Protect tender plants</li>
                                        <li>Clean and maintain tools</li>
                                        <li>Feed winter birds</li>
                                        <li>Order seeds and supplies</li>
                                    </ul>
                                </div>
                            </div>
                            
                            <h3>Pro Tips</h3>
                            <ul>
                                <li>Keep a garden journal to track what works</li>
                                <li>Check local frost dates before planting</li>
                                <li>Rotate crops annually to prevent disease</li>
                                <li>Compost kitchen and garden waste</li>
                                <li>Join our community for region-specific advice</li>
                            </ul>
                        </div>
                    `;
                    break;
                    
                case 'plant-diary':
                    content = `
                        <img src="https://images.unsplash.com/photo-1455659817273-f96807779a8a?w=800&h=500&fit=crop" alt="Plant Diary" class="modal-image">
                        <div class="content-text">
                            <h2>Digital Plant Diary</h2>
                            <p>Track your garden's progress, learn from your experiences, and create a valuable record of your gardening journey.</p>
                            
                            <h3>What to Record</h3>
                            <div class="content-grid">
                                <div>
                                    <h4>📝 Planting Information</h4>
                                    <ul>
                                        <li>Plant names and varieties</li>
                                        <li>Planting dates and locations</li>
                                        <li>Source of seeds/plants</li>
                                        <li>Spacing and depth</li>
                                        <li>Companion plants used</li>
                                    </ul>
                                </div>
                                <div>
                                    <h4>📈 Growth Tracking</h4>
                                    <ul>
                                        <li>Germination dates</li>
                                        <li>First flowers/fruit</li>
                                        <li>Harvest dates and yields</li>
                                        <li>Weekly measurements</li>
                                        <li>Monthly photos</li>
                                    </ul>
                                </div>
                            </div>
                            
                            <h3>Weather & Environment</h3>
                            <ul>
                                <li>Daily temperatures and rainfall</li>
                                <li>Frost dates and warnings</li>
                                <li>Sunlight hours in different areas</li>
                                <li>Soil conditions and pH tests</li>
                                <li>Pest and disease occurrences</li>
                            </ul>
                            
                            <h3>Care & Maintenance Log</h3>
                            <ul>
                                <li>Watering schedule and amounts</li>
                                <li>Fertilizer applications</li>
                                <li>Pruning and training dates</li>
                                <li>Pest control measures</li>
                                <li>Successes and challenges</li>
                            </ul>
                            
                            <h3>Benefits of Keeping a Diary</h3>
                            <p>A plant diary helps you learn from each season, make better decisions, and create a personalized gardening guide based on your specific conditions and experiences.</p>
                        </div>
                    `;
                    break;

                case 'delivery-info':
                    content = `
                        <img src="https://images.unsplash.com/photo-1566576721346-d4a3b4eaeb55?w=800&h=500&fit=crop" alt="Delivery Information" class="modal-image">
                        <div class="content-text">
                            <h2>Delivery Information</h2>
                            <p>Everything you need to know about receiving your Gardens box</p>
                            
                            <h3>How Delivery Works</h3>
                            <div class="delivery-process">
                                <div class="process-step">
                                    <div class="process-number">1</div>
                                    <h4>Order Processing</h4>
                                    <p>Your order is carefully prepared within 1-2 business days</p>
                                </div>
                                <div class="process-step">
                                    <div class="process-number">2</div>
                                    <h4>Quality Check</h4>
                                    <p>Each box is inspected to ensure premium quality</p>
                                </div>
                                <div class="process-step">
                                    <div class="process-number">3</div>
                                    <h4>Shipping</h4>
                                    <p>Secure packaging and tracking number sent via email</p>
                                </div>
                                <div class="process-step">
                                    <div class="process-number">4</div>
                                    <h4>Delivery</h4>
                                    <p>Arrives at your door ready to plant and enjoy!</p>
                                </div>
                            </div>
                            
                            <h3>Delivery Times by Region</h3>
                            <ul>
                                <li><strong>Europe:</strong> 5-7 business days (2-3 express)</li>
                                <li><strong>Asia:</strong> 7-10 business days (3-5 express)</li>
                                <li><strong>New Zealand:</strong> 3-5 business days (1-2 express)</li>
                                <li><strong>Australia:</strong> 4-6 business days (2-3 express)</li>
                                <li><strong>North America:</strong> 6-8 business days (3-4 express)</li>
                            </ul>
                            
                            <h3>Shipping Costs</h3>
                            <ul>
                                <li><strong>Standard Shipping:</strong> Free on orders over €50</li>
                                <li><strong>Express Shipping:</strong> €15 flat rate</li>
                                <li><strong>Subscription Boxes:</strong> Free shipping worldwide</li>
                                <li><strong>Remote Areas:</strong> May incur additional charges</li>
                            </ul>
                            
                            <h3>Package Protection</h3>
                            <p>All our boxes are specially designed to protect plants during transit:</p>
                            <ul>
                                <li>Biodegradable insulation materials</li>
                                <li>Moisture-controlled packaging</li>
                                <li>Temperature-sensitive items in cool packs</li>
                                <li>Fragile items clearly marked</li>
                                <li>100% plastic-free packaging</li>
                            </ul>
                            
                            <h3>What to Do When Your Box Arrives</h3>
                            <ol>
                                <li>Open your box immediately upon delivery</li>
                                <li>Check all items against your packing slip</li>
                                <li>Water any plants that need it</li>
                                <li>Plant or store according to instructions</li>
                                <li>Recycle or compost packaging materials</li>
                            </ol>
                            
                            <h3>Missing or Damaged Items?</h3>
                            <p>Contact us within 48 hours of delivery and we'll resolve the issue immediately. We guarantee all our products and offer 100% satisfaction.</p>
                        </div>
                    `;
                    break;

                case 'faq':
                    content = `
                        <img src="https://images.unsplash.com/photo-1560472354-b33ff0c44a43?w=800&h=500&fit=crop" alt="Frequently Asked Questions" class="modal-image">
                        <div class="content-text">
                            <h2>Frequently Asked Questions</h2>
                            <p>Quick answers to common questions about Gardens</p>
                            
                            <div class="faq-grid">
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        How often are subscription boxes delivered?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>It depends on the box you choose: Oddbox delivers weekly, Flourish delivers quarterly (4 times per year), and Cottage delivers monthly. You can pause or cancel your subscription at any time.</p>
                                    </div>
                                </div>
                                
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        Can I customize my subscription box?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>Yes! All our subscription boxes can be customized based on your preferences, growing conditions, and experience level. Contact our team to discuss your specific needs.</p>
                                    </div>
                                </div>
                                
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        Do you ship internationally?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>Yes, we ship to over 40 countries across Europe, Asia, New Zealand, Australia, and North America. Shipping times vary by location. All subscription boxes include free international shipping.</p>
                                    </div>
                                </div>
                                
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        What if I receive damaged plants?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>We guarantee all our plants. If any arrive damaged, contact us within 48 hours with photos, and we'll send replacements immediately at no extra cost.</p>
                                    </div>
                                </div>
                                
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        Are the seeds organic and non-GMO?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>Yes! All our seeds are 100% organic, non-GMO, and sourced from certified organic seed suppliers. We never use treated or genetically modified seeds.</p>
                                    </div>
                                </div>
                                
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        How do I cancel my subscription?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>You can cancel anytime through your account dashboard or by contacting customer service. There are no cancellation fees, and you'll receive any boxes already paid for.</p>
                                    </div>
                                </div>
                                
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        Do you offer corporate or gift subscriptions?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>Yes! We offer special corporate gift programs and one-time gift subscriptions. Contact our corporate team for bulk discounts and custom packaging options.</p>
                                    </div>
                                </div>
                                
                                <div class="faq-item">
                                    <div class="faq-question" onclick="toggleFaq(this)">
                                        Can beginners really use your boxes?
                                        <span class="faq-toggle">+</span>
                                    </div>
                                    <div class="faq-answer">
                                        <p>Absolutely! Our Flourish box is specifically designed for beginners with easy-to-follow guides, simple plants to grow, and all the tools you need to get started successfully.</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    `;
                    break;

                case 'privacy-policy':
                    content = `
                        <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800&h=500&fit=crop" alt="Privacy Policy" class="modal-image">
                        <div class="content-text">
                            <h2>Privacy Policy</h2>
                            <p><strong>Last Updated:</strong> January 15, 2026</p>
                            
                            <h3>1. Information We Collect</h3>
                            <p>We collect information you provide directly to us, including:</p>
                            <ul>
                                <li><strong>Personal Information:</strong> Name, email address, postal address, phone number</li>
                                <li><strong>Account Information:</strong> Username, password, preferences</li>
                                <li><strong>Payment Information:</strong> Credit card details (processed securely by our payment partners)</li>
                                <li><strong>Garden Information:</strong> Your location, climate zone, garden size, experience level</li>
                                <li><strong>Communication:</strong> Messages, feedback, and support requests</li>
                            </ul>
                            
                            <h3>2. How We Use Your Information</h3>
                            <p>We use your information to:</p>
                            <ul>
                                <li>Process orders and deliver products</li>
                                <li>Personalize your gardening experience</li>
                                <li>Provide customer support</li>
                                <li>Send gardening tips and updates (with your consent)</li>
                                <li>Improve our products and services</li>
                                <li>Comply with legal obligations</li>
                            </ul>
                            
                            <h3>3. Information Sharing</h3>
                            <p>We do not sell your personal information. We only share information with:</p>
                            <ul>
                                <li><strong>Service Providers:</strong> Shipping companies, payment processors</li>
                                <li><strong>Legal Requirements:</strong> When required by law</li>
                                <li><strong>Business Transfers:</strong> In connection with mergers or acquisitions</li>
                                <li><strong>With Your Consent:</strong> When you explicitly agree</li>
                            </ul>
                            
                            <h3>4. Data Security</h3>
                            <p>We implement appropriate security measures including:</p>
                            <ul>
                                <li>SSL encryption for all data transmission</li>
                                <li>Secure storage with access controls</li>
                                <li>Regular security audits</li>
                                <li>Employee privacy training</li>
                            </ul>
                            
                            <h3>5. Your Rights</h3>
                            <p>You have the right to:</p>
                            <ul>
                                <li>Access your personal information</li>
                                <li>Correct inaccurate data</li>
                                <li>Request deletion of your data</li>
                                <li>Opt-out of marketing communications</li>
                                <li>Data portability</li>
                                <li>Lodge complaints with regulatory authorities</li>
                            </ul>
                            
                            <h3>6. International Transfers</h3>
                            <p>Your information may be transferred to and processed in countries other than your own. We ensure appropriate safeguards are in place for such transfers.</p>
                            
                            <h3>7. Children's Privacy</h3>
                            <p>Our services are not directed to children under 16. We do not knowingly collect information from children under 16.</p>
                            
                            <h3>8. Changes to This Policy</h3>
                            <p>We may update this policy periodically. We will notify you of significant changes via email or website notice.</p>
                            
                            <h3>9. Contact Us</h3>
                            <p>For privacy-related questions or requests:</p>
                            <ul>
                                <li>Email: privacy@gardens.com</li>
                                <li>Mail: Gardens Privacy Team, 123 Green Street, London, UK</li>
                                <li>Phone: +44 20 1234 5678</li>
                            </ul>
                        </div>
                    `;
                    break;

                case 'terms-of-service':
                    content = `
                        <img src="https://images.unsplash.com/photo-1589829545856-d10d557cf95f?w=800&h=500&fit=crop" alt="Terms of Service" class="modal-image">
                        <div class="content-text">
                            <h2>Terms of Service</h2>
                            <p><strong>Effective Date:</strong> January 15, 2026</p>
                            
                            <h3>1. Acceptance of Terms</h3>
                            <p>By accessing or using Gardens' website, products, or services, you agree to be bound by these Terms of Service. If you disagree with any part, you may not access our services.</p>
                            
                            <h3>2. Account Registration</h3>
                            <p>To use certain features, you must register for an account. You agree to:</p>
                            <ul>
                                <li>Provide accurate and complete information</li>
                                <li>Maintain security of your account credentials</li>
                                <li>Notify us immediately of unauthorized access</li>
                                <li>Accept responsibility for all activities under your account</li>
                            </ul>
                            
                            <h3>3. Subscription Services</h3>
                            <p>Our subscription services operate as follows:</p>
                            <ul>
                                <li><strong>Billing:</strong> Recurring payments based on your selected frequency</li>
                                <li><strong>Renewal:</strong> Automatic renewal unless cancelled</li>
                                <li><strong>Cancellation:</strong> May cancel anytime; no refunds for partial periods</li>
                                <li><strong>Price Changes:</strong> 30 days notice for subscription price increases</li>
                            </ul>
                            
                            <h3>4. Product Information</h3>
                            <p>We strive for accuracy but cannot guarantee:</p>
                            <ul>
                                <li>All product descriptions are completely accurate</li>
                                <li>Images exactly match products</li>
                                <li>Products will be continuously available</li>
                                <li>Specific results from using our products</li>
                            </ul>
                            
                            <h3>5. Shipping and Delivery</h3>
                            <p>Shipping terms include:</p>
                            <ul>
                                <li>Risk of loss passes upon delivery to carrier</li>
                                <li>Delivery times are estimates only</li>
                                <li>International customers responsible for customs duties</li>
                                <li>We're not liable for carrier delays</li>
                            </ul>
                            
                            <h3>6. Returns and Refunds</h3>
                            <p>Our return policy:</p>
                            <ul>
                                <li><strong>Plants:</strong> 14-day guarantee from delivery</li>
                                <li><strong>Tools/Equipment:</strong> 30-day return period</li>
                                <li><strong>Seeds:</strong> Non-returnable for safety reasons</li>
                                <li><strong>Subscription Boxes:</strong> Return unopened boxes within 7 days</li>
                                <li><strong>Processing Time:</strong> Refunds processed within 14 business days</li>
                            </ul>
                            
                            <h3>7. Intellectual Property</h3>
                            <p>All content on our website is owned by Gardens or its licensors, including:</p>
                            <ul>
                                <li>Text, graphics, logos, and images</li>
                                <li>Software and code</li>
                                <li>Gardening guides and content</li>
                                <li>Product designs and packaging</li>
                            </ul>
                            
                            <h3>8. User Content</h3>
                            <p>By submitting content (photos, reviews, comments), you grant us:</p>
                            <ul>
                                <li>Non-exclusive, royalty-free license to use</li>
                                <li>Right to modify, publish, and distribute</li>
                                <li>Permission to use for marketing purposes</li>
                            </ul>
                            
                            <h3>9. Limitation of Liability</h3>
                            <p>Gardens is not liable for:</p>
                            <ul>
                                <li>Indirect, incidental, or consequential damages</li>
                                <li>Loss of profits or data</li>
                                <li>Damages exceeding amount paid for products</li>
                                <li>Third-party actions or products</li>
                            </ul>
                            
                            <h3>10. Governing Law</h3>
                            <p>These terms are governed by English law. Disputes shall be resolved in courts of England.</p>
                            
                            <h3>11. Changes to Terms</h3>
                            <p>We may modify these terms at any time. Continued use after changes constitutes acceptance.</p>
                        </div>
                    `;
                    break;

                case 'shipping-policy':
                    content = `
                        <img src="https://images.unsplash.com/photo-1566576721346-d4a3b4eaeb55?w=800&h=500&fit=crop" alt="Shipping Policy" class="modal-image">
                        <div class="content-text">
                            <h2>Shipping Policy</h2>
                            <p><strong>Last Updated:</strong> January 15, 2026</p>
                            
                            <h3>1. Shipping Destinations</h3>
                            <p>We currently ship to the following regions:</p>
                            <ul>
                                <li><strong>Europe:</strong> All EU countries plus UK, Switzerland, Norway</li>
                                <li><strong>Asia:</strong> Japan, South Korea, Singapore, Taiwan, Hong Kong</li>
                                <li><strong>Oceania:</strong> Australia, New Zealand</li>
                                <li><strong>North America:</strong> USA, Canada</li>
                            </ul>
                            <p>Some remote locations may have shipping restrictions.</p>
                            
                            <h3>2. Shipping Methods & Times</h3>
                            <p>We offer two shipping options:</p>
                            <ul>
                                <li><strong>Standard Shipping:</strong> 5-10 business days</li>
                                <li><strong>Express Shipping:</strong> 2-5 business days</li>
                            </ul>
                            
                            <h3>3. Shipping Costs</h3>
                            <table style="width: 100%; border-collapse: collapse; margin: 1.5rem 0;">
                                <thead>
                                    <tr>
                                        <th style="padding: 1rem; background: var(--light-sage); text-align: left;">Region</th>
                                        <th style="padding: 1rem; background: var(--light-sage); text-align: left;">Standard</th>
                                        <th style="padding: 1rem; background: var(--light-sage); text-align: left;">Express</th>
                                        <th style="padding: 1rem; background: var(--light-sage); text-align: left;">Free Shipping Over</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">Europe</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€7.99</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€14.99</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€50</td>
                                    </tr>
                                    <tr>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">Asia</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€12.99</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€24.99</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€75</td>
                                    </tr>
                                    <tr>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">Oceania</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€15.99</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€29.99</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">€100</td>
                                    </tr>
                                    <tr>
                                        <td style="padding: 1rem;">North America</td>
                                        <td style="padding: 1rem;">€14.99</td>
                                        <td style="padding: 1rem;">€27.99</td>
                                        <td style="padding: 1rem;">€90</td>
                                    </tr>
                                </tbody>
                            </table>
                            
                            <h3>4. Plant Shipping Special Instructions</h3>
                            <p>Live plants require special handling:</p>
                            <ul>
                                <li>Shipped Monday-Wednesday to avoid weekend delays</li>
                                <li>Temperature-controlled packaging in extreme weather</li>
                                <li>Water-retaining gel for roots during transit</li>
                                <li>Clear unpacking instructions included</li>
                                <li>48-hour plant guarantee upon delivery</li>
                            </ul>
                            
                            <h3>5. International Shipping Notes</h3>
                            <ul>
                                <li><strong>Customs Duties:</strong> Customer's responsibility</li>
                                <li><strong>Import Restrictions:</strong> Check local regulations for plants/seeds</li>
                                <li><strong>Phytosanitary Certificates:</strong> Provided for all international plant shipments</li>
                                <li><strong>Delivery Delays:</strong> Possible due to customs processing</li>
                            </ul>
                            
                            <h3>6. Order Processing Time</h3>
                            <p>Orders are processed within:</p>
                            <ul>
                                <li><strong>Standard Orders:</strong> 1-2 business days</li>
                                <li><strong>Custom Orders:</strong> 3-5 business days</li>
                                <li><strong>Subscription Boxes:</strong> Processed on your billing date</li>
                                <li><strong>Weekends/Holidays:</strong> Not counted as business days</li>
                            </ul>
                            
                            <h3>7. Tracking Your Order</h3>
                            <p>You'll receive:</p>
                            <ul>
                                <li>Order confirmation email immediately</li>
                                <li>Shipping confirmation with tracking number</li>
                                <li>Delivery notification when out for delivery</li>
                                <li>Access to real-time tracking via carrier website</li>
                            </ul>
                            
                            <h3>8. Failed Deliveries</h3>
                            <p>If delivery fails:</p>
                            <ul>
                                <li>Carrier will attempt delivery 3 times</li>
                                <li>Package held at local depot for pickup</li>
                                <li>Returned to us after 10 days</li>
                                <li>Restocking fee may apply for returns</li>
                            </ul>
                            
                            <h3>9. Damaged or Lost Packages</h3>
                            <p>Contact us immediately if:</p>
                            <ul>
                                <li>Package arrives damaged</li>
                                <li>Items are missing</li>
                                <li>Tracking shows delivered but not received</li>
                                <li>Plants arrive in poor condition</li>
                            </ul>
                            <p>We'll resolve within 48 hours.</p>
                        </div>
                    `;
                    break;

                case 'accessibility':
                    content = `
                        <img src="https://images.unsplash.com/photo-1545235617-9465d2a55698?w=800&h=500&fit=crop" alt="Accessibility Statement" class="modal-image">
                        <div class="content-text">
                            <h2>Accessibility Statement</h2>
                            <p><strong>Last Updated:</strong> January 15, 2026</p>
                            
                            <h3>Our Commitment</h3>
                            <p>Gardens is committed to ensuring digital accessibility for people with disabilities. We are continually improving the user experience for everyone and applying relevant accessibility standards.</p>
                            
                            <h3>Conformance Status</h3>
                            <p>We aim to conform to the Web Content Accessibility Guidelines (WCAG) 2.1 Level AA. These guidelines explain how to make web content more accessible for people with disabilities.</p>
                            
                            <h3>Accessibility Features</h3>
                            <p>Our website includes the following accessibility features:</p>
                            <ul>
                                <li><strong>Keyboard Navigation:</strong> Full site navigation using keyboard only</li>
                                <li><strong>Screen Reader Compatibility:</strong> Compatible with major screen readers</li>
                                <li><strong>Text Alternatives:</strong> Alt text for all meaningful images</li>
                                <li><strong>Color Contrast:</strong> Minimum contrast ratio of 4.5:1</li>
                                <li><strong>Resizable Text:</strong> Text can be resized up to 200% without loss of functionality</li>
                                <li><strong>Focus Indicators:</strong> Clear focus states for all interactive elements</li>
                                <li><strong>Skip Links:</strong> Skip to main content links available</li>
                                <li><strong>ARIA Labels:</strong> Proper ARIA labels for complex elements</li>
                            </ul>
                            
                            <h3>Accessible Gardening Products</h3>
                            <p>We offer products designed for accessibility:</p>
                            <ul>
                                <li><strong>Raised Garden Beds:</strong> At wheelchair-appropriate heights</li>
                                <li><strong>Ergonomic Tools:</strong> Designed for limited hand mobility</li>
                                <li><strong>Audio Guides:</strong> Planting instructions in audio format</li>
                                <li><strong>Braille Seed Packets:</strong> Available upon request</li>
                                <li><strong>Large Print Guides:</strong> Gardening instructions in large print</li>
                            </ul>
                            
                            <h3>Feedback and Support</h3>
                            <p>We welcome your feedback on the accessibility of our website and products. Please let us know if you encounter accessibility barriers:</p>
                            <ul>
                                <li><strong>Email:</strong> accessibility@gardens.com</li>
                                <li><strong>Phone:</strong> +44 20 1234 5678 (text relay service available)</li>
                                <li><strong>Mail:</strong> Gardens Accessibility Team, 123 Green Street, London, UK</li>
                            </ul>
                            
                            <h3>Technical Specifications</h3>
                            <p>Accessibility of our website relies on the following technologies:</p>
                            <ul>
                                <li>HTML</li>
                                <li>WAI-ARIA</li>
                                <li>CSS</li>
                                <li>JavaScript</li>
                            </ul>
                            
                            <h3>Assessment Approach</h3>
                            <p>We assess accessibility through:</p>
                            <ul>
                                <li>Regular automated testing</li>
                                <li>Manual testing by our team</li>
                                <li>User testing with people with disabilities</li>
                                <li>Expert accessibility audits annually</li>
                            </ul>
                            
                            <h3>Compatibility</h3>
                            <p>Our website is designed to be compatible with:</p>
                            <ul>
                                <li>Latest versions of major browsers</li>
                                <li>Assistive technologies including screen readers</li>
                                <li>Mobile devices and tablets</li>
                                <li>Operating systems with accessibility features</li>
                            </ul>
                            
                            <h3>Ongoing Improvements</h3>
                            <p>We are continuously working to improve accessibility by:</p>
                            <ul>
                                <li>Training staff on accessibility requirements</li>
                                <li>Implementing user feedback</li>
                                <li>Staying current with WCAG updates</li>
                                <li>Regular accessibility reviews of new content</li>
                            </ul>
                        </div>
                    `;
                    break;

                case 'cookie-policy':
                    content = `
                        <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=800&h=500&fit=crop" alt="Cookie Policy" class="modal-image">
                        <div class="content-text">
                            <h2>Cookie Policy</h2>
                            <p><strong>Last Updated:</strong> January 15, 2026</p>
                            
                            <h3>1. What Are Cookies?</h3>
                            <p>Cookies are small text files that are placed on your device when you visit our website. They help the website remember information about your visit, which can make it easier to visit the site again and make the site more useful to you.</p>
                            
                            <h3>2. How We Use Cookies</h3>
                            <p>We use cookies for the following purposes:</p>
                            <table style="width: 100%; border-collapse: collapse; margin: 1.5rem 0;">
                                <thead>
                                    <tr>
                                        <th style="padding: 1rem; background: var(--light-sage); text-align: left;">Cookie Type</th>
                                        <th style="padding: 1rem; background: var(--light-sage); text-align: left;">Purpose</th>
                                        <th style="padding: 1rem; background: var(--light-sage); text-align: left;">Duration</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);"><strong>Essential</strong></td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">Site functionality, shopping cart, security</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">Session</td>
                                    </tr>
                                    <tr>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);"><strong>Preferences</strong></td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">Remember your settings, theme choice, language</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">1 year</td>
                                    </tr>
                                    <tr>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);"><strong>Analytics</strong></td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">Understand how visitors use our site</td>
                                        <td style="padding: 1rem; border-bottom: 1px solid var(--light-sage);">2 years</td>
                                    </tr>
                                    <tr>
                                        <td style="padding: 1rem;"><strong>Marketing</strong></td>
                                        <td style="padding: 1rem;">Show relevant gardening content and offers</td>
                                        <td style="padding: 1rem;">90 days</td>
                                    </tr>
                                </tbody>
                            </table>
                            
                            <h3>3. Essential Cookies</h3>
                            <p>These cookies are necessary for the website to function and cannot be switched off. They include:</p>
                            <ul>
                                <li><strong>Session Cookies:</strong> Maintain your login state and shopping cart</li>
                                <li><strong>Security Cookies:</strong> Protect against malicious activities</li>
                                <li><strong>Load Balancing Cookies:</strong> Distribute traffic across servers</li>
                                <li><strong>Cookie Consent:</strong> Remember your cookie preferences</li>
                            </ul>
                            
                            <h3>4. Performance Cookies</h3>
                            <p>These cookies help us understand how visitors interact with our website:</p>
                            <ul>
                                <li><strong>Google Analytics:</strong> Tracks page views, time on site, bounce rates</li>
                                <li><strong>Heatmaps:</strong> Shows where users click and scroll</li>
                                <li><strong>A/B Testing:</strong> Tests different website versions</li>
                                <li><strong>Error Tracking:</strong> Identifies and fixes website errors</li>
                            </ul>
                            
                            <h3>5. Functional Cookies</h3>
                            <p>These enable enhanced functionality and personalization:</p>
                            <ul>
                                <li><strong>Theme Preference:</strong> Remembers your light/dark mode choice</li>
                                <li><strong>Language Settings:</strong> Stores your preferred language</li>
                                <li><strong>Garden Zone:</strong> Remembers your climate zone for relevant advice</li>
                                <li><strong>Recently Viewed:</strong> Shows plants and products you've viewed</li>
                            </ul>
                            
                            <h3>6. Advertising Cookies</h3>
                            <p>These cookies may be set through our site by advertising partners:</p>
                            <ul>
                                <li><strong>Retargeting:</strong> Shows relevant ads on other sites</li>
                                <li><strong>Social Media:</strong> Enables social sharing and tracking</li>
                                <li><strong>Affiliate Marketing:</strong> Tracks referrals from partner sites</li>
                                <li><strong>Conversion Tracking:</strong> Measures ad campaign effectiveness</li>
                            </ul>
                            
                            <h3>7. Third-Party Cookies</h3>
                            <p>Some cookies are placed by third parties, including:</p>
                            <ul>
                                <li><strong>Payment Processors:</strong> Stripe, PayPal for secure payments</li>
                                <li><strong>Social Media:</strong> Facebook, Instagram, Pinterest buttons</li>
                                <li><strong>Video Services:</strong> YouTube for gardening tutorials</li>
                                <li><strong>Map Services:</strong> Google Maps for nursery locations</li>
                            </ul>
                            
                            <h3>8. Managing Cookies</h3>
                            <p>You can control cookies through:</p>
                            <ul>
                                <li><strong>Browser Settings:</strong> Most browsers allow you to refuse cookies</li>
                                <li><strong>Cookie Consent Banner:</strong> Manage preferences when you first visit</li>
                                <li><strong>Opt-Out Tools:</strong> Industry opt-out programs for advertising</li>
                                <li><strong>Do Not Track:</strong> Some browsers support "Do Not Track" signals</li>
                            </ul>
                            
                            <h3>9. Cookie Lifespan</h3>
                            <p>Cookies have different lifespans:</p>
                            <ul>
                                <li><strong>Session Cookies:</strong> Expire when you close your browser</li>
                                <li><strong>Persistent Cookies:</strong> Remain until expiration date or deletion</li>
                                <li><strong>First-Party Cookies:</strong> Set by our domain</li>
                                <li><strong>Third-Party Cookies:</strong> Set by other domains</li>
                            </ul>
                            
                            <h3>10. Updates to This Policy</h3>
                            <p>We may update this Cookie Policy periodically. We encourage you to review this page for the latest information on our cookie practices.</p>
                        </div>
                    `;
                    break;

                case 'blog':
                    content = `
                        <img src="https://images.unsplash.com/photo-1416879595882-3373a0480b5b?w=800&h=500&fit=crop" alt="Gardening Blog" class="modal-image">
                        <div class="content-text">
                            <h2>Gardens Blog</h2>
                            <p>Tips, stories, and inspiration from our community</p>
                            
                            <div class="content-grid">
                                <div>
                                    <h3>📝 Featured Articles</h3>
                                    <ul>
                                        <li><strong>Getting Started with Winter Gardening</strong><br>Learn how to grow fresh produce even in cold months</li>
                                        <li><strong>Companion Planting Guide</strong><br>Which plants grow well together for maximum yield</li>
                                        <li><strong>5 Easy Herbs for Beginners</strong><br>Start your herb garden with these foolproof plants</li>
                                        <li><strong>Creating a Pollinator-Friendly Garden</strong><br>Attract bees and butterflies to your space</li>
                                        <li><strong>Water-Wise Gardening Tips</strong><br>Conserve water while keeping your garden lush</li>
                                    </ul>
                                </div>
                                <div>
                                    <h3>🎥 Video Tutorials</h3>
                                    <ul>
                                        <li><strong>Pruning Fruit Trees</strong><br>Step-by-step guide for healthy trees</li>
                                        <li><strong>Building a Raised Bed</strong><br>DIY project for weekend gardeners</li>
                                        <li><strong>Seed Starting Masterclass</strong><br>From seed to seedling success</li>
                                        <li><strong>Organic Pest Control</strong><br>Natural solutions for common pests</li>
                                        <li><strong>Composting Made Easy</strong><br>Turn waste into garden gold</li>
                                    </ul>
                                </div>
                            </div>
                            
                            <h3>🌱 Seasonal Guides</h3>
                            <p>Our comprehensive seasonal guides help you make the most of every gardening season:</p>
                            <ul>
                                <li><strong>Spring Planting Calendar:</strong> What to plant and when</li>
                                <li><strong>Summer Garden Maintenance:</strong> Keeping your garden thriving in heat</li>
                                <li><strong>Fall Harvest Guide:</strong> Preserving and storing your bounty</li>
                                <li><strong>Winter Garden Prep:</strong> Getting ready for next season</li>
                            </ul>
                            
                            <h3>👩‍🌾 Community Stories</h3>
                            <p>Read inspiring stories from our gardening community:</p>
                            <ul>
                                <li><strong>Urban Rooftop Transformation:</strong> How Maria created a green oasis in the city</li>
                                <li><strong>School Garden Project:</strong> Teaching children about growing food</li>
                                <li><strong>Senior Gardening Program:</strong> Therapeutic gardening for older adults</li>
                                <li><strong>Community Allotment Success:</strong> How neighbors transformed a vacant lot</li>
                            </ul>
                            
                            <h3>📚 Expert Q&A</h3>
                            <p>Our gardening experts answer your questions:</p>
                            <ul>
                                <li><strong>Soil Health:</strong> Testing and improving your soil</li>
                                <li><strong>Plant Diseases:</strong> Identifying and treating common issues</li>
                                <li><strong>Container Gardening:</strong> Maximizing small spaces</li>
                                <li><strong>Organic Certification:</strong> What it means for home gardeners</li>
                            </ul>
                            
                            <h3>📅 Upcoming Events</h3>
                            <ul>
                                <li><strong>Virtual Garden Tour:</strong> Monthly showcase of member gardens</li>
                                <li><strong>Seed Swap Events:</strong> Exchange seeds with fellow gardeners</li>
                                <li><strong>Workshop Wednesdays:</strong> Live gardening workshops</li>
                                <li><strong>Q&A Sessions:</strong> Ask our experts anything</li>
                            </ul>
                            
                            <h3>🔔 Subscribe to Our Newsletter</h3>
                            <p>Get weekly gardening tips, seasonal advice, and exclusive content delivered to your inbox.</p>
                        </div>
                    `;
                    break;

                // Additional activity modals from original files
                case 'greenhouse-tips':
                    content = `
                        <img src="https://images.unsplash.com/photo-1530836369250-ef72a3f5cda8?w=800&h=500&fit=crop" alt="Greenhouse Tips" class="modal-image">
                        <div class="content-text">
                            <h2>Greenhouse Tips</h2>
                            <p>Expert advice for maximizing your greenhouse potential year-round</p>
                            
                            <h3>Temperature Control</h3>
                            <ul>
                                <li><strong>Ventilation:</strong> Install automatic vents to prevent overheating</li>
                                <li><strong>Heating:</strong> Use thermostatically controlled heaters for cold nights</li>
                                <li><strong>Shading:</strong> Apply shade paint or use shade cloth in summer</li>
                                <li><strong>Insulation:</strong> Use bubble wrap on north-facing walls in winter</li>
                            </ul>
                            
                            <h3>Seasonal Planting Guide</h3>
                            <ul>
                                <li><strong>Winter:</strong> Start hardy vegetables and flowers</li>
                                <li><strong>Spring:</strong> Begin tender vegetables and annuals</li>
                                <li><strong>Summer:</strong> Grow heat-loving crops like tomatoes and peppers</li>
                                <li><strong>Autumn:</strong> Extend growing season with salads and herbs</li>
                            </ul>
                            
                            <h3>Pest Management</h3>
                            <p>Greenhouses can attract specific pests. Here's how to manage them naturally:</p>
                            <ul>
                                <li><strong>Aphids:</strong> Introduce ladybugs or use soap spray</li>
                                <li><strong>Whitefly:</strong> Use yellow sticky traps</li>
                                <li><strong>Spider Mites:</strong> Increase humidity and use predatory mites</li>
                                <li><strong>Slugs:</strong> Use beer traps or copper tape</li>
                            </ul>
                            
                            <h3>Watering Systems</h3>
                            <p>Efficient watering is crucial in greenhouses:</p>
                            <ul>
                                <li><strong>Drip Irrigation:</strong> Most efficient for individual plants</li>
                                <li><strong>Capillary Matting:</strong> Great for seedlings and cuttings</li>
                                <li><strong>Misting Systems:</strong> Ideal for propagation areas</li>
                                <li><strong>Water Butts:</strong> Collect rainwater for sustainable watering</li>
                            </ul>
                        </div>
                    `;
                    break;

                case 'maintenance-advice':
                    content = `
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSDZNFiXi6Z-d_SrkjBAVVd9__-bctMGDCbmw&s" alt="Maintenance Advice" class="modal-image">
                        <div class="content-text">
                            <h2>Maintenance Advice</h2>
                            <p>Keep your garden healthy with professional maintenance guidance</p>
                            
                            <h3>Soil Health</h3>
                            <ul>
                                <li><strong>Testing:</strong> Test soil pH and nutrients annually</li>
                                <li><strong>Amending:</strong> Add compost or organic matter each season</li>
                                <li><strong>Aeration:</strong> Aerate compacted soil to improve drainage</li>
                                <li><strong>Mulching:</strong> Apply mulch to retain moisture and suppress weeds</li>
                            </ul>
                            
                            <h3>Tool Maintenance</h3>
                            <p>Well-maintained tools work better and last longer:</p>
                            <ul>
                                <li><strong>Cleaning:</strong> Clean tools after each use to prevent disease spread</li>
                                <li><strong>Sharpening:</strong> Sharpen blades regularly for clean cuts</li>
                                <li><strong>Oiling:</strong> Oil metal parts to prevent rust</li>
                                <li><strong>Storage:</strong> Store tools in dry, organized space</li>
                            </ul>
                            
                            <h3>Seasonal Maintenance Schedule</h3>
                            <ul>
                                <li><strong>Spring:</strong> Clean beds, divide perennials, fertilize</li>
                                <li><strong>Summer:</strong> Regular watering, deadheading, pest monitoring</li>
                                <li><strong>Autumn:</strong> Clean up, plant bulbs, prepare for winter</li>
                                <li><strong>Winter:</strong> Plan, order seeds, maintain structures</li>
                            </ul>
                            
                            <h3>Problem Solving</h3>
                            <p>Common garden problems and solutions:</p>
                            <ul>
                                <li><strong>Poor Drainage:</strong> Add organic matter or create raised beds</li>
                                <li><strong>Nutrient Deficiencies:</strong> Use specific fertilizers based on soil test</li>
                                <li><strong>Compacted Soil:</strong> Aerate and add compost</li>
                                <li><strong>Pest Outbreaks:</strong> Identify pests early and use targeted controls</li>
                            </ul>
                        </div>
                    `;
                    break;

                case 'allotment-jobs':
                    content = `
                        <img src="https://images.unsplash.com/photo-1466692476868-aef1dfb1e735?w=800&h=500&fit=crop" alt="Allotment Jobs" class="modal-image">
                        <div class="content-text">
                            <h2>Allotment Jobs</h2>
                            <p>Practical tips for maintaining productive allotment spaces</p>
                            
                            <h3>Monthly Allotment Tasks</h3>
                            <div class="month-grid">
                                <div class="month-card">
                                    <h3>🌱 Spring Tasks</h3>
                                    <ul>
                                        <li>Prepare seedbeds</li>
                                        <li>Sow early vegetables</li>
                                        <li>Plant potatoes</li>
                                        <li>Weed and mulch</li>
                                    </ul>
                                </div>
                                <div class="month-card">
                                    <h3>☀️ Summer Tasks</h3>
                                    <ul>
                                        <li>Water consistently</li>
                                        <li>Harvest regularly</li>
                                        <li>Sow succession crops</li>
                                        <li>Control pests</li>
                                    </ul>
                                </div>
                            </div>
                            
                            <h3>Crop Rotation Planning</h3>
                            <p>Prevent disease and maintain soil fertility with proper rotation:</p>
                            <ul>
                                <li><strong>Year 1:</strong> Potatoes and tomatoes (Solanaceae)</li>
                                <li><strong>Year 2:</strong> Beans and peas (Legumes)</li>
                                <li><strong>Year 3:</strong> Brassicas (cabbage, broccoli, kale)</li>
                                <li><strong>Year 4:</strong> Root vegetables (carrots, beets, onions)</li>
                            </ul>
                            
                            <h3>Composting on Allotments</h3>
                            <ul>
                                <li><strong>Materials:</strong> Vegetable scraps, garden waste, cardboard</li>
                                <li><strong>Turning:</strong> Turn compost every 4-6 weeks</li>
                                <li><strong>Using:</strong> Ready compost in 6-12 months</li>
                                <li><strong>Benefits:</strong> Improves soil, reduces waste, saves money</li>
                            </ul>
                        </div>
                    `;
                    break;

                case 'photo-competitions':
                    content = `
                        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSo6TAItljN06ZYSH4nj46wvu3GD1qOFF59dA&s" alt="Photo Competitions" class="modal-image">
                        <div class="content-text">
                            <h2>Photo Competitions</h2>
                            <p>Share your garden beauty and win prizes in seasonal contests</p>
                            
                            <h3>Upcoming Competitions</h3>
                            <ul>
                                <li><strong>Spring Blossom:</strong> March 1-31, 2026 (Prize: Premium tools set)</li>
                                <li><strong>Summer Harvest:</strong> July 1-31, 2026 (Prize: Year's subscription)</li>
                                <li><strong>Autumn Colors:</strong> October 1-31, 2026 (Prize: Garden makeover)</li>
                                <li><strong>Winter Wonderland:</strong> December 1-31, 2026 (Prize: Greenhouse kit)</li>
                            </ul>
                            
                            <h3>How to Enter</h3>
                            <ol>
                                <li>Take high-quality photos of your garden</li>
                                <li>Submit through our website or mobile app</li>
                                <li>Include garden details and story</li>
                                <li>Vote for your favorite entries</li>
                            </ol>
                            
                            <h3>Photo Tips</h3>
                            <ul>
                                <li><strong>Lighting:</strong> Shoot during golden hour (sunrise/sunset)</li>
                                <li><strong>Composition:</strong> Use rule of thirds for balanced shots</li>
                                <li><strong>Focus:</strong> Ensure plants are sharp and in focus</li>
                                <li><strong>Details:</strong> Capture close-ups of flowers and textures</li>
                            </ul>
                        </div>
                    `;
                    break;

                case 'seasonal-surveys':
                    content = `
                        <img src="https://images.unsplash.com/photo-1542601906990-b4d3fb778b09?w=800&h=500&fit=crop" alt="Seasonal Surveys" class="modal-image">
                        <div class="content-text">
                            <h2>Seasonal Surveys</h2>
                            <p>Contribute to our community knowledge base with your experiences</p>
                            
                            <h3>Current Surveys</h3>
                            <ul>
                                <li><strong>Spring Planting Survey:</strong> What are you growing this season?</li>
                                <li><strong>Pollinator Watch:</strong> Track bees and butterflies in your garden</li>
                                <li><strong>Weather Impact Study:</strong> How is climate affecting your garden?</li>
                                <li><strong>Organic Practices Survey:</strong> Share your sustainable gardening methods</li>
                            </ul>
                            
                            <h3>Why Participate?</h3>
                            <ul>
                                <li>Contribute to gardening research</li>
                                <li>Get personalized advice based on your data</li>
                                <li>Compare your experiences with other gardeners</li>
                                <li>Help improve gardening products and services</li>
                                <li>Earn rewards and recognition</li>
                            </ul>
                            
                            <h3>How It Works</h3>
                            <ol>
                                <li>Join our citizen science program</li>
                                <li>Complete simple monthly surveys</li>
                                <li>Share photos and observations</li>
                                <li>Receive personalized reports</li>
                                <li>Contribute to collective knowledge</li>
                            </ol>
                        </div>
                    `;
                    break;

                case 'advice-talks':
                    content = `
                        <img src="https://goglobal.com/wp-content/uploads/2025/01/Success-in-Africa.png" alt="Online Advice Talks" class="modal-image">
                        <div class="content-text">
                            <h2>Online Advice Talks</h2>
                            <p>Join live sessions with gardening experts and community members</p>
                            
                            <h3>Upcoming Talks</h3>
                            <ul>
                                <li><strong>Organic Pest Control:</strong> March 15, 2026 (Expert: Dr. Green)</li>
                                <li><strong>Container Gardening:</strong> April 12, 2026 (Expert: Urban Gardener)</li>
                                <li><strong>Soil Health Masterclass:</strong> May 10, 2026 (Expert: Soil Scientist)</li>
                                <li><strong>Seasonal Planting Guide:</strong> June 14, 2026 (Expert: Master Gardener)</li>
                            </ul>
                            
                            <h3>How to Join</h3>
                            <ol>
                                <li>Register for free on our website</li>
                                <li>Receive Zoom link via email</li>
                                <li>Join 5 minutes before start time</li>
                                <li>Ask questions during Q&A session</li>
                                <li>Access recording if you miss live session</li>
                            </ol>
                            
                            <h3>Topics Covered</h3>
                            <ul>
                                <li>Seasonal gardening tasks</li>
                                <li>Problem-solving specific issues</li>
                                <li>New gardening techniques</li>
                                <li>Product reviews and recommendations</li>
                                <li>Community Q&A sessions</li>
                            </ul>
                        </div>
                    `;
                    break;

                default:
                    content = `<h2>Content Loading...</h2>`;
            }
            
            modalContent.innerHTML = content;
            modalOverlay.classList.add('active');
            document.body.style.overflow = 'hidden';
            
            // Initialize FAQ toggles if present
            setTimeout(() => {
                document.querySelectorAll('.faq-question').forEach(question => {
                    question.addEventListener('click', function() {
                        toggleFaq(this);
                    });
                });
            }, 100);
        }

        function closeModal() {
            modalOverlay.classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        function toggleFaq(element) {
            const faqItem = element.parentElement;
            faqItem.classList.toggle('active');
        }

        // Close modal when clicking outside content
        modalOverlay.addEventListener('click', (e) => {
            if (e.target === modalOverlay) {
                closeModal();
            }
        });

        // Close modal with Escape key
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape' && modalOverlay.classList.contains('active')) {
                closeModal();
            }
        });

        // Form Submission Handler
        const contactForm = document.querySelector('.contact-form');
        if (contactForm) {
            contactForm.addEventListener('submit', (e) => {
                e.preventDefault();
                
                // Get form data
                const formData = new FormData(contactForm);
                const data = Object.fromEntries(formData);
                
                // Here you would normally send to backend
                console.log('Form submitted:', data);
                
                // Show success message
                const successMessage = document.createElement('div');
                successMessage.className = 'success-message';
                successMessage.style.cssText = `
                    position: fixed;
                    top: 50%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    background: var(--primary-green);
                    color: white;
                    padding: 2rem 3rem;
                    border-radius: 12px;
                    box-shadow: 0 8px 30px var(--shadow);
                    z-index: 10000;
                    text-align: center;
                    animation: fadeInUp 0.5s ease-out;
                `;
                successMessage.innerHTML = `
                    <h3 style="margin-bottom: 0.5rem;">Thank You!</h3>
                    <p>We'll get back to you within 24 hours.</p>
                `;
                document.body.appendChild(successMessage);
                
                // Remove message after 3 seconds
                setTimeout(() => {
                    successMessage.style.animation = 'fadeOut 0.5s ease-out';
                    setTimeout(() => {
                        successMessage.remove();
                    }, 500);
                }, 3000);
                
                // Reset form
                contactForm.reset();
            });
        }

        // Subscribe Button Handlers
        const subscribeButtons = document.querySelectorAll('.subscribe-btn');
        subscribeButtons.forEach(btn => {
            btn.addEventListener('click', () => {
                const boxName = btn.closest('.box-card').querySelector('h3').textContent;
                
                const modal = document.createElement('div');
                modal.className = 'subscription-modal';
                modal.style.cssText = `
                    position: fixed;
                    top: 0;
                    left: 0;
                    width: 100%;
                    height: 100%;
                    background: rgba(0, 0, 0, 0.7);
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    z-index: 10000;
                    animation: fadeIn 0.3s ease-out;
                `;
                
                modal.innerHTML = `
                    <div style="
                        background: var(--card-bg);
                        padding: 3rem;
                        border-radius: 16px;
                        max-width: 500px;
                        text-align: center;
                        animation: fadeInUp 0.5s ease-out;
                    ">
                        <h2 style="color: var(--primary-green); margin-bottom: 1rem; font-family: 'Fraunces', serif;">Subscribe to ${boxName}</h2>
                        <p style="color: var(--text-primary); margin-bottom: 2rem;">Start your gardening journey with ${boxName}!</p>
                        <form class="subscription-form">
                            <input type="email" placeholder="Enter your email" required style="
                                width: 100%;
                                padding: 1rem;
                                border: 2px solid var(--light-sage);
                                border-radius: 8px;
                                margin-bottom: 1rem;
                                font-size: 1rem;
                                background: var(--bg-primary);
                                color: var(--text-primary);
                            ">
                            <button type="submit" style="
                                width: 100%;
                                padding: 1rem;
                                background: var(--primary-green);
                                color: white;
                                border: none;
                                border-radius: 50px;
                                font-size: 1.1rem;
                                font-weight: 600;
                                cursor: pointer;
                                margin-bottom: 1rem;
                            ">Subscribe Now</button>
                            <button type="button" class="close-modal" style="
                                background: transparent;
                                border: none;
                                color: var(--text-secondary);
                                cursor: pointer;
                                font-size: 1rem;
                            ">Cancel</button>
                        </form>
                    </div>
                `;
                
                document.body.appendChild(modal);
                
                modal.querySelector('.close-modal').addEventListener('click', () => {
                    modal.remove();
                });
                
                modal.addEventListener('click', (e) => {
                    if (e.target === modal) {
                        modal.remove();
                    }
                });
                
                modal.querySelector('.subscription-form').addEventListener('submit', (e) => {
                    e.preventDefault();
                    alert(`Thank you for subscribing to ${boxName}! Check your email for confirmation.`);
                    modal.remove();
                });
            });
        });

        // Intersection Observer for Animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe elements for animation
        document.querySelectorAll('.box-card, .activity-card, .feature, .gallery-item, .testimonial-card, .quick-link-card').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
            observer.observe(el);
        });

        // Initialize by showing home page
        showPage('home');
    </script>
</body>
</html>
