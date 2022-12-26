### Table of content

- [JavaScript Type Conversion](#javascript-type-conversion)
  - [JavaScript Implicit Conversion](#javascript-implicit-conversion)
  - [JavaScript Explicit Conversion](#javascript-explicit-conversion)
  - [Convert into String](#convert-into-string)
  - [Convert into Number](#convert-into-number)
  - [Convert into Boolean](#convert-into-boolean)
  - [JavaScript Type Conversion Table](#javascript-type-conversion-table)

# JavaScript Type Conversion

There are two types of type conversion in JavaScript.

- Implicit Conversion - automatic type conversion
- Explicit Conversion - manual type conversion

## JavaScript Implicit Conversion

In certain situations, JavaScript automatically converts one data type to another (to the right type). This is known as implicit conversion.

Example 1: Implicit Conversion to String

```javascript
// numeric string used with + gives string type
let result;
result = "3" + 2;
console.log(result); // "32"

result = "3" + true;
console.log(result); // "3true"
```

Example 2: Implicit Conversion to Number

```javascript
// numeric string used with - , / , * results number type
let result;

result = "4" - "2"; // 2

result = "4" - 2; // 2
```

Example 3: Non-numeric String Results to NaN

```javascript
// non-numeric string used with - , / , * results to NaN

let result;

result = "hello" - "world"; // NaN

result = "4" - "hello"; // NaN
```

Example 4: Implicit Boolean Conversion to Number

```javascript
// if boolean is used, true is 1, false is 0

let result;

result = "4" - true; // 3

result = 4 + false; // 4
```

Example 5: null Conversion to Number

```javascript
// null is 0 when used with number
let result;

result = 4 + null; // 4

result = 4 - null; // 4
```

Example 6: undefined used with number, boolean or null

```javascript
// Arithmetic operation of undefined with number, boolean or null gives NaN

let result;

result = 4 + undefined; // NaN

result = true + undefined; // NaN

result = null + undefined; // NaN
```

## JavaScript Explicit Conversion

You can also convert one data type to another as per your needs. The type conversion that you do manually is known as explicit type conversion. In JavaScript, explicit type conversions are done using built-in methods.

Here are some common methods of explicit conversions: `toString()`, `String()`, `Number()`, `Boolean()` etc.

## Convert into String

### String constructor

```javascript
const num = 3.1416;
const str = String(num); // typeof num => string

const str = String(10 + 5 * 3);

const boolean = true;
const str = String(boolean);
```

### toString()

```javascript
const num = 100;
const str = num.toString(); // typeof str => string

const boolean = Infinity;
const str = boolean.toString(); // typeof str = string
```

## Convert into Number

### Number constructor

```javascript
let str = "Hello";
let num = Number(str); // NaN =>  typeof num => number

let str2 = "100";
let num2 = Number(str2); // 100      => typeof num2 => number

let b = false;
let b2n = Number(b); // 0  => typeof b2n => number

let u = undefined;
let u2n = Number(u); // NaN  => typeof u2n => number
```

### parseInt();

```javascript
const a = "25.34845";
const b = parseInt(a); //    25 =>  typeof b => number
```

### parseFloat();

```javascript
const a = "40.456";
const b = parseFloat(a); //    40.456 =>  typeof b => number
```

### JavaScript Dates to Numbers

Example: Convert Date to Number

```javascript
// program to convert date to number
// create date
const d1 = new Date();
console.log(d1);

// converting to number
const result = d1.getTime();
console.log(result);
```

### JavaScript Dates to String

Example: Convert Date to string

```javascript
Example : Display Current Date
// program to display the date
// get local machine date time
const date = new Date();

// get the date as a string
const n = date.toDateString();

// get the time as a string
const time = date.toLocaleTimeString();

// display date
console.log('Date: ' + n);

// display time
console.log('Time: ' + time);
```

## Convert into Boolean

```javascript
const a = 0;
const b = Boolean(a); //    false =>  typeof b => boolean

const c = "";
const d = Boolean(c); //    false =>  typeof b => boolean

const e = "Hello";
const f = Boolean(e); // true => typeof f => boolean
```

## JavaScript Type Conversion Table

The table shows the conversion of different values to String, Number, and Boolean in JavaScript.

| Value     | String Conversion | Number Conversion | Boolean Conversion |
| --------- | ----------------- | ----------------- | ------------------ |
| 1         | "1"               | 1                 | true               |
| 0         | "0"               | 0                 | false              |
| "1"       | "1"               | 1                 | true               |
| "0"       | "0"               | 0                 | true               |
| "ten"     | "ten"             | NaN               | true               |
| true      | "true"            | 1                 | true               |
| false     | "false"           | 0                 | false              |
| null      | "null"            | 0                 | false              |
| undefined | "undefined"       | NaN               | false              |
| ''        | ""                | 0                 | false              |
| ' '       | " "               | 0                 | true               |

## Falsy value

falsy values are: `""`, `0`, `false`, `null`, `undefined`, `NaN`

```javascript
Boolean(""); // output: false
Boolean(0); // output: false
Boolean(false); //output: false
Boolean(null); // output: false
Boolean(undefined); // output: false
Boolean(NaN); // output: false

Boolean(" "); // output: true
Boolean("0"); // output: true
Boolean(Infinity); // output: true
Boolean(-Infinity); // output: true
```
