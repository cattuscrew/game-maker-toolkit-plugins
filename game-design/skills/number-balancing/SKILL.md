---
name: number-balancing
description: Choose, compare, or defend a number in a game mechanic. Name the intended player experience first, split the mechanic into the moments the player experiences, mark each moment as price or reward, and use mathematics to check rather than generate the choice. Use for balancing options, chances, values, caps, and costs; do not use for simple lookups of already-authored values.
---

# Number Balancing

Use this route to choose a number from design intent rather than reason backward
from a total or average.

## Automatic trigger threshold

Enter this route when a request chooses a number, compares options, asks whether
a trade is fair, or asks a chance, value, cap, or cost to be defended.

Stay out of it when the request only reads an authored value, explains what a
mechanic does, or contains no design choice. A lookup is not a balance question.
A question about which resource to charge, or whether the economy inflates or
starves, is structure rather than magnitude — hand it to `economy-design`.

## Step 0 — read the authored numbers

Do this before step 1, unconditionally. It is a gate, not a fallback for when a
value is missing. Every number in the answer comes from an authored source or
from the designer; none comes from what a number of that kind usually is.

- **Name the sources holding the values in play, and read them** before
  reasoning about any of them. Reading them afterward to confirm a conclusion is
  the same error later.
- **Never quote a chance, a range, or a count that has not been read.** A die is
  not numbered 1 to `n` because it has `n` sides, and a rarity is not uniform
  because it has categories. Authored faces and weights decide both.
- **A sample is not the whole.** A starting loadout bounds what the player holds
  at the start, never what the system permits. Say which of the two any number
  describes, and read the validation that owns the legal bound rather than
  inferring it from the values that happen to exist.
- **When a needed value sits in no source, ask for it.** Do not pick a plausible
  range and reason from it. A number invented here is invisible by step 6,
  because every later step treats it as read.

## The eight steps

Follow these in order. Steps 1 to 5 happen in words with the designer before any
arithmetic.

1. **Name the intended player experience.** A number exists to produce that
   experience. If it has not been named, ask before calculating.
2. **Split the mechanic into the moments the player experiences.** Compare the
   first moment with the first, later moments with later ones, and meaningful
   checkpoints across a longer system. A total hides their order.
3. **Give each moment a job: price or reward.** State where the player gives
   something up and where the mechanic pays them back.
4. **Make the price perceptible on the axes that carry it.** Identify the
   relevant axes from the mechanic instead of assuming they are chance, value,
   time, or another particular quantity.
5. **Make the reward legible beside the price.** Express both in a comparable
   unit when possible, and show the outcome or opportunity the price buys.
6. **Compute last.** Use expected value and the other relevant lenses to check
   that the proposed trade satisfies its stated constraints. Mathematics checks
   the choice; it does not supply the intended experience.
7. **Ask whether every knob can be wrong.** If moving a knob in one direction
   only improves every measured outcome, it is not balancing a trade. Name what
   it actually chooses, such as scale, duration, rarity, or spectacle.
8. **Never judge a fragment.** If the visible part does not carry the intended
   experience, ask for the missing mechanic, time horizon, alternatives, or
   player state instead of tuning the fragment alone.

Two rules prevent backward reasoning:

- **Design intent generates; mathematics checks.** Exact arithmetic cannot say
  which player experience was wanted.
- **The average and the remembered event answer different questions.** Tune the
  average where it settles, then choose any remaining depth or spread for the
  size and rarity of memorable outcomes.

The warning sign is a conclusion drawn from totals alone.

## Fix one unit

Name the comparison unit once near the top of the answer. Prefer a quantity the
player directly observes. Convert comparable values once, then stay in that
unit.

If price and reward cannot honestly share a unit, keep separate axes and show
the trade rather than inventing a conversion. Use any unit named by the current
project's product direction before introducing a new one.

## Project overlay

This skill holds the reusable method, not a game's vocabulary, authored values,
or mechanic-specific balancing rules. Before applying it in a project, read that
project's product direction and its current authored sources — the data that
owns current values and the validation that owns legal bounds — and treat those
as your Step 0 sources. Do not copy authored values or legal bounds into this
generic method.

## Diverge before converging

Steps 2 to 5 produce options. This section decides when there is more than one.

- **List the axes the mechanic has** before proposing anything, read from its
  authored shape and the surrounding system rather than from imagination. An
  axis is something that can differ between options: a value, a trigger, a
  duration, a count, a chance, an added or removed rule.
- **Name the axis each proposal uses.** Two proposals on one axis are one
  proposal, however far apart their numbers sit.
- **Exhaust the list before returning to an axis already tried.** When every
  axis is tried and none carries the design, say so. That is a real result, and
  it usually means the change needs new capability rather than a new number.
- The failure this catches: **keeping one option's reward and attaching a price
  to it is a single shape, not a design space.** When every proposal is that
  shape, nothing has been designed yet — the options differ in their price, not
  in what they are.

## Step 6 — pick the mathematics

`p` is a chance per opportunity, `v` a value, and `n` a repeat count.

| Question | Lens | Calculation |
| --- | --- | --- |
| what returns on average | expected value | `E = Σ pᵢ·vᵢ` |
| what bounded repeats return | truncated geometric | `E = v·(p + p² + … + pⁿ)` |
| where unbounded repeats settle | settling series | `E = v·p/(1−p)`, plus what each further step adds |
| how options with one average differ | variance | `σ² = Σ pᵢ·(vᵢ − E)²` |
| how value changes across time or count | growth curve | compare at the full intended horizon |
| whether an option is worse on every axis | dominance | remove it or add a meaningful axis |
| how much one authored step changes | sensitivity | `ΔE / Δknob` across the legal range |
| how often a ceiling appears | reach frequency | `P(top)` per opportunity, reported as a rate |

`n_max = floor(ln N / ln(1/p))` describes the deepest chain typically seen
across `N` opportunities. It is not a pass/fail check. A repeat count with no
downside term cannot fail a balance test.

Read `references/lenses.md` when choosing a lens or when a worked example would
help. It states what each lens cannot decide.

## Step 6 — correct with cognitive effects

Use these only for direction. Never take a magnitude from them without evidence
from the game being balanced, and mark each use as an assumption.

| Effect | Direction | Applies to |
| --- | --- | --- |
| just-noticeable difference | a small relative change may not be felt | the quantity the player observes |
| probability weighting | rare chances can feel larger and near-certain chances smaller | uncertain outcomes |
| loss aversion | a loss can land harder than an equal gain | explicit costs |
| certainty effect | removing the final risk can matter more than reducing it | guaranteed outcomes |
| reference point | a new value is felt against the previous one | upgrades and replacements |
| hyperbolic discounting | a delayed payoff can feel smaller than its arithmetic | deferred rewards |
| peak-end memory | the strongest and final moments can dominate recall | mechanics with a spread of outcomes |

Apply a felt-difference assumption to the quantity the player notices, not to an
invisible average. When the mean and the memorable outcome disagree about
whether a change matters, report both instead of letting either stand in for the
other.

## When the number is not the problem

Sometimes the mechanic's shape is the defect rather than its setting. Say so
only when the numbers prove one of these results, name the parameter that must
change, and stop tuning the current knob.

| Result | Why the setting cannot repair it |
| --- | --- |
| empty feasible window | no legal value satisfies the stated constraints together |
| dominance | one option is worse on every meaningful axis |
| sensitivity near zero | the knob barely changes the outcome across its legal range |
| every legal value unfelt | the whole feasible window sits inside the assumed felt-difference band |

The last result depends on a borrowed perception assumption. Mark that limit.
This route can show that a shape cannot meet its stated constraints; it cannot
decide whether the shape is interesting.

## Output

Use this layout:

- **intended experience:** the designer's words, one line
- **unit:** the comparison unit, or the separate axes if no honest conversion exists
- **table:** one row per player-experienced moment or checkpoint, each marked price or reward
- **checks:** numbered calculations; use `PASS/FAIL` only for explicit constraints
- **window:** when choosing a knob, show its feasible band and current or proposed value
- **feel:** applicable cognitive effects, direction only, each marked as an assumption
- **verdict:** one plain sentence

Report reach frequency as a rate, never as a pass or fail. Report a knob with no
downside as not balancing a trade, and name what it actually chooses.

## Boundaries

**This route ends at the verdict.** It writes no plan and changes no file. A plan
follows a person confirming the solution and never precedes it, because a plan
written first presents an unconfirmed design as settled.

This route is read-only advisory. It reasons about numbers and changes no
authored data. Changing an authored value is a separate step in your project's
normal change process; this route ends at the verdict.

It does not run the game or infer product intent from arithmetic. When current
values, legal bounds, or the whole mechanic are missing, read their owning
sources or ask for the missing intent before giving a number.
