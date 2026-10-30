# 05 — User guide (development prototype)

## Intended user
An internal operations user who needs to inspect order and related facility-reservation information without navigating individual Dataverse tables.

## Asking questions
Enter an order number and a question in Finnish. Examples:

| Question | Intended answer |
| --- | --- |
| `Näytä tilaus AR--1000` | Verified order summary |
| `Mitä tiloja tilaukselle AR--1000 on varattu?` | Related reservation records |
| `Kuinka monta osallistujaa tilauksella AR--1000 on?` | Participant count from the order |
| `Milloin tilaus AR--1000 alkaa?` | Event start date and time |
| `Näytä tilaus AR--9999` | Not-found message when absent |

The assistant was also manually tested with informal Finnish and minor spelling errors. Always inspect the canonical order number displayed in the answer.

## Reading the result
- Order details come from the order record.
- Reserved facilities should come from the linked reservation records.
- A facility mentioned in a note or special request is not automatically a confirmed reservation.
- A missing-order response is not the same as a service error.

## Troubleshooting as a user
If an order is not found, check its number and hyphens. If the agent reports a technical error, retry later or ask the administrator to inspect connector access and platform limits. Do not interpret a rate-limit error as proof that an order is absent.

## Availability
The documented version is a development prototype tested inside Copilot Studio. This guide does not claim a published end-user channel.
