<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interação de Botões</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px;
            background-color: #f0f0f0;
            margin: 0;
        }

        #question {
            font-size: 24px;
            margin-bottom: 20px;
        }

        #yes-button {
            background-color: green;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            cursor: pointer;
            border-radius: 5px;
        }

        #no-button {
            background-color: red;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 18px;
            cursor: pointer;
            border-radius: 5px;
            position: absolute;
        }

        .heart {
            font-size: 50px;
            color: red;
            animation: pulse 1s infinite;
        }

        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.2);
            }
            100% {
                transform: scale(1);
            }
        }

        #hearts {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(255, 255, 255, 0.9);
            z-index: 1000;
            text-align: center;
        }

        #hearts span {
            position: absolute;
            animation: move-hearts 3s linear infinite;
        }

        @keyframes move-hearts {
            0% {
                top: 100%;
                left: 50%;
            }
            100% {
                top: 0%;
                left: random;
            }
        }
    </style>
</head>
<body>
    <div id="question">Pode me enviar uma foto sua?</div>
    <button id="yes-button">Sim</button>
    <button id="no-button">Não</button>

    <div id="hearts"></div>

    <script>
        const noButton = document.getElementById('no-button');
        const heartsContainer = document.getElementById('hearts');

        // Função para gerar uma posição aleatória para o botão "não"
        function randomizePosition() {
            const randomTop = Math.random() * window.innerHeight;
            const randomLeft = Math.random() * window.innerWidth;
            noButton.style.top = `${randomTop}px`;
            noButton.style.left = `${randomLeft}px`;
        }

        // Chama a função sempre que o botão "não" é clicado
        noButton.addEventListener('click', randomizePosition);

        // Quando clicar no botão "Sim", exibe a tela cheia de corações
        document.getElementById('yes-button').addEventListener('click', () => {
            heartsContainer.style.display = 'block';

            // Gerar corações aleatórios na tela
            for (let i = 0; i < 100; i++)
