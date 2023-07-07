- **Feature Name:** `var-const`
- **Start date:** 2023-07-02
- **RFC PR:** [zom-lang/evolution#0002](https://github.com/zom-lang/evolution/pull/0002)
- **Zom Issue:** [zom-lang/zom#0000](https://github.com/zom-lang/zom/issues/0000)

# Summary
[summary]: #summary

This RFC bring a way to store data with Zom source code. You can store immutable data, with `const` or mutable data with `var`.

# Motivation
[motivation]: #motivation

We are doing this because we need to store data, and some time mutate its content. This is why this RFC introduce variables and constants.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation


## `const`

The value stored in `const`, after initialization will not change. `const` are prefered over `var` when there is no need changing the stored value.

e.g:
```Zom
const foo: i32 = 2048;
```
You can declare a `const` with the keyword `const`, followed by the name of the constant, in this case `foo`; the type, in this case `i32`,
and its initialization, to `2048`.

## `var`

The value stored in `var`, after initialization could change, but if it will never change it's prefered to use `const`.

e.g:
```Zom
var bar: i32 = 8402;
```
You can declare a `var` with the keyword `const`, followed by the name of the variable, in this case `bar`; the type, in this case `i32`,
and its initialization, to `8402`.

### `var` assignement

e.g:
```Zom
var bar: i32 = 8402;
(* ... *)
bar = 1234;
```

In this case, `bar` is initialized to `8402`, and after `bar` is assigned to `1234`. This only works if `bar` was a `var`. 

## Type inference

It's not mandatory to specify the type of a `const` or `var`, it can be inferred by the type checker,

e.g: 
```Zom
const bar = 16;
```

# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

The grammars are :

## `const` statement

```
const $Ident = $Expr;
```

## `var` statement

```
var $Ident = $Expr;
```

## `var` assignement

```
$Ident = $Expr;
```

## How that works ?

`const` will be stored in the stack, but the compiler will ensure that you will never change the stored value.

`var` will be stored in the stack, you will be able to change the stored value.

# Alternatives
[alternatives]: #alternatives

We could use instead of `var`, `let mut` and `let` for `const` like Rust; but I think it's better to use `var` for mutable data because `var` means
variable. And it's better to use `const` because `const` means constant.

# Drawbacks
[drawbacks]: #drawbacks

### Because the `const` keyword is often used in other programming language to store values that is used multiple time but not like a variable; Zom programmers could always use `var`.

Make lints warn when a `const` could be used instead of a `var`.

# Unresolved questions
[unresolved-questions]: #unresolved-questions

No unresolved questions for the moment.
