# Overview

This repository is a **public-safe architecture skeleton**. It captures the *shape* of a platform—components, trust boundaries, and operational concerns—without exposing private implementation details.

## Goals

- Provide a technical reviewer a fast, high-signal view of the platform
- Make key architectural **boundaries and invariants** explicit
- Show how the system is designed to be operable (telemetry, audits, change control)
- Demonstrate judgment in how tradeoffs are recorded and managed

## Non-goals

- Publishing production code or deployment manifests
- Sharing internal topology, routing, endpoints, or credentials
- Providing step-by-step exploitation guidance
- Documenting token economics or launch plans

## System at a glance

At a high level, the platform is described in separable layers:

1. **Interface layer**: clients and integrations
2. **Edge layer**: request normalization, authorization, abuse control
3. **Execution layer**: deterministic state transitions and business rules
4. **Validation layer**: verification and attestation boundaries
5. **Data plane**: durable state and event history
6. **Networking layer**: propagation, synchronization, reconciliation
7. **Operations layer**: observability, auditing, governance surface

See `architecture.md` and the diagrams in `../diagrams/`.

## Reading guide

- Start with `architecture.md` to understand boundaries and interfaces
- Then read `threat-model.md` for adversarial assumptions and mitigations
- Then `tradeoffs.md` for explicit “why” decisions
- `governance-and-compliance.md` explains operational constraints that shape design
