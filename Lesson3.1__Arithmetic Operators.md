# JavaScript Arithmetic Operators

Arithmetic operators perform arithmetic on numbers (literals or variables).

Arithmetic (পাটিগনিত) => `+`, `-`, `*`, `**`, `/`, `%`, `++`, `--`

| Operator | Description             |
| -------- | ----------------------- |
| `+`      | Addition                |
| `-`      | Subtraction             |
| `*`      | Multiplication          |
| `**`     | Exponentiation (ES2016) |
| `/`      | Division                |
| `%`      | Modulus (Remainder)     |
| `++`     | Increment               |
| `--`     | Decrement               |

## Adding

The addition operator (`+`) adds numbers:

```javascript
console.log(10 + 20); // result => 30;
const a = 5;
const b = 10;
const res = a + b;
console.log(res); // result => 15;
```

## Subtracting

The subtraction operator (`-`) subtracts numbers.

```javascript
console.log(10 - 5); // result => 5;
const a = 15;
const b = 5;
const res = a - b;
console.log(res); // result => 10;
```

## Multiplying

The multiplication operator (`*`) multiplies numbers.

```javascript
console.log(10 * 5); // result => 50;
const a = 15;
const b = 5;
const res = a * b;
console.log(res); // result => 75;
```

## Dividing

The division operator (`/`) divides numbers.

```javascript
console.log(10 / 5); // result => 2;
const a = 15;
const b = 10;
const res = a / b;
console.log(res); // result => 1.5;
```

## পাঁচমিশালী

```javascript
// how to exchange value between two variables
let num1 = 10;
let num2 = 15;

let temp = num1;
num1 = num2;
num2 = temp;
console.log(num1);
console.log(num2);
```

```javascript
// how to exchange value between two variables by arithmetic operator
let num1 = 10;
let num2 = 15;
let num3 = num1 + num2;

num1 = num3 - num1;
num2 = num3 - num2;
```

## Remainder

The modulus operator (`%`) returns the division remainder.

```javascript
console.log(11 % 5); // result => 1;
const a = 15;
const b = 10;
const res = a % b;
console.log(res); // result => 5;
```

```javascript
// how to get 12 from 125
let num = 125;
let reminder = num % 10;
let res = (num - reminder) / 10; // result => 12;
```

```javascript
// how to get the middle number from a number like: 12345 => 5

let a = 12345;
let b = a % 100;
let c = (a - b) / 100;
let res = c % 10; // result => 3;
```

## Incrementing

The increment operator (`++`) increments numbers.

### prefix or pre increment

pre increment সাথে সাথে increment করে দেয়। অর্থাৎ, যে লাইনে `++a` লেখা হয়, সে লাইনেই `a` ‍এর value ১ বেড়ে যায়।

```javascript
let a = 10;
++a; // here a = 11;
console.log(a); // here a = 11;
console.log(a); // here a = 11;
```

### postfix or post increment

post increment সাথে সাথে increment করে না। পরের বার increment করে। অর্থাৎ, যে লাইনে `a++` লেখা হয়, সে লাইনেই `a` ‍এর value বাড়ে না। পরের বার যখন `a` লেখা হয়, তখন `a` ‍এর value ১ বেড়ে যায়।

```javascript
let a = 10;
a++; // here a = 10;
console.log(a); // here a = 11;
console.log(a); // here a = 11;
```

## Decrementing

The decrement operator (`--`) decrements numbers.

### prefix or pre decrement

pre decrement সাথে সাথে decrement করে দেয়। অর্থাৎ, যে লাইনে `--a` লেখা হয়, সে লাইনেই `a` ‍এর value ১ কমে যায়।

```javascript
let a = 10;
--a; // here a = 9;
console.log(a); // 9;
console.log(a); // 9
```

### postfix or post decrement

post decrement সাথে সাথে decrement করে না। পরের বার decrement করে। অর্থাৎ, যে লাইনে `a--` লেখা হয়, সে লাইনেই `a` ‍এর value কমে না। পরের বার যখন `a` লেখা হয়, তখন `a` ‍এর value ১ কমে যায়।

```javascript
let a = 10;
a--; // here a = 10;
console.log(a); // here a = 9;
console.log(9); // here a = 9;
```

## Exponentiation

The exponentiation operator (`**`) raises the first operand to the power of the second operand.

```javascript
let a = 2;
let b = 5;
console.log(a ** b); // (2)^5     => 32

// x ** y produces the same result as Math.pow(x,y)
console.log(Math.pow(2, 5)); // (2)^5     => 32
```

## Operator Precedence

Operator precedence describes the order in which operations are performed in an arithmetic expression.

- As in traditional school mathematics, the multiplication is done first.
  Multiplication (`*`) and division (`/`) have higher precedence than addition (`+`) and subtraction (`-`).

```javascript
let cal = 10 + 5 * 3;
console.log(cal); // result => 10 + 15 => 25
```

- When using parentheses, the operations inside the parentheses are computed first:

```javascript
let cal = (10 + 5) * 3;
console.log(cal); // result => 15 * 3 => 45
```

- When many operations have the same precedence (like addition and subtraction or multiplication and division), they are computed from left to right:

```javascript
let cal = (10 / 4) * 5;
console.log(cal); // result => 2.5 * 5 => 12.5
```

```javascript
let cal = (10 * 4) / 5;
console.log(cal); // result => 40 / 5 => 8
```
