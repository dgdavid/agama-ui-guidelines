# UI principles

Everyone can use Agama comfortably, however they use it: with a mouse, a
touch screen, only a keyboard, a screen reader, or zoomed in. Accessibility is
built in from the start, not added later as a layer on top.

Nine rules. When a design choice runs into one of them, the rule wins.
Everything else in the UI can be argued about. These cannot.

## At a glance

1. [The keyboard reaches everything](#1-the-keyboard-reaches-everything):
   anything a mouse can do, the keyboard can do too.
2. [Nobody gets less information](#2-nobody-gets-less-information): whatever
   the screen shows, a screen reader says.
3. [If it can't be used, it isn't there](#3-if-it-cant-be-used-it-isnt-there):
   no greyed-out controls, the reason in words instead.
4. [Don't get in the way](#4-dont-get-in-the-way): no errors while typing,
   and no focus moving behind the user's back.
5. [Never lose what the user did](#5-never-lose-what-the-user-did): typed
   text and deliberate choices survive.
6. [One way to do each thing](#6-one-way-to-do-each-thing): a single path
   per task, familiar patterns first.
7. [Plain words, in every language](#7-plain-words-in-every-language):
   written for users, and written to be translated.
8. [Standards first](#8-standards-first-our-own-code-when-they-fall-short):
   HTML, then the W3C patterns, then PatternFly, our own code when they fall
   short.
9. [Every screen, every zoom](#9-every-screen-every-zoom): a layout that fits
   small screens and puts large ones to use.

## 1. The keyboard reaches everything

Anything a mouse can do, the keyboard can do too: get there, use it, and get
out again. Focus never gets stuck: a dialog keeps it inside while it is
open, and there is always a way out. A control made of several parts, such as
a group of radios, a menu or a row of tabs, is one stop on the Tab key, and
the arrow keys move inside it. Focus is always visible, never clipped, and
stands out at 3:1 in every theme.

*Why:* installations happen on virtual machines, remote consoles and with
assistive technology. A working mouse is never a given.

## 2. Nobody gets less information

Whatever the screen shows, a screen reader says. Color, position or a red
border never carry meaning on their own: words say the same thing, both on
the screen and to the screen reader.

*Why:* a hint that only the eyes can catch is a hint some users never get,
and a hint carried only by color is lost on anyone who can't tell the colors
apart.

## 3. If it can't be used, it isn't there

Don't show greyed-out controls to explain what is unavailable. Leave the
control out, and put the reason in words where the user will read it. A value
the user cannot change is shown as text, not as a locked input.

*Why:* disabled controls are easy to miss, hard to read in some themes, and
they offer something that cannot happen.

*The exceptions:*

- A button that sends something waits while it is being sent.
- A dialog's confirm button may wait for the one thing it confirms, such as a
  device picker's "Use…" until a device is picked.
- An option in a set the user is already looking at, such as a menu or a
  group of choices, may stay visible but unavailable *(playground)*. It keeps
  focus and gives its reason in its own text. An option that never makes
  sense is left out, and an action is never renamed into its own refusal.

A form's submit button never waits for its fields, however short the form is.
It stays available, and the attempt says what is missing or wrong.

*Why:* a single step next to the button needs no explanation. A form is
checked when it is submitted, and every form behaves the same way, so nobody
has to guess which kind of button they are looking at.

## 4. Don't get in the way

- No errors while typing: input is checked when the user submits.
- The user always knows when a choice takes effect: a form on submit, a page
  that applies each choice at once by showing its result right away. Nothing
  touches the system until the installation starts.
- Focus never moves behind the user's back.
- Nothing covers the screen longer than the work it waits for.

*Why:* a screen that changes while you are still working on it is
disorienting for everyone, and more so for screen reader users.

## 5. Never lose what the user did

Typed text survives switching options. A deliberate choice is never overridden
by a default, or by a later choice about something else. Changes from the
server never overwrite a form being edited. The view survives a reload, the
Back button and a shared link.

*Why:* redoing work the installer threw away is the fastest way to lose a
user's trust.

## 6. One way to do each thing

Every task has a single path. Don't add a second button "for convenience".
When there is a familiar pattern, use it before inventing a clever one.

*Why:* two ways to do one thing double the questions and the clutter, and
familiar behavior needs no explanation.

*The exception:* the same setting may live in two places when each serves a
different task, such as a quick change while viewing something and setting it
while editing it. Both places always show the same value.

## 7. Plain words, in every language

Write for someone who wants a working system, not for someone who knows how
Agama works inside. Every text is written so it can be translated well: whole
sentences, with context for the translator.

*Why:* jargon excludes people, and a sentence that cannot be translated
reaches the user in English.

## 8. Standards first, our own code when they fall short

Use what already exists, in this order: native HTML elements, the W3C
accessibility patterns, then PatternFly. The target is WCAG 2.2, level AA.
When PatternFly only half solves the problem, writing our own is the right
call. A departure from a W3C pattern needs a stated reason that helps
accessibility.

*Why:* standard behavior is behavior users and assistive tools already know. A
half-fitting component still leaves the gap.

Where we look: [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/), the
[ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/),
PatternFly's own guidelines, and the work of people and teams like the
[GOV.UK Design System](https://design-system.service.gov.uk/),
[Heydon Pickering](https://inclusive-components.design/) or
[Adrian Roselli](https://adrianroselli.com/).

## 9. Every screen, every zoom

Agama works on whatever screen it gets, from a phone to a wide monitor, zoomed
in or out. Responsive goes both ways: a small screen gets a layout that fits,
and a large one gets its space put to use.

*Why:* the installer can be driven from a virtual machine window, a laptop, a
tablet or a phone, and zoom changes the width a layout gets on any of them.
