# monamour-
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Notre Ciel Étoilé ❤️️</title>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&family=Poppins:wght@300;400&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #05050f;
            color: #ffffff;
            font-family: 'Poppins', sans-serif;
            height: 100vh;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            padding: 30px;
        }

        header {
            text-align: center;
            z-index: 10;
        }

        h1 {
            font-family: 'Cinzel', serif;
            font-size: 2rem;
            color: #ffd700;
            margin-bottom: 5px;
            letter-spacing: 2px;
        }

        p {
            font-size: 0.95rem;
            color: #a0a0c0;
        }

        /* Le Ciel / Zone interactive */
        .sky {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            cursor: pointer;
            transition: transform 0.3s, background-color 0.3s;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.8);
        }

        .star:hover {
            transform: scale(2);
            background-color: #ffd700;
        }

        /* Fenêtre de message flottante */
        .message-box {
            position: relative;
            z-index: 10;
            background: rgba(20, 20, 35, 0.85);
            border: 1px solid rgba(255, 215, 0, 0.3);
            padding: 20px 30px;
            border-radius: 15px;
            max-width: 500px;
            text-align: center;
            backdrop-filter: blur(5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            min-height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .message-box p {
            color: #ffffff;
            font-size: 1.05vrem;
            line-height: 1.5;
        }

        /* Instructions */
        .instruction {
            font-size: 0.85rem;
            color: #ffd700;
            letter-spacing: 1px;
            text-transform: uppercase;
            z-index: 10;
            margin-bottom: -10px;
        }
    </style>
</head>
<body>

    <header>
        <h1>Notre Constellation</h1>
        <p>1 an d'amour gravé dans les étoiles, Sarah.</p>
    </header>

    <div class="sky" id="sky"></div>

    <div class="instruction">Clique sur les étoiles scintillantes pour lire nos souvenirs</div>

    <div class="message-box">
        <p id="memory-text">Chaque étoile de ce ciel représente un moment magique partagé à tes côtés depuis un an. Clique sur l'une d'elles pour commencer le voyage...</p>
    </div>

    <script>
        // Liste des souvenirs cachés dans les étoiles
        const memories = [
            "Le premier jour : Ce regard qui a tout basculé et qui a fait de toi mon évidence.",
            "Nos fous rires interminables : Ces moments où on rit pour rien, juste parce qu'on est ensemble.",
            "Nos projets et nos rêves : Regarder dans la même direction et construire l'avenir.",
            "Le quotidien : Même les jours ordinaires deviennent extraordinaires quand tu es là.",
            "Aujourd'hui - 1 An : 365 jours de bonheur pur. Et ce n'est que le tout début de notre histoire. Je t'aime, Sarah ❤️"
        ];

        const sky = document.getElementById("sky");
        const memoryText = document.getElementById("memory-text");

        // Générer un ciel étoilé aléatoire
        const starCount = 40;
        for (let i = 0; i < starCount; i++) {
            const star = document.createElement("div");
            star.className = "star";
            
            const x = Math.random() * 90 + 5; // position en %
            const y = Math.random() * 70 + 15;
            const size = Math.random() * 4 + 2; // taille entre 2 et 6px
            
            star.style.left = x + "vw";
            star.style.top = y + "vh";
            star.style.width = size + "px";
            star.style.height = size + "px";
            
            // Effet de scintillement aléatoire
            star.style.animation = `twinkle ${Math.random() * 3 + 2}s infinite alternate`;

            // Assigner un souvenir aléatoire ou séquentiel au clic
            const randomMemory = memories[Math.floor(Math.random() * memories.length)];
            star.onclick = () => {
                memoryText.style.opacity = 0;
                setTimeout(() => {
                    memoryText.innerText = randomMemory;
                    memoryText.style.opacity = 1;
                }, 200);
            };

            sky.appendChild(star);
        }
    </script>
</body>
</html>
