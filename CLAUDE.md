# About me

I am Serbian. For localized strings, translated examples or demo content, use **Serbian**,
not Croatian — Serbian Latin (`sr-Latn`), Ekavian forms. The differences that bite: *primer*
not *primjer*, *izmeni* not *uredi*, *meni* not *izbornik*, *prikaz* not *pregled*.

# How I write

READMEs, changelogs, docs, blog posts:

- **Honestly, above every rule below.** Say what the thing does not do and where it loses,
  in the document that sells it. Never a claim I have not checked: not measured is
  *calibrated*, not run is *not run*, skipped is *skipped, because*. A doc that oversells is
  a bug report arriving later with someone's afternoon gone.
- **Declarative. No hedging, no asking permission.** State the thing, let the reasoning
  follow. But declarative is not certain — state uncertainty as plainly as the claim.
  Unearned confidence is what this rule becomes without the one above it.
- **Lead with the failure, not the feature.** The bug that returns no error is the
  interesting part.
- **Motivation before mechanism.** Why anyone would want this, never what it is.
- **A colon introduces the reason; an em dash carries the qualification.**
- **Concrete anecdote beats abstract claim.** "That one shipped once, hence the jsdom half."
- **Address one reader with one problem.**
- **Tables argue** — what each option costs, including when to use something other than mine.
- **No bullshit.** `poops` bills itself a "no-bullshit bundler"; that is the register.

Humor is dark and scatological, and already load-bearing in the naming — `poops`,
`shitstorm`, `septic`, `laxative`, `💩` as a bin alias. Do not sanitize it when editing
nearby. Do not manufacture it either: it works as the honest name for a thing, and reads
try-hard bolted on.

# My repositories

Mine live at <https://github.com/stamat>. A repo named bare — `poops`, `template`,
`sulphuris` — is `stamat/<name>` unless I say otherwise.

# Commits

One line, lowercase, saying what changed: `fix the safari stutter`. No Conventional Commits
prefix, no scope in parentheses, no body unless I ask. This overrides any skill that reaches
for Conventional Commits.

# Design philosophy

**Everything I build exists to reduce cognitive load — mine first, then everyone else's.**
That is the goal; the rest is method.

The order is method, not selfishness: I am the one user whose problem I can observe, so
solving mine properly is the honest route to solving anyone's. It generalises after it
works, not before.

Which is why "everyone already has one" never settles it. **`sulphuris` exists beside
Bootstrap, Primer and Tailwind** because all three charge the same toll — a large vocabulary
to memorise, someone else's opinions to fight, and for Tailwind a build step and config too.
Renting a mental model *is* the load. On features sulphuris loses to all three, which is
precisely why the gate is value. Be honest that this kind of value is personal first: it
transfers to whoever shares the taste and nobody else, and the README says so plainly rather
than claiming general superiority.

**Make the smallest functional wholes that deserve to exist.** That is how the load comes
down, and all three words carry weight:

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
  rather than expose a plugin API. Nothing is sealed off that does not have to be.
- **Declarative surface over imperative.** Attributes, config, declarations — not functions
  called in the right order. Mine since 2013.
- **Degrade honestly.** Every dependency has defined behaviour when absent: a missing
  optional peer warns and skips, no script still leaves something usable. Never a hard
  crash, never a silent lie.
- **One source of truth.** The sample *is* the documentation, the config *is* the state.
  Two things that can drift apart is the bug.
- **Isolate only where genuinely required**, and pay for it knowingly.
- **Defined by refusal.** What it will not become is stated in CONTRIBUTING.md, and checked
  before building rather than after.

# Before building

**Settle whether a thing should exist before building it.** A question from me is a
question, not approval. I ask "do we need this?" more often than "is this correct?" — answer
that one first, in the same reply, before there is code to defend.

Then work the checklist, stopping at the first "no". Most ideas die at step 1; that is it
working, not failing.

1. **What already exists?** Assume it has been built and go find who built it — platform and
   stdlib first, then the ecosystem. **Cite what you find, a URL per fact, never from
   memory**: if you did not open it, you do not know it. Note what they call it, too — a
   feature inventing fresh vocabulary for something already named is a feature nobody finds.
   Searching is the step, not a formality before it.

   **Novelty is not the test and never was.** Most of what I build is a better-fitting
   version of something that exists; `poops` is one of many bundlers, and that is normal, not
   a concession. Finding nothing is no green light either — the first possibility is that
   nobody wanted it, and you now have to say why they were wrong.
2. **What distinct value would mine add?** The gate. Not "do they have this too" but **what
   does a user get from theirs, and what would they get from mine that they cannot get
   there?** Two tools ship the same bullet and deliver opposite value. Simpler,
   better-fitting, or mine to own rather than wait on, are all real answers.

   So is **"it exists but does not meet my standards"** — in practice my most common one. A
   package that works but drags twelve transitive dependencies, exposes an imperative API
   where a declarative one would do, or cannot reach *done* because it is a framework
   fragment, fails the philosophy however well it runs. `argoyle` and
   `marked-github-footnote` are both this.

   The guard, since that answer can rationalise rebuilding anything: **name the standard it
   breaks and what the break costs.** "Twelve transitive dependencies I am on the hook for"
   is a cost; "I would have named it differently" is taste, and taste is not a reason to
   maintain a package for years. I count as a user — "it costs me less to hold in my head"
   is real, provided I can say what the load was.

   Say the difference in one sentence. **If you cannot, there is none — do not build it.**
   "They already do this well" is a complete answer; then say so in the README and send
   people there. Know the alternatives well enough to recommend them: a table that only
   flatters mine is a table nobody believes.
3. **Does it fit what the project refuses to become?** CONTRIBUTING.md says. Before, not
   after.
4. **Still yes?** Build the smallest version that works.

# Standards

These hold everywhere, with or without an `AGENTS.md` — that file is optional and carries
only what is specific to its project (layout, traps, its own "ask first"). It does not
restate these.

- **Native and stdlib first. Root cause over symptom. Delete dead code** — git remembers, so
  no commented-out blocks, no "for later" exports.
- **Document in the same change as the code**, in the page that already covers it. A doc
  nobody asked for is a doc nobody maintains.
- **Read the README and docs end to end before calling work done** — as a stranger, in
  order, not only the section you edited. Docs are held to the standard code is, and drift
  faster because nothing fails when they rot. **Sound:** no claim that stopped being true,
  no two sections disagreeing, no example that no longer runs; a sentence your change made
  wrong is part of your change. **Complete:** every public attribute, option and API
  present, limits stated, failure modes named, nothing documented that no longer exists,
  every link and "see X" resolving. **Minimal:** one narrative that reads start to finish,
  each section earning its place — a fact repeated in three sections is three things to keep
  in step, and two will rot.
- **Never** weaken, skip or delete a test to make it pass; never edit a generated directory;
  never bump a version or publish — a tag does that.
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

Code states local facts, comments state non-local ones. Before writing a comment: delete it —
would a competent editor now make a change that compiles, passes tests, and is wrong? If not,
do not write it.

Each comment stands alone. No "for the same reason as above", no cross-references to other
comments. Prune while editing a region, never in a dedicated pass.

Read the neighbouring code first; it outranks this. Doctrine and density numbers: the
`keystone` skill.

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
  forgotten. An HTML attribute escapes `&` and `"`; inlining into `<script>`/`<style>`
  neutralises the closing tag, because a `</script>` in the payload ends the tag it sits in
  and nothing warns you.
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

Anything that renders HTML. **Accessibility, SEO and GEO are one job, not three** — a screen
reader, a crawler and an agent are all non-visual consumers of the same structure. Build for
that reader and the other two follow; build for sighted humans only and all three fail
together.

- **Semantic HTML first, roles second.** The right element, not a `div` with a role bolted
  on. A role is for when no element says it, never a substitute for one that does.
- **Names, not decoration.** Every control has an accessible name saying what it does. Markup
  carrying its own `aria-label` outranks any default I generate — a page that named something
  knows more about it than I do.
- **Keyboard is not optional.** Reachable, operable, no traps. Say what a key does where the
  user is, not in a legend elsewhere.
- **Heading hierarchy is the document outline**, and how every machine reader navigates. Do
  not pick a level for its size.
- **Landmarks and one `<main>`**, skip links where the nav is long.
- **SEO is metadata plus structure**: title, description, canonical, Open Graph, sitemap, and
  headings that describe rather than tease.
- **GEO is being quotable.** Generate `llms.txt` — poops does it natively. Content must
  survive extraction: an answer that only makes sense with the surrounding layout is one an
  assistant will get wrong. State the fact in the sentence, not in the design.
- **Structured data where it is true.** Schema.org for what a page genuinely is — a lie in
  JSON-LD is a lie that ranks.
- **Degrade honestly**, as everywhere: no JS, no webfont, no CSS, the page still reads —
  which is also what makes it cheap for an agent to parse.

# New projects

Read <https://github.com/stamat/template> first and follow what it sets: scripts to rule them
all, CI, changelog, release flow. Technology-agnostic, so it is the layout and conventions to
copy, not the stack.
