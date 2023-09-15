---
title: JS Calculator
comments: true
layout: default
description: A common way to become familiar with a language is to build a calculator.  This calculator shows off button with actions.
permalink: /techtalk/home_style
categories: [C7.0]
courses: { csse: {week: 1}}
type: hacks
---

<html>
<head>
    <title>JavaScript Calculator</title>
    <style>
        /* CSS styling goes here */
        .calculator-output {
            grid-column: span 4;
            grid-row: span 1;
            border-radius: 10px;
            padding: 0.25em;
            font-size: 20px;
            border: 5px solid black;
            display: flex;
            align-items: center;
        }
        /* Add more CSS styles as needed */
    </style>
</head>
<body>
    <!-- Calculator buttons and display -->
    <div class="calculator-container">
        <div class="calculator-output" id="output">0</div>
        <div class="calculator-row">
            <div class="calculator-number">1</div>
            <div class="calculator-number">2</div>
            <div class="calculator-number">3</div>
            <div class="calculator-operation">+</div>
        </div>
        <div class="calculator-row">
            <div class="calculator-number">4</div>
            <div class="calculator-number">5</div>
            <div class="calculator-number">6</div>
            <div class="calculator-operation">-</div>
        </div>
        <div class="calculator-row">
            <div class="calculator-number">7</div>
            <div class="calculator-number">8</div>
            <div class="calculator-number">9</div>
            <div class="calculator-operation">*</div>
        </div>
        <div class="calculator-row">
            <div class="calculator-clear">A/C</div>
            <div class="calculator-number">0</div>
            <div class="calculator-number">.</div>
            <div class="calculator-equals">=</div>
        </div>
    </div>
    <!-- JavaScript implementation -->
    <script>
        // Initialize variables
        let firstNumber = null;
        let operator = null;
        let nextReady = true;
        const output = document.getElementById("output");
        const numbers = document.querySelectorAll(".calculator-number");
        const operations = document.querySelectorAll(".calculator-operation");
        const clear = document.querySelectorAll(".calculator-clear");
        const equals = document.querySelectorAll(".calculator-equals");
        // Add event listeners for number buttons
        numbers.forEach(button => {
            button.addEventListener("click", () => number(button.textContent));
        });
        // Input numbers into the calculator
        function number(value) {
            if (value !== ".") {
                if (nextReady) {
                    output.innerHTML = value;
                    if (value !== "0") {
                        nextReady = false;
                    }
                } else {
                    output.innerHTML += value;
                }
            } else {
                if (output.innerHTML.indexOf(".") === -1) {
                    output.innerHTML += value;
                    nextReady = false;
                }
            }
        }
        // Add event listeners for operation buttons
        operations.forEach(button => {
            button.addEventListener("click", () => operation(button.textContent));
        });
        // Input operations into the calculator
        function operation(choice) {
            if (firstNumber === null) {
                firstNumber = parseFloat(output.innerHTML);
                nextReady = true;
                operator = choice;
                return;
            }
            firstNumber = calculate(firstNumber, parseFloat(output.innerHTML));
            operator = choice;
            output.innerHTML = firstNumber.toString();
            nextReady = true;
        }
        // Calculate the result of the equation
        function calculate(first, second) {
            switch (operator) {
                case "+":
                    return first + second;
                case "-":
                    return first - second;
                case "*":
                    return first * second;
                case "/":
                    if (second === 0) {
                        alert("Cannot divide by zero!");
                        return first;
                    }
                    return first / second;
                default:
                    return first;
            }
        }
        // Add event listener for equals button
        equals.forEach(button => {
            button.addEventListener("click", equal);
        });
        // Calculate and display the result
        function equal() {
            firstNumber = calculate(firstNumber, parseFloat(output.innerHTML));
            output.innerHTML = firstNumber.toString();
            nextReady = true;
        }
        // Add event listener for clear button
        clear.forEach(button => {
            button.addEventListener("click", clearCalc);
        });
        // Clear the calculator
        function clearCalc() {
            firstNumber = null;
            output.innerHTML = "0";
            nextReady = true;
        }
    </script>
</body>
</html>


