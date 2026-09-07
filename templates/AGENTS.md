# Project

Describe what the system does, its users, and its primary outcome.

## Architecture

List the major components, entry points, data stores, external services, and ownership boundaries.

## Important Invariants

- List conditions that must always remain true.
- State which layer enforces each invariant.
- Identify data or workflow states that must never be exposed or published.

## Engineering Constraints

- Record scope limits and non-goals.
- Name files, systems, or contracts that require explicit approval to change.
- State any deployment, privacy, or compatibility constraints.

## Commands

Document the repository-approved commands for:

- local development
- focused tests
- full test suite
- linting and formatting
- build and deployment checks

## Testing

Run the smallest relevant checks first. Expand coverage when the change affects shared behavior, persistence, contracts, or runtime configuration. State what was not verified.

## AI / LLM Rules

- Keep validation, authorization, state changes, and side effects deterministic.
- Require structured, validated model output before it affects application behavior.
- Define safe fallback and failure behavior.
- Treat retrieval and generation as separately testable stages.
- Add or update evaluation cases when AI behavior changes.

## Definition of Done

- Requirement satisfied within scope.
- Relevant tests and checks run.
- Failure paths considered.
- No unrelated changes.
- Final diff reviewed.
- Documentation updated when needed.
- Unverified work reported explicitly.
