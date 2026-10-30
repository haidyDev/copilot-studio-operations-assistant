# 02 — Solution architecture

## Components
The prototype has a Copilot Studio conversational interface, agent instructions, two Microsoft Dataverse connector tools, and two Dataverse tables: Orders and Reservations.

## Retrieval flow
1. The user asks a Finnish question that identifies an order.
2. The agent forms an OData filter using the order-number logical field.
3. The Orders lookup returns a matching record or no result.
4. For related reservations, the agent uses the returned order record's GUID.
5. The Reservations lookup uses the Dataverse lookup field to retrieve records related to that GUID.
6. The assistant summarizes retrieved fields in Finnish. If no order is found, it explains that result without inventing values.

## Data relationship
The business-facing order number and the Dataverse record GUID are distinct identifiers. The first locates the order; the second links reservations to it.

## Read-only boundary
Both configured tools are Dataverse List rows actions. The implementation does not expose create, update or delete tools. The effective permissions of the connected account still matter.

## Design considerations
The order-number filter must use the correct logical field. The reservation query must use the order record GUID. Notes and free-text special requests must not be presented as proof of a booked facility. Technical errors should be distinguished from an empty query result.

## See also
- [Dataverse integration](03-dataverse-integration.md)
- [Architecture decisions](11-architecture-decisions.md)
- [Testing and evaluation](06-testing-and-evaluation.md)
