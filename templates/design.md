# Design: <System>

**Session:** <N> · **Week/Day:** W<W>D<D> · **Timed:** <yes/no, minutes> · **Track:** <SD / ML / GenAI>

> Follow the 7-step loop in order. The order *is* the skill — jumping to boxes-and-arrows
> before requirements is the most common way strong engineers lose design interviews.

---

## 1. Requirements
**Functional:**
-

**Non-functional** (each with a number, not an adjective):
- Scale:
- Latency:
- Availability:
- Consistency:

**Explicitly out of scope:**
-

## 2. Estimates
<QPS, storage, bandwidth, and the arithmetic that got you there. Show the work — an interviewer
scores the reasoning, not the number.>

- Read QPS / Write QPS / ratio:
- Storage per year:
- Bandwidth:
- Anything the numbers just ruled out:

## 3. API
<Endpoints or RPCs. Signatures, not prose. Note idempotency where it matters.>

## 4. Data model
<Entities, relationships, access patterns. Then the storage choice, **justified by the access
patterns** — not by preference.>

## 5. High-level architecture
<Components and data flow. Text is fine; ASCII is fine. Clarity over decoration.>

## 6. Deep dive
<The 1–2 components that actually make this problem interesting. This is where interviews are
won. Pick the hard part deliberately rather than being led to it.>

## 7. Bottlenecks & tradeoffs
| Bottleneck | At what scale it bites | Mitigation | What the mitigation costs |
|---|---|---|---|
| | | | |

**Failure modes:** <what breaks, how it's detected, how it degrades>

**What I'd do differently with 10× the scale:**

**What I'd do differently with 1/10th the budget:**

---

## Self-assessment
| Axis | 1–5 | Note |
|---|---|---|
| Requirements gathering | | |
| Estimation | | |
| Structure & order | | |
| Depth on the hard part | | |
| Tradeoff articulation | | |

**Where I stalled:**
**What I'd want to be asked again:**
