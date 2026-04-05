# execution-boundaries


![Design Notes](https://img.shields.io/badge/design-notes-lightgrey)
![Status: Exploratory](https://img.shields.io/badge/status-exploratory-blue)
![Focus: Execution Boundaries](https://img.shields.io/badge/focus-execution--boundaries-black)

> We are not criticizing or attacking Matter or existing platforms.  
> We raise this issue from the perspective of helping them evolve faster and become safer.

---

## 1. The Problem: The Gap Between Execution and Awareness

The system is not wrongly designed.  
**The situation is changing.**

We are no longer controlling systems purely through human commands.  
**AI-driven control based on inference has already begun.**

---

We believe modern IoT systems are “under control.”  
But reality is different.

### Same Treatment

A baby mobile, a desk lamp, a high-heat space heater…  
From the system’s perspective, they are all just **“endpoints.”**

---

### Lack of Judgment

The system executes actions.  
But it cannot answer:

> **“Should this action be executed in this situation?”**

There is no layer that can answer this question.

---

The problem is not incorrect execution.

> **The real problem is that the action itself  
should not have happened in the first place.**

---

## 2. Our Proposal: Beyond Device-Type, Towards Execution Context

We are not adding another feature.  
We are redesigning how execution itself is defined.

---

### Limitations of Device-Type Based Systems

Current IoT systems rely on **Device-Type**.

This approach has two fundamental limitations:

- **Lack of scalability**  
  Adding new device types for every variation is not sustainable  

- **Lack of context**  
  A “switch” does not carry meaning —  
  the system cannot distinguish between a light and a heater  

---

### A New Approach: Context-Based Labeling

Instead of introducing new device types,  
we propose embedding AI-interpretable context into existing labels:

- **Intent**  
- **Safety**  
- **Boundary**  

using **UserLabel / FixedLabel**.

---

### Core Philosophy: Capability vs. Permission

Knowing **what AI can do (Capability)** is a technical problem.

But,

> **Knowing what AI is allowed to do (Permission & Safety)**

is a design problem.

---

## 3. Core Frameworks

This project introduces four frameworks to address this gap.

---

### ① Making the Physical World Callable for AI

Redefine physical actions beyond ON/OFF signals by including:

- Intent  
- Context  
- Condition  

**Goal**  
→ AI understands what it is interacting with, not just triggering signals

---

### ② Intent–State–Effect: A Minimal Interaction Model

Structure actions into:

- Intent  
- State  
- Effect  

**Goal**

- Reduce unnecessary execution  
- Enable state-aware decision making  
- Lower system complexity  

> **Less cost, more accurate execution**

---

### ③ The 9-Question Protocol for Responsible AI Actions

A practical, immediately applicable **technical method (JSON Schema)**.

Every action must be validated before it can exist:

- What is the intent?  
- What is the effect?  
- When is it allowed to execute?  
- What boundaries must never be crossed?  
- What are the physical impacts (start/stop)?  

**Result**

> From systems that execute blindly  
> → to systems where undefined actions cannot exist

---

### ④ An Interpretive Framework for AI Safety

When abstraction diverges from physical reality,  
the issue becomes **responsibility**, not technology.

**Problems**

- Mismatch between user expectation and actual behavior  
- Conflicts between manufacturers and platforms  
- Undefined responsibility in case of incidents  

**Goal**

> Provide a legal and ethical interpretation framework for AI execution

---

## 4. Concrete Implementation

👉 https://github.com/anna-soft/Nemo-Anna

This repository provides:

- Structural design  
- JSON-based definition model  
- Execution validation framework  

---

## 🔗 Related Discussions (Hugging Face)

This is not just a proposal.  
It is part of an ongoing discussion on how AI should interact with the physical world.

- [Making the Physical World Callable for AI](https://discuss.huggingface.co/t/making-the-physical-world-callable-for-ai/172627)
- [Intent–State–Effect: A Minimal Interaction Model](https://discuss.huggingface.co/t/ise-intent-state-effect-model-isolating-judgment-for-cost-optimization-and-explainable-safety/172853)
- [The 9-Question Protocol for Responsible AI Actions](https://discuss.huggingface.co/t/the-9-question-protocol-for-responsible-ai-actions/173045)
- [An Interpretive Framework for AI Safety](https://discuss.huggingface.co/t/stop-turning-buttons-into-switches/173264)

## 🔑 Core Idea

> **Execution is not a right.  
> It is a permission.**

## 🌐 Project overview:
https://anna.software
