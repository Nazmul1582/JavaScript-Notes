### Table of Contents

- [JavaScript Function](#javascript-function)

  - [Function define](#function-define)
  - [Function call or function invoke](#function-call-or-function-invoke)
  - [Function define and call together](#function-define-and-call-together)
  - [Function Return](#function-return)
  - [## Why Functions?](#why-functions)
  - [Local variables](#local-variables)

  -[Chapter:8 Function](#chapter8-function)

  - [058. What is Function in Javascript | JS All You Need To Know](#058-what-is-function-in-javascript--js-all-you-need-to-know)
  - [059. Defining a Function in Javascript | JS All You Need To Know](#059-defining-a-function-in-javascript--js-all-you-need-to-know)
  - [060. Invoking a Function in Javascript | JS All You Need To Know](#060-invoking-a-function-in-javascript--js-all-you-need-to-know)
  - [061. Function Arguments and Parameters in Javascript | JS All You Need To Know](#061-function-arguments-and-parameters-in-javascript--js-all-you-need-to-know)
  - [062. Argument Object in Javascript | JS All You Need To Know](#062-argument-object-in-javascript--js-all-you-need-to-know)
  - [063. Return Something from a Function in Javascript | JS All You Need To Know](#063-return-something-from-a-function-in-javascript--js-all-you-need-to-know)
  - [064. Function Expression in Javascript | JS All You Need To Know](#064-function-expression-in-javascript--js-all-you-need-to-know)
  - [065. Inner Function in Javascript | JS All You Need To Know](#065-inner-function-in-javascript--js-all-you-need-to-know)
  - [066. Function Scoping in Javascript](#066-function-scoping-in-javascript)

# JavaScript Function

function => কাজ

A JavaScript function is a block of code designed to perform a particular task.

A JavaScript function is executed when "something" invokes it (calls it).

JavaScript কে বলা হয় একটা functional programming language. JavaScript এ সবকিছু function দিয়ে কল্পনা করা হয়।

## Function define:

```javascript
function sleep(parameter) {
  console.log("Abdullah is sleeping");
}
// এখানে function sleep(parameter){console.log("Abdullah is sleeping")} সম্পূর্ণটা একটি function define. এটাকে বলা যায় defined sleep function.

// এখানে parameter টা variable এর মত আচারণ করে।
```

## Function call or function invoke

The code inside the function will execute when "something" invokes (calls) the function:

- When an event occurs (when a user clicks a button)
- When it is invoked (called) from JavaScript code. [programmer can call it]
- Automatically (self invoked)

```javascript
// invoking (call/use/run) a funciton
sleep(argument);

// এখানে argument means value. argument এর স্থানে value pass করা হয়।
```

### Function define and call together

```javascript
function sleep(name, time) {
  console.log(name + " is sleep from " + time);
}

sleep("Abdullah", "9pm"); // Abdullah is sleeping from 9pm
sleep("Abdur Rahman", "8:30pm"); // Abdur Rahman is sleeping from 8:30pm
```

```javascript
function toCelsius(fahrenheit) {
  return (5 / 9) * (fahrenheit - 32);
}
document.getElementById("demo").innerHTML = toCelsius(77);
// here, toCelsius refers to the function object, and toCelsius() refers to the function result.
// function এর name টা function object refer করে। আর function call: function এর result টা refer করে।
```

## Function Return

When JavaScript reaches a return statement, the function will stop executing.

```javascript
function sum(a, b) {
  return a + b;
  console.log("Hello"); // not working after return
}
sum(3, 4); // output: nothing
console.log(sum(3, 4)); // output: 7

const result = sum(3, 4); // এখানে result এর value হবে 7
console.log(result); // output: 7
```

```javascript
function myFunc(a, b) {
  console.log("hello");
  // return undefined => function এর ভিতর থেকে কোনো কিছু return না করলে, সে undefined return করে।
}
let res = myFunc(4, 3); // এখানে myFunc() করার কারণে myFunc(4,3) এর স্থানে hello হয়ে যাবে।
console.log(res); // output: ১ম লাইনে hello( myFunc(4,3) থেকে) আর তারপরের লাইনে undefined হবে।
```

## Why Functions?

You can reuse code: Define the code once, and use it many times.

You can use the same code many times with different arguments, to produce different results.

Functions Used as Variable Values

## Local variables

```javascript
// code here can not use myName

function myInfo() {
  let myName = "Md. Nazmul Hasan"; // can use myName
}

// can not use myName here
```

# Chapter:8 Function

## 058. What is Function in Javascript | JS All You Need To Know

what is function?

function একটা মেশিন। যার ভিতরে তিনটি পার্ট আছে।
1.input
2.processing
3.output

টোটাল তিনটা ইউনিট আছে ।

একটা জায়গায় আমরা কোন না কোন data বা কোন না কোন ইনগ্রেডিয়েন্ট, ওই মেশিনটার ভিতরে দিয়ে দেই। দিয়ে দেওয়ার পরে প্রসেসিং part টা তে, function ওর ভিতরে এগুলো নিয়ে কিছু একটা করে। কি করে আমরা জানিনা। আমরা যখন define করবো তখন আমরা জানবো। কিন্তু যারা এ ফাংশনটা ব্যবহার করবে তারা মূলত জানবে না।
তাহলে কি কি হল?

একটা হল input: যেখানে আমরা ইনগ্রেডিয়েন্ট দিব।
processing unit: যেখানে ওই ইনগ্রেডিয়েন্স নিয়ে কিছু একটা ঘটবে। কি ঘটবে সেটা আমাদের ফাংশন জানে বা মেশিন জানে। যখন প্রসেসিংটা কমপ্লিট হয়ে যাবে তখন সে একটা সম্পুর্ণ নতুন ডাটা output দেবে। এটাই হচ্ছে মুলত function.

ফাংশানের দুইজন ইউজার থাকে। একজন হচ্ছে যে function টা ক্রিয়েট করবে আর আরেকজন হচ্ছে যে function টা কল করবে। রিয়েল লাইফে আপনিই দুইজন। কিন্তু এমনও হতে পারে ফাংশনটা আপনি ক্রিয়েট করছেন কিন্তু আপনি ব্যবহার করছেন না। যেমনটা থার্ড পার্টি লাইব্রেরীগুলোর ক্ষেত্রে হয়ে থাকে।

String(), Number(), Math(), Date() এগুলো আমরা ক্রিয়েট করিনি আমরা জাস্ট কল করে ব্যবহার করছি। আমরা জানি না কোনগুলো কিভাবে কাজ করছে। কিন্তু আমরা কল করলেই কাজ করছে।
আমরা শুধু জানি হয় একটাই imput দিতে হবে, সে আমাদের একটা আউটপুট দিবে। প্রসেসিং ইউনিটটা আমাদের কাছ থেকে পুরোপুরি হিডেন করে রাখা হয়েছে । এটাকে বলা হয় অ্যাবস্ট্রাকশন। ফাংশন হচ্ছে খুবই বেসিক লেভেলের একটা অ্যাবস্ট্রাকশন।

ফাংশনের কাজ হল: repeated কাজগুলো reduce করবে। (লুপও repeated কাজগুলো reduce করে। )

তাহলে লুপ আর ফাংশন কি same?

একটা লুপ একটা নির্দিষ্ট কাজ একটা নির্দিষ্ট সময় পর্যন্ত করতেই থাকবে। যদি আপনি টাইম লিমিট বলে না দেন। যদি আপনি বলে না দেন কতবার সে চলতে থাকবে। তাহলে সে ইনফিনিটি টাইম পর্যন্ত চলতেই থাকবে, চলতেই থাকবে চলতেই থাকবে। যেখানে আপনার কোন কন্ট্রোল নেই।
আপনার কন্ট্রোল আছে কতটুকু?
আপনি টাইম মতো এটাকে ব্রেক করতে পারবেন কোন একটা কন্ডিশনের উপর ভিত্তি করে। তাও কোন না কোন কন্ডিশনের উপরে নির্ভর করতে হচ্ছে। so, আপনি ডিরেক্টলি এর উপরে হস্তক্ষেপ করতে পারছেন না।

কিন্তু ফাংশন ঐরকম কোন ব্যাপার না। যে কাজগুলো আমাদের বারবার করা লাগে সেই কাজগুলো একটা জায়গায় নিয়ে আমরা একটা ফাংশন তৈরি করব। ফাংশনটাকে আমরা যখন খুশি তখন ম্যানুয়ালি কল করব। যেমনটা একটা date বের করার ফাংশন।

```javascript
// ***** Chapter Eight: Functions in Javascript

// What is Function

// Input Output Processing

var date = new Date();
date.getFullYear();
```

## 059. Defining a Function in Javascript | JS All You Need To Know

```javascript
function functionName() {
  //
}
```

```javascript
function functionName() {
  console.log("I am a Function");
}

function add() {
  var a = 10;
  var b = 20;
  console.log(a + b);
}

function sub() {
  var a = 50;
  var b = 20;
  console.log(a - b);
}
```

## 060. Invoking a Function in Javascript | JS All You Need To Know

Invoking (call/use/run) a funciton

```javascript
functionName(); // output: I am a Function
functionName(); // output: I am a Function

for (var i = 0; i < 10; i++) {
  functionName();
} // output : (10) I am a function

add(); // 30
add(); // 30

console.log(add); // output: all function
console.log(add()); // output: 30
```

## 061. Function Arguments and Parameters in Javascript | JS All You Need To Know

```javascript
function add(a, b) {
  var result = a + b;
  console.log(result);
}

add(10, 20); // 30
add(7, 3); // 10
add(500, 700); // 1200

var arr1 = [1, 2, 3];
var arr2 = [5, 7, 9, 10];
var arr3 = [9, 7, 1, 5, 7];

var sum1 = 0;
for (var i = 0; i < arr1.length; i++) {
  sum1 += arr1[i];
}
console.log(sum1); // 6

var sum2 = 0;
for (var i = 0; i < arr2.length; i++) {
  sum2 += arr2[i];
}
console.log(sum2); //  31

var sum3 = 0;
for (var i = 0; i < arr3.length; i++) {
  sum3 += arr3[i];
}
console.log(sum3); // 29

function sumOfArray(arr) {
  var sum = 0;
  for (var i = 0; i < arr.length; i++) {
    sum += arr[i];
  }
  console.log(sum);
}

sumOfArray(arr1); // 6
sumOfArray(arr2); // 31
sumOfArray(arr3); // 29
```

## 062. Argument Object in Javascript | JS All You Need To Know

```javascript
function test() {
  // console.log(arguments)
  // console.log(typeof a)

  for (var i = 0; i < arguments.length; i++) {
    console.log(arguments[i]);
  }
}
// test()
test(10, 20, 30);

function addAll() {
  var sum = 0;
  for (var i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  console.log(sum);
}

addAll(1, 2, 3);
addAll(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

var a = addAll(1, 2, 3);
var b = addAll(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
console.log(a, b);
```

## 063. Return Something from a Function in Javascript | JS All You Need To Know

আমরা ফাংশানের ভিতরের রেজাল্টাকে কোন একটা variable এ স্টোর করতে চাইলে return ব্যবহার করব। যেন আমরা পরবর্তীতে কোথাও রেজাল্ট টা ব্যবহার করতে পারি। retrun এর পর function নিচের code গুলোকে আর execute করে না।

```javascript
function addAll() {
  var sum = 0;
  for (var i = 0; i < arguments.length; i++) {
    sum += arguments[i];
  }
  return sum;
}

var result = addAll(1, 2, 3);
console.log(result); // 6

function person(name, email) {
  return {
    name: name,
    email: email,
  };
  console.log("I will never be shown");
}

var p1 = person("Nazmul Hasan", "nazmul@gmail.com");
console.log(p1); // { name: 'Nazmul Hasan', email: 'nazmul@gmail.com' }
```

## 064. Function Expression in Javascript | JS All You Need To Know

```javascript
var addition = function (a, b) {
  return a + b;
};
// এখানে addition variable এ একটা anonymous function ব্যবহার করা হয়েছে।

addition(10, 40);

// anonymous function এর আরেকটা ব্যবহার।
setTimeout(function () {
  console.log("I will call after 5 seconds");
}, 5000);

var another = addition;
console.log(another(7, 8));
```

## 065. Inner Function in Javascript | JS All You Need To Know

```javascript
function something(greet, name) {
  function getFirstName() {
    if (name) {
      return name.split(" ")[0];
    } else {
      return "";
    }
  }

  var message = greet + " " + getFirstName();
  console.log(message);
}

something("Good Morning", "Saikat Molla");
```

## 066. Function Scoping in Javascript

```javascript
var a = "abc";

if (true) {
  if (true) {
    var b = "I am B";
  }
}

console.log(b); // I am B ( এখানে b, nested block এ থেকেও বাইরে থেকে accessible. কিন্তু function এর ক্ষেত্রে এমন টা হয় না।)

// step 1 ========
function x() {
  function y() {
    console.log(a); // a = abc (from global scope)
  }

  y();
}
x(); // a = abc

// step 2 ========
function x() {
  let a = 20;
  function y() {
    console.log(a); // a = 20 (from parent function. not from global scope)
  }
  y();
}

x();

// step 3 =========
function x() {
  function y() {
    let a = 10;
    console.log(a); // a = 10 (from local scope. not from parent function or global)
  }
  console.log(a); // a = abc (from global. not from child function)
  y();
}
x();

// step 4 =========
function x() {
  let a = 20;
  function y() {
    let a = 10;
    console.log(a); // a = 10 (from local scope. not from parent function or global)
  }
  console.log(a); // a = 20 (from local. not from child function or global)
  y();
}
x();

function test(n) {
  function a() {
    return n % 3 === 0;
  }

  function b() {
    return n % 5 === 0;
  }

  if (a() && b()) {
    console.log(n + " is divisible by both 3 and 5");
  } else {
    console.log("Not a valid number");
  }
}

test(15);
```
