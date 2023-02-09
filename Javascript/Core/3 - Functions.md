Like other OOP languages like C#, JS supports the use of functions

Functions in JS must first be defined, like so:
```
function greetings(name)
{
	return('Hello' + name);
}

// Call the function
greetings('John');
```

Function can take anynumber of arguments. And in JS, not all the arguments have to be declared or given a name. The below is a valid JS function:
```
function printAll()
{
	for(int i = 0; i < arguments.length; i++)
	{
		console.log(arguments[i]);
	}
}

printAll(1,2,3,4,5) // 1 2 3 4 5
```

All of the values sent to the function in this case are put into an array-like object called arguments. You can iterate through this object like an array, but many of the built array methods, such as *map* and *foreach* are not available to it. NOTE: In order for the arguments object to be created, the functions arguments need to be left blank.
____

### Scope

#### Function Scope
Functions only have access to variables/objects decalred *within* the {} brackets of the function. However, a function can acces a variable if it is a nested function within its parent function

Example:
```
function() {
	var message = "Hello":
	let sayHi = function() {
		console.log(message);
	}
}
```
Here, sayHi function can access the message variable because it is within the scope of it's parent function. JS will go through all of the parent functions in order to find a reference to the variable before throwing a reference error

### Block Scope
This is scope that occurs in between a set of {} braces

Variables that have been declared with the var keyword DO NOT have block scope, instead it becomes a global scope. Unless you intend global scope, you should always use the let keyword to declare variables instead

____
### Immediatly Invoked Function Expression (IIFE)

Design pattern for JS functions

```
//Normal Function
function grettgin() {
	console.log('Hello');
}

// IIFE Style
// this function will be invoked right away instead of waiting to be called 
(function() {
	console.log("Hello");
})();

```
These functions are normally used when assigned to a variable

##### Closures
This is part of an IIFE function to return values

```
let greeting = (function() {
	let message = "Hello";
	let getMessage = function() {
		return message;
	}
})();

console.log(greeting.message) // undefined
```
greetings.message returns undefined because it *is out of scope*. We can use closures to prevent message form going out of scope

```
let greeting = (function() {
	let message = "Hello";
	let getMessage = function() {
		return message;
	};
	return {
		getMessage: getMessage,
	}
})();

console.log(greeting.message) // Hello
```
This returns an object. Typically in this format the key and value are the same, but it doesn't have to be.

```
function setupCounter( val) {
	return function counter() {
		return val++;
	}
}

let counter1 = setupCounter(0);
console.log(counter1()); // 0
console.log(counter1()); // 1
let counter2 = setupCounter(10);
console.log(counter2()); // 10
```
This produced the same function with two different contexts with their own seperate values

## Arrow Functions

Arrow functions for a syntaxically compact version of declaring a function.

Note: some behaviors change when in an arrow function. The *this* keyword is a primary example

```
let greetings = function() {
	return "Hello World!";
}

let message = greetings(); // Hellow World
console.log(message)
// Is the same as this:
let greetings2 = () =>
{
	return "Hello WOrld!";
}

console.log(greetings2)

// And is the same as this:
// Because the function is only 1 line of code

let greetings = () => "Hello WOrld";

// Arrows can also take arguments

let greetings = (name) => "Hello " + name;
let message = greetings("John");
console.log(message) // Hello John;
```
 Arrow functions do not have their own this values, and as such, values are inherited from the enclosing scope

## Function Contexts

Functions in JS are really just another kind of object, and as such can have their own properites


