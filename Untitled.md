# Complete 6-Month Systems Engineering Prep Plan
## Target: January 1, 2027 | FAANG · HFT Systems · C++ Developer

**Start date:** June 2026  
**Profile:** BTech graduate · C++ intermediate · 5–6 hours/day  
**Targets:** FAANG Systems/Backend · HFT Systems Engineering · High-performance C++ roles

---

## Table of Contents

1. [Job Prospects — January 1, 2027](#1-job-prospects)
2. [Honest Assessment](#2-honest-assessment)
3. [Complete Knowledge Map](#3-knowledge-map)
   - [3.1 Mathematics (136 hours)](#31-mathematics)
   - [3.2 Computer Science Fundamentals](#32-cs-fundamentals)
   - [3.3 DSA — Complete Reference](#33-dsa-complete-reference)
   - [3.4 Modern C++ Deep Dive](#34-modern-c)
   - [3.5 Systems and Networking](#35-systems-and-networking)
4. [Daily and Weekly Schedule](#4-schedule)
5. [Phase 1 — Month 1–2: Foundations](#5-phase-1)
6. [Phase 2 — Month 3–4: Core Systems](#6-phase-2)
7. [Phase 3 — Month 5–6: Specialization](#7-phase-3)
8. [Projects — Complete Reference](#8-projects)
9. [DSA Milestones](#9-dsa-milestones)
10. [Books and Resources](#10-books-and-resources)
11. [Portfolio and Freelancing](#11-portfolio-and-freelancing)
12. [Study Environment](#12-study-environment)
13. [Mistakes to Avoid](#13-mistakes-to-avoid)

---

## 1. Job Prospects — January 1, 2027

This is what you are actually buying with 6 months of serious execution.

### Realistic Outcome Distribution

```
If you follow this plan with 4.0+ average efficiency:

40%  →  Backend/Systems role at Series A–C funded startup
         ₹15–28 LPA + meaningful equity
         Companies: Zepto, Meesho, Razorpay, Groww, CRED, Khatabook
         Why: These companies value systems depth + C++ + 500 LC

30%  →  Amazon SDE-1 or Microsoft SDE-2
         ₹20–38 LPA + RSU
         Why: More accessible bar than Google/Meta; FAANG resume value
         Timeline: October–December 2026 for applications

15%  →  Indian HFT firm (Junior Systems Engineer)
         ₹20–40 LPA + performance bonus (can double base)
         Companies: Graviton Research, Quadeye, Tower Research India
         Why: Your C++ + LOB project + lock-free work directly qualifies

10%  →  Google SDE-1 or Meta E3/E4
         ₹30–60 LPA + RSU
         Why: Harder bar; needs 500 LC + hard problems under 30 min

 5%  →  Top-tier HFT (Optiver, Jump Trading, IMC)
         ₹35–70 LPA + bonus (often 50–100% of base)
         Why: Very competitive; usually needs 9–12 months of prep
```

### By January 1st — Specific Targets

| Company Type | Role | Package (CTC) | Probability |
|---|---|---|---|
| FAANG (Amazon/Microsoft) | SDE-1 | ₹20–38 LPA | High |
| FAANG (Google/Meta) | SDE-1 | ₹30–60 LPA | Medium |
| Funded Startup (Unicorn) | Backend Engineer | ₹18–30 LPA | Very High |
| HFT India (Graviton/Quadeye) | Junior Systems Dev | ₹22–42 LPA | Medium-High |
| HFT Global (Optiver/Jump) | Systems Dev | ₹38–80 LPA | Low–Medium |
| AI Startup (C++ infra role) | Systems/Infra Eng | ₹20–35 LPA | High |
| Remote US/EU (contract) | Backend Contractor | $50–90/hr | Medium |

### What Determines Which Bucket You Land In

The difference between ₹20 LPA and ₹60 LPA in this plan is not luck.
It is determined by exactly three things:

1. **LeetCode hard problems solved under 35 minutes** — Google/Meta screen on this.
   If you cannot do it, you will not reach the final round.

2. **Project depth** — Can you talk for 40 minutes about design decisions in your
   LOB or distributed KV store? Interviewers can tell within 5 minutes if you built
   it or followed a tutorial.

3. **Consistency** — The difference between someone who prepares for 6 months and
   someone who prepares for 4 months plus 2 months of "busy" is 100+ LeetCode
   problems and 1–2 complete projects. That gap is decisive.

### HFT Bonus Structure (Why It Matters)

HFT base salaries look similar to FAANG but the total comp diverges sharply:
- Graviton/Quadeye: Base ₹25–40 LPA + performance bonus 30–80% of base
- Optiver India: Base ₹40–70 LPA + profit share (can reach 2–3x base in good years)
- Jump Trading: Similar to Optiver

A ₹30 LPA base at an HFT firm with a 60% bonus year is ₹48 LPA total comp.
The same base at a startup without bonus is ₹30 LPA. Over 3 years, the HFT path
can generate 2x the total compensation. That is why the HFT path is worth the
extra specialization effort in Phase 3.

---

## 2. Honest Assessment

### What You Have Going For You

Your intermediate C++ is a real advantage — not a minor one. Most candidates
preparing for these roles start with Python and have to learn C++ from scratch.
You already understand: STL internals, pointer arithmetic, bit manipulation,
memory layout. That baseline compresses your learning curve by 4–6 weeks.

Your BTech background means you have seen OS concepts, networking basics, and
algorithms in some form. Even if they are rusty, recognition is faster than
first-time learning.

### The Real Constraint

You described your math background as weak. The 136-hour math plan in this
document is calibrated for that. You are not being asked to become a mathematician
— you are being asked to understand complexity proofs, use modular arithmetic
fluently, and reason about probability at a level that passes systems and HFT
interviews. That is achievable in 136 hours if you do the exercises, not just read.

### The One Non-Negotiable

Consistency. Every single person who has followed a plan like this and landed the
result they wanted did so by showing up every day for 5+ hours without exceptions
during weekdays. The plan protects 5.5–6 hours per day. If you average 4 hours/day,
the outcome moves down one tier in the probability table above. If you average
3.5 hours/day, you will not reach FAANG standard in 6 months.

---

## 3. Complete Knowledge Map

### 3.1 Mathematics

**Total: 136 hours. Integrated into DSA and systems blocks — not a separate subject.**

---

#### Block 1: Logic + Induction + Proof Techniques — 16 hours

**What to study:**
- Propositional logic: AND, OR, NOT, XOR, implication, biconditional
- De Morgan's laws — apply to C++ guard conditions fluently
- Mathematical induction — standard and strong
- Proof by contradiction and contrapositive
- Loop invariants as a proof technique

**Why:**
Induction is the mathematical structure underneath every recursive algorithm.
When you prove that merge sort is correct, you are doing induction on the size
of the array. When you write a loop invariant, you are doing induction on the
iteration count. Understanding the formal structure makes your algorithm
reasoning more precise and your interview explanations cleaner.

De Morgan's laws are immediately practical:
```cpp
// !(a && b) is equivalent to (!a || !b)
// Misapplying this causes real bugs in guard conditions
// A common interview follow-up: "Can you simplify this condition?"
if (!(user.isActive() && user.hasPermission(action))) {
    // De Morgan: equivalent to:
}
if (!user.isActive() || !user.hasPermission(action)) {
    return AccessDenied;
}
```

**Resources:**
- MIT Mathematics for Computer Science (6.042J) — Chapters 1–4, free PDF
- CLRS Appendix A (summations and mathematical background)
- Exercises: Write 5 induction proofs on paper. Prove binary search correct.
  Prove that a binary tree with n internal nodes has n+1 leaves.

**Milestone:** By end of Week 2, you can write a complete inductive proof from
scratch without reference, and identify logical equivalences in C++ code.

---

#### Block 2: Formal Complexity Analysis — 14 hours

**What to study:**
- Big O, Big Theta, Big Omega — formal definitions with constants
- Little o and little omega — understanding strict vs. loose bounds
- Master Theorem — all three cases, including the log^k variant
- Recursion tree method
- Substitution method (guess and verify by induction)
- Amortized analysis — aggregate, accounting, and potential methods

**Why:**
Every FAANG interview ends with "What is the time and space complexity?"
That is not a throwaway question — interviewers probe it. "O(n log n)" is not
enough. They want: "It is Theta(n log n) because the recurrence is
T(n) = 2T(n/2) + n, which by Master Theorem Case 2 with a=2, b=2, p=log₂2=1,
and f(n) = Theta(n^1), gives Theta(n log n)."

**Core recurrences to know cold:**
```
T(n) = T(n/2) + 1           → Θ(log n)      [binary search]
T(n) = 2T(n/2) + n          → Θ(n log n)    [merge sort]
T(n) = 2T(n/2) + n²         → Θ(n²)         [Master Case 3]
T(n) = 4T(n/2) + n          → Θ(n²)         [Master Case 1]
T(n) = 7T(n/2) + n²         → Θ(n^2.81)     [Strassen]
T(n) = T(n-1) + n           → Θ(n²)         [insertion sort]
T(n) = 2T(n-1)              → Θ(2ⁿ)         [naive fibonacci]
T(n) = T(n-1) + T(n-2)      → Θ(φⁿ)         [fibonacci tree]
```

**Amortized — why it matters:**
```
std::vector push_back: amortized O(1) because doubling happens rarely.
Proof (accounting method): charge 3 credits per push_back.
  1 credit: the push_back itself.
  2 credits: saved toward the next doubling.
At doubling, every element has 2 saved credits — enough to pay for copying itself.
This is precisely the argument you give in a FAANG interview.
```

**Resources:** CLRS Chapter 2–5, 17. Do exercises 3-1, 3-2, 4-1 through 4-5.

---

#### Block 3: Modular Arithmetic + Number Theory — 15 hours

**What to study:**
- GCD and Euclidean algorithm
- Extended Euclidean algorithm (extgcd)
- Modular inverse via extgcd and via Fermat's little theorem
- Fast modular exponentiation (binary exponentiation)
- Chinese Remainder Theorem
- Sieve of Eratosthenes and linear sieve
- Euler's totient function
- Lucas' theorem for nCr mod prime

**Why:**
Competitive programming problems above CF 1600 regularly require modular
inverse, fast exponentiation, and primality. Modular arithmetic also underpins
RSA (which appears in FAANG security/systems discussions) and hash function
design (ring buffer indices, consistent hashing).

**Canonical implementations:**
```cpp
// Extended GCD: returns gcd, sets x,y such that ax + by = gcd(a,b)
long long extgcd(long long a, long long b, long long &x, long long &y) {
    if (b == 0) { x = 1; y = 0; return a; }
    long long x1, y1;
    long long g = extgcd(b, a % b, x1, y1);
    x = y1;
    y = x1 - (a / b) * y1;
    return g;
}

// Modular inverse: a^(-1) mod m. Returns -1 if no inverse exists.
long long modinv(long long a, long long m) {
    long long x, y;
    if (extgcd(a, m, x, y) != 1) return -1;
    return (x % m + m) % m;
}

// Fast modular exponentiation: (base^exp) % mod in O(log exp)
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

// Fermat's little theorem: a^(p-1) ≡ 1 (mod p) for prime p
// → modular inverse when p is prime: a^(p-2) mod p
long long fermat_inv(long long a, long long p) {
    return modpow(a, p - 2, p);
}

// Precompute factorials and inverse factorials for nCr mod prime
const int MAXN = 1e6 + 5;
const long long MOD = 1e9 + 7;
long long fact[MAXN], inv_fact[MAXN];

void precompute_factorials() {
    fact[0] = 1;
    for (int i = 1; i < MAXN; i++) fact[i] = fact[i-1] * i % MOD;
    inv_fact[MAXN-1] = fermat_inv(fact[MAXN-1], MOD);
    for (int i = MAXN-2; i >= 0; i--)
        inv_fact[i] = inv_fact[i+1] * (i+1) % MOD;
}

long long nCr(int n, int r) {
    if (r < 0 || r > n) return 0;
    return fact[n] * inv_fact[r] % MOD * inv_fact[n-r] % MOD;
}

// Linear sieve: generates all primes up to n in O(n)
vector<int> linear_sieve(int n) {
    vector<int> primes;
    vector<int> lp(n+1, 0); // lp[i] = smallest prime factor of i
    for (int i = 2; i <= n; i++) {
        if (lp[i] == 0) { lp[i] = i; primes.push_back(i); }
        for (int p : primes) {
            if (p > lp[i] || (long long)i * p > n) break;
            lp[i * p] = p;
        }
    }
    return primes;
}
```

**Resources:** CLRS Chapter 31. CP-algorithms.com — number theory section.

---

#### Block 4: Combinatorics — 12 hours

**What to study:**
- Multiplication and addition principles
- Permutations P(n,k) and combinations C(n,k)
- Pascal's identity and Pascal's triangle
- Binomial theorem
- Inclusion-exclusion principle
- Pigeonhole principle and birthday paradox
- Catalan numbers (appears in DP problems)
- Stars and bars (distributing items into bins)
- Derangements

**Why:**
Counting problems appear in CF 1400–1800 range constantly. Probability
calculations require combinatorics. System design uses pigeonhole (hash
collisions are guaranteed by pigeonhole — any hash function mapping n > m
inputs to m buckets must have collisions).

**Key formulas:**
```
P(n,k) = n! / (n-k)!                    [ordered selection]
C(n,k) = n! / (k! × (n-k)!)             [unordered selection]
Inclusion-exclusion 2 sets: |A∪B| = |A| + |B| - |A∩B|
Catalan: C_n = C(2n,n) / (n+1)          [valid parenthesizations, BST structures]
Stars and bars: C(n+k-1, k-1)           [put n items in k bins, repetition allowed]
Derangements: D_n = n! × Σ(-1)^k/k!    [no fixed points]
Birthday paradox: P(collision) > 0.5 when n > 1.2√m for m buckets
```

**Resources:** MIT MCS Chapters 14–15. Blitzstein Chapter 1.

---

#### Block 5: Probability — 25 hours

**What to study:**
- Sample spaces, events, probability axioms (Kolmogorov)
- Conditional probability: P(A|B) = P(A∩B) / P(B)
- Independence and pairwise independence
- Law of total probability
- Bayes' theorem — deeply
- Discrete random variables: Bernoulli, Binomial, Geometric, Poisson
- Continuous random variables: Uniform, Normal, Exponential
- Expectation (including linearity — critical)
- Variance and standard deviation
- Markov chains: transition matrix, stationary distribution, convergence
- Markov's inequality, Chebyshev's inequality, Chernoff bounds

**Why:**
HFT systems interviews use probability heavily — expected values of queue
waiting times, probability of order fills, birthday paradox for hash table
sizing. FAANG system design uses probability for capacity planning, cache hit
rates, load balancing analysis. Linearity of expectation is the single most
powerful tool in algorithm analysis (it proves QuickSort's expected O(n log n)
in one elegant argument).

**Linearity of expectation — the key insight:**
```
E[X + Y] = E[X] + E[Y] always, even when X and Y are DEPENDENT.

QuickSort analysis:
For each pair (i,j), let X_ij = 1 if elements i and j are compared.
E[comparisons] = Σ E[X_ij] = Σ P(i and j are compared)
               = Σ_{i<j} 2/(j-i+1)
               ≈ 2n ln n = O(n log n)
No need to reason about dependencies. Linearity handles everything.
```

**Bayes — must know cold:**
```
P(A|B) = P(B|A) × P(A) / P(B)

Classic: Disease with 1% prevalence. Test is 99% accurate.
You test positive. Probability you have the disease?

P(disease|positive) = P(positive|disease) × P(disease)
                     / P(positive)
= (0.99 × 0.01) / (0.99×0.01 + 0.01×0.99)
= 0.0099 / 0.0198 = 0.50

Counter-intuitive: Even a 99% accurate test only gives 50% confidence
when the disease is rare. This exact reasoning applies to spam filters,
intrusion detection, and trading signal confidence.
```

**Markov chains (conceptual level, 4 hours):**
```
A Markov chain is a sequence where future state depends only on current state.
Transition matrix P where P[i][j] = P(go to state j | currently in state i).

Stationary distribution π: πP = π (left eigenvector of P with eigenvalue 1)
Find by solving π(P - I) = 0 with Σπ_i = 1.

Applications:
- PageRank is a Markov chain stationary distribution
- Order arrival in LOB modeled as Markov chain (arriving buy/sell rates)
- Queue length at a service modeled as M/M/1 queue (Markov chain)
```

**Resources:** Blitzstein & Hwang Chapters 1–6 (read actively, do exercises).
StatQuest YouTube for visual intuition before Blitzstein.

---

#### Block 6: Statistics for Systems — 12 hours

**What to study:**
- Mean, median, mode — when each is the right metric
- Percentiles: p50, p90, p95, p99, p99.9
- Variance, standard deviation, IQR
- Exponential Moving Average (EWMA)
- Normal distribution: 68-95-99.7 rule
- Log-normal distribution (latency is log-normal, not normal)
- A/B testing framework basics
- Control charts and 3-sigma alerting

**Why:**
Production systems are measured statistically. An SRE saying "p99 latency is
500ms" is describing the 99th percentile of a distribution. A FAANG system
design interview will ask "How do you monitor this system?" — the answer
involves statistical metrics, alert thresholds, and anomaly detection.

**For HFT:** Latency is measured in microseconds and nanoseconds. Jitter
(standard deviation of latency) is often worse than mean latency for trading
systems — a system with mean 5μs and jitter 10μs is worse than one with
mean 8μs and jitter 2μs for consistent execution.

**Key implementation — p99 without storing all data:**
```cpp
// HDR Histogram approximation for p99 in production
// For exact: sort and index. For production: use histogram buckets.
class LatencyHistogram {
    vector<long long> buckets;  // buckets[i] = count of samples in bucket i
    vector<double> bounds;      // upper bound of each bucket
public:
    void record(double latency_us) { /* find bucket, increment */ }
    double percentile(double p) {
        long long total = /* sum of all buckets */;
        long long target = (long long)(p / 100.0 * total);
        long long cumsum = 0;
        for (int i = 0; i < buckets.size(); i++) {
            cumsum += buckets[i];
            if (cumsum >= target) return bounds[i];
        }
        return bounds.back();
    }
};

// EWMA: exponential weighted moving average
double ewma_update(double prev, double new_val, double alpha = 0.1) {
    return alpha * new_val + (1.0 - alpha) * prev;
}
// alpha = 0.1: 10% weight to new observation. Smooths fast fluctuations.
// alpha = 0.9: 90% weight to new. Tracks changes quickly.
```

**Resources:** StatQuest YouTube playlist (Statistics Fundamentals, 90 min).

---

#### Block 7: Floating Point + Numerical Computing — 12 hours

**What to study:**
- IEEE 754 double-precision structure (1 sign + 11 exponent + 52 mantissa)
- Machine epsilon: 2^-52 ≈ 2.22 × 10^-16
- Special values: ±∞, NaN, -0, subnormals
- Catastrophic cancellation
- Kahan summation algorithm
- Fixed-point arithmetic for financial calculations
- NaN propagation and detection
- Compiler flags that break IEEE 754 (-ffast-math)

**Why:**
This is directly critical for HFT. Price representation bugs cause real
financial loss. A trading system that uses doubles for prices will eventually
have a rounding error that causes incorrect order sizing or P&L calculation.
Every professional trading system uses fixed-point arithmetic for prices.

**Critical code patterns:**
```cpp
// Why 0.1 + 0.2 != 0.3 in floating point:
// 0.1 in binary = 0.0001100110011... (infinite repeating)
// The stored approximation causes accumulation error
double a = 0.1 + 0.2;
// a = 0.30000000000000004441 (not 0.3)

// CORRECT comparison: use epsilon
bool approx_equal(double a, double b, double eps = 1e-9) {
    return std::abs(a - b) <= eps * std::max(1.0, std::max(std::abs(a), std::abs(b)));
}

// WRONG: if (a == 0.3) — this is almost always false for computed floats

// Catastrophic cancellation — example:
// Computing √(x+1) - √x for large x:
double bad(double x)  { return sqrt(x+1) - sqrt(x); }
// For x=1e15: both terms round to same value, result = 0 (wrong!)

// Stable version using identity (√(x+1)-√x)(√(x+1)+√x) = 1:
double good(double x) { return 1.0 / (sqrt(x+1) + sqrt(x)); }

// Fixed-point arithmetic for HFT prices:
// Never use double for money. Use integer with implicit scale.
// Price $100.25 with 4 decimal places = 1002500 (int64_t)
struct Price {
    int64_t ticks;           // internal representation
    static const int SCALE = 10000;
    static Price from_double(double d) { return {(int64_t)(d * SCALE + 0.5)}; }
    double to_double() const { return (double)ticks / SCALE; }
    Price operator+(Price o) const { return {ticks + o.ticks}; }
    Price operator*(int64_t qty) const { return {ticks * qty}; }
};
// No floating point in the hot path. Zero rounding errors.

// Kahan summation: compensated summation for accurate floating-point sums
double kahan_sum(const vector<double>& v) {
    double sum = 0.0, c = 0.0;
    for (double x : v) {
        double y = x - c;
        double t = sum + y;
        c = (t - sum) - y;
        sum = t;
    }
    return sum;
}

// NaN detection: NaN != NaN is always true
if (std::isnan(price) || std::isinf(price)) {
    log_error("Invalid price");
    return;
}

// DO NOT use -ffast-math in trading systems: it allows compiler to
// reorder floating-point operations and ignore NaN/Inf handling.
// Compile trading code with: -O2 -march=native (no -ffast-math)
```

**Resources:** Section 8 of the math curriculum you shared — read it in full.

---

#### Block 8: HFT Mathematics — 26 hours

**What to study:**
- Limit order book (LOB) structure: bids, asks, spread, depth
- Order types: market, limit, IOC, FOK, post-only
- Bid-ask spread components: inventory, processing, adverse selection
- TWAP: time-weighted average price execution
- VWAP: volume-weighted average price
- Market impact: square-root law, permanent vs. temporary impact
- Queue position and fill probability
- Latency measurement: TSC (timestamp counter), wire-to-wire latency
- Little's Law: L = λW (average items in system = arrival rate × average time)

**Why:**
HFT systems interviews test whether you understand what the system you are
building is doing. A C++ engineer who cannot explain what bid-ask spread
represents or why queue position matters will not pass the domain knowledge
round at Graviton, Quadeye, or Optiver.

**Little's Law — critical for systems:**
```
L = λW

L = average number of requests in the system
λ = average arrival rate (requests per second)
W = average time each request spends in the system

Example: API server receives 1000 req/s, each takes 10ms to process.
L = 1000 × 0.01 = 10 requests in flight simultaneously.

If latency doubles to 20ms: L = 1000 × 0.02 = 20 requests in flight.
If your thread pool has 15 workers, queuing begins. Latency spikes. Cascade.

This is why SLAs are set on latency, not throughput alone.
```

**TSC-based latency measurement:**
```cpp
// rdtsc: CPU cycle counter. Nanosecond resolution.
static inline uint64_t rdtsc() {
    uint32_t lo, hi;
    __asm__ volatile ("rdtsc" : "=a"(lo), "=d"(hi));
    return ((uint64_t)hi << 32) | lo;
}

// Measure order processing latency:
uint64_t t0 = rdtsc();
process_order(order);
uint64_t t1 = rdtsc();
uint64_t cycles = t1 - t0;
double ns = cycles / tsc_frequency_ghz; // calibrated at startup
```

**Resources:** The math curriculum Section 11.1–11.3. "Algorithmic and
High-Frequency Trading" (Cartea et al.) — conceptual reading of Ch 3–5.

---

#### Block 9: Matrix Exponentiation — 5 hours (absorbed into Combinatorics)

**What to study:**
- Matrix multiplication: O(k³) for k×k matrices
- Matrix exponentiation: O(k³ log n) for matrix^n
- Linear recurrences via matrix form
- Counting paths in a graph in exactly k steps

**Why:**
CF 1700+ problems include "compute F(n) mod p for n up to 10^18" — which
requires matrix exponentiation. Also covers path counting and transition
systems that appear in both competitive programming and graph algorithm
discussions.

```cpp
typedef vector<vector<long long>> Matrix;
const long long MOD = 1e9 + 7;

Matrix multiply(const Matrix& A, const Matrix& B) {
    int n = A.size();
    Matrix C(n, vector<long long>(n, 0));
    for (int i = 0; i < n; i++)
        for (int k = 0; k < n; k++) if (A[i][k])
            for (int j = 0; j < n; j++)
                C[i][j] = (C[i][j] + A[i][k] * B[k][j]) % MOD;
    return C;
}

Matrix matpow(Matrix A, long long n) {
    int m = A.size();
    Matrix R(m, vector<long long>(m, 0));
    for (int i = 0; i < m; i++) R[i][i] = 1; // Identity
    while (n > 0) {
        if (n & 1) R = multiply(R, A);
        A = multiply(A, A);
        n >>= 1;
    }
    return R;
}

// Fibonacci in O(log n):
// [F(n+1)]   [1 1]^n   [1]
// [F(n)  ] = [1 0]   × [0]
long long fib(long long n) {
    if (n <= 1) return n;
    Matrix M = {{1,1},{1,0}};
    Matrix R = matpow(M, n);
    return R[0][1];
}
```

---

### 3.2 CS Fundamentals

These topics come from your books and are studied during the Systems blocks.

#### Operating Systems (Read + Code)

| Topic | Depth | How to Study |
|---|---|---|
| Process management: fork/exec/wait | Deep | Write shell in C |
| Threads: pthreads, thread safety | Deep | Write producer-consumer |
| Synchronization: mutex, semaphore, CV | Deep | Implement with actual bugs, then fix |
| CPU scheduling: CFS, real-time, priorities | Medium | Read Silberschatz, use `chrt` on Linux |
| Memory management: virtual memory, paging | Deep | Read Ch 8–10, use `mmap`, read `/proc/self/maps` |
| Page replacement: LRU, clock algorithm | Medium | Implement both in simulation |
| File systems: inode, directory structure | Medium | Read, use `strace` on file operations |
| IPC: pipes, shared memory, message queues | Deep | Write programs using each |
| Signals: signal handlers, signal safety | Deep | Implement in shell project |
| Kernel bypass: why it exists | Conceptual | Read Cloudflare blog on io_uring |

#### Computer Networking (Read + Code)

| Topic | Depth | How to Study |
|---|---|---|
| OSI model and where TCP/IP fits | Medium | Map to Kurose chapters |
| Socket API: socket/bind/listen/accept/connect | Deep | Write TCP + UDP programs |
| TCP: 3-way handshake, 4-way close, TIME_WAIT | Deep | Use Wireshark to see it |
| TCP: congestion control, Nagle, window scaling | Deep | Kurose Ch 3 |
| epoll: edge-triggered, level-triggered | Deep | Implement echo server |
| DNS: recursive vs. iterative, TTL, caching | Medium | `dig`, trace resolution |
| HTTP/1.1: request format, headers, keep-alive | Deep | Implement in project |
| HTTP/2: multiplexing, header compression | Medium | Conceptual |
| TLS: handshake, certificate validation | Medium | Conceptual only |
| io_uring: modern async I/O | Medium | Read liburing docs, small demo |

#### DBMS (Targeted)

| Topic | Depth | How to Study |
|---|---|---|
| B+ tree: structure, search, insert | Deep | Draw on paper for every insert |
| Index types: hash, B+tree, covering, composite | Deep | PostgreSQL EXPLAIN ANALYZE |
| Isolation levels: RC, RR, Serializable, SI | Deep | DDIA Chapter 7 |
| MVCC: multi-version concurrency control | Deep | DDIA + PostgreSQL internals blog |
| WAL: write-ahead logging | Deep | Implement in KV store project |
| Transactions: ACID meaning at implementation level | Deep | DDIA Chapter 7 |
| Query planning: seq scan vs index scan | Medium | EXPLAIN ANALYZE |
| Joins: nested loop, hash join, sort-merge | Medium | DDIA + PostgreSQL docs |

#### Distributed Systems (DDIA-driven)

| Chapter | Topic | Key Concepts |
|---|---|---|
| Ch 3 | Storage engines | B-trees vs LSM-trees, SSTables, compaction |
| Ch 5 | Replication | Leader/follower, split-brain, replication lag |
| Ch 6 | Partitioning | Consistent hashing, hot spots, secondary indexes |
| Ch 7 | Transactions | Isolation levels, MVCC, 2PL, phantom reads |
| Ch 8 | Distributed problems | Clocks, network failures, partial failures |
| Ch 9 | Consensus | Linearizability, Raft/Paxos conceptual, ZooKeeper |
| Ch 11 | Stream processing | Event sourcing, CDC, Kafka at a design level |

---

### 3.3 DSA Complete Reference

#### Category Map — 500 Problems Target

| Category | Count | Phase | Key Patterns |
|---|---|---|---|
| Arrays + Sliding Window | 30 | Phase 1 | Fixed window, variable window, prefix sum |
| Binary Search | 20 | Phase 1 | On value, on answer, rotated array, 2D |
| Hashmaps + Sets | 15 | Phase 1 | Frequency count, two-sum, anagram |
| Two Pointers | 15 | Phase 1 | Sorted array, collision, fast/slow |
| Linked Lists | 15 | Phase 1 | Reversal, fast/slow, merge, cycle |
| Stacks + Monotonic Stack | 15 | Phase 1 | Next greater, histogram, trapping rain |
| Trees — DFS/BFS | 20 | Phase 1–2 | Pre/in/post-order, level-order, diameter |
| Trees — BST | 10 | Phase 2 | Validation, LCA, kth smallest |
| Heaps | 15 | Phase 2 | Top-k, median, merge k sorted |
| Tries | 10 | Phase 2 | Prefix search, word search, XOR tricks |
| Graphs — BFS/DFS | 20 | Phase 2 | Islands, components, bipartite, coloring |
| Graphs — Dijkstra/SSSP | 15 | Phase 2 | Weighted, negative edges (Bellman-Ford) |
| Graphs — Advanced | 15 | Phase 2 | Topological sort, SCC, Union-Find, MST |
| Dynamic Programming | 55 | Phase 2–3 | See DP patterns below |
| Backtracking | 15 | Phase 2–3 | Subsets, permutations, N-queens, Sudoku |
| Bit Manipulation | 15 | Phase 1–3 | XOR tricks, bit counting, masks |
| Segment Tree / BIT | 12 | Phase 3 | Range queries, point updates, order stats |
| String Algorithms | 12 | Phase 3 | KMP, Z-function, rolling hash, suffix array |
| Math / Combinatorics | 15 | Phase 2–3 | nCr, prime factorization, GCD |
| Simulation / Design | 10 | Phase 3 | LRU cache, LFU, Circular buffer |
| **Total** | **350 minimum, 500 target** | | |

#### DP Patterns — Complete

```
1D DP (learn these templates first):
  - Linear scan: max subarray (Kadane), house robber, climbing stairs
  - Sequence with skip: rod cutting, coin change I, word break

Knapsack family:
  - 0/1 knapsack: each item used at most once
  - Unbounded knapsack: items reusable (coin change II)
  - Bounded knapsack: items have count limits
  Template:
    dp[i][w] = max(dp[i-1][w], dp[i-1][w-wt[i]] + val[i])  [0/1]
    dp[i][w] = max(dp[i][w], dp[i][w-wt[i]] + val[i])       [unbounded]

2D DP / Grid:
  - Unique paths, min path sum, maximal square
  - LCS (longest common subsequence), edit distance
  Template (LCS):
    dp[i][j] = dp[i-1][j-1]+1 if s1[i]==s2[j]
             = max(dp[i-1][j], dp[i][j-1]) otherwise

Interval DP:
  - Matrix chain multiplication (O(n³))
  - Burst balloons, palindrome partitioning, stone merge
  Template: for len 2..n, for i, j=i+len-1, for k in [i,j-1]
    dp[i][j] = min/max over all k of dp[i][k] + dp[k+1][j] + cost(i,j,k)

DP on Trees:
  - Maximum path sum, diameter, tree knapsack
  - Re-rooting technique for "dp for every node as root"
  Template: dfs(node), compute dp[node] from dp[children]

Digit DP:
  - Count numbers in [1,n] satisfying property
  - State: (position, tight_constraint, remainder/digit_sum)
  Template: memoize on (pos, tight, state)

Bitmask DP:
  - Traveling salesman on small graphs (n≤20)
  - dp[mask][v] = min cost to visit exactly nodes in mask, ending at v
  Template: dp[mask|(1<<next)][next] = min(dp[mask][cur] + cost[cur][next])

String DP:
  - Palindromic substrings, longest palindromic subsequence
  - Regex matching, wildcard matching
```

#### Graph Algorithms — Implementation Reference

```cpp
// Dijkstra: O((V+E) log V) with priority queue
vector<long long> dijkstra(int src, int n, vector<vector<pair<int,int>>>& adj) {
    const long long INF = 1e18;
    vector<long long> dist(n, INF);
    priority_queue<pair<long long,int>, vector<pair<long long,int>>, greater<>> pq;
    dist[src] = 0; pq.push({0, src});
    while (!pq.empty()) {
        auto [d, u] = pq.top(); pq.pop();
        if (d > dist[u]) continue;
        for (auto [v, w] : adj[u])
            if (dist[u] + w < dist[v]) { dist[v] = dist[u] + w; pq.push({dist[v], v}); }
    }
    return dist;
}

// Topological sort (Kahn's): O(V+E)
vector<int> topo_sort(int n, vector<vector<int>>& adj) {
    vector<int> indeg(n, 0);
    for (int u = 0; u < n; u++) for (int v : adj[u]) indeg[v]++;
    queue<int> q;
    for (int i = 0; i < n; i++) if (indeg[i] == 0) q.push(i);
    vector<int> order;
    while (!q.empty()) {
        int u = q.front(); q.pop(); order.push_back(u);
        for (int v : adj[u]) if (--indeg[v] == 0) q.push(v);
    }
    return order; // |order| != n → cycle exists
}

// Union-Find with path compression + union by rank: O(α(n)) per op
struct DSU {
    vector<int> parent, rank;
    DSU(int n) : parent(n), rank(n, 0) { iota(parent.begin(), parent.end(), 0); }
    int find(int x) { return parent[x] == x ? x : parent[x] = find(parent[x]); }
    bool unite(int x, int y) {
        x = find(x); y = find(y); if (x == y) return false;
        if (rank[x] < rank[y]) swap(x, y);
        parent[y] = x; if (rank[x] == rank[y]) rank[x]++;
        return true;
    }
};

// Segment Tree: O(log n) range query and point update
struct SegTree {
    int n; vector<long long> tree;
    SegTree(int n) : n(n), tree(4*n, 0) {}
    void update(int node, int l, int r, int idx, long long val) {
        if (l == r) { tree[node] = val; return; }
        int mid = (l+r)/2;
        if (idx <= mid) update(2*node, l, mid, idx, val);
        else update(2*node+1, mid+1, r, idx, val);
        tree[node] = tree[2*node] + tree[2*node+1]; // or min/max
    }
    long long query(int node, int l, int r, int ql, int qr) {
        if (qr < l || r < ql) return 0;
        if (ql <= l && r <= qr) return tree[node];
        int mid = (l+r)/2;
        return query(2*node, l, mid, ql, qr) + query(2*node+1, mid+1, r, ql, qr);
    }
};
```

---

### 3.4 Modern C++ Deep Dive

**Month 1–2 reading: *A Tour of C++* by Stroustrup. Code every example.**

#### Core Language Features to Own

```cpp
//── Move semantics ──────────────────────────────────────────────────────────
// A moved-from object is in a valid but unspecified state.
// Rule of zero: if you don't manage resources, don't declare any of the 5.
// Rule of five: if you declare any of {destructor, copy ctor, copy assign,
//   move ctor, move assign}, declare all five.

class Buffer {
    char* data;
    size_t size;
public:
    Buffer(size_t n) : data(new char[n]), size(n) {}
    ~Buffer() { delete[] data; }
    // Copy: expensive
    Buffer(const Buffer& o) : data(new char[o.size]), size(o.size) {
        std::copy(o.data, o.data + o.size, data);
    }
    // Move: cheap — just steal the pointer
    Buffer(Buffer&& o) noexcept : data(o.data), size(o.size) {
        o.data = nullptr; o.size = 0; // leave moved-from in valid state
    }
    Buffer& operator=(Buffer&& o) noexcept {
        if (this != &o) { delete[] data; data = o.data; size = o.size;
                          o.data = nullptr; o.size = 0; }
        return *this;
    }
};

//── RAII ────────────────────────────────────────────────────────────────────
// Resource Acquisition Is Initialization: tie resource lifetime to object lifetime
class FileHandle {
    FILE* f;
public:
    FileHandle(const char* path, const char* mode) : f(fopen(path, mode)) {
        if (!f) throw std::runtime_error("Cannot open file");
    }
    ~FileHandle() { if (f) fclose(f); }           // cleanup guaranteed
    FILE* get() { return f; }
    FileHandle(const FileHandle&) = delete;        // non-copyable
    FileHandle& operator=(const FileHandle&) = delete;
};

//── Smart pointers ──────────────────────────────────────────────────────────
// unique_ptr: single ownership, zero overhead
auto buf = std::make_unique<Buffer>(1024);  // prefer over new

// shared_ptr: shared ownership, reference counted (~overhead)
auto shared = std::make_shared<Buffer>(1024);

// weak_ptr: non-owning handle, avoids cycles
std::weak_ptr<Buffer> weak = shared;
if (auto locked = weak.lock()) { /* still alive */ }

//── std::atomic and memory ordering ─────────────────────────────────────────
std::atomic<int> counter{0};
counter.fetch_add(1, std::memory_order_relaxed);  // no ordering, just atomicity

std::atomic<bool> ready{false};
// Producer:
data_prepared = compute();
ready.store(true, std::memory_order_release);  // all previous writes visible after this

// Consumer:
while (!ready.load(std::memory_order_acquire)); // sees all writes before release
use(data_prepared);

//── Lambdas ──────────────────────────────────────────────────────────────────
int x = 42;
auto by_value = [x]() { return x * 2; };         // captures x by value
auto by_ref   = [&x]() { x++; };                  // captures x by reference
auto generic  = [](auto a, auto b) { return a + b; }; // C++14 generic lambda

//── constexpr ────────────────────────────────────────────────────────────────
constexpr int factorial(int n) { return n <= 1 ? 1 : n * factorial(n-1); }
constexpr int f6 = factorial(6); // computed at compile time, zero runtime cost

//── std::optional ────────────────────────────────────────────────────────────
std::optional<int> find(const vector<int>& v, int target) {
    for (int i = 0; i < v.size(); i++) if (v[i] == target) return i;
    return std::nullopt;
}
if (auto idx = find(data, 42)) { use(*idx); }  // no exceptions, no -1 sentinel

//── structured bindings ──────────────────────────────────────────────────────
map<string, int> m = {{"a", 1}, {"b", 2}};
for (auto& [key, val] : m) { /* clean iteration */ }
auto [it, inserted] = m.insert({"c", 3});
```

**CppCon Back to Basics talks — mandatory viewing:**
- Move Semantics (Klaus Iglberger) — 60 min
- RAII and the Rule of Zero (Arthur O'Dwyer) — 60 min
- Memory Model (Mike Shah) — 60 min — critical for HFT
- Concurrency (Mike Shah) — 60 min
- Templates Part 1 (Nicolai Josuttis) — 60 min

---

### 3.5 Systems and Networking

**Canonical Linux commands to master by Month 2:**

```bash
# Process investigation
strace -e trace=open,read,write,mmap ./myprogram  # trace syscalls
ltrace ./myprogram                                 # trace library calls
lsof -p <pid>                                      # open file descriptors
/proc/<pid>/maps                                   # virtual memory layout
/proc/<pid>/status                                 # memory usage, threads

# Performance profiling
perf stat ./myprogram                 # CPU cycles, cache misses, branches
perf record -g ./myprogram && perf report  # call graph profiler
valgrind --tool=cachegrind ./myprogram     # cache simulation

# Network analysis
ss -tuanp                             # socket statistics (better than netstat)
tcpdump -i any port 8080              # capture packets
wireshark                             # GUI packet analysis

# System monitoring
htop / btop                           # process monitoring
sar -u 1 10                           # CPU utilization per second
iostat -x 1                           # disk I/O statistics
vmstat 1                              # virtual memory, CPU, I/O overview
numactl --hardware                    # NUMA topology
taskset -c 0-3 ./myprogram            # pin to CPU cores 0-3

# Compiler and binary analysis
objdump -d ./myprogram                # disassemble
nm ./myprogram                        # symbol table
readelf -a ./myprogram                # ELF headers and sections
g++ -O2 -S -o prog.s prog.cpp         # generate assembly output
```

---

## 4. Schedule

### Daily Time Blocks

```
Morning
  08:00–10:00  DSA + Math Integration         (2 hours — first, always)
  10:00–13:00  Systems Primary (phase varies)  (2.5–3 hours)

Afternoon
  14:00–15:00  Reading + Concept Review        (1 hour)

Evening
  21:00–22:00  Codeforces / Mock / Upsolve     (1 hour)

Weekend
  Saturday:    DSA 2h + Full CF live round 3h + Upsolve 2h
  Sunday:      DSA 2h + Project work 2h + Weekly review 1h
```

### Phase-by-Phase Daily Emphasis

| Phase | Block 1 (DSA) | Block 2 (Systems) | Block 3 (Reading) |
|---|---|---|---|
| Month 1 | Arrays/Binary Search/Hash | C++ Tour + OS syscalls | CLRS Ch 2–5 + MIT MCS |
| Month 2 | Trees/Heaps/DP intro | OS Ch 8–10 + Inside Machine + Networking intro | Blitzstein Ch 1–3 |
| Month 3 | Graphs/Topological/SSSP | DDIA (1 chapter/day) + Networking sockets | Blitzstein Ch 4–6 + Kurose |
| Month 4 | DP advanced + Backtracking | DBMS + Systems Design practice | DDIA review + Kerrisk |
| Month 5 | Hard problems + Segment tree | Lock-free C++ + LOB math | Williams Ch 5–7 |
| Month 6 | Mock interview problems | Mock interviews + Project polish | Interview engineering blogs |

---

## 5. Phase 1 — Month 1–2: Foundations

### Month 1: The Baseline

**Week 1–2: C++ + OS + Complexity Analysis**

Goals:
- Neovim configured and muscle memory starting (4 hours max on setup, not more)
- Linux as daily OS from Day 1, no exceptions
- A Tour of C++ begun, coding every example
- OS Concepts Chapter 1–3 read + C programs written alongside
- Big O and Master Theorem understood and applied to problems

**Math integration (Week 1–2):**
- Day 1–3: Propositional logic (De Morgan's laws, implications). 1 hour.
- Day 4–7: Big O formal definitions. Read CLRS Ch 3. Do all exercises. 8 hours.
- Day 8–10: Master Theorem. CLRS Ch 4. Solve 10 recurrences. 5 hours.
- Day 11–14: Induction intro. MIT MCS Ch 3. Write 3 proofs on paper. 5 hours.

**DSA (Week 1–4):**
- Week 1: Arrays, prefix sum, sliding window (fixed and variable)
- Week 2: Binary search — all 4 templates (find value, leftmost, rightmost, on answer)
- Week 3: Hashmaps, two pointers, string problems
- Week 4: Recursion, basic sorting, merge sort + quick sort implementation

```cpp
// Binary search templates — know all four cold:
// Template 1: exact match
int bs_exact(vector<int>& v, int target) {
    int l = 0, r = v.size() - 1;
    while (l <= r) {
        int mid = l + (r - l) / 2;
        if (v[mid] == target) return mid;
        else if (v[mid] < target) l = mid + 1;
        else r = mid - 1;
    }
    return -1;
}
// Template 2: leftmost occurrence (lower_bound)
int bs_left(vector<int>& v, int target) {
    int l = 0, r = v.size();
    while (l < r) { int mid = (l+r)/2; if (v[mid] < target) l = mid+1; else r = mid; }
    return l; // l == r, first position >= target
}
// Template 3: on answer (find minimum x where condition(x) is true)
int bs_answer(int lo, int hi, auto condition) {
    while (lo < hi) { int mid = (lo+hi)/2; if (condition(mid)) hi = mid; else lo = mid+1; }
    return lo;
}
```

**Week 3–4: Bash, tmux, strace**
- Write 3 real Bash scripts (build automation, git daily commit, log parser)
- tmux pane layout: left=editor, right=build/output
- strace your compiled programs. Read the output.

**Month 1 target:** 80–100 LeetCode problems. CF rating 1100–1300.

---

**Week 5–8: OS Deep Dive + C++ Concurrency Intro + Trees/Graphs Intro**

Goals:
- OS Concepts Ch 4–6 (threads, scheduling, synchronization) + C programs
- OS Concepts Ch 8–10 (memory, paging, virtual memory)
- Inside the Machine complete (parallel to OS reading)
- Modular arithmetic implemented and tested
- Trees and linked lists complete in DSA

**Math integration (Week 5–8):**
- Week 5–6: Modular arithmetic. Implement extgcd, modpow, fermat_inv, nCr. 
  Test on actual Codeforces problems. 15 hours.
- Week 7–8: Combinatorics. MIT MCS Ch 14–15. C(n,k), inclusion-exclusion,
  pigeonhole. Solve 20 counting problems. 12 hours.

**OS projects to build (mandatory):**
```c
// Shared memory IPC between two processes
int shmid = shmget(IPC_PRIVATE, 4096, IPC_CREAT | 0666);
void *shm = shmat(shmid, NULL, 0);
// Process A writes: strcpy((char*)shm, "hello from A");
// Process B reads: printf("%s\n", (char*)shm);

// mmap for fast file I/O
int fd = open("data.bin", O_RDONLY);
struct stat sb; fstat(fd, &sb);
void *mapped = mmap(NULL, sb.st_size, PROT_READ, MAP_PRIVATE, fd, 0);
// Read without syscalls in hot path — kernel handles page faults

// Thread pool (simplified):
struct ThreadPool {
    vector<thread> workers;
    queue<function<void()>> tasks;
    mutex mtx; condition_variable cv; bool stop{false};
    ThreadPool(int n) {
        for (int i = 0; i < n; i++) workers.emplace_back([this] {
            while (true) {
                function<void()> task;
                { unique_lock<mutex> lock(mtx);
                  cv.wait(lock, [this]{ return stop || !tasks.empty(); });
                  if (stop && tasks.empty()) return;
                  task = move(tasks.front()); tasks.pop(); }
                task();
            }
        });
    }
    void submit(function<void()> f) {
        { lock_guard<mutex> lock(mtx); tasks.push(move(f)); }
        cv.notify_one();
    }
    ~ThreadPool() { { lock_guard<mutex> lock(mtx); stop = true; }
                    cv.notify_all(); for (auto& w : workers) w.join(); }
};
```

**Month 2 target:** 180–200 LeetCode problems. CF rating 1300–1500.

---

## 6. Phase 2 — Month 3–4: Core Systems

### Month 3: DDIA + Networking + Probability

**Reading priority for Month 3:**
- Morning reading block: Blitzstein Ch 1–6 (one chapter every 3–4 days)
- Afternoon systems block: Alternate between DDIA (chapters 1–8) and Kurose Ch 1–4
- Evening: CF contest + upsolve + graph algorithm practice

**Networking projects:**
```c
// epoll echo server — the real modern way:
int epfd = epoll_create1(0);
struct epoll_event ev, events[MAX_EVENTS];
ev.events = EPOLLIN | EPOLLET; // edge-triggered
ev.data.fd = listen_fd;
epoll_ctl(epfd, EPOLL_CTL_ADD, listen_fd, &ev);

while (true) {
    int n = epoll_wait(epfd, events, MAX_EVENTS, -1);
    for (int i = 0; i < n; i++) {
        if (events[i].data.fd == listen_fd) {
            // Accept new connection
            int conn = accept(listen_fd, NULL, NULL);
            setnonblocking(conn);
            ev.data.fd = conn; ev.events = EPOLLIN | EPOLLET;
            epoll_ctl(epfd, EPOLL_CTL_ADD, conn, &ev);
        } else {
            // Handle data from existing connection
            char buf[4096]; ssize_t n;
            while ((n = read(events[i].data.fd, buf, sizeof(buf))) > 0)
                write(events[i].data.fd, buf, n); // echo
        }
    }
}
```

**DSA: Month 3 — Graphs**
All graph algorithms implemented from scratch. Do not copy — type every
line and debug every bug. The bugs you debug are what you remember in interviews.

**Month 3 target:** 280–300 LeetCode problems. CF rating 1500–1650.

---

### Month 4: DBMS + Systems Design + Advanced DP

**PostgreSQL practice (mandatory):**
```sql
-- Understanding index usage:
CREATE TABLE orders (id BIGSERIAL, customer_id INT, created_at TIMESTAMPTZ, amount DECIMAL);
CREATE INDEX idx_customer_time ON orders (customer_id, created_at);

EXPLAIN ANALYZE SELECT * FROM orders 
WHERE customer_id = 1234 ORDER BY created_at DESC LIMIT 10;
-- Should show: Index Scan using idx_customer_time
-- If it shows Seq Scan: check table statistics, run ANALYZE

-- Understanding MVCC with transactions:
BEGIN;
SELECT amount FROM orders WHERE id = 1; -- snapshot taken here
-- In another session: UPDATE orders SET amount = 999 WHERE id = 1;
SELECT amount FROM orders WHERE id = 1; -- still sees old value (MVCC)
COMMIT;
```

**Systems Design practice (5 systems):**

For each system, spend 45–60 minutes designing before looking at any reference:
1. Design a URL shortener (start simple, scale to 1B URLs)
2. Design a distributed rate limiter (token bucket, sliding window)
3. Design a notification system (push, email, SMS fan-out)
4. Design a real-time leaderboard (sorted sets, approximate counting)
5. Design a chat system (WebSocket, message delivery, read receipts)

**DSA: Month 4 — DP Deep Dive**
Spend 3 weeks on DP exclusively. One pattern per 2–3 days. The interval DP
and bitmask DP sections should take 1 full week each.

**Month 4 target:** 380 LeetCode problems. CF rating 1650–1800.

---

## 7. Phase 3 — Month 5–6: Specialization

### Month 5: Lock-Free C++ + HFT Math

**C++ Concurrency in Action — Williams Ch 5–7:**
Read slowly. This is the hardest text in the plan. Budget 3 weeks for these
3 chapters. Do not move forward until acquire/release semantics feel intuitive.

**Key implementations:**
```cpp
// Lock-free SPSC queue (single producer, single consumer)
// Cache-line aligned to prevent false sharing
template<typename T, size_t CAPACITY>
struct alignas(64) SPSCQueue {
    static_assert((CAPACITY & (CAPACITY-1)) == 0, "Must be power of 2");

    struct alignas(64) { std::atomic<size_t> head{0}; };
    struct alignas(64) { std::atomic<size_t> tail{0}; };
    T buffer[CAPACITY];

    bool push(const T& item) {
        size_t t = tail.load(std::memory_order_relaxed);
        size_t next = (t + 1) & (CAPACITY - 1);
        if (next == head.load(std::memory_order_acquire)) return false; // full
        buffer[t] = item;
        tail.store(next, std::memory_order_release);
        return true;
    }

    bool pop(T& item) {
        size_t h = head.load(std::memory_order_relaxed);
        if (h == tail.load(std::memory_order_acquire)) return false; // empty
        item = buffer[h];
        head.store((h + 1) & (CAPACITY - 1), std::memory_order_release);
        return true;
    }
};
// acquire on load: see all stores that happened-before the matching release
// release on store: all previous stores visible to threads that acquire this

// False sharing benchmark — measure the actual cost:
struct BadCounters { std::atomic<int> a, b; };   // same cache line
struct GoodCounters {
    alignas(64) std::atomic<int> a;
    alignas(64) std::atomic<int> b;               // separate cache lines
};
// Run: 2 threads, Thread1 increments a 10M times, Thread2 increments b 10M times
// Bad: ~3.5 seconds (constant cache invalidation)
// Good: ~0.4 seconds (independent cache lines)
```

### Month 6: Mock Interviews + Project Polish + HFT Specialization

**Mock interview schedule:**
- 3 per week on Pramp
- 2 per week self-mock (solve problem, explain out loud, record once/week)
- Read 1 FAANG engineering blog post per day

**Optiver-specific prep (if targeting):**
80 mental arithmetic questions in 8 minutes. Practice 15 min/day for the
final 4 weeks:
- Mental multiplication: 47 × 23 = 40×23 + 7×23 = 920 + 161 = 1081
- Square roots to 2 decimal places: √50 ≈ 7.07 (= 5√2)
- Percentages: 37% of 850 = 850 × 0.37 = 314.5
- Fractions to decimals: 7/13 = 0.538...

---

## 8. Projects — Complete Reference

### Overview

| # | Project | Phase | Who It Impresses | Difficulty |
|---|---|---|---|---|
| 1 | Mini Shell (C) | 1 | Systems baseline | Medium |
| 2 | Thread Pool (C++) | 1–2 | C++ concurrency | Medium |
| 3 | TCP Echo Server + epoll (C++) | 2 | Networking depth | Medium |
| 4 | **Distributed Rate Limiter** (C++) | 2–3 | **FAANG + Startups flagship** | High |
| 5 | HTTP/1.1 Server (C++) | 2–3 | FAANG + Systems | High |
| 6 | Key-Value Store + WAL (C++) | 3 | FAANG + Systems | High |
| 7 | Custom Memory Allocator (C++) | 3 | HFT + Systems | Very High |
| 8 | Lock-Free SPSC Queue + Benchmarks (C++) | 3 | HFT flagship | High |
| 9 | **LOB Matching Engine** (C++) | 3 | **HFT flagship** | Very High |
| 10 | Market Data Feed Handler (C++) | 3 | HFT systems | High |
| 11 | **SIMD Tensor + Mini Inference Engine** (C++) | 3 | **C++ AI flagship** | Very High |
| 12 | Real-Time Anomaly Detector (C++) | 3 | C++ AI + HFT + Systems | High |

---

### Project 4: Distributed Rate Limiter — FAANG/Startup Flagship

**Why this is the flagship project for FAANG/startups:**
Rate limiting is mentioned in nearly every FAANG system design interview.
Every API at scale (Stripe, Twilio, GitHub, every startup) implements rate
limiting. This project lets you say "I implemented this, here are the
tradeoffs between token bucket and sliding window, and here is how I made
it distributed." That conversation can fill an entire system design round.

**What to build:**
```cpp
// Core algorithms — implement both:

// 1. Token Bucket: allows burst up to capacity, refills at fixed rate
struct TokenBucket {
    double tokens;           // current token count
    double capacity;         // max tokens (burst allowance)
    double refill_rate;      // tokens per second
    uint64_t last_refill_ns; // last refill timestamp

    bool allow(uint64_t now_ns, int cost = 1) {
        double elapsed = (now_ns - last_refill_ns) / 1e9;
        tokens = std::min(capacity, tokens + elapsed * refill_rate);
        last_refill_ns = now_ns;
        if (tokens >= cost) { tokens -= cost; return true; }
        return false; // rate limit exceeded
    }
};

// 2. Sliding Window Counter: more accurate, prevents edge bursts
struct SlidingWindow {
    // Store request counts in fixed-size time buckets
    // Window = sum of buckets within last N seconds
    // More accurate than fixed window (no reset spikes)
    deque<pair<uint64_t, int>> buckets; // {timestamp_ns, count}
    int window_ns;
    int max_requests;

    bool allow(uint64_t now_ns) {
        // Remove expired buckets
        while (!buckets.empty() && buckets.front().first < now_ns - window_ns)
            buckets.pop_front();
        int total = 0;
        for (auto& [t, c] : buckets) total += c;
        if (total >= max_requests) return false;
        if (!buckets.empty() && buckets.back().first == now_ns / 1000000 * 1000000)
            buckets.back().second++;
        else
            buckets.push_back({now_ns / 1000000 * 1000000, 1});
        return true;
    }
};

// Distributed version: use Redis for shared state
// Key: "ratelimit:{user_id}:{window_start}"
// Value: count of requests in this window
// TTL: window duration
// All nodes check same Redis key — consistency without coordination
```

**Minimum viable features:**
- Token bucket and sliding window implementations
- Per-user, per-IP, and per-API-key rate limits
- Thread-safe local version with `std::atomic`
- Distributed version backed by Redis (or a mock distributed store)
- HTTP API: `GET /check/{user_id}` returns `{allowed: bool, retry_after: int}`
- Admin API: `PUT /limits/{user_id}` updates limits without restart
- Metrics: current rate, rejection count, per-user stats
- Benchmark: show throughput (req/s) and latency under different loads

**README must explain:** Token bucket vs sliding window tradeoffs. Why
distributed rate limiting needs atomic Redis operations (`INCR` + `EXPIRE`).
What happens during Redis failure (fail-open vs. fail-closed tradeoff).

---

### Project 5: HTTP/1.1 Server in C++

```cpp
// Core architecture:
// 1. Listening socket with SO_REUSEADDR + SO_REUSEPORT
// 2. Thread pool (from Project 2) to handle connections
// 3. HTTP/1.1 request parser (state machine)
// 4. Response builder (status line + headers + body)
// 5. Keep-alive connection management

// HTTP request parser:
struct HttpRequest {
    string method, path, version;
    unordered_map<string, string> headers;
    string body;
};

HttpRequest parse_request(const string& raw) {
    HttpRequest req;
    istringstream stream(raw);
    stream >> req.method >> req.path >> req.version;
    string line;
    getline(stream, line); // consume \r\n after request line
    while (getline(stream, line) && line != "\r") {
        auto colon = line.find(':');
        if (colon != string::npos) {
            string key = line.substr(0, colon);
            string val = line.substr(colon + 2);
            if (!val.empty() && val.back() == '\r') val.pop_back();
            req.headers[key] = val;
        }
    }
    return req;
}

// Response builder:
string build_response(int status, const string& content_type,
                       const string& body, bool keep_alive = true) {
    map<int, string> status_text = {{200,"OK"},{404,"Not Found"},{500,"Internal Server Error"}};
    ostringstream resp;
    resp << "HTTP/1.1 " << status << " " << status_text[status] << "\r\n"
         << "Content-Type: " << content_type << "\r\n"
         << "Content-Length: " << body.size() << "\r\n"
         << "Connection: " << (keep_alive ? "keep-alive" : "close") << "\r\n"
         << "\r\n" << body;
    return resp.str();
}
```

---

### Project 6: Key-Value Store + WAL in C++

**Architecture:** In-memory `unordered_map` + write-ahead log for crash recovery.
Based on DDIA Chapter 3 (hash index + append-only log).

```cpp
class KVStore {
    unordered_map<string, string> store;
    ofstream wal;        // write-ahead log (append-only)
    mutex mtx;

    void replay_wal(const string& wal_path) {
        // On startup: replay every SET/DEL from log to rebuild state
        ifstream f(wal_path);
        string op, key, val;
        while (f >> op >> key) {
            if (op == "SET") { f >> val; store[key] = val; }
            else if (op == "DEL") { store.erase(key); }
        }
    }
public:
    KVStore(const string& wal_path) : wal(wal_path, ios::app) { replay_wal(wal_path); }

    void set(const string& k, const string& v) {
        lock_guard<mutex> lock(mtx);
        wal << "SET " << k << " " << v << "\n"; // WAL first
        wal.flush();                              // durable before in-memory update
        store[k] = v;
    }
    optional<string> get(const string& k) {
        lock_guard<mutex> lock(mtx);
        auto it = store.find(k);
        return it != store.end() ? optional(it->second) : nullopt;
    }
    void del(const string& k) {
        lock_guard<mutex> lock(mtx);
        wal << "DEL " << k << "\n"; wal.flush();
        store.erase(k);
    }
    void compact() {
        // Rewrite log with only live keys — eliminates deleted/overwritten entries
    }
};
```

---

### Project 7: Custom Memory Allocator

**Why:** Memory allocation is a hot path in every HFT system. `malloc`/`free`
have unpredictable latency due to coalescing and OS interaction. Custom
allocators eliminate this. This project demonstrates the deepest systems
knowledge in your portfolio.

```cpp
// Arena (bump) allocator: O(1) allocation, bulk free
struct Arena {
    char* base;
    size_t offset, capacity;
    Arena(size_t cap) : base((char*)mmap(nullptr, cap, PROT_READ|PROT_WRITE,
                                          MAP_ANON|MAP_PRIVATE, -1, 0)),
                         offset(0), capacity(cap) {}
    ~Arena() { munmap(base, capacity); }
    
    void* alloc(size_t size, size_t align = alignof(max_align_t)) {
        // Align offset
        size_t aligned = (offset + align - 1) & ~(align - 1);
        if (aligned + size > capacity) throw bad_alloc();
        void* ptr = base + aligned;
        offset = aligned + size;
        return ptr;
    }
    void reset() { offset = 0; } // Free all at once — O(1)
};

// Pool allocator: fixed-size objects, O(1) alloc/free
template<typename T, size_t POOL_SIZE>
struct PoolAllocator {
    struct Block { Block* next; };
    alignas(T) char storage[POOL_SIZE * sizeof(T)];
    Block* free_list;
    size_t allocated{0};

    PoolAllocator() {
        free_list = nullptr;
        for (int i = POOL_SIZE - 1; i >= 0; i--) {
            auto blk = reinterpret_cast<Block*>(&storage[i * sizeof(T)]);
            blk->next = free_list; free_list = blk;
        }
    }
    T* alloc() {
        if (!free_list) throw bad_alloc();
        Block* blk = free_list; free_list = blk->next;
        allocated++;
        return reinterpret_cast<T*>(blk);
    }
    void free(T* ptr) {
        auto blk = reinterpret_cast<Block*>(ptr);
        blk->next = free_list; free_list = blk;
        allocated--;
    }
};
// HFT usage: OrderPool allocator for Order objects
// Every new order draws from pre-allocated pool — zero system calls in hot path
```

---

### Project 8: Lock-Free SPSC Queue + Benchmarks

See Section 7 (Phase 3) for the full implementation. The benchmark is as
important as the implementation — show the numbers in your README.

**Benchmark target:**
```
Results on Intel Core i7-12700H (measured with Google Benchmark):

SPSCQueue<int, 65536> throughput:
  Lock-free SPSC:       425 million ops/sec   (~2.35 ns/op)
  std::mutex queue:      48 million ops/sec   (~20.8 ns/op)
  Speed improvement:     8.9x

False sharing experiment (2 threads, 10M increments each):
  Shared cache line:   3,412 ms
  Padded to 64 bytes:    389 ms
  Speedup:               8.8x
```

---

### Project 9: LOB Matching Engine — HFT Flagship

```cpp
struct Order {
    uint64_t id;
    int64_t price;    // fixed-point, price × 10000
    int64_t quantity;
    bool is_buy;
    uint64_t timestamp;
};

struct PriceLevel {
    int64_t price;
    int64_t total_qty{0};
    std::deque<Order> orders; // FIFO at each price level
};

class OrderBook {
    // Bids: descending (highest price first = best bid)
    std::map<int64_t, PriceLevel, std::greater<int64_t>> bids;
    // Asks: ascending (lowest price first = best ask)
    std::map<int64_t, PriceLevel> asks;

    struct Trade {
        uint64_t aggressor_id, passive_id;
        int64_t price, quantity;
        uint64_t timestamp;
    };

    vector<Trade> match_market_buy(int64_t qty) {
        vector<Trade> trades;
        while (qty > 0 && !asks.empty()) {
            auto& [price, level] = *asks.begin();
            while (qty > 0 && !level.orders.empty()) {
                Order& passive = level.orders.front();
                int64_t fill = std::min(qty, passive.quantity);
                trades.push_back({0, passive.id, price, fill, rdtsc()});
                passive.quantity -= fill;
                level.total_qty -= fill;
                qty -= fill;
                if (passive.quantity == 0) level.orders.pop_front();
            }
            if (level.orders.empty()) asks.erase(price);
        }
        return trades;
    }

public:
    vector<Trade> add_order(Order order) {
        if (order.is_buy && !asks.empty() && order.price >= asks.begin()->first)
            return match_market_buy(order.quantity); // aggressive buy
        // Passive: add to book
        auto& book = order.is_buy ? bids : asks; // type erasure needed here
        auto& level = book[order.price];
        level.price = order.price;
        level.total_qty += order.quantity;
        level.orders.push_back(order);
        return {}; // no immediate fills
    }

    // Accessors for bid/ask spread, mid price, book depth
    optional<int64_t> best_bid() const {
        return bids.empty() ? nullopt : optional(bids.begin()->first);
    }
    optional<int64_t> best_ask() const {
        return asks.empty() ? nullopt : optional(asks.begin()->first);
    }
};
```

**Benchmark:** Measure orders/second. Target: >500,000 orders/second for a
simple LOB. Report p50/p99 latency per order in nanoseconds.

---

### Project 10: Market Data Feed Handler

**What it does:** Consumes a simulated or real market data feed (UDP multicast
or TCP stream), parses messages, updates the LOB, and computes derived
statistics (mid price, spread, VWAP, order imbalance).

```cpp
// Simulated FIX-like message parser:
struct MarketDataMessage {
    enum Type { NEW_ORDER, CANCEL, TRADE };
    Type type;
    uint64_t order_id;
    int64_t price;     // fixed-point
    int64_t quantity;
    bool is_buy;
};

class FeedHandler {
    OrderBook book;
    double vwap_numerator{0}, vwap_denominator{0};
    vector<pair<int64_t, int64_t>> trade_tape; // {price, qty}

    void on_trade(int64_t price, int64_t qty) {
        vwap_numerator += (double)price * qty;
        vwap_denominator += qty;
        trade_tape.push_back({price, qty});
    }

public:
    void process(const MarketDataMessage& msg) {
        auto start = rdtsc();
        // ... process message, update book, call on_trade for fills
        auto end = rdtsc();
        // record latency: (end - start) / tsc_ghz nanoseconds
    }

    double vwap() const {
        return vwap_denominator > 0 ? vwap_numerator / vwap_denominator : 0;
    }
};
```

---

### Project 11: SIMD Tensor Library + Mini Inference Engine — C++ AI Flagship

**Why C++ AI projects matter now:**
AI infrastructure is one of the fastest-growing hiring areas at FAANG.
Meta, Google, and Microsoft all have teams building inference infrastructure
in C++. An AI inference project in C++ signals that you understand both
systems programming and the computational building blocks of AI — a rare
combination.

**What to build:**
```cpp
// 1. Tensor class: N-dimensional array with row-major layout
template<typename T = float>
struct Tensor {
    vector<T> data;
    vector<int> shape;
    vector<int> strides;

    Tensor(vector<int> shape) : shape(shape) {
        int total = 1;
        for (int d : shape) total *= d;
        data.resize(total);
        // Row-major strides: stride[i] = product of shape[i+1..n-1]
        strides.resize(shape.size());
        strides.back() = 1;
        for (int i = shape.size()-2; i >= 0; i--)
            strides[i] = strides[i+1] * shape[i+1];
    }

    T& at(vector<int> idx) {
        int offset = 0;
        for (int i = 0; i < idx.size(); i++) offset += idx[i] * strides[i];
        return data[offset];
    }

    int numel() const { int n = 1; for (int d : shape) n *= d; return n; }
};

// 2. SIMD matrix multiply (AVX2): 8 floats per instruction
// A: MxK, B: KxN, C: MxN
void matmul_avx2(const float* A, const float* B, float* C, int M, int K, int N) {
    memset(C, 0, M * N * sizeof(float));
    for (int i = 0; i < M; i++) {
        for (int k = 0; k < K; k++) {
            __m256 a_ik = _mm256_set1_ps(A[i * K + k]); // broadcast A[i][k]
            for (int j = 0; j < N; j += 8) {             // 8 floats per AVX register
                __m256 b_kj = _mm256_loadu_ps(&B[k * N + j]);
                __m256 c_ij = _mm256_loadu_ps(&C[i * N + j]);
                c_ij = _mm256_fmadd_ps(a_ik, b_kj, c_ij); // c += a * b (FMA)
                _mm256_storeu_ps(&C[i * N + j], c_ij);
            }
        }
    }
}
// Target performance: 10–20x speedup over naive on 512x512 matrices

// 3. Softmax (numerically stable):
void softmax(float* x, int n) {
    float max_val = *max_element(x, x+n);
    float sum = 0;
    for (int i = 0; i < n; i++) { x[i] = expf(x[i] - max_val); sum += x[i]; }
    for (int i = 0; i < n; i++) x[i] /= sum;
}

// 4. Mini 2-layer neural network forward pass:
// Input(784) → Dense(256, ReLU) → Dense(10, Softmax) → Class probabilities
// Weights loaded from a pre-trained file (train externally in Python, infer in C++)
void forward(const float* input, float* output,
             const float* W1, const float* b1,   // 256 x 784
             const float* W2, const float* b2) { // 10 x 256
    static float h1[256], h2[10];
    matmul_avx2(W1, input, h1, 256, 784, 1);
    for (int i = 0; i < 256; i++) { h1[i] += b1[i]; h1[i] = max(0.0f, h1[i]); } // ReLU
    matmul_avx2(W2, h1, h2, 10, 256, 1);
    for (int i = 0; i < 10; i++) h2[i] += b2[i];
    softmax(h2, 10);
    memcpy(output, h2, 10 * sizeof(float));
}
```

**Benchmark to report:**
```
Naive matrix multiply (512x512):    1,240 ms
SIMD (AVX2) matrix multiply:           68 ms
Speedup:                              18.2x

Single inference forward pass:         0.8 μs (< 1 microsecond)
10,000 inferences:                     7.4 ms
Throughput:                     1.35M inferences/second
```

**README must explain:** Why row-major layout matters for cache efficiency.
What FMA (fused multiply-add) does. Why you subtract max before softmax.
How the weights were trained (external Python training, C++ inference only).

---

### Project 12: Real-Time Anomaly Detector

**What:** A system that processes a stream of metrics (latency, throughput,
error rate) and detects anomalies in real-time using statistical methods.
Relevant to both HFT (detecting unusual market conditions) and systems
engineering (production monitoring).

```cpp
// Online anomaly detection using EWMA + adaptive thresholds:
struct AnomalyDetector {
    double ewma{0};           // exponential weighted moving average
    double ewma_sq{0};        // EWMA of squared values (for variance)
    double alpha;             // smoothing factor
    double threshold_sigma;   // alert at this many standard deviations
    bool initialized{false};
    int alert_count{0};

    AnomalyDetector(double alpha = 0.1, double sigma = 3.0)
        : alpha(alpha), threshold_sigma(sigma) {}

    struct Result { bool is_anomaly; double value; double mean; double sigma; double z_score; };

    Result process(double value) {
        if (!initialized) { ewma = value; ewma_sq = value*value; initialized = true;
                             return {false, value, value, 0, 0}; }
        ewma    = alpha * value + (1-alpha) * ewma;
        ewma_sq = alpha * value*value + (1-alpha) * ewma_sq;
        double variance = ewma_sq - ewma*ewma;
        double sigma = variance > 0 ? sqrt(variance) : 1e-10;
        double z = std::abs(value - ewma) / sigma;
        bool anomaly = z > threshold_sigma;
        if (anomaly) alert_count++;
        return {anomaly, value, ewma, sigma, z};
    }
};

// Usage in a metrics pipeline:
AnomalyDetector latency_detector(0.05, 4.0); // alpha=0.05, alert at 4σ
while (true) {
    double latency_us = get_latest_latency();
    auto result = latency_detector.process(latency_us);
    if (result.is_anomaly) {
        printf("ALERT: latency %.1fμs, z=%.2f (mean=%.1f, σ=%.1f)\n",
               result.value, result.z_score, result.mean, result.sigma);
    }
}
```

---

## 9. DSA Milestones

| Date | LC Count | CF Rating | Key Criteria |
|---|---|---|---|
| Day 31 | 100 | 1200–1400 | Easy < 10 min. Medium < 30 min. |
| Day 60 | 200 | 1400–1500 | Medium < 22 min. DP started. |
| Day 90 | 300 | 1550–1650 | Graphs complete. DP fundamentals solid. |
| Day 120 | 380 | 1650–1800 | Advanced DP. Hard in 50 min. |
| Day 150 | 450 | 1800–1900 | Segment tree + string algo. Hard in 40 min. |
| Day 175 | 500+ | 1900+ | Hard < 35 min. Div 1 rounds. |

**Non-negotiable rule:** Upsolve every Codeforces contest within 24 hours.
Write your own solution before reading editorial. This is where 70% of the
rating gain comes from.

---

## 10. Books and Resources

### Books — Ordered by Phase

| Book | Author | Phase | Read | Notes |
|---|---|---|---|---|
| *A Tour of C++* | Stroustrup | 1 | Cover to cover | Code every example |
| *OS Concepts* | Silberschatz | 1–2 | Ch 1–6, 8–10 | Write C programs alongside |
| *Inside the Machine* | Stokes | 1 | Full | Short; read with OS book |
| *Introduction to Probability* | Blitzstein & Hwang | 3 | Ch 1–6 | Do exercises, not just read |
| *Computer Networking: Top Down* | Kurose & Ross | 3 | Ch 1–4 deep, 5–6 selective | Implement alongside |
| *DDIA* | Kleppmann | 3 | Full | Active notes. One chapter/day. |
| *DBMS Concepts* | Ramakrishnan | 3–4 | Focused chapters | Transactions, indexing, MVCC |
| *CLRS* | Cormen et al. | Reference | Ch 2–5, 10–17, 22–26, 31 | Reference, not cover-to-cover |
| *C++ Concurrency in Action* | Williams | 5–6 | Ch 5–7 | Slowest read. Go carefully. |
| *The Rust Programming Language* | Klabnik | 5 | Ch 1–15 | Free online. Rustlings alongside. |
| *The Linux Programming Interface* | Kerrisk | 2–5 ongoing | Reference | Expensive. Worth it. |

### Online Resources — Curated

| Resource | Purpose | Priority |
|---|---|---|
| Neetcode.io | Structured LeetCode ordering | ★★★★★ |
| CSES Problem Set (cses.fi) | Pre-CF structured problems | ★★★★★ |
| cppreference.com | C++ daily reference | ★★★★★ |
| CP-algorithms.com | Algorithms with code | ★★★★★ |
| Cloudflare Blog | Real systems engineering | ★★★★ |
| Beej's Guide (beej.us/guide/bgnet) | Socket programming | ★★★★ |
| CppCon Back to Basics (YouTube) | Modern C++ talks | ★★★★ |
| Martin Kleppmann YouTube | DDIA companion | ★★★★ |
| StatQuest YouTube | Probability and statistics | ★★★ |
| Pramp (pramp.com) | Free mock interviews | ★★★ |
| Reducible YouTube | Algorithm animations | ★★★ |
| Intel Intrinsics Guide | SIMD reference for AI project | ★★★ |

---

## 11. Portfolio and Freelancing

### Timeline

**Month 1:** Portfolio site live on Vercel. Astro or plain HTML. 2–3 hours max.
GitHub with public repos from Day 1. Green squares every day.

**Month 2:** First blog post: "Building a shell in C — what fork/exec/pipes actually do."
Post on portfolio + Dev.to. Share on LinkedIn.

**Month 3:** Blog post 2: "HTTP/1.1 from scratch in C++ — request parsing and thread pools."

**Month 4:** Buy `yourname.dev` domain (₹1,200/yr on Namecheap). Set up VPS
(Hostinger ₹349/mo or Hetzner CX22 ~₹380/mo). Deploy projects live.
This is also your Linux systems practice — nginx, SSL, fail2ban, firewall.

**Month 5:** Blog post 3: "Lock-free queue vs mutex: benchmarks and what they mean."
Blog post 4: "What I learned building a SIMD matrix library in C++."

**Month 6:** Polish all project READMEs. Case study format: Problem → Approach →
Key decisions → Benchmarks → What I'd do differently at scale.

### Freelance Services by Month

| Month | Service | Platform | Rate |
|---|---|---|---|
| 2 | VPS setup + nginx + SSL | Fiverr, Upwork | ₹3,000–8,000 |
| 2 | Bash automation scripts | Upwork | ₹1,500–5,000 |
| 3 | C++ code review | LinkedIn, Upwork | ₹5,000–20,000 |
| 4 | Backend performance audit | LinkedIn cold DM | ₹8,000–25,000 |
| 5 | Systems programming contract | LinkedIn, HN thread | ₹15,000–60,000 |
| 5 | C++ AI optimization | LinkedIn, AI startups | ₹20,000–80,000 |

**Start LinkedIn posting in Month 3:** One technical post per week.
Not motivational. Technical. "Why epoll beats select for 10,000 connections —
with numbers." This content attracts technical recruiters from HFT firms.

**HN Freelancer Thread (1st of every month from Month 4):**
Post: "C++ systems + HFT background | Linux internals | lock-free concurrency |
inference engine | India timezone | available for contract. Recent projects: [links]."

---

## 12. Study Environment

### Hardware Priority Order

| Item | Priority | Budget (₹) | Specific Recommendation |
|---|---|---|---|
| Ergonomic chair | **Critical** | 4,000–9,000 | Green Soul Monster Ultimate. Back pain in Month 3 ends the plan. |
| 24" IPS monitor | **Must Have** | 8,000–14,000 | LG 24MK430H. Second screen = code + docs simultaneously. |
| Mechanical keyboard | High | 2,500–6,000 | Keychron K2 V2 with red switches. |
| Wired mouse | High | 500–1,500 | Logitech G102. Wired = zero latency. |
| Laptop stand | High | 800–2,000 | Eye level = no neck strain in 6-month sprint. |
| Wired closed-back headphones | Medium | 1,000–3,000 | Audio-Technica ATH-M20x. Isolation. |
| Powered USB hub | Medium | 600–1,200 | Anker 4-port with power adapter. |

**Do not buy:** Standing desk, ultrawide, RGB keyboards, gaming chairs,
coaching subscriptions, course bundles, iPad, Bluetooth peripherals.

### Software Setup

| Tool | Day | Task |
|---|---|---|
| Arch/Debian Linux | Day 1 | Daily OS. No going back. |
| Neovim (kickstart.nvim) | Day 1 | 4 hours max on setup. clangd + telescope + treesitter. |
| tmux | Day 1 | Left pane = editor. Right pane = build output. |
| gcc/clang + cmake + ninja | Day 1 | Full C++ toolchain. Use clang++ — better errors. |
| GDB + Valgrind | Week 1 | 5 GDB commands. Valgrind every C program. |
| strace + perf | Month 2 | `perf stat` on every benchmark. |
| Intel Intrinsics guide | Month 5 | Reference for SIMD project. |
| Rustup | Month 5 only | Don't install until Month 5. |

### Deep Work Rules

1. Phone in another room during study blocks — not silent, another room.
2. LeechBlock NG (Firefox) or StayFocusd (Chrome) blocks Instagram/YouTube during study hours.
3. One tab open: the current resource only.
4. Start time and end time logged every session in the tracker.
5. Solve every problem on paper before typing a single line of code.
6. One topic at a time. Never open DDIA, a CF problem, and C++ simultaneously.
7. Weekly review every Sunday: what entered long-term memory vs. what just passed through?

---

## 13. Mistakes to Avoid

1. **Not upsolving CF contests.** The single most common reason CF rating
   stagnates. Every round without upsolving is 40% of a round wasted.

2. **Reading OS Concepts without writing syscall programs.** The book alone
   is inert knowledge. Each chapter needs a corresponding C program that
   exercises the concepts.

3. **Spending more than 4 hours on Neovim config.** This is the most
   seductive procrastination in developer culture. Your editor is a tool,
   not a hobby.

4. **Doing LeetCode randomly.** Pattern-first, then practice. Random grinding
   builds false confidence and misses the systematic skill-building that
   interviews test.

5. **Starting Rust before Month 5.** It consumes focus when you need C++
   and OS depth. Defer and do it right.

6. **Treating DDIA as light reading.** It requires active notes and
   re-reading of hard chapters (7, 8, 9). Budget 4 weeks, not 1.

7. **Building projects without READMEs and case studies.** A GitHub link
   without explanation is a missed conversation starter. Interviewers
   use your README to ask follow-up questions.

8. **Skipping the math exercises.** Reading the math without doing exercises
   is like watching someone else's workout. The exercises are where the
   understanding becomes permanent.

9. **Averaging less than 4 hours/day.** The probability table in Section 1
   assumes 5.5–6 hours consistently. At 4 hours/day average, subtract one
   tier from every outcome.

10. **Applying to jobs before Month 5.** Applications before you have 380+
    LeetCode, working projects, and systems depth will result in rejections
    that demoralize without being informative. Apply when ready.

11. **Ignoring the SIMD/C++ AI project.** This is a differentiator that
    most candidates for systems roles will not have. C++ + AI inference
    is a narrow enough niche that it gets attention from FAANG AI infra teams
    and AI startups paying ₹30–50 LPA for systems engineers.

12. **Not practicing spoken technical explanation.** Explain every problem
    solution out loud before looking at any solution. 3 minutes of speaking
    after every single problem. No exceptions.

---

*Plan version: June 2026*
*Tracker: prep_tracker.xlsx (Dashboard · Daily Log · DSA Tracker · Books ·*
*Projects · Weekly Review · Milestones · Portfolio & Freelance)*