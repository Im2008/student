---
toc: true
comments: true
layout: post
title: Game Of Life
description: The game of life is a randomly generated game where black squares are implemented on a white base where it'll keep spreading or decreasing depending on random chance.
courses: {'csse': {'week': 4} }
type: hacks
---


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ian's Game Of Life</title>
    <style>
        .cell {
            width: 20px;
            height: 20px;
            border: 1px solid #ccc;
            display: inline-block;
        }
    </style>
</head>
<body>
    <h1>Ian's Game Of Life</h1>
    <button onclick="startGame()">Start</button>
    <button onclick="stopGame()">Stop</button>
    <button onclick="clearGrid()">Clear</button>
    <button onclick="randomizeGrid()">Randomize</button>
    <div id="grid-container"></div>
    <script>
        const numRows = 30; // Number of rows in the grid
        const numCols = 50; // Number of columns in the grid
        const cellSize = 20; // Size of each cell in pixels
        const speed = 100; // Speed of the simulation in milliseconds
        let grid = createGrid();
        let intervalId;
        function createGrid() {
            const gridContainer = document.getElementById('grid-container');
            gridContainer.style.gridTemplateColumns = `repeat(${numCols}, ${cellSize}px)`;
            const grid = [];
            for (let i = 0; i < numRows; i++) {
                const row = [];
                for (let j = 0; j < numCols; j++) {
                    const cell = document.createElement('div');
                    cell.className = 'cell';
                    cell.addEventListener('click', () => toggleCell(i, j));
                    gridContainer.appendChild(cell);
                    row.push(false);
                }
                grid.push(row);
            }
            return grid;
        }
        function toggleCell(row, col) {
            grid[row][col] = !grid[row][col];
            const cell = document.getElementsByClassName('cell')[row * numCols + col];
            cell.style.backgroundColor = grid[row][col] ? 'black' : 'white';
        }
        function startGame() {
            intervalId = setInterval(updateGrid, speed);
        }
        function stopGame() {
            clearInterval(intervalId);
        }
        function clearGrid() {
            stopGame();
            grid = grid.map(row => row.fill(false));
            const cells = document.getElementsByClassName('cell');
            for (const cell of cells) {
                cell.style.backgroundColor = 'white';
            }
        }
        function randomizeGrid() {
            clearGrid();
            for (let i = 0; i < numRows; i++) {
                for (let j = 0; j < numCols; j++) {
                    if (Math.random() < 0.2) {
                        toggleCell(i, j);
                    }
                }
            }
        }
        function updateGrid() {
            const newGrid = grid.map(row => [...row]);
            for (let i = 0; i < numRows; i++) {
                for (let j = 0; j < numCols; j++) {
                    const neighbors = countNeighbors(i, j);
                    if (grid[i][j]) {
                        newGrid[i][j] = neighbors === 2 || neighbors === 3;
                    } else {
                        newGrid[i][j] = neighbors === 3;
                    }
                }
            }
            grid = newGrid;
            const cells = document.getElementsByClassName('cell');
            for (let i = 0; i < numRows; i++) {
                for (let j = 0; j < numCols; j++) {
                    const cell = cells[i * numCols + j];
                    cell.style.backgroundColor = grid[i][j] ? 'black' : 'white';
                }
            }
        }
        function countNeighbors(row, col) {
            let count = 0;
            const neighbors = [
                [-1, -1], [-1, 0], [-1, 1],
                [0, -1],           [0, 1],
                [1, -1], [1, 0], [1, 1],
            ];
            for (const [dx, dy] of neighbors) {
                const newRow = row + dx;
                const newCol = col + dy;
                if (newRow >= 0 && newRow < numRows && newCol >= 0 && newCol < numCols) {
                    count += grid[newRow][newCol] ? 1 : 0;
                }
            }
            return count;
        }
    </script>
</body>
</html>