
<!DOCTYPE html>
<html lang="es">
<head>
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
<label for="loanAmount">Minicrédito:</label>
<input type="range" id="loanAmount" min="50" max="1000" value="50" oninput="updateLoanAmount()">
<span id="loanAmountValue">50</span> €<br><br>
<label for="loanTerm">Plazo:</label>
<input type="text" id="loanTerm" value="1" oninput="updateLoanTerm()">
<span id="loanTermValue">1</span> día(s)<br><br>
<button id="applyButton" class="apply-button">Solicitar</button>
<div id="loanOptions"></div>
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
        loanOptionsDiv.innerHTML += '<a href="http://doafftracking.tech/zaimoo.es/u2wsh/1">Enlace 1</a>';
    } else if (amount > 100 && amount <= 750) {
        loanOptionsDiv.innerHTML += '<a href="http://doafftracking.tech/zaimoo.es/u2wsh/1">Enlace 2</a>';
    } else if (amount > 750 && amount <= 1000) {
        loanOptionsDiv.innerHTML += '<a href="http://doafftracking.tech/credityes.es/u2wsh/1">Enlace 3</a>';
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
