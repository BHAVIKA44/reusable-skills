---
name: change-impact-plan
description: Convert a requirement into the smallest coherent implementation plan before code changes begin.
---

# Change Impact Plan

## Purpose

Translate a requirement into a safe, evidence-based plan that respects existing architecture and avoids accidental scope growth.

## Use when

- A feature, behavior, API, schema, or workflow change is non-trivial.
- The request may affect callers, consumers, data, or state.

## Do not use when

- The change is a clearly isolated typo or presentation-only edit with no shared behavior.

## Inputs

- Requirement and constraints.
- Repository evidence map or equivalent focused discovery.
- Existing tests and current diff.

## Workflow

1. Restate the observable behavior, not an assumed implementation.
2. Compare current behavior with the requirement using repository evidence.
3. Identify entry points, callers, consumers, contracts, and feature flags affected.
4. Inspect schema, migrations, stored data, and state transitions if behavior persists or evolves over time.
5. Identify frontend, backend, integration, and runtime implications where they exist.
6. List failure paths, backward-compatibility risks, and migration or rollout needs.
7. Propose the smallest coherent change. Reuse existing boundaries before adding abstractions.
8. Define focused checks first, broader checks only where shared behavior changed.
9. Explicitly state what must not change.

## Required checks

- Callers inspected before a contract changes.
- Migrations inspected before a schema changes.
- Terminal and failure states considered for workflow changes.
- Existing tests mapped to the changed behavior.
- Assumptions and unknowns made explicit.

## Common failure modes

- Planning from the requirement alone.
- Adding an abstraction before proving existing boundaries are insufficient.
- Forgetting old records, clients, or asynchronous consumers.
- Treating happy-path tests as the full plan.

## Output contract

```text
REQUIREMENT
CURRENT BEHAVIOUR
AFFECTED COMPONENTS
CONTRACT CHANGES
DATA / STATE CHANGES
IMPLEMENTATION PLAN
EDGE CASES
RISKS
TEST PLAN
OUT OF SCOPE
UNKNOWNS
```

## Example

For “add an expiration date to approvals,” plan the API field, persisted representation, state-transition rule, existing records, UI behavior, scheduled enforcement, and tests before editing.
