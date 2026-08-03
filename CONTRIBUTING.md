# Contributing

This is a personal configuration. It optimises for one observable user — me — and
generalises only where that happens to transfer. Issues and questions are welcome; a PR
that makes it bigger is probably answered by the list below. Take
[what is worth stealing](README.md#the-parts-worth-stealing) instead.

## What this will not become

Checked before building, not after — a feature failing this list is not needed, however
cleanly it could be written.

- **An agent zoo or skill marketplace.** The field has these at every scale —
  [135-agent toolkits](https://github.com/rohitg00/awesome-claude-code-toolkit),
  [100+-agent personal configs, since archived](https://github.com/zircote/.claude) — and
  [feiskyer's own caveats](https://github.com/feiskyer/claude-code-settings) name the
  cost: more skills, more token burn, worse trigger accuracy. A skill enters here when a
  wall was actually hit, never to fill a category.
- **Provider templates or multi-agent portability.** One agent is in use. The day a
  second one is, the agent-agnostic sections get an `AGENTS.md` mirror — a mirror, not a
  port, and not before.
- **Auto-committing sync.** `script/sync` pulls and stops. A timestamped "chore: sync"
  commit is exactly what the commit convention forbids; an edit becomes a commit when it
  can say what changed.
- **A framework.** Smallest functional whole: three skills, three scripts, a `CLAUDE.md`
  and a settings file. Cut until cutting more would break it.

## What a change needs

- `CLAUDE.md` is a behaviour file, not documentation — the changelog entry says which
  rule changed, written for the person pulling it.
- The README's token claim stays true; CI runs `script/tokens` and fails the push that
  breaks it.
- The standards in `CLAUDE.md` hold here too: ask first on a config format change, docs
  in the same change as the code.

## Threat model

The trust boundary is the GitHub repo. `script/sync` pulls it at session start and
`settings.json` executes what arrives — hooks, scripts — so push access to this repo is
arbitrary execution on every machine that bootstrapped it, by design and without a
prompt. Held down by single-owner push and 2FA, not by review. The permissions that
auto-approve execution are named in the [README's caveats](README.md#caveats); read them
before copying, they are deliberate.
