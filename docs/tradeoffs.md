# Tradeoffs

This system is designed under real-world constraints. This document captures **explicit tradeoffs** and why alternatives were not selected.

## Determinism vs throughput
- Preference: deterministic processing and auditable state transitions
- Tradeoff: some performance optimizations are deferred until correctness is proven

## Modularity vs simplicity
- Preference: clear boundaries between edge, execution, validation, and operations
- Tradeoff: more components, but lower coupling and easier reasoning

## Policy flexibility vs attack surface
- Preference: a policy surface that can adapt to new constraints
- Tradeoff: policy systems can be abused if overly dynamic, so changes are controlled and audited

## Privacy vs auditability
- Preference: data minimization and controlled visibility
- Tradeoff: auditability requires sufficient evidence; architecture must support both safely

## Build velocity vs long-term operability
- Preference: operational realism (telemetry, runbooks, migration posture) is built early
- Tradeoff: slower initial feature delivery, but fewer production surprises

## Public communication vs sensitive detail
- Preference: share the structure and the reasoning
- Tradeoff: private implementation and exact mechanics are intentionally not published
