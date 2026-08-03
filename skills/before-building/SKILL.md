---
name: before-building
description: Checklist that settles whether a thing should exist before any code — prior art search with a URL per fact, the distinct-value gate, the project's stated refusals. Use when the user proposes a new feature, option, package or project, asks "do we need this" or "should we build X", or a task implies creating something that does not exist yet.
user_invocable: true
---

# Before building

**Settle whether a thing should exist before building it.** A question from me is a
question, not approval. I ask "do we need this?" more often than "is this correct?" — answer
that one first, in the same reply, before there is code to defend.

Then work the checklist, stopping at the first "no". Most ideas die at step 1; that is the
checklist working, not failing.

1. **What already exists?** Assume it has been built and go find who built it — platform and
   stdlib first, then the ecosystem. **Cite what you find, a URL per fact, never from
   memory**: if you did not open it, you do not know it. Note what they call it, too — a
   feature inventing fresh vocabulary for something already named is a feature nobody finds.
   Searching is the step, not a formality before it.

   **Novelty is not the test.** Most of what I build is a better-fitting version of
   something that exists; `poops` is one of many bundlers. Finding nothing is no green
   light — the first possibility is nobody wanted it, and you must say why they were wrong.
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
