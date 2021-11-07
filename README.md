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

## Object-oriented JavaScript (OOP)

We use objectss to model real world things that we want to represent inside ouf program

- **Encapsulation**: object data (information, functionality/behavior) can be stored inside an object package
- **Abstration**: Creating a simple model of a more complex thing
  (For example, Person objects can have a lot of things such as an address, height but we focus on only what we interested in for our program)
- **Inheritance**: Child classes (subclasses) can be created to inherit the data of their parent class
- **Polymorphism**: The ability of multiple object types to implement the same functionality

```javascript
class Person {
	// When an object instance is created from a class,
	// the class's construction function is run to create it
	constructor(name) {
		this.name = name;
		this.greeting = () => {
			console.log(`Hello ${this.name}`);
		};
	}
}

const person1 = new Person('Grace');
person1.greeting(); // Hello Grace
const person2 = new Person('Peter');
person2.greeting(); // Hello Peter
```

### Other ways to create Objects

1. Object() constructor

```javascript
const person1 = new Object();
person1.name = 'Grace';
person1.greeting = function () {
	console.log(`Hello ${this.name}`);

	// It doesn't work
	// person1.greeting = () => {
	//		console.log(`Hello ${this.name}`);
	// }
};

person1.greeting(); // Hello Grace
```

2. create() method

```javascript
const person2 = Object.create(person1);
```

Reference: [MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_JS)

## DOM (Document Object Model)

- parsing HTML, CSS and display the results
- provide DOM API

### DOM selector

```html
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

#### HTMLCollection, NodeList

- DOM Object

1. HTMLCollection

- getElementsByTagName, getElementsByClassName
- live

**HTMLCollection to Array**

```html
<ul id="fruits">
	<li>Apple</li>
	<li>Banana</li>
	<li>Orange</li>
</ul>
```

```javascript
const fruits = document.getElementsByTagName('li');
console.log(fruits); // HTMLCollection(3) [li, li, li]
console.log([...fruits]); // (3) [li, li, li]
console.log(Array.from(fruits)); // (3) [li, li, li]

// Now, we can use Array.methods (forEach, map, filter, reduce...)
const fruitsArray = [...fruits].forEach((fruit) => (fruit.className = 'red'));
```

2. NodeList

- querySelectorAll
- static, (\*exception: live (Node.childNodes))

```javascript
const fruits = document.getElementById('fruits');
console.log(fruits.childNodes); // NodeList(7) [text, li, text, li, text, li, text]
```

- you can use `forEach` method
- [more methods](https://developer.mozilla.org/en-US/docs/Web/API/NodeList)

#### Walking the DOM

1. Child Node

```html
<ul id="fruits">
	<li>Apple</li>
	<li>Banana</li>
	<li>Orange</li>
</ul>
```

```javascript
const fruits = document.getElementById('fruits');
console.log(fruits.childNodes); // NodeList(7) [text, li, text, li, text, li, text]
console.log(fruits.children); // HTMLCollection(3) [li, li, li]

console.log(fruits.firstChild); // #text
console.log(fruits.firstElementChild); // li.apple

console.log(fruits.lastChild); // #text
console.log(fruits.lastElementChild); // <li>...</li>
```

- check if the Node has child nodes or not
- return a boolean

```html
<ul id="fruits">
	<!--  -->
</ul>
```

```javascript
console.log(fruits.hasChildNodes()); // true * because of white space
console.log(fruits.children.length); // 0
console.log(fruits.childElementCount); // 0
```

2. Parent Node

3. Sibling

#### nodeType, nodeName

#### nodeValue, textContent

### DOM Manipulation

#### Create Elements

**index.html**

```html
<ul id="to-do-list">
	<li class="to-do-item">study</li>
</ul>
```

**script.js**

```javascript
const toDoList = document.getElementById('to-do-list');

const createEl = () => {
	const doToItem = document.createElement('li');
	doToItem.textContent = 'walking';
	doToItem.classList.add('to-do-item');
	doToItem.setAttribute('onclick', 'done()');

	//append
	toDoList.appendChild(doToItem);
};

const done = () => {
	console.log('nice job!');
};

createEl();
```

### DOM Event

**index.html**

```html
<button class="button">Click me!</button>
```

**script.js**

```javascript
const greeting = () => {
	console.log('hi there');
};

const button = document.querySelector('.button');
button.addEventListener('click', greeting);
```

#### Event Bubbling & Event Delegation

**index.html**

```html
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>5</li>
	<li>6</li>
	<li>7</li>
	<li>8</li>
	<li>9</li>
	<li>10</li>
</ul>
```

**style.css**

```css
.done {
	text-decoration: line-through;
}
```

**script.js**

```javascript
// Bad 👎
const lis = document.querySelectorAll('li');
lis.forEach((li) => {
	li.addEventListener('click', () => {
		li.classList.add('done');
	});
});

// Good 👍
const ul = document.querySelector('ul');
ul.addEventListener('click', (e) => {
	if (e.target.tagName == 'LI') {
		e.target.classList.toggle('done');
	}
});
```

[Learn more about Event](https://developer.mozilla.org/en-US/docs/Web/Events)

## Advanced Concepts

### Global Execution Context

## 🔗 Useful Websites

- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [The Modern JavaScript Tutorial](https://javascript.info/)
