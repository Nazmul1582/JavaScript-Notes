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
