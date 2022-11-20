<!-- TABLE OF CONTENTS -->

### Table of Contents

- [JavaScript Syntax](#javascript-syntax)
- [JavaScript Expressions](#javascript-expressions)
- [JavaScript Statement](#javascript-statement)
  - [Semicolons](#semicolons)
  - [White Space](#white-space)
  - [JavaScript Block](#javascript-block)
  - [Keywords and Reserved works](#keywords-and-reserved-works)
  - [Comments](#comments)
  - [JavaScript Identifiers or Names](#javascript-identifiers-or-names)
  - [JavaScript Line Length and Line Breaks](#javascript-line-length-and-line-breaks)
  - [JavaScript Code Structure](#javascript-code-structure)
- [Statement vs Expression](#statement-vs-expression)

# JavaScript Syntax

**JavaScript syntax** is the set of rules how JavaScript programs are constructed.
=> JavaScript syntax নিয়মের সেটকে বুঝায়, যা জাভাস্ক্রিপ্ট প্রোগ্রামগুলো কিভাবে তৈরি তা নির্ধারণ করে।
**JavaScript Value**
JavaScript syntax defines two types of value.

1. Fixed values (Fixed values are called **literals** like: numbers, strings)
2. Variable values (variable values are called variables [var, let, const]

### JavaScript Expressions

An expression is a combination of values, variables, and operators, which computes to a value.

The computation is called an evaluation.

```JavaScript
 5 * 10
 "John" + " " + "Doe"
```

## JavaScript Statement

The programming instructions written in a programming language are known as statements.
JavaScript statements are composed of: Values, Operators, Expressions, Keywords & Comments.

JavaScript programs and JavaScript statements are often called JavaScript code. A simple statement is terminated by a semicolon (;)

### Semicolons:

Semicolons separete JavaScript statements.
When separated by semicolons, multiple statements on one line are allowed:

```JavaScript
var a = 5; b = 6; c = a + b;
```

### White Space:

JavaScript ignores multiple spaces. You can add white spacec to your script to make it more readable.

```JavaScript
function() => {
   console.log("Hello");
}
```

### JavaScript block

JavaScript statements can be grouped together inside curly brackets. Such group are known as code block.The purpose of grouping is to define statements to be executed together.

```JavaScript
function sum(){
   var a = 5;
   var b = 6;
   console.log(a + b);
}
```

### Keywords and Reserved works

JavaScript defines a list of reserved keywords that have specific uses. Therefore, you cannot use the reserved keywords as identifiers or property names by rules.

The following table shows the JavaScript reserved words defined in ECMA-262:

`break` `case` `catch` `continue` `debugger` `default` `else` `export` `extends` `function` `if` `import` `new` `return` `super` `throw` `try` `null` `void` `while` `with` `class` `delete` `finally` `in` `switch` `typeof` `yield` `const` `do` `for` `instanceof` `this` `var`

In addition to the reserved keywords, ECMA-252 also define a list of future reserved words that cannot be used as identifiers or property names:

`enum` `implements` `let` `protected` `private` `public` `await` `interface` `package` `implements` `public`

### Comments

- code after double slashes `//` or between `/*` and `*/` is treated as a comment.
- comments are ignored and will not be executed.

```JavaScript
var a = 5;  // It will be executed
 // var a = 5;  // It will not be executed
```

### JavaScript Identifiers or Names

Identifiers are JavaScript names.

Identifiers are used to name variables and keywords, and functions.

The rules for legal names are the same in most programming languages.

A JavaScript name must begin with:

- A letter (A-Z or a-z)
- A dollar sign ($)
- Or an underscore (\_)
  Subsequent characters may be letters, digits, underscores, or dollar signs.
- All JavaScript identifiers are case sensitive.

_Note:_ Numbers are not allowed as the first character in names.

- identifiers are case-sensitive. JavaScript doesn't interpret LET or Let as the keyword let.
- Hyphens are not allowed in JavaScript. They are reserved for subtractions (first-name, last-name, master-card).
- Underscore is allowed: first_name, last_name.
- Upper Camel Case (Pascal Case) is allowed: FirstName, LastName
- Lower Camel Case is allowed: firstName, lastName.

### JavaScript Line Length and Line Breaks

For best readability, programmers often like to avoid code lines longer than 80 characters.

If a JavaScript statement does not fit on one line, the best place to break it is after an operator:

```Javascript
document.getElementById("demo").innerHTML =
"Hello World!";
```

### JavaScript Code Structure

console.log(👉"Hello"👈);👈

console.log(👉'Hello'👈);👈

\*Quotation and Semicolon.

# Statement vs Expression

**এপ্রেশন:** সহজ কথায় বললে, জাভাস্ক্রিপ্টের কোনো কোড যদি ভ্যালু প্রডিউস করে তাহলে সেটা এপ্রেশন।
যেমন:

- 5 → produces 5
- "hello → produces hello
- undefined → produces undefined
- result === true ? "correct" : "wrong"
  num > 100 → produces either true or false
  isHappy ? "🙂" : "🙁" → produces an emoji
  [1, 2, 3].pop() → produces the number 3
  একটা এক্সপ্রেশন এর মধ্যে ও এক্সপ্রেশন থাকতে পারে।

যেমন: (5 + 1) \* 2 এইটা একটা এক্সপ্রেশন তাই না ?

এই এক্সপ্রেশন এর মধ্যে মোট কয়টা এক্সপ্রেশন আছে?

উত্তর: মোট 5 টা।

কিভাবে?

1. (5 + 1) \* 2 পুরোটা একটা এক্সপ্রেশন।
2. (5 + 1) এইটা একটা এক্সপ্রেশন।
3. 5 একটা এক্সপ্রেশন।
4. 1 একটা এক্সপ্রেশন।
5. 2 একটা এক্সপ্রেশন।

**স্টেটমেন্ট:** একটা প্রোগ্রামের মাধ্যমে আমরা কম্পিউটারকে কিছু নির্দেশনা(statement) দিয়ে থাকি যা সে এক্সিকিউট করে থাকে। প্রোগ্রামিং ল্যাঙ্গুয়েজে এই নির্দেশনাগুলোকেই স্টেটমেন্ট বলে। একটা জাভাস্ক্রিপ্ট প্রোগ্রাম ও কিছু লিস্ট অফ প্রোগ্রামিং স্টেটমেন্ট এর সমন্বয়। যেমন:

`var num = 100`

```javascirpt
if (hi > 10) {
  // More statements here
}
```

```javascirpt
throw new Error('Something exploded!');
```

স্টেটমেন্ট এর মধ্যে কিছু জায়গায় আমরা এক্সপ্রেশন লিখে থাকি। যেমনঃ

```javascirpt
// Statement 1:
let hi = /* expression slot */;

// Statement 2:
return /* expression slot */;

// Statement 3:
if (/* expression slot */) { }

```

সর্বশেষ যদি আবার একবার একথায় বুঝতে চাই তাহলে, এক্সপ্রেশন হল যদি কোন জাভাস্কিপ্ট কোড অথবা কোড এর অংশ আমাদেরকে কোনো ভ্যালু প্রডিউস করে তাহলে সেটা এক্সপ্রেশন এবং স্টেটমেন্ট হল একটা নির্দেশনা। একটা স্টেটমেন্ট এর মধ্যে ও এক্সপ্রেশন থাকতে পারে। [source](https://boolean.hashnode.dev/statement-vs-expression-in-javascript)
