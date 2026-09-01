# game-maker-toolkit-plugins

A Claude Code marketplace of game-making skills. It currently holds one plugin,
with room for more over time.

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

## Install

```
/plugin marketplace add <owner>/game-maker-toolkit-plugins
/plugin install game-design@game-maker-toolkit-plugins
```

Skills then fire as `game-design:number-balancing`, `game-design:economy-design`,
and so on.

## Local development

```
claude --plugin-dir ./game-design          # load the plugin without a marketplace
claude plugin validate ./game-design        # check the plugin
claude plugin validate .                     # check the marketplace
```
