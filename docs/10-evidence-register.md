# 10 — Evidence register

Seven anonymized screenshots have been uploaded to the [screenshots directory](../screenshots/README.md). The table links each evidence item to its original published filename (including the double `.png.png` extension where present).

| ID | Evidence subject | Screenshot | Documentation |
| --- | --- | --- | --- |
| E01 | Initial evaluation summary | [View image](../screenshots/01-copilot-studio-evaluation-initial-results.png.png) | [Testing](06-testing-and-evaluation.md) |
| E02 | Apparent evaluator false negative | [View image](../screenshots/02-evaluation-false-negative-analysis.png.png) | [Testing](06-testing-and-evaluation.md) |
| E03 | Orchestration planner rate limit | [View image](../screenshots/03-evaluation-orchestration-rate-limit.png.png) | [Testing](06-testing-and-evaluation.md) |
| E04 | Dynamic Orders OData filter | [View image](../screenshots/04-dataverse-ai-dynamic-odata-filter.png.png) | [Dataverse integration](03-dataverse-integration.md) |
| E05 | Related Reservations GUID filter | [View image](../screenshots/05-dataverse-related-records-guid-filter.png.png) | [Dataverse integration](03-dataverse-integration.md) |
| E06 | Agent overview | [View image](../screenshots/06-copilot-studio-agent-overview.png) | [Agent configuration](04-agent-configuration.md) |
| E07 | Agent test conversation | [View image](../screenshots/07-agent-dataverse-query-response.png.png) | [Testing](06-testing-and-evaluation.md) |

## Evidence interpretation
Screenshots support the documented configuration and visible test results. They do not constitute an exportable solution, production deployment verification or comprehensive security assessment. The evaluation's **50% reported score** remains unchanged: the apparently incorrect evaluator judgment and the service-side rate limit are explained separately, not reclassified as passes.

## Image naming
Files are linked using their actual uploaded names to avoid broken references. Several filenames contain a doubled `.png.png` extension; these are valid repository paths and can be normalized later if desired.
