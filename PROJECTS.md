# Hard & Very Hard CS Projects
## Zero AI Generation — Built Entirely By Hand
### Crosses Multiple Domains Per Project

> Every project below spans **3–4 categories** from your toolkit list.  
> Difficulty is rated **Hard** or **Very Hard** — nothing below that.  
> No AI can generate these. Each requires original systems thinking,  
> debugging at the kernel/hardware level, and deep domain knowledge.

---

## Legend

```
Difficulty:   🔴 Hard    🔥 Very Hard
Categories:   Each tag represents one of your 9 toolkits
Timeline:     Realistic solo build time with 4–5 hrs/day focus
```

---

## Project 01 — `xdp-firewall` — Programmable Packet Filter at Line Rate

```
🔥 Very Hard  |  Timeline: 8–12 weeks
Categories: Networking/DPI · Linux/Bash · Docker/Kubernetes · C++
```

**What you build:**  
A stateful XDP (eXpress Data Path) firewall that inspects packets at the
NIC driver level — before the Linux kernel networking stack sees them.
It classifies traffic using DPI (HTTP, DNS, TLS fingerprinting via JA3
hashes), enforces connection rate limits per source IP, performs stateful
TCP session tracking, and exposes real-time metrics via a gRPC API running
in a sidecar container. The control plane runs as a Kubernetes DaemonSet;
the data plane is an eBPF/XDP C program loaded via `libbpf`.

**Tech Stack:**
- eBPF/XDP in C — the data plane kernel program
- `libbpf` — loader and map management from userspace
- `bpftool` — inspect running programs and maps
- C++ control plane — gRPC server exposing metrics + rule updates
- Linux TC (traffic control) for egress filtering (XDP only handles ingress)
- Docker — containerize the control plane
- Kubernetes DaemonSet + CRD — deploy to every node, configure via YAML
- Prometheus + Grafana — visualize packets/sec, drops, connection rates
- Bash — `tc`, `ip link`, `bpftool prog list` automation scripts

**What makes it hard:**
XDP programs have strict constraints — no loops over unbounded data,
no dynamic memory allocation, verifier rejects invalid programs silently,
map accesses require careful boundary checks or the verifier kills it.
Stateful TCP tracking in an XDP program requires BPF maps with careful
concurrency — multiple CPUs hit the same map simultaneously.
JA3 TLS fingerprinting requires parsing TLS ClientHello within the
40-microsecond budget XDP operates in.

**Why it impresses:**
Cloudflare, Meta, and every major CDN uses XDP for DDoS mitigation.
This demonstrates kernel-level networking that almost no candidate has.
The Kubernetes deployment shows you understand both systems depth
and cloud-native operations simultaneously.

**References:**  
`github.com/xdp-project/xdp-tutorial` — start here for XDP fundamentals  
`github.com/cilium/cilium` — production XDP/eBPF reference  
Cloudflare blog: "XDP in production" series

---

## Project 02 — `gpunet` — CUDA-Accelerated Packet Classification Engine

```
🔥 Very Hard  |  Timeline: 10–14 weeks
Categories: NVCC/GPU · Networking/DPI · C++ · Linux/Bash
```

**What you build:**  
A packet classification engine that offloads DPI pattern matching to the
GPU using CUDA. The CPU receives raw packets via DPDK (kernel-bypass),
batches them into GPU-friendly structures, copies to device memory, runs
Aho-Corasick multi-pattern matching on thousands of packets in parallel
across CUDA thread blocks, then copies classification results back.
Benchmark it against a CPU-only Hyperscan (Intel's SIMD regex engine)
baseline and measure throughput and latency at 1M, 10M packets/second.

**Tech Stack:**
- NVCC / CUDA C++ — GPU kernel for parallel Aho-Corasick
- DPDK — kernel bypass packet reception (userspace NIC driver)
- C++17 — pipeline orchestration, CPU↔GPU transfer management
- `cudaMemcpyAsync` + CUDA streams — overlap CPU and GPU work
- `nvprof` / Nsight Systems — GPU performance profiling
- Bash — automated benchmark harness, packet generator scripts
- `pktgen-dpdk` — generate test traffic at line rate
- Linux hugepages + NUMA-aware memory allocation

**What makes it hard:**
DPDK requires physical hardware or careful VM configuration.
GPU memory bandwidth is the bottleneck — naive copies kill performance.
CUDA kernel occupancy must be tuned: too few threads wastes GPU,
too many causes register spilling to slow local memory.
The Aho-Corasick state machine must be restructured for coalesced
memory access — sequential CPU layout destroys GPU performance.
Measuring end-to-end latency correctly requires TSC synchronization
between CPU and GPU timing domains.

**Why it impresses:**
This is the intersection of GPU programming and networking that
almost no engineer has. Research papers (ResearchGate, 2014 onward)
show GPU-accelerated DPI outperforms CPU by 10–30x at high packet rates.
Demonstrates you can think in parallel across both SIMD and CUDA simultaneously.

**References:**  
`github.com/DPDK/dpdk` — DPDK source and examples  
ResearchGate: "On implementing packet inspection using CUDA"  
NVIDIA Nsight Systems documentation for profiling

---

## Project 03 — `chronos` — Multi-Level Feedback Queue Job Scheduler in Userspace

```
🔥 Very Hard  |  Timeline: 8–10 weeks
Categories: OS/Job-Scheduler · C++ · Linux/Bash · Docker/Kubernetes
```

**What you build:**  
A userspace process scheduler implementing Multi-Level Feedback Queue
(MLFQ) scheduling with CPU pinning, cgroup v2 resource isolation, and
real-time priority boosting. It manages a pool of worker processes,
dynamically adjusts their Linux scheduler class (`SCHED_FIFO`,
`SCHED_RR`, `SCHED_NORMAL`) based on observed behavior, pins latency-
sensitive jobs to isolated CPU cores using `taskset` and `cpuset` cgroups,
and tracks scheduling fairness via per-job wait time histograms.
A Python FastAPI dashboard visualizes queue depths, turnaround times,
and CPU utilization per queue level in real-time.

**Tech Stack:**
- C++ — MLFQ engine: priority queues, job state machine, CPU affinity
- Linux cgroup v2 — `cpu.max`, `cpuset.cpus`, `memory.max` per job group
- `SCHED_FIFO` / `SCHED_RR` / `sched_setattr()` — kernel scheduler interaction
- `taskset` + `numactl` — CPU and NUMA pinning
- `clone()` / `fork()` / `execve()` — job process lifecycle management
- `perf_event_open()` — measure per-job CPU cycles and cache misses
- Python FastAPI — REST API + WebSocket for live dashboard
- Docker — containerize the daemon + dashboard
- Kubernetes — deploy as a DaemonSet, expose metrics via Prometheus
- Bash — `cgcreate`, `cgset`, stress-testing scripts

**What makes it hard:**
cgroup v2 hierarchy must be designed carefully — wrong hierarchy causes
unexpected resource inheritance. `SCHED_FIFO` is real-time priority and
can starve normal processes entirely if misconfigured — your system hangs.
Measuring scheduler fairness requires tracking per-job wait time in
nanoseconds, which means TSC-based timing (not `clock_gettime` which has
syscall overhead that distorts the measurement).
The boost mechanism (preventing starvation by promoting old jobs) requires
careful threshold tuning — too aggressive and MLFQ degrades to FIFO,
too conservative and starvation occurs anyway.

**Why it impresses:**
OS schedulers are the core of every systems interview at FAANG and HFT firms.
Building one means you understand the tradeoffs — not just from a textbook
but from debugging why `SCHED_FIFO` at priority 99 froze your terminal.
The Kubernetes DaemonSet deployment shows real operational thinking.

**References:**  
Silberschatz OS Concepts Ch 5 — MLFQ theory  
`man 7 sched` — Linux scheduler classes  
`man 2 sched_setattr` — setting scheduler parameters programmatically

---

## Project 04 — `voltex` — GPU-Accelerated Time Series Inference Engine

```
🔥 Very Hard  |  Timeline: 10–16 weeks
Categories: NVCC/GPU · AI & ML · C++ · HFT/Quant · Python Full Stack
```

**What you build:**  
A low-latency inference engine for financial time series. You train a
1D-CNN + LSTM hybrid model in Python (PyTorch) on tick data to predict
short-term price direction. Export the trained weights. Build a C++/CUDA
inference engine from scratch — no TensorFlow, no ONNX Runtime — that
implements: 1D convolution with cuDNN or hand-written CUDA kernels,
matrix multiplications with cuBLAS, sigmoid/tanh activations in CUDA,
and a ring buffer that feeds sliding 100-tick windows into the engine
at sub-millisecond latency. The Python backend serves a FastAPI dashboard
showing live predictions, confidence intervals, and per-signal latency.

**Tech Stack:**
- NVCC / CUDA C++ — inference kernels (conv1D, matmul, activations)
- cuBLAS — optimized BLAS for matrix operations
- cuDNN (optional) — reference implementation to validate against
- PyTorch Python — model training only (not inference)
- C++17 — ring buffer, sliding window, FIX message parser
- Python FastAPI + WebSocket — live prediction streaming to browser
- React + Recharts — real-time chart of predictions vs actual
- Docker — package the inference service
- Linux `perf` + `nvprof` — latency profiling
- Fixed-point arithmetic — prices in int64_t ticks, no doubles

**What makes it hard:**
Writing a CUDA conv1D kernel with correct boundary handling, coalesced
memory access, and shared memory tiling is 3–4 days of debugging alone.
The sliding window must be lock-free — a mutex on the ring buffer adds
50–200μs latency which defeats the purpose entirely.
Validating CUDA kernel output against PyTorch reference requires bit-exact
floating-point comparison (which is architecture-dependent — results differ
between V100 and A100 due to non-deterministic reduction operations).
The end-to-end latency budget: FIX message parse → window update →
GPU inference → signal output must be under 500μs.

**Why it impresses:**
This is the rarest combination in the market: HFT-grade latency engineering
meets GPU inference meets full-stack visualization. Covers all 5 of NVCC,
C++, AI/ML, HFT, and Python Full Stack simultaneously.

**References:**  
`docs.nvidia.com/cuda/cublas` — cuBLAS API  
`github.com/NVIDIA/cudnn-frontend` — cuDNN interface  
PyTorch `torch.onnx.export` — weight extraction

---

## Project 05 — `riptide` — Distributed FIX Protocol Gateway with eBPF Telemetry

```
🔥 Very Hard  |  Timeline: 10–14 weeks
Categories: HFT/Quant · Networking/DPI · Linux/Bash · Docker/Kubernetes
```

**What you build:**  
A FIX 4.2/4.4 protocol gateway — the standard messaging protocol used
by every exchange and broker for order submission. It parses inbound FIX
messages from a TCP stream, validates them (checksum, sequence numbers,
required fields), routes them to an internal order management system
(which you also build), and responds with FIX execution reports.
The twist: an eBPF program attached to the TCP socket using `SO_ATTACH_BPF`
measures wire-to-application latency for every single message with
nanosecond precision, exposing a Prometheus histogram. Deploy the entire
stack on Kubernetes with a Helm chart.

**Tech Stack:**
- C++20 — FIX parser (tag=value format, checksum validation), OMS state machine
- eBPF/BPF socket filter — nanosecond latency measurement at kernel level
- `SO_ATTACH_BPF` — attach BPF to individual sockets
- Linux `SO_TIMESTAMPING` — hardware/software packet timestamps
- Python — FIX message simulator (client that sends synthetic orders)
- Docker — multi-container: gateway, OMS, metrics collector
- Kubernetes + Helm — production-grade deployment
- Prometheus + Grafana — per-message latency histogram, p50/p99/p999
- Bash — load testing scripts, FIX message generators

**What makes it hard:**
FIX parsing looks simple (tag=value pairs delimited by `\x01`) but edge
cases are brutal: partial reads on TCP, split messages across recv() calls,
sequence number gaps requiring resend requests, heartbeat management.
Attaching eBPF to individual sockets requires kernel 4.19+ and careful
privilege management in containers.
The sequence number state machine (FIX has strict ordering guarantees)
requires lock-free design — a mutex in the parser hot path adds 2–5μs.
Kubernetes networking adds latency variability that the eBPF telemetry
will expose — tuning pod QoS class and CPU pinning to reduce jitter is
a separate week of work.

**Why it impresses:**
FIX protocol knowledge is the entry credential for HFT systems roles.
Adding eBPF telemetry at the kernel level, deploying via Kubernetes,
and measuring wire-to-application latency demonstrates the full stack
from hardware timestamps to Grafana dashboards.

**References:**  
`github.com/quickfix/quickfix` — reference FIX implementation (study, not use)  
`github.com/0burak/imperial_hft` — HFT C++ patterns  
FIX Protocol Ltd spec: `fixtrading.org/standards`

---

## Project 06 — `konductor` — Kubernetes Operator for GPU Workload Scheduling

```
🔥 Very Hard  |  Timeline: 10–14 weeks
Categories: Docker/Kubernetes · AI & ML · NVCC/GPU · Python Full Stack
```

**What you build:**  
A custom Kubernetes operator (in Go or C++) that manages GPU-accelerated
ML inference workloads. It defines custom CRDs: `InferenceDeployment` and
`GPUBudget`. When an `InferenceDeployment` is created, the operator:
schedules pods with specific GPU fraction requests (using NVIDIA MIG or
time-slicing), monitors GPU utilization via NVML (NVIDIA Management Library),
automatically scales replicas based on request queue depth + GPU idle time,
evicts low-priority inference jobs when a high-priority job arrives,
and reports per-model inference latency p99 to Prometheus.
Build a Python FastAPI + React dashboard showing live GPU utilization,
model serving latency, and scaling decisions with explanations.

**Tech Stack:**
- Go or C++ — Kubernetes operator using `controller-runtime`
- Kubernetes CRD + API — `InferenceDeployment`, `GPUBudget` custom resources
- NVML (NVIDIA Management Library) — GPU utilization, memory, temperature
- CUDA C++ — the actual inference workload (use your SIMD tensor from earlier)
- Docker — multi-stage build: CUDA base → inference binary → operator binary
- Helm — package the operator for deployment
- Python FastAPI — metrics API + scheduling decision audit log
- React + Recharts — live dashboard
- Prometheus custom metrics — GPU util, queue depth, inference latency
- Bash — integration test scripts, chaos engineering (kill random pods)

**What makes it hard:**
Kubernetes operators require understanding the reconciliation loop deeply —
if your reconciler is not idempotent, you get infinite re-queues.
NVML from inside a container requires `privileged: true` or careful device
plugin integration — not well documented.
GPU time-slicing is a relatively new feature (NVIDIA drivers 470+) with
fragile configuration. CUDA MIG (Multi-Instance GPU) partitioning changes
the device name visible inside containers which breaks naive GPU detection.
The scaling algorithm must avoid oscillation (scale up → GPU idle → scale
down → queue builds → scale up again in a loop) — requires hysteresis.

**Why it impresses:**
Custom Kubernetes operators are what platform engineering teams at
FAANG actually build. Combining one with GPU workload management covers
two of the hottest intersection points in the industry right now:
ML infrastructure and cloud-native operations.

**References:**  
`kubebuilder.io` — Kubernetes operator framework  
`github.com/NVIDIA/k8s-device-plugin` — reference GPU plugin  
NVIDIA NVML documentation

---

## Project 07 — `memstorm` — Userspace Memory Allocator with NUMA Awareness

```
🔥 Very Hard  |  Timeline: 6–10 weeks
Categories: C++ · OS/Job-Scheduler · Linux/Bash · HFT/Quant
```

**What you build:**  
A production-grade general-purpose memory allocator to replace `malloc`/`free`
in latency-critical applications. Implements: slab allocator for fixed-size
objects (per-CPU caches to eliminate cross-thread contention), buddy system
allocator for large allocations (power-of-2 splitting and coalescing),
huge page support via `mmap(MAP_HUGETLB)` for large arenas (eliminates TLB
misses on working sets > 1GB), NUMA-aware allocation (allocates memory
on the same NUMA node as the calling thread via `numa_alloc_onnode`),
lock-free free list using compare-and-swap for the per-CPU cache path,
and a poisoning debug mode that writes 0xDEADBEEF on free and checks
on allocation (catches use-after-free in debug builds, disabled via
`#ifdef NDEBUG` macro to zero overhead in release).

**Tech Stack:**
- C++20 — allocator core, per-CPU caches, buddy system implementation
- `mmap(MAP_HUGETLB)` — 2MB huge pages from Linux kernel
- `libnuma` / `numa.h` — NUMA topology queries and node-local allocation
- `__atomic_compare_exchange_n` / `std::atomic` — lock-free free lists
- `#ifdef NDEBUG` macros — debug poisoning compiled out in release
- `LD_PRELOAD` — swap your allocator into any existing binary without recompilation
- `valgrind --tool=massif` — memory profiling to validate allocator behavior
- `perf stat -e cache-misses` — measure TLB miss reduction from huge pages
- Google Benchmark — measure allocation latency vs `malloc`, `jemalloc`, `tcmalloc`
- Bash — benchmark harness, `numactl` topology scripts

**What makes it hard:**
The per-CPU slab cache requires thread-local storage with careful
migration handling — what happens when a thread migrates between CPUs
mid-allocation? The free list that was "local" is now remote.
Huge page availability is not guaranteed — `mmap` with `MAP_HUGETLB`
silently falls back to regular pages if the huge page pool is exhausted.
Your allocator must handle this fallback transparently.
The buddy system coalescing algorithm is O(log n) but with terrible
cache behavior — adjacent buddies are not adjacent in memory, requiring
a bitmap that itself pollutes cache.
Benchmarking allocators correctly is an art — thread count, allocation
size distribution, free pattern all dramatically change relative performance.

**Why it impresses:**
jemalloc (used by Firefox, FreeBSD), tcmalloc (used by Chrome, Google's
services), and mimalloc (used by Microsoft) are the canonical allocators.
Building one demonstrates the deepest OS and C++ knowledge in your portfolio.
HFT firms use custom allocators in their hot path — this project is directly
applicable and almost no candidate has built one.

**References:**  
`github.com/jemalloc/jemalloc` — study the slab + arena design  
`github.com/microsoft/mimalloc` — study the segment-based approach  
Paul Wilson's "Dynamic Storage Allocation: A Survey and Critical Review"

---

## Project 08 — `pyroscale` — Distributed Continuous Profiler with eBPF

```
🔴 Hard  |  Timeline: 7–10 weeks
Categories: Linux/Bash · Networking/DPI · Docker/Kubernetes · Python Full Stack
```

**What you build:**  
A continuous CPU profiler that uses eBPF `perf_event` sampling to capture
stack traces from every process on a Linux host at 99Hz — with zero code
changes to the profiled application. The eBPF kernel program collects
stack traces via `bpf_get_stackid()`, stores them in a BPF map, a userspace
Go or C++ daemon reads the map every 100ms, symbolizes the stack frames
using `/proc/PID/maps` + `libunwind`, aggregates into flamegraph data,
and streams to a central server. Deploy as a Kubernetes DaemonSet.
The central server (Python FastAPI) stores profiles in SQLite, serves a
React frontend that renders interactive flamegraphs (using the `d3-flame-graph`
library) and lets you diff two time ranges to see what got slower.

**Tech Stack:**
- eBPF — `perf_event` sampling, `BPF_MAP_TYPE_STACK_TRACE` maps
- `libbpf` + C — eBPF program loader
- C++ or Go — userspace daemon: map reader, symbolizer, HTTP client
- `libunwind` / `libdw` — stack frame symbolization
- Python FastAPI — central aggregation server + REST API
- React + `d3-flame-graph` — interactive flamegraph visualization
- SQLite — profile storage with time-range queries
- Docker — agent container + server container
- Kubernetes DaemonSet — deploy agent to every node
- Bash — deployment scripts, `bpftool prog list` diagnostics

**What makes it hard:**
Stack symbolization is the hard part: ASLR randomizes load addresses,
so you must read `/proc/PID/maps` at the exact time the sample was taken.
JIT-compiled code (Java, Python) has no symbols at all — requires runtime
agent hooks or `perf map` files.
The eBPF `BPF_MAP_TYPE_STACK_TRACE` map fills up fast at 99Hz across
many processes — designing the eviction policy without losing important
samples requires careful map sizing and cleanup logic.
Flamegraph diffing requires stable stack frame normalization — the same
function must hash identically across two captures even if address
randomization changed its virtual address.

**Why it impresses:**
This is production observability infrastructure. Pyroscope (16K GitHub stars)
and Parca are the open-source equivalents. Building one means you understand
the full Linux observability stack from eBPF kernel programs to interactive
frontend visualization — a combination that is extremely rare at entry level.

**References:**  
`github.com/grafana/pyroscope` — production reference  
`github.com/parca-dev/parca-agent` — eBPF profiler reference  
Brendan Gregg's flamegraph papers and blog

---

## Project 09 — `arbitron` — Statistical Arbitrage Backtesting Platform

```
🔴 Hard  |  Timeline: 8–10 weeks
Categories: HFT/Quant · Python Full Stack · C++ · Linux/Bash
```

**What you build:**  
A full backtesting platform for pairs trading / statistical arbitrage
strategies on tick-level historical data. The core engine is C++ for
performance — it processes 100M+ ticks without memory copies by memory-
mapping the data file, runs cointegration tests (Engle-Granger, Johansen)
implemented in C++ from scratch (no pandas/statsmodels), simulates order
execution with realistic market impact (square-root law) and queue priority
modeling, and outputs per-trade P&L with transaction cost attribution.
A Python FastAPI + React frontend lets you configure strategy parameters,
submit backtest jobs, and visualize equity curves, Sharpe ratio, max
drawdown, and signal decomposition.

**Tech Stack:**
- C++20 — backtesting engine, cointegration math, tick data parser
- `mmap` — memory-map multi-GB tick data files, zero-copy reads
- Fixed-point arithmetic — prices in int64_t, no floating point
- BLAS (OpenBLAS) — matrix operations for Johansen cointegration
- Python FastAPI — job submission API + results storage
- Celery + Redis — async backtest job queue
- React + Recharts — equity curve, drawdown, signal visualization
- PostgreSQL — strategy configs, backtest results, trade logs
- Docker Compose — C++ engine + Python API + Redis + Postgres
- Bash — data download scripts, CI pipeline, benchmark harness

**What makes it hard:**
Cointegration from scratch: Engle-Granger requires OLS regression,
Johansen requires eigendecomposition of a matrix — both must be
implemented without scipy. BLAS for eigendecomposition via `LAPACK`
`dsyev_` is the correct approach but the Fortran-style API is brutal.
Realistic market impact modeling requires estimating queue position —
a limit order placed at the current best bid is behind all existing orders
at that level. Ignoring this makes backtests unrealistically profitable.
Processing 100M ticks in C++ with `mmap` is fast but memory access patterns
matter — sequential reads are CPU cache-friendly; random access by symbol
is not. Designing the file format for sequential access by time requires
offline sorting of the raw tick data.

**Why it impresses:**
This directly targets HFT infrastructure and quant developer roles.
The C++ engine + Python API split is exactly how real trading infrastructure
is built — C++ for the hot path, Python for configuration and analysis.
Implementing cointegration from scratch (not sklearn) proves mathematical
competence that most candidates at your level do not have.

**References:**  
`github.com/0burak/imperial_hft` — HFT C++ patterns  
Ernest Chan "Algorithmic Trading" — pairs trading theory  
`lapack.org` — `dsyev_` eigendecomposition

---

## Project 10 — `netwatch` — Real-Time Network Topology Mapper via Passive DPI

```
🔴 Hard  |  Timeline: 6–9 weeks
Categories: Networking/DPI · Linux/Bash · Python Full Stack · Docker/Kubernetes
```

**What you build:**  
A passive network topology discovery system. It sniffs raw packets on a
Linux network interface using `AF_PACKET` sockets (no libpcap), performs
DPI to identify application protocols (HTTP, DNS, Redis, PostgreSQL, gRPC)
by inspecting payload bytes, builds a service dependency graph (which IP
is talking to which service on which port), stores it in a graph database
(Neo4j or plain adjacency lists in PostgreSQL), and renders a live interactive
service map in a browser. Deploy as a Kubernetes DaemonSet — one instance
per node, each monitoring its node's pod traffic. A central FastAPI
aggregator merges node-level graphs into a cluster-wide topology.

**Tech Stack:**
- C++ — raw `AF_PACKET` socket capture, protocol classifier (DPI)
- Protocol signatures — Redis: `*N\r\n`, HTTP: `GET/POST/HTTP`, 
  PostgreSQL: startup message format, gRPC: HTTP/2 MAGIC prefix
- Python FastAPI — central graph aggregation + REST API
- Neo4j or PostgreSQL + adjacency lists — topology storage
- `d3.js` — force-directed graph visualization in browser
- React — dashboard shell, filter controls
- Docker — per-node capture agent + central server
- Kubernetes DaemonSet — deploy agent per node
- Bash — `tcpdump` validation, integration tests, namespace-aware sniffing

**What makes it hard:**
`AF_PACKET` in `TPACKET_V3` ring buffer mode requires careful ring buffer
sizing — too small and packets are dropped at high rates.
Protocol fingerprinting without libpcap means you parse Ethernet → IP →
TCP/UDP → payload manually, including IP fragmentation reassembly and
TCP stream reconstruction for protocols that span multiple packets.
Redis and PostgreSQL can be identified after 1–2 packets; gRPC requires
seeing the HTTP/2 SETTINGS frame which may arrive after the MAGIC prefix.
Kubernetes network namespaces mean the DaemonSet must enter each pod's
network namespace to see its traffic — requires `setns()` syscall with
careful permission management.

**Why it impresses:**
Service mesh observability (what Cilium, Pixie, and Datadog APM do)
is built on exactly this pattern. Demonstrating passive DPI-based
topology discovery without any instrumentation of the target services
is what distinguishes systems engineers who think in kernel primitives
from those who use frameworks.

**References:**  
`github.com/libbpf/libbpf` — alternative to AF_PACKET using XDP  
`man 7 packet` — AF_PACKET documentation  
Wireshark dissector source code — protocol format references

---

## Project 11 — `colossus` — Distributed KV Store with Raft Consensus

```
🔥 Very Hard  |  Timeline: 12–18 weeks
Categories: System Design · C++ · Networking/DPI · Docker/Kubernetes
```

**What you build:**  
A distributed key-value store with strong consistency, implemented from
scratch. The storage engine: log-structured merge tree (LSM) with
memtable (red-black tree in-memory), WAL (write-ahead log with `fdatasync`),
and SSTables on disk with bloom filter. The consensus layer: Raft protocol
implemented in C++ — leader election, log replication, log compaction via
snapshots. The network layer: custom binary protocol over TCP with length-
prefixed framing. A Python client library. Deploy as a 3-node or 5-node
Kubernetes StatefulSet with persistent volumes. Measure consistency
under network partition using `tc netem` to inject packet loss.

**Tech Stack:**
- C++20 — Raft state machine, LSM tree, WAL, SSTable, bloom filter
- `fdatasync()` — durability guarantee, not just `fwrite`
- `mmap` — SSTable random reads via memory-mapped files
- Custom binary protocol over TCP — length prefix + message type byte
- Python — client library with automatic leader routing
- Docker — multi-stage build: compiler → runtime minimal image
- Kubernetes StatefulSet + PersistentVolumeClaim — stable network identity
- `tc netem` — inject latency, packet loss, network partition for chaos testing
- Prometheus — replication lag, election count, write latency p99
- Bash — 3-node startup scripts, fault injection, consistency validation

**What makes it hard:**
Raft is deceptively complex in implementation. The leader election timeout
randomization must be truly random across nodes or split-vote loops occur.
Log replication requires tracking `nextIndex` and `matchIndex` per follower
and handling the AppendEntries RPC failure retry correctly.
Log compaction (snapshot) requires freezing the state machine,
serializing it, and truncating the log — all while handling incoming
requests. Getting this wrong causes data loss.
The LSM tree compaction must run in a background thread without blocking
reads — requires careful lock-free design at the memtable boundary.
`fdatasync()` must be called after every WAL entry — measuring the
performance penalty and showing you can still achieve 50K writes/second
with it enabled is part of the story.

**Why it impresses:**
This is the hardest project on the list. Implementing Raft correctly
is a multi-month effort that most engineers never attempt. etcd (the
Kubernetes control plane backing store) is a Raft-based KV store.
CockroachDB's storage layer is an LSM tree. This project covers the
exact technical depth that distinguishes L5/L6 engineers from L3/L4.

**References:**  
Ongaro & Ousterhout "In Search of an Understandable Consensus Algorithm"  
`github.com/etcd-io/raft` — reference Raft (read, don't copy)  
`github.com/facebook/rocksdb` — production LSM tree reference

---

## Project 12 — `bpfscope` — eBPF-Based System Call Auditor + Container Security

```
🔴 Hard  |  Timeline: 6–9 weeks
Categories: Linux/Bash · Networking/DPI · Docker/Kubernetes · C++
```

**What you build:**  
A Falco-like runtime security tool that uses eBPF tracepoints to intercept
every system call across all processes on a Linux host, applies policy rules
(expressed as a simple DSL you design), and alerts on violations — e.g.
"a container process executed `chmod u+s`", "a process in namespace X called
`ptrace()`", "a process opened a file outside its declared volume mounts".
Kubernetes-aware: reads pod metadata from the kubelet API and enriches
every alert with pod name, namespace, and container ID.
The policy DSL is evaluated at the eBPF level for low-overhead rules
and in userspace for complex rules. Deploy as a DaemonSet.

**Tech Stack:**
- eBPF tracepoints — `sys_enter_*` and `sys_exit_*` hook points
- `libbpf` + C — eBPF program loader, BPF ring buffer for event streaming
- C++ — policy engine, rule DSL parser (recursive descent), alert publisher
- Kubernetes API (`/api/v1/pods`) — pod metadata enrichment
- Python FastAPI — alert webhook receiver + rule management API
- Docker — DaemonSet container with correct capabilities
- Kubernetes DaemonSet — node-level deployment, hostPID: true
- `seccomp` — comparison point (show why eBPF is more flexible)
- Bash — policy testing scripts, alert simulation, `bpftool` diagnostics

**What makes it hard:**
eBPF tracepoints fire on every syscall from every process on the host —
at 100K syscalls/second on a busy node, the ring buffer and userspace
consumer must process without dropping events.
`hostPID: true` in Kubernetes gives the DaemonSet access to all host
PIDs, but cross-referencing PID → pod requires atomically reading
`/proc/PID/cgroup` and the Kubernetes pod list — a PID can exit between
the eBPF event and the lookup.
The policy DSL must be compilable to BPF bytecode for simple rules
(single syscall + argument checks) but falls back to userspace for complex
rules — the boundary between "BPF-expressible" and "userspace-required"
is non-obvious and requires careful DSL design.

**Why it impresses:**
Falco (CNCF graduated project, used by Netflix) does exactly this.
Building your own demonstrates the deepest Linux kernel knowledge:
tracepoints, BPF ring buffers, PID namespace traversal, and Kubernetes
metadata enrichment — all in one coherent project with a real security use case.

**References:**  
`github.com/falcosecurity/falco` — production reference  
`github.com/qmonnet/awesome-ebpf` — eBPF resource list  
Linux kernel docs: `Documentation/bpf/`

---

## Difficulty and Category Matrix

| Project | Hard/VH | C++ | CUDA/GPU | AI/ML | Net/DPI | OS/Sched | Sys Design | Python | Docker/K8s | Linux |
|---|---|---|---|---|---|---|---|---|---|---|
| xdp-firewall | 🔥 | ✓ | — | — | ✓ | — | — | — | ✓ | ✓ |
| gpunet | 🔥 | ✓ | ✓ | — | ✓ | — | — | — | — | ✓ |
| chronos | 🔥 | ✓ | — | — | — | ✓ | — | ✓ | ✓ | ✓ |
| voltex | 🔥 | ✓ | ✓ | ✓ | — | — | — | ✓ | ✓ | — |
| riptide | 🔥 | ✓ | — | — | ✓ | — | — | — | ✓ | ✓ |
| konductor | 🔥 | — | ✓ | ✓ | — | — | — | ✓ | ✓ | — |
| memstorm | 🔥 | ✓ | — | — | — | ✓ | — | — | — | ✓ |
| pyroscale | 🔴 | ✓ | — | — | — | — | — | ✓ | ✓ | ✓ |
| arbitron | 🔴 | ✓ | — | — | — | — | ✓ | ✓ | ✓ | ✓ |
| netwatch | 🔴 | ✓ | — | — | ✓ | — | — | ✓ | ✓ | ✓ |
| colossus | 🔥 | ✓ | — | — | ✓ | — | ✓ | ✓ | ✓ | — |
| bpfscope | 🔴 | ✓ | — | — | ✓ | — | — | ✓ | ✓ | ✓ |

---

## Recommended Build Order for Your 6-Month Plan

```
Month 1–2 (Phase 1 — Foundations):
  Start: memstorm (C++ + OS depth, no external dependencies)

Month 3 (Phase 2 — Systems):
  Start: chronos (OS scheduler + Linux cgroups, ties to OS Concepts reading)
  
Month 4 (Phase 2 — Networking):
  Start: xdp-firewall OR netwatch (pick one based on eBPF interest)

Month 5 (Phase 3 — Specialization):
  Start: riptide (HFT FIX protocol, directly interview-relevant)
  Parallel: voltex GPU inference if targeting AI infra roles

Month 6 (Phase 3 — Flagship):
  Start: colossus (the hardest, for L5+ signal)
  OR: arbitron (if HFT systems is primary target)
```

**Do not attempt colossus or gpunet before Month 4.**  
Both require deep foundations in C++ concurrency, networking, and  
Linux systems that Phase 1 and 2 build. Starting them early means  
you will spend 80% of the time debugging fundamentals, not learning  
the interesting parts of the project itself.