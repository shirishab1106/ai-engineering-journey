Suppose the AI marks a customer's email as “low priority,” but the customer says their account has been compromised. What could go wrong, and how would you design the system to reduce that risk?

Think about the failure, the impact, the safeguards, and how you would test them. This will start developing the risk-aware system-design thinking expected of an AI Agent Engineer.

My answers :
If the customer priority is high but considered as low then as per technical details review the model,its context and system messages and categorization. identlfy which category or wording caused to consider it as low priority and adjust or fix that business goal is address the customer concern with appropriate care and concerns which should not effect the business outcomes
1. Review of your answer

What you got right

Investigate the model's context and system instructions.

Examine the categorization and wording that may have caused the error.

Connect technical quality to the business goal of caring for customers and protecting business outcomes.

What is missing

Immediate mitigation: How do we protect the customer before the root cause is fixed?

A reliable safeguard: Should a single AI classification determine priority?

Testing: How do we confirm that the fix works and doesn't create new errors?

Measurement: How do we know whether the problem is happening repeatedly?

Example :
2. Think in three layers

Imagine a customer writes:

“Someone has accessed my account without permission, and I can no longer log in.”

The AI classifies this as low priority because it interprets the message as a routine login problem.

Here's how an engineer should approach it.

Layer 1: Protect the customer now

Do not wait for a model improvement. Add a deterministic safety rule or escalation path for explicit account-compromise indicators. Flag the email for urgent human review and follow the company's approved account-security procedure.

Layer 2: Investigate the root cause

Inspect the input email, system instructions, classification schema, model output, and relevant logs. Determine whether the model misunderstood the wording, the priority definitions were unclear, or the business rules failed to escalate the case.

Layer 3: Fix and validate

Add this email to a regression test set. Improve the instructions or classification logic if needed, then test account compromise, routine login trouble, ambiguous messages, and other priority levels before deploying the change.

One important distinction: don't assume the prompt is always the cause. The problem could be an ambiguous priority definition, missing business rules, incorrect data, or a failure in the routing code.

3. Improve your engineering approach

Your original approach was essentially:

Review the model and context.

Identify the cause.

Adjust the instructions or categorization.

Protect the business outcome.

A stronger production approach adds two steps at the beginning and one at the end:

Contain the risk so the customer isn't left waiting.

Investigate the failure using the input, output, rules, and logs.

Identify the root cause rather than assuming it is a prompt issue.

Implement the fix in the appropriate layer.

Run regression tests to check both the original failure and related cases.

Monitor results to see whether the error rate decreases.

For an AI Agent Engineer, the key is to build a system that can tolerate occasional model mistakes—not to assume that better prompting will eliminate every mistake.

# Failure Analysis — Incorrect Priority Classification

## Scenario

A customer reports possible unauthorized access to their account. The AI classifies the email as low priority instead of escalating it for urgent review.

## Potential impact

* The customer may experience further account compromise.
* The security team may not be notified promptly.
* Customer trust and business reputation may be damaged.
* The business may incur additional recovery or incident-response costs.

## Immediate mitigation

Route emails containing credible account-compromise indicators to an urgent human-review path, regardless of a low priority predicted by the model. Follow approved security procedures and avoid taking unauthorized account actions automatically.

## Root-cause investigation

Inspect the original email, system instructions, priority definitions, model output, structured-output validation, escalation rules, and relevant processing logs.

Determine whether the error originated from language interpretation, ambiguous requirements, incomplete business rules, or a software defect.

## Corrective action

Implement the appropriate fix in the layer responsible for the failure. This might involve clarifying priority definitions, improving examples in the evaluation dataset, adding deterministic escalation rules, or correcting application logic.

## Validation

Add the failure case to a regression test suite. Test similar account-security messages, routine login problems, ambiguous emails, and other priority categories.

Compare results against human-reviewed labels and verify that urgent cases are escalated correctly.

## Monitoring

Track missed urgent cases, false urgent alerts, human overrides, and processing failures. Review recurring mistakes and refine the system based on evidence.

## Key lesson

AI output should inform business decisions, but high-impact decisions require suitable safeguards. A reliable system combines language understanding, deterministic controls, human oversight, testing, and monitoring.
