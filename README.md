# ⚠️ RFC process temporarly stopped, see [#9](https://github.com/zom-lang/rfcs/issues/9)
# ⚡ Zom RFCs
[Zom RFCs]: #⚡-zom-rfcs

[![lines of code](https://tokei.rs/b1/github/zom-lang/rfcs)](https://github.com/Aaronepower/tokei)
[![License][licence-badge]](#license)
[![discord server](https://img.shields.io/discord/1115546838729240596?label=Discord%20Server&color=5765F2)][Discord Server]

[licence-badge]: https://img.shields.io/badge/License-%20Apache--2.0-lightblue

This repository contains **Request For Comments** (RFC), that describe the
whole Zom Programming Language, its libraries, its compiler and its tools.
The RFC process is intended to provide a consistent and controlled path for
changes to Zom.

Many bug fixes, sentence correction can just be implemented and reviewed with
the normal GitHub pull request workflow.

> note that until version 1.0 of Zom is not released, the RFC process could
> have a lack of interest because we prefer to develop the compiler but that
> does not prevent RFCs from being made if necessary.

## Table of Content
[Table of Content]: #table-of-content

- [Zom RFCs]
- [Table of Content]
- [When you need to follow this process]
- [Before creating an RFC]
- [What the RFC Process is]
- [The RFC life-cycle]
- [Reviewing RFCs]
- [Implement an RFC]
- [License]
- [Contribution]

## When you need to follow this process
[When you need to follow this process]: #when-you-need-to-follow-this-process

You need to follow this process if you intend to make "substantial" changes to
Zom, or an other tool of the Zom project, or the RFC process itself. What
constitutes a "substantial" change is evolving based on community norms and
varies depending on what part of the ecosystem you are proposing to change, but
may include the following.

  - Any semantic or syntactic change to the language that is not a bugfix.
  - Removing language features, including those that are feature-gated.
  - Changes to the interface between the compiler and libraries, including lang
    items and intrinsics.
  - Additions to `std`.

Some changes do not require an RFC:

  - Rephrasing, reorganizing, refactoring, or otherwise "changing shape does
    not change meaning".
  - Additions that strictly improve objective, numerical quality criteria
    (warning removal, speedup, better platform coverage, more parallelism, trap
    more errors, etc.)
  - Additions only likely to be *noticed by* other developers-of-zom,
    invisible to users-of-zom.

If you submit a pull request to implement a new feature without going through
the RFC process, it may be closed with a polite request to submit an RFC first.


## Before creating an RFC
[Before creating an RFC]: #before-creating-an-rfc

A hastily-proposed RFC can hurt its chances of acceptance. Low quality
proposals, proposals for previously-rejected features, or those that don't fit
into the near-term roadmap, may be quickly rejected, which can be demotivating
for the unprepared contributor. Laying some groundwork ahead of the RFC can
make the process smoother.

Although there is no single way to prepare for submitting an RFC, it is
generally a good idea to pursue feedback from other project developers
beforehand, to ascertain that the RFC may be desirable; having a consistent
impact on the project requires concerted effort toward consensus-building.

The most common preparations for writing and submitting an RFC include talking
the idea over on our [official Zulip server], discussing the topic on our
[Discord Server], and occasionally posting "pre-RFCs" on the Zulip server.
You may file issues on this repo for discussion, but prefer using Zulip or
Discord.

As a rule of thumb, receiving encouraging feedback from long-standing project
developers, and particularly members of the relevant [sub-team] a is a good
indication that the RFC is worth pursuing.


## What the RFC Process is
[What the RFC Process is]: #the-rfc-process

In short, the Zom Programming language specification is driven through a RFC
process, if you want to change the programming language or its libraries, you
must follow the RFC process :

- Fork the RFC repo [RFC repository]

- Copy `0000-template.md` to `text/0000-my-feature.md`, where `my-feature` is
  an unique identifier of the feature. Don't assign an RFC number yet; This is
  going to be the PR number and we'll rename the file accordingly if the RFC
  is accepted.

- Fill the RFC according to the template and put care into the details: RFC
  that doesn't have a convincing motivation, demontrate lack of understanding
  of the desigh impact or are disingenuous about the drawbacks or alternatives,
  tend to be not well received.

- Submit a pull request with the pull request template `RFC PR`. As a pull request
  the RFC will receive design feedback from the larger community, and the author
  should be prepared to revise it in response.

- Now that your RFC has an open pull request, use the issue number of the PR to
  update your `0000-` prefix to that number.

- Each PR will be labeled accordingly to the RFC proposal.

- RFC with some comments and reviews are prefered, so feel free to assignee
  people in particular to get help identifying stakeholders and obstacles.

- At some point, a member of the Zom Organization will propose a "final
  commentting period" (FCP), along with a disposition for the RFC: close,
  postpone, merge.

  - This decision is taken when enough of the tradeoffs have been discussed
    and resolved. That does not require consensus among all participants in
    the RFC thread (which can be impossible). However, the arguments supporting
    the disposition on the RFC needs to have already been clearly articulated.

- In most cases, the FCP period is quiet, and the RFC is either merged or
  closed. However, sometimes substantial new arguments or ideas are raised,
  the FCP is canceled, and the RFC goes back into development mode.

- When the FCP is ended and the RFC has been approved, a member of the Zom
  Organization if possible already implied in the RFC will:
  - Create an issue that track the implementation of the feature in the
    [Zom repository].
  - And in the comment of the issue, a brief explenation of the RFC
    (the brief explenation can just be the `summary` section of the RFC).
  - Add the link of the issue in the RFC header
  - Add the relevant labels on the tracking issue
  - Merge the RFC.

## The RFC life-cycle
[The RFC life-cycle]: #the-rfc-life-cycle

Once an RFC becomes "active" then authors may implement it and submit the
feature as a pull request to the Zom repo. Being "active" is not a rubber
stamp, and in particular still does not mean the feature will ultimately be
merged; it does mean that in principle all the major stakeholders have agreed
to the feature and are amenable to merging it.

Furthermore, the fact that a given RFC has been accepted and is "active"
implies nothing about what priority is assigned to its implementation, nor does
it imply anything about whether a Zom developer has been assigned the task of
implementing the feature. While it is not *necessary* that the author of the
RFC also write the implementation, it is by far the most effective way to see
an RFC through to completion: authors should not expect that other project
developers will take on responsibility for implementing their accepted feature.

Modifications to "active" RFCs can be done in follow-up pull requests. We
strive to write each RFC in a manner that it will reflect the final design of
the feature; but the nature of the process means that we cannot expect every
merged RFC to actually reflect what the end result will be at the time of the
next major release.

In general, once accepted, RFCs should not be substantially changed. Only very
minor changes should be submitted as amendments. More substantial changes
should be new RFCs, with a note added to the original RFC. Exactly what counts
as a "very minor change" is up to the sub-team to decide.


## Reviewing RFCs
[Reviewing RFCs]: #reviewing-rfcs

While the RFC pull request is up, the sub-team may schedule meetings with the
author and/or relevant stakeholders to discuss the issues in greater detail,
and in some cases the topic may be discussed at a sub-team meeting. In either
case a summary from the meeting will be posted back to the RFC pull request.

A sub-team makes final decisions about RFCs after the benefits and drawbacks
are well understood. These decisions can be made at any time, but the sub-team
will regularly issue decisions. When a decision is made, the RFC pull request
will either be merged or closed. In either case, if the reasoning is not clear
from the discussion in thread, the sub-team will add a comment describing the
rationale for the decision.


## Implement an RFC
[Implement an RFC]: #implement-an-rfc

Some accepted RFCs represent vital features that need to be implemented right
away. Other accepted RFCs can represent features that can wait until some
arbitrary developer feels like doing the work. Every accepted RFC has an
associated issue tracking its implementation in the Zom repository; thus that
associated issue can be assigned a priority via the triage process that the
team uses for all issues in the Zom repository.

The author of an RFC is not obligated to implement it. Of course, the RFC
author (like any other developer) is welcome to post an implementation for
review after the RFC has been accepted.

If you are interested in working on the implementation for an "active" RFC, but
cannot determine if someone else is already working on it, feel free to ask
(e.g. by leaving a comment on the associated issue).


## License
[License]: #license

Licensed under Apache License, Version 2.0 [LICENSE](/LICENSE) or
<http://www.apache.org/licenses/LICENSE-2.0>. This files may not be copied,
modified, or distributed except according to those terms.

> See [notice](/NOTICE) for more informations.


## Contribution
[Contribution]: #contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
licensed as above, without any additional terms or conditions.

**The Zom RFCs process is highly inspired by [the Rust RFC process](https://github.com/rust-lang/rfcs)**

[Discord Server]: https://discord.gg/pcDknYP9Bf
[official Zulip server]: https://zom-lang.zulipchat.com/
[Zom repository]: https://github.com/zom-lang/zom
[RFC repository]: https://github.com/zom-lang/rfcs
