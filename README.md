# 🤖 claude

My [Claude Code](https://claude.com/claude-code) configuration — the instructions,
standards and skills I want in every session, on every machine.

One `script/bootstrap` symlinks it into `~/.claude`. An edit on any machine is a tracked
change here; a `git pull` on the others is the whole sync.

It is public because a config worth copying is one that actually commits to something. Take
the parts that survive the trip and delete the rest — the language rules and the commit
convention are mine, the doctrine is not.

## Install

```sh
git clone https://github.com/stamat/claude.git
cd claude
script/bootstrap
```

Existing files are moved to `~/.claude/backups/bootstrap-<timestamp>/` before anything is
linked. Re-running after a pull is a no-op.

## What is in it

| | |
| --- | --- |
| [CLAUDE.md](CLAUDE.md) | Loaded every session, every repo. Voice, commits, tests, how I build, design philosophy, standards. |
| [skills/keystone](skills/keystone) | Comment doctrine — what earns a comment when the reader is an agent. |
| [skills/changelog-entry](skills/changelog-entry) | Drafts a Keep a Changelog `[Unreleased]` entry from the diff. |
| [skills/release](skills/release) | Preflight, then hands off to `script/publish`. |
| [settings.json](settings.json) | Permissions, hooks, statusline, enabled plugins. |

Project-level agent notes are a separate layer and live in each repo, generated from
[stamat/template](https://github.com/stamat/template)'s `AGENTS.md`. `CLAUDE.md` holds what
is true everywhere; `AGENTS.md` holds what is true in one project — its layout, its traps,
its own "ask first". Neither restates the other.

## The parts worth stealing

**The comment doctrine.** Code states local facts, comments state non-local ones. The test
is not "is this helpful" — it is: delete the comment, does a competent editor now make a
change that compiles, passes tests, and is wrong? If not, delete it for real. Judge a
comment by what breaks in its absence.

Then the part that is new: an agent reads a *window*, not a file. So a comment saying "for
the same reason as above" is resolvable by a human who scrolls and a coin flip for anything
reading one function in isolation. Duplicate the fact, never the essay. And rot is
asymmetric now — a human seeing prose contradict code trusts the code; an agent may trust
the prose and edit the code to match.

**Stable leaves, volatile trunk.** Low-level packages in domains that do not move take zero
dependencies and reach *done*. The integrators above them carry the churn. This is the
answer to the usual objection to many small packages: that failure mode came from
transitive dependency trees, not from package count.

**Settle whether a thing should exist before building it.** A question is a question, not
approval. Most agent configs say what to build; almost none say when to stop and ask.

## Caveats

`settings.json` carries absolute paths under `/Users/stamat` in its hook commands. Fine
across my machines, needs editing on yours.

The density numbers in `keystone` are calibrated against real repos, not measured against
outcomes. Treat a file outside the range as worth a look, never as a violation to correct
mechanically.

## Changelog

[CHANGELOG.md](CHANGELOG.md). A change to `CLAUDE.md` is a behaviour change, not a
documentation change — a rule only takes effect when it is read.

## License

[MIT](LICENSE)
