# Review Queue

Spaced repetition, **indexed by session count — not calendar date**. A skipped week never
silently expires the queue; if you return at session 31, everything due at ≤31 is due.

## The rule

When a concept is touched, schedule it at the current session **+1, +3, +7, +16, +35, +80**.

| Outcome at review | Action |
|---|---|
| Recalled correctly | advance to the next interval in the chain |
| **Missed** | **reset to +1** and restart the chain from the beginning |

A concept leaves the queue after clearing **+80**, at which point it should be L4 with a
passing ELI5 (`TUTOR.md` §7). If it isn't, it does not leave — keep it cycling.

Cold recall means **notes closed**. Reading the answer is recognition, not retrieval, and
recognition is what makes people feel prepared while failing interviews.

---

## Due

| Due at session | Concept | Chain position | Last outcome |
|---|---|---|---|
| 1 | Tokenization → letter-level failure | +1 | blank at S0 |
| 1 | Scaled dot-product, the √d_k term | +1 | blank at S0 |
| 1 | KV cache correctness ← causal mask | +1 | blank at S0 |
| 1 | Cosine vs dot product | +1 | blank at S0 |
| 1 | Python: `.lower()`, `while`, index bounds | +1 | 3 errors at S0 |
| 3 | Retrieval failure taxonomy | +3 | partial at S0 |
| 3 | Adaptation: fine-tune vs RAG | +3 | partial at S0 |
| 3 | Retry amplification | +3 | partial at S0 |
| 3 | Class imbalance & base rates | +3 | wrong direction at S0 |
| 7 | `hash(key) % N` resharding | +7 | blank at S0 |
| 7 | Isolation level anomalies | +7 | blank at S0 |
| 7 | LSM vs B-tree | +7 | blank at S0 |
| 7 | Data leakage | +7 | blank at S0 |
| 7 | **Re-solve Problem A from scratch** | +7 | failed at S0 |

---

## Cleared (past +80)

| Concept | Cleared at session | Final level |
|---|---|---|
| — | — | — |
