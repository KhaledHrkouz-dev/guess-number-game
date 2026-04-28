DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>AI Guess The Number Game</title>

<style>
    body {
        font-family: Arial;
        text-align: center;
        background: #eef2f3;
        padding-top: 40px;
    }

    .box {
        background: white;
        padding: 20px;
        width: 320px;
        margin: auto;
        border-radius: 12px;
        box-shadow: 0px 0px 12px gray;
    }

    input, select {
        padding: 10px;
        width: 85%;
        margin: 8px 0;
    }

    button {
        padding: 10px;
        margin: 5px;
        cursor: pointer;
    }

    #result {
        font-size: 18px;
        margin-top: 10px;
        font-weight: bold;
    }
</style>
</head>

<body>

<div class="box">

    <h2>🎮 Guess The Number Game</h2>

    <h4>Student: Khaled Arkouz</h4>
    <h4>Project: Simple AI Game</h4>

    <p>Select Difficulty:</p>
    <select id="difficulty">
        <option value="50">Easy (1-50)</option>
        <option value="100" selected>Medium (1-100)</option>
        <option value="200">Hard (1-200)</option>
    </select>

    <input type="number" id="guess" placeholder="Enter your guess">

    <br>

    <button onclick="checkGuess()">Check</button>
    <button onclick="newGame()">New Game</button>

    <p id="result">Start the game!</p>
    <p id="attempts">Attempts: 0</p>

</div>

<script>
let number;
let attempts = 0;
let max = 100;

function newGame() {
    max = document.getElementById("difficulty").value;
    number = Math.floor(Math.random() * max) + 1;
    attempts = 0;

    document.getElementById("result").innerText = "🎮 New game started!";
    document.getElementById("attempts").innerText = "Attempts: 0";
    document.getElementById("guess").value = "";
}

function checkGuess() {
    let guess = Number(document.getElementById("guess").value);

    if (!guess) {
        document.getElementById("result").innerText = "❌ Please enter a number!";
        return;
    }

    attempts++;

    if (guess > number) {
        document.getElementById("result").innerText = "📈 Too high!";
    } else if (guess < number) {
        document.getElementById("result").innerText = "📉 Too low!";
    } else {
        document.getElementById("result").innerText =
        "🎉 Correct! You won in " + attempts + " attempts!";
    }

    document.getElementById("attempts").innerText = "Attempts: " + attempts;
}

newGame();
</script>

</body>
</html>
