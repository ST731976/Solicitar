<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iniciar tu solicitud</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: #1d0552;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            padding: 10px;
            box-sizing: border-box;
        }
        #container {
            background: rgba(29, 5, 82, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.7);
            text-align: center;
            width: 100%;
            max-width: 600px;
        }
        #question-container, #processing, #result {
            display: none;
        }
        #processing {
            font-size: 20px;
            color: #00c853;
        }
        #result {
            font-size: 20px;
        }
        .button {
            background-color: #4caf50;
            border: none;
            color: #ffffff;
            padding: 15px 40px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 20px;
            margin-top: 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }
        input[type="text"], input[type="number"] {
            width: calc(100% - 22px);
            padding: 12px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            box-sizing: border-box;
        }
        input[type="radio"] {
            width: 18px;
            height: 18px;
            margin-right: 8px;
        }
        label {
            display: inline-block;
            margin: 10px 20px;
            font-size: 16px;
            text-align: left;
        }
        h1, p {
            color: #ffffff;
        }
        h1 {
            font-size: 24px;
            margin-bottom: 20px;
        }
        p {
            font-size: 18px;
            text-align: left;
            margin-bottom: 10px;
        }
        .options-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
        }
        .option {
            width: calc(50% - 10px);
            margin-bottom: 10px;
            display: flex;
            align-items: center;
        }
        .option span {
            margin-left: 10px;
        }
        #result-text {
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>Iniciar tu solicitud</h1>
        <div id="question-container">
            <p id="question"></p>
            <div id="answer-container" class="options-container"></div>
            <button class="button" onclick="nextQuestion()">Siguiente</button>
        </div>
        <div id="processing">Procesando tu solicitud...</div>
        <div id="result">
            <p id="result-text">Hemos encontrado la oferta adecuada para ti. Si estás interesado, haz clic en <a href="http://doafftracking.tech/zaimoo.es/u2wsh/1" class="button" target="_blank">Solicitar</a>.</p>
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
                required: true,
                min: 50
            },
            {
                question: "Plazo (en meses, mínimo 1 mes)",
                type: "number",
                required: true,
                min: 1
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
                required: true,
                min: 0
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

        let currentQuestion = 0;

        function showQuestion() {
            if (currentQuestion < questions.length) {
                const questionData = questions[currentQuestion];
                document.getElementById('question').innerText = questionData.question;
                const answerContainer = document.getElementById('answer-container');
                answerContainer.innerHTML = '';

                if (questionData.type === 'text' || questionData.type === 'number') {
                    const input = document.createElement('input');
                    input.type = questionData.type;
                    input.id = 'answer';
                    input.required = questionData.required;
                    if (questionData.min !== undefined) {
                        input.min = questionData.min;
                    }
                    input.setAttribute('aria-label', questionData.question);
                    answerContainer.appendChild(input);
                } else if (questionData.type === 'radio') {
                    const optionsContainer = document.createElement('div');
                    optionsContainer.classList.add('options-container');

                    questionData.options.forEach(option => {
                        const label = document.createElement('label');
                        label.classList.add('option');

                        const input = document.createElement('input');
                        input.type = 'radio';
                        input.name = 'answer';
                        input.value = option;
                        input.setAttribute('aria-label', option);

                        const span = document.createElement('span');
                        span.textContent = option;

                        label.appendChild(input);
                        label.appendChild(span);

                        optionsContainer.appendChild(label);
                    });

                    answerContainer.appendChild(optionsContainer);
                }

                document.getElementById('question-container').style.display = 'block';
            } else {
                document.getElementById('question-container').style.display = 'none';
                document.getElementById('processing').style.display = 'block';
                setTimeout(function() {
                    document.getElementById('processing').style.display = 'none';
                    document.getElementById('result').style.display = 'block';
                }, 3000);
            }
        }

        function nextQuestion() {
            const questionData = questions[currentQuestion];
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
                showQuestion();
                return;
            } else if (questionData.question.includes('¿Tienes un código de oferta?') && answer === 'No') {
                currentQuestion += 2;
            }

            currentQuestion++;
            showQuestion();
        }

        showQuestion();
    </script>
</body>
</html>
