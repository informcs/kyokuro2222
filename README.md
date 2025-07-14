<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>รับจ้างเขียนโปรแกรม & เกม | Developer Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: #0a0a0a;
            color: #fff;
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Stars Background */
        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .star {
            position: absolute;
            width: 2px;
            height: 2px;
            background: white;
            border-radius: 50%;
            animation: twinkle 2s infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }

        /* Shooting Stars */
        .shooting-star {
            position: fixed;
            width: 2px;
            height: 2px;
            background: #00ffff;
            border-radius: 50%;
            box-shadow: 0 0 6px #00ffff;
            animation: shoot 3s linear infinite;
            z-index: 2;
        }

        @keyframes shoot {
            0% {
                transform: translateX(-100px) translateY(-100px);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateX(100vw) translateY(100vh);
                opacity: 0;
            }
        }

        /* Floating Particles */
        .particle {
            position: fixed;
            width: 4px;
            height: 4px;
            background: linear-gradient(45deg, #00ffff, #ff00ff);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
            z-index: 2;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(180deg); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            position: relative;
            z-index: 10;
        }

        /* Header */
        header {
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px);
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            padding: 1rem 0;
            border-bottom: 1px solid #00ffff;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: #00ffff;
            text-decoration: none;
            text-shadow: 0 0 10px #00ffff;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #ff00ff;
            text-shadow: 0 0 5px #ff00ff;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            position: relative;
            background: radial-gradient(circle at 50% 50%, #1a1a2e 0%, #0a0a0a 100%);
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                linear-gradient(45deg, transparent 30%, rgba(0, 255, 255, 0.1) 50%, transparent 70%),
                linear-gradient(-45deg, transparent 30%, rgba(255, 0, 255, 0.1) 50%, transparent 70%);
            animation: neonFlow 3s ease-in-out infinite alternate;
        }

        @keyframes neonFlow {
            0% { opacity: 0.5; transform: translateX(-50px); }
            100% { opacity: 1; transform: translateX(50px); }
        }

        .hero-content {
            position: relative;
            z-index: 1;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            text-shadow: 0 0 20px #00ffff;
            color: #00ffff;
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .cta-button {
            background: linear-gradient(45deg, #00ffff, #ff00ff);
            color: #000;
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-block;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.5);
        }

        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 0 30px rgba(255, 0, 255, 0.8);
        }

        /* Services Section */
        .services {
            padding: 5rem 0;
            background: #0f0f0f;
            position: relative;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: #00ffff;
            text-shadow: 0 0 10px #00ffff;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .service-card {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s, box-shadow 0.3s;
            border: 1px solid #00ffff;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.2);
        }

        .service-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 0 25px rgba(255, 0, 255, 0.4);
            border-color: #ff00ff;
        }

        .service-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #fff;
        }

        /* Skills Section */
        .skills {
            padding: 5rem 0;
            background: #0a0a0a;
            color: white;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .skill-item {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            padding: 1.5rem;
            border-radius: 10px;
            text-align: center;
            backdrop-filter: blur(10px);
            border: 1px solid #00ffff;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.3);
            transition: all 0.3s;
        }

        .skill-item:hover {
            border-color: #ff00ff;
            box-shadow: 0 0 25px rgba(255, 0, 255, 0.5);
        }

        .skill-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        /* Portfolio Section */
        .portfolio {
            padding: 5rem 0;
            background: #0f0f0f;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .portfolio-item {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.2);
            transition: transform 0.3s;
            border: 1px solid #00ffff;
        }

        .portfolio-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 0 30px rgba(255, 0, 255, 0.4);
            border-color: #ff00ff;
        }

        .portfolio-image {
            height: 200px;
            background: linear-gradient(45deg, #00ffff, #ff00ff);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            color: #000;
        }

        .portfolio-content {
            padding: 1.5rem;
        }

        .portfolio-content h3 {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            color: #00ffff;
        }

        .portfolio-content p {
            color: #ccc;
            margin-bottom: 1rem;
        }

        .tech-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .tech-tag {
            background: linear-gradient(45deg, #00ffff, #ff00ff);
            color: #000;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
        }

        /* Contact Section */
        .contact {
            padding: 5rem 0;
            background: #0a0a0a;
            color: white;
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            padding: 2rem;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid #00ffff;
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.3);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #00ffff;
            text-shadow: 0 0 5px #00ffff;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #00ffff;
            border-radius: 5px;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            font-size: 1rem;
            transition: all 0.3s;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            outline: none;
            border-color: #ff00ff;
            box-shadow: 0 0 10px rgba(255, 0, 255, 0.5);
        }

        .form-group input::placeholder,
        .form-group textarea::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        .submit-btn {
            background: linear-gradient(45deg, #00ffff, #ff00ff);
            color: #000;
            padding: 1rem 2rem;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            width: 100%;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.5);
        }

        .submit-btn:hover {
            box-shadow: 0 0 25px rgba(255, 0, 255, 0.8);
            transform: translateY(-2px);
        }

        /* Success Message */
        .success-message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            color: #00ffff;
            padding: 2rem;
            border-radius: 15px;
            border: 1px solid #00ffff;
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.5);
            z-index: 2000;
            display: none;
            text-align: center;
        }

        .success-message.show {
            display: block;
            animation: popIn 0.5s ease-out;
        }

        @keyframes popIn {
            0% { transform: translate(-50%, -50%) scale(0.8); opacity: 0; }
            100% { transform: translate(-50%, -50%) scale(1); opacity: 1; }
        }

        /* Footer */
        footer {
            background: #000;
            color: white;
            text-align: center;
            padding: 2rem 0;
            border-top: 1px solid #00ffff;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .nav-links {
                display: none;
            }
            
            .services-grid,
            .portfolio-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Stars Background -->
    <div class="stars" id="stars"></div>

    <header>
        <nav class="container">
            <a href="#" class="logo">⚡ Kyokuro222</a>
            <ul class="nav-links">
                <li><a href="#home">หน้าแรก</a></li>
                <li><a href="#services">บริการ</a></li>
                <li><a href="#skills">ความเชี่ยวชาญ</a></li>
                <li><a href="#portfolio">ผลงาน</a></li>
                <li><a href="#contact">ติดต่อ</a></li>
            </ul>
        </nav>
    </header>

    <section class="hero" id="home">
        <div class="hero-content">
            <h1>รับจ้างเขียนโปรแกรม & เกม</h1>
            <p>พัฒนาแอปพลิเคชัน เว็บไซต์ และเกมคุณภาพสูง<br>ด้วยเทคโนโลยีล่าสุด</p>
            <a href="#contact" class="cta-button">ติดต่อเลย</a>
        </div>
    </section>

    <section class="services" id="services">
        <div class="container">
            <h2 class="section-title">บริการของเรา</h2>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">🌐</div>
                    <h3>เว็บแอปพลิเคชัน</h3>
                    <p>พัฒนาเว็บไซต์และเว็บแอปพลิเคชันที่ทันสมัย รองรับทุกอุปกรณ์ ใช้งานง่าย</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">📱</div>
                    <h3>แอปพลิเคชัน</h3>
                    <p>สร้างแอปพลิเคชันสำหรับธุรกิจ ระบบจัดการ และเครื่องมือต่างๆ</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">🎮</div>
                    <h3>เกม</h3>
                    <p>พัฒนาเกมคุณภาพสูง ทั้งแบบ 2D และ 3D สำหรับทุกแพลตฟอร์ม</p>
                </div>
                <div class="service-card">
                    <div class="service-icon">🤖</div>
                    <h3>ระบบอัตโนมัติ</h3>
                    <p>สร้างบอท สคริปต์ และระบบอัตโนมัติเพื่อเพิ่มประสิทธิภาพ</p>
                </div>
            </div>
        </div>
    </section>

    <section class="skills" id="skills">
        <div class="container">
            <h2 class="section-title">ความเชี่ยวชาญ</h2>
            <div class="skills-grid">
                <div class="skill-item">
                    <div class="skill-icon">🟨</div>
                    <h3>JavaScript</h3>
                    <p>Frontend & Backend</p>
                </div>
                <div class="skill-item">
                    <div class="skill-icon">🐍</div>
                    <h3>Python</h3>
                    <p>AI, Web, Automation</p>
                </div>
                <div class="skill-item">
                    <div class="skill-icon">⚡</div>
                    <h3>C++</h3>
                    <p>Game Development</p>
                </div>
                <div class="skill-item">
                    <div class="skill-icon">🟢</div>
                    <h3>Node.js</h3>
                    <p>Backend Development</p>
                </div>
                <div class="skill-item">
                    <div class="skill-icon">🌙</div>
                    <h3>Lua</h3>
                    <p>Scripting & Gaming</p>
                </div>
            </div>
        </div>
    </section>

    <section class="portfolio" id="portfolio">
        <div class="container">
            <h2 class="section-title">ผลงานตัวอย่าง</h2>
            <div class="portfolio-grid">
                <div class="portfolio-item">
                    <div class="portfolio-image">🛒</div>
                    <div class="portfolio-content">
                        <h3>ระบบ E-commerce</h3>
                        <p>เว็บไซต์ขายของออนไลน์ครบครัน พร้อมระบบการชำระเงินและจัดการสต็อก</p>
                        <div class="tech-tags">
                            <span class="tech-tag">JavaScript</span>
                            <span class="tech-tag">Node.js</span>
                            <span class="tech-tag">Python</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="portfolio-image">🎮</div>
                    <div class="portfolio-content">
                        <h3>เกม RPG 2D</h3>
                        <p>เกมผจญภัยแฟนตาซี พร้อมระบบการต่อสู้ เควส และคาแรคเตอร์</p>
                        <div class="tech-tags">
                            <span class="tech-tag">C++</span>
                            <span class="tech-tag">Lua</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="portfolio-image">📊</div>
                    <div class="portfolio-content">
                        <h3>ระบบจัดการข้อมูล</h3>
                        <p>แดชบอร์ดสำหรับการจัดการข้อมูล พร้อมกราฟและรีพอร์ต</p>
                        <div class="tech-tags">
                            <span class="tech-tag">Python</span>
                            <span class="tech-tag">JavaScript</span>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="portfolio-image">🤖</div>
                    <div class="portfolio-content">
                        <h3>บอทอัตโนมัติ</h3>
                        <p>บอทสำหรับการทำงานอัตโนมัติ ตอบข้อความ และจัดการงาน</p>
                        <div class="tech-tags">
                            <span class="tech-tag">Python</span>
                            <span class="tech-tag">Node.js</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="contact" id="contact">
        <div class="container">
            <h2 class="section-title">ติดต่อเรา</h2>
            <div class="contact-form">
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">ชื่อ</label>
                        <input type="text" id="name" name="name" placeholder="ชื่อของคุณ" required>
                    </div>
                    <div class="form-group">
                        <label for="email">อีเมล</label>
                        <input type="email" id="email" name="email" placeholder="อีเมลของคุณ" required>
                    </div>
                    <div class="form-group">
                        <label for="project">ประเภทงาน</label>
                        <select id="project" name="project" required>
                            <option value="">เลือกประเภทงาน</option>
                            <option value="web">เว็บไซต์/เว็บแอป</option>
                            <option value="app">แอปพลิเคชัน</option>
                            <option value="game">เกม</option>
                            <option value="automation">ระบบอัตโนมัติ</option>
                            <option value="other">อื่นๆ</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="message">รายละเอียด</label>
                        <textarea id="message" name="message" rows="5" placeholder="อธิบายงานที่ต้องการ งบประมาณ และเวลา" required></textarea>
                    </div>
                    <button type="submit" class="submit-btn">ส่งข้อความ</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Success Message -->
    <div class="success-message" id="successMessage">
        <h3>🚀 ส่งข้อความสำเร็จแล้ว!</h3>
        <p>ขอบคุณที่ติดต่อเรา เราจะตอบกลับเร็วๆ นี้ 😊</p>
    </div>

    <footer>
        <div class="container">
            <p>&copy; 2024 Kyokuro222. Crafting digital experiences with neon soul 🌟⚡</p>
        </div>
    </footer>

    <script>
        // Create stars background
        function createStars() {
            const starsContainer = document.getElementById('stars');
            const starCount = 150;
            
            for (let i = 0; i < starCount; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.animationDelay = Math.random() * 2 + 's';
                star.style.animationDuration = (Math.random() * 3 + 2) + 's';
                starsContainer.appendChild(star);
            }
        }

        // Create shooting stars
        function createShootingStar() {
            const shootingStar = document.createElement('div');
            shootingStar.className = 'shooting-star';
            shootingStar.style.left = Math.random() * 100 + '%';
            shootingStar.style.top = Math.random() * 100 + '%';
            shootingStar.style.animationDuration = (Math.random() * 2 + 1) + 's';
            document.body.appendChild(shootingStar);
            
            setTimeout(() => {
                shootingStar.remove();
            }, 3000);
        }

        // Create floating particles
        function createParticles() {
            const particleCount = 20;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.animationDuration = (Math.random() * 4 + 4) + 's';
                document.body.appendChild(particle);
            }
        }

        // Initialize space effects
        createStars();
        createParticles();
        
        // Create shooting stars periodically
        setInterval(createShootingStar, 2000);

        // Smooth scrolling with particle effects
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                // Create particles when navigating
                for (let i = 0; i < 5; i++) {
                    setTimeout(() => {
                        const particle = document.createElement('div');
                        particle.className = 'particle';
                        particle.style.left = Math.random() * 100 + '%';
                        particle.style.top = Math.random() * 100 + '%';
                        particle.style.animationDuration = '1s';
                        document.body.appendChild(particle);
                        
                        setTimeout(() => particle.remove(), 1000);
                    }, i * 100);
                }
                
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Form submission with EmailJS
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form data
            const formData = new FormData(this);
            const data = {
                name: formData.get('name'),
                email: formData.get('email'),
                project: formData.get('project'),
                message: formData.get('message')
            };
            
            // Create mailto link
            const subject = encodeURIComponent(`งาน${data.project} - ${data.name}`);
            const body = encodeURIComponent(`
ชื่อ: ${data.name}
อีเมล: ${data.email}
ประเภทงาน: ${data.project}

รายละเอียด:
${data.message}
            `);
            
            const mailtoLink = `mailto:genshinxd1138@gmail.com?subject=${subject}&body=${body}`;
            
            // Open email client
            window.location.href = mailtoLink;
            
            // Show success message
            const successMessage = document.getElementById('successMessage');
            successMessage.classList.add('show');
            
            // Create celebration particles
            for (let i = 0; i < 10; i++) {
                setTimeout(() => {
                    const particle = document.createElement('div');
                    particle.className = 'particle';
                    particle.style.left = Math.random() * 100 + '%';
                    particle.style.top = Math.random() * 100 + '%';
                    particle.style.animationDuration = '2s';
                    document.body.appendChild(particle);
                    
                    setTimeout(() => particle.remove(), 2000);
                }, i * 100);
            }
            
            // Hide success message after 3 seconds
            setTimeout(() => {
                successMessage.classList.remove('show');
            }, 3000);
            
            // Reset form
            this.reset();
        });

        // Add interactive effects to skill items
        const skillItems = document.querySelectorAll('.skill-item');
        skillItems.forEach(item => {
            item.addEventListener('mouseenter', function() {
                this.style.transform = 'scale(1.05)';
                
                // Create hover particles
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDuration = '1s';
                document.body.appendChild(particle);
                
                setTimeout(() => particle.remove(), 1000);
            });
            
            item.addEventListener('mouseleave', function() {
                this.style.transform = 'scale(1)';
            });
        });

        // Add scroll effects
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const parallax = document.querySelector('.stars');
            const speed = scrolled * 0.5;
            
            parallax.style.transform = `translateY(${speed}px)`;
        });

        // Add service card hover effects
        const serviceCards = document.querySelectorAll('.service-card');
        serviceCards.forEach(card => {
            card.addEventListener('mouseenter', function() {
                // Create sparkle effect
                for (let i = 0; i < 3; i++) {
                    setTimeout(() => {
                        const sparkle = document.createElement('div');
                        sparkle.className = 'particle';
                        sparkle.style.left = Math.random() * 100 + '%';
                        sparkle.style.top = Math.random() * 100 + '%';
                        sparkle.style.animationDuration = '0.8s';
                        document.body.appendChild(sparkle);
                        
                        setTimeout(() => sparkle.remove(), 800);
                    }, i * 100);
                }
            });
        });

        // Add portfolio item hover effects
        const portfolioItems = document.querySelectorAll('.portfolio-item');
        portfolioItems.forEach(item => {
            item.addEventListener('mouseenter', function() {
                // Create orbital effect
                const orbital = document.createElement('div');
                orbital.className = 'particle';
                orbital.style.left = '50%';
                orbital.style.top = '50%';
                orbital.style.animationDuration = '2s';
                this.appendChild(orbital);
                
                setTimeout(() => orbital.remove(), 2000);
            });
        });
    </script>
</body>
</html>
