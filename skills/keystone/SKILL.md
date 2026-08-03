---
name: keystone
description: Comment doctrine for codebases read by agents. Comments state non-local facts only — ordering, silent failure modes, rejected alternatives, invariants, boundaries. Everything else is deleted. Use when writing or reviewing comments, when a file feels over- or under-commented, or when the user says "keystone", "comment doctrine", "should this be a comment".
user_invocable: true
---

# Keystone

You delete comments ruthlessly and defend a handful absolutely. Most comments in most
codebases are net negative the day they are written. A few prevent entire classes of bug
and must survive every cleanup. Knowing which is which is the whole skill.

## Persistence

ACTIVE EVERY RESPONSE. Applies to comments you write and comments you review. Off only:
"stop keystone" / "normal mode". Default level: **full**.

## The axis

**Code states local facts. Comments state non-local facts.**

A local fact is one visible in the code you are looking at. Anything local, written in a
comment, is duplication — value zero, rot cost above zero, therefore net negative on the
day it is written, not the day it goes stale.

## The test

Never ask "is this comment helpful?" — everyone answers yes and nothing is falsifiable.
Ask:

> **Delete it. Does a competent editor now make a change that compiles, passes tests, and
> is wrong?**

- **No** → delete it for real.
- **Yes** → it is load-bearing. Mark it, keep it, never let a cleanup take it.

Judge a comment by what breaks in its absence, not by what it adds.

## What survives

Five categories, all non-local:

| Category | Why code cannot say it |
|---|---|
| **Ordering / timing** | The constraint lives across two files, or between a load and a callback |
| **Silent failure modes** | Visible only at runtime, to a user who will not report it |
| **Rejected alternatives** | The Chesterton's fence, made explicit, before someone removes it |
| **Invariants callers rely on** | Visible only at call sites you cannot see from here |
| **Boundaries** | What this deliberately does not do, and who owns the rest |

The sharpest heuristic: **the comment worth writing is usually the one you would otherwise
put in the PR description.** That is where "why" traditionally goes, and it is exactly
where nothing reads it at edit time. Moving it into the code is the point.

## What dies

- Restating the signature, the type, or the line below it
- Narrating control flow — `// loop over users`, `// increment i`
- Section banners, decorative rules, ASCII dividers
- `TODO` with no named condition that would resolve it
- Commented-out code — git remembers
- Changelog entries in source — git remembers that too
- Anything that would be obvious from a better name

## Writing for a windowed reader

An agent reads a window, not a file. Three consequences:

**Self-containment beats brevity.** "For the same reason as above" is resolvable by a human
who scrolls and a coin flip for anything reading one function in isolation.

**Duplicate the fact, never the essay.** Two sites carrying the same constraint each get
one sentence. One paragraph plus a cross-reference is worse than two short claims.
Repetition of a short fact is fine. Pointers are the anti-pattern.

**Rot is asymmetric now.** A human seeing prose contradict code trusts the code. An agent
may trust the prose and edit the code to match. A stale comment is no longer merely
useless — it is a live hazard, and it is the strongest argument for writing fewer.

## Density

Comments are read tokens. Every visit, every session, no skipping — agents do not skim past
the paragraph they do not need.

Measure it: comment lines over code lines, per file.

- **Under 0.1** — likely under-commented. Check whether the non-local facts are written
  anywhere at all.
- **0.2 to 0.6** — the working range for most code.
- **Above 1.0** — the file costs more to read than its own logic. Audit it; expect
  narration and cross-references.

These are guidance calibrated against real repos, not measured against outcomes. Treat a
file outside the range as worth a look, never as a violation to mechanically correct.

Prune while editing a region. Never open a dedicated comment-cleanup PR: large diff, no
functional change, and it is exactly the diff where load-bearing comments get lost.

## Rules

- Explain why. The code says what.
- One reason per comment, at the site it constrains.
- Present tense for what the code does, past for what went wrong before.
- Name things in backticks so a search finds them.
- Full sentences. A comment worth keeping is worth punctuating.
- No comment to defend code that should be rewritten instead. Fix the code.

## Intensity

| Level | What changes |
|---|---|
| **lite** | Apply the test to new comments only. Leave existing ones alone. |
| **full** | The test on everything you touch. Prune while editing. Default. |
| **ultra** | Every comment in a touched file justifies itself or goes. Report the ratio before and after. |

## When NOT to delete

Never strip: a licence or attribution header, a comment carrying a spec or RFC reference, a
security rationale, a workaround naming the upstream bug it routes around, or a comment
whose deletion you cannot test because you do not understand the code yet.

**Read before pruning.** A comment you do not understand is more likely load-bearing than
noise — that is what non-local means.

## Boundaries

Governs comments, not naming, structure, or whether the code is any good. Pairs with a
laziness skill for the code itself. The project's existing convention outranks this: a
codebase with a real documentation standard gets matched, not converted.

The comment that survives deletion is the only one worth writing.
