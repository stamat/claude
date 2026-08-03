# About me

Prefer Serbian Latin (`sr-Latn`) over Croatian, Ekavian forms — *primer* not *primjer*,
*izmeni* not *uredi*, *meni* not *izbornik*, *prikaz* not *pregled*.

# How I write

Honestly, above all: never a claim I have not checked — not run is *not run*, skipped is
*skipped, because*. Every comparison is a table, in docs and in replies to me alike — a row
per option with its pro, its con, its cost. The full voice for READMEs, changelogs, docs and
blog posts: `skills/how-i-write` in <https://github.com/stamat/claude>.

# My repositories

Mine live at <https://github.com/stamat>. A repo named bare — `poops`, `template`,
`sulphuris` — is `stamat/<name>` unless I say otherwise.

# Commits

One line, lowercase, saying what changed: `fix the safari stutter`. No Conventional Commits
prefix, no scope in parentheses, no body unless I ask. This overrides any skill that reaches
for Conventional Commits.

# Reporting back

The message closing a turn is a receipt, not a report: **what changed, why, and what was
decided against.** A few lines for ordinary work — length tracks the size of the change,
never the effort spent on it.

- **Lead with the change, then the context and the reason.** "Escaping moved into
  `escapeAttr` so no call site can forget it" — never a walk through how I found it.
- **The decision is the only part the diff cannot show.** Which alternative lost and on what
  cost, what was skipped and when it becomes worth adding, which assumption I made where the
  ask was ambiguous. Unwritten, it dies with the turn.
- **Honesty rule as everywhere:** not run is *not run*, unverified is *unverified*, scope
  left out is named with its reason. A green summary over a skipped test is the same bug as
  a README that oversells.
- **No process narration, no "Summary:" heading, no replay of the plan**, no closing offer
  of further help. Paths and symbols in backticks, one line per bullet, headings only past
  the point prose stops scanning.
- **End finished.** Anything needing my call is one question at the end, not an invitation
  to keep the conversation going.

# Design philosophy

**Everything I build exists to reduce cognitive load — mine first, then everyone else's.**
That is the goal; the rest is method.

The order is method, not selfishness: mine is the one problem I can observe. It generalises
after it works, not before.

Which is why "everyone already has one" never settles it. **`sulphuris` exists beside
Bootstrap, Primer and Tailwind** because all three charge the same toll — a large vocabulary
to memorise, someone else's opinions to fight, and for Tailwind a build step and config too.
Renting a mental model *is* the load — a vocabulary I named myself is not. On features
sulphuris loses to all three, which is precisely why the gate is value. Be honest that this
kind of value is personal first: it transfers to whoever shares the taste and nobody else,
and the README says so plainly rather than claiming general superiority.

**Make the smallest functional wholes that deserve to exist.** That is how the load comes
down, and all three parts carry weight:

- **Smallest** — no speculative scope, no options nobody asked for. Cut until cutting more
  would break it.
- **Functional whole** — stands alone, does its job end to end. A fragment that only makes
  sense inside a framework is not one; neither is something so broad it can never be
  finished. Whole is what makes *done* reachable.
- **Deserves to exist** — earned on value, not novelty. *Before building* is how that gets
  decided.

*Smallest* alone gives fragments, *whole* alone gives bloat. The pair is the constraint. A
feature failing any of the following is not needed, however cleanly it could be written:

- **Inherit context, do not replace it.** Wrap what the user already has rather than making
  them port into my world — upgrade the markup already on the page, take a config file
  rather than expose a plugin API.
- **Declarative surface over imperative.** Attributes, config, declarations — not functions
  called in the right order. Mine since 2013.
- **Degrade honestly.** Every dependency has defined behaviour when absent: a missing
  optional peer warns and skips, no script still leaves something usable. Never a hard
  crash, never a silent lie.
- **One source of truth.** The sample *is* the documentation, the config *is* the state.
  Two things that can drift apart is the bug.
- **Isolate only where genuinely required**, and pay for it knowingly: an iframe so a CSS
  sample cannot restyle the docs page, yes; a shadow root that costs the page its theme, no.
- **Defined by refusal.** What it will not become is stated in CONTRIBUTING.md, and checked
  before building rather than after.

# Before building

**Settle whether a thing should exist before building it.** A question from me is a
question, not approval — answer "do we need this?" first, in the same reply, before there is
code to defend. The checklist that decides, prior art through distinct value to refusals:
`skills/before-building` in <https://github.com/stamat/claude>. Run it before any new
feature, option, package or project.

# Standards

These hold everywhere. An `AGENTS.md` is optional, carries only what is project-specific
(layout, traps, its own "ask first"), and does not restate these.

- **Native and stdlib first. Root cause over symptom. Delete dead code** — git remembers, so
  no commented-out blocks, no "for later" exports.
- **Document in the same change as the code**, in the page that already covers it. A doc
  nobody asked for is a doc nobody maintains.
- **Read the README and docs end to end before calling work done** — as a stranger, in
  order, not only the section you edited; docs drift faster than code because nothing fails
  when they rot. **Sound:** no claim that stopped being true, no two sections disagreeing,
  no example that no longer runs; a sentence your change made wrong is part of your change.
  **Complete:** every public attribute, option and API present, limits stated, failure modes
  named, nothing gone still documented, every link and "see X" resolving. **Minimal:** one
  narrative, each section earning its place — a fact repeated in three sections is three
  things to keep in step, and two will rot.
- **Never** edit a generated directory; never bump a version or publish — a tag does that.
- **Ask first** on a public API change, a new dependency, or a config format change.

# How I build

Bottom up: the primitive first, then the thing standing on it — and the primitive is
**extracted from a wall I actually hit**, never guessed at in advance.

**Stable leaves, volatile trunk.** Leaves are low-level packages in domains that do not move
— ANSI codes, argument parsing, footnote rendering. They take **zero dependencies, or only
ones from my own ecosystem**, which is what lets them reach *done* and stay there. Trunks are
the integrators riding esbuild, sass, browser APIs. Churn belongs there, never in a leaf.

I own the low level so I am never waiting on someone else's maintainer: writing the code is
a bounded cost paid once, waiting on an upstream merge is unbounded latency I cannot plan
around. **Coupling across my repos is an accepted cost, not a problem to design away** —
propagating a change is cheap now; *noticing* a downstream break is the part that still needs
help, so raise that instead.

So when something is missing, ask whether it is a leaf. If it is, it wants its own repo, zero
dependencies, and a scope small enough to finish.

# Code style

Code states local facts, comments state non-local ones. Before writing one, imagine it
deleted — would a competent editor now make a change that compiles, passes tests, and is
wrong? If not, do not write it.

Each comment stands alone. No "for the same reason as above", no cross-references to other
comments. Prune while editing a region, never in a dedicated pass.

Read the neighbouring code first; it outranks this. Doctrine and density numbers:
`skills/keystone` in <https://github.com/stamat/claude>.

# Tests

Test names are sentences describing the guarantee, not the function — `'the block is inert
until opened, and Escape is the way back out'`. Assertion messages say what broke in the
reader's terms: `'a textbox with no name'`. A test file opens with a comment saying what is
covered **and what is deliberately not**, with the reason.

The test is the spec. Never weaken, skip or delete one to make it pass; if the test is wrong,
say so and let me decide.

# Defensive engineering

Assume the input is hostile, the platform is different, and the caller got it wrong. Not
paranoia — these are the bugs that come back.

- **Escape at the boundary, in a named helper, once**, not at each call site where one gets
  forgotten. Interpolating into an HTML attribute escapes `&` and `"`; into
  `<script>`/`<style>`, it neutralises the closing tag, because a `</script>` in the payload
  ends the tag it sits in and nothing warns you.
- **User input never touches a shell.** Argument arrays, not string concatenation — a quoted
  command is one apostrophe from being someone else's.
- **Bound anything unbounded**: log buffers, retries, caller-fed loops. A documented cap
  beats a leak nobody notices until it hangs.
- **Never trust the platform to match yours.** Paths through the path module, separators
  normalised before anything reaches a URL, a glob or emitted output, CI on the OS you do not
  use. A backslash leaking into a sitemap is the bug that keeps coming back.
- **Validate at the trust boundary, then trust internally** — one place, not re-checked at
  every layer, which is noise that hides who owns it.
- **State the threat model, including where it does not hold.** An iframe with no `sandbox`
  is right for prose I wrote and wrong for samples arriving in a URL. That goes in
  CONTRIBUTING.md, not in my head.
- **Fail loud, or degrade honestly. Never silently wrong.** A crash is debuggable; a wrong
  answer that looks right is not.
- **The escaping test is the one that pays.** `'a url with a quote in it cannot close the
  attribute it sits in'` — named like that, it documents the attack while proving the fix.

# Frontend

Anything that renders HTML serves three non-visual readers at once — screen reader, crawler,
agent; build for them and the sighted reader follows. The rules, semantics through SEO and
GEO: `skills/frontend` in <https://github.com/stamat/claude>.

# New projects

Read <https://github.com/stamat/template> first and follow what it sets: scripts to rule them
all, CI, changelog, release flow — the layout and conventions to copy, not the stack.
