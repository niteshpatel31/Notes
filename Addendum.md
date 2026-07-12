# Addendum: Book Integration + Compensation Reality
## Companion to the 6-Month Systems Engineering Prep Plan
**Generated:** July 2026

This addendum does two things: (1) integrates your 25-book list into the existing plan with honest verdicts, and (2) replaces vague salary hopes with current, sourced numbers and a brutally honest read on where you'll actually land.

---

## 1. Book-by-Book Verdict

| # | Book | Verdict | Where it fits | Why |
|---|------|---------|---------------|-----|
| 1 | *Fluent Python* | **SKIP** | — | Wrong stack. Your path is C++. Only relevant if you're quietly pivoting to a Python-heavy backend track — say so if that's true, it changes the plan. |
| 2 | *The Art of Writing Efficient Programs* (Pikus) | **ADD** | Phase 3, Month 5, after lock-free C++ | Genuinely excellent for HFT-adjacent latency thinking — CPU cache behavior, branch prediction, compiler optimization. Advanced; only start it once Phase 1 C++ is solid. |
| 3 | *Practical Vim* | **SKIP** | — | Plan uses Neovim, not Vim. Redundant purchase. |
| 4 | *Learning the vi and Vim Editors* | **SKIP** | — | Same reason as #3. Don't buy three editor books for a decision already made. |
| 5 | *Modern Vim* | **SKIP** | — | Same. |
| 6 | *tmux 3* | **SKIP (use cheat sheet instead)** | — | tmux setup is a 30-minute task (Section 5.3 of the main plan). A full book is disproportionate. |
| 7 | *Programming with C++20* (Fertig) | **ADD** | Month 2, right after *A Tour of C++* | Concepts, coroutines, ranges — genuinely current and interview-relevant for a C++20-shop. |
| 8 | *High Performance Python* | **SKIP** | — | Wrong stack, same reasoning as #1. |
| 9 | *DDIA* (Kleppmann) | **Already in plan** | Month 3 | No change. |
| 10 | *C++ Lambda Story* | **SKIP** | — | Lambdas are adequately covered by *A Tour of C++* + the CppCon talks already scheduled. A whole book on one feature is low ROI here. |
| 11 | *C++ Templates: The Complete Guide* | **SKIP for this 6-month window** | Reference only, post-Month 6 | 1,500+ pages of template metaprogramming depth. Not tested at entry-level FAANG or HFT systems interviews. Keep it as a Year 2 book. |
| 12 | *C++: A Beginner's Guide* (Schildt) | **HARD SKIP** | — | Too basic for someone already C++-intermediate, and Schildt's C/C++ books have a well-documented reputation for technical inaccuracies in the C++ community. Not worth the risk of learning something wrong. |
| 13 | *C++ Software Design* (Iglberger) | **ADD — high value** | Month 4–5, before Systems Design phase | Modern C++ design patterns done right. This is your replacement for GoF's dated examples. |
| 14 | *Effective Modern C++* (Meyers) | **ADD — should be a core book, not optional** | Month 1–2, alongside *A Tour of C++* | Arguably more interview-relevant than *A Tour of C++* for someone already intermediate. Move constructors, `noexcept`, smart pointer pitfalls — this is asked in real interviews. |
| 15 | *C++17 In Detail* | **OPTIONAL — reference, don't read linearly** | Skim during Month 2 | Overlaps with #7 and #14. Use the index, not cover-to-cover. |
| 16 | *Beautiful C++* (Core Guidelines) | **OPTIONAL — one weekend read** | Month 2 | Short book, quick reinforcement of good habits. Not essential. |
| 17 | *Inside the Machine* (Stokes) | **Already in plan** | Month 1 | No change. |
| 18 | *OS: Three Easy Pieces* (Arpaci-Dusseau) | **ADD, upgrade over Silberschatz** | Month 1–2 | Free online (pages.cs.wisc.edu/~remzi/OSTEP), more modern, more implementation-focused, widely used in university OS courses. Honest take: better for self-study than Silberschatz. Use it as primary, keep Silberschatz as a reference if you already own it. |
| 19 | *TCP/IP Illustrated Vol. 1* (Stevens) | **ADD — reference, not linear read** | Phase 2–3, dip in for TCP handshake, congestion control chapters | 1,000-page protocol reference. Kurose stays your primary textbook; use Stevens for the specific chapters that come up in interviews. |
| 20 | *Design Patterns* (GoF) | **CAUTION — read for vocabulary only** | Month 4, alongside #13 | 1994 book, C++98/Smalltalk-era code style that modern C++ doesn't write. Learn the pattern names and intent (Strategy, Observer, Factory, Decorator); don't copy the implementations. |
| 21 | *C++ Best Practices* (Turner) | **ADD** | Month 2, one weekend | Short, practical, quick to finish. |
| 22 | *Daily C++ Interview* (Dargo) | **ADD** | Phase 3, Month 5–6 | One-question-a-day format fits directly into the existing daily "explain out loud" routine (Section 16 of the main plan). |
| 23 | *Elements of Programming Interviews* | **ADD — but as a substitute, not an addition** | Phase 3 | Do **not** do this cover-to-cover on top of full LeetCode/Neetcode grinding — that's double-counting hours on the same skill. Use it for interview-format practice (state the problem, brute force, optimize, code) in Month 5–6, or swap it in for part of your LeetCode volume if you prefer book structure. |
| 24 | *C++ Concurrency in Action* (Williams) | **Already in plan** | Month 5–6 | No change. |
| 25 | *Trading Systems Developer Interview Guide (C++ Edition)* (Vogels) | **ADD — high value, exactly on target** | Month 5–6, HFT specialization | This is the most directly relevant book on your list for the HFT track specifically. |

**Bottom line:** 9 adds, 6 hard skips, ~10 reference-only. Scheduling all 25 as full reads would add 150–250+ hours to a plan that's already fully booked — that time has to come from somewhere, and it would come from DSA and the projects, which are the things that actually get you interviews.

---

## 2. Compensation Reality After Completing the Roadmap

Numbers below are pulled from Glassdoor, Levels.fyi, and public offer-report aggregators as of July 2026. Flagging honestly: **this data is noisy.** Self-reported salary sites disagree with each other by 2x on the same role at the same company, and HFT comp in particular is thin-sample and skews toward people who post because their number is impressive. Treat every range as directional, not a quote.

### FAANG / Big Tech — India

| Company | Role | Realistic fresher total comp | Notes |
|---|---|---|---|
| Amazon | SDE-1 | ₹20–32 LPA | Glassdoor's raw median (~₹12–14L) is dragged down by older/non-negotiated offers; ₹20–30L reflects current 2026 fresher postings. Top of range needs strong interview performance. |
| Google | SWE 1 / L3 | ₹30–45 LPA total comp (base often ₹18–25L, rest RSU/bonus) | Genuinely the top of the domestic pay scale — but see the honesty note below on how you actually get an offer. |
| Microsoft | SDE | Comparable to Amazon, slightly lower base, similar total | — |
| Mid-tier product/fintech (Razorpay, Flipkart, PhonePe, Zerodha, Groww, CRED) | SDE-1 | ₹15–30 LPA | Wider hiring funnel, more realistic first landing spot for most non-IIT/NIT candidates. |

**The part nobody puts in the salary table:** the number is only real if you clear the resume screen, and that's where this plan's math gets uncomfortable. Google and Amazon's *campus* pipelines run almost exclusively through IITs, NITs, IIITs, and BITS. Their *off-campus* fresher postings get thousands of applications per opening, and ATS filtering leans hard on college tier and referrals before a human ever looks at your DSA skills. Your 6-month plan makes you interview-ready. It does not fix a resume-screen filter that isn't evaluating your skills at all. The realistic sequencing for most non-tier-1-college candidates is: **mid-tier product/fintech company first → 2 years of real experience and a shipped project portfolio → lateral into FAANG at SDE-2-equivalent**, which is a meaningfully easier door to walk through than fresher off-campus.

### HFT / Prop Trading Systems — India

| Firm | City | Entry-level engineering (non-quant-research) total comp — realistic median | Notes |
|---|---|---|---|
| Optiver | Mumbai (BKC) | Data too thin for India-specific fresher figures; global entry bands run high but India office opened 2024 and is still small | New office, few data points, treat any number you see online with suspicion |
| IMC Trading | Mumbai (Worli) | Same caveat as Optiver | Office opened 2021, still building out India headcount |
| Tower Research Capital | Gurugram | ₹38–70+ LPA depending on level; Glassdoor's low end for "Software Engineer II" is ₹38L, Levels.fyi medians (which skew toward more senior/negotiated reporters) show ₹70L+ | Wide spread — assume the lower end for a genuine fresher hire |
| Graviton, Quadeye | Gurugram | The ₹80–95 LPA fresher numbers circulating on LinkedIn are real but are **outlier data points from a handful of hires**, not a median. Treat them the way you'd treat a lottery-winner interview — true, but not representative. | — |

**The uncomfortable honesty here, straight from people who actually work at these firms (not marketing):** multiple firsthand LinkedIn posts from current/former Quadeye and Graviton employees state plainly that these firms hire almost exclusively from the top 5–7 IITs, and that fresher openings are extremely rare relative to FAANG volume — "for every 1,000 FAANG openings there might be one here." This isn't a skill-ceiling problem, it's a sourcing-funnel problem. Your project portfolio (the LOB matching engine, the lock-free queue with benchmarks) is exactly the right proof-of-work for these firms, but proof-of-work only matters once someone reads your resume — and cold applications from non-IIT BTech grads reportedly convert at very low rates. Referrals matter disproportionately here. If you know anyone at these firms, that relationship is worth more than another 50 LeetCode problems.

### Cities — where these jobs actually are

- **Gurugram (Delhi NCR):** India's real HFT hub — Graviton, Quadeye, Tower Research, and most other prop trading firms are clustered in DLF Cyber City. Not Bangalore.
- **Mumbai (BKC/Worli):** Optiver and IMC specifically, because they're close to NSE. If you're targeting global market makers rather than Indian prop shops, Mumbai is the city.
- **Bangalore:** The FAANG/big-tech center of gravity (Google, Amazon, Microsoft all have major India engineering hubs here), plus most of the fintech/product companies (Flipkart, Razorpay). This is where the "mid-tier landing spot" strategy above plays out.
- **Hyderabad:** Secondary FAANG hub (Amazon, Microsoft, Google all have large Hyderabad offices) — often easier hiring bar than Bangalore for the same company due to lower applicant density.

### Realistic 6-month-to-offer timeline, stated plainly

- **FAANG/big tech, fresher, off-campus, no tier-1 college, no referral:** Possible but the odds are genuinely long — budget for many rejections and plan on the mid-tier company as your real first target, not a fallback.
- **HFT systems engineering, fresher, cold application:** Low probability regardless of prep quality, for sourcing-funnel reasons, not skill reasons. The plan's own Section 15 says "initial conversations Month 6, offers Month 8–9" — I'd go further: without a referral or a top-tier college on the resume, treat Month 8–9 as optimistic, not baseline.
- **Mid-tier product/fintech company, fresher:** This is where the 6-month plan's ROI is highest and most certain. Strong DSA + a couple of real systems projects genuinely moves the needle here.
- **The two-step path (mid-tier → lateral into FAANG/HFT at 2–3 YOE) is the statistically likelier route to the big numbers**, even though it's slower and less satisfying than "6 months to Optiver."

None of this means don't try for the top-tier firms — it means don't build your self-worth or your timeline around them being the *baseline* outcome of this plan. They're the stretch goal. The mid-tier product/fintech offer is the realistic floor this plan is actually built to deliver, and it's a genuinely good floor.

---

*This addendum should be read alongside the main plan's Section 15 (HFT Realism Assessment) and Section 14 (Mistakes to Avoid) — nothing here contradicts those, it just puts numbers and city names on what was already an honest section.*
