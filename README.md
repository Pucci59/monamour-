# monamour-
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>La Quête de notre Amour ❤️</title>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #1a1a2e;
            --card-bg: #16213e;
            --primary: #e94560;
            --text: #ffffff;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--bg);
            color: var(--text);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .game-container {
            background-color: var(--card-bg);
            width: 100%;
            max-width: 600px;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(233, 69, 96, 0.3);
            border: 2px solid var(--primary);
            text-align: center;
        }

        h2 {
            font-family: 'Press Start 2P', cursive;
            font-size: 1rem;
            color: var(--primary);
            margin-bottom: 25px;
            line-height: 1.6;
        }

        .story-box {
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 30px;
            min-height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 10px;
        }

        .choices {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        button {
            background-color: var(--primary);
            color: var(--text);
            border: none;
            padding: 15px 20px;
            border-radius: 10px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s, background-color 0.2s;
            box-shadow: 0 4px 15px rgba(233, 69, 96, 0.4);
        }

        button:hover {
            transform: scale(1.02);
            background-color: #ff6b81;
        }

        .heart-rain {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: 999;
            display: none;
        }

        .heart {
            position: absolute;
            color: var(--primary);
            font-size: 24px;
            animation: fall linear forwards;
        }

        @keyframes fall {
            0% { transform: translateY(-10vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="game-container">
        <h2 id="game-title">Étape 1 : Le Point de Départ</h2>
        <div class="story-box" id="story-text">
            Il était une fois, un regard qui a tout changé... Prête à revivre notre première année, Sarah ?
        </div>
        <div class="choices" id="choices-container">
            <button onclick="nextStep(1)">Commencer l'aventure ❤️</button>
        </div>
    </div>

    <div class="heart-rain" id="heartRain"></div>

    <script>
        const steps = [
            {
                title: "Étape 1 : Le Regard",
                text: "Tout a commencé il y a un an jour pour jour. Si tu devais résumer notre premier regard, ce serait...",
                choices: [
                    { text: "Une évidence totale instantanée ✨", next: 2 },
                    { text: "Un coup de foudre mémorable ⚡", next: 2 }
                ]
            },
            {
                title: "Étape 2 : Les Fous Rires",
                text: "Depuis, on ne compte plus les éclats de rire et les moments de complicité. Quel est notre super-pouvoir ?",
                choices: [
                    { text: "Se comprendre rien qu'en se regardant 🤫", next: 3 },
                    { text: "Rire de tout, n'importe quand 😂", next: 3 }
                ]
            },
            {
                title: "Étape 3 : Le Bilan",
                text: "365 jours plus tard, on en est là. Qu'est-ce qui t'attend pour la suite ?",
                choices: [
                    { text: "Encore des milliers de moments magiques 🚀", next: 4 },
                    { text: "Une vie entière de bonheur à mes côtés 🥰", next: 4 }
                ]
            },
            {
                title: "Victoire : 1 an d'Amour pur !",
                text: "Joyeux anniversaire de rencontre, mon amour ! Tu gagnes mon cœur pour l'éternité (et ça, c'est permanent). Je t'aime plus que tout, Sarah !",
                choices: [
                    { text: "Célébrer notre amour 💖", next: 'end' }
                ]
            }
        ];

        function nextStep(stepIndex) {
            if (stepIndex === 'end') {
                triggerCelebration();
                return;
            }

            const current = steps[stepIndex - 1];
            document.getElementById("game-title").innerText = current.title;
            document.getElementById("story-text").innerText = current.text;
            
            const container = document.getElementById("choices-container");
            container.innerHTML = "";
            
            current.choices.forEach(choice => {
                const btn = document.createElement("button");
                btn.innerText = choice.text;
                btn.onclick = () => nextStep(choice.next);
                container.appendChild(btn);
            });
        }

        function triggerCelebration() {
            document.querySelector(".game-container").innerHTML = `
                <h2 style="font-family: 'Poppins'; font-size: 1.8rem; color: #e94560;">Joyeux 1 An, Sarah ! ❤️</h2>
                <p style="font-size: 1.2rem; line-height: 1.8; margin: 20px 0;">
                    Merci d'illuminer mes journées, d'être là, et de rendre chaque instant si précieux.<br>
                    <strong>Je t'aime infiniment.</strong>
                </p>
            `;
            
            const rain = document.getElementById("heartRain");
            rain.style.display = "block";
            for (let i = 0; i < 50; i++) {
                setTimeout(() => {
                    const heart = document.createElement("div");
                    heart.className = "heart";
                    heart.innerHTML = "❤️";
                    heart.style.left = Math.random() * 100 + "vw";
                    heart.style.animationDuration = (Math.random() * 2 + 2) + "s";
                    rain.appendChild(heart);
                    setTimeout(() => heart.remove(), 4000);
                }, i * 100);
            }
        }
    </script>
</body>
</html>
