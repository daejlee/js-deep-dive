# Chapter 16: Property Attributes

---

## 1. Internal Slots and Methods

- Concept: Implementation-level entities in JavaScript engines
- Not directly accessible by developers
- Some can be indirectly accessed (e.g., `[[Prototype]]` via `__proto__`)

```javascript
const obj = {};
console.log(obj.__proto__ === Object.prototype); // true
```

---

## 2. Property Attributes and Property Descriptor Objects

- Property attributes: Metadata about object properties
- Automatically defined by JavaScript engine when creating properties
- Accessible via `Object.getOwnPropertyDescriptor()` method

```javascript
const obj = { a: 1 };
console.log(Object.getOwnPropertyDescriptor(obj, 'a'));
// { value: 1, writable: true, enumerable: true, configurable: true }
```

---

## 3. Data Properties vs Accessor Properties

### 3.1 Data Properties

- Have four attributes:
  - `[[Value]]`: The property's value
  - `[[Writable]]`: If the value can be changed
  - `[[Enumerable]]`: If the property appears in for...in loops
  - `[[Configurable]]`: If the property can be deleted or its attributes modified

### 3.2 Accessor Properties

- Don't store a value directly
- Have four attributes:
  - `[[Get]]`: Function called when property is read
  - `[[Set]]`: Function called when property is assigned a value
  - `[[Enumerable]]`: Same as data properties
  - `[[Configurable]]`: Same as data properties

```javascript
// Using accessor properties for data validation
const user = {
  _age: 0,
  get age() { return this._age; },
  set age(value) {
    if (typeof value !== 'number' || value < 0 || value > 120) {
      throw new Error('Invalid age');
    }
    this._age = value;
  }
};

user.age = 25;
console.log(user.age); // 25
// user.age = 150; // Throws Error: Invalid age

```

---

## 4. Property Definition

- Use `Object.defineProperty()` to define or modify property attributes
- `Object.defineProperties()` for defining multiple properties at once

```javascript
const obj = {};

Object.defineProperty(obj, 'a', {
  value: 1,
  writable: false,
  enumerable: true,
  configurable: false
});

Object.defineProperties(obj, {
  b: { value: 2, writable: true }, // defining data property
  c: { get() { return this.b * 2; } } // defining accessor property
});

console.log(Object.getOwnPropertyDescriptor(obj, 'a')); // { value: 1, writable: false, enumerable: true, configurable: false }
console.log(Object.getOwnPropertyDescriptor(obj, 'b')); // { value: 2, writable: true, enumerable: false, configurable: false }
console.log(Object.getOwnPropertyDescriptor(obj, 'c')); // { get: [Function: get], set: undefined, enumerable: false, configurable: false }
```

```javascript
// Using property attributes for full name
const person = {};

Object.defineProperties(person, {
  firstName: {
    value: 'John',
    writable: true,
    enumerable: true,
    configurable: true
  },
  lastName: {
    value: 'Doe',
    writable: true,
    enumerable: true,
    configurable: true
  },
  fullName: {
    get() {
      return `${this.firstName} ${this.lastName}`;
    },
    set(value) {
      const parts = value.split(' ');
      this.firstName = parts[0];
      this.lastName = parts[1];
    },
    enumerable: true,
    configurable: true
  }
});

console.log(person.fullName); // John Doe
person.fullName = 'Jane Smith';
console.log(person.fullName); // Jane Smith
console.log(person.firstName); // Jane
console.log(person.lastName); // Smith
```

---

## 5. Object Change Prevention

| method                       | adding properties | deleting properties | reading property value | writing property value | redefining property attributes |
| ---------------------------- | ----------------- | ------------------- | ---------------------- | ---------------------- | ------------------------------ |
| `Object.preventExtensions()` | ❌                 | ✅                   | ✅                      | ✅                      | ✅                              |
| `Object.seal()`              | ❌                 | ❌                   | ✅                      | ✅                      | ❌                              |
| `Object.freeze()`            | ❌                 | ❌                   | ✅                      | ❌                      | ❌                              |

### 5.1 Object Extension Prevention

- `Object.preventExtensions()`: Prevents adding new properties
- Check with `Object.isExtensible()`

### 5.2 Object Sealing

- `Object.seal()`: Prevents adding/deleting properties and redefining attributes
- Check with `Object.isSealed()`

### 5.3 Object Freezing

- `Object.freeze()`: Prevents all modifications (adding, deleting, writing, redefining)
- Check with `Object.isFrozen()`
- But it doesn't prevent nested objects from being modified

```javascript
const config = {
  apiKey: 'abc123',
  maxRetries: 3,
  timeout: 5000
  nested: {
    prop: 1
  }
};

Object.freeze(config);

// In strict mode, these would throw errors
config.apiKey = 'xyz789'; // No effect
delete config.maxRetries; // No effect
Object.defineProperty(config, 'newProp', { value: true }); // Throws TypeError
config.nested.prop = 2; // Works

console.log(config);
// Still { apiKey: 'abc123', maxRetries: 3, timeout: 5000, nested: { prop: 2 } }
```

### 5.4 Deep Freezing

- Recursive freezing for nested objects to create truly immutable objects

```javascript
function deepFreeze(obj) {
  // skip non-objects and already frozen objects
  if (obj === null || typeof obj !== 'object' || Object.isFrozen(obj)) {
    return;
  }

  // Freeze the object itself
  Object.freeze(obj);

  // Recursively freeze nested objects
  Object.getOwnPropertyNames(obj).forEach(prop => deepFreeze(obj[prop]));

  // Return the frozen object
  return obj;
}

const person = {
  name: 'John',
  address: {
    city: 'New York',
    country: 'USA'
  }
};

deepFreeze(person);

// In strict mode, these would throw errors
person.name = 'Jane'; // No effect
person.address.city = 'Los Angeles'; // No effect
```

---

## 6. Best Practices

- Use property attributes to control object behavior
- Consider object change prevention methods for data integrity
- Be aware of shallow vs deep prevention when dealing with nested objects
- Use strict mode to catch silent failures in object modifications
