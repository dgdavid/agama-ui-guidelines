# Web UI technical guidelines

How to build what [the structure](structure.md) describes. Each entry settles
a question that keeps coming back in reviews, so it gets decided once and
looked up afterwards.

## Decisions

| Topic | Answers |
| --- | --- |
| [URL as UI state](https://github.com/agama-project/agama/blob/master/doc/ui/guidelines/url-state.md) | Which view state goes in the address bar, and how to keep the URLs sane |
| [Forms](https://github.com/agama-project/agama/blob/master/web/src/components/form/conventions.md) | Field patterns, validation, TanStack Form usage, file layout |
| [Pages and sections](https://github.com/agama-project/agama/blob/master/web/src/components/layout/conventions.md) | Naming a section, heading levels, extending shared containers |
| [Tests](https://github.com/agama-project/agama/blob/master/web/src/test-conventions.md) | Which render helper to use, how to mock, fake timers |
| [Theming](https://github.com/agama-project/agama/blob/master/doc/theming.md) | The roles a product can restyle, and the ones it cannot |
| [Web terminal](https://github.com/agama-project/agama/blob/master/doc/web-terminal.md) | Opening it, keyboard access, the session lifecycle |

## Components worth reading first

Their TSDoc is the documentation. This index only says where to look.

| Component | Read it for |
| --- | --- |
| `layout/Page` | Page anatomy, `Page.Section` and its naming rules |
| `layout/Header`, `layout/StandardLayout`, `layout/MinimalLayout` | What the masthead holds, and which pages get the shared tools |
| `layout/SideBySideLayout` | The arrangement for single-purpose screens |
| `core/Popup` | Dismissible and must-answer dialogs, the action vocabulary |
| `form/ReadOnlyField` | Showing a value that cannot be changed |
| `form/DropdownField`, `form/RadioGroupField` | Choices, keyboard behavior, the footer entry |
| `form/ArrayField`, `form/multi-select-field/MultiSelectField` | Several values in one field, and the keyboard model |
| `form/SearchableSelectField` | Long lists with type-to-search |

## Adding a guideline

A topic earns a page when it is a decision rather than a description: two
reasonable people could do it differently, and the codebase needs them to
agree. How a single component behaves belongs in its TSDoc.

Write the decision and the reason for it, then stop. Implementation detail
ages badly in prose and is better read from the code.
