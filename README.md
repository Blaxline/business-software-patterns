# Business software patterns

Patterns for designing reliable software around real business operations.

Business software becomes difficult when the real operation contains rules, exceptions, approvals, integrations, state changes, human judgment and long-running work that cannot be represented cleanly by generic CRUD.

This repository collects patterns for modeling and implementing those situations without flattening the business into simplistic software.

The focus is not frameworks or vendor-specific architecture.

The focus is the operating reality the software must represent.

---

## Why this repository exists

Most operational complexity does not live in individual screens or database tables.

It lives in things like:

- multi-stage approvals
- exception paths
- ownership and authority
- long-running processes
- asynchronous work
- external-system dependencies
- retries and failure recovery
- auditability
- changing business rules
- human judgment
- operational visibility

These concerns appear repeatedly across business systems, regardless of industry or technology stack.

The goal of this repository is to document patterns that make those systems easier to reason about, operate and evolve.

---

## Pattern library

### Workflow and state

- Long-running workflows
- Explicit process state
- State transitions
- Timers and deadlines
- Resumable processes
- Workflow versioning

### Rules and decisions

- Business rules
- Conditional routing
- Decision tables
- Approval thresholds
- Human-in-the-loop decisions
- Exception handling

### Authority and accountability

- Process ownership
- Role-based authority
- Delegation
- Multi-stage approvals
- Separation of duties
- Audit trails

### Integrations and reliability

- Integration boundaries
- Idempotent operations
- Retries and backoff
- External dependency failure
- Webhook processing
- Synchronization strategies

### Operational visibility

- Business events
- Process observability
- Operational metrics
- Exception monitoring
- Auditability
- Value signals

### AI-assisted operations

- AI as decision support
- Human approval boundaries
- Structured model output
- Tool execution boundaries
- AI failure handling
- Model-independent business rules

---

## How each pattern is documented

Each pattern should answer the same questions:

### Problem

What recurring operational problem does this pattern address?

### When to use it

What conditions make the pattern appropriate?

### When not to use it

What simpler alternative should be preferred when possible?

### Model

How should the business concept be represented?

### Implementation considerations

What technical concerns matter when implementing it?

### Failure modes

How does this pattern commonly break in production?

### Example

A concrete but generalized example of the pattern in use.

---

## Design principles

These patterns follow a few principles.

### Business reality before software abstraction

The model should represent how the operation actually works rather than forcing the business into an arbitrary software structure.

### Explicit state beats hidden coordination

Important status, ownership, decisions and exceptions should exist in the system rather than only in email, chat or human memory.

### Simple before distributed

Start with the simplest architecture that satisfies the reliability, isolation and evolution requirements.

### Integrate before replace

Existing systems of record should remain in place when they already perform their role well.

### Observable by design

Important state changes should produce evidence that makes the operation understandable after launch.

### Human judgment stays explicit

Automation should remove repetition without hiding where human authority, ambiguity or accountability still matter.

### Design for change

Business rules, workflows and integrations will evolve. The system should make those changes understandable and controllable.

---

## Repository structure

```text
patterns/
├── workflow/
├── decisions/
├── approvals/
├── exceptions/
├── integrations/
├── reliability/
├── observability/
├── auditability/
└── ai-assisted-operations/

examples/
diagrams/
```

---

## Contributing

This repository is being developed incrementally from recurring patterns found in real business software.

Patterns should be:

- generally applicable
- implementation-aware
- explicit about tradeoffs
- grounded in operational reality
- independent of unnecessary framework choices

A pattern should not be added simply because an architecture technique exists.

It should solve a recurring business-software problem.

---

## About Blaxline

[Blaxline](https://blaxline.com) designs, builds, operates and evolves custom business software for important operations that standard tools no longer fit.

We work from the operation itself: its people, rules, decisions, exceptions, data and systems.

This repository reflects part of the engineering thinking behind that work.

---

<sub>Maintained by Blaxline · Intelligence. By design.</sub>
