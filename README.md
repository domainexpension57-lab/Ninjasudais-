<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anime Life - Your Ultimate Anime Destination</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://accounts.google.com/gsi/client" async defer></script>
    <script src="https://cdn.jsdelivr.net/npm/jwt-decode@3/build/jwt-decode.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: #fff;
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            padding: 30px 0;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            color: #ff6b6b;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        .tagline {
            font-size: 1.2rem;
            opacity: 0.9;
        }

        .nav-menu {
            display: flex;
            justify-content: center;
            list-style: none;
            gap: 2rem;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .nav-menu a {
            color: white;
            text-decoration: none;
            padding: 10px 20px;
            border-radius: 30px;
            background: rgba(255, 255, 255, 0.1);
            transition: all 0.3s;
        }

        .nav-menu a:hover {
            background: rgba(255, 107, 107, 0.7);
            transform: translateY(-3px);
        }

        .article-container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }

        .article-header {
            margin-bottom: 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            padding-bottom: 15px;
        }

        .article-title {
            font-size: 2.2rem;
            margin-bottom: 10px;
            color: #ffd166;
        }

        .article-meta {
            display: flex;
            justify-content: space-between;
            color: #ccc;
            font-size: 0.9rem;
            margin-bottom: 10px;
        }

        .article-content p {
            margin-bottom: 20px;
            font-size: 1.1rem;
        }

        .highlight {
            background: rgba(255, 209, 102, 0.2);
            padding: 15px;
            border-left: 4px solid #ffd166;
            margin: 20px 0;
            border-radius: 0 8px 8px 0;
        }

        .btn {
            display: inline-block;
            background: #ff6b6b;
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 600;
            transition: all 0.3s ease;
            text-decoration: none;
            box-shadow: 0 4px 10px rgba(255, 107, 107, 0.3);
        }

        .btn:hover {
            background: #ff5252;
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(255, 107, 107, 0.4);
        }

        .btn-large {
            padding: 15px 35px;
            font-size: 1.1rem;
        }

        .btn-container {
            text-align: center;
            margin: 30px 0;
        }

        /* Google Sign-In Button Styling */
        .google-signin-container {
            display: flex;
            justify-content: center;
            margin: 20px 0;
        }

        .policy-text {
            margin-top: 20px;
            font-size: 14px;
            color: #ccc;
            text-align: center;
            max-width: 400px;
            margin-left: auto;
            margin-right: auto;
        }

        .policy-text a {
            color: #ffd166;
            text-decoration: none;
            margin: 0 8px;
        }

        .policy-text a:hover {
            text-decoration: underline;
        }

        /* WhatsApp Button */
        .whatsapp-float {
            position: fixed;
            bottom: 25px;
            right: 25px;
            background: #25D366;
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            box-shadow: 0 4px 15px rgba(37, 211, 102, 0.5);
            z-index: 100;
            transition: all 0.3s;
            text-decoration: none;
        }

        .whatsapp-float:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 20px rgba(37, 211, 102, 0.7);
        }

        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: #ccc;
            font-size: 0.9rem;
        }

        .user-info {
            display: none;
            align-items: center;
            justify-content: center;
            gap: 15px;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 15px;
            margin-top: 20px;
            flex-direction: column;
        }

        .user-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: #ff6b6b;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            color: white;
            overflow: hidden;
        }

        .user-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .user-details {
            text-align: center;
        }

        .user-name {
            font-size: 1.5rem;
            font-weight: 600;
            margin-bottom: 5px;
        }

        .user-email {
            font-size: 1rem;
            opacity: 0.8;
            margin-bottom: 15px;
        }

        .logout-btn {
            background: transparent;
            border: 1px solid #ff6b6b;
            color: #ff6b6b;
            padding: 8px 20px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .logout-btn:hover {
            background: rgba(255, 107, 107, 0.1);
        }

        /* Anime Sections */
        .anime-section {
            display: none;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }

        .anime-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.2);
            padding-bottom: 15px;
        }

        .naruto-logo {
            font-size: 2.5rem;
            color: #ff9500;
            margin-right: 20px;
        }

        .onepiece-logo {
            font-size: 2.5rem;
            color: #ff0000;
            margin-right: 20px;
        }

        .dbz-logo {
            font-size: 2.5rem;
            color: #ffcc00;
            margin-right: 20px;
        }

        .anime-title {
            font-size: 2.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }

        .naruto-title {
            color: #ff9500;
        }

        .onepiece-title {
            color: #ff0000;
        }

        .dbz-title {
            color: #ffcc00;
        }

        .character-section {
            margin: 30px 0;
        }

        .character-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .character-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 20px;
            transition: transform 0.3s;
        }

        .character-card:hover {
            transform: translateY(-5px);
        }

        .character-name {
            font-size: 1.5rem;
            color: #ffd166;
            margin-bottom: 10px;
        }

        .arc-list {
            list-style-type: none;
            margin: 20px 0;
        }

        .arc-list li {
            padding: 10px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .back-btn {
            background: #ff9500;
            margin-top: 20px;
        }

        .back-btn:hover {
            background: #e08500;
        }

        .onepiece-back-btn {
            background: #ff0000;
        }

        .onepiece-back-btn:hover {
            background: #cc0000;
        }

        .dbz-back-btn {
            background: #ffcc00;
            color: #333;
        }

        .dbz-back-btn:hover {
            background: #e6b800;
        }

        .table-of-contents {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
        }

        .toc-title {
            font-size: 1.5rem;
            color: #ffd166;
            margin-bottom: 15px;
        }

        .toc-list {
            list-style-type: none;
            columns: 2;
        }

        .toc-list li {
            margin-bottom: 8px;
        }

        .toc-list a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
        }

        .toc-list a:hover {
            color: #ffd166;
        }

        .section-title {
            font-size: 2rem;
            color: #ffd166;
            margin: 30px 0 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid rgba(255, 209, 102, 0.3);
        }

        .sub-section {
            margin-left: 20px;
            margin-bottom: 20px;
        }

        .sub-title {
            font-size: 1.5rem;
            color: #ffd166;
            margin: 20px 0 10px;
        }

        .saga-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .saga-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 20px;
        }

        .saga-title {
            font-size: 1.3rem;
            color: #ffd166;
            margin-bottom: 10px;
        }

        .transformation-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .transformation-card {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            padding: 15px;
            border-left: 4px solid #ffcc00;
        }

        .transformation-name {
            font-size: 1.2rem;
            color: #ffcc00;
            margin-bottom: 8px;
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2.2rem;
            }
            
            .article-title {
                font-size: 1.8rem;
            }
            
            .article-meta {
                flex-direction: column;
            }
            
            .nav-menu {
                flex-direction: column;
                align-items: center;
            }
            
            .character-grid, .saga-grid, .transformation-grid {
                grid-template-columns: 1fr;
            }
            
            .toc-list {
                columns: 1;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Anime Life</h1>
            <p class="tagline">Your source for the latest anime news and updates</p>
            
            <ul class="nav-menu">
                <li><a href="#" id="homeLink">Home</a></li>
                <li><a href="#" id="jjkLink">Jujutsu Kaisen</a></li>
                <li><a href="#" id="narutoLink">Naruto</a></li>
                <li><a href="#" id="onepieceLink">One Piece</a></li>
                <li><a href="#" id="dragonballLink">Dragon Ball Z</a></li>
            </ul>
        </header>

        <main>
            <!-- JJK Article Section -->
            <section id="jjkSection" class="article-container">
                <div class="article-header">
                    <h2 class="article-title">Jujutsu Kaisen season 3 announces January 2026 release with new PV and visual</h2>
                    <div class="article-meta">
                        <span>By Mudassir Kamran</span>
                        <span>Modified Aug 31, 2025 13:27 GMT</span>
                    </div>
                </div>

                <div class="article-content">
                    <p>Jujutsu Kaisen season 3 is officially set to premiere in January 2026, sending a rush of excitement through fans across the globe. In addition to the announcement, a brand new promotional video and visuals were released as well, highlighting some of the dark, action-packed storyline.</p>
                    
                    <div class="highlight">
                        The season will adapt the fan-favorite Culling Game arc, the next arc in Gege Akutami's well-received manga. In this arc, survival and explosive battles are the main focus of the series.
                    </div>
                    
                    <p>The previous seasons of Jujutsu Kaisen have led up to this particular arc, giving Jujutsu Kaisen season 3 the potential to be one of the most exhilarating arcs in the whole series.</p>
                    
                    <h3>Jujutsu Kaisen season 3 finally confirmed the January 2026 release date</h3>
                    
                    <p>On August 31, 2025, the 5th Anniversary Special Program for Jujutsu Kaisen aired at 9:30 PM JST and unveiled a series of major updates for the franchise. The heart of the event was the announcement of Jujutsu Kaisen season 3, titled Culling Game Part 1, coming in January 2026.</p>
                    
                    <p>Additionally, fans got a new promo video and key visual, providing glimpses of the battles and shadows of this arc and storyline arc. Included in the announcement was an additional surprise, a theatrical release. Titled Jujutsu Kaisen the Movie: Shibuya Incident - Special Edition, a re-edited movie of season 2's Shibuya Incident arc comes complete with a preview of the upcoming Culling Game.</p>
                </div>
            </section>

            <!-- Naruto Section -->
            <section id="narutoSection" class="anime-section">
                <!-- Naruto content would go here -->
                <div class="anime-header">
                    <div class="naruto-logo">
                        <i class="fas fa-leaf"></i>
                    </div>
                    <h2 class="anime-title naruto-title">Naruto</h2>
                </div>
                <div class="article-content">
                    <p>Naruto content would be displayed here...</p>
                </div>
                <div class="btn-container">
                    <button class="btn back-btn" id="backFromNaruto">
                        <i class="fas fa-arrow-left"></i> Back to Home
                    </button>
                </div>
            </section>

            <!-- One Piece Section -->
            <section id="onepieceSection" class="anime-section">
                <!-- One Piece content would go here -->
                <div class="anime-header">
                    <div class="onepiece-logo">
                        <i class="fas fa-skull-crossbones"></i>
                    </div>
                    <h2 class="anime-title onepiece-title">One Piece</h2>
                </div>
                <div class="article-content">
                    <p>One Piece content would be displayed here...</p>
                </div>
                <div class="btn-container">
                    <button class="btn back-btn onepiece-back-btn" id="backFromOnepiece">
                        <i class="fas fa-arrow-left"></i> Back to Home
                    </button>
                </div>
            </section>

            <!-- Dragon Ball Z Section -->
            <section id="dbzSection" class="anime-section">
                <div class="anime-header">
                    <div class="dbz-logo">
                        <i class="fas fa-dragon"></i>
                    </div>
                    <h2 class="anime-title dbz-title">Dragon Ball Z</h2>
                </div>

                <div class="article-content">
                    <!-- Table of Contents -->
                    <div class="table-of-contents">
                        <h3 class="toc-title">Contents</h3>
                        <ul class="toc-list">
                            <li><a href="#dbz-overview">Overview</a></li>
                            <li><a href="#dbz-sagas">Sagas</a></li>
                            <li><a href="#dbz-characters">Main Characters</a></li>
                            <li><a href="#dbz-transformations">Transformations</a></li>
                            <li><a href="#dbz-legacy">Legacy</a></li>
                        </ul>
                    </div>

                    <h3 id="dbz-overview" class="section-title">Dragon Ball Z Overview</h3>
                    <p>Dragon Ball Z is the sequel to the original Dragon Ball anime and adapts the final 325 chapters of the Dragon Ball manga created by Akira Toriyama. The series first aired in Japan on Fuji TV from April 1989 to January 1996, spanning 291 episodes.</p>
                    
                    <div class="highlight">
                        Dragon Ball Z continues the adventures of Son Goku and his friends, defending Earth against an array of villains including aliens, androids, and magical creatures. The series is famous for its intense battles, power-ups, and the introduction of the Super Saiyan transformation.
                    </div>

                    <h3 id="dbz-sagas" class="section-title">Dragon Ball Z Sagas</h3>
                    
                    <div class="saga-grid">
                        <div class="saga-card">
                            <h4 class="saga-title">Saiyan Saga</h4>
                            <p>The arrival of Raditz reveals Goku's Saiyan heritage and sets the stage for the arrival of Vegeta and Nappa. Features the first major character death and the introduction of power levels.</p>
                        </div>
                        
                        <div class="saga-card">
                            <h4 class="saga-title">Frieza Saga</h4>
                            <p>The battle on Planet Namek against the galactic tyrant Frieza. Features the first Super Saiyan transformation and some of the most iconic moments in anime history.</p>
                        </div>
                        
                        <div class="saga-card">
                            <h4 class="saga-title">Cell Saga</h4>
                            <p>The emergence of the bio-android Cell and his quest to become perfect. Introduces Future Trunks and features the Cell Games tournament.</p>
                        </div>
                        
                        <div class="saga-card">
            
