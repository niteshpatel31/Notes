# 6-Month Systems Engineering Prep Plan (v2)
## FAANG Backend → HFT Systems Path
**Profile:** BTech graduate · C++ intermediate · Weak math background · 5–6 hrs/day
**Generated:** July 2026 · Target roles: FAANG Systems/Backend + HFT Systems Engineering

---

## Table of Contents

1. [Honest Assessment](#1-honest-assessment)
2. [Math Audit](#2-math-audit)
3. [Priority Ordering of All Subjects](#3-priority-ordering)
4. [Daily and Weekly Schedule](#4-schedule)
5. [Phase 1 — Month 1–2: Foundations](#5-phase-1)
6. [Phase 2 — Month 3–4: Core Systems](#6-phase-2)
7. [Phase 3 — Month 5–6: Specialization + Interviews](#7-phase-3)
8. [DSA Milestones](#8-dsa-milestones)
9. [Mathematics Milestones](#9-math-milestones)
10. [Complete Book List — With Verdicts](#10-books)
11. [Projects](#11-projects)
12. [Portfolio and Freelancing](#12-portfolio)
13. [Study Environment](#13-study-environment)
14. [Mistakes to Avoid](#14-mistakes)
15. [HFT Realism Assessment](#15-hft-realism)
16. [Technical Communication](#16-comms)
17. [Compensation Reality + Cities — Brutally Honest](#17-money)

---

## 1. Honest Assessment

Your C++ baseline puts you ahead of most BTech grads starting this journey. Your weak math is the real constraint, but the good news is your target — HFT *systems* engineering, not quant research — needs far less math than the 1,200-hour curriculum you're picturing. You need about 200 hours of math, integrated into DSA and systems work, not a separate track.

**What 6 months realistically gets you:**
- FAANG systems/backend interview-readiness: yes, fully reachable.
- HFT systems engineering (non-quant): initial conversations by Month 6, offers realistically Month 8–9 — and only with a referral or strong project portfolio, see Section 17.
- HFT quant research: not the target. That needs stochastic calculus and PDEs. Don't detour there.

**Three real risks:** splitting focus across too many subjects, treating every recommended book as mandatory instead of a menu, and doing DSA in isolation from real systems code.

---

## 2. Math Audit

### 2.1 Study — Priority Order

| # | Topic | Why | Hours |
|---|--------|-----|--------|
| 1 | Complexity Analysis (Big O, Master Theorem, amortized) | Every FAANG interview probes this | 25–30 |
| 2 | Mathematical Induction | Loop invariants, recursion proofs, DP correctness | 15–18 |
| 3 | Modular Arithmetic | Modular inverse, fast exponentiation, CRT — constant in CP | 18–22 |
| 4 | Recurrence Relations | Daily occurrence in algorithm analysis | 15–18 |
| 5 | Combinatorics | Counting, probability, pigeonhole in interviews and CP | 20–25 |
| 6 | Probability Basics | System design, HFT reasoning, expected value | 25–30 |
| 7 | Bit Manipulation | Mostly known — close gaps only | 5–8 |
| 8 | IEEE 754 / Floating Point | Price representation bugs are a real production-incident category | 12–15 |
| 9 | Graph Theory Math | Handshaking lemma, BFS layers, SCC structure | 10–12 |
| 10 | Statistics Essentials | p50/p99 latency, monitoring | 10–12 |
| 11 | Concentration Inequalities (light) | Hash tables, Bloom filters | 6–8 |
| 12 | Propositional Logic | De Morgan's, condition simplification | 5–6 |
| 13 | LOB & Market Microstructure | Conceptual — required for HFT interviews | 20–25 |
| 14 | Linear Algebra (vectors/matrices only) | Matrix exponentiation for CP recurrences | 8–10 |

**Total: 185–215 hours over 6 months — about 1 hr/day, absorbed into DSA and systems blocks.**

### 2.2 Skip Entirely

Predicate logic (deep), contradiction/contrapositive proof-writing fluency, formal sets/relations/functions treatment, generating functions, full Markov chain math, probability distributions/hypothesis testing/regression, eigenvalues/SVD, SIMD math, calculus, optimization/Lagrange/gradient descent, Avellaneda-Stoikov and Almgren-Chriss mathematical detail, the full quant-developer track, real analysis/measure theory/topology.

### 2.3 Integration Strategy

- Complexity, induction, recurrences → absorbed into the DSA block, Month 1.
- Modular arithmetic, combinatorics → learned through CP problems as they appear.
- Probability → 30 min/day in the reading block, Month 2–3.
- IEEE 754 → one focused week, Month 2.
- LOB + microstructure → HFT specialization block, Month 5–6.

---

## 3. Priority Ordering — All Subjects

1. DSA — every day, non-negotiable.
2. Complexity + Recurrences — Week 1–2, applied forever after.
3. Modern C++ — your differentiator, deep in Phase 1.
4. Linux + OS Internals — Day 1 start, both target paths need it.
5. Modular Arithmetic + Combinatorics — CP fuel.
6. Networking — Phase 2, prerequisite for distributed systems.
7. DDIA — Month 3, cover to cover, no shortcuts.
8. Probability — Phase 2–3.
9. DBMS — Phase 2, 2–3 weeks max.
10. Systems Design Practice — Phase 3.
11. IEEE 754 — Phase 2, one focused week.
12. Lock-Free C++ / Concurrency — Phase 3, HFT track.
13. LOB + Microstructure — Phase 3, HFT track.
14. Rust basics — Phase 3, Month 5, gradual.
15. Statistics Essentials — Phase 2–3.
16. Kotlin — postpone past 6 months entirely.

---

## 4. Schedule

```
Block 1 — 08:00–10:00 (2 hrs)     DSA + Math Integration
Block 2 — 10:00–13:00 (2.5–3 hrs) Systems Primary (phase-dependent)
Block 3 — 14:00–15:00 (1 hr)      Reading + Concept Review
Evening  — 21:00–22:00 (1 hr)     Codeforces / Mock / Upsolve
```
**Total: 5.5–6 hrs/day.** DSA always comes first — fresh brain for algorithmic thinking.

| Day | Morning | Afternoon | Evening |
|---|---|---|---|
| Mon | DSA — new pattern | Systems primary | Upsolve Monday's CF problem |
| Tue | DSA — new pattern | Systems primary | Review Tuesday concepts aloud |
| Wed | DSA — harder problem | Systems primary | Codeforces virtual round |
| Thu | DSA — variation | Systems primary | Upsolve Wed's round (mandatory) |
| Fri | DSA — review weak areas | Systems primary | Mock technical explanation (recorded) |
| Sat | DSA (2 hrs) | Full CF live round (3–4 hrs) | Upsolve + post-contest analysis |
| Sun | DSA (2 hrs) | Project work (2 hrs) | Weekly review + planning |

**Daily rating (1–5):** 5 = 3+ problems, 3+ hrs systems, zero distractions. 3 = acceptable floor. 1 = wasted day, write why. **Weekly average target: 3.0+, elite: 4.0+.**

---

## 5. Phase 1 — Month 1–2: Foundations

### 5.1 Modern C++

**Goal:** idiomatic Modern C++ by reflex.

**Primary books, in this order:**
1. *A Tour of C++* (Stroustrup) — Weeks 1–2. Code every example.
2. *Effective Modern C++* (Meyers) — Weeks 2–4, running alongside. This is your highest-value C++ book — move semantics, `noexcept`, smart pointer pitfalls are asked verbatim in interviews.
3. *Programming with C++20* (Fertig) — Month 2. Concepts, coroutines, ranges — current material.
4. *C++ Best Practices* (Turner) — one weekend, Month 2. Short, practical.
5. *Beautiful C++* (Core Guidelines) — optional, one weekend, Month 2.
6. *C++17 In Detail* (Filipek) — reference only, skim, don't read linearly.

**Own completely:** move semantics, RAII (write 3 wrappers: file, mutex, socket), `unique_ptr`/`shared_ptr`/`weak_ptr`, `optional`/`variant`/`expected`, `constexpr`, `thread`/`mutex`/`atomic`/`condition_variable`, lambdas (capture modes, generic lambdas), template basics (no metaprogramming yet), STL algorithms (`sort`, `transform`, `accumulate`, `partition`, `lower_bound`).

**Reference daily:** cppreference.com.

**CppCon Back to Basics (2–3/week):** "The Structure of a Program" (Godbolt), "Move Semantics" (Iglberger), "RAII and the Rule of Zero" (O'Dwyer), "Smart Pointers" (O'Dwyer), "Concurrency" (Shah), "Memory Model" (Shah), "Templates Part 1" (Josuttis).

### 5.2 Linux + OS Internals

**Primary book:** *Operating Systems: Three Easy Pieces* (Arpaci-Dusseau) — free at pages.cs.wisc.edu/~remzi/OSTEP. More modern and implementation-focused than Silberschatz; use it as primary. Cover the chapters on processes, scheduling, concurrency, and virtual memory.

**Paired reading:** *Inside the Machine* (Stokes), one chapter every 3 days — maps CPU pipeline, cache hierarchy, TLB, NUMA to what the OS book describes conceptually.

**Code every chapter:**
```c
// fork/exec, pthreads+mutex, semaphores, mmap — write a C program for each concept
```

**Tools to master:** `strace`, `gdb` (5 core commands: break, run, next, print, bt), `valgrind --leak-check=full` on every program, `htop`/`btop`, `perf stat`.

### 5.3 Bash + Neovim + tmux

**No book purchases needed here** — the Vim books on your list (*Practical Vim*, *Learning the vi and Vim Editors*, *Modern Vim*) are skipped; this plan uses Neovim, not Vim.

**Neovim (Day 1, max 4 hours):** `kickstart.nvim` base + `nvim-lspconfig` (clangd, rust-analyzer later) + `telescope.nvim` + `nvim-treesitter` + `conform.nvim` + `oil.nvim`. Learn `<leader>ff/fg/fb`, `gd`, `gr`, `K`, split navigation, `gcc`.

**tmux (Day 1):** prefix `Ctrl+a`, learn splits/zoom/copy-mode from a cheat sheet — a full book (*tmux 3*) is unnecessary for this.

**Bash:** learn by writing real scripts from Week 1 — auto-commit LeetCode solutions, build/test scripts, log parsers, backup scripts.

### 5.4 Mathematics — Phase 1

**Complexity Analysis (Weeks 1–2):** CLRS Ch 3, then Ch 2.2. Do every exercise in 3-1 and 3-2. Be able to: state formal O/Θ/Ω/o/ω definitions, prove Θ(n²) with constants, order 10 functions by growth, apply all 3 Master Theorem cases, solve recurrences by substitution.

```
T(n) = T(n/2) + 1     → O(log n)
T(n) = 2T(n/2) + n    → O(n log n)
T(n) = 2T(n/2) + n²   → O(n²)  [Master Theorem Case 3]
T(n) = 4T(n/2) + n    → O(n²)  [Master Theorem Case 1]
T(n) = T(n-1) + n     → O(n²)
T(n) = 2T(n-1) + 1    → O(2ⁿ)
```

**Induction (Weeks 3–4):** MIT MCS Ch 3 (free, MIT OCW 6.042J). Prove: mergesort recurrence, binary search correctness, leaf-count of binary trees, handshaking lemma.

**Modular Arithmetic (Month 1–2):** CLRS Ch 31.1–31.5. Implement extended GCD, modular inverse, fast modpow, Fermat inverse — these three functions cover 80% of CP modular arithmetic. Standard modulus: `1e9+7`.

### 5.5 DSA — Phase 1

**Month 1:** arrays, strings, hashmaps, sliding window, two pointers, binary search variants, recursion, sorting.
**Month 2:** linked lists, stacks, queues, heaps, trees (BST, traversals, LCA), tries.

**Daily:** 1 new pattern problem, 1 variation, 30-min review of yesterday's problem.

Follow **Neetcode.io** order exactly — don't jump around.

```
Arrays + Sliding Window: 30   Binary Search: 20   Hashmaps: 15
Two Pointers: 15   Linked Lists: 15   Stacks/Queues: 15
Trees: 20   Heaps: 10
Phase 1 target: 140–160 problems (180–200 cumulative by Phase 1 end)
```

**Codeforces:** Weeks 1–4 Div 3 (A, B, occasional C); Weeks 5–8 Div 3+Div 2 (A, B consistent, working on C). Upsolve every contest without exception — this is where 70% of the learning happens. **Target rating by end of Phase 1: 1300–1500.**

---

## 6. Phase 2 — Month 3–4: Core Systems

### 6.1 Computer Networking (Month 3)

**Read:** Kurose & Ross, Ch 1–4 thoroughly, 5–6 selectively.
**Implement alongside (Beej's Guide, free at beej.us/guide/bgnet):** UDP echo, TCP echo (blocking), multi-client TCP with `select()`, multi-client TCP with `epoll` (edge-triggered).

Know why epoll beats select: select is O(n) per call, epoll is O(active events).

**Reference:** *TCP/IP Illustrated, Vol. 1* (Stevens) — don't read cover to cover, it's 1,000 pages. Dip into the chapters on the three-way handshake, congestion control (slow start, AIMD, Nagle), and TCP state machine when Kurose's coverage isn't deep enough.

**Weekly:** one Cloudflare blog post throughout Phase 2.

**Know cold:** TCP handshake/close/TIME_WAIT, congestion control, DNS resolution chain, HTTP/1.1 vs HTTP/2 vs HTTP/3, TLS handshake at design level, "what happens when you type google.com."

### 6.2 DDIA (Month 3)

Cover to cover, active notes, 4 weeks minimum:
- Week 1 (Ch 1–3): data models, storage engines, B-Trees vs LSM-Trees.
- Week 2 (Ch 4–6): encoding, replication (leader/follower, multi-leader, leaderless).
- Week 3 (Ch 7–9): transactions (isolation levels, phantom reads, 2PL vs MVCC), distributed systems fundamentals.
- Week 4 (Ch 10–12): batch/stream processing.

Watch Kleppmann's "Is Kafka a Database?" talk afterward.

### 6.3 DBMS (Month 3, 2–3 weeks)

Focused chapters only: transactions/ACID/isolation/MVCC, indexing (B+ tree structure), query execution (`EXPLAIN ANALYZE`, join algorithms), concurrency control (2PL, deadlock detection, OCC).

**Practical:** install PostgreSQL, run real `EXPLAIN ANALYZE` queries, understand Seq Scan vs Index Scan vs Bitmap Index Scan.

### 6.4 C++ Design (Month 4, new addition)

**Read:** *C++ Software Design* (Iglberger) — modern C++ design patterns done right, this is your primary design-patterns book.

**Reference, read for vocabulary only, not implementation style:** *Design Patterns* (GoF). It's a 1994 book with C++98/Smalltalk-era code. Learn the pattern names and intent (Strategy, Observer, Factory, Decorator) — don't emulate the code.

### 6.5 Mathematics — Phase 2

**Combinatorics (Month 3, via DSA):** nCr mod prime (Pascal + Fermat inverse), inclusion-exclusion, stars and bars, pigeonhole.

```cpp
const long long MOD = 1e9 + 7;
long long fact[MAXN], inv_fact[MAXN];
// precompute factorials + inverse factorials, then:
long long nCr(int n, int r) {
    if (r < 0 || r > n) return 0;
    return fact[n] * inv_fact[r] % MOD * inv_fact[n-r] % MOD;
}
```

**Probability (Month 3):** Blitzstein & Hwang Ch 1–6, one chapter every 3–4 days. Ch 3 (Bayes) especially deep — it shows up in HFT interviews.

**IEEE 754 (Month 2, Week 7–8):** why `0.1+0.2 != 0.3`, machine epsilon, catastrophic cancellation, NaN propagation, fixed-point pricing.

```cpp
// Never compare floats for financial code:
bool approx_equal(double a, double b, double eps = 1e-9) {
    return std::abs(a - b) <= eps * std::max(1.0, std::max(std::abs(a), std::abs(b)));
}
// Trading systems use fixed-point:
int64_t price_in_ticks = 100250;  // $100.25 as integer ticks
```

### 6.6 DSA — Phase 2

**Month 3:** graphs (BFS/DFS applications, Dijkstra, Bellman-Ford, topo sort, union-find, MST, SCCs).
**Month 4:** DP (1D, 2D, knapsack, interval, tree DP, bitmask, digit DP), backtracking, divide and conquer.

For every DP problem, write state + transition before coding.

**Codeforces:** Div 2, targeting A/B/C consistently, D occasionally. **Target rating: 1500–1700.** Complete CSES graph + DP sections in parallel — cleaner than CF for pattern learning.

**LeetCode target by end of Phase 2:** 350–380 problems.

---

## 7. Phase 3 — Month 5–6: Specialization + Interviews

### 7.1 Systems Design

Apply DDIA. Read one engineering blog/week (Cloudflare, Discord, Uber, Figma, DoorDash).

**Practice designing:** URL shortener, distributed rate limiter, distributed KV store, pub-sub system, web crawler, real-time leaderboard, notification system. Always state the consistency/availability tradeoff explicitly.

### 7.2 Lock-Free C++ + Concurrency (HFT track)

**Read:** *C++ Concurrency in Action* (Williams), Ch 5–7 — the hardest reading in the plan, go slowly.
**Read alongside, Month 5:** *The Art of Writing Efficient Programs* (Pikus) — CPU cache behavior, branch prediction, compiler optimization. Advanced; start only once Phase 1 C++ is solid.

**Memory model — own completely:** relaxed, acquire, release, acq_rel, seq_cst.

**Implement from scratch:** lock-free SPSC queue (ring buffer + 2 atomics), lock-free stack with CAS (handle ABA), cache-line-aligned wrapper to eliminate false sharing.

**Benchmark with `rdtsc`** for sub-microsecond measurement.

### 7.3 HFT Math — LOB + Microstructure (Month 5–6)

Cover curriculum sections 11.1–11.3, skip 11.4–11.5.

**Implement a LOB:** price levels as sorted map, FIFO queue per level, market/limit order matching.

**Implement VWAP and TWAP.**

**Understand:** bid-ask spread's three components, adverse selection, queue position and fill probability, square-root market impact law.

### 7.4 Rust (Month 5, gradual)

*The Rust Programming Language* (free, doc.rust-lang.org/book), Ch 1–15. Rustlings exercises. Implement a linked list and binary tree (deliberately hard in Rust — teaches ownership). Goal: explain the borrow checker confidently, not ship production Rust.

### 7.5 Interview-Specific Books (new additions)

- *Daily C++ Interview* (Dargo) — one question a day, slots directly into the existing "explain out loud" daily habit (Section 16).
- *Elements of Programming Interviews* (Aziz, Lee, Prakash) — **do not** run this alongside full LeetCode grinding, that double-counts hours on the same skill. Use it specifically for interview-format practice (restate → brute force → optimize → code) in Month 5–6, or substitute it for part of your LeetCode volume if you prefer book-structured problems.
- *Trading Systems Developer Interview Guide (C++ Edition)* (Vogels) — the single most directly relevant book on your original list for the HFT track. Read in Month 5–6.

### 7.6 Mock Interviews (Month 5–6)

3 mocks/week minimum on Pramp, both sides (interviewer teaches you what good/bad answers look like).

**4-step method, every time:** restate + clarify → brute force first → optimal solution → analyze then code, test edge cases.

Record yourself once a week explaining a solution; watch playback; fix one specific gap per week.

---

## 8. DSA Milestones

| Milestone | Day | Criteria |
|---|---|---|
| 100 problems | 31 | Arrays, binary search, hashmaps, linked lists — Easy in 10 min, Medium in 25–30 |
| 200 problems | 60 | + Trees, heaps, stacks — Medium in 20–25 min |
| 300 problems | 90 | + Graphs, Union-Find — starting Hard |
| 380 problems | 120 | + DP — Mediums under 20 min |
| 450 problems | 150 | + Interval DP, bitmask, advanced graphs |
| 500+ problems | 175 | All categories — Hard in 30–40 min |

**Codeforces:** M1 1200–1400 → M2 1400–1500 → M3 1550–1650 → M4 1650–1800 → M5 1800–1900 → M6 1900+.

**CSES (complete in Phase 1–2):** Sorting/Searching (19), Graph Algorithms (19), DP (19), Tree Algorithms (16).

---

## 9. Mathematics Milestones

| Milestone | Phase | Verify by |
|---|---|---|
| Master Theorem, all 3 cases | M1 W2 | 10 CLRS Ch4 recurrences solved |
| Big-O proved with constants | M1 W1 | CLRS 3-1, 3-2 exercises |
| Induction — full proof | M1 W3–4 | 5 algorithm properties proven |
| Extended GCD + modpow | M1 | Passes a CF modular-inverse problem |
| Amortized analysis of std::vector | M2 | Explain all 3 methods (aggregate/accounting/potential) |
| nCr mod prime | M2 | Solves LC 62, 518 |
| Bayes' theorem cold | M3 | Medical test problem + 5 variants, no reference |
| Catastrophic cancellation | M2 | Spot the bug in 3 float code samples |
| Fixed-point pricing | M3 | Order value calc with zero doubles |
| Full LOB matching engine | M5–6 | GitHub project, FIFO per price level |
| VWAP from trade tape | M5 | Correct on 10 test cases |

---

## 10. Complete Book List — With Verdicts {#10-books}

### Core reading schedule

| Book | When | Verdict |
|---|---|---|
| *A Tour of C++* (Stroustrup) | M1–2 | Keep — primary intro |
| *Effective Modern C++* (Meyers) | M1–2 | **Add — core, not optional** |
| *Programming with C++20* (Fertig) | M2 | **Add** |
| *C++ Best Practices* (Turner) | M2 | **Add** — one weekend |
| *Operating Systems: Three Easy Pieces* (Arpaci-Dusseau) | M1–2 | **Add, replaces Silberschatz as primary** |
| *Inside the Machine* (Stokes) | M1 | Keep |
| *Introduction to Probability* (Blitzstein) | M3 | Keep |
| *Computer Networking: Top Down* (Kurose) | M3 | Keep — primary |
| *TCP/IP Illustrated Vol. 1* (Stevens) | M3, reference | **Add — reference only, not linear** |
| *DDIA* (Kleppmann) | M3 | Keep — most important book in the plan |
| *DBMS Concepts* (Ramakrishnan) | M3–4 | Keep — focused chapters |
| *CLRS* | Reference | Keep — reference, not cover-to-cover |
| *C++ Software Design* (Iglberger) | M4–5 | **Add — replaces GoF as primary design-patterns book** |
| *C++ Concurrency in Action* (Williams) | M5–6 | Keep |
| *The Art of Writing Efficient Programs* (Pikus) | M5 | **Add — advanced, HFT-relevant** |
| *The Rust Programming Language* | M5 | Keep |
| *Trading Systems Developer Interview Guide, C++ Ed.* (Vogels) | M5–6 | **Add — most directly HFT-relevant book on your list** |
| *Daily C++ Interview* (Dargo) | M5–6 | **Add — one Q/day format** |
| *Elements of Programming Interviews* | M5–6 | **Add as substitute, not addition, to LeetCode volume** |
| *The Linux Programming Interface* (Kerrisk) | Ongoing reference | Keep — reference for syscall projects |

### Optional / reference-only — don't schedule linear reading time

*C++17 In Detail* (overlaps C++20 book), *Beautiful C++* (short, nice-to-have), *Design Patterns/GoF* (vocabulary only, dated code style).

### Skip entirely

- *Practical Vim*, *Learning the vi and Vim Editors*, *Modern Vim* — plan uses Neovim, not Vim. Three redundant purchases.
- *tmux 3* — a cheat sheet covers what you need in 30 minutes.
- *Fluent Python*, *High Performance Python* — wrong stack for this path.
- *C++ Lambda Story* — one feature, already covered by *A Tour of C++* + CppCon talks.
- *C++ Templates: The Complete Guide* — 1,500-page metaprogramming reference, not tested at entry-level. Year 2 book.
- *C++: A Beginner's Guide* (Schildt) — too basic for your level, and Schildt's C/C++ books have a documented reputation for technical errors in the community. Don't risk learning something wrong.

**Reality check:** scheduling all 25 original books as full linear reads would add 150–250+ hours on top of an already full plan. That time has to come from somewhere — it would come from DSA and projects, which are what actually get you interviews. 9 adds, 6 skips, the rest reference-only.

---

## 11. Projects {#11-projects}

Build in order, each with a proper README explaining design decisions.

1. **Mini Shell in C** (M2, ~2 wks) — fork/exec/pipe/wait/signal, SIGCHLD, SIGSTOP/SIGCONT. Features: command exec, pipes, redirection, background jobs, built-ins.
2. **TCP Echo Server with epoll** (M3, ~1 wk) — epoll_create1/ctl/wait, non-blocking sockets, edge- vs level-triggered.
3. **HTTP/1.1 Server in C++** (M3–4, ~3 wks) — the most interview-relevant project. Request parsing, thread pool, Content-Type logic, keep-alive, 404/500 handling.
4. **Key-Value Store with WAL** (M4–5, ~3 wks) — DDIA Ch 3 is the conceptual foundation. GET/SET/DEL over TCP, write-ahead log, compaction, crash recovery.
5. **Lock-Free SPSC Queue** (M5–6, ~2 wks, HFT track) — cache-line aligned, correct memory ordering, benchmarked vs mutex-based version. Explain the throughput crossover point.
6. **LOB Matching Engine** (M6, ~2 wks, HFT track) — sorted-map price levels, FIFO per level, market/limit matching, cancel by ID, VWAP, `rdtsc` latency measurement per order. **This is your single best HFT-interview asset** — walk through architecture and latency profile confidently.

---

## 12. Portfolio and Freelancing {#12-portfolio}

- **M1–2:** portfolio site (Astro/plain HTML on Vercel, one weekend max), all projects on public GitHub from Day 1.
- **M3:** first technical blog post (mini shell writeup), post to portfolio + Dev.to + LinkedIn.
- **M4:** domain + VPS (Hostinger/Hetzner, ~₹350–380/month), configure nginx + certbot + fail2ban + ufw — this is systems practice, not overhead.
- **M5+:** start freelance outreach, not before — nothing to show means every proposal gets rejected.

**Platforms:** LinkedIn (M3, weekly technical posts), Fiverr (M3, VPS setup gigs), HN freelancer thread (M4), Upwork (M4, niche C++/Linux gigs), Toptal (M5–6, once 500 LC + 3 projects + blog exist).

**Four blog posts that carry the whole content strategy:** mini shell internals (M2), HTTP server from scratch (M3), DDIA notes on replication (M4), lock-free vs mutex benchmarks (M5).

---

## 13. Study Environment {#13-study-environment}

**Hardware, in priority order:** chair with lumbar support (₹3–8K) > 24" IPS monitor (₹8–14K) > mechanical keyboard (₹2.5–6K) > wired mouse (₹500–1.5K) > laptop stand (₹800–2K) > powered USB hub (₹600–1.2K) > wired headphones (₹1–3K). **Skip:** standing desk, ultrawide, RGB peripherals, course bundles.

**Software (all free):** Arch/Debian Linux (Day 1, daily driver, no exceptions), Neovim + kickstart.nvim (Day 1, 4 hrs max), tmux (Day 1), gcc/clang/cmake/ninja (Day 1), gdb + valgrind (Week 1), zsh (Week 1), strace/ltrace/perf (M2), Git with daily commits (Day 1), Rustup (M5 only), UptimeRobot (M4).

**Deep work rules:** phone in another room during blocks, one browser tab open, block YouTube/Instagram during study hours (LeechBlock/StayFocusd), log start/end time every session, solve on paper before typing, one topic at a time, Sunday weekly review.

---

## 14. Mistakes to Avoid {#14-mistakes}

1. Following the full 1,200-hour math curriculum — you need ~200 hours, integrated.
2. Grinding LeetCode randomly instead of pattern-based (Neetcode order).
3. Reading OS Concepts/OSTEP without writing the corresponding C programs.
4. Treating DDIA as light reading — budget 4 weeks, active notes.
5. Only doing virtual Codeforces rounds — live pressure is qualitatively different.
6. Not upsolving — this is where the growth happens.
7. 500 LeetCode problems with zero real project code — both matter, the schedule's ratio is deliberate.
8. Attempting Rust as a main language before Month 5.
9. Treating probability as optional for the HFT track.
10. Building a portfolio without case-study READMEs.
11. Isolating yourself — join CP Discord servers, find an upsolve partner.
12. More than 4 hours on Neovim configuration — the most seductive procrastination trap in developer culture.
13. **New:** buying and scheduling all 25 books from your list instead of the ~9 that are actually load-bearing for this timeline.

---

## 15. HFT Realism Assessment {#15-hft-realism}

**What HFT systems roles actually require:** exceptional C++ (lock-free, memory model, cache efficiency), deep Linux (scheduling, NUMA, huge pages, CPU/IRQ affinity), network stack depth (kernel bypass, DPDK, RDMA), understanding why things are slow (pipeline stalls, cache misses, memory bandwidth), LOB literacy, basic microstructure (adverse selection, spread, queue position).

**Not required for systems roles:** options pricing theory, stochastic calculus, portfolio optimization, Sharpe ratios.

**What 6 months gets you:** interview-ready C++/OS depth, a directly relevant LOB project, a benchmarked lock-free queue demonstrating latency thinking, microstructure literacy at the systems-interview level.

**Realistic outcome:** initial conversations and screens Month 6. Full-loop interviews and offers Month 8–9 — *and this assumes a competitive resume gets read at all; see Section 17 for why that assumption needs scrutiny.*

**Firms to target after 6 months:** Graviton, Quadeye, Tower Research (India offices) first, then Optiver/IMC/Jump with more seasoning.

**Optiver's "80 in 8" mental arithmetic test:** practice 15 min/day in the final 4 weeks if targeting Optiver specifically — mental multiplication, division, percentages, square-root estimation.

---

## 16. Technical Communication {#16-comms}

Your written English is precise; the gap is spoken technical fluency. The only fix is speaking technically, frequently — no separate schedule needed:

- After every DSA problem: explain your approach out loud, 3–5 min, before checking any solution.
- After every systems chapter: 5-min spoken summary.
- Weekly: record yourself explaining a concept, watch it back, fix one thing.
- Pramp mocks from Month 3, 2/week in M5–6.

Read engineering blogs actively (Cloudflare, Discord, Uber) for real technical vocabulary in context. Watch QCon/StrangeLoop talks without subtitles as your model for technical speech.

---

## 17. Compensation Reality + Cities — Brutally Honest {#17-money}

Numbers pulled from Glassdoor, Levels.fyi, and public offer aggregators, July 2026. **This data is noisy** — self-reported salary sites disagree by 2x on the same role at the same company, and HFT comp specifically is thin-sample and skews toward people who post because their number is impressive. Treat every figure as directional.

### FAANG / Big Tech — India

| Company | Role | Realistic fresher total comp | Note |
|---|---|---|---|
| Amazon | SDE-1 | ₹20–32 LPA | Current 2026 fresher postings, not the lower raw Glassdoor median which includes older/unnegotiated offers |
| Google | SWE 1 / L3 | ₹30–45 LPA | Top of the domestic pay scale — but see below on how offers are actually sourced |
| Microsoft | SDE | Comparable to Amazon, slightly lower base | — |
| Mid-tier product/fintech (Razorpay, Flipkart, PhonePe, Zerodha, Groww, CRED) | SDE-1 | ₹15–30 LPA | Wider funnel, realistic first landing spot for most candidates |

**The uncomfortable part:** Google/Amazon *campus* pipelines run almost entirely through IITs, NITs, IIITs, BITS. Off-campus fresher postings draw thousands of applicants per opening, and ATS/resume-screen filters lean on college tier and referrals before your DSA skill is ever evaluated. This plan makes you interview-ready — it doesn't fix a screening filter that isn't testing your skills at all. **Realistic sequencing for most candidates: mid-tier company first → 2 years experience + shipped projects → lateral into FAANG at SDE-2-equivalent**, a meaningfully easier door than fresher off-campus.

### HFT / Prop Trading — India

| Firm | City | Entry-level engineering (non-quant-research) | Note |
|---|---|---|---|
| Optiver | Mumbai (BKC) | Data too thin for India-specific fresher figures | Office opened 2024, still small |
| IMC Trading | Mumbai (Worli) | Same caveat | Office opened 2021 |
| Tower Research Capital | Gurugram | ₹38–70+ LPA depending on level | Wide spread — assume the low end for a genuine fresher |
| Graviton, Quadeye | Gurugram | ₹80–95 LPA figures online are **real but outlier data points**, not medians | Handful of hires, not representative |

**Straight from people who work there (not marketing):** multiple firsthand posts from current/former Quadeye and Graviton employees state these firms hire almost exclusively from the top 5–7 IITs, and fresher openings are extremely rare relative to FAANG volume. This is a sourcing-funnel problem, not a skill-ceiling problem — your LOB project and benchmarked lock-free queue are exactly the right proof-of-work, but they only matter once someone reads your resume. Referrals matter disproportionately here.

### Cities — where these jobs actually are

- **Gurugram (Delhi NCR):** India's real HFT hub — Graviton, Quadeye, Tower Research, and most other prop shops. Not Bangalore.
- **Mumbai (BKC/Worli):** Optiver, IMC — near NSE, for global market makers specifically.
- **Bangalore:** FAANG/big-tech center — Google, Amazon, Microsoft, plus most fintech/product companies. This is where the mid-tier landing-spot strategy plays out.
- **Hyderabad:** secondary FAANG hub, often an easier bar than Bangalore for the same company.

### Timeline, stated plainly

- **FAANG, fresher, off-campus, no tier-1 college, no referral:** possible, but budget for many rejections; treat the mid-tier company as the real first target, not a fallback.
- **HFT, fresher, cold application:** low probability regardless of prep quality — sourcing funnel, not skill. Treat "offers by Month 8–9" as optimistic without a referral or tier-1 college.
- **Mid-tier product/fintech, fresher:** this plan's ROI is highest and most certain here.
- **The two-step path (mid-tier → lateral into FAANG/HFT at 2–3 YOE) is the statistically likelier route to the big numbers**, even though it's slower than "6 months to Optiver."

This doesn't mean don't aim for the top-tier firms. It means: don't build your timeline or self-worth around them being the *baseline* outcome. They're the stretch goal. The mid-tier offer is the realistic floor this plan is built to deliver, and it's a genuinely good floor.

---

*Plan version: v2, July 2026. Revisit and adjust at the end of each phase.*