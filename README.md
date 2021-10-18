# JavaScript

## Basic

### Terminology

1. Function declaration

```javascript
function myFunction() {}
```

2. Function expression

```javascript
const myFunction = function () {};

const newFunction = () => {};
```

3. Expression

- expression is something that produces a value.

```javascript
1 + 3;
let a = 2;
return true;
```

4. Calling or invoking a function

```javascript
myFunction();
myFunction(param1, param2);
```

5. Assign a variable

```javascript
let age = 20;
```

6. Function VS Methods

```javascript
function thisIsFunction() {}

const obj = {
	thisIsMethod: function () {},
};

// how to access
thisIsFunction();
obj.thisIsMethod();
```

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

- always anonymous

```javascript
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

### Loops

1. For Loop

```javascript
const friends = ['Monica', 'Rachel', 'Phoebe', 'Chandler', 'Ross', 'Joey'];

for (let i = 0; i < friends.length; i++) {
	console.log(friends[i]);
}
```

2. forEach

```javascript
const friends = ['Monica', 'Rachel', 'Phoebe', 'Chandler', 'Ross', 'Joey'];

const logFriends = (friend) => {
	console.log(friend);
};
friends.forEach(logFriends);

// can be more simple and readable
friends.forEach((friend) => {
	console.log(friend);
});

// how to access index in forEach
friends.forEach((friend, i) => {
	console.log(friend, i);
});
```

3. While

```javascript
let counter = 10;

while (counter > 0) {
	console.log(counter);
	counter--;
}
```

4. Do ... while

```javascript
let counter = 10;

do {
	console.log(counter);
	counter--;
} while (counter > 0);
```

**'while' vs 'do ... while'**

```javascript
let number = 10;

while (number > 10) {
	console.log('while', number);
	number--;
}

do {
	console.log('do while', number);
	number--;
} while (number > 10);

// result: do while 10
```

### Data Structures

#### Arrays

#### Objects

collections of properties and methods

- [Array Methods Cheat Sheet](https://www.notion.so/81628d655d734671ba195a5283089b84?v=a276134512f445f4892725d7ce8ba0c4)

## DOM (Document Object Model) Manipulation

- A web browser has a window object that has a 'document' property
- A document property specifies what should be displayed
- DOM reads HTML, CSS
- JavaScript is read line by line by the JavaScript engine in the browser

### DOM selector

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<link rel="stylesheet" href="styles.css" />
		<title>JavaScript</title>
		<script defer src="script.js"></script>
	</head>
	<body>
		<h1>To do List</h1>
		<p id="first">First</p>
		<p class="second">Second</p>
		<ul>
			<li random="123">Walking</li>
			<li>Studying</li>
			<li>Cooking</li>
			<li>Reading</li>
		</ul>
	</body>
</html>
```

1. Selector

```javascript
document.getElementsByTagName('h1')[0]; // <h1>To do List</h1>
document.getElementsByClassName('second'); // <p class="second">Second</p>
document.getElementById('first'); // <p id="first">First</p>

// Better way
document.querySelector('h1'); // <h1>To do List</h1>
document.querySelector('li'); // <li>Walking</li> *only first one
document.querySelectorAll('li'); // get all of them (Array)

document.querySelector('li').getAttribute('random'); // 123
document.querySelector('li').setAttribute('random', 1000); // arribute will be changed 123 to 1000
```

2. Changing Styles

```javascript
// style.{property}
document.querySelector('h1').style.color = 'red'; // "To do List" color: red
// but it is better to seperate style from javascript file
```

2.1. Changing Styles Better way

**script.js**

```javascript
const title = document.querySelector('h1');
title.className = 'title'; // class ('title') will be added
title.classList; // DOMTokenList ['title', value: 'title']

title.classList.add('title--red');
title.classList.remove('title--red');
title.classList.toggle('title--red');
```

**style.css**

```css
.title--red {
	color: red;
}
```

3. parentElement, children

```javascript
document.querySelectorAll('li')[1].parentElement; // <ul>
document.querySelector('ul').children; // [li, li, li, li]
```

[learn more...](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)

## 🔗 Useful Websites

- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [The Modern JavaScript Tutorial](https://javascript.info/)
