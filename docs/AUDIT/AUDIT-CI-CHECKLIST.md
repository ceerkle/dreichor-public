# dreichor — Audit & CI Checklist

This document defines the **minimum, non-negotiable checks**
that must pass for dreichor to be considered:

- deterministic
- auditable
- governance-correct

This checklist applies to:
- CI pipelines
- internal audits
- external audits
- release qualification

It is normative and binding.

---

## Scope

This checklist verifies:
- determinism
- replayability
- responsibility boundaries
- absence of hidden control paths

It does **not** verify:
- business correctness
- domain performance
- outcome quality

Governance, not intelligence, is in scope.

---

## Binding References

This checklist is grounded in:
- `docs/ARCHITECTURE.md`
- `docs/TESTING-PHILOSOPHY.md`
- `docs/decisions/ADR-004-deterministic-replay-as-proof.md`
- `.cursorrules`

If any item below fails,
the build or audit **MUST FAIL**.

---

## Build Integrity

The following must succeed:

- [ ] TypeScript compilation completes with **zero errors**
- [ ] No `any` types introduced
- [ ] No CHOR code modified outside allowed scope
- [ ] No forbidden dependencies introduced

Failure ⇒ **STOP**

---

## Determinism Checks

The system must demonstrate:

- [ ] No usage of wall-clock time (`Date`, `performance.now`)
- [ ] No unseeded randomness (`Math.random`)
- [ ] No environment-dependent branching
- [ ] No unordered iteration affecting outcomes

Any occurrence ⇒ **FAIL**

---

## Replay Proof (Mandatory)

The following demos must execute successfully
and produce **bit-identical output across runs**:

- [ ] `demos/replay/`
- [ ] `demos/configuration/`
- [ ] `demos/persistence/`
- [ ] `demos/explanation/`
- [ ] `demos/trace/`

Rules:
- replay mismatch ⇒ **FAIL**
- missing demo ⇒ **FAIL**
- partial execution ⇒ **FAIL**

Replay is proof, not testing.

---

## Governance Correctness

The audit must confirm:

- [ ] No implicit trust promotion exists
- [ ] All trust transitions are rule-based
- [ ] Default behavior is **no change**
- [ ] Missing evidence is explicit
- [ ] Governance never mutates decisions

If trust increases without an explicit rule ⇒ **FAIL**

---

## Explanation & Trace Stability

The system must demonstrate:

- [ ] Governance explanations are deterministic
- [ ] Explanations reference observable evidence only
- [ ] Decision traces are stable and named
- [ ] Replays produce identical explanations and traces

Any inferred or generated reasoning ⇒ **FAIL**

---

## Persistence Neutrality

If persistence is wired:

- [ ] Governance outcomes are identical with or without sinks
- [ ] Persistence does not influence decisions
- [ ] Replay from persisted artifacts reproduces outcomes exactly

Persistence affecting behavior ⇒ **FAIL**

---

## Responsibility Boundaries

The audit must verify:

- [ ] dreichor does not execute actions
- [ ] dreichor does not stop systems
- [ ] dreichor does not manage infrastructure
- [ ] dreichor does not enforce compliance

dreichor emits **judgments only**.

Any hidden control path ⇒ **FAIL**

---

## CI Pass Criteria

A CI run is valid **only if**:

- all demos execute
- all outputs are deterministic
- no divergence occurs
- no forbidden behavior is detected

Coverage metrics are irrelevant.

---

## Auditor Assertion

If all checks above pass, the auditor may conclude:

- governance decisions are deterministic
- trust evolution is explicit and auditable
- replay constitutes sufficient proof
- responsibility boundaries are intact

---

## Final Statement

> **If any item in this checklist fails,  
> trust in dreichor is not justified.**

This checklist exists to make trust
verifiable, repeatable, and defensible.