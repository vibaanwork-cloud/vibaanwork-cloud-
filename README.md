<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vibaan Studios | Matrix Protocol</title>
    <style>
        /* 1. BASIC SETUP (Black & Green) */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Courier New', Courier, monospace; }
        body { background-color: #000; color: #00ff00; overflow-x: hidden; }
        
        /* 2. MATRIX BACKGROUND */
        canvas { display: block; position: fixed; top: 0; left: 0; z-index: -1; }

        /* 3. MAIN CONTAINER */
        .container {
            position: relative;
            width: 100%;
            max-width: 500px; /* Mobile View similar to video */
            margin: 0 auto;
            padding: 20px;
            text-align: center;
            background: rgba(0, 0, 0, 0.8); /* Thoda transparent taaki Matrix dikhe */
            min-height: 100vh;
        }

        /* 4. PROFILE IMAGE (Photo) */
        .profile-box {
            width: 150px;
            height: 150px;
            margin: 40px auto 20px;
            border-radius: 50%;
            border: 3px solid #00ff00;
            padding: 5px;
            box-shadow: 0 0 20px #00ff00;
        }
        .profile-img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            /* Yahan apni photo lagana */
            background-image: url('https://avatars.githubusercontent.com/u/156475735?v=4'); 
            background-size: cover;
        }

        /* 5. TEXT STYLES */
        h1 { font-size: 28px; letter-spacing: 2px; margin-bottom: 5px; text-shadow: 0 0 10px #00ff00; }
        p { color: #fff; font-size: 14px; margin-bottom: 20px; }
        
        .btn-main {
            display: inline-block;
            padding: 10px 20px;
            border: 2px solid #00ff00;
            color: #00ff00;
            text-decoration: none;
            font-weight: bold;
            margin-bottom: 30px;
            box-shadow: 0 0 10px #00ff00 inset;
            transition: 0.3s;
        }
        .btn-main:hover { background: #00ff00; color: #000; cursor: pointer; }

        /* 6. STATS & SERVICES (Boxes) */
        .section-title {
            border-top: 1px dashed #00ff00;
            border-bottom: 1px dashed #00ff00;
            padding: 10px;
            margin: 20px 0;
            font-size: 20px;
            letter-spacing: 3px;
        }

        .card {
            border: 1px solid #333;
            background: rgba(0, 20, 0, 0.6);
            padding: 15px;
            margin-bottom: 15px;
            text-align: left;
            border-left: 3px solid #00ff00;
        }
        .card h3 { color: #fff; margin-bottom: 5px; font-size: 16px; }
        .card p { color: #aaa; font-size: 12px; margin-bottom: 0; }

        /* Progress Bar */
        .progress-container { margin-bottom: 15px; text-align: left; }
        .progress-label { display: flex; justify-content: space-between; font-size: 12px; margin-bottom: 5px; color: #fff; }
        .progress-bar { width: 100%; height: 8px; background: #111; border: 1px solid #333; }
        .progress-fill { height: 100%; background: #00ff00; width: 0%; transition: width 2s; box-shadow: 0 0 5px #00ff00; }

        /* 7. CONNECT BUTTONS */
        .btn-group { display: flex; gap: 10px; justify-content: center; margin-top: 20px; }
        .btn-action {
            flex: 1;
            padding: 12px;
            border: 1px solid #00ff00;
            background: transparent;
            color: #fff;
            text-decoration: none;
            font-size: 14px;
            font-weight: bold;
        }
        .whatsapp { background: rgba(0, 255, 0, 0.2); }
        .email { background: rgba(255, 255, 255, 0.1); }

    </style>
</head>
<body>

    <canvas id="matrixCanvas"></canvas>

    <div class="container">
        
        <div class="profile-box">
            <div class="profile-img"></div>
        </div>

        <h1>VIBAAN STUDIOS</h1>
        <p>2D & 3D Web Development...</p>
        
        <a href="#services" class="btn-main">INITIALIZE SYSTEM</a>

        <h2 class="section-title">TECHNICAL STATS</h2>
        
        <div class="progress-container">
            <div class="progress-label"><span>PYTHON / AI DEV</span><span>98%</span></div>
            <div class="progress-bar"><div class="progress-fill" style="width: 98%"></div></div>
        </div>
        
        <div class="progress-container">
            <div class="progress-label"><span>WEB ARCHITECTURE</span><span>95%</span></div>
            <div class="progress-bar"><div class="progress-fill" style="width: 95%"></div></div>
        </div>

        <div class="progress-container">
            <div class="progress-label"><span>ETHICAL HACKING</span><span>80%</span></div>
            <div class="progress-bar"><div class="progress-fill" style="width: 80%"></div></div>
        </div>

        <h2 class="section-title" id="services">DEPLOYABLE SERVICES</h2>

        <div class="card">
            <h3>📂 CS STUDENT PROJECTS</h3>
            <p>Complete Final Year Projects (AI, Python, Web) with source code & documentation.</p>
        </div>

        <div class="card">
            <h3>🐛 CODE DEBUGGING & FIX</h3>
            <p>Expert bug fixing for Python, HTML, CSS errors. We solve runtime issues.</p>
        </div>

        <div class="card">
            <h3>🤖 PERSONAL AI (LYRA)</h3>
            <p>Custom-built Personal AI Assistants for laptop automation & security.</p>
        </div>

        <h2 class="section-title">ESTABLISH CONNECTION</h2>
        <div class="btn-group">
            <a href="#" class="btn-action whatsapp">WHATSAPP NOW</a>
            <a href="#" class="btn-action email">EMAIL</a>
        </div>

        <br><br>
        <p style="opacity: 0.5;">Vibaan Studios © 2026</p>

    </div>

    <script>
        // --- MATRIX RAIN EFFECT SCRIPT ---
        const canvas = document.getElementById('matrixCanvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const katakana = 'アァカサタナハマヤャラワガザダバパイィキシチニヒミリヰギジヂビピウゥクスツヌフムユュルグズブヅプエェケセテネヘメレヱゲゼデベペオォコソトノホモヨョロヲゴゾドボポヴッン';
        const latin = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
        const nums = '0123456789';
        const alphabet = katakana + latin + nums;

        const fontSize = 16;
        const columns = canvas.width/fontSize;
        const rainDrops = [];

        for( let x = 0; x < columns; x++ ) {
            rainDrops[x] = 1;
        }

        const draw = () => {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)'; // Black fade effect
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.fillStyle = '#0F0'; // Neon Green Text
            ctx.font = fontSize + 'px monospace';

            for(let i = 0; i < rainDrops.length; i++)
            {
                const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length));
                ctx.fillText(text, i*fontSize, rainDrops[i]*fontSize);

                if(rainDrops[i]*fontSize > canvas.height && Math.random() > 0.975){
                    rainDrops[i] = 0;
                }
                rainDrops[i]++;
            }
        };

        setInterval(draw, 30);
        
        // Resize canvas on window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
