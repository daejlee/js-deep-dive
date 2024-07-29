Here's a study note for Chapter 19: Prototype, based on the content you provided:

# Chapter 19: Prototype

## 1. Object-Oriented Programming in JavaScript

- JavaScript supports object-oriented programming through prototype-based inheritance
- Objects have properties (data) and methods (behavior)
- Inheritance allows objects to share properties and methods

## 2. Inheritance and Prototype

- Prototype is used to implement inheritance in JavaScript
- It helps eliminate unnecessary duplication of code

```javascript
function Circle(radius) {
  this.radius = radius;
}

Circle.getArea = function () {
  return Math.PI * this.radius ** 2;
};

const circle1 = new Circle(1);
const circle2 = new Circle(2);

// same method is created for each instance
console.log(circle1.getArea() === circle2.getArea()); // false
```

```javascript
function Circle(radius) {
  this.radius = radius;
}

Circle.prototype.getArea = function () { // Add method to prototype
  return Math.PI * this.radius ** 2;
};

const circle1 = new Circle(1);
const circle2 = new Circle(2);

// method is shared between instances
console.log(circle1.getArea() === circle2.getArea()); // true
```

## 3. Prototype Object

... From here, I really can't understand what the book is trying to say. Fxxk it 🤪. I will just skip this part. However, I will try to figure out what is the best practice to use prototype in JavaScript.

## 4. Best Practice 👍

### 4.1 Use prototype to define methods for objects

Avoid defining methods directly on the object constructor. This will create a new method for each instance, which is unnecessary duplication as mentioned earlier.

```javascript
function Circle(radius) {
  this.radius = radius;
}

Circle.prototype.getArea = function () {
  return Math.PI * this.radius ** 2;
};
```

### 4.2 Use Object.create() for Inheritance

Use `Object.create()` to create objects with a specified prototype. Therefore, you can create objects that inherit properties and methods from a prototype object.

> Q: What is the difference between `Object.create()` and `new` keyword?

**Basic Mechanism:**

- Object.create(): Creates a new object with the specified prototype object and properties.
- new keyword: Creates a new instance of a constructor function or class.

**Prototype Chain:**

- Object.create(): Allows you to directly specify the prototype of the new object.
- new keyword: Sets the prototype based on the constructor function's prototype property.

**Constructor Invocation:**

- Object.create(): Does not invoke a constructor.
- new keyword: Invokes the constructor function.

**Property Initialization:**

- Object.create(): Properties can be defined in a second argument, but it's less common.
- new keyword: Properties are typically initialized inside the constructor function.

### 4.3 Avoid Modifying Built-in Prototypes

Avoid modifying built-in prototypes like `Array.prototype` or `Object.prototype` as it can lead to unexpected behavior and conflicts with other code.

```javascript
Array.prototype.shuffle = function () {
  // Custom method added to Array prototype
};
```

### 4.4 Use Classes for Cleaner Syntax

ES6 introduced class syntax for defining objects and inheritance which is a syntactic sugar 😋 over prototype-based inheritance.

Example using prototype:

```javascript
// Animal constructor
function Animal(name) {
  this.name = name;
}

// Add method to prototype
Animal.prototype.speak = function () {
  console.log(`${this.name} makes a sound.`);
};

// Dog constructor
function Dog(name) {
  // Call Animal constructor
  Animal.call(this, name);
}

// Set up inheritance(prototype chain)
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

// Override speak method for Dog
Dog.prototype.speak = function () {
  console.log(`${this.name} barks.`);
};

// Create Dog instance
const dog = new Dog('Buddy');
```

Example using class:

```javascript
// Animal class
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    console.log(`${this.name} makes a sound.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog('Buddy');
```
