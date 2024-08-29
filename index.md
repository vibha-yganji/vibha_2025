---
layout: base
title: Vibha Ganji's Home Page
description: Home Page
hide: true
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About Me and Dino Game</title>
    <style>
        @font-face {
            font-family: 'Product Sans';
            src: url('/Users/vibhaganji/Downloads/product-sans/Product Sans Regular.ttf');
        }
        body {
            margin: 0;
            font-family: "Product Sans", sans-serif;
            background-color: black;
            color: white;
            text-align: center;
            padding: 50px;
            font-size: 20px;
            overflow: hidden;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        p {
            margin-top: -80px !important;
            font-size: 25px;
        }
        canvas {
            border: 2px solid black;
            display: block;
            background: #ffcfca;
            margin: 50px auto;
        }
        #gameOver {
            display: none;
            font-size: 30px;
            color: red;
        }
    </style>
</head>
<body>
    <div class="container">
        <p>Hello! My name is Vibha!. I'm very passionate about biology and neuroscience. This page is dedicated to sharing a bit more about myself and my past projects.</p>
        <canvas id="gameCanvas" width="800" height="200"></canvas>
        <div id="gameOver">Game Over! Your score is <span id="finalScore"></span></div>
    </div>
    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const gameOverDiv = document.getElementById('gameOver');
        const finalScoreSpan = document.getElementById('finalScore');
        const dino = {
            x: 50,
            y: canvas.height - 50,
            width: 30,
            height: 30,
            color: 'green',
            gravity: 0.5,
            velocityY: 0,
            jumpPower: -10,
            isJumping: false
        };
        const cactus = {
            x: canvas.width,
            y: canvas.height - 50,
            width: 20,
            height: 30,
            color: 'brown'
        };
        let score = 0;
        let isGameOver = false;
        function drawDino() {
            ctx.fillStyle = dino.color;
            ctx.fillRect(dino.x, dino.y, dino.width, dino.height);
        }
        function drawCactus() {
            ctx.fillStyle = cactus.color;
            ctx.fillRect(cactus.x, cactus.y, cactus.width, cactus.height);
        }
        function drawScore() {
            ctx.fillStyle = 'black';
            ctx.font = '20px Arial';
            ctx.fillText('Score: ' + score, 10, 20);
        }
        function update() {
            if (isGameOver) return;
            if (dino.isJumping) {
                dino.velocityY += dino.gravity;
                dino.y += dino.velocityY;
                if (dino.y >= canvas.height - dino.height) {
                    dino.y = canvas.height - dino.height;
                    dino.velocityY = 0;
                    dino.isJumping = false;
                }
            }
            cactus.x -= 5;
            if (cactus.x + cactus.width < 0) {
                cactus.x = canvas.width;
                score++;
            }
            if (dino.x < cactus.x + cactus.width && dino.x + dino.width > cactus.x && dino.y < cactus.y + cactus.height && dino.y + dino.height > cactus.y) {
                gameOverDiv.style.display = 'block';
                finalScoreSpan.textContent = score;
                isGameOver = true;
                return;
            }
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawDino();
            drawCactus();
            drawScore();
            requestAnimationFrame(update);
        }
        function resetGame() {
            dino.y = canvas.height - dino.height;
            dino.velocityY = 0;
            dino.isJumping = false;
            cactus.x = canvas.width;
            score = 0;
            isGameOver = false;
            gameOverDiv.style.display = 'none';
            update();
        }
        document.addEventListener('keydown', (e) => {
            if (e.code === 'Space' && !dino.isJumping && !isGameOver) {
                dino.velocityY = dino.jumpPower;
                dino.isJumping = true;
            }
            if (e.code === 'KeyR' && isGameOver) {
                resetGame();
            }
        });
        update();
    </script>
</body>
</html>
