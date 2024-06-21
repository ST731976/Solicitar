<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Iniciar tu solicitud</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: #1d0552; /* Fondo púrpura sólido */
            color: #ffffff; /* Color del texto blanco */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            padding: 10px;
            box-sizing: border-box;
        }
        #container {
            background: rgba(29, 5, 82, 0.9); /* Fondo del contenedor con algo de transparencia */
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
            color: #00c853; /* Verde para el texto de procesamiento */
        }
        #result {
            font-size: 20px;
            color: #ffffff; /* Color del texto blanco */
        }
        .button {
            background-color: #4caf50; /* Verde */
            border: none;
            color: #ffffff; /* Blanco para el texto */
            padding: 15px 40px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 20px;
            margin-top: 20px; /* Espacio entre el mensaje y el botón */
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .button:hover {
            background-color: #45a049; /* Verde más oscuro al pasar el mouse */
            transform: scale(1.05);
        }
        input[type="text"], input[type="number"] {
            width: calc(100% - 22px); /* Padding adjustment */
            padding: 12px;
            margin: 10px 0;
            border: none;
            border-radius: 5px; /* Cuadrados para las cifras */
            font-size: 16px;
            box-sizing: border-box;
        }
        input[type="radio"] {
            width: 18px; /* Ancho más grande para los círculos de selección */
            height: 18px; /* Alto más grande para los círculos de selección */
            margin-right: 8px;
        }
        label {
            display: inline-block;
            margin: 10px 20px;
            font-size: 16px;
            color: #ffffff; /* Color del texto blanco */
            text-align: left;
        }
        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            color: #ffffff; /* Color del texto blanco */
        }
        p {
            font-size: 18px;
            color: #ffffff; /* Color del texto blanco */
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
            width: calc(50% - 10px); /* Para dos opciones, con margen */
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

        function showQuestion() {
            if (currentQuestion < questions.length) {
                const questionData = questions[currentQuestion];
                document.getElementById('question').innerText = questionData.question.replace('¿', '').replace('?', '');
                const answerContainer = document.getElementById('answer-container');
                answerContainer.innerHTML = '';

                if (questionData.type === 'text' || questionData.type === 'number') {
                    const input = document.createElement('input');
                    input.type = questionData.type;
                    input.id = 'answer';
                    input.required = questionData.required;
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
                }, 3000); // Mostrar el mensaje de procesamiento durante 3 segundos
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
                currentQuestion += 2; // Saltar la pregunta opcional
            }

            currentQuestion++;
            showQuestion();
        }

        // Iniciar la primera pregunta
        showQuestion();
    </script>
</body>
</html>
