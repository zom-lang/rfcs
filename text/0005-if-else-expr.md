- **Feature Name:** `if-else-expr`
- **Start date:** 2023-07-02
- **RFC PR:** [zom-lang/rfc#0005](https://github.com/zom-lang/rfcs/pull/0005)
- **Zom Issue:** [zom-lang/zom#0000](https://github.com/zom-lang/zom/issues/0000)

# Summary
[summary]: #summary

If-else expression is a control flow expression, the code can branch if a
condition is true or false.

# Motivation
[motivation]: #motivation

The ability to run some code depending on whether a condition is true, is basic
building blocks in most programming languages.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

## Basic if-else

```zom
const a = 12;
if a == 12 {
    // ...
} else {
    // ...
}
```

You can branch the code depending on a condition, in this case the condition is
`a == 12`, if it's true the code will branch in the code block after the condition
but if it's false, the execution will branch after the else.

## if-else expr in other expression

Because if-else is in Zom an expression, so you can use it as an expression, but the
else is mandatory.

```zom
const a = 12;
const bar = if a == 12 {
    "twelve"
} else {
    "not twelve"
};
```

All the branches needs to have the same type. So that code not compile:

```zom
const a = 12;
const bar = if a == 12 {
    "twelve"
}else {
    12
};
```

## Using only if

You can use only an if expression if the return type is void.

```zom
func main() void {
    const a = 12;
    if a == 12 {
        return;
    }
    // ...
}
```

## Else-if

You can have multiple conditions in one if-else expression.

```zom
const a = 12;
const b = if a == 12 {
    "twelve"
} else if a == 13 {
    "thirteen"
} else if a == 14 {
    "fourteen"
} else {
    "not twelve, thirteen or fourteen"
};
```

# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

This is the technical portion of the RFC. Explain the design such as contributor to the compiler don't have to guess who, 
in details this needs to be implemented :

- You can explain previous examples in details.
- Interaction of your feature with existing feature is clear.
- Corner cases are dissected by example.

# Alternatives
[alternatives]: #alternatives

*N/A*

# Drawbacks
[drawbacks]: #drawbacks

*N/A*

# Unresolved questions
[unresolved-questions]: #unresolved-questions

Do we accept `if-else` expression without block ? like so
```zom
const a = 12;
if a == 12:
    return;
else:
    // ...
```
that can be useful when you want to early return of a function but I don't know if it's in Zom mentality.
