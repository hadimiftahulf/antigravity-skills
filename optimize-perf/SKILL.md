---
name: optimize-perf
description: Systematic performance tuning workflow to identify bottlenecks in Database, Backend, and Frontend layers. Includes static profiling for N+1, sync IO, and memory bloat.
---
# Optimize Performance (The Racer 🏎️)

Merged: `performance-profiler` + `optimize-perf`.

## When to Activate
- User mentions: "slow", "optimize", "performance", "benchmark", "N+1", "memory".

## Phase 1: Profiling (formerly performance-profiler)
Detect anti-patterns before optimizing:
1.  **Database**: N+1 queries, missing indexes, full table scans, unbounded queries.
2.  **Backend**: Synchronous IO in request cycle, blocking calls, missing caching.
3.  **Frontend**: Large bundle size, unoptimized images, excessive re-renders, layout thrashing.
4.  **Memory**: Object retention, circular references, unbounded lists.

## Phase 2: Optimization
After profiling, apply fixes:
1.  **Database**: Add indexes, eager loading, query optimization, pagination.
2.  **Backend**: Async processing, queue jobs, Redis/Memcached caching, connection pooling.
3.  **Frontend**: Code splitting, lazy loading, image optimization, memoization.

## Rules
- Profile FIRST, optimize SECOND. Never guess.
- Measure before and after. Quantify improvement.
- One optimization at a time to isolate impact.

## Cost: High (Explicit Trigger Required)
