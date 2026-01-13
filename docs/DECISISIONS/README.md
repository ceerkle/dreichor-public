# dreichor — Architectural Decision Records (ADR Index)

This document provides an overview of all
**binding architectural decisions** in dreichor.

These decisions are **non-negotiable**.
They define the governance guarantees,
auditability, and scope boundaries of the framework.

If an implementation or proposal conflicts with any ADR,
the ADR takes precedence.

---

## What Are ADRs in dreichor?

Architectural Decision Records (ADRs) in dreichor:
- document irreversible design decisions
- define responsibility boundaries
- protect determinism and auditability
- serve as normative references for auditors, architects, and implementers

ADRs are not historical notes.
They are **active constraints**.

---

## ADR Overview

### ADR-001 — Governance Events in CHOR  
**File:** `ADR-001-governance-events-in-chor.md`

Defines canonical, domain-neutral `GovernanceEvent`s
as immutable, replayable records.

Purpose:
- shared language across layers
- audit and replay foundation

---

### ADR-002 — Explicit Governance Aggregation  
**File:** `ADR-002-governance-aggregation.md`

Separates gate evaluation from trust decisions.

Purpose:
- prevent implicit escalation
- ensure explicit, auditable trust logic

---

### ADR-003 — Trust Lifecycle & Escalation  
**File:** `ADR-003-trust-lifecycle-and-escalation.md`

Defines trust states, transitions, and escalation rules.

Key rule:
- **default no-promotion**
- promotions only via explicit rules

---

### ADR-004 — Deterministic Replay as Proof  
**File:** `ADR-004-deterministic-replay-as-proof.md`

Defines replay as a proof mechanism, not a debug tool.

Purpose:
- verifiable governance behavior
- regulator- and audit-ready evidence

---

### ADR-005 — Governance Explanation Model (WHY Layer)  
**File:** `ADR-005-governance-explanation-model.md`

Introduces deterministic, structured explanations
for governance outcomes.

Key rule:
- explanations are derived, not generated

---

### ADR-006 — Non-Intervention Principle  
**File:** `ADR-006-non-intervention-principle.md`

States that dreichor must never intervene in execution.

Purpose:
- legal clarity
- safe use in critical infrastructure

---

### ADR-007 — External Persistence & Storage  
**File:** `ADR-007-external-persistence.md`

Explicitly excludes storage and persistence from the framework.

Purpose:
- infrastructure neutrality
- no hidden state

---

### ADR-008 — Framework Boundary & Implementing System Responsibility  
**File:** `ADR-008-framework-boundaries.md`

Defines dreichor as a governance framework,
not a runtime or execution system.

Purpose:
- universality
- clean licensing and adoption

---

## Architectural Closure

Together, these ADRs define a **closed architecture**.

After ADR-008:
- CHOR is immutable
- governance semantics are fixed
- responsibility boundaries are explicit

Future work must:
- respect all ADRs
- extend via features, adapters, or configuration
- never weaken determinism or auditability

---

## Final Assertion

> If a change requires breaking an ADR,
> it is not an extension —
> it is a different system.

dreichor’s value lies in these constraints.