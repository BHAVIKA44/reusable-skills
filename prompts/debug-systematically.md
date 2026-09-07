# Debug Systematically

Do not patch symptoms before understanding the failure.

1. Reproduce the failure or characterize it precisely.
2. Collect concrete evidence: request/input, observed output, logs, errors, state, environment, and relevant history.
3. Identify the failing layer and trace the execution path through it.
4. Generate a small number of hypotheses, rank them by evidence, and test one at a time.
5. Identify the root cause before changing code.
6. Make the smallest root-cause fix. Do not combine unrelated changes.
7. Re-run the original failure, then check adjacent regression and failure modes.
8. Inspect the final diff and report anything not verified.

Do not:

- increase timeouts without evidence;
- swallow exceptions or add blind retries;
- spread null checks as a substitute for diagnosis;
- rewrite a component before locating the defect;
- claim success because one test passed.

For AI-related behavior, distinguish deterministic application defects from retrieval, ranking, context assembly, generation, structured-output parsing, and provider/runtime failures.

Return only:

```text
SYMPTOM
REPRODUCTION
EVIDENCE
FAILING LAYER
HYPOTHESES
ROOT CAUSE
PROPOSED FIX
FILES CHANGED
VERIFICATION
REGRESSION CHECKS
NOT VERIFIED
```
