# throughlines

*Early thinking, unfolding in public. Expect revision.*

## What this is about

Most ways of specifying systems assume someone planning from above, executing a transition others will follow. This is about the opposite situation: you are the user, the authority, and the one deciding how fast to go. You want a way of thinking — and a durable record — that helps you move from your current setup to something better, at your own tempo, with an LLM as collaborator rather than controller.

This repo is an attempt at that.

## Why this matters

The default trajectory of AI tooling is toward centralization: a handful of companies own the systems you work in, capture the reasoning you do inside them, and mediate your choices through their interfaces. Each tool becomes a place where your patterns, preferences, and accumulated judgment live inside someone else's product.

This is an attempt to center technical autonomy with the individual rather than with centralized tech companies. The record you accumulate — your throughlines, your unfoldings, your reasons — stays yours. It lets you reason about your own systems without delegating that reasoning to whoever happens to own your current tools. It gives you sovereignty over your own choices: what to try, when, how fast, what to back off, what to keep.

An adjacent observation: as this record grows, it naturally becomes a per-person body of *whats* and *whys* — your working vocabulary, your preferred moves, the rationales behind your choices. That body is portable. It survives the death or replacement of any particular tool. It is the part of your working life that belongs to you and doesn't get captured by whatever product you happen to be using today.

## An example

You use Tana to manage projects. You manually scan job boards for opportunities worth turning into projects. You use Claude Code to research topics and draft project plans.

You can imagine a version of this where scanning happens automatically, projects get created for you, and initial research is already attached when you open them. You don't want to get there in one jump. You want to try small changes, keep what works, back off what doesn't, and stay in charge of the pace.

## The core idea

Tools come and go. Tana might be replaced. Claude Code will change. Job boards will be superseded by something else. What persists across those changes — if anything — is *you*: your patterns, your preferences, your values, the ways of operating you've earned through practice.

Those persistent things are your **throughlines**. They're the threads that run through your successive setups, tying them together into one continuous working life rather than disconnected episodes.

The proposal is:

1. Your throughlines are worth making explicit.
2. The moves you make to reshape your setup — each one small, reversible, under your authority — are worth recording.
3. The record becomes a living document that both you and an LLM can reason with: to notice patterns, propose next moves, and regenerate your setup on new tools when the current ones die.

The durable layer is the throughlines and the record. The tools are ephemeral.

## Vocabulary

A small kit of plain-English terms used throughout:

**Throughline** — something that persists across your changing setups. A value, a preference, a way of operating. You discover throughlines by living; you name them once you notice them.

**Setup** — your current bounded configuration: tools, arrangements, workflows. "My current setup uses Tana and manual scanning." Setups change; throughlines persist.

**Unfolding** — a small move that changes a setup. Reversible by design. Each unfolding is recorded with what prompted it, what's changing, what's staying, the smallest version to try, and what would make you back off.

**The record** — the accumulated log of unfoldings. Grows at the same tempo as your practice. Both you and an LLM read it to reason about what to do next.

**Reflecting** — looking back across the record to see what's happening. You do it; Claude does it. The output is noticing.

**Noticing** — catching a pattern while reflecting. "I've reversed every automation-of-approval move within two weeks" is a noticing.

**Taking stock** — a larger, deliberate reflection at a chosen cadence. A monthly rather than a daily thing.

**Backing off** — reversing an unfolding. Returns you to a prior setup. Not a failure; a data point.

**Pattern** — a recurring shape of unfolding that you've named (*shadow-run*, *confirm-before-create*, *context-attach*). Patterns accumulate into a personal vocabulary that makes future unfoldings faster to propose and easier to reason about.

## Characteristics

Eight things worth expanding (each will become its own section as the thinking develops):

1. **The record is generative in both directions.** Forward, it helps propose the next unfolding. Backward, it lets you reconstruct a prior setup.

2. **The unit is the unfolding, not the state.** The current setup is derivable from the sequence of unfoldings. What's durable is the moves and their rationales.

3. **Reversibility is a property of the move.** Every unfolding has a built-in rollback trigger — not just "how do I undo this" but "what would tell me I should."

4. **The LLM proposes candidate next unfoldings from the record.** Given the accumulated moves, preferences, and tempo, Claude suggests coherent small moves. The human picks, adapts, or discards.

5. **The LLM notices patterns the individual might miss.** Reading the full record enables reflection that's hard to do from memory alone.

6. **Malleable software is the substrate.** Unfoldings can stay small only if the tools underneath them are under your control. Vendor-locked tools force bigger, rarer, less reversible moves.

7. **Personal patterns accumulate into a pattern language.** Over time, recurring unfolding shapes get named and become reusable vocabulary.

8. **Throughlines plus record are durable; tools are ephemeral.** If Tana dies, the throughlines and record let you and an LLM regenerate an equivalent setup on new substrates — possibly better, because everything you learned is captured.

## What this isn't

Not a project management framework. Not a productivity system. Not a plan for someone else to execute. Not a finished artifact.

It's an attempt at a specification form that serves an individual's slow, self-paced migration from their current way of working to something better — keeping the human in the loop, keeping reversibility as a first-class property, and keeping the durable layer portable across tool deaths.

## Lineage

A few threads this draws from:

- **Phoenix Architecture** (Chad Fowler) — the durable/ephemeral split, with durable specs regenerating ephemeral implementations.
- **Christopher Alexander** — pattern languages, unfolding step by step, the inhabitant as authority on cadence. Adapted here to be just-in-time rather than batched.
- **Malleable software** (Geoffrey Litt, Ink & Switch, local-first) — the substrate assumption that makes small unfoldings possible.
- **Ship of Theseus** — persistence through incremental replacement, stated in plain English via throughlines.
- **Stanislavski's throughline** (origin of the word) — a thread that makes a succession of moments one continuous thing.
- **Context graphs** (Foundation Capital, Jaya Gupta and Ashu Garg, and the broader discussion they kicked off) — the insight that decision traces are the durable layer that makes AI actually useful, taken here and inverted: from institutional memory for enterprises to personal memory for individuals, with the individual rather than the company owning the graph.

## Status

Early. Much of this is still being worked out. The repo is the durable record of the thinking itself — written so that it can be revised, extended, and partially retracted as the ideas develop.

Contributions welcome once the shape is clearer. For now, issues and discussions are the right place to push on any of this.

## License

The specifications, documentation, and all content in this repository are
licensed under the Creative Commons Attribution-ShareAlike 4.0 International
License (CC BY-SA 4.0). See [LICENSE](./LICENSE) for the full text and
[ATTRIBUTION.md](./ATTRIBUTION.md) for citation and authorship.

Any implementation, derivative specification, or generated code derived from
this work must preserve attribution to this repository and be made publicly
available under CC BY-SA 4.0 or a compatible license. For software
implementations, this includes GPLv3 (explicitly one-way compatible with
CC BY-SA 4.0 per the [CC BY-SA 4.0 compatibility provisions](https://creativecommons.org/compatiblelicenses))
and GPLv3-derived licenses such as AGPLv3.
