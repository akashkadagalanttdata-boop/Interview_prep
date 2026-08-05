# Coding Log

One line per problem, all 26 weeks. ~180 problems by the end.

**Verdict:** `solved` (clean, in time) · `solved-slow` (correct, over 25 min) · `hint`
(needed a nudge) · `failed` (didn't get there)

**Retry rule:** anything not `solved` gets a retry date at **current session +7**. On the retry
you **re-solve from scratch** — you do not re-read your earlier solution. Reading builds
recognition; re-solving builds retrieval, and only retrieval shows up in an interview.

A `failed` problem that fails its retry goes to `weak-spots.md` as type `model` — twice in a
row usually means the pattern's invariant is wrong in your head, not that you forgot a detail.

---

| # | Session | Problem | Pattern | Time | Verdict | Retry at | Notes |
|---|---|---|---|---|---|---|---|
| 1 | 0 | Valid palindrome (alphanumeric, O(1) space) | two pointers | — | `failed` | 7 | Approach stated correctly before coding ✓. Pattern identified ✓. Execution: missed the alnum filter entirely (the actual problem), `right` off by one, `for` for `while`, `lower(x)` for `x.lower()`. |
| 2 | 0 | Longest substring without repeating chars | sliding window | — | `failed` | 7 | Blank. W2 material. |

---

## Pattern coverage

Filled in as you go — a quick read on which patterns are under-practiced.

| Pattern | Problems | Solved clean | Level |
|---|---|---|---|
| two pointers | 0 | 0 | L0 |
| sliding window | 0 | 0 | L0 |
| binary search (+ on answer) | 0 | 0 | L0 |
| prefix sums | 0 | 0 | L0 |
| intervals | 0 | 0 | L0 |
| linked lists | 0 | 0 | L0 |
| monotonic stack | 0 | 0 | L0 |
| heaps / top-k | 0 | 0 | L0 |
| tree BFS/DFS | 0 | 0 | L0 |
| tries | 0 | 0 | L0 |
| graph traversal | 0 | 0 | L0 |
| topological sort | 0 | 0 | L0 |
| union-find | 0 | 0 | L0 |
| Dijkstra | 0 | 0 | L0 |
| backtracking | 0 | 0 | L0 |
| DP 1D / knapsack | 0 | 0 | L0 |
| DP 2D / LIS / interval | 0 | 0 | L0 |
| greedy | 0 | 0 | L0 |
| bit manipulation | 0 | 0 | L0 |
| matrix | 0 | 0 | L0 |
| design (LRU/LFU, rate limiter) | 0 | 0 | L0 |

## Python fluency micro-skill

Drilled continuously, not as a topic (`TUTOR.md` §6).

**S1 drill: 1 correct of 8.** Re-tested cold at S2.

| Tool | Comfortable? | Last used |
|---|---|---|
| `heapq` (incl. max-heap trick, `nlargest`) | **no — blank S1** | S1 |
| `bisect` (`bisect_left` vs `right`, `key=`) | **no — blank S1** | S1 |
| `collections` (`deque`, `defaultdict`, `Counter`) | **no — blank S1** | S1 |
| `itertools` (`accumulate`, `pairwise`, `product`) | not yet drilled | — |
| `functools.lru_cache` / `cache` for memoization | not yet drilled | — |
| `//` and `%` on negatives | **no — 0/3 at S1, C/Java intuition** | S1 |
| Mutable default args | **no — inverted model at S1** | S1 |
| Sort stability under `reverse=True` | **no — blank S1** | S1 |
| `KeyError` on `d[k] += 1`, and the three fixes | mechanism ✓, fixes ✗ | S1 |

### The nine facts, for cold re-test at S2

1. `-7 // 2 == -4` — Python floors toward −∞, it does not truncate toward zero.
2. `-7 % 3 == 2` — `%` takes the sign of the **divisor**, forced by `a == (a//b)*b + (a%b)`.
3. `def f(x, acc=[])` — the default list is built **once at definition**, shared by every call.
   Fix: `acc=None`, then `if acc is None: acc = []`.
4. `heapq.nlargest(3, nums)` — O(n log k). `sorted(nums, reverse=True)[:3]` — O(n log n).
5. Max-heap: push `-x`, pop and negate.
6. `bisect_left([1,2,2,2,3], 2) == 1`, `bisect_right(...) == 4`. **The difference is the count.**
7. `Counter(text)` for frequencies.
8. `d[k] += 1` reads before writing → `KeyError`. Fixes: `defaultdict(int)`, `Counter`,
   `d.get(k, 0) + 1`.
9. Python's sort is **stable, and stays stable under `reverse=True`** — ties keep their original
   relative order rather than flipping.
