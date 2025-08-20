# JavaScript Objects Guide

## Objects in JavaScript

### Definition
Objects in JavaScript are collections of key-value pairs that allow you to store and organize related data and functionality together. They are one of the fundamental data types in JavaScript and are used to represent real-world entities with properties and behaviors.

### Syntax
```javascript
// Object literal syntax
const objectName = {
  key1: value1,
  key2: value2,
  key3: value3
};

// Constructor syntax
const objectName = new Object();
objectName.key1 = value1;
objectName.key2 = value2;
```

### Examples
```javascript
// Simple object
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

// Object with different data types
const student = {
  firstName: "Alice",
  lastName: "Smith",
  age: 22,
  grades: [85, 90, 78],
  isEnrolled: true,
  address: {
    street: "123 Main St",
    city: "Boston"
  }
};
```

## Properties and Values

### Definition
Properties are the key-value pairs that make up an object. The key (property name) is always a string, while the value can be any JavaScript data type including numbers, strings, booleans, arrays, functions, or other objects.

### Examples
```javascript
const car = {
  // String property
  brand: "Toyota",
  
  // Number property
  year: 2022,
  
  // Boolean property
  isElectric: false,
  
  // Array property
  colors: ["red", "blue", "white"],
  
  // Object property
  engine: {
    type: "V6",
    horsepower: 300
  },
  
  // Function property (method)
  start: function() {
    return "Engine started!";
  }
};
```

## Accessing Items in Objects

There are two primary ways to access object properties: dot notation and bracket notation.

## Dot Notation

### Definition
Dot notation is the most common way to access object properties using a dot (.) followed by the property name.

### Syntax
```javascript
objectName.propertyName
```

### Examples
```javascript
const person = {
  name: "Sarah",
  age: 25,
  occupation: "Engineer"
};

// Accessing properties
console.log(person.name);       // "Sarah"
console.log(person.age);        // 25
console.log(person.occupation); // "Engineer"

// Setting properties
person.city = "Seattle";        // Adding new property
person.age = 26;                // Updating existing property

console.log(person.city);       // "Seattle"
```

### Limitations
- Cannot be used with property names that contain spaces or special characters
- Cannot be used with property names that start with numbers
- Cannot be used when the property name is stored in a variable

## Bracket Notation

### Definition
Bracket notation allows you to access object properties using square brackets and a string representation of the property name.

### Syntax
```javascript
objectName["propertyName"]
objectName[variableName]
```

### Examples
```javascript
const person = {
  name: "Mike",
  age: 35,
  "favorite color": "blue",
  "123abc": "weird property name"
};

// Basic bracket notation
console.log(person["name"]);           // "Mike"
console.log(person["age"]);            // 35

// Properties with spaces or special characters
console.log(person["favorite color"]); // "blue"
console.log(person["123abc"]);         // "weird property name"

// Using variables
const propertyName = "name";
console.log(person[propertyName]);     // "Mike"

// Dynamic property access
const properties = ["name", "age"];
properties.forEach(prop => {
  console.log(person[prop]);
});

// Setting properties
person["location"] = "California";
person["favorite color"] = "green";    // Updating
```

### Advantages
- Works with any property name (including those with spaces, special characters, or starting with numbers)
- Allows dynamic property access using variables
- Essential for computed property names

## Delete

### Definition
The `delete` operator is used to remove properties from objects. It returns `true` if the property was successfully deleted, and `false` otherwise.

### Syntax
```javascript
delete objectName.propertyName
delete objectName["propertyName"]
```

### Examples
```javascript
const student = {
  name: "Emma",
  age: 20,
  grade: "A",
  email: "emma@email.com",
  phone: "123-456-7890"
};

console.log(student);
// Output: { name: "Emma", age: 20, grade: "A", email: "emma@email.com", phone: "123-456-7890" }

// Delete using dot notation
delete student.phone;
console.log(student);
// Output: { name: "Emma", age: 20, grade: "A", email: "emma@email.com" }

// Delete using bracket notation
delete student["email"];
console.log(student);
// Output: { name: "Emma", age: 20, grade: "A" }

// Check if property exists before and after deletion
console.log("grade" in student);      // true
delete student.grade;
console.log("grade" in student);      // false

// Delete returns boolean
const deleteResult = delete student.age;
console.log(deleteResult);            // true
console.log(student);                 // { name: "Emma" }
```

### Important Notes
- `delete` only removes the property from the object, not the object itself
- Cannot delete variables, functions, or function parameters
- Does not work on array elements (use array methods like `splice()` instead)
- Some built-in properties cannot be deleted
- In strict mode, attempting to delete non-deletable properties will throw an error

### Alternative to Delete
```javascript
// Instead of delete, you can set property to undefined
const obj = { a: 1, b: 2, c: 3 };

// Using delete (removes property completely)
delete obj.a;
console.log(obj);        // { b: 2, c: 3 }
console.log("a" in obj); // false

// Setting to undefined (property still exists)
obj.b = undefined;
console.log(obj);        // { b: undefined, c: 3 }
console.log("b" in obj); // true
```

## Object References

### Definition
Object references in JavaScript refer to how objects are stored and accessed in memory. Unlike primitive values, objects are stored by reference, meaning variables hold a reference (memory address) to the object rather than the object itself.

### How References Work
```javascript
// Primitive values are copied by value
let a = 5;
let b = a;  // b gets a copy of the value 5
a = 10;
console.log(a);  // 10
console.log(b);  // 5 (unchanged)

// Objects are copied by reference
let obj1 = { name: "John", age: 25 };
let obj2 = obj1;  // obj2 gets a reference to the same object
obj1.age = 30;
console.log(obj1.age);  // 30
console.log(obj2.age);  // 30 (changed because it's the same object)
```

### Examples of Reference Behavior

#### Modifying Objects Through References
```javascript
const person = { name: "Alice", city: "Boston" };
const student = person;  // Both variables reference the same object

// Modifying through either reference affects the same object
student.grade = "A+";
person.age = 22;

console.log(person);   // { name: "Alice", city: "Boston", grade: "A+", age: 22 }
console.log(student);  // { name: "Alice", city: "Boston", grade: "A+", age: 22 }
console.log(person === student);  // true (same reference)
```

#### Function Parameters and References
```javascript
function modifyObject(obj) {
  obj.modified = true;
  obj.count = 100;
}

function reassignObject(obj) {
  obj = { newProperty: "new value" };  // Creates new object, doesn't affect original
}

const myObj = { original: true };

modifyObject(myObj);
console.log(myObj);  // { original: true, modified: true, count: 100 }

reassignObject(myObj);
console.log(myObj);  // { original: true, modified: true, count: 100 } (unchanged)
```

#### Comparing Objects
```javascript
// Objects with same content but different references
const obj1 = { name: "John", age: 25 };
const obj2 = { name: "John", age: 25 };
console.log(obj1 === obj2);  // false (different objects in memory)

// Same reference
const obj3 = obj1;
console.log(obj1 === obj3);  // true (same reference)

// Arrays work the same way
const arr1 = [1, 2, 3];
const arr2 = [1, 2, 3];
const arr3 = arr1;
console.log(arr1 === arr2);  // false
console.log(arr1 === arr3);  // true
```

### Copying Objects

#### Shallow Copy
```javascript
const original = { name: "Tom", hobbies: ["reading", "gaming"] };

// Method 1: Object.assign()
const copy1 = Object.assign({}, original);

// Method 2: Spread operator
const copy2 = { ...original };

// Both create shallow copies
copy1.name = "Jerry";
console.log(original.name);  // "Tom" (unchanged)
console.log(copy1.name);     // "Jerry"

// But nested objects are still referenced
copy1.hobbies.push("cooking");
console.log(original.hobbies);  // ["reading", "gaming", "cooking"] (changed!)
console.log(copy1.hobbies);     // ["reading", "gaming", "cooking"]
```

#### Deep Copy
```javascript
const original = { 
  name: "Sarah", 
  address: { city: "Seattle", state: "WA" },
  hobbies: ["tennis", "painting"]
};

// Deep copy using JSON (limitations: no functions, undefined, symbols)
const deepCopy1 = JSON.parse(JSON.stringify(original));

// Using structuredClone() (modern browsers)
const deepCopy2 = structuredClone(original);

// Now nested objects are truly independent
deepCopy1.address.city = "Portland";
deepCopy1.hobbies.push("hiking");

console.log(original.address.city);  // "Seattle" (unchanged)
console.log(deepCopy1.address.city); // "Portland"
console.log(original.hobbies);       // ["tennis", "painting"] (unchanged)
console.log(deepCopy1.hobbies);      // ["tennis", "painting", "hiking"]
```

### Common Pitfalls

#### Unexpected Mutations
```javascript
function processUsers(users) {
  // Modifying the original array!
  users.forEach(user => {
    user.processed = true;
  });
  return users;
}

const originalUsers = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 }
];

const processedUsers = processUsers(originalUsers);
console.log(originalUsers[0].processed);  // true (original was modified!)
```

#### Solutions to Avoid Mutations
```javascript
function processUsersSafe(users) {
  // Create a deep copy first
  const usersCopy = users.map(user => ({ ...user }));
  usersCopy.forEach(user => {
    user.processed = true;
  });
  return usersCopy;
}

const originalUsers = [
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 }
];

const processedUsers = processUsersSafe(originalUsers);
console.log(originalUsers[0].processed);  // undefined (original unchanged)
console.log(processedUsers[0].processed); // true
```
