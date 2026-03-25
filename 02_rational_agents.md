This means:
- the agent considers **all past percepts**
- not just the current input

Why?

Because:
> The correct action often depends on history, not only the present.

---

## 6. Definition of a Rational Agent

A rational agent:

- considers the full percept sequence
- uses prior knowledge
- accounts for uncertainty
- chooses the action that maximizes expected performance

Important:

> Rationality is about decision quality, not outcome perfection.

---

## 7. Rationality ≠ Omniscience

A rational agent:
- does **not** know the future
- operates under uncertainty

Therefore:

> A bad outcome does not imply a bad decision.

Rationality is judged based on:
- available information
- expected outcomes

---

## 8. Expected Utility

Since outcomes are uncertain, agents maximize:

> Expected utility

This means:
- each outcome has a value (utility)
- each outcome has a probability

The agent chooses the action with the highest expected value.

---

## 9. Learning and Autonomy

Agents may start with built-in knowledge, but:

> A good agent improves through experience.

This means:
- updating beliefs
- adapting to the environment
- increasing autonomy over time

---

## 10. Task Environment (PEAS Framework)

To design an agent, we must define its **task environment**:

### PEAS

- **P** → Performance measure  
- **E** → Environment  
- **A** → Actuators  
- **S** → Sensors  

---

### Example: Autonomous Taxi

- Performance: safe, fast, legal, comfortable, profitable  
- Environment: roads, traffic, pedestrians  
- Actuators: steering, brake, accelerator  
- Sensors: cameras, GPS, speedometer  

---

### Example: Delivery Drone

- Performance: safe, fast, legal, profitable  
- Environment: airspace, weather, obstacles  
- Actuators: propellers, flight control  
- Sensors: GPS, LiDAR, altitude sensors  

---

## 11. Types of Environments

### Fully Observable vs Partially Observable
- Fully: agent sees everything  
- Partial: agent must infer missing information  

### Deterministic vs Stochastic
- Deterministic: outcome is fixed  
- Stochastic: outcomes involve randomness  

### Episodic vs Sequential
- Episodic: decisions are independent  
- Sequential: decisions affect future  

### Static vs Dynamic
- Static: environment does not change during thinking  
- Dynamic: environment changes over time  

### Discrete vs Continuous
- Discrete: finite states/actions  
- Continuous: real-valued variables  

### Single-agent vs Multi-agent
- Single: no interaction  
- Multi: cooperation or competition  

---

## 12. Types of Agents

### 1. Simple Reflex Agent
- Uses current percept only  
- No memory  
- Works in fully observable environments  

---

### 2. Model-Based Agent
- Maintains internal state  
- Handles partial observability  

---

### 3. Goal-Based Agent
- Uses goals to guide decisions  
- Considers future consequences  

---

### 4. Utility-Based Agent
- Uses a utility function  
- Chooses the best outcome among alternatives  

Key idea:

> Utility-based agents are more flexible than goal-based agents.

---

## 13. World Representations

### Atomic
- State is indivisible  
- Used in search and games  

### Factored
- State described by variables  
- Used in ML and probabilistic models  

### Structured
- Objects, attributes, relationships  
- Highly expressive but complex  

---

## 14. Key Takeaways

- AI systems are **agents that perceive and act**
- Rational agents **maximize expected utility**
- Rationality is about **decision quality under uncertainty**
- Proper design requires:
  - clear performance measures
  - well-defined environments
  - appropriate agent architecture

---

## 15. Common Mistakes

- Confusing goal with performance measure  
- Assuming rational = always correct outcome  
- Thinking agents must be complex or human-like  

---

## 16. One-Line Summary

> A rational agent is a system that uses perception, knowledge, and reasoning to choose actions that maximize expected utility within a defined environment.

---
---

## Lecture 2 — Rational Agents (Understanding Check Answers)

## 1. Why is a thermostat still an agent?

A thermostat is still an agent because it satisfies the formal definition of an agent:

- It perceives the environment through a sensor (temperature)
- It acts on the environment through an actuator (turning heating or cooling on/off)

An agent does not need to be intelligent, complex, or human-like. The definition is purely structural: if something receives input from the environment and produces actions based on it, it is an agent.

---

## 2. What is the difference between a goal and a performance measure?

A goal is a description of what the agent is trying to achieve. It is usually abstract and qualitative.

Example:
- “Keep the room clean”

A performance measure is a quantitative way to evaluate how well the agent is achieving its goal. It defines what the agent is actually optimizing.

Examples:
- number of clean tiles
- penalty for each movement
- total energy consumption

This distinction is important because behavior is determined by the performance measure, not by the goal description. Two agents with the same goal can behave differently if their performance measures are different.

---

## 3. Why is rationality not the same as omniscience?

Omniscience means knowing the exact outcome of every action in advance.

Rationality means choosing the best action based on the available information and expected outcomes.

A rational agent operates under uncertainty and does not have perfect knowledge of the future. Therefore, it may make decisions that lead to bad outcomes, even though the decision itself was correct given the information at the time.

Rationality is evaluated based on the decision process, not the final outcome.

---

## 4. Why is a utility-based agent more expressive than a goal-based agent?

A goal-based agent evaluates outcomes in a binary way:
- goal achieved → success
- goal not achieved → failure

A utility-based agent assigns numerical values to different outcomes, allowing it to distinguish between multiple successful outcomes.

Example:
- reaching a destination quickly, safely, and cheaply can be evaluated differently

This makes utility-based agents more expressive because they can compare trade-offs and select the best option among several acceptable outcomes.

---

## 5. Why does partial observability force the use of internal state?

In a fully observable environment, the agent has access to all relevant information at the current moment. No memory is required.

In a partially observable environment, the current percept does not contain enough information to fully determine the state of the environment.

To handle this, the agent must maintain an internal state (memory) that:
- stores past percepts
- helps infer hidden aspects of the environment

Without internal state, the agent cannot reconstruct the true situation and will make poor decisions.

This is why reflex agents are insufficient in partially observable environments, and model-based agents are required.

---

## Final Summary

An agent uses percepts (and memory when needed) to choose actions that maximize expected utility under uncertainty, based on a defined performance measure.
