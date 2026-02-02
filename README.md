# valanwmuah
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For You ❤️</title>
    <style>
        /* THE STYLING (CSS) */
        body {
            margin: 0;
            background-color: #ffdae0; /* Soft Pink */
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
        }

        .card {
            background: white;
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: center;
            z-index: 100;
            max-width: 400px;
        }

        h1 { color: #d63384; }
        p { color: #555; }

        .btn-container {
            margin-top: 30px;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        button {
            padding: 12px 25px;
            border: none;
            border-radius: 50px;
            font-size: 18px;
            cursor: pointer;
            transition: 0.3s;
        }

        #yesBtn { background-color: #ff4d6d; color: white; font-weight: bold; }
        #noBtn { background-color: #eee; color: #444; }

        /* RSVP Form */
        #rsvpSection { display: none; }
        input, textarea {
            width: 100%;
            margin: 10px 0;
            padding: 10px;
            border: 1px solid #ffc0cb;
            border-radius: 10px;
        }

        /* Floating Hearts */
        .heart {
            position: absolute;
            color: #ff8fa3;
            animation: floatUp 4s linear infinite;
            pointer-events: none;
        }

        @keyframes floatUp {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="card" id="mainCard">
        <div id="askSection">
            <h1>Will you be my Valentine? ❤️</h1>
            <p>I promise it'll be fun!</p>
            <div class="btn-container">
                <button id="yesBtn" onclick="showRSVP()">Yes!</button>
                <button id="noBtn" onmouseover="moveNo()">No</button>
            </div>
        </div>

        <div id="rsvpSection">
            <h1>Yay! 🥰</h1>
            <p>Send me a quick note!</p>
            <form action="https://formspree.io/f/YOUR_ID_HERE" method="POST">
                <input type="text" name="name" placeholder="Your Name" required>
                <textarea name="message" placeholder="What's on your mind?" required></textarea>
                <button type="submit" style="background:#d63384; color:white; width:100%;">Send ✨</button>
            </form>
        </div>
    </div>

    <script>
        /* THE LOGIC (JS) */
        function moveNo() {
            const btn = document.getElementById('noBtn');
            const x = Math.random() * (window.innerWidth - btn.offsetWidth);
            const y = Math.random() * (window.innerHeight - btn.offsetHeight);
            btn.style.position = 'absolute';
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        function showRSVP() {
            document.getElementById('askSection').style.display = 'none';
            document.getElementById('rsvpSection').style.display = 'block';
            setInterval(createHeart, 100);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 4000);
        }
        setInterval(createHeart, 400);
    </script>
</body>
</html>
