# Prompt Engineering Techniques

A beginner-friendly collection of prompt engineering techniques. Each technique has examples, one real-world example, and practice tasks.

> **Weak prompt** = vague, leaves the AI to guess.
> **Strong prompt** = clear and specific (role, task, details, format, constraints).

## Table of Contents

1. [Direct Prompting](#1-direct-prompting)
2. [Zero-Shot vs Few-Shot](#2-zero-shot-vs-few-shot)
3. [Chain of Thought](#3-chain-of-thought)
4. [Instruction Prompting](#4-instruction-prompting-high-control)
5. [ReAct (Reason + Act)](#5-react-reason--act)
6. [Tree of Thoughts](#6-tree-of-thoughts)
7. [Directional Stimulus](#7-directional-stimulus)
8. [Iterative Prompting](#8-iterative-prompting)
9. [Data Extraction](#9-data-extraction)
10. [Error Correction](#10-error-correction)
11. [RAG](#11-rag-retrieval-augmented-generation)
12. [Breaking Complex Problems](#12-breaking-complex-problems)
13. [Meta Prompting](#13-meta-prompting)
14. [Perspective Switching](#14-perspective-switching)
15. [Thinking Modes](#15-thinking-modes)
16. [Nested Complexity](#16-nested-complexity)

---

## 1. Direct Prompting

Tell the AI exactly what you want, with a role, details, and format.

**Example 1**

Weak:
```text
List the top 5 countries by population.
```

Strong:
```text
Act as a geography expert.
List the top 5 countries by population.
Include population numbers and rank them in a table.
```

**Example 2**

Weak:
```text
List 5 healthy foods
```

Strong:
```text
Act as a nutrition expert.
Suggest 5 healthy foods for students.
Keep it simple and explain benefits briefly.
Give the answer in bullet points.
```

**Real-world example: ordering at a tea shop**

Saying "Give me tea" gets you a random tea. Saying "One masala tea, less sugar, in a paper cup" gets exactly what you want. AI works the same way.

```text
Act as a travel guide.
Suggest 3 budget-friendly places to visit in Tamil Nadu for a weekend trip.
Give the answer in a table with place name and why to visit.
```

---

## 2. Zero-Shot vs Few-Shot

- **Zero-shot:** no examples, just the instruction.
- **Few-shot:** give examples so the AI learns the pattern.

### Zero-Shot

```text
Classify the sentiment of this review:
'The product quality is great but delivery was very slow.'
```

```text
Classify the sentiment of this sentence as positive, negative, or neutral:
'I really enjoyed the movie but the ending was disappointing.'
```

### Few-Shot

Give examples, and the AI learns the pattern.

```text
Convert feedback into structured JSON

Example 1:
Input: "Amazing service and fast delivery"
Output: { "sentiment": "positive", "confidence": 0.9 }

Example 2:
Input: "Very bad experience, not recommended"
Output: { "sentiment": "negative", "confidence": 0.95 }

Task:
Input: "The product is okay but packaging was poor"
Output:
```

```text
Classify sentiment into positive or negative

Example 1:
'I love this product' → positive

Example 2:
'This is terrible' → negative

Now classify:
'The service was slow but food was good'
```

**Real-world example: training a new shop assistant**

If you only say "sort these customer reviews," the new assistant may be confused (zero-shot). If you first show two reviews already sorted into "Happy" and "Unhappy," they understand quickly (few-shot).

```text
Sort customer reviews into Happy or Unhappy.

Example 1: "Dress fits perfectly, loved it!" → Happy
Example 2: "Colour faded after one wash." → Unhappy

Now sort this review:
"Nice design but the stitching came out in a week."
```

---

## 3. Chain of Thought

Force the AI to think step by step.

Weak:
```text
If a train travels 60 km in 1 hour, how far in 5 hours?
```

Strong:
```text
If a train travels 60 km in 1 hour, how far in 5 hours?
Think step-by-step before answering.
```

**Better real-world example**

```text
You are a financial advisor.
A person earns ₹50,000/month, spends ₹30,000, saves the rest.
Calculate yearly savings and suggest 2 investment strategies.
Explain step-by-step.
```

**Practice:** A prompt where the AI helps someone decide between two options step-by-step.

```text
A student has two options:
Option A: Take a job with ₹10,000/month
Option B: Do a course for 6 months with no income but better future opportunities

Analyze both options step-by-step considering short-term and long-term benefits, risks, and career growth.
Then suggest the better choice with reasoning.
```

**Real-world example: splitting a restaurant bill**

Four friends eat together. The bill has food, tax, and a tip, and one friend did not eat dessert. Working step by step avoids mistakes.

```text
Four friends had dinner. Food cost ₹1,600, tax is 5%, and tip is ₹100.
One friend did not eat the ₹200 dessert, so the other three share it.
Calculate how much each person pays.
Think step-by-step and show every calculation.
```

---

## 4. Instruction Prompting (High Control)

Strictly control AI behavior. This is not asking, it is **controlling**.

```text
Act as a career coach.
Write a cold email to a recruiter for a product management role.

Constraints:
* Keep it under 120 words
* Tone should be confident but not arrogant
* Do not use generic phrases like 'I am passionate'

Output: Professional email format
```

**Practice:** A prompt where the AI writes content with strict rules.

```text
Act as a professional content writer.
Write a short article about the importance of discipline for students.

Constraints:
* Maximum 120 words
* Use simple language
* Do not use motivational clichés
* Include one real-life example

Output format: 1 paragraph
```

**Real-world example: leave letter to a principal**

A leave letter must be short, polite, and in the right format. Rules make sure the AI follows them.

```text
Act as a college student.
Write a leave application to the principal for 2 days because of a family function.

Constraints:
* Maximum 80 words
* Polite and formal tone
* Do not use slang

Output format: Formal letter with date, subject, body, and signature
```

---

## 5. ReAct (Reason + Act)

The AI **thinks → takes action → observes**, in a loop.

```text
Solve the task using a Thought → Action → Observation loop

Task: Compare recent performance of electric vehicles vs petrol vehicles in India

Instructions:
* First think what data is needed
* Then simulate search
* Then analyze
* Then conclude
```

**Insight:** Used in tools like search agents.

**Real-world example: buying a new phone**

Before buying, you think about what matters, check prices and reviews, notice what you find, and then decide. ReAct makes the AI do the same.

```text
Solve the task using a Thought → Action → Observation loop.

Task: Help me choose a smartphone under ₹20,000.

Instructions:
* Thought: what matters most (battery, camera, performance)?
* Action: simulate searching for 3 popular phones in this range
* Observation: note the pros and cons of each
* Repeat if needed, then give a final recommendation
```

---

## 6. Tree of Thoughts

Brainstorming through multiple thinking paths.

```text
Imagine 3 experts solving this problem:
How can a small YouTube channel grow to 100K subscribers in 3 months?

Step 1: Each expert gives a strategy
Step 2: They critique each other
Step 3: Combine into best plan
```

**Practice:** A prompt where multiple experts solve a problem.

```text
Imagine 3 experts discussing how students can improve productivity.
Each expert gives a different idea.
Then they critique each other.
Finally combine the best ideas into one plan.
```

**Insight:** This creates multiple thinking paths.

**Real-world example: planning a college farewell party**

Three friends each suggest a plan, argue about the weak points, and then agree on the best combined plan.

```text
Imagine 3 friends planning a college farewell party on a small budget.
Friend 1 suggests a plan, Friend 2 suggests a different plan, Friend 3 suggests a third plan.
Then they point out the problems in each other's plans.
Finally combine the best parts into one final plan.
```

---

## 7. Directional Stimulus

Give a main instruction plus specific keywords or hints to guide the focus.

```text
Summarize the impact of social media on society
Focus on: mental health, productivity, and relationships
```

**Insight:** You guide the AI's attention.

**Practice:** A prompt where you guide the AI to focus on specific points.

```text
Explain the impact of social media on society.
Focus on mental health, productivity, and relationships.
```

**Real-world example: making exam notes from a news article**

You do not need the whole article. You only need the important points for your exam.

```text
Summarize this news article about the new education policy.
Focus on: key dates, important names, and changes for students.
```

---

## 8. Iterative Prompting

Start with a basic prompt, then improve it step by step.

**Example (powerful)**

| Step | Prompt |
|------|--------|
| Prompt 1 | `Write a motivational speech` |
| Refinement | `Make it emotional and relatable for students facing failure` |
| Final | `Add real-life story and end with a strong call to action` |

**Practice flow**

| Step | Prompt |
|------|--------|
| Prompt 1 | `Write a story` |
| Prompt 2 | `Write a short story about a student overcoming failure` |
| Prompt 3 | `Write a short emotional story about a student overcoming failure with a strong ending` |

**Real-world example: writing a resume summary**

| Step | Prompt |
|------|--------|
| Prompt 1 | `Write a resume summary` |
| Prompt 2 | `Write a resume summary for a fresher applying for a web developer job` |
| Prompt 3 | `Add JavaScript, React, and Node.js skills and keep it under 50 words` |

---

## 9. Data Extraction

Pull structured information out of unstructured text.

**Input text**

> Rahul Sharma is a software engineer with 3 years of experience in web development. He has worked on multiple projects using JavaScript, React, and Node.js. Currently, he is working at a startup as a frontend developer and is interested in learning AI and backend technologies.

**Prompt**

```text
Extract the following from this text:
* Name
* Skills
* Experience

Output: JSON format
```

**Real-world example: reading a customer complaint email**

A shop gets hundreds of emails. Extracting key details into JSON helps the team sort them quickly.

```text
Extract the following from this email:
* Customer name
* Order number
* Problem
* Date of order

Output: JSON format

Email: "Hi, I am Priya. I ordered a blue kurta on 12 March, order number 48213. It arrived torn at the sleeve. Please replace it."
```

---

## 10. Error Correction

Ask the AI to review and fix its own answer.

```text
Explain artificial intelligence in simple terms.
After that, review your answer and correct any mistakes.
```

**Real-world example: checking your own homework**

After finishing an essay, a good student reads it again to fix spelling, grammar, and wrong facts. You can ask the AI to do the same.

```text
Write a 100-word paragraph about the water cycle for a Class 8 student.
After that, review your paragraph, fix any grammar or factual mistakes, and show the corrected version.
```

---

## 11. RAG (Retrieval-Augmented Generation)

Sometimes the AI doesn't know the answer, so we **give it the data**.

```text
Based on this document, summarize key points
```

**Real-world example: asking about a college notice**

The AI cannot know your college's exam dates. But if you paste the notice, it can answer from it.

```text
Based on the notice below, tell me the last date to pay the exam fee and the fine after that date.

Notice: [paste your college notice here]
```

---

## 12. Breaking Complex Problems

Split a big task into smaller steps.

```text
A person wants to lose weight in 2 months.
Break this into steps:
* diet plan
* workout routine
* daily schedule
* progress tracking
Explain each step clearly.
```

**Practice:** A prompt where you break a big task into smaller steps.

```text
A student wants to prepare for exams in 1 month.
Break this into steps:
* syllabus planning
* daily schedule
* revision strategy
* practice tests
Explain each step clearly.
```

**Real-world example: finishing a college project in 2 weeks**

A big project feels scary, but small steps make it easy.

```text
A student must finish a final-year project in 2 weeks.
Break this into steps:
* choosing the topic
* dividing the work by day
* building the project
* preparing the report and presentation
Explain each step clearly.
```

---

## 13. Meta Prompting

Use AI to improve your prompts.

```text
Here is my prompt: 'Give me career advice'
Improve this prompt to make it more specific, detailed, and useful
```

**Practice:** A prompt where the AI improves your original prompt.

```text
Here is my prompt: 'Explain AI'
Improve this prompt to make it more detailed, clear, and effective for better output
```

**Real-world example: getting a better email prompt**

You are not sure how to ask, so you let the AI help you write a better question.

```text
Here is my prompt: 'Write an email to my boss'
Improve this prompt to make it more specific, so the email is clear, polite, and professional.
```

---

## 14. Perspective Switching

Get the same topic explained from different viewpoints.

```text
Explain online education from three perspectives:
* a student
* a teacher
* a working professional
```

**Practice:** A prompt where the AI answers from multiple perspectives.

```text
Explain the impact of social media from three perspectives:
* a student
* a parent
* a psychologist
```

**Real-world example: a college fee increase**

One decision looks different to different people.

```text
Explain the effect of a college fee increase from three perspectives:
* a student
* a parent
* the college principal
```

---

## 15. Thinking Modes

Make the AI switch between brainstorming, analytical, and teaching modes.

```text
Give 5 business ideas for students (brainstorming).
Then analyze the pros and cons of each idea (analytical).
Finally explain the best idea in simple terms (teaching mode).
```

**Real-world example: choosing a weekend side project**

```text
Give 5 side project ideas for a beginner programmer (brainstorming).
Then analyze the pros and cons of each idea (analytical).
Finally explain the best idea in simple terms, like teaching a friend (teaching mode).
```

---

## 16. Nested Complexity

Multiple layers of tasks in one prompt.

```text
Plan a complete trip for 3 days:
* Step 1: Suggest destination options
* Step 2: Create a daily itinerary
* Step 3: Estimate budget
* Step 4: Suggest packing list
* Step 5: Give safety tips
Output everything in a structured format
```

**Practice:** A prompt with multiple layers of tasks.


**Real-world example: planning a friend's birthday party**

```text
Plan a complete birthday party for a friend:
* Step 1: Suggest 3 party themes
* Step 2: Create a schedule for the evening
* Step 3: Plan the food and decorations
* Step 4: Estimate the budget for 50 people
* Step 5: Identify possible problems and solutions
Output everything in a structured format
```