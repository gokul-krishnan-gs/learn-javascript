# JavaScript Timing Functions Reference

## setTimeout()

### Definition
The `setTimeout()` function executes a specified function or code snippet once after a specified delay (in milliseconds). It's used to delay the execution of code.

### Syntax
```javascript
setTimeout(function, delay, param1, param2, ...)
setTimeout(code, delay)
```

**Parameters:**
- `function` - The function to be executed
- `delay` - Time delay in milliseconds before execution
- `param1, param2, ...` - Optional parameters to pass to the function

**Returns:** A timeout ID that can be used with `clearTimeout()`

### Example
```javascript
// Basic usage
setTimeout(() => {
    console.log("This runs after 2 seconds");
}, 2000);

// With parameters
function greetUser(name, age) {
    console.log(`Hello ${name}, you are ${age} years old`);
}

setTimeout(greetUser, 1500, "Alice", 25);

// Storing timeout ID for potential cancellation
const timeoutId = setTimeout(() => {
    console.log("This might not run if cleared");
}, 3000);

// Cancel the timeout
clearTimeout(timeoutId);
```

---

## setInterval()

### Definition
The `setInterval()` function repeatedly executes a specified function or code snippet at fixed time intervals (in milliseconds). It continues executing until cleared or the page is closed.

### Syntax
```javascript
setInterval(function, interval, param1, param2, ...)
setInterval(code, interval)
```

**Parameters:**
- `function` - The function to be executed repeatedly
- `interval` - Time interval in milliseconds between executions
- `param1, param2, ...` - Optional parameters to pass to the function

**Returns:** An interval ID that can be used with `clearInterval()`

### Example
```javascript
// Basic usage - runs every 1 second
const intervalId = setInterval(() => {
    console.log("Current time:", new Date().toLocaleTimeString());
}, 1000);

// With parameters
function updateCounter(step) {
    console.log("Counter:", counter);
    counter += step;
}

let counter = 0;
const counterId = setInterval(updateCounter, 500, 5);

// Real-world example - Auto-save feature
let autoSaveId = setInterval(() => {
    // Simulate saving data
    console.log("Auto-saving document...");
    saveDocument();
}, 30000); // Save every 30 seconds

function saveDocument() {
    // Save logic here
    console.log("Document saved successfully");
}
```

---

## clearInterval()

### Definition
The `clearInterval()` function cancels a repeated execution that was previously established by calling `setInterval()`. It stops the interval from continuing to execute.

### Syntax
```javascript
clearInterval(intervalId)
```

**Parameters:**
- `intervalId` - The ID returned by `setInterval()`

**Returns:** `undefined`

### Example
```javascript
// Start an interval
let count = 0;
const intervalId = setInterval(() => {
    count++;
    console.log(`Count: ${count}`);
    
    // Stop after 5 executions
    if (count >= 5) {
        clearInterval(intervalId);
        console.log("Interval cleared!");
    }
}, 1000);

// Clear interval based on user action
const stopButton = document.getElementById('stopButton');
let timerId = setInterval(() => {
    console.log("Running...");
}, 2000);

stopButton.addEventListener('click', () => {
    clearInterval(timerId);
    console.log("Timer stopped by user");
});

// Conditional clearing
let attempts = 0;
const maxAttempts = 10;

const checkStatus = setInterval(() => {
    attempts++;
    console.log(`Checking status... Attempt ${attempts}`);
    
    // Simulate some condition
    const success = Math.random() > 0.7;
    
    if (success || attempts >= maxAttempts) {
        clearInterval(checkStatus);
        console.log(success ? "Success!" : "Max attempts reached");
    }
}, 1000);
```

---

## Additional Notes

### clearTimeout()
Similar to `clearInterval()`, there's also `clearTimeout()` to cancel a timeout:

```javascript
const timeoutId = setTimeout(() => {
    console.log("This won't run");
}, 5000);

clearTimeout(timeoutId); // Cancels the timeout
```

### Best Practices
1. **Always store IDs**: Keep references to timeout/interval IDs for cleanup
2. **Clear intervals**: Always clear intervals when they're no longer needed to prevent memory leaks
3. **Avoid short intervals**: Very short intervals (< 10ms) may impact performance
4. **Use requestAnimationFrame**: For animations, consider `requestAnimationFrame()` instead of `setInterval()`

### Common Use Cases
- **setTimeout**: Delayed notifications, debouncing user input, one-time animations
- **setInterval**: Real-time updates, polling APIs, recurring tasks, timers
- **clearInterval**: User-triggered stops, cleanup on page unload, conditional stopping
