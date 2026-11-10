<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Convite</title>
    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ffedf1 0%, #ffd6e7 30%, #ffe8c7 100%);
            font-family: Arial, sans-serif;
            padding: 20px;
        }

        .phone {
            width: 100%;
            max-width: 420px;
            height: 760px;
            background: #111827;
            border-radius: 36px;
            padding: 14px 14px 18px;
            box-shadow: 0 25px 50px rgba(0, 0, 0, 0.18);
        }

        .screen {
            width: 100%;
            height: 100%;
            background: linear-gradient(180deg, #fff8fb 0%, #ffeef4 100%);
            border-radius: 26px;
            padding: 20px 18px;
            position: relative;
            overflow: hidden;
        }

        .top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 0.95rem;
            font-weight: 700;
            color: #2d1b2c;
            margin-bottom: 18px;
        }

        .status {
            display: flex;
            gap: 6px;
            align-items: center;
        }

        .status .dot {
            width: 8px;
            height: 8px;
            background: #1f2937;
            border-radius: 50%;
            opacity: 0.8;
        }

        .card {
            position: relative;
            background: rgba(255, 255, 255, 0.75);
            border: 1px solid rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(10px);
            border-radius: 28px;
            padding: 28px 20px 18px;
            text-align: center;
            box-shadow: 0 18px 35px rgba(255, 109, 157, 0.2);
            height: calc(100% - 30px);
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .heart {
            width: 88px;
            height: 88px;
            margin: 0 auto 18px;
            border-radius: 26px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, #ff5b8f, #ff3864);
            color: white;
            font-size: 2.5rem;
            box-shadow: 0 16px 30px rgba(255, 56, 100, 0.28);
            animation: pulse 1.8s infinite ease-in-out;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.08); }
        }

        h1 {
            margin: 0 0 12px;
            font-size: 2rem;
            color: #2f1b2f;
        }

        p {
            margin: 0 0 18px;
            color: #5e3a4d;
            line-height: 1.6;
            font-size: 1rem;
        }

        .actions {
            position: relative;
            height: 60px;
            margin-top: 10px;
        }

        button {
            border: none;
            border-radius: 18px;
            font-size: 1rem;
            font-weight: 700;
            cursor: pointer;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        button:hover {
            transform: translateY(-2px);
        }

        .yes {
            position: absolute;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 46%;
            background: linear-gradient(135deg, #ff4d8d, #ff2e63);
            color: white;
            padding: 14px 10px;
            box-shadow: 0 12px 22px rgba(255, 46, 99, 0.28);
        }

        .no {
            position: absolute;
            right: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 46%;
            background: #f3e9ef;
            color: #6b3d56;
            padding: 14px 10px;
            box-shadow: inset 0 0 0 1px rgba(107, 61, 86, 0.08);
        }

        .message {
            margin-top: 18px;
            min-height: 48px;
            font-size: 0.95rem;
            font-weight: 700;
            color: #8d2e5a;
        }

        .message.success {
            color: #1f8f5f;
        }

        @media (max-width: 430px) {
            .phone {
                height: 700px;
            }

            h1 {
                font-size: 1.75rem;
            }
        }
    </style>
</head>
<body>
    <div class="phone">
        <div class="screen">
            <div class="top-bar">
                <span>9:41</span>
                <div class="status">
                    <span class="dot"></span>
                    <span class="dot"></span>
                    <span class="dot"></span>
                </div>
            </div>

            <div class="card">
                <div class="heart">❤</div>
                <h1>Você topa sair comigo?</h1>
                <p>Eu queria te chamar pra um café, uma volta e um papo bem gostoso. Você me acompanha?</p>

                <div class="actions">
                    <button id="simBtn" class="yes">Sim 😍</button>
                    <button id="naoBtn" class="no">Não 😅</button>
                </div>

                <div id="resultado" class="message">Eu fico te esperando 😌</div>
            </div>
        </div>
    </div>

    <script>
        const simBtn = document.getElementById('simBtn');
        const naoBtn = document.getElementById('naoBtn');
        const resultado = document.getElementById('resultado');

        simBtn.addEventListener('click', () => {
            resultado.textContent = 'Yesss! ❤️ Vamos marcar uma data e curtir um momento juntos!';
            resultado.classList.add('success');
            simBtn.textContent = 'Vamos! 🎉';
            naoBtn.style.display = 'none';
        });

        let tentativas = 0;

        naoBtn.addEventListener('click', () => {
            tentativas++;
            const actions = document.querySelector('.actions');
            const maxX = actions.clientWidth - naoBtn.offsetWidth - 10;
            const maxY = actions.clientHeight - naoBtn.offsetHeight - 10;

            const randomX = Math.random() * maxX;
            const randomY = Math.random() * maxY;

            naoBtn.style.left = randomX + 'px';
            naoBtn.style.top = randomY + 'px';
            naoBtn.style.right = 'auto';
            naoBtn.style.transform = 'none';

            if (tentativas === 1) {
                resultado.textContent = 'Ah, um pouco de suspense não faz mal 😄';
            } else if (tentativas === 2) {
                resultado.textContent = 'Tá difícil resistir, né? 😏';
            } else {
                resultado.textContent = 'Então me deixa tentar de novo 😌';
            }
        });
    </script>
</body>
</html>
