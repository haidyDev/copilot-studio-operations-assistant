# 03 — Dataverse integration and OData

## Data model
The prototype reads two relevant Dataverse tables:
- **Orders** (UI label: `Tilaukset`; table technical name observed as `aroh_order`).
- **Reservations** (UI label: `Tilavaraukset`), linked to an order through a lookup.

Additional tables exist in the wider operations application, but this agent's verified tool path uses these two retrievals.

## Tool A — order lookup
**Connector action:** Microsoft Dataverse — List rows from selected environment.

**Configured inputs:** a specific development environment, Orders table, and an AI-populated filter input.

**Filter generation instruction:** construct a valid OData predicate using the logical name `aroh_ordernumber`; the order number is a string and must be quoted.

```text
aroh_ordernumber eq 'AR--1000'
```

Do not substitute `aroh_OrderNumber` for the logical field name. Do not run an unrestricted query when an order number is unavailable.

### Order-number variations
In manual testing, the agent found the sample order even when the user wrote the prefix in lowercase and, in another test, used a single hyphen. This is **observed conversational behavior**, not a guaranteed normalization algorithm or a change to the Dataverse primary key. The exact canonical order number should remain visible in the response.

## Tool B — reservation lookup
**Connector action:** Microsoft Dataverse — List rows from selected environment.

**Configured inputs:** the same selected development environment, Reservations table, and an AI-populated filter input.

The predicate uses the Dataverse lookup value field and the GUID returned by Tool A:

```text
_aroh_order_value eq 00000000-0000-0000-0000-000000000000
```

The GUID above is a **placeholder**, not a real record ID. Do not put the order number in this position. The exact GUID comes from the retrieved order record.

## Relationship integrity
The reservations query is scoped to the selected order's identifier. This is more reliable than searching facility names in notes and helps avoid mixing reservations belonging to different orders.

## Failure handling
| Situation | Expected behavior |
| --- | --- |
| Order number missing | Ask for it unless prior conversation clearly identifies the order |
| Order not found | State that no matching order was found; do not invent fields |
| Reservations absent | State that no linked reservation records were returned; do not infer them from notes |
| Connector or orchestration error | Report a technical error, not 'order not found' |
| Multiple plausible number formats | Verify against returned records and avoid claiming an unverified match |

## Validation boundary
These are tool configuration patterns and observed behavior, not a published connector export or a full schema migration script.
