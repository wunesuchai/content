[console-export-2022-10-29_5-43-27.txt](https://github.com/mdn/content/files/9897088/console-export-2022-10-29_5-43-27.txt)
[console-export-2022-10-31_4-32-35.txt](https://github.com/mdn/content/files/9897089/console-export-2022-10-31_4-32-35.txt)
[console-export-2022-10-31_4-32-45.txt](https://github.com/mdn/content/files/9897090/console-export-2022-10-31_4-32-45.txt)
![notification-ok](https://user-images.githubusercontent.com/115897626/198908485-e7b59b6e-433c-4cf0-9be6-78c77b3a5b41.svg)
[README.md](https://github.com/mdn/content/files/9897091/README.md)
[README.md](https://github.com/mdn/content/files/9897092/README.md)
![ทฤษฏีการจับคู่สี-ที่หลายๆ-คนอาจลืมไปแล้ว-4 (1)](https://user-images.githubusercontent.com/115897626/198908504-328e2c5c-384e-4ac8-b797-7c9fa31ad838.jpg)
---
title: 'SyntaxError: Unexpected token'
slug: Web/JavaScript/Reference/Errors/Unexpected_token
tags:
  - Error
  - Errors
  - JavaScript
  - SyntaxError
---

{{jsSidebar("Errors")}}

The JavaScript exceptions "unexpected token" occur when a specific language construct
was expected, but something else was provided. This might be a simple typo.

## Message

```
SyntaxError: expected expression, got "x"
SyntaxError: expected property name, got "x"
SyntaxError: expected target, got "x"
SyntaxError: expected rest argument name, got "x"
SyntaxError: expected closing parenthesis, got "x"
SyntaxError: expected '=>' after argument list, got "x"
```

## Error type

{{jsxref("SyntaxError")}}

## What went wrong?

A specific language construct was expected, but something else was provided. This might
be a simple typo.

## Examples

### Expression expected

For example, when chaining expressions, trailing commas are not allowed.

```js example-bad
for (let i = 0; i < 5,; ++i) {
  console.log(i);
}
// Uncaught SyntaxError: expected expression, got ';'
```

Correct would be omitting the comma or adding another expression:

```js example-good
for (let i = 0; i < 5; ++i) {
  console.log(i);
}
```

### Not enough brackets

Sometimes, you leave out brackets around `if` statements:

```js example-bad
function round(n, upperBound, lowerBound) {
  if (n > upperBound) || (n < lowerBound) { // Not enough brackets here!
    throw new Error(`Number ${n} is more than ${upperBound} or less than ${lowerBound}`);
  } else if (n < (upperBound + lowerBound) / 2) {
    return lowerBound;
  } else {
    return upperBound;
  }
} // SyntaxError: expected expression, got '||'
```

The brackets may look correct at first, but note how the `||` is outside the
brackets. Correct would be putting brackets around the `||`:

```js example-good
function round(n, upperBound, lowerBound) {
  if ((n > upperBound) || (n < lowerBound)) {
    throw new Error(`Number ${n} is more than ${upperBound} or less than ${lowerBound}`);
  } else if (n < (upperBound + lowerBound) / 2) {
    return lowerBound;
  } else {
    return upperBound;
  }
}
```

## See also

- {{jsxref("SyntaxError")}}
