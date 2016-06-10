

Contributing
============

All of our code is peer-reviewed (PR'd) via pull requests (also PR) from a dedicated Git branch. Our current process is something like this: One team member finishes some work and runs the units tests. Once they all pass, he then pushes the branch up to Bitbucket, creates a pull request (usually against the master branch) and adds _all_ the other front-end engineers as reviewers. Once at least two reviewers have marked the PR as approved, which usually takes well under 24 hours, the author can then merge the PR. 

## Discussion

This process works well in so far as its a relatively non-disruptive way of ensuring that everyone has a chance to comb over and offer feedback on proposed changes. A potential weakness of this process is that when there is a high volume of PRs it can be difficult for each reviewer to exercise the proper level of scrutiny for each type of change. The quality of the reviewing work may also be lowered by a bystander effect when there are many reviewers.

The issues of volume and bystanders can both be addressed by lowering the number of reviewers per PR. But what is the ideal number of reviewers and how should they be chosen? That's something we can and should experiment with.

Another potential problem with how PRs are currently done is the time and energy expended by reviewers in "ramping up" to a point where they can understand the proposed changes and offer useful feedback. This can be helped by:

1. favoring creating smaller PRs over larger PRs _while maintaining coherence_
2. by anticipating the reviewers' questions and proactively including that information in the PR. #2 has a side-benefit of the author explaining his changes in plain language, to himself as well as to the reviewers, and possibly catching some mistakes or oversights on his own.

> If you can't explain it simply, you don't understand it well enough.
> -- Albert Einstein

A suggestion for how to structure the descriptions for any non-trivial PR:

- Part One: Thesis, or how things currently are.
- Part Two: Antithesis, or what is the reason for this PR being created, what problem is being addressed?
- Part Three: Synthesis, or how this PR goes about solving the problem explained above.

It's also helpful to proactively leave comments around particularly tricky parts of the PR, either as comments in the code itself or comments made in Bitbucket's PR interface, whatever makes the most sense.

Also, extra points for pictures! Or even better, GIFs!

_Contribute to this discussion by creating a PR!_ (I know, so meta)
