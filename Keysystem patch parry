<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KeySystem - Obtenha Sua Chave Aleatória</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            text-align: center;
        }
        .container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
        }
        h1 {
            color: #4CAF50;
        }
        .step {
            margin: 20px 0;
        }
        .timer {
            font-size: 24px;
            color: #FF5722;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 4px;
            margin-top: 10px;
        }
        button:hover {
            background-color: #45a049;
        }
        button:disabled {
            background-color: #ccc;
            cursor: not-allowed;
        }
        #key {
            font-size: 20px;
            color: #2196F3;
            word-break: break-all;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>KeySystem</h1>
        <p>Bem-vindo ao KeySystem! Complete 3 passos simples para obter uma chave aleatória. Cada passo dura 5 segundos.</p>
        
        <div id="step1" class="step">
            <h2>Passo 1: Aguarde 5 segundos</h2>
            <div class="timer" id="timer1">5</div>
            <button id="startStep1">Iniciar Passo 1</button>
        </div>
        
        <div id="step2" class="step hidden">
            <h2>Passo 2: Aguarde 5 segundos</h2>
            <div class="timer" id="timer2">5</div>
            <button id="startStep2">Iniciar Passo 2</button>
        </div>
        
        <div id="step3" class="step hidden">
            <h2>Passo 3: Aguarde 5 segundos</h2>
            <div class="timer" id="timer3">5</div>
            <button id="startStep3">Iniciar Passo 3</button>
        </div>
        
        <div id="result" class="hidden">
            <h2>Chave Gerada!</h2>
            <p id="key"></p>
            <button id="copyKey">Copiar Chave</button>
            <p><small>Chave gerada aleatoriamente. Use como quiser!</small></p>
        </div>
    </div>

    <script>
        function startTimer(stepId, nextStepId, timerId) {
            const startButton = document.getElementById(`start${stepId}`);
            const timerElement = document.getElementById(timerId);
            let timeLeft = 5;

            startButton.disabled = true;
            const interval = setInterval(() => {
                timeLeft--;
                timerElement.textContent = timeLeft;
                if (timeLeft <= 0) {
                    clearInterval(interval);
                    document.getElementById(stepId.toLowerCase()).classList.add('hidden');
                    if (nextStepId) {
                        document.getElementById(nextStepId.toLowerCase()).classList.remove('hidden');
                    } else {
                        showKey();
                    }
                }
            }, 1000);
        }

        function generateRandomKey() {
            const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
            let key = '';
            for (let i = 0; i < 16; i++) {
                key += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return key.match(/.{1,4}/g).join('-'); // Formato XXXX-XXXX-XXXX-XXXX
        }

        function showKey() {
            document.getElementById('result').classList.remove('hidden');
            const keyElement = document.getElementById('key');
            keyElement.textContent = generateRandomKey();
        }

        document.getElementById('startStep1').addEventListener('click', () => startTimer('Step1', 'Step2', 'timer1'));
        document.getElementById('startStep2').addEventListener('click', () => startTimer('Step2', 'Step3', 'timer2'));
        document.getElementById('startStep3').addEventListener('click', () => startTimer('Step3', null, 'timer3'));

        document.getElementById('copyKey').addEventListener('click', () => {
            const key = document.getElementById('key').textContent;
            navigator.clipboard.writeText(key).then(() => {
                alert('Chave copiada para a área de transferência!');
            });
        });
    </script>
</body>
</html>
