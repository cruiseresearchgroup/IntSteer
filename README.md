
# IntSteer — Mechanistic Indicators of Steering Success in Large Language Models

**IntSteer** is a research codebase for analyzing the internal mechanistic signals that govern the success and failure of activation-based steering in large language models (LLMs).

> **Preprint title:**  
> *Mechanistic Indicators of Steering Effectiveness in Large Language Models*

---

## Overview

Activation-based steering enables large language models to exhibit targeted behaviors by intervening on intermediate activations—without retraining. Despite its widespread adoption, the mechanistic conditions under which steering succeeds or fails remain poorly understood. Most existing work evaluates steering exclusively through black-box behavioral outputs and LLM-based judges.



The project extends prior work on activation-based steering—particularly  
[SAE-TS](https://github.com/slavachalnev/SAE-TS)—with the following contributions:

- Integration of an additional, architecturally distinct **Gemini-based LLM judge**
- Extraction of **mechanistic interpretability signals** during generation
- A **regression-based prediction pipeline** for steering quality
- Introduction of a **new rotation-based steering function**


---

## Abstract

Activation-based steering enables large language models (LLMs) to exhibit targeted behaviors by intervening on intermediate activations without retraining. Despite its widespread use, the mechanistic conditions under which steering succeeds or fails remain poorly understood, as existing research relies largely on black-box outputs and LLM-based judges.

In this work, we examine whether steering reliability can be assessed using internal model signals. We focus on two information-theoretic measures: the entropy-derived **Normalized Branching Factor (NBF)** and the **Kullback–Leibler (KL) divergence** between steered activations and targeted concept distributions in vocabulary space.

We hypothesize that effective steering is characterized by structured entropy preservation and coherent KL alignment across decoding steps. Following a reliability study demonstrating strong inter-judge agreement between two architecturally distinct LLMs, we employ LLM-generated annotations as ground truth. Our results show that mechanistic signals extracted from the model provide meaningful predictive power for identifying steering success and estimating failure probability.

Finally, we introduce a stronger evaluation baseline for **Contrastive Activation Addition (CAA)** and **Sparse Autoencoder (SAE)**–based steering—the two most widely adopted activation-based steering approaches.



## Installation

Install the package in editable mode:

```bash
pip install -e .
```

## Environment Setup

Create a `.env` file in the project root containing your OpenAI API key  
(required only for LLM-based evaluation):

`OPENAI_API_KEY="sk-..."`
## Running Experiments

To run the full evaluation pipeline:

`python -m sae_ts.baselines.analysis`

This command executes:

-   **2 steering vector extraction methods**
    
    -   Contrastive Activation Addition (CAA)
        
    -   Sparse Autoencoder (SAE)
        
-   **2 steering functions**
    
    -   Additive steering
        
    -   Rotation-based steering
        
-   **9 steering concepts**
    
