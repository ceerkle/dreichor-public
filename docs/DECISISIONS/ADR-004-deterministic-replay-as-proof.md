# ADR-004 — Deterministic Replay as Proof

## Status
Accepted

## Context

Governance decisions in dreichor affect
whether systems are allowed to act autonomously.

In regulated or safety-critical environments,
it is insufficient to claim that governance logic
*would have* behaved correctly.

Auditors, operators, and regulators require
**verifiable proof** that governance decisions:

- are deterministic
- can be reproduced
- are free from implicit behavior
- do not depend on runtime conditions

Traditional debugging or logging
is insufficient for this purpose.

---

## Decision

dreichor defines **deterministic replay**
as a **primary proof mechanism**, not as a debugging aid.

A replay is defined as:
- a fixed, explicit input set
- deterministic governance evaluation
- a hard-failing comparison against expected outcomes

Replay results must be:
- identical across runs
- independent of wall-clock time
- independent of environment state
- independent of execution side effects

Replay is considered **authoritative evidence**
of governance behavior.

---

## Scope

Deterministic replay applies to:
- governance aggregation
- escalation rules
- trust transitions
- governance explanations

Replay does **not** apply to:
- execution systems
- infrastructure behavior
- external services
- adapters

---

## Consequences

### Positive

- Governance behavior is auditable
- Disputes can be resolved objectively
- Regulatory review is simplified
- Trust decisions are provable, not asserted

### Constraints

- Replay inputs must be explicitly curated
- Governance logic must remain deterministic
- No hidden state is permitted

---

## Explicit Non-Goals

Replay is **not**:
- a debugging convenience
- a performance optimization tool
- a simulation of reality
- a substitute for monitoring

Replay exists solely to prove
that governance decisions are correct,
stable, and reproducible.

---

## Architectural Assertion

> If a governance decision cannot be replayed,
> it cannot be trusted.

Deterministic replay is a **hard requirement**
for governance validity in dreichor.