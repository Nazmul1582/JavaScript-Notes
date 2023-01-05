 <br />
 <p align="center">
    <h1 align="center"> Prototype in JavaScript </h1>
</p>

<!-- TABLE OF CONTENTS -->

### Table of Contents

- [Prototype](#this-keyword)

## Prototype

**create a object**

```javascript
const person = {};
person.name = "Jasim";
person.age = 35;
person.eat = function () {
  console.log(`Person is eating`);
};
person.sleep = function () {
  console.log(`Person is sleeping`);
};
console.log(person);
```

**create dynamic object**

```javascript
function Person(name, age) {
  const person = {};
  person.name = name;
  person.age = age,
    person.eat = function () {
      console.log(`${this.name} is eating`);
    },
    person.sleep = function () {
      console.log(`${this.name} is sleeping`);
    };
  return person;
}

const sakib = Person("Sakib", 35);
const tamim = Person(" Tamim", 34);
```

- এখানে যতগুলো object create করা হচ্ছে ততবারই Person এর ভেতরের property এবং method গুলো নতুন করে প্রত্যেকটা object এর জন্য create হচ্ছে। যেটা large application এ memory issue হতে পারে। তাই আমাদের কমন method গুলোর জন্য আলাদা একটা object তৈরি করতে হয়।

```javascript
const personMethods = {
  eat() {
    console.log(`Person is eating`);
  },
  sleep() {
    console.log(`Person is sleeping`);
  },
};

function Person(name, age) {
  const person = {};
  perspn.name = name;
  person.age = age;
  person.eat = personMethods.eat;
  person.sleep = personMethods.sleep;
}
const sakib = Person("Sakib", 35);
const tamim = Person("Tamim", 34);
sakib.eat();
tamim.sleep();
```

- এক্ষেত্রে আরেকটা problem হলো নতুন কোনো method add করতে চাইলে প্রথমে personMethods এ add করতে হয়। তারপর Person() এ reference টা বলে দিতে হয়। যেটা একটা combarsome.
  এটার solution হচ্ছে Object.create() use করা।

```javascript
const captain = {
  name: "Mashrafe",
  age: 36,
  country: " Bangladesh",
};
const player = Object.create(capital);
console.log(player); // null
console.log(player.name); // Mashrafe
console.log(player.age); // 36
```

- এখানে player কে `consol.log( )`করলে output আসছে `{}` কিন্তু `player.name` লিখলে আসছে `Mashrafe`. আবার `player.age = 36` দেখাচ্ছে। কারণ `Object.create()` এর মাধ্যমে parent object(captain) দিয়ে child object (player) create করা হয়েছে। তাই player empty দেখালেও `player.name` এর মাধ্যমে parent এর প্রপারটিগুলোর access নেওয়া যাচ্ছে।
  এটা কিভাবে হচ্ছে? হ্যাঁ, এটা হচ্ছে `Object.create()` এর behaviour. (JavaScript একটু extra smart. তাই সে এরকম অদ্ভুত behave করে। unpredictable behaviour.) কিন্তু সে কাজটা কিভাবে করে। এটা সে করে basically prototype এর মাধ্যমে। এ জিনিসটা করতে পারে সে prototype এর কারণে।

তার মানে আমরা এখন পর্যন্ত `Object.create()` এর behaviour সম্পর্কে যা বুঝলাম তা হলো: আমি যদি একটা child object, parent object এর মাধ্যমে create করি তাহলে child, parent এর প্রপারটিগুলোরকে access করতে পারবো।

তো সেটাকে কাজে লাগিয়ে:

```javascript
const personMethods = {
	eat(){
		console.log(`Person is eating`);
	}
	sleep(){
		console.log(`Person is sleeping`);
	}
	play(){
		console.log(`Person is playing`);
	}
}

function Person(name, age) {
  const person = Object.create(personMethods);
  console.log(person); // {};
  person.name = name;
  person.age = age;
  return person;
}
const sakib = Person("Sakib", 35);
const tamim = Person("Tamim", 34);
sakib.play(); // Person is playing
tamim.play(); // Person is playing
```

- `Object.create` এর behaviour অনুযায়ী; যেহেতু `personMethods` হচ্ছে parent. parent এর method গুলোকে আমি child এ access করতে পারি। তাই আমি `play` কে access করতে পারছি।
  কিন্তু আমাদের এই কোডটাকে আরও improve করার way আছে। আর মজাটা এখান থেকেই শুরু…

- আমরা এতক্ষণ যা দেখলাম এটা কিন্তু প্রোগ্রামিংয়ের খুবই পরিচিত একটা প্যাটার্ণ।
  যা আমরা parent থেকে কিছু প্রোপারটি শেয়ার করি child এ। child এর কাছে সব প্রোপারটি available থাকে। আবার child নিজেও নিজের মত প্রোপারটি এড করে নিতে পারে।

- কিন্তু এখানে, এই simple pattern টার জন্য আমাকে আলাদা একটা object maintain করতে হচ্ছে outside of that object. মানে এই person এর বাইরে আমাকে কিন্তু আরেকটা object এর assistance নিতে হচ্ছে। এ ব্যাপারটা একটু কেমন জানি? built-in তো কিছু থাকার কথা! আছে, এখানেই prototype এর প্রয়োজন।

```javascript
function test() {}
console.log(test.prototype); // {constructor: f }
```

- এখানে test একটা function. (আমরা জানি function একটা object.) সে কিছুই করেনা। তার মধ্যে কিছু নাই। কিন্তু আমরা যদি console.log(test.prototype) করি, তাহলে আমরা কিন্তু কিছু একটা পাচ্ছি। কি পাচ্ছি সেটা পরের কথা।
  আমি একটা blank function করেছিলাম। যেটা itself is a object. যখন এটাকে console.log(test.prototype) করছি তখন কিন্তু কিছু একটা পাচ্ছি। আমি যদি console.dir(test) করি, তাহলে test এর বডির মধ্যে আমরা prototype বলে একটা প্রোপারটি পাচ্ছি। prototype আর কিছুই না। এটা sakib.name, sakib.age এরকম simple প্রোপারটির মতোই prototype হচ্ছে একটা simple property of a function.(JavaScript এর যেকোনো function এর একটা প্রোপারটি) যেটা কোনো একটা object কে point করে।

🚀🚀 prototype এর definition:
prototype হচ্ছে JavaScript এর যেকোনো function এর একটা প্রোপারটি, যেটা একটা object কে point করে।

- এখানে আমি যে method গুলো শেয়ার করছি, সেগুলোর আলাদা একটা object create করতে হচ্ছে। সেটা না করে; আমার যে Person() সেটার prototype বলে একটা object কিন্তু আছে তার মধ্যে। যেটা JavaScript এর built-in.
  আমি আলাদা object create না করে, prototype এর মধ্যে শেয়ার করা মেথডগুলো রাখতে পারি।

```javascript
function Person() {
  const person = Object.create(Person.prototype);
  person.name = name;
  person.age = age;
  return person;
}

Person.prototype = {
  eat() {
    console.log(`Person is eating`);
  },
  sleep() {
    console.log(`Person is sleeping`);
  },
  play() {
    console.log(`Person is playing`);
  },
};

const sakib = Person("Sakib", 35);
const tamim = Person("Tamim", 34);
sakib.play();
tamim.eat();
```

- `Object.create()` এর behaviour অনুযায়ী parent এর সবকিছু যেহেতু child access নিতে পারে। তাই এখানে, `Object.create(Person.prototype)` এর মেথডগুলো `sakib.play()` এবং `tamim.eat()` তে accessible. অর্থাৎ, এখনো `sakib.play()` বা `tamim.play()` দিলে কাজ করছে।

- তাহলে আগেরবার থেকে আমরা যে advanced হইলাম সেটা হচ্ছে, আমরা prototype কে ব্যবহার করে;

- prototype আর কিচ্ছু না! prototype হচ্ছে function এর একটা built-in প্রোপার্টি; যেটা JavaScript আমাদেরকে দেয়। সেই prototype এর মধ্যে যেই যেই জিনিসগুলো আমার শেয়ার করা প্রয়োজন, সেই শেয়ার করা জিনিসগুলো যেটা কমন সে জিনিসটাকে আমি রেখে দিতে পারি। এবং সেটার মাধ্যমে আমি call করে একই output পাচ্ছি।
  JavaScript কে prototype base language. Prototype জাভাস্ক্রিপ্টের কোনো নতুন ফিচার না। এটা জাভাস্ক্রিপ্টের শুরু থেকে ছিল। JavaScript is based on prototype.
  C বা Java হচ্ছে class based language. Class এভাবেই কাজ করে।
  vanilla JavaScript এ class বলে কিছু ছিল না। যার কারণে JavaScript prototype এর মাধ্যমে তার প্যারেন্টের প্রোপারটিগুলোকে child এর মধ্যে inherite করত। যেটাকে আমরা inheritance বলি। অন্যান্য লেঙ্গুয়েজে inheritance হয় Class এর মাধ্যমে। আর JavaScript এ inheritance হয় prototype এর মাধ্যমে।

prototype আর কিছুই না! prototype হচ্ছে function এর একটা built-in প্রোপার্টি; যেটা আসলে জাস্ট inheritance এ হেল্প করে।

আমরা এতক্ষণ যা দেখলাম, তা থেকে ৩টি জিনিস শিখলাম।

1. How to create a constructor function (like: Person) JavaScript এর সমস্ত function ই বাই-ডিফল্ট constructor function. কারণ, সেই function দিয়ে আমি একটা object চাইলেই create করতে পারি।
2. constructor function এর prototype এর মধ্যে কিভাবে মেথড এড করতে হয়।
3. Object.create() এর মাধ্যমে কিভাবে আমরা পেরেন্টের প্রোপার্টিগুলোকে চাইল্ডে নিয়ে আসতে পারি, inherit করতে পারি।

- আমাদের মেইন উদ্দেশ্যটা কি ছিল?

আমাদের মেইন উদ্দেশ্যটা ছিল: constructor function এর সবগুলো instance এর মধ্যে এই কমন মেথডগুলো শেয়ার করা।

কমন মেথডগুলো শেয়ার করা; এটাতো খুব বেসিক একটা কনসেপ্ট। এটা তো আরও simple way তে থাকার কথা, built-in কিছু একটা থাকার কথা! হ্যাঁ আছে। শর্টকাট আছে আরেকটা। এই যে আমরা sakib, tamim যে instance গুলো create করলাম, সেগুলো আমরা JavaScript এর new keyword দিয়ে একই কাজটা করতে পারতাম। যেমন:

```javascript
/*
const sakib = Person("Sakib", 35);
const tamim = Person("Tamim", 34);
*/

const sakib = new Person("Sakib", 35);
const tamim = new Person("Tamim", 34);
```

আমি এখানে একটা new person তৈরি করছি।
আগেরবারের থেকে এবার `new` দিয়ে call করাতে কি এমন extra benefit পাচ্ছি? benefit হলো:

```javascript
function Person(name, age) {
  let person = Object.create(Person.prototype);
  person.name = name;
  person.age = age;
  return person;
}
Person.prototype = {
  eat() {
    console.log(`Person is eating`);
  },
  sleep() {
    console.log(`Person is sleeping`);
  },
  play() {
    console.log(`Person is playing`);
  },
};

function PersonWithNew(name, age) {
  // let this = Object.create(PersonWithNew.prototype);
  this.name = name;
  this.age = age;
  // return this
}
/*
const sakib = Person("Sakib", 35);
const tamim = Person("Tamim", 34);
*/

const sakib = new PersonWithNew("Sakib", 35);
const tamim = new PersonWithNew("Tamim", 34);
```

`new` keyword দিয়ে লিখলে `let person = Object.create(PersonWithNew.prototype);` এবং `return person` লিখতে হয় না। ধরে নিতে পারেন JavaScript এটা আপনার জন্য লিখে দিচ্ছে। JavaScript (person) এটাকে naming করে this দিয়ে।
তার মানে ব্যাপারটা দাঁড়াচ্ছে, আমি যেমন এখানে let person (`let person = Object.create(Person.prototype)` ধরে নিয়েছিলাম; JavaScript এটাকে জাস্ট this নামে তৈরি করে(`let this = Object.create(PersonWithNew.prototype);`) এবং return করে `this`.

```javascript
function Person (name, age){
	// let this = Object.create(Person.prototype);
	this.name = name;
	this.age = age;
	// return this;
};

Person.prototype = {
	eat(){
		console.log(`Person is eating`);
	};
	sleep(){
		console.log(`Person is sleeping`);
	};
	play(){
		console.log(`Person is playing`);
	};
};

const sakib = new Person("Sakib", 35);
sakib.play(); // Person is playing
const tamim = new Person("Tamim", 34);
```

- normally অন্যান্য programming language (class based language) এ এভাবেই ( `new Something()` ) object create করা হয়।

আমরা এরপর land করব `class` এ। JavaScript এখন `class` ও সাপোর্ট করে।

এবার তাহলে আমরা এটাকে `class` এ convert করে ফেলি। …………

```javascript
class Person {
  constructor(name, age) {
    // let this = Object.create(Person.prototype);
    this.name = name;
    this.age = age;
    // return this;
  }
  eat() {
    console.log(`Person is eating`);
  }
  sleep() {
    console.log(`Person is sleeping`);
  }
  play() {
    console.log(`Person is playing`);
  }
}

const sakib = new Person("Sakib", 35);
sakib.play(); // Person is playing
const tamim = new Person("Tamim", 34);
```

- So, আমরা prototype থেকে `class` syntax এ convert হয়ে গেলাম।
  finally আমরা prototype থেকে বের হয়ে এসে, আমরা পরা আমাদের কোডটাকে Object Oriented Programming Language মানে `class` এর মত করে নিয়ে চলে আসলাম। So, এতক্ষণ আমরা যেটা দেখলাম সেটা হচ্ছে prototype এর fundamental ব্যাপারটা; যে prototype কিভাবে কাজ করে।

**Optional:**

আমরা JavaScript এ array create করি:

```javascript
// let persons = [];
let persons = new Array();
```

- `let persons = new Array()` মানে persons নামে নতুন একটা array. `let persons = [];` হচ্ছে `let persons = new Array()` এর শর্ট ফর্ম। মানে বারবার `new Array()` না লিখে `[]` লিখলেই হবে। এখন:

```javascript
let persons = new Array();
persons.push("Sakib");
console.log(persons); // ["Sakib"]
```

- `persons.push("Sakib");` এখানে `.push()` কোথ্থেকে আসলো? আমরা বলেছিলাম যে, prototype এর মধ্যে যেগুলো থাকে সেগুলো child নিয়ে আসে। এখানে child হলো persons, আর parent কে? এই যে বড় হাতের Array.

```javascript
console.dir(persons);
console.log(persons.prototype);
```

আমরা যদি `console.dir(Array)` করি তাহলে prototype প্রোপার্টিটা দেখতে পাবো। আর `console.log(Array.prototype);` করলে `push()` সহ আরও অনেকগুলো মেথড দেখতে পাচ্ছি।
এখানে এই যে Array; আমার parent. তার prototype এর মধ্যে মেথডগুলো আছে। that's why এগুলো আমি(persons) ব্যবহার করতে পারছি।

তার মানে আমরা যখন একটা object create করছি কোনো একটা object থেকে, তখন সে আসলে তার পেরেন্টের মধ্যে যে property method যা আছে সবকিছু সে inherit করছে, নিয়ে আসছে। এবং সেটাতে তার access থাকছে। শুধু তাই না! তার child তারও child ও কিন্তু সেগুলোকে access করতে পারে। যদি আমি এভাবে create করতে করতে যাই। তো এটাকে আসলে prototype chain ও বলা হয়।
JavaScript হচ্ছে web এর accembly language. JavaScript ছাড়া Website কল্পনাই করা যায় না …………..

