- **Feature Name:** `struct`
- **Start date:** 2023-08-04
- **RFC PR:** [zom-lang/rfcs#0000](https://github.com/zom-lang/rfcs/pull/0000)
- **Zom Issue:** [zom-lang/zom#0000](https://github.com/zom-lang/zom/issues/0000)

# Summary
[summary]: #summary

A struct type is a heterogeneous product of other types, called the fields of the type.
A struct definition is a nominal struct type defined with the keyword `struct` in a
const, global variable because Zom treat type as value.

# Motivation
[motivation]: #motivation

We expect with structs, that function prototypes will be cleaner and bundling data &
functionnalities will be easier.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

Imagine your proposal is already included in the language and explain it to
another Zom programmer. That generally means:

- Introducing new named concepts
- Explain the feature with examples
- If there is, provide sample error or warnings messages.
- Discuss how your feature impact the ability to read or understand Zom
  source code.
- Will the proposed feature make code esaier to maintain / read ? Why ?

## Struct definition

Their are two types of struct definition;
* tuple struct definition where fields doesn't have name
* and named field struct definiton

### Tuple like

To define a new struct without named fields, you first create a new const with
a Upper Camel Case name. Followed by the keyword `struct` and type(s) separated
by commas in parenthesis.

e.g:
```zom
const 3DCoordonates = struct (
  u32,
  u32,
  u32
)
```

### Named fields

To define a new struct with named fields, you first create a new const with an Upper
Camel Case name; And then the keyword `struct` and a field pair separated with commas.
A field pair consist of an identifier

# Deep-dive explenation
[deep-dive-explenation]: #deep-dive-explenation

This is the technical portion of the RFC. Explain the design such as
contributor to the compiler don't have to guess who, in details this
needs to be implemented :

- You can explain previous examples in details.
- Interaction of your feature with existing feature is clear.
- Corner cases are dissected by example.

# Alternatives
[alternatives]: #alternatives

What other designs have been considered? What is the impact of not doing
this? And why don't do this ?

# Drawbacks
[drawbacks]: #drawbacks

Why should we *not* do this? Do you have an answer/partial answer why
we should still do this?

# Unresolved questions
[unresolved-questions]: #unresolved-questions

What parts of the design are still TBD ?
What part of the design you expect through the RFC process ?