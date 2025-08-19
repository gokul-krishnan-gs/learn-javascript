# JavaScript Arrays - Complete Guide

## Understanding Arrays

An **array** is a data structure that stores multiple values in a single variable. Arrays are ordered collections of elements that can hold different data types including numbers, strings, objects, and even other arrays.

### Definition and Syntax

```javascript
// Creating an empty array
let emptyArray = [];

// Creating an array with initial values
let fruits = ['apple', 'banana', 'orange'];

// Using Array constructor
let numbers = new Array(1, 2, 3, 4, 5);

// Mixed data types
let mixedArray = ['hello', 42, true, null, {name: 'John'}];
```

## Zero-Based Indexing

Arrays in JavaScript use **zero-based indexing**, meaning the first element is at index 0, the second at index 1, and so on.

```javascript
let colors = ['red', 'green', 'blue'];
console.log(colors[0]); // 'red' (first element)
console.log(colors[1]); // 'green' (second element)
console.log(colors[2]); // 'blue' (third element)
```

## Empty Arrays

```javascript
// Creating empty arrays
let emptyArray1 = [];
let emptyArray2 = new Array();

// Checking if array is empty
if (emptyArray1.length === 0) {
    console.log('Array is empty');
}
```

## Accessing Array Items

```javascript
let students = ['Alice', 'Bob', 'Charlie', 'Diana'];

// Accessing by index
console.log(students[0]);    // 'Alice'
console.log(students[2]);    // 'Charlie'

// Accessing last element
console.log(students[students.length - 1]); // 'Diana'

// Using at() method (newer approach)
console.log(students.at(-1)); // 'Diana' (last element)
console.log(students.at(-2)); // 'Charlie' (second to last)
```

## Nested/2D Arrays

Arrays can contain other arrays, creating multidimensional structures.

```javascript
// 2D Array (matrix)
let matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// Accessing nested elements
console.log(matrix[0][1]); // 2 (first row, second column)
console.log(matrix[2][0]); // 7 (third row, first column)

// Nested arrays with different data types
let nestedData = [
    ['John', 25, 'Engineer'],
    ['Jane', 30, 'Designer'],
    ['Bob', 35, 'Manager']
];
```

## Array Methods

### Adding/Removing Elements

#### push() - Add to End
```javascript
let fruits = ['apple', 'banana'];
fruits.push('orange');
console.log(fruits); // ['apple', 'banana', 'orange']

// Adding multiple elements
fruits.push('grape', 'mango');
console.log(fruits); // ['apple', 'banana', 'orange', 'grape', 'mango']
```

#### pop() - Remove from End
```javascript
let fruits = ['apple', 'banana', 'orange'];
let removed = fruits.pop();
console.log(removed); // 'orange'
console.log(fruits);  // ['apple', 'banana']
```

#### unshift() - Add to Beginning
```javascript
let fruits = ['banana', 'orange'];
fruits.unshift('apple');
console.log(fruits); // ['apple', 'banana', 'orange']

// Adding multiple elements
fruits.unshift('grape', 'mango');
console.log(fruits); // ['grape', 'mango', 'apple', 'banana', 'orange']
```

#### shift() - Remove from Beginning
```javascript
let fruits = ['apple', 'banana', 'orange'];
let removed = fruits.shift();
console.log(removed); // 'apple'
console.log(fruits);  // ['banana', 'orange']
```

### Other Important Array Methods

#### concat() - Join Arrays
```javascript
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let combined = arr1.concat(arr2);
console.log(combined); // [1, 2, 3, 4, 5, 6]

// Concatenating multiple arrays
let arr3 = [7, 8];
let result = arr1.concat(arr2, arr3);
console.log(result); // [1, 2, 3, 4, 5, 6, 7, 8]
```

#### includes() - Check if Element Exists
```javascript
let fruits = ['apple', 'banana', 'orange'];
console.log(fruits.includes('banana')); // true
console.log(fruits.includes('grape'));  // false
```

#### sort() - Sort Array Elements
```javascript
let fruits = ['banana', 'apple', 'orange'];
fruits.sort();
console.log(fruits); // ['apple', 'banana', 'orange']

// Sorting numbers (requires compare function)
let numbers = [3, 1, 4, 1, 5];
numbers.sort((a, b) => a - b);
console.log(numbers); // [1, 1, 3, 4, 5]
```

#### slice() - Extract Portion of Array
```javascript
let fruits = ['apple', 'banana', 'orange', 'grape', 'mango'];
let sliced = fruits.slice(1, 3);
console.log(sliced); // ['banana', 'orange']
console.log(fruits); // Original array unchanged
```

#### splice() - Add/Remove Elements at Specific Position
```javascript
let fruits = ['apple', 'banana', 'orange'];

// Remove elements
fruits.splice(1, 1); // Remove 1 element at index 1
console.log(fruits); // ['apple', 'orange']

// Add elements
fruits.splice(1, 0, 'grape', 'mango'); // Add at index 1, remove 0 elements
console.log(fruits); // ['apple', 'grape', 'mango', 'orange']

// Replace elements
fruits.splice(1, 2, 'kiwi'); // Remove 2 elements at index 1, add 'kiwi'
console.log(fruits); // ['apple', 'kiwi', 'orange']
```

#### join() - Convert Array to String
```javascript
let fruits = ['apple', 'banana', 'orange'];
let joined = fruits.join(', ');
console.log(joined); // 'apple, banana, orange'

// Different separator
let withDashes = fruits.join(' - ');
console.log(withDashes); // 'apple - banana - orange'
```

#### reverse() - Reverse Array Order
```javascript
let numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers); // [5, 4, 3, 2, 1]
```

## Key Points to Remember

### Important Characteristics
- **Zero-based indexing**: First element is at index 0
- **Dynamic size**: Arrays can grow and shrink during runtime
- **Mixed data types**: Can store different types of data in the same array
- **Reference type**: Arrays are objects and passed by reference

### Performance Considerations
- `push()` and `pop()` are faster than `unshift()` and `shift()`
- `unshift()` and `shift()` require reindexing all elements
- `splice()` can be expensive for large arrays as it may require shifting elements

### Mutating vs Non-Mutating Methods
- **Mutating**: `push()`, `pop()`, `shift()`, `unshift()`, `splice()`, `sort()`, `reverse()`
- **Non-Mutating**: `concat()`, `slice()`, `join()`, `includes()`

### Common Pitfalls
- Remember that `sort()` converts elements to strings by default
- `splice()` modifies the original array, `slice()` does not
- Accessing non-existent indices returns `undefined`
- Array length can be manually set, which may create empty slots

### Best Practices
- Use `const` for arrays that won't be reassigned (contents can still change)
- Check array length before accessing elements to avoid undefined values
- Use appropriate methods based on whether you want to mutate the original array
- Consider using `Array.from()` or spread operator `...` for array copying
- Use descriptive variable names for better code readability

### Memory and Efficiency
- Arrays are stored as objects in memory
- Large arrays with sparse data (many empty slots) can be memory inefficient
- Consider using `Array.isArray()` to check if a variable is actually an array
