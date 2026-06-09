# 6-Month FAANG + HFT Systems Engineering Prep
## Complete Roadmap — BTech Graduate, C++ Background

---
## Honest Assessment
**FAANG Systems/Backend Engineering:** Achievable in 6 months with this plan. The ask is strong DSA, OS depth, networking, distributed systems, and the ability to talk about real systems. Your C++ foundation is a genuine advantage over most candidates who learn Java/Python DSA and stop there.

**HFT Systems Engineering (non-quant):** Realistic, but 6 months gets you to *interview-ready*, not necessarily *hired* at Optiver or Jump Trading. HFT systems roles need ultra-low-latency C++, lock-free data structures, CPU/memory architecture, and kernel-level networking knowledge. Plan for Month 5–6 to begin HFT specialization. Both paths share ~80% of content, so you are not splitting effort.

**Recommendation:** Follow the FAANG path for 6 months. Layer HFT-specific material in Months 5–6. Apply to both simultaneously.

**What makes this achievable for you specifically:**
- You already know C++ (basic to intermediate, STL, pointers, bit ops, memory)
- You have 5–6 hours/day of real focus time
- You have the books already (OS Concepts, DBMS Concepts, CLRS)
- You are approaching this with intellectual honesty about constraints

---

## Priority Ordering

1. DSA (runs every single day — non-negotiable, compounds with time)
2. Modern C++ (foundational for everything in both paths)
3. Linux + OS depth (required for both FAANG systems and HFT)
4. Computer Networking (required for backend understanding and HFT networking)
5. DDIA + Distributed Systems (required for FAANG, good-to-know for HFT)
6. DBMS (supporting role — important but not primary)
7. Systems Design practice (Month 5–6)
8. HFT-specific: lock-free, concurrency, hardware (Month 5–6)
9. Rust (Month 5, gradual — investment for Month 7+)
10. Kotlin (postpone entirely)

The ordering is deliberate: DSA takes the longest to master and must start immediately. Modern C++ depth enables everything else. OS + networking are the core of systems interviews. DDIA and distributed systems fill in the backend picture.

---

## The 6-Month Roadmap

### Phase 1: Months 1–2 — Foundations (Weeks 1–8)

#### Modern C++

Read *A Tour of C++* by Bjarne Stroustrup from cover to cover. Code every concept — do not just read. The goal is hands-on familiarity with:

- Move semantics and rvalue references
- RAII (Resource Acquisition Is Initialization) — write classes that use it
- Smart pointers: `unique_ptr`, `shared_ptr`, `weak_ptr` — understand why each exists
- Lambdas and `std::function`
- `std::optional`, `std::variant`, `std::string_view`
- `std::thread`, `std::mutex`, `std::condition_variable`
- `std::atomic` — understand why it exists, not just how to use it
- Structured bindings, `constexpr`, `if constexpr`
- Ranges (light overview only — this is C++20)

Use cppreference.com daily. It is your primary reference for the rest of the plan. Bookmark it. Watch 2–3 CppCon "Back to Basics" talks per week during breaks — they are dense, free, and directly relevant.

Do NOT attempt: advanced TMP, CRTP, expression templates, `std::execution`. These are post-placement topics.

#### OS and Linux

Install Arch Linux or Debian on a VM or spare machine. Use it as your daily driver from Day 1. No exceptions, no going back to Windows.

Read *OS Concepts* (Silberschatz) — **chapters only, not cover-to-cover:**
- Chapters 1–6: processes, threads, CPU scheduling, synchronization, deadlock
- Chapters 8–10: main memory, virtual memory
- Skip: file system implementation chapters, security, advanced topics

Read *Inside the Machine* (Jon Stokes) alongside OS Concepts. It is a short book. Understand: CPU pipeline, caches (L1/L2/L3), TLB, NUMA, branch prediction. This is directly required for HFT and important for any systems conversation at FAANG.

**The key practice rule:** For every concept in the OS book, write a C program that demonstrates it. This is not optional.

- `fork()`, `exec()`, `wait()` — write process management programs
- `pthread_create`, `pthread_mutex_lock`, `sem_init` — threading and synchronization
- `mmap()` — memory-mapped files
- `pipe()`, `socketpair()` — IPC
- Semaphores, condition variables
- Use `strace` to inspect what your programs actually do

*The Linux Programming Interface* (Michael Kerrisk) is the definitive companion for this work. It is expensive but worth it. Use it as a reference and companion to your project work.

#### Bash and Neovim

**Neovim:** Set it up in Week 1 with a clean config. Use kickstart.nvim as your base. Add: `nvim-lspconfig` (with clangd), `telescope.nvim`, `nvim-treesitter`, `conform.nvim`, `oil.nvim`. Use it exclusively from Day 1. The discomfort of learning keybindings is the point — it pays off permanently.

**tmux:** Install and configure immediately alongside Neovim. Prefix key: Ctrl+a. Learn pane splits, window management, copy mode. Your workflow: Neovim on left, terminal on right, man pages or GDB below.

**Bash:** Do not read a book. Write real scripts:
- Automate your LeetCode submission log
- Write build scripts for your C++ projects
- Write a log parser for your server logs (Month 3)
- Write a backup script for your VPS (Month 4)

You learn Bash by needing it, not by reading about it.

#### DSA — Phase 1

Two hours every single day. Follow the Neetcode.io roadmap for ordering. Do not do LeetCode randomly.

Month 1 categories:
- Arrays and sliding window
- Two pointers
- Binary search (all variations, not just basic)
- Hashing and frequency maps
- Linked list
- Stack and monotonic stack
- Recursion basics

Month 2 categories:
- Binary trees and BST
- Heaps and priority queues
- Tries
- Graphs: BFS, DFS, connected components, islands
- Union-Find (Disjoint Set Union)
- Topological sort

Target: 200 problems by end of Phase 1.

---

### Phase 2: Months 3–4 — Core Systems (Weeks 9–16)

#### Computer Networking

Read *Computer Networking: A Top-Down Approach* (Kurose & Ross).

Read carefully: Chapters 1–4 (application layer, transport layer, network layer).
Read selectively: Chapters 5–6.
Skip: Chapter 7–8 for now.

Supplement with Beej's Guide to Network Programming (free at beej.us/guide/bgnet) — write every example.

Practical work to do alongside reading:
- Write a TCP echo server in C
- Write a UDP server
- Implement basic HTTP request parsing
- Understand `epoll_create`/`epoll_ctl`/`epoll_wait` — write a server that uses it
- Read and understand a real HTTP/1.1 response at the byte level using Wireshark or tcpdump

Concepts you must know cold:
- TCP three-way handshake (explain it in code, not just words)
- TCP congestion control (understand Tahoe and Reno at a high level)
- DNS resolution chain
- HTTP/1.1 vs HTTP/2 differences at the protocol level
- TLS at a design level (not implementation, but how the handshake works)
- `epoll` vs `select` vs `poll` — when and why each
- What a socket is at the OS level (it is a file descriptor)

Read the Cloudflare engineering blog actively. They explain real networking with production-level depth and clarity.

#### DDIA (Designing Data-Intensive Applications)

Read it end-to-end in Month 3. Do not rush it. Take active notes — physical paper, not laptop. This book requires synthesis, not just reading.

Focus areas (in priority order):
1. Replication — leader-follower, multi-leader, leaderless, quorums
2. Partitioning — range vs hash, secondary indexes, rebalancing
3. Transactions — ACID, isolation levels (read uncommitted through serializable)
4. The trouble with distributed systems — clocks, ordering, causality
5. Consistency and consensus — linearizability, CAP theorem (and its nuance)
6. Chapter 3 — storage engines: B-trees, LSM trees, SSTables
7. Batch and stream processing (light read — Chapters 10–12)

Watch Martin Kleppmann's talks on YouTube alongside reading. He wrote the book and his talks deepen the chapters significantly.

#### DBMS

From your DBMS Concepts book (Ramakrishnan):
- Transactions and ACID properties (deep)
- Isolation levels: read uncommitted, read committed, repeatable read, serializable
- Concurrency control: locking, MVCC
- Indexing: B-tree indexes, hash indexes — understand the tradeoffs
- Query execution and join algorithms (nested loop, hash join, sort-merge join)

Install PostgreSQL. Run `EXPLAIN ANALYZE` on non-trivial queries and understand what you see. This connects the theory to production behavior. Spend no more than 2.5–3 weeks on DBMS — it is supporting material, not primary.

#### DSA — Phase 2

Month 3 focus: graphs (Dijkstra, Bellman-Ford, Floyd-Warshall, topological sort), segment trees, Fenwick trees (BIT).

Month 4 focus: Dynamic Programming — this is the most time-consuming category. Allocate more time here than anywhere else.

DP patterns to cover, in order:
1. 1D DP: climbing stairs, house robber, Kadane's
2. 0-1 Knapsack and Unbounded Knapsack
3. LCS and Edit Distance
4. Coin Change and all variants
5. Interval DP: Matrix Chain Multiplication, Burst Balloons
6. DP on Trees
7. Digit DP (light)
8. Bitmask DP

For each pattern: solve one canonical problem completely, understand it cold, then solve 3–4 variants. Do not move on until the pattern is internalized. Random grinding of DP problems without pattern recognition is almost useless.

Target: 380 problems by end of Phase 2.

---

### Phase 3: Months 5–6 — Specialization (Weeks 17–26)

#### Systems Design Practice

DDIA is your primary resource and you have already read it. Now practice applying it.

Read real engineering blog posts — these are free and describe actual production tradeoffs:
- Discord: how they scaled to millions of concurrent users
- Cloudflare: how they built their global network
- Uber: their database migration decisions
- Figma: how they multiplexed WebSocket connections
- Notion: how they migrated their monolith

Practice designing (out loud or on paper, not just reading solutions):
- URL shortener (classic, covers hashing + storage + redirect)
- Distributed key-value store (covers partitioning + replication)
- Rate limiter (covers sliding window + Redis + distributed state)
- Pub-sub system (covers Kafka-like architecture)
- Distributed cache (covers eviction + consistency)

Alex Xu's *System Design Interview* book is a reasonable checklist but not a primary learning source. DDIA is deeper.

#### HFT-Specific (if that path)

Read *C++ Concurrency in Action* (Anthony Williams), Chapters 5–7. This covers:
- C++ memory model (the most important topic here)
- `std::memory_order`: `relaxed`, `acquire`, `release`, `acq_rel`, `seq_cst`
- Lock-free data structures
- ABA problem and how to avoid it

Implement a single-producer single-consumer (SPSC) lock-free queue:
- Cache-line aligned using `alignas(64)` or `__attribute__((aligned(64)))`
- Correct memory ordering on every atomic operation
- Benchmarked against a mutex-based version using your own timing harness

Study these concepts at a conceptual level (you do not need to implement them):
- Why the Linux network stack is too slow for HFT (kernel context switches, memory copies)
- What DPDK does and why (kernel bypass networking)
- What RDMA does (remote direct memory access, zero-copy)
- False sharing — write a benchmark that demonstrates it
- CPU cache line size (64 bytes) and its practical implications

Understand `perf stat` at a basic level. Be able to use it to measure CPU counters.

#### Rust Introduction

Read *The Rust Programming Language* (free at doc.rust-lang.org/book), Chapters 1–10. The goal is to understand:
- Ownership and borrowing (the core mental model)
- Lifetimes (basic understanding — advanced lifetimes come later)
- `Result` and `Option` error handling
- Traits

Do Rustlings exercises alongside reading. Implement a singly linked list in Rust — it is hard on purpose and teaches ownership deeply.

The goal is not to build systems in Rust yet. The goal is to understand the ownership model cold, because it is directly relevant to how you think about memory in C++ and will be a major skill in Month 7+.

#### Mock Interviews

Starting Month 5:
- 3 Pramp mock interviews per week (free)
- After solving every LeetCode problem, explain your solution out loud before typing
- Record yourself doing a technical explanation once per week and watch it back — this is uncomfortable and directly useful
- Practice explaining your projects as you would in an interview: problem → approach → decisions → tradeoffs

The goal of mock interviews is not to practice problem-solving — you do that daily. The goal is to develop fluency in thinking out loud and communicating under pressure.

---

## Daily Schedule

```
08:00 – 10:00   DSA (2 hours)
                Problems first — brain is freshest. 2–3 problems minimum.
                Neetcode order. Upsolve after contests.

10:00 – 13:00   Systems Primary (2.5–3 hours)
                Current phase topic: C++ / OS / DDIA / Networking.
                Code every concept. Don't just read.

14:00 – 15:00   Reading / Concept Review (1 hour)
                Book reading + physical notes for current phase.
                No coding here — synthesis only.

15:00 – 18:00   Buffer (1–2 hours)
                Extra problems / life / interruptions.
                Use surplus for upsolving or project work.

21:00 – 22:00   Evening (1 hour)
                Weekend: full Codeforces round (3–4 hrs, plan accordingly).
                Weekday: upsolve + explain LC solution out loud.
```

**Weekly:**
- Saturday: Full Codeforces round or virtual contest (3–4 hours) + upsolving (1–2 hours, same day)
- Sunday: 2 hours DSA, 2 hours project work, 1 hour weekly review

**Weekly review questions (every Sunday):**
1. What did I actually internalize this week vs. just read?
2. What is still fuzzy — do I understand it well enough to explain it to someone?
3. What is next week's primary system topic?
4. Did I upsolve every contest? If not, why not?
5. What is my current LeetCode count and CF rating?

---

## DSA Milestones

### LeetCode Targets

| Month | Cumulative | Key Categories |
|-------|-----------|----------------|
| End Month 1 | 100 | Arrays, binary search, linked list, hashing, stack |
| End Month 2 | 200 | Trees, graphs, heaps, tries started |
| End Month 3 | 280 | Graphs advanced, segment tree, bit manipulation |
| End Month 4 | 380 | DP patterns — all major types covered |
| End Month 5 | 450 | Hards becoming solvable, string algorithms |
| End Month 6 | 500+ | Mediums in <20 min, most hards solvable |

Category targets (exact counts to hit):

| Category | Target |
|---------|--------|
| Arrays & Sliding Window | 30 |
| Binary Search (all variants) | 20 |
| Linked List | 15 |
| Stack & Monotonic Stack | 15 |
| Hashing & Maps | 15 |
| Two Pointers | 10 |
| Recursion & Backtracking | 15 |
| Binary Trees & BST | 20 |
| Heaps & Priority Queue | 15 |
| Tries | 10 |
| Graphs (BFS/DFS) | 20 |
| Graphs (Advanced) | 20 |
| Topological Sort | 10 |
| Dynamic Programming | 50 |
| DP — Interval & Bitmask | 15 |
| Segment Tree / Fenwick | 10 |
| Bit Manipulation | 10 |
| String Algorithms | 10 |
| Math (light) | 5 |
| Simulation / Misc | 15 |
| **Total** | **500** |

### Codeforces Rating Targets

| Milestone | Target Rating | When | What It Means |
|----------|--------------|------|---------------|
| Month 1 end | 1300 | Week 8 | Div 3 A/B consistent, Div 2 A starting |
| Month 2 end | 1500 | Week 16 | Div 2 B/C consistent |
| Month 3 end | 1650 | Week 20 | Div 2 C solid, D occasional |
| Month 4 end | 1800 | Week 24 | Div 2 D occasional |
| Month 6 end | 1900+ | Week 34 | Div 1 C attempts, Div 2 D/E comfortable |

**The non-negotiable rule:** Upsolve every contest without exception. Upsolving is where 70% of the rating growth happens. Every time you participate in a contest and do NOT upsolve the problems you couldn't solve, you have wasted the most valuable learning opportunity that contest could provide.

**Rating 1700+ in 6 months is realistic** if you compete in live rounds consistently and upsolve every single time. Virtual contests are fine for practice, but live rounds develop the pressure tolerance you need.

---

## Book Reading Order

| Book | When | Approach |
|------|------|----------|
| *Inside the Machine* (Stokes) | Month 1, first 2 weeks | Read alongside OS Concepts. Short book. |
| *A Tour of C++* (Stroustrup) | Month 1–2 | Code every example. Daily reference. |
| *OS Concepts* (Silberschatz) | Month 1–2 | Ch 1–6, 8–10 only. Code syscalls alongside. |
| *DBMS Concepts* (Ramakrishnan) | Month 2 | Transactions, indexing, MVCC, joins. 2–3 weeks only. |
| *DDIA* (Kleppmann) | Month 3 | Cover to cover. Active notes on paper. |
| *Computer Networking: Top Down* (Kurose) | Month 3 | Ch 1–4 carefully. Ch 5–6 selectively. |
| *C++ Concurrency in Action* (Williams) | Month 5–6 | Ch 5–7 minimum. Critical for HFT path. |
| *The Rust Programming Language* | Month 5 | Ch 1–10. Free online. Do Rustlings. |
| *CLRS* (Cormen et al.) | Throughout | **Reference only.** Ch 6, 15, 22–25. Do not read proofs. |
| *Linux Programming Interface* (Kerrisk) | Month 2–5 ongoing | Use as companion to project work. Expensive but definitive. |

---

## Projects to Build

### Project 1: Mini Shell in C (Phase 1, 2 weeks)

Implement fork, exec, wait, pipes, basic signal handling (SIGCHLD, SIGSTOP, SIGCONT), and job control (fg/bg commands). This is your first real systems project.

Every project needs a README that answers: what it does, design decisions made, what you would do differently at scale. This is what you walk interviewers through.

### Project 2: OS Syscall Experiments (Phase 1, ongoing)

One C file per concept: `mmap_demo.c`, `shared_memory.c`, `semaphore_producer_consumer.c`, etc. Not a single project but a collection. Use `strace` to inspect what your programs actually do at the syscall level.

### Project 3: TCP Echo Server with epoll (Phase 2, 1 week)

Non-blocking sockets, `epoll` event loop, handle multiple concurrent connections without threads. Write a version with `select` first to understand why `epoll` is better. Document the comparison in the README.

### Project 4: HTTP/1.1 Server in C++ (Phase 2–3, 3 weeks)

Parse HTTP requests, serve static files, handle concurrent connections via a thread pool. This is the most interview-relevant project. It combines C++, networking, OS, and concurrency knowledge. Features: keep-alive connections, proper HTTP/1.1 response formatting, MIME type handling, configurable thread pool size.

### Project 5: Key-Value Store in C++ (Phase 3, 2–3 weeks)

In-memory hashmap storage + write-ahead log for durability. DDIA Chapter 3 is the design specification. Implement: GET, PUT, DELETE operations, WAL for crash recovery, log compaction (basic). This demonstrates you understood DDIA at a deeper level than just reading it.

### Project 6: Lock-Free SPSC Queue (Phase 3, HFT path, 1–2 weeks)

Single-producer single-consumer queue using `std::atomic`. Requirements: cache-line aligned (64 bytes), correct memory ordering (`acquire`/`release`), benchmarked against a mutex-based version. The benchmark showing the latency difference is the deliverable — the code alone is not enough.

### Project 7: Toy Distributed KV (Phase 3, stretch goal, 2 weeks)

Two-node setup, basic replication log, leader/follower. Does not need to be production quality. Shows you understand the concepts from DDIA and can implement them, not just describe them. gRPC or raw TCP for communication.

---

## Portfolio and Personal Brand

### Portfolio Website

Build it in Month 1 on Vercel or Netlify (free) using Astro or plain HTML/CSS. Get online fast. Upgrade to a self-hosted VPS in Month 4 when you have real projects to show.

Every section of your portfolio serves a specific function:

**Hero:** Name + role ("Systems & Backend Engineer") + one-line value proposition + two CTAs. Be specific — "C++ systems and backend" beats "full stack developer" for your target roles.

**Projects:** 3–4 curated projects, not everything you have built. Each needs: a screenshot or GIF showing it working, a one-line description, the tech stack, a GitHub link, a live demo link, and a 2-paragraph case study.

**Case Study Pages:** For each project: Problem → Approach → Key Decisions → What I'd do differently at scale → Benchmarks. This separates you from 99% of portfolios. Clients and technical interviewers read these to assess your engineering maturity.

**Technical Blog:** 2–3 posts minimum. Write about what you actually built. These create SEO inbound and prove depth that a project list cannot.

**Contact:** Email (from your own domain) + LinkedIn + GitHub. No friction. Make it trivially easy to reach you.

### Domain and VPS Setup (Month 4)

1. Buy `yourname.dev` on Namecheap (~₹1,200/year) — `.dev` signals developer credibility
2. Set up professional email `you@yourdomain.com` via Zoho Mail (free tier)
3. Get a VPS: Hostinger KVM2 at ₹349/month or Hetzner CX22 at ~₹350/month (2vCPU, 4GB RAM, NVMe)
4. Install Ubuntu 22.04, nginx reverse proxy, Certbot SSL (free HTTPS via Let's Encrypt)
5. Deploy portfolio and project demos — accessible via your domain
6. Add fail2ban + UFW firewall (basic server hardening — this is Linux practice)
7. Add UptimeRobot monitoring (free — pings every 5 minutes)

Setting up and managing your own VPS is itself interview material. It demonstrates real Linux and deployment knowledge.

### Sample Work / Content Plan

These are not optional extras — they are the evidence that gets clients and passes technical screens:

- **Blog Post 1 (Month 2):** "How I built a mini shell in C — fork, exec, pipes explained with code"
- **Blog Post 2 (Month 3):** "Building an HTTP/1.1 server in C++ — thread pool design and epoll choices"
- **Blog Post 3 (Month 3):** "DDIA reading notes — what every backend developer should know about distributed systems"
- **Blog Post 4 (Month 5):** "Mutex vs lock-free queue: benchmarks and what they mean for latency-critical systems" (include actual numbers)
- **GitHub Profile README (Month 1):** Current focus, what you're building, contact — updated monthly
- **Project READMEs (all projects):** Architecture diagram (ASCII is fine), build instructions, design decisions, what's next
- **LinkedIn posts (1/week from Month 3):** Short technical observations — "Today I learned X about Y" — purely technical, never motivational
- **Open Source PR (Month 4–5):** At least one real contribution to a project in your domain

---

## Freelancing

### Honest Timing

Do not chase freelance in Months 1–3. Build skills and projects first. Starting outreach with no live projects to show results in rejection and wasted time. Begin in Month 4 with real deployed projects.

Systems and backend freelance pays ₹1,500–5,000/hour for competent demonstrated work. The key word is *demonstrated* — a GitHub with live projects is your credibility, not a profile bio.

### Platform Strategy

**LinkedIn Services Marketplace (Primary):**
The best channel for your profile. Optimize your headline: "C++ Systems & Backend Engineer | Linux | TCP/IP | High-Performance Systems." Post one technical post per week from Month 3. This creates inbound over time. DM startup CTOs with specific technical observations about their stack — never pitch first. Add value first.

**Hacker News Freelancer Thread (High Priority):**
Posted on the 1st of every month: "Ask HN: Freelancer? Seeking Freelancer?" Reply with: what you do, tech stack, timezone, rate range, links to GitHub and portfolio. HN skews toward backend and systems — this is your audience. Quality of inquiries is exceptional.

**Cold LinkedIn DMs (Highest ROI when done right):**
Find seed/Series A startups on Product Hunt or Wellfound. Find their CTO. Message them with a specific technical observation about their product's apparent architecture — never a generic pitch. "I noticed your API has X behavior that suggests Y pattern — I solved a similar problem by doing Z." Three-message sequence: email Day 1, LinkedIn connection Day 3, follow-up email Day 7 if no response.

**Upwork (Secondary):**
Niche down hard. Do not compete on price. Target: "C++ performance optimization", "Linux systems programming", "backend API performance tuning." Apply only to jobs posted under 2 hours ago. Filter for verified payment and under 5 proposals.

**Toptal (Long-term Goal, Month 5–6):**
Apply when you have 500+ LC, 3+ live projects, and a technical blog. Three-stage technical screening. Once in, clients pay $80–200/hr USD equivalent.

**Fiverr (Reviews Only):**
Create specific gigs: "Debug your C++ performance issue," "Set up Linux VPS with nginx + SSL." Price low to get first 3–5 reviews quickly. Reviews unlock credibility on Upwork.

### Services to Sell

Aligned to your actual skills by month they unlock:

| Service | Rate Range | Unlock Month |
|---------|-----------|-------------|
| VPS / Linux server setup and hardening | ₹3,000–8,000 per setup | Month 2 |
| Bash automation scripts | ₹1,500–5,000 per script | Month 2 |
| C++ code review and performance audit | ₹5,000–20,000 per review | Month 3 |
| Technical documentation writing | ₹3,000–10,000 per set | Month 3 |
| Backend API performance audit | ₹8,000–25,000 per audit | Month 4 |
| Linux systems programming contract | ₹15,000–60,000 per project | Month 4–5 |
| Architecture consultation (1-hr call) | ₹2,000–5,000 per hour | Month 4–5 |

### Getting the First Client

The first client is the hardest. The goal is not revenue — the goal is one testimonial on LinkedIn or Upwork. That testimonial is worth more than 100 cold pitches.

Strategy for first client (Month 4):
1. Post your first two blog posts and share them on LinkedIn
2. Reply to the HN freelancer thread with your profile
3. Offer your VPS setup service on Upwork at a price that makes it a no-brainer for a first hire
4. Ask your network (college batchmates, professors) if they know anyone who needs a developer

A referral from someone you know is your best first client. Everyone knows someone who needs a "tech person."

### Proposal Writing

A proposal that converts follows this structure:
1. **Opening (1 sentence):** Reference something specific about their problem — shows you read it
2. **Credibility (2–3 sentences):** One specific past result or project relevant to their problem, with link
3. **Your Approach (3–5 sentences):** How you would solve their specific problem
4. **Deliverables (bullet list):** Specific, concrete, with timeline
5. **Rate:** Specific, not a range — "₹X for the full project" or "₹X/hr, estimated Y hours"
6. **CTA:** Ask for a 15-minute call, not an immediate yes

The most common proposal mistake: leading with your skills. Clients do not care about your skills until they believe you understand their problem.

---

## Study Environment

### Hardware (Priority Order)

| Item | Priority | Cost Range (₹) |
|------|----------|----------------|
| Good ergonomic chair (lumbar support) | CRITICAL | 3,000–8,000 |
| External monitor 24" IPS | MUST HAVE | 8,000–14,000 |
| Mechanical keyboard | HIGH | 2,500–6,000 |
| Wired mouse | HIGH | 500–1,500 |
| Laptop stand or monitor arm | HIGH | 800–2,000 |
| Powered USB hub | MEDIUM | 600–1,200 |
| Closed-back wired headphones | MEDIUM | 1,000–3,000 |
| Adjustable desk lamp | LOW | 500–1,500 |

**Specific recommendations:**
- Chair: Green Soul Monster or Savya Home — not gaming chairs (marketing, not ergonomics)
- Monitor: LG 24MK430H or Dell E2422H — IPS panels only, TN panels cause eye strain
- Keyboard: Keychron K2 or K8 hot-swap, red switches for silence
- Mouse: Logitech G102 or M90 — reliability over features
- Headphones: Sony MDR-ZX310 or Audio Technica ATH-M20x — wired, closed-back, padded

**What NOT to buy:**
- Standing desk (₹15,000–50,000): not worth it for a 6-month sprint
- Ultrawide monitor: a second 24" IPS gives more usable screen for half the price
- Coaching institute subscriptions (₹15,000–50,000): you have CLRS, DDIA, and a plan
- Multiple course subscriptions: buying more courses is procrastination that feels like preparation

### Software Setup (All Free)

| Tool | When | What to Configure |
|------|------|-------------------|
| Arch/Debian Linux | Day 1 | Install as daily driver — VM or dual boot |
| Neovim | Day 1 | kickstart.nvim base + clangd + treesitter + conform |
| tmux | Day 1 | Prefix Ctrl+a + vim copy mode + status bar |
| gcc/clang + cmake/ninja | Day 1 | alias cc=clang, c++=clang++ |
| GDB + Valgrind | Week 1 | Learn 5 core GDB commands cold |
| Zsh + autosuggestions + syntax-highlighting | Week 1 | oh-my-zsh + 2 plugins |
| strace / perf | Month 2 | strace -e trace=read,write,open ./program |
| Rustup | Month 5 | Install only when you start Rust — not before |
| Git (proper config) | Day 1 | Global .gitignore + meaningful commit messages |

### Deep Work Rules

1. Phone in another room during study blocks — not on silent, not face-down — in another room
2. One browser tab during study: only the resource you are currently reading
3. Install LeechBlock NG (Firefox) or StayFocusd (Chrome) — block YouTube and Instagram 8am–6pm
4. Solve every problem on paper first before typing — forces thinking, not pattern copying
5. Log start time and end time for every session — friction of logging reveals time wasted
6. No music with lyrics during DSA or reading — instrumental or silence only
7. Note-taking on paper for concepts, not laptop — forces synthesis rather than copy-paste
8. One topic at a time — opening DDIA and LeetCode and C++ simultaneously means learning none of them

---

## Communication and Spoken English

Your written English (demonstrated by the question you asked) is precise and technical. What you need is spoken fluency in technical contexts, not general English improvement.

Practical approach — no separate "English improvement" activity needed:

**Daily (5 minutes after each problem):** Explain your solution out loud as if presenting to an interviewer. Do this before looking at editorial solutions. This builds the habit of thinking out loud under pressure.

**Daily (5 minutes before sleep):** Summarize what you studied in spoken English. Explain it to yourself as if teaching someone else.

**Weekly (record once):** Do a mock technical explanation of one of your projects. Record it. Watch it back. This is uncomfortable and directly useful.

**From Month 3 (2–3 per week):** Pramp mock interviews. These are peer-to-peer and free. The goal is not to find hard problems — the goal is practice communicating under time pressure with another person watching.

**Passive input:** Watch QCon, StrangeLoop, and CppCon talks on YouTube. This builds technical vocabulary and exposes you to how senior engineers speak about systems. The Cloudflare and Uber engineering blogs do the same for written technical communication.

---

## Common Mistakes to Avoid

**DSA mistakes:**
- Doing LeetCode randomly instead of category by category
- Grinding 500 problems without understanding patterns — same mistake repeated 500 times
- Never attempting Codeforces rounds live — virtual contests don't build pressure tolerance
- Not upsolving after every contest — this is where 70% of growth happens
- Treating CLRS as a cover-to-cover textbook — it is a reference

**Systems mistakes:**
- Reading OS Concepts without writing the corresponding syscalls in C
- Treating DDIA as light reading — it requires active note-taking and synthesis
- Bouncing between resources — pick one resource per topic and finish it
- "I'll pause DSA for 2 weeks while I finish this systems topic" — never do this

**Career mistakes:**
- 500 LeetCode problems and zero deployed projects — weak profile in any interview
- Starting freelance outreach before having live projects to show
- Buying multiple course subscriptions as a form of procrastination
- Treating Kotlin and Rust as urgent — go deep in C++ first

**Workflow mistakes:**
- Not committing code to GitHub daily — green squares matter
- Not using Linux as your daily OS — reading about Linux is not the same as living in it
- Using VS Code instead of Neovim — you lose the Linux workflow integration

---

## Topics to Postpone

**Postpone entirely until after placement:**
- Kotlin
- Advanced TMP, CRTP, expression templates in C++
- Kubernetes, Docker (30 minutes conceptual understanding is enough)
- Full stack or frontend development
- TCP/IP Illustrated Vol. 1 (Kurose is sufficient; this is a post-placement deep dive)
- Kafka, Spark, data engineering

**Postpone until Month 7+:**
- Real systems Rust (beyond learning ownership basics)
- DPDK implementation (conceptual understanding is enough for HFT interviews)
- Advanced competitive math (number theory, combinatorics — learn only what specific CF problems require)
- CLRS proofs

---

## Are Coaching Institutes Worth It?

No, for your profile.

AlgoUniversity, Pepcoding, Striver's courses — these exist for people who need external structure and direction. You have CLRS, DDIA, a detailed plan, 5+ hours per day, and the intellectual honesty to assess your own progress. You would be paying someone to read books to you at a slower pace.

The only scenario where a paid program adds value: if you are genuinely struggling with consistency and want a peer cohort for accountability. Some platforms (AlgoUniversity fellowship) offer this. Even then, it is optional — Discord communities and Codeforces friends provide the same thing for free.

Do not buy systems design courses. DDIA plus engineering blogs plus building real things is better than any course you will find. The blogs are free and describe real production systems at a depth no course can match.

---

## HFT Realism Check

**Can you get into HFT systems in 6 months?** You can get to interview-ready in 6 months. Getting hired at top shops (Optiver, IMC, Jump Trading, Virtu) typically takes 8–10 months of preparation at this intensity, because the technical bar is higher than FAANG and the number of roles is smaller.

**What HFT systems roles actually test:**
- Ultra-low-latency C++17/20: every allocation matters, heap allocation is often banned in hot paths
- Lock-free data structures: understand the memory model cold, not just by rote
- CPU architecture: cache lines, false sharing, NUMA topology, branch prediction
- Kernel bypass: why the Linux network stack is too slow (microsecond latency is the goal, kernel adds hundreds of microseconds)
- `perf`, `valgrind`, `cachegrind`: profiling at a hardware counter level
- Order book implementation: this is the classic HFT systems interview problem

**What you will have by Month 6 on this plan:**
- Strong Modern C++ including concurrency and atomics
- OS internals depth (processes, memory, scheduling)
- Networking fundamentals
- One lock-free data structure implemented and benchmarked
- Understanding of CPU architecture (from *Inside the Machine*)

**The gap you will need to close for HFT specifically:**
- More hardware-level profiling experience
- Real-time systems concepts
- More depth on kernel bypass (DPDK conceptual understanding)
- Order book implementation practice

This plan puts you in a strong position to start HFT conversations in Month 5–6, with realistic chances of offers in Month 8–10.

---

## Resources List

### DSA and Competitive Programming
- Neetcode.io — structured LeetCode ordering by pattern (primary guide for LC order)
- CSES Problem Set (cses.fi) — best pre-Codeforces warm-up set, all major categories
- Codeforces — live rounds every week; aim for Div 2-3 consistently
- CLRS — reference only, not cover-to-cover

### C++
- cppreference.com — daily reference, bookmark immediately
- *A Tour of C++* — Bjarne Stroustrup — primary reading Month 1–2
- *C++ Concurrency in Action* — Anthony Williams — primary reading Month 5–6
- CppCon "Back to Basics" talks on YouTube — watch 2–3 per week during breaks

### OS and Linux
- *OS Concepts* — Silberschatz — primary, chapters 1–6, 8–10
- *Inside the Machine* — Jon Stokes — primary, read first
- *Linux Programming Interface* — Michael Kerrisk — companion reference, ongoing
- man pages — for every syscall you write, read the man page

### Networking
- *Computer Networking: A Top-Down Approach* — Kurose & Ross — chapters 1–4
- Beej's Guide to Network Programming (beej.us/guide/bgnet) — free, practical
- Cloudflare Blog — real networking depth with production context
- Wireshark — use it to inspect real traffic while reading

### Systems Design and Distributed Systems
- *DDIA* — Kleppmann — primary reading Month 3, cover to cover
- Martin Kleppmann's talks on YouTube — watch alongside DDIA
- Discord, Uber, Figma, Cloudflare engineering blogs — free, real systems

### Rust
- *The Rust Programming Language* (doc.rust-lang.org/book) — free, authoritative
- Rustlings (github.com/rust-lang/rustlings) — exercises, do alongside book

### Mock Interviews
- Pramp.com — free peer mock interviews, start Month 3
- LeetCode mock interview mode — for timed practice

### Freelancing and Portfolio
- Neetcode.io (also has good system design content)
- Namecheap — domain registration
- Hostinger (₹349/mo) or Hetzner (€3.79/mo) — VPS hosting
- Vercel or Netlify — free static hosting for portfolio
- Zoho Mail — free professional email on your domain
- UptimeRobot — free uptime monitoring
- Contra, LinkedIn Services, Toptal — freelance platforms

---

## Milestones Summary

| Milestone                             | Target Date | Category   |
| ------------------------------------- | ----------- | ---------- |
| Linux + Neovim daily driver           | Week 1      | Setup      |
| C++ Tour complete + projects coded    | Month 2     | C++        |
| OS Concepts Ch 1–6 + syscalls coded   | Month 2     | OS         |
| Mini Shell on GitHub                  | Month 2     | Project    |
| LeetCode: 100 problems                | Month 1     | DSA        |
| CF Rating: 1300+                      | Month 2     | CF         |
| LeetCode: 200 problems                | Month 2     | DSA        |
| DDIA read with notes                  | Month 3     | Systems    |
| Networking Ch 1–4 + socket projects   | Month 3     | Networking |
| TCP echo server (epoll) live          | Month 3     | Project    |
| CF Rating: 1700+                      | Month 4     | CF         |
| LeetCode: 380 problems                | Month 4     | DSA        |
| HTTP/1.1 server in C++ live           | Month 4     | Project    |
| VPS + domain + portfolio live         | Month 4     | Portfolio  |
| KV store with WAL                     | Month 5     | Project    |
| DP mastery: 50 problems               | Month 5     | DSA        |
| Lock-free SPSC queue benchmarked      | Month 5     | HFT/C++    |
| First freelance project + testimonial | Month 5     | Freelance  |
| LeetCode: 500+ problems               | Month 6     | DSA        |
| CF Rating: 1900+                      | Month 6     | CF         |
| 10 Pramp mocks complete               | Month 6     | Interviews |
| Rust: ownership + Rustlings done      | Month 6     | Rust       |
| Total application submitted           | Month 6     | Freelance  |