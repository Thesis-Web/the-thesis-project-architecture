
---

#  `data-flow.md`

**Intent:** Show **runtime reasoning, event flow, and failure awareness**  
**Style:** Node.js + async flows + Mermaid sequence

```md
// TARGET: diagrams/data-flow.md

# Data Flow

This document outlines how data moves through the system during a typical operation,
emphasizing **order, validation, and failure containment**.


---

## References

- [Architecture Overview](../docs/architecture.md)
- [Diagram Conventions](../docs/diagram-conventions.md)
- [Glossary](../docs/glossary.md)

---

## Design Constraints

- All flows must be observable
- Validation occurs before mutation
- No implicit side effects
- Failure must be local

---

## Conceptual Flow (Node / Async)

```ts

async function handleInput(input: ExternalInput): Promise<Result> {
  const normalized = normalize(input);
  const validated = await validate(normalized);

  if (!validated.ok) {
    return reject(validated.reason);
  }

  const executed = await execute(validated.value);
  await attest(executed);

  return commit(executed);
}
```
Each step is:

Explicit
	- Awaited
	- Observable
	

###  Runtime Sequence
	- sequenceDiagram
  		- participant Client
  		- participant Execution
  		- participant Validation
 		- participant Attestation
  		- participant Storage

  		- Client->>Execution: submit(input)
  		- Execution->>Validation: validate(input)
  		- Validation-->>Execution: ok
  		- Execution->>Attestation: attest(result)
  		- Attestation-->>Execution: proof
  		- Execution->>Storage: commit(result)

Failure Behavior

- Validation failure halts execution

- Attestation failure prevents commit

- Storage failure does not retroactively mutate state

- The system prefers explicit rejection over silent correction.


---
