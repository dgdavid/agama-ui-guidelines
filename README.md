# Agama UI guidelines (proof of concept)

This repository is a proof of concept for issue #4072: writing down the
reasoning behind the Agama web UI in plain words, so that anyone can add a
setting, an area or a form without having to ask first.

It is not the final text. It tests two things:

- whether the three levels proposed in the issue (principles, structure and
  technical) work as a format, and
- whether the rules written in them are the right ones.

If both hold, the pages move to `doc/ui/` in the Agama repository with few
changes.

## What is in it

| Page | Read it when |
| --- | --- |
| [Principles](principles.md) | Once. The rules that are never broken |
| [Structure](structure.md) | Before building something new |
| [Technical guidelines](guidelines.md) | While writing the code |
| [Open questions](open-questions.md) | When you want to help settle what isn't decided yet |
| [What is left to do](TODO.md) | When you want to see what the guidelines still ask of the code |

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
