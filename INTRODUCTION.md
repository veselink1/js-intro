# JavaScript - An Overview

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

Variables in JavaScript need to be defined before use. Otherwise bad things will happen! This is different from the way that variables are specified in Python and PHP (they are simply assigned to).
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
- `Null` (value `null`)
- `Undefined` (value `undefined`)
- `Number` (floating-point numbers)
- `String`

\* `BigInt` and `Symbol` omitted from the list

There also is the non-primitive (because sub-types exists) `Object` type.

- The `Array` type in JavaScript is an `Object`
- Associative array are also `Object`s
- The `document` object is also an `Object`

