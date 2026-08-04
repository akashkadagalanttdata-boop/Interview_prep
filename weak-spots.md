# Weak Spots

**The most valuable file in this repo.** Everything you got wrong, every intuition that turned
out backwards, every unresolved conflict between sources.

Errors are higher-signal review material than correct answers, because they mark the exact
boundary of what you actually know. Keep this file honest and keep it uncomfortable — a short
weak-spots file usually means a lenient tutor, not a strong learner.

## Rules

- Every error goes in, including small ones, including ones you'd rather not write down.
- An entry is removed **only** after being re-tested cold and correct in a later session.
  Not after re-reading it. Not after nodding along to an explanation.
- **Source conflicts go here too.** When your reading material and the tutor disagree, log it
  and resolve it from first principles in-session (`TUTOR.md` §5.6). Do not settle for "both
  views are valid" — these moments are the highest-value learning in the program.
- Recurring entries (same concept missed 3+ times) get flagged `RECURRING` and reviewed for a
  broken mental model rather than a memory gap. Repeatedly forgetting one thing usually means
  something upstream of it is wrong.

---

## Open

| # | Session | Concept | What went wrong | Type | Re-tested |
|---|---|---|---|---|---|
| 1 | 0 | Tokenization → letter-level tasks | No mechanism for why models can't count letters. Doesn't know the model never sees characters. | gap | — |
| 2 | 0 | Scaled dot-product — the √d_k term | Blank. Core W2 material. | gap | — |
| 3 | 0 | KV cache correctness | Blank. Didn't connect cache validity to causal masking. | gap | — |
| 4 | 0 | Retrieval failure taxonomy | Named prompt assembly only. Missing position bias, conflicting chunks, multi-hop, parametric override. | gap | — |
| 5 | 0 | Cosine vs dot product | Blank. Doesn't know they coincide under normalization. | gap | — |
| 6 | 0 | `hash(key) % N` resharding | Blank. Didn't know ~80% of keys remap, or that the consequence is a cache-miss stampede. | gap | — |
| 7 | 0 | Isolation level anomalies | Blank. No model of what each level still permits. | gap | — |
| 8 | 0 | LSM vs B-tree | Blank. No model of sequential-vs-random write conversion. | gap | — |
| 9 | 0 | Class imbalance & metric choice | 99.2% accuracy on fraud didn't trigger base-rate suspicion. Asked about dataset sizes instead. **Blocks Build #2 (W6) — eval harness needs this.** | model | — |
| 10 | 0 | Data leakage | Blank. Can't name a plausible instance. | gap | — |
| 11 | 0 | **Python mechanics** | 3 errors in 12 lines: `len(text)` not `len(text)-1`; `for` where `while` belongs; `lower(x)` not `x.lower()`. Will bottleneck Lane A on syntax instead of patterns. | `RECURRING`-risk | — |
| 12 | 0 | **Reading constraints fully** | Problem A ignored the alphanumeric-filtering requirement — the actual substance of the problem. Same error class as the off-by-one: skimming the spec. | model | — |
| 13 | 0 | Sliding window | Blank. W2 Lane A material. | gap | — |

**Type:** `error` (got it wrong) · `gap` (didn't know it existed) · `model` (wrong mental
model, not a fact) · `conflict` (source disagreement) · `articulation` (knew it, explained it
badly — costs real interview points)

---

## Resolved

| Concept | Opened | Resolved | How it was fixed |
|---|---|---|---|
| — | — | — | — |
