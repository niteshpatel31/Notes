# Elite Systems / Backend Engineering Resource Map

> Target: FAANG backend/systems + long-term HFT infrastructure compatibility

## Core Direction

```txt
C++ → Linux → OS → Networking → Systems Projects → Distributed Systems
```

Avoid:

```txt
Framework hopping, endless tutorials, premature Kubernetes/cloud obsession
```

---

# 1. Competitive Programming & DSA

## Platforms

| Purpose                 | Resource                   |
| ----------------------- | -------------------------- |
| Interview prep          | https://leetcode.com/      |
| Competitive programming | https://codeforces.com/    |
| Structured learning     | https://usaco.guide/       |
| Algorithms reference    | https://cp-algorithms.com/ |
| Interview patterns      | https://neetcode.io/       |

## DSA Order

### Phase 1

```txt
Arrays
Binary Search
Sliding Window
Prefix Sum
Hashing
Stack/Queue
Greedy
Recursion
```

### Phase 2

```txt
Trees
Heap
Graph BFS/DFS
DSU
Shortest Paths
Backtracking
Dynamic Programming
```

### Phase 3

```txt
Segment Tree
Fenwick Tree
Advanced DP
Sparse Table
```

## Targets

| Time    | LeetCode | Codeforces |
| ------- | -------- | ---------- |
| Month 1 | 150–200  | 1000–1100  |
| Month 3 | 300–350  | 1300–1450  |
| Month 6 | 450+     | 1500–1600  |

---

# 2. Linux + Bash + Workflow

## Linux

| Resource                          | Purpose              |
| --------------------------------- | -------------------- |
| https://linuxjourney.com/         | Linux fundamentals   |
| https://linuxcommand.org/tlcl.php | Shell depth          |
| https://explainshell.com/         | Command explanations |

## Topics

```txt
Filesystem
Permissions
Processes
Signals
Pipes
SSH
systemd
Environment Variables
grep/sed/awk
```

## Bash

Learn:

```txt
Variables
Loops
Conditionals
Pipelines
Cron Jobs
Automation Scripts
```

## Terminal Stack

| Tool    | Purpose      |
| ------- | ------------ |
| tmux    | Multiplexing |
| ripgrep | Fast search  |
| fzf     | Fuzzy finder |
| fd      | Better find  |
| lazygit | Git TUI      |

---

# 3. Neovim

## Recommended

| Resource                           | Purpose             |
| ---------------------------------- | ------------------- |
| https://github.com/LazyVim/LazyVim | Best balanced setup |
| https://github.com/NvChad/NvChad   | Fast starter config |

## Keep Only

```txt
LSP
Treesitter
Telescope
Harpoon
Git integration
```

Avoid:

```txt
Theme/plugin addiction
```

---

# 4. Modern C++

## Books

| Book                      | Priority  |
| ------------------------- | --------- |
| C++ Primer                | High      |
| Effective C++             | Mandatory |
| Effective Modern C++      | Mandatory |
| C++ Concurrency in Action | Later     |

## References

| Resource                           | Purpose                |
| ---------------------------------- | ---------------------- |
| https://en.cppreference.com/w/     | Official reference     |
| https://isocpp.org/                | C++ resources          |
| https://www.youtube.com/@CppCon    | Advanced talks         |
| https://www.youtube.com/@TheCherno | Practical explanations |

## Important Topics

### Mandatory

```txt
RAII
Move Semantics
Smart Pointers
Templates
Lambdas
Memory Layout
Cache Locality
Concurrency Basics
```

### Postpone

```txt
TMP
Expression Templates
Coroutines
Advanced Allocators
```

---

# 5. Operating Systems

## Resources

| Resource                                | Purpose         |
| --------------------------------------- | --------------- |
| Operating System Concepts               | Primary book    |
| https://pages.cs.wisc.edu/~remzi/OSTEP/ | Best supplement |

## Topics

```txt
Processes
Threads
Scheduling
Virtual Memory
Paging
Synchronization
Deadlocks
File Systems
I/O
Context Switching
```

Study OS by tracing:

```txt
What actually happens inside the machine
```

---

# 6. Networking

## Books

| Book                                     | Priority |
| ---------------------------------------- | -------- |
| Computer Networking: A Top-Down Approach | First    |
| TCP/IP Illustrated                       | Later    |

## Socket Programming

| Resource                     | Purpose           |
| ---------------------------- | ----------------- |
| https://beej.us/guide/bgnet/ | Practical sockets |

## Topics

```txt
TCP
UDP
HTTP
DNS
TLS Basics
Sockets
Congestion Control
Latency
Load Balancing
Keep Alive
```

---

# 7. Databases + DDIA

## Books

| Book                                  | Purpose                           |
| ------------------------------------- | --------------------------------- |
| DBMS Concepts                         | Database fundamentals             |
| Designing Data-Intensive Applications | Distributed systems understanding |

## Database Topics

```txt
Indexing
B+ Trees
Transactions
Isolation Levels
MVCC
Joins
Storage Engines
```

## DDIA Topics

```txt
Replication
Partitioning
Consistency
Transactions
Stream Processing
LSM Trees
```

Start DDIA around Month 4.

---

# 8. Systems / HFT-Oriented Concepts

## Important Areas

```txt
CPU Cache
Memory Hierarchy
Profiling
Lock Contention
Thread Pools
epoll
Syscalls
Low-Latency Networking
```

## Learn Later

```txt
io_uring
eBPF
DPDK
NUMA
SIMD
Kernel Development
```

---

# 9. Inside the Machine

## Focus Areas

```txt
CPU Pipeline
Caching
Instruction Execution
Branch Prediction
Memory Hierarchy
```

Purpose:

```txt
Build hardware + performance intuition
```

---

# 10. Projects

## Beginner Systems Projects

```txt
HTTP Server
Shell Clone
Thread Pool Library
Mini grep
Logging Library
```

## Strong Intermediate Projects

```txt
Redis Clone
Async Backend Server
TCP Chat Server
Key-Value Store
Linux Observability Tool
```

## Advanced Projects

```txt
Kafka-lite
Distributed Cache
Metrics System
Event Streaming Backend
```

---

# 11. Interview Preparation

## Coding

Focus:

```txt
Speed
Debugging
Pattern Recognition
Communication
```

## System Design

| Resource                                            | Purpose             |
| --------------------------------------------------- | ------------------- |
| https://github.com/donnemartin/system-design-primer | Intro system design |

Most juniors fail because of:

```txt
Weak coding + shallow fundamentals
```

Not because of:

```txt
Missing Kubernetes knowledge
```

---

# 12. English Communication

## Goal

```txt
Clear technical communication
```

## Practice

Daily:

```txt
Explain OS concepts aloud
Summarize DDIA chapters
Record explanations
Discuss project tradeoffs
```

## Resources

| Resource                               | Purpose       |
| -------------------------------------- | ------------- |
| https://www.bbc.co.uk/learningenglish/ | Listening     |
| https://youglish.com/                  | Pronunciation |

---

# 13. Daily Schedule

```txt
2h    Competitive Programming
1h    OS / Networking / DB Theory
1.5h  Systems Project Development
45m   Linux / Bash / Neovim
30m   English Speaking Practice
```

---

# 14. Weekly Structure

| Day      | Focus                            |
| -------- | -------------------------------- |
| Mon–Fri  | Deep work + implementation       |
| Saturday | Long contest + project push      |
| Sunday   | DDIA + mock interview + revision |

---

# 15. Avoid Early

```txt
Kubernetes
Cloud Certifications
React Ecosystem
Advanced Rust
DevOps Rabbit Holes
Blockchain
ML Distractions
```

---

# 16. Priority Order

```txt
1. Competitive Programming
2. Linux
3. Modern C++
4. Operating Systems
5. Networking
6. Systems Projects
7. Databases
8. DDIA
9. Distributed Systems
10. Rust
```

---

# Final Trajectory

```txt
Strong C++ Engineer
→ Systems Backend Engineer
→ Performance Engineer
→ HFT Infrastructure Possibility
```
