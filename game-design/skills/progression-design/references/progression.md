# Progression concepts

One entry per concept named in `SKILL.md`. Each says what it answers, what it is,
when it misleads, and what it cannot tell you. The last line matters most: a concept
used past its limit hides a broken arc behind a plausible number.

## The arc

### Difficulty curve

- **Answers:** what shape does the challenge trace across the run.
- **Is:** the aggregate difficulty section by section — ramps, plateaus, boss spikes,
  and rest valleys — read across the whole run, not one encounter.
- **Misleads when:** read as one encounter's number. A single hard fight is not the
  curve; the curve is the sequence.
- **Cannot tell you:** the right height at any point. That depends on the power curve
  beside it, not on the difficulty alone.

### Challenge vs power (two curves)

- **Answers:** does the difficulty rise track the player's rising strength.
- **Is:** the gap between the challenge curve and the build-power curve across the
  run. The run stays tense only while the gap stays small and positive.
- **Misleads when:** either curve is judged alone. A steep difficulty ramp is right
  against a steep power ramp and a wall against a flat one.
- **Cannot tell you:** the size of a correction. That the curves diverge is an arc
  result; by how much to move a value is a magnitude for `number-balancing`.

### Horizon / convergence

- **Answers:** how long the arc runs and where it stops being decisions.
- **Is:** the intended length of the run, and the point where the best line is found
  and the remaining run repeats it.
- **Misleads when:** measured at the start, where every run still has choices. Judge
  convergence at the full horizon.
- **Cannot tell you:** which new axis to add late. It only shows that the run has
  gone solved.

## The rhythm

### Pacing / rhythm

- **Answers:** does the run breathe.
- **Is:** the placement of peaks and rests, tension and release, across the arc. A run
  climbs and recovers; it does not climb without pause.
- **Misleads when:** confused with average difficulty. A run can average correctly and
  still be a monotone grind with no rests.
- **Cannot tell you:** how long a rest should last. That is a pacing call to test, not
  a value to derive.

### Peak-end

- **Answers:** what will the player remember of the run.
- **Is:** the tendency to recall the strongest moment and the last one far more than
  the average. Place both on purpose.
- **Misleads when:** the average is optimized and the peak and ending left to chance.
  A flat run with a weak ending is remembered as weak.
- **Cannot tell you:** how large a peak is enough. That is a felt magnitude, tested,
  not computed.

## The borrowed lens

### Flow channel

- **Answers:** is the challenge near the player's mastery.
- **Is:** the band where challenge sits just above current skill — below it is dull,
  far above it is punishing — as skill grows across the run.
- **Misleads when:** its thresholds are treated as measured facts of this game. The
  band is borrowed from outside and its edges are not known here.
- **Cannot tell you:** the width of the band in this game. **Mark every use as an
  assumption and test the arc with players.**

### Mastery / learning rate

- **Answers:** how fast does the player get better across the run.
- **Is:** the rate at which the player learns the systems and improves their build,
  which the difficulty curve must track.
- **Misleads when:** assumed uniform. A player learns fastest early and plateaus; a
  linear difficulty ramp can drift out of the flow band as mastery bends.
- **Cannot tell you:** the real learning rate. Observe it in playtests rather than
  assuming a shape.

## Worked example

A fictional roguelike runs eight sections. The player's build gains a compounding
damage bonus each section; enemies gain a flat health increase each section. The
designer asks whether section 8 enemies "need more health" because late runs feel
trivial.

**Step 1 — the arc.** The run should stay tense to the end: each section a little
harder than the player's growing build can comfortably handle.

**Steps 2 and 3 — the two curves.** Enemy health rises *linearly* (a flat step per
section). Player damage rises *multiplicatively* (a compounding bonus per section). By
section 8 the power curve has pulled far ahead of the challenge curve.

**Step 4 — the gap.** The curves diverge: power outpaces difficulty, and the gap
widens every section because one curve compounds and the other adds. Section 8 is not
the problem; the *shapes* are mismatched, so no health number for section 8 alone
holds — buff it enough to matter at 8 and sections 5 to 7 become a wall.

**Verdict.** The defect is a power curve that compounds against a difficulty curve
that only adds — an arc problem, not a section-8 value. The fix changes a shape: let
enemy difficulty scale with the player's build (track the power curve), or cap the
compounding bonus through `systems-design`. Then hand the specific scaling values
to `number-balancing`. Adding health at section 8 alone would leave the late run
trivial and the mid run brutal.
