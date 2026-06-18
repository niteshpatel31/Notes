# 6-Month Systems Engineering Prep Plan
## FAANG Backend → HFT Systems Path
**Profile:** BTech graduate · C++ intermediate · Weak math background · 5–6 hrs/day  
**Generated:** June 2026 · Target roles: FAANG Systems/Backend + HFT Systems Engineering

---

## Table of Contents

1. [Honest Assessment](#1-honest-assessment)
2. [Math Audit — What You Actually Need](#2-math-audit)
3. [Priority Ordering of All Subjects](#3-priority-ordering)
4. [Daily and Weekly Schedule](#4-schedule)
5. [Phase 1 — Month 1–2: Foundations](#5-phase-1)
6. [Phase 2 — Month 3–4: Core Systems](#6-phase-2)
7. [Phase 3 — Month 5–6: Specialization + Interviews](#7-phase-3)
8. [DSA Milestones — LeetCode + Codeforces](#8-dsa-milestones)
9. [Mathematics Milestones](#9-math-milestones)
10. [Books and Resources](#10-books-and-resources)
11. [Projects](#11-projects)
12. [Portfolio and Freelancing](#12-portfolio-and-freelancing)
13. [Study Environment](#13-study-environment)
14. [Mistakes to Avoid](#14-mistakes-to-avoid)
15. [HFT Realism Assessment](#15-hft-realism)
16. [Technical Communication](#16-technical-communication)

---

## 1. Honest Assessment

### Where You Stand

Your C++ baseline — STL fluency, pointer arithmetic, bit operations, memory model — puts you well ahead of most BTech grads starting this journey. That is a genuine advantage, not a minor one. Systems and HFT roles care deeply about low-level C++ instinct, and you already have the skeleton.

Your weak math background is the real constraint. The math curriculum you shared is a 1,200–1,800 hour, 12-month program designed for someone building from scratch toward quant research depth. **You do not need most of it.** Your path is HFT systems engineering and FAANG backend, not quant research. The math requirements are fundamentally different.

### What 6 Months Gets You

- **FAANG systems/backend:** Fully reachable. Strong DSA + OS + networking + distributed systems + systems design gets you interviews and offers at L4–L5 level.
- **HFT systems engineering (non-quant):** Reachable in 6 months for initial conversations. Hirable in 8–9 months. The delta is depth in lock-free concurrency, CPU/memory architecture, and LOB implementation.
- **HFT quant research:** Not the target. That path needs stochastic calculus, PDEs, the full math curriculum. Avoid that detour.

### The Three Real Risks

1. Splitting focus between too many subjects instead of going deep on the ones that matter.
2. Treating the math document as a requirement rather than a reference — it will consume all your time if you follow it naively.
3. Doing DSA in isolation with no real systems code. Both must run in parallel every single day.

---

## 2. Math Audit

The math curriculum you shared covers 14 major sections and 1,200–1,800 hours of study. Here is a precise audit for your specific path.


### 2.1 What to Study — Ordered by Priority
| # | Topic | Why You Need It | Hours |
|---|--------|----------------|--------|
| 1 | Complexity Analysis (Big O, Θ, Ω, Master Theorem, Amortized Analysis) | Every FAANG interview probes this. Cannot avoid. | 25–30 |
| 2 | Mathematical Induction | Loop invariants, recursion correctness, DP proofs. | 15–18 |
| 3 | Modular Arithmetic | Competitive programming requires modular inverse, fast exponentiation, CRT constantly. | 18–22 |
| 4 | Recurrence Relations | Solving recurrence equations is a daily occurrence in algorithm analysis. | 15–18 |
| 5 | Combinatorics | Counting problems, probability, pigeonhole principle in interviews and competitive programming. | 20–25 |
| 6 | Probability Basics | System design questions, HFT understanding, expected value analysis. | 25–30 |
| 7 | Bit Manipulation | You mostly know this. Focus on exercises to close gaps. | 5–8 |
| 8 | IEEE 754 + Floating Point Arithmetic | Critical for C++ systems and HFT. Price representation bugs are a real category of production incidents. | 12–15 |
| 9 | Graph Theory Mathematics | Algorithms come with mathematical structure (handshaking lemma, BFS layers, SCC theory). | 10–12 |
| 10 | Statistics Essentials | p50/p99 latency, control charts, production monitoring. Know percentiles thoroughly. | 10–12 |
| 11 | Concentration Inequalities (Markov, Chebyshev) | Useful for randomized algorithm analysis (hash tables, Bloom filters). Light coverage is sufficient. | 6–8 |
| 12 | Propositional Logic | De Morgan's laws and logical simplification of conditions. | 5–6 |
| 13 | Limit Order Book (LOB) & Market Microstructure | Conceptual understanding of order books, VWAP, market impact. Required for HFT systems interviews. | 20–25 |
| 14 | Linear Algebra (Vectors & Matrices) | Matrix exponentiation for competitive programming and linear recurrences. | 8–10 |

**Total mathematics hours for your path: 185–215 hours spread across 6 months.**  
This is roughly 1 hour per day on average, **integrated into DSA and systems blocks**, not a separate subject.

---

### 2.2 What to Skip — With Reasons

| # | Topic | Skip Reason |
|---|-------|-------------|
| 1 | Predicate Logic (Deep) | Surface-level understanding from propositional logic is enough. Full predicate logic is mainly for formal verification or academic CS. |
| 2 | Contradiction & Contrapositive Proofs | Read once (≈1 hour), but do not practice extensively. You need the concepts, not proof-writing fluency. |
| 3 | Sets, Relations & Functions (Formal Treatment) | Learn the vocabulary and basic concepts. Extensive proofs are unnecessary. |
| 4 | Generating Functions | Mostly useful for advanced combinatorics, research, or specialized CP problems. Skip for now. |
| 5 | Markov Chains (Full Treatment) | Understand the intuition and stationary distributions at a high level. Full mathematical treatment is overkill. |
| 6 | Probability Distributions, Hypothesis Testing & Regression | More relevant to statistics, data science, and experimentation than systems engineering. |
| 7 | Linear Transformations, Eigenvalues & SVD | Generally unnecessary for FAANG backend and HFT systems roles. More relevant to ML and quantitative research. |
| 8 | SIMD Mathematics & Compiler Optimization Theory | Interesting topic, but better studied after core systems fundamentals. Not interview-critical. |
| 9 | Calculus | Minimal relevance for systems engineering or HFT systems roles. |
| 10 | Optimization, Lagrange Multipliers & Gradient Descent | Primarily useful for machine learning and quantitative research. |
| 11 | Avellaneda-Stoikov & Almgren-Chriss Models | Quant research material. Learn the intuition only; avoid the mathematical details. |
| 12 | Full Quant Developer Mathematics Track | Misaligned with a systems-focused path. Skip unless targeting quantitative research/development specifically. |
| 13 | Real Analysis, Measure Theory, Topology, etc. | Advanced pure mathematics with little practical value for FAANG or HFT systems engineering. |

**Bottom line:** Of 14 sections, you need 6 fully, 4 partially, and should skip 4 entirely.

---

### 2.3 Math Integration Strategy

Math is not a separate subject in your plan. It gets absorbed into existing blocks:

- **Complexity Analysis, Induction, Recurrences** → Part of your DSA block in Month 1. When you study an algorithm, you analyze and prove its complexity. These are not extra hours.
- **Modular Arithmetic, Combinatorics** → Your DSA block in Month 1–2 naturally requires these for competitive programming problems. Learn them as you encounter them in problems.
- **Probability** → 30 minutes per day during your reading/review block in Month 2–3. Not a separate slot.
- **Floating Point / IEEE 754** → One focused week during C++ deep dive in Month 2. Then apply it to every piece of code you write forever.
- **LOB + Microstructure** → Part of your HFT specialization block in Month 5–6.

The document's 12-month curriculum assigns 45–60 hours to probability alone. You will cover it adequately in 25–30 hours because you are not building to PhD-level rigor — you are building to interview-ready competence.

---

## 3. Priority Ordering

### All Subjects — Strict Priority

1. **DSA** — Runs every single day without exception. Non-negotiable.
2. **Complexity Analysis + Recurrences** — Learn this in Week 1–2, apply it forever.
3. **Modern C++** — Your differentiator. Go deep in Phase 1.
4. **Linux + OS Internals** — Both paths require this. Start Day 1.
5. **Modular Arithmetic + Combinatorics** — Fuel for competitive programming.
6. **Computer Networking** — Phase 2 priority. Cannot do distributed systems without it.
7. **DDIA** — Read cover to cover in Month 3. No shortcuts.
8. **Probability Basics** — Phase 2–3. Needed for HFT understanding and system design.
9. **DBMS** — Phase 2, 2–3 weeks maximum.
10. **Systems Design Practice** — Phase 3.
11. **IEEE 754 + Floating Point** — Phase 2. One focused week.
12. **Lock-Free C++ + Concurrency** — Phase 3, HFT path.
13. **LOB + Market Microstructure** — Phase 3, HFT path.
14. **Rust basics** — Phase 3, Month 5. Gradual.
15. **Statistics Essentials** — Phase 2–3, absorbed into systems reading.
16. **Kotlin** — Postpone entirely past 6 months.

---

## 4. Schedule

### Daily Time Blocks

```
Block 1 — 08:00–10:00 (2 hrs)     DSA + Math Integration
Block 2 — 10:00–13:00 (2.5–3 hrs) Systems Primary (phase-dependent)
Block 3 — 14:00–15:00 (1 hr)      Reading + Concept Review
Evening  — 21:00–22:00 (1 hr)     Codeforces / Mock / Upsolve
```

**Total focused study: 5.5–6 hours/day consistently.**

Block 1 comes first because algorithmic thinking requires a fresh brain. Never do DSA after heavy systems reading.

### Weekly Structure

| Day | Morning Block | Afternoon Block | Evening |
|---|---|---|---|
| Mon | DSA — new pattern | Systems primary | Upsolve Mon's CF problem |
| Tue | DSA — new pattern | Systems primary | Review Tuesday concepts aloud |
| Wed | DSA — harder problem | Systems primary | Codeforces virtual round |
| Thu | DSA — variation | Systems primary | Upsolve Wed's round (mandatory) |
| Fri | DSA — review weak areas | Systems primary | Mock technical explanation (recorded) |
| Sat | DSA — 2 hrs | Full CF live round (3–4 hrs) | Upsolve + post-contest analysis |
| Sun | DSA — 2 hrs | Project work (2 hrs) | Weekly review + next week planning |

### Efficiency Ratings

Rate yourself 1–5 at the end of each day in the tracker:

- **5:** 3+ DSA problems solved, 3+ hrs systems, zero phone distractions, concepts stuck.
- **4:** 2 problems, 2.5 hrs systems, minor interruptions.
- **3:** 1 problem, 2 hrs systems — acceptable floor.
- **2:** Under 1.5 hrs total useful work — log the reason, fix tomorrow.
- **1:** Wasted day — write one honest sentence about why.

**Weekly minimum average: 3.0. Elite target: 4.0+**

---

## 5. Phase 1 — Month 1–2: Foundations

**Theme:** Get the fundamentals locked. Everything built on top depends on this phase being done properly.

### 5.1 Modern C++ (Month 1–2, runs throughout)

**Goal:** Write idiomatic Modern C++ by reflex, not by thought.

**Week 1–2:** Read *A Tour of C++* (Stroustrup) cover to cover. Code every example.  
Do not read passively. For each concept, write a small standalone program that demonstrates it.

**Key concepts to own completely:**
- Move semantics: understand when copies happen vs. moves, when to use `std::move`, what `noexcept` does to move constructors
- RAII: every resource you acquire must be wrapped. Write 3 RAII wrappers for different resources (file, mutex, socket)
- Smart pointers: `unique_ptr`, `shared_ptr`, `weak_ptr` — know the ownership semantics, know when `shared_ptr` becomes a performance problem
- `std::optional`, `std::variant`, `std::expected` — modern error handling without exceptions
- `constexpr` and compile-time computation — understand when the compiler can do work for you
- `std::thread`, `std::mutex`, `std::atomic`, `std::condition_variable` — concurrency foundations. You will go deep on this in Phase 3.
- Lambdas: capture by value vs. reference, mutable lambdas, generic lambdas in C++20
- Template basics: function templates, class templates, `auto` return types — do not attempt TMP yet
- STL algorithms: `std::sort`, `std::transform`, `std::accumulate`, `std::partition`, `std::lower_bound` — use these, do not reinvent them

**Reference:** cppreference.com open in a tab every single day. If you touch a function, read its cppreference page.

**CppCon Back to Basics talks to watch (2–3 per week, 50–60 min each):**
- "The Structure of a Program" — Matt Godbolt
- "Move Semantics" — Klaus Iglberger  
- "RAII and the Rule of Zero" — Arthur O'Dwyer
- "Smart Pointers" — Arthur O'Dwyer
- "Concurrency" — Mike Shah
- "Memory Model" — Mike Shah (critical for HFT path)
- "Templates" — Nicolai Josuttis (just Part 1)

---

### 5.2 Linux + OS Internals (Month 1–2, daily)

**Goal:** Linux as your native habitat. OS concepts understood at syscall level.

**Setup (Day 1):** Install Arch Linux or Debian on a VM or spare machine. Never go back to your previous OS for study. Every file you edit, every program you compile — do it on Linux.

**Read:** *OS Concepts* (Silberschatz) — Chapters 1–6, 8–10. Skip the rest.
- Ch 1–2: OS structure and services. Read fast.
- Ch 3–4: Processes and threads. Code the examples in C.
- Ch 5–6: CPU scheduling and synchronization. Understand semaphores, mutexes, condition variables at the implementation level.
- Ch 8–10: Memory management, virtual memory, paging. Map these concepts to what you know about pointers.

**Read alongside:** *Inside the Machine* (Jon Stokes). 12 chapters. Read one chapter every 3 days alongside Silberschatz. Maps CPU pipeline, cache hierarchy (L1/L2/L3), TLB, and NUMA to what OS chapters describe conceptually.

**Code alongside reading (mandatory — every chapter gets a C program):**
```c
// Ch 3 exercise: fork and exec
pid_t pid = fork();
if (pid == 0) { execl("/bin/ls", "ls", "-la", NULL); }
wait(NULL);

// Ch 4 exercise: pthreads with mutex
pthread_mutex_t lock;
pthread_mutex_init(&lock, NULL);
// ... create threads, lock, increment shared counter, unlock

// Ch 5 exercise: semaphores
sem_t sem;
sem_init(&sem, 0, 1);
// ... producer-consumer with semaphores

// Ch 8 exercise: mmap
void *ptr = mmap(NULL, 4096, PROT_READ|PROT_WRITE,
                 MAP_ANON|MAP_PRIVATE, -1, 0);
// ... write, read, munmap
```

**Tools to master in Phase 1:**
- `strace` — trace system calls. Run it on your programs. This makes OS reading real.
- `gdb` — 5 core commands: `break`, `run`, `next`, `print`, `bt`. Enough to debug your C programs.
- `valgrind --leak-check=full` — run on every C/C++ program. Fix every leak.
- `htop`/`btop` — watch CPU cores, memory, processes as you read about scheduling.
- `perf stat ./myprogram` — CPU cycles, cache misses, branch mispredictions. This is your first window into hardware-level performance.

---

### 5.3 Bash + Neovim (Week 1, then ongoing)

**Neovim setup (Day 1, spend at most 4 hours, no more):**
Start from `kickstart.nvim` as base. Add exactly these plugins — nothing more:
- `nvim-lspconfig` with clangd for C/C++ and rust-analyzer for later
- `telescope.nvim` for fuzzy file finding
- `nvim-treesitter` for syntax highlighting
- `conform.nvim` for formatting (clang-format, rustfmt)
- `oil.nvim` for file browsing

Set `<leader>` to space. Learn these keybindings in Week 1 and use them until they are reflex:
- `<leader>ff` — find file, `<leader>fg` — grep, `<leader>fb` — buffers
- `gd` — go to definition, `gr` — references, `K` — hover docs
- `<C-w>` splits, `<C-h/j/k/l>` navigation between splits
- `gcc` — comment toggle, `<C-o>/<C-i>` — jump back/forward

**tmux (Day 1):** Install, set prefix to `Ctrl+a`. Learn: `prefix + |` vertical split, `prefix + -` horizontal split, `prefix + z` zoom pane, `prefix + [` copy mode. You will always have: left pane = editor, right pane = compiler/runner.

**Bash:** Do not read a book. Write real scripts starting Week 1:
- Auto-commit your LeetCode solutions to GitHub daily (cron + git script)
- Build script for your C++ projects (compile, run tests, show output)
- Log parser that extracts your daily study hours from a text log
- Backup script: tar and copy your project directories

You learn Bash by needing it, not by reading it.

---

### 5.4 Mathematics — Phase 1 Integration

**Week 1–2 alongside DSA (15–18 hours total):**

**Complexity Analysis** — This is not optional and not light.

Start by reading CLRS Chapter 3 (Growth of Functions) carefully. Then Chapter 2.2 (Analyzing Algorithms). Do every exercise in section 3-1 and 3-2. The exercises are where the understanding happens.

What you must be able to do cold after Week 2:
- State the formal definitions of O, Θ, Ω, o, ω
- Prove that f(n) = 3n² + 5n + 7 = Θ(n²) formally with constants
- Order any 10 functions by asymptotic growth
- Apply all 3 cases of Master Theorem correctly
- Solve a recurrence by substitution (guess and verify by induction)
- Determine the exact Big-O of any piece of code you write

```
Common recurrences to know cold:
T(n) = T(n/2) + 1          → O(log n)        [binary search]
T(n) = 2T(n/2) + n         → O(n log n)      [merge sort]
T(n) = 2T(n/2) + n²        → O(n²)           [Master Theorem Case 3]
T(n) = 4T(n/2) + n         → O(n²)           [Master Theorem Case 1]
T(n) = T(n-1) + n          → O(n²)           [selection sort]
T(n) = 2T(n-1) + 1         → O(2ⁿ)           [naive recursion]
```

**Mathematical Induction (Week 3–4, 10–12 hours):**

Read MIT MCS Chapter 3 (available free at MIT OCW). Do exercises 3.1–3.5 on paper.

You need induction for:
- Proving your recursive algorithms correct (especially in Phase 2 for graphs and DP)
- Writing loop invariants in interviews
- Understanding why amortized analysis works (CLRS Chapter 17)

Practice problems (write proofs on paper):
1. Prove that T(n) = 2T(n/2) + n = O(n log n) by substitution
2. Prove binary search is correct by induction on the size of the search space
3. Prove that a binary tree with n internal nodes has n+1 leaves
4. Prove that the sum of degrees in a graph equals 2|E| (handshaking lemma)

**Modular Arithmetic (Month 1–2, 15–18 hours):**

Read CLRS Chapter 31.1–31.5. This directly enables competitive programming.

Implement these in C++ and understand every line:
```cpp
// Extended GCD — returns gcd, sets x, y such that ax + by = gcd
long long extgcd(long long a, long long b, long long &x, long long &y) {
    if (b == 0) { x = 1; y = 0; return a; }
    long long x1, y1;
    long long g = extgcd(b, a % b, x1, y1);
    x = y1; y = x1 - (a / b) * y1;
    return g;
}

// Modular inverse using extended GCD
long long modinv(long long a, long long m) {
    long long x, y;
    if (extgcd(a, m, x, y) != 1) return -1; // No inverse
    return (x % m + m) % m;
}

// Fast modular exponentiation — O(log exp)
long long modpow(long long base, long long exp, long long mod) {
    long long result = 1;
    base %= mod;
    while (exp > 0) {
        if (exp & 1) result = result * base % mod;
        base = base * base % mod;
        exp >>= 1;
    }
    return result;
}

// Modular inverse via Fermat's little theorem (p must be prime)
// a^(p-2) mod p = a^(-1) mod p
long long fermat_inv(long long a, long long p) {
    return modpow(a, p - 2, p);
}
```

These three functions cover 80% of modular arithmetic in competitive programming. The standard modulus in CP problems is `1e9 + 7` (a prime — that's why Fermat's little theorem applies).

---

### 5.5 DSA — Phase 1 (Month 1–2)

**Month 1 topics:** Arrays, strings, hashmaps, sliding window, two pointers, binary search (all variations), recursion, sorting.

**Month 2 topics:** Linked lists, stacks, queues, heaps, trees (BST, traversals, LCA), tries.

**Daily structure:**
- 1 new pattern problem (understand the approach deeply before coding)
- 1 variation problem (apply the pattern differently)
- 30-minute review of yesterday's problem — can you solve it in 15 minutes now?

**Neetcode.io roadmap** — follow the order exactly. Do not jump around.

**LeetCode category distribution for Phase 1:**
```
Arrays + Sliding Window:    30 problems
Binary Search (all forms):  20 problems  
Hashmaps + Sets:            15 problems
Two Pointers:               15 problems
Linked Lists:               15 problems
Stacks + Queues:            15 problems
Trees (BFS/DFS, BST):       20 problems
Heaps:                      10 problems
──────────────────────────────────────
Phase 1 total target:      140–160 problems
```

**Target by end of Phase 1:** 180–200 LeetCode problems. Comfortable with mediums in 25–30 minutes.

**Codeforces in Phase 1:**
- Weeks 1–4: Div 3 rounds only. Target A, B, occasional C.
- Weeks 5–8: Div 3 + Div 2. Target A, B consistently. Working on C.
- Upsolve every single contest without exception. Upsolving is where 70% of the learning happens.
- If you do not upsolve, the contest was wasted time.

**Codeforces target at Phase 1 end:** Rating 1300–1500.

---

## 6. Phase 2 — Month 3–4: Core Systems

**Theme:** Go wide on systems knowledge. DDIA, networking, and DBMS form the foundation for every distributed systems conversation.

### 6.1 Computer Networking (Month 3)

**Read:** Kurose & Ross (Top Down Approach), Chapters 1–4 thoroughly. Chapters 5–6 selectively.

**Supplement:** Beej's Guide to Network Programming (free at beej.us/guide/bgnet). This is the practical counterpart — after reading Kurose Ch 3 (transport layer), implement what you just read.

**What to implement — in order:**
1. UDP echo server and client (start here — simpler)
2. TCP echo server (blocking I/O first, understand the syscalls)
3. Multi-client TCP server using `select()` (understand file descriptor sets)
4. Multi-client TCP server using `epoll` (the real way — edge-triggered, non-blocking)

Understanding *why* epoll beats select:
- `select` is O(n) per call — iterates all file descriptors
- `epoll` is O(active events) per call — the kernel maintains the interest list
- For a server with 10,000 connections and 10 active at any moment: select = O(10,000) per iteration, epoll = O(10) per iteration

**Active reading (Cloudflare Blog):** Read one Cloudflare blog post per week throughout Phase 2. These posts explain real networking problems at production scale — TCP head-of-line blocking, QUIC, anycast routing, DDoS mitigation. This is how real engineers talk about networking.

**What to know cold before moving to Phase 3:**
- TCP three-way handshake, four-way close, TIME_WAIT state and why it exists
- TCP congestion control (slow start, AIMD, Nagle algorithm)
- DNS resolution chain (resolver → root → TLD → authoritative)
- HTTP/1.1 keep-alive vs HTTP/2 multiplexing vs HTTP/3 over QUIC
- TLS handshake at a design level (not implementation details, just what happens)
- What happens when you type `google.com` — every layer, in order

---

### 6.2 DDIA — Designing Data-Intensive Applications (Month 3)

Read this book cover to cover. Take notes. Do not rush it.

**This is the single most important book in the plan for systems design interviews.**

It teaches you to reason about systems the way senior engineers do — not "what technology do I use" but "what guarantees does this technology provide and what does it trade away."

**Reading schedule (Chapter by Chapter):**

| Week | Chapters | Focus |
|---|---|---|
| Week 1 | 1–3 | Data models, storage engines, how databases actually store data on disk |
| Week 2 | 4–6 | Encoding, replication — understand leader/follower, multi-leader, leaderless |
| Week 3 | 7–9 | Transactions (ACID in depth), distributed systems problems, consistency and consensus |
| Week 4 | 10–12 | Batch processing, stream processing, the future of data systems |

**What to extract from each chapter:**

*Chapter 3 (Storage Engines):* Why B-Trees vs LSM-Trees? Write a paragraph comparing them. This question appears in FAANG systems design interviews.

*Chapter 5 (Replication):* What is replication lag? What are the consistency guarantees of eventual consistency vs. read-your-writes vs. monotonic reads? Can you explain split-brain?

*Chapter 7 (Transactions):* Explain the difference between Read Committed, Repeatable Read, Serializable, and Snapshot Isolation. What is a phantom read? When does 2PL fail? When does MVCC win?

*Chapter 8 (Distributed Systems):* The fundamental problems — clocks are unreliable, networks are unreliable, processes can fail. How does everything else build on top of these constraints?

*Chapter 9 (Consistency and Consensus):* What is linearizability? What is causality? What does Paxos/Raft actually guarantee? What does "consensus" even mean?

**After reading:** Watch Martin Kleppmann's talks on YouTube (he wrote DDIA). His talk "Is Kafka a Database?" and "Distributed Systems" lectures add depth to the book.

---

### 6.3 DBMS (Month 3, 2–3 weeks)

**Read:** Your DBMS Concepts book, focused chapters only:
- Transactions: ACID properties in depth, isolation levels, MVCC
- Indexing: B+ tree structure, when indexes help vs. hurt, covering indexes, composite index order
- Query execution: what does `EXPLAIN ANALYZE` show you, join algorithms (nested loop, hash join, sort-merge join)
- Concurrency control: two-phase locking, deadlock detection, optimistic concurrency

**Practical (mandatory):** Install PostgreSQL. Run real queries. Understand the output:
```sql
-- Analyze a real query
EXPLAIN ANALYZE SELECT * FROM orders WHERE customer_id = 1234;
-- Understand: Seq Scan vs Index Scan vs Bitmap Index Scan
-- Understand: cost estimates, actual rows, actual time
-- Understand: when PostgreSQL is wrong about statistics

-- Understand transaction isolation
BEGIN ISOLATION LEVEL SERIALIZABLE;
-- ... queries ...
COMMIT;
```

**Target knowledge:** Explain to an interviewer why an index on `(customer_id, created_at)` is useful for `WHERE customer_id = X ORDER BY created_at` but not for `WHERE created_at > X`. Understand this at the B+ tree level.

---

### 6.4 Mathematics — Phase 2 Integration

**Combinatorics (Month 3, absorbed into DSA, 20–25 hours):**

When you start doing DP problems that involve counting (LC 62 Unique Paths, LC 518 Coin Change 2, LC 70 Climbing Stairs variants), the underlying math is combinatorics. Learn it through the problems.

Specifically need to understand:
- nCr computation modulo a prime (Pascal's triangle DP + Fermat inverse)
- Inclusion-exclusion principle (derangements, counting with restrictions)
- Stars and bars (distributing items into bins — shows up in partition DP)
- Pigeonhole principle (hash collision arguments, birthday paradox)

Implement nCr precomputation:
```cpp
const long long MOD = 1e9 + 7;
const int MAXN = 1e6 + 5;
long long fact[MAXN], inv_fact[MAXN];

void precompute() {
    fact[0] = 1;
    for (int i = 1; i < MAXN; i++) fact[i] = fact[i-1] * i % MOD;
    inv_fact[MAXN-1] = modpow(fact[MAXN-1], MOD-2, MOD);
    for (int i = MAXN-2; i >= 0; i--) inv_fact[i] = inv_fact[i+1] * (i+1) % MOD;
}

long long nCr(int n, int r) {
    if (r < 0 || r > n) return 0;
    return fact[n] * inv_fact[r] % MOD * inv_fact[n-r] % MOD;
}
```

**Probability (Month 3, reading block, 25–30 hours total):**

Read Blitzstein & Hwang Chapters 1–6. This is the probability book recommended in the curriculum. It is genuinely excellent — clear, rigorous enough, and well-exercised.

Chapter priority:
- Ch 1–2: Counting + probability axioms — mandatory, deep
- Ch 3: Conditional probability and Bayes — mandatory, very deep. Bayes shows up in HFT interviews.
- Ch 4: Discrete random variables — mandatory
- Ch 5–6: Continuous RVs, expectation — mandatory
- Ch 7+: Read lightly, do not do exercises beyond a few per chapter

Use your reading block (1 hr/day) for Blitzstein in Month 3. One chapter every 3–4 days.

**IEEE 754 + Floating Point (Month 2, Week 7–8, 12–15 hours):**

Read Section 8 of the math curriculum entirely. This section is excellent and directly applicable.

Critical concepts to own:
- Why `0.1 + 0.2 != 0.3` in floating point (binary fractions)
- Machine epsilon: what it means, how to use it for comparison
- Catastrophic cancellation: recognize it, know the stable alternatives
- NaN propagation: how it silently corrupts downstream computation
- Fixed-point arithmetic: why HFT uses integers scaled by 10^4 for prices, not doubles

**In your code from now on:**
```cpp
// NEVER do this for financial or precision-critical code:
if (a == b) { ... }           // Floating point equality is almost always wrong

// DO this:
bool approx_equal(double a, double b, double eps = 1e-9) {
    return std::abs(a - b) <= eps * std::max(1.0, std::max(std::abs(a), std::abs(b)));
}

// For prices in a trading system — use fixed point:
int64_t price_in_ticks = 100250;  // $100.25 stored as 100250 (precision = 0.01)
int64_t quantity = 100;
int64_t notional = price_in_ticks * quantity;  // No floating point involved
```

---

### 6.5 DSA — Phase 2 (Month 3–4)

**Month 3 topics:** Graphs (BFS/DFS applications, Dijkstra, Bellman-Ford, topological sort, union-find, MST, SCCs)

**Month 4 topics:** Dynamic Programming (all major patterns), backtracking, divide and conquer

**DP patterns to cover (in this order):**
1. 1D DP: climbing stairs, house robber, coin change, word break
2. 2D DP: unique paths, grid-based DP, LCS, edit distance
3. Knapsack (0/1, unbounded, bounded): the template problems
4. Interval DP: matrix chain multiplication, burst balloons, palindrome partitioning
5. DP on trees: diameter, max path sum, re-rooting technique
6. Bitmask DP: traveling salesman on small graphs, subset problems
7. Digit DP: count numbers with specific properties in a range

**The right way to learn DP:** Every DP problem has a state definition and a transition. Write these two things down before you code. If you cannot state them in words, you do not understand the problem yet.

```
State: dp[i] = maximum profit achievable from day i to the end
Transition: dp[i] = max(dp[i+1], prices[i+j] - prices[i] + dp[i+j+1]) for all j > 0
Base case: dp[n] = 0 (no profit from no days left)
```

**Codeforces in Phase 2:**
- Div 2 rounds. Target A, B, C consistently. D occasionally.
- Target rating: 1500–1700 by end of Phase 2.
- CSES Problem Set: complete the graph section and DP section. CSES problems are cleaner than Codeforces for learning patterns without the competitive noise.

**LeetCode target by end of Phase 2:** 350–380 problems. Hard problems starting to feel solvable in 45–60 minutes.

---

## 7. Phase 3 — Month 5–6: Specialization + Interviews

**Theme:** Deep expertise in systems, HFT-specific knowledge, and aggressive interview preparation.

### 7.1 Systems Design

**Primary resource:** DDIA (already read in Phase 2). Apply it.

**Supplementary:** Engineering blogs — not courses, not YouTube lectures. Real engineering blogs from companies that solve real problems:
- Cloudflare: networking, performance, distributed systems
- Discord: scaling, WebSocket, message delivery
- Uber: microservices, matching, real-time systems
- Figma: collaborative editing, conflict resolution
- DoorDash: reliability engineering, delivery routing

**Systems to design (practice these until the decisions feel natural):**

1. **URL Shortener** — consistent hashing, base62 encoding, cache layers, redirect vs. proxy
2. **Distributed Rate Limiter** — token bucket vs. leaky bucket, Redis vs. in-memory, sliding window
3. **Key-Value Store (Distributed)** — consistent hashing, replication factor, quorum reads/writes, compaction
4. **Pub-Sub System** — fan-out, message ordering guarantees, at-least-once vs. exactly-once delivery
5. **Web Crawler** — BFS/DFS tradeoffs, politeness, URL frontier, deduplication at scale
6. **Real-Time Leaderboard** — sorted sets, approximate ranking, segment trees
7. **Notification System** — push vs. pull, read receipts, offline delivery, fan-out writes

**For each design:** Begin with requirements (functional + non-functional), estimate scale, design the data model, then the API, then the architecture. Always discuss the consistency/availability tradeoff explicitly. Know what you are giving up when you choose eventual consistency.

---

### 7.2 Lock-Free C++ + Concurrency (HFT Path)

**Read:** *C++ Concurrency in Action* (Anthony Williams), Chapters 5–7. These chapters cover the memory model, atomic operations, and lock-free data structures. This is the hardest technical reading in the plan — go slowly.

**The C++ Memory Model — Must Own Completely:**
```cpp
// Memory orderings — from weakest to strongest:
std::memory_order_relaxed   // No ordering guarantees. Use for counters.
std::memory_order_acquire   // Load: see all writes that happened before the matching release
std::memory_order_release   // Store: all previous writes visible to matching acquire
std::memory_order_acq_rel   // Both acquire and release (read-modify-write)
std::memory_order_seq_cst   // Total sequential consistency — safest, slowest

// A lock-free flag pattern:
std::atomic<bool> ready{false};

// Producer thread:
data = 42;                              // prepare data
ready.store(true, memory_order_release); // make it visible

// Consumer thread:
while (!ready.load(memory_order_acquire)); // wait
use(data);                               // safe — acquire sees everything before release
```

**Implement these from scratch (no peeking at the solution until you've tried for 30+ minutes):**

1. Lock-free SPSC (single-producer, single-consumer) queue using a ring buffer and two atomics
2. Lock-free stack using CAS (compare-and-swap) — implement the ABA problem workaround
3. Cache-line aligned wrapper to eliminate false sharing

```cpp
// False sharing example — naive:
struct Counters {
    std::atomic<int> a;  // Thread 1 writes this
    std::atomic<int> b;  // Thread 2 writes this
    // a and b are on the same cache line (64 bytes) → cache invalidation on every write
};

// Fixed version — cache-line padding:
struct alignas(64) CounterA { std::atomic<int> val; char pad[60]; };
struct alignas(64) CounterB { std::atomic<int> val; char pad[60]; };
// Now a and b are on different cache lines → no false sharing
```

**Benchmark everything you implement.** Use `std::chrono::high_resolution_clock` or better — `rdtsc` (CPU timestamp counter) for sub-microsecond measurements:
```cpp
static inline uint64_t rdtsc() {
    uint32_t lo, hi;
    __asm__ volatile ("rdtsc" : "=a"(lo), "=d"(hi));
    return ((uint64_t)hi << 32) | lo;
}
```

---

### 7.3 HFT Math — LOB + Microstructure (Month 5–6)

This is Section 11 of the math curriculum. Cover Sections 11.1–11.3. Skip 11.4–11.5.

**Limit Order Book — Implement It:**

The LOB is the core data structure in market making. Implement it in C++ as a project.

```cpp
// Price level structure
struct PriceLevel {
    double price;
    std::deque<Order> orders;  // FIFO queue at each price level
    int64_t total_qty;
};

// LOB: sorted map of price levels
std::map<double, PriceLevel> bids;   // Descending: highest bid first → use reverse iterator
std::map<double, PriceLevel> asks;   // Ascending: lowest ask first → begin()

// Matching: when a market buy order arrives:
// Match against the best ask (asks.begin()), fill FIFO at that level
// If quantity remaining, move to next level, repeat
```

**VWAP and TWAP — Implement Both:**
- TWAP execution scheduler: divide order into N equal time slices
- VWAP calculation from a trade tape: `Σ(price × volume) / Σ(volume)`

**Market Impact — Understand the Intuition:**
- Every large order moves the price against you (market impact)
- Square-root law: impact ≈ σ × √(Q/ADV) where Q = order size, ADV = average daily volume
- This is why large orders use VWAP/TWAP — spreading reduces impact

**What HFT systems interviews test on microstructure:**
- Explain the bid-ask spread and its three components (inventory cost, order processing, adverse selection)
- What is adverse selection? Why do market makers widen spread around news events?
- What is queue position and why does it matter for fill probability?
- Explain VWAP execution and when you'd use it vs. market orders

---

### 7.4 Rust (Month 5, gradual)

**Read:** *The Rust Programming Language* (free at doc.rust-lang.org/book), Chapters 1–15.

Do not try to use Rust for your main projects. The goal in 6 months is:
- Own the ownership and borrowing model conceptually
- Understand lifetimes at a high level
- Do Rustlings exercises (all of them)
- Implement a linked list and binary tree in Rust (famous for being hard in Rust — teaches ownership)

By Month 6 you should be able to explain: "In C++ you manage memory manually and can have use-after-free bugs. In Rust the compiler rejects your code at compile time if you'd have a use-after-free. The mechanism is the ownership + borrow checker. Here is how it works: ..."

That explanation, delivered confidently, is all you need in 6 months. Production Rust systems work is Month 7+.

---

### 7.5 Mock Interviews (Month 5–6)

Starting Month 5: 3 mock interviews per week minimum.

**Pramp** — Free, peer-to-peer mocks. Do both sides (interviewer and interviewee). Being the interviewer teaches you what good vs. bad answers look like.

**The 4-step solving method (do this every single time, even alone):**

1. **Restate + clarify:** "So I need to find the kth largest element in a stream. Is the stream unbounded? Can I use extra space?" Do not code yet.
2. **Brute force first:** "The naive approach is to sort after each insertion — O(n log n) per insert. That's too slow. Now let me optimize."
3. **Optimal solution:** "I'll maintain a min-heap of size k. Every new element: if it's larger than the heap's minimum, pop the minimum and push the new element."
4. **Analyze and code:** State the complexity before you code, then code it cleanly. Test with 2–3 examples, including edge cases.

**Recording yourself:** Once a week, record yourself explaining a problem solution as if talking to an interviewer. Watch the playback. You will immediately spot the gaps — excessive filler words, imprecise language, skipping steps. Fix one thing per recording.

---

## 8. DSA Milestones

### 8.1 LeetCode

| Milestone | Target Date | Problems | Key Criteria |
|---|---|---|---|
| 100 problems | Day 31 | Arrays, sliding window, binary search, hashmaps, linked lists | Easy in 10 min, Medium in 25–30 min |
| 200 problems | Day 60 | + Trees, heaps, stacks | Medium in 20–25 min consistently |
| 300 problems | Day 90 | + Graphs (BFS/DFS), Union-Find | Starting hard problems |
| 380 problems | Day 120 | + DP (1D, 2D, knapsack) | Mediums in under 20 min |
| 450 problems | Day 150 | + Interval DP, bitmask, advanced graphs | Hard in 40–50 min regularly |
| 500+ problems | Day 175 | All categories complete | Hard problems in 30–40 min |

**Category coverage you must ensure (avoid random grinding):**

| Category | Target Count | Priority |
|---|---|---|
| Arrays + Sliding Window | 30 | Week 1–2 |
| Binary Search (all forms) | 20 | Week 1–2 |
| Hashmaps + Sets | 15 | Week 1–2 |
| Two Pointers | 10 | Week 1–2 |
| Linked Lists | 15 | Week 3–4 |
| Stacks + Monotonic Stack | 15 | Week 3–4 |
| Trees (DFS/BFS, BST, LCA) | 25 | Week 4–6 |
| Heaps + Priority Queue | 15 | Week 5–6 |
| Graphs (BFS/DFS, all apps) | 35 | Week 7–10 |
| Topological Sort | 10 | Week 9–10 |
| Dijkstra + Shortest Paths | 10 | Week 9–10 |
| Union-Find | 10 | Week 9–10 |
| Dynamic Programming | 50 | Week 10–18 |
| Backtracking | 15 | Week 12–14 |
| Tries | 10 | Week 14–16 |
| Segment Tree / BIT | 10 | Week 16–20 |
| Bit Manipulation | 10 | Week 1–4 (you partly know this) |
| String Algorithms (KMP, Z) | 10 | Week 18–22 |

**Total: 335 problems in categories above + 165 additional = 500+.**

---

### 8.2 Codeforces

| Month End | Target Rating | Division | Consistency Target |
|---|---|---|---|
| Month 1 | 1200–1400 | Div 3 | A, B consistently; C occasionally |
| Month 2 | 1400–1500 | Div 3 + Div 2 | A, B in Div 2; C in Div 3 |
| Month 3 | 1550–1650 | Div 2 | C consistently; D occasionally |
| Month 4 | 1650–1800 | Div 2 | D occasionally; C in under 30 min |
| Month 5 | 1800–1900 | Div 2 | D/E territory; Div 1 C attempts |
| Month 6 | 1900+ | Div 1/2 | Competing in Div 1 rounds |

**Non-negotiable rules:**
- Compete in every round possible (live, not virtual). Real-time pressure is different.
- Upsolve every contest without exception. Write your own solution, do not read editorial first — try for 30 more minutes before looking.
- After upsolving, write one sentence about what pattern or technique you missed.

**CSES Problem Set — do these in Phase 1–2:**
Complete the following CSES sections before going deep on Codeforces rating:
- Sorting and Searching (19 problems)
- Graph Algorithms (19 problems)
- Dynamic Programming (19 problems)
- Tree Algorithms (16 problems)

CSES problems are cleaner and harder than equivalent-rated CF problems. Completing all 4 sections will push your CF rating to ~1600 naturally.

---

## 9. Mathematics Milestones

| Milestone | Phase | How to Verify |
|---|---|---|
| Master Theorem — apply all 3 cases correctly | Month 1 Week 2 | Solve 10 recurrences in CLRS Ch 4 exercises |
| Big-O — prove formally with constants | Month 1 Week 1 | Do exercises 3-1, 3-2 in CLRS |
| Induction — write a complete proof | Month 1 Week 3–4 | Prove 5 algorithm properties from scratch |
| Extended GCD + modpow implemented | Month 1 | Passes Codeforces problem requiring modular inverse |
| Amortized analysis of std::vector | Month 2 | Explain all 3 methods (aggregate, accounting, potential) in an interview |
| nCr mod prime precomputation working | Month 2 | Solves LC 62, 518, and equivalent CF problems |
| Probability — Bayes' theorem cold | Month 3 | Solve the medical test problem and 5 variants without reference |
| IEEE 754 — explain catastrophic cancellation | Month 2 | Identify the bug in 3 provided floating-point code samples |
| Fixed-point price arithmetic implemented | Month 3 | Order value calculation without any doubles |
| LOB — implement full matching engine | Month 5–6 | GitHub project: matching engine with FIFO queue at each price level |
| VWAP implemented from trade tape | Month 5 | Correct output on 10 test cases |

---

## 10. Books and Resources

### Core Books (Read in Order)

| Book | When | Chapters | Notes |
|---|---|---|---|
| *A Tour of C++* (Stroustrup) | Month 1–2 | All | Code every example. Do not read passively. |
| *OS Concepts* (Silberschatz) | Month 1–2 | 1–6, 8–10 | Write syscall programs alongside every chapter. |
| *Inside the Machine* (Stokes) | Month 1 | All | Short book. Read alongside OS Concepts. |
| *Introduction to Probability* (Blitzstein) | Month 3 | 1–6 | One chapter every 3–4 days during reading block. |
| *Computer Networking: Top Down* (Kurose) | Month 3 | 1–4 carefully, 5–6 selectively | Implement socket programs alongside Ch 2–3. |
| *DDIA* (Kleppmann) | Month 3 | All | Active notes. Slowest read in the plan. |
| *DBMS Concepts* (Ramakrishnan) | Month 3–4 | Transactions, Indexing, Query Exec | Run every query on real PostgreSQL. |
| *CLRS* | Reference | Ch 2–5, 10–17, 22–26, 31 | Use as reference when encountering algorithms, not cover-to-cover. |
| *C++ Concurrency in Action* (Williams) | Month 5–6 | 5–7 | The hardest read. Go slowly. |
| *The Rust Programming Language* | Month 5 | 1–15 | Free at doc.rust-lang.org. Rustlings alongside. |
| *The Linux Programming Interface* (Kerrisk) | Month 2–5 ongoing | As needed | Expensive but definitive. Use as reference for syscall projects. |

### Math Resources (Specific)

| Resource | Topics | Where |
|---|---|---|
| CLRS Ch 2–5, 31 | Complexity analysis, Master Theorem, number theory | Your CLRS copy |
| MIT MCS (free PDF) | Logic, induction, sets, graph theory math, probability | MIT OCW 6.042J |
| Blitzstein & Hwang | Probability full treatment | Book or free PDF online |
| CP-algorithms.com | Modular arithmetic, combinatorics, number theory with code | cp-algorithms.com |

### Online Resources

| Resource | Purpose | Priority |
|---|---|---|
| Neetcode.io | LeetCode ordering and pattern grouping | ★★★★★ |
| CSES Problem Set (cses.fi) | Clean structured problems, pre-CF warmup | ★★★★★ |
| cppreference.com | Daily C++ reference | ★★★★★ |
| Cloudflare Blog | Real systems engineering writing | ★★★★ |
| Beej's Guide to Network Programming | Practical socket programming | ★★★★ |
| CppCon Back to Basics (YouTube) | Modern C++ concepts via talks | ★★★★ |
| Martin Kleppmann talks (YouTube) | DDIA depth | ★★★★ |
| Pramp (pramp.com) | Free peer mock interviews | ★★★ |
| Discord: CS Career Hub | CP community, upsolve partners | ★★★ |

---

## 11. Projects

Build these in order. Each project should have a proper README.

### Project 1: Mini Shell in C (Month 2, ~2 weeks)

**What:** A shell that supports command execution, pipes, I/O redirection, and basic job control.

**Concepts demonstrated:** `fork(2)`, `exec(2)`, `pipe(2)`, `wait(2)`, `signal(2)`, `SIGCHLD`, `SIGSTOP`/`SIGCONT`, file descriptor manipulation.

**Minimum features:**
- Execute commands: `ls -la`, `grep pattern file`
- Pipes: `ls -la | grep .cpp`
- I/O redirection: `cat file.txt > output.txt`
- Background jobs: `./long_process &`
- Built-ins: `cd`, `exit`, `jobs`, `fg`, `bg`

**README must explain:** How you handle orphan processes, how signal handling works, what happens to file descriptors across fork.

---

### Project 2: TCP Echo Server with epoll (Month 3, ~1 week)

**What:** A non-blocking event-driven server that handles 100+ simultaneous connections using epoll.

**Concepts demonstrated:** `epoll_create1`, `epoll_ctl`, `epoll_wait`, non-blocking sockets (`O_NONBLOCK`), edge-triggered vs. level-triggered mode.

**README must explain:** Why epoll beats select for high connection counts (with complexity analysis), what edge-triggered mode means and when it bites you.

---

### Project 3: HTTP/1.1 Server in C++ (Month 3–4, ~3 weeks)

**The most interview-relevant project in the plan.**

**What:** A server that parses HTTP/1.1 requests, serves static files, handles concurrent connections via a thread pool.

**Concepts demonstrated:** HTTP request parsing (method, path, headers, body), thread pool with work queue, `Content-Type` header logic, keep-alive connections, `send(2)`/`recv(2)` with partial reads.

**Minimum spec:**
- Handle `GET` requests for static files
- Correct `Content-Type` headers (html, css, js, jpeg, png, plain)
- `Connection: keep-alive` support
- Thread pool with configurable worker count
- 404 and 500 error responses

**README must explain:** Design decisions — why thread pool vs. fork-per-request, how you handle partial sends, what happens when the server is under load.

---

### Project 4: Key-Value Store in C++ with WAL (Month 4–5, ~3 weeks)

**What:** An in-memory hashmap with a write-ahead log for crash recovery.

**DDIA Chapter 3 is the conceptual foundation for this project.** Reading Ch 3 before building this makes the design decisions obvious.

**Minimum spec:**
- `GET key`, `SET key value`, `DEL key` via TCP (wire protocol of your design)
- Write-ahead log: every mutation appended to a log file before applied to memory
- Compaction: when log exceeds N entries, rewrite only the live key-value pairs
- Recovery: on startup, replay log to rebuild in-memory state

**README must explain:** What the WAL buys you (durability without fsync on every write), why compaction is necessary, what would be needed to support replication (explain without implementing).

---

### Project 5: Lock-Free SPSC Queue (Month 5–6, ~2 weeks, HFT path)

**What:** A single-producer, single-consumer lock-free ring buffer, cache-line aligned, with correct memory ordering, benchmarked against a mutex-based version.

**Concepts demonstrated:** `std::atomic`, `memory_order_acquire`/`release`, cache line padding (64 bytes), false sharing, `alignas(64)`.

**The benchmark must show:** At what throughput does the lock-free version win over mutex? (Typically: at high throughput, lock-free wins by 2–5x. At low throughput, the difference is small.)

**README must explain:** The memory ordering choices (why acquire/release and not relaxed), the ABA problem and why SPSC avoids it, what cache line alignment achieves numerically.

---

### Project 6: LOB Matching Engine (Month 6, ~2 weeks, HFT path)

**What:** A simplified limit order book with a matching engine — accepts orders, matches them, reports fills.

**Minimum spec:**
- Price levels as sorted map (bids descending, asks ascending)
- FIFO queue at each price level
- Market order matching: walk the book, fill completely if possible
- Limit order: add to book if no immediate match, else match and add remainder
- Cancel order by ID
- VWAP calculation on executed trades
- Latency measurement per order using `rdtsc`

**This project is gold in HFT systems interviews.** Walk through the architecture, the data structure choices, and the latency profile in your interview.

---

## 12. Portfolio and Freelancing

### Timeline

**Month 1–2:** Get online. Portfolio site using Astro or plain HTML/CSS on Vercel — free, takes 2–3 hours. Do not spend more than a weekend on this in Phase 1. Push all projects to GitHub with public repos from Day 1. Green squares every day.

**Month 3:** Write your first technical blog post: "Building a mini shell in C — what fork/exec/pipes actually do." Post on your portfolio + Dev.to + LinkedIn. Do not wait for it to be perfect. Ship it.

**Month 4:** Buy a domain (`yourname.dev`, ~₹1,200/year on Namecheap). Set up a VPS (Hostinger ₹349/month or Hetzner CX22 ~₹380/month). This is not optional — a self-hosted VPS running your projects demonstrates Linux/deployment competence more than any certificate.

**VPS configuration (this is your systems practice, not extra work):**
```bash
# Standard production setup on Ubuntu 22.04:
sudo apt update && sudo apt upgrade
sudo apt install nginx certbot python3-certbot-nginx fail2ban ufw
sudo ufw allow 22/tcp && sudo ufw allow 80/tcp && sudo ufw allow 443/tcp && sudo ufw enable
sudo certbot --nginx -d yourdomain.dev    # Free SSL via Let's Encrypt
# fail2ban auto-blocks brute force SSH attempts
```

**Month 5+:** Start freelance outreach. Not before. Having nothing to show means every proposal is rejected.

### Freelance Platform Strategy

| Platform | Start | Strategy |
|---|---|---|
| LinkedIn | Month 3 (posting) | 1 technical post/week. "What I learned debugging X." Not motivational. |
| Hacker News monthly freelancer thread | Month 4 | Post in "Ask HN: Freelancer?" thread (1st of each month) |
| Upwork | Month 4 | Niche gigs only: "C++ code review", "Linux VPS setup", "Backend API audit" |
| Fiverr | Month 3 | Small gigs to get first reviews: "Set up your Ubuntu VPS with nginx and SSL" |
| LinkedIn cold DM | Month 4 | Find seed-stage startup CTOs, comment on their technical posts before DMing |
| Toptal | Month 5–6 | Apply when: 500 LC done, 3+ live projects, technical blog exists |

### Services to Sell (Matched to Your Skills)

| Service | Unlock Month | Price Range |
|---|---|---|
| VPS/Linux server setup + hardening | Month 2 | ₹3,000–8,000 per setup |
| Bash automation scripts | Month 2 | ₹1,500–5,000 per script |
| C++ code review and performance notes | Month 3 | ₹5,000–20,000 per review |
| Backend API performance audit | Month 4 | ₹8,000–25,000 per audit |
| Linux systems programming (contract) | Month 4–5 | ₹15,000–60,000 per project |
| Technical documentation | Month 3 | ₹3,000–10,000 per doc set |

### Portfolio Content Plan

**Blog posts to write (specific topics, not generic):**
1. Month 2: "What fork() and exec() actually do — building a shell from scratch"
2. Month 3: "HTTP/1.1 from scratch in C++ — parsing, keep-alive, and thread pools"
3. Month 4: "My DDIA notes — what every backend dev needs to know about replication"
4. Month 5: "Lock-free queue vs mutex — benchmarks and when it actually matters"

**These four posts establish you as someone who builds real things and can explain them.** That is the entire freelance content strategy.

---

## 13. Study Environment

### Hardware — Buy in This Order

| Item | Priority | Budget (₹) | Recommendation |
|---|---|---|---|
| Good chair (lumbar support) | **Critical** | 3,000–8,000 | Green Soul Monster or Savya Home. Not a gaming chair. |
| External monitor 24" IPS | **Must Have** | 8,000–14,000 | LG 24MK430H or Dell E2422H. IPS only. |
| Mechanical keyboard | High | 2,500–6,000 | Keychron K2 or K8. Red or brown switches. |
| Wired mouse | High | 500–1,500 | Logitech G102. Ignore gaming features. |
| Laptop stand / arm | High | 800–2,000 | Any aluminum adjustable stand. Eye level. |
| USB hub (powered) | Medium | 600–1,200 | Anker 4-port with own power adapter. |
| Closed-back headphones (wired) | Medium | 1,000–3,000 | Sony MDR-ZX310. Wired = no charging anxiety. |

**Do not buy:** Standing desk, ultrawide monitor, RGB keyboards, coaching subscriptions, course bundles, iPad. These are all procrastination purchases.

### Software Setup (All Free)

| Tool | Day | Setup Task |
|---|---|---|
| Arch/Debian Linux | Day 1 | Daily driver. No exceptions. |
| Neovim + config | Day 1 | kickstart.nvim base. 4 hours max on setup. |
| tmux | Day 1 | `.tmux.conf` with Ctrl+a prefix. Pane splits. |
| gcc/clang + cmake + ninja | Day 1 | Full C/C++ toolchain. |
| GDB + Valgrind | Week 1 | 5 core GDB commands. Valgrind on every program. |
| Zsh + zsh-autosuggestions | Week 1 | Better shell DX. |
| strace + ltrace + perf | Month 2 | System call tracing. `perf stat` for counters. |
| Git with daily commits | Day 1 | Every project in GitHub from Day 1. |
| Rustup | Month 5 | Install when you start Rust. Not before. |
| UptimeRobot (free) | Month 4 | Monitor your VPS uptime. Alerts on down. |

### Deep Work Rules

1. Phone in another room during study blocks. Not on silent — another room.
2. One tab open in browser during study: only the current resource.
3. Install LeechBlock NG (Firefox) or StayFocusd (Chrome). Block YouTube and Instagram during study hours.
4. Log start time and end time every session. The friction of logging exposes wasted time.
5. Solve every problem on paper before typing. Thinking ≠ typing.
6. Never open two topics simultaneously. One resource at a time.
7. Weekly review every Sunday: what actually got into long-term memory vs. what just passed through?

---

## 14. Mistakes to Avoid

1. **Following the full 1,200-hour math curriculum.** It is designed for a different destination. You need roughly 200 hours of math, integrated. The other 1,000 hours belong to systems, DSA, and building things.

2. **Doing LeetCode problems randomly.** The pattern-based approach in Neetcode.io exists because pattern recognition is the skill being tested. Random grinding builds false confidence.

3. **Reading OS Concepts without writing system calls in C.** The book without the code is inert. Every chapter needs a corresponding C program.

4. **Treating DDIA as light reading.** This book requires active notes and deliberate re-reading of the hard chapters. Budget 4 weeks, not 1.

5. **Only doing virtual Codeforces rounds.** The live competitive pressure is qualitatively different. You need both.

6. **Not upsolving.** The growth happens in upsolving. Every round without upsolving is half a round.

7. **Grinding 500 LeetCode problems with zero real project code.** Both matter. The ratio in this plan (DSA daily + projects per phase) is deliberate.

8. **Attempting Rust as a main language before Month 5.** Rust has a steep learning curve that will eat your study time if you try it too early. C++ first, deeply.

9. **Treating probability as optional.** If you are going for HFT systems roles, you will be asked about expected values, Bayes' theorem, and basic distributions. Budget the time.

10. **Building a portfolio without case studies.** A GitHub link without explanation is a missed opportunity. Every project needs a README that explains design decisions and tradeoffs.

11. **Isolating yourself entirely.** Join CP Discord servers. Find an upsolve partner. Explaining problems to others doubles retention.

12. **Spending more than 4 hours on Neovim configuration.** This is the most seductive procrastination trap in developer culture. Your editor needs to work, not be perfect.

---

## 15. HFT Realism Assessment

### What HFT Systems Engineering Actually Requires

HFT systems roles (non-quant) ask for:
- Exceptional C++ (lock-free, memory model, cache efficiency)
- Deep Linux (kernel scheduling, NUMA, huge pages, CPU affinity, IRQ affinity)
- Network stack understanding (kernel bypass, DPDK, Solarflare, RDMA)
- Understanding of why things are slow (CPU pipeline stalls, cache misses, memory bandwidth)
- LOB understanding (you are building the systems that interact with the LOB)
- Basic market microstructure literacy (adverse selection, spread, queue position)

They do **not** require (for systems roles): options pricing theory, stochastic calculus, portfolio optimization, Sharpe ratios.

### What 6 Months Gets You

By the end of this plan:
- Your C++ and OS depth will be interview-ready for HFT systems roles
- Your LOB project demonstrates direct domain relevance
- Your lock-free queue with benchmarks demonstrates latency thinking
- You will understand the microstructure at the level needed for systems interviews

**Realistic outcome:** Initial conversations and technical screens at HFT firms in Month 6. Full-loop interviews and offers likely in Month 8–9. The gap is typically one or two rounds of deeper C++ and Linux internals questions that require more practice.

**Firms to target after 6 months:** Graviton Research, Quadeye, Tower Research (India offices for the first cycle), then Optiver/Jump/IMC with more preparation.

**One honest constraint:** Optiver's infamous "80 in 8" test (80 mental arithmetic questions in 8 minutes) requires specific practice — mental multiplication, division, percentage calculations, square root estimation. Spend 15 minutes per day in the final 4 weeks practicing this if Optiver is a target.

---

## 16. Technical Communication

Your written English is precise and structured — the question that generated this plan is evidence of that. The gap is spoken technical fluency.

**The only way to improve spoken technical fluency is to speak technically, frequently.**

### Integrated Practice (No Separate Schedule)

- **After every DSA problem:** Explain your approach out loud as if presenting to an interviewer, before looking at any solution. 3–5 minutes. Do this every single time.
- **After every systems chapter:** Summarize what you read in spoken English. 5 minutes. Explain it to yourself or to the wall.
- **Weekly recording:** Once per week, record yourself explaining a technical concept or problem solution. Watch it back. Fix one specific thing next week.
- **Pramp mocks from Month 3:** Do 2 mocks per week in Month 5–6. The live pressure of explaining to a real person is not replicable by any other method.

### Technical Vocabulary to Build

Read engineering blogs actively — Cloudflare, Discord, Uber. These blogs use real technical vocabulary in context. You absorb the language by reading how working engineers write about their systems.

Watch QCon and StrangeLoop talks on YouTube. These are senior engineers explaining real production systems in spoken English. Watch without subtitles. This is your model for technical speech.

---

## Quick Reference Summary

```
6-Month Phase Summary
─────────────────────────────────────────────────────────────
Phase 1 (Month 1–2): Modern C++, OS + Linux, Bash + Neovim,
                     Complexity Analysis, Modular Arithmetic,
                     DSA Foundations (200 problems, CF ~1500)

Phase 2 (Month 3–4): TCP/IP Networking, DDIA cover-to-cover,
                     DBMS (focused), Probability (Blitzstein 1–6),
                     IEEE 754 + Floating Point, Combinatorics,
                     Advanced DSA (380 problems, CF ~1800)

Phase 3 (Month 5–6): Systems Design, Lock-Free C++,
                     LOB + Market Microstructure, Rust basics,
                     Mock Interviews (3/week), Statistics essentials,
                     Final Projects (500+ problems, CF ~1900+)
─────────────────────────────────────────────────────────────

Math Hours Breakdown (total: ~200 hours over 6 months)
─────────────────────────────────────────────────────────────
Complexity Analysis + Master Theorem:  25 hrs  (Month 1)
Induction + Basic Proofs:              15 hrs  (Month 1)
Modular Arithmetic + Number Theory:    18 hrs  (Month 1–2)
Recurrence Relations:                  12 hrs  (Month 1)
IEEE 754 + Floating Point:             13 hrs  (Month 2)
Combinatorics (via DSA):               22 hrs  (Month 2–3)
Probability (Blitzstein 1–6):          28 hrs  (Month 3)
Graph Theory Math (via algorithms):    10 hrs  (Month 3)
Statistics Essentials (p99, etc.):     10 hrs  (Month 3–4)
Concentration Inequalities:             7 hrs  (Month 3)
LOB + Market Microstructure Math:      22 hrs  (Month 5–6)
Linear Algebra (matrices only):         8 hrs  (Month 4)
─────────────────────────────────────────────────────────────
SKIP: Calculus, Real Analysis, Measure Theory, Topology,
      Abstract Algebra, Category Theory, Full Quant Math,
      Avellaneda-Stoikov (mathematical), SVD, Eigenvalues
─────────────────────────────────────────────────────────────
```

---

*Plan version: June 2026. Revisit and adjust at the end of each phase.*  
*Companion tracker: prep_tracker.xlsx (8 sheets: Dashboard, Daily Log, DSA Tracker,*  
*Books, Projects, Weekly Review, Milestones, Portfolio & Freelance)*