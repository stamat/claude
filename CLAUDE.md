# About me

I am Serbian. For localized strings, translated examples, or demo content in my
language, use **Serbian** — not Croatian.

Serbian Latin (`sr-Latn`) for public-facing demo content. Ekavian forms, and the
vocabulary differences that matter in practice: *primer* not *primjer*, *izmeni* not
*uredi*, *meni* not *izbornik*, *prikaz* not *pregled*.

# How I write

Prose in my repos — READMEs, changelogs, docs, blog posts — sounds like this:

- **Honestly, before anything else. Every rule below yields to this one.** Say what the
  thing does not do, where it loses, and what is not covered — in the same document that
  sells it, not in a footnote. Never a claim I have not checked: if it was not measured,
  say calibrated rather than measured; if it was not run, say so; if part of the work was
  skipped, name it and why. A doc that oversells is a bug report arriving later with
  someone's afternoon already gone.
- **Declarative. No hedging, no asking permission.** State the thing, then let the reasoning
  follow. Not "you might want to consider" — say it. Declarative is not the same as
  certain, though: state the uncertainty as plainly as the claim. Confidence I have not
  earned is what this rule turns into when it is not held down by the one above it.
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
- **No bullshit.** `poops` bills itself as a "no-bullshit bundler"; that is the register for
  the work as much as the prose.

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

# Design philosophy

**Everything I build exists to reduce cognitive load — mine first, then everyone else's.**
That is the goal; the rest of this file is method.

The order is the method, not selfishness. I am the one user whose problem I can actually
observe, so solving mine properly is the only honest route to solving anyone's — and a
thing built for a hypothetical user usually serves neither. It generalises after it works,
not before.

This is also why "everyone already has one" never settles it. **`sulphuris` exists next to
Bootstrap, Primer and Tailwind** because all three charge the same toll: a large vocabulary
to memorise, someone else's opinions to fight, and for Tailwind a build step and a config on
top. Renting a mental model *is* the load. Zero dependencies and a vocabulary I named myself
is not. On a feature comparison sulphuris loses to all three — which is precisely why the
gate is value and not features.

Be honest that this kind of value is personal first: it transfers to whoever shares the
taste and to nobody else. That belongs in the README, stated plainly, rather than dressed up
as general superiority.

**Make the smallest functional wholes that deserve to exist.** That is how the load comes
down, and each of the three parts is load-bearing:

- **Smallest** — no speculative scope, no options nobody asked for. Cut until cutting more
  would break it.
- **Functional whole** — it stands on its own and does its job end to end. A fragment that
  only makes sense inside a framework is not one, and neither is a thing so broad it can
  never be finished. Whole is what makes *done* reachable.
- **Deserves to exist** — earned against what is already out there, on value not novelty.

*Smallest* alone produces fragments; *whole* alone produces bloat. The pair is the
constraint.

A feature fails here is not needed, however cleanly it could be written:

- **Inherit context, do not replace it.** Wrap what the user already has rather than asking
  them to port into my world — upgrade the `<pre><code>` the generator emitted, take a
  config file rather than expose a plugin API, live in the light DOM so the host page's
  theme and prose styles still reach in. Nothing gets sealed off that does not have to be.
- **Degrade honestly.** Every dependency has a defined behaviour when absent: no
  highlighter means monochrome, a missing optional peer warns and skips, no script at all
  means a plain code block. Never a hard crash, and never a silent lie.
- **One source of truth.** The sample *is* the documentation, the config *is* the state.
  If two things can drift apart, that is the bug.
- **Isolate only where isolation is genuinely required** — and pay for it knowingly. An
  iframe because a CSS sample would otherwise restyle the docs page, yes; a shadow root
  that costs the page's own theme, no.
- **Defined by refusal.** What it will not become is stated up front, in CONTRIBUTING.md,
  and checked before building rather than after.
- **Declarative surface over imperative.** Attributes, config, declarations — not functions
  to call in the right order. `poops.json` over a plugin API. Mine since 2013.

# Before building
- **Settle whether a thing should exist before building it.** A question from me is a
  question, not approval — do not start until the premise is agreed. I will ask "do we need
  this?" more often than "is this correct?", so answer that one first, in the same reply,
  before there is code to defend.

Stop at the first "no". Most ideas die at step 1; that is the checklist working, not
failing.

1. **What already exists? Find out before designing anything.** Assume it has been built
   and go looking for who built it — the platform or the stdlib first, since that is the
   cheapest way for a thing to already exist, then the ecosystem. **Cite what you find, a
   URL per fact, never from memory.** If you did not open it, you do not know it. Note what
   they call it too: a feature that invents fresh vocabulary for something already named is
   a feature nobody finds. Searching is the step, not a formality before the step.

   **Novelty is not the test and never was.** Most of what I build is a better-fitting
   version of something that exists — `poops` is one of many bundlers, and that is the
   normal case, not a concession. Finding nothing is not a green light either: if nobody
   has built it, the first possibility is that nobody wanted it, and you now have to say
   why they were wrong.
2. **What distinct value would mine add?** This is the gate. Judge on value, never on
   features — the question is not "do they have this too" but **what does a user actually
   get from theirs, and what would they get from mine that they cannot get there?** Two
   tools ship the same bullet and deliver opposite value. Simpler, better-fitting, or mine
   to own rather than wait on, are all real answers.

   **So is "it exists but does not meet my standards"** — in practice my most common one. A
   package that works but drags twelve transitive dependencies, or exposes an imperative
   API where a declarative one would do, or cannot reach *done* because it is a framework
   fragment, fails the design philosophy however well it runs. `argoyle` and
   `marked-github-footnote` are both this: crowded domains where the zero-dependency
   version was not there.

   The guard, because this answer can rationalize rebuilding anything: **name the standard
   it breaks and the cost that break puts on a user.** "Twelve transitive dependencies I
   would be on the hook for" is a cost. "I would have named it differently" is taste, and
   taste is not a reason to maintain a package for years.

   Say the difference in one sentence.
   **If you cannot, there is none — do not build it.** "They already do this well" is a
   complete and correct answer; the move is to say so in the README and send people there.
   Know the alternatives well enough to recommend them — a table that only flatters mine is
   a table nobody believes, and being trusted about where mine loses is what makes the rest
   of the page credible.
3. **Does it fit what the project refuses to become?** CONTRIBUTING.md says. Check before
   building, not after.
4. **Still yes?** Build the smallest version that works.

# Standards

These hold in every repo of mine, whether or not it has an `AGENTS.md` — that file is
optional, and where it exists it carries only what is specific to that project (its layout,
its traps, its own "ask first"). Do not restate the standing rules there; this file is where
they live.

- **Native and stdlib first. Root cause over symptom. Delete dead code** — git
  remembers, so no commented-out blocks and no "for later" exports.
- **Document in the same change as the code**, in the page that already covers it. A doc
  nobody asked for is a doc nobody maintains.
- **Never** weaken, skip or delete a test to make it pass; never edit a generated
  directory; never bump a version or publish — a tag does that.
- **Ask first** on a public API change, a new dependency, or a config format change.

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

# Defensive engineering

Assume the input is hostile, the platform is different, and the caller got it wrong. Not
paranoia — these are the bugs that come back.

- **Escape at the boundary, in a named helper, once.** Not at each call site where one will
  eventually be forgotten. Interpolating into an HTML attribute escapes `&` and `"`;
  inlining into `<script>`/`<style>` neutralises the closing tag, because a `</script>` in
  the payload ends the tag it sits in and nothing warns you.
- **User input never touches a shell.** Argument arrays, not string concatenation. A
  quoted-string command is one apostrophe away from being someone else's command.
- **Bound anything unbounded.** Log buffers, retries, loops fed by a caller. A cap with a
  documented number beats a leak nobody notices until it is a hang.
- **Never trust the platform to match yours.** Build paths with the path module, normalise
  separators before anything reaches a URL, a glob or emitted output, and let CI run on the
  OS you do not use. A backslash leaking into a sitemap is the bug that keeps coming back.
- **Validate at the trust boundary, then trust internally.** One place, not defensively
  re-checked at every layer — that is noise, and it hides which layer actually owns it.
- **State the threat model, including where it does not hold.** An iframe with no `sandbox`
  is right for prose I wrote and wrong for samples arriving in a URL. Write that down in
  CONTRIBUTING.md rather than leaving it as something I happen to know.
- **Fail loud, or degrade honestly. Never silently wrong.** A crash is debuggable; a wrong
  answer that looks right is not.
- **The escaping test is the one that pays.** `'a url with a quote in it cannot close the
  attribute it sits in'`, `'a closing tag inside a pane cannot end the tag it is inlined
  into'` — write them, name them like that, and they document the attack while proving the
  fix.

# Frontend

Anything that renders HTML. **Accessibility, SEO and GEO are one job, not three** — a
screen reader, a crawler and an agent are all non-visual consumers parsing the same
structure. Markup that a screen reader can navigate is markup an agent can consume. Build
for that reader and the other two follow; build for sighted humans only and all three fail
together.

- **Semantic HTML first, roles second.** The right element, not a `div` with a role bolted
  on. A role is what you reach for when no element says it — never a substitute for the one
  that does.
- **Names, not decoration.** Every control has an accessible name that says what it does.
  Markup that already carries its own `aria-label` outranks any default I generate — a page
  that named something knows more about it than I do.
- **Keyboard is not optional.** Reachable, operable, and no traps. State what a key does
  where the user is, not in a legend elsewhere.
- **Heading hierarchy is the document outline**, and it is the thing every machine reader
  uses to find its way. Do not pick a level for its size.
- **Landmarks and one `<main>`.** Skip links where the nav is long.
- **SEO is metadata plus structure**: title, description, canonical, Open Graph, a
  `sitemap.xml`, and headings that describe the content rather than tease it.
- **GEO is being quotable.** Generate `llms.txt` — poops does this natively, `llms.full`
  for a page whose prose is the answer. Content should survive extraction: an answer that
  only makes sense with the surrounding layout is an answer an assistant will get wrong.
  State the fact in the sentence, not in the design.
- **Structured data where it is true.** Schema.org for the things a page genuinely is. Not
  as a trick — a lie in JSON-LD is a lie that ranks.
- **Degrade honestly**, as everywhere: no JS, no webfont, no CSS, the page still reads —
  which is also what makes it cheap for an agent to parse.

# New projects

Starting a new project: read <https://github.com/stamat/template> first and follow
the practices it sets — scripts to rule them all, CI, changelog, release flow. It is
technology-agnostic, so it is the layout and the conventions to copy, not the stack.
