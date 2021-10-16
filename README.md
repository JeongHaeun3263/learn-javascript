# JavaScript

## Basic

### Type of Data

- Number
- String
  [String Methods Cheat Sheet](https://www.notion.so/b511826f7ef948089e11c0f0e7ac7491?v=7eb505cec57f42519e36a3a2f0a048ae)

- Boolean
- Undefined
- Null
- Symbol
- Object

### Operator

- Arithmetic
  - binary +, -, \*, /, %
  - unary ++, —, +, -
- Assignment: =, +=, -=, \*=, /=, %=
- Comparison: ==, ===, !=, !==, <, <, >=, <=
- Ternary Operator
  ```javascript
  let result = score >= 60 ? 'pass' : 'fail';
  ```
- Logical: ||, &&, !
- Comma
- Grouping
- typeof
- Exponentiation (ES7)
  ```javascript
  console.log(3 ** 2); // 9
  ```
- more... (?., ??, delete, new, instanceof, in)

### Type conversion

1. Explicit
2. Implicit conversion (Type coercion)

### Functions

1. Function declaration

```javascript
function printHello() {
	console.log('Hello');
}
printHello();

function log(message) {
	console.log(message);
}
log('Hello@');
log(1234);
```

2. Parameters

- premitive parameters: passed by value
- object parameters: passed by reference

```javascript
function changeName(obj) {
	obj.name = 'grace';
	obj.isMarried = true;
}

const haeun = { name: 'haeun', age: 20 };
changeName(haeun);
console.log(haeun);
```

3. Default parameters (added in ES6)

```javascript
function showMessage(message, from = 'unknown') {
	console.log(`${message} by ${from}`);
}
showMessage('Hi!'); // result: Hi! by unknown
showMessage('Hello', 'Grace'); // result: Hello by Grace
```

4. Rest parameters (added in ES6)

```javascript
function printAll(...args) {
	console.log(args); // ['Hello', 'World', 'Grace']
	// 1
	for (let i = 0; i < args.length; i++) {
		console.log(1, args[i]);
	}

	// 2
	for (const arg of args) {
		console.log(2, arg);
	}

	// 3
	args.forEach((arg) => console.log(3, arg));
}
printAll('Hello', 'World', 'Grace');
```

5. Local scope

```javascript
let globalMessage = 'global'; // global variable
function printMessage() {
	let message = 'local'; // local variable
	console.log(message); // result: local
	console.log(globalMessage); // result: global
	function printAnother() {
		console.log(message); // result: undefined
		let childMessage = 'hello';
	}
	// console.log(childMessage); //error: Uncaught ReferenceError: childMessage is not defined
}
printMessage();
```

6. Return a value

```javascript
function sum(a, b) {
	return a + b;
}
const result = sum(1, 2); // 3
console.log(`sum: ${sum(1, 2)}`);
```

7. Early return, early exit

```javascript
// bad
function upgradeUser(user) {
	if (user.point > 10) {
		// long upgrade logic...
	}
}

// good
function upgradeUser(user) {
	if (user.point <= 10) {
		return;
	}
	// long upgrade logic...
}
```

### First-class function

- functions are treated like any other variable
- can be assigned as a value to variable
- can be passed as an argument to other functions.
- can be returned by another function

1. Function expression

- a function declaration can be called earlier than it is defiend. (hoisted)
- a function expression is created when the execution reaches it.

```javascript
// example 1
const print = function () {
	// anonymous function
	console.log('hello world');
};
print();

const printAgain = print;
printAgain();

// example 2
function sum(a, b) {
	return a + b;
}

const sumAgain = sum;
console.log(sumAgain(1, 3));
```

2. Callback function using function expression

```javascript
function squidGame(answer, printYes, printNo) {
	if (answer === 'green light') {
		printGo();
	} else {
		printStop();
	}
}
// anonymous function
const printGo = function () {
	console.log('You can go!');
};

// named function
// better debugging in debugger's stack traces
// recursions
const printStop = function print() {
	console.log('You have to stop!');
};
squidGame('green light', printGo, printStop); // result: You can go!
squidGame('dance', printGo, printStop); // result: You have to stop!
```

3. Arrow function

```javascript
// always anonymous
// const simplePrint = function () {
//   console.log('simplePrint!');
// };

const simplePrint = () => console.log('simplePrint!');
const add = (a, b) => a + b;
const simpleMultiply = (a, b) => {
	// do something more
	return a * b;
};

// IIFE: Immediately Invoked Function Expression
(function hello() {
	console.log('IIFE');
})();
```

### Data Structures

#### Arrays

#### Objects

collections of properties and methods

- [Array Methods Cheat Sheet](https://www.notion.so/81628d655d734671ba195a5283089b84?v=a276134512f445f4892725d7ce8ba0c4)

## 🔗 Useful Websites

- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [The Modern JavaScript Tutorial](https://javascript.info/)
