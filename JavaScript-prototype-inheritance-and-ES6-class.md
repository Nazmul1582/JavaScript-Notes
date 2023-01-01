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

- JavaScript এ কোন একটা function যখন আমরা লিখি, সেই function এর মধ্যে আমরা এরকম `this` দিয়ে সেইটার property কে access করতে পারি(`this.name = name`)। কারণ JavaScript যেহেতু একটা functional programming language, functional programming language এ function কিন্তু অনেক কিছুই করে। like: function মানে কিন্তু শুধু কাজ করা না। যেমন: এক্ষেত্রে function (Person) কাজ করছে কিন্তু একটা কাঠামো হিসেবে। সে কিন্তু কোনো কাজ করছে না। আমি জাস্ট এই (Person) function টাকে একটা কাঠামো হিসেবে use করছি এবং person নতুন একজন person তৈরি করছে এখানে sakib নামে। এবং new keyword use করে করছি। এখানে কিন্তু function জাস্ট call হচ্ছে না; এখানে function টা একটা কাঠামো হিসেবে কাজ করছে, (নতুন একটা object তৈরি করার কাজে use হচ্ছে।) এবং নতুন মানে
