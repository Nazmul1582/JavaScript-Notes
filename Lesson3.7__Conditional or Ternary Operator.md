# Conditional (ternary) operator

```javascript
Ternary operator =>  condition ? trueExpression : falseExpression
```

```javascript
const status = age >= 18 ? "adult" : "minor";
// এক্ষেত্রে age যদি 18 বা তার থেকে বেশি হয় তাহলে output হবে adult. কিন্তু age যদি 18 থেকে কম হয় তাহলে output হবে minor
```

```javascript
let marks = 50;
let result = marks >= 80 ? "Excellent" : marks >= 60 ? "Good" : "Do better";
console.log(result); // Do better
// makes = 70 হলে output হবে Good
// makes = 90 হলে output হবে Do better
```
