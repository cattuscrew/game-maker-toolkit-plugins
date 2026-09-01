---
name: economy-design
description: Choose, defend, or restructure a game's resource economy — its currencies, sources and sinks, and what a mechanic charges. Name the intended economic tension, map every resource flow as a source or a sink, check whether inflow and outflow balance, and decide the currency structure before any magnitude. Use for adding or weighing a currency, resource flow, sinks, and what to charge; hand every magnitude to number-balancing and do not use for a plain lookup of an authored value.
---

# Economy Design

Use this route to shape a game's resource economy from design intent — what
resources exist, where value enters and leaves, and what a mechanic should charge
— rather than reaching for a bigger number on the resource already in use.

This route decides **structure**: which resources are in play, whether each flow
is a source or a sink, whether the economy inflates or starves, and whether a
decision needs a new currency or a different one. It does not decide **magnitude**.
The moment a specific value, chance, cap, or cost must be sized, hand it to
`number-balancing`; that route owns every expected-value, variance, and curve
lens, and this route repeats none of them.

## Automatic trigger threshold

Enter this route when a request adds, removes, or weighs a currency or resource;
asks where value enters or leaves the game; asks whether a cost is a real cost; or
asks whether the economy inflates or starves.

Hand off, do not enter, when the request only needs a magnitude — how big a cost,
how likely a drop, how large a cap. That is `number-balancing`. Stay out
entirely when the request only reads an authored value or explains what a mechanic
does; a lookup is not an economy question.

## Step 0 — read the authored economy

Do this before the method, unconditionally. It is a gate, not a fallback for when a
value is missing.

- **Name every resource actually in play, and read it.** A resource is anything the
  game tracks that a mechanic can add to or take from — health, a currency, a hand,
  a deck, a capacity, a counter. Read the sources that hold them before reasoning
  about the flow between them.
- **Never assume a resource is a currency because it has a number.** A quantity the
  game tracks is not a cost until a mechanic spends it against something the player
  wants. Read whether anything charges it.
- **A source is not a sink.** Reading where a resource is granted tells you nothing
  about where it is spent. Find both before judging the flow, because an economy is
  the balance between them, not the size of either.
- **When a resource, source, or sink sits in no authored place, ask.** Do not infer
  the economy from the mechanics that happen to exist; a missing sink is a finding,
  not a value to invent.

## The method

Follow these in order. Steps 1 to 5 happen in words with the designer, before any
magnitude is chosen.

1. **Name the intended economic tension.** What scarce thing should the player feel
   they are weighing? An economy exists to make one resource cost another. If the
   tension has not been named, ask before mapping anything.
2. **Map every resource as flows, and give each flow a job: source or sink.** A
   source grants the resource; a sink spends it. List them apart. A resource with
   only sources piles up; a resource with only sinks runs dry.
3. **Check the flow pressure.** Compare the sources against the sinks for each
   resource. Too many sources and the resource **inflates** — it loses meaning and
   every price denominated in it stops biting. Too many sinks and the player
   **starves** — the resource stops being a choice and becomes a wall.
4. **Check the currency structure.** Ask whether one resource carries every cost,
   so every trade collapses into the same decision at a different size. When it
   does, a second currency changes more decisions than any retuning of the first —
   but before inventing one, find a resource the game already models and never
   charges. The cheapest new currency is the one already on the table.
5. **Check that each cost is a real cost.** Spending here must forgo something the
   player wants — an opportunity cost. A currency with nothing to compete for, or a
   cost the player would pay anyway, is decoration, not a price.
6. **Hand every magnitude to `number-balancing`.** This route names the sink and
   the currency; that route sizes them. Economy-design sets what flows; it never
   sets how much.

Two rules keep the reasoning honest:

- **Structure precedes magnitude.** A well-sized number in a broken economy is
  still broken. Fix what flows before choosing how much.
- **The already-modeled resource beats the invented one.** A second currency the
  codebase already tracks costs nothing to add and reuses existing machinery; an
  invented one adds a whole system to author, balance, and teach.

## When the structure is the problem

Sometimes the economy's shape is the defect, not its numbers. Say so only when the
mapping proves one of these, name the flow that must change, and stop reaching for
a magnitude — no value repairs a broken structure.

| Result | Why a number cannot repair it |
| --- | --- |
| source with no sink | the resource inflates however it is priced; the fix adds a sink |
| single-currency collapse | every cost weighs the same thing; the fix adds a second currency, not a bigger first one |
| dominant conversion | one resource converts into another so cheaply that only that loop is played; the fix changes the rate or the rule, not the stakes |
| runaway source | a source that scales with the resource it grants compounds; the fix caps or breaks the loop, not the payout |
| dead currency | the resource has no sink the player wants, so it never becomes a choice; the fix gives it something to buy |

## Project overlay

This skill holds the reusable method, not a game's currencies, authored values, or
economy-specific rules. Before applying it in a project, read that project's
product direction and its current authored sources — the data that owns current
values and the validation that owns legal bounds — and treat those as your Step 0
sources. Do not copy authored values or legal bounds into this generic method.

## Output

Use this layout:

- **intended tension:** the scarce thing the player weighs, one line
- **resources:** each resource in play, with its sources and its sinks listed apart
- **pressure:** for each resource, whether sources and sinks balance, inflate, or starve
- **structure:** the currency decision — one currency or a second, and which resource carries the new cost
- **magnitudes:** the sinks and currencies to hand to `number-balancing`, named but not sized
- **verdict:** one plain sentence

Report a broken structure as a stop with the flow that must change, never as a
number to tune.

## Boundaries

**This route ends at the verdict.** It writes no plan and changes no file. A plan
follows a person confirming the solution and never precedes it.

This route is read-only advisory. It reasons about resource flow and changes no
authored data. Changing an authored value is a separate step in your project's
normal change process; this route ends at the verdict.

It does not run the game or infer product intent from the mechanics that happen to
exist. When resources, sources, sinks, or the intended tension are missing, read
their owning sources or ask before judging the economy.
