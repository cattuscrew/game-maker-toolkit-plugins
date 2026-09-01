---
name: systems-design
description: Judge how a mechanic interacts with the others — synergy, feedback loops, dominant strategies, degenerate combos, and whether a change adds a real decision or collapses one. Name the intended play pattern, map the mechanic against the others it touches, classify each interaction, and check feedback and the decision space before any magnitude. Use for combos, synergy, feedback, dominance, and degeneracy; hand resource flow to economy-design and every magnitude to number-balancing, and do not use for a plain lookup.
---

# Systems Design

Use this route to judge a mechanic by what it does **with the others**, not alone —
whether it enriches the system or breaks it. A mechanic that looks fine in
isolation can form an unbounded loop, a dominant line, or a dead duplicate the
moment it meets the rest.

This route decides **interaction**: how mechanics combine, which feedback loops a
change creates or removes, whether a strategy dominates, whether a combo is
degenerate, and whether a change adds a real decision. It does not decide
**magnitude** — hand a value, chance, or cap to `number-balancing` — and it does
not decide **resource flow** — hand a currency, source, or sink to
`economy-design`. It repeats no lens from either.

## Automatic trigger threshold

Enter this route when a request adds or weighs a mechanic against the others — a
combo, a synergy, a feedback loop, a possible dominant line, a possible degenerate
loop, or whether a change adds a genuine choice.

Hand off, do not enter, when the request needs a magnitude (that is
`number-balancing`) or asks about a resource's flow, a currency, or what to
charge (that is `economy-design`). Stay out entirely when the request only reads
an authored value or explains what a mechanic does; a lookup is not an interaction
question.

## Step 0 — read the actual interactions

Do this before the method, unconditionally. It is a gate, not a fallback for when a
detail is missing.

- **Read how the mechanic actually combines with the others.** An interaction
  lives in how effects compose and in the order they fire, not in one card's text.
  Read the composition before reasoning about the combination.
- **Never judge a mechanic in isolation.** Its value is what it does with the rest
  of the system. A mechanic that is fine alone can be degenerate in a pair.
- **Name the other mechanics a change touches, and read them too.** A change to one
  trigger, cost, or effect reaches every mechanic that shares it. Find them before
  judging the whole.
- **When the firing order or a touched mechanic sits in no place you have read,
  find it or ask.** Do not assume the interaction from the mechanic that prompted
  the question.

## The method

Follow these in order. Steps 1 to 6 happen in words with the designer, before any
magnitude is chosen.

1. **Name the intended play pattern.** What decisions should the system keep
   producing? A mechanic exists to add to that pattern, not only to be strong. If
   the pattern has not been named, ask before mapping anything.
2. **Map the mechanic's interactions.** List the other mechanics it touches — shared
   triggers, shared costs, shared effects, shared firing order — not the
   mechanic alone.
3. **Classify each interaction.** Mark each as **synergy** (they combine into a new
   capability), **redundancy** (the pair does what an existing pair already does),
   **anti-synergy** (they cancel), or **degeneracy** (they form an unbounded chain
   or a loop).
4. **Check feedback.** Does the mechanic create a **positive** loop — a snowball
   where an advantage produces more advantage — and if so, is it capped? Or does it
   **remove a negative** loop — a self-correction the design relied on, such as a
   constraint the player could always satisfy until it was randomized?
5. **Check kind versus degree.** Does the mechanic change a **rule** or only a
   **number**? A change that stays on the axis it started on is degree, not a new
   decision; a real new mechanic changes what the thing *is*.
6. **Check the decision space.** Does the mechanic add a genuinely different axis of
   choice, or does it dominate and collapse an axis the player already had?
7. **Hand resource flow to `economy-design` and every magnitude to
   `number-balancing`.** This route names the interaction and the fix; those
   routes size and structure it.

Two rules keep the reasoning honest:

- **A mechanic is its interactions.** Judging it alone is judging half of it.
- **Kind before degree.** A number cannot repair a broken interaction, and a new
  number on the same axis is not a new decision.

## When the structure is the problem

Sometimes the interaction is the defect, not any value. Say so only when the mapping
proves one of these, name what must change, and stop reaching for a magnitude — no
number repairs a broken interaction.

| Result | Why a number cannot repair it |
| --- | --- |
| dominant strategy | one line beats all others regardless of situation; the fix removes or changes the line, not its stakes |
| degenerate loop | a combo forms an unbounded chain; the fix caps or breaks the loop, and the cap's size is a magnitude |
| redundancy | two mechanics make the same decision; the fix cuts one or gives it a different axis |
| lost self-correction | a stabilizer the design relied on was removed; the fix restores the loop, or re-prices its failure through `number-balancing` |
| false depth | the mechanic adds rules without adding decisions; the fix simplifies rather than tunes |

## Project overlay

This skill holds the reusable method, not a game's mechanics, authored values, or
interaction-specific rules. Before applying it in a project, read that project's
product direction and its current authored sources — the data that owns current
values and the validation that owns legal bounds — and treat those as your Step 0
sources. Do not copy authored values or legal bounds into this generic method.

## Output

Use this layout:

- **intended pattern:** the decisions the system should keep producing, one line
- **interactions:** each other mechanic the change touches, and the shared trigger, cost, effect, or order
- **classification:** each interaction marked synergy, redundancy, anti-synergy, or degeneracy
- **feedback:** the loops created or removed, and whether a snowball is capped
- **decision space:** the axis the mechanic adds, dominates, or collapses
- **hand-offs:** the resource-flow questions for `economy-design` and the magnitudes for `number-balancing`
- **verdict:** one plain sentence

Report a broken interaction as a stop with what must change, never as a number to
tune.

## Boundaries

**This route ends at the verdict.** It writes no plan and changes no file. A plan
follows a person confirming the solution and never precedes it.

This route is read-only advisory. It reasons about how mechanics interact and
changes no authored data. Changing an authored value is a separate step in your
project's normal change process; this route ends at the verdict.

It does not run the game or infer product intent from the mechanics that happen to
exist. When the firing order, a touched mechanic, or the intended play pattern
is missing, read its owning source or ask before judging the interaction.
