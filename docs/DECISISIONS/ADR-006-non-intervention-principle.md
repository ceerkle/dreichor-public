# ADR-006 — Non-Intervention Principle

## Status
Accepted

## Context

dreichor evaluates decisions that may affect
critical systems, capital, access, or operations.

In such environments, **active intervention**
by a governance framework (e.g. stopping systems,
killing processes, or enforcing behavior)
introduces significant legal, operational,
and organizational risk.

In particular:
- automated stops may violate operational obligations
- intervention blurs responsibility boundaries
- liability becomes unclear
- availability guarantees may be compromised

---

## Decision

dreichor SHALL NEVER actively intervene in execution.

dreichor:
- evaluates decisions
- emits governance judgments
- exposes trust state and explanations

dreichor does NOT:
- stop systems
- block processes
- kill executions
- enforce behavior
- override infrastructure

All enforcement actions are the responsibility
of the implementing system or organization.

---

## Scope

This principle applies to:
- governance evaluation
- escalation logic
- trust transitions
- explanations
- replay mechanisms

It applies across all domains
(financial, industrial, AI, critical infrastructure).

---

## Consequences

### Positive

- Clear responsibility boundaries
- Legal and regulatory clarity
- Safe adoption in critical environments
- No hidden control paths

### Constraints

- Implementing systems must decide
  how to react to governance outcomes
- dreichor cannot guarantee safety by force

This is intentional.

---

## Explicit Non-Goals

dreichor is NOT:
- a control plane
- a safety interlock
- an emergency shutdown system
- an execution supervisor

---

## Architectural Assertion

> Governance must judge — not act.

If dreichor intervenes,
it becomes responsible for outcomes.

That responsibility is explicitly refused.