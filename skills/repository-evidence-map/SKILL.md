---
name: repository-evidence-map
description: Build an evidence-backed architecture map before changing an unfamiliar repository.
---

# Repository Evidence Map

## Purpose

Build a verified mental model of a repository without assuming its architecture from names, folders, or documentation.

## Use when

- Starting work in an unfamiliar codebase.
- Reviewing a broad change, incident, or inherited system.
- A request crosses UI, API, persistence, or runtime boundaries.

## Do not use when

- The requested edit is isolated, already understood, and has no meaningful callers or side effects.

## Inputs

- The requested outcome.
- Repository root and any local instructions.
- Existing documentation, commands, and relevant history.

## Workflow

1. Read repository instructions and current working-tree status.
2. Inventory top-level structure, package manifests, entry points, and test locations.
3. Trace one representative request or workflow from entry point to response, including persistence and external calls.
4. Inspect configuration, migrations, background work, deployment/runtime files, and error handling only where the trace points.
5. Read focused tests to learn asserted behavior and missing boundaries.
6. Inspect history when it explains why a risky area exists or how a workflow evolved.
7. Label each conclusion `CONFIRMED`, `INFERRED`, or `UNKNOWN`.
8. Stop discovery once the requested change can be planned safely. Do not read every file by default.

## Required checks

- Identify entry points and owning modules.
- Identify data stores, external dependencies, and state boundaries.
- Trace at least one relevant path end to end.
- Separate documentation claims from implementation evidence.
- Report unknowns that could change the plan.

## Common failure modes

- Treating folder names as architecture evidence.
- Reading only the target file and missing callers or persistence.
- Confusing a test double with runtime behavior.
- Presenting an inference as a confirmed fact.

## Output contract

```text
SYSTEM SUMMARY
ENTRY POINTS
COMPONENTS AND BOUNDARIES
DATA FLOW
PERSISTENCE AND EXTERNAL DEPENDENCIES
TESTING AND RUNTIME
CONFIRMED FACTS
INFERENCES
UNKNOWNS
RISKS
```

## Example

For a request to change an approval rule, trace the request handler, decision service, state model, persistence write, consumer query, and the tests that cover terminal states.
