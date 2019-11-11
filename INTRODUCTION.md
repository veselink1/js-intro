# **JavaScript** - An Overview

This document is a very high-level introduction to the JavaScript language and assumes little programming knowledge. All rights belong to the author (Veselin Karaganev). The document is only to be distributed under the terms of the GPL 3.0 Licence.

## What is JavaScript?

JavaScript is one of triad of technologies that build the World Wide Web, the other two being HTML5 (the HTML Living Standard) and CSS (usually stylized as CSS3).

JavaScript is the most popular implementation of ECMAScript. The two are often confused. Here is the gist of it: ECMAScript is a specification, which describes the syntax and workings of the language.

JavaScript is an implementation of that specification, which builds on top of it (e.g.: the document object which is used to interface with the current HTML document is specified in the JS (short for JavaScript) specification, whereas ECMAScript does not mention anything about the code running in a browser and interfacing with web pages).

In 2015, the long-awaited ECMAScript 6 (also knows as ES2015) was released and added many new features to JavaScript. Current web browsers support most of the ES6 specification and the general consensus is that new JavaScript projects should try to make use of these new features. ES6+ features will be mentioned separately in this document.

JavaScript is also a considered a scripting language, for which there is not a strict definition, but a simple and straightforward explanation of what that means is that the “programs” (called scripts) are usually distributed in source form (as opposed to being compiled) and are meant to act as a bridge between usually several other technologies (HTML, CSS) in this case).

## Why do we need JavaScript?

With HTML describing the layout of the pages (using element blocks) and CSS specifying the way that page looks (using rules), JavaScript is needed to enable interaction with that page and to process the user’s input. 
So **why** JavaScript? JavaScript is the only scripting language that is fully supported by all popular browsers. That’s why. There is no other technology that allows developers to create interactive experiences on the World Wide What.

Everything is on the web, which puts JavaScript in a very special place. JavaScript is a language that is often criticized for many of its design decisions (similarly to PHP, although not to that extent). What is important to remember is that it is a technology that has held up against the test of time and has been the core of a modern-day technological renaissance. 

## What can I use JavaScript for?

JavaScript, for good or bad, can be used for much, much more that what it was originally designed for. Here is a non-exhaustive list: web applications, mobile application, desktop applications, server applications and games.

Here is a list of popular pieces of software that make extensive use of JavaScript:

- The Google Slides web application which can be used to create presentations in the browser
- Netflix has stated they have built part of the back-end in JavaScript
- The Visual Studio Code and Atom cross-platform text editors
- The Spotify Web Player and Desktop application
- Most current web browser games (see http://hexgl.bkcore.com/)
- Most of the Firefox OS user-space and applications (Firefox OS is a mobile OS that uses HTML, CSS and JS for its applications)

## How is JavaScript loaded and executed in the Browser?

JavaScript has a particular execution model that can be summed-up in a number of steps:

1. The HTML code “invokes” the JavaScript script by means of the `<script>` tag.
    a. If the `<script>` tag has a `src=”.../something/myscript.js”` attribute, the browsers stops loading of the HTML document and sends a request for the script and continues with step 2.
    b. If the `<script>` tag contains embedded JavaScript code, step 2 happens.

2. The JavaScript source code is loaded by the JavaScript engine and immediately executed to completion

3. The browser continues loading and displaying the rest of the HTML

To be able to later respond to a user’s action, an appropriate “event listener” has to be added to the HTML element on which the action is to happen. For this to happen, that element needs to have been loaded before step 2 (as the JavaScript code is executed in-between the loading of the page). Also note, that the code being executed in response to that user action is executed outside of that 3-step model. 

## Variables

Variables in JavaScript need to be defined before use. Otherwise bad things will happen! This is different from the way that variables are specified in Python and PHP (they are simply assigned to). Variable names are bound to the scope of the function that contains them or to the global scope. 

A variable declaration looks like this:
```js
var variableName;
```
And can optionally include an assignment of an initial value:
```js
var variableName = 10;
```

Note that for later reassignment of the variable, the `var` keyword must **not** be used.

ECMAScript 2015 adds two new ways to declare variables in JavaScript:

```js
let variableName;
let variableName = 10;
```

For most intents and purposes, `let` is equivalent to `var` and **should be preferred**.

```js
const variableName = 10;
```

The `const` keyword is used to specify a variable which **cannot be reassigned**. Constant variables should be assigned a value at the time of declaration.

### Variable Naming
Variable names are written in [camelCase](https://en.wikipedia.org/wiki/Camel_case). 

```js
let firstNameInput = document.getElementById('first-name');
```

Constant names are written in [SCREAMING_SNAKE_CASE](https://en.wikipedia.org/wiki/Snake_case).

```js
const MY_CONSTANT = 10;
```

## Data Types

There are *five primitive data types in JavaScript:
- `Boolean` (values `true` or `false`)
- `Number` (floating-point numbers)
- `String`
- `Null` (value `null`)
- `Undefined` (value `undefined`)

\* `BigInt` and `Symbol` omitted from the list

There also is the non-primitive (because sub-types exists) `Object` type.

- The `Array` type in JavaScript is an `Object`
- Associative array are also `Object`s
- The `document` object is also an `Object`

## Embedding JavaScript in a web page
There are two common methods to do that:
- Write the JavaScript code between the opening and closing `<script>` tags.
- Write the JavaScript code in a separate `.js` file and include it in the web page by means of `<script src="myscript.js"></script>` (leave the content of the element empty).

The location of the inclusion also has to be considered (recall the execution model from above):
- Including the script in the `<head>` means that by the time the script is executed, the `<body>` tag has even been seen by the browser, so it is likely that any element you immediately interact with will not be available.
- Including the script at the end of the `<body>` means that the script will only be executed after **all** other resources have loaded (including possibly large image files!).

You will see a third, more commonly-used approach in the examples.
The first approach will be used in these examples only, but might be looked down upon in an actual project.

## Data Types

### `Boolean`
The `Boolean` data type has two values, written `true` and `false`. Example:
```js
let isValid = true;
```

### `Number`
Literals of the `Number` type are written in the usual decimal notation. Hexadecimal (base-16), Octal (base-8) and Scientific notations are also supported. Example:
```js
let decimal = 10.34; // 10.34
let hexadecimal = 0x10; // 16
let octal = 0o10; // 8
let sci = 1E3; // 1000
```

### `String`
Strings are created by enclosing text in single (`'`), double (`"`) quotes, or less-commonly backticks (\`) (for multi-line or interpolated strings). 
Quote-enclosed strings can only span a single line. Example:
```js
let text = 'Hello, World!';
```
Which style you prefer is irrelevant, but choose a style and stick to it.

### `Null`
The `Null` data type describes the absence of a value and is equivalent to Python's `None` (of type `NoneType`). The only value of the `Null` data type is `null`. Example:
```js
let myVar = null;
```

### `Undefined`
The `Undefined` data type describes the unassigned variables. The only value of the `Undefined` data type is `undefined`.
```js
let myVar; // value is undefined
let myOtherVar = undefined; // this is discouraged
```

### `Array`
Arrays can be created using `[]` (square brackets) just like in Python. Example:
```js
let arr = [1, 2, 3];
```

### `Object`
`Object` is the base type of all non-primitive types in JavaScript. Instances of `Object` can be created directly using `{}` (curly braces). Example:
```js
let obj = { name: 'Veselin Karaganev', yearOfBirth: 2000 };
```
Objects declared in this way are somewhat similar to Python's `dict` objects. If a key is not a valid identifier, the name of the key should be enclosed in quotes. Example:

```js
let obj = { 'invalid key': true };
```

## Conditional Statements
See [Making decisions in your code — conditionals](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/conditionals).

## Loops
See [Looping code](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Looping_code).

## Functions
```js
function myFunc(a, b) {
    return a + b;
}
let resultA = myFunc(1, 2);
let resultB = myFunc(5, 10);
```
Functions are reusable, discrete blocks of code that can optionally have arguments and a return value. The argument list of functions does not need to be prepended by a variable declaration keyword (`var`, `let`, `const`).

### Function Naming
Function names are written in [camelCase](https://en.wikipedia.org/wiki/Camel_case). 

```js
function addTwoNumbers(x, y) {
    return x + y;
}
```

### Arrow Functions
Since ECMAScript 2015, an alternative way to define functions also exists and may be preferred in certain circumstances. 

```js
let myFunc = (a, b) => {
    return a + b;
};

let resultA = myFunc(1, 2);
let resultB = myFunc(5, 10);
```

Functions defined with `() =>` are known as **arrow functions**. In other languages they are also known as lambda functions or closures (the two are mostly used synonymously). Notice that since the arrow function syntax does not allow us to directly specify a name on the right hand side of the definition, to bind the arrow function to a name we assign it to a variable (`myFunc` in this cases).

A nice thing about **arrow functions** is that if the body of the function includes only a single statement, the `{}` braces can be omitted.

```js
let myFunc = (a, b) => a + b;
```

## The `document` object
The `document` object is accessible by the global `document` variable. The `document` object provides access to the current page's Document Object Model (DOM) - the representation of the webpage in JavaScript. 

One can query different elements from the document by using one of the following methods:
- `document.getElementById(id)` - by the value of the **unique** `id` attribute of the element
- `document.getElementsByClassName(className)` - by the contents of the `class-name` attribute of the element
- `document.getElementsByTagName(tagName)` - by the tag name of the elements
- `document.querySelector(querySelector)` - by using a CSS selector (e.g. `"div.className"`)
- `document.querySelectorAll(querySelector)` - by using a CSS selector (e.g. `"div.className"`)

Methods containing plural forms or all in their name return a list of elements.

After you have obtained a DOM object referring to an HTML element, you can use methods on the object to change the properties of that element. Example:

```html
<div id="myDiv">Hello, World!</div>
<script>
let myDiv = document.getElementById('myDiv');
myDiv.textContent = myDiv.textContent.toUpperCase();
</script>
```

Here the `toUpperCase()` method on `String` is used. The `Element#textContent` property is equal to the textual content of the element (the string `Hello, World!` in this case).

New elements can be added to the document using the `createElement` and `appendChild` methods. Example:

```html
<ul id="myList">
    <li>Broccoli</li> <!-- Oh, noo! -->
</ul>
<script>
let myList = document.getElementById('myList');

let newItem = document.createElement('li');
newItem.textContent = 'Ice Cream'; // Oh, yeeaah!

// Insert the element object into the document
// by adding it as a child of the myList element.
myList.appendChild(newItem);
</script>
```

Note that until the `Element#appendChild` method is invoked, the element exists but is not present in the visible DOM.

## Using event listeners
Event listeners are a fundamental part of any JavaScript web application. They allow the execution of code in response to an event (as opposed to only while loading the page). Event listeners can be attached to elements and removed from them with the `addEventListener(eventName, callback)` and `removeEventListener(eventName, callback)` methods. Event listeners are defined by an event type an a callback function.

```html
<button id="myButton">Click me!</button>
<script>

function onButtonClick() {
    alert("You win an iPhone 11! But first, you have to take our survey!")
}

let myButton = document.getElementById('myButton');
myButton.addEventListener('click', onButtonClick);

</script>
```

Try this code in your browser. Or, even better, use [JSFiddle](https://jsfiddle.net/).
Here is a link to the above example: https://jsfiddle.net/15k2hvzc/

Many different event types exist corresponding to different actions:
- click - for when the user clicks on the button 
- keydown - for when the user presses a key down on the keyboard
- keyup - for when the user releases a key on the keyboard
- change - for when the contents of an input field changes
- many more...

Also see the examples on the following pages:
- [DOM Elements](https://www.w3schools.com/js/js_htmldom_elements.asp)
- [Modifying DOM Elements](https://www.w3schools.com/js/js_htmldom_html.asp)
- [Event Listeners](https://www.w3schools.com/js/js_htmldom_eventlistener.asp)

## Reducing script execution delay
As mentioned someplace above, embedding scripts in the `<head>` element means that most of the page won't have loaded yet, and embedding scripts at the end of the `<body>` would mean that the browser would wait for images and other resources to load before even downloading the script. 

There is a third, better way to execute JavaScript - in-between these two event. By using the DOMContentLoaded event, we can make sure that all the HTML is loaded, but not necessarily all the fancy imagery and fonts. Here is how to do that:
```html
<head>
...
<script>
    function runAfterDOMLoads() {
        let button = document.getElementById('button');
        // Use button
    }
    document.addEventListener('DOMContentLoaded', runAfterDOMLoads);
</script>
</head>
<body>
    <button id="button">Click</button>
    <!-- Many images and more content -->
</body>
```

Of course, it is imperative for the `document.addEventListener('DOMContentLoaded', ...)` statement to be executed prior to the body loading for maximum gains. That is, don't do that if the script is already at the bottom of the `<body>` element, as that would make no sense.

## JSON

JSON is an acronym for JavaScript Object Notation. It a format specification for describing single or compound values. The JSON syntax is a subset of the JavaScript syntax for literal values. JSON is usually used as a means of communication between different applications or computers. 

Over the time, JSON has replaced XML as the de facto standard for client <-> server communication due to the increasing popularity of JavaScript for building ever more complex applications and the built-in support for the syntax.

The following example constitute valid JSON.
```json
{ 
    "first_name": "Veselin", 
    "last_name": "Karaganev", 
    "email": "vesko.karaganev@example.com" 
}
```

Open [OpenWeatherMap API](https://openweathermap.org/current) to see how JSON is used as an exchange format to provide information about the weather. 

Also see [Example API Request](https://samples.openweathermap.org/data/2.5/weather?q=London,uk&appid=b6907d289e10d714a6e88b30761fae22) and study the response. What do you notice?

Being a subset of the JavaScript syntax for specifying literal values, any valid JSON can be freely used to specify values in JavaScript.

```js
let user = { 
    "first_name": "Veselin", 
    "last_name": "Karaganev", 
    "email": "vesko.karaganev@example.com" 
};
```

Note that the opposite is not strictly true! The following constraints apply in JSON:
- Object (dictionary) keys should always be enclosed in double quotes (`"`)
- A trailing comma is not allowed after the last key-value pair in the object specification.
- The only supported types in JSON are `Number`, `String`, `Array`, `Object`, `Null`.

The following is **not** valid JSON, but is **valid** JavaScript.
```js
{
    first_name: "Veselin", // <- note the missing double quotes (")
    "last_name": 'Karaganev', // <- note the single quotes (')
    "email": "vesko.karaganev@email.com", // <- note the trailing comma
}
```

## Other resources
An unmatched resource for HTML, CSS and JavaScript is [MDN - the Mozilla Developer Network website](https://developer.mozilla.org/en-US/).
Another popular, although not so thorough and often not very precise in the definitions and explanations of stuff is [W3Schools](https://www.w3schools.com/).

In particular, it is important to take a look at the following:
- [JavaScript Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
- [JavaScript Functions](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Functions)
- [JavaScript Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)

A good idea is to always make sure to lookup any unknown language constructs or built-ins on [MDN](https://developer.mozilla.org/en-US/).

For example to see all 260 methods and properties of the `document` object, [click here](https://developer.mozilla.org/en-US/docs/Web/API/Document). That is of course not possible for any person to go through at once. That is why I would recommend carefully reading through the summary of the page and then finding some examples on the internet of how to use it.


## Examples & Exercises

1. 
    i. Open the [Todo List](https://jsfiddle.net/otcrna8p/4/) example and study it. 

    ii. Add CSS to enhance the appearance of the UI. Do not use tag name selectors. Use class-name instead.
    
    iii. Add input checking via JS. Verify that the input string is at least 3 characters long. Show a message to the user on incorrect input.
