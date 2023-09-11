---
title: JavaScript Output
description: Quick launch into Variables, Functions, Arrays, Classes, HTML.
layout: default
courses: {'csse': {'week': 5}, 'csp': {'week': 2, 'categories': ['1.A', '3.B']}, 'csa': {'week': 1}}
type: ccc
week: 4
---

## JavaScript and Jupyter references
> JavaScript is the most important language you need to learn as a frontend developer.  Jupyter Notebooks is a convenient way to learn the language without the overhead of creating a full Website.  Jupyter Notebooks had ChatGPT plugins to assist with design and troubleshooting problems.  This Notebook has colors on HTML pages that were designed with a dark mode background.

- JavaScript / Jupyter General References
    - [W3Schools JS Reference](https://www.w3schools.com/js/)
    - ChatGPT AI assistant for [Chrome/Jupyter](https://chrome.google.com/webstore/detail/chatgpt-jupyter-ai-assist/dlipncbkjmjjdpgcnodkbdobkadiejll) 
    - Theme setup for Jupyter [Article](https://linuxhint.com/change-theme-jupyter-notebook/).  Or do these commands from shell...
        - Install pip: pip install jupyterthemes
        - Revert to original theme: jt -r 
        - List themes: jt -l
        - Install with Theme, Name, Logo: jt -t onedork -T -N -kl
    - [Chrome Dev Tools](https://developer.chrome.com/docs/devtools/)

- Coding with jQuery
    - Jupyter Notebook [GitHub](https://github.com/nighthawkcoders/APCSP/blob/master/_notebooks/2022-09-19-PBL-javascript_tutorial.ipynb), wget: https://raw.githubusercontent.com/nighthawkcoders/APCSP/master/_notebooks/2022-09-19-PBL-javascript_tutorial.ipynb
    - Markdown [Fetch example](https://nighthawkcoders.github.io/APCSP/frontend/jquery) in GitHub project for [APCSP](https://github.com/nighthawkcoders/APCSP/blob/master/_posts/2023-06-01-jquery-sort.md)
    - HTML [Static example](https://flask.nighthawkcodingsociety.com/table/) in GitHub project for [flask_portfolio](https://github.com/nighthawkcoders/flask_portfolio/blob/main/templates/table.html)
 


### output using HTML and CSS
 Multiple cells are used to setup HTML in this lesson. Many of the JavaScript cells will use the output tag(s) to write into the HTML that has been setup.  
- %%html is used to setup HTML code block
- "style" tag enables visuals customization
- "div" tag is setup to receive data


```python
%%html
<html>
    <head>
        <style>
            #output {
                background-color: #353b45;
                padding: 10px;
                border: 3px solid #ccc;
            }
        </style>
    </head>
    <body>
        <div id="output">
            Hello!
        </div>
    </body>
</html>
```


<html>
    <head>
        <style>
            #output {
                background-color: #353b45;
                padding: 10px;
                border: 3px solid #ccc;
            }
        </style>
    </head>
    <body>
        <div id="output">
            Hello!
        </div>
    </body>
</html>



### output explored
There are several ways to ouput the classic introduction message: "Hello, World!" 
- Before you go further, open Console on your Browser. <mark>JavaScript developer leaves Console open</mark> all the time!!!
- The function <mark>console.log()</mark> outputs to Console, this is often used for inspection or debugging.
- "Hello, World" is a String literal. This is the referred to as <mark>Static text</mark>, as it does not change.  Developer call this a <mark>hard coded string</mark>.
- <mark>"Hello, World" literal is a parameter</mark> to console.log(), element.txt() and alert().
- The element.txt function is part of <mark>Jupyter Notebook %%js magic</mark>.  This is convenient for Notebook and testing.
- The <mark>alert command outputs the parameter to a dialog box</mark>, so you can see it in this Jupyter notebook. The alert commands are shown, but are commented out as the stop run all execution of the notebook.
- Note, in a Web Application Debugging: An alert is often used for less savy Developers. Console is used by more savy developers; console often requires setting up a lot of outputs. Source level debugging is the most powerful solution for debugging and does not require alert or console commands.


```python
%%js // required to allow cell to be JavaScript enabled
console.log("JavaScript/Jupyter Output Intro");

// Browser Console output; debugging or tracing
console.log("Hello, World!");
console.log("Hello, World Again!");

// Document Object Model (DOM) output; output to HTML, CSS which is standard for a Web Page
// <mark>select element method</mark>: DOM native JavaScript get, document.getElementByID
document.getElementById("output").textContent = "Hello, World!";
// <mark>jQuery CSS-style method</mark>: Tag for DOM selector, $('#output')
$('#output').append('<br><b>Hello World Again!');  // br is break or new line, b is bold

// Jupyter built in magic element for testing and convenience of development
element.text("Hello, World!"); // element is output option as part of %%js magic
element.append('<br><b>Hello World Again!');

//alert("Hello, World!");
```


    <IPython.core.display.Javascript object>


### multiple outputs using one variable
This second example is a new <mark>sequence of code</mark>, two or more lines of code forms a sequence.  This example defines a variable, thank goodness!!! In the previous example we were typing the string `"Hello, World" over and over`.  Observe with the variable `msg="Hello, World!";` we type the string once and now use `msg` over and over.
- The variable "var msg =" is used to capture the data
- The console.log(msg) outputs to console, be sure to Inspect it!
- The element.text() is part of Jupyter Notebooks and displays as output blow the code on this page. Until we build up some more interesting data for Web Site, we will not use be using the Python HTML, CSS technique.
- The alert(msg) works the same as previous, but as the other commands uses msg as parameter.


```python
%%js
console.log("Variable Definition");

var msg = "Hello, World!";

// Use msg to output code to Console and Jupyter Notebook
console.log(msg);  //right click browser select Inspect, then select Console to view
element.text(msg);
//alert(msg);

```


    <IPython.core.display.Javascript object>


### output showing use of a function
This example passes the defined variable "msg" to the newly defined "function logIt(output)".
- There are multiple steps in this code..
    - The "definition of the function": "function logIt(output) {}" and everything between curly braces is the definitions of the function. Passing a parameter is required when you call this function.
    - The "call to the function:"logIt(msg)" is the call to the function, this actually runs the function.  The variable "msg" is used a parameter when calling the logIt function.
- Showing reuse of function...
    - There are two calls to the logIt function
    - This is called Prodedural Abstraction, a term that means reusing the same code


```python
%%js
console.log("Function Definition");

/* Function: logIt
 * Parameter: output
 * Description: The parameter is "output" to console and jupyter page
*/
function logIt(output) {
    console.log(output); 
    element.append(output + "<br>");
    //alert(output);
}

// First sequence calling logIt function
var msg = "Hello, World!";
logIt(msg);

// Second sequence calling logIt function
var msg = "Hello, <b>Students</b>!" // replaces content of variable
var classOf = "Welcome CS class of 2023-2024."
logIt(msg + "  " + classOf); // concatenation of strings
```


    <IPython.core.display.Javascript object>


### output showing Loosely typed data
<mark>JavaScript is a loosely typed language</mark>, meaning you don't have to specify what type of information will be stored in a variable in advance.  
- To define a variable you prefix the name with <mark>var or const</mark>.   The variable type is determined by JavaScript at runtime.
- Python and many interpretive languages are loosely typed like JavaScript.  This is considered programmer friendly.  
- Java which is a compiled language is strongly typed, thus you will see terms like <mark>String, Integer, Double, and Object</mark> in the source code. 
- In JavaScript, the <mark>typeof keyword</mark> returns the type of the variable.  Become familiar with type as it is valuable in conversation and knowing type help you understand how to modify data.  Each variable type will have built in methods to manage content within the data type.


```python
%%js
console.log("Examine Data Types");

// Function to add typeof to output
function getType(output) {
    return typeof output + ": " + output;
}

// Function defintion
function logIt(output) {
    console.log(getType(output));  // logs string
    console.info(output);          // logs object
    element.append(getType(output) + "<br>");  // adds to Jupyter output
    //alert(getType(output));
}

// Common Types
element.append("Common Types <br>");
logIt("Mr M"); // String
logIt(1997);    // Number
logIt(true);    // Boolean
element.append("<br>");

// Object Type, this definition is often called a array or list
element.append("Object Type, array <br>");
var scores = [
    90,
    80, 
    100
];  
logIt(scores);
element.append("<br>");

// Complex Object, this definition is often called hash, map, hashmap, or dictionary
element.append("Object Type, hash or dictionary <br>");
var person = { // key:value pairs seperated by comma
    "name": "Mr M", 
    "role": "Teacher"
}; 
logIt(person);
logIt(JSON.stringify(person));  //method used to convert this object into readable format
```


    <IPython.core.display.Javascript object>


### Build a Person object and JSON
JavaScript and other languages have special properties and syntax to store and represent data.  In fact, a class in JavaScript is a special function.

- <mark>Definition of class allows for a collection of data</mark>, the "class Person" allows programmer to retain name, github id, and class of a Person.
- <mark>Instance of a class</mark>, the "const teacher = new Person("Mr M", "jm1021", 1977)" makes an object "teacher" which is an object representation of "class Person".
- <mark>Setting and Getting properties</mark> After creating teacher and student objects, observe that properties can be changed/muted or extracted/accessed.


```python
%%html
<!-- load jQuery and tablesorter scripts -->
<html>
    <head>
        <!-- load jQuery and tablesorter scripts -->
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery.tablesorter/2.31.3/js/jquery.tablesorter.min.js"></script>
        <style>
            /* CSS-style selector maps to table id or other id's in HTML */
            #jsonTable, #flaskTable {
                background-color: #353b45;
                padding: 10px;
                border: 3px solid #ccc;
                box-shadow: 0.8em 0.4em 0.4em grey;
            }
        </style>
    </head>

    <body>
        <!-- Table for writing and extracting jsonText -->
        <table id="jsonTable">
            <thead>
                <tr>
                    <th>Classroom JSON Data</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td id="jsonText">{"classroom":[{"type":"object","name":"sample","ghID":"sample","classOf":2000,"role":"sample"}]}</td>
                </tr>
            </tbody>
        </table>

    </body>
</html>
```


<!-- load jQuery and tablesorter scripts -->
<html>
    <head>
        <!-- load jQuery and tablesorter scripts -->
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery.tablesorter/2.31.3/js/jquery.tablesorter.min.js"></script>
        <style>
            /* CSS-style selector maps to table id or other id's in HTML */
            #jsonTable, #flaskTable {
                background-color: #353b45;
                padding: 10px;
                border: 3px solid #ccc;
                box-shadow: 0.8em 0.4em 0.4em grey;
            }
        </style>
    </head>

    <body>
        <!-- Table for writing and extracting jsonText -->
        <table id="jsonTable">
            <thead>
                <tr>
                    <th>Classroom JSON Data</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td id="jsonText">{"classroom":[{"type":"object","name":"sample","ghID":"sample","classOf":2000,"role":"sample"}]}</td>
                </tr>
            </tbody>
        </table>

    </body>
</html>




```python
%%js
console.log("Person objects");

/* class: Person
 * Description: A collection of Person data
*/
class Person {
  /* method: constructor
   * parameters: name, ghID - GitHub ID, classOf - Graduation Class 
   * description: returns object when "new Person()" is called with matching parameters
   * assignment: this.name, this.ghID, ... are properties retained in the returned object
   * default: role uses a default property, it is set to "Student"
  */
  constructor(name, ghID, classOf, role="Student") {
    this.name = name;
    this.ghID = ghID;
    this.classOf = classOf;
    this.role = role;
  }

  /* method: setter
   * parameters: role - role in classroom
   * description: this.role is updated from default value to value contained in role parameter
  */
  setRole(role) {
    this.role = role;
  }
  
  /* method: getter
   * description: turns properties of object into JSON object
   * return value: JSON object
  */
  getJSON() {
    const obj = {type: typeof this, name: this.name, ghID: this.ghID, classOf: this.classOf, role: this.role};
    const json = JSON.stringify(obj);
    return json;
  }

  /* method: logIT
   * description: "this" Person object is logged to console
  */
  logIt() {
    //Person Object
    console.info(this);
    //Log to Jupter
    element.append("Person object in JSON <br>");
    element.append(this.getJSON() + "<br>");  
    //alert(this.getJSON());
  }
    
}

// make a new Person Object
const teacher = new Person("Mr M", "jm1021", 1977); // object type is easy to work with in JavaScript
// update role to Teacher
teacher.setRole("Teacher"); // set the role
teacher.logIt();  // log to console

// make a new Person Object
const student = new Person("Jane Doe", "jane", 2007); // object type is easy to work with in JavaScript
student.logIt(); // log to console
```


    <IPython.core.display.Javascript object>


### Build a Classroom Array/List of Persons and JSON
Many key elements are shown again.  New elements include...
- <mark>Building an Array</mark>, "var students" is an array of many persons
- Building a Classroom, this show <mark>forEach iteration</mark> through an array and <mark>.push adding</mark> to an array.  These are key concepts in all programming languages.


```python
%%js
console.log("Classroom object");

/* class: Person
 * Description: A collection of Person data
*/
class Person {
  /* method: constructor
   * parameters: name, ghID - GitHub ID, classOf - Graduation Class 
   * description: returns object when "new Person()" is called with matching parameters
   * assignment: this.name, this.ghID, ... are properties retained in the returned object
   * default: this.role is a default property retained in object, it is set to "Student"
  */
  constructor(name, ghID, classOf, role="Student") {
    this.name = name;
    this.ghID = ghID;
    this.classOf = classOf;
    this.role = role;
  }

  /* method: setter
   * parameters: role - role in classroom
   * description: this.role is updated from default value to value contained in role parameter
  */
  setRole(role) {
    this.role = role;
  }
  
  /* method: getter
   * description: turns properties of object into JSON object
   * return value: JSON object
  */
  getJSON() {
    const obj = {type: typeof this, name: this.name, ghID: this.ghID, classOf: this.classOf, role: this.role};
    const json = JSON.stringify(obj);
    return json;
  }

  /* method: logIT
   * description: "this" Person object is logged to console
  */
  logIt() {
    //Person Object
    console.info(this);
    //Log to Jupter
    element.append("Person json <br>");
    element.append(this.getJSON() + "<br>");  
    //alert(this.getJSON());
  }
    
}

/* class: Classroom
 * Description: A collection of Person objects
*/
class Classroom {
  /* method: constructor
   * parameters: teacher - a Person object, students - an array of Person objects
   * description: returns object when "new Classroom()" is called containing properties and methods of a Classroom
   * assignment: this.classroom, this.teacher, ... are properties retained in the returned object
  */
  constructor(teacher, students) {
    /* spread: this.classroom contains Teacher object and all Student objects
     * map: this.json contains of map of all persons to JSON
    */
    this.teacher = teacher;
    this.students = students;
    this.classroom = [teacher, ...students]; // ... spread option
    this.json = '{"classroom":[' + this.classroom.map(person => person.getJSON()) + ']}';
  }

  /* method: logIT
   * description: "this" Classroom object is logged to console
  */
  logIt() {
    //Classroom object
    console.log(this);
    
    //Classroom json
    element.append("Classroom object in JSON<br>");
    element.append(this.json + "<br>");  
    //alert(this.json);
  }
}

/* function: constructCompSciClassroom
 * Description: Create data for Classroom and Person objects
 * Returns: A Classroom Object
*/
function constructCompSciClassroom() {
    // define a Teacher object
    const teacher = new Person("Mr M", "jm1021", 1977, "Teacher");  // optional 4th parameter

    // define a student Array of Person objects
    const students = [ 
        new Person("Anthony", "tonyhieu", 2022),
        new Person("Bria", "B-G101", 2023),
        new Person("Allie", "xiaoa0", 2023),
        new Person("Tigran", "Tigran7", 2023),
        new Person("Rebecca", "Rebecca-123", 2023),
        new Person("Vidhi", "VidhiKulkarni", 2024)
    ];

    // make a CompSci classroom from formerly defined teacher and student objects
    return new Classroom(teacher, students);  // returns object
}

// assigns "compsci" to the object returned by "constructCompSciClassroom()" function
const compsci = constructCompSciClassroom();
// output of Objects and JSON in CompSci classroom
compsci.logIt();
// enable sharing of data across jupyter cells
$('#jsonText').text(compsci.json);  // posts/embeds/writes compsci.json to HTML DOM element called jsonText
```


    <IPython.core.display.Javascript object>


###  for loop to generate Table Rows in HTML output
This code extracts JSON text from HTML, that was placed in DOM in an earlier JavaScript cell, then it parses text into a JavaScript object.  In addition, there is a for loop that iterates over the extracted object generating formated rows and columns in an HTML table.

- Table generation is broken into parts...
    - table data is obtained from a classroom array inside of the extracted object.  
    - the JavaScript for loop allows the construction of a new row of data for each Person hash object inside of the the Array.
    - in the loop a table row `<tr> ... </tr>` is created for each Hash object in the Array.
    - in the loop table data, a table column, `<td> ... </td>` is created for name, ghID, classOf, and role within the Hash object.


```python
%%js
console.log("Classroom Web Page");

// extract JSON text from HTML page
const jsonText = document.getElementById("jsonText").innerHTML;
console.log(jsonText);
element.append("Raw jsonText element embedded in HTML<br>");
element.append( jsonText + "<br>");

// convert JSON text to Object
const classroom = JSON.parse(jsonText).classroom;
console.log(classroom);

// from classroom object creates rows and columns in HTML table
element.append("<br>Formatted data sample from jsonText <br>");
for (var row of classroom) {
    element.append(row.ghID + " " + row.name + '<br>');
    // tr for each row, a new line
    $('#classroom').append('<tr>')
    // td for each column of data
    $('#classroom').append('<td>' + row.name + '</td>')
    $('#classroom').append('<td>' + row.ghID + '</td>')
    $('#classroom').append('<td>' + row.classOf + '</td>')
    $('#classroom').append('<td>' + row.role + '</td>')
    // tr to end row
    $('#classroom').append('</tr>');
}
```


    <IPython.core.display.Javascript object>



```python
%%html
<head>
    <!-- load jQuery and DataTables syle and scripts -->
    <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
    <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>var define = null;</script>
    <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>
<table id="flaskTable" class="table" style="width:100%">
    <thead id="flaskHead">
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>DOB</th>
            <th>Age</th>
        </tr>
    </thead>
    <tbody id="flaskBody"></tbody>
</table>

<script>
  $(document).ready(function() {
    fetch('https://flask.nighthawkcodingsociety.com/api/users/', { mode: 'cors' })
    .then(response => {
      if (!response.ok) {
        throw new Error('API response failed');
      }
      return response.json();
    })
    .then(data => {
      for (const row of data) {
        // BUG warning/resolution - DataTable requires row to be single append
        $('#flaskBody').append('<tr><td>' + 
            row.id + '</td><td>' + 
            row.name + '</td><td>' + 
            row.dob + '</td><td>' + 
            row.age + '</td></tr>');
      }
      // BUG warning - Jupyter does not show Datatable controls, works on deployed GitHub pages
      $("#flaskTable").DataTable();
    })
    .catch(error => {
      console.error('Error:', error);
    });
  });
</script>
```


<head>
    <!-- load jQuery and DataTables syle and scripts -->
    <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.13.4/css/jquery.dataTables.min.css">
    <script type="text/javascript" language="javascript" src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>var define = null;</script>
    <script type="text/javascript" language="javascript" src="https://cdn.datatables.net/1.13.4/js/jquery.dataTables.min.js"></script>
</head>
<table id="flaskTable" class="table" style="width:100%">
    <thead id="flaskHead">
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>DOB</th>
            <th>Age</th>
        </tr>
    </thead>
    <tbody id="flaskBody"></tbody>
</table>

<script>
  $(document).ready(function() {
    fetch('https://flask.nighthawkcodingsociety.com/api/users/', { mode: 'cors' })
    .then(response => {
      if (!response.ok) {
        throw new Error('API response failed');
      }
      return response.json();
    })
    .then(data => {
      for (const row of data) {
        // BUG warning/resolution - DataTable requires row to be single append
        $('#flaskBody').append('<tr><td>' + 
            row.id + '</td><td>' + 
            row.name + '</td><td>' + 
            row.dob + '</td><td>' + 
            row.age + '</td></tr>');
      }
      // BUG warning - Jupyter does not show Datatable controls, works on deployed GitHub pages
      $("#flaskTable").DataTable();
    })
    .catch(error => {
      console.error('Error:', error);
    });
  });
</script>



## Hacks
> One key to these hacks is to build confidence with me going into final grade, I would like to see each student adapt this frontend work in their final project.  Second key is the finished work can serve as review for the course, notes for the future in relationship to frontend.
- Adapt this tutorial to your own work
- Consider what you need to work on to be stronger developer
- Show something creative or unique, no cloning
- Be ready to talk to Teacher for 5 to 10 minutes. Individually!!!
- Show in Jupyter Notebook during discussion, show Theme and ChatGPT
- Have a runtime final in GithHub Pages (or Fastpage)
