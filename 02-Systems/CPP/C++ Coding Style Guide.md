## Naming Conventions

| Entity | Convention | Example |
|---------|------------|---------|
| Namespace | `snake_case` | `pricing`, `market_data` |
| Class | `PascalCase` | `OrderBook` |
| Struct | `PascalCase` | `TickData` |
| Enum | `PascalCase` | `Side` |
| Enum Value | `PascalCase` | `Side::Buy` |
| Concept | `PascalCase` | `Numeric` |
| Type Alias / `using` | `PascalCase` | `using PriceVec = std::vector<Price>;` |
| Global Variable | `g_name` | `g_clock`, `g_logger` |
| Global Static Variable | `s_name` | `s_instanceCount` |
| Global Static Function | `s_name` | `s_initialize()` |
| Free Function | `snake_case` | `load_config()` |
| Private Variable | `m_name` | `m_bidPrice` |
| Private Function | `m_name` | `m_recalculate()` |
| Protected Variable | `p_name` | `p_capacity` |
| Protected Function | `p_name` | `p_resize()` |
| Public Variable | `camelCase` | `lastTradePrice` |
| Public Function | `camelCase` | `getMidPrice()` |
| Atomic / Shared-State Variable | `a_name` | `a_sequenceNumber` |
| Constant | `UPPER_CASE` | `MAX_ORDER_SIZE` |
| Macro | `UPPER_CASE` | `LIKELY(x)` |
| Template Parameter | `PascalCase` | `typename PriceType` |

---

# Variables

## Member Variables

### Private

```cpp
class OrderBook
{
private:
    double m_bidPrice;
    size_t m_depth;
};
```

### Protected

```cpp
class Strategy
{
protected:
    int p_lookback;
};
```

### Public

```cpp
struct Config
{
public:
    int windowSize;
    double tickSize;
};
```

### Atomics / Shared State

Cross-thread state gets its own prefix so a reviewer can spot synchronization
concerns without reading the type.

```cpp
class Sequencer
{
private:
    std::atomic<uint64_t> a_sequenceNumber{0};
};
```

---

# Global Variables

```cpp
Clock g_clock;
Logger g_logger;
```

---

# Static Globals

```cpp
static int s_instanceCount = 0;

static void s_initialize();
```

---

# Local Variables

**Recommended:** Use `camelCase` everywhere.

```cpp
void load_config()
{
    int retryCount;
    double totalNotional;
}
```

Avoid changing naming style based on location.

❌

```cpp
void foo()
{
    int retry_count;
}
```

Using one convention everywhere is easier to read.

---

# Functions

## Free Functions

```cpp
void load_config();
void connect_feed();
void publish_tick();
```

## Member Functions

```cpp
class OrderBook
{
public:
    void addOrder();
    void cancelOrder();

private:
    void m_rebuildLevels();
};
```

---

# Constants

```cpp
constexpr int MAX_ORDER_SIZE = 10'000;
constexpr double TICK_SIZE = 0.01;
```

Prefer scoped constants (namespace or `static constexpr` class members) over
free-floating globals to avoid polluting the global namespace and to keep
constants co-located with the code that uses them.

---

# Classes / Structs / Enums

```cpp
class OrderBook;
struct TickData;

enum class Side
{
    Buy,
    Sell
};
```

---

# Namespaces

Organize namespaces around **domain modules**, not technical layers. This
keeps the codebase navigable as it scales and mirrors how a quant system is
actually reasoned about (pricing vs. risk vs. execution vs. data).

```cpp
namespace pricing
{
}

namespace risk
{
}

namespace market_data
{
}

namespace execution
{
}

namespace backtest
{
}
```

Avoid `using namespace` in headers. It is acceptable in `.cpp` files for
well-scoped, short-lived convenience (e.g. `using namespace std::chrono;`
inside a single function).

---

# File Names

```
order_book.cpp
order_book.hpp

market_data_feed.cpp
market_data_feed.hpp

risk_engine.cpp
risk_engine.hpp
```

---

# Include Guards

Use `#pragma once` as the default — it is supported by every compiler this
project targets and eliminates the boilerplate/maintenance cost of manually
naming guard macros.

```cpp
#pragma once
```

If a header may ever be consumed by a toolchain without reliable
`#pragma once` support (rare, but possible for exported public SDK headers),
fall back to a fully-qualified traditional guard instead:

```cpp
#ifndef QUANTLIB_PRICING_OPTION_HPP
#define QUANTLIB_PRICING_OPTION_HPP

// ...

#endif // QUANTLIB_PRICING_OPTION_HPP
```

Guard names should be `PROJECT_MODULE_FILE_HPP` to guarantee uniqueness
across the whole codebase.

---

# Indentation

- 4 spaces
- No tabs

---

# Braces

```cpp
if (condition)
{
    do_work();
}
```

Never:

```cpp
if (condition) {
    do_work();
}
```

---

# Pointers & References

```cpp
int* ptr;
const char* str;

std::unique_ptr<Order> order;
std::shared_ptr<MarketDataFeed> feed;

void process(const Order& order);
int& value = number;
```

Ownership must always be explicit:

- `std::unique_ptr<T>` — sole ownership, default choice.
- `std::shared_ptr<T>` — only when shared lifetime is a genuine requirement
  (e.g. shared across async callbacks). Avoid as a default.
- Raw pointer / reference — non-owning observation only. Never use a raw
  pointer to signal ownership transfer.

---

# Const Correctness

```cpp
void draw() const;

const std::string& getName() const;
```

Mark everything `const` by default; remove `const` only when mutation is
required. This applies to member functions, parameters, and locals alike.

---

# Casting

Never use C-style casts. Always use the named cast that matches intent:

```cpp
static_cast<double>(count);        // well-defined numeric/type conversions
dynamic_cast<Derived*>(basePtr);   // polymorphic downcasts (avoid in hot path)
const_cast<T&>(constRef);          // rare, justify in a comment
reinterpret_cast<uint8_t*>(ptr);   // low-level reinterpretation only
```

`reinterpret_cast` and `const_cast` require a one-line comment explaining
why the cast is safe.

---

# Auto

Use only when the type is obvious from context.

Good

```cpp
auto it = book.find(orderId);
auto lock = std::lock_guard(m_mutex);
```

Avoid

```cpp
auto price = 10;
auto result = compute();
```

---

# Header Order

```cpp
// Standard Library
#include <vector>
#include <chrono>

// Third-party
#include <fmt/core.h>

// Project
#include "pricing/option.hpp"
#include "market_data/tick.hpp"
```

Forward-declare where possible instead of including, especially in headers,
to keep compile times manageable as the codebase grows.

---

# Class Layout

```cpp
class OrderBook
{
public:
    OrderBook();

    void addOrder();
    void cancelOrder();

public:
    int depth;

protected:
    void p_resize();

protected:
    int p_capacity;

private:
    void m_rebuildLevels();

private:
    double m_bidPrice;
    double m_askPrice;
};
```

---

# Numerical Precision & Money

Correctness of numeric representation is a first-class concern in quant
code — silent precision loss is a correctness bug, not a style nit.

- Never represent money as `float`/`double`. Use an integer tick/cent
  representation (`int64_t` ticks scaled by a known tick size) or a fixed-
  point decimal type.
- Never compare floating-point values with `==`. Use an explicit epsilon or
  a relative-tolerance comparison, and name the tolerance constant.
- Be explicit about `float` vs `double` at every API boundary; do not let
  implicit narrowing conversions happen silently — enable
  `-Wconversion -Wshadow` and treat warnings as errors.
- Prefer `std::chrono` types (with explicit clock and duration precision,
  e.g. nanoseconds) over raw integer timestamps. Never mix epoch units
  (ms/us/ns) without a type-enforced distinction.

```cpp
constexpr double PRICE_EPSILON = 1e-9;

bool pricesEqual(double a, double b)
{
    return std::abs(a - b) < PRICE_EPSILON;
}

using Nanoseconds = std::chrono::nanoseconds;
using TimePoint   = std::chrono::time_point<std::chrono::system_clock, Nanoseconds>;
```

---

# Performance & Memory

Hot-path code (tick processing, order matching, pricing loops) follows
stricter rules than cold-path code (config loading, reporting, CLI tools).
Mark hot-path sections explicitly in comments.

- No heap allocation in the hot path. Pre-allocate, use object pools, or
  arena/bump allocators; reuse buffers instead of allocating per-message.
- No exceptions in the hot path. Reserve `try`/`catch` for cold paths
  (startup, config, non-critical I/O); use `std::expected<T, Error>` (or an
  equivalent result type) for recoverable errors in latency-sensitive code.
- No virtual dispatch in the innermost hot loop; prefer templates / CRTP /
  `if constexpr` for compile-time polymorphism where latency matters.
- Favor data-oriented, cache-friendly layouts (Structure-of-Arrays) for
  large collections that are iterated frequently, over Array-of-Structures.
- Avoid `std::shared_ptr` in the hot path — atomic refcounting has real
  cost. Use raw/observer pointers into pools instead.
- Mark single-argument constructors `explicit` unless implicit conversion
  is intentional; this avoids accidental temporary allocations.

---

# Concurrency

- Use `std::atomic<T>` (prefixed `a_`) for cross-thread counters/flags;
  document the memory order explicitly rather than relying on the default
  `seq_cst` when it matters for performance.
- Prefer single-producer/single-consumer lock-free queues for pipeline
  stages (feed handler → strategy → execution) over shared-mutex designs.
- Name threads (`pthread_setname_np` / platform equivalent) so profiler and
  crash-dump output is immediately readable.
- Any shared mutable state must be documented at its declaration: who
  writes, who reads, and under what synchronization.

---

# Error Handling

- Cold path: exceptions are acceptable and preferred for unrecoverable
  startup/config errors.
- Hot path: no exceptions. Use a result/error-code type
  (`std::expected<T, ErrorCode>` or a project `Result<T>`), and make
  failure paths as branch-predictable as possible.
- Never use exceptions for expected control flow (e.g. "order not found"
  is not exceptional in an order book — return `std::optional`).
- All error enums are `enum class` with explicit, descriptive values —
  never bare `int` error codes.

---

# Testing & Benchmarking

- Unit tests live under `tests/`, mirroring the `src/` directory structure.
  File name: `order_book_test.cpp` for `order_book.cpp`.
- Use a standard framework (GoogleTest) with table-driven tests for
  numerical edge cases (rounding, overflow, zero/negative inputs).
- Tests must be deterministic: seed all RNGs explicitly, never depend on
  wall-clock time — inject a `Clock` interface instead.
- Any code touching pricing, risk, or PnL calculations requires a
  regression test with a known reference value.
- Performance-critical code requires a companion benchmark (Google
  Benchmark) checked in under `benchmarks/`, so regressions are caught in
  CI, not production.

---

# Static Analysis & Compiler Hygiene

- Build with `-Wall -Wextra -Wpedantic -Wconversion -Wshadow
  -Werror` as the default project configuration.
- Run `clang-tidy` and `clang-format` in CI; formatting is enforced by
  tooling, not code review.
- Run `AddressSanitizer` / `UndefinedBehaviorSanitizer` in the standard
  test CI job; run `ThreadSanitizer` on any concurrency-touching module.
- Mark all overridden virtual functions with `override`, and destructors
  of polymorphic base classes `virtual`.

---

# Project Structure

```
project/
├── include/<module>/      # public headers, one dir per domain module
├── src/<module>/          # implementation, mirrors include/
├── tests/<module>/        # unit tests, mirrors src/
├── benchmarks/<module>/   # perf benchmarks for hot-path code
├── tools/                 # CLIs, offline scripts
├── third_party/           # vendored or pinned external deps
└── CMakeLists.txt
```

Each domain module (`pricing`, `risk`, `market_data`, `execution`,
`backtest`) is a self-contained library target with its own `CMakeLists.txt`,
minimizing rebuild blast radius as the codebase scales.

---

# Documentation

Public headers use Doxygen-style comments on every class and public
function; document units for any numeric parameter or return value
(price, notional, ticks, nanoseconds) explicitly, since unit ambiguity is a
recurring source of quant bugs.

```cpp
/// Returns the mid price in the instrument's quoted currency.
/// @return mid price, or std::nullopt if the book is empty.
std::optional<double> getMidPrice() const;
```

---

# Summary

| Prefix | Meaning |
|---------|----------|
| `g_` | Global |
| `s_` | Global static |
| `m_` | Private member |
| `p_` | Protected member |
| `a_` | Atomic / cross-thread shared state |

| Style | Used For |
|--------|----------|
| `PascalCase` | Classes, Structs, Enums, Concepts, type aliases |
| `camelCase` | Public members, local variables |
| `snake_case` | Free functions, namespaces, file names |
| `UPPER_CASE` | Constants, macros |

---

# Notes

- Prefer `constexpr` over `#define` for constants.
- Minimize the use of global variables (`g_`).
- Use `static` globals (`s_`) only for translation-unit-private state.
- Favor composition over inheritance where practical.
- Keep headers lightweight; include only what you need, forward-declare
  where possible.
- Use RAII for resource management, always.
- Mark overridden virtual functions with `override`.
- Mark single-argument constructors `explicit` unless implicit conversion
  is intended.
- Never represent money as floating point; never compare floats with `==`.
- No heap allocation, exceptions, or virtual dispatch in the hot path.
- Every domain module is its own library target — structure the codebase
  for independent compilation and testing as it scales.
- Treat compiler warnings as errors; let tooling (clang-format,
  clang-tidy, sanitizers) enforce style and correctness, not memory.