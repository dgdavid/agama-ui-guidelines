# Open questions

What the guidelines deliberately leave undecided. Writing these as rules now
would freeze them too early.

## Came up, not settled

- In multi-value fields, Tab commits the value and keeps focus there. That
  departs from the W3C pattern and is waiting for feedback.
- One checkbox per license, while the preferred UX is a single checkbox.
- The product selection form is the one form whose submit button waits: until
  a product, a mode and the license acceptance are given, with a line under
  the button saying which is missing. It should probably behave like every
  other form. Making it do so was tried while migrating the form to the new
  forms stack, and left out so that
  [#3791](https://github.com/agama-project/agama/pull/3791) could ship. Two
  things to decide before retrying: whether the line under the button stays
  once the attempt reports the same thing, and where focus goes after a
  failed attempt.
- Settings applied at once could do nothing when the value already chosen is
  chosen again. Storage menus send the request again today.
- Settings applied at once could show the chosen value right away, before the
  result arrives. Storage waits under the progress overlay today, and shows
  the value once the result is back.
- Rechecking a form's errors as the user fixes them, once a submit has
  failed. Wanted, as long as the form library makes it possible.
- Asking before leaving a form with unsaved changes by any way other than
  Cancel: another link, a changed URL, closing the tab. Wanted, and React
  Router's navigation blocking may make it possible. Changing the view of the
  same page, such as a filter or the sort order, must never ask.
- Whether every control that opens a dialog should be announced as opening
  one. Only the header's language and keyboard buttons are today.
- The width at which the side panel stops covering the page and sits next to
  the list.
- A way to jump between the list and the side panel on wide screens, such as
  landmarks or a shortcut.
- A side panel that covers the page without blocking it, with careful focus
  handling instead of a backdrop.
- Moving focus to the content of a page after going to it, and whether it
  lands on the heading or on the main content. Needs a screen reader to
  decide.
- Where focus goes after a failed submit. One attempt kept it in place and
  let the alert announce itself.
- Back and Cancel returning to where the user left the page, while a link or
  a reload opens it at the top.
- A link styled as a button when it sits next to a real button.
- The default dialog width.
- Dialogs that can be maximized, or that get an address of their own when it
  makes sense.
- Whether the summary should reopen the last storage view.
- Whether the error page stays on the minimal layout.
- Keeping language and keyboard reachable on the login page, whose header is
  empty: a password typed with the wrong keyboard layout fails.
- Collapsible software categories: prototyped and parked.

## Not settled anywhere yet

The structure page marks these as *to be agreed* rather than inventing
answers:

- Button order inside forms and dialogs.
- Anatomy of the storage device side panel (in progress).

