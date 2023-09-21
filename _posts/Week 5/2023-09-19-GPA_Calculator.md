---
toc: true
comments: true
layout: post
title: GPA calculator
description: The GPA calculator helps calculate the overall grade of a single student that depends on the grades of other classes.
courses: {'csse': {'week': 5} }
type: hacks
---

<html>
<head>
    <title>GPA calculator</title>
</head>
<body>
    <!-- Help Message -->
    <h3>Input scores, press tab to add each new grade.</h3>
    <p>(A+, A) = 4.0 <br>
    (A-) = 3.7 <br>
    (B+) = 3.3 <br>
    (B) = 3.0 <br>
    (B-) = 2.7 <br>
    (C+) = 2.4 <br>
    (C) = 2.1 <br>
    (C-) = 1.8 <br>
    (D+) = 1.5 <br>
    (D) = 1.2 <br>
    (D-) = 1.0 <br>
    (F) = 0.0 <!--It's 0.00001, however, the calculator won't count the letter if it's directly equal to 0. --><br>
    </p>
    <!-- Instructions -->
    <h2>Please put a letter in the box, or a number between 0 and 4, and it’ll calculate it based on the key above.</h2>
    <!-- Totals -->
    <ul>
        <li>
            Total : <span id="total">0.0</span>
            Count : <span id="count">0</span>
            Average : <span id="average">0.0</span>
            Pass/Fail : <span id="passFail">N/A</span>
        </li>
    </ul>
    <!-- Rows added using scores ID -->
    <div id="scores">
        <!-- JavaScript-generated inputs -->
    </div>
    <script>
        // GPA mapping (saves it in a variable and uses it like a memory card)
        const gpaMapping = {
            "A+": 4.0,
            "A": 4.0,
            "A-": 3.7,
            "B+": 3.3,
            "B": 3.0,
            "B-": 2.7,
            "C+": 2.4,
            "C": 2.1,
            "C-": 1.8,
            "D+": 1.5,
            "D": 1.2,
            "D-": 1.0,
            "F": 0.0,
        };
        // Passing GPA value
        const passingGPA = 2.0; // Adjust this as needed
        // Executes on input event and calculates totals
        function calculator(event) {
            var key = event.key;
            // Check if the pressed key is the "Tab" key (key code 9) or "Enter" key (key code 13)
            if (key === "Tab" || key === "Enter") {
                event.preventDefault(); // Prevent default behavior (tabbing to the next element)
                var array = document.getElementsByName('score'); // setup array of scores
                var total = 0; // running total
                var count = 0; // count of input elements with valid values
                for (var i = 0; i < array.length; i++) { // iterate through array
                    var value = array[i].value.trim().toUpperCase(); // Convert input to uppercase and remove extra spaces
                    if (gpaMapping[value] !== undefined) {
                        total += gpaMapping[value]; // add GPA value to running total
                        count++;
                    } else if (!isNaN(value) && value >= 0 && value <= 4) {
                        total += parseFloat(value); // add numeric value to running total
                        count++;
                    }
                }
                // Calculate average GPA
                var averageGPA = count > 0 ? (total / count).toFixed(2) : "0.0";
                // Update totals
                document.getElementById('total').innerHTML = total.toFixed(2); // show two decimals
                document.getElementById('count').innerHTML = count;
                document.getElementById('average').innerHTML = averageGPA;
                // Determine pass/fail
                var passFail = averageGPA >= passingGPA ? "Pass" : "Fail";
                document.getElementById('passFail').innerHTML = passFail;
                // Adds newInputLine, only if all array values satisfy GPA mapping
                if (count === document.getElementsByName('score').length) {
                    newInputLine(count); // make a new input line
                }
            }
        }
        // Creates a new input box
        function newInputLine(index) {
            // Add a label for each score element
            var title = document.createElement('label');
            title.htmlFor = index;
            title.innerHTML = index + ". ";
            document.getElementById("scores").appendChild(title); // add to HTML
            // Setup score element and attributes
            var score = document.createElement("input"); // input element
            score.id = index; // id of input element
            score.onkeydown = calculator; // Each key triggers event (using function as a value)
            score.type = "text"; // Use text type to allow typing letter grades or numbers
            score.name = "score"; // name is used to group all "score" elements (array)
            score.style.textTransform = "uppercase"; // Convert input to uppercase
            score.style.textAlign = "right";
            score.style.width = "5em";
            document.getElementById("scores").appendChild(score); // add to HTML
            // Create and add a blank line after the input box
            var br = document.createElement("br"); // line break element
            document.getElementById("scores").appendChild(br); // add to HTML
            // Set focus on the new input line
            document.getElementById(index).focus();
        }
        // Creates 1st input box on Window load
        newInputLine(0);
    </script>
</body>
</html>

