# UI principles

Eight rules. When a design choice runs into one of them, the rule wins.
Everything else in the UI can be argued about. These cannot.

## 1. The keyboard reaches everything

Anything a mouse can do, the keyboard can do too: get there, use it, and get
out again. Nothing ever traps the focus. Each control is one stop on the Tab
key, and the arrow keys move around inside it.

*Why:* installations happen on virtual machines, remote consoles and with
assistive technology. A working mouse is never a given.

## 2. Nobody gets less information

Whatever the screen shows, a screen reader says. Color, position or a red
border never carry meaning on their own. Behind each of them there is a name,
a heading or an announcement.

*Why:* a hint that only the eyes can catch is a hint some users never get.

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

A form's submit button never waits for its fields, however short the form is.
It stays available, and the attempt says what is missing or wrong.

*Why:* a single step next to the button needs no explanation. A form is
checked when it is submitted, and every form behaves the same way, so nobody
has to guess which kind of button they are looking at.

## 4. Don't get in the way

- No errors while typing: input is checked when the user submits.
- Nothing is saved until the user asks.
- Focus never moves behind the user's back.
- Nothing covers the screen longer than the work it waits for.

*Why:* a screen that changes while you are still working on it is
disorienting for everyone, and more so for screen reader users.

## 5. Never lose what the user did

Typed text survives switching options. A deliberate choice is never overridden
by a default. The view survives a reload, the Back button and a shared link.

*Why:* redoing work the installer threw away is the fastest way to lose a
user's trust.

## 6. One way to do each thing

Every task has a single path. Don't add a second button "for convenience".
When there is a familiar pattern, use it before inventing a clever one.

*Why:* two ways to do one thing double the questions and the clutter, and
familiar behavior needs no explanation.

## 7. Plain words, in every language

Write for someone who wants a working system, not for someone who knows how
Agama works inside. Every text is written so it can be translated well: whole
sentences, with context for the translator.

*Why:* jargon excludes people, and a sentence that cannot be translated
reaches the user in English.

## 8. Standards first, our own code when they fall short

Use what already exists, in this order: native HTML elements, the W3C
accessibility patterns, then PatternFly. Contrast meets WCAG AA. When
PatternFly only half solves the problem, writing our own is the right call.

*Why:* standard behavior is behavior users and assistive tools already know. A
half-fitting component still leaves the gap.
