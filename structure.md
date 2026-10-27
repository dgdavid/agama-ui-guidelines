# How the UI is put together

The shape of the interface, and the reason behind each part. It applies
[the principles](principles.md).

## At a glance

- [The map](#the-map): the summary is the hub, one line per area showing the
  real choice, and installing is a deliberate step.
- [The header](#the-header): the left says where you are, the right holds the
  same tools on every page, and there is no call to action.
- [Pages](#pages): one title with sections below it, named sections as
  landmarks, and no Back button.
- [Where actions go](#where-actions-go): Cancel never asks, a confirmation
  only before writing to the disks, destructive actions last.
- [Forms](#forms): settings in a form or applied at once, one submit,
  checked on submit, and the control picked by the choice it offers.
- [Pages, side panels and dialogs](#pages-side-panels-and-dialogs): picked by
  the interaction. A side panel holds details, a dialog blocks the page.
- [Tables and lists](#tables-and-lists): rows open their side panel through a
  real link, long names are cut in the middle, the view lives in the address.
- [Feedback](#feedback): background work in the progress monitor, the kind of
  empty said, one place for announcements.
- [Keyboard and focus](#keyboard-and-focus): arrows explore, Enter commits,
  and changing the view never moves focus.
- [Words](#words): controls instruct and reports describe, links named after
  where they go, plain words that translate well.
- [Appearance](#appearance): looks match importance, a status is text, one
  color per status, AA contrast.
- [Screen sizes](#screen-sizes): from a phone to a wide monitor, no maximum
  width, the side panel covering the page on narrow windows.
- [Terminal](#terminal): docked at the bottom, always available, with a stop
  in front of it.
- [Recipes](#recipes): the steps for a new setting, a new area or a new
  dialog.

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
- **A summary line goes through fixed states:** a placeholder while loading,
  then the problem if there is one, then the actual choice. A hint such as
  "No desktop selected" shows only when the product asks for that choice. A
  line is never empty.
- **Status claims only what it knows.** The progress monitor reports
  background tasks only. When idle it says "No pending tasks", in a neutral
  color, never "Ready".
  *Why:* a green "Ready" would mislead while problems still block the
  installation.
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

  > [!NOTE]
  > Menus in the breadcrumb, to jump between areas without going back to the
  > summary every time, are being discussed in
  > [#3913](https://github.com/agama-project/agama/issues/3913).

- **The product keeps its full name,** never shortened, and the header keeps
  the same height on every page.
  *Why:* a short name can clash with the trademark, and a header that changes
  height makes the page jump.
- **A new interface language applies at once,** without reloading the page.
- **The right side has the same tools on every page of the standard layout:**
  - language and keyboard, because they are needed anywhere, a password page
    included;
  - the progress monitor, always present so it is easy to find, except on the
    pages that show the progress themselves;
  - appearance;
  - "More options": show the configuration, download logs, terminal, change
    product.

  A page may put its own tools first, such as storage's device connections.
- **There is no call to action in the header.** An "Install" button there
  would duplicate the summary and start endless debates about its label.
- **Icons with tooltips save room.** The tooltip is for the eyes: the control
  already has its accessible name.

## Pages

| Layout | For | Examples |
| --- | --- | --- |
| Standard | Everything inside the installation flow | Summary, every area, edit pages, progress, finished |
| Minimal | Pages that stand alone, with nothing to navigate to and an empty header | Login, failed, errors |

Pages that stand alone usually lay out their content side by side: an icon, a
title and a sentence on one side, the one thing to do on the other.

- **One title per page, and sections below it.** Heading levels follow the
  outline: sections start at h2, and nothing inside the page adds a second
  h1, an empty state included. How big a heading looks is a design choice,
  apart from its level.
- **A section has a visible title or no name at all.** An invisible name is the
  last resort.
- **Named sections are landmarks; controls that belong together are a
  group.** A set of related controls under a heading is a group named by that
  heading, not a section of its own.
  *Why:* screen reader users jump between landmarks, so each one has to be a
  real part of the page.
- **Pages have no Back button.** The breadcrumb leads up, and the browser goes
  back. A page that has to send the user elsewhere uses a link named after
  where it goes.
- **The reading order is the screen order.** Layouts also work right to left.

## Where actions go

| The action affects | It goes | Example |
| --- | --- | --- |
| The data of a form | Under the form: submit, then cancel | Accept / Cancel |
| A whole section, such as adding to it | At the end of the section, after its content | "Add connection" |
| A whole section, and is rarely needed | In the section's menu, in its header | "Reset to defaults" |
| One item in a list | In that row's menu | Edit, Delete |
| Nothing on this page, or rarely needed | "More options" in the header | Download logs |

- **Cancel goes back, and never asks:** it already means "discard".
- **Ask only before writing to the disks:** installing, or formatting a DASD
  now. The confirm button says what it does ("Format now") and uses the danger
  style.
  *Why:* everything else can still be changed before installing, so a
  question would only slow the user down.
- **Everything else shows its cost while it is being chosen,** naming what
  is lost ("including Windows 11") rather than asking afterwards.
- **Destructive actions on an item come last in its menu,** after a
  separator, in the danger style.
- **Undoing a plan for something that stays is not destructive**
  *(playground)*: "Stop reusing" is plain, not a red "Delete".
- **Managing the machine is not configuring it.** Tools that act on the
  machine, such as rescanning devices or connecting iSCSI, zFCP and DASD, sit
  in the page's own menu in the header. Resetting the page's settings goes in
  the section's menu. The two never merge.
- **Form actions come after the content they confirm,** in the same place on
  every page, never inside a group of choices or a list item.
  *Why:* the reading order follows the task, first choose and then confirm,
  and a consistent place is easier to find.
- **A row's menu is named after its row** ("Actions for enp1s0"), behind the
  same horizontal dots everywhere.
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
- **Checked on submit.** Errors are checked again on the next submit. Errors
  from the server show at the top of the form.
- **Mark what is optional**, with "(optional)". No asterisks for what is
  required.
- **A value the user can't change is shown as plain text,** with the reason
  when circumstances leave only one answer ("New partition (all partitions on
  /dev/vdd are already assigned)"). When there could never be a choice, the
  field isn't rendered at all.
- **Help sits under the field, in a few words.** No examples that repeat the
  default value.
- **Short facts go in place, not behind an info icon.** A tooltip on static
  text can't be reached with the keyboard. If an explanation needs a popover,
  its trigger is a real button.
- **Values the installer fills in step aside once the user types.** It never
  overwrites the user's own text.
- **No field waits, disabled, for another one.** Every field stays usable,
  and the dependency is checked on submit.
- **Dependent fields react once the user has finished typing,** on leaving
  the field or picking a suggestion, not on every keystroke.
- **A later change never swaps in a different value.** When it makes an
  earlier choice impossible, the field falls back to automatic, and a choice
  to keep what exists comes back once it is possible again.
- **"Automatic" says what it will be and why.** The first sentence is the
  result ("XFS will be used for /home"), the second what decided it.
- **Inherited values say where they come from** *(playground)*: "LUKS2 · from
  the installation settings". The way back is named after the scope: "Use the
  installation setting".
- **Switching mode clears the errors of the mode left behind.**
- **No two controls share an accessible name.** A generic visible label
  ("Mode") gets its group's name in its accessible name ("Hostname mode").
  *Why:* screen readers and voice control can't tell identical names apart.
- **A placeholder is never the only instruction,** and doesn't repeat the
  label or the help.
- **Known values are offered,** not listed in help text for the user to
  retype.
- **One field per line.** One list of settings is never split into two
  columns.

Pick the control by the choice it offers:

| The choice | Control |
| --- | --- |
| One of a short fixed list, up to about a dozen | Dropdown |
| One of hundreds | Searchable select |
| Several free values | Multi-value text field |
| Several from a known list | Multi-select |
| One of two or three weighty options | Radios, each with its consequence on one line |

How visible a field should be depends on how many people need it. Pick the
first rung that fits:

1. **Always shown.** Most people need it.
2. **Revealed by a choice the user makes** ("Static IP" reveals the address
   fields). Prefer a choice of mode over a "Configure X" checkbox.
3. **Revealed by an opt-in checkbox.** For options most people never touch.
   An optional field that many people fill stays visible instead, marked
   "(optional)".
4. **An entry at the end of a list,** for the rare path ("Browse with
   details…"). It never becomes a second control next to the field.

## Pages, side panels and dialogs

Pick by the interaction, not by the look. A dialog says "stop and deal with
me": it blocks the page. A side panel says "here is more about what you are
looking at": the page stays in use.

| Need | Use |
| --- | --- |
| Settings with Accept and Cancel | A page with a form |
| Details of one item in a list, with its settings applied at once | A side panel *(planned)* |
| Picking from a list too detailed for a dropdown | A dialog, opened from a plain selector |
| A view of the whole, such as the storage result | A dialog *(planned)* |
| A question the installer must get answered | A dialog without a close button |

- **Opening a dialog or a side panel moves focus into it,** onto the current
  choice if there is one. Closing it returns focus to the control that opened
  it.

### Side panels

- **A side panel holds details, nothing else** *(planned)*. It may hold
  settings applied at once and links to other pages, but never a form with
  Accept and Cancel, and never alerts or a view of the whole.
  *Why:* each earlier panel that held something else, a form or the
  installation issues, had to be dropped.
- **A side panel lives in the address** *(planned)*. Opening it adds one step
  to the history, and moving to another item while it is open does not. Back
  closes it; the next Back leaves the page.
  *Why:* with no step at all, Back on a panel that covers the page leaves the
  page by surprise; with a step for every item, leaving the page takes as many
  Backs as items were looked at.
- **What changes the whole stays in view** *(planned)*. An alert about the
  whole page is one line, with an action that opens its full content in a
  dialog, and the side panel opens below it. A change made in the panel shows
  up in the alert at once.

### Dialogs

- **A dialog the user can walk away from** has a close button and closes with
  Escape.
- **Every dialog has a name.** Its confirm button says what it does: "Use
  enp1s0", not "OK".
- **A dialog always opens with the current values.** What was left
  unconfirmed last time is gone.
- **Nothing is applied until confirmed.**
- **Show before acting:** the configuration is shown before it is downloaded.
- **A menu entry that opens a dialog ends in "…".**

## Tables and lists

- **Rows highlight on hover and on keyboard focus**, but they don't pretend to
  be links.
- **In a list with a side panel, a row opens it through a real link on the
  item's name** *(playground)*, stretched over the row, never through a click
  handler on the row. The row's menu keeps its own Tab stop, and the open
  item is marked as current. Lists without a side panel have no row link.
- **A selection inside a table is one Tab stop.** The arrow keys move within
  it.
- **Long names are cut in the middle,** and stay complete for screen readers
  and on hover, with no extra Tab stop. A sighted keyboard user can't see the
  full name: an accepted gap.
- **Columns earn their place.** A column that says the same on every row, or
  is mostly empty, goes. Headers stay in the markup even when not shown, and
  every table has a name.
- **Search matches what people type:** it ignores accents and case, matches
  hidden terms such as codes or the UTC offset, and accepts words in any
  order.
- **No search box on a short list.**
- **Filtering keeps the layout still.** Groups stay in place, and an empty one
  says "No patterns match the filter". The result count is shown and announced
  politely. Selection counters include selected items the filter hides.
- **Sort order, filters and searches live in the address bar,** so a reload or
  a shared link lands on the same view. Tables inside dialogs keep them to
  themselves, the layout never goes in the address, and typing in a filter
  doesn't add a history step per key.

## Feedback

- **Background work shows in the progress monitor.** A blocking overlay covers
  only the page that is waiting, and only until that work is done.
- **Progress shows the step and the total.** No made-up percentages.
- **A long side action,** such as downloading logs, gets a toast when it starts
  and another when it finishes.
- **A form that stays open after saving says so,** telling "saved" apart from
  "nothing changed". The message goes away on the next edit.
- **Recomputing part of a form keeps the old content on screen.** Any loading
  stays inside that part.
- **When a choice can't apply to an item, the item says so** *(playground)*:
  "cannot be shrunk", not "keep", with the first reason underneath.
- **Say which kind of empty:** nothing planned, not used, or could not be
  worked out. The big empty-state layout is only for screens that are truly
  empty. A section with nothing in it gets one plain line.
- **Standing information is not an alert.** It gets a quiet treatment, and an
  ordinary result has no alert heading and no announcement.
- **One place makes announcements for screen readers.** It keeps working while
  a dialog is open. Announcements are polite, and assertive only when missing
  one would lose data. A new one replaces a pending one, and noisy sources
  wait until they settle. A summary that is recalculated often is never
  announced, and a hint that changes is linked to its field instead.
- **A dead end always offers a way out.** An empty page says why it is empty
  and what to do: "Go to network settings", "Try again".
- **Partly bad settings keep their good parts:** the user sees "Invalid
  settings", not a crash. A missing item gets a "not found" page, and a crash
  gets a readable error page.

## Keyboard and focus

- **In a dropdown, the arrow keys explore and Enter or Space commits.**
  Escape leaves the value unchanged.
  *Why:* a choice often shows or hides other fields, so it should happen only
  when the user means it.
- **Typing in a combobox filters, but never picks a match on its own:** "eth"
  never silently becomes "eth0".
- **A field holding several values is still one Tab stop.** The arrow keys
  reach the values.
- **Enter and Space toggle an expandable section;** the arrow keys never do.
- **A widget that takes every key has a stop in front of it,** with a key to
  go in and another to come out, both said on screen. The terminal is one.
- **Enter in a dialog's field submits the dialog.**
- **Changing the view of a page never moves focus:** a filter, the sort
  order, a tab.
- **Moving through a list never moves focus into the side panel**
  *(playground)*. Going in takes a deliberate step.
- **A failed submit brings its alert into view,** not the top of the page.

## Words

- **Short labels inside a form, full ones on their own.** "Name", not
  "Connection name", inside a connection form. Breadcrumbs, links and row
  buttons name their object: "Edit connection", "Configure sda".
- **Controls instruct, reports describe:** "Delete" on the button, "To be
  deleted" in the report, never worded as already done. Each act has one verb
  and one noun everywhere ("actions", never "changes").
- **A link is named after where it goes,** not after what it reports. Danger
  color goes on the statement, not on the link.
- **Every place a sentence names is a link to it,** like "Uses" and "Used by"
  between devices.
- **Repeat only when it helps:** to keep the user oriented (a side panel
  repeats the name of its row), to spare remembering (a summary in the list,
  the details in the panel), or for a different task. Repetition hurts when
  it adds noise, shows one action twice, can drift out of sync, or makes a
  screen reader say the same thing twice. No intro paragraph restates the
  table below it.
- **Error messages say what is wrong with that field.** "Required" and "wrong
  format" are different messages, and a format error shows an example ("e.g.
  20 GiB"). The label, the help and the errors use the same word.
- **A control's accessible name starts with its visible label,** so voice
  control finds it by what the user sees.
- **Plain words, not symbols or internals:** "at least 5 GiB", not "≥". No
  internal names ("space policy"), outcomes rather than mechanisms, and never
  "the control below".
- **Text in another language is marked with its language,** such as each
  entry in the language list.
- **Sentence case.** Whole sentences, never stitched together from pieces.
- **A note for translators on every string:** what it is, and where it shows
  up.
- **A string freeze is never dodged by reusing a string from another
  context.** A string is reused only where it means the same thing in the
  same place. New text waits, tracked as a follow-up, and strings that will be
  needed are reserved early.

## Appearance

- **Two independent settings:** light, dark or follow the system; and normal or
  high contrast.
- **Products restyle through a fixed set of roles,** and only those. A role a
  product leaves unset changes nothing. High contrast always wins over
  branding.
- **The right theme applies from the first paint,** with no flash of the wrong
  colors.
- **How loud something looks matches how much it matters.** Values read far
  more often than changed are text links, not buttons. Hierarchy comes from
  type size and weight, not from boxes. One bold element per row. Color,
  frames and marks never repeat what the words already say.
- **A status is text with one small mark, never a pill** *(planned)*. A tag
  that names something, such as "Beta", "Recommended" or a file system label,
  may be a pill. An action's icon, such as the trash can, never marks a
  status.
- **One status, one color,** the same in alerts, help text and icons. No
  status color looks like a link, and when one collides with the brand color,
  the brand changes.
- **Contrast is AA:** 4.5:1 for text, muted and disabled text included, and
  3:1 for icons, borders, focus rings and everything else that isn't text.
  High contrast is PatternFly's AAA theme, and no branding overrides it.
  *Why:* AAA in the default themes would flatten the visual hierarchy, and
  the high contrast setting exists for users who need more.
- **When the system asks for reduced motion, nothing moves.**
- **Supported browsers:** Firefox, the browser on the ISO, and current
  standard engines. No workarounds for older ones.

## Screen sizes

- **Every screen works from a phone to a wide monitor.** Check it at 375 wide
  (a phone), 768 (a tablet), 1024 (the usual virtual machine), 1440, 1920 and
  2560, and at 200% and 400% zoom.
- **The app as a whole has no maximum width.** What gets hard to read is
  limited on its own: text around 65 to 75 characters wide, a narrow form on
  a fluid page.
  *Why:* zoom changes the width a layout gets, so a cap only avoids large
  screens instead of adapting to them.
- **Wide screens are put to use** *(playground)*: a side panel next to its
  list, sections side by side, where it helps.
- **A side panel covers the page on narrow windows** *(planned)*, with a
  backdrop and the page underneath out of reach. On wide windows it sits next
  to the list, with neither.
- **A side panel belongs to a page, a dock to the whole window.** A dock takes
  height, not width: the terminal docks at the bottom.
  *Why:* the header and the page are laid out by window width, so a dock
  beside them would push them out of sight.
- **Side-by-side screens become one column** on narrow windows, in reading
  order.
- **A feature that cannot fit says so** instead of squeezing in: the terminal
  says it is unavailable below 1024×768.

## Terminal

- **It docks at the bottom of the window, splitting the screen.** It is not a
  tab, a pop-up or a drawer: the page stays visible and the browser keeps its
  shortcuts.
- **It opens from "More options".** The session survives moving between pages.
- **It stays available during and after the installation.**
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

1. Make sure it shouldn't be a page or a side panel instead: settings with
   Accept and Cancel go on a page, details of an item in a side panel.
2. Decide whether the user may walk away. If yes, add a close button and
   Escape.
3. Give it a name and a confirm button that says what it does.

Then try it with the keyboard alone, and with a screen reader.
