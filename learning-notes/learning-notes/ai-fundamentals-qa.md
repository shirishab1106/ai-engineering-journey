# AI Fundamentals — Questions and Answers

**Learning stage:** AI Engineering Foundations  
**Review status:** First review completed  
**Purpose:** Interview preparation and quick revision

## Q1. What is the difference between AI, Generative AI, and an LLM?

**Answer:**
- **Artificial Intelligence (AI):** The broader field of building systems that perform tasks associated with intelligence.
- **Generative AI:** AI that generates content, such as text, images, audio, or code.
- **Large Language Model (LLM):** A model trained to process and generate language.

An LLM can answer general questions. It does not automatically restrict its answers to documents supplied by an application.

Providing documents in a prompt is not the same as training or fine-tuning the model.

## Q2. How does an LLM generate a response?

**Answer:**

1. The application assembles the instructions, relevant conversation history, and user message.
2. The text is converted into tokens.
3. The model processes the tokens using its learned neural-network parameters.
4. The model estimates probabilities for the next token.
5. A decoding method selects the next token.
6. The process repeats until the response is complete or a stopping condition is reached.

An LLM is not simply searching a database for a stored answer.

## Q3. What is a token?

**Answer:**

A token is a unit of text processed by a language model. It might represent a word, part of a word, punctuation, or another text unit.

There is no fixed relationship between a token and a word or character. Tokenization varies with the text, language, and tokenizer.

## Q4. What is a context window?

**Answer:**

A context window is the amount of tokenized input and output a model can handle in a request, subject to that model's limits.

It is not the same as long-term memory. The application controls which conversation history and documents to include. It may summarize older messages, remove irrelevant history, or retrieve useful information.

## Q5. What is prompting, and how is it different from training?

**Answer:**

Prompting means giving the model instructions, context, examples, and a task at inference time.

Training changes model parameters using training data. Fine-tuning is a form of additional training for a particular purpose.

A useful prompt specifies:
- The task and objective
- Relevant context
- Required output fields and formats
- Allowed categories or values
- What to do when information is missing
- Examples, when helpful

**Prompting approaches:**
- Zero-shot: no examples
- One-shot: one example
- Few-shot: a small number of examples

For production systems, a concise, verifiable explanation is often more useful than relying on an unverified model rationale.

## Q6. What is the difference between chunking, embeddings, vector search, and RAG?

**Answer:**

- **Chunking:** Splits a document into smaller, manageable pieces.
- **Embedding:** Converts text into a numerical vector representing aspects of its meaning.
- **Vector index:** Organizes vectors so that similar items can be searched efficiently.
- **Similarity search:** Finds vectors close to the query vector according to a similarity measure.
- **Retrieval:** Selects relevant content for use in answering a question.
- **RAG (Retrieval-Augmented Generation):** Retrieves relevant information and supplies it to an LLM to help generate a grounded answer.

**Typical RAG flow:**

1. Split documents into chunks.
2. Generate embeddings for the chunks.
3. Store the vectors and associated text.
4. Embed the user's query.
5. Retrieve relevant chunks.
6. Send the question and retrieved context to the LLM.
7. Return the answer, ideally with supporting sources.

There is no universal minimum chunk size, such as 748 tokens, that every embedding requires.

## Q7. How can an AI application reduce hallucinations?

**Answer:**

- Provide reliable, relevant source data.
- Instruct the model not to invent missing facts.
- Require it to indicate when evidence is insufficient.
- Validate the response with application code.
- Use trusted systems for authoritative facts.
- Evaluate answers against known examples.
- Escalate high-risk or uncertain cases to a human.

Temperature settings do not guarantee factual accuracy. Fine-tuning is not the first solution when the real problem is missing or outdated information.

For example, use an order database—not an LLM's guess—to determine whether an order has shipped.

## Q8. Which tasks should use an LLM, and which should use ordinary code?

**Answer:**

Use an LLM for tasks that benefit from language understanding, such as:
- Summarizing customer messages
- Classifying unstructured text
- Extracting information from emails
- Drafting a response

Use ordinary code for predictable operations, such as:
- Validating fields and data types
- Mapping a category to a support team
- Checking permissions
- Saving records to a database
- Enforcing business rules

**Principle:** Use AI for interpretation and deterministic code for predictable execution.

## Q9. Why not send an entire document to an LLM for every question?

**Answer:**

Sending a large document with every request can:
- Increase token usage and cost
- Increase latency
- Include irrelevant information
- Exceed the model's context limit
- Expose more information than necessary

RAG can retrieve only the most relevant document sections. Sending the entire document may still be appropriate when it is short and the full context is important.

## Q10. How do you ensure an LLM returns reliable structured output?

**Answer:**

1. Define the expected schema.
2. Use structured-output features when available.
3. Validate the response on the backend.
4. Check required fields, data types, allowed values, and business rules.
5. Handle invalid responses with a bounded retry or safe escalation.

Valid JSON does not automatically mean the content is correct. Structural validity and factual correctness must be evaluated separately.

## Q11. How should you test a prompt change?

**Answer:**

1. Create a representative set of test examples with expected results.
2. Run the current prompt against that dataset.
3. Record relevant quality metrics.
4. Change the prompt.
5. Run the same dataset against the new prompt.
6. Compare improvements and regressions.
7. Add tests for newly discovered failure cases.

Do not judge a prompt change using only one successful example.

## Q12. How would you design an AI system to process 500 support emails per day?

**Answer:**

**High-level architecture:**

Email integration → Backend service → LLM API → Output validation and business rules → Database and support queue → Agent interface

The system could extract a summary, category, urgency, and suggested next action.

**Reliability requirements:**
- Error handling and bounded retries
- Duplicate-message prevention
- Schema and business-rule validation
- Human review for high-risk or uncertain cases
- Monitoring and logging
- Access controls and protection of customer data

**Useful metrics:**
- Classification accuracy
- Missed urgent cases
- Human correction rate
- Processing time
- End-to-end latency
- Cost per email

**Key design principle:** The LLM should assist with understanding the email; trusted application logic should control consequential actions.

---

## Reflection

**Concepts I understand well:** Update after each review.

**Concepts I need to revisit:** Update after practice and testing.

**Practical application:** Build an AI Request Analyzer that extracts structured information from support emails and validates the result.

**Next review:** Re-answer the questions without looking at these notes, then check the answers and record any gaps.
