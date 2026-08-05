# Next-token prediction, cross-entropy, perplexity

**Session:** 1 · **Week/Day:** W1D1 · **Level reached:** L2

> Scaffolded by the tutor with the scope covered. **The recall sections marked `TODO` are yours
> to write** — from memory, notes closed, per `TUTOR.md` §3. A tutor-written note teaches
> nothing; the writing is the mechanism.

---

## The one-sentence version
A language model is a function that takes a sequence and returns how likely every possible next
token is — and training is just making the token that actually came next more likely.

## Why it exists
You need labelled data to train a predictor, and labelling is expensive. Next-token prediction
is **self-supervised**: cut any sentence at any position and the next word is a free label.
Ordinary text is already the dataset. That's why the internet was enough.

## How it works

**The black box.** Sequence of tokens in → a probability distribution over the whole vocabulary
out. Generation is: sample one, append, feed back, repeat. Everything else in this program is
either *how the box computes that distribution* (W2 — transformer internals) or *how you pick
from it* (W4 — decoding).

**Cross-entropy.** `−log(p)`, where `p` is the probability assigned to the token that actually
appeared.

| model said | −log(p) | |
|---|---|---|
| p = 1.0 | 0 | perfect |
| p = 0.5 | 0.69 | mild |
| p = 0.01 | 4.6 | painful |
| p → 0 | → ∞ | **confidently wrong is unboundedly expensive** |

The asymmetry is the design: hedging is penalized gently, certainty-and-wrong enormously.
Cross-entropy trains *calibration*, not just accuracy.

**Perplexity.** `e^(cross-entropy)` — the same information in interpretable units: **the
effective number of options the model was choosing between.** Cross-entropy 4.6 → perplexity
≈ 100, i.e. as confused as picking uniformly among 100 tokens.

## Irreducible entropy — the part I missed in session

"The capital of France is ___" has one answer. "My favourite colour is ___" has a dozen. The
second isn't a worse prediction; **the world is genuinely more uncertain there.** A model
answering `blue: 0.9` would be *worse* — confidently asserting the unknowable.

Three consequences:

1. Loss never reaches zero. A model approaching zero on real text is memorizing.
2. **Perplexity is only comparable on identical test sets.** Perplexity 12 on children's books
   and 12 on legal contracts are different achievements — different floors.
3. Low confidence is sometimes the *correct* output. → forward to calibration (W18) and to the
   eval harness (Build #2, W6), where "unsure" and "wrong" must score differently.

## Shapes / numbers
`TODO` — write out: vocab size, what the output vector's shape is, and what it sums to.

## ELI5
**Banned words:** entropy, cross-entropy, probability, distribution, logarithm, loss, token,
model, penalty, score
**Grade: 1 — did not pass.**

> Attempt 1 (S1): described one wrong forecast, but dropped the *comparison* and the *"by a
> lot."* A reader learns a weatherman was wrong, not that confidence changes the cost of being
> wrong.

`TODO` — rewrite at session 2. Say it aloud first; the spoken version was better than the
written one.

## Where this shows up in my actual work
`TODO` — answered "perplexity" in session, one word. Expand: *why* would knowing perplexity a
year ago have changed something you did?

## Open questions
`TODO`

## Links
[[02-tokenization]] · [[eli5-glossary]] · forward to W2 attention, W4 decoding, W18 calibration
