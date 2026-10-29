# What is left to do

The work these guidelines create. Decisions the team still has to make live
in [Open questions](open-questions.md) instead.

## Rules to confirm with the team

Added by the review against WCAG 2.2 AA and the APG. Each one stays here
until the team agrees with it, or is removed from the pages if not.

- [ ] Focus is never hidden behind other content (principles, 1).
- [ ] A waiting button keeps the focus (principles, 3).
- [ ] Both orientations work, and 320 wide is checked (principles, 9;
  structure, Screen sizes).
- [ ] Tooltips show on focus, close with Escape, and use the control's name
  (structure, The header).
- [ ] The browser tab names the page (structure, Pages).
- [ ] Help and errors are tied to their field (structure, Forms and Words).
- [ ] Focus goes somewhere sensible when the opener is gone (structure, Pages,
  side panels and dialogs).
- [ ] Questions that must be answered are alert dialogs (structure, Dialogs).
- [ ] A toast never holds the only copy of an error or action (structure,
  Feedback).
- [ ] A side panel that covers the page behaves as a dialog (structure,
  Screen sizes).
- [ ] The recipes check at 400% zoom (structure, Recipes).
- [ ] A control that shows more names what it shows (structure, Words).
  Added after the first team feedback.
- [ ] Agama may set its own rule over PatternFly or other guidance when it
  serves users better in an installer, never at the cost of a standard, and
  says what it departs from and why (principles, 8).
- [ ] A waiting button says it is waiting to screen readers (principles, 3).
  Added after reading React Aria, as are the four below.
- [ ] The browser's own error messages never show (structure, Forms).
- [ ] A toast stays at least five seconds, waits while the pointer or the
  focus is on it, and can be closed (structure, Feedback).
- [ ] A failed submit reaches screen readers, by an announcement or by moving
  focus (structure, Keyboard and focus). WCAG asks for it, and it came up
  while comparing React Aria's answer with the code.
- [ ] Editing the text of a combobox clears the highlighted option
  (structure, Keyboard and focus).
- [ ] An option in a list or a menu holds only text and icons (structure,
  Keyboard and focus).

## Checks against the code

Claims in the guidelines that still need checking.

- [ ] "A form never holds a switch" (structure, Forms): look for forms that use
  a switch today.
- [ ] "Reset to defaults" in the section's menu (structure, Where actions go):
  check it still sits there on the new Storage page.
- [ ] "A menu entry that opens a dialog ends in '…'" (structure, Pages, side
  panels and dialogs): check the menus follow it.
- [ ] "Toolbars wrap instead of scrolling sideways, tables stay tables": check
  before adding it to Screen sizes.
- [ ] "'Automatic' says what it will be and why" and "Switching mode clears
  the errors of the mode left behind" (structure, Forms): both come from
  notes only, check the forms follow them.
- [ ] "Typing in a combobox never picks a match on its own", "Enter and Space
  toggle an expandable section" and "Enter in a dialog's field submits the
  dialog, unless the field uses Enter itself" (structure, Keyboard and
  focus): check the code follows them.
- [ ] "A form that stays open after saving tells 'saved' apart from 'nothing
  changed'" and "Recomputing part of a form keeps the old content on screen"
  (structure, Feedback): check the code follows them.
- [ ] "The header keeps the same height on every page" (structure, The
  header): check it, including the minimal layout's empty header.
- [ ] "A control's accessible name includes its visible label, word for
  word" (structure, Words): comes from notes only, look for controls whose
  `aria-label` replaces or rewords the visible text.
- [ ] "Words say the same thing, both on the screen and to the screen reader"
  (principles, 2): look for meaning carried by color, such as a status or an
  error, whose only text is hidden from sight.
- [ ] "Inline styles only for computed one-off values" and "PatternFly utility
  classes come from its style modules" (guidelines, Styling): check the 21
  files with inline styles, and how utility classes are used.
- [ ] "High contrast is PatternFly's AAA theme" (structure, Appearance):
  check that PatternFly's high contrast theme does reach 7:1.
- [ ] "The tooltip shows on hover and on keyboard focus, and Escape hides it"
  (structure, The header): check the header's icon buttons.
- [ ] Help and errors tied to their field (structure, Forms and Words):
  check that every field's help and error reach screen readers with the
  field, not only in `ArrayField`, `SearchableSelectField` and
  `MultiSelectField`.
- [ ] "A button that sends something keeps the focus while it waits"
  (principles, 3): check what happens to focus on a submit button that
  waits.
- [ ] "Focus goes somewhere sensible when the opener is gone" (structure,
  Pages, side panels and dialogs): check where focus lands after deleting an
  item from its own row menu.
- [ ] "A toast never holds the only copy of an error or action" (structure,
  Feedback): check what every toast holds.
- [ ] "Focus is always visible" (principles, 1) in forced colors, such as
  Firefox overriding the page colors: buttons draw their focus ring as a
  box shadow, which forced colors remove. Check it, and add a transparent
  outline if the ring disappears.
- [ ] "A choice that keeps existing data is remembered, and comes back as
  soon as it is possible again" (structure, Forms): confirm it in the UI on
  a disk with a partition that has data. Keep its data ("Current"), change
  the mount point to swap, then back. Tests cover it, but it has not been
  seen in the running UI.
- [ ] Run the screen size checks (structure, Screen sizes): 320, 375 and 768
  wide, both orientations, and 400% zoom, have never been tried.
- [ ] "A screen reader hears that a waiting button is waiting" (principles,
  3): check what Orca says when a submit button starts waiting.
- [ ] "A toast stays at least five seconds and waits while the pointer or the
  focus is on it" (structure, Feedback): the download toast closes after 8
  seconds whatever the user does. Make its timer wait.
- [ ] "Editing the text of a combobox clears the highlighted option"
  (structure, Keyboard and focus): `SearchableSelectField` follows it,
  `MultiSelectField` highlights the best match as the user types. Check
  that one with a screen reader before changing it.
- [ ] "An option in a list or a menu holds only text and icons" (structure,
  Keyboard and focus): look for options and menu items that hold a button
  or a link.
- [ ] The header's tooltips on a touch screen (structure, The header):
  PatternFly shows them on the tap that presses the button. Check whether
  one stays stuck over the dialog the button opens.

## Research

- [ ] List every control that opens a dialog, and whether it is announced as
  opening one. Then decide if it is worth it on all of them.
- [ ] Check the UI against WCAG 2.2 AA once the guidelines are approved,
  starting with what 2.2 adds: focus not hidden behind the floating side
  panel or the terminal (2.4.11), 24×24 px targets (2.5.8), pasting into the
  login password (3.3.8), no repeated entry (3.3.7). Also the dark theme's
  2.5:1 borders against the 3:1 that `doc/theming.md` asks for.
- [ ] Write a "check before merge" page: the passes to run before merging UI
  work, with a matrix of machine states, testing with Orca and Firefox
  first. My notes on checking the storage page are a starting point.
  React Aria tests with VoiceOver, JAWS, NVDA and TalkBack, not Orca, so
  what it found about screen readers still needs trying with Orca.

## Changes in Agama

- [ ] Make a failed submit reach screen readers. Today its alert is only
  scrolled into view: focus stays on the submit button and nothing is
  announced, while WCAG 4.1.3 asks for one or the other. Which of the two is
  the open question on focus after a failed submit. Confirm the gap with Orca
  first.
- [ ] Clean up the deprecated `Page.Back`, `Page.Cancel` and `Page.Submit`
  against master: remove what nothing uses any more, and the TSDoc that still
  describes them. The guidelines are already written as if this were done.
- [ ] On the storage page branch: open the side panel with a history push,
  and switch items while it is open with a replace (`use-sheet.ts`, the links
  in `EntryRow.tsx` and `SheetOpener.tsx`), and update the TSDoc that
  explains the replace. Then drop *(planned)* from the side panel rule.
- [ ] On the `storage-result-popup` branch (in progress): the side panel
  covers the page on narrow windows, with a backdrop and the page underneath
  out of reach; the storage result moves to a dialog opened from a one-line
  alert, and the side panel opens below that alert. The covering side panel
  keeps focus inside and closes with Escape. Then drop *(planned)*
  from those rules (structure, Screen sizes and Pages, side panels and
  dialogs), and from the side panel holding details only.
- [ ] Once the new Storage page lands on master, drop *(planned)* from the
  side panel row in the table of Pages, side panels and dialogs.
- [ ] Once the storage side panel is settled, document its anatomy in its
  TSDoc. When a second area adopts a side panel, move the shared anatomy to
  the structure page.
- [ ] Once `core/Sheet` lands on master, add it to the components in
  guidelines.md as the side panel.
- [ ] `form/conventions.md` is 2469 lines. Once the structure page holds the
  field patterns in plain words, shrink it to its technical decisions and
  move it under `doc/ui/guidelines/`.
- [ ] The Popup TSDoc carries a structure decision (dismissible vs
  must-answer dialogs). Link it to the structure page instead.
- [ ] Merge the "still living next to their code" table in
  `doc/ui/guidelines.md` into Decisions, and move those docs under
  `doc/ui/guidelines/` one by one, starting with forms once it is trimmed.
- [ ] Improve the weak TSDoc of `TextField`, `InstallerOptionsMenu` and
  `NestedContent` when touching them.
- [ ] Update `web/README.md`, which still mentions JSDoc and `@ts-check`.
- [ ] Rename our own classes that don't start with `agm-` yet (`custom-`,
  `sticky-`, `proposal-` and others, about 13 on master).
- [ ] Remove the unused `core/RowActions`, the only row menu with vertical
  dots.
- [ ] Make every form's errors say what is wrong with each field (structure,
  Words): add an example to network's format errors, and give localization
  one message per field once the string freeze ends. iSCSI's errors sit in
  one alert above the form, and get fixed with its migration below.
- [ ] Name the browser tab after the page ("Storage · Agama"), which is
  "Agama" on every page today (`web/src/index.html`). Then drop *(planned)*
  from that rule (structure, Pages).
- [ ] Give the dialogs that must be answered the alert dialog role, which
  the questions don't have today. Then drop *(planned)* from that rule
  (structure, Dialogs).
- [ ] Replace the "New" pill in the storage result with text and one small
  mark, which the new Storage page does anyway. Then drop *(planned)* from
  the status rule (structure, Appearance).
- [ ] Move the remaining forms to TanStack Form. A quick search on master
  finds, among others, the iSCSI forms, the WiFi connection form, the
  software patterns form and several storage settings pages (boot,
  encryption, LVM, space policy). Make the full list first.
- [ ] Once the ESLint `translated-prop` rule lands, mention it in the
  Translations section of guidelines.md.

## Ideas

- The principles could also explain design choices to users, so they are
  written to go on the website unchanged.
- Once the storage side panel lands, reword principle 3 around what it
  protects against, something unavailable with no visible reason: "Nothing is
  unavailable without its reason". The option exception would become the
  rule, the waiting buttons would follow from it (their reason is the single
  step next to them), and forms would remain the one explicit rule.
- Explain the jargon the UI cannot avoid, such as GPT, btrfs or by-path,
  where it shows up, for example with a short help text. Principle 7 asks for
  plain words, and some of these have no plain replacement.
