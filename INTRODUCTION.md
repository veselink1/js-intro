# **JavaScript** - An Overview

This document is a very high-level introduction to the JavaScript language and assumes little programming knowledge. All rights belong to the author (Veselin Karaganev). The document is only to be distributed under the terms of the GPL 3.0 Licence.

## What is JavaScript?

JavaScript is one of triad of technologies that build the World Wide Web, the other two being HTML5 (the HTML Living Standard) and CSS (usually stylized as CSS3).

JavaScript is the most popular implementation of ECMAScript. The two are often confused. Here is the gist of it: ECMAScript is a specification, which describes the syntax and workings of the language.

JavaScript is an implementation of that specification, which builds on top of it (e.g.: the document object which is used to interface with the current HTML document is specified in the JS (short for JavaScript) specification, whereas ECMAScript does not mention anything about the code running in a browser and interfacing with web pages).

JavaScript is also a considered a scripting language, for which there is not a strict definition, but a simple and straightforward explanation of what that means is that the “programs” (called scripts) are usually distributed in source form (as opposed to being compiled) and are meant to act as a bridge between usually several other technologies (HTML, CSS) in this case).

## Why do we need JavaScript?

With HTML describing the layout of the pages (using element blocks) and CSS specifying the way that page looks (using rules), JavaScript is needed to enable interaction with that page and to process the user’s input. 
So **why** JavaScript? JavaScript is the only scripting language that is fully supported by all popular browsers. That’s why. There is no other technology that allows developers to create interactive experiences on the World Wide What.

Everything is on the web, which puts JavaScript in a very special place. JavaScript is a language that is often criticized for many of its design decisions (similarly to PHP, although not to that extent). What is important to remember is that it is a technology that has held up against the test of time and has been the core of a modern-day technological renaissance. 

## What can I use JavaScript for?

JavaScript, for good or bad, can be used for much, much more that what it was originally designed for. Here is a non-exhaustive list: web applications, mobile application, desktop applications, server applications and games.

Here is a list of popular pieces of software that were built with JavaScript:

- The Google Slides web application which was used to create this application
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

## `Boolean`
The `Boolean` data type has two values, written `true` and `false`. Example:
```js
var isValid = true;
```

## `Number`
Literals of the `Number` type are written in the usual decimal notation. Hexadecimal (base-16), Octal (base-8) and Scientific notations are also supported. Example:
```js
var decimal = 10.34; // 10.34
var hexadecimal = 0x10; // 16
var octal = 0o10; // 8
var sci = 1E3; // 1000
```

## `String`
Strings are created by enclosing text in single (`'`), double (`"`) quotes, or less-commonly backticks (\`) (for multi-line or interpolated strings). 
Quote-enclosed strings can only span a single line. Example:
```js
var text = 'Hello, World!';
```
Which style you prefer is irrelevant, but choose a style and stick to it.

### `Null`
The `Null` data type describes the absence of a value and is equivalent to Python's `None` (of type `NoneType`). The only value of the `Null` data type is `null`. Example:
```js
var myVar = null;
```

### `Undefined`
The `Undefined` data type describes the unassigned variables. The only value of the `Undefined` data type is `undefined`.
```js
var myVar; // value is undefined
var myOtherVar = undefined; // this is discouraged
```

### `Array`
Arrays can be created using `[]` (square brackets) just like in Python. Example:
```js
var arr = [1, 2, 3];
```

### `Object`
`Object` is the base type of all non-primitive types in JavaScript. Instances of `Object` can be created directly using `{}` (curly braces). Example:
```js
var obj = { name: 'Veselin Karaganev', dob: 2000 };
```
Objects declared in this way are somewhat similar to Python's `dict` objects.
