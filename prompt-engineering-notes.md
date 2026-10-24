# Prompt Engineering Techniques

A beginner-friendly collection of prompt engineering techniques.

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

**Example**

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

---

## 2. Zero-Shot vs Few-Shot

- **Zero-shot:** no examples, just the instruction.
- **Few-shot:** give examples so the AI learns the pattern.

### Zero-Shot

```text
Classify the sentiment of this review:
'The product quality is great but delivery was very slow.'
```

### Few-Shot

Give examples, and the AI learns the pattern.

```text
Convert feedback into structured JSON

**Example**

Input: "Amazing service and fast delivery"
Output: { "sentiment": "positive", "confidence": 0.9 }


**Real-world example: training a new shop assistant**

If you only say "sort these customer reviews," the new assistant may be confused (zero-shot). If you first show two reviews already sorted into "Happy" and "Unhappy," they understand quickly (few-shot).

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
---

## 5. ReAct (Reason + Act)

The AI **thinks → takes action → observes**, in a loop.

**Insight:** Used in tools like search agents.

**Real-world example: buying a new phone**

Before buying, you think about what matters, check prices and reviews, notice what you find, and then decide. ReAct makes the AI do the same.

```text

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
Imagine 3 experts discussing how students can improve productivity.
Each expert gives a different idea.
Then they critique each other.
Finally combine the best ideas into one plan.
```
---

## 7. Directional Stimulus

Give a main instruction plus specific keywords or hints to guide the focus.

```text
Explain the impact of social media on society.
Focus on mental health, productivity, and relationships.
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

---

## 10. Error Correction

Ask the AI to review and fix its own answer.

**Real-world example: checking your own homework**

After finishing an essay, a good student reads it again to fix spelling, grammar, and wrong facts. You can ask the AI to do the same.

---

## 11. RAG (Retrieval-Augmented Generation)

Sometimes the AI doesn't know the answer, so we **give it the data**.

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

---

## 13. Meta Prompting

Use AI to improve your prompts.

```text
Here is my prompt: 'Give me career advice'
Improve this prompt to make it more specific, detailed, and useful
```

---

## 14. Perspective Switching

Get the same topic explained from different viewpoints.

```text
Explain the impact of social media from three perspectives:
* a student
* a parent
* a psychologist
```
---

## 15. Thinking Modes

Make the AI switch between brainstorming, analytical, and teaching modes.

```text
Give 5 business ideas for students (brainstorming).
Then analyze the pros and cons of each idea (analytical).
Finally explain the best idea in simple terms (teaching mode).
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