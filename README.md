<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Portfolio | Developer Resume</title>
    
    <!-- FontAwesome for Social & Skill Icons -->
    <link rel="stylesheet" href="https://cloudflare.com">
    
    <style>
        /* CSS STYLES */
        :root {
            --primary: #2563eb;
            --secondary: #3b82f6;
            --bg-dark: #0f172a;
            --card-bg: #1e293b;
            --text-main: #f8fafc;
            --text-dim: #94a3b8;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Roboto, sans-serif;
        }

        body {
            background-color: var(--bg-dark);
            color: var(--text-main);
            line-height: 1.6;
            scroll-behavior: smooth;
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 10%;
            background: rgba(15, 23, 42, 0.95);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid #334155;
        }

        .logo { font-size: 1.5rem; font-weight: bold; color: var(--primary); }
        
        .nav-links { display: flex; list-style: none; gap: 2rem; }
        
        .nav-links a {
            text-decoration: none;
            color: var(--text-main);
            font-weight: 500;
            transition: 0.3s;
        }

        .nav-links a:hover { color: var(--primary); }

        /* Hero Section */
        #home {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 20px;
        }

        #home h1 { font-size: 3.5rem; margin-bottom: 10px; }
        
        .typewriter { color: var(--primary); border-right: 3px solid; }

        /* Sections General */
        section { padding: 80px 10%; }

        h2 {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 50px;
            position: relative;
        }

        h2::after {
            content: '';
            width: 60px;
            height: 4px;
            background: var(--primary);
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }

        /* Skills Grid */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 25px;
        }

        .card {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            text-align: center;
            transition: transform 0.3s;
            border: 1px solid transparent;
        }

        .card:hover {
            transform: translateY(-10px);
            border-color: var(--primary);
        }

        .card i { font-size: 2.5rem; color: var(--primary); margin-bottom: 15px; }

        /* Contact Form */
        form {
            max-width: 600px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        input, textarea {
            padding: 12px;
            border-radius: 6px;
            border: 1px solid #334155;
            background: #020617;
            color: white;
        }

        .btn {
            background: var(--primary);
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
        }

        .btn:hover { background: var(--secondary); }

        footer {
            text-align: center;
            padding: 40px;
            background: #020617;
            color: var(--text-dim);
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">PORTFOLIO.</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#skills">Skills</a></li>
            <li><a href="#projects">Projects</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>

    <section id="home">
        <h1>Hi, I'm <span class="highlight">krishnanand</span></h1>
        <h3>I am a <span class="typewriter" id="type-text"></span></h3>
        <p style="margin-top: 20px; max-width: 600px; color: var(--text-dim);">
            I build responsive, high-performance web applications using modern technologies.
        </p>
        <div style="margin-top: 30px;">
            <a href="#contact" class="btn" style="text-decoration:none;">Hire Me</a>
        </div>
    </section>

    <section id="skills">
        <h2>My Skills</h2>
        <div class="grid">
            <div class="card"><i class="fab fa-html5"></i><h3>HTML5</h3></div>
            <div class="card"><i class="fab fa-css3-alt"></i><h3>CSS3</h3></div>
            <div class="card"><i class="fab fa-js"></i><h3>JavaScript</h3></div>
            <div class="card"><i class="fab fa-react"></i><h3>React</h3></div>
        </div>
    </section>

    <section id="projects">
        <h2>Recent Projects</h2>
        <div class="grid" id="project-list">
            <!-- JavaScript will inject cards here -->
        </div>
    </section>

    <section id="contact">
        <h2>Contact Me</h2>
        <p> phone no. +918887958010
        email id :- krishnanandy379@gmail.com </p>
        </section>

    <footer>
        <p>&copy; 2024 Avanish. All Rights Reserved.</p>
    </footer>

    <script>
        /* JAVASCRIPT CODE */

        // 1. Typewriter Effect
        const textElement = document.getElementById('type-text');
        const phrases = ["Web Developer", "UI Designer", "Freelancer"];
        let phraseIndex = 0;
        let charIndex = 0;

        function type() {
            if (charIndex < phrases[phraseIndex].length) {
                textElement.textContent += phrases[phraseIndex].charAt(charIndex);
                charIndex++;
                setTimeout(type, 100);
            } else {
                setTimeout(erase, 2000);
            }
        }

        function erase() {
            if (charIndex > 0) {
                textElement.textContent = phrases[phraseIndex].substring(0, charIndex - 1);
                charIndex--;
                setTimeout(erase, 50);
            } else {
                phraseIndex = (phraseIndex + 1) % phrases.length;
                setTimeout(type, 500);
            }
        }

        // 2. Dynamic Project Loading
        const projects = [
            { name: "Portfolio Website", icon: "fa-code" },
            { name: "E-Commerce App", icon: "fa-shopping-cart" },
            { name: "Weather Dashboard", icon: "fa-cloud-sun" }
        ];

        const projectList = document.getElementById('project-list');
        projects.forEach(p => {
            projectList.innerHTML += `
                <div class="card">
                    <i class="fas ${p.icon}"></i>
                    <h3>${p.name}</h3>
                    <p style="font-size:0.9rem; color:#94a3b8">Modern solution with clean code.</p>
                </div>
            `;
        });

        // Start animations
        document.addEventListener("DOMContentLoaded", type);

        // Simple Form Submission Alert
        document.getElementById('contact-form').addEventListener('submit', (e) => {
            e.preventDefault();
            alert("Thank you! Your message has been sent (Demo only).");
        });
    </script>
</body>
</html>
