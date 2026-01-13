# ADR-008 — Framework Boundary & Implementing System Responsibility

## Status
Accepted

## Context

dreichor is intended to be used across domains:
- trading systems
- banking platforms
- insurance engines
- AI-driven decision systems

In such environments, it is critical to distinguish
between **governance logic** and **system operation**.

Without a strict boundary,
scope creep would turn dreichor into:
- a runtime platform
- an execution engine
- a domain-specific system

This would undermine universality and auditability.

---

## Decision

dreichor is a **governance framework**, not a runtime system.

dreichor provides:
- decision governance
- trust evaluation
- escalation logic
- deterministic explanations
- replay proof mechanisms

Implementing systems provide:
- execution (paper, live, dry-run)
- infrastructure
- availability guarantees
- failover and recovery
- operational controls

---

## Scope

The following are EXPLICITLY outside dreichor:

- execution modes (paper/live)
- simulation engines
- risk management
- capital allocation
- scheduling
- retries and failover
- monitoring and alerting

dreichor evaluates.
Others decide how to act.

---

## Consequences

### Positive

- Universal applicability
- Clean integration boundaries
- No domain leakage
- Clear licensing surface

### Constraints

- More responsibility for implementers
- No “out of the box” execution behavior

This is intentional.

---

## Explicit Non-Goals

dreichor is NOT:
- a trading system
- a banking platform
- an AI runtime
- an orchestration framework

---

## Architectural Assertion

> dreichor governs decisions.  
> It does not run systems.

If execution logic enters dreichor,
the framework has failed.