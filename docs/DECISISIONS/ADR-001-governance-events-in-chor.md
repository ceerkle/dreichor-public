# dreichor — Architectural Decisions

This document records irreversible or high-impact architectural decisions
made in the design of dreichor.

These decisions are considered **binding**.
Future changes must be justified explicitly and documented here.

---

## ADR-001: Governance Events as CHOR Contracts

### Status
Accepted

### Context

dreichor is a governance framework whose primary value lies in:
- auditability
- determinism
- explainable trust evaluation

Governance decisions are based on observed facts.
These facts must be represented in a way that is:
- domain-neutral
- non-interpretive
- immutable
- replayable

A design decision was required regarding the ownership of these facts.

---

### Decision

**GovernanceEvents are defined as contracts in `/chor/chor`.**

They are not owned by the governance layer.

---

### Rationale

1. **Separation of Fact and Interpretation**

   Governance evaluates behavior.
   It must not define what constitutes reality.

   By placing GovernanceEvents in CHOR:
   - events represent factual observations only
   - governance becomes a pure interpreter

2. **Audit Integrity**

   Auditors require a clear distinction between:
   - what happened
   - how it was evaluated
   - what action was taken

   CHOR represents observable reality.
   Governance represents judgment.

3. **Licensing and Product Boundaries**

   dreichor is licensed primarily as a governance framework.

   Placing GovernanceEvents in CHOR ensures:
   - governance can be licensed independently
   - customers retain ownership of their event streams
   - trust evaluation remains portable and reproducible

4. **Replay and Determinism**

   Events defined in CHOR are:
   - deterministic inputs
   - independent of policy evolution
   - suitable for historical replay

5. **Architectural Neutrality**

   CHOR is immutable by design.
   It contains no policies, logic, or execution assumptions.

   Governance must not be able to alter or reinterpret event semantics.

---

### Consequences

- Governance may only **consume** GovernanceEvents.
- Governance may not:
  - redefine events
  - filter events implicitly
  - mutate event data
- All governance behavior must remain explainable
  purely in terms of CHOR-level events.

---

### Alternatives Considered

**Defining GovernanceEvents in `/governance`**

Rejected because it:
- collapses fact and interpretation
- weakens auditability
- creates implicit authority in governance
- complicates licensing boundaries

---

### Enforcement

- No governance component may introduce its own event model.
- Violations of this decision constitute an architectural breach.

---

## Closing Statement

dreichor treats reality as immutable.

Governance earns trust by interpreting reality —
not by defining it.