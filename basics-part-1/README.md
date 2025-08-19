# JavaScript Comprehensive Guide

JavaScript is a **high-level, interpreted programming language** that is one of the core technologies of the World Wide Web. It enables interactive web pages and is an essential part of web applications.

## Table of Contents
- [1. What is JavaScript?](#1-what-is-javascript)
- [2. File Extension & Setup](#2-file-extension--setup)
- [3. Using the `<script>` Tag](#3-using-the-script-tag)
- [4. Console Methods](#4-console-methods)
- [5. Comments](#5-comments)
- [6. Variables](#6-variables)
- [7. Variable Naming Conventions](#7-variable-naming-conventions)
- [8. Primitive Data Types](#8-primitive-data-types)
- [9. String Operations](#9-string-operations)
- [10. typeof Operator](#10-typeof-operator)
- [11. Operators](#11-operators)
- [12. Boolean, NaN, and Undefined](#12-boolean-nan-and-undefined)
- [13. Falsy and Truthy Values](#13-falsy-and-truthy-values)
- [14. Comparison Operators](#14-comparison-operators)
- [15. Type Conversion](#15-type-conversion)

---

## 1. What is JavaScript?

### Definition
JavaScript is a **dynamic, weakly typed, prototype-based** programming language that runs in web browsers and server environments (Node.js). It was created by Brendan Eich in 1995.

### Key Features
- **Client-side scripting** - Runs in web browsers
- **Server-side development** - Node.js environment
- **Dynamic typing** - Variables can hold different data types
- **Event-driven** - Responds to user interactions
- **Object-oriented** - Supports objects and classes
- **Functional programming** - Functions are first-class citizens

---

## 2. File Extension & Setup

### File Extension
JavaScript files use the `.js` extension:
```
script.js
main.js
app.js
index.js
```

### Basic HTML Setup
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Example</title>
</head>
<body>
    <h1>My JavaScript App</h1>
    
    <!-- JavaScript can be included here -->
    <script src="script.js"></script>
</body>
</html>
```

---

## 3. Using the `<script>` Tag

### Definition
The `<script>` tag is used to embed or reference JavaScript code in HTML documents.

### Inline JavaScript
```html
<script>
    console.log("Hello, World!");
    alert("Welcome to JavaScript!");
</script>
```

### External JavaScript File
```html
<script src="path/to/your/script.js"></script>
```

### Script Tag Placement Options

#### 1. In the `<head>` section
```html
<head>
    <script src="script.js"></script>
</head>
```

#### 2. Before closing `</body>` tag (Recommended)
```html
<body>
    <!-- HTML content -->
    <script src="script.js"></script>
</body>
```

#### 3. With `defer` attribute
```html
<head>
    <script src="script.js" defer></script>
</head>
```

#### 4. With `async` attribute
```html
<head>
    <script src="script.js" async></script>
</head>
```

---

## 4. Console Methods

### Definition
Console methods are used for debugging and displaying information in the browser's developer console.

### console.log()
**Definition**: Outputs general information to the console
```javascript
console.log("Hello, World!");
console.log("My age is", 25);
console.log("User:", {name: "John", age: 30});

// Multiple values
console.log("Name:", "Alice", "Age:", 28);
```

### console.warn()
**Definition**: Displays warning messages with a yellow warning icon
```javascript
console.warn("This is a warning message!");
console.warn("User not found in database");
console.warn("Deprecated function used");
```

### console.error()
**Definition**: Displays error messages with a red error icon
```javascript
console.error("This is an error message!");
console.error("Failed to load user data");
console.error("Network connection failed");
```

### console.table()
**Definition**: Displays data in a table format (great for arrays and objects)
```javascript
// Array of objects
const users = [
    {name: "Alice", age: 25, city: "New York"},
    {name: "Bob", age: 30, city: "London"},
    {name: "Charlie", age: 35, city: "Paris"}
];
console.table(users);

// Simple array
const fruits = ["apple", "banana", "orange"];
console.table(fruits);

// Object
const person = {name: "John", age: 28, occupation: "Developer"};
console.table(person);
```

### console.clear()
**Definition**: Clears the console output
```javascript
console.log("This will be cleared");
console.warn("This warning will also be cleared");
console.clear(); // Clears all previous console output
console.log("Fresh start!");
```

### Other Useful Console Methods
```javascript
// Grouping console messages
console.group("User Information");
console.log("Name: John");
console.log("Age: 30");
console.groupEnd();

// Timing operations
console.time("Operation Timer");
// ... some code execution
console.timeEnd("Operation Timer"); // Shows elapsed time

// Counting occurrences
console.count("Button clicked"); // Button clicked: 1
console.count("Button clicked"); // Button clicked: 2
```

---

## 5. Comments

### Definition
Comments are notes in code that are ignored by the JavaScript engine. They're used to explain code and make it more readable.

### Single-line Comments
```javascript
// This is a single-line comment
let name = "John"; // Comment at the end of a line

// You can use multiple single-line comments
// to create a block of explanatory text
// like this example here
```

### Multi-line Comments
```javascript
/*
This is a multi-line comment
It can span multiple lines
Very useful for longer explanations
*/

let age = 25;

/*
Function to calculate the area of a rectangle
Parameters: length and width
Returns: area as a number
*/
function calculateArea(length, width) {
    return length * width;
}
```

### Best Practices for Comments
```javascript
// Good: Explains WHY, not WHAT
// Calculate tax based on current tax rate for this fiscal year
let tax = income * 0.25;

// Bad: Explains obvious code
// Assign 25 to age variable
let age = 25;

// Good: Explains complex logic
// Check if user has premium access and hasn't exceeded daily limit
if (user.isPremium && user.dailyRequests < 1000) {
    processRequest();
}
```

---

## 6. Variables

### Definition
Variables are **containers that store data values**. They act as named storage locations in memory.

### Declaration vs Initialization
```javascript
// Declaration (creating the variable)
let name;
console.log(name); // undefined

// Initialization (assigning a value)
name = "John";
console.log(name); // "John"

// Declaration and initialization together
let age = 25;
let city = "New York";
```

### var (Legacy - Function Scoped)
```javascript
var firstName = "Alice";
var lastName = "Johnson";
var isEmployed = true;

// Function-scoped
function example() {
    var x = 10;
    console.log(x); // 10
}
// console.log(x); // Error: x is not defined

// Hoisting behavior
console.log(hoistedVar); // undefined (not an error)
var hoistedVar = "I'm hoisted!";

// Can be redeclared
var message = "Hello";
var message = "Hi"; // No error
```

### let (Modern - Block Scoped)
```javascript
let firstName = "Bob";
let lastName = "Smith";
let score = 95;

// Block-scoped
if (true) {
    let blockVariable = "I'm in a block";
    console.log(blockVariable); // Works
}
// console.log(blockVariable); // Error: blockVariable is not defined

// Temporal dead zone
// console.log(letVar); // Error: Cannot access before initialization
let letVar = "I'm a let variable";

// Cannot be redeclared in same scope
let count = 1;
// let count = 2; // Error: Identifier 'count' has already been declared
```

### const (Constants - Block Scoped)
```javascript
const PI = 3.14159;
const APP_NAME = "My JavaScript App";
const MAX_USERS = 1000;

// Must be initialized when declared
// const uninitialized; // Error: Missing initializer

// Cannot be reassigned
// PI = 3.14; // Error: Assignment to constant variable

// Objects and arrays can be modified (contents, not reference)
const colors = ["red", "green", "blue"];
colors.push("yellow"); // This works - modifying contents
console.log(colors); // ["red", "green", "blue", "yellow"]

const person = {name: "John", age: 30};
person.age = 31; // This works - modifying property
person.city = "New York"; // This works - adding property
// person = {}; // Error: Assignment to constant variable
```

---

## 7. Variable Naming Conventions

### Definition
Naming conventions are standardized ways of naming variables to make code more readable and maintainable.

### camelCase (Recommended for JavaScript)
```javascript
// camelCase: first letter lowercase, capitalize first letter of each subsequent word
let firstName = "John";
let lastName = "Doe";
let userAccountBalance = 1500.75;
let isUserLoggedIn = true;
let maxRetryAttempts = 3;
let calculateTotalPrice = function() { /* ... */ };
```

### Valid Variable Names
```javascript
// Starting with letters
let name = "Alice";
let userName = "alice123";
let user_name = "alice123"; // snake_case (less common in JS)

// Starting with underscore (often used for private variables)
let _private = "internal use";
let _userId = 12345;

// Starting with dollar sign (often used by libraries)
let $element = document.getElementById("myDiv");
let $price = 99.99;

// Numbers can be used (but not at the beginning)
let user1 = "First user";
let item2Count = 5;
let version2024 = "latest";
```

### Invalid Variable Names
```javascript
// Cannot start with numbers
// let 2users = "Invalid";
// let 1stPlace = "Invalid";

// Cannot use hyphens or spaces
// let user-name = "Invalid";
// let first name = "Invalid";

// Cannot use reserved keywords
// let let = "Invalid";
// let function = "Invalid";
// let class = "Invalid";
// let return = "Invalid";
```

### Naming Best Practices
```javascript
// Use descriptive names
// Good
let userAccountBalance = 1500;
let isEmailValid = true;
let maxLoginAttempts = 3;

// Bad
let x = 1500;
let flag = true;
let num = 3;

// Use consistent naming
let firstName = "John";
let lastName = "Doe";
let fullName = firstName + " " + lastName;

// Constants in UPPER_CASE
const MAX_RETRY_ATTEMPTS = 5;
const API_BASE_URL = "https://api.example.com";
const DEFAULT_TIMEOUT = 3000;

// Boolean variables with is/has/can prefixes
let isLoggedIn = false;
let hasPermission = true;
let canEdit = false;
let shouldUpdate = true;
```

---

## 8. Primitive Data Types

### Definition
Primitive data types are the basic data types in JavaScript that store simple values directly in memory.

### Numbers
```javascript
// Integers
let age = 25;
let score = 100;
let temperature = -5;

// Floating point numbers
let price = 19.99;
let pi = 3.14159;
let percentage = 0.75;

// Special number values
let infinity = Infinity;
let negativeInfinity = -Infinity;
let notANumber = NaN;

// Number operations
let sum = 10 + 5;        // 15
let difference = 20 - 8;  // 12
let product = 4 * 6;     // 24
let quotient = 15 / 3;   // 5
let remainder = 17 % 5;  // 2
let power = 2 ** 3;      // 8

// Number methods
let decimal = 3.14159;
console.log(decimal.toFixed(2));     // "3.14"
console.log(decimal.toPrecision(3)); // "3.14"
console.log(parseInt("42"));         // 42
console.log(parseFloat("3.14"));     // 3.14
```

### Strings
```javascript
// String creation
let singleQuote = 'Hello World';
let doubleQuote = "Hello World";
let templateLiteral = `Hello World`;

// Strings with quotes inside
let message1 = "She said, 'Hello there!'";
let message2 = 'He replied, "Nice to meet you!"';
let message3 = `Both "single" and 'double' quotes work here`;

// Escape characters
let escaped = "Line 1\nLine 2\tTabbed";
let quote = "She said, \"Hello!\"";
let backslash = "This is a backslash: \\";

// Multi-line strings
let multiLine = `This is line 1
This is line 2
This is line 3`;
```

### Template Strings (Template Literals)
```javascript
// Basic template literals with variables
let name = "Alice";
let age = 28;
let greeting = `Hello, my name is ${name} and I'm ${age} years old.`;
console.log(greeting); // "Hello, my name is Alice and I'm 28 years old."

// Expressions in template literals
let price = 19.99;
let quantity = 3;
let total = `Total cost: $${(price * quantity).toFixed(2)}`;
console.log(total); // "Total cost: $59.97"

// Multi-line template literals
let htmlTemplate = `
    <div class="user-card">
        <h2>${name}</h2>
        <p>Age: ${age}</p>
        <p>Status: Active</p>
    </div>
`;

// Function calls in template literals
let upperName = `Welcome, ${name.toUpperCase()}!`;
console.log(upperName); // "Welcome, ALICE!"
```

---

## 9. String Operations

### String Concatenation
```javascript
let firstName = "John";
let lastName = "Doe";

// Using + operator
let fullName1 = firstName + " " + lastName;
console.log(fullName1); // "John Doe"

// Using += operator (append)
let message = "Hello";
message += " World";
message += "!";
console.log(message); // "Hello World!"

// Multiple concatenations
let greeting = "Hi" + " " + firstName + ", " + "welcome!";
console.log(greeting); // "Hi John, welcome!"
```

### concat() Method
```javascript
let str1 = "Hello";
let str2 = " ";
let str3 = "World";
let str4 = "!";

// Using concat method
let result1 = str1.concat(str2, str3, str4);
console.log(result1); // "Hello World!"

// Chaining concat
let result2 = "Hello".concat(" ", "beautiful").concat(" ", "world");
console.log(result2); // "Hello beautiful world"

// concat with variables
let greeting = "Welcome".concat(" ", firstName, " ", lastName);
console.log(greeting); // "Welcome John Doe"
```

### String Properties and Methods

#### .length Property
```javascript
let text = "JavaScript";
console.log(text.length); // 10

let empty = "";
console.log(empty.length); // 0

let spaces = "   ";
console.log(spaces.length); // 3

// Using length in conditions
if (password.length < 8) {
    console.log("Password too short!");
}
```

#### toLowerCase() and toUpperCase()
```javascript
let mixedCase = "Hello World";

// Convert to lowercase
let lower = mixedCase.toLowerCase();
console.log(lower); // "hello world"

// Convert to uppercase
let upper = mixedCase.toUpperCase();
console.log(upper); // "HELLO WORLD"

// Original string unchanged
console.log(mixedCase); // "Hello World"

// Practical use case - case-insensitive comparison
let input = "JAVASCRIPT";
if (input.toLowerCase() === "javascript") {
    console.log("Match found!");
}
```

#### String slice()
```javascript
let text = "Hello World";

// slice(start, end) - end is exclusive
console.log(text.slice(0, 5));   // "Hello"
console.log(text.slice(6, 11));  // "World"
console.log(text.slice(6));      // "World" (from index 6 to end)

// Negative indices (count from end)
console.log(text.slice(-5));     // "World" (last 5 characters)
console.log(text.slice(-5, -1)); // "Worl" (from 5th last to 2nd last)
console.log(text.slice(0, -6));  // "Hello" (from start to 6th last)

// Extract file extension
let filename = "document.pdf";
let extension = filename.slice(filename.lastIndexOf('.') + 1);
console.log(extension); // "pdf"
```

#### split() Method
```javascript
let sentence = "The quick brown fox";

// Split by space
let words = sentence.split(" ");
console.log(words); // ["The", "quick", "brown", "fox"]

// Split by character
let letters = "hello".split("");
console.log(letters); // ["h", "e", "l", "l", "o"]

// Split with limit
let limitedSplit = sentence.split(" ", 2);
console.log(limitedSplit); // ["The", "quick"]

// Split CSV data
let csvData = "John,25,Developer,New York";
let userInfo = csvData.split(",");
console.log(userInfo); // ["John", "25", "Developer", "New York"]

// Split by multiple characters
let path = "home/user/documents/file.txt";
let pathParts = path.split("/");
console.log(pathParts); // ["home", "user", "documents", "file.txt"]
```

#### includes() Method
```javascript
let text = "JavaScript is awesome";

// Check if string contains substring
console.log(text.includes("Script"));     // true
console.log(text.includes("script"));     // false (case-sensitive)
console.log(text.includes("Java"));       // true
console.log(text.includes("Python"));     // false

// Case-insensitive check
let searchTerm = "JAVASCRIPT";
console.log(text.toLowerCase().includes(searchTerm.toLowerCase())); // true

// Check from specific position
console.log(text.includes("is", 10)); // true (starts searching from index 10)
console.log(text.includes("is", 15)); // false

// Practical use cases
let email = "user@example.com";
if (email.includes("@")) {
    console.log("Valid email format");
}

let allowedDomains = ["gmail.com", "yahoo.com", "hotmail.com"];
let userDomain = email.split("@")[1];
if (allowedDomains.includes(userDomain)) {
    console.log("Domain is allowed");
}
```

#### trim() Method
```javascript
let messyString = "   Hello World   ";

// Remove whitespace from both ends
let cleaned = messyString.trim();
console.log(cleaned); // "Hello World"
console.log(cleaned.length); // 11

// Original string unchanged
console.log(messyString); // "   Hello World   "
console.log(messyString.length); // 17

// trimStart() and trimEnd()
let leadingSpace = "   Hello";
let trailingSpace = "World   ";

console.log(leadingSpace.trimStart());  // "Hello"
console.log(trailingSpace.trimEnd());   // "World"

// Practical use - form input validation
let userInput = "  john.doe@email.com  ";
let cleanEmail = userInput.trim();
console.log(cleanEmail); // "john.doe@email.com"

// Clean array of strings
let names = ["  Alice  ", "  Bob  ", "  Charlie  "];
let cleanNames = names.map(name => name.trim());
console.log(cleanNames); // ["Alice", "Bob", "Charlie"]
```

---

## 10. typeof Operator

### Definition
The `typeof` operator returns a string indicating the type of the operand.

### Basic Usage
```javascript
// Primitive types
console.log(typeof "Hello");          // "string"
console.log(typeof 42);               // "number"
console.log(typeof 3.14);             // "number"
console.log(typeof true);             // "boolean"
console.log(typeof false);            // "boolean"
console.log(typeof undefined);        // "undefined"
console.log(typeof Symbol("id"));     // "symbol"
console.log(typeof 123n);             // "bigint"

// Special cases
console.log(typeof null);             // "object" (this is a known bug in JavaScript)
console.log(typeof NaN);              // "number"
console.log(typeof Infinity);         // "number"

// Objects and functions
console.log(typeof {});               // "object"
console.log(typeof []);               // "object"
console.log(typeof new Date());       // "object"
console.log(typeof function() {});    // "function"
console.log(typeof Math);             // "object"
```

### Practical Examples
```javascript
// Type checking before operations
let value = "123";
if (typeof value === "string") {
    console.log("Converting string to number:", Number(value));
}

// Function parameter validation
function greet(name) {
    if (typeof name !== "string") {
        throw new Error("Name must be a string");
    }
    return `Hello, ${name}!`;
}

// Dynamic type handling
function processValue(value) {
    switch (typeof value) {
        case "string":
            return value.toUpperCase();
        case "number":
            return value * 2;
        case "boolean":
            return !value;
        default:
            return "Unknown type";
    }
}

console.log(processValue("hello"));  // "HELLO"
console.log(processValue(5));        // 10
console.log(processValue(true));     // false
```

### typeof with Variables
```javascript
let undeclaredVariable;
console.log(typeof undeclaredVariable); // "undefined"

let nullVariable = null;
console.log(typeof nullVariable); // "object"

let arrayVariable = [1, 2, 3];
console.log(typeof arrayVariable); // "object"

// Better array checking
console.log(Array.isArray(arrayVariable)); // true

// Check if variable is defined
if (typeof someVariable !== "undefined") {
    // Safe to use someVariable
    console.log(someVariable);
}
```

---

## 11. Operators

### Arithmetic Operators
```javascript
let a = 10;
let b = 3;

console.log(a + b);  // 13 (Addition)
console.log(a - b);  // 7  (Subtraction)
console.log(a * b);  // 30 (Multiplication)
console.log(a / b);  // 3.333... (Division)
console.log(a % b);  // 1  (Modulus/Remainder)
console.log(a ** b); // 1000 (Exponentiation - ES6+)

// Order of operations (PEMDAS)
let result = 2 + 3 * 4;      // 14 (not 20)
let grouped = (2 + 3) * 4;   // 20
```

### Increment and Decrement Operators
```javascript
let count = 5;

// Pre-increment (++variable)
console.log(++count); // 6 (increment first, then return value)
console.log(count);   // 6

// Post-increment (variable++)
count = 5;
console.log(count++); // 5 (return value first, then increment)
console.log(count);   // 6

// Pre-decrement (--variable)
count = 5;
console.log(--count); // 4 (decrement first, then return value)
console.log(count);   // 4

// Post-decrement (variable--)
count = 5;
console.log(count--); // 5 (return value first, then decrement)
console.log(count);   // 4

// Practical example
let attempts = 3;
while (attempts-- > 0) {
    console.log(`Attempts remaining: ${attempts + 1}`);
}
```

### Assignment Operators
```javascript
let x = 10;

// Basic assignment
x = 15;   // x is now 15

// Compound assignment operators
x += 5;   // x = x + 5  → x is now 20
x -= 3;   // x = x - 3  → x is now 17
x *= 2;   // x = x * 2  → x is now 34
x /= 2;   // x = x / 2  → x is now 17
x %= 5;   // x = x % 5  → x is now 2
x **= 3;  // x = x ** 3 → x is now 8

// String concatenation assignment
let message = "Hello";
message += " World";  // message is now "Hello World"
message += "!";       // message is now "Hello World!"
```

---

## 12. Boolean, NaN, and Undefined

### Boolean Data Type
```javascript
// Boolean literals
let isTrue = true;
let isFalse = false;

// Boolean from expressions
let isGreater = 10 > 5;        // true
let isEqual = "hello" === "hi"; // false
let isLoggedIn = user !== null; // depends on user value

// Boolean constructor (not recommended for literals)
let boolFromConstructor = Boolean(1);    // true
let anotherBool = Boolean(0);            // false

// Practical boolean usage
let hasPermission = true;
let isAdult = age >= 18;
let canProceed = hasPermission && isAdult;

if (canProceed) {
    console.log("User can proceed");
}
```

### NaN (Not a Number)
```javascript
// What creates NaN
let result1 = 0 / 0;              // NaN
let result2 = parseInt("hello");   // NaN
let result3 = Math.sqrt(-1);      // NaN
let result4 = "text" * 5;         // NaN

console.log(typeof NaN); // "number" (surprisingly!)

// Checking for NaN
console.log(isNaN(NaN));        // true
console.log(isNaN("hello"));    // true (converts to NaN first)
console.log(Number.isNaN(NaN)); // true (more reliable)
console.log(Number.isNaN("hello")); // false (doesn't convert)

// NaN comparisons
console.log(NaN === NaN);       // false (NaN is not equal to itself!)
console.log(NaN == NaN);        // false

// Practical NaN handling
function safeParseInt(value) {
    let result = parseInt(value);
    if (Number.isNaN(result)) {
        return 0; // or throw error, or return null
    }
    return result;
}

console.log(safeParseInt("123"));   // 123
console.log(safeParseInt("abc"));   // 0
```

### Undefined
```javascript
// What creates undefined
let declaredButNotInitialized;  // undefined
console.log(declaredButNotInitialized);

// Function without return statement
function noReturn() {
    console.log("This function returns undefined");
}
console.log(noReturn()); // undefined

// Accessing non-existent object property
let person = {name: "John"};
console.log(person.age); // undefined

// Array element that doesn't exist
let numbers = [1, 2, 3];
console.log(numbers[10]); // undefined

// Function parameter not provided
function greet(name) {
    console.log(name); // undefined if not provided
}
greet(); // undefined

// Checking for undefined
let value;
console.log(value === undefined);        // true
console.log(typeof value === "undefined"); // true
```

### Difference between NaN and Undefined

#### Type Difference
```javascript
console.log(typeof NaN);       // "number"
console.log(typeof undefined); // "undefined"
```

#### Origin Difference
```javascript
// NaN comes from invalid number operations
let nan1 = 0 / 0;
let nan2 = parseInt("hello");
let nan3 = Math.sqrt(-1);

// undefined comes from uninitialized or missing values
let undef1;                    // declared but not initialized
let undef2 = {}.nonExistent;   // accessing non-existent property
let undef3 = function() {}();  // function with no return
```

#### Comparison Behavior
```javascript
// NaN is never equal to anything, including itself
console.log(NaN === NaN);       // false
console.log(NaN == NaN);        // false

// undefined is equal to itself
console.log(undefined === undefined); // true
console.log(undefined == undefined);  // true

// undefined vs null
console.log(undefined == null);  // true (loose equality)
console.log(undefined === null); // false (strict equality)
```

#### Practical Usage
```javascript
// Checking for NaN
function isValidNumber(value) {
    return typeof value === "number" && !Number.isNaN(value);
}

// Checking for undefined
function hasValue(value) {
    return typeof value !== "undefined" && value !== null;
}

// Default values for undefined
function greet(name = "Guest") {
    // If name is undefined, use "Guest"
    return `Hello, ${name}!`;
}

// Handle both cases
function processValue(value) {
    if (typeof value === "undefined") {
        return "No value provided";
    }
    if (Number.isNaN(value)) {
        return "Invalid number";
    }
    return value;
}
```

---

## 13. Falsy and Truthy Values

### Definition
In JavaScript, values are either **truthy** (evaluate to `true` in boolean context) or **falsy** (evaluate to `false` in boolean context).

### Falsy Values (Only 8 values)
```javascript
// All falsy values in JavaScript
console.log(Boolean(false));      // false
console.log(Boolean(0));          // false
console.log(Boolean(-0));         // false
console.log(Boolean(0n));         // false (BigInt zero)
console.log(Boolean(""));         // false (empty string)
console.log(Boolean(null));       // false
console.log(Boolean(undefined));  // false
console.log(Boolean(NaN));        // false

// Testing falsy values in conditions
if (!false) console.log("false is falsy");
if (!0) console.log("0 is falsy");
if (!"") console.log("empty string is falsy");
if (!null) console.log("null is falsy");
if (!undefined) console.log("undefined is falsy");
if (!NaN) console.log("NaN is falsy");
```

### Truthy Values (Everything else)
```javascript
// All non-falsy values are truthy
console.log(Boolean(true));           // true
console.log(Boolean(1));              // true
console.log(Boolean(-1));             // true
console.log(Boolean(3.14));           // true
console.log(Boolean("hello"));        // true
console.log(Boolean("0"));            // true (string "0", not number 0)
console.log(Boolean("false"));        // true (string "false", not boolean false)
console.log(Boolean([]));             // true (empty array)
console.log(Boolean({}));             // true (empty object)
console.log(Boolean(function(){}));   // true (function)
console.log(Boolean(new Date()));     // true (Date object)
console.log(Boolean(Infinity));       // true
console.log(Boolean(-Infinity));      // true

// Surprising truthy values
console.log(Boolean("   "));          // true (string with spaces)
console.log(Boolean([0]));            // true (array with falsy element)
console.log(Boolean([false]));        // true (array with falsy element)
```

### Difference Between Falsy and Truthy Values

#### In Conditional Statements
```javascript
// Falsy values in if statements
let falsyValues = [false, 0, "", null, undefined, NaN];

falsyValues.forEach(value => {
    if (value) {
        console.log(`${value} is truthy`); // This won't execute
    } else {
        console.log(`${value} is falsy`);  // This will execute
    }
});

// Truthy values in if statements
let truthyValues = [true, 1, "hello", [], {}, function(){}];

truthyValues.forEach(value => {
    if (value) {
        console.log(`${value} is truthy`); // This will execute
    } else {
        console.log(`${value} is falsy`);  // This won't execute
    }
});
```

#### Logical Operations
```javascript
// OR operator with falsy/truthy values
let name = "" || "Default Name";        // "Default Name" (empty string is falsy)
let age = 0 || 25;                      // 25 (0 is falsy)
let user = null || {name: "Guest"};     // {name: "Guest"} (null is falsy)

// AND operator with falsy/truthy values
let isLoggedIn = true && "User is logged in";  // "User is logged in"
let hasAccess = false && "Access granted";     // false (short-circuit)
let result = 5 && 10;                          // 10 (both truthy, returns last)

// Nullish coalescing operator (??) - only null/undefined are falsy
let score = 0 ?? 100;           // 0 (0 is not null/undefined)
let points = null ?? 50;        // 50 (null triggers default)
let level = undefined ?? 1;     // 1 (undefined triggers default)
```

#### Practical Examples
```javascript
// Form validation
function validateForm(data) {
    if (!data.name) {
        return "Name is required";
    }
    if (!data.email) {
        return "Email is required";
    }
    if (!data.age || data.age <= 0) {
        return "Valid age is required";
    }
    return "Form is valid";
}

// Default values
function createUser(name, email, role) {
    return {
        name: name || "Anonymous",
        email: email || "no-email@example.com",
        role: role || "user",
        isActive: true
    };
}

// Array filtering
let mixed = [0, 1, "", "hello", null, "world", undefined, 42];
let truthyOnly = mixed.filter(Boolean); // [1, "hello", "world", 42]
let falsyOnly = mixed.filter(x => !x);  // [0, "", null, undefined]

console.log(truthyOnly);
console.log(falsyOnly);

// Safe property access
let user = null;
if (user && user.profile && user.profile.name) {
    console.log(user.profile.name);
} else {
    console.log("User name not available");
}

// Modern optional chaining (ES2020)
console.log(user?.profile?.name || "Name not found");
```

#### Common Gotchas
```javascript
// These might be surprising
console.log(Boolean("0"));        // true (string, not number)
console.log(Boolean("false"));    // true (string, not boolean)
console.log(Boolean([]));         // true (empty array is truthy)
console.log(Boolean({}));         // true (empty object is truthy)

// Array length check
let emptyArray = [];
if (emptyArray) {
    console.log("This runs!"); // Array itself is truthy
}
if (emptyArray.length) {
    console.log("This doesn't run"); // Length is 0 (falsy)
}

// Better array checking
if (emptyArray.length > 0) {
    console.log("Array has elements");
} else {
    console.log("Array is empty");
}

// Object property checking
let emptyObj = {};
if (emptyObj) {
    console.log("Object exists"); // This runs
}
if (Object.keys(emptyObj).length > 0) {
    console.log("Object has properties"); // This doesn't run
}
```

---

## 14. Comparison Operators

### Relational Operators
```javascript
let a = 10;
let b = 5;
let c = "10";

// Greater than
console.log(a > b);   // true
console.log(b > a);   // false
console.log(a > c);   // false (10 > "10" → 10 > 10 → false)

// Less than
console.log(a < b);   // false
console.log(b < a);   // true
console.log(a < 20);  // true

// Greater than or equal
console.log(a >= b);  // true
console.log(a >= 10); // true
console.log(b >= 10); // false

// Less than or equal
console.log(a <= b);  // false
console.log(a <= 10); // true
console.log(b <= 5);  // true

// String comparisons (lexicographical order)
console.log("apple" < "banana");    // true
console.log("Apple" < "banana");    // true (uppercase comes first in ASCII)
console.log("10" < "2");            // true (string comparison, not numeric)
console.log("10" < "9");            // true
```

### Equality Operators

#### Loose Equality (==) - Type Coercion
```javascript
// Loose equality performs type conversion
console.log(5 == "5");        // true (string converted to number)
console.log(true == 1);       // true (boolean converted to number)
console.log(false == 0);      // true (boolean converted to number)
console.log(null == undefined); // true (special case)
console.log("" == 0);         // true (empty string converted to 0)
console.log(" " == 0);        // true (space converted to 0)
console.log([] == "");        // true (array converted to string)
console.log([0] == 0);        // true (array converted to string, then number)

// Some surprising cases
console.log("0" == false);    // true
console.log("" == false);     // true
console.log(" \t\n" == 0);    // true (whitespace converted to 0)
```

#### Strict Equality (===) - No Type Coercion
```javascript
// Strict equality checks type AND value
console.log(5 === "5");        // false (different types)
console.log(true === 1);       // false (different types)
console.log(false === 0);      // false (different types)
console.log(null === undefined); // false (different types)
console.log("" === 0);         // false (different types)

// Same type comparisons
console.log(5 === 5);          // true
console.log("hello" === "hello"); // true
console.log(true === true);    // true
console.log(null === null);    // true
console.log(undefined === undefined); // true

// Object comparisons (reference-based)
let obj1 = {name: "John"};
let obj2 = {name: "John"};
let obj3 = obj1;

console.log(obj1 === obj2);    // false (different objects)
console.log(obj1 === obj3);    // true (same reference)
```

#### Inequality Operators
```javascript
// Loose inequality (!=)
console.log(5 != "5");        // false (converts "5" to 5)
console.log(5 != "6");        // true
console.log(true != 1);       // false (converts true to 1)

// Strict inequality (!==)
console.log(5 !== "5");       // true (different types)
console.log(5 !== 5);         // false (same type and value)
console.log(true !== 1);      // true (different types)
```

### Practical Comparison Examples
```javascript
// User input validation
function validateAge(input) {
    // Convert to number first
    let age = Number(input);
    
    // Check if valid number
    if (Number.isNaN(age)) {
        return "Please enter a valid number";
    }
    
    // Age validation with strict comparison
    if (age < 0) {
        return "Age cannot be negative";
    }
    if (age > 150) {
        return "Please enter a realistic age";
    }
    if (age < 18) {
        return "Must be 18 or older";
    }
    
    return "Valid age";
}

// Array searching
let users = [
    {id: 1, name: "Alice"},
    {id: "2", name: "Bob"},    // String ID
    {id: 3, name: "Charlie"}
];

// Loose equality might give unexpected results
let foundUser1 = users.find(user => user.id == "1");  // Finds Alice
let foundUser2 = users.find(user => user.id === "1"); // Doesn't find Alice

// Better approach - convert types explicitly
function findUserById(users, id) {
    return users.find(user => String(user.id) === String(id));
}

// Null/undefined checking
let userInput = null;

// Check for both null and undefined
if (userInput == null) {  // true for both null and undefined
    console.log("No input provided");
}

// Check specifically for null
if (userInput === null) {
    console.log("Input is specifically null");
}

// Check specifically for undefined
if (userInput === undefined) {
    console.log("Input is specifically undefined");
}
```

### Best Practices for Comparisons
```javascript
// 1. Use strict equality by default
let score = 85;
if (score === 100) {
    console.log("Perfect score!");
}

// 2. Be explicit with type conversions
let userAge = "25";
if (Number(userAge) >= 18) {
    console.log("Adult user");
}

// 3. Use strict inequality
let status = "active";
if (status !== "inactive") {
    console.log("User is active");
}

// 4. Handle null/undefined explicitly
function processData(data) {
    if (data === null) {
        return "Data is null";
    }
    if (data === undefined) {
        return "Data is undefined";
    }
    return `Processing: ${data}`;
}

// 5. Object comparison helper function
function deepEqual(obj1, obj2) {
    return JSON.stringify(obj1) === JSON.stringify(obj2);
}

let person1 = {name: "John", age: 30};
let person2 = {name: "John", age: 30};
console.log(deepEqual(person1, person2)); // true
```

---

## 15. Type Conversion

### Definition
Type conversion is the process of converting data from one type to another. JavaScript has both automatic (implicit) and manual (explicit) type conversion.

### String to Number Conversion

#### Using Number() Function
```javascript
// String to number conversion
console.log(Number("123"));        // 123
console.log(Number("123.45"));     // 123.45
console.log(Number("123abc"));     // NaN (invalid number)
console.log(Number(""));           // 0 (empty string)
console.log(Number("   "));        // 0 (whitespace)
console.log(Number("true"));       // NaN
console.log(Number("false"));      // NaN

// Boolean to number
console.log(Number(true));         // 1
console.log(Number(false));        // 0

// null and undefined
console.log(Number(null));         // 0
console.log(Number(undefined));    // NaN
```

#### Using parseInt() Function
```javascript
// parseInt for integers
console.log(parseInt("123"));      // 123
console.log(parseInt("123.45"));   // 123 (stops at decimal)
console.log(parseInt("123abc"));   // 123 (stops at first non-digit)
console.log(parseInt("abc123"));   // NaN (starts with non-digit)
console.log(parseInt("   456"));   // 456 (ignores leading whitespace)

// parseInt with radix (base)
console.log(parseInt("1010", 2));  // 10 (binary to decimal)
console.log(parseInt("FF", 16));   // 255 (hexadecimal to decimal)
console.log(parseInt("77", 8));    // 63 (octal to decimal)

// Always specify radix for clarity
console.log(parseInt("010", 10));  // 10 (decimal)
console.log(parseInt("010", 8));   // 8 (octal)
```

#### Using parseFloat() Function
```javascript
// parseFloat for decimal numbers
console.log(parseFloat("123.45"));    // 123.45
console.log(parseFloat("123.45abc")); // 123.45 (stops at first invalid character)
console.log(parseFloat("123"));       // 123
console.log(parseFloat("abc123.45")); // NaN (starts with non-digit)
console.log(parseFloat("3.14159"));   // 3.14159

// Scientific notation
console.log(parseFloat("1.23e-4"));   // 0.000123
console.log(parseFloat("1.23e+2"));   // 123
```

#### Using Unary Plus Operator (+)
```javascript
// Unary plus for quick conversion
console.log(+"123");        // 123
console.log(+"123.45");     // 123.45
console.log(+"123abc");     // NaN
console.log(+"");           // 0
console.log(+true);         // 1
console.log(+false);        // 0
console.log(+null);         // 0
console.log(+undefined);    // NaN

// Practical use
let userInput = "42";
let age = +userInput;  // Quick conversion
console.log(typeof age, age); // "number" 42
```

### String to Decimal (Advanced)
```javascript
// Converting strings with specific decimal places
function parseDecimal(str, decimals = 2) {
    let num = parseFloat(str);
    if (isNaN(num)) return null;
    return Math.round(num * Math.pow(10, decimals)) / Math.pow(10, decimals);
}

console.log(parseDecimal("123.456", 2));    // 123.46
console.log(parseDecimal("123.456", 1));    // 123.5
console.log(parseDecimal("123.999", 0));    // 124

// Currency conversion
function parseCurrency(currencyStr) {
    // Remove currency symbols and spaces
    let cleaned = currencyStr.replace(/[$,\s]/g, '');
    return parseFloat(cleaned);
}

console.log(parseCurrency("$1,234.56"));    // 1234.56
console.log(parseCurrency("$ 999.99"));     // 999.99
```

### Number to String Conversion

#### Using String() Function
```javascript
// Number to string conversion
console.log(String(123));          // "123"
console.log(String(123.45));       // "123.45"
console.log(String(0));            // "0"
console.log(String(-456));         // "-456"
console.log(String(Infinity));     // "Infinity"
console.log(String(NaN));          // "NaN"

// Boolean to string
console.log(String(true));         // "true"
console.log(String(false));        // "false"

// null and undefined to string
console.log(String(null));         // "null"
console.log(String(undefined));    // "undefined"
```

#### Using toString() Method
```javascript
// toString method
let num = 123.45;
console.log(num.toString());       // "123.45"

// toString with radix (base)
let decimal = 255;
console.log(decimal.toString(16)); // "ff" (hexadecimal)
console.log(decimal.toString(8));  // "377" (octal)
console.log(decimal.toString(2));  // "11111111" (binary)

// Fixed decimal places
let price = 19.9;
console.log(price.toFixed(2));     // "19.90"
console.log(price.toFixed(0));     // "20"

// Exponential notation
let bigNum = 123456789;
console.log(bigNum.toExponential(2)); // "1.23e+8"

// Precision (total significant digits)
let precise = 123.456;
console.log(precise.toPrecision(4));  // "123.5"
console.log(precise.toPrecision(2));  // "1.2e+2"
```

#### Using Template Literals
```javascript
// Template literals for string conversion
let age = 25;
let height = 5.8;
let message = `I am ${age} years old and ${height} feet tall.`;
console.log(message); // "I am 25 years old and 5.8 feet tall."

// Expressions in template literals
let price = 29.99;
let quantity = 3;
let total = `Total: ${(price * quantity).toFixed(2)}`;
console.log(total); // "Total: $89.97"
```

### Implicit Type Conversion (Coercion)
```javascript
// JavaScript's automatic type conversion
console.log("5" + 3);         // "53" (number to string, concatenation)
console.log("5" - 3);         // 2 (string to number, subtraction)
console.log("5" * 3);         // 15 (string to number, multiplication)
console.log("5" / 3);         // 1.666... (string to number, division)
console.log("5" % 3);         // 2 (string to number, modulus)

// Boolean in arithmetic
console.log(true + 1);        // 2 (true becomes 1)
console.log(false + 1);       // 1 (false becomes 0)
console.log(true * 5);        // 5
console.log(false * 5);       // 0

// Mixed operations
console.log("3" + 2 + 1);     // "321" (left to right, string concatenation)
console.log(3 + 2 + "1");     // "51" (addition first, then concatenation)
console.log("3" - 2 + 1);     // 2 (subtraction forces number conversion)
```

### Type Conversion Best Practices
```javascript
// 1. Be explicit about conversions
function calculateTotal(priceStr, quantityStr) {
    // Bad: rely on implicit conversion
    // return priceStr * quantityStr;
    
    // Good: explicit conversion with validation
    let price = parseFloat(priceStr);
    let quantity = parseInt(quantityStr, 10);
    
    if (isNaN(price) || isNaN(quantity)) {
        throw new Error("Invalid price or quantity");
    }
    
    return price * quantity;
}

// 2. Input validation function
function validateAndConvert(input, type) {
    switch (type) {
        case 'number':
            let num = Number(input);
            return isNaN(num) ? null : num;
        
        case 'integer':
            let int = parseInt(input, 10);
            return isNaN(int) ? null : int;
        
        case 'float':
            let float = parseFloat(input);
            return isNaN(float) ? null : float;
        
        case 'string':
            return String(input);
        
        default:
            return input;
    }
}

// Usage examples
console.log(validateAndConvert("123", 'number'));    // 123
console.log(validateAndConvert("123.45", 'float'));  // 123.45
console.log(validateAndConvert("abc", 'number'));    // null
console.log(validateAndConvert(456, 'string'));      // "456"

// 3. Safe conversion with defaults
function safeNumberConvert(value, defaultValue = 0) {
    let result = Number(value);
    return isNaN(result) ? defaultValue : result;
}

function safeStringConvert(value, defaultValue = "") {
    return value == null ? defaultValue : String(value);
}

// Examples
console.log(safeNumberConvert("123"));      // 123
console.log(safeNumberConvert("abc"));      // 0
console.log(safeNumberConvert("abc", -1));  // -1

console.log(safeStringConvert(123));        // "123"
console.log(safeStringConvert(null));       // ""
console.log(safeStringConvert(null, "N/A")); // "N/A"
```

### Common Type Conversion Patterns
```javascript
// Form input handling
function handleFormSubmit(formData) {
    return {
        name: String(formData.name || "").trim(),
        age: parseInt(formData.age, 10) || 0,
        salary: parseFloat(formData.salary) || 0,
        isActive: formData.isActive === "true" || formData.isActive === true,
        startDate: new Date(formData.startDate)
    };
}

// API response processing
function processApiResponse(response) {
    return {
        id: Number(response.id),
        title: String(response.title),
        price: parseFloat(response.price).toFixed(2),
        available: Boolean(response.available),
        tags: String(response.tags || "").split(",").map(tag => tag.trim())
    };
}

// URL parameter parsing
function parseUrlParams(urlSearchParams) {
    const params = {};
    for (const [key, value] of urlSearchParams.entries()) {
        // Try to convert to number if it looks like a number
        if (/^\d+$/.test(value)) {
            params[key] = parseInt(value, 10);
        } else if (/^\d+\.\d+$/.test(value)) {
            params[key] = parseFloat(value);
        } else if (value === "true" || value === "false") {
            params[key] = value === "true";
        } else {
            params[key] = value;
        }
    }
    return params;
}

// Example: ?page=2&limit=10&active=true&search=javascript
// Result: {page: 2, limit: 10, active: true, search: "javascript"}
```

---

## Summary

This comprehensive JavaScript guide covers the fundamental concepts you need to understand JavaScript programming:

- **Setup and Syntax**: File extensions, script tags, and basic structure
- **Console Methods**: Debugging and output techniques  
- **Comments**: Code documentation practices
- **Variables**: Declaration, initialization, and scoping with `var`, `let`, and `const`
- **Naming Conventions**: camelCase and best practices
- **Data Types**: Primitives (numbers, strings, booleans) and their operations
- **String Manipulation**: Concatenation, methods, and template literals
- **Type System**: `typeof` operator, NaN, undefined, and their differences
- **Operators**: Arithmetic, increment/decrement, and assignment operators  
- **Boolean Logic**: Falsy/truthy values and their practical applications
- **Comparisons**: Relational, equality (strict vs loose), and best practices
- **Type Conversion**: Converting between strings, numbers, and other types

Each section includes practical examples and real-world use cases to help you apply these concepts effectively in your JavaScript projects.

**Next Steps**: With these fundamentals mastered, you can explore more advanced JavaScript topics like functions, arrays, objects, DOM manipulation, and modern ES6+ features.
