# Build #3 — LoRA fine-tune with before/after eval

**Week 6 Days 6–7, spilling into Week 7 Day 7 · ~5 hours**

> The spill into W7's consolidation day is planned, not slippage. Two builds don't fit in one
> week alongside W6's concept load, and pretending otherwise is how study plans quietly fail
> in month two.

## Why this build exists

To make the **prompting vs RAG vs fine-tuning decision** concrete instead of theoretical.

Almost everyone in AI engineering has an opinion about when to fine-tune. Far fewer have
fine-tuned something, measured it honestly, and watched it fail to fix the thing they hoped it
would fix. That experience is what turns W6 Day 1's decision framework from a table you read
into judgment you have.

The specific lesson you're buying: **fine-tuning shapes behavior and format well, and teaches
new knowledge badly.** You'll believe that much more firmly after measuring it than after
reading it here.

## Scope

LoRA/SFT on a small open model, on a narrow task. Small is the point — this is about the
measurement loop, not the model.

Pick a task where you have or can build ~100–500 examples. Ideally something where you can
*also* try a prompting-only solution, so the comparison is real.

## Stages

| # | Stage | Notes |
|---|---|---|
| 1 | **Baseline first** | Evaluate the base model on your held-out set *before* touching training. Skipping this makes everything after it unfalsifiable. |
| 2 | Prompting-only attempt | Your actual competition. Sometimes it wins, and that's a result worth having. |
| 3 | Dataset prep | Format, split, hold out. Check for leakage — W18 arrives early here. |
| 4 | LoRA train | Rank, alpha, target modules, LR. Note what you chose and why. |
| 5 | Evaluate | Same held-out set, same harness from Build #2. Reuse it; don't write a second one. |
| 6 | Probe the limits | Try to make it answer something factual it wasn't trained on. Watch what happens. |

## Acceptance

- [ ] Baseline measured **before** training
- [ ] Training runs and loss decreases
- [ ] **Measured before/after delta on a held-out set** — a number, with the eval method stated
- [ ] Prompting-only baseline measured for comparison
- [ ] Written answer: what did fine-tuning fix, and what did it fail to fix?

A build with no measured delta doesn't count as complete. "It seems better" is the thing this
build exists to make impossible for you to say again.

## Dependencies

```
torch
transformers
peft
datasets
accelerate
```

Plus the eval harness from Build #2 — reuse it deliberately.

## Rules

- **No weights, checkpoints, adapters, or datasets committed.** See `.gitignore`. Adapters are
  small enough to be tempting; still no.
- Track hyperparameters in a file so the run is reproducible.
- If the fine-tune loses to prompting, **write that down as the result.** A negative result you
  measured is worth more than a positive one you assumed.

## Debrief

**What fine-tuning fixed:**

**What it failed to fix (and did I expect that?):**

**Prompting vs RAG vs fine-tuning — what would I now actually reach for first, and when:**

**What this cost in time and compute, vs what I'd budget next time:**
