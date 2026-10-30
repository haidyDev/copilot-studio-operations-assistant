# 01 — Project overview

## Executive summary
This portfolio project demonstrates a Finnish-language, read-only operations assistant built in Microsoft Copilot Studio and connected to Microsoft Dataverse. The assistant helps an internal user retrieve an order and its related facility reservations by asking questions in natural language.

**Status:** development-environment prototype; manually tested; one four-case automated evaluation recorded. **Not claimed:** production deployment, independent security audit, or guaranteed accuracy.

## Business problem
Operational order information is stored in structured Dataverse records. A user who needs the customer, event dates, attendee count or booked facilities would otherwise navigate the application and inspect multiple related records. The prototype explores a conversational retrieval interface for this workflow.

## Scope and success criteria
- Accept Finnish questions, including common spelling mistakes and informal wording.
- Retrieve an order by its external order number.
- Retrieve related facility reservations through the order record's Dataverse GUID.
- Summarize only information supported by returned records; distinguish missing orders from technical errors.
- Remain read-only: no order changes, reservation changes or emails.
- Provide reproducible evidence of tests and limitations.

## Out of scope
Creation or editing of records; customer-facing deployment; approvals; automated notifications; billing; production monitoring; formal accessibility certification.

## Implementation snapshot
| Component | Implemented role |
| --- | --- |
| Copilot Studio | Conversation, instructions, tool orchestration |
| Microsoft Dataverse | Structured source of order and reservation records |
| Dataverse connector tool #1 | Query the Orders table with an OData filter |
| Dataverse connector tool #2 | Query Reservations by order GUID |
| Agent instructions | Finnish response policy, lookup rules, missing-data and read-only behavior |
| Test chat | Manual positive, negative and conversational tests |
| Evaluation | Four single-response cases; 2 pass / 2 fail reported |

## Evidence and caveats
See [evidence register](10-evidence-register.md), [testing](06-testing-and-evaluation.md) and [limitations](08-security-and-limitations.md). Screenshot labels and example values have been generalized for public documentation; the implementation used an identifiable development environment. All screenshots should be reviewed before publication.
