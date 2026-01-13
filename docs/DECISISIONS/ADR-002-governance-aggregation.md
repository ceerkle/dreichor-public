# ADR-002: Explicit Governance Aggregation

## Status
Accepted

## Context
Gates evaluate localized trust signals.
However, no component currently defines
how multiple gate results are combined
into a single trust decision.

Without explicit aggregation,
trust escalation would be implicit,
non-auditable, and unstable.

## Decision
Governance aggregation is introduced
as a distinct responsibility outside CHOR.

Aggregation:
- consumes GateResults and GovernanceEvents
- produces explicit trust transitions
- is deterministic and replayable

Gates MUST NOT:
- modify trust directly
- infer escalation logic

## Consequences
- Trust evolution becomes auditable
- Gate semantics remain local and simple
- Aggregation becomes a licensable control point