<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iniciar tu solicitud</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(to right, #1c1f26, #283048);
            color: #ffeb3b;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            padding: 10px;
            box-sizing: border-box;
        }
        #container {
            background: rgba(0, 0, 0, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.7);
            text-align: center;
            width: 100%;
            max-width: 500px;
        }
        .question-container {
            background: rgba(0, 0, 0, 0.8);
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
            text-align: left;
            display: none; /* Inicialmente oculto */
        }
        .question-container.active {
            display: block; /* Mostrar cuando esté activo */
        }
        #processing, #result {
            display: none;
        }
        #processing {
            font-size: 20px;
            color: #00c853;
        }
        #result {
            font-size: 20px;
            color: #00b0ff;
        }
        .button {
            background-color: #00b0ff;
            border: none;
            color: white;
            padding: 12px 25px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 18px;
            margin: 15px 0;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            width: 100%;
            max-width: 200px; /* Ajuste el ancho máximo para dispositivos móviles */
        }
        .button:hover {
            background-color: #0091ea;
            transform: scale(1.05);
        }
        input[type="text"], input[type="number"], input[type="radio"] {
            width: calc(100% - 22px); /* Padding adjustment */
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            box-sizing: border-box;
        }
        label {
            display: block;
            margin: 10px 0;
            font-size: 16px;
            color: #ffeb3b;
            text-align: left;
        }
        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            color: #ffeb3b;
        }
        p {
            font-size: 18px;
            text-align: left;
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>Iniciar tu solicitud</h1>
        <div class="question-container" id="question-container-1">
            <p id="question-1"></p>
            <div id="answer-container-1"></div>
            <button class="button" onclick="nextQuestion(1)">Siguiente</button>
        </div>
        <div class="question-container" id="question-container-2">
            <p id="question-2"></p>
            <div id="answer-container-2"></div>
            <button class="button" onclick="nextQuestion(2)">Siguiente</button>
        </div>
        <div class="question-container" id="question-container-3">
            <p id="question-3"></p>
            <div id="answer-container-3"></div>
            <button class="button" onclick="nextQuestion(3)">Siguiente</button>
        </div>
        <div id="processing">Procesando tu solicitud...</div>
        <div id="result">
            Nuestro sistema automático ha procesado tus datos y a continuación te ofrece la opción más adecuada para ti.
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "Hola, me presento, soy el Asistente de IA y te ayudaré a encontrar la financiación que necesitas. ¿Estás de acuerdo?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "Cantidad que necesitas (mínimo 50 euros)",
                type: "number",
                required: true
            },
            {
                question: "Plazo (en meses, mínimo 1 mes)",
                type: "number",
                required: true
            },
            {
                question: "Actividad laboral (necesario)*",
                type: "radio",
                options: ["Trabajo asalariado", "Autónomo", "Pensionista", "Desempleado"],
                required: true
            },
            {
                question: "Ingresos mensuales aproximados",
                type: "number",
                required: true
            },
            {
                question: "ASNEF (necesario)*",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "¿Actualmente tienes préstamos o deudas pendientes? (necesario)*",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "¿Tienes un código de oferta?",
                type: "radio",
                options: ["Sí", "No"],
                required: true
            },
            {
                question: "Si tienes un código de oferta, colócalo aquí. (opcional)",
                type: "text",
                required: false
            }
        ];

        const links = [
            "http://doafftracking.tech/zaimoo.es/u2wsh/1" // Este es el enlace que redirige al usuario.
        ];

        let currentQuestion = 0;

        function showQuestion(questionNumber) {
            const questionData = questions[questionNumber];
            const containerId = `question-container-${questionNumber + 1}`;
            const questionId = `question-${questionNumber + 1}`;
            const answerContainerId = `answer-container-${questionNumber + 1}`;
            
            document.getElementById(containerId).classList.add('active');
            document.getElementById(questionId).innerText = questionData.question.replace('&#191;', '');
            
            const answerContainer = document.getElementById(answerContainerId);
            answerContainer.innerHTML = '';

            if (questionData.type === 'text' || questionData.type === 'number') {
                const input = document.createElement('input');
                input.type = questionData.type;
                input.id = 'answer';
                input.required = questionData.required;
                answerContainer.appendChild(input);
            } else if (questionData.type === 'radio') {
                questionData.options.forEach(option => {
                    const label = document.createElement('label');
                    const input = document.createElement('input');
                    input.type = 'radio';
                    input.name = 'answer';
                    input.value = option;
                    label.appendChild(input);
                    label.appendChild(document.createTextNode(option));
                    answerContainer.appendChild(label);
                    answerContainer.appendChild(document.createElement('br'));
                });
            }
        }

        function nextQuestion(questionNumber) {
            const questionData = questions[questionNumber];
            let answer = '';
            
            if (questionData.type === 'text' || questionData.type === 'number') {
                answer = document.getElementById('answer').value;
            } else if (questionData.type === 'radio') {
                const selectedOption = document.querySelector('input[name="answer"]:checked');
                if (selectedOption) {
                    answer = selectedOption.value;
                }
            }

            if (questionData.required && answer.trim() === '') {
                alert('Por favor, responde la pregunta.');
                return;
            }

            if (questionData.question.includes('Asistente de IA') && answer === 'No') {
                alert('Lo siento, no podemos continuar sin tu consentimiento.');
                return;
            }

            if (questionData.question.includes('Cantidad que necesitas') && Number(answer) < 50) {
                alert('La cantidad solicitada debe ser igual o superior a 50 euros.');
                return;
            }

            if (questionData.question.includes('Plazo') && Number(answer) < 1) {
                alert('El plazo debe ser igual o superior a 1 mes.');
                return;
            }

            if (questionData.question.includes('¿Tienes un código de oferta?') && answer === 'Sí') {
                currentQuestion++;
                showQuestion(currentQuestion);
                return;
            } else if (questionData.question.includes('¿Tienes un código de oferta?') && answer === 'No') {
                currentQuestion += 2; // Saltar la pregunta opcional
            }

            currentQuestion++;
            if (currentQuestion < questions.length) {
                showQuestion(currentQuestion);
            } else {
                processRequest();
            }
        }

        function processRequest() {
            document.querySelectorAll('.question-container').forEach(container => {
                container.style.display = 'none';
            });
            document.getElementById('processing').style.display = 'block';
            setTimeout(function() {
                document.getElementById('processing').innerText = 'A continuación te redirigiremos a la opción más adecuada para ti.';
                setTimeout(redirectToOffer, 2000); // Esperar 2 segundos antes de redirigir
            }, 3000); // Mostrar el mensaje de procesamiento durante 3 segundos
        }

        function redirectToOffer() {
            const randomIndex = Math.floor(Math.random() * links.length);
            window.location.href = links[randomIndex]; // Cambio a window.location.href para evitar el bloqueo de ventanas emergentes
        }

        // Iniciar la primera pregunta
        showQuestion(currentQuestion);
    </script>
</body>
</html>
