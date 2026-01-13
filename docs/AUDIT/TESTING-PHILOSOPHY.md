# dreichor — Testing Philosophy

This document defines the **testing philosophy**
of the dreichor framework.

Testing in dreichor is not about coverage.
It is about **proof**.

---

## Normative Basis

This testing philosophy is **normative**.

It derives directly from the following architectural decision:

- **ADR-004 — Deterministic Replay as Proof**

ADR-004 establishes deterministic replay as the primary mechanism
for verification, auditability, and trust validation in dreichor.

As a consequence:
- tests are not written to increase coverage
- tests are not used as debugging tools
- tests do not assert internal implementation details

All testing exists to **prove** that governance behavior
is deterministic, replayable, and auditable.

This document does not introduce a new testing strategy.
It formalizes the **required implications of ADR-004**.

---

## Core Principle

> **If behavior cannot be replayed deterministically,  
> it cannot be trusted.**

All tests exist to demonstrate:
- determinism
- reproducibility
- explicit responsibility boundaries

---

## What Testing Is in dreichor

Testing in dreichor means:

- proving that identical inputs produce identical outputs
- proving that governance decisions are replayable
- proving that explanations and traces are stable
- proving that configuration does not introduce implicit behavior

Tests are **evidence**, not safety nets.

---

## What Testing Is NOT

Testing in dreichor is **not**:

- unit test coverage maximization
- mocking-based behavior simulation
- probabilistic or fuzzy validation
- time-dependent assertions
- environment-dependent assertions

If a test depends on:
- wall-clock time
- randomness
- execution-order side effects
- hidden or mutable state

it is invalid.

---

## Determinism First

All valid tests must satisfy:

- identical inputs
- identical configuration
- identical ordering

Result:
- identical outputs
- identical explanations
- identical traces

Any deviation is a **hard failure**.

---

## Replay as the Primary Test Mechanism

Replay is the canonical testing method.

A valid test demonstrates that:
- governance artifacts can be persisted
- persisted artifacts can be replayed
- replay produces identical governance outcomes

Replay is **not a debug tool**.
Replay is **proof**.

---

## Categories of Tests

### 1. Replay Proofs (Primary)

Located under:

```code
demos/replay/
demos/configuration/
demos/persistence/
```

Characteristics:
	•	no mocks
	•	no stubs
	•	no test runners
	•	hard failure on mismatch

These tests prove:
	•	determinism
	•	auditability
	•	correctness under replay

⸻

## 2. Structural Assertions (Secondary)

Used sparingly to assert:
	•	invariant violations
	•	invalid configuration rejection
	•	forbidden trust transitions

These tests:
	•	fail loudly
	•	never auto-correct
	•	never infer intent

⸻

## 3. Documentation-Backed Demonstrations

Demos act as executable documentation.

They show:
	•	how governance works
	•	how configuration is applied
	•	how explanations and traces are produced

If documentation and demo diverge,
the demo is wrong.

⸻

## Why There Is No Traditional Test Suite

Traditional unit tests:
	•	isolate components artificially
	•	rely on mocks
	•	hide emergent behavior

dreichor explicitly rejects this model.

Governance is about system behavior,
not isolated functions.

⸻

## CI Implications

A valid CI run must:
	•	compile successfully
	•	execute all demos
	•	fail on any nondeterministic output
	•	fail on any divergence across runs

Coverage metrics are irrelevant.

⸻

## Auditor Perspective

An auditor should be able to:
	•	run demos locally
	•	inspect outputs
	•	replay decisions
	•	reach identical conclusions

No special tooling required.
No privileged access required.

⸻

## Final Assertion

If a test cannot be replayed,
it is not a test.

dreichor is trusted
not because it passes tests,
but because it produces
the same answers
every time it is questioned.