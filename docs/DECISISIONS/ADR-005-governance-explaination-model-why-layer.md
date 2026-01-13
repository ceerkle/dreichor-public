# ADR-005 — Governance Explanation Model (WHY Layer)

## Status
Accepted

## Context

Governance decisions that affect autonomy
must be understandable by humans.

Without explanations, governance becomes opaque,
even if it is technically correct.

However, traditional explanations often rely on:
- heuristics
- free-form text
- inferred intent
- post-hoc interpretation

These approaches introduce ambiguity
and undermine auditability.

---

## Decision

dreichor introduces a **deterministic explanation model**
for governance outcomes.

Explanations are:
- derived from observable governance data
- structurally defined
- deterministic
- replayable

Explanations are **not generated**.
They are **constructed** from facts.

---

## Design Principles

### 1. Derived, Not Generated

Explanations may only reference:
- GovernanceEvents
- GateResults
- escalation rules
- trust transitions
- explicit configuration

No inference.
No summarization.
No probabilistic language.

---

### 2. Structure Before Text

Explanations are machine-structured first.

Human-readable representations
are projections of structured data,
not the source of truth.

---

### 3. Explicit Absence

If trust is not escalated,
the explanation must state **why not**.

Missing evidence is itself evidence.

Implicit promotion is forbidden.

---

## Scope

The explanation model applies to:
- governance evaluation results
- trust transitions
- escalation outcomes

It does not apply to:
- execution logic
- domain semantics
- business interpretation
- operator intent

---

## Consequences

### Positive

- Governance decisions become explainable
- Audits can focus on facts, not interpretation
- Operators can understand restrictions
- Trust evolution becomes transparent

### Constraints

- No natural language generation
- No hidden reasoning
- No contextual enrichment

---

## Explicit Non-Goals

The explanation model does **not**:
- justify decisions
- defend outcomes
- assess correctness
- assign blame

It exposes facts only.

---

## Architectural Assertion

> Explanations do not justify decisions.  
> They expose them.

If an explanation is uncomfortable,
the decision was already wrong.