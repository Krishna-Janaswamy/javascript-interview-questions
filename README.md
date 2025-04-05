# JavaScript Core Topics - Top 30 Questions and Answers

This document covers the top 30 core JavaScript questions and answers to help you understand and master JavaScript.

## Topics Covered

1. Variables and Data Types
2. Functions
3. Scope and Closures
4. Objects and Arrays
5. Prototypes and Inheritance
6. Asynchronous JavaScript (Promises, Async/Await)
7. Error Handling
8. ES6+ Features

---

## 1. Variables and Data Types

### Question 1: What are the different types of variables in JavaScript?

**Answer:**
JavaScript has three types of variables:
- `var`: Function scoped variable.
- `let`: Block scoped variable (introduced in ES6).
- `const`: Block scoped constant (introduced in ES6).

### Question 2: What are the different data types in JavaScript?

**Answer:**
JavaScript has the following data types:
- Primitive Types: `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`
- Reference Types: `object`, `array`, `function`

### Question 3: How do you check the type of a variable in JavaScript?

**Answer:**
You can use the `typeof` operator to check the type of a variable.

```javascript
let name = "John";
console.log(typeof name); // Output: "string"
```

---

## 2. Functions

### Question 4: How do you define a function in JavaScript?

**Answer:**
You can define a function in JavaScript using function declaration or function expression.

**Function Declaration:**
```javascript
function greet(name) {
  return `Hello, ${name}!`;
}
```

**Function Expression:**
```javascript
const greet = function(name) {
  return `Hello, ${name}!`;
};
```

### Question 5: What are arrow functions?

**Answer:**
Arrow functions are a concise syntax for writing function expressions. They do not have their own `this` context.

```javascript
const greet = (name) => `Hello, ${name}!`;
```

### Question 6: What is a higher-order function?

**Answer:**
A higher-order function is a function that takes another function as an argument or returns a function as a result.

```javascript
function higherOrderFunction(callback) {
  return callback();
}
```

---

## 3. Scope and Closures

### Question 7: What is the difference between global scope and local scope?

**Answer:**
- Global Scope: Variables declared outside any function or block are in the global scope and can be accessed from anywhere in the code.
- Local Scope: Variables declared inside a function or block are in the local scope and can only be accessed within that function or block.

### Question 8: What is a closure in JavaScript?

**Answer:**
A closure is a function that has access to its own scope, the scope of the outer function, and the global scope. It allows a function to access variables from an enclosing scope even after the outer function has finished executing.

```javascript
function outerFunction() {
  const outerVariable = 'I am outside!';

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

const closureFunction = outerFunction();
closureFunction(); // Output: I am outside!
```

---

## 4. Objects and Arrays

### Question 9: How do you create an object in JavaScript?

**Answer:**
You can create an object using object literal syntax or the `new Object()` syntax.

**Object Literal Syntax:**
```javascript
const person = {
  name: 'John',
  age: 30
};
```

**Using `new Object()`:**
```javascript
const person = new Object();
person.name = 'John';
person.age = 30;
```

### Question 10: How do you create an array in JavaScript?

**Answer:**
You can create an array using array literal syntax or the `new Array()` syntax.

**Array Literal Syntax:**
```javascript
const numbers = [1, 2, 3, 4, 5];
```

**Using `new Array()`:**
```javascript
const numbers = new Array(1, 2, 3, 4, 5);
```

### Question 11: How do you access properties of an object?

**Answer:**
You can access properties of an object using dot notation or bracket notation.

```javascript
const person = { name: 'John', age: 30 };
console.log(person.name); // Output: "John"
console.log(person['age']); // Output: 30
```

### Question 12: How do you iterate over an array?

**Answer:**
You can iterate over an array using a `for` loop, `forEach` method, `for...of` loop, or other array methods like `map`, `filter`, etc.

```javascript
const numbers = [1, 2, 3, 4, 5];

// Using a for loop
for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
}

// Using forEach method
numbers.forEach(number => {
  console.log(number);
});

// Using for...of loop
for (const number of numbers) {
  console.log(number);
}
```

---

## 5. Prototypes and Inheritance

### Question 13: What is a prototype in JavaScript?

**Answer:**
A prototype is an object from which other objects inherit properties and methods. Every JavaScript object has a prototype, and you can add properties and methods to an object’s prototype to be shared among all instances of that object.

### Question 14: How do you implement inheritance in JavaScript?

**Answer:**
You can implement inheritance in JavaScript using prototypes or the `class` syntax (introduced in ES6).

**Using Prototypes:**
```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

function Student(name, age, grade) {
  Person.call(this, name, age);
  this.grade = grade;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

const student = new Student('Alice', 20, 'A');
student.greet(); // Output: Hello, my name is Alice
```

**Using `class` Syntax:**
```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}`);
  }
}

class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }
}

const student = new Student('Alice', 20, 'A');
student.greet(); // Output: Hello, my name is Alice
```

---

## 6. Asynchronous JavaScript (Promises, Async/Await)

### Question 15: What are promises in JavaScript?

**Answer:**
Promises are objects that represent the eventual completion (or failure) of an asynchronous operation and its resulting value. They have three states: `pending`, `fulfilled`, and `rejected`.

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Promise resolved!');
  }, 1000);
});

myPromise.then((result) => {
  console.log(result); // Output: Promise resolved!
}).catch((error) => {
  console.error(error);
});
```

### Question 16: What is `async/await` in JavaScript?

**Answer:**
`async/await` is syntactic sugar built on top of promises to make asynchronous code look and behave more like synchronous code. The `async` keyword is used to define an asynchronous function, and the `await` keyword is used to wait for a promise to resolve.

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

fetchData();
```

### Question 17: How do you handle multiple promises?

**Answer:**
You can handle multiple promises using `Promise.all` or `Promise.race`.

**Using `Promise.all`:**
```javascript
const promise1 = Promise.resolve(1);
const promise2 = Promise.resolve(2);
const promise3 = Promise.resolve(3);

Promise.all([promise1, promise2, promise3]).then((values) => {
  console.log(values); // Output: [1, 2, 3]
});
```

**Using `Promise.race`:**
```javascript
const promise1 = new Promise((resolve) => setTimeout(resolve, 500, 'one'));
const promise2 = new Promise((resolve) => setTimeout(resolve, 100, 'two'));

Promise.race([promise1, promise2]).then((value) => {
  console.log(value); // Output: "two"
});
```

---

## 7. Error Handling

### Question 18: How do you handle errors in JavaScript?

**Answer:**
You can handle errors in JavaScript using `try...catch` blocks.

```javascript
try {
  // Code that may throw an error
  throw new Error('Something went wrong!');
} catch (error) {
  // Handle the error
  console.error(error.message);
} finally {
  // Code that will always run, regardless of whether an error occurred or not
  console.log('This will always run.');
}
```

### Question 19: How do you handle errors in asynchronous code?

**Answer:**
You can handle errors in asynchronous code using `catch` method for promises and `try...catch` blocks for `async/await`.

**Using Promises:**
```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .catch(error => {
    console.error('Error:', error);
  });
```

**Using `async/await`:**
```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}

fetchData();
```

---

## 8. ES6+ Features

### Question 20: What are some new features introduced in ES6?

**Answer:**
Some new features introduced in ES6 include:
- Arrow functions
- Classes
- Template literals
- Destructuring assignment
- Default parameters
- Rest and spread operators
- Let and const
- Promises
- Modules (import/export)

### Question 21: What is destructuring assignment?

**Answer:**
Destructuring assignment is a syntax that allows you to unpack values from arrays or properties from objects into distinct variables.

**Example with Arrays:**
```javascript
const [a, b] = [1, 2];
console.log(a); // Output: 1
console.log(b); // Output: 2
```

**Example with Objects:**
```javascript
const person = { name: 'John', age: 30 };
const { name, age } = person;
console.log(name); // Output: John
console.log(age); // Output: 30
```

### Question 22: What are template literals?

**Answer:**
Template literals are string literals that allow embedded expressions. They are enclosed by backticks (`) instead of single or double quotes.

```javascript
const name = 'John';
const message = `Hello, ${name}!`;
console.log(message); // Output: Hello, John!
```

### Question 23: What are the rest and spread operators?

**Answer:**
The rest operator (`...`) allows you to represent an indefinite number of arguments as an array. The spread operator (`...`) allows you to expand an array or object into individual elements.

**Rest Operator:**
```javascript
function sum(...numbers) {
  return numbers.reduce((total, number) => total + number, 0);
}

console.log(sum(1, 2, 3, 4)); // Output: 10
```

**Spread Operator:**
```javascript
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5, 6];
console.log(arr2); // Output: [1, 2, 3, 4, 5, 6]

const obj1 = { a: 1, b: 2 };
const obj2 = { ...obj1, c: 3 };
console.log(obj2); // Output: { a: 1, b: 2, c: 3 }
```

### Question 24: What are default parameters in JavaScript?

**Answer:**
Default parameters allow you to specify default values for function parameters if no arguments are passed or if `undefined` is passed.

```javascript
function greet(name = 'Guest') {
  return `Hello, ${name}!`;
}

console.log(greet()); // Output: Hello, Guest!
console.log(greet('John')); // Output: Hello, John!
```

### Question 25: What is the difference between `let`, `const`, and `var`?

**Answer:**
- `var`: Function scoped. Can be redeclared and updated.
- `let`: Block scoped. Cannot be redeclared but can be updated.
- `const`: Block scoped. Cannot be redeclared or updated.

---

## 9. Miscellaneous

### Question 26: What is the event loop in JavaScript?

**Answer:**
The event loop is a mechanism in JavaScript that allows non-blocking I/O operations by offloading operations to the system kernel whenever possible. It continuously checks the message queue and processes any pending messages (callbacks) in the order they were added.

### Question 27: What is the difference between `==` and `===`?

**Answer:**
- `==`: Loose equality operator. Compares values for equality after performing type conversion.
- `===`: Strict equality operator. Compares values for equality without performing type conversion.

```javascript
console.log(1 == '1'); // Output: true
console.log(1 === '1'); // Output: false
```

### Question 28: What is the difference between `null` and `undefined`?

**Answer:**
- `null`: Explicitly represents the absence of a value.
- `undefined`: Represents a variable that has been declared but not yet assigned a value.

### Question 29: What is hoisting in JavaScript?

**Answer:**
Hoisting is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase. Only the declarations are hoisted, not the initializations.

```javascript
console.log(x); // Output: undefined
var x = 5;
```

### Question 30: What is the `this` keyword in JavaScript?

**Answer:**
The `this` keyword refers to the object it belongs to. It has different values depending on where it is used:
- In a method, `this` refers to the owner object.
- Alone, `this` refers to the global object.
- In a function, `this` refers to the global object (in non-strict mode) or `undefined` (in strict mode).
- In an event, `this` refers to the element that received the event.
- In arrow functions, `this` retains the value of the enclosing lexical context.

```javascript
const obj = {
  name: 'John',
  greet: function() {
    console.log(this.name);
  }
};

obj.greet(); // Output: John
```
