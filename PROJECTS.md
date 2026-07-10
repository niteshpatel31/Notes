# Hard & Very Hard CS Projects: A Self-Build Roadmap

Every project below is picked so the hard part is the **engineering**, not the typing — getting something correct under concurrency, fast on real hardware, or resilient to real failure. That's deliberate: none of this holds up if a model just writes it for you, and each entry lists *why* that's true.

---

## Why These Actually Resist "Just Prompt It"

| Resistance factor | What it means |
|---|---|
| **Correctness only shows up at runtime** | Race conditions, partial failures, and split-brain bugs in concurrent/distributed code don't appear by reading the source — you find them by running under load, injecting faults, and reasoning about interleavings. |
| **Performance claims require a real machine** | You can't guess your way to a fast CUDA kernel or a sub-microsecond order book. You profile on your actual GPU/CPU, find the actual bottleneck (occupancy, cache misses, false sharing, NUMA), and iterate. The numbers are the proof of work. |
| **The bugs live across layers** | Kernel + network + hardware + application is one system. Debugging a container escape or a dropped packet means understanding the whole stack, not the function you just wrote. |
| **The design decisions are judgment calls** | Which consensus protocol, which eviction policy, which data structure for *this* access pattern — these depend on constraints only you know, and picking wrong doesn't show up until much later. |

Every project lists **why it's hard**, the **core stack**, and a **"done when"** bar — something measurable, so you know you built the hard part and not a demo of it.

---

## Table of Contents

1. [NVCC & GPU Programming (CUDA)](#1--nvcc--gpu-programming-cuda)
2. [C++ (Systems Programming)](#2--c-systems-programming)
3. [AI & ML (From Scratch)](#3--ai--ml-from-scratch)
4. [Networking (DPI) & OS (Job Scheduling)](#4--networking-dpi--os-job-scheduling)
5. [System Design](#5--system-design)
6. [Python Full Stack](#6--python-full-stack)
7. [HFT & Quant — Infrastructure & Systems Engineering](#7--hft--quant--infrastructure--systems-engineering)
8. [Docker & Kubernetes](#8--docker--kubernetes)
9. [Linux & Bash](#9--linux--bash)
10. [Bonus Toolkits](#10--bonus-toolkits-worth-adding)
11. [Networking Protocols & Runtimes From Scratch](#11--networking-protocols--runtimes-from-scratch)
12. [Parallel & Scientific Computing (CPU-side)](#12--parallel--scientific-computing-cpu-side)
13. [Distributed Consensus, Beyond Plain Raft](#13--distributed-consensus-beyond-plain-raft)
14. [Where to Go Deeper](#14--where-to-go-deeper)

---

## 1 · NVCC & GPU Programming (CUDA)

#### 🟡 Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Tiled shared-memory GEMM** — hand-write matrix multiplication using shared-memory tiling and register blocking | Bank-conflict-free shared memory access, memory coalescing, and tiling all have to line up at once; naive versions run 10–50x slower than they should | CUDA C++, Nsight Compute | You hit >50% of your GPU's theoretical FLOPs and can explain every stall the profiler shows you |
| **Parallel graph algorithms on GPU** — BFS or PageRank on a multi-million-edge graph | Irregular memory access and load imbalance are GPU-hostile; naive per-vertex parallelism just thrashes memory bandwidth | CUDA, CSR graph representation, frontier-based load balancing | You beat a well-written single-threaded CPU baseline by an order of magnitude on a real graph dataset |
| **CUDA radix/bitonic sort at scale** — sort hundreds of millions of keys | Efficient prefix sums, coalesced scatter/gather, and multi-pass digit binning all have to work together correctly | CUDA, cooperative groups | You're within 2x of Thrust's sort on the same hardware |

#### 🔴 Very Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **FlashAttention from scratch** — reimplement IO-aware fused attention: tiling, online softmax, no materialized N×N score matrix | It's two back-to-back GEMMs plus a numerically-stable softmax fused into one kernel, with tensor-core `mma` instructions and `cp.async`/`ldmatrix` memory choreography — a well-known multi-week project even for experienced CUDA engineers | CUDA C++, tensor cores (Ampere+), Nsight Compute | Your forward+backward pass matches PyTorch's SDPA to ~1e-6 and lands within 2x of its latency |
| **Hand-tuned tensor-core GEMM vs. cuBLAS** — FP16/BF16 GEMM using `mma.sync`/WMMA | Getting near cuBLAS/CUTLASS means double buffering, swizzled shared-memory layouts, and warp specialization — cuBLAS is some of the most optimized software that exists | CUDA C++, CUTLASS as reference, Nsight Compute | You're within 20% of cuBLAS on at least one real matrix size on your GPU |
| **GPU ray tracer with an on-device BVH** — build and traverse a bounding volume hierarchy entirely on the GPU | Building a good BVH in parallel and traversing it without divergence-killing performance is a different problem than CPU ray tracing | CUDA or OptiX, LBVH/SAH construction | It renders a 10k+ triangle scene at interactive frame rates |
| **Multi-GPU ring all-reduce** — implement your own gradient synchronization across GPUs, no NCCL | Correct ring topology, overlapping compute with communication, and uneven chunk handling are all easy to get subtly wrong | CUDA, NVLink/PCIe peer access, MPI or raw sockets | You match NCCL's bandwidth utilization within a reasonable margin on 2+ GPUs |

---

## 2 · C++ (Systems Programming)

#### 🟡 Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Custom allocator suite** — arena, pool, and slab allocators with fragmentation analysis | Correct alignment, free-list management, and thread-safety without just wrapping malloc | C++17/20, `std::pmr` as reference | It beats the default allocator on an allocation-heavy workload you designed, with numbers |
| **Lock-free SPSC/MPMC queue** — built on atomics, not mutexes | Correct memory ordering (`acquire`/`release`), avoiding false sharing, and proving correctness under stress rather than "it seemed to work" | `std::atomic`, ThreadSanitizer | It survives a multi-hour ThreadSanitizer stress run with zero reported races |
| **Work-stealing thread pool** — per-thread deques with lock-free steal operations | Avoiding thundering-herd wakeups while keeping steal operations lock-free | C++20, atomics, condition variables or futex-style waiting | It scales near-linearly up to your core count on a fork-join workload |

#### 🔴 Very Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Port the LMAX Disruptor pattern to C++ and benchmark it** — pre-allocated ring buffer, sequence barriers, lock-free producer/consumer coordination | The entire point is avoiding false sharing and CAS contention — subtle padding or memory-ordering mistakes silently destroy the latency numbers that are the reason to build it | C++20, atomics, cache-line padding | Your latency histogram shows it beating a mutex-protected queue by an order of magnitude at p99 |
| **Toy compiler for a C subset** — lexer → parser → AST → codegen to x86-64 or LLVM IR | Register allocation, correct calling conventions, and control flow in generated assembly are unforgiving — one wrong instruction and the binary segfaults with no explanation | C++, LLVM's C++ API, or hand-written x86-64 | It compiles and correctly runs a nontrivial program (recursion, arrays, structs) |
| **Disk-based KV store with WAL and crash recovery** — B+Tree or LSM-tree storage engine | Durability means getting fsync ordering and write-ahead logging exactly right, and surviving a `kill -9` mid-write with a consistent recovered state | C++, raw file I/O, `mmap` optional | A fault-injection harness you write yourself can kill the process at any point during writes and it always recovers to a consistent state |

---

## 3 · AI & ML (From Scratch)

#### 🟡 Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Autograd engine + small NN framework** — reverse-mode automatic differentiation, then real CNN layers on top | Every op's backward pass (conv, batchnorm, pooling) has to be mathematically and numerically correct — one wrong gradient and training silently fails to converge | Python + NumPy only (no PyTorch/TF as the engine itself) | You train a CNN on CIFAR-10 and match a reference PyTorch implementation's accuracy within a couple of points |
| **BPE tokenizer from scratch** — merge-rule learning at corpus scale | Efficient merge learning and matching a reference tokenizer's exact output — off-by-one merge-order bugs are common and silent | Python or Rust for speed | It round-trips text exactly and reproduces GPT-2's vocabulary/merges trained on the same data |
| **DQN or PPO from scratch** | RL is notoriously sensitive to implementation details (advantage normalization, reward scaling, target-network updates) that don't fail loudly — they just quietly never learn | PyTorch for tensors, Gymnasium for environments | It solves a nontrivial Gym environment (e.g., LunarLander) reproducibly across multiple seeds |

#### 🔴 Very Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Pretrain, fine-tune, and serve your own small LLM end-to-end** — tokenizer → pretraining → SFT → (optionally RL) → a working chat interface, in the spirit of Karpathy's nanoGPT/nanochat lineage | Every stage has its own silent failure modes (loss spikes, data pipeline bugs, distributed desyncs), and the only real signal that it worked is a coherent model at the end. Karpathy's own nanochat gets a coherently-chatting model in ~4 hours (~$100) on an 8×H100 node, surpassing GPT-2's benchmark score by ~12 hours — that's the reference point | PyTorch, multi-GPU data-parallel training, a tokenizer you trained yourself | You have a model that holds a coherent conversation, backed by loss curves and eval numbers, not vibes |
| **Mixture-of-experts transformer with custom routing** | Load-balancing tokens across experts without dropping tokens or starving experts is an open-ended systems problem stacked on the modeling problem | PyTorch, hand-written routing/gating logic | Your MoE model matches a same-parameter-budget dense model's loss while activating meaningfully fewer parameters per token |
| **Diffusion model from scratch** — DDPM/DDIM: noise schedule, U-Net, sampler | The forward/reverse process math has to be exactly right, and sample quality is a black box until you generate images and actually look at them | PyTorch, a U-Net you write yourself | It generates recognizable, non-garbage images on CelebA or CIFAR-10 after a training run you ran yourself |
| **Quantization pipeline for LLM deployment** — a GPTQ/AWQ-style post-training quantization method | Preserving accuracy while cutting precision needs careful per-channel/group calibration — get it wrong and the model still "runs," just silently worse | PyTorch, a model you trained or downloaded | Your quantized model's eval score stays within a small margin of full precision, at a real memory/speed win |

---

## 4 · Networking (DPI) & OS (Job Scheduling)

### 4A. Deep Packet Inspection / Networking

#### 🟡 Hard

| Project | Core idea |
|---|---|
| **Packet sniffer with TCP stream reassembly** | Raw sockets/libpcap, reconstruct application-layer streams from out-of-order segments |
| **Signature-based NIDS** | Aho-Corasick multi-pattern matching against known attack signatures at real traffic rates |
| **Stateful firewall via eBPF/XDP** | Filter and rate-limit at the kernel hook, not in userspace |

#### 🔴 Very Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **DPDK-based DPI engine at line rate** — kernel-bypass packet I/O (poll-mode driver, huge pages, zero-copy `rte_mbuf`) with protocol fingerprinting that identifies HTTP/TLS/QUIC/BitTorrent by behavior, not port number | This is a real production pattern; DPI vendors ship exactly this architecture because the kernel networking stack can't keep up past 10Gbps | You process a saturated multi-Gbps link on one or two cores with the kernel stack visibly bypassed — it should stop even answering a ping while your app owns the NIC |
| **Encrypted traffic classification** | JA3/JA3S TLS fingerprinting plus a flow-statistics ML classifier for traffic you can't decrypt | — |
| **Evasion-resistant stream reassembly** | Correctly handle overlapping/out-of-order TCP segments and common IDS-evasion tricks | — |

### 4B. Operating Systems — Job & Process Scheduling

#### 🟡 Hard

| Project | Core idea |
|---|---|
| **Scheduler simulator** | Round Robin, MLFQ, and a CFS-like weighted-fair scheduler, compared on turnaround/wait-time metrics |
| **Green-threads library** | User-level cooperative threading with your own context switching (`ucontext` or hand-written assembly) |
| **Distributed job scheduler** | A mini-Slurm/Celery: a master assigns jobs, workers pull and execute, with retries and failure handling |

#### 🔴 Very Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **Write a real Linux scheduler with `sched_ext`** — Linux 6.12+ lets you load a custom CPU scheduling policy as an eBPF program (via `struct_ops`) without recompiling the kernel | This is genuinely new, active territory — NVIDIA and Canonical engineers are building production schedulers on it right now | Your scheduler is loaded and running real workloads, and you can show one workload where it beats the default EEVDF scheduler and one where it doesn't — and explain why |
| **Full container runtime** | Same project as the Docker/Kubernetes section, viewed from the OS side | — |
| **Distributed workflow orchestrator with gang scheduling** | Bin-pack jobs onto a worker pool with priority preemption and all-or-nothing scheduling for jobs needing multiple workers simultaneously | — |

---

## 5 · System Design

#### 🟡 Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Distributed rate limiter** — token bucket or sliding window, correct under concurrent access from multiple app servers | A naive Redis `INCR` isn't atomic enough under real concurrency; you need Lua scripting or a proper CAS loop, correct even at the boundary as request rate climbs | Redis, Lua scripting, a load generator | Under concurrent load testing, it never lets more than the configured limit through, even at edge cases |
| **Consistent-hashing distributed cache** — a mini-Memcached with replication | Handling node add/remove with minimal key remapping, and replicating without a single point of failure | Your language of choice, consistent hashing with virtual nodes | Removing a node redistributes only ~1/N of keys, verified by instrumentation |
| **Fan-out notification system** — push/email/SMS with retries and a dead-letter queue | Idempotency, retry storms, and ordering guarantees across channels that all fail independently | A message queue (RabbitMQ/SQS/Kafka) | It survives a downstream provider going down for 5 minutes with no duplicate and no lost deliveries |

#### 🔴 Very Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Raft-based distributed KV store** — leader election, log replication, snapshotting, linearizable reads | MIT's 6.5840 (formerly 6.824) is the canonical version of this project — students build exactly this across a semester, and it's deliberately difficult because of the randomness and timing involved in real network partitions and crashes | Go, or your language of choice | It survives randomized network partitions, delays, and crashes in an automated test harness, repeatably — not "it worked when I ran it once" |
| **Mini-Kafka** — partitioned log, replication, consumer groups, exactly-once semantics | Exactly-once delivery across a partitioned, replicated log is a genuinely hard distributed-systems problem; most real systems only get there with careful idempotency tricks | — | You can kill a broker mid-write and consumers still see each message exactly once |
| **Distributed transactions across services** — two-phase commit or the Saga pattern, tested with injected network partitions | Partial failure mid-transaction is the whole problem — you need compensating actions or a coordinator that survives crashes | Your microservices of choice, Toxiproxy for chaos | A chaos test suite injecting partition/latency/crash faults leaves the system provably consistent (or explicitly documents what it sacrifices, per CAP) |

---

## 6 · Python Full Stack

#### 🟡 Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Multi-tenant SaaS boilerplate** — RBAC, Stripe billing, audit logging, background jobs | — | FastAPI or Django, Postgres with row-level tenancy, Celery + Redis | Two tenants' data is provably isolated (write a test that tries to leak it) and billing events reconcile against Stripe's records |
| **Real-time chat with horizontal scaling** — WebSockets, presence, multi-instance fan-out via Redis pub/sub | A WebSocket connection is pinned to one server process — broadcasting to users connected to *other* instances is the actual problem to solve | — | It works correctly behind a load balancer with 2+ app instances, no sticky-session hack masking the real problem |
| **Observability stack for microservices** — distributed tracing, metrics, and log correlation across services | — | OpenTelemetry, Prometheus, structured logging with trace-ID propagation | You can take one slow user request and trace it through every service it touched, with timing per hop |

#### 🔴 Very Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **Build your own ASGI framework** — routing, middleware chain, and dependency injection against the raw ASGI spec | You're implementing the thing FastAPI/Starlette sit on top of — async request lifecycle, streaming responses, and middleware ordering all have real edge cases | An existing simple FastAPI app runs on your framework with minimal changes |
| **Distributed task orchestrator (mini-Airflow)** — DAG-based scheduling, retries, backfills, a web UI showing run status | — | A multi-step DAG with a failing task retries correctly, downstream tasks wait for it, and all of it is visible in your UI |
| **Train and serve your own small LLM through a full-stack app** — connects back to Section 3: your own trained/fine-tuned model behind a FastAPI inference server with a real chat frontend | — | It's a deployed, working chat app backed by a model you trained, not an API call to someone else's |

---

## 7 · HFT & Quant — Infrastructure & Systems Engineering

#### 🟡 Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **Limit order book with price-time priority matching** — the foundational HFT systems project | The data structure has to support O(log n)-or-better add/cancel/match while staying cache-friendly enough for nanosecond-scale latency. Real open-source attempts reach tens of millions of operations per second with p99 latencies around a microsecond | Modern C++ or Rust; sorted price levels, hash map for O(1) lookup, intrusive doubly-linked list per price level | A benchmark harness produces a real latency histogram (not just an average), and IOC/FOK/post-only flags all work correctly |
| **Lock-free logging library** — nanosecond-scale logging that never blocks the hot path | Formatting and I/O are slow, so you push raw data onto a lock-free ring buffer on the hot path and format/flush on a separate thread | — | Logging from the hot path adds single-digit nanoseconds of measured overhead |
| **FIX protocol engine** — session management (logon/heartbeat/sequence numbers) plus message parsing/generation | — | — | It correctly handles a sequence-number gap and resend request against a real or simulated counterparty |

#### 🔴 Very Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **NASDAQ ITCH feed handler that reconstructs a full order book** — parse the binary TotalView-ITCH protocol (delivered over MoldUDP64) and maintain a live book from add/cancel/execute/replace messages | A real, publicly-documented exchange protocol with 20+ message types and big-endian binary encoding, running against gigabytes of daily data. Open implementations reach order-book processing latencies in the tens of nanoseconds per message on ordinary hardware | C++, NASDAQ's public ITCH 5.0 sample data | Your reconstructed book matches a reference implementation's state at any point in the replay, with real throughput/latency numbers |
| **Kernel-bypass tick-to-trade pipeline** — multicast feed handler → order book → signal → order gateway, using DPDK or io_uring instead of the kernel network stack, with CPU pinning and NUMA-aware memory placement | Huge pages, poll-mode drivers, core isolation, and cache-topology-aware design all have to work together — the entire discipline exists because standard kernel networking can't hit the latency HFT firms need | — | You have an end-to-end tick-to-trade latency number (in microseconds, ideally sub-10) measured on real hardware, not simulated |
| **Matching engine with deterministic crash recovery** — persistence, journal replay, and provably identical state after a crash-and-restart | Determinism under replay is unforgiving — any nondeterminism in your matching logic (unordered iteration, floating point, thread scheduling) breaks the guarantee silently | — | Killing the process mid-session and replaying the journal produces byte-identical order-book state |

---

## 8 · Docker & Kubernetes

#### 🟡 Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **Multi-container app with a real CI/CD image pipeline** — Compose locally, then automated build/push/deploy against a real registry | Health checks, networking, and image versioning all have to line up so deploys are actually repeatable, not "works on my machine" | A fresh clone with zero manual steps builds, tests, and deploys itself through the pipeline alone |
| **Sidecar mTLS proxy pattern** — a basic service-mesh building block that intercepts traffic and terminates/originates TLS without touching application code | Certificate rotation, transparent traffic redirection (iptables/eBPF), and handling a sidecar that itself becomes unhealthy are all easy to get wrong invisibly | Two services communicate over verified mTLS with the application code completely unaware encryption is happening |
| **GitOps progressive delivery** — canary or blue/green rollout with automatic rollback triggered by real metrics, not a timer | The rollback decision has to come from real error-rate/latency signals wired into the deployment controller, not a fixed wait | You inject a deliberately bad deploy and watch it get rolled back automatically before it reaches all traffic |

#### 🔴 Very Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **OCI-compliant container runtime from scratch** — your own `runc`-equivalent: namespaces (PID/net/mount/UTS/IPC/user), cgroups v2 resource limits, `pivot_root`, and enough of the OCI runtime spec to run a real image | This is precisely what Docker/containerd/runc do under the hood. Get a namespace or cgroup wrong and you get a container that isn't actually isolated — which usually looks fine until it very much isn't | It runs a real Alpine/Debian rootfs with working process, network, and filesystem isolation, and a cgroup memory limit that actually kills a process that exceeds it |
| **Custom Kubernetes scheduler plugin** — implement Filter and Score extension points in the real Scheduling Framework for a workload-specific policy (e.g., preferring nodes with available GPU or low network load) | You're writing against the same framework the built-in scheduler plugins use — real Kubernetes API objects, informer caches, and the actual scheduling loop | Deployed to a real (or `kind`) cluster, pods requesting your scheduler are placed verifiably differently than the default scheduler would place them |
| **Chaos engineering tool for Kubernetes** — inject pod kills, network partitions, and resource exhaustion; measure recovery time | — | You have before/after SLO numbers for a real deployment under injected faults |

---

## 9 · Linux & Bash

#### 🟡 Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **`/proc`-based monitoring and alerting tool** — parse `/proc` and `/sys` directly, ship alerts via webhook, keep historical data | `/proc` counters are raw and cumulative — correct rates (CPU%, IOPS) require careful delta sampling, and noisy alerts erode trust fast | It correctly alerts on a real induced problem (a memory leak or fork bomb you trigger yourself) with zero false positives during normal operation |
| **Build your own shell in C** — job control, pipes, I/O redirection, signal handling (`SIGCHLD`, `SIGINT`, foreground/background jobs) | Correct process-group and terminal signal handling for job control is famously fiddly — get it wrong and Ctrl-C kills the wrong process or background jobs never report as finished | It correctly handles multi-stage pipelines, backgrounding/foregrounding, and Ctrl-C/Ctrl-Z like a real shell |
| **Encrypted incremental backup system with verified restores** — the "verified" part is the actual hard part; most backup scripts have never been test-restored | Incremental logic, key management, and proving a restore reproduces the original bit-for-bit are each their own failure surface | An automated test wipes a directory, restores it from backup, and diffs clean against the original |

#### 🔴 Very Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **Write a real Linux CPU scheduler with `sched_ext`** — same project as in the OS section above, listed here because it's as much a Linux/eBPF project as a scheduling-theory one | You're loading BPF `struct_ops` callbacks the kernel invokes on every scheduling decision, on a genuinely current kernel feature (mainlined in 6.12) | `lsns`/`bpftool` show your scheduler active and handling real processes, with a benchmark against the default |
| **eBPF/bpftrace observability suite** — trace syscall latency, disk I/O, or network stalls system-wide, in the spirit of a mini-BCC toolkit | — | It correctly diagnoses a real performance problem you deliberately introduced (e.g., pinpoints exactly which syscall a slow script is stuck in) |
| **Custom FUSE filesystem** — an encrypted overlay or content-addressable dedup filesystem | — | It survives a real workload (untar a large repo, run a build) without corruption, and delivers on its one core feature verifiably |

---

## 10 · Bonus Toolkits Worth Adding

These four come up constantly in "genuinely hard CS project" circles and pair well with everything above.

| Category | 🟡 Hard | 🔴 Very Hard | Done when (very hard) |
|---|---|---|---|
| **Database Internals** | A buffer pool manager with LRU-K eviction; a standalone B+Tree index with concurrent latching | A full disk-oriented DBMS — buffer pool + index + query execution operators + concurrency control — in the mold of CMU's 15-445 course (their teaching DBMS, BusTub, is real and open-source) | It executes real SQL-like queries correctly under concurrent transactions with your chosen isolation level actually enforced, not just assumed |
| **Security: Fuzzing & Binary Analysis** | A mutation-based fuzz harness against a real open-source library, with crash triage (dedup crashes by stack hash) | A coverage-guided fuzzer from scratch — compile-time edge instrumentation feeding a coverage bitmap, plus a genetic algorithm mutating inputs toward new coverage (the actual mechanism tools like AFL use) | It finds a real, previously-unknown crash in a real target you didn't write, and you can explain why the mutation strategy found it |
| **Compilers & Language Runtimes** | A tree-walking interpreter for a small language with closures and a real (if simple) garbage collector | A full ahead-of-time compiler — lexer, parser, AST, code generation to LLVM IR or a custom bytecode VM with its own GC | It compiles and correctly runs a nontrivial program (recursive data structures, first-class functions) faster than tree-walking the same program |
| **Rust Systems Programming** | A Redis clone — RESP protocol, in-memory data structures, basic persistence (RDB-style snapshot) | Your own async runtime — executor, reactor, and futures, no `tokio` | It correctly runs a real concurrent workload (e.g., a small web server) under load with no data races (verified with `cargo miri` or loom) |

---

## 11 · Networking Protocols & Runtimes From Scratch

#### 🟡 Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **DNS server from scratch** | The binary packet format (label compression, record types, header flags) is unforgiving, and TTL-correct caching is easy to get subtly wrong | Any language, raw UDP sockets | `dig`/`nslookup` return correct A, AAAA, CNAME, and MX answers, including compressed-name parsing |
| **Redis clone (RESP protocol)** | The fun part isn't the hash map — it's making persistence and replica sync correct under concurrent writes | Your language of choice; Redis's protocol docs as spec | A real `redis-cli` talks to your server for GET/SET/EXPIRE/replication, no compatibility shim |
| **Userspace TCP/IP stack over TAP** | Correct TCP means implementing the state machine (SYN/ACK/FIN/RST), retransmission timers, and window management — get it wrong and connections hang silently instead of erroring | C or Rust, a TAP device, `tcpdump` for verification | A real browser or `curl` completes an HTTP request through your stack, verified byte-for-byte against a capture |

#### 🔴 Very Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **TCP/IP stack inside a teaching kernel** | You're debugging protocol logic and kernel scheduling/interrupts at once — a bug can live in either layer, with no userspace safety net | C, an xv6-style kernel, virtual NIC | Kernel serves a real TCP connection to a host machine, with congestion control visibly backing off under induced packet loss |
| **Video/audio codec + real-time streaming protocol** | Correctness and performance matter simultaneously — a decoder bug produces visible artifacts, a slow encoder can't hit real framerates | C/C++/Rust, raw frame buffers, a documented bitstream format | A real video source streams end-to-end at target framerate, visually lossless at your target bitrate |
| **WebAssembly runtime from scratch** | Correctness against the spec's type system and control-flow validation *is* the project — most toy interpreters silently accept invalid modules | Rust, C++, or Zig | Passes a meaningful chunk of the official WebAssembly spec test suite, not a hand-picked sample |

---

## 12 · Parallel & Scientific Computing (CPU-side)

> Sourced from CMU 15-418/618's own final-project lists — the canonical parallel-programming course, used for over a decade because these categories reliably surface real parallel-speedup problems.

#### 🟡 Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **Parallel ray tracer** | Load imbalance across scene regions and cache-unfriendly access patterns mean naive parallelism scales poorly | Near-linear speedup up to your core count on a real, non-trivial scene |
| **Parallel BDD package** | The most widely used BDD library is purely sequential for a reason — parallelizing graph construction at this scale is genuinely open territory | Your parallel implementation beats a sequential BDD library on a real verification-style workload |

#### 🔴 Very Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **High-resolution physical simulation** (fluid / cloth / rigid-body) | The numerical solver has sequential dependencies that resist naive parallelization; stability and performance fight each other | Runs at interactive rates at a resolution that's intractable single-threaded, with a documented stability check |
| **Parallel sparse linear solver** (conjugate-gradient / multigrid) | Sparse matrix access patterns are irregular and memory-bandwidth-bound; naive decomposition thrashes cache | Matches or beats a well-known sequential baseline by a meaningful margin, with a scaling chart |

---

## 13 · Distributed Consensus, Beyond Plain Raft

> Section 5's "Raft-based distributed KV store" is the right entry point — these go further, toward what production systems actually run.

#### 🟡 Hard

| Project | Why it's hard | Done when |
|---|---|---|
| **Multi-Paxos with cluster membership changes** | Paxos's own inventors (and the Raft paper) note its abstract description is far from a working implementation — you make the same real engineering calls (multi-decree optimization, leader leases) production systems had to invent | Cluster survives node add/remove mid-operation under a fault-injection harness, with no split-brain |

#### 🔴 Very Hard

| Project | Why it's hard | Stack | Done when |
|---|---|---|---|
| **PBFT-style Byzantine fault tolerance** | Unlike Raft/Paxos, no single node's report can be trusted — every phase needs enough independent confirmation to detect a lying node, and message complexity is real | Castro & Liskov's original PBFT paper as reference | A harness where some nodes send conflicting/malicious messages still leaves the honest majority in agreement |
| **Minimal blockchain with a real fork-choice rule** | The interesting failure mode is a network partition producing two valid-looking chains — your fork-choice rule must deterministically converge once it heals, under adversarial reordering | Your language of choice | A simulated partition producing two competing forks converges to one canonical chain across all nodes, verified automatically |

---

## 14 · Where to Go Deeper

Not exhaustive, just real anchors worth reading before you start.

| Area | Resource |
|---|---|
| **Distributed systems** | MIT's 6.5840 course site (labs + lecture notes on Raft, sharding) |
| **Databases** | CMU's 15-445 course site and the public BusTub repo |
| **HFT infra** | The LMAX Disruptor technical papers; NASDAQ's public ITCH 5.0 specification |
| **Linux scheduling** | The `sched-ext/scx` repo and its example schedulers |
| **GPU kernels** | The GPU-MODE community (lectures + Discord) for CUDA kernel-writing culture |
| **Fuzzing** | The AFL++ documentation and `google/fuzzing` tutorials |
| **Parallel computing** | CMU 15-418/618's project ideas pages — published most years, a direct current source for scoping |
| **Protocol scaffolding** | CodeCrafters' project list (Redis clone, DNS server, Git clone, Kafka clone, your-own-shell) — "build a real thing against a real spec" with automated test suites |
| **Consensus** | raft.github.io for Raft; the original Paxos and PBFT papers for the harder variants |
| **WebAssembly** | The official WebAssembly spec test suite — the actual bar for "done," not a hand-rolled sample |

---

## How to Actually Use This

- **Go deep on 2–3 categories, not wide on 14.** A finished "very hard" project with real benchmarks and a written design doc beats six half-finished "hard" ones.
- **Do the hard tier in a category before the very-hard one.** The hard-tier projects usually build a piece you'll reuse — the allocator shows up in the KV store, the order book shows up in the matching engine, the namespaces show up in the runtime.
- **Instrument before you optimize, and keep the raw numbers.** Every "done when" bar above needs a benchmark harness you wrote yourself — that harness, plus the numbers it produced, is most of the actual evidence you built the thing.
- **Write down what you'd do differently.** A README with your design trade-offs and known limitations is worth more than clean code with no explanation, and it's the part that's genuinely hard to fake.

Given a mix like GPU kernels, DPI, HFT infra, kernel scheduling, and k8s scheduling, this reads like a low-level infrastructure/systems-engineering track rather than general app development. The closest new fits from Sections 11–14 are:

- **§11's TCP/IP-in-kernel project** — pairs naturally with DPI work; same protocol layer, different angle.
- **§13's PBFT** — pairs with the Raft KV store from §5 as a strictly harder next step; same skill, higher ceiling.