Problem Statement : Imagine a business receives 500 customer support emails every day.

Answer these questions in your notes:

What problem are we trying to solve?
customer efficieny work or organising the custom suppot system based on request,prioroty,validity and genuine andmany other factors and increase the productivity of a customer agent

Which steps require understanding natural language?
summarizing the emails and seggregatig the emails based on the content and responing back with the necessary output

Which steps can use normal programming rules?
inputing the emails and sending an automated emails

What information should the application produce?
proper email to customer and also proper organised flow for customer support system so that they cannot mis any of the eamils which helps them in ganing trust for company
How will we know whether the result is correct?
may be based on the customers response and if its aproducts sales of products or appreciations received

Review / Corrections :
1. Review of your answers

Question 1: What problem are we trying to solve?

Good direction

You identified productivity, request prioritization, and organizing support work. Those are relevant business goals.

What to improve: Describe the current problem and the measurable outcome, rather than listing possible features such as validity checks and prioritization.

A stronger answer would be:

“The business receives 500 support emails daily. Manually reviewing, categorizing, prioritizing, and routing this volume can be time-consuming and may cause delays or missed requests. We want to help support agents process emails faster, prioritize urgent issues, route requests to the right team, and ensure every email is tracked.”

Question 2: Which steps require understanding natural language?

Partially correct

Summarizing and categorizing are good examples. Responding to customers may also require language understanding, but it is a separate capability and should not automatically happen for every email.

Consider these language-understanding tasks:

Identifying what the customer wants.

Summarizing the issue.

Classifying the request, such as billing, refund, technical support, or shipping.

Understanding urgency and customer sentiment.

Extracting details such as order numbers, dates, and product names.

Drafting a relevant reply when appropriate.

Important distinction: understanding an email and deciding what action to take are related, but not the same thing.

Question 3: Which steps can use normal programming rules?

Needs more detail

You mentioned receiving emails and sending automated emails. Those are application operations, but the question is really asking which decisions can be handled reliably by explicit rules rather than an LLM.

Examples:

Receiving emails through an email API or webhook.

Checking required fields and validating email addresses.

Detecting duplicate messages using an email ID.

Assigning a team based on a known category-to-team mapping.

Applying a defined escalation rule for high-priority cases.

Saving results to a database.

Sending notifications, retrying failed requests, and tracking processing status.

For example, if a validated category is billing, ordinary code can route it to the billing queue. The LLM may help identify the category, but code should enforce the routing rule.

Question 4: What information should the application produce?

Good business outcome

You correctly identified organized support workflows and customer trust. Those are outcomes, however, rather than the specific information the application should return.

Think about what an agent needs to see for each email:

A short summary.

Request category.

Priority and urgency reason.

Extracted order number or other relevant details.

Recommended next action.

Suggested response, if appropriate.

Assigned queue or team.

Processing status and a reference to the original email.

These outputs make the system useful to both the support agent and the rest of the application.

Question 5: How will we know whether the result is correct?

Important correction

Customer feedback, sales, and appreciation can be useful business signals, but they don't directly establish whether the AI classified or summarized an email correctly.

A customer may be unhappy even when the system handled the email correctly. Conversely, a customer may be happy despite a wrong classification.

Evaluate the system at two levels:

Technical quality

Is the category correct compared with a human-reviewed answer?

Was the urgency correctly identified?

Were order numbers and dates extracted accurately?

Does the output follow the required schema?

Were all emails processed without duplication or loss?

Business impact

How long does it take to triage an email?

How often are urgent emails missed?

How many emails require manual correction?

Does the system reduce the time agents spend on repetitive tasks?

Customer satisfaction can be a later business metric, but it should not be your only correctness measure.
2. How to think through this kind of problem

As an AI Agent Engineer, don't begin by asking, “Which AI model should I use?” Start by understanding the workflow.

Use this thinking sequence whenever you receive a business problem.

Step 1 — Understand the pain

What is happening today? Who is affected? What is slow, expensive, unreliable, or risky?

For this problem: Agents must manually process a high volume of emails.

Step 2 — Map the workflow

Break the work into individual steps before deciding which technology to use.

For this problem: Receive → understand → classify → prioritize → route → track → respond.

Step 3 — Choose the right approach for each step

Use an LLM when meaning, context, or ambiguous language matters. Use regular code when the rules are explicit and deterministic. Use both when language understanding informs a controlled action.

Step 4 — Define outputs and safeguards

Specify what the system returns, what happens when it is unsure, and which actions need human approval.

Step 5 — Define how you will measure success

Set a baseline, test the system against reviewed examples, and compare results after implementation.

A useful engineering principle is:

Use AI for the parts that need interpretation; use ordinary software for the parts that need predictable execution.

You don't need an autonomous agent for every step. A straightforward LLM application with deterministic routing may solve this problem better than a complex agent. You can introduce agent behavior later if the workflow genuinely requires a model to choose among tools or actions dynamically.

AI Fundamentals — Problem-Solving Exercise 01
Problem: Automating Customer Support Email Triage

Scenario: A business receives approximately 500 customer support emails every day.

Objective: Design an application that helps the customer support team understand, categorize, prioritize, and route incoming emails efficiently while reducing manual work and preventing important requests from being missed.

1. What problem are we trying to solve?

The business receives a large volume of customer support emails daily. Support agents must manually read each email, understand the issue, determine its priority, and route it to the appropriate team.

This process can consume significant time, delay responses, result in inconsistent categorization, and cause urgent emails to be overlooked.

We want to build a system that assists support agents by automatically analyzing incoming emails, extracting relevant information, assigning categories and priority levels, and recommending the next action.

Expected business benefits
Reduce the time spent manually reviewing emails.
Improve consistency in categorization and prioritization.
Identify urgent customer issues more reliably.
Route emails to the correct support team.
Track every email and its processing status.
Allow support agents to focus on complex customer issues.

Initial scope: Assist with email triage and response suggestions. Fully automated customer replies are not required in the first version.

2. Which steps require natural language understanding?

Natural language understanding is useful when the application must interpret the meaning and context of a customer's message.

Examples:

Intent identification: Understand whether the customer is asking for a refund, reporting a technical issue, requesting shipping information, or making a complaint.
Summarization: Produce a short summary of the customer's issue.
Classification: Assign a category based on the email's meaning.
Urgency assessment: Identify signals such as a missed delivery deadline, a service outage, or an account access problem.
Information extraction: Identify order numbers, product names, relevant dates, and other details mentioned in the email.
Response drafting: Suggest a relevant reply using the available information and approved company guidance.

Some decisions, such as whether an issue meets a defined escalation policy, should be enforced by application code after the language model produces its assessment.

3. Which steps can use normal programming rules?

Traditional programming is appropriate when the behavior can be described with explicit, predictable rules.

Examples:

Receive emails through an email provider API or webhook.
Validate required fields and check that the email content is available.
Detect duplicate messages using a stable message identifier.
Call the AI service and validate its response.
Map categories to predefined support queues.
Apply escalation rules to issues identified as urgent.
Store the original email, analysis, processing status, and timestamps.
Retry temporary failures and log errors.
Notify support agents when manual review is needed.
Send a customer reply only when the relevant authorization and approval rules are satisfied.

Example: The AI identifies an email as billing. The application uses a predefined rule to route that email to the billing team.

The model interprets the message; the application enforces the routing rule.

4. What information should the application produce?

For each email, the application should produce a structured result containing:

Original email ID
Short summary
Request category
Priority level
Reason for the assigned priority
Extracted details, such as order number or requested delivery date
Recommended next action
Suggested customer response, when appropriate
Assigned support team
Processing status
Whether human review is required
Example output

This is an illustrative result, not an actual model evaluation.

{
  "email_id": "EMAIL-1001",
  "summary": "Customer's laptop delivery is delayed and they need it before a business trip.",
  "category": "shipping",
  "priority": "high",
  "priority_reason": "The customer has a time-sensitive delivery requirement.",
  "extracted_details": {
    "product": "laptop",
    "delivery_deadline": "Friday"
  },
  "recommended_action": "Check shipment status and available delivery options.",
  "assigned_team": "shipping_support",
  "human_review_required": true,
  "status": "awaiting_review"
}

The output should follow a defined schema so that the backend, user interface, database, and other services can process it consistently.

5. How will we know whether the result is correct?

We should evaluate both the technical quality of the AI output and the business impact of the application.

A. Technical evaluation

Create a test dataset of representative customer emails and have support experts label the correct category, priority, and relevant extracted information.

Compare the application's output against these reviewed answers.

Measure:

Classification accuracy: How often is the predicted category correct?
Urgent-case recall: How many genuinely urgent emails does the system identify? Missing an urgent case can be more harmful than incorrectly flagging a routine email.
Extraction accuracy: Are order numbers, dates, and other important details correct?
Summary quality: Does the summary preserve the customer's main issue and important constraints?
Schema validity: Does the response follow the expected structure and allowed values?
Reliability: Are emails processed without unintended loss or duplicate actions?
Latency and cost: How long does processing take, and what does it cost per email?
B. Business evaluation

Compare the workflow before and after introducing the application.

Measure:

Average time required to triage an email.
Time until an urgent email is assigned.
Percentage of emails requiring manual correction.
Percentage of emails successfully routed to the correct team.
Number of missed or unprocessed emails.
Support agent satisfaction and customer satisfaction.

Customer feedback and sales outcomes can provide additional business signals, but they do not independently prove that an AI classification or summary is correct.

C. Failure scenarios

Test emails that are:

Empty or malformed.
Ambiguous or missing important information.
Very long or contain multiple issues.
Written with sarcasm or contradictory statements.
Designed to manipulate the model through instructions embedded in the email.
Associated with an unavailable AI service or invalid response.

The system should handle uncertainty safely, preserve processing status, and route appropriate cases for human review.

6. Initial architecture
Incoming Customer Email
          |
          v
Email Ingestion Service
          |
          v
Validation and Duplicate Check
          |
          v
LLM Analysis
          |
          v
Structured Output Validation
          |
          v
Business Rules and Routing
          |
          v
Database / Support Queue
          |
          v
Agent Review and Suggested Reply

If analysis fails, the application should record the failure and retry where appropriate, or route the email to a safe manual-review queue.

The initial version does not require a fully autonomous AI agent. A conventional backend, an LLM API, schema validation, and deterministic business rules are sufficient to validate the core idea.

7. Assumptions and open questions

Before implementing a production solution, clarify:

Which email platform does the business use?
What categories and priority levels already exist?
What qualifies as urgent?
Which team owns each category?
Is the AI allowed to draft replies, send replies, or only recommend actions?
What customer data can be sent to the model provider?
How long must emails and analysis results be retained?
What should happen when the model is uncertain?
What baseline metrics will be used to measure improvement?

These are requirements to investigate, not facts we should assume.

8. Key engineering lesson

A useful AI application is not just a model that generates text. It is a complete software workflow that combines language understanding, validated outputs, deterministic business logic, data persistence, error handling, security, and measurable evaluation.

The goal is not to use AI for every step. The goal is to use AI where it adds value and ordinary software where predictable behavior is essential.

9. Learning reflection

My initial understanding: I focused on improving customer support productivity, organizing emails, and sending responses.

What I learned: I need to distinguish the business problem, language-understanding tasks, deterministic application logic, structured outputs, and evaluation metrics.

Questions to investigate next:

How do LLMs return structured JSON?
How can we validate model outputs?
How should we handle uncertain classifications?
How can we evaluate a model using a labeled test dataset?

Status: Reviewed first draft — not yet implemented or evaluated against real emails.