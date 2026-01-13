# dreichor

**Note:** The public repository focuses on architecture, guarantees,
and governance boundaries. Not all internal implementation details
are published.

**dreichor** is a universal decision & trust governance framework  
for systems that must act under uncertainty.

**dreichor** is designed for architects, auditors, and engineers
responsible for systems where incorrect autonomy is a material risk.

It provides a formal, deterministic governance layer that sits **above domain logic**  
and **below real-world execution**, ensuring that decisions are explainable, auditable,
and only deployed when sufficient trust has been earned.

dreichor does not optimize outcomes.  
It governs **behavior**.

## Who dreichor Is For

dreichor is intended for teams that:
- operate systems with real-world consequences
- require auditability and replayable decision logic
- must justify autonomy to regulators, auditors, or internal governance
- prefer explicit guarantees over adaptive optimization

If you are looking for:
- faster decisions
- smarter models
- automatic optimization
- self-healing autonomy

dreichor is not the right tool.

---

## What Problem Does dreichor Solve?

Modern systems increasingly make autonomous or semi-autonomous decisions:

- financial systems allocating capital  
- insurance systems assessing risk  
- compliance engines approving or rejecting actions  
- AI-assisted systems operating with incomplete knowledge  

These systems often fail not because they are unintelligent,
but because **trust in their decisions is assumed instead of earned**.

Traditional approaches rely on:
- configuration instead of observation  
- parameter tuning instead of accountability  
- optimization instead of explanation  

dreichor introduces a missing layer:  
**decision governance**.

---

## Core Principle

> **Decisions must be governed before they are trusted.**

A system may only act autonomously if it has demonstrated,
through consistent and observable behavior,
that it can handle uncertainty responsibly.

---

## Architecture — CHOR

At the heart of dreichor lies **CHOR** — the immutable core architecture.

CHOR is built on three strictly separated yet inseparable layers.
This separation is the **first and unbreakable rule** of the system.

### RAGE — Reactive Algorithmic Goal Engine  
**The Will**

- Where decisions are formed  
- Deterministic and reproducible  
- Independent of execution, cost, or reality  

RAGE decides *what should be done*  
without knowing *how* or *whether* it will be executed.

---

### NOISE — Non-Optimal Inherent System Entropy  
**The Friction**

- Where deviation between will and outcome becomes visible  
- Models uncertainty, loss, and imperfection  
- Does not optimize, correct, or smooth reality  

NOISE exists to make uncertainty explicit, not to eliminate it.

---

### MEATSPACE — Reality Layer  
**The World**

- Networks, humans, organizations, law, randomness  
- Non-deterministic and uncontrollable  
- Observable, but never fully modelable  

MEATSPACE is where systems either survive or fail.

---

## The CHOR Rule (Unbreakable)

> **RAGE, NOISE, and MEATSPACE are strictly separated.**

- Each layer is executed in sequence  
- No layer may assume responsibility of another  
- Layers are aware of each other’s existence  
- They do not know how the others operate internally  

Breaking this rule breaks trust.

---

## Governance Outside the Core

CHOR itself is intentionally minimal.

All governance logic exists **around** CHOR, not inside it:
- gates
- trust levels
- proposals
- escalation rules
- replay and audit

Governance **observes** decisions and behavior.  
It never alters the will expressed by CHOR.

---

## Repository Structure (Conceptual)

```txt
/chor                # Immutable domain core
  /rage
  /noise
  /meatspace

/features            # Vertical slices
  /governance
  /trust
  /replay
  /audit
  /observability

/adapters            # IO, persistence, clocks, APIs
```

## Rule:
CHOR must not import from features or adapters.
Everything else may depend on CHOR.

---

## Language

dreichor is implemented in TypeScript.

TypeScript is used as a **design language**, not just a runtime choice.

Key constraints:
	•	strict mode enabled
	•	no any
	•	no wall-clock time inside CHOR
	•	no side effects in the core

This ensures:
	•	deterministic behavior
	•	explicit domain models
	•	auditability and enterprise readiness

⸻

## What dreichor Is Not
	•	❌ Not an AI system
	•	❌ Not a machine learning framework
	•	❌ Not a rules engine
	•	❌ Not a decision optimizer
	•	❌ Not domain-specific

dreichor does not replace intelligence.
It governs how intelligence is allowed to act.

⸻

## License

This project is licensed under the Mozilla Public License 2.0 (MPL-2.0).

The source code is available for review and integration under the terms
of the MPL-2.0 license.

Commercial licensing, enterprise assurances, or regulated-use agreements
may be offered separately and are not covered by this repository.

⸻

## Philosophy

Profit without governance is luck.
Governance without action is philosophy.
dreichor insists on both.

## Documentation

Start here for architecture, audit walkthroughs,
formal guarantees, and responsibility boundaries:

- Documentation Index: /docs/README.md

## Further Information

Official project site:
https://www.dreichor.io

The website provides:
- executive overview
- audit perspective
- licensing boundaries