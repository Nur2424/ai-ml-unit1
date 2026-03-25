# Lecture 1 — Artificial Intelligence and Machine Learning I

## 1. What this course is about

This course is not about buzzwords like ChatGPT or neural networks.

The core idea is:

> Designing rational agents

An agent is the central concept that everything in the course builds on.

---

## 2. Core Concept: Agent

An agent is:

> An entity that perceives and acts

- Perceives → receives input from the environment  
- Acts → produces output/actions  

Examples:
- Robot → sensors + motors  
- Chat system → text input + text output  
- Self-driving car → cameras + steering  

---

## 3. Core Concept: Rational Agent

This is the most important definition in the lecture.

> A rational agent selects actions that maximize expected utility

Breakdown:
- Goal → what the agent wants to achieve  
- Utility → how good an outcome is  
- Expected → accounts for uncertainty  

Key idea:

> The agent does not choose the “best action”  
> It chooses the action with the best expected outcome  

---

### Intuition

Example:

- Option A: guaranteed €2000  
- Option B: 50% chance €0, 50% chance €10,000  

A rational agent evaluates expected outcomes, not just immediate results.

---

### Important Clarification

Incorrect:
> AI tries to be smart

Correct:
> AI systems are designed to maximize expected utility

---

## 4. What is AI?

The lecture presents four perspectives:

Should machines:
- Think like humans?
- Act like humans?
- Think rationally?
- Act rationally?

The course focuses on:

> Acting rationally

This means:
- Not copying humans  
- Not being emotional  
- Only maximizing outcomes  

---

## 5. AI vs Popular Perception

AI is often misunderstood.

### Not AI:
- Science fiction robots  
- Human-level intelligence  

### Actual AI:
- Narrow, task-specific systems  

Example:
- AlphaGo → superhuman at Go  
- Cannot generalize beyond that task  

---

## 6. What AI Can and Cannot Do

AI can:
- Beat humans at chess  
- Beat humans at Go  

AI struggles with:
- General physical tasks (e.g., unloading a dishwasher)  
- Complex real-world environments  
- Full autonomy in dynamic settings  

Key insight:

> AI performs well in structured environments  
> AI performs poorly in messy, real-world situations  

---

## 7. History of AI (Conceptual Overview)

### Phase 1: Logic-Based AI (1950–1970)
- Rule-based systems  
- Failed due to lack of flexibility  

### Phase 2: Knowledge-Based Systems (1970–1990)
- Expert systems  
- Led to AI Winter  

### Phase 3: Statistical AI (1990–2010)
- Focus on probability and learning  

### Phase 4: Deep Learning (2010–)
- Enabled by big data and GPUs  

### Phase 5: Large Language Models (2017–)
- Transformer architecture  
- Systems like ChatGPT  

Important takeaway:

> Early AI failed because it could not handle uncertainty and complexity  

---

## 8. Brain vs AI

Key points:

- Human brains are not perfectly rational  
- Brains are difficult to reverse engineer  
- AI can outperform humans in specific tasks  
- AI does not need to replicate the brain  

Important idea:

> Intelligence does not require copying biological systems  

---

## 9. Perspectives on Intelligence

### 1. Skills-Based Perspective
- Intelligence = ability to perform a specific task  
- Limitation: too narrow  

### 2. Psychometric Perspective
- Intelligence = ability to generalize across tasks  
- Focus on adaptability  

### 3. Human-Compatible Perspective
- AI should:
  1. Maximize human utility  
  2. Be uncertain about human preferences  
  3. Learn from human behavior  

This is important for modern AI safety.

---

## 10. Modern AI Agents

A modern AI agent consists of:

- Brain → typically a large language model  
- Memory → short-term and long-term  
- Planning → task decomposition  
- Tools → external APIs (e.g., search, calculator)  

Key insight:

> A standalone model is limited  
> A system combining model + tools is significantly more powerful  

---

## 11. Course Structure

The course builds rational agents through four main components:

### 1. Search and Planning
- How to choose actions  

### 2. Probability and Inference
- How to deal with uncertainty  

### 3. Supervised Learning
- How to learn from data  

### 4. Reinforcement Learning
- How to learn from interaction  

---

## 12. Key Mental Model

Everything in the course connects to this idea:

> AI systems are agents that perceive, reason, and act  
> to maximize expected utility  

This is the foundation for all topics that follow.

---

## 13. Key Distinctions

### AI vs ML vs AGI

- AI: Systems designed to perform tasks intelligently  
- ML: A subset of AI that learns from data  
- AGI: Hypothetical system that can perform any intellectual task a human can  

Important:

> Current systems are not AGI  
> They are specialized, narrow AI systems  

---

## 14. Summary

- AI is about rational decision-making, not human imitation  
- The core unit is the rational agent  
- Intelligence is defined by goal-directed behavior under uncertainty  
- The course teaches methods to build such systems
- 
---
---

## ❓ Key Questions & Answers

---

## 1️⃣ Why is “acting rationally” better than “acting like humans”?

### ✅ Answer

Acting rationally is better because it focuses on **optimizing outcomes**, not imitating human behavior.

- Humans are:
  - biased
  - emotional
  - inconsistent

- Rational agents:
  - maximize expected utility
  - make consistent decisions
  - are goal-oriented

### 🧠 Key Insight

> “Acting like humans” = imitation  
> “Acting rationally” = optimization

---

## 2️⃣ Give an example where humans are not rational

### ✅ Answer

A person chooses **€100 now instead of €200 in one week**.

- Rational decision:
  → wait → €200 (higher utility)

- Human behavior:
  → chooses immediate reward due to impatience

### 🧠 Key Insight

> Humans often fail to maximize expected utility due to biases.

---

## 3️⃣ Why did early (logic-based) AI fail?

### ✅ Answer

Early AI systems failed because they relied on **strict logical rules** and could not handle:

- uncertainty
- incomplete information
- real-world complexity

### 🧠 Example

Rule-based system:
