---
name: retrieval-answer-evaluation
description: Evaluate retrieval-augmented answers by separating corpus, retrieval, context, generation, evidence, and no-answer behavior.
---

# Retrieval Answer Evaluation

## Purpose

Diagnose RAG and search changes without collapsing every bad answer into a prompt problem.

## Use when

- Building, changing, or debugging search, retrieval, ranking, context assembly, citations, or generated answers.

## Do not use when

- The feature does not retrieve knowledge or generate an answer from retrieved context.

## Inputs

- Representative questions, expected evidence, corpus rules, retrieval policy, and answer contract.
- Existing evaluation data, telemetry, tests, or manually verified examples.

## Workflow

1. Define the answer boundary: which corpus and source states are eligible.
2. Select representative cases: direct match, paraphrase, partial coverage, no-answer, and adversarial or unrelated query.
3. Inspect corpus admission before changing retrieval. Missing or poor knowledge is not a ranking defect.
4. For each case, record retrieved candidates, rank order, filtering decisions, and selected context.
5. Evaluate context for sufficiency, relevance, duplication, metadata boundaries, and contamination.
6. Evaluate the generated answer separately for correctness, support, completeness, uncertainty, and refusal behavior.
7. Verify citations or supporting references actually support important claims.
8. Find the earliest failing stage and change that stage, not only the prompt.
9. Add or update a compact representative evaluation set when the repository supports it.

## Required checks

- Relevant evidence is retrieved and ranked high enough.
- Irrelevant evidence is filtered.
- Context is bounded and source-aware.
- The answer does not exceed evidence.
- Partial and no-answer behavior are explicit.
- Evidence presentation is truthful.

## Common failure modes

- Fixing retrieval with a more restrictive generation prompt.
- Measuring only answer fluency.
- Treating top-k candidates as evidence without checking them.
- Making thresholds looser to force results.
- Claiming citations support an answer without inspecting them.

## Output contract

```text
TEST CASE
CORPUS QUALITY
RETRIEVAL RESULT
RANKING RESULT
CONTEXT QUALITY
ANSWER QUALITY
CITATION / EVIDENCE QUALITY
NO-ANSWER BEHAVIOUR
ROOT CAUSE
RECOMMENDED CHANGE
NOT VERIFIED
```

## Example

For a paraphrased question, first check whether the right passage entered the candidate set. If it did not, investigate embeddings or filters before changing the answer prompt.
