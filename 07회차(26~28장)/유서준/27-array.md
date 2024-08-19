# Chapter 27: Arrays

---

## 1. Introduction to Arrays

- Arrays are ordered lists of values
- JavaScript arrays are not truly arrays but objects with special behaviors
- Arrays have a `length` property and numeric indices

---

## 2. Array Creation

1. Array Literal: `const arr = [1, 2, 3];`
2. Array Constructor: `const arr = new Array(1, 2, 3);`
3. Array.of(): `const arr = Array.of(1, 2, 3);`
4. Array.from(): Converts array-like objects or iterables to arrays

---

## 3. Accessing, Inserting, Updating, and Deleting Elements

### 3.1 Accessing Elements

- Bracket Notation: `arr[index]`

### 3.2 Deleting Elements

- Deleting: `delete arr[index]`

```javascript
const arr = [1, 2, 3];
delete arr[1];
console.log(arr); // [1, 1 empty item, 3]
```

### 3.3 Inserting Elements

- Adding: `arr[index] = value`
- If the index you're adding to is greater than the length of the array, the array will be padded with `undefined` values

```javascript
const arr = [1, 2, 3];
arr[5] = 6;
console.log(arr); // [1, 2, 3, undefined, undefined, 6]
```

### 3.4 Updating Elements

- Updating: `arr[index] = newValue`

```javascript
const arr = [1, 2, 3];
arr[1] = 4;
console.log(arr); // [1, 4, 3]
```

## 4. Array Methods

### 4.1 Mutator Methods (modify the original array)

- Array.prototype.`push()`: Adds elements to the end of an array

- Array.prototype.`pop()`: Removes the last element from an array

- Array.prototype.`unshift()`: Adds elements to the beginning of an array. Returns the new length of the array

```javascript
const arr = [1, 2, 3];
let result = arr.unshift(0);
console.log(result); // 4
console.log(arr); // [0, 1, 2, 3]
```

- Array.prototype.`shift()`: Removes the first element from an array. Returns the removed element

```javascript
const arr = [1, 2, 3];
let result = arr.shift();
console.log(result); // 1
console.log(arr); // [2, 3]
```

- Array.prototype.`splice()`: Adds or removes elements from an array. Returns the removed elements

```javascript
const arr = [1, 2, 3, 4, 5];
let result = arr.splice(1, 2, 6, 7); // Removes 2 elements starting from index 1 and adds 6 and 7
console.log(result); // [2, 3]
console.log(arr); // [1, 6, 7, 4, 5]
```

### 4.2 Accessor Methods (return a new value or array)

- Array.prototype.`slice()`: Returns a shallow copy of a portion of an array

```javascript
const arr = [1, 2, 3, 4, 5];
let result = arr.slice(1, 3); // Returns elements from index 1 to 2
console.log(result); // [2, 3]
console.log(arr); // [1, 2, 3, 4, 5] (original array is unchanged)
```

### 4.3 Iteration Methods

### 4.4 etc

- Array.`isArray()`: Checks if a value is an array

- Array.prototype.`indexOf()`: Returns the first index of an element

```javascript
// Check if the value is in the array
const arr = ["apple", "banana", "cherry"];
if (arr.indexOf("banana") !== -1) {
  console.log("Found");
} else {
  console.log("Not found");
}

// Using Array.prototype.includes() - ES7
if (arr.includes("banana")) {
  console.log("Found");
} else {
  console.log("Not found");
}

```
.... NOT FINISHED YET