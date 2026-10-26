# How the UI is put together

The shape of the interface, and the reason behind each part. Read
[the principles](principles.md) first: this page applies them.

## The map

```
Installation (summary, at /)
 ├─ Localization, Network, Storage, Software, Users, System...   one page per area
 │    └─ edit pages                                            reached from their area
 └─ Install  →  confirmation  →  progress  →  finished / failed
```

- **The summary is the hub.** Every area is one line on it, and that line
  shows the real choice ("GNOME", "No desktop selected"), not a generic
  "Configured".
- **Problems show up where they live:** on the summary, and in the area that
  has them. They don't follow the user onto every other page.
- **Installing is a deliberate step.** The confirmation screen covers the whole
  window, says what data will be lost, and links straight to the area to fix
  it.

## The header

```
[ Product logo, name ]
[ Installation › Storage › Edit "/home" ]       [lang] [progress] [appearance] [⋮]
```

- **The left side says where you are.** The product shows what is being
  installed, and the breadcrumb shows the path. Its last item is the page
  title.
- **The right side has the same tools on every page:**
  - language and keyboard, because they are needed anywhere, a password page
    included;
  - the progress monitor, always present so it is easy to find;
  - appearance;
  - "More options": show the configuration, download logs, terminal, change
    product.
- **There is no call to action in the header.** An "Install" button there
  would duplicate the summary and start endless debates about its label.
- **Icons with tooltips save room.** The tooltip is for the eyes: the control
  already has its accessible name.

## Pages

| Layout | For | Examples |
| --- | --- | --- |
| Standard | Everything inside the installation flow | Summary, every area, edit pages |
| Minimal | Pages that stand alone, with nothing to navigate to | Login, progress, finished, failed, errors |

Pages that stand alone usually lay out their content side by side: an icon, a
title and a sentence on one side, the one thing to do on the other.

- **One title per page**, and sections below it. No heading level is skipped.
- **A section has a visible title or no name at all.** An invisible name is the
  last resort.
- **The reading order is the screen order.** Layouts also work right to left.

## Where actions go

| The action affects | It goes | Example |
| --- | --- | --- |
| The data of a form | Under the form: submit, then cancel | Accept / Cancel |
| A whole section, such as adding to it | At the end of the section, after its content | "Add connection" |
| A whole section, and is rarely needed | In the section's menu, in its header | "Reset to defaults" |
| One item in a list | In that row's menu | Edit, Delete |
| Nothing on this page, or rarely needed | "More options" in the header | Download logs |

- **Cancel goes back.** Leaving a form with unsaved changes asks first;
  changing the view of the same page never does. *When to confirm other
  destructive actions is still to be agreed.*
- **No sticky action bar.** The actions belong to the form they submit.
- **The order of buttons inside forms and dialogs is still to be agreed.**

## Forms

**Two ways to edit settings.** The page and its controls tell the user which
one applies:

- **In a form**, with Accept and Cancel, on a page for creating or editing
  something. Every checkbox, radio and field waits for the submit, even one
  that would make sense on its own.
- **Applied at once**, outside any form: a switch on a page that shows
  something, or an action in a menu. Also areas where each choice changes a
  calculated result, as in storage. These settings:
  - never sit inside a form, and a form never holds a switch;
  - show what each choice will cause while it is being chosen.

The rest of this section is about forms.

- **A form has one submit.** Its settings never save themselves one checkbox
  at a time.
- **Checked on submit.** After the first attempt, errors update as the user
  fixes them. Errors from the server show at the top of the form.
- **Mark what is optional**, with "(optional)". No asterisks for what is
  required.
- **A value the user can't change is shown as plain text.** A field that can't
  be edited isn't rendered at all.
- **Help sits under the field, in a few words.** Never only in a tooltip, and
  no examples that repeat the default value.
- **Values the installer fills in step aside once the user types.** It never
  overwrites the user's own text.
- **Anything that loses data says so,** right next to the choice.

How visible a field should be depends on how many people need it. Pick the
first rung that fits:

1. **Always shown.** Most people need it.
2. **Revealed by a choice the user makes** ("Static IP" reveals the address
   fields). Prefer a choice of mode over a "Configure X" checkbox.
3. **Revealed by an opt-in checkbox.** For options most people never touch.
4. **An entry at the end of a list,** for the rare path ("Browse with
   details…"). It never becomes a second control next to the field.

## Dialogs or pages

| Need | Use |
| --- | --- |
| Changing settings | A page with a form |
| Browsing details or picking an item | A dialog over the page |
| A question the installer must get answered | A dialog without a close button |

- **A dialog the user can walk away from** has a close button and closes with
  Escape.
- **Every dialog has a name.** Its confirm button says what it does: "Use
  enp1s0", not "OK".
- **Nothing is applied until confirmed.**
- **Show before acting:** the configuration is shown before it is downloaded.
- **A menu entry that opens a dialog ends in "…"**, and is announced as
  opening one.

## Tables and lists

- **Rows highlight on hover and on keyboard focus**, but they don't pretend to
  be links.
- **A selection inside a table is one Tab stop.** The arrow keys move within
  it.
- **Cut-off names stay complete for screen readers and on hover.**
- **Sort order, filters and searches live in the address bar,** so a reload or
  a shared link lands on the same view.

## Feedback

- **Background work shows in the progress monitor.** A blocking overlay covers
  only the page that is waiting, and only until that work is done.
- **Progress shows the step and the total.** No made-up percentages.
- **A long side action,** such as downloading logs, gets a toast when it starts
  and another when it finishes.
- **One place makes announcements for screen readers.** It keeps working while
  a dialog is open. A permanent hint belongs on its control, not in an
  announcement.
- **A dead end always offers a way out.** An empty page says why it is empty
  and what to do: "Go to network settings", "Try again".
- **Partly bad settings keep their good parts:** the user sees "Invalid
  settings", not a crash. A missing item gets a "not found" page, and a crash
  gets a readable error page.

## Words

- **Short labels when the context already says the rest:** "Name", not
  "Connection name", inside a connection form.
- **Sentence case.** Whole sentences, never stitched together from pieces.
- **A note for translators on every string:** what it is, and where it shows
  up.
- **During a string freeze, reuse existing strings.** Note the better wording
  as a follow-up.

## Appearance

- **Two independent settings:** light, dark or follow the system; and normal or
  high contrast.
- **Products restyle through a fixed set of roles,** and only those. A role a
  product leaves unset changes nothing. High contrast always wins over
  branding.
- **The right theme applies from the first paint,** with no flash of the wrong
  colors.

## Terminal

- **It docks at the bottom of the window, splitting the screen.** It is not a
  tab, a pop-up or a drawer: the page stays visible and the browser keeps its
  shortcuts.
- **It opens from "More options".** The session survives moving between pages.
- **It has a stop in front of it:** Enter goes in, Ctrl+Shift+L comes back out.

## Recipes

**A new setting in an existing area**

1. Pick its visibility rung, from the four in Forms above.
2. Add it to the area's form. Mark it optional if it is.
3. Check it on submit, with an error the user can act on.
4. Update the area's line on the summary if the setting changes it.

**A new area**

1. Give it a line on the summary that shows the actual choice.
2. Create a Standard page. The breadcrumb reads Installation › Area.
3. Report its problems on the summary and on its own page, nowhere else.

**A new dialog**

1. Make sure it shouldn't be a page instead: settings go on pages.
2. Decide whether the user may walk away. If yes, add a close button and
   Escape.
3. Give it a name and a confirm button that says what it does.

Then try it with the keyboard alone, and with a screen reader.
