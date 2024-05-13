# 1. Introduction to JavaScript

## Overview of JavaScript:

JavaScript is a high-level, interpreted programming language primarily used for adding interactivity to web pages. It was initially developed by Brendan Eich at Netscape and has since become one of the most popular programming languages in the world.

## Setting up Development Environment:
To start coding in JavaScript, you need a text editor and a web browser. Popular text editors include Visual Studio Code, Sublime Text, and Atom. You can write JavaScript directly within an HTML file or link an external JavaScript file to your HTML document using the `<`script`>` tag.

## Basic Syntax and Structure:
JavaScript syntax is similar to other programming languages like C++ and Java. Here's a basic structure of a JavaScript program:

``` javascript
// This is a single-line comment

/*
   This is a multi-line comment
*/

// Declaring a variable
var message = "Hello, World!";

// Displaying a message in the console
console.log(message);

```

## 2. Data Types and Variables
### Primitive Data Types:
JavaScript has six primitive data types: `String`, `Number`, `Boolean`, `Null`, `Undefined`, and `Symbol` (added in ECMAScript 6).

```javascript
var name = "John"; // String
var age = 30; // Number
var isMale = true; // Boolean
var car = null; // Null
var city; // Undefined
```
### Complex Data Types:
JavaScript has two complex data types: `Object` and `Array`.

``` javascript
var person = {
    name: "John",
    age: 30,
    city: "New York"
};

var fruits = ["Apple", "Banana", "Orange"];
```

### Variables and Constants:
In JavaScript, you can declare variables using the `var`, `let`, or `const` keywords. Variables declared with var have function-level scope, while those declared with let and const have block-level scope.

```javascript
var x = 10;
let y = 20;
const PI = 3.14;
```
`var` Example:
```javascript
function display(){
    var x = 10;
    console.log(x);
}
function display_2(){
    console.log(x);
}
display();      // 10
display_2();    // 10
```
`let` & `const` Scoping Example:
```javascript
function display(){
    let x = 10;
    const y = 20;
    console.log(x, y);
}

function display_2(){
    console.log(x, y);
}
display();      // 10 20
display_2();    // ReferenceError: x,y is not defined
```
`const` Example:
```javascript
const x = 20;
x = 30; // TypeError: Assignment to constant variable.
```
## 3. Control Flow and Loops

# Conditional Statements:
Conditional statements allow you to execute different blocks of code based on specified conditions. JavaScript supports `if`, `else if`, and `else` statements, as well as the `switch` statement.

```javascript
var age = 18;

if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}

// Switch statement
var day = "Monday";

switch (day) {
    case "Monday":
        console.log("Today is Monday.");
        break;
    case "Tuesday":
        console.log("Today is Tuesday.");
        break;
    default:
        console.log("Today is not Monday or Tuesday.");
}
```

# Loops:
Loops are used to execute a block of code repeatedly. JavaScript supports `for`, `while`, and `do-while` loops.
```javascript
// For loop
for (var i = 1; i <= 5; i++) {
    console.log(i);
}

// While loop
var count = 0;
while (count < 5) {
    console.log(count);
    count++;
}

// Do-while loop
var num = 1;
do {
    console.log(num);
    num++;
} while (num <= 5);
```

#### Practice Questions:
- Write a program to check if a number is even or odd using conditional statements.
- Implement a for loop to print numbers from 1 to 10.
- Rewrite a given for loop using a while loop and vice versa.

## 4. Functions
### Declaring and Invoking Functions:
Functions in JavaScript are declared using the `function` keyword. They can be invoked using the function name followed by parentheses.
```javascript
// Function declaration
function greet() {
    console.log("Hello!");
}

// Function invocation
greet();
```
### Function Parameters and Return Values:
Functions can accept parameters and return values.
```javascript
// Function with parameters
function greet(name) {
    console.log("Hello, " + name + "!");
}

// Function with return value
function add(a, b) {
    return a + b;
}

var sum = add(5, 3); // sum = 8
```
### Scope and Closures:
JavaScript has function scope, meaning variables defined within a function are only accessible within that function. Closures allow functions to access variables from their outer scope even after the outer function has finished executing.
```javascript
// Function scope
function myFunction() {
    var x = 10;
    console.log(x); // Outputs 10
}

// Closure
function outerFunction() {
    var x = 10;

    function innerFunction() {
        console.log(x); // Outputs 10
    }

    return innerFunction;
}

var closureFunction = outerFunction();
closureFunction();
```
## 5. Arrays and Objects
### Array Methods:
JavaScript arrays come with built-in methods that make it easier to work with arrays. Some commonly used methods include `map`, `filter`, `reduce`, and `forEach`.
```javascript
// Map
var numbers = [1, 2, 3, 4, 5];
var doubled = numbers.map(function(num) {
    return num * 2;
});
//Output: [2, 4, 6, 8, 10] 

// Filter
var evenNumbers = numbers.filter(function(num) {
    return num % 2 === 0;
});
// Output: [2, 4]

// Reduce
var sum = numbers.reduce(function(acc, curr) {
    return acc + curr;
}, 0);
// Output: 15


// forEach
numbers.forEach(function(num) {
    console.log(num);
});
```

### Object Properties and Methods:
Objects in JavaScript can contain properties and methods.
```javascript
var person = {
    firstName: "John",
    lastName: "Doe",
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};

console.log(person.fullName()); // Outputs "John Doe"
```
### Object-oriented Programming Concepts:
JavaScript supports object-oriented programming (OOP) concepts like inheritance, encapsulation, and polymorphism.
```javascript
// Inheritance
function Animal(name) {
    this.name = name;
}

Animal.prototype.sound = function() {
    console.log("Animal sound");
};

function Dog(name) {
    Animal.call(this, name);
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.sound = function() {
    console.log("Woof");
};

var dog = new Dog("Buddy");
dog.sound(); // Outputs "Woof"
```
#### Practice Questions:
- Use array methods to manipulate an array of numbers (e.g., filter out even numbers, find the sum of all elements).
- Create an object representing a person with properties like name, age, and city. Add methods to modify these properties.
- Implement inheritance in JavaScript using prototype chaining.

## 6. Asynchronous JavaScript
### Callbacks:
Callbacks are functions passed as arguments to another function and are executed after the completion of an asynchronous operation.
```javascript
function fetchData(callback) {
    setTimeout(function() {
        callback("Data fetched");
    }, 1000);
}

fetchData(function(data) {
    console.log(data);
});
```

### Promises:
Promises are objects representing the eventual completion or failure of an asynchronous operation.
```javascript
function fetchData() {
    return new Promise(function(resolve, reject) {
        setTimeout(function() {
            resolve("Data fetched");
        }, 1000);
    });
}

fetchData().then(function(data) {
    console.log(data);
});
```
### Async/Await:
Async/await is a syntactic sugar for working with promises, making asynchronous code look synchronous.

```javascript
async function fetchData() {
    return new Promise(function(resolve, reject) {
        setTimeout(function() {
            resolve("Data fetched");
        }, 1000);
    });
}

async function getData() {
    var data = await fetchData();
    console.log(data);
}

getData();
```
#### Practice Questions:
- Write a function that simulates fetching data from an API using callbacks.
- Convert a callback-based function into a Promise-based one.
- Rewrite a Promise-based function using async/await syntax.

## 7. DOM Manipulation
### Selecting DOM Elements:
JavaScript can be used to select and manipulate HTML elements in the Document Object Model (DOM). You can select elements by their id, class, tag name, or using more complex selectors.

```html
<!-- HTML -->
<div id="myDiv" class="container">
    <p>Hello, World!</p>
</div>
```
```javascript
// JavaScript
var elementById = document.getElementById("myDiv");
var elementsByClass = document.getElementsByClassName("container");
var elementsByTagName = document.getElementsByTagName("p");
```
### Modifying DOM Elements:
JavaScript can modify the content, style, and attributes of DOM elements dynamically.
```javascript
// Change text content
elementById.textContent = "Goodbye, World!";

// Change CSS style
elementById.style.color = "red";

// Add/remove CSS classes
elementById.classList.add("highlight");
elementById.classList.remove("container");

// Manipulate attributes
elementById.setAttribute("data-id", "123");
```
### Handling Events:
JavaScript can handle various events triggered by user actions (e.g., click, mouseover, keypress) and execute corresponding functions.
```javascript
// Event listener
elementById.addEventListener("click", function() {
    alert("Element clicked!");
});
```
#### Practice Questions:
- Use JavaScript to change the background color of a webpage when a button is clicked.
- Write a program to validate a form using JavaScript and display appropriate error messages.
- Implement a simple todo list application using DOM manipulation.

## 8. Advanced Topics
### ES6 Features:
ES6 (ECMAScript 2015) introduced several new features to JavaScript, including arrow functions, template literals, destructuring, and more.

```javascript
// Arrow functions
var add = (a, b) => a + b;

// Template literals
var name = "John";
console.log(`Hello, ${name}!`);

// Destructuring
var [x, y] = [1, 2];
```
### Modules:
ES6 introduced native support for modules in JavaScript, allowing you to organize code into separate files and import/export functionality.
```javascript
// math.js
export function add(a, b) {
    return a + b;
}

// main.js
import { add } from "./math.js";
```
### Error Handling:
JavaScript provides mechanisms for handling errors, such as try...catch blocks, to gracefully handle exceptions.

```javascript
try {
    // Code that may throw an error
    throw new Error("An error occurred");
} catch (error) {
    // Handle the error
    console.log(error.message);
}
```
#### Practice Questions:
- Rewrite a given function using arrow function syntax.
- Explain the benefits of using ES6 modules over traditional script tags.
- Implement error handling in a function that divides two numbers.
