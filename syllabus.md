# Syllabus — 26 Weeks, Day Level

**1.5 hr/day · 7 days/week · ~273 hours.** Lane A = coding (30 min). Lane B = concepts (60 min).

`D7` of every week is **consolidation**: no new material. Clear the review backlog, run the
mock, or advance a build.

Modes are defined in `TUTOR.md` §4. **Nothing advances out of a week below L3** (`TUTOR.md` §7).

> ## Session 0 calibration result (2026-08-04)
>
> 14 items: **9 blanks, 3 partials, 1 wrong-direction, 1 right-pattern-failed-execution.**
>
> **No compression is available anywhere.** The plan was written expecting some topics to be at
> L3 already and to free hours for the design-first weeks. Nothing was. The 26 weeks are tight,
> not generous — treat the Day-7 consolidation slots as real capacity, not slack.
>
> **Two changes, both narrow:**
>
> 1. **Lane A gets a Python fluency prepend in W1 D1–2, before the first two-pointer problem.**
>    Three mechanical errors in twelve lines (`len(text)` vs `len(text)-1`, `for` where `while`
>    belongs, `lower(x)` vs `x.lower()`) means the coding lane would otherwise spend six months
>    bottlenecked on syntax while trying to teach pattern recognition. Fix the substrate first.
> 2. **Constraint restatement is now mandatory in Lane A.** Problem A's approach was correct and
>    its implementation ignored the alphanumeric filter — the actual substance of the question.
>    That's the same error class as the off-by-one. From Session 1: restate the constraints in
>    your own words *before* stating the approach. Two extra sentences, and it addresses the
>    failure mode that cost the most in calibration.
>
> **What calibration did not change:** the AI-first ordering is confirmed correct. Q1–Q3
> (tokenization, the √d_k term, KV-cache validity) were all blanks, and they are W1, W2, and W4
> material respectively. **Where answers did come, the reasoning was sound** — staleness as the
> deciding factor on fine-tune-vs-RAG, retry amplification under load. That distinction matters
> for how to run the program: this is a knowledge gap, not a reasoning gap, which is why
> teach-then-test is the right opening mode and why socratic can start on schedule in W2 rather
> than being deferred.
>
> **One dependency to watch:** weak-spot #9 (class imbalance and base rates) is W18 material but
> **Build #2 in W6 needs it** — you can't design an eval harness without knowing why 99.2%
> accuracy can be worthless. Cover it inline during W6 D3 rather than moving the whole ML block.

---

# PART I · AI/LLM FUNDAMENTALS (W1–6)

Front-loaded because it's job-critical, and because it has almost no dependency on the
system-design track. Teaching mode is **rigorous reasoning**: derive shapes, explain every
component, debug real models. Three scoped builds anchor it.

## Week 1 · Tokens to embeddings · *teach-then-test*
**Lane A:** **Python fluency (D1–2, added post-calibration)**, then two pointers (D3–7)

| D | Lane B |
|---|---|
| 1 | What a language model actually optimizes: next-token prediction, cross-entropy, perplexity. Why this objective produces everything else. |
| 2 | Tokenization: BPE construction, vocab tradeoffs. Why token boundaries cause letter-counting failures, arithmetic weirdness, and a real cost penalty for non-English text. |
| 3 | Embeddings: what a learned vector space *is*. Distributional semantics. Why nearby ≠ synonymous. |
| 4 | Similarity metrics: cosine vs dot vs Euclidean. When each is wrong, and why normalization changes the answer. |
| 5 | Linear-algebra intuition, only as needed: matmul as transformation, batching, and **shapes as the thing you always track**. |
| 6 | Why scaling worked: parameters vs data vs compute, scaling-law intuition, what "emergence" does and doesn't mean. |
| 7 | Consolidation + **job hook**: where does tokenization actually bite you at work? |

## Week 2 · Transformer architecture, rigorously · *teach-then-test → socratic*
**Lane A:** sliding window

| D | Lane B |
|---|---|
| 1 | Attention **derived**, not presented. Start from "which earlier positions matter here?" and arrive at Q/K/V. Why scaled dot-product; what breaks without the scale factor. |
| 2 | Softmax's role. Attention as soft lookup. Reading an attention matrix; what sharp vs diffuse rows mean. |
| 3 | Multi-head attention: why several heads beat one big one. What heads specialize in. Head dimension arithmetic. |
| 4 | Positional information: why attention alone is permutation-invariant. Absolute → learned → RoPE, and what RoPE buys for extrapolation. |
| 5 | The rest of the block: residual stream, pre- vs post-LayerNorm (and why pre- won), the FFN/MLP block and its width. |
| 6 | **Full forward pass, shapes traced end to end** for a real published config. Causal masking. Encoder vs decoder vs encoder-decoder, and which modern models are which. |
| 7 | Consolidation. **Deliverable:** hand-derived shape flow, no reference. **Mock: AI oral exam #1.** |

## Week 3 · Training + Build #1 · *teach-then-test*
**Lane A:** binary search, including binary-search-on-answer

| D | Lane B |
|---|---|
| 1 | Pretraining in practice: data sourcing, dedup, curriculum, contamination. Why data quality outranks architecture now. |
| 2 | Optimization: AdamW, LR schedules, warmup, gradient clipping, gradient accumulation, mixed precision. What each one prevents. |
| 3 | Reading loss curves: healthy vs diverging vs plateaued vs overfit. Loss spikes and what causes them. |
| 4–6 | **Build #1 — mini-GPT (~7 hr, scaffolded).** Tokenizer → attention → block → training loop → sampling. You write it; the tutor reviews and interrogates. Purpose: make shapes and gradients physical, once. |
| 7 | Build wrap: sample text must be coherent-ish. Debrief what surprised you — that list is the real output. |

## Week 4 · Inference internals + prompting core · *socratic*
**Lane A:** prefix sums + intervals

| D | Lane B |
|---|---|
| 1 | **KV cache derived from the causal mask** — why the cache is *possible*, not just useful. Memory cost arithmetic. |
| 2 | Prefill vs decode: two different workloads with different bottlenecks. TTFT vs TPOT vs throughput. Why batching helps one and hurts another. |
| 3 | Decoding strategies: greedy, temperature, top-k, top-p, min-p, beam search — and why beam lost for open-ended generation. |
| 4 | Context windows: what "128k context" actually costs, attention's quadratic term, long-context degradation and position bias. Quantization intuition (what precision buys and breaks). |
| 5 | **Prompting as engineering, part 1:** structured output, decomposition, context construction, few-shot mechanics and why order matters. |
| 6 | **Prompting part 2:** what's obsolete on modern reasoning models (and what isn't), prompt regression testing, failure taxonomy. Prompting is refined continuously from here on, not finished. |
| 7 | Consolidation + **job hook**: which of your current prompts are load-bearing and untested? |

## Week 5 · RAG, rigorously · *socratic*
**Lane A:** linked lists

| D | Lane B |
|---|---|
| 1 | Why RAG exists: parametric vs non-parametric knowledge. What RAG fixes, what it can't, and when fine-tuning is the wrong reach. |
| 2 | Chunking: the full tradeoff surface — size, overlap, semantic vs fixed, structure-aware. Why chunking is where most RAG quality is won or lost. |
| 3 | Embedding models: selection criteria, dimension tradeoffs, domain mismatch, asymmetric query/document embedding. |
| 4 | ANN algorithms: HNSW, IVF, PQ. **How each trades recall for latency and memory** — derive the tradeoff, don't memorize the names. |
| 5 | Hybrid retrieval: BM25 + dense, fusion strategies. Reranking: cross-encoder vs bi-encoder and why the distinction is the whole game. Query rewriting, HyDE. |
| 6 | **Retrieval failure taxonomy:** bad chunk vs bad embedding vs bad ranking vs bad synthesis — and how to diagnose which one you have. Grounding, citations, hallucination *despite* correct retrieval. Metrics: recall@k, MRR, NDCG. |
| 7 | Consolidation. **Mock: AI oral exam #2** (RAG diagnosis under questioning). |

## Week 6 · Adaptation, evals, safety + Builds #2–3 · *socratic*
**Lane A:** monotonic stack

| D | Lane B |
|---|---|
| 1 | **Decision framework:** prompting vs RAG vs SFT vs LoRA vs DPO/RLHF vs distillation, with cost/latency/data thresholds. What fine-tuning fixes well (style, format, refusal behavior) and badly (knowledge). |
| 2 | LoRA mechanics: why low-rank adaptation works, rank selection, what it can't reach. RLHF vs DPO intuition. |
| 3–4 | **Build #2 — eval harness + LLM-as-judge (~5 hr).** Build the suite, then find where the judge misleads: position bias, self-preference, verbosity bias. **Retrieval evaluation folds in here** — recall@k and NDCG on your own retrieval set. |
| 5 | Safety fundamentals: prompt injection, indirect injection, data exfiltration, PII handling, jailbreak taxonomy. Treated as design constraints, not a compliance checkbox. |
| 6–7 | **Build #3 — LoRA fine-tune with before/after eval (~5 hr).** Measured delta on a held-out set or it doesn't count. **Spills into W7 D7 by design.** **Mock: AI oral exam #3.** |

---

# PART II · SYSTEM DESIGN FUNDAMENTALS (W7–10)

The **7-step interview loop** — requirements → estimates → API → data model → high-level →
deep dive → bottlenecks/tradeoffs — is drilled from W7 D1 so it's reflex by W15.

## Week 7 · Scale foundations · *teach-then-test*
**Lane A:** heaps / top-k · *(W6 Build #3 finishes on D7)*

| D | Lane B |
|---|---|
| 1 | The 7-step interview loop itself. Latency numbers worth knowing. Requirements: functional vs non-functional, and how to scope out loud. |
| 2 | Back-of-envelope estimation: QPS, storage, bandwidth. Practice until the arithmetic stops being the hard part. |
| 3 | Single server → scale out. Vertical vs horizontal, and the honest case for vertical. |
| 4 | Load balancing: L4 vs L7, algorithms, health checks, sticky sessions and why they're a smell. |
| 5 | **Statelessness as the precondition for everything else.** Where state actually has to live. |
| 6 | DNS and CDN mechanics: resolution path, TTLs, anycast, edge caching, cache-control, invalidation. |
| 7 | Consolidation + first timed design walkthrough. |

## Week 8 · Data storage · *teach-then-test*
**Lane A:** tree BFS/DFS

| D | Lane B |
|---|---|
| 1 | B-trees and index internals. Clustered vs secondary, covering indexes, why index choice dominates query cost. |
| 2 | Query plans: reading one, and the usual pathologies. |
| 3 | ACID, each letter concretely. |
| 4 | Isolation levels and **the specific anomaly each one still permits** — derive the anomalies, don't memorize a table. |
| 5 | Replication: leader–follower, sync vs async, replication lag, read-your-writes and monotonic-read violations. |
| 6 | Read replicas, connection pooling, multi-leader and its conflict problem. |
| 7 | Consolidation. |

## Week 9 · Caching & partitioning · *teach-then-test → socratic*
**Lane A:** tries + advanced trees

| D | Lane B |
|---|---|
| 1 | Cache patterns: aside, read-through, write-through, write-behind, refresh-ahead. Failure mode of each. |
| 2 | Eviction policies; TTL design; the hardest problem, invalidation. |
| 3 | Thundering herd, cache stampede, negative caching, hot keys. |
| 4 | Sharding strategies: range, hash, directory, geo. Resharding pain. |
| 5 | **Consistent hashing derived, not memorized** — start from "what breaks with modulo?" and arrive at the ring. Virtual nodes. |
| 6 | Rebalancing; the celebrity/hot-shard problem; when to give up and dedicate capacity. |
| 7 | Consolidation. |

## Week 10 · Networking & APIs · *socratic*
**Lane A:** graph traversal (grid + adjacency)

| D | Lane B |
|---|---|
| 1 | HTTP/1.1 vs 2 vs 3: head-of-line blocking, multiplexing, QUIC. What actually changed and why. |
| 2 | TLS handshake, termination, mTLS. |
| 3 | REST vs gRPC vs GraphQL: real tradeoffs, and where GraphQL bites back (N+1, caching). |
| 4 | Idempotency and idempotency keys; retries and exactly-once at the API boundary; pagination at scale (offset vs cursor). |
| 5 | Rate limiting: token bucket, leaky bucket, fixed window, sliding window log and counter. Derive why each has the burst behavior it has. |
| 6 | API gateway responsibilities; auth patterns; webhooks and delivery guarantees. |
| 7 | Consolidation. **Mock: system design #1.** |

---

# PART III · DISTRIBUTED SYSTEMS (W11–14) · *socratic throughout*

## Week 11 · Consistency & consensus
**Lane A:** topological sort + union-find

| D | Lane B |
|---|---|
| 1 | CAP stated precisely, then why **PACELC** is the more useful frame day to day. |
| 2 | Consistency models: linearizable → sequential → causal → eventual. What each forbids. |
| 3 | Quorums, R + W > N, sloppy quorums, hinted handoff. |
| 4 | Clocks: why wall clocks lie, logical clocks, vector clocks, and what they cost. |
| 5 | Raft: leader election and log replication, derived from the safety requirement. Paxos intuition by contrast. |
| 6 | Split brain, fencing tokens, and why "just use a lock" fails in a distributed system. |
| 7 | Consolidation. |

## Week 12 · Async & messaging
**Lane A:** Dijkstra / weighted graphs

| D | Lane B |
|---|---|
| 1 | Queues vs logs — the structural difference and what it implies for replay. |
| 2 | Kafka architecture: partitions, offsets, consumer groups, ISR, retention, rebalancing. |
| 3 | Delivery semantics: at-most-once, at-least-once, and **what "exactly-once" actually means** (and where it's marketing). |
| 4 | Ordering guarantees and their cost. Partition keys as a design decision. |
| 5 | Backpressure, consumer lag, poison messages, DLQs. |
| 6 | Transactional outbox; CDC; the dual-write problem and why it's so common. |
| 7 | Consolidation. |

## Week 13 · Storage engines & data at scale
**Lane A:** backtracking

| D | Lane B |
|---|---|
| 1 | LSM trees vs B-trees: write vs read vs space amplification. Derive which workload wants which. |
| 2 | SSTables, memtables, compaction strategies (size-tiered vs leveled), WAL. |
| 3 | Bloom filters — derive the false-positive tradeoff. Where else probabilistic structures earn their keep (HLL, count-min sketch). |
| 4 | NoSQL families and honest use cases. Dynamo-style vs Bigtable-style lineages. |
| 5 | MapReduce → Spark: shuffle, partitioning, skew. |
| 6 | Batch vs stream; event time vs processing time; watermarks; windowing. Lambda vs Kappa. |
| 7 | Consolidation. |

## Week 14 · Reliability & operations
**Lane A:** DP part 1 — 1D + knapsack

| D | Lane B |
|---|---|
| 1 | Failure taxonomy: crash, omission, timing, Byzantine, gray failure. Gray failure is the one that hurts. |
| 2 | Timeouts, retries, exponential backoff **with jitter** — and how naive retries cause the outage they were meant to survive. |
| 3 | Circuit breakers, bulkheads, load shedding, graceful degradation. |
| 4 | Distributed transactions: 2PC and its blocking problem, sagas and compensating actions, and why sagas usually win. |
| 5 | Observability: metrics vs logs vs traces, cardinality cost, sampling, what to alert on. |
| 6 | SLI/SLO/error budgets; capacity planning; deploy strategies (blue-green, canary, feature flags). |
| 7 | Consolidation. **Mock: system design #2.** |

---

# PART IV · SD CANONICAL DESIGNS (W15–17) · *design-first*

Sessions open cold with a problem. Concepts enter **only** where you hit a wall. Two mocks
per week. Every design gets a writeup in `design/writeups/`.

## Week 15 · Read-heavy & feeds
**Lane A:** DP part 2 — 2D, LIS, interval DP

| D | Design |
|---|---|
| 1 | URL shortener (the warm-up: ID generation, redirect path, analytics) |
| 2 | Pastebin (blob storage, expiry, access control) |
| 3 | News feed — **fan-out on write vs read vs hybrid**, derived |
| 4 | Twitter timeline at scale (celebrity problem returns) |
| 5 | Instagram (media pipeline, thumbnails, feed ranking hooks) |
| 6 | **Mocks: SD #3 and #4**, timed 45 min |
| 7 | Consolidation: compare your six writeups; find the reusable skeleton |

## Week 16 · Write-heavy & realtime
**Lane A:** greedy + bit manipulation

| D | Design |
|---|---|
| 1 | Chat / WhatsApp (connection state, delivery receipts, ordering) |
| 2 | Notification system (multi-channel, dedup, preferences, retries) |
| 3 | Live comments / activity streams at high write volume |
| 4 | Presence (the deceptively hard one: heartbeats, scale, staleness) |
| 5 | Collaborative editing: OT vs CRDT, derived from the conflict requirement |
| 6 | **Mocks: SD #5 and #6** |
| 7 | Consolidation |

## Week 17 · Search, geo, infra, hard mode
**Lane A:** matrix + **design problems: LRU/LFU cache** *(bridges into Lane B)* · **interleaved random starts**

| D | Design |
|---|---|
| 1 | Typeahead / autocomplete (trie at scale, ranking, freshness) |
| 2 | Search indexing (inverted index, sharding, relevance) |
| 3 | Proximity service: geohash vs quadtree vs S2, derived |
| 4 | Ride matching (Uber): the write-heavy realtime + geo combination |
| 5 | **Payment ledger** — exactly-once with money, double-entry, idempotency, reconciliation. The hardest correctness problem in the set. |
| 6 | Distributed job scheduler; distributed rate limiter; blob store (S3). **Mock: SD #7.** |
| 7 | Consolidation |

---

# PART V · ML (W18–22)

## Week 18 · ML fundamentals ramp, classical ground · *teach-then-test*
**Lane A:** interleaved random + **rate limiter design problem**

| D | Lane B |
|---|---|
| 1 | Supervised framing; features vs labels; what problems are *not* ML problems. |
| 2 | Train/val/test discipline; **leakage** (the #1 real-world killer); cross-validation. |
| 3 | Bias–variance; regularization; capacity. |
| 4 | Class imbalance: resampling, weighting, threshold moving, and why accuracy lies. |
| 5 | **The metric zoo:** precision/recall/F1, ROC-AUC vs PR-AUC, NDCG, calibration — and **which one a business goal maps to**. This is the interview's favorite trapdoor. |
| 6 | Trees, random forests, GBDT — still the tabular/ranking workhorse. Why they beat deep nets on tabular data. |
| 7 | Consolidation. |

## Week 19 · ML fundamentals ramp, modern bridge · *teach-then-test → socratic*
**Lane A:** interleaved random

| D | Lane B |
|---|---|
| 1 | Representation learning: what changed when features stopped being hand-made. |
| 2 | Contrastive objectives; in-batch negatives; hard negative mining. |
| 3 | **Two-tower retrieval architecture** — leans directly on W1–2 embeddings, which is why the AI block came first. |
| 4 | Transfer learning and fine-tuning in the pre-LLM sense; when to freeze what. |
| 5 | Sequence models before and after attention; what the transformer replaced and why. |
| 6 | What actually changed 2020→2026: scale, instruction tuning, RLHF, multimodality, reasoning models. Explicitly closing your 5-year gap. |
| 7 | Consolidation. **Mock: ML design #1.** |

## Week 20 · ML system design framework · *socratic*
**Lane A:** interleaved random

| D | Lane B |
|---|---|
| 1 | **Business goal → ML problem framing.** The single highest-scoring skill in an ML design interview. |
| 2 | Choosing offline metrics that predict online outcomes — and when they don't. |
| 3 | Online metrics, guardrail metrics, and the proxy-metric trap. |
| 4 | Data sources; labeling strategies: human, implicit feedback, weak supervision, synthetic. |
| 5 | Label quality, delay, and bias. Position bias in implicit feedback. |
| 6 | Train/serve skew; offline/online consistency; the reproducibility baseline. |
| 7 | Consolidation. |

## Week 21 · Features, serving, monitoring · *socratic*
**Lane A:** interleaved random

| D | Lane B |
|---|---|
| 1 | Feature engineering; feature stores; **point-in-time correctness** (the subtle one). |
| 2 | Batch vs streaming features; freshness vs cost; backfills. |
| 3 | **Retrieval + ranking two-stage architecture** — why nearly every large ML system converges here. Candidate generation, filtering, ranking, re-ranking. |
| 4 | Serving: batch vs online inference, latency budgets, model registry, versioning, rollback. |
| 5 | Shadow deploys, canaries, A/B testing, interleaving, sequential testing pitfalls. |
| 6 | Drift (data, concept, label); **degenerate feedback loops**; cold start; monitoring what matters. |
| 7 | Consolidation. |

## Week 22 · ML canonical designs · *design-first*
**Lane A:** interleaved random

| D | Design |
|---|---|
| 1 | Video / feed recommendation end to end |
| 2 | Ad click prediction (calibration matters here, and why) |
| 3 | Search ranking / learning to rank |
| 4 | Visual search (embeddings + ANN, connecting straight back to W5) |
| 5 | Harmful content detection (multimodal, adversarial, human-in-the-loop) |
| 6 | People-you-may-know / link prediction. **Mocks: ML design #2 and #3.** |
| 7 | Consolidation |

---

# PART VI · GenAI SYSTEM DESIGN (W23–25) · *design-first*

The interview-shaped version of W1–6: same concepts at 10M-user scale. This is why it sits
after distributed systems rather than next to the AI fundamentals block.

## Week 23 · LLM serving at scale
**Lane A:** interleaved random

| D | Lane B |
|---|---|
| 1 | Serving architecture: gateway, queue, scheduler, workers. Where the GPUs actually go. |
| 2 | Continuous batching; **paged attention and KV-cache memory management** — now with W4's derivation underneath. |
| 3 | GPU memory math: weights + KV + activations. Deriving max concurrency from a memory budget. |
| 4 | Parallelism: tensor, pipeline, expert. When each is forced on you. |
| 5 | Autoscaling GPU fleets (cold starts, spot capacity); cost modeling per million tokens. |
| 6 | Model routing, cascades, semantic caching; multi-tenancy, fairness, noisy neighbors. |
| 7 | Consolidation |

## Week 24 · RAG and agents at scale
**Lane A:** interleaved random

| D | Lane B |
|---|---|
| 1 | Production RAG architecture: ingestion, indexing, serving as three separate systems. |
| 2 | Index freshness, incremental updates, reindexing without downtime. |
| 3 | **Permissions-aware retrieval** — the enterprise requirement that breaks naive RAG. Multi-tenant isolation. |
| 4 | Agent orchestration: tool calling, planning loops, termination, retry/idempotency for non-deterministic steps. |
| 5 | Memory tiers (working, episodic, semantic); context budgeting; sandboxing tool execution. |
| 6 | **Prompt injection as a design constraint**, not an afterthought: trust boundaries, indirect injection via retrieved documents, exfiltration paths, guardrail placement. Cost and latency control. |
| 7 | Consolidation |

## Week 25 · Full GenAI designs
**Lane A:** interleaved random

| D | Design |
|---|---|
| 1 | AI coding assistant (context assembly, latency, IDE constraints) |
| 2 | Enterprise document Q&A (permissions, freshness, citations, audit) |
| 3 | Customer support agent (tools, escalation, eval, safety) |
| 4 | LLM content moderation (throughput, cost, false-positive economics) |
| 5 | Text-to-image service; realtime voice assistant (streaming, interruption, latency budget) |
| 6 | **Mocks: GenAI design #1 and #2** |
| 7 | Consolidation. **Mocks: GenAI design #3 and #4.** |

---

# WEEK 26 · INTEGRATION

**Lane A:** interleaved random, timed, mixed difficulty

| D | Activity |
|---|---|
| 1 | **Blind mixed mock #1** — track not revealed until the problem is read. Actual interview conditions. |
| 2 | Weak-spot cleanup: everything still open in `weak-spots.md`, resolved from first principles. |
| 3 | **Blind mixed mock #2** |
| 4 | **`eli5-glossary.md` audit:** every L4 concept re-tested cold. Any ELI5 that needs a follow-up question to make sense gets demoted and rewritten. |
| 5 | **Blind mixed mock #3** |
| 6 | **Blind mixed mock #4** |
| 7 | Final review: mastery table sweep, mock score trends, and an honest list of what's still L2. Then decide what a maintenance cadence looks like. |

---

## Lane A pattern schedule (reference)

| Weeks | Patterns |
|---|---|
| 1–6 | two pointers · sliding window · binary search (+ on answer) · prefix sums · intervals · linked lists · monotonic stack |
| 7–13 | heaps/top-k · tree BFS/DFS · tries · graph traversal · topological sort · union-find · Dijkstra · backtracking |
| 14–16 | DP (1D, knapsack, 2D, LIS, interval) · greedy · bit manipulation · matrix |
| 17–18 | design problems: LRU/LFU, rate limiter *(deliberate bridge into Lane B)* |
| 17–26 | **interleaved random** — the pattern is not revealed; identifying it is the exercise |

**~180 problems total.** Every one logs to `coding/log.md`. Missed problems are re-solved from
scratch on the retry date, never re-read.

---

## Mock schedule (~30 total)

| When | Mock |
|---|---|
| W2, W5, W6 D7 | AI fundamentals oral exams #1–3 |
| W10, W14 | System design #1–2 |
| W15, W16, W17 | System design #3–7 |
| W19, W22 | ML design #1–3 |
| W25 | GenAI design #1–4 |
| W26 | 4 blind mixed |
| Lane A, ~every other week | Coding mocks (~11) |

Every mock produces a scorecard from `templates/mock-scorecard.md`, appended to the history
table in `progress.md`.
