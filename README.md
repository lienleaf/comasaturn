<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>先生の日</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            font-family: 'Arial', sans-serif;
            overflow: hidden;
        }
        .card {
            background: #fff;
            width: 300px;
            height: auto;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            padding: 20px;
            text-align: center;
            transition: transform 0.4s ease, opacity 0.4s ease;
        }
        .card.hidden {
            display: none;
        }
        .btn {
            padding: 10px 20px;
            font-size: 1em;
            color: #fff;
            background-color: #ff6b81;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
        }
        .btn:hover {
            background-color: #ff4757;
        }
        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: #ff6b81;
            transform: rotate(45deg);
            animation: float 5s infinite ease-in-out;
            opacity: 0.7;
            box-shadow: 0 0 10px rgba(255, 107, 129, 0.5);
        }
        .heart::before,
        .heart::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: #ff6b81;
            border-radius: 50%;
        }
        .heart::before {
            top: -10px;
            left: 0;
        }
        .heart::after {
            left: -10px;
            top: 0;
        }
        @keyframes float {
            0% {
                transform: translateY(0) rotate(45deg);
                opacity: 0.7;
            }
            50% {
                transform: translateY(-100px) rotate(45deg);
                opacity: 1;
            }
            100% {
                transform: translateY(-200px) rotate(45deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div class="card" id="messageCard">
        <h1>Click to Open</h1>
        <button class="btn" onclick="openCard()">Open</button>
    </div>

    <div class="card hidden" id="contentCard">
        <h1>トリ先生へ</h1>
        <p>
            先生、いつも優しく教えてくださり<br>ありがとうございます！<br>
            私たちに日本語だけでなく、たくさんの大切なことを教えてくれました。<br>
            先生のおかげで、新しい世界を見ることができました。<br>
            これからもよろしくお願いします！<br><br>
            ハッピー先生の日！
        </p>
    </div>

    <script>
        function openCard() {
            document.getElementById("messageCard").style.display = "none";
            const contentCard = document.getElementById("contentCard");
            contentCard.classList.remove("hidden");
            createHearts();
        }

        function createHearts() {
            for (let i = 0; i < 50; i++) {
                const heart = document.createElement("div");
                heart.className = "heart";
                heart.style.left = Math.random() * 100 + "vw";
                heart.style.animationDuration = Math.random() * 2 + 3 + "s";
                document.body.appendChild(heart);
                heart.addEventListener("animationend", () => heart.remove());
            }
        }
    </script>
</body>
</html>

