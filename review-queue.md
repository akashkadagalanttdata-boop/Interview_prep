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
| — | — | — | *Empty. Session 0 seeds this.* |

---

## Cleared (past +80)

| Concept | Cleared at session | Final level |
|---|---|---|
| — | — | — |
