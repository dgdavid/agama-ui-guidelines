# Agama UI guidelines (proof of concept)

This repository is a proof of concept for issue #4072: writing down the
reasoning behind the Agama web UI in plain words, so that anyone can add a
setting, an area or a form without having to ask first.

It is not the final text. It tests two things:

- whether the three levels proposed in the issue (principles, structure and
  technical) work as a format, and
- whether the rules written in them are a good starting point to shape the
  final ones together.

If both hold, the team shapes the rules from here, and the pages move to
`doc/ui/` in the Agama repository.

## What is in it

| Page | What it covers |
| --- | --- |
| [Principles](principles.md) | The rules every part of the UI follows, and why |
| [Structure](structure.md) | How the UI is put together, from the summary and the header to forms, side panels, dialogs and words, with recipes for common additions |
| [Technical guidelines](guidelines.md) | How to build it: translations, styling, and the docs and components that answer recurring questions |
| [Open questions](open-questions.md) | What is deliberately left undecided |
| [What is left to do](TODO.md) | The claims still to check against the code, and the changes in Agama that make the planned rules true |

## Background

[Learning from earlier interfaces](learning-from-earlier-interfaces.md) is not
a guideline. It tells how the interface got here: the versions before this
one, and why each one changed, so the same mistakes are not made twice.

## How it was built

1. **From the pull requests.** An AI assistant (Claude Code) was told to read
   the descriptions of 157 web UI pull requests merged over the last twelve
   months, plus the docs already on master, and to extract the recurring UI
   decisions into three drafts. A rule became a principle only if it came back
   in many pull requests and was never traded away.
2. **Checked against my working notes.** The assistant was then told to read
   my working notes (plans, prototypes and review notes) against those drafts
   and pull out what they add: statements that don't match the code, answers
   to some open gaps, and rules no pull request had stated yet. Where it
   mattered, it checked those statements against the code.
3. **The storage prototype discussion.** The questions and answers I wrote
   after discussing the new Storage page with Áncor were read the same way,
   and added the rules about dialogs, side panels and screen sizes.
4. **What I do.** The assistant extracts and proposes. I decide what goes in
   and edit every rule before it lands here.

## Status of a rule

- **Decided:** shipped, or agreed by the team.
- **Planned:** agreed, not built yet.
- **Playground:** tried only in a prototype.

Anything still open lives in [Open questions](open-questions.md), not in the
pages.

## What is left to do

Some rules describe where the UI is going rather than where it is, and some
claims still need checking against the code. [TODO](TODO.md) lists that work,
so a rule marked *(planned)* always has the change that will make it true.

## How to review

Open an issue for anything you disagree with, find unclear, or know to be
wrong, quoting the rule and naming its page. One issue per topic, so each can
be discussed and closed on its own. Changes to the rules go through pull
requests, so they can be commented on line by line.
