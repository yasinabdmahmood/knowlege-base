# Regular Expression
A regular expression is a pattern that can be used to match, search, or replace strings. 
They are often used to validate input, search for patterns, and perform other tasks related to manipulating text.
<br>
In JavaScript, you can use regular expressions by creating a RegExp object. Here's an example of how to create a regular expression that matches a string that starts with "hello" and ends with "world":
```JavaScript
const regex = new RegExp('^hello.*world$');
```
<br>
You can also create a regular expression using the forward slash (/) character. This is known as a regular expression literal, and it looks like this:
```JavaScript
const regex = /^hello.*world$/;
```
<br>
To use a regular expression, you can call methods such as `test`, `match`, `search`, and `replace` on a string. Here are some examples:
```JavaScript
const str = "hello world";

// Test if the string matches the regular expression
console.log(regex.test(str)); // outputs true

// Get an array of all matches
console.log(str.match(regex)); // outputs ["hello world"]

// Get the index of the first match
console.log(str.search(regex)); // outputs 0

// Replace all matches with a new string
console.log(str.replace(regex, "hi universe")); // outputs "hi universe"
```
