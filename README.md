# execution-boundaries


![Design Notes](https://img.shields.io/badge/design-notes-lightgrey)
![Status: Exploratory](https://img.shields.io/badge/status-exploratory-blue)
![Focus: Execution Boundaries](https://img.shields.io/badge/focus-execution--boundaries-black)

> We are not criticizing or attacking Matter or existing platforms.  
> We raise this issue from the perspective of helping them evolve faster and become safer.

---

**Defining not just what AI can do, but what it may and should do.**

AI is no longer confined to screens. It is beginning to act in the physical world—turning on devices, controlling systems, and triggering real-world effects. But there is a critical problem.

**AI knows how to execute actions, but it does not know whether those actions should be executed in a given context.**

---

## 1. The Problem Is Not Control — It’s Missing Semantics

The same `Switch → ON` command can produce completely different outcomes depending on the device:

- Baby mobile → music and rotation (safe)
- Electric heater → heat generation and fire risk (potentially dangerous)

Most smart home standards, such as Matter, treat both as the same type of "switch." The system lacks **semantics**.

We must move beyond asking:
> "Can this action be executed?"

and start asking:
> **"Should this action be executed now?"**

---

## 2. Paradigm Shift: From Capability to Permission

We introduce a semantic layer between AI and the physical world that fundamentally changes how execution works.

| Aspect | Device-Centric (Traditional) | Action-Centric (Proposed) |
|--------|-----------------------------|---------------------------|
| Perspective | Can it execute? | Is it allowed? |
| Model | Device-based (Switch, Light) | Action-based (Heating, Rotation) |
| Logic | Execute when condition is true | Reject when constraints are violated |
| Result | Execution is default | Execution is validated |

---

## 3. Core Mechanism: Execution Validation + Boundaries

Actions are not treated as commands, but as **objects that must pass validation before execution**.

- **Intent**: What is the goal of the action?
- **Effect**: What physical change does it cause?
- **Boundaries**: What limits must never be exceeded?
- **Conditions**: Under what context is it allowed?

**Execution Flow:**
```
AI Command
→ Execution Validation (Intent / Effect / Conditions / Boundaries)
→ Approved → Execute
→ Rejected → Explain why
```

**Principle:** If any condition or boundary is violated, the system must reject the action and provide a clear reason.

---

## 4. Why This Is Important

When AI interacts with physical systems, lack of context directly leads to safety risks.

- ❌ Past: Was the execution correct?
- ✅ Present: Should the execution have happened at all?

---

## 5. Who This Is For

- **End Users**: Understand why a device acted (or refused to act) and build trust in AI systems.
- **Developers**: Move beyond simple ON/OFF abstractions and define actions with intent and constraints.
- **Platforms & AI Safety Systems**: Introduce a veto layer that prevents unsafe execution and clarifies responsibility.

---

## 6. Core Principles

1. Validate before execution (Validate → Execute, not Execute → Fix)
2. Shift from device-centric to action-centric modeling
3. Treat boundaries as first-class elements of action definition
4. Enable systems to reject actions, not just execute them

---

## 🔗 Related Discussions (Hugging Face)

This work is part of a broader exploration of how AI should interact with the physical world:

### Core Concepts
- [**Making the Physical World Callable for AI**](https://discuss.huggingface.co/t/making-the-physical-world-callable-for-ai/172627)     
  Defines how physical actions are represented between devices and platforms so that AI can interpret them meaningfully.

- [**The 9-Question Protocol for Responsible AI Actions**](https://discuss.huggingface.co/t/ise-intent-state-effect-model-isolating-judgment-for-cost-optimization-and-explainable-safety/172853)      
  Defines how actions are validated, including who is responsible for approval and under what conditions execution is allowed.

### Supporting Model
- [**Intent–State–Effect: A Minimal Interaction Model**](https://discuss.huggingface.co/t/the-9-question-protocol-for-responsible-ai-actions/173045)      
  Provides a simplified structure for modeling actions, focusing on efficiency and reducing unnecessary execution cost.

### Extended Perspective
- [**An Interpretive Framework for AI Safety**](https://discuss.huggingface.co/t/stop-turning-buttons-into-switches/173264)      
  Explores responsibility, legal interpretation, and accountability across users, manufacturers, and platforms.

---

## 📦 Implementation

A working implementation of this concept is available here:

👉 https://github.com/anna-soft/Nemo-Anna

## 🌐 Project Overview

👉 https://anna.software

This project defines **what actions are allowed, when they are allowed, and how they should behave**.

With just **9 structured questions**, a complete device behavior can be defined.

This is not a concept.  
**It is already implemented.**

Scan a QR code on a Matter-enabled platform, and the device works immediately.

