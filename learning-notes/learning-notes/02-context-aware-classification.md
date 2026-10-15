Suppose we add a rule that automatically marks every email containing the word “urgent” as high priority.
That may catch some important emails—but it could also flag routine messages such as “This is not urgent.”
How would you design a better solution that catches genuine urgent cases without sending too many routine emails for urgent review?

# Context-Aware Classification and Risk-Based Routing

## Problem

An AI system may classify an important customer email as low priority because it misunderstands the situation or misses important context.

A keyword-based solution is insufficient because the same words can appear in routine and serious situations.

## Proposed solution

1. Preserve the complete original email.
2. Use an LLM to interpret the customer's intent, situation, impact, and time sensitivity.
3. Produce a structured classification with a summary, category, priority, supporting evidence, and recommended action.
4. Validate the output against a defined schema and approved business rules.
5. Apply additional checks for high-impact cases and conflicting assessments.
6. Route uncertain or potentially serious cases to human review.
7. Record outcomes and evaluate errors using a labeled test dataset.

## Why use examples?

Few-shot examples can demonstrate how the model should distinguish similar situations. For example, a routine password reset and a suspected account takeover require different handling.

Examples guide model behavior but cannot guarantee correctness.

## Why not rely only on a second model call?

A second assessment may catch errors, but it can also repeat the original model's mistake. Use targeted verification alongside independent safeguards, human review, and regression testing.

## Evaluation metrics

- Recall for urgent or high-impact cases.
- Precision for urgent classifications.
- Correct category and priority rates.
- Human override rate.
- Percentage of emails requiring manual correction.
- Processing latency and cost.

## Engineering principle

Classify the customer's situation rather than relying on individual keywords. Combine contextual AI analysis with deterministic safeguards, human oversight, and measurable evaluation.

## Open questions

- How should the system handle conflicting priority signals?
- How can we measure uncertainty reliably?
- Which cases require mandatory human review?
- How can we test for missed urgent cases before deployment?
