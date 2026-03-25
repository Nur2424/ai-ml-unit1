# Lecture — Local Search

## 1. Key Shift in Problem Definition

In previous approaches, the objective was to find a **path** from a start state to a goal.

In local search:

> The path is irrelevant; only the final state (solution) matters.

This applies to optimization problems where we only care about the quality of the final configuration.

### Examples

- N-Queens → find a configuration with no conflicts  
- Traveling Salesman → find the best route  

---

## 2. What is Local Search?

Local search does not build a search tree.

Instead:

> It maintains a single current state and iteratively improves it.

---

### Key Properties

- No path tracking  
- Constant memory usage  
- Scales to very large state spaces  
- Suitable for optimization problems  

---

### Mental Model

Start from a configuration and move step by step toward better configurations.

---

## 3. Hill Climbing

### Core Idea

> Move to the best neighboring state at each step.

---

### Algorithm Behavior

1. Start from an initial state  
2. Evaluate neighboring states  
3. Move to the best neighbor  
4. Repeat  
5. Stop when no improvement is possible  

---

### Intuition

Like climbing a mountain in fog: always go uphill without seeing the full landscape.

---

## 4. Limitations of Hill Climbing

Hill climbing often fails due to the structure of the search space.

---

### Local Maximum

- The algorithm reaches a peak that is not the global optimum  

---

### Plateau

- A flat region where no neighbor is better  
- The algorithm stops prematurely  

---

### Shoulder

- A flat region that eventually leads to improvement  
- The algorithm may fail to continue  

---

### Key Insight

> Hill climbing makes decisions based only on local information.

---

## 5. Improvements to Hill Climbing

### Random Restart

- Run the algorithm multiple times from different initial states  
- Increases chance of reaching a good solution  

---

### Sideways Moves

- Allow moves to equal-value states  
- Helps escape flat regions  

---

### Limitation

- Still no guarantee of finding the optimal solution  

---

## 6. Simulated Annealing

### Core Idea

> Occasionally accept worse states to escape local optima.

---

### Mechanism

- High temperature → more randomness, accept worse moves  
- Low temperature → behaves like hill climbing  

---

### Acceptance Rule

- If the new state is better → accept  
- If worse → accept with probability:

  exp(ΔE / T)

---

### Intuition

- Early stage → exploration  
- Later stage → refinement  

---

### Theoretical Property

If the temperature decreases slowly enough:

> The algorithm converges to an optimal solution.

---

### Practical Limitation

- “Slow enough” cooling may be computationally impractical  

---

## 7. Local Beam Search

### Core Idea

> Maintain multiple candidate states simultaneously.

---

### Process

1. Start with K random states  
2. Generate all successors  
3. Select the best K states  
4. Repeat  

---

### Key Feature

States share information during the search process.

---

### Insight

This is not independent search runs; it is a cooperative process.

---

## 8. Genetic Algorithms

### Core Idea

Inspired by biological evolution.

---

### Process

1. Maintain a population of solutions  
2. Select individuals based on fitness  
3. Combine solutions (crossover)  
4. Introduce variation (mutation)  

---

### Intuition

Solutions evolve over time toward better configurations.

---

## 9. Local Search in Continuous Spaces

Not all problems are discrete.

---

### Example

Minimizing distance in spatial problems (e.g., facility placement).

---

### Gradient-Based Methods

Use derivatives to guide search.

---

### Gradient Descent

Update rule:

x ← x − α∇f(x)

---

### Interpretation

- Move in the direction that reduces the objective function  
- Step size controlled by α  

---

## 10. When to Use Local Search

Local search is suitable when:

- The state space is extremely large  
- The path to the solution is irrelevant  
- The objective is to optimize a configuration  

---

## 11. Strengths and Limitations

### Strengths

- Low memory usage  
- Fast in practice  
- Scales well to large problems  

---

### Limitations

- No guarantee of optimality  
- Sensitive to initial state  
- Can get stuck in local optima  

---

## 12. Applications

Local search is widely used in:

- Optimization problems  
- Planning systems  
- Engineering design (e.g., VLSI layout)  
- Machine learning algorithms  

---

## 13. Final Mental Model

- Traditional search → explores paths  
- Local search → improves a single solution  

---

## 14. Key Takeaways

- Local search focuses on solutions, not paths  
- Hill climbing is simple but limited  
- Simulated annealing introduces controlled randomness  
- Beam search and genetic algorithms use multiple states  
- Gradient methods handle continuous optimization

---
---

# Lecture — Local Search (Understanding Check Answers)

## 1. Why does local search ignore paths?

Local search is used in problems where:

- The path to the solution is irrelevant
- Only the final configuration matters

Examples:
- N-Queens → only the final board matters
- Optimization problems → only the best solution matters

Tracking the path would:
- Waste memory
- Not provide additional value

Therefore:

> Local search focuses only on the current state and its quality, not how it was reached.

---

## 2. Why is hill climbing fundamentally flawed?

Hill climbing makes decisions based only on local information.

It always moves to a better neighbor, but:

- It cannot see the global structure of the search space
- It cannot move to worse states (unless modified)

As a result, it gets stuck in:

- Local maxima → better than neighbors, but not optimal  
- Plateaus → no improvement possible  
- Shoulders → flat regions hiding better states  

Therefore:

> Hill climbing is greedy and myopic, which prevents it from finding global optima reliably.

---

## 3. Why does simulated annealing work better?

Simulated annealing improves hill climbing by allowing worse moves.

This helps because:

- Escaping a local maximum often requires moving downhill first
- Pure hill climbing cannot do this

Mechanism:

- At high temperature → more randomness → exploration  
- At low temperature → less randomness → refinement  

This balance allows the algorithm to:

- Explore the space early  
- Focus on good solutions later  

Therefore:

> Simulated annealing can escape local optima and has a chance to reach the global optimum.

---

## 4. Why is beam search not just multiple hill climbs?

In multiple independent hill climbs:

- Each search runs separately
- No information is shared

In beam search:

- Multiple states are maintained together
- All successors are compared globally
- The best states are selected collectively

This means:

> The searches cooperate and guide each other toward better regions

Therefore:

> Beam search is a coordinated search process, not independent runs.

---

## 5. Why is local search used in machine learning?

Many machine learning problems are optimization problems.

The goal is typically:

- Minimize a loss function
- Maximize a performance metric

This is equivalent to:

> Searching for the best configuration in a large space

Examples:
- Training neural networks → minimizing loss via gradient descent  
- Parameter tuning → finding optimal weights  

Local search methods:

- Start from an initial solution  
- Iteratively improve it  

Therefore:

> Machine learning is essentially local search in high-dimensional spaces.
