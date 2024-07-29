# Chapter 17: Object Creation by Constructor Function

---

## 1. Object Constructor Function

- Use `new` operator with `Object` constructor function to create an empty object
- Properties and methods can be added to the object after creation

```javascript
const person = new Object(); // person here is called an instance of Object
person.name = 'Lee';
person.sayHello = function () {
  console.log('Hi! My name is ' + this.name);
};
```

Javascript provides built-in constructor functions for creating objects of various types:
`Object()`, `String()`, `Number()`, `Boolean()`, `Function()`, `Array()`, `RegExp()`, `Date()`, `Error()`.
These functions can be used to create objects of their respective types.

---

## 2. Constructor Functions

### 2.1 Problems with Object Literal Creation

- Inefficient for creating multiple objects with the same structure
- Requires repeating the same code for each object

### 2.2 Advantages of Constructor Functions

- Acts as a template for creating objects with the same structure
- More efficient for creating multiple objects

```javascript
function Circle(radius) {
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

const circle1 = new Circle(5);
const circle2 = new Circle(10);
```

### 2.3 Instance Creation Process

1. Create an instance and bind it to `this`
   - **Binding** is a process of associating an identifier with a value
2. Add properties and methods to `this`
3. Implicitly return `this` (the created instance)

```javascript
function Circle(radius) {
  // 1. Create an instance and bind it to `this`
  this.radius = radius; // 2.1 add properties to `this`
  this.getDiameter = function () { // 2.2 add methods to `this`
    return 2 * this.radius;
  };
  // 3. Implicitly return `this`
  // - if an object is returned explicitly, it will override `this`
  // - if an primitive value is returned, it will be ignored and `this` will be returned
}
```

### 2.4 Internal Methods [[Call]] and [[Construct]]

- Functions have [[Call]] for normal invocation
- Constructor functions also have [[Construct]] for use with `new` operator

```JavaScript
function foo() {}
foo(); // [[Call]] method is invoked
new foo(); // [[Construct]] method is invoked
```

### 2.5 Constructor vs Non-constructor

- Constructors: Function declarations, function expressions, classes
- Non-constructors: ES6 method shorthand, arrow functions

### 2.6 The `new` Operator

- Makes a function behave as a constructor
- Calls [[Construct]] instead of [[Call]]
- Function which is called with `new` is called a constructor function

```javascript
function Circle(radius) {
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

const circle = Circle(5); // Without `new`, `this` is the global object
console.log(circle); // undefined
console.log(radius); // 5 -> because `this` is the global object
```

### 2.7 new.target

- Used to detect if a function was called with `new`
- Undefined when called without `new`
- Can be used to ensure constructor behavior:

```javascript
function Circle(radius) {
  if (!new.target) {
    return new Circle(radius);
  }
  this.radius = radius;
}
```
