 <br />
 <p align="center">
    <h1 align="center"> This in JavaScript </h1>
</p>

<!-- TABLE OF CONTENTS -->

### Table of Contents

- [This Keyword](#this-keyword)
  - [implicit binding](#implicit-binding)
  - [explicit binding](#explicit-binding)
  - [new binding](#new-binding)
  - [window binding](#window-binding)

## This Keyword

- This keyword JavaScript এ আছে কেন? কি দরকার?

- এটা একটা function কে different context এ reuse করতে help করে।

this keyword ব্যবহারের ৪টি নিয়ম:

1. implicit binding
2. explicit binding
3. new binding
4. window binding

```javascript
var printPlayerName = function (name) {
  console.log(name);
};
printPlayerName("sakib");
```

**🚀 this এর ব্যবহার জানতে হলে আগে জানতে হবে function কে কল করা হয়েছে কোন জায়গায়। (কোন লাইনে)**

## implicit binding

```javascript
var sakib = {
  name: "sakib",
  age: 23,
  printPlayerName: function () {
    console.log(this.name);
  },
};

sakib.printPlayerName();
```

- implicit binding এর ক্ষেত্রে দুইটি জিনিস দেখতে হবে।

- ১) function টি কত নাম্বার লাইনে/ কোথায় কল হয়েছে?

- ২) function টি যেখানে কল হয়েছে তার বামে যদি dot(.) notation এবং কোন object থাকে, তাহলে this সেই object কে নির্দেশ করে(not work for fat arrow function)। (এখানে this মানে sakib object টি)

### Example: 1

```javascript
const sakib = {
  name: " Sakib",
  age: 35,
  printPlayerName: function () {
    console.log(this.name);
  },
};
sakib.printPlayerName(); // Sakib
```

### Example: 2

```javascript
const printPlayerNameFunction = function (obj) {
  obj.printPlayerName = function () {
    console.log(this.name);
  };
};

const sakib = {
  name: "Sakib",
  age: 35,
};

const tamim = {
  name: " Tamim",
  age: 34,
};

printPlayerNameFunction(sakib);
printPlayerNameFunction(tamim);
sakib.printPlayerName(); // Sakib
tamim.printPlayerName(); // Tamim
```

### Example: 3;

```javascript
const Person = function (name, age) {
  return {
    name: name,
    age: age,
    printName: function () {
      console.log(this.name);
    },
  };
};
const sakib = Person("Sakib", 35);
sakib.printName(); // Sakib
```

### Example: 4

```javascript
const Person = function (name, age) {
  return {
    name: name,
    age: age,
    printName: function () {
      console.log(this.name);
    },
    father: {
      name: "Mr. A",
      printName: function () {
        console.log(this.name);
      },
    },
  };
};

const sakib = Person("Sakib", 35);
sakib.father.printName(); // Mr. A
```

## explicit binding

### Example: 1

```javascript
const printName = function () {
  console.log(this.name);
};

const sakib = {
  name: " Sakib",
  age: 35,
};
printName.call(sakib); // Sakib
printName.apply(sakib); // Sakib
const res = printName.bind(sakib);
res(); // Sakib
```

### Example: 2

```javascript
const printName = function () {
  console.log(this.name);
};

const sakib = {
  name: "Sakib",
  age: 35,
};

let v1 = "Handsome";
let v2 = "All-rounder";
let v3 = "Best Player";
const v = [v1, v2, v3];

printName.call(sakib, v1, v2, v3);
printName.apply(sakb, [vSakib]);
const res = printName.bind(sakib, v1, v2, v3);
res(); // Sakib
```

## new binding

```javascript
function Person(name, age) {
 // this = Object.create()
 this.name: name;
 this.age: age;
 printName: function(){
   console.log(this.name)
 };
// return this;
}
const sakib = new Person(" Sakib", 35);
```

## window binding

```javascript
const printName = function () {
  console.log(this); // window obj
  console.log(this === window); // true
  console.log(this.name); // undefined
};
const sakib = {
  name: "Sakib",
};

printName();
```

### Example: 2

```javascript
("use strict");
const printName = function () {
  console.log(this); // undefined
  console.log(this === window); // false
  console.log(this.name); // error
};
const sakib = {
  name: "Sakib",
};

printName();
```
