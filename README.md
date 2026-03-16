# CacheForge++: LLM-Driven Cache Replacement Policy Discovery

This project extends the **CacheForge** LLM-in-the-loop framework into a full **agentic discovery system** capable of automatically generating, evaluating, and refining last-level cache (LLC) replacement policies. Our goal was to outperform state-of-the-art baseline policies across **SPEC CPU 2006** workloads—specifically targeting improvements in **Instructions Per Cycle (IPC)** under strict metadata constraints.

---

## Enhancements to CacheForge

### **1. Graph-of-Thought (GoT) Memory**
A persistent, structured reasoning graph that stores:
- Candidate policies  
- Lineage relationships  
- Performance metrics  
- Design patterns  

GoT enables long-range reasoning across iterations, avoids repeated mistakes, and guides the LLM toward productive regions of the design space.

---

### **2. Surrogate Performance Model**
A lightweight, feature-based predictor (**Ridge Regression**) that evaluates candidate policies without costly ChampSim simulations.  
This model:
- Filters poor candidates early  
- Reduces the number of full simulations by **up to 10×**

---

We trained the model with over 2000+ samples. 

### **3. Intelligent Search Strategy**
A dynamic mixture of:
- **Lineage diversity** (exploration)  
- **Performance-guided refinement** (exploitation)  
- **Novelty injection** (breakthrough discovery)  

This structure ensures both breadth and depth as the system evolves policies over time. The strategy also used our DAG and our discovery log path to reason for future iterations.

---

## Policy Explainer Module
An automatic **C++-to-JSON** summarizer that interprets cache replacement policies and generates structured, human-readable representations.

---

## Evolutionary Discovery Artifacts
The system outputs:
- Discovery database (`GoT.db`)  
- Lineage graphs  
- All generated policies  
- Scored surrogate predictions  
- ChampSim results for every iteration  

> **Note:** Different experiments, files, and scripts vary across branches.  
> See our final report for more details.

---

# How to Run the Framework

You may execute the evolutionary search loop **through the HPC** or **locally**.

---

## HPC Execution (Recommended)

Inside `run_loop/`, submit:

```bash
bsub < reproduce.sh
```
or locally:

python3 run_loop.py

