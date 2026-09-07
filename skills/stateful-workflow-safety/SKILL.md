---
name: stateful-workflow-safety
description: Design or review multi-step workflows with state, side effects, retries, and recovery.
---

# Stateful Workflow Safety

## Purpose

Make long-running or multi-step workflows correct under retries, duplicates, partial failures, concurrency, and restarts.

## Use when

- Work moves through states over time: approvals, imports, jobs, payments, provisioning, exports, or orchestration.
- A request performs multiple persistent writes or external side effects.

## Do not use when

- A request is stateless, synchronous, and has no durable side effect beyond one isolated write.

## Inputs

- Workflow trigger, actors, expected terminal outcomes, and persistence model.
- Existing state machine, job runner, event flow, or polling behavior.

## Workflow

1. Name all meaningful states, including terminal failure and rejection states where they differ.
2. Define allowed and invalid transitions. Do not rely on vague booleans.
3. List each transition's database writes and external side effects.
4. Choose transaction boundaries so dependent writes succeed or fail together.
5. Define idempotency for repeated requests, retries, and duplicate delivery.
6. Decide when side effects occur relative to persistence and how failures are compensated.
7. Model restart, timeout, partial failure, concurrent actor, and stale-client behavior.
8. Persist identifiers and enough progress to recover or diagnose work.
9. Expose truthful user-visible status and stop polling or events at terminal states.

## Required checks

- Invalid transitions are rejected.
- Repeated requests do not duplicate effects.
- Terminal states are stable.
- Failure does not leave contradictory persisted state.
- Recovery path is explicit for interrupted work.
- Users can distinguish rejection, pending work, and system failure.

## Common failure modes

- Updating state before an unprotected side effect.
- Calling an action twice because a client retries.
- Leaving partial writes after an exception.
- Treating in-memory job state as durable.
- Showing stale actions after a terminal decision.

## Output contract

```text
WORKFLOW
STATE MACHINE
TRANSITIONS
SIDE EFFECTS
TRANSACTION BOUNDARIES
IDEMPOTENCY STRATEGY
RETRY BEHAVIOUR
FAILURE SCENARIOS
RECOVERY STRATEGY
CONCURRENCY RISKS
VERIFICATION
```

## Example

For an import approval, ensure that accepting twice does not publish twice, a failed publish rolls back the approval, and a restart can identify unfinished work.
