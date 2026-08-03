# About me

I am Serbian. For localized strings, translated examples, or demo content in my
language, use **Serbian** — not Croatian.

Serbian Latin (`sr-Latn`) for public-facing demo content. Ekavian forms, and the
vocabulary differences that matter in practice: *primer* not *primjer*, *izmeni* not
*uredi*, *meni* not *izbornik*, *prikaz* not *pregled*.

# How I write

Prose in my repos — READMEs, changelogs, docs, blog posts — sounds like this:

- **Declarative. No hedging, no asking permission.** State the thing, then let the reasoning
  follow. Not "you might want to consider" — say it.
- **Lead with the failure, not the feature.** The bug that returns no error is the
  interesting part. What goes wrong first, what fixes it second.
- **Motivation before mechanism.** Open with why anyone would want this. Never with what it
  is.
- **A colon introduces the reason; an em dash carries the qualification.** Not parentheses,
  not a second sentence.
- **Concrete anecdote beats abstract claim.** "That one shipped once, hence the jsdom half."
- **Address one reader with one problem**, directly.
- **Tables argue.** A comparison table says what each option costs, including when to use
  something other than mine.

Humor is dark and scatological, and it is load-bearing in the naming already — `poops`,
`shitstorm`, `septic`, `laxative`, `💩` as a bin alias, "Fucking awesome, right?" in
`script/publish`. Do not sanitize it when editing near it. Do not manufacture it either: it
lands when it is the honest name for the thing, and reads as try-hard when bolted on.

# My repositories

Mine live at <https://github.com/stamat>. When I mention a repo by bare name —
`poops`, `template`, `poops-images`, `shitstorm` — that is `stamat/<name>` unless I say
otherwise.

# Commits

One line. No Conventional Commits prefix — no `feat:`, `fix:`, `chore:`, no scope in
parentheses. Lowercase, and say what changed: `fix the safari stutter`, `add shields to
the demo page`. No body unless I ask for one.

This overrides any skill or default that reaches for Conventional Commits.

# Code style

Code states local facts, comments state non-local ones. Before writing a comment, ask
whether deleting it would let a competent editor make a change that compiles, passes tests,
and is wrong. If not, do not write it.

Each comment stands alone — no "for the same reason as above", no cross-references to other
comments. Prune while editing a region, never in a dedicated pass.

Read the neighbouring code first; it outranks this. The doctrine and the density numbers:
the `keystone` skill.

# Tests

Test names are sentences describing the guarantee, not the function under test — `'the
block is inert until opened, and Escape is the way back out'`. Assertion messages say what
broke in the reader's terms: `'a textbox with no name'`.

A test file opens with a comment saying what is covered **and what is deliberately not**,
with the reason.

The test is the spec. Never weaken, skip or delete one to make it pass; if the test itself
is wrong, say so and let me decide.

# How I build

Bottom up. The primitive first, then the thing standing on it — and the primitive gets
**extracted from a wall I actually hit**, never guessed at in advance.

**Stable leaves, volatile trunk.** Leaves are low-level packages in domains that do not
move — ANSI codes, CLI argument parsing, GFM footnote rendering. They take **zero
dependencies, or only ones from my own ecosystem**, which is what lets them reach *done*
and stay there. Trunks are the integrators — `poops`, `code-preview-element` — riding
esbuild, sass, codejar, browser APIs. Churn belongs there, not in a leaf.

I own the low level so I am never waiting on someone else's maintainer. Writing the code is
a bounded cost paid once; waiting on an upstream merge is unbounded latency I cannot plan
around.

**Coupling across my repos is an accepted cost, not a problem to design away.** Propagating
a change through the ecosystem is cheap now. The part that still needs help is *noticing* a
downstream break — so raise that, don't raise the coupling itself.

So: when something is missing, ask whether it is a leaf. If it is, it wants its own repo,
zero dependencies, and a scope small enough to finish.

# Design philosophy

Check a proposed feature against this before asking whether to build it. A thing that fails
here is not needed, however cleanly it could be written.

- **Inherit context, do not replace it.** Wrap what the user already has rather than asking
  them to port into my world — upgrade the `<pre><code>` the generator emitted, take a
  config file rather than expose a plugin API, live in the light DOM so the host page's
  theme and prose styles still reach in. Nothing gets sealed off that does not have to be.
- **Declarative surface.** Attributes, config, declarations — not functions to call in the
  right order.
- **Degrade honestly.** Every dependency has a defined behaviour when absent: no
  highlighter means monochrome, a missing optional peer warns and skips, no script at all
  means a plain code block. Never a hard crash, and never a silent lie.
- **One source of truth.** The sample *is* the documentation, the config *is* the state.
  If two things can drift apart, that is the bug.
- **Isolate only where isolation is genuinely required** — and pay for it knowingly. An
  iframe because a CSS sample would otherwise restyle the docs page, yes; a shadow root
  that costs the page's own theme, no.
- **Defined by refusal.** What it will not become is stated up front, in CONTRIBUTING.md,
  and it is checked before building rather than after.
- **Small enough to finish.** Scope to something that can reach *done*.

# Standards

These hold in every repo of mine, whether or not it has an `AGENTS.md` — that file is
optional, and where it exists it carries only what is specific to that project (its layout,
its traps, its own "ask first"). Do not restate the standing rules there; this file is where
they live.

- **Settle whether a thing should exist before building it.** A question from me is a
  question, not approval — do not start until the premise is agreed. I will ask "do we need
  this?" more often than "is this correct?", so answer that one first, in the same reply,
  before there is code to defend.
- **Focus before features.** Before writing any code: is it needed at all, checked against
  the design philosophy above? Does the platform or stdlib already do it? What is the prior
  art — cited, a URL per fact, never guessed? Does it fit what the project refuses to
  become? Only then, the smallest version that works. Stop at the first "no".
- **Declarative over imperative.** A behaviour expressible as config, an attribute or a
  declaration beats a function someone has to call. `poops.json` over a plugin API,
  attributes over JavaScript setup. This one is not in the template — it is mine, and it
  goes back to 2013.
- **YAGNI. Native and stdlib first. Root cause over symptom. Delete dead code** — git
  remembers, so no commented-out blocks and no "for later" exports.
- **Document in the same change as the code**, in the page that already covers it. A doc
  nobody asked for is a doc nobody maintains.
- **Never** weaken, skip or delete a test to make it pass; never edit a generated
  directory; never bump a version or publish — a tag does that.
- **Ask first** on a public API change, a new dependency, or a config format change.

No bullshit — `poops` bills itself as a "no-bullshit bundler", and that is the register for
the work as much as the prose.

# New projects

Starting a new project: read <https://github.com/stamat/template> first and follow
the practices it sets — scripts to rule them all, CI, changelog, release flow. It is
technology-agnostic, so it is the layout and the conventions to copy, not the stack.
