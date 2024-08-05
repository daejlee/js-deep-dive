# Chapter 21: Built-in Objects

---

## 1. Classification of JavaScript Objects

JavaScript objects can be classified into three categories:

- Standard built-in objects
- Host objects
- User-defined objects

---

## 2. Standard Built-in Objects

- Defined in ECMAScript specification
- Provide common functionality across all JavaScript environments (browsers, Node.js, etc.)
- Available as properties of the global object which means they can be accessed directly
- There are about 40 standard built-in objects. They are constructor function object types(except Math, Reflect and JSON)

```javascript
const strObj = new String('hello'); // Creating a String object using the constructor
```

---

## 3. Primitive Values and Wrapper Objects

- Primitive values (strings, numbers, booleans) can behave like objects
- JavaScript engine temporarily converts primitives to their corresponding wrapper objects
- Wrapper objects: String, Number, Boolean
- Allow method calls on primitive values
- `null` and `undefined` do not have wrapper objects

```javascript
const str = 'hello'; // Here, the identifier str is a primitive value

console.log(str.length); // JS Engine converts str to a String object temporarily
// Temporary object is destroyed(Garbage Collection) after the method call
console.log(typeof str, str); // identifier str is still a primitive value (string hello)
```

---

## 4. Global Object

- Created before code execution
- Serves as the ultimate parent for all objects
- Browser: `window` (or `self`, `this`, `frames`)
- Node.js: `global`
- ECMAScript 2020: `globalThis` (unified identifier)

```javascript
const bla = globalThis.String('My codes are awesome!'); // globalThis is a global object
console.log(bla); // My codes are awesome!
```

### 4.1 Built-in Global Properties

- `Infinity`

```javascript
console.log(3/0); // Infinity
console.log(-3/0); // -Infinity
console.log(typeof Infinity); // number
```

- `NaN`

```javascript
console.log(Number('abc')); // NaN
console.log(1 * "blabla"); // NaN
console.log(typeof NaN); // number
```

- `undefined`

```javascript
let x;
console.log(x); // undefined
```

### 4.2 Built-in Global Functions

- `eval()`

```javascript
const x = 1;
const y = 2;
const result = eval('x + y'); // Evaluates the string as JavaScript code
console.log(result); // 3
```

> personal note: The person who uses `eval()` should go to hell.

- `isFinite()` : Returns `true` if the argument is a finite number, `false` otherwise
- `isNaN()` : Returns `true` if the argument is `NaN`, `false` otherwise
- `parseFloat()` : Parses a string argument and returns a floating-point number
- `parseInt()`: Parses a string argument and returns an integer

Check when to use these functions

- `encodeURI()` / `decodeURI()`
- `encodeURIComponent()` / `decodeURIComponent()`

### 4.3 Implicit Globals

- Assigning to an undeclared variable creates a property on the global object
- Not true variables (no hoisting)
- Can be deleted with `delete` operator

```javascript
function foo() {
  y = 20; // Implicitly creates window.y
}
foo();
console.log(y); // 20
```

---

## Summary

- JavaScript objects can be classified into standard built-in objects, host objects, and user-defined objects.
- Lets use `globalThis` instead of `window` or `global` to access the global object.
- There are some useful global objects and functions available in JavaScript. Check it out.
