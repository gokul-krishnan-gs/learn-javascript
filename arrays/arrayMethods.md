# JavaScript Array Methods Reference

## Mutating Methods (modify the original array)

### `push()`
Adds one or more elements to the end of an array and returns the new length.
```javascript
const arr = [1, 2, 3];
arr.push(4, 5); // Returns 5, arr is now [1, 2, 3, 4, 5]
```

### `pop()`
Removes the last element from an array and returns that element.
```javascript
const arr = [1, 2, 3];
const last = arr.pop(); // Returns 3, arr is now [1, 2]
```

### `unshift()`
Adds one or more elements to the beginning of an array and returns the new length.
```javascript
const arr = [2, 3];
arr.unshift(0, 1); // Returns 4, arr is now [0, 1, 2, 3]
```

### `shift()`
Removes the first element from an array and returns that element.
```javascript
const arr = [1, 2, 3];
const first = arr.shift(); // Returns 1, arr is now [2, 3]
```

### `splice()`
Changes the contents of an array by removing or replacing existing elements and/or adding new elements.
```javascript
const arr = [1, 2, 3, 4, 5];
arr.splice(2, 1, 'a', 'b'); // Returns [3], arr is now [1, 2, 'a', 'b', 4, 5]
```

### `sort()`
Sorts the elements of an array in place and returns the sorted array.
```javascript
const arr = [3, 1, 4, 1, 5];
arr.sort((a, b) => a - b); // arr is now [1, 1, 3, 4, 5]
```

### `reverse()`
Reverses an array in place and returns the reversed array.
```javascript
const arr = [1, 2, 3];
arr.reverse(); // arr is now [3, 2, 1]
```

### `fill()`
Fills all elements of an array from start to end index with a static value.
```javascript
const arr = [1, 2, 3, 4];
arr.fill(0, 1, 3); // arr is now [1, 0, 0, 4]
```

### `copyWithin()`
Copies a sequence of array elements within the array to the position starting at target.
```javascript
const arr = [1, 2, 3, 4, 5];
arr.copyWithin(0, 3); // arr is now [4, 5, 3, 4, 5]
```

## Non-Mutating Methods (return new arrays or values)

### `concat()`
Returns a new array that is the result of merging two or more arrays.
```javascript
const arr1 = [1, 2];
const arr2 = [3, 4];
const merged = arr1.concat(arr2); // [1, 2, 3, 4]
```

### `slice()`
Returns a shallow copy of a portion of an array into a new array.
```javascript
const arr = [1, 2, 3, 4, 5];
const sliced = arr.slice(1, 4); // [2, 3, 4]
```

### `join()`
Joins all elements of an array into a string using a separator.
```javascript
const arr = ['Hello', 'World'];
const str = arr.join(' '); // "Hello World"
```

### `toString()`
Returns a string representing the array and its elements.
```javascript
const arr = [1, 2, 3];
const str = arr.toString(); // "1,2,3"
```

### `toLocaleString()`
Returns a string representing the array elements using locale-specific formatting.
```javascript
const arr = [1000, 2000, 3000];
const str = arr.toLocaleString(); // "1,000,2,000,3,000" (in US locale)
```

## Iteration Methods

### `forEach()`
Executes a provided function once for each array element.
```javascript
const arr = [1, 2, 3];
arr.forEach(item => console.log(item * 2)); // Prints: 2, 4, 6
```

### `map()`
Creates a new array with the results of calling a provided function on every element.
```javascript
const arr = [1, 2, 3];
const doubled = arr.map(x => x * 2); // [2, 4, 6]
```

### `filter()`
Creates a new array with all elements that pass a provided test function.
```javascript
const arr = [1, 2, 3, 4, 5];
const evens = arr.filter(x => x % 2 === 0); // [2, 4]
```

### `reduce()`
Executes a reducer function on each element, resulting in a single output value.
```javascript
const arr = [1, 2, 3, 4];
const sum = arr.reduce((acc, curr) => acc + curr, 0); // 10
```

### `reduceRight()`
Applies a function against an accumulator and each element (from right to left) to reduce to a single value.
```javascript
const arr = [1, 2, 3, 4];
const result = arr.reduceRight((acc, curr) => acc - curr, 10); // 0 (10-4-3-2-1)
```

### `find()`
Returns the first element in an array that satisfies a provided testing function.
```javascript
const arr = [1, 2, 3, 4, 5];
const found = arr.find(x => x > 3); // 4
```

### `findIndex()`
Returns the index of the first element that satisfies a provided testing function.
```javascript
const arr = [1, 2, 3, 4, 5];
const index = arr.findIndex(x => x > 3); // 3
```

### `findLast()`
Returns the last element in an array that satisfies a provided testing function.
```javascript
const arr = [1, 2, 3, 4, 5];
const found = arr.findLast(x => x > 3); // 5
```

### `findLastIndex()`
Returns the index of the last element that satisfies a provided testing function.
```javascript
const arr = [1, 2, 3, 4, 5];
const index = arr.findLastIndex(x => x > 3); // 4
```

## Search Methods

### `indexOf()`
Returns the first index at which a given element can be found, or -1 if not present.
```javascript
const arr = [1, 2, 3, 2, 1];
const index = arr.indexOf(2); // 1
```

### `lastIndexOf()`
Returns the last index at which a given element can be found, or -1 if not present.
```javascript
const arr = [1, 2, 3, 2, 1];
const index = arr.lastIndexOf(2); // 3
```

### `includes()`
Determines whether an array includes a certain value, returning true or false.
```javascript
const arr = [1, 2, 3];
const hasTwo = arr.includes(2); // true
```

## Test Methods

### `some()`
Tests whether at least one element in the array passes the provided function test.
```javascript
const arr = [1, 2, 3, 4, 5];
const hasEven = arr.some(x => x % 2 === 0); // true
```

### `every()`
Tests whether all elements in the array pass the provided function test.
```javascript
const arr = [2, 4, 6, 8];
const allEven = arr.every(x => x % 2 === 0); // true
```

## Advanced Methods

### `flat()`
Creates a new array with all sub-array elements concatenated into it recursively up to specified depth.
```javascript
const arr = [1, [2, 3], [4, [5, 6]]];
const flattened = arr.flat(2); // [1, 2, 3, 4, 5, 6]
```

### `flatMap()`
Maps each element using a mapping function, then flattens the result into a new array.
```javascript
const arr = [1, 2, 3];
const result = arr.flatMap(x => [x, x * 2]); // [1, 2, 2, 4, 3, 6]
```

### `entries()`
Returns a new Array Iterator object that contains key/value pairs for each index.
```javascript
const arr = ['a', 'b', 'c'];
for (const [index, value] of arr.entries()) {
  console.log(index, value); // 0 'a', 1 'b', 2 'c'
}
```

### `keys()`
Returns a new Array Iterator object that contains the keys for each index in the array.
```javascript
const arr = ['a', 'b', 'c'];
const keys = [...arr.keys()]; // [0, 1, 2]
```

### `values()`
Returns a new Array Iterator object that contains the values for each index in the array.
```javascript
const arr = ['a', 'b', 'c'];
const values = [...arr.values()]; // ['a', 'b', 'c']
```

## Static Methods

### `Array.from()`
Creates a new Array instance from an array-like or iterable object.
```javascript
const str = "hello";
const arr = Array.from(str); // ['h', 'e', 'l', 'l', 'o']
```

### `Array.of()`
Creates a new Array instance with a variable number of arguments.
```javascript
const arr = Array.of(1, 2, 3); // [1, 2, 3]
```

### `Array.isArray()`
Determines whether the passed value is an array.
```javascript
const result = Array.isArray([1, 2, 3]); // true
const result2 = Array.isArray("hello"); // false
```

## Newer Methods (ES2022+)

### `at()`
Returns the element at the specified index, allowing negative indices.
```javascript
const arr = [1, 2, 3, 4, 5];
const last = arr.at(-1); // 5
const first = arr.at(0); // 1
```

### `with()`
Returns a new array with the element at the given index replaced with the given value.
```javascript
const arr = [1, 2, 3, 4, 5];
const newArr = arr.with(2, 'three'); // [1, 2, 'three', 4, 5]
```

### `toReversed()`
Returns a new array with the elements in reversed order.
```javascript
const arr = [1, 2, 3];
const reversed = arr.toReversed(); // [3, 2, 1] (original arr unchanged)
```

### `toSorted()`
Returns a new array with the elements sorted.
```javascript
const arr = [3, 1, 4, 1, 5];
const sorted = arr.toSorted((a, b) => a - b); // [1, 1, 3, 4, 5] (original arr unchanged)
```

### `toSpliced()`
Returns a new array with some elements removed and/or replaced at a given index.
```javascript
const arr = [1, 2, 3, 4, 5];
const newArr = arr.toSpliced(2, 1, 'a', 'b'); // [1, 2, 'a', 'b', 4, 5] (original arr unchanged)
```
