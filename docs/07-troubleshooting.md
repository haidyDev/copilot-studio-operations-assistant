# 07 — Troubleshooting and incident notes

## Issue 1: OData field naming
**Symptom:** a query cannot resolve the intended order-number field.

**Likely cause:** confusing Dataverse display/schema names with the logical name.

**Resolution:** use `aroh_ordernumber` in the OData filter, not `aroh_OrderNumber`.

**Verification:** order lookup returned the expected record during interactive tests.

## Issue 2: Order number versus record GUID
**Symptom:** related reservations are missing or filtering is invalid.

**Likely cause:** passing an external order number into the reservation lookup field.

**Resolution:** query Orders first, obtain the record GUID, then use `_aroh_order_value eq <GUID>` for Reservations.

**Verification:** interactive tests retrieved two facilities linked to the example order.

## Issue 3: Missing order graded as a failure
**Symptom:** the evaluation labels the missing-order case 'Not answered'.

**Evidence:** the visible response says the order was not found, recommends checking the order number, and does not invent data. The expected response describes that same behavior.

**Interpretation:** apparent false-negative grading. This is an interpretation of visible evidence, not proof of the evaluator's internal cause.

**Next step:** refine the expected response and grading rubric; rerun.

## Issue 4: `GenAIToolPlannerRateLimitReached`
**Symptom:** the agent cannot complete a request and reports a generative orchestration usage limit.

**Interpretation:** service-side orchestration capacity/limit interrupted the run. It does not show that the requested order was absent.

**Next step:** wait for capacity to become available; retry and track the frequency. Do not modify production settings or purchase licenses solely to improve a portfolio test.

## Issue 5: Hyphen variations
**Symptom:** the user's order number differs from the canonical stored format.

**Observed behavior:** at least one one-hyphen request was resolved to a two-hyphen order.

**Risk:** overly broad normalization could match the wrong order.

**Next step:** preserve the original input, verify the returned canonical number, and ask for clarification if multiple records are plausible.

## Diagnostic checklist
Confirm (1) requested order number, (2) selected environment, (3) connector identity and permissions, (4) Orders filter, (5) returned GUID, (6) Reservations filter, (7) service errors and limits, and (8) whether the issue concerns answer quality or test grading.
