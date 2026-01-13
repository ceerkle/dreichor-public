# dreichor — UI & Observability Boundaries (Step 38)

This document defines **what dreichor does and does not provide**
with respect to user interfaces, dashboards, and operational control.

It is binding.

This is not an implementation guide.
It is a **responsibility and expectation contract**.

---

## Purpose

dreichor is a **governance framework**, not an operational platform.

This document exists to ensure that:
- customers do not expect a UI that does not exist
- responsibility boundaries remain explicit
- audit, legal, and operational roles are not blurred

Clarity here prevents misuse later.

---

## Core Assertion

> **dreichor is headless.**

It exposes governance state.
It does not visualize it.
It does not control execution.
It does not provide operator interfaces.

This is intentional.

---

## What dreichor Explicitly Does NOT Provide

dreichor does **not** ship with:

- dashboards
- web UIs
- CLIs for operational control
- buttons or toggles
- start / stop mechanisms
- approval dialogs
- emergency kill switches
- visualization frameworks
- monitoring frontends

There is no:
- “Allow / Deny” button
- “Pause execution” control
- “Override governance” UI
- “Manual escalation” screen

If you are looking for these,
you are looking **outside** of dreichor by design.

---

## Why dreichor Does Not Provide a UI

This is not a missing feature.
It is an architectural constraint.

Reasons:

### 1. Governance Must Not Become Control

If dreichor shipped a UI, it would implicitly:
- influence operator behavior
- suggest intervention paths
- create perceived authority

This would violate:
- non-intervention principles
- audit separation
- legal responsibility clarity

---

### 2. UI Equals Liability

A provided UI would:
- imply operational responsibility
- imply compliance guarantees
- imply safety assurances

dreichor intentionally avoids this.

Governance is **observational**, not operational.

---

### 3. Every Organization Is Different

UI requirements differ by:
- industry
- regulation
- internal processes
- risk appetite

A generic UI would either:
- be insufficient, or
- be dangerously misleading

---

## What dreichor DOES Provide Instead

dreichor provides **read-only, deterministic artifacts**
specifically designed to be consumed by external systems.

Including:

- GovernanceReadAPI
- TrustLevel
- Gate summaries
- GovernanceExplanation (WHY)
- DecisionTrace (WHAT / WHERE)
- Replayable governance artifacts

These are:
- structured
- explicit
- stable
- audit-ready

They are intended to be:
- rendered
- visualized
- inspected
- logged

—but never controlled.

---

## Customer Responsibilities (Explicit)

If you integrate dreichor, **you** are responsible for:

- building your own UI (if desired)
- deciding how governance is visualized
- deciding who can see what
- deciding how governance outcomes affect execution
- implementing stop / pause / override logic (outside dreichor)

dreichor will not:
- stop your systems
- pause your pipelines
- block your infrastructure

Those decisions remain yours.

---

## Recommended UI Semantics (Non-Binding)

While dreichor does not ship a UI,
it is designed to support clear visual semantics.

Typical patterns include:

- Decision timelines
- Trust evolution graphs
- Gate status tables
- “Why / Why Not” explanation panels
- Replay comparison views

These are **examples**, not requirements.

---

## Audit & Compliance Perspective

From an audit standpoint:

- dreichor produces evidence
- customer systems enact decisions

This separation ensures:
- accountability remains with the operator
- governance logic is inspectable
- intervention paths are explicit and external

Auditors should never ask:
> “Why did dreichor stop the system?”

They should ask:
> “Why did the system act, given dreichor’s evaluation?”

---

## Final Assertion

> **dreichor does not govern people.  
> It governs decisions.**

It tells you:
- what was evaluated
- what was allowed
- what was denied
- why trust changed or did not

What you do with that information
is an explicit organizational choice.

If a UI suggests otherwise,
the integration is wrong.

---

End of document.