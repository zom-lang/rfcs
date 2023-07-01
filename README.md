# ⚡ Zom Language Evolution

This repository contains **Request For Comments** (RFC), that describe the whole Zom Programming Language and its libraries.
The RFC process is intended to provide a consistent and controlled path for changes to Zom.

Many bug fixes, sentence correction can just be implemented and reviewed with the normal GitHub pull request workflow.

<!-- omit in toc -->
## Table of Content
- [The RFC Process](#the-rfc-process)
- [Review an RFC](#review-an-rfc)
- [Implement an RFC](#implement-an-rfc)
- [License](#license)


## The RFC process

In short, the Zom Programming language specification is driven through a RFC process, if you want to change the programming language or its libraries, you
must follow the RFC process :

- Fork the [evolution tracking repository](https://github.com/zom-lang/evolution)
- Copy `0000-template.md` to `text/0000-my-feature.md`, where `my-feature` is an unique identifier of the feature. For the moment, don't change the RFC number
  (`0000`).
- Fill the RFC according to the template (don't use abreviations) and put care into the details: RFC that doesn't have a convincing motivation, demontrate lack
  of understanding of the desigh impact or are disingenuous about the drawbacks or alternatives, tend to be not well received.
- Submit a pull request with the pull request template `Submit a RFC`. You need to have time, because there will probably be review, questions, comments about
  your RFC. It's prefered if you can answer the majority of them.
- Now, you have a pull request associated to your RFC proposal, use the PR number of your RFC to update your `0000-` prefix to that number.
- Each PR will be labeled with some GitHub labels.
- RFC with some comments and reviews are prefered, so feel free to assignee people in particular to get help identifying stakeholders and obstacles.
- At some point, a member of the Zom Organization will propose a "final commentting period" (FCP), along with a disposition for the RFC: close, postpone, merge.
  - This decision is taken when enough of the tradeoffs have been discussed and probably resolved. That does not require consensus among all participants in
    the RFC thread (which can be impossible). However, the arguments supporting the disposition on the RFC needs to have already been clearly articulated.
- When the FCP is ended and the RFC has been approved, a member of the Zom Organization (already implied in the RFC if possible) will:
  - Create an issue that track the implementation of the feature in [the Zom repository](https://github.com/zom-lang/zom).
  - And in the comment of the issue, a brief explenation of the feature.
  - Add the link of the issue in the RFC header
  - Merge the RFC.
- You can after, [implement the RFC into the compiler](#implement-an-rfc)


## Review an RFC

You can also contribute by review or make comments on an RFC pull request.


## Implement an RFC

If an RFC was been merged you can contribute to Zom by implementing the RFC :
- Read the RFC and make sure you have understand the RFC.
- Fork [`zom-lang/zom`](https://github.com/zom-lang/zom).
- Make sure you understood how the compiler works
- After the implementation of the RFC feature, create a PR in the [`zom-lang/zom`](https://github.com/zom-lang/zom) repo.
  - In the first comment, link the tracking issue of the RFC and the PR of the RFC.
  - If you haven't finished yet or you need help you can make a tasklist.
- You will have comments and / or reviews of your code.
- Before a member of the Zom Organization merge your PR, the CI must pass. If it doesn't you will need to fix your code.


## License

Licensed under Apache License, Version 2.0 [LICENSE](/LICENSE) or <http://www.apache.org/licenses/LICENSE-2.0> 

This files may not be copied, modified, or distributed except according to those terms.

> More informations [here](/NOTICE).


## Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you shall be licensed as above, without any
additional terms or conditions.
