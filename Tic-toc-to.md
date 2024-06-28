<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
    body {
    font-family: 'Arial', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.game-container {
    text-align: center;
}

.grid {
    display: grid;
    grid-template-columns: repeat(3, 100px);
    gap: 5px;
    margin-bottom: 10px;
}

.cell {
    width: 100px;
    height: 100px;
    border: 2px solid #333;
    font-size: 2em;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    color: #80FF00;
}

.cell:hover {
    background-color: #E7FED1
}

.result {
    font-size: 1.5em;
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
    body {
    font-family: 'Arial', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.game-container {
    text-align: center;
}

.grid {
    display: grid;
    grid-template-columns: repeat(3, 100px);
    gap: 5px;
    margin-bottom: 10px;
}

.cell {
    width: 100px;
    height: 100px;
    border: 2px solid #333;
    font-size: 2em;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    color: #80FF00;
}

.cell:hover {
    background-color: #E7FED1
}

.result {
    font-size: 1.5em;
    margin-bottom: 10px;
}

button {
    font-size: 1em;
    padding: 5px 10px;
    cursor: pointer;
}
</style>
    <title>Tic Tac Toe</title>
</head>
<body>
    <div class="game-container">
        <div class="grid" id="grid">
            <!-- Grid cells will be dynamically created here -->
        </div>
        <div id="result" class="result"></div>
        <button onclick="resetGame()">Reset Game</button>
    </div>
    <script >let currentPlayer = 'X';
let gameBoard = ['', '', '', '', '', '', '', '', ''];
let gameActive = true;

function handleCellClick(index) {
    if (gameBoard[index] === '' && gameActive) {
        gameBoard[index] = currentPlayer;
        document.getElementById('grid').children[index].innerText = currentPlayer;
        
        if (checkWinner()) {
            document.getElementById('result').innerText = `Player ${currentPlayer} wins!`;
            gameActive = false;
        } else if (gameBoard.every(cell => cell !== '')) {
            document.getElementById('result').innerText = 'It\'s a draw!';
            gameActive = false;
        } else {
            currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
        }
    }
}

function checkWinner() {
    const winPatterns = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8], // Rows
        [0, 3, 6], [1, 4, 7], [2, 5, 8], // Columns
        [0, 4, 8], [2, 4, 6]             // Diagonals
    ];

    return winPatterns.some(pattern => {
        const [a, b, c] = pattern;
        return gameBoard[a] !== '' && gameBoard[a] === gameBoard[b] && gameBoard[b] === gameBoard[c];
    });
}

function resetGame() {
    currentPlayer = 'X';
    gameBoard = ['', '', '', '', '', '', '', '', ''];
    gameActive = true;

    document.getElementById('result').innerText = '';
    
    const cells = document.getElementById('grid').children;
    for (let i = 0; i < cells.length; i++) {
        cells[i].innerText = '';
    }
}

// Dynamically create grid cells
const gridContainer = document.getElementById('grid');
for (let i = 0; i < 9; i++) {
    const cell = document.createElement('div');
    cell.className = 'cell';
    cell.addEventListener('click', () => handleCellClick(i));
    gridContainer.appendChild(cell);
}

</script>
</body>
</html>
￼Enter    margin-bottom: 10px;
}

button {
    font-size: 1em;
    padding: 5px 10px;
    cursor: pointer;
}
</style>
    <title>Tic Tac Toe</title>
</head>
<body>
    <div class="game-container">
        <div class="grid" id="grid">
            <!-- Grid cells will be dynamically created here -->
        </div>
        <div id="result" class="result"></div>
        <button onclick="resetGame()">Reset Game</button>
    </div>
    <script >let currentPlayer = 'X';
let gameBoard = ['', '', '', '', '', '', '', '', ''];
let gameActive = true;

function handleCellClick(index) {
    if (gameBoard[index] === '' && gameActive) {
        gameBoard[index] = currentPlayer;
  document.getElementById('grid').children[index].innerText = currentPlayer;
        
        if (checkWinner()) {
            document.getElementById('result').innerText = `Player ${currentPlayer} wins!`;
            gameActive = false;
        } else if (gameBoard.every(cell => cell !== '')) {
            document.getElementById('result').innerText = 'It\'s a draw!';
            gameActive = false;
        } else {
            currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
        }
    }
}

function checkWinner() {
    const winPatterns = [
        [0, 1, 2], [3, 4, 5], [6, 7, 8], // Rows
        [0, 3, 6], [1, 4, 7], [2, 5, 8], // Columns
        [0, 4, 8], [2, 4, 6]             // Diagonals
    ];

    return winPatterns.some(pattern => {
        const [a, b, c] = pattern;
        return gameBoard[a] !== '' && gameBoard[a] === gameBoard[b] && gameBoard[b] === gameBoard[c];
    });
}
