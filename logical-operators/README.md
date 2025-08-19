# JavaScript Logical Operators - Complete Guide

## Definition

Logical operators in JavaScript are symbols used to combine, modify, or evaluate boolean expressions. They are essential for creating conditional logic and controlling program flow based on multiple conditions.

## Types of JavaScript Logical Operators

### 1. AND Operator (`&&`)
**Definition**: Returns the first falsy value or the last value if all are truthy.

**Syntax**: `operand1 && operand2`

**Truth Table**:
| A | B | A && B |
|---|---|--------|
| true | true | true |
| true | false | false |
| false | true | false |
| false | false | false |

**Examples**:
```javascript
// Basic boolean logic
let age = 25;
let hasLicense = true;

if (age >= 18 && hasLicense) {
    console.log("Can drive"); // This will execute
}

// With truthy/falsy values
let user = "John";
let isActive = true;

console.log(user && isActive); // Output: true (last truthy value)
console.log("" && isActive);   // Output: "" (first falsy value)
console.log(0 && "hello");     // Output: 0 (first falsy value)

// Practical usage for default values
function greetUser(name) {
    name && console.log(`Hello, ${name}!`);
}

greetUser("Alice"); // Output: Hello, Alice!
greetUser("");      // No output (empty string is falsy)
```

### 2. OR Operator (`||`)
**Definition**: Returns the first truthy value or the last value if all are falsy.

**Syntax**: `operand1 || operand2`

**Truth Table**:
| A | B | A \|\| B |
|---|---|----------|
| true | true | true |
| true | false | true |
| false | true | true |
| false | false | false |

**Examples**:
```javascript
// Basic boolean logic
let isWeekend = false;
let isHoliday = true;

if (isWeekend || isHoliday) {
    console.log("No work today!"); // This will execute
}

// Setting default values
let username = "";
let displayName = username || "Guest";
console.log(displayName); // Output: "Guest"

let config = {
    theme: null,
    language: "en"
};
let currentTheme = config.theme || "light";
console.log(currentTheme); // Output: "light"

// Multiple conditions
let score = 0;
let bonus = 100;
let finalScore = score || bonus || 50;
console.log(finalScore); // Output: 100 (first truthy value)
```

### 3. NOT Operator (`!`)
**Definition**: Returns the opposite boolean value, converting truthy values to false and falsy values to true.

**Syntax**: `!operand`

**Truth Table**:
| A | !A |
|---|-----|
| true | false |
| false | true |

**Examples**:
```javascript
// Basic boolean negation
let isLoggedIn = false;
if (!isLoggedIn) {
    console.log("Please log in"); // This will execute
}

// Converting to boolean
let value1 = "hello";
let value2 = "";
let value3 = 0;
let value4 = null;

console.log(!value1); // false (string is truthy)
console.log(!value2); // true (empty string is falsy)
console.log(!value3); // true (0 is falsy)
console.log(!value4); // true (null is falsy)

// Double negation for boolean conversion
console.log(!!value1); // true
console.log(!!value2); // false
console.log(!!value3); // false
console.log(!!value4); // false

// Practical usage
function isValidEmail(email) {
    return !(!email || email.indexOf('@') === -1);
}

console.log(isValidEmail("test@example.com")); // true
console.log(isValidEmail("invalid-email"));    // false
```

### 4. Nullish Coalescing Operator (`??`)
**Definition**: Returns the right operand when the left operand is null or undefined, otherwise returns the left operand.

**Syntax**: `operand1 ?? operand2`

**Examples**:
```javascript
// Basic usage
let userName = null;
let defaultName = userName ?? "Anonymous";
console.log(defaultName); // Output: "Anonymous"

// Difference from || operator
let count = 0;
let withOR = count || 10;        // 10 (0 is falsy)
let withNullish = count ?? 10;   // 0 (0 is not null/undefined)

console.log(withOR);      // 10
console.log(withNullish); // 0

// Practical example
function processConfig(config) {
    return {
        theme: config.theme ?? "default",
        timeout: config.timeout ?? 5000,
        debug: config.debug ?? false
    };
}

console.log(processConfig({}));
// Output: { theme: "default", timeout: 5000, debug: false }

console.log(processConfig({ theme: "dark", timeout: 0 }));
// Output: { theme: "dark", timeout: 0, debug: false }
```

## Operator Precedence

JavaScript logical operator precedence (highest to lowest):

1. **NOT** (`!`)
2. **AND** (`&&`)
3. **OR** (`||`)
4. **Nullish Coalescing** (`??`)

**Examples**:
```javascript
// Without parentheses
let result1 = !false && true || false;
// Evaluates as: ((!false) && true) || false = true

// With parentheses for clarity
let result2 = ((!false) && true) || false; // Same result but clearer

// Complex example
let a = false;
let b = true;
let c = false;
let result3 = !a && b || c; // true
console.log(result3);

// Mixing different operators
let value = null;
let fallback1 = false;
let fallback2 = "default";
let final = value ?? fallback1 || fallback2;
console.log(final); // "default"
```

## Short-Circuit Evaluation

JavaScript implements short-circuit evaluation for performance optimization:

### AND Short-Circuit (`&&`)
If the left operand is falsy, the right operand is not evaluated.

```javascript
function expensiveOperation() {
    console.log("This function was called");
    return true;
}

// Short-circuit prevents function call
let result1 = false && expensiveOperation();
console.log(result1); // false, function not called

// Function is called because left operand is truthy
let result2 = true && expensiveOperation();
// Output: "This function was called"
console.log(result2); // true

// Practical usage
let user = null;
user && user.updateProfile(); // Safe - won't throw error if user is null
```

### OR Short-Circuit (`||`)
If the left operand is truthy, the right operand is not evaluated.

```javascript
function getDefaultValue() {
    console.log("Getting default value");
    return "default";
}

// Short-circuit prevents function call
let result1 = "existing" || getDefaultValue();
console.log(result1); // "existing", function not called

// Function is called because left operand is falsy
let result2 = "" || getDefaultValue();
// Output: "Getting default value"
console.log(result2); // "default"

// Chain of fallbacks
let name = "" || null || undefined || getName() || "Anonymous";
```

## Truthy and Falsy Values

Understanding JavaScript's truthy and falsy values is crucial for logical operators:

### Falsy Values
```javascript
// These are the only falsy values in JavaScript
console.log(!false);     // true
console.log(!0);         // true
console.log(!"");        // true
console.log(!null);      // true
console.log(!undefined); // true
console.log(!NaN);       // true
console.log(!0n);        // true (BigInt zero)
```

### Truthy Values
```javascript
// Everything else is truthy
console.log(!true);        // false
console.log(!1);           // false
console.log(!"hello");     // false
console.log(!{});          // false
console.log(![]);          // false
console.log(!function(){}); // false
console.log(!"0");         // false (string "0" is truthy!)
console.log(!-1);          // false
```

## Key Points to Note

### 1. Return Values
Unlike many languages, JavaScript logical operators don't always return boolean values:
```javascript
console.log("hello" && "world"); // "world"
console.log("hello" || "world"); // "hello"
console.log(!"hello");           // false (NOT always returns boolean)
```

### 2. Type Coercion
Be aware of JavaScript's type coercion:
```javascript
console.log(1 && "hello");  // "hello"
console.log(0 || "world");  // "world"
console.log(!!"0");         // true (string "0" is truthy)
console.log(!!0);           // false (number 0 is falsy)
```

### 3. Common Patterns

**Default Values**:
```javascript
function greet(name) {
    name = name || "World";
    console.log(`Hello, ${name}!`);
}

// Modern alternative with nullish coalescing
function greetModern(name) {
    name = name ?? "World";
    console.log(`Hello, ${name}!`);
}
```

**Conditional Execution**:
```javascript
let user = getCurrentUser();
user && renderUserProfile(user);

// Alternative to if statement
isLoggedIn && showDashboard();
```

**Guard Clauses**:
```javascript
function processData(data) {
    if (!data || !data.length) {
        return;
    }
    // Process data...
}
```

### 4. Performance Considerations
- Short-circuit evaluation can improve performance by avoiding unnecessary computations
- Use logical operators for conditional assignments instead of if-else when appropriate
- Be mindful of function calls in logical expressions

### 5. Common Pitfalls
```javascript
// Pitfall 1: Confusing || with ??
let timeout = 0;
let withOR = timeout || 5000;        // 5000 (unexpected!)
let withNullish = timeout ?? 5000;   // 0 (expected)

// Pitfall 2: Assuming boolean return values
let result = "hello" && "world";     // "world", not true
let boolResult = !!(("hello" && "world")); // true

// Pitfall 3: Operator precedence
let mixed = true || false && false;  // true (not false)
let clarified = true || (false && false); // Same result, clearer intent
```

## Interview Questions and Answers

### Basic Level

**Q1: What will be the output of `console.log(false && true || true)`?**
```javascript
console.log(false && true || true); // Output: true
// Explanation: (false && true) || true = false || true = true
```

**Q2: Explain the difference between `||` and `??` operators.**
```javascript
let value1 = 0;
console.log(value1 || 10);  // 10 (0 is falsy)
console.log(value1 ?? 10);  // 0 (0 is not null/undefined)

let value2 = null;
console.log(value2 || 10);  // 10
console.log(value2 ?? 10);  // 10
```

**Q3: What are falsy values in JavaScript?**
Answer: `false`, `0`, `-0`, `0n`, `""`, `null`, `undefined`, and `NaN`.

### Intermediate Level

**Q4: What will this code output and why?**
```javascript
let a = "hello";
let b = "";
let c = "world";
console.log(a && b || c);
```
Answer: `"world"` - Because `a && b` evaluates to `""` (falsy), then `"" || c` returns `"world"`.

**Q5: How can you safely call a method on an object that might be null?**
```javascript
// Using &&
obj && obj.method();

// Using optional chaining (modern approach)
obj?.method();
```

**Q6: What's the difference between `!` and `!!`?**
```javascript
let value = "hello";
console.log(!value);  // false (negation)
console.log(!!value); // true (convert to boolean)
```

### Advanced Level

**Q7: Implement a function that sets default values using logical operators.**
```javascript
function createUser(options) {
    options = options || {};
    return {
        name: options.name || "Anonymous",
        age: options.age ?? 0,
        active: options.active ?? true,
        permissions: options.permissions || ["read"]
    };
}
```

**Q8: What will this complex expression output?**
```javascript
let result = null || undefined && "hello" || 0 && "world" || "default";
console.log(result); // "default"
// Breakdown: null || (undefined && "hello") || (0 && "world") || "default"
//           = null || undefined || false || "default"
//           = "default"
```

**Q9: How would you implement a simple caching mechanism using logical operators?**
```javascript
let cache = {};

function expensiveOperation(key) {
    return cache[key] || (cache[key] = performCalculation(key));
}

function performCalculation(key) {
    console.log(`Calculating for ${key}`);
    return key * 2;
}
```

**Q10: Explain short-circuit evaluation with a practical example.**
```javascript
// Unsafe way
function processUser(user) {
    if (user.isActive) {
        user.updateLastLogin();
    }
}

// Safe way using short-circuit
function processUserSafe(user) {
    user && user.isActive && user.updateLastLogin();
}

// The second approach won't throw an error if user is null/undefined
```
