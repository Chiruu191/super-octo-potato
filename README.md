<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Paul's Digital Portfolio</title>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap">
    <style>
        /* Reset and base styles */
        * {
            margin: 0;
            padding: 0;	
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
            scroll-behavior: smooth; /* CSS-only smooth scrolling */
        }

        body {
            background-color: #0a0a0a;
            color: white;
            line-height: 1.6;
        }

        /* Navigation styles */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            background-color: rgba(10, 10, 10, 0.85);
            padding: 1.5rem 4rem;
            z-index: 1000;
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 20px rgba(0, 0, 0, 0.3);
        }

        nav ul {
            display: flex;
            justify-content: flex-end;
            list-style: none;
            gap: 2rem;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
            letter-spacing: 2px;
            transition: all 0.3s ease;
            padding-bottom: 5px;
            position: relative;
        }

        nav ul li a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background-color: white;
            transition: width 0.3s ease;
        }

        nav ul li a:hover::after {
            width: 100%;
        }

        nav ul li a.active::after {
            width: 100%;
        }

        /* Section styling */
        section {
            min-height: 100vh;
            padding: 8rem 4rem 5rem 4rem; /* Added top padding for nav bar */
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            width: 100%;
        }

        /* Typography */
        h1, h2 {
            font-weight: 300;
            line-height: 1.2;
            letter-spacing: -1px;
        }

        h1 {
            font-size: 4.5rem;
            margin-bottom: 2rem;
            background: linear-gradient(to right, #ffffff, #a0a0a0);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: fadeIn 1s ease-out;
        }

        h2 {
            font-size: 3.5rem;
            margin-bottom: 2rem;
            background: linear-gradient(to right, #ffffff, #a0a0a0);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        h3 {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: #f0f0f0;
        }

        p {
            color: rgba(255, 255, 255, 0.8);
            font-size: 1.05rem;
            line-height: 1.8;
            max-width: 800px;
            margin-bottom: 1.5rem;
        }

        /* Image styling */
        .image-container {
            overflow: hidden;
            border-radius: 8px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            transition: all 0.5s ease;
            position: relative;
        }

        .image-container:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.4);
        }

        .image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.8s ease;
            display: block;
        }

        .image-container:hover img {
            transform: scale(1.05);
        }

        .profile-image {
            width: 300px;
            height: 300px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            transition: all 0.3s ease;
        }

        .profile-image:hover {
            border-color: rgba(255, 255, 255, 0.3);
            transform: scale(1.03);
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 20px;
            margin-top: 30px;
        }

        .gallery-grid .image-container {
            height: 600px;
            position: relative;
            background-color: #ffffff;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .gallery-caption {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.8);
            padding: 15px;
            opacity: 1;
        }

        /* Hero section */
        .hero-content {
            display: grid;
            grid-template-columns: 1fr;
            gap: 3rem;
            align-items: center;
        }

        .name-badge {
            display: inline-block;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 9999px;
            padding: 0.75rem 1.5rem;
            font-size: 0.95rem;
            font-weight: 500;
            letter-spacing: 1px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(5px);
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .name-badge:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 16px rgba(0, 0, 0, 0.15);
            background: rgba(255, 255, 255, 0.08);
        }
        
        .name-badge p {
            margin-bottom: 0;
            color: rgba(255, 255, 255, 0.9);
        }
		
        /* About section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }

        .divider {
            width: 120px;
            height: 2px;
            background: linear-gradient(to right, rgba(255, 255, 255, 0.5), rgba(255, 255, 255, 0.1));
            margin-top: 2rem;
        }

        /* Background section */
        .background-item {
            margin-bottom: 4rem;
            animation: fadeIn 0.8s ease-out;
        }

        .background-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.5rem;
        }

        .bullet-list {
            margin-left: 2.5rem;
        }

        .bullet-list li {
            margin-bottom: 1rem;
            list-style-type: none;
            position: relative;
            padding-left: 0.5rem;
            font-size: 1.05rem;
            line-height: 1.6;
            color: rgba(255, 255, 255, 0.8);
            transition: transform 0.2s ease;
        }

        .bullet-list li:hover {
            transform: translateX(5px);
            color: rgba(255, 255, 255, 1);
        }

        .bullet-list li::before {
            content: '•';
            position: absolute;
            left: -1.5rem;
            color: rgba(255, 255, 255, 0.6);
            font-size: 1.2rem;
        }

        /* Quote section */
        .quote-content {
            display: grid;
            grid-template-columns: 1fr;
            gap: 3rem;
            align-items: center;
        }

        .quote-content h2 {
            font-style: italic;
            font-weight: 400;
            font-size: 2.8rem;
            line-height: 1.4;
            color: white;
            background: none;
            position: relative;
            padding-left: 2rem;
        }

        .quote-content h2::before {
            content: '"';
            position: absolute;
            left: 0;
            top: -1rem;
            font-size: 5rem;
            color: rgba(255, 255, 255, 0.2);
            font-family: Georgia, serif;
        }
		
        /* Contact section */
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            margin-top: 2rem;
        }

        .contact-grid div {
            background: rgba(255, 255, 255, 0.03);
            padding: 2rem;
            border-radius: 8px;
            transition: all 0.3s ease;
        }

        .contact-grid div:hover {
            background: rgba(255, 255, 255, 0.06);
            transform: translateY(-5px);
        }

        /* Email link styling */
        a {
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            transition: all 0.3s ease;
            position: relative;
            font-weight: 500;
        }
        
        a:hover {
            color: white;
        }

        a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 1px;
            bottom: -2px;
            left: 0;
            background-color: white;
            transition: width 0.3s ease;
        }

        a:hover::after {
            width: 100%;
        }

        /* Animations */
        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive styles */
        @media (max-width: 768px) {
            nav {
                padding: 1rem 2rem;
            }
            
            nav ul {
                justify-content: center;
                gap: 1rem;
            }
            
            section {
                padding: 7rem 2rem 3rem 2rem;
            }

            h1 {
                font-size: 3rem;
            }

            h2 {
                font-size: 2.5rem;
            }

            .hero-content, .quote-content, .about-content {
                grid-template-columns: 1fr;
            }

            .contact-grid, .gallery-grid {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .profile-image {
                width: 200px;
                height: 200px;
                margin: 0 auto 2rem;
                display: block;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <ul>
            <li><a href="#hero">HOME</a></li>
            <li><a href="#about" class="active">ABOUT</a></li>
            <li><a href="#background">BACKGROUND</a></li>
            <li><a href="#quote">QUOTE</a></li>
            <li><a href="#projects">PROJECTS</a></li>
            <li><a href="#contact">CONTACT</a></li>
        </ul>
    </nav>
    
    <!-- Hero Section -->
    <section id="hero">
        <div class="container">
            <div class="hero-content">
                <div>
                    <h1>Welcome to<br>My Digital<br>Portfolio</h1>
                    <div class="name-badge">
                        <p>Paul Landric L. Federez/BSIT 1-Y2-6</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about">
        <div class="container">
            <h2>Who is Paul?</h2>
            <div class="about-content">
                <div>
                    <p>I'm a passionate IT student with a keen interest in web development and digital innovation. My journey in technology began with a curiosity about how digital systems shape our world, and has evolved into a dedicated pursuit of knowledge and skills in the IT field. I thrive on creative problem-solving and am constantly exploring new technologies to expand my expertise. When I'm not coding, you might find me exploring photography, enjoying strategic games, or volunteering in tech community events.</p>
                    <div class="divider"></div>
                </div>
                <div>
                    <img src="https://scontent.fmnl30-3.fna.fbcdn.net/v/t39.30808-6/489814790_1367225264401580_8387063313234508833_n.jpg?stp=cp6_dst-jpg_tt6&_nc_cat=101&ccb=1-7&_nc_sid=6ee11a&_nc_ohc=J0zccrUf8y0Q7kNvwETCn0j&_nc_oc=Adlb9BN1H1CKru2Gi7DMHzvFqguPG2KQA9H_8NGzpDOawOMpIJjhI9UbQLSmxvd665M&_nc_zt=23&_nc_ht=scontent.fmnl30-3.fna&_nc_gid=yXrG1qc9xiOcvg9oMQUvlw&oh=00_AfFfLoDmCodvzUwpgThGXRM6fMiIX1mtwHkiK_2XVf9gzg&oe=67FD8F56" alt="Paul's Profile" class="profile-image" />
                </div>
            </div>
        </div>
    </section>

    <!-- Background Section -->
    <section id="background">
        <div class="container">
            <h2>My Background</h2>
            
            <div class="background-item">
                <div class="background-header">
                    <h3>Education</h3>
                </div>
                <ul class="bullet-list">
                    <li>Our Lady of Fatima University - Bachelor of Science in Information Technology (Current)</li>
                    <li>Mystical Rose School of Caloocan - Senior High School, TVL-ICT Track (2021-2023)</li>
                    <li>Silanganan Elementary School - Primary Education (2012-2018)</li>
                </ul>
            </div>
            
            <div class="background-item">
                <div class="background-header">
                    <h3>Skills</h3>
                </div>
                <ul class="bullet-list">
                    <li>Programming: HTML, CSS, and C++ fundamentals with a focus on algorithm development</li>
                    <li>Digital Tools: Microsoft Office, and various project management platforms</li>
                    <li>Soft Skills: Effective communication, team collaboration, and adaptive problem-solving</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Quote Section -->
    <section id="quote">
        <div class="container">
            <div class="quote-content">
                <div>
                    <h2>Technology is best when it brings people together.</h2>
                    <p>This quote by Matt Mullenweg resonates deeply with me. I believe that the true power of technology lies not just in its technical capabilities, but in its ability to connect people, solve human problems, and create meaningful experiences. This philosophy guides my approach to every project I undertake.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects">
        <div class="container">
            <h2>My Projects</h2>
            <p>Here are some of the projects I've worked on during my academic journey and personal exploration.</p>
            
            <div class="gallery-grid">
                <div class="image-container">
                    <img src="https://i.pinimg.com/736x/09/ca/e2/09cae26419be245b0a5e63b55fab37e3.jpg" alt="FOPR PROECT" />
                    <div class="gallery-caption">
                        <h3>10 DIFFERENT PROGRAMS</h3>
                        <p>C++</p>
                    </div>
					<div class="image-container">
                    <img src="https://i.pinimg.com/736x/7b/7b/49/7b7b493630ea995aa300e8542f7d8e81.jpg" alt="Mobile App Design" />
                    <div class="gallery-caption">
                        <h3>Source Code</h3>
						<p>C++</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <div class="container">
            <h2>Reach Out<br>to Me</h2>
            <div class="contact-grid">
                <div>
                    <h3>Address</h3>
                    <p>Phase 3, Package 2, Block 33, Lot 4, Bagong Silang, Caloocan City, Philippines</p>
                </div>
                
                <div>
                    <h3>Email</h3>
                    <p><a href="mailto:plfederez1816qc@student.fatima.edu.ph">plfederez1816qc@student.fatima.edu.ph</a></p>
                </div>
                
                <div>
                    <h3>Phone</h3>
                    <p>(+63) 992 433 5088</p>
                </div>
            </div>
        </div>
    </section>
</body>
</html>
