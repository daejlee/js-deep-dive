# Chapter 11: Primitive Values vs Objects

---

## 1. Primitive Values

- **Definition**: Basic data types in JavaScript (number, string, boolean, null, undefined, symbol, bigint)
- **Characteristics**:
  - Immutable (cannot be changed after creation)
  - Stored directly in the variable's memory space
  - Compared by value
- **Memory**:
  - Fixed size, predictable memory usage
  - Stored on the stack for quick access

```javascript
let a = 5;
let b = a;
a = 10;
console.log(b); // Still 5, not affected by changing a
```

---

## 2. Objects

- **Definition**: Complex data structures that can hold multiple values
- **Characteristics**:
  - Mutable (can be modified after creation)
  - Stored by reference
  - Compared by reference, not by content
- **Memory**:
  - Dynamic size, more complex memory management
  - Reference stored on the stack, actual data on the heap

```javascript
let obj1 = {x: 10};
let obj2 = obj1;
obj1.x = 20;
console.log(obj2.x); // 20, affected by changing obj1
```

---

## 3. Value Passing

- **Primitives**:
  - Pass by value
  - A copy of the value is passed

- **Objects**:
  - Pass by reference
  - The reference to the object is passed

```javascript
function modifyPrimitive(val) {
  val = 10;
}

function modifyObject(obj) {
  obj.x = 20;
}

let a = 5;
let obj = {x: 10};

modifyPrimitive(a);
modifyObject(obj);

console.log(a); // 5, not affected by modifyPrimitive

console.log(obj.x); // 20, affected by modifyObject
```

---

## 4. Variable Assignment

- **Primitives**:
  - Direct value assignment
  - `let a = 5;` assigns the value 5 directly to `a`

- **Objects**:
  - Reference assignment
  - `let obj = {x: 5};` assigns the reference to the object to `obj`

```javascript
let a = 5;
let b = a; // b is a copy of the value 5

let obj1 = {x: 10};
let obj2 = obj1; // obj2 refers to the same object as obj1
```

---

## 5. Copying

- **Primitives**:
  - Deep copy by default
  - `let b = a;` creates a new, independent copy of the value

- **Objects**:
  - Shallow copy by default
  - Deep copy requires special methods (e.g., `JSON.parse(JSON.stringify(obj))` or libraries like Lodash)

```javascript
let obj1 = {x: 10};
let obj2 = obj1; // Shallow copy, obj2 refers to the same object

let obj3 = JSON.parse(JSON.stringify(obj1)); // Deep copy
```

---

## 6. Performance Considerations

- Objects offer flexibility but at a cost of performance in some cases
- Creating and modifying objects is generally more expensive than working with primitives

---

## 7. Immutability of Strings

- Despite being primitive, strings behave like objects in some ways
- String methods always return new strings, never modify the original

---

## 8. Object Mutability

- Can add, modify, or delete properties without reassignment
- Allows for dynamic changes to object structure

```javascript
let person = {name: "Alice"};
person.age = 30; // Adding a new property
delete person.name; // Deleting a property
```

---

## 9. Reference Sharing

- Multiple variables can refer to the same object
- Changes through one variable affect all references

```javascript
let arr1 = [1, 2, 3];
let arr2 = arr1;
arr1.push(4);
console.log(arr2); // [1, 2, 3, 4]
```

---

## 10. Best Practices

1. Be aware of the differences when working with primitives vs objects
2. Use const for objects to prevent reassignment (but not to prevent mutation)
3. Be cautious when passing objects to functions, as they can be modified
4. Consider using immutable data patterns for more predictable code
