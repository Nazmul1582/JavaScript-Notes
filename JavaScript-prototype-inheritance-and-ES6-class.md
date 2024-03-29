 <br />
 <p align="center">
    <h1 align="center">JavaScript prototype inheritance and ES6 class</h1>
</p>

### Table of Contents

- [Prototype Inheritance](#prototype-inheritance)
  - [Summary of prototype](#summary-of-prototype)

## Prototype Inheritance

```javascript
// prototype এর recap
function Person(name, age) {
  this.name = name;
  this.age = age;
}
const sakib = new Person("Sakib", 35);
```

- JavaScript এ কোন একটা function যখন আমরা লিখি, সেই function এর মধ্যে আমরা এরকম `this` দিয়ে সেইটার property কে access করতে পারি(`this.name = name`)। কারণ JavaScript যেহেতু একটা functional programming language, functional programming language এ function কিন্তু অনেক কিছুই করে। like: function মানে কিন্তু শুধু কাজ করা না। যেমন: এক্ষেত্রে function (`Person`) কাজ করছে কিন্তু একটা কাঠামো হিসেবে। সে কিন্তু কোনো কাজ করছে না। আমি জাস্ট এই (`Person`) function টাকে একটা কাঠামো হিসেবে use করছি এবং person নতুন একজন person তৈরি করছে এখানে sakib নামে। এবং new keyword use করে করছি। এখানে কিন্তু function জাস্ট call হচ্ছে না; এখানে function টা একটা কাঠামো হিসেবে কাজ করছে, (নতুন একটা object তৈরি করার কাজে use হচ্ছে।)
- এখন যদি আমরা `Person` ফাংশনে একটা নতুন মেথড (`eat()`) এড করি, তাহলে:

```javascript
fuction Person(name, age) {
	this.name = name;
	this.age = age;
	this.eat = function(){
		console.log(`${this.name} is eating.`)
  }
}
const sakib = new Person("Sakib", 35);
const tamim  = new Person("Tamim", 36);
sakib.eat(); // Sakib is eating.
tamim.eat() // Tamim is eating.
```

কিন্তু এই প্রসেসের মধ্যে একটা সমস্যা আছে। সমস্যাটা কি?
আমরা যদি এখানে `console.log()` করি:

```javascript
const sakib = new Person("Sakib", 35);
console.log(sakib);
const tamim = new Person("Tamim", 36);
console.log(tamim);
```

এটা সেপারেট অবজেক্ট প্রিন্ট হয়েছে। এবং দুইটার মধ্যেই `eat()` ফংশনটা আছে।
কিন্তু `eat()` ফাংশনটা একটা ফাংশনের বডি, রেফারেন্স। এটাতো মেমোরিতে একটা জায়গা নিচ্ছে। কারণ দুইটা অবজেক্টের মধ্যেই `eat()` ফাংশনটা আছে। তার মানে আমার যদি আরো এরকম অসংখ্য মেথড থাকতো; যে মেথডগুলো আসলে কমন প্রপার্টি; যেটাকে এই `Person` থেকে ক্রিয়েক হওয়া সব অবজেক্টই ইউজ করে, তাহলে আমার অবজেক্টের সাইজগুলো বড় হয়ে যাবে এবং মেমোরিতে জায়গা বেশি নিবে। So, এখান থেকে বের হয়ে আসার জন্য আমরা Prototype ইউজ করেছিলাম:

```javascript
Person.prototype{
	eat: function(){
		console.log(`${this.name} is eating.`);
  }
}
```

```javascript
fuction Person(name, age) {
	this.name = name;
	this.age = age;
	this.eat = function(){
		console.log(`${this.name} is eating.`)
  }
}

Person.prototype{
	eat: function(){
		console.log(`${this.name} is eating.`);
  }
}

const sakib = new Person("Sakib", 35);
console.log(sakib);
const tamim  = new Person("Tamim", 36);
console.log(tamim);

```

এখানে `Person` একটা ফাংশন। আমরা জানি যে ফাংশানের মধ্যে `prototype` বলে একটা প্রপার্টি থাকে। আমরা যদি `eat()` ফাংশনটাকে `Person` থেকে বের করে এই `prototype` এর মধ্যে রেখে দেই, তাহলে আউটপুট একই আসবে। এখন কিন্তু `eat()` ফাংশনটা দুজনের (`sakib`, `tamim`) মধ্যে নাই। সে আসলে `__proto__` র মধ্যে ঢুকে গেছে। তার মানে সে এই কাঠামো (`Person`) থেকে অবজেক্টটাকে রেফার করছে; বারবার কিন্তু সে নতুন নতুন অবজেক্টের মধ্যে `eat()` ফাংশনটাকে দিয়ে দিচ্ছে না। তাতে আমার অবজেক্ট সাইজগুলো ছোট হচ্ছে এবং কমন প্রপার্টিগুলো একটা জেনারিক কাঠামোর মধ্যে থাকছে। এই ছিল প্রটোটাইপের সামারি।

## Summary of prototype

`prototype` হচ্ছে সিম্পলি ফাংশনের একটা প্রপার্টি, জাভাস্ক্রিপ্টের। সেই প্রপার্টিটা কোন একটা অবজেক্টকে পয়েন্ট করে। সেই প্রপার্টির মধ্যে যা থাকবে, আমি যদি ওই ফাংশন থেকে কোন নতুন অবজেক্ট তৈরি করি তাহলে সেই অবজেক্টগুলো প্রটোটাইপের মধ্যে থাকা সব কিছু পেয়ে যাবে।

## Inheritance and Class

### Prototype Inheritance

```javascript
function Person(name, age) {
	this.name = name;
	this.age = age;
}
const sakib = new Person(“Sakib”, 35);
```

- Java তে আমরা একটা `class` তৈরি করি। সেই `class` থেকে আমরা `new ClassName()` এর মাধ্যমে অবজেক্ট তৈরি করি।
- মানে জাভাতে যদি এই কোডটা লিখতাম তাহলে class Person: `new Person()` থাকতো, function Person না।
  কিন্তু জাভাস্ক্রিপ্টে আমরা ফাংশন থেকে (আসলে ফাংশন থেকে না কনস্ট্রাক্টর থেকে) অবজেক্ট তৈরি করি।
  তার মানে জাভাস্ক্রিপ্টে বাই ডিফল্ট every function is a constructor.
  -কনভেনশন হচ্ছে: যখনই আমরা কোনো constructor ফাংশন explicitly বুঝাতে যাবো, তখন আমরা ক্যামেল কেইসে (Person) লিখব।
- জাভাস্ক্রিপ্টের কাছে যেহেতু ফাংশনও একটা অবজেক্ট, তাই `new` কিওয়ার্ড বুঝতে পারে। নিউ আবজেক্ট করার মতই করছে সে আসলে। দেখতে অনেকটা ক্লাসের মতো দেখাচ্ছে।
- জাভাস্ক্রিপ্ট যেটা করছে: ডাইরেক্ট এই কনস্ট্রাক্টর থেকে আমরা অবজেক্ট বানাতে পারছি। জাস্ট `new Person()`) কল করে দিচ্ছি। একদম বলতে গেলে এটা একটা constructor function.

**Master Object:**
জাভাস্ক্রিপ্টে ফাংশন ও একটা অবজেক্ট। আমরা যদি একটা অবজেক্ট ক্রিয়েট করি:

```javascript
var f = function Person() {};
console.dir(f);
```

এখানে আমরা ফাংশনটাকে `console.dir(f)` করলে দেখব, এর একটা `__proto__` আছে এবং সেই প্রোটোর মধ্যে আরেকটা `__proto__`:Object আছে। এটা হচ্ছে master objects। `Object.create()` একটা master object. জাভাস্ক্রিপ্টের সব অবজেক্টই (ফাংশনে একটি অবজেক্ট) এই মাস্টার অবজেক্ট থেকে তৈরি হয়।

**Prototype Chain:**

এখানে মাস্টার অবজেক্ট থেকে প্রথমে ফাংশন ক্রিয়েট হয়েছে। তারপর ফাংশন প্রোটো থেকে আমাদের এই `f` টা ক্রিয়েট হয়েছে (যেটা আমি `f` এর মধ্যে রেখেছি সেটা ক্রিয়েট হয়েছে)।

- যদি পুরো জিনিসটাকে ভিজুয়ালাইজ করি তাহলে জিনিসটা এরকম দাঁড়ায়।

এটা অবজেক্ট। অবজেক্ট থেকে ফাংশন ক্রিয়েট হয়েছে। ফাংশন থেকে `f` ক্রিয়েট হয়েছে। প্রত্যেকটা জিনিসের মধ্যে আবার তাদের নিজস্ব প্রোটোটাই প্রপার্টি আছে। এবং প্রত্যেকটা প্রোটোটাইপের নিজস্ব প্রপার্টি এবং মেথড থাকতে পারে। এই যে জিনিসটা, এই যে একটা চেইনের মত এটাকে বলা হয় প্রোটোটাইপ চেইন।

এখন আমি যদি এই `f` থেকে আরেকটা নতুন অবজেক্ট তৈরি করি তাহল, সেই অবজেক্ট দিয়ে আমি এই প্রোটোটাইপ চেইনের যেকোনো প্রোপার্টি বা মেথড এক্সেস করতে পারব।

ধরলাম আমি `f` থেকে f1 নামে আরেকটা তৈরি করলাম। এখন আমি `f1`. দিয়ে ফাংশন প্রোটো অথবা অবজেক্ট প্রোটোর প্রপারটি এবং মেথডগুলো অ্যাক্সেস করতে পারব।

সে প্রথমে দেখবে এটা `f1` এর মধ্যে আছে কিনা? যদি `f1` এর মধ্যে না থাকে তাহলে সে একধাপ উপরে গিয়ে `f` এর মধ্যে খুঁজবে। `f` এর প্রপার্টি বা মেথডের মধ্যে না থাকলে এক ধাপ উপরে গিয়ে খুঁজবে। এভাবে একদম ফাইনাল মাস্টার অবজেক্ট পর্যন্ত সে যেতে পারে। যার কারণে আমরা যখন কোন built-in ফাংশন ইউজ করি। সেই built-in ফাংশনটা কিন্তু এই মাস্টার অবজেক্ট এর সাথে অ্যাটাস থাকে। যেমন এখানে মাস্টার অবজেক্ট এ `toString`, `toLocaleString` এরকম built-in ফাংশনগুলো আছে।

- আমরা মাস্টার অবজেক্টের কোন প্রপার্টি কিন্তু একদম বাইরে থেকে এক্সেস করতে পারছি। তাই না? তাহলে আমরা কিন্তু নিজেরাই একটা built-in ফাংশন তৈরি করে ফেলতে পারি নিজেদের নামে। যেমন:

```javascript
Object.prototype.nazmul = function () {
  console.log("I am Md. Nazmul Hasan");
};
```

মাস্টার যে অবজেক্টা সেটার প্রোটোটাইপে আমার নামে একটা প্রপার্টি দিলাম। এবং সেটা একটা ফাংশন। তার মানে এই জাভাস্ক্রিপ্ট ফাইলে আমি যত জায়গায়ই চাই `nazmul` ফাংশনটা কে কল করতে পারব। যে কোন অবজেক্ট দিয়ে যে কোন জায়গা থেকে। কারণ এটা তো মাস্টার অবজেক্টে প্রোটোটাইপের মধ্যে মধ্যে ঢুকিয়ে দিয়েছি আমি।

- আমি যদি এখন নতুন একটা অবজেক্ট ক্রিয়েট করি, যেমন:

```javascript
var p = {};
p.nazmul(); // I am Md. Nazmul Hasan
```

- তার মানে এটা সে কেন এক্সেস করতে পারছে? প্রোটোটাইপ চেইনের কারণে।

- জাভাস্ক্রিপ্ট সবকিছু তার অবজেক্টের (Object) মধ্যেই রাখে।
  জাভাস্ক্রিপ্টের সমস্ত অবজেক্ট আল্টিমেটলি মাস্টার অবজেক্ট থেকে আসে।

**Inheritance:**
```javascript
function Person (name, age){
  this.name: name;
  this.age = age;
}
function Cricketer(type, country){
  this.type = type;
  this.country = country;
}
Person.prototype = {
  eat = function(){
    console.log(`${this.name} is eating`)
  }
}

const sakib = new Person("Sakib", 35)
```
জাভাস্ক্রিপ্ট Person আর Cricketer এর মধ্যে  কোনো কানেকশন জানে না। তাই আমাদেরকে ম্যানুয়ালি এই দুইটার মধ্যে কানেকশন করে দিতে হবে যে, sakib আগে একজন Person তারপর সে একজন Cricketer. 
মানে Person তার প্যারেন্ট ক্লাস হবে এবং Cricketer তার সাব-ক্লাস হবে।
সেই কানেকশনটা আমরা কিভাবে তৈরি করব? সেটাই হচ্ছে inheritance. 
এই কানেকশনটা তৈরি করার জন্য ফাস্টে যেটা করব:
আমার উদ্দেশ্য হল, আমি কিন্তু new Person()  করব না, আমি new Cricketer() করব যেন সে Person() এর প্রোপারটিগুলো একবারে নিয়ে নেয়। এটাই হচ্ছে আসলে মেইন গোল। যেটা class based language এ হয়।

এখন new Cricketer() করার আগে কানেকশন করানোর জন্য Cricketer() এর মধ্যে পার্সন কনস্ট্রাক্টর টা কে কল করে দিব, তাহলেই এই বিশিষ্ট গুলো চলে আসবে । আর এটা আমরা করব.  .call() ব্যবহার করে । 

```javascript
function Cricketer(type, country){
	Person.call(this) // মানে পার্সোন এর মধ্যে ক্রিকেটার কে কল করে দেওয়া হলো। অর্থাৎ Cricketer কল হবে পারসন কনটেক্সটে। মানে এই this(Cricketer) টাকে পাঠিয়ে দিবে 
  this.type = type;
  this.country = country;
}
```

Person.call(this) করার কারণে Person()  টা কল হয়ে যাবে। এবং this হিসেবে পাবে Cricketer() এর মধ্যে যে অবজেক্টটা সেইটাকে। এটা করা মানেই হচ্ছে আমার এই দুইটার মধ্যে একটা কানেকশন অটোমেটিক হয়ে গেল। 
একটা কাজ করা কিন্তু আমাদের এখনো বাকি আছে। আর সেটা হচ্ছে: আমরা ক্রিকেটারের প্রভার্টিগুলোকে ইনহেরিট করে নিয়ে এসেছি কিন্তু এরপর প্রোটোটাইপের প্রপার্টিগুলোকে ইনহেরিট করিনি। সেটার জন্য আমরা Object.create() এর বিহেভিয়ারটা ব্যবহার করব। 
Object.create() এর বিহেভিয়ার হল:
```javascript
const a = {  name: "Nazmul" }
const p = Object.create(a)
console.log(p.name) // Nazmul
```
এই বিহেবিয়রটা কাজে লাগিয়ে Person.prototype কে Cricketer এর প্রোটোপাইপের মধ্যে ইনহেরিট করে নিয়ে আসব। 
```javascript
Cricketer.prototype = Object.create(Person.prototype)  
```



