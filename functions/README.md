# JavaScript Functions and Scope Reference

## Functions

**Definition:** A reusable block of code that performs a specific task and can be called multiple times.

**Syntax:** `function functionName() { // code }`

**Example:**
```javascript
function greet() {
    console.log("Hello World!");
}
```

## Function Declaration

**Definition:** A way to define a function using the `function` keyword that is hoisted and can be called before its definition.

**Syntax:** `function functionName(parameters) { return value; }`

**Example:**
```javascript
function add(a, b) {
    return a + b;
}
```

## Function Calling

**Definition:** The process of executing a function by using its name followed by parentheses.

**Syntax:** `functionName(arguments)`

**Example:**
```javascript
greet(); // Calls the greet function
let result = add(5, 3); // Calls add function with arguments
```

## Parameters

**Definition:** Variables listed in the function definition that act as placeholders for values that will be passed to the function.

**Syntax:** `function functionName(parameter1, parameter2) { }`

**Example:**
```javascript
function multiply(x, y) { // x and y are parameters
    return x * y;
}
```

## Arguments

**Definition:** The actual values passed to a function when it is called.

**Syntax:** `functionName(argument1, argument2)`

**Example:**
```javascript
multiply(4, 7); // 4 and 7 are arguments passed to the function
```

## Return in Function

**Definition:** A statement that ends function execution and specifies the value to be returned to the function caller.

**Syntax:** `return value;` or `return;`

**Example:**
```javascript
function square(num) {
    return num * num; // Returns the square of num
}
let result = square(5); // result = 25
```

## Anonymous Function

**Definition:** A function without a name, often used as a value or passed as an argument to other functions.

**Syntax:** `function() { // code }`

**Example:**
```javascript
let sayHello = function() {
    console.log("Hello from anonymous function!");
};
sayHello();
```

## Function Expression

**Definition:** A way to define a function as part of an expression, where the function is assigned to a variable.

**Syntax:** `let variableName = function(parameters) { // code };`

**Example:**
```javascript
let divide = function(a, b) {
    return a / b;
};
console.log(divide(10, 2)); // Output: 5
```

## Callback Function - Detailed Understanding

**Definition:** A function that is passed as an argument to another function and is executed after (or during) the execution of that function.

**Why Use Callbacks:**
- Enable asynchronous programming
- Allow customizable behavior
- Support event handling
- Enable functional programming patterns

**How They Work:**
1. A function accepts another function as a parameter
2. The receiving function calls the callback at the appropriate time
3. The callback executes with provided arguments

**Common Use Cases:**
- Event handlers (click, load, etc.)
- Array methods (map, filter, forEach)
- Asynchronous operations (setTimeout, API calls)
- Custom functions that need flexible behavior

**Syntax:** `function mainFunction(callback) { callback(); }`

**Examples:**

**Basic Callback:**
```javascript
function processUser(name, callback) {
    console.log("Processing user: " + name);
    callback(name);
}

function welcomeUser(name) {
    console.log("Welcome, " + name + "!");
}

processUser("John", welcomeUser);
```

**Array Method Callback:**
```javascript
let numbers = [1, 2, 3, 4];
let doubled = numbers.map(function(num) {
    return num * 2;
}); // [2, 4, 6, 8]
```

**Asynchronous Callback:**
```javascript
setTimeout(function() {
    console.log("This runs after 2 seconds");
}, 2000);
```

## Scopes in JavaScript

**Definition:** The accessibility and visibility of variables and functions in different parts of the code.

**Types:** Global Scope, Local Scope (Function Scope, Block Scope)

**Example:**
```javascript
let globalVar = "I'm global"; // Global scope

function myFunction() {
    let localVar = "I'm local"; // Local scope
    console.log(globalVar); // Can access global
    console.log(localVar);  // Can access local
}
```

## Global Scope

**Definition:** Variables declared outside any function or block that are accessible from anywhere in the program.

**Syntax:** Variables declared without `let`, `const`, `var` or declared outside functions become global.

**Example:**
```javascript
var globalName = "Alice"; // Global scope
let globalAge = 25;       // Global scope

function showInfo() {
    console.log(globalName); // Accessible here
    console.log(globalAge);  // Accessible here
}

showInfo(); // Works fine
console.log(globalName); // Accessible here too
```

## Local Scope

**Definition:** Variables declared inside a function or block that are only accessible within that specific function or block.

**Syntax:** Variables declared with `let`, `const`, or `var` inside functions or blocks.

**Example:**
```javascript
function calculateArea() {
    let length = 10;    // Local to this function
    let width = 5;      // Local to this function
    let area = length * width;
    
    if (area > 40) {
        let message = "Large area"; // Block scope (local to if block)
        console.log(message);
    }
    
    console.log(area);     // Accessible here
    // console.log(message); // Error: not accessible here
}

// console.log(length); // Error: not accessible outside function
```

## Methods in JavaScript Objects

**Definition:** Functions that are properties of objects and can access and manipulate the object's data.

**Syntax:** `objectName.methodName()` or defined as `methodName: function() { }`

**Example:**
```javascript
let person = {
    name: "Bob",
    age: 30,
    
    // Method definition
    introduce: function() {
        return "Hi, I'm " + this.name + " and I'm " + this.age + " years old.";
    },
    
    // ES6 method shorthand
    celebrate() {
        this.age++;
        console.log("Happy birthday! Now I'm " + this.age);
    },
    
    // Arrow function method (note: 'this' behaves differently)
    getInfo: () => {
        return "Person object info";
    }
};

// Calling methods
console.log(person.introduce()); // "Hi, I'm Bob and I'm 30 years old."
person.celebrate(); // "Happy birthday! Now I'm 31"
console.log(person.getInfo()); // "Person object info"
```
