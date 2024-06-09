<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minicréditos</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; background-color: #f5f5f5; }
        .container { padding: 10px; text-align: center; max-width: 300px; margin: 0 auto; }
        label { font-weight: bold; display: block; margin-bottom: 5px; color: #007BFF; }
        input[type="range"] { width: 100%; height: 10px; background: #ddd; outline: none; }
        input[type="range"]::-webkit-slider-thumb { width: 20px; height: 20px; background: #007BFF; border-radius: 50%; }
        input[type="range"]::-moz-range-thumb { width: 20px; height: 20px; background: #007BFF; border-radius: 50%; }
        .apply-button { display: inline-block; padding: 10px 20px; margin-top: 10px; background-color: #28a745; color: #fff; font-size: 1em; font-weight: bold; text-decoration: none; border-radius: 5px; cursor: pointer; }
        .apply-button:hover { background-color: #218838; }
    </style>
</head>
<body>
    <div class="container">
        <div>
            <label for="loanAmount">Minicrédito: €<span id="loanAmountValue">50</span></label>
            <input type="range" id="loanAmount" min="50" max="1000" value="50" step="50" oninput="updateLoanAmount()">
        </div>
        <div>
            <label for="loanTerm">Plazo: <span id="loanTermValue">1</span> día(s)</label>
            <input type="range" id="loanTerm" min="1" max="90" value="1" step="1" oninput="updateLoanTerm()">
        </div>
        <button id="applyButton" class="apply-button">Solicitar</button>
        <div id="loanOptions" style="margin-top: 20px;"></div>
    </div>
    <script>
        function updateLoanAmount() {
            const loanAmount = document.getElementById('loanAmount').value;
            document.getElementById('loanAmountValue').textContent = loanAmount;
            updateLoanOptions(loanAmount);
        }

        function updateLoanTerm() {
            const loanTerm = document.getElementById('loanTerm').value;
            document.getElementById('loanTermValue').textContent = loanTerm;
        }

        function updateLoanOptions(amount) {
            const loanOptionsDiv = document.getElementById('loanOptions');
            loanOptionsDiv.innerHTML = '';

            if (amount >= 50 && amount <= 100) {
                loanOptionsDiv.innerHTML = '<a href="http://doafftracking.tech/zaimoo.es/u2wsh/1">Enlace 1</a>';
            } else if (amount > 100 && amount <= 750) {
                loanOptionsDiv.innerHTML = '<a href="http://doafftracking.tech/zaimoo.es/u2wsh/1">Enlace 2</a>';
            } else if (amount > 750 && amount <= 1000) {
                loanOptionsDiv.innerHTML = '<a href="http://doafftracking.tech/credityes.es/u2wsh/1">Enlace 3</a>';
            }
        }

        document.getElementById('applyButton').addEventListener('click', function() {
            const loanAmount = document.getElementById('loanAmount').value;
            const loanTerm = document.getElementById('loanTerm').value;
            let url;

            if (loanAmount >= 50 && loanAmount <= 1000) {
                if (loanAmount >= 50 && loanAmount <= 100) {
                    url = `http://doafftracking.tech/zaimoo.es/u2wsh/1`;
                } else if (loanAmount > 100 && loanAmount <= 750) {
                    url = `http://doafftracking.tech/zaimoo.es/u2wsh/1`;
                } else if (loanAmount > 750 && loanAmount <= 1000) {
                    url = `http://doafftracking.tech/credityes.es/u2wsh/1`;
                }
                window.open(url, '_blank');
            } else {
                alert("El monto del minicrédito debe estar entre 50 y 1000 euros.");
            }
        });
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Préstamos</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; background-color: #f5f5f5; }
        .container { padding: 10px; text-align: center; max-width: 300px; margin: 0 auto; }
        label { font-weight: bold; display: block; margin-bottom: 5px; }
        input[type="range"] { width: 100%; height: 10px; background: #ddd; outline: none; }
        input[type="range"]::-webkit-slider-thumb { width: 20px; height: 20px; background: #007BFF; border-radius: 50%; }
        input[type="range"]::-moz-range-thumb { width: 20px; height: 20px; background: #007BFF; border-radius: 50%; }
        .apply-button { display: inline-block; padding: 10px 20px; margin-top: 10px; background-color: #28a745; color: #fff; font-size: 1em; font-weight: bold; text-decoration: none; border-radius: 5px; cursor: pointer; }
        .apply-button:hover { background-color: #218838; }
    </style>
</head>
<body>
    <div class="container">
        <div>
            <label for="loanAmount">Préstamo: €<span id="loanAmountValue">1000</span></label>
            <input type="range" id="loanAmount" min="1000" max="60000" value="1000" step="100" oninput="updateLoanAmount()">
        </div>
        <div>
            <label for="loanTerm">Plazo: <span id="loanTermValue">1</span> mes(es)</label>
            <input type="range" id="loanTerm" min="1" max="240" value="1" step="1" oninput="updateLoanTerm()">
        </div>
        <button id="applyButton" class="apply-button">Solicitar</button>
    </div>
    <script>
        function updateLoanAmount() {
            const loanAmount = document.getElementById('loanAmount').value;
            document.getElementById('loanAmountValue').textContent = loanAmount;
        }

        function updateLoanTerm() {
            const loanTerm = document.getElementById('loanTerm').value;
            document.getElementById('loanTermValue').textContent = loanTerm;
        }

        document.getElementById('applyButton').addEventListener('click', function() {
            const loanAmount = document.getElementById('loanAmount').value;
            const loanTerm = document.getElementById('loanTerm').value;
            let url;

            if (loanAmount >= 1000 && loanAmount <= 10000) {
                url = `https://track.adtraction.com/t/t?a=1497931818&as=1889896122&t=2&tk=1&amount=${loanAmount}&term=${loanTerm}`;
            } else if (loanAmount > 10000 && loanAmount <= 20000) {
                url = `https://track.adtraction.com/t/t?a=1861732160&as=1889896122&t=2&tk=1&amount=${loanAmount}&term=${loanTerm}`;
            } else if (loanAmount > 20000 && loanAmount <= 30000) {
                url = `https://track.adtraction.com/t/t?a=1498404511&as=1889896122&t=2&tk=1&amount=${loanAmount}&term=${loanTerm}`;
            } else if (loanAmount > 30000 && loanAmount <= 40000) {
                url = `https://track.adtraction.com/t/t?a=1498404511&as=1889896122&t=2&tk=1&amount=${loanAmount}&term=${loanTerm}`;
            } else if (loanAmount > 40000 && loanAmount <= 50000) {
                url = `https://track.adtraction.com/t/t?a=1498404511&as=1889896122&t=2&tk=1&amount=${loanAmount}&term=${loanTerm}`;
            } else if (loanAmount > 50000 && loanAmount <= 60000) {
                url = `https://track.adtraction.com/t/t?a=1498404511&as=1889896122&t=2&tk=1&amount=${loanAmount}&term=${loanTerm}`;
            }

            window.open(url, '_blank');
        });
    </script>
</body>
</html>

