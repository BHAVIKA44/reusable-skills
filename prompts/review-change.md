# Review a Change

Review the complete diff as a strict senior engineer. Use `failure-path-release-verification` when the change has shared behavior, persistence, asynchronous work, external dependencies, or release impact.

Compare the implementation directly with the requirement. Inspect callers and consumers for changed contracts. Review schema and migrations, state consistency, concurrency, idempotency, retries, external side effects, error handling, security, observability, performance, tests, documentation, and runtime/configuration changes where relevant.

Ask:

- What happens if this fails halfway through?
- What happens if this operation is repeated?
- What happens after process restart?
- Did behavior change outside the requirement?
- Which assumptions lack repository evidence?

For AI changes, also review deterministic versus model responsibilities, structured-output validation, unsupported-output risk, fallback behavior, retrieval versus generation boundaries, evaluation coverage, and material cost or latency effects.

Do not manufacture issues. Every finding must cite concrete repository or diff evidence.

Return only:

```text
VERDICT: PASS / PASS WITH RISKS / FAIL
REQUIREMENT COVERAGE
CORRECTNESS FINDINGS
ARCHITECTURE / DESIGN
FAILURE PATHS
DATA / STATE SAFETY
AI-SPECIFIC FINDINGS
TEST COVERAGE
ISSUES BY SEVERITY
BLOCKERS
HIGH
MEDIUM
LOW
NOT VERIFIED
RECOMMENDATION
```
