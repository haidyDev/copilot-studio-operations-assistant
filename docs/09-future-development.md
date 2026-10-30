# 09 — Roadmap

These are **proposals**, not implemented features.

## Near term
- Repeat evaluation after service limits reset.
- Introduce structured test cases for ambiguous and malformed order numbers.
- Add multi-turn conversation tests and regression baselines.
- Separate answer correctness, tool execution and evaluation grading in reporting.
- Improve error messages for permission, connector and quota failures.

## Medium term
- Add explicit confirmation when multiple possible order matches exist.
- Add observability for tool calls, error categories and response times.
- Assess data minimization and field-level permissions for each user role.
- Export the agent solution and maintain environment-independent deployment notes where licensing permits.

## Longer term
- Evaluate additional read-only operational questions across related entities.
- Consider controlled operational actions only with explicit authorization, audit logging and human confirmation.
- Establish production readiness criteria: permissions, licensing, monitoring, test coverage, rollback and support ownership.

## Acceptance criteria for future release
A future release should have repeatable tests, documented permissions, quota monitoring, verified data correctness, and an approved publishing/licensing path.
