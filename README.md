# Reusable Engineering Skills

This repository contains small, reusable engineering workflows for AI coding agents.

They came from recurring patterns in building and reviewing production-style software and AI systems. Each skill turns a repeatable piece of engineering judgment into an executable workflow: what to inspect, what to verify, where agents commonly fail, and what to report.

The collection is intentionally small. A skill is useful only when it changes an agent's decisions or prevents a recurring mistake. These are not framework manuals or generic style guides.

## Skills

| Skill | Purpose |
| --- | --- |
| [repository-evidence-map](skills/repository-evidence-map/SKILL.md) | Build an evidence-backed model of an unfamiliar repository. |
| [change-impact-plan](skills/change-impact-plan/SKILL.md) | Plan the smallest coherent change before editing code. |
| [stateful-workflow-safety](skills/stateful-workflow-safety/SKILL.md) | Design and review multi-step, stateful, or asynchronous workflows. |
| [deterministic-llm-boundary](skills/deterministic-llm-boundary/SKILL.md) | Decide what application code must own versus what an LLM may judge. |
| [retrieval-answer-evaluation](skills/retrieval-answer-evaluation/SKILL.md) | Diagnose retrieval, context, generation, and evidence separately. |
| [failure-path-release-verification](skills/failure-path-release-verification/SKILL.md) | Verify a change honestly before calling it complete. |

## How I use them

```text
Requirement
    ↓
Repository Evidence Map
    ↓
Change Impact Plan
    ↓
Implementation
    ↓
Relevant domain skill
    ↓
Failure-Path Release Verification
```

Domain skills are invoked only when they fit the work. A stateful workflow change may use `stateful-workflow-safety`; a retrieval feature may use `retrieval-answer-evaluation`. They are composable, not a mandatory checklist for every edit.

Example: for “add approval expiration to a review workflow,” I would first map the repository, plan the contract and state changes, apply the workflow-safety skill, implement the smallest change, then verify failures and recovery paths.

## AGENTS.md vs. skills

`AGENTS.md` is repository-specific: architecture, local constraints, commands, and invariants.

Skills are portable: they describe how to perform recurring engineering work well. Copy the [template](templates/AGENTS.md) into a repository, then use these skills alongside its local guidance.

### Start with the AGENTS.md template

The [AGENTS.md template](templates/AGENTS.md) is a short repository map for coding agents. Fill it with the project's purpose, architecture, invariants, local commands, testing expectations, and any AI-specific boundaries. Keep it specific to that repository; it should point agents to the right context, not replace the repository's documentation.

## Templates and Prompt Library

Skills are reusable engineering workflows that agents can invoke. Prompts are lightweight entry points for interactive work. Templates are consistent artifacts created during engineering work.

- [implementation-plan.md](templates/implementation-plan.md): a structure for planning non-trivial changes before implementation.
- [plan-feature.md](prompts/plan-feature.md): use before implementation.
- [debug-systematically.md](prompts/debug-systematically.md): use when the cause of a failure is uncertain.
- [review-change.md](prompts/review-change.md): use after implementation before merge or release.

## Principles

- Evidence before assumptions.
- Prefer the smallest coherent change.
- Deterministic rules before probabilistic reasoning.
- Treat failure paths as first-class behavior.
- Verification is part of implementation.
- Never claim testing that was not performed.
- AI output still requires engineering judgment.

AI can accelerate implementation. It does not replace responsibility for architecture, correctness, or verification.
