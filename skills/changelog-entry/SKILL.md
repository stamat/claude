---
name: changelog-entry
description: Draft a CHANGELOG.md [Unreleased] entry from the current diff, in the repo's own house voice. Use when the user says "changelog", "add a changelog entry", "write the changelog", "/changelog-entry", or after landing a user-visible change in a repo that keeps a CHANGELOG.md.
user_invocable: true
---

# changelog-entry

Draft the `## [Unreleased]` entry for what just changed. Keep a Changelog format, written
for the person upgrading.

## Read the CHANGELOG's own rules first

**Always.** Every repo of mine states its conventions in its own CHANGELOG.md header, above
the first `##`, and they differ per project. That header outranks everything below.

Two real examples of what lives up there:

- **poops** — the `[Unreleased]` heading takes a short title after an em dash, and the
  entry opens with one paragraph saying what was wrong before. Those two become the title
  and description of a generated changelog post, so they are not decoration. Write plain
  Markdown; template tags get fenced automatically.
- **code-preview-element** — call out anything that changes the **DOM the element
  produces**, the **CSS an author may already be targeting**, or the **contents of the
  preview iframe**. None of the three shows up in a function signature, so none of them is
  visible in the diff to a reader.

If the header asks for something not listed here, do that instead.

## Steps

1. `git diff` (or `git diff --staged`, or against the merge base) to see what landed.
2. Read `CHANGELOG.md`'s header block for the house rules.
3. Read the last two or three released entries for bolding and grouping. Match their
   shape, not their length — an existing entry that runs long is not a licence to.
4. Write the entry under `## [Unreleased]`, in the right group.

## Groups

`### Added`, `### Changed`, `### Deprecated`, `### Removed`, `### Fixed`, `### Security`.
Only the ones you need, in that order. Create `## [Unreleased]` if it is missing.

## Voice

Bare. One sentence saying what changed, one saying why. Two sentences is the ceiling, not
the target — most bullets are one.

- **Write for the person upgrading, not the person who wrote the code.** "Describe what
  changed for someone using this, not which functions moved."
- Lead each bullet with a bold sentence stating the change. Add the *why* only when the
  diff cannot show it — a fix, a rework, a reversed default.
- No commit hashes, no file paths, no function names unless they are public API.
- No AI attribution.

Shape of a bullet that works:

```markdown
- **The console strip moved from under the preview to under the code block.** The lines are
  logged by the js in the pane, so they belong against the pane.
```

### Cut before writing

An entry is not a design note, a test report or a post-mortem. None of these belong in it:

- **How it was verified.** Browsers driven, scenarios run, numbers measured — that is the PR.
- **Alternatives rejected**, and why the shape is what it is — that is the commit body.
- **Internals a reader cannot touch** — a listener removed, a helper inlined, a selector
  constant. Only what they can call, write in markup, style or catch.
- **The second telling.** One narrative per bullet; a rename table replaces its prose, not
  joins it.

Long is the failure, not the effort. If a bullet needs three paragraphs to land, the thing
it describes needs a docs page — link that instead.

## Breaking changes

Say so in the bullet, in the words someone hits it with — the error they will see, the
attribute that stopped working, the migration. A `[Unreleased]` entry becomes the GitHub
release body verbatim via `script/publish`, so this is the only place the migration gets
written.

## Boundaries

Writes the entry. Does not bump the version, does not cut the release, does not commit —
`script/publish` does all three, and it reads what this wrote. See the `release` skill.
