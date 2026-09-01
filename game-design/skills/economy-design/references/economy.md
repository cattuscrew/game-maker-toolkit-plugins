# Economy concepts

One entry per concept named in `SKILL.md`. Each says what it answers, what it is,
when it misleads, and what it cannot tell you. The last line matters most: a
concept used past its limit hides a broken economy behind a plausible number.

## Flows

### Source (faucet)

- **Answers:** where does this resource enter the game.
- **Is:** any rule that grants the resource — a reward, a drop, a regeneration, a
  starting amount.
- **Misleads when:** counted as the whole economy. A generous source is only half a
  flow; what matters is whether a sink meets it.
- **Cannot tell you:** whether the grant is felt. That is the reference point the
  player is holding, which `number-balancing` sizes.

### Sink (drain)

- **Answers:** where does this resource leave the game.
- **Is:** any rule that spends the resource — a cost, an upkeep, a decay, a loss.
- **Misleads when:** assumed to exist because a source does. Many resources are
  granted and never spent; that is the defect, not the baseline.
- **Cannot tell you:** whether the player wants what the sink buys. A sink nobody
  chooses is a wall, not a price.

### Flow balance (economic pressure)

- **Answers:** does this resource hold its meaning over time.
- **Is:** the sources weighed against the sinks. Sources over sinks is inflation;
  sinks over sources is starvation.
- **Misleads when:** read at one moment. Pressure is a rate across the whole run,
  not the amount held on one turn.
- **Cannot tell you:** the size of the imbalance. Whether inflation is slow or
  ruinous is a magnitude for `number-balancing`.

## Sinks and currencies

### Sink types

- **Answers:** will this resource ever run dry.
- **Is:** three kinds of spend — mandatory (upkeep the player cannot skip), optional
  (upgrades the player may buy), and aspirational (a long goal). A resource with
  only optional and aspirational sinks piles up until it stops mattering.
- **Misleads when:** every sink is treated as equal. Only a mandatory sink applies
  steady pressure; optional ones apply it only when the player chooses.
- **Cannot tell you:** how much upkeep to charge. That is a magnitude.

### Currency count

- **Answers:** does every trade weigh the same thing.
- **Is:** whether one resource carries every cost. Under one currency every decision
  is the same decision at a different size, so the only knob left is the number. A
  second currency makes the player weigh a different thing.
- **Misleads when:** a single currency looks varied because its numbers vary.
  Different volumes of the same question are one question.
- **Cannot tell you:** which second resource to use. Read what the game already
  tracks.

### Reuse an already-modeled resource

- **Answers:** what is the cheapest second currency.
- **Is:** a resource the game already tracks but never charges — a capacity, a slot,
  a counter sitting free. Charging it adds a currency with no new system.
- **Misleads when:** skipped in favor of inventing a resource, which adds a whole
  system to author, balance, and teach.
- **Cannot tell you:** whether the reused resource carries the intended tension.
  That is step 1, not a search of the codebase.

### Opportunity cost

- **Answers:** is this cost a real cost.
- **Is:** the thing the player gives up by spending here rather than elsewhere. A
  currency is only a cost when it has more than one thing worth buying.
- **Misleads when:** confused with the printed price. A large number the player
  would pay anyway costs nothing; a small one that forecloses a wanted option costs
  a lot.
- **Cannot tell you:** how the player ranks the options. Ask, or test.

### Conversion (exchange rate)

- **Answers:** does one resource collapse into another.
- **Is:** any rule that turns one resource into a second at a rate. A rate too
  generous makes the conversion the only play; a rate too poor makes it dead.
- **Misleads when:** read as a price rather than a rule. The problem is usually the
  existence or direction of the conversion, not its number.
- **Cannot tell you:** the balanced rate, once the conversion is worth keeping. That
  is a magnitude.

### Runaway loop (positive feedback)

- **Answers:** does this economy compound.
- **Is:** a source that scales with the resource it grants, so more of the resource
  produces more of the resource. Left uncapped it dominates the late game.
- **Misleads when:** judged at the first step, where it looks modest. Compare at the
  full intended horizon, the way a growth curve is read.
- **Cannot tell you:** where to cap it. The cap's size is a magnitude; that a cap is
  needed is a structure result.

## Worked example

A fictional game grants one resource, Spark, from every victory, and spends it on
upgrades. The designer asks to "make the upgrades cost more" because players end a
run with far too much Spark.

**Step 1 — the tension.** The player should weigh *which* upgrade to buy, feeling
the ones they skip.

**Step 2 — the flows.**

| resource | sources | sinks |
| --- | --- | --- |
| Spark | every victory (steady) | upgrades (optional only) |

**Step 3 — pressure.** Spark inflates: a steady source meets only optional sinks,
so a player who buys little accumulates Spark until its price stops biting. Raising
the upgrade cost does not fix this — a richer player still outpaces it.

**Step 4 — structure.** Every upgrade is bought with Spark, so every purchase is the
same decision at a different size. The question "which upgrade" is really "do I have
enough Spark," which a large enough hoard answers "always." A second currency would
make the player weigh a different thing.

Before inventing one: the game already tracks **Charges**, a per-run count spent
only on a rare ability and otherwise sitting free. Pricing the strongest upgrades in
Charges as well as Spark makes the player weigh a scarce, non-inflating resource —
the choice the single currency had collapsed.

**Verdict.** The defect is a source with no matching sink and a single currency, not
the upgrade price. Add a mandatory Spark sink or a second currency (reuse Charges),
then hand the two prices to `number-balancing`. Raising the number alone would
leave the economy inflating.
