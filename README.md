# LLM-Evals-Basics
Vibe testing
Vibe testing means casually trying an LLM app with a few prompts and judging it by feel.
Basically:
"I asked it 5–10 questions, the answers looked good, so I think it works."
It is informal, subjective, and usually not repeatable.
And it only works at a personal project level!

AI ENGINEER
An AI engineer is someone who builds applications and products on top of foundation models

What are LLM Evals?
Wednesday, 17 June 2026 11:33 AM
LLM evals are systematic, repeatable tests used to judge an LLM or LLM-powered system against a clear criteria.
Systematic
It should not be random prompting.
Instead of asking 5 questions casually and saying "looks good," we create planned test cases.
For example:
• 100 real student doubts for a CampusX course assistant.

Repeatable
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
Would you like me to list the practical questions typically cut off at the bottom of this slide, or would you like to deep dive into one of the setup elements like choosing a testing tool?

• Can the model be used for a particular task/application?
• Is this system good enough to ship?
• Did prompt v2 improve over prompt v1?
• Is the RAG answer grounded in the retrieved context?
• Is the agent completing the task correctly?
• Is the chatbot safe for real users?
• Is the latency under control?


<img width="588" height="306" alt="image" src="https://github.com/user-attachments/assets/7b577918-3034-493e-80f4-d014edab7ca7" />

Model Evals vs Application Evals

Model Evals
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
LLM APPLICATION EVAL WORKFLOW:
<img width="896" height="1200" alt="image_c7e92071" src="https://github.com/user-attachments/assets/80900ee9-b1d5-4c4a-a776-c6ee24b0e4d9" />

<img width="896" height="1200" alt="image_c7e92071" src="https://github.com/user-attachments/assets/d5cc2c02-d11e-47bd-8baa-c238224dc9d8" />

<img width="1529" height="704" alt="image_ce9b61c5" src="https://github.com/user-attachments/assets/a0d34d93-d693-4eb6-99f9-aa559fac5542" />
One LLM-based application can have several LLM evals.

<img width="819" height="341" alt="image" src="https://github.com/user-attachments/assets/91742d7b-97fa-4d69-9027-8531950107a9" />

