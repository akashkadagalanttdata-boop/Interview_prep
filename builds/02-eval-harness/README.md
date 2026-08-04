# Build #2 — Eval harness + LLM-as-judge

**Week 6, Days 3–4 · ~5 hours**

## Why this build exists

Two reasons, both practical.

**It's directly job-relevant and rare.** Most engineers using LLMs in production have no real
eval story — they ship on vibes and discover regressions from users. Being the person who can
build a defensible eval suite is disproportionately valuable.

**It covers the RAG build you declined.** You skipped the standalone "build a RAG pipeline and
break it" project, so **retrieval evaluation folds in here** instead. You'll measure recall@k
and NDCG on a real retrieval set, which forces the W5 concepts to become concrete rather than
staying theoretical.

## Scope

An eval harness for a task you actually care about — ideally something adjacent to your day
job. Two halves:

**Half A — deterministic evals**
Exact match, regex/schema validation, structured-output conformance, latency and cost tracking.
The boring half. It catches more real regressions than the interesting half.

**Half B — LLM-as-judge, and its failure modes**
Build the judge, then deliberately find where it lies to you:

| Bias | How to demonstrate it |
|---|---|
| Position bias | Swap A/B order on identical pairs; measure the flip rate |
| Verbosity bias | Pad a worse answer with correct-but-redundant text; watch the score rise |
| Self-preference | Have a model judge its own output vs another model's |
| Score compression | Check whether the judge ever actually uses the bottom of its scale |

**Half C — retrieval eval (folded in from the declined RAG build)**
Build a small labelled retrieval set. Measure recall@k, MRR, NDCG. Then degrade one stage at a
time — chunk size, embedding model, reranker on/off — and watch which metric moves. That
mapping from *symptom* to *broken stage* is the W5 retrieval failure taxonomy, learned the way
it sticks.

## Acceptance

- [ ] Suite runs end to end from one command
- [ ] **Reproducible: two runs on identical inputs give the same scores** (or you can explain
      precisely why not, and have bounded the variance)
- [ ] At least one judge bias demonstrated with numbers, not asserted
- [ ] Retrieval metrics computed on your own labelled set
- [ ] One degradation experiment showing which metric detects which broken stage

## Dependencies

```
# an LLM client for whichever provider you have access to
pydantic          # structured output validation
numpy
```

Keep it provider-agnostic where you reasonably can — this repo outlives any one vendor, which
is a theme.

## Rules

- **No API keys committed.** Use `.env`; it's gitignored.
- Log costs as you go. Eval suites get expensive quietly, and knowing the number is part of the
  skill.
- Small labelled sets beat large unlabelled ones. 50 well-chosen examples with real labels are
  worth more than 5,000 generated ones.

## Debrief

**Where the judge misled me:**

**Which retrieval degradation was hardest to detect, and why:**

**What I'd now insist on before shipping any LLM feature:**
