# Build #1 — mini-GPT from scratch

**Week 3, Days 4–6 · ~7 hours · You write the code; the tutor reviews and interrogates.**

## Why this build exists

You chose *"reason about it rigorously"* for transformer depth, not *"implement everything from
scratch."* This is the one exception — a single scoped project rather than the pedagogy for the
whole block.

The reason is narrow and specific: **shapes and gradients stay abstract until you've had them
wrong.** Reading that attention is `softmax(QKᵀ/√d)V` teaches you the formula. Getting a
shape mismatch at 11pm and having to reason out which axis you transposed teaches you the
mechanism. You need that once. After that, rigorous reasoning is enough.

## Scope — deliberately small

Not a competitive model. A character-level or small-BPE model on a small text corpus, trained
on whatever hardware you have (CPU is fine — a tiny model on a few MB of text is the point).

## Stages

| # | Stage | What you must be able to explain afterwards |
|---|---|---|
| 1 | Data + tokenizer | Why vocab size trades against sequence length |
| 2 | Single-head attention | Every shape in the forward pass, and why the scale factor is there |
| 3 | Multi-head | Why heads split the embedding dim rather than duplicating it |
| 4 | Full block | Where the residual connections attach, and what breaks without them |
| 5 | Training loop | What the loss curve is telling you, batch by batch |
| 6 | Sampling | How temperature and top-k change the output, demonstrated not asserted |

## Acceptance

- [ ] Model trains without shape errors **that you can't explain**
- [ ] Loss decreases and you can read the curve
- [ ] Sampled text is coherent-ish (locally plausible, globally nonsense is fine)
- [ ] **You can hand-derive every shape in the forward pass with the code closed**

The last box is the actual deliverable. The code is a by-product.

## Dependencies

```
torch
numpy
```

That's intentional — no HuggingFace, no Lightning. Frameworks hide exactly the parts this
build exists to expose.

## Rules

- **Write it yourself.** The tutor reviews, questions, and points at bugs; it does not hand you
  working code. If you get stuck for more than ~20 minutes, ask for a hint at level 1 or 2
  (`TUTOR.md` §4) — not the answer.
- **No checkpoints or datasets committed.** See `.gitignore`.
- When you finish, write the debrief below. The list of things that surprised you is the real
  output of this build.

## Debrief

**What surprised me:**

**What I had wrong before starting:**

**Which shape I got wrong most often, and why:**
