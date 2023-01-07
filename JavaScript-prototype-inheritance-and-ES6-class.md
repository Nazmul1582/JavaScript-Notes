 <br />
 <p align="center">
    <h1 align="center">JavaScript prototype inheritance and ES6 class</h1>
</p>

### Table of Contents

- [Prototype Inheritance](#prototype-inheritance)

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
কিন্তু `eat()` ফাংশনটা একটা ফাংশনের বডি, রেফারেন্স। এটাতো মেমোরিতে একটা জায়গা নিচ্ছে। কারণ দুইটা অবজেক্টের মধ্যেই `eat()` ফাংশনটা আছে। তার মানে আমার যদি আরো এরকম অসংখ্য মেথড থাকতো; যে মেথডগুলো আসলে কমন প্রপার্টি; যেটাকে এই `Person` থেকে ক্রিয়েক হওয়া সব অবজেক্টই ইউজ করে, তাহলে আমার অবজেক্টের সাইজগুলো বড় হয়ে যাবে এবং মেমোরিতে জায়গা বেশি নিবে। So, এখান থেকে বের হয়ে আসার জন্য আমরা Prototype ইউজ করেছিলাম।
