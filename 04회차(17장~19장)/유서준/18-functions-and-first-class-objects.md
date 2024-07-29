# Chapter 18: Functions and First-Class Objects

---

## 1. Functions as First-Class Objects

In JavaScript, functions are first-class objects, which means:

1. Can be assigned to variables or properties
2. Can be passed as arguments to other functions
3. Can be returned from functions
4. Can be created dynamically

```javascript
// 1. Assigning to a variable
const foo = function() {};

// 2 & 3. Passing as argument and returning from a function
function bar(func) {
  return func();
}

// 4. Creating dynamically
const dynamicFunc = new Function('x', 'return x * x');
```

This allows for functional programming paradigms in JavaScript.

---

## 2. Function Object Properties

Functions, being objects, have their own properties. These can be viewed using `console.dir(functionName)`.

### 2.1 `arguments` Property

- Contains an array-like object of the arguments passed to the function
- Accessible within the function
- Allows for flexible argument handling

```javascript
function multiply(x, y) {
  console.log("Arguments: ", arguments);
  return x * y;
}

const result1 = multiply(1);
console.log("Result1: " + result1);

// Arguments:  [Arguments] { '0': 1 }
// Result1: NaN (1 * undefined)

const result2 = multiply(1, 2);
console.log("Result2: " + result2);

// Arguments:  [Arguments] { '0': 1, '1': 2 }
// Result2: 2

const result3 = multiply(1, 2, 3);
console.log("Result3: " + result3);
// Arguments:  [Arguments] { '0': 1, '1': 2, '2': 3 }
// Result3: 2 (ignores the extra argument)
```

### 2.2 `caller` Property (Non-standard)

- References the function that called the current function
- Not standardized and should be avoided

### 2.3 `length` Property

- Indicates the number of parameters expected by the function

```javascript
function foo(x, y) {}
console.log(foo.length); // 2
```

### 2.4 `name` Property

- Contains the function's name
- For anonymous functions, behavior differs between ES5 and ES6

```javascript
// Named function expression
const namedFunc = function foo() {};
console.log(namedFunc.name); // "foo"

// Anonymous function expression
const anonymousFunc = function() {};
console.log(anonymousFunc.name); // ES5: "", ES6: "anonymousFunc"
```

### 2.5 `__proto__` Accessor Property

- `__proto__` work as a getter/setter for the internal `[[Prototype]]` property

```javascript
function foo() {}
console.log(foo.__proto__ === Function.prototype); // true
```

### 2.6 prototype Property

- Only exists on constructor functions
- Points to the prototype object of instances created by the constructor

```javascript
function Foo() {}
console.log(Foo.hasOwnProperty('prototype')); // true

const obj = {};
console.log(obj.hasOwnProperty('prototype')); // false
```
