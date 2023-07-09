- **Feature Name:** `primitives`
- **Start date:** 2023-07-02
- **RFC PR:** [zom-lang/evolution#0003](https://github.com/zom-lang/evolution/pull/0003)
- **Zom Issue:** [zom-lang/zom#0000](https://github.com/zom-lang/zom/issues/0000)

# Summary
[summary]: #summary

This RFC bring primitive types, like integers, floating point number, strings, char; and primitive values, like `true` and `false`.

# Motivation
[motivation]: #motivation

*No interest, primitive types are mandatory for all programming languages*

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
|*Unsigned*| *Unsigned number, without two's complement*              |
|  `u8`    | 0 to 255                                                 |
|  `u16`   | 0 to 65_535                                              |
|  `u32`   | 0 to 4_294_967_295                                       |
|  `u64`   | 0 to 18_446_744_073_709_551_615                          |
|  `i128`  | 0 to 340_282_366_920_938_463_463_374_607_431_768_211_455 |
|  `usize` | 0 to +(2^*XLEN* - 1), *see below for more info*          |

The size of `isize` and `usize` is how many bytes to reference (or point) any location in memory. e.g: on a 32 bit target, `isize` and `usize` will be 4 bytes 
and on a 64 bit target, it will be 8 bytes.

## Boolean

Booleans, with the type name `bool`, is a primitive integer type, 1 bit long, it can be mapped to LLVM `u1`. Their is two primitive values, with `bool`; `true` is 
1 and `false` is 0.

## Floating point number.

Zom follows the IEEE 754 floating point number standard; `f16`, `f32`, `f64`, `f128` is respectively Half precision, single precision, double precision,
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

*This follows the unicode standard*

## String slice

*This follows UTF-8.*

# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

Integers type, follows LLVM integers types, and `usize` and `isize` is replaced at compile time by the respective `uNN` or `iNN`.

Floating point number match the IEEE 754 standard and map `f16`, `f32`, `f64`, `f128` map respectively to LLVM, `half`, `float`, `double`
and `fp128`.

**TODO: Char and String slice**

# Alternatives
[alternatives]: #alternatives

For integers and floating point types, we could use the same as C / C++, but I think it's better to know the length directly by the name.
And very often in C / C++ project they redefine the name of integer types to a thing similar to `iNN` or `uNN`.

# Drawbacks
[drawbacks]: #drawbacks

*No drawbacks found for now.*

# Unresolved questions
[unresolved-questions]: #unresolved-questions

*No unresolved questions for now.*