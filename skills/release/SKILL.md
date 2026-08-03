---
name: release
description: Preflight and run a release via script/publish — clean tree, tests green, changelog entry present, then hand off to the interactive script. Use when the user says "release", "publish", "cut a release", "ship it", "bump the version", or "/release".
user_invocable: true
---

# release

`script/publish` does the release. This skill runs the checks that script does *not* do,
then hands over.

## Preflight — run all of these before touching script/publish

1. **Working tree clean.** `git status --porcelain`. The script warns and offers to
   continue, but a dirty tree means uncommitted work gets swept into the release commits by
   the `git add .` after the build. Stop and ask.
2. **On the default branch, and pushed up to date.** `git status -sb`.
3. **Tests and lint green.** `script/test` and `script/lint` if present, otherwise
   `npm test`. Do not skip this — `script/publish` tags and pushes without running either.
4. **`## [Unreleased]` has content.** If `CHANGELOG.md` exists and that section is empty,
   stop: the release will ship with empty notes. Offer the `changelog-entry` skill.
5. **The version argument makes sense.** Semver, and not the version already in
   `package.json`. Breaking changes in the changelog mean a major.

Report anything that fails and stop. Do not "fix" a failing test to unblock a release.

## Then hand off

```bash
script/publish <version>
```

**It is interactive** — readline prompts for the version, and for whether to create the
GitHub release. Never run it in the background, never pipe it, never try to answer its
prompts for the user. Tell them to run it, or run it in the foreground and let them type.

If they want it non-interactive, pass the version as the argument — that skips the version
prompt, but the GitHub release prompt remains.

## What it does, so you can tell them what to expect

1. Writes the version into `package.json`.
2. Runs `script/changelog <version>` if present — cuts `## [Unreleased]` into a dated
   release entry, starts a fresh one, writes the changelog post, and leaves the cut entry
   in the temp dir as the release notes.
3. Commits `Bump version to <version>`.
4. Runs `script/build` if present, commits `Build version <version>`.
5. Tags `v<version>`, pushes commits and tags.
6. Offers to `gh release create` with the cut changelog entry as `--notes-file`.

**npm publish happens in CI** (`publish.yml`, trusted publishing) when the tag lands. It is
not part of this script. If the package did not appear on npm, that is a CI problem, not a
publish-script problem — check the workflow run.

## Notes

- `Bump version to X` and `Build version X` are the script's own commit messages. They are
  generated, and are the one place the no-prefix one-liner rule does not apply — leave them.
- The release notes file is `$TMPDIR/<repo>-release-notes-v<version>.md`. A failing `gh`
  leaves it there on purpose, for a manual `gh release create --notes-file` retry.
- `script/changelog`, `script/publish` and `script/lint` are identical across my repos —
  they come from `stamat/template`. A fix to one belongs upstream in the template, not
  copy-pasted around.

## Boundaries

Preflight and hand-off. Does not write the changelog entry (see `changelog-entry`), does
not decide the version number — propose one from the changelog and let the user confirm.
