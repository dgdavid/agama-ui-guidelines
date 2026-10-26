# Open questions

What the guidelines deliberately leave undecided. Writing these as rules now
would freeze them too early.

## Came up, not settled

- In multi-value fields, Tab commits the value and keeps focus there. That
  departs from the W3C pattern and is waiting for feedback.
- One checkbox per license, while the preferred UX is a single checkbox.
- A link styled as a button when it sits next to a real button.
- The default dialog width.
- Whether the summary should reopen the last storage view.
- Whether the error page stays on the minimal layout.
- Collapsible software categories: prototyped and parked.

## Not settled anywhere yet

The structure page marks these as *to be agreed* rather than inventing
answers:

- Button order inside forms and dialogs.
- Focus after navigation and after submit.
- When to ask before a destructive action.
- Small-screen behaviour in general.
- A stated WCAG target.
- Anatomy of the storage device sheet (in progress).

## Follow-ups in the Agama repository

- `form/conventions.md` is 2469 lines. Once the structure page holds the field
  patterns in plain words, it can shrink to its technical decisions and move
  under `doc/ui/guidelines/`.
- Page and Popup TSDoc carry structure decisions (Back vs Cancel, dismissible
  vs must-answer dialogs). The structure page now states them, and the TSDoc
  can link there instead.
- The principles could explain design choices to users too, so they are
  written to go on the website unchanged.
- The "still living next to their code" table in `doc/ui/guidelines.md` merges
  into Decisions. Those docs move under `doc/ui/guidelines/` one by one,
  starting with forms once it is trimmed, about 60% shorter.
- Weak TSDoc to improve when touched: `TextField`, `InstallerOptionsMenu`,
  `NestedContent`.
- `web/README.md` is stale: it still mentions JSDoc and `@ts-check`.
