# Systems concepts

One entry per concept named in `SKILL.md`. Each says what it answers, what it is,
when it misleads, and what it cannot tell you. The last line matters most: a concept
used past its limit hides a broken interaction behind a plausible number.

## Interaction

### Interaction / emergence

- **Answers:** what does this mechanic do with the others.
- **Is:** the behavior that appears only when two or more mechanics act together —
  a combination none of them produces alone.
- **Misleads when:** the mechanic is judged in isolation. A card that is fine alone
  can be degenerate in a pair.
- **Cannot tell you:** which combination the player will actually build. Read the
  roster and the resolution order, do not assume the pairing.

### Redundancy / orthogonality

- **Answers:** does this mechanic add a different decision, or repeat one.
- **Is:** whether two mechanics let the player make genuinely different choices
  (orthogonal) or the same choice under two names (redundant).
- **Misleads when:** difference in flavor is read as difference in decision. Two
  mechanics with different art and one effect are one decision.
- **Cannot tell you:** which of two redundant mechanics to cut. That is a design
  call about theme and role, not a systems result.

### Depth vs complexity

- **Answers:** does this mechanic add decisions or only rules.
- **Is:** depth is the count of meaningful decisions the system sustains; complexity
  is the count of rules. They are not the same, and more rules can lower depth.
- **Misleads when:** a rule count is read as richness. A mechanic that adds
  complexity without a new decision is a cost with no payoff.
- **Cannot tell you:** how much complexity the audience will bear. That is a
  teaching and audience question, not a systems one.

## Feedback

### Positive feedback (snowball)

- **Answers:** does an advantage produce more advantage.
- **Is:** a loop where holding more of something makes it easier to gain more —
  power, tempo, or position that compounds.
- **Misleads when:** judged at the first step, where it looks modest. Compare at the
  full intended horizon, the way a growth curve is read.
- **Cannot tell you:** where to cap it. That a cap is needed is a systems result;
  the cap's size is a magnitude for `number-balancing`.

### Negative feedback (self-correction)

- **Answers:** does the system pull itself back toward a stable state.
- **Is:** a loop that resists a lead — a catch-up, a rising cost, or a constraint the
  player sets from what they hold and therefore cannot fail.
- **Misleads when:** its removal is read as a small change. Randomizing a
  player-set constraint removes a guarantee, and any penalty tied to failing it
  multiplies.
- **Cannot tell you:** the new failure rate or the re-priced penalty. Those are
  magnitudes; hand them to `number-balancing`.

## Convergence

### Kind vs degree

- **Answers:** does this mechanic change a rule or only a number.
- **Is:** the difference between changing what a mechanic *is* (a new rule, a twist)
  and changing how much it does (a value on the same axis).
- **Misleads when:** a tuned number is presented as a new mechanic. Tuning cannot
  leave the axis it starts on, so it is degree, not kind.
- **Cannot tell you:** which new rule to reach for. It only shows that a number is
  not a new decision.

### Dominant strategy

- **Answers:** does one line of play beat the others.
- **Is:** a strategy that wins regardless of situation, so the player stops choosing
  and repeats it. It collapses the decision space around itself.
- **Misleads when:** confused with one option being dead. A dead option is a
  magnitude result (worse on every axis); a dominant strategy is a whole line the
  system rewards too well.
- **Cannot tell you:** the value that would un-dominate it. Often no value does; the
  fix changes the line, not its stakes.

### Degeneracy (unbounded combo / loop)

- **Answers:** does a combination run away without a limit.
- **Is:** two or more mechanics that chain into an unbounded result — infinite value,
  an endless loop, or a lock the opponent cannot answer.
- **Misleads when:** treated as a strong combo to be priced down. An unbounded chain
  has no price; the fix caps or breaks the loop.
- **Cannot tell you:** where to place the cap. That a cap is needed is a systems
  result; its size is a magnitude.

## Worked example

A fictional game has two mechanics. **Echo** repeats the last action played.
**Kindle** grants one extra action whenever an action deals damage. Each is fine
alone. The designer asks whether adding Echo to a game that already has Kindle needs
its repeat "toned down."

**Step 1 — the pattern.** The player should choose *which* action to spend a limited
turn on.

**Step 2 — the interaction.** Echo repeats an action; Kindle grants an action when an
action deals damage. A damaging action triggers Kindle (extra action), which can be
Echo (repeat the damaging action), which deals damage (triggers Kindle again).

**Step 3 — classify.** This is **degeneracy**: Echo + Kindle form an unbounded loop
as long as the repeated action deals damage. It is not synergy to be admired; it is a
chain with no limit.

**Step 4 — feedback.** The loop is pure positive feedback with no negative term — each
step funds the next — so it does not settle.

**Verdict.** The defect is a degenerate loop between Echo and Kindle, not the size of
Echo's repeat. Toning the number down slows the loop but does not bound it — with
enough damage it still runs away. The fix is structural: cap Kindle's extra actions
per turn, or stop Echo from copying a Kindle-granted action. Then hand the cap's size
to `number-balancing`. Reducing the repeat alone would leave the loop unbounded.
