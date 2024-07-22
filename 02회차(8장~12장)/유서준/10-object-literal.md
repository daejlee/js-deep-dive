# Chapter 10: Object Literals

---

## 1. What is Object?

- Object is a complex data structure that can store multiple values
- Everything in JavaScript is an object except primitive values
- Objects are collections of key-value pairs (properties)

---

## 2. Object Structure

- Properties: Key-value pairs representing object state
- Methods: Functions associated with an object, representing behavior

---

## 3. Creating Objects with Object Literals

- Simplest way to create an object
- Syntax: `const obj = { key1: value1, key2: value2 };`

---

## 4. Properties

- Can be any valid JavaScript value (primitives, functions, other objects)
- Keys are always strings. If the key is not following the rules of a valid identifier, it must be enclosed in quotes

```javascript
const obj = {
  'key with spaces': 'value',
  '123': 'value',
  'special-characters!': 'value'
};
```

- Properties can be accessed and modified using dot or bracket notation

```javascript
const obj = { key: 'value' };
console.log(obj.key); // value
console.log(obj['key']); // value
```

---

## 5. Methods

- Functions stored as object properties
- Defined using either traditional function syntax or ES6 method shorthand

```javascript
const obj = {
  method1: function() {
    console.log('Method 1');
  },
  method2() {
    console.log('Method 2');
  }
};
```

---

## 6. Property Access and Modification

- Dot notation: `obj.propertyName`
- Bracket notation: `obj['propertyName']`
- Can add new properties: `obj.newProp = value;`
- Can modify existing properties: `obj.existingProp = newValue;`

---

## 7. Deleting Properties

- Use `delete` operator: `delete obj.propertyName;`

```javascript
const obj = { key: 'value' };
delete obj.key;
delete obj.nonExistentKey; // No error
console.log(obj); // {}
```

---

## 8. ES6 Enhancements

1. Property Shorthand:
   - `const x = 1; const obj = { x };` equivalent to `{ x: x }`
2. Computed Property Names:
   - `const prop = 'foo'; const obj = { [prop]: 'bar' };`
3. Method Shorthand:
   - `const obj = { method() { ... } };` instead of `method: function() { ... }`

---

## 9. Object Property Characteristics

- Enumerable: Appears in for...in loops and Object.keys()
- Configurable: Can be deleted or have attributes modified
- Writable: Value can be changed

---

## 10. Best Practices

- Use `const` for object declarations to prevent reassignment
- Prefer object literal notation for creating objects
- Use meaningful property and method names
- Utilize ES6 enhancements for cleaner, more readable code
