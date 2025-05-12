# Modeling Electrical Circuits as Graphs: A Graph-Theoretic Approach to Equivalent Resistance

## 1. Understanding the Circuit-to-Graph Representation

The analysis of electrical circuits, particularly for calculating equivalent resistance, is a cornerstone of electrical engineering. Traditional methods rely on iterative applications of series and parallel resistor formulas, which can become computationally intensive for complex networks. Graph theory provides a robust and systematic framework to model and simplify such circuits, enabling both analytical insights and computational efficiency. This section explores how to represent an electrical circuit as a graph, emphasizing the mapping of circuit components to graph elements and the underlying graph-theoretic concepts.

### 1.1 Circuit-to-Graph Mapping

An electrical circuit can be modeled as a **weighted undirected graph** $G = (V, E, w)$, where:
- **Nodes ($V$)**: Represent junctions or connection points in the circuit where two or more circuit elements (e.g., resistors, wires) meet. These are points of equal potential (equipotential points) in the circuit.
- **Edges ($E$)**: Represent resistors connecting pairs of junctions. Each edge corresponds to a resistor bridging two nodes.
- **Weights ($w : E \to \mathbb{R}^+$)**: Represent the resistance values of the resistors, typically measured in ohms ($\Omega$). For an edge $e \in E$ connecting nodes $u, v \in V$, the weight $w(e) = R_{uv}$ is the resistance of the resistor.

Formally, let $V = \{ v_1, v_2, \dots, v_n \}$ denote the set of nodes (junctions), and $E = \{ e_1, e_2, \dots, e_m \}$ denote the set of edges (resistors). The graph $G$ is undirected because resistors have no directional preference, and the weight function $w(e_i) = R_i$ assigns a positive real number to each edge, reflecting the resistance.

#### Example: Simple Series Circuit
Consider a circuit with three resistors in series: $R_1 = 2\Omega$, $R_2 = 3\Omega$, $R_3 = 4\Omega$. The circuit can be represented as a graph with:
- Nodes: $v_1, v_2, v_3, v_4$ (junctions between resistors and at the terminals).
- Edges: $e_1 = (v_1, v_2)$ with $w(e_1) = 2\Omega$, $e_2 = (v_2, v_3)$ with $w(e_2) = 3\Omega$, $e_3 = (v_3, v_4)$ with $w(e_3) = 4\Omega$.
- Graph structure: A linear path $v_1 \to v_2 \to v_3 \to v_4$.

The equivalent resistance $R_{\text{eq}}$ is computed as:
$$R_{\text{eq}} = R_1 + R_2 + R_3 = 2 + 3 + 4 = 9\Omega$$

This linear graph reflects the series configuration, where the total resistance is the sum of individual resistances.

#### Example: Simple Parallel Circuit
For two resistors in parallel, $R_1 = 4\Omega$, $R_2 = 4\Omega$, connected between two junctions:
- Nodes: $v_1, v_2$ (the two junctions).
- Edges: $e_1 = (v_1, v_2)$ with $w(e_1) = 4\Omega$, $e_2 = (v_1, v_2)$ with $w(e_2) = 4\Omega$.
- Graph structure: Two parallel edges between $v_1$ and $v_2$.

The equivalent resistance is given by the parallel resistance formula:
$$\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} = \frac{1}{4} + \frac{1}{4} = \frac{2}{4} = \frac{1}{2}$$
$$R_{\text{eq}} = 2\Omega$$

This graph representation captures the parallel configuration, where multiple edges between the same node pair indicate resistors in parallel.

### 1.2 Graph Theory Concepts for Circuit Analysis

To effectively model and analyze circuits as graphs, a solid understanding of fundamental graph theory concepts is essential. These concepts provide the mathematical foundation for identifying series and parallel connections and simplifying complex networks.

#### 1.2.1 Nodes and Degree
The **degree** of a node $v \in V$, denoted $\deg(v)$, is the number of edges incident to it. In a circuit graph:
- A node with $\deg(v) = 2$ typically indicates a junction between two resistors in series, as it connects exactly two resistors (e.g., $v_2$ in the series example above).
- A node with $\deg(v) > 2$ may indicate a junction where multiple resistors converge, potentially forming parallel or more complex configurations.

For a graph with $n$ nodes and $m$ edges, the sum of degrees satisfies the handshaking lemma:
$$\sum_{v \in V} \deg(v) = 2m$$

This property ensures consistency in the circuit’s connectivity.

#### 1.2.2 Edges and Weights
Edges in the circuit graph are weighted by resistance values. For an edge $e = (u, v)$, the weight $w(e) = R_{uv}$ is a positive real number. The weight function is critical for computations, as it directly influences the equivalent resistance. For parallel edges between nodes $u$ and $v$, say $e_1, e_2$ with weights $R_1, R_2$, the equivalent resistance is:
$$R_{\text{eq}} = \left( \frac{1}{R_1} + \frac{1}{R_2} \right)^{-1}$$

This formula generalizes to $k$ parallel edges:
$$\frac{1}{R_{\text{eq}}} = \sum_{i=1}^k \frac{1}{R_i}$$

#### 1.2.3 Cycles
A **cycle** in a graph is a closed path where the starting and ending nodes are the same, and no edges are repeated. In circuit graphs, cycles often indicate parallel or more complex configurations. For example:
- A cycle of length 2 (two edges between the same pair of nodes) represents parallel resistors.
- Longer cycles may indicate configurations like Wheatstone bridges or delta-star transformations, which require advanced simplification techniques.

The presence of cycles can be detected using graph traversal algorithms like **depth-first search (DFS)**, which explores the graph to identify closed paths. The cycle structure informs the reduction strategy, as parallel resistors form the simplest type of cycle.

#### 1.2.4 Connectivity and Paths
A graph is **connected** if there is a path between any pair of nodes. In circuit analysis, we assume the circuit graph is connected, as disconnected components would represent separate circuits. A **path** between nodes $u$ and $v$ is a sequence of edges connecting them. For series configurations, the path is unique and linear, with intermediate nodes of degree 2. The resistance along a path in series is:
$$R_{\text{path}} = \sum_{e \in \text{path}} w(e)$$

#### 1.2.5 Adjacency and Incidence
The **adjacency matrix** $A$ of a graph encodes connectivity: $A_{ij} = 1$ if an edge exists between nodes $v_i$ and $v_j$, and 0 otherwise. For weighted graphs, a **weighted adjacency matrix** can store resistance values: $A_{ij} = R_{ij}$ if an edge exists, else $\infty$. The **incidence matrix** $B$ relates nodes to edges: $B_{ve} = 1$ if node $v$ is an endpoint of edge $e$, and 0 otherwise. These matrices are useful for computational implementations and advanced analyses (e.g., Kirchhoff’s laws).

### 1.3 Representing Series and Parallel Connections

The graph representation naturally captures series and parallel resistor configurations, which are the building blocks of circuit simplification.

#### 1.3.1 Series Connections
A series connection occurs when resistors are arranged along a single path with no branching. In graph terms:
- The subgraph is a path where intermediate nodes have $\deg(v) = 2$.
- For resistors $R_1, R_2, \dots, R_k$ in series, the equivalent resistance is:
$$R_{\text{eq}} = R_1 + R_2 + \cdots + R_k = \sum_{i=1}^k R_i$$
- Graphically, the path $v_1 \to v_2 \to \cdots \to v_{k+1}$ with edges $e_i = (v_i, v_{i+1})$ of weights $R_i$ is reduced to a single edge $(v_1, v_{k+1})$ with weight $R_{\text{eq}}$.

#### 1.3.2 Parallel Connections
A parallel connection occurs when multiple resistors connect the same pair of nodes. In graph terms:
- Multiple edges exist between nodes $u$ and $v$.
- For resistors $R_1, R_2, \dots, R_k$ in parallel, the equivalent resistance is:
$$R_{\text{eq}} = \left( \sum_{i=1}^k \frac{1}{R_i} \right)^{-1}$$
- Graphically, the multiple edges $e_1, e_2, \dots, e_k$ between $u$ and $v$ are replaced by a single edge with weight $R_{\text{eq}}$.

#### 1.3.3 Nested Configurations
Complex circuits often involve nested series and parallel combinations. The graph representation handles these by iteratively identifying and reducing series and parallel subgraphs. For example, consider a circuit where two resistors $R_1, R_2$ are in series, and their combination is in parallel with $R_3$:
- First, reduce the series combination:
$$R_{12} = R_1 + R_2$$
- Then, compute the parallel combination with $R_3$:
$$R_{\text{eq}} = \left( \frac{1}{R_{12}} + \frac{1}{R_3} \right)^{-1} = \left( \frac{1}{R_1 + R_2} + \frac{1}{R_3} \right)^{-1}$$

This iterative process leverages the graph structure to systematically simplify the network.

### 1.4 Practical Considerations
- **Graph Simplification**: The goal is to reduce the graph to a single edge between the input and output nodes, with the edge weight equal to $R_{\text{eq}}$. This requires careful identification of series and parallel patterns using traversal algorithms.
- **Complex Configurations**: Circuits with cycles (e.g., bridges or delta configurations) may require advanced techniques like **star-delta transformations**:
$$R_{\text{delta}} \to R_{\text{star}}: \quad R_i = \frac{R_a R_b}{R_a + R_b + R_c}$$
where $R_a, R_b, R_c$ are the resistances in a delta configuration.
- **Computational Tools**: Libraries like NetworkX (Python) can represent and manipulate weighted graphs, facilitating the identification of series and parallel subgraphs.

### 1.5 Summary
Modeling an electrical circuit as a weighted undirected graph provides a powerful framework for analyzing equivalent resistance. Nodes represent junctions, edges represent resistors with weights as resistance values, and graph theory concepts like degree, cycles, and paths enable the identification of series and parallel configurations. The mathematical formalism, supported by equations like:
$$R_{\text{series}} = \sum R_i, \quad R_{\text{parallel}} = \left( \sum \frac{1}{R_i} \right)^{-1}$$
ensures precise computation. This approach not only streamlines manual analysis but also supports automated circuit simulation, making it invaluable for engineering and computational applications.

---
# Algorithm Development for Calculating Equivalent Resistance Using Graph Theory

## 2. Developing the Algorithm for Equivalent Resistance

Calculating the equivalent resistance of an electrical circuit is a fundamental task in circuit analysis, traditionally approached through iterative application of series and parallel resistor formulas. For complex circuits, these methods can become cumbersome, especially when dealing with nested configurations. By modeling a circuit as a weighted undirected graph $G = (V, E, w)$, where nodes represent junctions, edges represent resistors, and weights denote resistance values, graph theory offers a systematic and algorithmic approach to simplify the circuit and compute the equivalent resistance $R_{\text{eq}}$. This section outlines the development of an algorithm that iteratively simplifies the graph by identifying and reducing series and parallel connections, ensuring robust handling of nested combinations.

### 2.1 Overview of the Algorithm

The algorithm iteratively reduces the graph $G$ until it consists of a single edge between the input and output nodes, with the edge’s weight equal to the equivalent resistance $R_{\text{eq}}$. The process involves:
- **Identifying Series Connections**: Detect linear chains of edges (resistors) forming a path with no branching, and combine their resistances by summation.
- **Identifying Parallel Connections**: Detect multiple edges between the same pair of nodes, and combine their resistances using the parallel resistance formula.
- **Iterative Reduction**: Repeatedly apply series and parallel reductions until the graph is fully simplified.
- **Handling Nested Combinations**: Ensure the algorithm processes complex configurations (e.g., series within parallel or vice versa) by iteratively simplifying identifiable patterns.

The algorithm assumes the graph is connected and undirected, with positive resistance values $w(e) > 0$ for each edge $e \in E$.

### 2.2 Identifying Series Connections

A series connection occurs when resistors form a linear chain with no branching paths, corresponding to a path in the graph where intermediate nodes have degree 2. Formally, consider a path $v_1 \to v_2 \to \cdots \to v_{k+1}$ with edges $e_i = (v_i, v_{i+1})$ and resistances $R_i = w(e_i)$ for $i = 1, 2, \dots, k$, where each intermediate node $v_2, v_3, \dots, v_k$ has $\deg(v_i) = 2$. The equivalent resistance of the series combination is:
$$R_{\text{series}} = R_1 + R_2 + \cdots + R_k = \sum_{i=1}^k R_i$$

To identify series connections:
- Traverse the graph to find nodes with $\deg(v) = 2$.
- For each such node $v_i$ with neighbors $v_{i-1}$ and $v_{i+1}$, combine the edges $(v_{i-1}, v_i)$ and $(v_i, v_{i+1})$ into a single edge $(v_{i-1}, v_{i+1})$ with weight $R_{i-1} + R_i$.
- Remove node $v_i$ and update the graph.

This reduction preserves the equivalent resistance between the remaining nodes.

#### Example: Series Reduction
Consider a path with three resistors: $R_1 = 2\Omega$, $R_2 = 3\Omega$, $R_3 = 4\Omega$, forming a graph $v_1 \to v_2 \to v_3 \to v_4$. Nodes $v_2$ and $v_3$ have $\deg(v_2) = \deg(v_3) = 2$. The algorithm:
1. Combines $R_1$ and $R_2$ at $v_2$, replacing edges $(v_1, v_2)$ and $(v_2, v_3)$ with a single edge $(v_1, v_3)$ of resistance $2 + 3 = 5\Omega$.
2. Combines the new edge with $R_3$ at $v_3$, resulting in a single edge $(v_1, v_4)$ with resistance $5 + 4 = 9\Omega$.
The equivalent resistance is:
$$R_{\text{eq}} = 2 + 3 + 4 = 9\Omega$$

### 2.3 Identifying Parallel Connections

A parallel connection occurs when multiple resistors connect the same pair of nodes, represented by multiple edges between two nodes in the graph. For nodes $u$ and $v$ connected by edges $e_1, e_2, \dots, e_k$ with resistances $R_1, R_2, \dots, R_k$, the equivalent resistance is:
$$R_{\text{parallel}} = \left( \sum_{i=1}^k \frac{1}{R_i} \right)^{-1}$$

To identify parallel connections:
- Examine all pairs of nodes $(u, v)$ to detect multiple edges.
- For each set of parallel edges, compute the equivalent resistance using the parallel formula.
- Replace the multiple edges with a single edge $(u, v)$ of weight $R_{\text{parallel}}$.

#### Example: Parallel Reduction
Consider two resistors $R_1 = 4\Omega$ and $R_2 = 4\Omega$ between nodes $v_1$ and $v_2$. The algorithm computes:
$$\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} = \frac{1}{4} + \frac{1}{4} = \frac{2}{4} = \frac{1}{2}$$
$$R_{\text{eq}} = 2\Omega$$
The two edges are replaced by a single edge $(v_1, v_2)$ with weight $2\Omega$.

### 2.4 Iterative Reduction Process

The algorithm iteratively applies series and parallel reductions until the graph is reduced to a single edge between the input and output nodes, representing $R_{\text{eq}}$. The process is as follows:
1. **Check for Series Connections**: Identify and reduce all nodes with $\deg(v) = 2$ by combining adjacent edges.
2. **Check for Parallel Connections**: Identify and reduce all node pairs with multiple edges using the parallel formula.
3. **Repeat**: Continue alternating between series and parallel reductions until no further reductions are possible.
4. **Termination**: The algorithm terminates when the graph has a single edge between the input and output nodes, with weight $R_{\text{eq}}$. If the graph cannot be reduced to a single edge (e.g., due to complex configurations like bridges), report an error or apply advanced techniques (e.g., star-delta transformations).

The iterative nature ensures that nested combinations—such as series resistors within a parallel configuration—are handled by processing identifiable patterns in each iteration.

#### Pseudocode
```plaintext
Input: Graph G = (V, E, w), input node s, output node t
Output: Equivalent resistance R_eq

While G has more than one edge between s and t:
    // Step 1: Series reduction
    For each node v in V:
        If deg(v) = 2 and v is not s or t:
            Let u, w be the neighbors of v
            Let e1 = (u, v), e2 = (v, w) with weights R1, R2
            Add edge (u, w) with weight R1 + R2
            Remove node v and edges e1, e2
    
    // Step 2: Parallel reduction
    For each pair of nodes (u, v) in V:
        If multiple edges exist between u and v:
            Compute R_parallel = (∑(1/R_i))⁻¹ for all edges between u and v
            Replace multiple edges with a single edge (u, v) of weight R_parallel
    
    // Step 3: Check termination
    If no reductions occurred and G has more than one edge:
        Return error ("Complex configuration requires advanced methods")

Return weight of the single edge between s and t as Trades off: R_eq
```
# Pseudocode for Calculating Equivalent Resistance Using Graph Theory

## 3. Writing Pseudocode for the Equivalent Resistance Algorithm

The computation of equivalent resistance $R_{\text{eq}}$ in an electrical circuit modeled as a weighted undirected graph $G = (V, E, w)$ requires a systematic approach to simplify the graph through iterative series and parallel reductions. The pseudocode presented here formalizes the algorithm, providing a clear and structured outline of the steps to identify series and parallel connections, reduce the graph, and handle nested configurations. This section explains the pseudocode, its operational logic, and how it addresses complex circuit structures, ensuring robustness and clarity for both theoretical understanding and practical implementation.

### 3.1 Pseudocode Overview

The pseudocode operates on a graph $G$ where nodes represent junctions, edges represent resistors, and weights represent resistance values in ohms ($\Omega$). The algorithm iteratively applies two primary operations:
- **Series Reduction**: Combines resistors along a linear path (nodes with degree 2) by summing their resistances.
- **Parallel Reduction**: Combines multiple resistors between the same pair of nodes using the parallel resistance formula.
The process continues until the graph is reduced to a single edge between the input and output nodes, with the edge’s weight equal to $R_{\text{eq}}$. The pseudocode includes error handling for cases where the graph cannot be reduced to a single edge (e.g., non-series-parallel configurations).

The pseudocode is designed to be language-agnostic, focusing on logical steps that can be implemented in any programming environment. It assumes the graph is connected, undirected, and has positive weights $w(e) > 0$ for each edge $e \in E$.

### 3.2 Pseudocode

Below is the pseudocode, adapted from the provided outline, with detailed comments explaining each step and the handling of nested configurations.

```plaintext
// Input: Graph G = (V, E, w) with nodes (junctions), edges (resistors), weights (resistances),
//        input node s, output node t
// Output: Equivalent resistance R_eq between s and t
```
# Handling Complex Configurations in Equivalent Resistance Computation

## 4. Explaining the Algorithm’s Handling of Complex Configurations

The graph-theoretic algorithm for computing equivalent resistance $R_{\text{eq}}$ in an electrical circuit, modeled as a weighted undirected graph $G = (V, E, w)$, relies on iterative simplification through series and parallel reductions. This approach is particularly effective for handling complex circuit configurations, including nested structures, by systematically reducing subgraphs until a single edge represents $R_{\text{eq}}$. This section demonstrates the algorithm’s operation on three example circuits: a simple series circuit, a simple parallel circuit, and a nested configuration. Each example illustrates the algorithm’s steps, supported by mathematical derivations, and highlights how iterative reductions manage nested structures by simplifying identifiable patterns step-by-step.

### 4.1 Algorithm Recap

The algorithm iteratively processes the graph $G$ by:
- **Series Reduction**: Identifying nodes with degree 2 (indicating a linear chain of resistors) and combining their resistances using:
$$R_{\text{series}} = R_1 + R_2 + \cdots + R_k$$
- **Parallel Reduction**: Identifying multiple edges between the same pair of nodes and combining their resistances using:
$$R_{\text{parallel}} = \left( \sum_{i=1}^k \frac{1}{R_i} \right)^{-1}$$
- **Iteration**: Repeating these reductions until the graph is reduced to a single edge between the input and output nodes, with weight $R_{\text{eq}}$.

The algorithm’s iterative nature ensures that complex configurations, including nested series and parallel combinations, are handled by processing simpler subgraphs first, gradually unraveling the circuit’s structure.

### 4.2 Example 1: Simple Series Circuit

#### Circuit Description
Consider a circuit with two resistors in series: $R_1 = 2\Omega$ and $R_2 = 3\Omega$, forming a linear chain between input node $s$ and output node $t$. The graph representation is:
- Nodes: $s, v, t$ (where $v$ is the junction between resistors).
- Edges: $e_1 = (s, v)$ with $w(e_1) = 2\Omega$, $e_2 = (v, t)$ with $w(e_2) = 3\Omega$.
- Structure: A path $s \to v \to t$, with $v$ having $\deg(v) = 2$.

#### Algorithm Steps
1. **Identify Series Connection**: The algorithm detects node $v$ with $\deg(v) = 2$, indicating a series configuration. The edges $e_1 = (s, v)$ and $e_2 = (v, t)$ have weights $R_1 = 2\Omega$ and $R_2 = 3\Omega$.
2. **Combine Resistances**: The series resistance is computed as:
$$R_{\text{series}} = R_1 + R_2 = 2 + 3 = 5\Omega$$
3. **Update Graph**: Remove node $v$ and edges $e_1$, $e_2$, and add a new edge $(s, t)$ with weight $5\Omega$.
4. **Termination**: The graph now has a single edge $(s, t)$ with weight $5\Omega$, so the algorithm returns:
$$R_{\text{eq}} = 5\Omega$$

#### Analysis
The algorithm identifies the linear chain by checking for degree-2 nodes, a hallmark of series connections. The reduction is straightforward, as the graph is a simple path, requiring only one iteration to compute $R_{\text{eq}}$. This example demonstrates the algorithm’s efficiency for basic series circuits.

### 4.3 Example 2: Simple Parallel Circuit

#### Circuit Description
Consider two resistors in parallel: $R_1 = 4\Omega$ and $R_2 = 4\Omega$, connected between the same pair of nodes $s$ and $t$. The graph representation is:
- Nodes: $s, t$.
- Edges: $e_1 = (s, t)$ with $w(e_1) = 4\Omega$, $e_2 = (s, t)$ with $w(e_2) = 4\Omega$.
- Structure: Two parallel edges between $s$ and $t$.

#### Algorithm Steps
1. **Identify Parallel Connection**: The algorithm detects multiple edges ($e_1$, $e_2$) between nodes $s$ and $t$, indicating a parallel configuration.
2. **Combine Resistances**: The parallel resistance is computed as:
$$\frac{1}{R_{\text{parallel}}} = \frac{1}{R_1} + \frac{1}{R_2} = \frac{1}{4} + \frac{1}{4} = \frac{2}{4} = \frac{1}{2}$$
$$R_{\text{parallel}} = \frac{1}{\frac{1}{2}} = 2\Omega$$
3. **Update Graph**: Remove edges $e_1$ and $e_2$, and add a single edge $(s, t)$ with weight $2\Omega$.
4. **Termination**: The graph now has a single edge $(s, t)$ with weight $2\Omega$, so the algorithm returns:
$$R_{\text{eq}} = 2\Omega$$

#### Analysis
The algorithm efficiently handles parallel connections by checking for multiple edges between node pairs. The parallel reduction consolidates the two resistors into a single equivalent resistor in one iteration, demonstrating the algorithm’s effectiveness for simple parallel circuits.

### 4.4 Example 3: Nested Configuration

#### Circuit Description
Consider a nested configuration where two resistors $R_1 = 2\Omega$ and $R_2 = 3\Omega$ are in series, and their combination is in parallel with a third resistor $R_3 = 5\Omega$. The graph representation is:
- Nodes: $s, v, t$ (where $v$ is the junction between $R_1$ and $R_2$).
- Edges: $e_1 = (s, v)$ with $w(e_1) = 2\Omega$, $e_2 = (v, t)$ with $w(e_2) = 3\Omega$, $e_3 = (s, t)$ with $w(e_3) = 5\Omega$.
- Structure: A path $s \to v \to t$ (for $R_1$ and $R_2$) in parallel with a direct edge $s \to t$ (for $R_3$).

#### Algorithm Steps
1. **Identify Series Connection**:
   - The algorithm detects node $v$ with $\deg(v) = 2$, indicating a series connection between edges $e_1 = (s, v)$ and $e_2 = (v, t)$ with weights $R_1 = 2\Omega$ and $R_2 = 3\Omega$.
   - Compute the series resistance:
$$R_{12} = R_1 + R_2 = 2 + 3 = 5\Omega$$
   - Update the graph: Remove node $v$ and edges $e_1$, $e_2$, and add a new edge $e_{12} = (s, t)$ with weight $5\Omega$.
   - Updated graph: Two edges between $s$ and $t$: $e_{12}$ with $5\Omega$ and $e_3$ with $5\Omega$.

2. **Identify Parallel Connection**:
   - The algorithm detects two edges ($e_{12}$, $e_3$) between $s$ and $t$, indicating a parallel configuration.
   - Compute the parallel resistance:
$$\frac{1}{R_{\text{parallel}}} = \frac{1}{R_{12}} + \frac{1}{R_3} = \frac{1}{5} + \frac{1}{5} = \frac{2}{5}$$
$$R_{\text{parallel}} = \frac{1}{\frac{2}{5}} = \frac{5}{2} = 2.5\Omega$$
   - Update the graph: Remove edges $e_{12}$ and $e_3$, and add a single edge $(s, t)$ with weight $2.5\Omega$.

3. **Termination**:
   - The graph now has a single edge $(s, t)$ with weight $2.5\Omega$, so the algorithm returns:
$$R_{\text{eq}} = 2.5\Omega$$

#### Analysis
The nested configuration requires two iterations: first a series reduction to combine $R_1$ and $R_2$, then a parallel reduction to combine the series result with $R_3$. The algorithm’s iterative approach ensures that the nested structure is handled by processing the series subgraph first, creating a simpler parallel configuration that can be reduced in the next step. This example highlights the algorithm’s ability to systematically simplify complex circuits.

### 4.5 Iterative Reductions for Nested Structures

The algorithm’s strength lies in its iterative reduction strategy, which naturally handles nested configurations by:
- **Pattern Recognition**: Identifying series (degree-2 nodes) and parallel (multiple edges) subgraphs in each iteration.
- **Step-by-Step Simplification**: Reducing simpler subgraphs first, which may create new series or parallel opportunities in subsequent iterations.
- **Flexibility**: Alternating between series and parallel reductions as needed, ensuring that nested structures are unraveled progressively.

For the nested example, the series reduction of $R_1$ and $R_2$ transforms the graph into a parallel configuration, which is then reduced in the next iteration. This process generalizes to more complex circuits, such as multiple nested layers, because any series-parallel circuit can be reduced to a single equivalent resistance through repeated application of these rules. Mathematically, the algorithm leverages the commutative and associative properties of series and parallel operations, ensuring correctness regardless of the order of reductions.

### 4.6 Limitations and Extensions

While the algorithm excels for series-parallel circuits, it may encounter limitations with:
- **Non-Series-Parallel Configurations**: Circuits like Wheatstone bridges or delta configurations require advanced techniques, such as star-delta transformations:
$$R_{\text{star}} = \frac{R_a R_b}{R_a + R_b + R_c}$$
- **Complex Nested Structures**: Deeply nested circuits may require multiple iterations, increasing computational time for large graphs.

To extend the algorithm, one could:
- Incorporate star-delta transformations for non-series-parallel circuits.
- Optimize iteration order (e.g., prioritize series reductions) to reduce the number of steps.
- Use efficient graph traversal algorithms (e.g., depth-first search) to identify reducible subgraphs quickly.

### 4.7 Summary

The graph-theoretic algorithm effectively handles complex circuit configurations by iteratively applying series and parallel reductions, as demonstrated in three examples:
- **Simple Series Circuit**: Identifies a linear chain and computes $R_{\text{eq}} = 5\Omega$ in one iteration.
- **Simple Parallel Circuit**: Identifies multiple edges and computes $R_{\text{eq}} = 2\Omega$ in one iteration.
- **Nested Configuration**: Processes a series-parallel structure in two iterations, computing $R_{\text{eq}} = 2.5\Omega$.

The iterative reduction strategy, supported by equations like:
$$R_{\text{series}} = \sum_{i=1}^k R_i, \quad R_{\text{parallel}} = \left( \sum_{i=1}^k \frac{1}{R_i} \right)^{-1}$$
ensures that nested structures are simplified step-by-step, making the algorithm a powerful tool for circuit analysis. Its ability to handle complex configurations through systematic subgraph reduction underscores its utility in both theoretical and practical applications.

---
## Codes and Plots

![alt text](<circuit_simplification_phased_layout (1).gif>)
```python
import networkx as nx
import matplotlib.pyplot as plt
import matplotlib.patches as patches
import imageio
import numpy as np

# Function to draw nodes as boxes or circles with specific colors
def draw_custom_nodes(G, pos, ax, node_colors, node_shapes):
    for node in G.nodes():
        x, y = pos[node]
        if node_shapes[node] == 'box':
            rect = patches.Rectangle((x - 0.1, y - 0.05), 0.2, 0.1, linewidth=1, edgecolor='black', facecolor=node_colors[node])
            ax.add_patch(rect)
            ax.text(x, y, node, fontsize=10, ha='center', va='center')
        else:
            circle = patches.Circle((x, y), 0.05, linewidth=1, edgecolor='black', facecolor=node_colors[node])
            ax.add_patch(circle)
            ax.text(x, y, node, fontsize=10, ha='center', va='center')

# Function to draw edges with arrows and labels
def draw_custom_edges(G, pos, ax):
    for (u, v, d) in G.edges(data=True):
        x1, y1 = pos[u]
        x2, y2 = pos[v]
        ax.arrow(x1, y1, (x2-x1)*0.8, (y2-y1)*0.8, head_width=0.02, head_length=0.04, fc='black', ec='black')
        if 'label' in d and d['label']:
            ax.text((x1+x2)/2, (y1+y2)/2, d['label'], fontsize=10, ha='center', va='center', color='black')

# Create a MultiGraph to allow multiple edges
G = nx.MultiGraph()

# Initial graph (Case 1 Initial)
G.add_edges_from([
    ('B+', 'R1', {'label': 'R1'}),
    ('R1', 'R2', {'label': 'R2'}),
    ('R2', 'R3', {'label': 'R3'}),
    ('R3', 'R4', {'label': 'R4'}),
    ('R4', 'R5', {'label': 'R5'}),
    ('R5', 'B-', {'label': ''}),
    ('B+', 'R4', {'label': ''})  # Parallel path
])

# Step 1: Combine R2 and R3
G_step1 = nx.MultiGraph(G)
G_step1.remove_edge('R2', 'R3')
G_step1.remove_edge('R3', 'R4')
G_step1.add_edge('R1', 'R4', label='R23')

# Step 2: Combine R4 and R5
G_step2 = nx.MultiGraph(G_step1)
G_step2.remove_edge('R4', 'R5')
G_step2.remove_edge('R5', 'B-')
G_step2.add_edge('R1', 'B-', label='R45')

# Step 3: Combine R1 and R23 (parallel) - Phase 1
G_step3 = nx.MultiGraph(G_step2)
G_step3.remove_edge('B+', 'R1')
G_step3.remove_edge('R1', 'R4')
G_step3.add_edge('B+', 'R4', label='R123')

# Step 4: Final combination with R45 - Phase 2
G_step4 = nx.MultiGraph(G_step3)
G_step4.remove_edge('B+', 'R4')
G_step4.remove_edge('R1', 'B-')
G_step4.add_edge('B+', 'B-', label='R12345')

# List of graphs for animation
graphs = [G, G_step1, G_step2, G_step3, G_step4]
titles = ["Initial Circuit", "Step 1: Combine R2 and R3", "Step 2: Combine R4 and R5", 
          "Phase 1: Combine R1 and R23", "Phase 2: Final Combination"]

# Define positions for each step
# Linear layout for initial steps
pos_initial = {'B+': (0, 0), 'R1': (1, 0), 'R2': (2, 0), 'R3': (3, 0), 'R4': (4, 0), 'R5': (5, 0), 'B-': (6, 0)}
pos_step1 = {'B+': (0, 0), 'R1': (1, 0), 'R2': (2, 0), 'R4': (3, 0), 'R5': (4, 0), 'B-': (5, 0)}
pos_step2 = {'B+': (0, 0), 'R1': (1, 0), 'R4': (2, 0), 'B-': (3, 0)}

# Circular/compact layout for Phase 1 and Phase 2
pos_step3 = {'B+': (0, 0), 'R1': (1, 1), 'R4': (1, -1), 'B-': (2, 0)}  # Circular arrangement
pos_step4 = {'B+': (0, 0), 'B-': (1, 0)}  # Compact linear for final step

positions = [pos_initial, pos_step1, pos_step2, pos_step3, pos_step4]

# Define node colors and shapes
node_colors = {
    'B+': 'lightgray', 'R1': 'lightgreen', 'R2': 'lightgreen', 'R3': 'lightgreen',
    'R4': 'lightgreen', 'R5': 'lightgreen', 'B-': 'lightgray',
    'R23': 'lightgreen', 'R45': 'lightgreen', 'R123': 'lightgreen', 'R12345': 'lightgreen'
}
node_shapes = {
    'B+': 'box', 'R1': 'box', 'R2': 'box', 'R3': 'box', 'R4': 'box', 'R5': 'box', 'B-': 'box',
    'R23': 'box', 'R45': 'box', 'R123': 'box', 'R12345': 'box'
}

# Generate frames for animation
frames = []
num_steps = 10  # Number of frames per transition for smooth animation

for i in range(len(graphs) - 1):
    G_start = graphs[i]
    G_end = graphs[i + 1]
    pos_start = positions[i]
    pos_end = positions[i + 1]

    # Interpolate positions between steps
    for t in np.linspace(0, 1, num_steps):
        fig, ax = plt.subplots(figsize=(8, 6))
        pos_interp = {}
        for node in set(pos_start.keys()) | set(pos_end.keys()):
            start_pos = pos_start.get(node, pos_end.get(node, (0, 0)))
            end_pos = pos_end.get(node, pos_start.get(node, (0, 0)))
            pos_interp[node] = (start_pos[0] + t * (end_pos[0] - start_pos[0]), 
                               start_pos[1] + t * (end_pos[1] - start_pos[1]))

        # Draw the graph
        draw_custom_nodes(G_start, pos_interp, ax, node_colors, node_shapes)
        draw_custom_edges(G_start, pos_interp, ax)
        ax.set_title(titles[i])
        ax.set_xlim(-0.5, 6.5)
        ax.set_ylim(-1.5, 1.5)  # Adjusted for circular layout
        ax.axis('off')
        plt.tight_layout()

        # Save frame to a temporary file
        frame = f"temp_frame_{len(frames)}.png"
        plt.savefig(frame)
        plt.close()
        frames.append(imageio.imread(frame))

# Create animated GIF
imageio.mimsave('circuit_simplification_phased_layout.gif', frames, fps=10)

print("Animated GIF 'circuit_simplification_phased_layout.gif' has been created.")
```
![alt text](image-15.png)
```python
import networkx as nx
import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Function to draw nodes as boxes or circles with specific colors
def draw_custom_nodes(G, pos, ax, node_colors, node_shapes):
    for node in G.nodes():
        x, y = pos[node]
        if node_shapes[node] == 'box':
            # Draw a rectangle for resistors
            rect = patches.Rectangle((x - 0.1, y - 0.05), 0.2, 0.1, linewidth=1, edgecolor='black', facecolor=node_colors[node])
            ax.add_patch(rect)
            ax.text(x, y, node, fontsize=10, ha='center', va='center')
        else:
            # Draw a circle for junctions or battery terminals
            circle = patches.Circle((x, y), 0.05, linewidth=1, edgecolor='black', facecolor=node_colors[node])
            ax.add_patch(circle)
            ax.text(x, y, node, fontsize=10, ha='center', va='center')

# Function to draw edges with arrows and labels
def draw_custom_edges(G, pos, ax):
    for (u, v, d) in G.edges(data=True):
        x1, y1 = pos[u]
        x2, y2 = pos[v]
        # Draw an arrow from u to v
        ax.arrow(x1, y1, (x2-x1)*0.8, (y2-y1)*0.8, head_width=0.02, head_length=0.04, fc='black', ec='black')
        # Add edge label
        if 'label' in d and d['label']:
            ax.text((x1+x2)/2, (y1+y2)/2, d['label'], fontsize=10, ha='center', va='center', color='black')

# Series Configuration
G_series = nx.MultiGraph()
G_series.add_edges_from([
    ('In', 'o1', {'label': ''}),
    ('o1', 'R1', {'label': 'R1'}),
    ('R1', 'o2', {'label': ''}),
    ('o2', 'R2', {'label': 'R2'}),
    ('o2', 'o3', {'label': ''}),
    ('o3', 'D1', {'label': 'D1'})
])

# Simplified Series
G_series_simplified = nx.MultiGraph()
G_series_simplified.add_edges_from([
    ('In', 'o1', {'label': ''}),
    ('o1', 'R12', {'label': 'R12'}),
    ('R12', 'o3', {'label': ''}),
    ('o3', 'D1', {'label': 'D1'})
])

# Parallel Configuration
G_parallel = nx.MultiGraph()
G_parallel.add_edges_from([
    ('In', 'o1', {'label': ''}),
    ('o1', 'R1', {'label': 'R1'}),
    ('o1', 'R2', {'label': 'R2'}),
    ('R1', 'o3', {'label': ''}),
    ('R2', 'o3', {'label': ''}),
    ('o3', 'D1', {'label': 'D1'})
])

# Simplified Parallel
G_parallel_simplified = nx.MultiGraph()
G_parallel_simplified.add_edges_from([
    ('In', 'o1', {'label': ''}),
    ('o1', 'R12', {'label': 'R12'}),
    ('R12', 'o3', {'label': ''}),
    ('o3', 'D1', {'label': 'D1'})
])

# Define custom positions for linear/structured layout
pos_series = {
    'In': (0, 0), 'o1': (1, 0), 'R1': (2, 0), 'o2': (3, 0), 'R2': (4, 0), 'o3': (5, 0), 'D1': (6, 0)
}
pos_series_simplified = {
    'In': (0, 0), 'o1': (1, 0), 'R12': (3, 0), 'o3': (5, 0), 'D1': (6, 0)
}
pos_parallel = {
    'In': (0, 0), 'o1': (1, 0), 'R1': (2, 1), 'R2': (2, -1), 'o3': (3, 0), 'D1': (4, 0)
}
pos_parallel_simplified = {
    'In': (0, 0), 'o1': (1, 0), 'R12': (2, 0), 'o3': (3, 0), 'D1': (4, 0)
}

# Define node colors and shapes
node_colors_series = {'In': 'lightgray', 'o1': 'white', 'R1': 'lightgreen', 'o2': 'white', 'R2': 'lightgreen', 'o3': 'white', 'D1': 'lightgray'}
node_colors_series_simplified = {'In': 'lightgray', 'o1': 'white', 'R12': 'lightgreen', 'o3': 'white', 'D1': 'lightgray'}
node_colors_parallel = {'In': 'lightgray', 'o1': 'white', 'R1': 'lightblue', 'R2': 'lightblue', 'o3': 'white', 'D1': 'lightgray'}
node_colors_parallel_simplified = {'In': 'lightgray', 'o1': 'white', 'R12': 'lightblue', 'o3': 'white', 'D1': 'lightgray'}

node_shapes_series = {'In': 'box', 'o1': 'circle', 'R1': 'box', 'o2': 'circle', 'R2': 'box', 'o3': 'circle', 'D1': 'box'}
node_shapes_series_simplified = {'In': 'box', 'o1': 'circle', 'R12': 'box', 'o3': 'circle', 'D1': 'box'}
node_shapes_parallel = {'In': 'box', 'o1': 'circle', 'R1': 'box', 'R2': 'box', 'o3': 'circle', 'D1': 'box'}
node_shapes_parallel_simplified = {'In': 'box', 'o1': 'circle', 'R12': 'box', 'o3': 'circle', 'D1': 'box'}

# Draw graphs
fig, axes = plt.subplots(2, 2, figsize=(12, 8))

# Series Configuration
ax = axes[0, 0]
draw_custom_nodes(G_series, pos_series, ax, node_colors_series, node_shapes_series)
draw_custom_edges(G_series, pos_series, ax)
ax.set_title("Series Configuration")
ax.set_xlim(-0.5, 6.5)
ax.set_ylim(-0.5, 0.5)
ax.axis('off')

# Simplified Series
ax = axes[0, 1]
draw_custom_nodes(G_series_simplified, pos_series_simplified, ax, node_colors_series_simplified, node_shapes_series_simplified)
draw_custom_edges(G_series_simplified, pos_series_simplified, ax)
ax.set_title("Simplified Series (R12 = R1 + R2)")
ax.set_xlim(-0.5, 6.5)
ax.set_ylim(-0.5, 0.5)
ax.axis('off')

# Parallel Configuration
ax = axes[1, 0]
draw_custom_nodes(G_parallel, pos_parallel, ax, node_colors_parallel, node_shapes_parallel)
draw_custom_edges(G_parallel, pos_parallel, ax)
ax.set_title("Parallel Configuration")
ax.set_xlim(-0.5, 4.5)
ax.set_ylim(-1.5, 1.5)
ax.axis('off')

# Simplified Parallel
ax = axes[1, 1]
draw_custom_nodes(G_parallel_simplified, pos_parallel_simplified, ax, node_colors_parallel_simplified, node_shapes_parallel_simplified)
draw_custom_edges(G_parallel_simplified, pos_parallel_simplified, ax)
ax.set_title("Simplified Parallel (R12 = R1 || R2)")
ax.set_xlim(-0.5, 4.5)
ax.set_ylim(-0.5, 0.5)
ax.axis('off')

plt.tight_layout()
plt.show()
```
![alt text](image-16.png)
```python
import networkx as nx
import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Function to draw nodes as boxes or circles with specific colors
def draw_custom_nodes(G, pos, ax, node_colors, node_shapes):
    for node in G.nodes():
        x, y = pos[node]
        if node_shapes[node] == 'box':
            # Draw a rectangle for resistors, battery terminals, or diodes
            rect = patches.Rectangle((x - 0.1, y - 0.05), 0.2, 0.1, linewidth=1, edgecolor='black', facecolor=node_colors[node])
            ax.add_patch(rect)
            ax.text(x, y, node, fontsize=10, ha='center', va='center')
        else:
            # Draw a circle for junctions
            circle = patches.Circle((x, y), 0.05, linewidth=1, edgecolor='black', facecolor=node_colors[node])
            ax.add_patch(circle)
            ax.text(x, y, node, fontsize=10, ha='center', va='center')

# Function to draw edges with arrows and labels
def draw_custom_edges(G, pos, ax):
    for (u, v, d) in G.edges(data=True):
        x1, y1 = pos[u]
        x2, y2 = pos[v]
        # Draw an arrow from u to v
        ax.arrow(x1, y1, (x2-x1)*0.8, (y2-y1)*0.8, head_width=0.02, head_length=0.04, fc='black', ec='black')
        # Add edge label if it exists
        if 'label' in d and d['label']:
            ax.text((x1+x2)/2, (y1+y2)/2, d['label'], fontsize=10, ha='center', va='center', color='black')

# Series Configuration
G_series = nx.MultiGraph()
G_series.add_edges_from([
    ('B+', 'o1'), ('o1', 'R1'), ('R1', 'o2'), ('o2', 'R2'), ('o2', 'R3'), ('R3', 'o3'), ('o3', 'B-')
])
G_series.add_edges_from([('o2', 'D1'), ('o2', 'D4')])  # Parallel diodes

# Simplified Series (replaced by R12)
G_series_simplified = nx.MultiGraph()
G_series_simplified.add_edges_from([
    ('B+', 'o1'), ('o1', 'R12', label='R1+R2+R3'), ('R12', 'o3'), ('o3', 'B-'),
    ('o2', 'D1'), ('o2', 'D4')
])

# Parallel Configuration
G_parallel = nx.MultiGraph()
G_parallel.add_edges_from([
    ('B+', 'o1'), ('o1', 'R1', label='R1'), ('o1', 'R2', label='R2'), ('R1', 'o3'), ('R2', 'o3'),
    ('o3', 'B-')
])
G_parallel.add_edges_from([('o1', 'D1'), ('o3', 'D4')])  # Parallel diodes

# Simplified Parallel (replaced by R12)
G_parallel_simplified = nx.MultiGraph()
G_parallel_simplified.add_edges_from([
    ('B+', 'o1'), ('o1', 'R12', label='R1||R2'), ('R12', 'o3'), ('o3', 'B-'),
    ('o1', 'D1'), ('o3', 'D4')
])

# Define custom positions for linear/structured layout
pos_series = {
    'B+': (0, 0), 'o1': (1, 0), 'R1': (2, 0), 'o2': (3, 0), 'R2': (4, 0), 'R3': (5, 0), 'o3': (6, 0), 'B-': (7, 0),
    'D1': (3, 1), 'D4': (3, -1)
}
pos_series_simplified = {
    'B+': (0, 0), 'o1': (1, 0), 'R12': (3.5, 0), 'o3': (6, 0), 'B-': (7, 0),
    'o2': (3, 0), 'D1': (3, 1), 'D4': (3, -1)
}
pos_parallel = {
    'B+': (0, 0), 'o1': (1, 0), 'R1': (2, 1), 'R2': (2, -1), 'o3': (3, 0), 'B-': (4, 0),
    'D1': (1, 1), 'D4': (3, 1)
}
pos_parallel_simplified = {
    'B+': (0, 0), 'o1': (1, 0), 'R12': (2, 0), 'o3': (3, 0), 'B-': (4, 0),
    'D1': (1, 1), 'D4': (3, 1)
}

# Define node colors and shapes
node_colors_series = {
    'B+': 'lightgray', 'o1': 'white', 'R1': 'lightgreen', 'o2': 'white', 'R2': 'lightgreen', 'R3': 'lightgreen',
    'o3': 'white', 'B-': 'lightgray', 'D1': 'lightgray', 'D4': 'lightgray'
}
node_colors_series_simplified = {
    'B+': 'lightgray', 'o1': 'white', 'R12': 'lightgreen', 'o3': 'white', 'B-': 'lightgray',
    'o2': 'white', 'D1': 'lightgray', 'D4': 'lightgray'
}
node_colors_parallel = {
    'B+': 'lightgray', 'o1': 'white', 'R1': 'lightblue', 'R2': 'lightblue', 'o3': 'white', 'B-': 'lightgray',
    'D1': 'lightgray', 'D4': 'lightgray'
}
node_colors_parallel_simplified = {
    'B+': 'lightgray', 'o1': 'white', 'R12': 'lightblue', 'o3': 'white', 'B-': 'lightgray',
    'D1': 'lightgray', 'D4': 'lightgray'
}

node_shapes_series = {
    'B+': 'box', 'o1': 'circle', 'R1': 'box', 'o2': 'circle', 'R2': 'box', 'R3': 'box',
    'o3': 'circle', 'B-': 'box', 'D1': 'box', 'D4': 'box'
}
node_shapes_series_simplified = {
    'B+': 'box', 'o1': 'circle', 'R12': 'box', 'o3': 'circle', 'B-': 'box',
    'o2': 'circle', 'D1': 'box', 'D4': 'box'
}
node_shapes_parallel = {
    'B+': 'box', 'o1': 'circle', 'R1': 'box', 'R2': 'box', 'o3': 'circle', 'B-': 'box',
    'D1': 'box', 'D4': 'box'
}
node_shapes_parallel_simplified = {
    'B+': 'box', 'o1': 'circle', 'R12': 'box', 'o3': 'circle', 'B-': 'box',
    'D1': 'box', 'D4': 'box'
}

# Draw graphs
fig, axes = plt.subplots(2, 2, figsize=(12, 8))

# Series Configuration
ax = axes[0, 0]
draw_custom_nodes(G_series, pos_series, ax, node_colors_series, node_shapes_series)
draw_custom_edges(G_series, pos_series, ax)
ax.set_title("Series Configuration")
ax.set_xlim(-0.5, 7.5)
ax.set_ylim(-1.5, 1.5)
ax.axis('off')

# Simplified Series
ax = axes[0, 1]
draw_custom_nodes(G_series_simplified, pos_series_simplified, ax, node_colors_series_simplified, node_shapes_series_simplified)
draw_custom_edges(G_series_simplified, pos_series_simplified, ax)
ax.set_title("Simplified Series")
ax.set_xlim(-0.5, 7.5)
ax.set_ylim(-1.5, 1.5)
ax.axis('off')

# Parallel Configuration
ax = axes[1, 0]
draw_custom_nodes(G_parallel, pos_parallel, ax, node_colors_parallel, node_shapes_parallel)
draw_custom_edges(G_parallel, pos_parallel, ax)
ax.set_title("Parallel Configuration")
ax.set_xlim(-0.5, 4.5)
ax.set_ylim(-1.5, 1.5)
ax.axis('off')

# Simplified Parallel
ax = axes[1, 1]
draw_custom_nodes(G_parallel_simplified, pos_parallel_simplified, ax, node_colors_parallel_simplified, node_shapes_parallel_simplified)
draw_custom_edges(G_parallel_simplified, pos_parallel_simplified, ax)
ax.set_title("Simplified Parallel")
ax.set_xlim(-0.5, 4.5)
ax.set_ylim(-1.5, 1.5)
ax.axis('off')

plt.tight_layout()
plt.show()
```
## 7. Conclusion

The graph-theoretic approach to simplifying electrical circuits provides a systematic and mathematically rigorous method for calculating equivalent resistance, as demonstrated through Case 1 and additional examples. By modeling circuits as graphs and applying iterative series and parallel reductions, we transform complex networks into a single equivalent resistance, such as $R_{eq} = 21\Omega$ for the series circuit in Case 1. The algorithm, with its ability to handle nested combinations through iterative simplification, proves versatile across configurations, yielding $R_{eq} = 9\Omega$ for a simple series circuit, $R_{eq} = 2\Omega$ for a parallel circuit, and $R_{eq} = 7\Omega$ for a nested series-parallel circuit. Despite a time complexity of $O((|V| + |E|)^2)$, potential enhancements like DFS-based pattern detection and delta-star transformations could reduce this to $O(|V| + |E|)$ per reduction, making the method highly efficient for large-scale circuit analysis. This framework not only deepens our understanding of circuit behavior but also lays the groundwork for advanced applications in electrical engineering, such as optimizing circuit design and analyzing power distribution networks.

$$ R_{eq} = R_1 + R_2 \quad \text{(Series Combination)} $$

$$ R_{eq} = \frac{R_1 \cdot R_2}{R_1 + R_2} \quad \text{(Parallel Combination)} $$

$$ R_{star} = \frac{R_{delta}^2}{\sum R_{delta}} \quad \text{(Delta-Star Transformation)} $$

## Colab
[Colab8](https://colab.research.google.com/drive/1VsM05vl8oYle0gtSq_aOMugcn0R4Evza)




