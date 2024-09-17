# Table of Contents 
1. STRING
2. NUMBERS
----
# JavaScript String Methods
### Javascript strings are primitive and immutable: All string methods produce a new string without altering the original string.
* String length    
* String charAt()
* String charCodeAt()
* String at()
* String [ ]
* String slice()
* String substring()
* String substr()
* String toUpperCase()
* String toLowerCase()
* String concat()
* String trim()
* String trimStart()
* String trimEnd()
* String padStart()
* String padEnd()
* String repeat()
* String replace()
* String replaceAll()
* String split()
---
# See Also:    
* String Search Methods
* String Templates
---
# JavaScript String Length
### The length property returns the length of a string:
* let text = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
* let length = text.length;
---
# Extracting String Characters
### There are 4 methods for extracting string characters:
* The at(position) Method
* The charAt(position) Method
* The charCodeAt(position) Method
* Using property access [] like in arrays
---
# JavaScript String charAt()
### The charAt() method returns the character at a specified index (position) in a string:
* let text = "HELLO WORLD";
* let char = text.charAt(0);
---
# JavaScript String charCodeAt()
#### The charCodeAt() method returns the code of the character at a specified index in a string:
#### The method returns a UTF-16 code (an integer between 0 and 65535).
* let text = "HELLO WORLD";
* let char = text.charCodeAt(0);
--- 
# JavaScript String at()
#### ES2022 introduced the string method at():
#### Get the third letter of name:
* const name = "W3Schools";
* let letter = name[2];
### The at() method returns the character at a specified index (position) in a string.
### The at() method is supported in all modern browsers since March 2022:
---
# Note
* The at() method is a new addition to JavaScript.
* It allows the use of negative indexes while charAt() do not.
* Now you can use myString.at(-2) instead of charAt(myString.length-2).
---
# Number
### Number values represent floating-point numbers like 37 or -9.25.
### The Number constructor contains constants and methods for working with numbers. Values of other
### types can be converted to numbers using the Number() function.
---
# Description
### Numbers are most commonly expressed in literal forms like 255 or 3.14159. The lexical grammar contains a more detailed reference.
![alt text](<Снимок экрана 2024-09-17 130451-1.png>)
### A number literal like 37 in JavaScript code is a floating-point value, not an integer. There is no separate integer type in common everyday use. (JavaScript also has a BigInt type, but it's not designed to replace Number for everyday uses. 37 is still a number, not a BigInt.)
### When used as a function, Number(value) converts a string or other value to the Number type. If the value can't be converted, it returns NaN.
![alt text](<Снимок экрана 2024-09-16 133653-1.png>)
---
# Number encoding
### The JavaScript Number type is a double-precision 64-bit binary format IEEE 754 value, like double in Java or C#. This means it can represent fractional values, but there are some limits to the stored number's magnitude and precision. Very briefly, an IEEE 754 double-precision number uses 64 bits to represent 3 parts:
* 1 bit for the sign (positive or negative)
* 11 bits for the exponent (-1022 to 1023)
* 52 bits for the mantissa (representing a number between 0 and 1)
### The mantissa (also called significand) is the part of the number representing the actual value (significant digits). The exponent is the power of 2 that the mantissa should be multiplied by. Thinking about it as scientific notation:
### The mantissa is stored with 52 bits, interpreted as digits after 1.… in a binary fractional number. Therefore, the mantissa's precision is 2-52 (obtainable via Number.EPSILON), or about 15 to 17 decimal places; arithmetic above that level of precision is subject to rounding.
### The largest value a number can hold is 21023 × (2 - 2-52) (with the exponent being 1023 and the mantissa being 0.1111… in base 2), which is obtainable via Number.MAX_VALUE. Values higher than that are replaced with the special number constant Infinity.
### Integers can only be represented without loss of precision in the range -253 + 1 to 253 - 1, inclusive (obtainable via Number.MIN_SAFE_INTEGER and Number.MAX_SAFE_INTEGER), because the mantissa can only hold 53 bits (including the leading 1).

### More details on this are described in the ECMAScript standard.
---
# Number coercion
### Many built-in operations that expect numbers first coerce their arguments to numbers (which is largely why Number objects behave similarly to number primitives). The operation can be summarized as follows:
* Numbers are returned as-is.
* undefined turns into NaN.
* null turns into 0.
* true turns into 1; false turns into 0.
* Strings are converted by parsing them as if they contain a number literal. Parsing failure results
### in NaN. There are some minor differences compared to an actual number literal:
### Leading and trailing whitespace/line terminators are ignored.
### A leading 0 digit does not cause the number to become an octal literal (or get rejected in strict mode).
### + and - are allowed at the start of the string to indicate its sign. (In actual code, they "look like" part of the literal, but are actually separate unary operators.) However, the sign can only appear once, and must not be followed by whitespace.
### Infinity and -Infinity are recognized as literals. In actual code, they are global variables.
### Empty or whitespace-only strings are converted to 0.
### Numeric separators are not allowed.
* BigInts throw a TypeError to prevent unintended implicit coercion causing loss of precision.
* Symbols throw a TypeError.
* Objects are first converted to a primitive by calling their [Symbol.toPrimitive]() (with "number" as hint), valueOf(), and toString() methods, in that order. The resulting primitive is then converted to a number.
### There are two ways to achieve nearly the same effect in JavaScript.
* Unary plus: +x does exactly the number coercion steps explained above to convert x. 
* The Number() function: Number(x) uses the same algorithm to convert x, except that BigInts don't throw a TypeError, but return their number value, with possible loss of precision.
### Number.parseFloat() and Number.parseInt() are similar to Number() but only convert strings, and have slightly different parsing rules. For example, parseInt() doesn't recognize the decimal point, and parseFloat() doesn't recognize the 0x prefix.
---
# Integer conversion
### Some operations expect integers, most notably those that work with array/string indices, date/time components, and number radixes. After performing the number coercion steps above, the result is truncated to an integer (by discarding the fractional part). If the number is ±Infinity, it's returned as-is. If the number is NaN or -0, it's returned as 0. The result is therefore always an integer (which is not -0) or ±Infinity.
### Notably, when converted to integers, both undefined and null become 0, because undefined is converted to NaN, which also becomes 0.
---
# Fixed-width number conversion
### JavaScript has some lower-level functions that deal with the binary encoding of integer numbers, most notably bitwise operators and TypedArray objects. Bitwise operators always convert the operands to 32-bit integers. In these cases, after converting the value to a number, the number is then normalized to the given width by first truncating the fractional part and then taking the lowest bits in the integer's two's complement encoding.
![alt text](<Снимок экрана 2024-09-17 132202-1.png>)
---
# Static properties
1. Number.EPSILON
* The smallest interval between two representable numbers.
2. Number.MAX_SAFE_INTEGER
* The maximum safe integer in JavaScript (253 - 1).
3. Number.MAX_VALUE
* The largest positive representable number.
4. Number.MIN_SAFE_INTEGER
* The minimum safe integer in JavaScript (-(253 - 1)).
5. Number.MIN_VALUE
* The smallest positive representable number—that is, the positive number closest to zero (without actually being zero).
6. Number.NaN
* Special "Not a Number" value.
7. Number.NEGATIVE_INFINITY
* Special value representing negative infinity. Returned on overflow.
8. Number.POSITIVE_INFINITY
* Special value representing infinity. Returned on overflow.
---
# Static methods

1. Number.isFinite()
* Determine whether the passed value is a finite number.
2. Number.isInteger()
* Determine whether the passed value is an integer.
3. Number.isNaN()
* Determine whether the passed value is NaN.
4. Number.isSafeInteger()
* Determine whether the passed value is a safe integer (number between -(253 - 1) and 253 - 1).
5. Number.parseFloat()
* This is the same as the global parseFloat() function.
6. Number.parseInt()
* This is the same as the global parseInt() function.
--- 
# Instance properties
### These properties are defined on Number.prototype and shared by all Number instances.
* Number.prototype.constructor
### The constructor function that created the instance object. For Number instances, the initial value is the Number constructor.
---
# Instance methods
1. Number.prototype.toExponential()
* Returns a string representing the number in exponential notation.
2. Number.prototype.toFixed()
* Returns a string representing the number in fixed-point notation.
3. Number.prototype.toLocaleString()
* Returns a string with a language sensitive representation of this number. Overrides the
4. Object.prototype.toLocaleString() method.
5. Number.prototype.toPrecision()
* Returns a string representing the number to a specified precision in fixed-point or exponential notation.
6. Number.prototype.toString()
* Returns a string representing the specified object in the specified radix ("base"). Overrides the
7. Object.prototype.toString() method.
8. Number.prototype.valueOf()
* Returns the primitive value of the specified object. Overrides the Object.prototype.valueOf() method.
---
# What is a Method in JavaScript?
### A method is a block of code which only runs when
it is called. You can pass data, known as
parameters, into a method. Methods are used to
perform certain actions, and they are also known
as functions.
---
---
# Thanks! Thanks! Thanks!
---