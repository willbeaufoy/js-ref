# Javascript (+ some HTML) reference

## Code and comments

- The computer will try and run all code in the file, except for comments.

HTML:

```html
<h1>Doc title</h1>
<!-- A comment -->
<!-- Commented out code (will not be run)
<h2>Subtitle</h2>
-->
```

Javascript:

```javascript
const var1 = 'hello';
// This is a comment.

/** This is the other way of writing comments */

/** Commented out code below
const b = 'rew';
*/
```

## Simple variables

- A variable is a stored value in a program.
- Variables have a name (which you choose to be whatever you want), and a value (which can be of various different types).
- Here we will deal with types `string`, `number` and `boolean`.
- Variable names should be meaningful, e.g. if the variable is to store an email address, it could be called `emailAddress`.
- By convention, variable names are written in [lowerCamelCase](https://wiki.c2.com/?LowerCamelCase).
- There are various ways to declare variables, but current best practice is to do so with the keyword `const` (if the variable's value will not change) or `let` (if it will).

### Declaration and assignment

```javascript
const month = 'jan'; // month is the variable name, and 'jan' is its value;
month = 'feb'; // ERROR! You cannot reassign a const.
let day = 'tues';
day = 'wed'; // OK to reassign as declared with let.
// If using let, you can declare without a value and assign later.
let year;
year = '2020';
```

### Numbers

```javascript
const num = 4;
const num2 = 2;
// Numbers can be manipulated with all the normal maths operations.
console.log(num + num2); // 6.
console.log(num - num2); // 2.
console.log(num * num2); // 8 (* means multiply).
console.log(num / num2); // 2.
```

### Strings

- A string is any set of characters contained in quotes.

```javascript
const greeting = 'hello';
let animal = 'dog';
animal = 'cat';
// This is a string, not a number, because it is in quotes.
const stringNum = '45';

// Create a new variable out of existing variables.
// Combining strings with + will concatenate them.
// Here we are combining the greeting variable, then an empty space, then the animal variable.
const animalGreeting = greeting + ' ' + animal;
console.log(animalGreeting); // hello cat.
```

### Booleans

- A boolean is a value that can be either true or false.
- It is named after boolean algebra, invented by George Boole.
- Booleans can be combined with operators, `&&` (AND), `||` (OR) and `!` (NOT).
- Numbers and strings can use the === (equals), !== (not equals), < (less than), <= (less than or equal to), > (greater than), and >= (greater than or equal to) operators to produce booleans.

```javascript
// Booleans can only be true or false.
let b1 = true;
b1 = false;
const b2 = true;

// The ! operator (NOT) negates a boolean (i.e. gives its opposite value).
console.log(b1); // false, because b1 is false.
console.log(!b1); // true, because ! negates the boolean.
console.log(b2); // true.
console.log(!b2); // false.

// The && operator (AND) returns true if the booleans on both sides are true.
let result = b1 && b2;
console.log(result); // false, because while b2 is true, b1 is false, therefore they are not both true.

// The || operator (OR) returns true if a boolean on either side is true.
result = b1 || b2;
console.log(result); // true, because one of the booleans (b2) is true.

// We can use numbers to demonstrate the comparison boolean operators.
console.log(2 === 2); // true, 2 is equal to 2.
console.log(2 === 3); // false.
console.log(2 !== 3); // true, 2 is not equal to 3.
console.log(2 < 4); // true, 2 is less than 4.
console.log(2 < 2); // false, 2 is not less than 2.
console.log(2 <= 2); // true, 2 is less than or equal to 2.
console.log(3 > 2); // true.
console.log(3 >= 3); // true.

// We can also compare strings by alphabetical order (earlier in the alphabet means a lower number).
console.log('b' < 'c'); // true.
console.log('b' < 'a'); // false.
```

## Functions

- Functions are bits of code that 'do something'.
- Optionally they can take in inputs that decide how they do that thing.
- Functions are declared with the keyword `function` (similar to how variables are declared with `const` or `let`).
- Like variables, they have a name which you choose, but which should be meaningful, and also like variables, the name is written in [lowerCamelCase](https://wiki.c2.com/?LowerCamelCase).
- A function's inputs/arguments/parameters (all these terms are used interchangeably) are between parentheses () and its body (what it does) is between curly braces {}.
- Once a function has been declared, it can be called, which is when it 'does its thing'.
- Most functions return a value, but they do not have to.

```javascript
// Function with no inputs that returns nothing and logs to the console.
// Declare the function.
function logToConsole() {
  console.log('func was called');
}
// Call the function.
logToConsole(); // func was called.

// Most functions return a value. This means you can assign the result of the function to a variable.
// Function with one input.
function addPrefix(prefix) {
  return prefix + ' dog';
}
// Call the function.
let result = addPrefix('big');
console.log(result); // big dog.

// Function with two inputs
function addPrefixAndSuffix(prefix, suffix) {
  return prefix + ' dog ' + suffix;
}
// Call the function.
result = addPrefixAndSuffix('big', 'barks');
console.log(result); // big dog barks.
```

## Objects

- Objects are 'bundles' of variables and/or functions.
- Variables in an object are called its properties, and functions in an object are called its methods.
- For example, in a web application there may be an object called `user`, which could have as its properties `firstName`, `lastName`, `dateOfBirth`, and `emailAddress`, and as methods `getFullName()` and `getInitials()`.

```javascript
const user = {
  // Properties (its variables).
  firstName: 'John',
  lastName: 'Smith',
  dateOfBirth: '1971-09-18',
  emailAddress: 'johnsmith@gmail.com',

  // Methods (function).
  // When inside an object, functions do not require the function keyword.
  getFullName() {
    // Inside a method, this. refers to the object itself. Therefore this.firstName refers to user.firstName.
    return this.firstName + ' ' + this.lastName;
  },

  getInitials() {
    // This method uses a string method 'slice' to get the first character of firstName and lastName.
    return this.firstName.slice(0, 1) + '. ' + this.lastName.slice(0, 1) + '.';
  },
};

// Access object properties with a dot:
console.log(user.lastName); // Smith.
// You can also change object properties in the same way.
user.lastName = 'Jones';
console.log(user.lastName); // Jones.
const fullName = user.getFullName();
console.log(fullName); // John Jones.
// You can also log the output of a function directly.
console.log(user.getInitials()); // J. S.
```

## If statements

- If statements check if a boolean condition is true or false, and do different things based on the result.
- Any number of different conditions can be checked, using the if ... else if ... else if ... else syntax.

```javascript
// This function takes a number as a parameter and outputs information about it using if statements.
function checkNum(num) {
  if (num === 1) {
    console.log('Num is 1');
  } else if (num === 2) {
    console.log('Num is 2');
  } else if (num < 10) {
    console.log('Num is less than 10');
  } else {
    console.log('Num is greater than or equal to 10');
  }
```

## HTML interaction

Javascript normally runs in a browser and interacts with HTML. There are many built-in functions and objects that enable them to do this.

### console

- `console` is an object automatically created by the browser for interacting with the browser console (open with ctrl+shift+i or f12).
- `console.log()` is a method of this object (i.e. a function), that outputs its parameter(s) to the console.
- So when you write `console.log('hello')` you are calling the `console` object's `log()` method with the parameter 'hello'.

```javascript
console.log('hello');
// If we were to write our own simplified version of the console object:
const myConsole = {
  log(message) {
    // Code to output the provided message to the console would be here.
  },
};
// Then we could call the method in the same way:
myConsole.log('hello');
```

### document

- `document` is an object automatically created by the browser for interacting with the HTML document.
- `document.querySelector()` is a method of this object (i.e. a function) that gets HTML elements in the document as Javascript objects so that Javascript can interact with them.

HTML:

```html
<!-- The page heading -->
<h1 class="heading">Page title</h1>
<!-- A text box for the user to input their name -->
<input type="text" class="nameInput" />
```

Javascript:

```javascript
// There are many ways to use querySelector to get HTML elements; one way is by class. Add a dot in front of the class name in JS to get the element by class.
const heading = document.querySelector('.heading');
// You can access the element's content like so.
console.log(heading.textContent); // Page title.
// And you can change it@
heading.textContent = 'New heading';
console.log(heading.textContent); // New heading.

// For an <input> element, you can access its value property (this is what the user has typed in).
const input = document.querySelector('.nameInput');
console.log(input.value);

// If we were to write a simplified version of the document object:
const myDocument = {
  querySelector(query) {
    // Code to find the HTML element identified by the query, e.g.
    // const element = ...
    return element;
  },
};
// Then we could call the method in the same way:
const element = myDocument.querySelector('.myClass');
```
