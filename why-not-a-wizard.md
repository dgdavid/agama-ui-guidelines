# Why Agama is not a wizard

**TL;DR:** Agama starts from a working proposal built on the defaults of the
product being installed, so most people only need to check it and press Install,
while people who need something specific go straight to it. A wizard would make
everyone walk every step to reach the same result, and it would get harder to
keep in order with every setting and every background task added to the
installer.

## The appeal of a wizard

Many people come to Agama from YaST, whose installer walks through a sequence of
screens: Next, Next, Next, until the installation starts. A wizard is easy to
like. It gives a clear order, a sense of progress, and the reassurance that
nothing is forgotten, because every step has to be visited before the last one.
For an installer whose every setting needs an answer, that is a reasonable
design.

The Agama team comes from YaST too, and Agama took another path from its first
release, which presented the overview as "the starting point, so you do not need
to traverse any wizard to get into it"
([blog](https://agama-project.github.io/blog/2022/03/31/first-public-release)).
Even the YaST sequence ended in an overview of the installation settings, where
everything could still be changed. Agama simply starts there.

The goals of a wizard still hold. Agama reaches them another way, because most
of its settings already have a good answer before the user arrives.

## The product already made most decisions

Each product installed with Agama comes with its own defaults: the file systems
and partitioning, the software to install, the security setup, and more. Those
defaults are not arbitrary. They are what the people behind each product
consider the right setup for its audience, and they can differ a lot from one
product to another. A general purpose distribution, an immutable system for
containers and an enterprise server do not want the same disk layout or the same
software, yet all of them are installed with the same interface.

So Agama does not open with questions. It opens with a proposal that already
works, and an overview that tells what is going to happen. A wizard would ask
the user to confirm, one screen at a time, decisions the product has already
made well. For most people, that is just a series of Next buttons.

## Nothing important is left behind

A few choices do not have a good default, because they belong to the user and
not to the product, such as how to log in to the new system. A product may also
leave a choice to the user on purpose, such as which desktop to install. The
overview says when any of those is still missing. Install is always at hand, and
when something still blocks the installation, it says what. Before anything is
written to disk, the confirmation says which data will be lost, with a link to
the area to change it. Depending on the product, it can also point out a choice
left open even when the installation does not need it, such as not having picked
a desktop.

So whatever matters to the product and to the installer does not get forgotten.
Personal preferences are another matter, and a wizard does not guarantee them
either: clicking Next past a screen is as easy as not visiting it. Anything left
out can be set up later in the installed system, as on any other system.

## From less to more

Agama is meant for people who know nothing about storage or networking and for
people who know a lot about both. The interface serves both by asking only as
much as each person wants to give:

- Someone who does not care about the details reads the overview, sets what is
  still missing, and installs.
- Someone who needs a specific disk layout or a static network goes straight to
  that area, and goes as deep as they need, without passing through the areas
  they do not care about.

The whole interface follows that idea, not only the overview. The Network page
lists the connections, a connection shows its settings, and a form keeps its
less common options out of the way until they are needed. Each level adds detail
only for those who go there.

A wizard puts every area on everyone's path. The novice faces screens they
cannot answer, and the expert walks through screens they do not need to reach
the one they came for.

## A wizard with shortcuts

A wizard does not have to be strict. YaST lets the user jump from its final
summary straight to any section, and a wizard can list its steps in a side panel
and let the user pick any of them. That leaves two choices:

- **Shortcuts with limits,** such as jumping back to steps already visited, but
  never ahead to the ones still to come. The wizard keeps its promise that every
  step gets visited, but everyone still walks every step at least once, which is
  what the defaults are meant to save.
- **Shortcuts anywhere.** The order is only a suggestion, and the promise is
  gone. What remains is a hub with a recommended path, and that path suggests an
  order the installation does not need.

Agama saw this with its own sidebar of sections, used from 2024 to 2026. Some
people read it as a list of steps, and expected to go through them in order and
end on the overview
([#1770](https://github.com/agama-project/agama/issues/1770)). Agama keeps the
hub and drops the path: the overview is where everything starts, and where the
user comes back to.

## Steps tend to multiply

Today, only a couple of settings need an answer from the user. Tomorrow there
may be more, and in a wizard each one is a candidate for its own step. That
leads to two problems:

- **Reordering.** Every new step has to fit somewhere, and every place has
  consequences for the steps around it. The order is never settled; it is
  renegotiated with each addition.
- **Competition for steps.** Once steps exist, areas compete for one even when
  they have a perfectly good default, "because the user might want to change
  it". Each step looks harmless on its own, and together they bring back the
  long walk the defaults were meant to save.

Agama puts that effort into the overview instead. It does not lay out every
option of every area: each area gets a short summary of its most important
settings, as brief and clear as possible. That is enough to see what is going to
happen. When something needs a change, the area's page shows more, and every
level below it, such as a connection, a device or a form, shows a bit more
again. Nobody faces every option at once. Keeping those summaries short and
still useful is the hard part, and it is the part worth getting right.

## Background tasks and dependent steps

An installer has work that takes time, such as reading the software repositories
or calculating the storage proposal, and some settings depend on its result.

A wizard can hide that for a while: move on to the steps that do not depend on
the task, and put the dependent ones at the end. That works until a change makes
another step depend on something, and the wizard has to be reordered again. This
time, no new setting asks for it: how the installer works inside does. Little by
little, the order of the steps follows the installer's internals instead of what
makes sense to the person installing. And when the user reaches a dependent step
before the task is done, all they can do is wait for Next to become available.
Some installers fill those waits with a carousel of highlights, which says
little to the user and is one more thing to maintain.

Without a fixed path, waiting is less awkward. The user can keep working on
other areas, look around to see what each one offers, or simply stay in the
overview and watch it update.

## Not a first boot, not just another distribution

Comparisons with other setups are natural, and they help to see what is
different about Agama.

The setup of a phone or a preinstalled computer is a first boot, not an
installation: the system is already on the disk, and only a few personal
settings remain. A short sequence of screens fits that well.

Many Linux distributions ship one product with one set of choices, and their
installers can follow a single path designed for it. Agama installs several
products with different targets, each with its own defaults, through the same
interface. Its structure has to work for all of them, which is easier with areas
the user visits when needed than with a sequence that has to suit every product
at once.

## The road ahead

Agama is a living product, and it has reached a good level of maturity. It also
has a lot of room to improve, and the team is working on it. Going back to a
wizard is not part of that plan.

Changing how something familiar works takes some getting used to, and that
deserves respect. The aim is to reach a point where people barely have to think
about where to go next: the overview tells what is set, what is missing and
where to change it, for someone installing for the first time and for an
administrator installing for the hundredth.

If something got in your way, such as a setting that was hard to find, a default
that did not fit, or something the overview did not make clear, we want to hear
about it. That kind of feedback improves the interface for everyone, without
making everyone walk the same path.
