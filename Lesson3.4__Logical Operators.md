# Logical Operators

logical operators are `&&` , `||` , `!`. (mainly 2ta: `&&`, `||`)

logical operator boolean value নিয়ে কাজ করে।

- or (`||`) operator এর ক্ষেত্রে ১টা `true` হলে পুরো result-ই `true` হবে।

```javaScript
true || false  // result (1 + 0 = 1)  => true
true || true  // result (1 + 1 = 1)   => true
false || true  // result (0 + 1 = 1)  => true
false || false  // result (0 + 0 = 0) => false
```

- and (`&&`) operator এর ক্ষেত্রে ১টা `false` হলে পুরো result-ই `false` হবে।

```javaScript
true && false  // result (1x0 = 0)  => true
true && true  // result (1x1 = 1)   => true
false && true  // result (0x1 = 0)  => true
false && false  // result (0x0 = 0) => false
```

```javascript
let a = false;
console.log(!a); // true;
```

### use of logical operators

```javascript
let a = 8,
  b = 7,
  c = 0;
a == c || c > a; // result => false
a !== c || c < a; // result => true
!(a == c) || c < a; // result => true   => (!false || true => true || true => true)

let d = true;
console.log(!d); // result =>  false
```
