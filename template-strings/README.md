# JavaScript Template Strings Reference

## Definition
Template strings (also called template literals) are string literals that allow embedded expressions and multi-line strings. They use backticks (`) instead of single or double quotes and support variable interpolation using `${}` syntax.

## Syntax
```javascript
`string text`
`string text line 1
 string text line 2`
`string text ${expression} string text`
```

**Key Features:**
- Enclosed in backticks (`) instead of quotes
- Support variable interpolation with `${}`
- Allow multi-line strings without escape characters
- Can contain expressions, function calls, and complex calculations

---

## Basic Examples

### Variable Interpolation
```javascript
const name = "Alice";
const age = 25;

// Traditional string concatenation
const greeting1 = "Hello, my name is " + name + " and I'm " + age + " years old.";

// Template string
const greeting2 = `Hello, my name is ${name} and I'm ${age} years old.`;

console.log(greeting2); // "Hello, my name is Alice and I'm 25 years old."
```

### Multi-line Strings
```javascript
// Traditional approach (requires escape characters)
const multiLine1 = "Line 1\nLine 2\nLine 3";

// Template string (natural multi-line)
const multiLine2 = `Line 1
Line 2
Line 3`;

console.log(multiLine2);
// Output:
// Line 1
// Line 2
// Line 3
```

---

## Advanced Examples

### Expression Evaluation
```javascript
const a = 10;
const b = 20;

const result = `The sum of ${a} and ${b} is ${a + b}`;
console.log(result); // "The sum of 10 and 20 is 30"

// Complex expressions
const price = 99.99;
const tax = 0.08;
const total = `Total: $${(price * (1 + tax)).toFixed(2)}`;
console.log(total); // "Total: $107.99"
```

### Function Calls
```javascript
function formatDate(date) {
    return date.toLocaleDateString();
}

function getTimeOfDay() {
    const hour = new Date().getHours();
    if (hour < 12) return "morning";
    if (hour < 18) return "afternoon";
    return "evening";
}

const today = new Date();
const message = `Good ${getTimeOfDay()}! Today is ${formatDate(today)}.`;
console.log(message); // "Good afternoon! Today is 12/25/2023."
```

### Conditional Logic
```javascript
const user = {
    name: "Bob",
    isAdmin: true,
    points: 150
};

const status = `Welcome ${user.name}! ${user.isAdmin ? 'You have admin privileges.' : 'You are a regular user.'}`;
console.log(status); // "Welcome Bob! You have admin privileges."

// Complex conditional
const badge = `${user.points >= 100 ? '🏆 Gold' : user.points >= 50 ? '🥈 Silver' : '🥉 Bronze'} Member`;
console.log(badge); // "🏆 Gold Member"
```

---

## HTML Template Generation

### Dynamic HTML Creation
```javascript
const products = [
    { name: "Laptop", price: 999.99, inStock: true },
    { name: "Phone", price: 599.99, inStock: false },
    { name: "Tablet", price: 399.99, inStock: true }
];

function generateProductCard(product) {
    return `
        <div class="product-card ${product.inStock ? 'available' : 'out-of-stock'}">
            <h3>${product.name}</h3>
            <p class="price">$${product.price}</p>
            <p class="status">${product.inStock ? 'In Stock' : 'Out of Stock'}</p>
            <button ${product.inStock ? '' : 'disabled'}>
                ${product.inStock ? 'Add to Cart' : 'Notify When Available'}
            </button>
        </div>
    `;
}

const productHTML = products.map(generateProductCard).join('');
console.log(productHTML);
```

### CSS Styling
```javascript
const theme = {
    primaryColor: '#3498db',
    secondaryColor: '#2c3e50',
    fontSize: '16px'
};

const styles = `
    .header {
        background-color: ${theme.primaryColor};
        color: white;
        font-size: ${theme.fontSize};
    }
    
    .sidebar {
        background-color: ${theme.secondaryColor};
        width: ${window.innerWidth > 768 ? '250px' : '100%'};
    }
`;

// Inject styles into page
const styleSheet = document.createElement('style');
styleSheet.textContent = styles;
document.head.appendChild(styleSheet);
```

---

## Tagged Templates

### Basic Tagged Template
```javascript
function highlight(strings, ...values) {
    return strings.reduce((result, string, i) => {
        const value = values[i] ? `<mark>${values[i]}</mark>` : '';
        return result + string + value;
    }, '');
}

const searchTerm = "JavaScript";
const text = highlight`Learning ${searchTerm} is fun and ${searchTerm} is powerful!`;
console.log(text); // "Learning <mark>JavaScript</mark> is fun and <mark>JavaScript</mark> is powerful!"
```

### URL Builder
```javascript
function url(strings, ...values) {
    return strings.reduce((result, string, i) => {
        const value = values[i] ? encodeURIComponent(values[i]) : '';
        return result + string + value;
    }, '');
}

const endpoint = "users";
const userId = "john doe";
const apiUrl = url`https://api.example.com/${endpoint}/${userId}`;
console.log(apiUrl); // "https://api.example.com/users/john%20doe"
```

---

## Real-World Use Cases

### API Requests
```javascript
const apiKey = "your-api-key";
const userId = 123;
const endpoint = "profile";

const apiUrl = `https://api.example.com/v1/${endpoint}/${userId}?key=${apiKey}`;

fetch(apiUrl)
    .then(response => response.json())
    .then(data => {
        const userInfo = `User: ${data.name} (${data.email})`;
        console.log(userInfo);
    });
```

### Log Messages
```javascript
function logError(error, context) {
    const timestamp = new Date().toISOString();
    const message = `[${timestamp}] ERROR in ${context.file}:${context.line} - ${error.message}`;
    console.error(message);
}

// Usage
logError(
    new Error("Database connection failed"), 
    { file: "database.js", line: 42 }
);
// Output: [2023-12-25T10:30:45.123Z] ERROR in database.js:42 - Database connection failed
```

### Email Templates
```javascript
function generateEmailTemplate(user, order) {
    return `
        <!DOCTYPE html>
        <html>
        <head>
            <title>Order Confirmation</title>
        </head>
        <body>
            <h1>Thank you, ${user.firstName}!</h1>
            <p>Your order #${order.id} has been confirmed.</p>
            <div class="order-details">
                <h2>Order Summary</h2>
                ${order.items.map(item => `
                    <div class="item">
                        <span>${item.name}</span>
                        <span>$${item.price}</span>
                    </div>
                `).join('')}
                <div class="total">
                    <strong>Total: $${order.total}</strong>
                </div>
            </div>
            <p>Estimated delivery: ${order.deliveryDate}</p>
        </body>
        </html>
    `;
}
```

---

## Best Practices

### Do's
- Use template strings for string interpolation instead of concatenation
- Utilize multi-line capability for HTML/CSS generation
- Combine with array methods like `map()` and `join()` for dynamic content
- Use tagged templates for specialized formatting

### Don'ts
- Don't use template strings for simple static strings
- Avoid deeply nested expressions (extract to variables instead)
- Be careful with user input to prevent XSS attacks in HTML generation

### Performance Notes
- Template strings are generally faster than string concatenation
- For simple cases, regular strings might have slight performance advantages
- The difference is negligible in most real-world applications

### Security Considerations
```javascript
// ❌ Dangerous - direct user input in HTML
const userInput = "<script>alert('XSS')</script>";
const html = `<div>${userInput}</div>`; // This could execute malicious code

// ✅ Safe - escape user input
function escapeHtml(text) {
    const div = document.createElement('div');
    div.textContent = text;
    return div.innerHTML;
}

const safeHtml = `<div>${escapeHtml(userInput)}</div>`;
```
