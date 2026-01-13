# dreichor — Audit Walkthrough  
**60-Minute Verification of Decision Governance Under Uncertainty**

## Purpose

This document enables an auditor, risk officer, or governance reviewer
to verify the core guarantees of **dreichor**
within approximately **60 minutes**.

It explains **what can be verified**, **how it is verified**,
and **what dreichor explicitly does not claim or control**.

This walkthrough focuses on **governance behavior**, not business outcomes.

---

## Scope & Assumptions (≈ 5 minutes)

This walkthrough verifies that dreichor:

- governs decisions through explicit, deterministic rules
- separates decision intent, friction, and reality
- evaluates trust through observation, not intervention
- supports replayable and auditable governance decisions

This walkthrough does **not** verify:
- correctness of business logic
- profitability, performance, or optimization
- safety or correctness of external systems
- compliance with specific regulations

dreichor is a **governance framework**, not an execution system.

---

## Architectural Invariants (≈ 10 minutes)

### What to Verify

1. **CHOR Separation**
   - RAGE (Will)
   - NOISE (Friction)
   - MEATSPACE (Reality)

2. **Strict Responsibility Boundaries**
   - Decisions are formed without execution knowledge
   - Friction is modeled deterministically
   - Reality is observed, not controlled

3. **Purity of the Core**
   - No IO
   - No wall-clock time
   - No unseeded randomness
   - No persistence
   - No governance logic inside CHOR

### Evidence

- `docs/ARCHITECTURE.md`
- Code structure under `/chor`
- `.cursorrules`

The auditor should confirm that:
- CHOR has no dependencies on features or adapters
- Dependency direction is enforced

---

## Governance Mechanics (≈ 10 minutes)

### What to Verify

1. **Observation-Only Governance**
   - Governance never executes actions
   - Governance never modifies decisions

2. **Gate Semantics**
   - Gates evaluate localized signals
   - Gates do not escalate trust

3. **Explicit Aggregation**
   - Gate results are combined deterministically
   - Aggregation logic is explicit and auditable

4. **Explicit Escalation**
   - Trust transitions are rule-based
   - Default behavior is **NO CHANGE**
   - No implicit promotion exists

### Evidence

- `docs/decisions/ADR-001-governance-events-in-chor.md`
- `docs/decisions/ADR-002-governance-aggregation.md`
- `docs/decisions/ADR-003-trust-lifecycle-and-escalation.md`
- `docs/ENTERPRISE-WHY-NO-PROMOTION.md`

The auditor should verify that:
- trust cannot increase without an explicit rule
- absence of failure does not imply promotion

---

## Determinism & Replay (≈ 15 minutes)

### What to Verify

dreichor governance decisions are:
- deterministic
- replayable
- auditable after the fact

### Replay Procedure

The auditor runs:

```bash
node dist/demos/replay/replay-run.js
````

## Expected Outcome

- The output is identical across runs
- Trust evolution matches documented expectations
- No implicit promotions occur
- Any mismatch causes a hard failure

## Evidence

- demos/replay/README.md
- demos/replay/fixtures.ts
- demos/replay/scenarios.ts
- demos/replay/replay-run.ts

This replay demonstrates that governance decisions  
can be reconstructed without ambiguity.

---

## Responsibility & Control Boundaries (≈ 10 minutes)

### Explicit Non-Responsibilities

dreichor does **not**:

- execute actions
- stop systems
- control infrastructure
- persist data
- manage access
- enforce compliance

dreichor emits **governance judgments only**.

### Responsibility Allocation

- **dreichor**: decision governance & trust evaluation  
- **Implementing system**: execution, storage, operational control  
- **Organization**: policy, escalation rules, accountability  

This separation is intentional and required  
to maintain legal and operational clarity.

---

## Audit Conclusion Checklist (≈ 10 minutes)

The auditor should be able to answer **YES** to all of the following:

- Decision governance is explicitly defined
- Trust escalation is rule-based and auditable
- No implicit promotion exists
- Governance decisions are deterministic
- Replay produces identical results
- Responsibilities are clearly separated
- No hidden control paths exist

If all checks pass,  
the governance guarantees of dreichor  
are verified for this scope.

---

## Final Statement

This walkthrough demonstrates that dreichor:

- does not assume trust
- does not hide escalation
- does not optimize governance away
- does not interfere with execution

Instead, it provides a verifiable framework  
for governing decisions under uncertainty.

> **Trust in dreichor is not claimed.  
> It is demonstrated.**