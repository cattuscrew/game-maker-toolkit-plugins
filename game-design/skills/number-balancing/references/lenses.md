# Lenses

One entry per lens named in `SKILL.md`. Each says what it answers, what it is,
when it misleads, and what it cannot tell you. The last line matters most: a
lens used past its limit produces a confident wrong number.

`p` is a chance per opportunity, `v` a value, `n` a count of repeats, `N` a
count of opportunities.

## Mathematics

These are exact once the inputs are supplied. They give numbers.

### Expected value

- **Answers:** what does this return on average, per opportunity.
- **Is:** `E = Σ pᵢ·vᵢ`, summed over every outcome.
- **Misleads when:** the spread matters more than the middle, which is most of
  the time in a game. Two mechanics with one average are two different mechanics.
- **Cannot tell you:** which feeling was wanted, or whether the average is the
  quantity the player experiences.

### Truncated geometric

- **Answers:** what is a repeat-until-it-fails effect worth when it stops at `n`.
- **Is:** `E = v·(p + p² + … + pⁿ)`.
- **Misleads when:** read as though `n` were a constraint. It is a reward
  parameter unless something charges for depth.
- **Cannot tell you:** where to stop. Nothing in it falls as `n` rises.

### Settling series

- **Answers:** what does an unbounded repeat converge to, and what does each
  further step still add.
- **Is:** `E = v·p/(1−p)`. Step `k` adds `v·pᵏ`, so the share still missing after
  a cap of `n` is `pⁿ`.
- **Misleads when:** used to argue a cap is pointless. The average settles; the
  best moment does not.
- **Cannot tell you:** how large the tail feels. That is peak-end memory.

### Variance

- **Answers:** are two options with one average actually the same option.
- **Is:** `σ² = Σ pᵢ·(vᵢ − E)²`.
- **Misleads when:** treated as a cost. A player behind in a run wants variance
  and will pay for it.
- **Cannot tell you:** which direction the spread is wanted in.

### Growth curve

- **Answers:** does this break late.
- **Is:** the shape of the value against the count — additive, multiplicative,
  or exponential. Compare options at the full intended horizon, not only at the
  first checkpoint.
- **Misleads when:** compared at the start, where every curve looks alike.
- **Cannot tell you:** the intended horizon. Ask, rather than storing a guess.

### Dominance

- **Answers:** is any option dead on arrival.
- **Is:** an option worse on every axis than another. No setting repairs it; the
  fix adds an axis.
- **Misleads when:** an axis is missing from the comparison, which makes a live
  option look dominated.
- **Cannot tell you:** which axis to add.

### Sensitivity

- **Answers:** is this knob a knob.
- **Is:** `ΔE / Δknob` across one authored step, read over the knob's whole legal
  range.
- **Misleads when:** measured at one point on a curve that bends.
- **Cannot tell you:** whether the movement is felt. That is the just-noticeable
  difference.

### Reach frequency

- **Answers:** how often is a printed ceiling actually reached.
- **Is:** `P(top)` per opportunity, reported as a rate. Across `N` opportunities
  the deepest chain typically seen is `n_max = floor(ln N / ln(1/p))` — a
  description, never a pass or a fail.
- **Misleads when:** turned into a requirement that the top be common. A top
  reached every run is not a rare event, and rarity is often the point.
- **Cannot tell you:** which rate was wanted. The designer picks that.

## Cognitive effects

These give directions. Every one was measured outside this game, so none of them
gives a magnitude in it. Mark every use as an assumption.

### Just-noticeable difference (Weber–Fechner)

- **Answers:** is this change large enough to author at all.
- **Direction:** a change under roughly 10–20% of the reference value is not
  noticed.
- **Applies to:** the quantity the player observes, which is often the best
  moment rather than the average.
- **Cannot tell you:** the threshold in this game. The band is borrowed.

### Probability weighting (Kahneman and Tversky)

- **Answers:** does a rare outcome feel as rare as it is.
- **Direction:** a small chance feels bigger than it is; a near-certain one feels
  smaller. So the price of rarity is felt as lighter than the arithmetic.
- **Cannot tell you:** by how much. The published curve was fitted to money.

### Loss aversion (Kahneman and Tversky)

- **Direction:** a loss lands about twice as hard as a same-sized gain, so a cost
  line is expensive and one of them does more work than five.
- **Cannot tell you:** the ratio here.

### Certainty effect

- **Direction:** removing the last of a risk is worth far more than reducing it,
  so "always" is a large promise and 95% is not nearly it.
- **Cannot tell you:** what to charge for the last step.

### Reference point

- **Direction:** value is felt against the number that came before, not against
  zero. The first number the player meets sets the scale for every later one.
- **Cannot tell you:** which reference the player is holding.

### Hyperbolic discounting

- **Direction:** a payoff that arrives later is worth much less than its
  arithmetic. Deferred rewards are discounted even when their expected value is
  unchanged.
- **Cannot tell you:** the discount rate here.

### Peak-end memory

- **Direction:** the player remembers the best moment and the last one, not the
  average. **Where this disagrees with expected value about whether a change
  matters, this wins.**
- **Cannot tell you:** how much peak is enough.

## Worked example

A fictional reward offers either a Steady Cache or an Echo Cache. Unit: reward
tokens per attempt. This runs all eight steps without relying on any one game's
vocabulary or rules.

**Step 1 — the intended experience.** The Echo Cache should feel like an
uncertain start with a spectacular streak. The Steady Cache is the reliable
alternative.

**Steps 2 and 3 — the moments, each given a job.**

| moment | job | Steady Cache: `50% × 4`, no repeat | Echo Cache: `20% × 6`, max 3 |
| --- | --- | --- | --- |
| reward 1 | price | `0.50 × 4 = 2.000` | `0.20 × 6 = 1.200` |
| reward 2 | reward | — | `0.04 × 6 = 0.240` |
| reward 3 | reward | — | `0.008 × 6 = 0.048` |
| total | | `2.000` | `1.488` |
| best moment | | `4` at 1 in 2 | `18` at 1 in 125 |

**Steps 4 and 5 — is the price perceptible, is the reward legible.** The Echo
Cache pays less in the first moment on both chance and expected reward. Its
streak can produce two later rewards and a best moment the Steady Cache cannot
produce. Those axes fit the intended experience; another mechanic could carry
its price and reward on different axes.

**Step 6 — the checks.**

```text
1  return         1.488 / 2.000 = 0.744    >= 1    FAIL
2  first moment   1.200 / 2.000 = 0.600    < 1     PASS
3  reach the top  0.20^3 = 0.8%  ->  1 in 125 attempts   (rate, not a test)
```

The current Echo Cache gives up about a quarter of the average return for a best
moment 4.5 times larger. Whether that is acceptable depends on the intended
trade; the calculation exposes both effects rather than choosing between them.

**Step 7 — can the cap be wrong.** Not without a downside attached to it.
Raising the cap adds average reward and enlarges the best moment. The cap chooses
the size and rarity of the longest streak:

| cap | best moment | reach the top | mean | share of unbounded mean |
| --- | --- | --- | --- | --- |
| 2 | 12 | 1 in 25 | 1.4400 | 96.0% |
| 3 | 18 | 1 in 125 | 1.4880 | 99.2% |
| 5 | 30 | 1 in 3,125 | 1.4995 | 99.968% |

The average settles while the largest possible streak keeps growing. This is a
choice about the remembered event, not a trade the cap itself balances.

**Step 8 and the verdict.** One possible setting is `25% × 7`, still capped at
3. Its first moment is `1.750`, below the Steady Cache's `2.000`; its total is
`2.297`, above the Steady Cache; and its best moment is `21`, reached once in 64
attempts. These numbers satisfy the stated price and return checks, but the
designer still decides whether that frequency produces the intended experience.

> **Verdict:** `25% × 7` keeps a weaker first moment, restores the average
> return, and buys a rare three-reward streak; the cap chooses how large and
> rare that streak can become.

**feel:** a 25% chance may feel larger than its arithmetic share — assumption.
The average improvement is modest beside a best moment more than five times the
Steady Cache's, so both should be tested with players rather than collapsed into
one claim — assumption.
