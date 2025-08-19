# JavaScript Control Flow

Control flow decides **how the code is executed** inside a program. By default, JavaScript runs statements **line by line**, but with conditionals and loops, we can **control** the execution order.

## Table of Contents
- [1. `if` Statement](#1-if-statement)
- [2. `else` Statement](#2-else-statement)
- [3. `else if` Statement](#3-else-if-statement)
- [4. `switch` Statement](#4-switch-statement)
- [5. `for` Loop](#5-for-loop)
- [6. `while` Loop](#6-while-loop)
- [7. `do...while` Loop](#7-dowhile-loop)
- [⭐ Important Points & Features](#-important-points--features)

---

## 1. `if` Statement

### Definition
Used to run a block of code **only if a condition is true**.

### Syntax
```javascript
if (condition) {
  // code to run if condition is true
}
```

### Example
```javascript
let age = 18;
if (age >= 18) {
  console.log("You are eligible to vote!");
}
```

---

## 2. `else` Statement

### Definition
Specifies a block of code to run if the condition is false.

### Syntax
```javascript
if (condition) {
  // runs if condition is true
} else {
  // runs if condition is false
}
```

### Example
```javascript
let temperature = 15;
if (temperature > 25) {
  console.log("It's hot outside!");
} else {
  console.log("It's cool outside!");
}
```

---

## 3. `else if` Statement

### Definition
Allows multiple conditions to be checked one after another.

### Syntax
```javascript
if (condition1) {
  // code if condition1 is true
} else if (condition2) {
  // code if condition2 is true
} else {
  // code if none are true
}
```

### Example
```javascript
let score = 85;
if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else if (score >= 70) {
  console.log("Grade: C");
} else {
  console.log("Grade: F");
}
```

---

## 4. `switch` Statement

### Definition
Tests a variable against multiple possible values. Cleaner than multiple `else if` statements.

### Syntax
```javascript
switch (expression) {
  case value1:
    // runs if expression === value1
    break;
  case value2:
    // runs if expression === value2
    break;
  default:
    // runs if no case matches
}
```

### Example
```javascript
let day = "Monday";
switch (day) {
  case "Monday":
    console.log("Start of the work week!");
    break;
  case "Friday":
    console.log("TGIF!");
    break;
  case "Saturday":
  case "Sunday":
    console.log("Weekend time!");
    break;
  default:
    console.log("Regular day");
}
```

---

## 5. `for` Loop

### Definition
Repeats a block of code a fixed number of times.

### Syntax
```javascript
for (initialization; condition; increment) {
  // code runs until condition is false
}
```

### Example
```javascript
// Print numbers 1 to 5
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
```

---

## 6. `while` Loop

### Definition
Repeats a block of code as long as the condition is true.

### Syntax
```javascript
while (condition) {
  // code runs while condition is true
}
```

### Example
```javascript
let count = 0;
while (count < 3) {
  console.log("Count is: " + count);
  count++; // Important: increment to avoid infinite loop
}
```

---

## 7. `do...while` Loop

### Definition
Similar to `while`, but ensures the code runs at least once, even if the condition is false.

### Syntax
```javascript
do {
  // code runs once, then repeats if condition is true
} while (condition);
```

### Example
```javascript
let input;
do {
  input = prompt("Enter a number greater than 10:");
} while (input <= 10);
console.log("You entered: " + input);
```

---

## ⭐ Important Points & Features

### Key Concepts
- **Control flow** allows decision-making (`if`, `else`, `switch`) and repetition (`for`, `while`, `do...while`)
- **Conditional statements** help your program make decisions based on different scenarios
- **Loops** help automate repetitive tasks efficiently

### Best Practices
- Use `if...else` for simple conditions that are not too numerous
- Use `switch` when checking one variable against many fixed values
- Use `for` loop when the number of iterations is known in advance
- Use `while` loop when the number of iterations is not known beforehand
- Use `do...while` loop when you need to guarantee at least one execution

### ⚠️ Important Warnings
- **Always be careful of infinite loops** (when the condition never becomes false)
- Remember to use `break` statements in `switch` cases to prevent fall-through
- Ensure loop counters are properly incremented to avoid infinite loops
- Use proper indentation and braces for better code readability

### Performance Tips
- `switch` statements are generally faster than multiple `else if` statements for many conditions
- `for` loops are typically faster than `while` loops for known iterations
- Consider using `for...of` or `for...in` loops for iterating over arrays and objects
