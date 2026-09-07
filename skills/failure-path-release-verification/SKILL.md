---
name: failure-path-release-verification
description: Verify a completed change through its diff, failure paths, runtime behavior, and honest reporting.
---

# Failure-Path Release Verification

## Purpose

Perform a strict final review before declaring a change complete, especially when an AI coding agent produced or modified it.

## Use when

- Preparing a change for merge, release, deployment, or handoff.
- The change touches shared behavior, persistence, asynchronous work, external dependencies, or user-critical flows.

## Do not use when

- The change is a trivial isolated edit with no runtime or behavioral effect.

## Inputs

- Original requirement, final diff, repository commands, and relevant runtime environment.

## Workflow

1. Inspect the complete diff and compare it directly with the requirement.
2. Identify unrelated edits, accidental formatting, generated files, secrets, and changed dependencies.
3. Inspect callers and contracts for changed public behavior.
4. Inspect migrations, configuration, and runtime packaging where applicable.
5. Enumerate happy path, failure path, retry, cancellation, concurrency, and stale-state behavior.
6. Run the smallest relevant existing tests, then broader checks only when shared behavior warrants them.
7. Manually exercise critical flows when automation cannot prove user-visible or integration behavior.
8. Inspect runtime logs and outputs for safe errors, unintended retries, warnings, and leaked internals.
9. Report verified evidence separately from risk, assumption, and unverified work.

## Required checks

- Requirement coverage is explicit.
- Error handling and state consistency are checked.
- Existing tests are discovered rather than invented.
- Final diff contains only intended changes.
- Secrets, credentials, and generated artifacts are excluded.
- Manual verification is not claimed unless it occurred.

## Common failure modes

- Reporting test success without running tests.
- Checking only a unit test after a runtime configuration change.
- Ignoring migration or compatibility impact.
- Hiding a flaky external dependency behind a generic “pass.”
- Forgetting to inspect the final diff after formatting or generated output.

## Output contract

```text
VERDICT: PASS / PASS WITH RISKS / FAIL
REQUIREMENT COVERAGE
DIFF REVIEW
AUTOMATED TESTS RUN
MANUAL VERIFICATION
FAILURE PATHS CHECKED
RUNTIME / CONFIG CHECKS
RISKS
NOT VERIFIED
FOLLOW-UP
```

## Example

For a new upload endpoint, verify malformed input, duplicate requests, storage failure, database rollback, public errors, and final working-tree contents in addition to the successful upload.
