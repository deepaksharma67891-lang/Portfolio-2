<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Calculator</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #1f1f2e, #2c2c54);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

/* Calculator box */
.calculator {
    background: #111;
    padding: 20px;
    border-radius: 20px;
    box-shadow: 0 0 25px rgba(0,255,255,0.3);
    width: 300px;
}

/* Display */
#display {
    width: 100%;
    height: 60px;
    font-size: 24px;
    border: none;
    border-radius: 10px;
    margin-bottom: 10px;
    text-align: right;
    padding: 10px;
    background: #000;
    color: #00ffcc;
}

/* Buttons */
.grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    height: 60px;
    font-size: 18px;
    border: none;
    border-radius: 12px;
    background: #222;
    color: white;
    cursor: pointer;
    transition: 0.2s;
}

button:hover {
    background: #00f7ff;
    color: black;
    transform: scale(1.05);
}

.operator {
    background: #ff4081;
}

.operator:hover {
    background: #ff79a8;
}

/* Footer */
.footer {
    text-align: center;
    margin-top: 10px;
    font-size: 12px;
    color: #aaa;
}
</style>
</head>

<body>

<div class="calculator">
    <input type="text" id="display" readonly>

    <div class="grid">
        <button onclick="clearDisplay()">C</button>
        <button onclick="deleteLast()">⌫</button>
        <button onclick="append('%')">%</button>
        <button class="operator" onclick="append('/')">÷</button>

        <button onclick="append('7')">7</button>
        <button onclick="append('8')">8</button>
        <button onclick="append('9')">9</button>
        <button class="operator" onclick="append('*')">×</button>

        <button onclick="append('4')">4</button>
        <button onclick="append('5')">5</button>
        <button onclick="append('6')">6</button>
        <button class="operator" onclick="append('-')">−</button>

        <button onclick="append('1')">1</button>
        <button onclick="append('2')">2</button>
        <button onclick="append('3')">3</button>
        <button class="operator" onclick="append('+')">+</button>

        <button onclick="append('0')">0</button>
        <button onclick="append('.')">.</button>
        <button class="operator" onclick="calculate()">=</button>
    </div>

    <div class="footer">Made by Deepak 🚀</div>
</div>

<script>
let display = document.getElementById("display");

function append(value) {
    display.value += value;
}

function clearDisplay() {
    display.value = "";
}

function deleteLast() {
    display.value = display.value.slice(0, -1);
}

function calculate() {
    try {
        // Safer evaluation using Function
        let result = Function("return " + display.value)();
        display.value = result;
    } catch {
        display.value = "Error";
    }
}
</script>

</body>
</html>
