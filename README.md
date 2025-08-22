
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
   
    <style>
        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            background-color: #000;
            color: #fff;
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            position: relative;
        }

        .glitter-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, rgba(255, 0, 127, 0.1) 0%, rgba(0, 0, 0, 0) 70%);
            animation: moveGlitter 10s linear infinite alternate;
            z-index: -2;
        }
        
        @keyframes moveGlitter {
            from {
                background-position: 0% 0%;
            }
            to {
                background-position: 100% 100%;
            }
        }

        .content {
            text-align: center;
            z-index: 1;
        }

        h1 {
            font-size: 5em;
            text-shadow: 0 0 10px #e60073, 0 0 20px #e60073, 0 0 30px #e60073;
        }
        
        h2 {
            font-size: 2.5em;
            text-shadow: 0 0 5px #e60073;
            margin-top: -30px;
        }

        h3 {
            font-size: 1.8em;
            text-shadow: 0 0 5px #e60073;
            margin-top: -20px;
        }

        .falling-heart {
            position: absolute;
            top: -50px;
            background-color: red;
            animation: fall linear infinite;
            pointer-events: none;
            filter: drop-shadow(0 0 5px #ff007f);
        }

        .falling-heart::before,
        .falling-heart::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: inherit;
        }

        .falling-heart::before {
            transform: rotate(-45deg);
            border-radius: 50% 50% 0 0;
            left: -50%;
        }

        .falling-heart::after {
            transform: rotate(45deg);
            border-radius: 50% 50% 0 0;
            top: -50%;
        }

        @keyframes fall {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="glitter-bg"></div>
    
    <div class="content">
        <h1>Aku Sayang Tara</h1>
        <h2>Dari Agasta</h2>
        <h3>Maafin aku ya sayang</h3>
    </div>
    
    <script>
        function createFallingHeart() {
            const heart = document.createElement('div');
            heart.classList.add('falling-heart');
            
            // Randomize starting position and size
            const size = Math.random() * 20 + 10;
            heart.style.width = `${size}px`;
            heart.style.height = `${size}px`;
            heart.style.left = `${Math.random() * 100}vw`;
            
            // Randomize animation duration and delay
            const duration = Math.random() * 5 + 5; // 5 to 10 seconds
            const delay = Math.random() * 5; // 0 to 5 seconds
            heart.style.animationDuration = `${duration}s`;
            heart.style.animationDelay = `${delay}s`;

            document.body.appendChild(heart);

            // Remove heart after it has fallen
            setTimeout(() => {
                heart.remove();
            }, (duration + delay) * 1000);
        }

        // Generate hearts continuously
        setInterval(createFallingHeart, 100);
    </script>
</body>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&display=swap');

        body {
            margin: 0;
            padding: 0;
            overflow: hidden;
            background-color: #000;
            color: #fff;
            font-family: 'Dancing Script', cursive;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            cursor: none; /* Menyembunyikan kursor bawaan */
        }
        
        .content {
            text-align: center;
            z-index: 1;
        }

        h1 {
            font-size: 6em;
            text-shadow: 0 0 10px #ff007f, 0 0 20px #ff007f, 0 0 30px #ff007f;
            animation: pulse 3s infinite ease-in-out;
        }

        .heart-particle {
            position: fixed;
            background-color: transparent;
            width: 15px;
            height: 15px;
            pointer-events: none;
            opacity: 0;
            animation: floatUp 5s forwards;
            filter: drop-shadow(0 0 5px #ff007f);
        }

        .heart-particle::before,
        .heart-particle::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: #ff007f;
            border-radius: 50% 50% 0 0;
        }

        .heart-particle::before {
            transform: rotate(-45deg);
            left: -50%;
        }

        .heart-particle::after {
            transform: rotate(45deg);
            top: -50%;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(0.5);
                opacity: 1;
            }
            100% {
                transform: translateY(-80vh) scale(1.5);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <script>
        document.addEventListener('mousemove', function(e) {
            const heart = document.createElement('div');
            heart.classList.add('heart-particle');
            heart.style.left = `${e.clientX}px`;
            heart.style.top = `${e.clientY}px`;
            
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 5000); // Hapus partikel setelah 5 detik
        });
    </script>
</body>
</html>
</html>
