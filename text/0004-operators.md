- **Feature Name:** `operators`
- **Start date:** 2023-07-02
- **RFC PR:** [zom-lang/rfcs#0004](https://github.com/zom-lang/rfcs/pull/0004)
- **Zom Issue:** [zom-lang/zom#0047](https://github.com/zom-lang/zom/issues/0047)


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
| :----- | :------------------------  | :------------- | :----: |
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
|  `&`   | `Borrow`                   | `OP_BORROW`    |*Unary* |
| `&var` | `Variable borrow`          | `OP_VAR_BORROW`|*Unary* |
|  `*`   | `Dereferencing`            | `OP_DEREF`     |*Unary* |
|  `-`   | `Unary minus`              | `OP_MINUS`     |*Unary* |
|  `+`   | `Unary plus`               | `OP_PLUS`      |*Unary* |

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

### Borrowing

*This operation will not be covered in details, in this RFC. It will be covered in the RFC about references and liveness.*

e.g: `&a`

### Variable Borrowing

*This operation will not be covered in details, in this RFC. It will be covered in the RFC about references and liveness.*

e.g: `&var a`

### Dereferencing

*This operation will not be covered in details, in this RFC. It will be covered in the RFC about references and liveness.*

e.g: `*a`

### Unary minus

e.g: `-a`

### Unary plus

e.g: `+a`

# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

## Operator precedence table

|      Operators       |  Technical Name  | Value |
| :------------------- | :--------------- | :---: |
| `.`                  | `PR_DOT`         |   13  |
| `!`, `~`, `&`, <br/>
  `&var`, `*`, `-`     | `PR_UNARY`       |   12  |
| `*`, `/`, `%`        | `PR_MUL_DIV_REM` |   11  |
| `+`, `-`             | `PR_ADD_SUB`     |   10  |
| `>>`, `<<`           | `PR_SHIFT`       |   9   |
| `<`, `>`, `<=`, `>=` | `PR_COMP`        |   8   |
| `==`, `!=`           | `PR_COMP_EQ_NE`  |   7   |
| `&`                  | `PR_BIT_AND`     |   6   |
| `^`                  | `PR_BIT_XOR`     |   5   |
| `\|`                 | `PR_BIT_OR`      |   4   |
| `&&`                 | `PR_LOGIC_AND`   |   3   |
| `\|\|`               | `PR_LOGIC_OR`    |   2   |
| `=`                  | `PR_EQ`          |   1   |


# Alternatives
[alternatives]: #alternatives

*No alternatives found for now.*


# Drawbacks
[drawbacks]: #drawbacks

*No drawbacks found for the moment.*


# Unresolved questions
[unresolved-questions]: #unresolved-questions

*No unresolved questions for now.*

> ### Note
> If an operator is added, you can add a note to this RFC that a new operator was been created or removed, after the `#operator-table` section.
