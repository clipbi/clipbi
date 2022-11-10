---
title: 'Calculations'
---

# Calculations

We can use calculations in chapter fields or in dataset variables (coming soon).

## Expression Syntax

The expression syntax has operators for all common arithmetic operations such as addition and multiplication. The expression syntax uses conventional infix notation for operators: an operator is placed between its arguments. Round parentheses can be used to override the default precedence of operators.

### Operators

The following operators are available. Note that almost every operator listed also has a function form with identical meaning that can be used interchangeably. For example, x+y will always evaluate identically to add(x,y). For a full list of the equivalences, see the section on Functions below.

| Operator   | Name                        | Syntax      | Associativity | Example              | Result          |
| ---------- | --------------------------- | ----------- | ------------- | -------------------- | --------------- |
| `(`, `)`   | Grouping                    | `(x)`       | None          | `2 * (3 + 4)`        | `14`            |
| `[`, `]`   | Matrix, Index               | `[...]`     | None          | `[[1,2],[3,4]]`      | `[[1,2],[3,4]]` |
| `{`, `}`   | Object                      | `{...}`     | None          | `{a: 1, b: 2}`       | `{a: 1, b: 2}`  |
| `,`        | Parameter separator         | `x, y`      | Left to right | `max(2, 1, 5)`       | `5`             |
| `.`        | Property accessor           | `obj.prop`  | Left to right | `obj={a: 12}; obj.a` | `12`            |
| `;`        | Statement separator         | `x; y`      | Left to right | `a=2; b=3; a*b`      | `[6]`           |
| `;`        | Row separator               | `[x; y]`    | Left to right | `[1,2;3,4]`          | `[[1,2],[3,4]]` |
| `\n`       | Statement separator         | `x \n y`    | Left to right | `a=2 \n b=3 \n a*b`  | `[2,3,6]`       |
| `+`        | Add                         | `x + y`     | Left to right | `4 + 5`              | `9`             |
| `+`        | Unary plus                  | `+y`        | Right to left | `+4`                 | `4`             |
| `-`        | Subtract                    | `x - y`     | Left to right | `7 - 3`              | `4`             |
| `-`        | Unary minus                 | `-y`        | Right to left | `-4`                 | `-4`            |
| `*`        | Multiply                    | `x * y`     | Left to right | `2 * 3`              | `6`             |
| `.*`       | Element-wise multiply       | `x .* y`    | Left to right | `[1,2,3] .* [1,2,3]` | `[1,4,9]`       |
| `/`        | Divide                      | `x / y`     | Left to right | `6 / 2`              | `3`             |
| `./`       | Element-wise divide         | `x ./ y`    | Left to right | `[9,6,4] ./ [3,2,2]` | `[3,3,2]`       |
| `%`        | Percentage                  | `x%`        | None          | `8%`                 | `0.08`          |
| `%`        | Addition with Percentage    | `x + y%`    | Left to right | `100 + 3%`           | `103`           |
| `%`        | Subtraction with Percentage | `x - y%`    | Left to right | `100 - 3%`           | `97`            |
| `%` `mod`  | Modulus                     | `x % y`     | Left to right | `8 % 3`              | `2`             |
| `^`        | Power                       | `x ^ y`     | Right to left | `2 ^ 3`              | `8`             |
| `.^`       | Element-wise power          | `x .^ y`    | Right to left | `[2,3] .^ [3,3]`     | `[8,27]`        |
| `'`        | Transpose                   | `y'`        | Left to right | `[[1,2],[3,4]]'`     | `[[1,3],[2,4]]` |
| `!`        | Factorial                   | `y!`        | Left to right | `5!`                 | `120`           |
| `&`        | Bitwise and                 | `x & y`     | Left to right | `5 & 3`              | `1`             |
| `~`        | Bitwise not                 | `~x`        | Right to left | `~2`                 | `-3`            |
| `|`        | Bitwise or                  | `x | y`     | Left to right | `5 | 3`              | `7`             |
| `^|`       | Bitwise xor                 | `x ^| y`    | Left to right | `5 ^| 2`             | `7`             |
| `<<`       | Left shift                  | `x << y`    | Left to right | `4 << 1`             | `8`             |
| `>>`       | Right arithmetic shift      | `x >> y`    | Left to right | `8 >> 1`             | `4`             |
| `>>>`      | Right logical shift         | `x >>> y`   | Left to right | `-8 >>> 1`           | `2147483644`    |
| `and`      | Logical and                 | `x and y`   | Left to right | `true and false`     | `false`         |
| `not`      | Logical not                 | `not y`     | Right to left | `not true`           | `false`         |
| `or`       | Logical or                  | `x or y`    | Left to right | `true or false`      | `true`          |
| `xor`      | Logical xor                 | `x xor y`   | Left to right | `true xor true`      | `false`         |
| `=`        | Assignment                  | `x = y`     | Right to left | `a = 5`              | `5`             |
| `?` `:`    | Conditional expression      | `x ? y : z` | Right to left | `15 > 100 ? 1 : -1`  | `-1`            |
| `:`        | Range                       | `x : y`     | Right to left | `1:4`                | `[1,2,3,4]`     |
| `to`, `in` | Unit conversion             | `x to y`    | Left to right | `2 inch to cm`       | `5.08 cm`       |
| `==`       | Equal                       | `x == y`    | Left to right | `2 == 4 - 2`         | `true`          |
| `!=`       | Unequal                     | `x != y`    | Left to right | `2 != 3`             | `true`          |
| `<`        | Smaller                     | `x < y`     | Left to right | `2 < 3`              | `true`          |
| `>`        | Larger                      | `x > y`     | Left to right | `2 > 3`              | `false`         |
| `<=`       | Smallereq                   | `x <= y`    | Left to right | `4 <= 3`             | `false`         |
| `>=`       | Largereq                    | `x >= y`    | Left to right | `2 + 4 >= 6`         | `true`          |

### Precedence

| Operators                                 | Description                                                                     |
| ----------------------------------------- | ------------------------------------------------------------------------------- |
| `(...)`<br>`[...]`<br>`{...}`             | Grouping<br>Matrix<br>Object                                                    |
| `x(...)`<br>`x[...]`<br>`obj.prop`<br>`:` | Function call<br>Matrix index<br>Property accessor<br>Key/value separator       |
| `'`                                       | Matrix transpose                                                                |
| `!`                                       | Factorial                                                                       |
| `^`, `.^`                                 | Exponentiation                                                                  |
| `+`, `-`, `~`, `not`                      | Unary plus, unary minus, bitwise not, logical not                               |
| `*`, `/`, `.*`, `./`, `%`, `mod`          | Multiply, divide, percentage, modulus                                           |
| `+`, `-`                                  | Add, subtract                                                                   |
| `:`                                       | Range                                                                           |
| `to`, `in`                                | Unit conversion                                                                 |
| `<<`, `>>`, `>>>`                         | Bitwise left shift, bitwise right arithmetic shift, bitwise right logical shift |
| `==`, `!=`, `<`, `>`, `<=`, `>=`          | Relational                                                                      |
| `&`                                       | Bitwise and                                                                     |
| `^|`                                      | Bitwise xor                                                                     |
| `|`                                       | Bitwise or                                                                      |
| `and`                                     | Logical and                                                                     |
| `xor`                                     | Logical xor                                                                     |
| `or`                                      | Logical or                                                                      |
| `?`, `:`                                  | Conditional expression                                                          |
| `=`                                       | Assignment                                                                      |
| `,`                                       | Parameter and column separator                                                  |
| `;`                                       | Row separator                                                                   |
| `\n`, `;`                                 | Statement separators                                                            |


### Functions

As mentioned above, there is a function form for nearly every one of the mathematical operator symbols.The following functions are available.

| Operator Expression | Equivalent Function Expression |
| ------------------- | ------------------------------ |
| `a or b`            | `or(a,b)`                      |
| `a xor b`           | `xor(a,b)`                     |
| `a and b`           | `and(a,b)`                     |
| `a \| b`            | `bitOr(a,b)`                   |
| `a ^\| b`           | `bitXor(a,b)`                  |
| `a & b`             | `bitAnd(a,b)`                  |
| `a == b`            | `equal(a,b)`                   |
| `a != b`            | `unequal(a,b)`                 |
| `a < b`             | `smaller(a,b)`                 |
| `a > b`             | `larger(a,b)`                  |
| `a <= b`            | `smallerEq(a,b)`               |
| `a << 3`            | `leftShift(a,3)`               |
| `a >> 3`            | `rightArithShift(a,3)`         |
| `a >>> 3`           | `rightLogShift(a,3)`           |
| `u to cm`           | `to(u, cm)`                    |
| `a + b + c + ...`   | `add(a,b,c,...)`               |
| `a - b`             | `subtract(a,b)`                |
| `a * b * c * ...`   | `multiply(a,b,c,...)`          |
| `A .* B`            | `dotMultiply(A,B)`             |
| `A ./ B`            | `dotDivide(A,B)`               |
| `a mod b`           | `mod(a,b)`                     |
| `+a`                | `unaryPlus(a)`                 |
| `-a`                | `unaryMinus(a)`                |
| `~a`                | `bitNot(a)`                    |
| `not a`             | `not(a)`                       |
| `a^b`               | `pow(a,b)`                     |
| `A .^ B`            | `dotPow(A,B)`                  |
| `a!`                | `factorial(a)`                 |
| `A'`                | `ctranspose(A)`                |

### Units

Units can be used in the arithmetic operations add, subtract, multiply, divide, and exponentiation. Units can also be converted from one to another.

| Expression      | Evaluated as          | Result               |
| --------------- | --------------------- | -------------------- |
| 100 g in kg     | (0.1 kg) / (1 kg)     | 0.1 kg               |

The following units are available.

| Base                      | Unit                                                                                                                                                                                                    |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Length                    | meter (m), inch (in), foot (ft), yard (yd), mile (mi), link (li), rod (rd), chain (ch), angstrom, mil                                                                                                   |
| Surface area              | m2, sqin, sqft, sqyd, sqmi, sqrd, sqch, sqmil, acre, hectare                                                                                                                                            |
| Volume                    | m3, litre (l, L, lt, liter), cc, cuin, cuft, cuyd, teaspoon, tablespoon                                                                                                                                 |
| Liquid volume             | minim, fluiddram (fldr), fluidounce (floz), gill (gi), cup (cp), pint (pt), quart (qt), gallon (gal), beerbarrel (bbl), oilbarrel (obl), hogshead, drop (gtt)                                           |
| Angles                    | rad (radian), deg (degree), grad (gradian), cycle, arcsec (arcsecond), arcmin (arcminute)                                                                                                               |
| Time                      | second (s, secs, seconds), minute (min, mins, minutes), hour (h, hr, hrs, hours), day (days), week (weeks), month (months), year (years), decade (decades), century (centuries), millennium (millennia) |
| Frequency                 | hertz (Hz)                                                                                                                                                                                              |
| Mass                      | gram(g), tonne, ton, grain (gr), dram (dr), ounce (oz), poundmass (lbm, lb, lbs), hundredweight (cwt), stick, stone                                                                                     |
| Electric current          | ampere (A)                                                                                                                                                                                              |
| Temperature               | kelvin (K), celsius (degC), fahrenheit (degF), rankine (degR)                                                                                                                                           |
| Amount of substance       | mole (mol)                                                                                                                                                                                              |
| Luminous intensity        | candela (cd)                                                                                                                                                                                            |
| Force                     | newton (N), dyne (dyn), poundforce (lbf), kip                                                                                                                                                           |
| Energy                    | joule (J), erg, Wh, BTU, electronvolt (eV)                                                                                                                                                              |
| Power                     | watt (W), hp                                                                                                                                                                                            |
| Pressure                  | Pa, psi, atm, torr, bar, mmHg, mmH2O, cmH2O                                                                                                                                                             |
| Electricity and magnetism | ampere (A), coulomb (C), watt (W), volt (V), ohm, farad (F), weber (Wb), tesla (T), henry (H), siemens (S), electronvolt (eV)                                                                           |
| Binary                    | bits (b), bytes (B)                                                                                                                                                                                     |

Note: all time units are based on the Julian year, with one month being 1/12th of a Julian year, a year being one Julian year, a decade being 10 Julian years, a century being 100, and a millennium being 1000.

Note that all relevant units can also be written in plural form, for example 5 meters instead of 5 meter or 10 seconds instead of 10 second.

Surface and volume units can alternatively be expressed in terms of length units raised to a power, for example 100 in^2 instead of 100 sqin.

### Strings

Strings are enclosed by double quotes “ or single quotes ‘. Strings can be concatenated using the function concat (not by adding them using + like in JavaScript). Parts of a string can be retrieved or replaced by using indexes. Strings can be converted to a number using function number, and numbers can be converted to a string using function string.

When setting the value of a character in a string, the character that has been set is returned. Likewise, when a range of characters is set, that range of characters is returned.

| Expression      | Evaluated as          | Result               |
| --------------- | --------------------- | -------------------- |
| "300"           |  String, "300"        | "300"                |
| number("300")   |  Number, 300          | 300                  |
| string(300)     |  String, "300"        | "300"                |

### Implicit multiplication

Implicit multiplication means the multiplication of two symbols, numbers, or a grouped expression inside parentheses without using the * operator. This type of syntax allows a more natural way to enter expressions.

| Expression      | Evaluated as          | Result               |
| --------------- | --------------------- | -------------------- |
| 20 kg / 4 kg    | (20 kg) / (4 kg)      | 5                    |
| 20 / 4 kg       | (20 / 4) kg           | 5 kg                 |
| (1 + 3) pi      | (1 + 3) \* pi         | 12.566370614359172   |
| (4 - 1) 2       | (4 - 1) \* 2          | 6                    |
| 3 / 4 mm        | (3 / 4) \* mm         | 0.75 mm              |
| 2 + 3 i         | 2 + (3 \* i)          | 2 + 3i               |
| (1 + 2) (4 - 2) | (1 + 2) \* (4 - 2)    | 6                    |
| sqrt(4) (1 + 2) | sqrt(4) \* (1 + 2)    | 6                    |
| 8 pi / 2 pi     | (8 \* pi) / (2 \* pi) | 4                    |
| pi / 2 pi       | pi / (2 \* pi)        | 0.5                  |
| 1 / 2i          | (1 / 2) \* i          | 0.5 i                |
| 8.314 J / mol K | 8.314 J / (mol \* K)  | 8.314 J / (mol \* K) |