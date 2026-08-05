# Progress

<!-- STATE BLOCK: machine-readable. Tutors read this first. Update every session. -->

```yaml
session: 1
week: 1
day: 1
mode: teach-then-test
lane_a_pattern: "Python fluency (day 1 of 2)"
lane_b_topic: "Next-token prediction, cross-entropy, perplexity — covered"
started: 2026-08-04
last_session_date: 2026-08-05
next_action: "Session 2 — W1D2: tokenization & BPE. Lane A: Python fluency day 2 (re-test all 8 items cold). Cross-entropy ELI5 rewrite is due."
mastery_counts: { L0: 141, L1: 3, L2: 4, L3: 0, L4: 0 }
problems_solved: 0
mocks_completed: 0
builds_completed: 0
eli5_passed: 0
calibration: "14 items. 9 blanks, 3 partials, 1 wrong-direction, 1 right-pattern-failed-execution. No compression available anywhere — 26-week plan is tight, not generous."
s1_finding: "Architectural scaffold absent, not just details — corrected S0's 'knows territory, missing details' read. Python fluency 1/8. But: computed perplexity correctly from machinery given 10 min earlier, and reached the cross-entropy core idea after one hint. Reasoning is sound where knowledge exists. Articulation is the new bottleneck — ELI5 failed on a concept demonstrably understood."
```

---

## How to read this file

- **State block above** — the current position. Bump it every session.
- **Mastery table below** — one row per concept, `L0`–`L4` per `TUTOR.md` §7.
  **Nothing advances out of a week below L3.** `L4` requires a passing ELI5 (grade 2).
- **Session log** — one line per session, appended.
- **Mock history** — scorecard results, so trends are visible rather than felt.

All 148 concepts start at **L0**. Session 0 calibration sets real starting levels.

---

## Mastery table

### AI/LLM fundamentals (W1–6)

| Concept | L | ELI5 | Notes |
|---|---|---|---|
| Next-token prediction & cross-entropy | 2 | 1 ✗ | S1: computed correctly, reached the core idea after one hint. ELI5 grade 1 — dropped the comparison and the "by a lot". Missed irreducible entropy unprompted. |
| Perplexity | 2 | — | S1: "effective number of options" understood and applied correctly. |
| Irreducible entropy / loss floor | 1 | — | S1: taught, not yet tested. Blocks correct perplexity comparison. |
| BPE tokenization | 0 | — | |
| Token-boundary failure modes | 0 | — | |
| Non-English token cost | 0 | — | |
| Embeddings / learned vector space | 0 | — | |
| Distributional semantics | 0 | — | |
| Cosine vs dot vs Euclidean | 0 | — | |
| Matmul as transformation | 0 | — | |
| Shape tracking discipline | 0 | — | |
| Scaling laws | 0 | — | |
| "Emergence" — what it does/doesn't mean | 0 | — | |
| Attention derived (Q/K/V) | 0 | — | |
| Scaled dot-product — why the scale | 0 | — | |
| Softmax's role in attention | 0 | — | |
| Reading an attention matrix | 0 | — | |
| Multi-head attention | 0 | — | |
| Head dimension arithmetic | 0 | — | |
| Permutation invariance problem | 0 | — | |
| Positional encoding: absolute → learned | 0 | — | |
| RoPE | 0 | — | |
| Residual stream | 0 | — | |
| Pre- vs post-LayerNorm | 0 | — | |
| FFN / MLP block | 0 | — | |
| Full forward pass, shapes end to end | 0 | — | |
| Causal masking | 0 | — | |
| Encoder vs decoder vs enc-dec | 0 | — | |
| Pretraining data: dedup, contamination | 0 | — | |
| AdamW | 0 | — | |
| LR schedules & warmup | 0 | — | |
| Gradient clipping | 0 | — | |
| Gradient accumulation | 0 | — | |
| Mixed precision | 0 | — | |
| Reading loss curves | 0 | — | |
| Loss spikes & divergence | 0 | — | |
| KV cache derived from causal mask | 0 | — | |
| KV cache memory arithmetic | 0 | — | |
| Prefill vs decode | 0 | — | |
| TTFT vs TPOT vs throughput | 0 | — | |
| Greedy / temperature / top-k / top-p / min-p | 0 | — | |
| Beam search & why it lost | 0 | — | |
| Context window cost & quadratic attention | 0 | — | |
| Long-context degradation & position bias | 0 | — | |
| Quantization intuition | 0 | — | |
| Prompting: structured output | 0 | — | |
| Prompting: decomposition | 0 | — | |
| Prompting: context construction | 0 | — | |
| Few-shot mechanics & order effects | 0 | — | |
| What's obsolete on reasoning models | 0 | — | |
| Prompt regression testing | 0 | — | |
| Parametric vs non-parametric knowledge | 0 | — | |
| Chunking tradeoff surface | 0 | — | |
| Embedding model selection | 0 | — | |
| Asymmetric query/doc embedding | 0 | — | |
| HNSW | 0 | — | |
| IVF | 0 | — | |
| Product quantization | 0 | — | |
| BM25 & hybrid retrieval | 0 | — | |
| Cross-encoder vs bi-encoder reranking | 0 | — | |
| Query rewriting / HyDE | 0 | — | |
| Retrieval failure taxonomy | 1 | — | S0: named prompt assembly as one branch. Missing position bias, conflicting chunks, multi-hop, parametric override. |
| Grounding & citations | 0 | — | |
| Hallucination despite retrieval | 0 | — | |
| recall@k / MRR / NDCG | 0 | — | |
| Adaptation decision framework | 2 | — | S0: reached staleness as the deciding factor unprompted. Sound instinct, incomplete framework. |
| LoRA mechanics | 0 | — | |
| SFT vs DPO vs RLHF | 0 | — | |
| Distillation | 0 | — | |
| What fine-tuning fixes badly | 0 | — | |
| LLM-as-judge biases | 0 | — | |
| Eval harness design | 0 | — | |
| Prompt injection (direct & indirect) | 0 | — | |
| Data exfiltration paths | 0 | — | |
| PII handling | 0 | — | |
| Jailbreak taxonomy | 0 | — | |

### System design fundamentals (W7–10)

| Concept | L | ELI5 | Notes |
|---|---|---|---|
| 7-step interview loop | 0 | — | |
| Latency numbers | 0 | — | |
| Back-of-envelope estimation | 0 | — | |
| Functional vs non-functional requirements | 0 | — | |
| Vertical vs horizontal scaling | 0 | — | |
| Load balancing L4 vs L7 | 0 | — | |
| LB algorithms & health checks | 0 | — | |
| Statelessness | 0 | — | |
| DNS resolution & TTLs | 0 | — | |
| CDN mechanics & invalidation | 0 | — | |
| B-trees & index internals | 0 | — | |
| Clustered vs covering indexes | 0 | — | |
| Query plans | 0 | — | |
| ACID | 0 | — | |
| Isolation levels & their anomalies | 0 | — | |
| Replication: sync vs async, lag | 0 | — | |
| Read-your-writes / monotonic reads | 0 | — | |
| Connection pooling | 0 | — | |
| Multi-leader & conflict resolution | 0 | — | |
| Cache patterns (aside/through/behind) | 0 | — | |
| Eviction policies | 0 | — | |
| Cache invalidation | 0 | — | |
| Thundering herd / stampede | 0 | — | |
| Hot keys | 0 | — | |
| Sharding strategies | 0 | — | |
| Consistent hashing derived | 0 | — | |
| Virtual nodes & rebalancing | 0 | — | |
| Celebrity / hot-shard problem | 0 | — | |
| HTTP/1.1 vs 2 vs 3, QUIC | 0 | — | |
| TLS handshake & mTLS | 0 | — | |
| REST vs gRPC vs GraphQL | 0 | — | |
| Idempotency keys | 0 | — | |
| Pagination: offset vs cursor | 0 | — | |
| Rate limiting algorithms | 0 | — | |
| API gateway & auth patterns | 0 | — | |
| Webhook delivery guarantees | 0 | — | |

### Distributed systems (W11–14)

| Concept | L | ELI5 | Notes |
|---|---|---|---|
| CAP stated precisely | 0 | — | |
| PACELC | 0 | — | |
| Linearizability | 0 | — | |
| Sequential / causal / eventual consistency | 0 | — | |
| Quorums, R+W>N | 0 | — | |
| Sloppy quorum & hinted handoff | 0 | — | |
| Why wall clocks lie | 0 | — | |
| Logical & vector clocks | 0 | — | |
| Raft election & log replication | 0 | — | |
| Paxos intuition | 0 | — | |
| Split brain & fencing tokens | 0 | — | |
| Queues vs logs | 0 | — | |
| Kafka: partitions, offsets, consumer groups | 0 | — | |
| ISR & retention | 0 | — | |
| Delivery semantics & "exactly-once" | 0 | — | |
| Ordering guarantees & partition keys | 0 | — | |
| Backpressure & consumer lag | 0 | — | |
| DLQs & poison messages | 0 | — | |
| Transactional outbox | 0 | — | |
| CDC & the dual-write problem | 0 | — | |
| LSM vs B-tree amplification | 0 | — | |
| SSTables & compaction strategies | 0 | — | |
| WAL | 0 | — | |
| Bloom filters | 0 | — | |
| HLL & count-min sketch | 0 | — | |
| NoSQL families | 0 | — | |
| Dynamo- vs Bigtable-style | 0 | — | |
| MapReduce → Spark, shuffle, skew | 0 | — | |
| Event vs processing time, watermarks | 0 | — | |
| Windowing; Lambda vs Kappa | 0 | — | |
| Failure taxonomy & gray failure | 0 | — | |
| Retries, backoff, jitter | 2 | — | S0: got retry amplification. Missing jitter/storms/circuit breakers/budgets. |
| Circuit breakers & bulkheads | 0 | — | |
| Load shedding & degradation | 0 | — | |
| 2PC vs sagas | 0 | — | |
| Observability: metrics/logs/traces | 0 | — | |
| SLI/SLO/error budgets | 0 | — | |
| Capacity planning | 0 | — | |
| Deploy strategies | 0 | — | |

### ML (W18–22)

| Concept | L | ELI5 | Notes |
|---|---|---|---|
| Supervised framing / not-an-ML-problem | 0 | — | |
| Train/val/test discipline | 0 | — | |
| Data leakage | 0 | — | |
| Bias–variance & regularization | 0 | — | |
| Class imbalance handling | 0 | — | |
| Precision/recall/F1 | 0 | — | |
| ROC-AUC vs PR-AUC | 0 | — | |
| NDCG | 0 | — | |
| Calibration | 0 | — | |
| Business goal → metric mapping | 1 | — | S0: knew to interrogate the number, asked about dataset sizes rather than base rate. Right instinct, wrong question. |
| Trees / GBDT | 0 | — | |
| Representation learning | 0 | — | |
| Contrastive objectives & hard negatives | 0 | — | |
| Two-tower retrieval | 0 | — | |
| Transfer learning (pre-LLM sense) | 0 | — | |
| What changed 2020→2026 | 0 | — | |
| Business goal → ML problem framing | 0 | — | |
| Offline metrics that predict online | 0 | — | |
| Guardrail metrics & proxy traps | 0 | — | |
| Labeling strategies | 0 | — | |
| Position bias in implicit feedback | 0 | — | |
| Train/serve skew | 0 | — | |
| Feature stores | 0 | — | |
| Point-in-time correctness | 0 | — | |
| Batch vs streaming features | 0 | — | |
| Retrieval + ranking two-stage | 0 | — | |
| Model registry & versioning | 0 | — | |
| Shadow / canary / A-B / interleaving | 0 | — | |
| Drift (data, concept, label) | 0 | — | |
| Degenerate feedback loops | 0 | — | |
| Cold start | 0 | — | |

### GenAI system design (W23–25)

| Concept | L | ELI5 | Notes |
|---|---|---|---|
| LLM serving architecture | 0 | — | |
| Continuous batching | 0 | — | |
| Paged attention & KV-cache management | 0 | — | |
| GPU memory math → max concurrency | 0 | — | |
| Tensor / pipeline / expert parallelism | 0 | — | |
| GPU autoscaling & cold starts | 0 | — | |
| Cost per million tokens | 0 | — | |
| Model routing & cascades | 0 | — | |
| Semantic caching | 0 | — | |
| Multi-tenancy & noisy neighbors | 0 | — | |
| Production RAG: ingest/index/serve | 0 | — | |
| Index freshness & incremental update | 0 | — | |
| Permissions-aware retrieval | 0 | — | |
| Agent orchestration & termination | 0 | — | |
| Idempotency for non-deterministic steps | 0 | — | |
| Memory tiers | 0 | — | |
| Context budgeting | 0 | — | |
| Tool sandboxing | 0 | — | |
| Injection as a design constraint | 0 | — | |
| Guardrail placement | 0 | — | |

---

## Session log

| # | Date | W/D | Lane A | Lane B | Outcome |
|---|---|---|---|---|---|
| 0 | 2026-08-04 | W0D0 | 2 problems, both failed | Calibration, 12 diagnostics | 9 blanks, 3 partials, 1 wrong-direction, 1 right-pattern-failed-execution. No compression available. AI-first ordering confirmed. Added Python fluency prepend to W1 Lane A + mandatory constraint restatement. 13 weak spots logged. |
| 1 | 2026-08-05 | W1D1 | Python fluency 1/8 | Next-token prediction, cross-entropy, perplexity | Recall 5 due: 1 partial, 3 blank, 1 skipped, R5 code-reading 2.5/4 (found a planted bug). Lane B: both closing questions answered correctly — first computation from newly-taught machinery. ELI5 grade 1, did not pass. **Finding: architectural scaffold absent; articulation is now the bottleneck, not comprehension.** |

---

## Mock history

| # | Session | Track | Problem | Scores | Takeaway |
|---|---|---|---|---|---|
| — | — | — | — | — | *No mocks yet.* |

---

## Build status

| Build | Week | Status | Acceptance |
|---|---|---|---|
| 01 mini-GPT | W3 | not started | Samples coherent-ish text |
| 02 eval harness + LLM-as-judge | W6 | not started | Reproducible scores across two runs |
| 03 LoRA fine-tune | W6→W7 | not started | Measured before/after delta on held-out set |
