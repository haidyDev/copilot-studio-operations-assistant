# 11 — Architecture decision records

## ADR-001 — Use Dataverse as source of truth
**Decision:** retrieve operational records from Dataverse rather than rely on the language model's memory.

**Reason:** order and reservation information changes and must be tied to structured records.

**Trade-off:** the assistant depends on connector availability, permissions and service quotas.

## ADR-002 — Separate order and reservation queries
**Decision:** retrieve an order first, then query reservations using the returned order GUID.

**Reason:** this preserves the Dataverse relationship and avoids guessing from free-text descriptions.

**Trade-off:** two tool calls increase latency and expose the workflow to orchestration limits.

## ADR-003 — Use logical OData field names
**Decision:** construct the order predicate with `aroh_ordernumber`.

**Reason:** OData requires the correct logical field, not an arbitrary display/schema label.

**Trade-off:** configuration must track Dataverse schema changes.

## ADR-004 — Keep the first release read-only
**Decision:** expose retrieval actions only.

**Reason:** this is sufficient to validate conversational discovery without adding mutation risk.

**Trade-off:** users cannot update or confirm reservations through the agent.

## ADR-005 — Document evaluation disagreements
**Decision:** retain the 50% reported score and explain both failed cases.

**Reason:** transparent evidence is more valuable than presenting the score as a universal quality metric or concealing failures.

**Trade-off:** readers must distinguish automated grading from functional observations.
