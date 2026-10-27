# Web UI technical guidelines

How to build what [the structure](structure.md) describes. Each entry settles
a question that keeps coming back in reviews, so it gets decided once and
looked up afterwards.

## At a glance

- [Decisions](#decisions): the technical docs that settle recurring
  questions, from URL state to theming.
- [Translations](#translations): user-facing text is typed
  `TranslatedString`, and code uses the words the UI shows.
- [Styling](#styling): `agm-` classes, PatternFly restyled through its
  tokens, logical properties.
- [Components worth reading first](#components-worth-reading-first): where
  the TSDoc explains a pattern.
- [Tools](#tools): checking contrast.
- [Adding a guideline](#adding-a-guideline): when a topic earns a page.

## Decisions

| Topic | Answers |
| --- | --- |
| [URL as UI state](https://github.com/agama-project/agama/blob/master/doc/ui/guidelines/url-state.md) | Which view state goes in the address bar, and how to keep the URLs sane |
| [Forms](https://github.com/agama-project/agama/blob/master/web/src/components/form/conventions.md) | Field patterns, validation, TanStack Form usage, file layout |
| [Pages and sections](https://github.com/agama-project/agama/blob/master/web/src/components/layout/conventions.md) | Naming a section, heading levels, extending shared containers |
| [Tests](https://github.com/agama-project/agama/blob/master/web/src/test-conventions.md) | Which render helper to use, how to mock, fake timers |
| [Theming](https://github.com/agama-project/agama/blob/master/doc/theming.md) | The roles a product can restyle, and the ones it cannot |
| [Theming packaging](https://github.com/agama-project/agama/blob/master/doc/theming_packaging.md) | Getting a product or brand appearance onto a medium |
| [Web terminal](https://github.com/agama-project/agama/blob/master/doc/web-terminal.md) | Opening it, keyboard access, the session lifecycle |

## Translations

- **User-facing text props are typed `TranslatedString`,** so an untranslated
  string fails the type check. Text that comes from the backend stays
  `string`.
- **Code uses the words the UI shows:** "installation", not "overview". A
  URL that moves keeps a redirect for a while.

## Styling

- **Inline styles only for computed one-off values.** Everything else goes in
  a stylesheet.
- **Our own classes start with `agm-`.**
- **`!important` only for reduced motion,** where the override has to win
  over any animation.
- **PatternFly is restyled through its tokens.** Overriding its classes
  happens only in `_patternfly-overrides.scss`, as a last resort.
- **Logical properties, not left and right,** so layouts flip for right to
  left languages.
- **PatternFly utility classes are imported from its style modules.**

## Components worth reading first

Their TSDoc is the documentation. This index only says where to look.

| Component | What its TSDoc explains |
| --- | --- |
| `layout/Page` | Page anatomy, `Page.Section` and its naming rules |
| `layout/Header`, `layout/StandardLayout`, `layout/MinimalLayout` | What the masthead holds, and which pages get the shared tools |
| `layout/SideBySideLayout` | The arrangement for single-purpose screens |
| `core/Popup` | Dismissible and must-answer dialogs, the action vocabulary |
| `form/ReadOnlyField` | Showing a value that cannot be changed |
| `form/DropdownField`, `form/RadioGroupField` | Choices, keyboard behavior, the footer entry |
| `form/ArrayField`, `form/multi-select-field/MultiSelectField` | Several values in one field, and the keyboard model |
| `form/SearchableSelectField` | Long lists with type-to-search |
| `core/Interpolate` | Links and other markup inside a translated sentence |
| `hooks/use-field-label` | A field's accessible name, and how to add context while keeping the visible label in it |
| `useAnnounce` (`context/announcer`) | Telling screen readers what changed, through the global live region |

## Tools

- `web/scripts/check-contrast.js` computes the contrast ratio between
  colors, for picking the values of a product's color roles.

## Adding a guideline

A topic earns a page when it is a decision rather than a description: two
reasonable people could do it differently, and the codebase needs them to
agree. How a single component behaves belongs in its TSDoc.

Write the decision and the reason for it, then stop. Implementation detail
ages badly in prose and is better read from the code.
