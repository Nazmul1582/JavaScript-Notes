# Comparision Operators

| Operator | Description                       |
| -------- | --------------------------------- |
| `==`     | equal to                          |
| `===`    | equal value and equal type        |
| `!=`     | not equal                         |
| `!==`    | not equal value or not equal type |
| `<`      | less than                         |
| `>`      | greater than                      |
| `<=`     | less than or equal to             |
| `>=`     | greater than or equal to          |

- number এর সাথে boolean compare করলে `true = 1` and `false = 0` হয়ে যায়।

```javascript
let a, b, c;
a = 5;
b = 7;
c = 9;

a < b < c; // result = true
c > b > a; // result = false => [ c > b > a => true(1) > 5 => false]

8 < 7 == 0; // result true;
8 < 7 === 0; // result false
/* 
এখানে  8 < 7 = false যার value 0, 
কিন্তু 8 < 7 = false এটার type boolean, আর ডানপাশের 0 একটি number
তাই 0 === 0 এর result হবে false
*/
```

## String comparision

- প্রত্যকটা letter এর একটা নির্দিষ্ট ASCII আছে।
  `a = 97`, `z = 122`
  `A = 65`, `Z = 90`
  _কিবোর্ড ‍এ ‍Alt + 65 একসাথে চাপলে A লেখা উঠবে।_

```javascript
let str1 = "a";
let str2 = "b";

console.log(str1 == str2); // false
console.log(str1 < str2); // true
console.log("b" < "ac"); // false
// String comparision word এর letter সংখ্যা দেখে না। ১ম letter(b) এর সাখে ২য় letter (a) এর  compare করে false return করেছে। (ac) এর c আর check করেনি। ১ম letter == ১ম letter একই হলে check করত।
```

```javascript
"bd" < "ac"; // false
"ba" < "s"; // true
"bd" < "bc"; // false
"bd" < "be"; // true

"a" < "A"; // false    (a = 97, A = 65)
"pastgjqerhiofgjhqos" < "q"; // true

let a = 54654654654654;
let b = "q";
console.log(a < b); // true
```
