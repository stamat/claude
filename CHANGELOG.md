# Changelog

All notable changes to this configuration are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and this repo
follows [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

**How to use it:** land changes under `## [Unreleased]`, grouped under _Added_, _Changed_,
_Deprecated_, _Removed_, _Fixed_ or _Security_. Releasing renames that heading to the
version and date and starts a fresh `[Unreleased]`. Write entries for the person pulling
this into their own `~/.claude` — a rule that changed how an agent behaves matters more here
than a rule that was reworded, so say which one it was.

Because a rule only takes effect when it is read, **a change to `CLAUDE.md` is a behaviour
change**, not a documentation change. Treat it as one.

## [Unreleased]

### Changed

- **The README names what the config expects but does not carry** — the caveman and
  ponytail plugins, their hook scripts and `peon-ping` under `~/.claude/hooks/`, and a
  pinned Homebrew node path. A fresh machine fails those hooks loudly until they exist;
  the caveat now says so and says what to delete instead.

## [1.4.0] — 2026-08-04

### Added

- **Reporting back** — the message closing a turn is a receipt, not a report: what changed,
  why, and what was decided against, length tracking the size of the change. No process
  narration, no summary headings, honesty rule throughout; anything needing a call is one
  question at the end.

### Changed

- **Voice, the before-building checklist and the frontend rules moved out of `CLAUDE.md`
  into skills** — [skills/how-i-write](skills/how-i-write),
  [skills/before-building](skills/before-building), [skills/frontend](skills/frontend).
  A behaviour change in both directions: every session drops ~1.1k tokens of always-on
  context, and those three sections now apply only when the skill triggers — a session
  Claude does not read as docs-writing or frontend work runs without them. `CLAUDE.md`
  keeps a one-line kernel of each with a pointer. Codex loads no skills; it gets the
  kernels and a path it must open itself.
- **The tables rule now covers replies, not only docs** — every comparison is a table: a
  row per option with its pro, its con, its cost; against competitors a row per feature,
  losing rows included. Stated in the `CLAUDE.md` kernel so it acts every session, in full
  in `skills/how-i-write`.

## [1.3.0] — 2026-08-03

### Added

- **Codex reads the same doctrine.** `script/bootstrap` now also links `CLAUDE.md` into
  `~/.codex/AGENTS.md` (respecting `CODEX_HOME`) when that directory exists — Codex's
  documented global-instructions path. One file, two agents, no second copy to rot; a
  machine without Codex skips the link silently, by design. Unverified by a live Codex
  yet — none is installed here; `codex --print-instructions` is the check when one is.

### Changed

- **The keystone pointer became a path.** "The `keystone` skill" resolves only inside
  Claude's skill system; `skills/keystone` in the repo resolves for any reader, Codex
  included.

- **The README opens with Eliot, sourced.** The epigraph for the theft doctrine — the
  real 1920 sentence from "Philip Massinger", cited, not the Picasso version Jobs
  popularised. "Good poets make it into something better, or at least something
  different" is the step-2 gate said eighty years earlier.

## [1.2.0] — 2026-08-03

### Added

- **Sessions pull the config themselves.** A `SessionStart` hook runs `script/sync`:
  fetch, fast-forward, one loud line on divergence, silence offline — a pull landing
  mid-session takes effect the next one. Stolen from
  [elizabethfuentes12/claude-code-dotfiles](https://github.com/elizabethfuentes12/claude-code-dotfiles),
  which wraps the `claude` command in a shell function; a hook needs no shell setup and
  rides the settings file already here. The half not stolen: auto-committing on exit,
  because a timestamped "chore: sync" commit is exactly what the commit convention here
  forbids.
- **CI.** Ubuntu runs shell syntax checks and `script/tokens` on every push. The drift
  check existed since 1.1.0 with nothing running it, and it shipped its first bug the day
  it was written — also, Ubuntu is the OS I do not use, which is the point.
- **CONTRIBUTING.md.** What this will not become — agent zoo, provider templates,
  auto-committing sync, a framework — checked before building, with the field cited. And
  the threat model in writing: push access to this repo is arbitrary execution on every
  bootstrapped machine at session start, by design; held down by single-owner push and
  2FA, not by review.

## [1.1.0] — 2026-08-03

### Added

- **`script/tokens`** — warns when the README's token claim drifts more than 10% from
  `CLAUDE.md`. Byte-based estimate calibrated once against a real tokenizer count, not
  measured per run; a warning means re-count and update the claim, never that the number
  is exact.

### Changed

- **`CLAUDE.md` cut from ~3.5k to ~3.3k tokens without losing a rule.** Checked against
  the published field — Anthropic's best-practices page, HumanLayer's instruction-budget
  numbers, the AGENTS.md spec — then compressed the restatements: every rule and its
  anecdote stayed, the second whys went. The one behaviour change: the language section is
  now a single preference line — Serbian Latin over Croatian, Ekavian forms, with the
  vocabulary pairs that bite — instead of a paragraph about demo-content defaults.
- **The README now states the cost:** ~3.3k tokens of context in every session, next to
  what the file buys.

### Fixed

- **Two rules said the wrong thing.** "Before writing a comment: delete it" told an agent
  to delete a comment that does not exist yet — now "imagine it deleted". "An HTML
  attribute escapes `&` and `"`" made the attribute the actor — now the interpolation does
  the escaping. Also restored: the sulphuris counter-clause ("a vocabulary I named myself
  is not"), the iframe-versus-shadow-root isolation example, and never-weaken-tests now
  lives once, in Tests, instead of twice.

## [1.0.0] — 2026-08-03

The configuration as it stands after being written, argued with, and cut back down.

### Added

- **`CLAUDE.md`, loaded in every session and every repo.** Thirteen sections: who I am and
  how I write, commit and code style, tests, defensive engineering, frontend, how I build,
  the design philosophy, the checklist that runs before anything gets built, and the
  standards that hold everywhere.

  The root of it is one sentence — **everything I build exists to reduce cognitive load,
  mine first, then everyone else's** — and the method under it is to make the smallest
  functional wholes that deserve to exist. `sulphuris` next to Bootstrap, Primer and
  Tailwind is the worked example: on a feature comparison it loses to all three, which is
  exactly why the gate is value rather than features.

- **`skills/keystone`** — the comment doctrine. Code states local facts, comments state
  non-local ones, and the test is not "is this helpful" but: delete it, would a competent
  editor now make a change that compiles, passes tests, and is wrong? Judge a comment by
  what breaks in its absence.

  The part that is new is what changes when the reader is an agent. An agent reads a window,
  not a file, so a comment saying "for the same reason as above" is resolvable by a human
  who scrolls and a coin flip for anything reading one function alone. Duplicate the fact,
  never the essay. And rot is asymmetric now: a human seeing prose contradict code trusts
  the code, an agent may trust the prose and edit the code to match.

- **`skills/changelog-entry`** — drafts a `[Unreleased]` entry from the diff, reading the
  repo's own CHANGELOG header first, because each one states its own rules.

- **`skills/release`** — the preflight `script/publish` does not do: clean tree, tests green,
  `[Unreleased]` non-empty, sane version. Then hands off, because that script is interactive.

- **`script/bootstrap`** — symlinks the repo into `~/.claude`, backing up anything already
  there. Symlinks rather than copies, so an edit on any machine is already a tracked change
  and a `git pull` is the whole sync.

- **`settings.json`** — permissions, hooks, statusline and enabled plugins, pruned from 71
  allow-entries to 19. The 52 removed were one-offs pinned to exact versions, filenames and
  paths that will never match again.

### Known limits

- `settings.json` carries absolute paths under `/Users/stamat` in its hook commands. Fine
  across my machines, needs editing on anyone else's.
- Five permission entries auto-approve arbitrary execution without a prompt — `node -e`,
  `python3 -c`, `docker exec`, `npm install`, `git checkout`. Deliberate, and worth a
  deliberate decision before copying.
- `keystone`'s density numbers are calibrated against real repositories, not measured against
  outcomes. Treat a file outside the range as worth a look, never as a violation to correct
  mechanically.
