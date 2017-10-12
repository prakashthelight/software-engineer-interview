# JavaScript Examples

## Array
Initializing array
```javascript
var nums = [10, 15, 45];
or
var nums = [];
nums.push(10);
nums.push(15);
nums.push(45);
```

Iterating over array
```javascript
var nums = [10, 15, 45, 35, 80];

// standard for loop
for (var i = 0; i < nums.length; i++) {
	console.log(nums[i]);
}

// for - in example
for (var index in nums) {
	console.log(nums[index]);
}

// for - of example
for (var item of nums){
	console.log(item);
}

// using Array.prototype.forEach()
nums.forEach(function(item) {
		console.log(item);
});

nums.forEach(function(item, index) {
	console.log(index + ": " + item);
});
```

## Functions in JavaScript
- Named functions
- Anonymous functions
- Immediately invoked function expressions

```javascript
// regular named function, called explicitly by its name
function printMessage(msg) {
	console.log(msg);
}
printMessage("Hello World!");

// anonymous function, reference stored in a variable
var print = function(msg) {
	console.log(msg);
};
print("Hello Another World!");

// immediately invoked function
(function() {
	console.log("Hello Universe");
}());

or
(function(msg) {
	console.log(msg);
}("Hello Universe"));
```

## Global and Local Variables
- variables defined in a function are local to that function block
- variables defined without a `var` keyword are global by default
- should use `'use strict'` to avoid accidently doing variable declaration without `var` keyword

```js
var factor = 7; // global variable
function multiply() {
	var num = 6; // local variable
	num1 = 10; // declared without var, accidently global variable
	return factor * num;
}

console.log(num); //Uncaught reference error: num is not defined as it is local to function blcok
console.log(num1); // accessible outside method, as it is global accidently
```

### const and let keywords
- variables declared `const` are constants
- variables declared `let` are block scoped

```js
function example() {
	var local = "I am local to function";
	if (local) {
		// overrides already defined local variable value
		var local = "I am local to this if block"
		console.log(local);
	}
	console.log(local);
}
example();
```
output
```
I am local to this if block
I am local to this if block
```

```js
function example() {
	var local = "I am local to function";
	if (local) {
		// let creates variable with block scope
		let local = "I am local to this if block"
		console.log(local);
	}
	console.log(local);
}
example();
```
output
```
I am local to this if block
I am local to function
```
## Objects
- Creating simple object

```js
// create person object
var person = {
    firstName: 'Prakash',
    lastName: 'Kumar'
};

// add properties to object
person.age = 30;

// add method to object
person.walk = function () {console.log('person is walking');}

// read object properties
console.log(person.firstName);
console.log(person['lastName']);
console.log(person.age);

// invole object method
person.walk();
```
- Person object with object constructor and initialized using `new` keyword

```js
// create Person class, constructor function
var Person = function (firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.walk = function () {
        console.log('person is walking');
    }
};

// create object of class Person
var person = new Person('Prakash', 'Kumar');

// read object properties
console.log(person.firstName + ', ' + person.lastName);
// invole object method
person.walk();
```
- Creating Person class using ECMAScript 6 class keyword

```js
// create Person class, using ECMAScript 6 classes
class Person {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    walk() {
        console.log('person is walking');
    }
};
```

```js
// read object properties
console.log(Object.getOwnPropertyDescriptor(person, 'firstName'));
// output
{
	value: "Prakash",
	writable: true,
	enumerable: true,
	configurable: true
}
```

```js
Object.defineProperty(person, 'fullName', {
	get: function () {
		return this.lastName + ', ' + this.firstName;
	},
	enumerable: true
});

// enumerating over properties of object
for (var propertyName in person) {
	console.log(propertyName + ": " + person[propertyName]);
}

// output
firstName: Prakash
lastName: Kumar
fullName: Kumar, Prakash
```

```js
var array = [12, 10, 15];
Object.defineProperty(Array.prototype, 'last', {
	get: function () {
		return this[this.length - 1];
	}
})

console.log(array.last);
```


## Closures

- a function inside a function which uses variables in outer function, as `getArea()` here is using pi from `getFormula()` function

```js
function getFormula(radius) {
	var pi = 22/7;
	function getArea() {
		return pi * radius * radius;
	}
	return getArea; // return function
}

var circleArea = getFormula(7);
console.log(circleArea()); // 154
```
