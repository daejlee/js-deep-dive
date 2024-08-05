# Chapter 22: This

## 1. Introduction to 'this' Keyword

- 'this' is a special identifier that's automatically created by JavaScript
- It refers to the object that is currently executing the code
- Allows methods to access and manipulate the object's properties

## 2. 'this' Binding

- The value of 'this' is determined by how a function is called (runtime binding)
- Different from lexical scope, which is determined at function creation time

## 3. Function Invocation Patterns and 'this' Binding

### 3.1 Global Function Invocation

- In non-strict mode: 'this' refers to the global object (window in browsers)
- In strict mode: 'this' is undefined

```javascript
// when this is called in global scope
console.log(this); // window
// refers to the global object (window in browsers)
```

### 3.2 Method Invocation

- 'this' refers to the object that owns the method

```javascript

// when this is called inside a method
const person = {
  name: 'Alice',
  greet() {
    console.log(this); // {name: "Alice", greet: ƒ}
    // in this case, 'this' refers to person
  }
};

person.greet(); // Alice
```

### 3.3 Constructor Function Invocation

- When used with 'new' keyword, 'this' refers to the newly created instance

```javascript

// when this is called inside a constructor
function Person(name) {
  this.name = name;
  console.log(this); // Person {name: "Alice"}
  // in this case, 'this' refers to the newly created instance
}

const alice = new Person('Alice');

```

### 3.4 Indirect Invocation (apply, call, bind methods)

> Q: what is apply, call, bind methods?
> A: These are the methods that allow you to call a function with a specific 'this' value.

- `apply` - Accepts an array of arguments
- `call` - Accepts a list of arguments
- `bind`
  - Returns a new function with the specified 'this' value

- Allows explicit setting of 'this' value

```javascript
function greet() {
  console.log(this.name);
}

const person = { name: 'Alice' };

greet.call(person); // Alice
greet.apply(person); // Alice

const greetPerson = greet.bind(person);
greetPerson(); // Alice
```

## Summary

- `this` is an identifier which refers to the object that is currently executing the code.
- The value of `this` is determined by how a function is called (runtime binding). So be careful when using it.
