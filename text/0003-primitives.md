- **Feature Name:** `primitives`
- **Start date:** 2023-07-02
- **RFC PR:** [zom-lang/evolution#0003](https://github.com/zom-lang/evolution/pull/0003)
- **Zom Issue:** [zom-lang/zom#0051](https://github.com/zom-lang/zom/issues/0051)

# Summary
[summary]: #summary

This RFC bring primitive types, like integers, floating point number, strings, char;
and primitive values, `true`, `false` and `undefined`.

# Motivation
[motivation]: #motivation

Primitive types are useful and mandatory ways to store numbers, string and char.

Add an `undefined` is useful when you want to create a variable and initialize it later.
But we need to be carful, because if function can return `undefined` the caller would need
to check if it's not `undefined`. This is why function cannot return `undefined` and variable
cannot be used if they are undefined.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

## Integers type.

|   Name   |                        Description                       |
| -------- | -------------------------------------------------------- |
| *Signed* | *Signed integer types, with two's complement.*           |
|  `i8`    | -127 to +127                                             |
|  `i16`   | −32_767 to +32_767                                       |
|  `i32`   | −2_147_483_647 to +2_147_483_647                         |
|  `i64`   | −9_223_372_036_854_775_807 to +9_223_372_036_854_775_807 |
|  `i128`  | -(2^127) to +(2^127 - 1)                                 |
|  `isize` | -(2^*XLEN*) to +(2^*XLEN* - 1), *see below for more info*|
|          |                                                          |
|*Unsigned*| *Unsigned integers*                                      |
|  `u8`    | 0 to 255                                                 |
|  `u16`   | 0 to 65_535                                              |
|  `u32`   | 0 to 4_294_967_295                                       |
|  `u64`   | 0 to 18_446_744_073_709_551_615                          |
|  `i128`  | 0 to 340_282_366_920_938_463_463_374_607_431_768_211_455 |
|  `usize` | 0 to +(2^*XLEN* - 1), *see below for more info*          |

The size of `isize` and `usize` is how many bytes to reference (or point) any location
in memory. e.g: on a 32 bit target, `isize` and `usize` will be 4 bytes and on a 64 bit
target, it will be 8 bytes.

## Boolean

Booleans, with the type name `bool`, is a primitive integer type, 1 bit long, it can be
mapped to LLVM `u1`. Their is two primitive values, with `bool`; `true` is 1 and `false`
is 0.

> `true` and `false` are treated as keywords.

## Floating point number.

Zom follows the IEEE 754 floating point number standard; `f16`, `f32`, `f64`, `f128` is
respectively Half precision, single precision, double precision,
quadruple precision floating point number.

|  Name |                                 Range                                 |
| ----- | --------------------------------------------------------------------- |
| `f16` | [`≈ 0.00006103515625` to `65504`][f16-wikipedia]                      |
| `f32` | [`≈ 1.1754943 × 10^−38` to `≈ 3.4028235 × 10^38`][f32-wikipedia]      |
| `f64` | [`≈ 2.2250738 × 10^−308` to `≈ 1.7976931 × 10^308`][f64-wikipedia]    |
| `f128`| [`≈ 3.3621032 × 10^−4932` to `≈ 1.1897315 × 10^4932`][f128-wikipedia] |

[f16-wikipedia]: https://en.wikipedia.org/wiki/Half-precision_floating-point_format
[f32-wikipedia]: https://en.wikipedia.org/wiki/Single-precision_floating-point_format
[f64-wikipedia]: https://en.wikipedia.org/wiki/Double-precision_floating-point_format
[f128-wikipedia]: https://en.wikipedia.org/wiki/Quadruple-precision_floating-point_format

## Char

A `char` is a 32 bit type. Corresponding to the unicode code point.

## String slice

A string slice doesn't have a size known at compile-time. It stores, the size of the
string with a usize first and after it's a `u8` sclice (see RFC about arrays & sclices).

## Void

`void` is a zero-size type that is used when you don't want to return nothing from
a function.

## `undefined`

`undefined` is a special value that is used when you want to initialize a `var` or
a `const` later. But:
- If you use a `var` or `const` and if it's value is undefined, you will have `use
  of undefined var / const` error.
- It you pass a `undefined` value to a function or method (or undefined var/const)
  you will have the `cannot pass undefined value to function` / `method` error.
- If you return from a function / method an `undefined`, you will have the `return
  an undefined expression`

> `undefined` is treated as a keyword

# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

The integers types, follows LLVM integers types. `usize` and `isize` is replaced at
compile time by the respective `uNN` or `iNN`.

Floating point number match the IEEE 754 standard and map `f16`, `f32`, `f64`, `f128`
map respectively to LLVM, `half`, `float`, `double` and `fp128`.

## Number Literal

| Number literals | Example |
| :-------------- | :-----: |
| Decimal integer | `98222` |
| Hex integer     | `0xff`  |
| Floating-point  | `987.65`|
> Future RFC may add octal and binary integers literal and advanced floating point
> literals and with `_` visual separator.

## Char literal

A `char` literal start with a simple quote and contains one character or an escape
sequence.

e.g:
```zom
const a = 'A'; // contains -> A
const simple_quote = '\''; // contains -> '
const double_quote = '"'; // contains -> "
```

## String literal

A `string` literal starts with a double quote and finish with another double quote.

e.g:
```zom
const hello_world = "Hello, world!"; // contains -> Hello, world!
const double_quote = "\""; // contains -> "
const simple_quote = "'"; // contains -> '
```

## Supported String slice / char escape sequence

| Escape |                         Name                        |
| :----: | :-------------------------------------------------- |
|`\xNN`¹ | 7-bit character code (exactly 2 digits, up to 0x7F) |
|  `\n`	 | Newline                                             |
|  `\r`  | Carriage return                                     |
|  `\t`  | Tab                                                 |
|  `\\`  | Backslash                                           |
|  `\0`	 | Null                                                |
|  `\'`  | Simple quote escape (used in char literals)         |
|  `\"`  | Double quote escape (used in string literals)       |
> In future RFC some escapes could be added.

¹ : Where `NN` are two hexdigits

# Alternatives
[alternatives]: #alternatives

For integers and floating point types, we could use the same as C / C++, but I think
it's better to know the length directly by the name for a system programming language.
And often in C / C++ project developers use `stdint.h`.

# Drawbacks
[drawbacks]: #drawbacks

*No drawbacks found for now.*

# Unresolved questions
[unresolved-questions]: #unresolved-questions

Do we accept 0 and 1 as boolean literals ?
