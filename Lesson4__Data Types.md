### Table of Contents

- [JavaScript Data types](#javascript-data-types)
  - [String](#string)
    - [String Literal](#string-literal)
    - [String Constructor](#string-constructor)
  - [Number](#number)
    - [Number Literal](#number-literal)
    - [Number Constructor](#number-constructor)
  - [Null](#null)
  - [Undefined](#undefined)
  - [Symbol](#symbol)

# JavaScript Data types

- There are 2 types of data type in JavaScript.

1. Primitive Data Type
   i. String
   ii. Number
   iii. Boolean
   iv. null ( কোনো value নেই। )
   v. undefined ( define করা হয়নি। )
   vi. symbol ( Symbol() )

2. Object(reference)
   - Array
   - Object
   - Function

 <!-- ================= String ================== -->

# String

## String Literal

```javascript
const str = "Nazmul";
const str2 = "15";
const str3 = " ";
```

## String Constructor

```javascript
const str = String(1000);
const str2 = String(12.25);
```

 <!-- ================= Number ================== -->

# Number

## Number Literal

```javascript
const num = 150
const num2 = 10.50
const num3 = 0.9851654165

const hex = 0xff;
console.log(hex)           result ==> 255

const oct = 0756
console.log(oct)           result ==> 494
```

## Number Constructor

```javascript
const num = Number("1000");
const num2 = Number("12.25");
```

 <!-- ================= Boolean ================== -->

# Boolean

## Boolean Literal

```javascript
const boolean = true;
const boolean2 = false;
```

## Boolean Constructor

```javascript
const bool = Boolean(Infinity)               result ==> true
const bool2 = Boolean(-Infinity)             result ==> true
```

 <!-- ================= Null and Undefined ================== -->

# Null

null => null means no value(কিছুই না)

```javascript
const a = null              result ==> Null/null
```

কোনো variable এ এখন `null` রাখলাম। পরে update করব। `undefined` রাখলে অনেক সময় `Error` হতে পারে। যেমন:

```javascript
console.log(myName);
let myName; // result ==> Error (here: let myName => undefined)
```

# Undefined

undefined => only defined variable

```javascript
const a;
console.log(a)             result ==> undefined
```

 <!-- ================= Symbol ================== -->

# Symbol(ES6)

```javascript
let s1 = Symbol()
let s2 = Symbol()

console.log(s1 === s2)              result ==> false
```

```javascript
let toss = {
  HEAD: Symbol("head"),
  TAIL: Symbol("tail"),
};
```

```javascript
let arr = [1, 2, 3]
let iterate = arr[Symbol.iterator]()

console.log(iterator.next())            result ==> { value: 1, done: false}
console.log(iterator.next())            result ==> { value: 2, done: false}
console.log(iterator.next())            result ==> { value: 3, done: false}
console.log(iterator.next())            result ==> { value: undefined, done: true}
```

```javascript
let str = "TEXT";
let iterateText = str[Symbol.iteratore]()

console.log(iterator.next())            result ==> { value: T, done: false}
console.log(iterator.next())            result ==> { value: E, done: false}
console.log(iterator.next())            result ==> { value: X, done: false}
console.log(iterator.next())            result ==> { value: T, done: false}
console.log(iterator.next())            result ==> { value: undefined, done: true}
```
