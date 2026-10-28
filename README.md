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

<img width="1277" height="832" alt="image_7476eda3" src="https://github.com/user-attachments/assets/093c8f06-4961-4cb2-9f10-475e85edffb8" />

<img width="975" height="525" alt="image" src="https://github.com/user-attachments/assets/ab097c8a-e443-4115-9bca-11cbed3d5b07" />

### Self Improving Loop

### Why AI Engineers need Model Evals

1. To compare different models fairly

2. To track whether newer models are actually improving

3. To decide whether a model is safe for release

### What are Model Evals

Model eval is the systematic process of measuring an underlying model's capabilities, behaviour, reliability and operational characteristics under controlled conditions.

At the highest level, every model eval follows the same arc:

1. Decide what to measure — reasoning? coding? safety? instruction-following?

2. Get a test for it

3. Run the model under a fixed protocol — same prompts, same conditions, so results are comparable across models.

4. Score and interpret — turn outputs into a number, then work out what that number actually tells you.

• A public benchmark — a standardized, shared test like MMLU or SWE-bench. Because everyone runs the same test, it's great for comparing models on common ground.

• Your own eval set — data you assemble from your actual task, which measures what you specifically care about rather than what's generically useful.

<img width="1276" height="832" alt="image_e435e28e" src="https://github.com/user-attachments/assets/010c284b-44f2-43ad-9a8c-ae224cd70f67" />

zomato → system → email

You're building a feature that triages incoming customer-support emails — it reads each email and outputs a category (Billing, Bug, Feature Request, Cancellation) plus an urgency level (Low / Medium / High).

You're choosing between two models:

• Model A — big, top-of-the-leaderboard, expensive ($15 / M tokens)

• Model B — smaller, cheaper ($0.50 / M tokens), mid-table on public benchmarks

<img width="722" height="286" alt="image" src="https://github.com/user-attachments/assets/c9fd4bdd-a471-45be-8d1a-e27a61cb01a8" />

### Capabilities

LLM general purpose

#### 1 Knowledge & Reasoning

What this domain measures

This domain measures two things:

• How much factual knowledge the model learned during training.

• Whether it can connect multiple pieces of information and reason through them to reach the correct conclusion.

What comes under it

#### Factual recall across different subjects:

Testing whether the model knows facts from areas such as biology, physics, chemistry, history, law, medicine, economics, and philosophy. This is the most basic test of what the model has learned.

#### Multi-step logical reasoning:

Testing whether the model can combine several facts in the correct sequence. Instead of answering from a single fact, it must follow a chain of reasoning to reach the final answer.

### Why frontier labs evaluate this separately

This domain is commonly used as a proxy for answering the question:

##### How intelligent is this model?

It is also the capability most often discussed by the media and the general public. Frontier labs therefore need to show that their models can match or outperform competitors on widely recognized knowledge and reasoning benchmarks.

Real-world relevance

This capability matters when models are used for:

• Analyzing research papers.

• Answering complex customer questions.

• Writing technically accurate documents.

• Assisting professionals in fields such as law, medicine, science, and finance.

### 2 Coding & Software Engineering

What this domain measures

This domain measures whether a model can write code that actually works.

It also tests whether the model can work inside real software engineering environments involving large codebases, multiple files, development tools, repositories, and complex workflows.

What comes under it

#### Function-level code generation:

Writing individual functions from natural-language instructions. The model must handle edge cases, validate inputs, and follow the required function interface.

#### Real-world bug fixing in existing codebases:

Giving the model a real GitHub issue and an existing repository, then asking it to identify the root cause and create a correct patch without breaking other parts of the software.

#### Multi-file, long-horizon engineering tasks:

Making changes across several files, understanding how different parts of the system depend on each other, and performing tasks such as refactoring or adding new features.

#### What comes under it

• Function-level code generation:

Writing individual functions from natural-language instructions. The model must handle edge cases, validate inputs, and follow the required function interface.

• Real-world bug fixing in existing codebases:

Giving the model a real GitHub issue and an existing repository, then asking it to identify the root cause and create a correct patch without breaking other parts of the software.

• Multi-file, long-horizon engineering tasks:

Making changes across several files, understanding how different parts of the system depend on each other, and performing tasks such as refactoring or adding new features.

• Command-line and system administration:

Completing multi-step tasks through a terminal, such as installing packages, configuring servers, running diagnostic commands, and combining different tools.

• API and function calling:

Making correct API calls with the right parameters, handling errors, and correctly processing the returned results.

• Why frontier labs evaluate this separately

Better coding performance can directly improve developer productivity and create significant business value.

Frontier labs also compete heavily on coding benchmarks because developers are an important customer group and a major source of revenue.

Real-world relevance

This domain matters for:

• Code generation.

• Debugging.

• Code review.

• CI/CD automation.

• Software maintenance.

• General software engineering work.

Coding evaluations often reveal some of the largest performance differences between leading models and weaker ones.

### What comes under it

• Grade-school mathematics and basic arithmetic reasoning:

Solving multi-step word problems by converting natural language into mathematical expressions and carrying out the correct sequence of calculations.

• Competition-level problem solving:

Solving problems from competitions such as AIME. These problems may require creative reasoning, combinatorics, geometry, number theory, and pattern recognition.

• Undergraduate and graduate-level mathematics:

Solving advanced problems from areas such as real analysis, abstract algebra, topology, probability theory, and differential equations. These may require long reasoning chains.

• Research-level mathematical reasoning:

Solving problems close to the frontier of mathematical research, where even expert mathematicians may need several days to arrive at a solution.

### Why frontier labs evaluate this separately

Mathematics provides one of the cleanest tests of genuine reasoning.

There is little room for a plausible-sounding but incorrect answer. This makes mathematical evaluation useful for checking whether a model can perform formal and verifiable reasoning instead of relying only on pattern matching.

Real-world relevance

This capability is important for:

• Scientific computing.

• Financial modelling.

• Engineering simulations.

• Data analysis.

• Any application requiring precise numerical results.

### 4 Long Context

What this domain measures

This domain measures whether a model can effectively use information from very long inputs, sometimes containing hundreds of thousands of tokens.

What comes under it

• Single-fact retrieval from long contexts:

Finding one specific piece of information hidden somewhere inside a very long document.

• Multi-fact co-reference across long texts:

Tracking the same person, entity, concept, or constraint across multiple mentions that appear far apart in a document or conversation.

• Aggregation over long content:

Summarizing, counting, comparing, or identifying patterns using information spread across a large amount of text.

• Code repository understanding:

Navigating a large codebase, understanding relationships between files, and reasoning about cross-file dependencies.

### Why frontier labs evaluate this separately

Context-window size has become an important marketing number:

128K → 200K → 1M tokens

However, a large advertised context window does not guarantee that the model can use all of that information effectively.

Labs therefore need to demonstrate that their models can genuinely use the context capacity they claim to support.

Real-world relevance

Long-context capability matters for:

• Reviewing legal contracts.

• Analyzing academic papers.

• Maintaining large codebases.

• Handling long customer-support conversations.

• Working with large collections of documents.

### 5 Vision & Multimodal

What this domain measures

This domain measures whether a model can understand and reason about visual information along with text.

What comes under it

• Scientific chart and graph understanding:

Reading axes, legends, data points, and trends. The model may need to extract exact values as well as explain the broader meaning of the chart.

• Document and form understanding:

Processing scanned documents, invoices, tables, and forms. The model must understand not only the words but also how the information is arranged on the page.

• GUI and screen understanding:

Understanding computer or mobile-device screens. This includes identifying buttons, menus, dialog boxes, input fields, and the current state of an application.

Why frontier labs evaluate this separately

Vision allows models to handle tasks that text-only systems cannot perform.

It enables new use cases and has become an important area where frontier models can differentiate themselves after many text benchmarks have started becoming saturated.

### Why frontier labs evaluate this separately

Vision allows models to handle tasks that text-only systems cannot perform.

It enables new use cases and has become an important area where frontier models can differentiate themselves after many text benchmarks have started becoming saturated.

Real-world relevance

This capability matters for:

• Processing invoices.

• Analyzing charts and research figures.

• Navigating software interfaces.

• Reading medical images.

• Understanding engineering diagrams.

• Working with visually complex documents.

### 6 Agentic & Tool Use

What this domain measures

This domain measures whether a model can take actions instead of only generating text.

An agentic model may browse the internet, call APIs, manipulate files, execute code, operate software, and complete complex multi-step tasks.

To succeed, the model must plan its actions, choose the right tools, track progress, and recover when something goes wrong.

This is widely considered one of the next major frontiers of AI evaluation.

What comes under it

• Web browsing and persistent research:

Navigating multiple websites, following links, searching for information, and combining findings from many online sources. Some tasks may require visiting dozens or even hundreds of pages.

• Structured tool calling and API interaction:

Using external tools and APIs correctly by selecting the right function, passing valid parameters, handling responses, chaining calls, and recovering from errors.

• Desktop and computer use:

Operating real applications through visual interaction, including clicking, typing, and navigating across word processors, spreadsheets, email clients, and file managers.

• Multi-turn task execution with planning:

Breaking a large goal into smaller steps, completing them in the correct order, checking intermediate results, and adjusting the plan when something fails.

We have now captured the complete set of slides detailing the core evaluation domains

### Why frontier labs evaluate this separately

A model may possess a large amount of knowledge but still be unable to use that knowledge to complete a practical task.

Agentic evaluation measures the difference between:

• What the model knows
and

• What the model can actually do

This gap remains large even among frontier models.

Real-world relevance

Agentic capability is important for:

• Coding agents.

• Research assistants.

• Customer-service bots.

• Data-entry automation.

• Personal assistants.

• Any workflow where the AI must perform actions rather than simply provide an answer.

### 7 Safety & Alignment

What this domain measures

This domain measures whether a model can be trusted to behave responsibly.

It checks whether the model refuses harmful requests, avoids deception and sycophancy, resists adversarial attacks, and continues following safety principles even when a user pressures it to behave differently.

What comes under it

• Refusal of harmful content generation:

Checking whether the model appropriately refuses requests involving cybercrime, violence, harassment, misinformation, and illegal activities.

At the same time, the model should not become so cautious that it refuses harmless or legitimate requests.

• Resistance to adversarial attacks and jailbreaks:

Testing whether the model maintains its safety rules when users attempt to bypass them through prompt injection, role-playing, encoded instructions, or other adversarial methods.

• Truthfulness versus sycophancy:

Checking whether the model gives the correct answer even when it disagrees with the user's beliefs or expectations.

A safe and reliable model should not simply tell users what they want to hear.

• Truthfulness versus sycophancy:

Checking whether the model gives the correct answer even when it disagrees with the user's beliefs or expectations.

A safe and reliable model should not simply tell users what they want to hear.

• Cybersecurity capabilities:

Evaluating whether the model can perform advanced cybersecurity tasks such as cryptography, reverse engineering, digital forensics, and exploitation.

This is especially important for understanding potentially dangerous autonomous capabilities.

Why frontier labs evaluate this separately

Safety is both a regulatory requirement and a major reputational concern.

#### Why frontier labs evaluate this separately

Safety is both a regulatory requirement and a major reputational concern.

Real-world relevance

Any organization deploying an AI model to the public must test whether its safety controls work properly.

This domain directly affects:

• Legal liability.

• Regulatory compliance.

• Brand reputation.

• User trust.

• Responsible deployment.

### 8 Instruction Following

What this domain measures

This domain measures whether a model does exactly what the user asked it to do — no more and no less.

The instructions may include requirements related to format, length, tone, style, structure, or content.

A model may have excellent knowledge but still be frustrating to use if it repeatedly ignores simple instructions.

What comes under it

• Verifiable constraint satisfaction:

Following instructions that can be checked automatically, such as:

   • Staying within a word limit.
	
   • Using bullet points.
	
   • Producing valid JSON.
	
   • Following a markdown structure.
	
   • Using specific section headings.

• Handling ambiguous or incomplete instructions:

Understanding what the user probably wants when the request is underspecified, asking a clarifying question when necessary, and choosing reasonable defaults when appropriate.

### Why frontier labs evaluate this separately

Instruction following strongly affects whether a model feels helpful or frustrating in everyday use.

It is one of the capabilities most directly connected to user satisfaction in real production environments.

Real-world relevance

Almost every practical use of a language model depends on instruction following.

Examples include:

• Generating reports in a required format.

• Writing code according to specific style rules.

• Producing structured JSON outputs.

• Following brand-tone requirements.

• Maintaining coherent multi-turn conversations.
