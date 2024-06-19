<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minicréditos</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; background-color: #f5f5f5; }
        .container { padding: 20px; text-align: center; max-width: 400px; margin: 0 auto; background-color: #fff; border-radius: 10px; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); }
        label { font-weight: bold; display: block; margin-bottom: 10px; color: #007BFF; font-size: 1.2em; }
        input[type="range"] { width: 100%; height: 20px; background: #ddd; outline: none; border-radius: 5px; -webkit-appearance: none; margin-bottom: 20px; }
        input[type="range"]::-webkit-slider-thumb { width: 30px; height: 30px; background: #007BFF; border-radius: 50%; cursor: pointer; -webkit-appearance: none; }
        input[type="range"]::-moz-range-thumb { width: 30px; height: 30px; background: #007BFF; border-radius: 50%; cursor: pointer; }
        .apply-button { display: inline-block; padding: 12px 25px; background-color: #28a745; color: #fff; font-size: 1.2em; font-weight: bold; text-decoration: none; border-radius: 5px; cursor: pointer; }
        .apply-button:hover { background-color: #218838; }
    </style>
</head>
<body>
    <div class="container">
        <div>
            <label for="loanAmount">Minicrédito: €<span id="loanAmountValue">50</span></label>
            <input type="range" id="loanAmount" min="50" max="10000" value="50" step="50" oninput="updateLoanAmount()">
        </div>
        <button id="applyButton" class="apply-button">Solicitar</button>
    </div>
    <script>
        function updateLoanAmount() {
            const loanAmount = document.getElementById('loanAmount').value;
            document.getElementById('loanAmountValue').textContent = loanAmount;
        }

        document.getElementById('applyButton').addEventListener('click', function() {
            const loanAmount = document.getElementById('loanAmount').value;

            let url;

            if (loanAmount == 1000) {
                url = 'http://doafftracking.tech/credityes.es/u2wsh/1';
            } else {
                url = 'http://doafftracking.tech/zaimoo.es/u2wsh/1';
            }

            window.open(url, '_blank');
        });
    </script>
</body>
</html>




