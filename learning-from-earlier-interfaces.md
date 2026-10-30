# Learning from earlier interfaces

Agama started in 2022 as D-Installer, an experimental Linux installer driven
from a web interface, a challenge of its own at the time. Coming from YaST, the
team had to find the best way to make the switch and keep up with the web,
accessibility above all.

The goal grew too. D-Installer started as a radically different idea: a
minimal installer, leaving the rest of the configuration for after the system
boots, at first boot or through Cockpit. Agama now offers much more, and its
unattended installation can configure far more than the web interface shows.
The web interface is meant to stay a subset of that: the settings most people
need, done well. Offering everything would be welcome one day, but it is not
the aim.

Each of those steps showed what the interface needed next, so it has gone
through four incarnations, and each earlier one left something that is still in
the current one. This page tells that story so the reasons behind each change
are not lost, and the next change can build on them instead of repeating what
was already tried. The rules in [the principles](principles.md) and [the
structure](structure.md) come from that experience.

## At a glance

- [No wizard](#no-wizard): from the first day, the user moves freely between
  settings, most of them already set by the product's defaults.
- [Timeline](#timeline): every change of interface, with the blog post and
  pull requests behind it.
- [One summary page](#2022-one-summary-page): a single page to read and
  change everything, until the settings outgrew it.
- [A page per section](#2023-a-page-per-section): the summary became a hub,
  each area got its own page, and dialogs slowly came back.
- [A navigation sidebar](#2024-a-navigation-sidebar): a classic layout with
  PatternFly, while the overview still lacked a clear summary.
- [The overview as the hub](#2026-the-overview-as-the-hub): back to the hub,
  with a read-only summary and the lessons of the versions before.
- [Looking ahead](#looking-ahead): the current interface grows step by step,
  with these reasons in mind.

## No wizard

Agama has never been a wizard, and that is on purpose. A wizard walks everyone
through every step in a fixed order. Agama starts from a proposal built on the
defaults of the product being installed, so for most settings people only need
to check them and change what matters to them. The first public release
described the summary as "the starting point, so you do not need to traverse
any wizard to get into it"
([blog](https://agama-project.github.io/blog/2022/03/31/first-public-release)).

That gives the user freedom. They can go to any setting in any order, come back
to it later, and start the installation as soon as they are happy. That matters
most when something takes a while, such as reading the software repositories:
instead of waiting for the next step of a wizard, the user goes on with other
settings. The 2024 redesign kept "the absence of wizard, to allow the user to
move as freely as possible" as one of its goals
([#1202](https://github.com/agama-project/agama/pull/1202)), and the current
interface still works the same way.

Some choices have no good default, because they belong to the user and not
to the product, such as how to log in to the new system. Agama leaves those
to the user on purpose, and the summary says what is still missing, so they
are the only settings everyone has to visit before installing.

## Timeline

| When | What changed | Sources |
| --- | --- | --- |
| Jan 2022 | D-Installer is announced with a web interface built on Chakra UI, and moves to PatternFly two weeks later | [blog](https://agama-project.github.io/blog/2022/01/18/announcing-d-installer), [#15](https://github.com/agama-project/agama/pull/15) |
| Mar 2022 | **One summary page**: a single-column, mobile-first layout with the Installation Summary as the starting point | [#44](https://github.com/agama-project/agama/pull/44), [blog](https://agama-project.github.io/blog/2022/03/31/first-public-release) |
| Jan 2023 | A sidebar behind a hamburger menu, first to hold the download of logs | [#379](https://github.com/agama-project/agama/pull/379), [blog](https://agama-project.github.io/blog/2023/02/16/d-installer-0-7) |
| Mar 2023 | **A page per section**: each area moves out of the summary into its own page | [#443](https://github.com/agama-project/agama/pull/443), [blog](https://agama-project.github.io/blog/2023/03/30/d-installer-0-8) |
| Apr 2023 | The options of each page move from the sidebar to a menu in the header | [#545](https://github.com/agama-project/agama/pull/545) |
| Jan 2024 | The issues page goes away, and each section shows its own issues | [#886](https://github.com/agama-project/agama/pull/886) |
| May 2024 | Agama 8 no longer runs inside Cockpit, and gets its own HTTP API | [blog](https://agama-project.github.io/blog/2024/05/17/agama-8) |
| Jun 2024 | **A navigation sidebar**: the interface is remade on PatternFly, with a sidebar to move between sections | [#1202](https://github.com/agama-project/agama/pull/1202), [blog](https://agama-project.github.io/blog/2024/06/28/agama-9) |
| Oct 2024 | "Install" moves to the header, reachable from every page | [#1690](https://github.com/agama-project/agama/pull/1690), [blog](https://agama-project.github.io/blog/2025/01/21/Agama-11) |
| Nov 2024 | "Install" is always available, and shows what blocks the installation when something does | [#1778](https://github.com/agama-project/agama/pull/1778) |
| Feb 2025 | PatternFly 6 and a new look | [#2033](https://github.com/agama-project/agama/pull/2033), [blog](https://agama-project.github.io/blog/2025/02/27/releasing-version-12-and-a-roadmap) |
| Jan 2026 | **The overview as the hub**: a useful overview and a richer confirmation, then the sidebar goes away in favor of breadcrumbs | [#2988](https://github.com/agama-project/agama/pull/2988), [#3009](https://github.com/agama-project/agama/pull/3009), [blog](https://agama-project.github.io/blog/2026/03/20/agama-19) |
| Jun 2026 | The header shows the product on every page, the breadcrumb starts at "Installation", and the installer tools are in reach everywhere | [#3607](https://github.com/agama-project/agama/pull/3607), [blog](https://agama-project.github.io/blog/2026/06/16/agama-22) |
| Jun 2026 | Dark and high contrast appearances, and products can restyle the installer | [#3604](https://github.com/agama-project/agama/pull/3604), [blog](https://agama-project.github.io/blog/2026/08/11/dressed-for-success) |
| Sep 2026 | A terminal docked at the bottom of the window | [#3622](https://github.com/agama-project/agama/pull/3622), [#3868](https://github.com/agama-project/agama/pull/3868), [blog](https://agama-project.github.io/blog/2026/10/21/agama-25) |

## 2022: One summary page

The first interface was a single column, designed for a phone first, with the
Installation Summary as its central page. The values in the summary were links
themselves, such as the language or the target disk, and each one opened a
dialog to change it. A fixed header kept the title and the main actions in view
while the page scrolled ([#44](https://github.com/agama-project/agama/pull/44),
[blog](https://agama-project.github.io/blog/2022/03/31/first-public-release)).

```text
+------------------------------------------------+
| Installation Summary                           |
+------------------------------------------------+
| Language                                       |
| <English (US)>                                 |
|                                                |
| Product                                        |
| <openSUSE Tumbleweed>                          |
|                                                |
| Target                                         |
| </dev/vda>                                     |
| * Delete partition /dev/vda3 (15.98 GiB)       |
| * Create partition /dev/vda3 for / with btrfs  |
|                                                |
| Users                                          |
| Root password <is set>                         |
| User <suse> is defined                         |
+------------------------------------------------+
| SUSE   <About>                     [ Install ] |
+------------------------------------------------+

<link>  [button or field]
Each <value> opened a dialog to change it.
```

That choice served Agama well. Going for "a tiny, single-column, mobile first
layout" was meant to "encourage us to develop a simple, yet powerful, UI",
usable from devices of any size, and the summary as the starting point is
still the heart of Agama.

As settings were added, though, the summary filled with "a bunch of
cluttering links and modal dialogs for each available setting"
([#443](https://github.com/agama-project/agama/pull/443)). With reading and
changing mixed on the same page, it was hard to decide which parts of the
summary should be links and which should not.

## 2023: A page per section

So each area moved to a page of its own, to make the interface "more fluent,
self-explanatory" and rely less on dialogs
([#443](https://github.com/agama-project/agama/pull/443)). The summary became
a hub: each section title linked to its page, with a short summary of its
settings below it. A sidebar behind a
hamburger menu held the installer's own tools, such as downloading the logs
([#379](https://github.com/agama-project/agama/pull/379)).

```text
+------------------------------------------------+
| openSUSE Tumbleweed                        [=] |
+------------------------------------------------+
| <Localization>                                 |
| The system will use Italiano (it_IT)           |
| as its default language.                       |
|                                                |
| <Network>                                      |
| 1 connection set: Papaya 192.168.68.58/22      |
|                                                |
| <Storage>                                      |
| ! There is no suitable device for installation |
|                                                |
| <Software>                                     |
| Installation will take 963 MiB                 |
|                                                |
| <Users>                                        |
| No user defined yet                            |
+------------------------------------------------+
| SUSE                               [ Install ] |
+------------------------------------------------+

<link>  [button or field]
Each <title> leads to its page. [=] opens the sidebar with the
installer's own tools.
```

An area's page, Localization in this case:

```text
+------------------------------------------------+
| Localization                               [=] |
+------------------------------------------------+
| Language                                       |
| Spanish - Spain                                |
| <Change language>                              |
|                                                |
| Keyboard                                       |
| Spanish                                        |
| <Change keyboard>                              |
|                                                |
| Time zone                                      |
| Atlantic Ocean - Canary                        |
| <Change time zone>                             |
+------------------------------------------------+
| SUSE                                  [ Back ] |
+------------------------------------------------+

<link>  [button or field]
Each <Change ...> opened a dialog with the full list.
```

A page of its own gave each area room to grow. The sidebar was first meant as
the main navigation, but once the options of each page left it, it held only
general links ([#550](https://github.com/agama-project/agama/pull/550)). It
settled on holding "actions related to the installer itself", while everything
about the system to install stayed on the pages
([#886](https://github.com/agama-project/agama/pull/886)).

Not everything worked along the way. Dialogs slowly came back, this time on
the pages: changing the language, the keyboard or the time zone each opened
one ([blog](https://agama-project.github.io/blog/2023/12/22/agama-7)), and
almost every change ended up in a dialog of its own. The options of each page
first lived in
the sidebar, and users did not find them, because it was not clear when the
menu had changed ([#545](https://github.com/agama-project/agama/pull/545)).
They moved to a menu in the header. A page listing every issue went the same
way, and each section shows its own issues instead
([#886](https://github.com/agama-project/agama/pull/886)).

In time, the summary "lost all its value" and became "a sort of navigation
menu or index". Moving between sections meant going back and forth through
it, large screens were wasted, and it was "way weird landing in a page with a
big, green, and enabled Install button" that would fail before the user had
done anything ([#1202](https://github.com/agama-project/agama/pull/1202)). In
the words of the release post, "the user interface would not scale"
([blog](https://agama-project.github.io/blog/2024/06/28/agama-9)).

## 2024: A navigation sidebar

Until Agama 8, the web interface ran inside Cockpit. Agama 8 dropped it for a
new architecture with its own HTTP API
([blog](https://agama-project.github.io/blog/2024/05/17/agama-8)), and the
interface was remade a month later.

The next interface took a "more classic approach, with a sidebar that makes
navigation easier"
([blog](https://agama-project.github.io/blog/2024/06/28/agama-9)). It used
PatternFly "as much as possible to the point of looking familiar with Cockpit
UI but keeping some bits of Agama's identity"
([#1202](https://github.com/agama-project/agama/pull/1202)). Cockpit was no
longer part of the installer, but it is meant to be the management tool of the
installed system, so looking familiar would ease the step from installing to
managing.

```text
+--------------------------------------------------------------------+
| [=] SUSE Linux Enterprise Server 16.0             [ Install ! ]  v |
+--------------------------------------------------------------------+
|  > Overview        | Overview                                      |
|    Registration    |                                               |
|    Localization    | Localization                                  |
|    Network         | The system will use English (United States).  |
|    Storage         | Storage                                       |
|    Software        | Install using device /dev/sda, 30 GiB,        |
|    Authentication  | deleting all its content.                     |
|                    | Software                                      |
|                    | The installation will take 2.1 GiB.           |
+--------------------------------------------------------------------+

<link>  [button or field]
The sidebar moves between sections. When something blocks the
installation, [ Install ! ] lists it in a drawer.
```

The same Localization page:

```text
+--------------------------------------------------------------------+
| [=] SUSE Linux Enterprise Server 16.0             [ Install ! ]  v |
+--------------------------------------------------------------------+
|    Overview        | Localization                                  |
|    Registration    |                                               |
|  > Localization    | Language       Keyboard       Time zone       |
|    Network         | English - US   English (US)   Europe - Berlin |
|    Storage         | <Change>       <Change>       <Change>        |
|    Software        |                                               |
|    Authentication  |                                               |
+--------------------------------------------------------------------+

<link>  [button or field]
Each <Change> led to a page of its own, with the full list to pick from.
```

It brought lasting changes: PatternFly used fully, instead of building and
keeping our own components, and the router used as designed, with nested
routes and the address as the state of the view. "Install" also became
reachable from everywhere, first in the header
([#1690](https://github.com/agama-project/agama/pull/1690)), then always
available, showing what blocks the installation instead of failing
([#1778](https://github.com/agama-project/agama/pull/1778)). A disabled
"Install" with a tooltip was tried and dropped, because the explanation was
hard to write and to keep up to date.

The overview was still the weak spot. It "lacks a clear, insightful summary
that helps users quickly get the big picture", and the confirmation before
installing was "a small popup displaying minimal information"
([#2988](https://github.com/agama-project/agama/pull/2988)). While those fixes
were being made, the confirmation got a page of its own, which lasted only a
few days. That work showed that the first idea, with everything learned since,
still made a lot of sense, and that "a cleaner, hopefully more usable
interface" was possible without the sidebar
([#3009](https://github.com/agama-project/agama/pull/3009)).

## 2026: The overview as the hub

Today the overview is the hub of the installation, right after picking the
product when there is a choice to make: several products, or a product with
several modes. For every area, it shows what is actually chosen, such as the
desktop to install, rather than a generic "Configured". Each area is a page
reached from it, and the breadcrumb leads back. The confirmation before
installing is still a dialog, but a richer one: it asks to delete existing data
and install when that is what will happen, and says what data will be lost
([#2988](https://github.com/agama-project/agama/pull/2988),
[#3009](https://github.com/agama-project/agama/pull/3009)).

```text
+------------------------------------------------------------------------+
| openSUSE Tumbleweed                                                    |
| Installation                                     tasks  lang  theme  v |
+------------------------------------------------------------------------+
| Take a moment to review the installation settings below and adjust     |
| them as needed.                                                        |
|                                                                        |
| <System>                  <Language and region>     +----------------+ |
| Name c15t - Default NTP   English (United States)   | System         | |
| Using transient name,     Spanish keyboard -        | Information    | |
| which may change after    Europe/Berlin timezone    | Model: QEMU    | |
| reboot or network changes                           | CPU: Intel ... | |
|                                                     | Memory: 9 GiB  | |
| <Software>                <Network>                 | IPs: 192...    | |
| ACME Desktop              Auto                      +----------------+ |
| Requires 5.95 GiB         Configured with 1                            |
|                           connection                                   |
|                                                                        |
| <Authentication>          <Storage>                                    |
| Configured for the root   Use device sdc (80 GiB)                      |
| user                      Potential data loss                          |
|                                                                        |
| [ Install now with potential data loss ]                               |
+------------------------------------------------------------------------+

<link>  [button or field]
The overview is the hub: each <title> leads to its page, and the
breadcrumb on every other page starts at <Installation>.
```

And Localization today:

```text
+------------------------------------------------------------------------+
| openSUSE Tumbleweed                                                    |
| <Installation> > Language and region             tasks  lang  theme  v |
+------------------------------------------------------------------------+
| Language                                                               |
| [ English (United States)            v ]                               |
|                                                                        |
| Keyboard                                                               |
| [ English (US)                       v ]                               |
|                                                                        |
| Time zone                                                              |
| [ Europe/Berlin                      v ]                               |
|                                                                        |
| [ Accept ]  <Cancel>                                                   |
+------------------------------------------------------------------------+

<link>  [button or field]
One form: each field filters its list as the user types, and nothing
changes until Accept.
```

Since then, the header shows the product on every page, starts the breadcrumb
at "Installation", and drops the "Review and install" button, which competed
with the breadcrumb and with each page's own actions
([#3607](https://github.com/agama-project/agama/pull/3607)). The rest of the
work has gone into the parts: forms, storage, network, appearance,
accessibility and the terminal.

The release post calls this interface a step "closer to our original vision"
([blog](https://agama-project.github.io/blog/2026/03/20/agama-19)). In many
ways it returns to the interface from 2023: a summary as the hub, leading to a
page per area. That approach was set aside in 2024 as one that "does not scale"
and looked like "a dead end"
([#1202](https://github.com/agama-project/agama/pull/1202)). At the time, with
the product, its requirements and the team's experience all changing, that was
a reasonable call. Seen from today, though, the hub itself was not the problem,
and what changed is the summary: it is now read-only, with the same structure
for every area, and sums up only the choices that matter, while the pages
behind it keep their settings in view, and open a dialog or a side panel only
where one really helps.

The [structure](structure.md) describes this interface as it is today.

## Looking ahead

Each of these interfaces was the team's best answer to what Agama was at the
time. By 2026 the interface had "settled, with a stable layout, pages following
the same structure, and forms sharing one stack"
([#3761](https://github.com/agama-project/agama/pull/3761)). It is meant to
keep improving step by step, not to change shape again, and the reasons on this
page are there to help each of those steps move forward, not back.
