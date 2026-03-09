# Lab-of-Geometry-GGT-in-lean
# Lean-Cayley: Formalizing Geometric Group Theory in Lean 4

This repository contains a formalization of foundational concepts in **Geometric Group Theory (GGT)** using the **Lean 4** interactive theorem prover. The project focuses on the structural properties of Cayley graphs, their connectivity, and metric properties.

## 🚀 Core Features

### 1. Cayley Graph Construction
* **Quiver Implementation**: Defined the Cayley graph as a `Quiver` where vertices are group elements and edges are labeled by generators[cite: 8, 44].
* **Symmetry & Generation**: Implemented predicates for symmetric generating sets (`IsSymmetric`) and group generation (`IsGenerating`).
* **Inverse Edges**: Proved that every edge has a reverse edge given a symmetric generating set[cite: 9, 45].

### 2. Connectivity Theorems
* **Main Theorem**: Formalized the proof that a Cayley graph is connected if and only if the set $S$ generates the group $G$[cite: 13, 37, 54].
* **Inductive Strategy**: Utilized submonoid induction to bridge the gap between algebraic group generation and graph-theoretical path existence[cite: 20, 62].
* **Path Shifting**: Developed a `shiftPath` mechanism to leverage left-translation invariance, allowing paths to be moved across the graph[cite: 11, 49].

### 3. Geometric Properties & Automorphisms
* **Left-Multiplication Automorphism**: Rigorously proved that left multiplication by a group element induces a graph automorphism[cite: 1, 4].
* **Word Metrics**: Defined `wordLength` as the shortest path from the identity [cite: 74] [cite_start]and `wordDist` using the translation-invariant formula $d_S(g, h) = |g^{-1}h|_S$[cite: 76].
* **Labeled Automorphisms**: Defined a structure for automorphisms that preserve edge labels[cite: 7].



## 📂 File Structure

| File | Description |
| :--- | :--- |
| `Cay.lean` | [cite_start]Core definitions of `CayleyGraph`, `Quiver` instances, and connectivity logic. |
| `Automorphism.lean` | [cite_start]Proofs regarding left-multiplication and `LabeledAut` structures. |
| `CayleyConnectivity.lean` | [cite_start]Detailed implementation strategy for the connectivity theorem. |
| `wordlength.lean` | [cite_start]Definitions of word length and word distance via `sInf` of path lengths. |

## 🛠️ Technical Implementation Details

The proof of `Isconnected` follows a 5-step strategy:
1. **Target Reduction**: Reduce $g \to h$ connectivity to $1 \to g^{-1}h$[cite: 40].
2. **Symmetry Handling**: Convert `Subgroup.closure` to `Submonoid.closure` using the symmetry of $S$[cite: 27, 57].
3. **Submonoid Induction**: Prove reachability for all elements in the closure[cite: 62].
4. **Path Shifting**: Implement left translation on `Quiver.Path`[cite: 11, 49].
5. **Endpoint Simplification**: Use group axioms to show the shifted path ends at the correct vertex[cite: 32, 71].

