### Table of Contents

- [JavaScript Variables](#javascript-variables)

  - [variable declaration](#variable-declaration)
    - [Right way for variable declaration](#right-way-for-variable-declaration)
  - [Loosely-typed Variables](#loosely-typed-variables)
  - [Variable Scope](#variable-scope)
  - [var let and const](#var-let-and-const)
    - [difference between var, let & const](#difference-between-var-let--const)

# JavaScript Variables

- variables are containers for storing data.
- variable helps us to make think dynamic.
- ভ্যারিয়েবল হচ্ছে একটা পাত্রের মতো, যেখানে আপনি ‘কিছু’ রাখতে পারবেন। জাভাস্ক্রিপ্ট এ ‘কিছু’ বলতে অনেককিছু। আপনি চাইলে নাম্বার থেকে শুরু করে স্ট্রিং, অবজেক্ট, এমনকি ফাংশনও ভ্যারিয়েবল এর মধ্যে সেইভ করে রাখতে পারবেন।

তবে আপনাকে ভ্যারিয়েবল নেওয়ার আগে সেটাকে অবশ্যই প্রথম বার ডিক্লেয়ার করে নিতে হবে। জাভাস্ক্রিপ্ট এ ভ্যারিয়েবল ডিক্লেয়ার করা হয় var/let/const কীওয়ার্ড দিয়ে। var/let/const লিখার পর আপনি ভ্যারিয়েবলের নাম দিবেন, কি নামে হবে ভ্যারিয়েবল সেটা। এই নাম যেকোনো কিছু ইউজ করতে পারবেন, তবে কিছু রুলস আছে এখানেঃ

১। জাভাস্ক্রিপ্ট এর রিসার্ভড কীওয়ার্ড ইউজ করতে পারবেন না। (Reserved Keywords)

২। ভ্যারিয়েবলের নাম অক্ষর দিয়ে শুরু হতে পারবে, তবে নাম্বার,স্পেশাল ক্যারেক্টার !, @, #, %, ^, &, \*, (, ) দিয়ে শুরু হতে পারবে না।কিন্তু ‘\_’(আন্ডারস্কোর) ও ‘$’ (ডলার সাইন) ইউজ করে শুরু করতে পারবেন।

৩। ভ্যারিয়েবলের নামের মাঝখানে স্পেস ইউজ করা যাবে না। যদি এমন কোনো নাম নিতে হয় যেটার মাঝখানে স্পেস দরকার তাইলে আপনি ক্যামেলকেস ফরম্যাট এ(পরে আসছি বিস্তারিত) বা দুইটা ওয়ার্ড এর মাঝখানে ‘\_’ (আন্ডারস্কোর) ইউজ করতে পারেন। কিন্তু স্পেস কোনোভাবেই অ্যালাউড না।

৪। জাভাস্ক্রিপ্ট এ ভ্যারিয়েবল এর নাম কেস-সেনসিটিভ। মানে myName এবং Myname বা myname এক না। আপনি ঠিক বড় হাতে ছোটো হাতে যেভাবে ভ্যারিয়েবলের নাম নিবেন সেটাকে অ্যাক্সেস করতে হলে ঠিক সেভাবেই লিখে অ্যাক্সেস করতে হবে। এখানে myName এবং Myname দুইটা সম্পূর্ন আলাদা আলাদা দুইটা ভ্যারিয়েবল।

**ক্যামেলকেস ফরম্যাট:** জাভাস্ক্রিপ্ট ডেভেলপার কমিউনিটিতে বেশী ইউজ হয়। এটাকে আসলে কনভেশনাল ফরম্যাট বলে। জাভাস্ক্রিপ্ট এ ক্যামেলকেস ইউজ করা একটা কনভেনশন।

There are 3 ways to declare a JavaScript variable

1. var
2. let
3. const

**let and const are block scope**

### variable summary

variable লিখতে ৫টি জিনিস লাগে।

1. var/let/const
2. ভ্যারিয়েবলের নাম
3. =
4. value
5. ; (সেমিকোলন)

```Javascript
var price = 15;
```

variable লিখতে যেগুলো ইউজ করা যাবে না: Reserved Keywords, শুরুতে Number অথবা Special Character (তবে $ এবং \_ দিয়ে শুরু করা যাবে), ‍Space

### variable declaration

```Javascript
var fullName;
var age;
// after declaration, the variable has no value. (technically it is undefined)
```

### variable assign/initialize

```Javascript
fullName = "Md. Nazmul Hasan";
age = 24;
```

### variable declare & assign

```Javascript
var fullName = "Md. Nazmul Hasan";
var age = 24;
let name = "Nazmul", age=24, homeDistrict="Cumilla";
```

### Right way for variable declaration

```Javascript
let a = 10, b = 20;
let a = 10; let b = 20;
let [a, b] = [10, 20];
```

- Since, JavaScript is a **dynamically typed** language, you can assign a value of different type of a variable. Though, it's not recommanded.

```Javascript
let message = "Hello";
message = 100
```

- It's a good programming practice to declare all variables at the beginning of a script.

## Loosely-typed Variables

C# or Java has strongly typed variables. It means a variable must be declared with the data type that specifies the type of data a variable will store.

JavaScript is a loosely typed language. It means it does not require a data type to be declared. You can assign any literal values to a variable, e.g., string, integer, float, boolean, etc.

```javascript
var myvariable = 1; // numeric value

myvariable = "one"; // string value

myvariable = 1.1; // decimal value

myvariable = true; // Boolean value

myvariable = null; // null value
```

## Variable Scope

In JavaScript, a variable can be declared either in the global scope or the local scope.

**_Global Variables:_**
Variables declared out of any function are called global variables. They can be accessed anywhere in the JavaScript code, even inside any function.

**_Local Variables:_**
Variables declared inside the function are called local variables to that function. They can only be accessed in the function where they are declared but not outside.

The following example includes global and local variables.

```javascript
var greet = "Hello "; // global variable

function myfunction() {
  var msg = "JavaScript!";
  console.log(greet + msg); //can access global and local variable
}

myfunction();

console.log(greet); //can access global variable
console.log(msg); //error: can't access local variable
```

### var, let and const

**var**

- The `var` is the oldest keyword to declare a variable in JavaScript.
- It is used in all JavaScript code from 1995 to 2015;

**let**

- The `let` keyword is an improved version of the `var` keyword.
- The scope of a `let` variable is only block scoped. It can’t be accessible outside the particular block ({block})

**const**

- The `const` keyword has all the properties that are the same as the `let` keyword, except the user cannot update it.
- When users declare a `const` variable, they need to initialize it, otherwise, it returns an error.
- The user cannot update the `const` variable once it is declared.

## difference between var, let & const

|                           | var | let | const |
| ------------------------- | --- | --- | ----- |
| 1. Stored in global scope | ✔   | ❌  | ❌    |
| 2. Function scope         | ✔   | ✔   | ✔     |
| 3. Block scope            | ❌  | ✔   | ✔     |
| 5. Can be reassigned?     | ✔   | ✔   | ❌    |
| 6. Can be redeclared?     | ✔   | ❌  | ❌    |
| 7. Can be hoistted?       | ✔   | ❌  | ❌    |

**_1.Stored in global scope_**

```Javascript
var a = 10;
function f(){
    console.log(a);
}
console.log(a);
```

**output**

```Javascript
10
10
```

**Scope:** Global scoped or function scoped. The scope of the `var` keyword is the global or function scope. It means variables defined outside the function can be accessed globally, and variables defined inside a particular function can be accessed within the function.

Example 1: Variable ‘a’ is declared globally. So, the scope of the variable ‘a’ is global, and it can be accessible everywhere in the program.

**but let and const is not stored in global scope**

**_2. Function scope_**

```javascript
    function f() {

        // It can be accessible any where within this function
        var a = 10;
        or, let a = 10;
        or, const a = 10;
        console.log(a)
    }
    f();

    // It cannot be accessible outside of function
    console.log(a);
```

**output**

```Javascript
10
ReferenceError: a is not defined
```

**_3. Block scope_**
variable declared inside a {} block with var **can be** accessed from outside the block;

```javascript
{
  var a = 2;
}
// a can be used here
```

But with `let/const` can not be accessed from outside the block;

```javascript
{
  let a = 2;
  const b = 2;
}
// a, b can not be used here
```

**_4. Reassigned_**

```javascript
var a = 5;
a = 6;
```

```Javascript
let b = 10;
    b = 12
```

```Javascript
const c = 10;
    c = 12;
    // not allowed
```

**_5. Redeclared_**
Redeclaring a variable inside a block (with `var`) also redeclared the variable outside the block;

**But with let/const, not redeclared**

```javascript
var a = 5;
let b = 6;
const c = 7;

{
  var a = 15;
  let b = 16;
  const c = 17;
}
```

**output**

```Javascript
// Here a is 15
// b is 6
// c is 7
```

```Javascript
const a = 2;
    a = 12; // not allowed
var a = 10; // not allowed
let a = 20; // not allowed
const a = 30; // not allowed

```

**_6. Hoisting_**
variables defined with `var` are hoisted to the top and can be initialized at any time. (can use the variable before it is declared)

```Javascript
carName = "Volvo";
var carName;
// output will be undefined
```

With `let` / `const` are hoisted to the top of the block, but not initialized. (using `let` / `const` variable before it is declared will result in a ReferenceError)

```Javascript
carName = "Volvo";
let carName;
or, const carName;
// output will be Uncaught ReferenceError: can not access ...
```
