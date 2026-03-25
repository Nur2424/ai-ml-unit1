# Lecture 3 — Search & Planning

## 1. Why Do We Need Search?

From previous lectures:

- An agent must choose actions
- A rational agent must maximize expected utility

The key question becomes:

> How does an agent choose the best sequence of actions?

Answer:

> By planning ahead using search

Search allows an agent to simulate possible future actions and choose the best path to a goal.

---

## 2. Reflex vs Planning Agents

### Reflex Agents

- Choose actions based only on the current percept
- Do not consider future consequences
- Focus on the present state

> “Consider how the world IS”

---

### Planning Agents

- Simulate future outcomes of actions
- Ask: “What will happen if I do this?”
- Use a model of the environment
- Consider future consequences

> “Consider how the world WOULD BE”

---

### Key Insight

- Reflex agents react
- Planning agents think ahead

Reflex agents can only be rational in very simple environments.

---

## 3. When Can We Use Search?

Search is applicable when the environment is:

- Deterministic
- Fully observable

In such environments:

- The agent knows exactly what will happen after each action
- The agent knows the full current state

This allows the agent to plan a complete sequence of actions before executing it.

---

### Open-Loop Execution

In these ideal conditions:

- The agent computes a full plan
- Executes it without re-checking the environment

This is called **open-loop control**

---

## 4. What is a Search Problem?

A search problem consists of:

1. State space  
2. Successor function (actions + costs)  
3. Start state  
4. Goal test  

A solution is:

> A sequence of actions that transforms the start state into a goal state

---

### Example: Romania Map

- States: cities  
- Actions: roads  
- Costs: distances  
- Start: Arad  
- Goal: Bucharest  

---

## 5. State Space and Abstraction

### World State

- Contains every detail of the environment

### Search State

- Contains only the information necessary to solve the problem

---

### Example: Pacman

- World state: ghosts, food, direction, etc.
- Search state (pathfinding): only position (x, y)

---

### Key Idea

> Good abstraction reduces complexity

Poor state representation can make a problem impossible to solve efficiently.

---

## 6. State Space Graph vs Search Tree

### State Space Graph

- Each state appears only once
- Represents the real structure of the problem

---

### Search Tree

- Expands possible sequences of actions
- May contain repeated states
- Represents all possible paths

---

### Key Insight

> The search tree can be exponentially larger than the state space graph

---

## 7. How Search Works

Search constructs a tree of possibilities:

- Root = start state  
- Nodes = states  
- Edges = actions  

---

### Important Concepts

- **Path**: sequence of actions from start to a state  
- **Fringe (Frontier)**: set of nodes waiting to be explored  

---

### Core Question

> Which node from the fringe should be expanded next?

This defines the search algorithm.

---

## 8. Depth-First Search (DFS)

### Strategy

- Expand the deepest node first

### Implementation

- Stack (LIFO)

---

### Properties

- Time complexity: O(b^m)  
- Space complexity: O(bm)  
- Complete: No (fails if infinite depth)  
- Optimal: No  

---

### Behavior

- Explores one path deeply
- Uses very little memory
- Can get stuck in deep or infinite paths

---

### When to Use

- Memory is limited  
- Solutions are deep  
- Dead ends are common but shallow  

---

## 9. Breadth-First Search (BFS)

### Strategy

- Expand the shallowest node first

### Implementation

- Queue (FIFO)

---

### Properties

- Time complexity: O(b^s)  
- Space complexity: O(b^s)  
- Complete: Yes  
- Optimal: Yes (if all costs = 1)  

---

### Behavior

- Finds shortest path in number of steps
- Uses a lot of memory

---

### When to Use

- Solutions are shallow  
- Need shortest path  
- Infinite depth possible  

---

## 10. DFS vs BFS

### BFS is better when:

- The solution is shallow  
- You need an optimal solution  
- There may be infinite paths  

---

### DFS is better when:

- Memory is limited  
- The solution is deep  
- Many wrong paths terminate quickly  

---

## 11. Iterative Deepening Search (IDS)

### Idea

- Run DFS with depth limit = 1  
- Then limit = 2  
- Then limit = 3  
- Continue increasing  

---

### Advantages

- Combines:
  - DFS memory efficiency
  - BFS optimality (for shallow solutions)

---

### Key Insight

Most nodes are at deeper levels, so repeated work is minimal.

---

## 12. Cost-Sensitive Search

BFS minimizes number of steps, not cost.

Problem:

> The shortest path is not always the cheapest path

---

## 13. Uniform Cost Search (UCS)

### Strategy

- Expand the node with the lowest cumulative cost

### Implementation

- Priority queue (ordered by cost)

---

### Properties

- Complete: Yes  
- Optimal: Yes  

---

### Behavior

- Explores paths in order of increasing cost
- Not limited by depth

---

### Drawback

- Explores many unnecessary directions
- Can be slow

---

## 14. Unifying Idea

All search algorithms share the same structure.

The only difference is how the fringe is ordered.

| Algorithm | Expansion Priority |
|----------|------------------|
| DFS      | Deepest node     |
| BFS      | Shallowest node  |
| UCS      | Lowest cost node |

---

## 15. Final Mental Model

Search is the process of exploring possible future states.

A planning agent:

1. Builds a tree of possible actions  
2. Explores it using a strategy  
3. Finds a path to the goal  

---

## 16. Key Takeaways

- Search is the foundation of planning in AI  
- Problem formulation (state space, actions, goal) is critical  
- The same framework applies to all search algorithms  
- The choice of strategy determines performance and optimality

---
---

# Lecture 3 — Understanding Check Answers

## 1. Why can’t we use search in non-deterministic environments?

Search assumes:

- The outcome of each action is known in advance
- The same action always leads to the same result

In a non-deterministic environment:

- The same action can lead to different outcomes
- The agent cannot predict the exact future state

Because of this, the agent cannot plan a single fixed sequence of actions (path).

Instead, it would need:
- conditional plans
- or policies (mapping states → actions)

Therefore, classical search (which outputs a single path) is not sufficient.

---

## 2. Why is BFS optimal but DFS not?

### Breadth-First Search (BFS)

- Explores nodes level by level (shallowest first)
- The first time it reaches the goal, it is guaranteed to be the shortest path (in number of steps)

This makes BFS optimal when all step costs are equal.

---

### Depth-First Search (DFS)

- Explores one path deeply before trying others
- It may find a solution that is:
  - deeper
  - more expensive

DFS does not compare paths; it just follows one branch.

Therefore:
- BFS → optimal (under equal costs)
- DFS → not optimal

---

## 3. Why can the search tree be much larger than the state space graph?

### State space graph

- Each state appears once

---

### Search tree

- Represents all possible paths
- The same state can appear multiple times via different paths

---

### Result

- Repeated states → exponential growth
- The tree can be much larger than the graph

---

### Key insight

A single state in the graph can correspond to many nodes in the tree (because each node represents a different path).

---

## 4. What EXACTLY changes between DFS, BFS, and UCS?

Nothing changes in the overall structure.

All algorithms:
- build a search tree
- maintain a fringe (frontier)
- expand nodes

---

### The ONLY difference:

> How the fringe is ordered

| Algorithm | Priority Rule |
|----------|--------------|
| DFS      | Expand deepest node |
| BFS      | Expand shallowest node |
| UCS      | Expand lowest cost node |

---

### Key idea

Same algorithmic framework, different strategy for choosing the next node.

---

## 5. Why is state representation the hardest part?

Because it defines:

- the size of the search space
- what information is available to the agent
- whether the problem is even solvable

---

### If the state is too detailed:

- The search space becomes enormous
- Computation becomes infeasible

---

### If the state is too simple:

- Important information is lost
- The agent cannot make correct decisions

---

### Example

Pacman:

- Too simple → only position → cannot plan eating dots  
- Too complex → include everything → too many states  

---

### Key insight

> A good state representation keeps only what is necessary for decision-making

This is called abstraction.

---

## Final Summary

- Search works by exploring possible future states
- The main challenge is choosing what to explore
- The difference between algorithms lies in how they prioritize exploration
- The biggest difficulty is modeling the problem correctly (state representation)

