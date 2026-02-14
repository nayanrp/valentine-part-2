
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For You</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #ffb7c5; /* Light Pink Background */
            height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            font-family: 'Arial', sans-serif;
        }

        /* The Gift Box */
        #gift-container {
            cursor: pointer;
            transition: transform 0.3s ease;
            z-index: 10;
        }

        #gift-container:hover {
            transform: scale(1.1) rotate(5deg);
        }

        .gift-emoji {
            font-size: 80px;
            filter: drop-shadow(0 10px 10px rgba(0,0,0,0.2));
            animation: bounce 2s infinite;
        }

        .click-text {
            margin-top: 10px;
            color: #d63384;
            font-weight: bold;
            font-size: 18px;
            text-align: center;
        }

        /* The Surprise Content (Hidden initially) */
        #surprise-container {
            display: none; /* Hidden by default */
            flex-direction: column;
            align-items: center;
            text-align: center;
            width: 100%;
            height: 100%;
            position: relative;
            z-index: 5;
            padding-top: 50px; 
            opacity: 0;
            transition: opacity 1s ease-in;
        }

        /* Anime Bouquet Image Styling */
        .bouquet-img {
            width: 280px; /* Adjust size as needed */
            max-width: 80%;
            border-radius: 15px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.15);
            margin-bottom: 20px;
            border: 5px solid white;
        }

        /* The Note */
        .note {
            background-color: rgba(255, 255, 255, 0.8);
            padding: 20px 40px;
            border-radius: 20px;
            font-size: 24px;
            color: #d6336c;
            font-family: 'Brush Script MT', cursive; /* Romantic font */
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            max-width: 80%;
        }

        /* The Peeking Cat at the bottom */
        .cat-container {
            position: absolute;
            bottom: -10px; /* Slight overlap to look like it's hanging */
            left: 50%;
            transform: translateX(-50%);
            z-index: 6;
        }
        
        .cat-img {
            width: 150px;
            transition: transform 0.3s ease;
        }
        
        .cat-img:hover {
            transform: translateY(-20px); /* Cat pops up when hovered */
        }

        /* Animations */
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
            40% {transform: translateY(-20px);}
            60% {transform: translateY(-10px);}
        }

        /* Falling Flowers (Sakura) */
        .petal {
            position: absolute;
            top: -10px;
            background-color: #ff69b4;
            border-radius: 100% 0 100% 0;
            opacity: 0.8;
            z-index: 1;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to {
                transform: translateY(105vh) rotate(720deg);
            }
        }

    </style>
</head>
<body>

    <div id="gift-container" onclick="openGift()">
        <div class="gift-emoji">🎁</div>
        <div class="click-text">Click me!</div>
    </div>

    <div id="surprise-container">
        
        <img src="https://i.pinimg.com/originals/96/6d/40/966d40e396dc1ee3650eb1df86a34791.gif" alt="Anime Bouquet" class="bouquet-img">

        <div class="note">
            That you are so beautiful... ❤️
        </div>

        <div class="cat-container">
            <img src="https://media.tenor.com/images/a44415510664923e100e4e7e6f851034/tenor.gif" alt="Cute Cat" class="cat-img">
        </div>

    </div>

    <script>
        function openGift() {
            const giftBox = document.getElementById('gift-container');
            const surprise = document.getElementById('surprise-container');

            // Hide gift, show surprise
            giftBox.style.display = 'none';
            surprise.style.display = 'flex';
            
            // Fade in effect
            setTimeout(() => {
                surprise.style.opacity = '1';
            }, 50);

            // Start the flower rain
            startFlowerShower();
        }

        function startFlowerShower() {
            setInterval(createPetal, 200); // Create a new petal every 200ms
        }

        function createPetal() {
            const petal = document.createElement('div');
            petal.classList.add('petal');
            
            // Randomize position, size, and animation duration
            petal.style.left = Math.random() * 100 + 'vw';
            petal.style.animationDuration = Math.random() * 3 + 2 + 's'; // Between 2 and 5 seconds
            
            const size = Math.random() * 10 + 10; // Random size
            petal.style.width = size + 'px';
            petal.style.height = size + 'px';
            
            // Random color variations (Pink to Deep Pink)
            const colors = ['#ffc0cb', '#ff69b4', '#ff1493', '#db7093'];
            petal.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];

            document.body.appendChild(petal);

            // Remove petal after animation to keep browser fast
            setTimeout(() => {
                petal.remove();
            }, 5000);
        }
    </script>
</body>
</html>
