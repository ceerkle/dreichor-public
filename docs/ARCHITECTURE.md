# dreichor — Architecture

This document defines the **non-negotiable architectural rules**
of the dreichor framework.

It is intentionally strict.
Architecture is not an implementation detail in dreichor —
it is the foundation of trust.

---

## Architectural Goal

The goal of dreichor’s architecture is to create
a **deterministic, auditable, and governance-first system**
for decisions under uncertainty.

This is achieved through:
- strict separation of responsibilities
- an immutable domain core
- governance by observation, not intervention

---

## CHOR — The Immutable Core

At the center of dreichor lies **CHOR**.

CHOR is the domain core and contains **only**:

- RAGE
- NOISE
- MEATSPACE

CHOR is deliberately minimal.
Its small size is a feature, not a limitation.

---

## The First and Unbreakable Rule

> **RAGE, NOISE, and MEATSPACE must remain strictly separated.**

This rule is absolute.

- Layers are executed in sequence
- No layer may assume responsibility of another
- No layer may correct or compensate for another
- Layers are aware of each other’s existence
- Layers do not know how the others are implemented

Violating this rule invalidates governance.

---

## Layer Responsibilities

### RAGE — Will

- Forms decisions deterministically
- Has no knowledge of execution, cost, or reality
- Produces intent, not outcome

### NOISE — Friction

- Observes deviation between will and outcome
- Makes uncertainty explicit
- Never optimizes or smooths behavior

### MEATSPACE — Reality

- Represents the external world
- Non-deterministic and uncontrollable
- Observable, never fully modelable

---

## What CHOR Must Never Contain

CHOR must never include:

- IO (network, filesystem, databases)
- Wall-clock time
- Randomness without explicit seeding
- Persistence logic
- Feature orchestration
- Governance rules
- UI or visualization

CHOR is pure domain logic.

---

## Governance Lives Outside CHOR

Governance is implemented as **vertical feature slices**
that observe CHOR behavior:

- trust levels
- gates
- proposals
- escalation logic
- replay and audit

Governance may:
- allow or deny execution
- warn or restrict autonomy
- build or reduce trust

Governance may never:
- change decisions produced by CHOR
- modify CHOR logic
- bypass CHOR execution order

---

## Dependency Rule

> **CHOR has no dependencies on features or adapters.**

Allowed:
features → CHOR
adapters → CHOR

Forbidden:
CHOR → features
CHOR → adapters

This rule enforces long-term stability and auditability.

---

## Determinism as a Contract

Determinism is not an optimization.
It is a contractual requirement.

Given identical inputs:
- CHOR must produce identical outputs
- Governance must reach identical decisions
- Replay must be exact

If this property is lost,
trust cannot be established.

---

## Architectural Invariant

> **CHOR is immutable.  
> Features may evolve.  
> Governance may adapt.  
> CHOR does not change to satisfy features.**

## Architectural Decisions

Key irreversible design decisions are documented separately
under `docs/decisions/`.

These decisions are binding and form the foundation
for auditability, determinism, and licensing.

This invariant protects dreichor’s core value.