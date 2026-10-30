# 08 — Security, privacy and limitations

## Scope of security claims
The documented agent uses **read-only Dataverse List rows** tools. This limits the visible action surface, but does not prove that the entire environment, account or future versions are technically read-only.

## Access model
Dataverse access depends on the connector identity and that identity's table/row permissions. Evaluation used an authenticated user profile and a Dataverse connection. The screenshots do not establish a production authorization design.

## Public portfolio safeguards
- Public prose uses generic project labels rather than the source organization's name.
- Screenshot identities and email addresses were visually redacted by the project author.
- Screenshots should be checked for names, account identifiers, tenant/environment IDs, email addresses and unintended records before upload.
- Do not publish connector secrets, tokens, credentials or unredacted real customer records.
- Example records in documentation are described as test data.

## Limitations
- Development environment only; no production deployment evidence.
- Small test sample, including a four-case automated evaluation.
- Runtime orchestration limits observed.
- No formal security or accessibility audit.
- Model-driven interpretation may vary between runs.
- No automated continuous regression suite in this version.
- No write actions, workflow execution or reservation management.
- No guarantee that spelling/hyphen variations always resolve correctly.

## Licensing
A Copilot Studio status warning indicated that publishing premium capabilities may require an upgraded license. This portfolio does not claim that licensing or production publishing requirements were satisfied.
