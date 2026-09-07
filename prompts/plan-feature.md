# Plan a Feature

Do not write code yet.

First understand the requirement and inspect the repository before proposing a change. Read repository guidance, including `AGENTS.md`, and use `repository-evidence-map` if the codebase is unfamiliar. Use `change-impact-plan` for the planning work. Invoke other domain skills only when relevant.

1. Trace the current behavior through relevant entry points, callers, consumers, contracts, persistence, state, async work, and external integrations.
2. Distinguish confirmed facts from inferences and unknowns.
3. Identify edge cases, failure paths, compatibility risks, security implications, and observability needs.
4. Propose the smallest coherent change. Do not add abstractions or unrelated cleanup without repository evidence.
5. Define focused tests, broader regression checks where justified, and manual verification where automation is insufficient.

Return only:

```text
REQUIREMENT UNDERSTANDING
CURRENT BEHAVIOUR
REPOSITORY EVIDENCE
AFFECTED COMPONENTS
PROPOSED PLAN
TECHNICAL DECISIONS
EDGE CASES
FAILURE PATHS
TEST PLAN
OUT OF SCOPE
ASSUMPTIONS / UNKNOWNS
RISKS
```

Do not implement anything yet. Stop after presenting the plan.
