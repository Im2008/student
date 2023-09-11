---
toc: True
comments: True
layout: post
title: Tic Tac Toe Game
description:
courses: {'csse': {'week': 3} }
type: hacks
---

<html lang="en">
<head>
<button id="restart-button">New Game</button>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic Tac Toe</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        .board {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            gap: 5px;
            margin: 20px auto;
        }
        .cell {
            width: 100px;
            height: 100px;
            font-size: 36px;
            text-align: center;
            vertical-align: middle;
            border: 2px solid #333;
            cursor: pointer;
        }
        .cell:hover {
            background-color: #eee;
        }
        .message {
            font-size: 24px;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <h1>Tic Tac Toe</h1>
    <div class="message">Player X's Turn</div>
    <div class="board" id="board">
        <!-- Create the game board cells -->
    </div>
    <script>
        const board = document.getElementById("board");
        const cells = [];
        let currentPlayer = "X";
        let gameActive = true;
        // Initialize the game board
        for (let i = 0; i < 9; i++) {
            const cell = document.createElement("div");
            cell.classList.add("cell");
            cell.dataset.index = i;
            cell.addEventListener("click", () => handleCellClick(i));
            cells.push(cell);
            board.appendChild(cell);
        }
        // Function to handle cell clicks
        function handleCellClick(index) {
            if (!gameActive || cells[index].textContent !== "") {
                return;
            }
            cells[index].textContent = currentPlayer;
            cells[index].classList.add("occupied");
            if (checkWin() || checkDraw()) {
                gameActive = false;
                return;
            }
            currentPlayer = currentPlayer === "X" ? "O" : "X";
            document.querySelector(".message").textContent = `Player ${currentPlayer}'s Turn`;
        }
        // Function to check for a win
        function checkWin() {
            const winningCombos = [
                [0, 1, 2],
                [3, 4, 5],
                [6, 7, 8],
                [0, 3, 6],
                [1, 4, 7],
                [2, 5, 8],
                [0, 4, 8],
                [2, 4, 6]
            ];
            for (const combo of winningCombos) {
                const [a, b, c] = combo;
                if (
                    cells[a].textContent &&
                    cells[a].textContent === cells[b].textContent &&
                    cells[a].textContent === cells[c].textContent
                ) {
                    document.querySelector(".message").textContent = `Player ${currentPlayer} Wins!`;
                    cells[a].classList.add("winner");
                    cells[b].classList.add("winner");
                    cells[c].classList.add("winner");
                    return true;
                }
            }
            return false;
        }
        // Function to check for a draw
        function checkDraw() {
            if (cells.every(cell => cell.textContent !== "")) {
                document.querySelector(".message").textContent = "It's a Draw!";
                return true;
            }
            return false;
        }
        // Add event listener to the restart button
        const restartButton = document.getElementById("restart-button");
        restartButton.addEventListener("click", () => restartGame());
        function restartGame() {
        // Clear the board and reset variables
            cells.forEach(cell => {
                cell.textContent = "";
                cell.classList.remove("occupied", "winner");
            });
            currentPlayer = "X";
            gameActive = true;
            document.querySelector(".message").textContent = `Player ${currentPlayer}'s Turn`;
}
    </script>
</body>
</html>