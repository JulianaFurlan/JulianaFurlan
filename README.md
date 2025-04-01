<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Florzinha Pixel Art</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #fce4ec;
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <canvas id="gameCanvas"></canvas>
    <script>
        const canvas = document.getElementById("gameCanvas");
        const ctx = canvas.getContext("2d");
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const flower = new Image();
        flower.src = "https://i.imgur.com/0hl9yLq.png"; // URL da flor em pixel art

        let x = 50;
        let y = 50;
        let dx = 2;
        let dy = 2;

        function update() {
            x += dx;
            y += dy;
            if (x + 32 > canvas.width || x < 0) dx *= -1;
            if (y + 32 > canvas.height || y < 0) dy *= -1;
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.drawImage(flower, x, y, 32, 32);
        }

        function loop() {
            update();
            draw();
            requestAnimationFrame(loop);
        }

        flower.onload = () => {
            loop();
        };
    </script>
</body>
</html>
