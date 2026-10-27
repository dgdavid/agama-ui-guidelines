# What is left to do

The work these guidelines create. Decisions the team still has to make live
in [Open questions](open-questions.md) instead.

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
- [ ] Run the screen size checks (structure, Screen sizes): 375 and 768 wide,
  and 400% zoom, have never been tried.

## Research

- [ ] List every control that opens a dialog, and whether it is announced as
  opening one. Then decide if it is worth it on all of them.
- [ ] Check the UI against WCAG 2.2 AA once the guidelines are approved,
  starting with what 2.2 adds: focus not hidden behind the floating side
  panel or the terminal (2.4.11), 24×24 px targets (2.5.8), pasting into the
  login password (3.3.8), no repeated entry (3.3.7). Also the dark theme's
  2.5:1 borders against the 3:1 that `doc/theming.md` asks for.

## Changes in Agama

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
  alert, and the side panel opens below that alert. Then drop *(planned)*
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

## Ideas

- The principles could also explain design choices to users, so they are
  written to go on the website unchanged.
