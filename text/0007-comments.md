- **Feature Name:** `comments`
- **Start date:** 2023-07-02
- **RFC PR:** [zom-lang/rfcs#0007](https://github.com/zom-lang/rfcs/pull/0007)
- **Zom Issue:** [zom-lang/zom#0014](https://github.com/zom-lang/zom/issues/0014)

# Summary
[summary]: #summary

This feature bring comments to Zom; line comments with two slashes `//` and
block comments starting with `/*` and finishing with `*/`.

# Motivation
[motivation]: #motivation

*No motivation just logic, commenting code is mandatory to keep the code clear.*

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

## Line comment

A line comment start with two slashes `//` and end until the line feed, in
ascii 0x`0A`.

e.g:
```Zom
// this is a line comment.
```

## Block comment

A block comment start with a slash and a start `/*` and end with a start
and a slah, `*/`.

e.g:
```Zom
/*
   This is a block comment.
   it can be multiple lines long.
*/
```


# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

The content of comments are ignored in the compiler, and nothing happen
with them.

# Alternatives
[alternatives]: #alternatives

We could use hastag for line comments but doc comment with hashtag will
look like that `#/` or `#!`, it's not very convenient. But with slashes,
doc-comment look like that `///` and `//!`.

And we could use `(*` and `*)` for block comments like in OCaml but if we
use `//`, using `/*` and `*/` is the most idiomatic.

# Drawbacks
[drawbacks]: #drawbacks

*No drawbacks*

# Unresolved questions
[unresolved-questions]: #unresolved-questions

*No unresolved questions*
