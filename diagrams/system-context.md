
---

#  `system-context.md`

**Intent:** Show **boundary thinking, trust zones, and integration awareness**  
**Style:** React mental model + context providers + Mermaid

```md
// TARGET: diagrams/system-context.md

# System Context

This document describes the system as a **bounded context** interacting with external actors.
The emphasis is on **trust boundaries**, not features.

---

## References

- [Architecture Overview](../docs/architecture.md)
- [Diagram Conventions](../docs/diagram-conventions.md)
- [Glossary](../docs/glossary.md)

---

## Contextual Model (React-Inspired)

```ts
type SystemContext = {
  inputs: ExternalInput[];
  outputs: VerifiedOutput[];
  policies: ActivePolicySet;
};

function SystemProvider({ context }: { context: SystemContext }) {
  return (
    <Infrastructure>
      <Execution context={context}>
        <Validation />
      </Execution>
    </Infrastructure>
  );
}
```
This model emphasizes:

- Composition over inheritance

- Context propagation

- Explicit dependency injectio

### External Relationships

graph TD
  User --> System
  System --> ExternalServices
  System --> RegulatoryInterfaces

  RegulatoryInterfaces --> System

### Trust Boundaries

External input is always untrusted

Internal state is always validated

External systems are treated as probabilistic

The system assumes hostile or degraded conditions by default.

### Summary

This context model allows the system to scale integrations without leaking assumptions or authority across boundaries.


---
