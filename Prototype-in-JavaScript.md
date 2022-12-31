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
  (person.age = age),
    (person.eat = function () {
      console.log(`${this.name} is eating`);
    }),
    (person.sleep = function () {
      console.log(`${this.name} is sleeping`);
    });
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
