---
name: deterministic-llm-boundary
description: Assign deterministic application responsibilities and LLM judgment deliberately in AI-assisted features.
---

# Deterministic LLM Boundary

## Purpose

Prevent probabilistic model output from controlling decisions that code can make exactly and safely.

## Use when

- Adding or changing LLM-assisted extraction, classification, summarization, review, or agent-like behavior.
- A model output could affect data, permissions, money, workflow state, or user trust.

## Do not use when

- The work has no model interaction or semantic judgment requirement.

## Inputs

- Requested model capability and decision consequences.
- Existing contracts, validators, side effects, provider limits, and failure behavior.

## Workflow

1. List every decision and side effect in the requested flow.
2. For each one, ask whether validation, exact matching, schema enforcement, authorization, calculation, deduplication, parsing, database constraints, or explicit rules can solve it.
3. Assign those deterministic responsibilities to application code.
4. Assign only genuine semantic judgment, ambiguous classification, summarization, semantic comparison, or unstructured extraction to the model.
5. Require structured output and validate it before it affects any application behavior.
6. Define confidence, human-review, fallback, timeout, retry, and safe-failure behavior in proportion to consequence.
7. Keep model input/output, prompt version, provider failure category, latency, and cost observable without logging sensitive content unnecessarily.
8. Verify the model cannot directly perform an irreversible effect.

## Required checks

- Model output is treated as untrusted input.
- Deterministic rules own authorization, state transitions, and side effects.
- Structured output is validated at the boundary.
- Failure and fallback behavior is explicit.
- Human review exists when semantic uncertainty has material consequences.

## Common failure modes

- Asking an LLM to enforce rules the database or code can guarantee.
- Parsing free-form prose into production actions.
- Letting a model choose retries, permissions, or publication state.
- Treating confidence as proof.
- Hiding provider failures behind a fabricated success.

## Output contract

```text
DECISION
DETERMINISTIC RESPONSIBILITIES
LLM RESPONSIBILITIES
WHY
VALIDATION BOUNDARY
FAILURE BEHAVIOUR
FALLBACK / HUMAN REVIEW
OBSERVABILITY
COST / LATENCY CONSIDERATIONS
```

## Example

For claim review, code checks required fields and policy rules; the model identifies possibly ambiguous claims; application code routes material ambiguity to a reviewer.
