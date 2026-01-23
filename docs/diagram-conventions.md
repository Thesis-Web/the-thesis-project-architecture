// TARGET: arch docs/diagram-conventions.md

# Diagram Conventions

This document defines the conventions used across architectural and system diagrams in this repository.
The goal is consistency, clarity, and the ability to reason about system behavior without relying on implementation details.

---

## General Principles

- Diagrams describe **structure and intent**, not deployment specifics
- All diagrams are **conceptual**, not operational
- Visual elements map to **logical responsibilities**, not services or hosts
- Absence of detail is intentional where disclosure is inappropriate

---

## Component Representation

- Boxes represent **bounded responsibilities**
- Nested boxes indicate **composition**, not ownership
- Lines indicate **directional dependency**, not transport protocols
- Bidirectional arrows are avoided unless symmetry is required

---

## Data Flow Diagrams

- Arrows represent **logical flow order**, not timing guarantees
- Validation steps are shown explicitly
- Failure paths are implied by sequence interruption rather than alternate flows
- No retries, queues, or buffers are shown unless central to the concept

---

## System Context Diagrams

- External actors are treated as **untrusted by default**
- Trust boundaries are conceptual, not network-defined
- Regulatory or governance entities are modeled as participants, not overlays

---

## What Diagrams Intentionally Exclude

- Hostnames, regions, or infrastructure providers
- Authentication mechanisms
- Cryptographic primitives
- Internal service names
- Performance characteristics

These exclusions are deliberate and do not imply absence in the underlying system.

---

## Reading Guidance

Diagrams should be read alongside their accompanying documentation.
No single diagram is intended to stand alone as a complete system description.
