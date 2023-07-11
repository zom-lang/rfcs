- **Feature Name:** `operators`
- **Start date:** 2023-07-02
- **RFC PR:** [zom-lang/evolution#0004](https://github.com/zom-lang/evolution/pull/0004)
- **Zom Issue:** [zom-lang/zom#0000](https://github.com/zom-lang/zom/issues/0000)


# Summary
[summary]: #summary

This RFC clarify which operator their is, what they do and introduce the operator precendence table.


# Motivation
[motivation]: #motivation

We are doing this to clarify operators in Zom and their operator precedence value.


# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

## Operator table

|   Op   |            Name            | Technical Name |  Type  |
| ------ | -------------------------- | -------------- | ------ |
|  `*`   | `Multiplication`           | `OP_MUL`       | Binary |
|  `/`   | `Division`                 | `OP_DIV`       | Binary |
|  `%`   | `Remainder`                | `OP_REM`       | Binary |
|  `+`   | `Addition`                 | `OP_ADD`       | Binary |
|  `-`   | `Substraction`             | `OP_SUB`       | Binary |
|  `>>`  | `Right shift`              | `OP_RSHIFT`    | Binary |
|  `<<`  | `Left shift`               | `OP_LSHIFT`    | Binary |
|  `<`   | `Less than`                | `OP_COMP_LT`   | Binary |
|  `>`   | `Greater than`             | `OP_COMP_GT`   | Binary |
|  `<=`  | `Less than or equal to`    | `OP_COMP_LTE`  | Binary |
|  `>=`  | `Greater than or equal to` | `OP_COMP_GTE`  | Binary |
|  `==`  | `Equal to`                 | `OP_COMP_EQ`   | Binary |
|  `!=`  | `Not equal to`             | `OP_COMP_NE`   | Binary |
|  `&`   | `Bitwise AND`              | `OP_BIT_AND`   | Binary |
|  `^`   | `Bitwise XOR`              | `OP_BIT_XOR`   | Binary |
|  `\|`  | `Bitwise OR`               | `OP_BIT_OR`    | Binary |
|  `~`   | `Bitwise NOT`              | `OP_BIT_NOT`   |*Unary* |
|  `&&`  | `Logical AND`              | `OP_LOGIC_AND` | Binary |
| `\|\|` | `Logical OR`               | `OP_LOGIC_OR`  | Binary |
|  `!`   | `Logical NOT`              | `OP_LOGIC_NOT` |*Unary* |
|  `=`   | `Simple assignement`       | `OP_EQ`        | Binary |
|  `.`   | `Member access (OOP)`      | `OP_DOT`       | Binary |

### Multiplication

e.g: `a * b`

### Division

e.g: `a / b`

### Remainder

e.g: `a % b`

### Addition

e.g: `a + b`

### Substraction

e.g: `a - b`

### Right shift

e.g: `a >> b`

### Left shift

e.g: `a << b`

### Less than

e.g: `a < b`

### Greater than

e.g: `a > b`

### Less than or equal to

e.g: `a <= b`

### Greater than or equal to

e.g: `a >= b`

### Equal to

e.g: `a == b`

### Not equal to

e.g: `a != b`

### Bitwise AND

e.g: `a & b`

### Bitwise XOR

e.g: `a ^ b`

### Bitwise OR

e.g: `a | b`

### Bitwise NOT

e.g: `~a`


### Logical AND

e.g: `a && b`

### Logical OR

e.g: `a || b`

### Logical NOT

e.g: `!a`

### Simple assignement

e.g: `a = b` or `a = 12`

### Member access (OOP)

*This operation will not be covered in details, in this RFC. It will be covered in the RFC about struct.*

e.g: `a.b`


# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

## Operator precedence table

|             Ops              |  Technical Name  | Value |
| ---------------------------- | ---------------- | ----- |
| `OP_DOT`                     | `PR_DOT`         |   13  |
| `OP_LOGIC_NOT`, `OP_BIT_NOT` | `PR_NOT`         |   12  |
| `OP_MUL`, `OP_DIV`, `OP_REM` | `PR_MUL_DIV_REM` |   11  |
| `OP_ADD`, `OP_SUB`           | `PR_ADD_SUB`     |   10  |
| `OP_RSHIFT`, `OP_LSHIFT`     | `PR_SHIFT`       |   9   |
| `OP_COMP_LT`, `OP_COMP_GT`, </br>
`OP_COMP_LTE`, `OP_COMP_GTE`   | `PR_COMP`        |   8   |
| `OP_COMP_EQ`, `OP_COMP_NE`   | `PR_COMP_EQ_NE`  |   7   |
| `OP_BIT_AND`                 | `PR_BIT_AND`     |   6   |
| `OP_BIT_XOR`                 | `PR_BIT_XOR`     |   5   |
| `OP_BIT_OR`                  | `PR_BIT_OR`      |   4   |
| `OP_LOGIC_AND`               | `PR_LOGIC_AND`   |   3   |
| `OP_LOGIC_OR`                | `PR_LOGIC_OR`    |   2   |
| `OP_EQ`                      | `PR_EQ`          |   1   |


# Alternatives
[alternatives]: #alternatives

*No alternatives found for now.*


# Drawbacks
[drawbacks]: #drawbacks

*No drawbacks found for the moment.*


# Unresolved questions
[unresolved-questions]: #unresolved-questions

*No unresolved questions for now.*