# Lecture 4 — Informed Search

## 1. Motivation: Why Do We Need Informed Search?

Uninformed (blind) search algorithms such as BFS, DFS, and UCS do not use any knowledge about the goal.

- BFS explores all nodes level by level  
- DFS explores deeply without direction  
- UCS explores all directions based on cost  

These methods are inefficient because:

> They do not know where the goal is

---

### Key Idea

> Use additional knowledge to guide the search toward the goal

This leads to:

> Informed search

---

## 2. Heuristics

### Definition

A heuristic is:

> A function that estimates how close a state is to a goal

---

### Examples

- Manhattan distance (grid-based movement)
- Euclidean distance (continuous space)

---

### Intuition

A heuristic answers:

> “How far am I from the goal?”

It is important to understand:

- A heuristic is an estimate, not the true cost
- It is problem-specific

---

## 3. Effect of Heuristics

Heuristics change the behavior of search:

- Without heuristic → blind exploration  
- With heuristic → directed exploration  

This can drastically reduce the number of explored states.

---

## 4. Greedy Search

### Strategy

Greedy search selects the node that appears closest to the goal:

> Expand node with lowest h(n)

---

### Properties

- Uses only heuristic information  
- Ignores path cost  

---

### Behavior

- Moves quickly toward the goal  
- Can be very fast in simple cases  

---

### Limitations

- Can choose a suboptimal path  
- Can get stuck in poor regions of the search space  
- Not guaranteed to find the best solution  

---

### Key Insight

> Greedy search is fast but unreliable

---

## 5. A* Search

A* is the most important informed search algorithm.

---

### Core Idea

Combine:

- Cost so far → g(n)  
- Estimated cost to goal → h(n)  

---

### Evaluation Function

> f(n) = g(n) + h(n)

---

### Interpretation

- g(n): cost from start to current node  
- h(n): estimated cost from current node to goal  
- f(n): estimated total cost of a solution through node n  

---

### Key Insight

> A* balances past cost and future estimate

---

## 6. Why A* Works

A* avoids the weaknesses of other methods:

- Unlike UCS → it does not explore blindly  
- Unlike Greedy → it does not ignore actual cost  

It combines both ideas to guide search efficiently.

---

## 7. Termination Condition (Important)

A* should:

> Stop when the goal node is removed from the frontier (fringe)

---

### Why?

Because:

- A cheaper path to the goal may still exist in the frontier  
- Stopping too early can lead to suboptimal solutions  

---

## 8. Admissible Heuristics

### Definition

A heuristic is admissible if:

> h(n) ≤ true cost from n to the goal

---

### Meaning

- The heuristic never overestimates  
- It is optimistic  

---

### Importance

Admissibility guarantees:

> A* will find an optimal solution

---

## 9. Consistency (Monotonicity)

### Definition

A heuristic is consistent if:

> h(n) ≤ cost(n → n') + h(n')

---

### Interpretation

- The heuristic obeys the triangle inequality  
- Estimated costs are “smooth” across transitions  

---

### Consequence

- f(n) values never decrease along a path  
- No need to revisit nodes  

---

### Key Relation

- Consistent ⇒ Admissible  
- Admissible does not always imply consistent  

---

## 10. Graph Search vs Tree Search

### Problem

In tree search:

- The same state may be expanded multiple times  
- This leads to unnecessary computation  

---

### Solution

Use graph search:

- Maintain a **closed set** of visited states  
- Do not expand the same state twice  

---

### Caution

- If the heuristic is not consistent, graph search can lose optimality  

---

## 11. Designing Heuristics

This is the most challenging part of informed search.

---

### Key Idea

> Good heuristics approximate the true cost as closely as possible without overestimating

---

### Common Strategy: Relaxed Problems

Create a simplified version of the problem:

- Remove constraints  
- Allow easier actions  

Solve the simplified problem to obtain a heuristic.

---

### Example: 8-Puzzle

Possible heuristics:

- Number of misplaced tiles  
- Manhattan distance  

---

### Trade-off

- Better heuristic → fewer nodes expanded  
- But higher computation per node  

---

## 12. Big Picture

Search becomes efficient when guided by good heuristics.

- Blind search → explores everything  
- Informed search → focuses on promising paths  

---

### A* as the Standard

A* is widely used because it is:

- Complete  
- Optimal (with admissible/consistent heuristic)  
- Efficient compared to uninformed methods  

---

## 13. Final Mental Model

- Search = exploring possible solutions  
- Heuristic = direction toward the goal  
- A* = balance between exploration and guidance  

---

## 14. Key Takeaways

- Heuristics are central to efficient search  
- Greedy search is fast but unreliable  
- A* combines cost and heuristic for optimal search  
- Admissibility and consistency determine correctness  
- Designing heuristics is often harder than implementing the algorithm


---
---

# Lecture 4 — Understanding Check Answers

## 1. Why is greedy search dangerous?

Greedy search uses only the heuristic h(n), meaning it selects the node that appears closest to the goal.

The problem is that it ignores the actual path cost g(n).

As a result:
- It may choose a path that looks promising but is actually very expensive
- It can get stuck in local minima or misleading regions
- It may reach a goal quickly, but not the optimal one

Therefore, greedy search is fast but unreliable and not optimal.

---

## 2. Why does A* need BOTH g(n) and h(n)?

A* uses:

- g(n): cost from the start to the current node  
- h(n): estimated cost from the current node to the goal  

If we use only:

- g(n) → we get Uniform Cost Search (slow, explores everywhere)
- h(n) → we get Greedy Search (fast but unreliable)

A* combines both:

> f(n) = g(n) + h(n)

This allows it to:
- consider the real cost already incurred
- estimate the remaining cost

This balance ensures both efficiency and optimality.

---

## 3. What happens if the heuristic overestimates?

If the heuristic overestimates the true cost:

- It becomes inadmissible
- A* may ignore the optimal path because it appears too expensive
- It can choose a suboptimal solution

Therefore:

> Overestimating breaks optimality

---

## 4. Why must A* wait until the goal is popped from the fringe?

When a goal is first discovered (added to the fringe):

- There may still exist another path to the goal with lower cost
- That better path may not have been explored yet

A* guarantees optimality only when:

> The goal node is removed from the fringe (i.e., selected for expansion)

At that point:
- It is the node with the lowest f(n)
- No cheaper solution can exist

Stopping earlier can lead to incorrect (non-optimal) solutions.

---

## 5. Why is designing heuristics harder than coding A*?

Implementing A* is straightforward:

- Use a priority queue
- Compute f(n) = g(n) + h(n)

However, the performance of A* depends almost entirely on the heuristic.

Designing a good heuristic requires:

- Deep understanding of the problem structure
- Ability to approximate the true cost without overestimating
- Balancing accuracy and computational cost

A poor heuristic:
- behaves like blind search (inefficient)

A strong heuristic:
- drastically reduces explored nodes

Therefore:

> The difficulty is not in the algorithm, but in designing the heuristic

