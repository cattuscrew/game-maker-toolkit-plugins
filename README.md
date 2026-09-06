# game-maker-toolkit-plugins

An agent-neutral marketplace of game-making skills for Claude Code and Codex. It
currently holds one plugin, with room for more over time.

## Plugins

### `game-design`

Four game-design **method** skills, each a reusable way of reasoning — not any one
game's numbers:

- `number-balancing` — choose, compare, or defend a number in a mechanic.
- `economy-design` — currencies, sources and sinks, and what a mechanic charges.
- `systems-design` — how a mechanic interacts with the others.
- `progression-design` — the difficulty and reward arc across a whole run.

They hand off to each other: a value goes to `number-balancing`, a resource flow to
`economy-design`, a self-compounding mechanic to `systems-design`, and the whole-run
arc to `progression-design`.

**Method only.** Each skill holds the reasoning and a `references/` file, plus
`evals/`. It carries **no** game-specific vocabulary, authored values, or paths — its
`## Project overlay` section tells you to read your own project's product direction
and authored sources before Step 0. Every project supplies its own numbers.

## Claude Code

```
/plugin marketplace add <owner>/game-maker-toolkit-plugins
/plugin install game-design@game-maker-toolkit-plugins
```

Skills then fire as `game-design:number-balancing`, `game-design:economy-design`,
and so on.

For local development without a marketplace:

```
claude --plugin-dir ./game-design
```

## Codex

The Codex marketplace catalog is `.agents/plugins/marketplace.json`, and the
Codex plugin manifest is `game-design/.codex-plugin/plugin.json`.

From this repository, register and install the local marketplace:

```
codex plugin marketplace add .
codex plugin add game-design@game-maker-toolkit-plugins
```

Start a new Codex thread after installation. You can explicitly request a skill
with `$game-design:number-balancing`, or let Codex select one from the request.

## Local development

```
claude plugin validate ./game-design        # check the Claude plugin
claude plugin validate .                   # check the Claude marketplace
codex plugin list --available --json        # inspect available Codex plugins
```
