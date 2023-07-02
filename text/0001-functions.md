- **Feature Name:** `functions`
- **Start date:** 2023-07-01
- **RFC PR:** [zom-lang/evolution#0001](https://github.com/zom-lang/evolution/pull/0001)
- **Zom Issue:** [zom-lang/zom#0040](https://github.com/zom-lang/zom/issues/0040)

# Summary
[summary]: #summary

Add function definition, function declaration and function call in Zom.

# Motivation
[motivation]: #motivation

Like many other programming language, Zom need functions, because this is the base of all functionnal programming language and because Zom will be
object oriented and a functional programming language, this is mandatory.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

## Function definition

e.g:
```Zom
func foo(bar: i16, baz: i16) i16 {
    return (bar + 9) / 2 * baz;
}
```

Function definition start with the `func` keyword, followed by an identifier: in this example, `foo`; and arguments in parenthesis with 
there type specified: in this example, `bar` and `baz`. And a return type after the parenthesis: in this example, an `i16`. And after there 
is a block code expression that contains expressions, separated by semi colon. 

By defult Zom uses the C calling convention for simple call of Zom functions into C code and vice versa.

### Return statement

In the block code expression of a function definition, you can use the `return` expression followed by an expression with the same type as the 
return type. A `return` statement breaks the control flow :

```Zom
func foo(bar: i16) i16 {
    (* if there is code here it will be runned *)
    return bar / 2;
    (* but not here *)
}
```

If a function has no return type or a return type of void, you can just use the `return` statement :

```Zom
func foo(bar: i16) {
    (* do some stuff *)
    return;
    (* but not here *)
}
```

## Function declaration

e.g:
```Zom
extern "C" func c_function(arg_a: u8, arg_b: u8) u16;
```

Function declaration start with the `extern` keyword, followed by a string literal who specify the calling convention[^1] and then the `func` keyword.
After it's like function definition but there is no block code expression, because extern functions are resolved at `link-time` and a semi colon is
needed after the return type.

## Function call

e.g:
```Zom
func foo(bar: i16, baz: i16) i16 {
    return (bar + 9) / 2 * baz;
}

func main() {
    foo(12, 32);
}
```

A function call, start with the identifier corresponding to the function you want to call, in parenthesis, expressions that match the type
expected by the function signature. Because function call are expression, you can call a function where an expression is excepected, as long
as type match.

# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

Functions have name mangling, to solve some known issues. Zom uses the [`Itanium C++ ABI name mangling rules`](http://itanium-cxx-abi.github.io/cxx-abi/abi.html#mangling).

Here is a more grammar-style,

## Function definition

function definition,
```
func $ident( [ $ident : $type , ]* ) ($type)? $code_expr
```

### Return statement

In a function, code expression, a return statement
```
return [ $expr ]? ;
```

## Function declaration

function declaration,
```
extern $string_literal func $ident( [ $ident : $type , ]* ) ($type)? ;
```

## Function call

In a code expression; a function call,
```
$ident ( [ $expr , ]* ) ;
```

# Alternatives
[alternatives]: #alternatives

Zom could have been using the keyword `fn` instead of `func`, because it's smaller; but, I don't like much it.

# Drawbacks
[drawbacks]: #drawbacks

> Why should we *not* do this?

We should, it's mandatory for all functional programming languages.

# Unresolved questions
[unresolved-questions]: #unresolved-questions

Do we really want to use the `C calling convention`?
Does the [`Itanium C++ ABI name mangling rules`](http://itanium-cxx-abi.github.io/cxx-abi/abi.html#mangling) correctly feets who Zom will work ?

[^1]: Zom support all calling convention supported by LLVM.
