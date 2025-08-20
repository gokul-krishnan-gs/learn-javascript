# JavaScript JSON Concepts Reference

## JSON

**Definition:** JavaScript Object Notation - a lightweight, text-based data interchange format that uses human-readable text to store and transmit data objects.

**Syntax:**
```javascript
{
  "key": "value",
  "number": 123,
  "boolean": true,
  "array": [1, 2, 3],
  "object": {"nested": "value"},
  "null": null
}
```

**Example:**
```javascript
const jsonData = {
  "name": "John Doe",
  "age": 30,
  "isActive": true,
  "hobbies": ["reading", "coding", "gaming"],
  "address": {
    "city": "New York",
    "zipCode": "10001"
  }
};
```

## JSON.stringify()

**Definition:** Converts a JavaScript object or value into a JSON string representation.

**Syntax:**
```javascript
JSON.stringify(value, replacer, space)
```

**Example:**
```javascript
const user = {
  name: "Alice",
  age: 25,
  skills: ["JavaScript", "Python"]
};

const jsonString = JSON.stringify(user);
console.log(jsonString);
// Output: '{"name":"Alice","age":25,"skills":["JavaScript","Python"]}'

// With formatting (pretty print)
const prettyJson = JSON.stringify(user, null, 2);
console.log(prettyJson);
// Output:
// {
//   "name": "Alice",
//   "age": 25,
//   "skills": [
//     "JavaScript",
//     "Python"
//   ]
// }
```

## JSON.parse()

**Definition:** Parses a JSON string and constructs the JavaScript value or object described by the string.

**Syntax:**
```javascript
JSON.parse(text, reviver)
```

**Example:**
```javascript
const jsonString = '{"name":"Bob","age":28,"isStudent":false}';

const parsedObject = JSON.parse(jsonString);
console.log(parsedObject);
// Output: { name: "Bob", age: 28, isStudent: false }

console.log(parsedObject.name); // "Bob"
console.log(typeof parsedObject); // "object"

// With error handling
try {
  const invalidJson = '{"name": "Invalid JSON"'; // Missing closing brace
  const result = JSON.parse(invalidJson);
} catch (error) {
  console.log("Invalid JSON:", error.message);
}
```

## Common Use Cases

### Converting between JavaScript objects and JSON strings:
```javascript
// Object to JSON string (for API requests, localStorage, etc.)
const data = { userId: 123, action: "login" };
const jsonPayload = JSON.stringify(data);

// JSON string to JavaScript object (from API responses, localStorage, etc.)
const response = '{"status":"success","data":{"id":456}}';
const responseObj = JSON.parse(response);
```

### Working with localStorage:
```javascript
// Storing object in localStorage
const userPreferences = { theme: "dark", language: "en" };
localStorage.setItem("preferences", JSON.stringify(userPreferences));

// Retrieving object from localStorage
const stored = localStorage.getItem("preferences");
const preferences = JSON.parse(stored);
```
