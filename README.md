# LLM-Evals-Basics

###  Vibe testing

Vibe testing means casually trying an LLM app with a few prompts and judging it by feel.

Basically:
"I asked it 5–10 questions, the answers looked good, so I think it works."

It is informal, subjective, and usually not repeatable.
And it only works at a personal project level!

### AI ENGINEER
An AI engineer is someone who builds applications and products on top of foundation models

### What are LLM Evals?

LLM evals are systematic, repeatable tests used to judge an LLM or LLM-powered system against a clear criteria.
Systematic

It should not be random prompting.

Instead of asking 5 questions casually and saying "looks good," we create planned test cases.

For example:

• 100 real student doubts for a CampusX course assistant.

### Repeatable

The same eval should be runnable again.

If we change the prompt, model, retriever, chunking strategy, or system instruction, we should be able to run the same test again and compare results.

This is how we know whether the system improved or became worse.

Clear criteria

We must define what good means.

For example, for a CampusX course assistant, a good answer should be:

• correct

• Simple explanation

• grounded in course content

• safe and policy-compliant

Without criteria, we are only judging by vibes.

An eval is not just a metric. An eval is the complete testing setup. It includes:

• What are we evaluating?

• What does good mean?

• What test cases are we using?

• How are we judging the output?

• When are we running it?

• Which tool are we using?

We are talking about the complete process of testing an LLM-powered system in a structured way.

The goal is not just to get a score. The goal is to answer practical questions like:

• Can the model be used for a particular task/application?

• Is this system good enough to ship?

• Did prompt v2 improve over prompt v1?

• Is the RAG answer grounded in the retrieved context?

• Is the agent completing the task correctly?

• Is the chatbot safe for real users?

• Is the latency under control?


<img width="588" height="306" alt="image" src="https://github.com/user-attachments/assets/7b577918-3034-493e-80f4-d014edab7ca7" />

### Model Evals vs Application Evals

### Model Evals

Model evals evaluate the model itself. The main idea is to test and evaluate the capabilities of a model.

<img width="971" height="383" alt="image" src="https://github.com/user-attachments/assets/d8cdcd1f-bc9b-4e4b-b92b-fb46d697cc54" />

Model capabilities are generally evaluated using Benchmarks. Some famous benchmarks include:

<img width="975" height="617" alt="image" src="https://github.com/user-attachments/assets/67271aa6-1159-4a90-9ae6-e94982555ad0" />

<img width="975" height="587" alt="image" src="https://github.com/user-attachments/assets/d65cca65-bd25-4534-88b5-f694f4b22fe0" />

Application evals assess the behaviour and performance of an LLM-powered application, whether at the level of the entire system or a specific component within it.

In application eval we don't ask:

Can the model do this?

Instead application eval tells whether the product works.

For example, suppose we build a CampusX course assistant.

Application evals ask:

• Did it answer the student's question correctly?

• Did it use the course material properly?

• Was the answer faithful to the retrieved context?

• Was it clear for a beginner?

• Did it avoid hallucinating policies?

• Did it respond quickly enough?

• Did it stay safe?

Smart Analogy - Smartphones

### LLM APPLICATION EVAL WORKFLOW:

<img width="896" height="1200" alt="image_c7e92071" src="https://github.com/user-attachments/assets/80900ee9-b1d5-4c4a-a776-c6ee24b0e4d9" />


<img width="896" height="1200" alt="image_c7e92071" src="https://github.com/user-attachments/assets/d5cc2c02-d11e-47bd-8baa-c238224dc9d8" />

<img width="1529" height="704" alt="image_ce9b61c5" src="https://github.com/user-attachments/assets/a0d34d93-d693-4eb6-99f9-aa559fac5542" />

One LLM-based application can have several LLM evals.

<img width="819" height="341" alt="image" src="https://github.com/user-attachments/assets/91742d7b-97fa-4d69-9027-8531950107a9" />

### LLM Applicaion Eval - Failure Points

<img width="811" height="510" alt="image" src="https://github.com/user-attachments/assets/34bbf6b2-af6e-4d37-a940-266b75d77304" />

<img width="975" height="535" alt="image" src="https://github.com/user-attachments/assets/d2d98dc6-4cec-4e00-ae7c-d494ed5c7ecb" />

### LLM Application Eval - Risk Categories

components / workflow / application

#### Application quality — "Is the answer any good?"

Whether the app does its actual job well: gives correct, relevant, complete answers that do what the user asked. This is the core "does it work" question — the thing the product exists to do.

#### Safety — "Could the answer cause harm?"

Whether the app avoids hurting anyone or exposing anything it shouldn't: no toxic or dangerous content, no bias against groups, no leaking private data, no getting tricked into breaking its own rules. Not about whether the answer is good, but whether it's harmful.

#### Operational — "Is it fast, cheap, and reliable enough to run?"

Whether the app is practical to operate at scale: responds quickly, doesn't cost too much per answer, and doesn't crash or fail under real traffic. Not about what the answer says, but about the system delivering it.
The clean way to hold the three apart: quality is about the content of the answer, safety is about the harm the answer could do, and operational is about the system producing it.

<img width="975" height="741" alt="image" src="https://github.com/user-attachments/assets/6e2da40e-c402-4ce4-8c5e-11c8709cafb6" />

<img width="882" height="359" alt="image" src="https://github.com/user-attachments/assets/a039a15d-17fc-4d2c-8cbf-d354efff4a53" />

<img width="975" height="280" alt="image" src="https://github.com/user-attachments/assets/ad461a18-741e-4982-922f-bc468813a68c" />

<img width="975" height="460" alt="image" src="https://github.com/user-attachments/assets/12b2fb92-75b2-4ddc-ae00-c82452ac9834" />

<img width="854" height="401" alt="image" src="https://github.com/user-attachments/assets/92d75ce6-caa5-4ce7-9f90-7d08e2df4193" />

### LLM Application Evals - Methods

An LLM eval method is the mechanism you use to decide whether an LLM's output is good or not — the actual procedure that takes an output and produces a judgment about it.

#### 1. Programmatic / deterministic — code produces the verdict.

The output is checked against a rule or a known correct answer by a program: exact match, regex, JSON schema validation, or running the output (execute the code, run the SQL) and comparing results.
Fast, cheap, reproducible — but only works where correctness is mechanically checkable.

#### 2. Human — a person produces the verdict.

People rate, rank, or compare outputs directly. The most expensive and slowest, but the gold standard for nuanced, subjective, or high-stakes judgments.

#### 3. Model-graded (LLM-as-judge) — a model(LLM) produces the verdict.

A strong LLM scores or ranks the output against a rubric. Used where there's no single right answer but you can describe what "good" looks like — helpfulness, tone, groundedness.

<img width="923" height="259" alt="image" src="https://github.com/user-attachments/assets/3aa576e8-43ed-408d-8f1a-638cac92fd44" />

<img width="948" height="650" alt="image" src="https://github.com/user-attachments/assets/e38855c1-54ad-44f2-b878-d8d7b790ee7b" />

<img width="916" height="384" alt="image" src="https://github.com/user-attachments/assets/e002b6e6-0c2e-4cb1-bacb-b1c9dfc78962" />

<img width="975" height="372" alt="image" src="https://github.com/user-attachments/assets/c6ab175f-5712-49ab-8274-ae86e5b8c66b" />

<img width="667" height="223" alt="image" src="https://github.com/user-attachments/assets/d792d82d-ddbc-4e92-9aac-e4a0d994d7fc" />

<img width="372" height="231" alt="image" src="https://github.com/user-attachments/assets/26205768-a554-4190-bd53-732cb57c57aa" />

<img width="975" height="517" alt="image" src="https://github.com/user-attachments/assets/f08c84a1-7746-48c3-809b-a9d7be370a09" />

<img width="975" height="619" alt="image" src="https://github.com/user-attachments/assets/ad45f9cd-60d0-4481-af40-82632b535953" />

• Red teaming — actively attacking the system to find failures: crafting jailbreaks, prompt injections, adversarial and edge-case inputs, trying to make it produce harmful or wrong output. Creative adversarial work automated evals can't originate.

• A/B testing — real users as graders in production; their behavior (thumbs-up, task completion, re-asking, escalation) is the verdict on which version is better.

• Direct grading / rating — a person reads outputs and scores them against a rubric (the human-eval pipeline you just built). The most basic role: human as the grader.

• Gold-answer / dataset creator — writing or verifying the correct answers (gold SQL, gold doc IDs, concept rubrics) and curating the test set to cover the real distribution.

• HITL (human-in-the-loop) — a human placed inside the production flow as a checkpoint, reviewing/approving/editing/rejecting live outputs before they reach the user — triggered on the risky slice (low-confidence, high-stakes, or flagged outputs).

### 3. Model-graded (LLM-as-judge) — a model(LLM) produces the verdict.
A strong LLM scores or ranks the output against a rubric. Used where there's no single right answer but you can describe what "good" looks like — helpfulness, tone, groundedness.

<img width="873" height="557" alt="image" src="https://github.com/user-attachments/assets/dc2f9ad7-a944-477c-a284-98b790b64e51" />

<img width="975" height="723" alt="image" src="https://github.com/user-attachments/assets/4f61761f-cdb2-4f1a-a6ce-b700b73976de" />

<img width="825" height="581" alt="image" src="https://github.com/user-attachments/assets/b793e271-43ea-4257-9f4b-7c3f2e6709bd" />

<img width="884" height="567" alt="image" src="https://github.com/user-attachments/assets/ee2fb3e8-cde1-4c9c-a82f-bd387bf00f27" />

### Reference Based Vs Reference Free Evals

### Reference-based

You have a reference — a known-correct answer (or the key things a correct answer must contain) written down in advance for each test case. You grade by comparing the output against that reference.

### Reference-free

You have no predefined correct answer. You judge the output's quality directly, on its own terms, against a criterion or rubric — but a rubric here is a scale/standard ("what does a good answer look like"), not a per-item correct answer.

<img width="1525" height="704" alt="image_b2a08e46" src="https://github.com/user-attachments/assets/d6eae60a-20c7-454c-bfe1-92566ff5cf78" />

### Why do we need Offline Evals

1. Pre-release testing (Gating)

2. Version Comparison
   
3. Regression Testing

### But, what about Post-deployment

1. Unanticipated Inputs (questions mixing Hindi and English, ambiguous half-questions, angry rants with a real question buried inside, adversarial prompt-injection attempts, questions about edge-case scenarios you never considered)

2. Emergent / systemic failures — problems that only exist at scale, under load, over time. (a retrieval index silently lagging its source document, cost per conversation quietly tripling after a prompt change, the latency tail (p99) frustrating a slice of users, a subtle bias that only becomes visible across thousands of conversations, degradation that only appears under real concurrent load.)

### Online Evals Pipeline

<img width="819" height="586" alt="image" src="https://github.com/user-attachments/assets/2eae46e3-fafe-43d6-b178-bf732243bfc4" />

<img width="975" height="616" alt="image" src="https://github.com/user-attachments/assets/24d72e00-cea3-41b2-90bb-0bff45ee170b" />

### Logging

Capture a structured, replayable record of every conversation turn.

Identity/threading: conversation_id, turn_id, user_id/session_id, timestamp.

Input: raw student message, plus any preprocessing (normalized text, detected language/intent).

### Retrieved context

Output: response text, model_name/prompt_version (needed for A/B testing and "which version regressed"), tool calls, finish reason.

Operational telemetry \(\rightarrow \) this is the operational-metric family, captured directly here: latency_ms (ideally split into retrieval vs generation), prompt_tokens, completion_tokens, derived cost, error/status codes.

Downstream user signals \(\rightarrow \) this is the behavioral-metric family, captured directly here: thumbs up/down, escalation to support, drop-off, rephrase, conversion.

### Engineering properties:

• Non-blocking — logging must never add latency to the response; fire to a queue, write in the background.

• Durable + queryable — a warehouse or observability tool you can run analytical queries against, not scattered text logs.


• Late-signal attachment — signals land at different times (thumbs-down in seconds, escalation in an hour, conversion the next day), so records are keyed on conversation_id and updated as signals arrive.

• PII handling — scrub/tokenize emails, phone numbers, payment details; apply retention limits and access control.

### Downstream user signals

this is the behavioral-metric family, captured directly here: thumbs up/down, escalation to support, drop-off, rephrase, conversion.

### Engineering properties:

• Non-blocking — logging must never add latency to the response; fire to a queue, write in the background.

• Durable + queryable — a warehouse or observability tool you can run analytical queries against, not scattered text logs.

• Late-signal attachment — signals land at different times (thumbs-down in seconds, escalation in an hour, conversion the next day), so records are keyed on conversation_id and updated as signals arrive.

• PII handling — scrub/tokenize emails, phone numbers, payment details; apply retention limits and access control.

<img width="867" height="522" alt="image" src="https://github.com/user-attachments/assets/7c8f2158-30a7-4dba-8437-12328828b3a9" />

<img width="1529" height="704" alt="image_d16124e6" src="https://github.com/user-attachments/assets/7aa372a7-b1fd-4a7a-b74a-89c9f88aed9d" />

<img width="975" height="534" alt="image" src="https://github.com/user-attachments/assets/dfd7d2c6-162c-4d19-b892-857e0909d8c7" />
