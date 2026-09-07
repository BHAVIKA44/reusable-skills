# Implementation Plan

Use this for a non-trivial change. Write `None` where a section does not apply. Mark statements as **confirmed**, **inferred**, or **unknown** when evidence is incomplete.

## 1. Requirement

What observable behavior is changing? Include constraints and success criteria.

## 2. Current Behavior

What happens today? Cite the relevant files, modules, functions, tests, or runtime evidence.

## 3. Proposed Behavior

What will happen after the change? State what remains unchanged.

## 4. Affected Components

| Component | Why affected | Expected change |
| --- | --- | --- |
| | | |

## 5. Contracts and Boundaries

List affected APIs, interfaces, events, model boundaries, callers, and consumers. Inspect callers before changing a contract.

## 6. Data / State Changes

Schema, migrations, state transitions, persisted identifiers, cache effects, and recovery implications. Inspect migrations before proposing schema changes.

## 7. Background / External Behavior

Async work, jobs, retries, queues, webhooks, providers, storage, or other external side effects. Write `None` if not applicable.

## 8. Implementation Steps

1. [First dependency-aware step]
2. [Next step]
3. [Final step]

Prefer the smallest coherent change. Do not include unrelated cleanup or speculative abstractions.

## 9. Edge Cases

- [Case]

## 10. Failure Paths

| Failure | Expected behavior | Recovery / user outcome |
| --- | --- | --- |
| | | |

## 11. Backward Compatibility

Existing clients, records, deployments, rollout, and rollback considerations.

## 12. Security and Observability

Security implications plus relevant logs, metrics, traces, audit events, or alerts. Write `None` when not relevant.

## 13. Test Plan

### Focused automated checks

- [Focused check]

### Broader regression checks

- [Broader check]

### Manual verification

- [Manual flow]

Only list checks that can realistically be performed.

## 14. Out of Scope

- [Explicitly excluded work]

## 15. Assumptions / Unknowns

- **Confirmed:** [Repository evidence]
- **Inferred:** [Reasonable conclusion needing confirmation]
- **Unknown:** [Question that could change the plan]

## 16. Definition of Done

- [ ] Requirement and constraints are met.
- [ ] Relevant callers, contracts, state, and persistence are safe.
- [ ] Failure paths are handled intentionally.
- [ ] Relevant verification is complete.
- [ ] Final diff contains no unrelated changes.
- [ ] Anything not verified is reported explicitly.
