# JavaScript Examples

## Array

## Objects

```javascript
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

```javascript
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

```javascript
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

```javascript
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
