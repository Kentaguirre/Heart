<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Raining Hearts</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #222;
        }

        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            transform: rotate(-45deg);
            position: absolute;
            animation: fall linear infinite;
        }

        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
        }

        .heart::before {
            top: -10px;
            left: 0;
        }

        .heart::after {
            top: 0;
            left: 10px;
        }

        @keyframes fall {
            0% {
                transform: translateY(-10vh) rotate(-45deg);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) rotate(-45deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>

<script>
    function createHeart() {
        const heart = document.createElement("div");
        heart.classList.add("heart");

        // Random position and animation duration
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.animationDuration = Math.random() * 3 + 2 + "s"; // Between 2-5 seconds
        heart.style.width = heart.style.height = Math.random() * 20 + 10 + "px"; // Varying sizes

        document.body.appendChild(heart);

        // Remove heart after animation ends
        setTimeout(() => {
            heart.remove();
        }, 5000);
    }

    setInterval(createHeart, 200);
</script>

</body>
</html>
