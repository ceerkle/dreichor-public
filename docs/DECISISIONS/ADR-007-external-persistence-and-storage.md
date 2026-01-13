# ADR-007 — External Persistence & Storage

## Status
Accepted

## Context

Governance systems often include:
- databases
- event stores
- configuration persistence
- stateful histories

Embedding storage inside a governance framework:
- couples it to infrastructure
- complicates audits
- restricts deployment models
- introduces hidden state

For regulated environments,
storage strategy is an architectural decision
that must remain under organizational control.

---

## Decision

dreichor SHALL NOT provide built-in persistence.

dreichor:
- operates on provided inputs
- produces deterministic outputs
- supports replay through explicit input sets

All storage concerns are external.

---

## Scope

dreichor does not include:
- databases
- event stores
- configuration storage
- secret management
- stateful history loading

Replay is achieved by:
- re-supplying governance inputs
- not by loading internal state

---

## Consequences

### Positive

- Infrastructure neutrality
- Simplified audits
- Easier integration into existing systems
- Clear ownership of data

### Constraints

- Implementing systems must manage storage
- Persistence quality affects replay quality

This is an explicit trade-off.

---

## Explicit Non-Goals

dreichor is NOT:
- a logging system
- an event store
- a configuration manager
- a data platform

---

## Architectural Assertion

> Governance must be stateless to be trusted.

Hidden state is hidden risk.

dreichor refuses both.