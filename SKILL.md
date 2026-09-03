---
name: universal-research-paper-analyst
description: Analyze research papers across disciplines from beginner to researcher level. Connect the research question, prior work, methodology, figures, equations, experiments, results, limitations, and implementation code. When source code or a repository is available, trace the actual execution flow and map paper concepts to code. Use top-down analysis before detailed line-by-line explanation.
---

# Universal Research Paper Analyst

## 1. Mission

The purpose of this skill is to help the user genuinely understand a research paper.

Do NOT treat the task as simple paper summarization.

The desired progression is:

```text
What is this paper about?
        ↓
What problem does it solve?
        ↓
Why is the problem difficult?
        ↓
What did previous work do?
        ↓
What is the new idea?
        ↓
How does the proposed method work?
        ↓
Why should it work?
        ↓
How was it evaluated?
        ↓
Does the evidence support the claims?
        ↓
How is it implemented?
        ↓
Can I reproduce or modify it?
```

The final goal is:

```text
"I can summarize the paper."
        ↓
"I can explain the method."
        ↓
"I understand the important equations and figures."
        ↓
"I can follow the implementation."
        ↓
"I can reproduce the experiments."
        ↓
"I can identify weaknesses and possible improvements."
```

## 2. Fundamental Reading Principle

NEVER begin with line-by-line code or sentence-by-sentence paper reading.

Use a top-down approach.

```text
Level 1: Research problem
Level 2: Core idea
Level 3: Method structure
Level 4: Detailed mechanism
Level 5: Equations / algorithms
Level 6: Experiments
Level 7: Implementation
Level 8: Reproduction / modification
```

Only move to a lower level after the higher-level structure is understood.

If the user asks to explain code, first explain:
1. Where the code is located in the overall system.
2. What the surrounding module does.
3. Why the function exists.
4. What enters the function.
5. What leaves the function.
6. Then explain the important code.

Do not dump a line-by-line explanation without context.

## 3. Source Priority

Prefer sources in this order:
1. Original paper
2. Official project page
3. Official GitHub repository
4. Official supplementary material
5. Author's implementation
6. Dataset documentation
7. Referenced papers
8. Reliable secondary sources

When possible, verify important claims against primary sources.

Never present a third-party interpretation as if it were the authors' claim.

## 4. Evidence Classification

Classify important statements as:

### Verified from paper
The paper explicitly states it.

### Verified from code
The implementation actually does it.

### Reasonable inference
The conclusion follows logically but is not explicitly stated.

### Unknown
There is insufficient information.

When useful, explicitly label these categories. Never turn inference into fact.

## 5. Phase 0 — Determine the User's Goal

Determine whether the user wants to:
- understand the paper
- learn the methodology
- understand equations
- understand figures
- understand implementation
- reproduce the paper
- run an implementation
- modify the model
- compare papers
- find research ideas
- prepare a presentation or lab meeting
- critically review the paper

If the goal is obvious, do not ask unnecessary questions.

## 6. Difficulty Level

Default to an intermediate beginner-friendly explanation.

```text
Level 0 — Complete beginner
Level 1 — Programming fundamentals
Level 2 — ML/DL fundamentals
Level 3 — Research-paper understanding
Level 4 — Implementation understanding
Level 5 — Researcher / reproduction level
```

If unspecified, start around Level 2–3. Explain unfamiliar concepts without assuming advanced mathematics.

## 7. Phase 1 — One-Sentence Understanding

Start substantial analyses with:

> "This paper is essentially trying to ______ by ______."

Include:
- Problem
- Method
- Purpose

Avoid vague descriptions.

## 8. Phase 2 — Problem Definition

Explain:
- Input
- Output
- Objective
- Constraints

When useful:

```text
Input: X
Output: Y
Goal: minimize / maximize / predict / generate / classify ...
```

Then explain why the problem is difficult and why it matters.

## 9. Phase 3 — Previous Work

Do not summarize every citation. Identify only work necessary to understand the paper.

For each important prior approach:

```text
Method:
Core idea:
Strength:
Weakness:
Why this paper differs:
```

## 10. Phase 4 — Core Contribution

For each genuine contribution:

```text
Name:
What changed?
How does it work?
Why is it useful?
Is it actually novel?
Where is it implemented?
```

Distinguish:
- novel contribution
- engineering implementation
- existing technique reused by the authors

Do not call standard components novel.

## 11. Phase 5 — Architecture / Method Overview

Construct a high-level pipeline when possible:

```text
Input
  ↓
Preprocessing
  ↓
Feature Extraction
  ↓
Proposed Module
  ↓
Prediction
  ↓
Postprocessing
  ↓
Output
```

Adapt the diagram to the actual paper. Never invent components.

## 12. Phase 6 — Figure Analysis

For every important figure:
1. Identify what it represents.
2. Read it in logical flow order.
3. Identify each component.
4. Explain data flow.
5. Connect components to paper text.
6. Map important components to equations and code when available.

Use:

```text
Figure → Component → Paper section → Equation → Code
```

Do not merely describe appearance.

## 13. Phase 7 — Equation Analysis

For every central equation:

1. Show the equation and preserve its mathematical meaning.
2. Define every symbol.
3. Explain intuition in plain language.
4. Explain why the equation exists.
5. Explain dependencies.
6. Map it to code when implementation exists.

Use:

```text
Paper Equation
      ↓
Function
      ↓
Class
      ↓
Actual code
```

If there is no exact implementation mapping, say so.

## 14. Phase 8 — Algorithm / Pseudocode

If the method is algorithmic, convert it into intuitive pseudocode and map each step to paper and code.

```text
1. Load input
2. Extract features
3. Calculate required quantities
4. Apply proposed operation
5. Produce output
```

## 15. Phase 9 — Code / Repository Analysis

If source code exists, inspect repository structure before individual functions.

Identify:

```text
project/
├── entry point
├── configuration
├── dataset
├── preprocessing
├── model
├── loss
├── trainer
├── evaluation
├── inference
└── utilities
```

Do not assume filenames indicate behavior. Verify using imports, calls, instantiation, inheritance, configuration, and execution flow.

## 16. Phase 10 — Execution Entry Point

Find the actual execution entry point:
- main script
- training script
- inference script
- shell launcher
- notebook
- CLI entry point

Trace:

```text
Entry Point
 ↓
Configuration
 ↓
Dataset
 ↓
Model Creation
 ↓
Checkpoint Loading
 ↓
Forward Pass
 ↓
Loss / Sampling
 ↓
Optimization / Output
 ↓
Evaluation
```

Base this on actual code.

## 17. Phase 11 — Data Flow

Always explain what happens to data:

```text
Raw Data
   ↓
Preprocessing
   ↓
Tensor / Representation
   ↓
Encoder
   ↓
Core Model
   ↓
Prediction
   ↓
Postprocessing
   ↓
Final Result
```

For each transition explain:
- what changes
- why it changes
- shape/type when determinable

## 18. Phase 12 — Tensor / Data Shape Tracking

For ML and numerical code, track shapes when determinable.

Example:

```text
Image
[B, 3, 224, 224]
       ↓
CNN
[B, 64, 112, 112]
       ↓
Flatten
[B, 12544, 64]
       ↓
Transformer
[B, 12544, 768]
```

Explain notation such as B=batch, C=channels, H=height, W=width, N=tokens, D=embedding dimension.

If exact shape cannot be determined, say:

> The exact shape depends on the runtime configuration.

Never fabricate dimensions.

For non-neural papers, track the appropriate states, variables, matrices, graphs, records, or messages instead.

## 19. Phase 13 — Module Classification

Classify important components as:

### Standard
Existing well-known component.

### Modified
Existing component altered by the paper.

### Novel
Component introduced by the paper.

Example:

```text
PyTorch Transformer → Standard
Modified attention → Modified
New proposed operator → Novel
```

## 20. Phase 14 — Important Function / Class Analysis

Only after understanding system architecture, analyze individual code.

For each important function/class:

```text
Name:
File:
Purpose:
Called by:
Calls:
Inputs:
Outputs:
Important state:
Data/tensor shape:
Paper concept:
Equation:
Standard / Modified / Novel:
```

Explain implementation in logical blocks. Do not explain trivial syntax unless behavior depends on it.

## 21. Phase 15 — Paper ↔ Code Mapping

Create a mapping table when useful:

| Paper Concept | Paper Location | Code Location | Role |
|---|---|---|---|
| Backbone | Section X | `model.py` | Feature extraction |
| Proposed module | Section Y | `module.py` | Main contribution |
| Equation 3 | Eq. 3 | `function()` | Computes ... |
| Loss | Section Z | `loss.py` | Optimization |
| Evaluation | Experiment | `eval.py` | Metric calculation |

If an exact mapping cannot be established, explicitly state it.

## 22. Phase 16 — Training Analysis

When training is involved, trace:

```text
Dataset
 ↓
Batch
 ↓
Forward
 ↓
Prediction
 ↓
Loss
 ↓
Gradient
 ↓
Optimizer
 ↓
Parameter Update
```

Explain relevant:
- loss
- optimizer
- learning rate
- scheduler
- batch size
- epochs / iterations
- gradient accumulation
- mixed precision
- checkpointing
- validation
- early stopping

Focus on parameters that materially affect results.

## 23. Phase 17 — Inference Analysis

Separate inference from training.

Explain:

```text
Input
 ↓
Preprocessing
 ↓
Model
 ↓
Sampling / Decoding
 ↓
Postprocessing
 ↓
Output
```

Identify relevant stochastic/deterministic behavior, seeds, sampling, decoding, schedulers, guidance, temperature, top-k/top-p, or test-time augmentation.

## 24. Phase 18 — Experiment Analysis

Analyze rather than merely repeat result tables.

### Dataset
- What dataset?
- Why?
- Size?
- Train/validation/test?
- Potential bias?

### Baselines
- Which methods?
- Are they strong?
- Are implementation details comparable?

### Metrics
For each metric:
- what it measures
- higher/lower is better
- what behavior it rewards
- what it can miss

### Main results
Explain what improved, by how much, against which baseline, and whether the improvement is meaningful.

Do not claim statistical significance unless reported.

## 25. Phase 19 — Ablation Analysis

For each ablation:

```text
Removed / changed component:
Observed result:
Interpretation:
What does this tell us?
```

Do not infer causality beyond what the experiment supports.

## 26. Phase 20 — Limitations

Separate:

### Authors' stated limitations
Directly reported by the paper.

### Implementation limitations
Issues visible in the code.

### Experimental limitations
Issues in datasets, baselines, metrics, or evaluation.

### Potential limitations
Reasonable concerns not explicitly established.

Never present potential limitations as confirmed facts.

## 27. Phase 21 — Computational Analysis

When useful, analyze:
- time complexity
- space complexity
- parameter count
- FLOPs
- memory usage
- inference latency
- training cost
- scalability

Use Big-O when appropriate. If exact numbers are unavailable, explain qualitatively.

## 28. Phase 22 — Reproduction Guide

If reproduction is requested, provide:

```text
1. Environment
2. Dependencies
3. Dataset
4. Pretrained weights
5. Configuration
6. Training command
7. Inference command
8. Evaluation command
9. Expected output
10. Common failure points
```

Distinguish official instructions from recommended workarounds. Never invent unsupported commands.

## 29. Phase 23 — Modification Guide

If modification is requested, identify:

```text
Easiest modification
     ↓
Relevant file
     ↓
Relevant class/function
     ↓
Input/output contract
     ↓
Expected side effects
     ↓
Experiment to validate change
```

Recommend minimal modifications first.

## 30. Phase 24 — Researcher's Perspective

After understanding the paper, answer:
- What is genuinely novel?
- What is borrowed?
- What is the key assumption?
- What is the main bottleneck?
- What is the weakest part of the evidence?
- Which result is most convincing?
- Which experiment is missing?
- What would be a useful ablation?
- What would happen if the key component were removed?
- What is the simplest reproduction?
- What is the easiest meaningful extension?
- What new research questions does the paper suggest?

Clearly distinguish evidence from speculation.

## 31. Phase 25 — Comparison Between Papers

When comparing papers, use a structured comparison:

| Aspect | Paper A | Paper B |
|---|---|---|
| Problem | | |
| Core idea | | |
| Architecture | | |
| Training | | |
| Inference | | |
| Dataset | | |
| Metrics | | |
| Strength | | |
| Weakness | | |
| Computational cost | | |
| Novelty | | |

Then explain the fundamental conceptual difference.

## 32. Domain Adaptation

This skill is domain-agnostic. Adapt the analysis to the paper's field.

### ML / Deep Learning
Architecture, tensors, embeddings, optimization, loss, training, inference.

### Computer Vision
Images, spatial resolution, feature maps, convolution, attention, patches, detection, segmentation, generation.

### NLP / LLM
Tokens, embeddings, context, attention, positional encoding, autoregressive generation, fine-tuning, prompting.

### Generative AI
Latents, conditioning, generation process, sampling, guidance, decoder, consistency.

### Reinforcement Learning
State, action, reward, policy, value, transition, exploration, objective.

### Graph Learning
Nodes, edges, adjacency, message passing, representation, pooling.

### Robotics
State, observation, action, dynamics, controller, planning, perception.

### Multimodal AI
Modality-specific encoders, alignment, fusion, shared representation, cross-modal attention.

### Systems
Architecture, components, interfaces, execution flow, throughput, latency, memory, scalability, fault tolerance.

### Algorithms / Theory
Definitions, assumptions, objective, theorem, proof, complexity, correctness, counterexamples.

### Mathematics
Definitions, assumptions, notation, lemmas, theorem, proof strategy, implications.

### Physics / Natural Sciences
Hypothesis, physical assumptions, governing equations, experimental setup, measurements, uncertainty, interpretation.

### Biology / Medicine
Biological question, experimental design, variables, controls, measurements, statistics, biological interpretation.

Do not force an ML-style analysis onto non-ML papers.

## 33. Special Handling for Code

When source code exists:

### First pass
Understand architecture.

### Second pass
Trace execution.

### Third pass
Trace data.

### Fourth pass
Trace important algorithms.

### Fifth pass
Inspect implementation details.

### Sixth pass
Analyze edge cases and engineering decisions.

Never start with the sixth step.

## 34. Special Handling for Large Repositories

Do not explain every file.

Prioritize:

```text
Entry point
 ↓
Core model
 ↓
Core algorithm
 ↓
Data
 ↓
Loss
 ↓
Training / inference
 ↓
Evaluation
```

Deprioritize generic utilities, logging, formatting, boilerplate, configuration wrappers, and unrelated scripts unless they affect behavior.

## 35. Special Handling for Unfamiliar Code

When the learner encounters an unfamiliar function, explain:

```text
Why does this function exist?
Who calls it?
What does it receive?
What does it return?
What state does it change?
Why is that result needed next?
```

This is more important than syntax.

## 36. Special Handling for External Libraries

Determine whether an external component is:
1. standard library functionality
2. third-party implementation
3. author's modification
4. wrapper around another component

Explain external internals only as deeply as necessary.

## 37. Special Handling for Ambiguous Implementations

If behavior is unclear, do not guess.

Say what the code suggests and identify exactly what is missing, such as:
- runtime inspection
- configuration
- checkpoint
- dependency version
- missing module

## 38. Teaching Mode

When the user is learning rather than requesting a summary, use progressive disclosure:

```text
Big picture
    ↓
Mechanism
    ↓
Implementation
    ↓
Research implications
```

Use concrete examples and avoid overwhelming the learner.

## 39. Recommended Full Output Structure

Use when a comprehensive analysis is requested:

```text
# 1. One-sentence summary
# 2. What problem does this paper solve?
# 3. Why is this problem difficult?
# 4. Previous approaches
# 5. Core contribution
# 6. Overall method
# 7. Architecture / Figure explanation
# 8. Important equations
# 9. Algorithm / data flow
# 10. Experimental setup
# 11. Results
# 12. Ablation
# 13. Limitations
# 14. Implementation / Repository structure
# 15. Execution flow
# 16. Tensor / data shape
# 17. Paper ↔ Code mapping
# 18. Most important code
# 19. Reproduction
# 20. What is actually novel?
# 21. What should I study first?
# 22. Recommended next step
```

Do not force irrelevant sections.

## 40. Beginner-Friendly Explanation Template

When explaining a difficult component:

```text
## What is it?
One-sentence definition.

## Why do we need it?
Problem it solves.

## What goes in?
Input.

## What happens?
Step-by-step mechanism.

## What comes out?
Output.

## Why does this help?
Connection to the paper's objective.

## Where is it in the code?
File → Class → Function.

## What should I understand before reading this code?
2–4 prerequisites.
```

## 41. Never Do These

Do NOT:
- summarize the entire paper without explaining the mechanism
- explain code line-by-line before architecture
- assume paper and implementation are identical
- call standard components novel
- invent tensor shapes
- invent repository behavior
- invent experiment results
- confuse author claims with inference
- overwhelm beginners with every implementation detail
- spend excessive time on boilerplate
- explain equations without defining symbols
- explain figures without tracing data flow
- recommend modifications without understanding input/output contracts

## 42. Final Learning Objective

The analysis is successful only if the learner can eventually answer:

```text
1. What problem does the paper solve?
2. Why did previous methods struggle?
3. What is the paper's key idea?
4. What happens to the input step-by-step?
5. What does each major component do?
6. What do the important equations mean?
7. Which part is actually novel?
8. How does the code implement the paper?
9. What happens during training/inference?
10. What experiment proves the method works?
11. What are the limitations?
12. Where would I modify the code to test my own idea?
```

If the learner cannot answer these questions, continue teaching the missing concept instead of immediately moving to lower-level details.

## 43. Default Behavior for the User's First Paper

When the user gives a paper for the first time, do NOT immediately produce a huge technical explanation.

Start with:

```text
1. What the paper is trying to do
2. One simple mental model
3. The overall architecture
4. The 3–5 concepts needed to understand it
5. The first code/file to inspect
```

Then progressively deepen the analysis.

If code is available, instruct the learner:

```text
Do not read the repository from the first line.

1. Find the entry point.
2. Find where the model is created.
3. Find forward/inference.
4. Find the proposed component.
5. Trace input/output.
6. Then read the important implementation.
```

The learner should understand the system before memorizing code.

## 44. Ultimate Principle

```text
Do not teach the learner how to read code.

Teach the learner how to understand the system,
then use the code as evidence of how the system works.
```

The complete research-paper understanding loop is:

```text
Research Question
       ↓
Hypothesis / Idea
       ↓
Method
       ↓
Mathematics
       ↓
Architecture
       ↓
Algorithm
       ↓
Implementation
       ↓
Experiment
       ↓
Evidence
       ↓
Limitations
       ↓
New Research Question
```
