# Chapter 26: ES6 Function Additional Features

---

## 1. Function Classification

- ES6 introduced clear distinctions between functions based on their purpose
- Now there are three types of function: Normal functions, Methods, Arrow functions

---

## 2. Methods

- ES6 method: Function defined using method shorthand notation in object literals
- Characteristics:
  - Non-constructor (can't be used with `new`)
  - No `prototype` property
  - Can use `super` keyword
  - Has `[[HomeObject]]` internal slot

---

## 3. Arrow Functions

### 3.1 Syntax

- Uses `=>` instead of `function` keyword
- Concise body for single expressions: `(x, y) => x + y`
- Block body for multiple statements: `(x, y) => { statements }`

### 3.2 Differences from Regular Functions

- Non-constructor (can't be used with `new`)
- No `prototype` property
- Can't have duplicate parameter names (even in non-strict mode)
- No `this`, `arguments`, `super`, or `new.target` bindings

### 3.3 Lexical `this`

- Inherits `this` from the surrounding scope
- Solves the common "callback function `this`" problem
- Particularly useful in methods that use callbacks (e.g., `Array.prototype.map`)

### 3.4 Notes on Usage

- Avoid using arrow functions for methods that need their own `this` context
- Ideal for callback functions and short, functional-style operations

---

## 4. Rest Parameters

- Syntax: `...paramName` as the last parameter
- Collects all remaining arguments into an array
- Replaces the need for the `arguments` object in many cases
- Can be used with arrow functions (unlike `arguments`)

```javascript
function sum(...args) {
  return args.reduce((acc, val) => acc + val, 0);
}

console.log(sum(1, 2, 3)); // 6
```

---

## 5. Default Parameters

- Syntax: `function fn(param1 = defaultValue1, param2 = defaultValue2) {}`
- Provides default values for parameters if not provided or `undefined`
- Simplifies parameter initialization and removes the need for manual checks

```javascript
function greet(name = 'World') {
  return `Hello, ${name}!`;
}

console.log(greet()); // Hello, World!
console.log(greet('Alice')); // Hello, Alice!
```

---

## 6. Summary

1. Use ES6 method syntax for object methods when possible
2. Arrow functions are great for callbacks and short operations, but be cautious with `this`
3. Rest parameters provide a cleaner way to handle variable-length argument lists
4. Default parameters simplify function definitions and improve readability
