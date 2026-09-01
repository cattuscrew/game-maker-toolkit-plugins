---
name: progression-design
description: Judge a game's difficulty and reward arc across a whole run or session — the difficulty curve, whether challenge tracks the player's growing power, pacing with peaks and rests, and the flow channel. Name the intended arc, plot the challenge curve against the power curve, check the pacing, and mark flow thresholds as assumptions. Use for the run ramp, boss spikes, rest beats, and reward cadence; hand magnitude to number-balancing, resource flow to economy-design, and self-compounding scaling to systems-design, and do not use for a plain lookup.
---

# Progression Design

Use this route to judge the shape of a whole run — how challenge and reward rise
across the session — not one value, one resource, or one interaction. A run can be
perfectly tuned mechanic by mechanic and still fail as an arc: a wall in the middle,
a trivial ending, a monotone ramp with no rest.

This route owns the **arc**: the difficulty curve, whether challenge tracks the
player's growing power, and the pacing of peaks and rests across the run. It does
not own **magnitude** (a value hands to `number-balancing`), **resource flow** (a
currency or a source and sink hands to `economy-design`), or a **self-compounding
mechanic** (a snowball hands to `systems-design`). It repeats no lens from any of
them.

## Automatic trigger threshold

Enter this route when a request shapes the run's arc — the difficulty ramp, a boss
spike, a rest beat, the reward cadence, or whether the run escalates to match the
player's growing build.

Hand off, do not enter, when the request needs a magnitude (that is
`number-balancing`), asks about a resource's flow or what to charge (that is
`economy-design`), or asks whether one mechanic's advantage compounds (that is
`systems-design`). Stay out entirely when the request only reads an authored
value; a lookup is not an arc question.

## Step 0 — read the authored progression

Do this before the method, unconditionally. It is a gate, not a fallback for when a
detail is missing.

- **Read how difficulty actually scales across the run.** The arc lives in the
  section structure and the enemies each section fields, not in one encounter. Read
  the escalation before reasoning about it.
- **Read how reward actually paces across the run.** Where the player gains power,
  and how fast, sets the curve the difficulty must race. Read the reward cadence,
  never assume it.
- **Read the whole horizon, not the first section.** Every curve looks alike at the
  start. Judge the arc at the full intended length of the run.
- **When the section structure, the enemy scaling, or the reward cadence sits in no
  place you have read, find it or ask.** Do not infer the arc from one section.

## The method

Follow these in order. Steps 1 to 6 happen in words with the designer, before any
magnitude is chosen.

1. **Name the intended arc.** What shape should challenge and reward trace across the
   run — the ramp, the peaks, the rests — and what should the run feel like at its
   start, middle, and end? If the arc has not been named, ask before plotting
   anything.
2. **Plot the challenge curve.** Trace how aggregate difficulty rises across the
   run's sections, not one encounter's number.
3. **Plot the power curve.** Trace how the player's build strength rises across the
   run, from starting kit to a late build.
4. **Check the two curves race in the zone.** Difficulty should track power, staying
   between trivial and brutal. Name where they diverge — where difficulty pulls ahead
   into a wall, or power pulls ahead into a trivial stretch.
5. **Check the pacing.** A run needs peaks and rests, tension and release, not a
   monotone climb. The player remembers the best moment and the last one, so place
   them on purpose.
6. **Check the flow channel.** Challenge should sit near the player's growing
   mastery — above it feels punishing, below it feels dull. **This threshold is
   borrowed from outside the game; mark every use of it as an assumption and
   recommend testing the arc with players.**
7. **Hand off the pieces.** A magnitude goes to `number-balancing`, a resource's
   flow to `economy-design`, and a self-compounding scaling to
   `systems-design`. This route sets the arc; those routes size and shape its
   parts.

Two rules keep the reasoning honest:

- **The arc is not its pieces.** A run tuned mechanic by mechanic can still fail as a
  whole; judge the shape across the horizon.
- **The two curves matter more than either alone.** A rising difficulty is only right
  against a rising power; measure the gap, not the height.

## When the arc is the problem

Sometimes the shape of the run is the defect, not any value. Say so only when the two
curves prove one of these, name what must change, and stop reaching for a magnitude —
no single number repairs a broken arc.

| Result | Why a number cannot repair it |
| --- | --- |
| difficulty outpaces power | a wall the player cannot grow past; the fix rebalances the two curves, not one enemy's number |
| power outpaces difficulty | a trivial late run; the fix raises the challenge curve, or caps the build snowball through `systems-design` |
| monotone ramp | every step harder than the last with no rest; the fix adds pacing, peaks and valleys, not a bigger number |
| flat arc | the run never escalates; the fix is a rising curve, not a tuned encounter |
| premature convergence | the run is solved partway and stops being decisions; the fix adds a new axis late, not a bigger number |

## Project overlay

This skill holds the reusable method, not a game's content, authored values, or
run-specific rules. Before applying it in a project, read that project's product
direction and its current authored sources — the data that owns current values and
the validation that owns legal bounds — and treat those as your Step 0 sources. Do
not copy authored values or legal bounds into this generic method.

## Output

Use this layout:

- **intended arc:** the shape of challenge and reward across the run, one line
- **challenge curve:** how aggregate difficulty rises across the sections
- **power curve:** how the player's build strength rises across the run
- **gap:** where the two curves diverge — a wall, a trivial stretch, or in the zone
- **pacing:** the peaks and rests, and the best and last moments placed on purpose
- **hand-offs:** the magnitudes for `number-balancing`, resource flow for `economy-design`, and self-compounding scaling for `systems-design`
- **verdict:** one plain sentence, with any flow claim marked an assumption to test

Report a broken arc as a stop with the curve that must change, never as a number to
tune.

## Boundaries

**This route ends at the verdict.** It writes no plan and changes no file. A plan
follows a person confirming the solution and never precedes it.

This route is read-only advisory. It reasons about the run's arc and changes no
authored data. Changing an authored value is a separate step in your project's
normal change process; this route ends at the verdict.

Its flow-channel knowledge is the least tested in the field; it never states a felt
difficulty threshold as fact, marks each as a borrowed assumption, and recommends a
playtest. When the section structure, the enemy scaling, the reward cadence, or the
intended arc is missing, read its owning source or ask before judging the run.
