# execution-boundaries


![Design Notes](https://img.shields.io/badge/design-notes-lightgrey)
![Status: Exploratory](https://img.shields.io/badge/status-exploratory-blue)
![Focus: Execution Boundaries](https://img.shields.io/badge/focus-execution--boundaries-black)

> We are not criticizing or attacking Matter or existing platforms.  
> We raise this issue from the perspective of helping them evolve faster and become safer.

---

AI has moved beyond mere words; it is now opening your front door and operating your machinery.

But there is a fatal flaw.

AI does not even know what the device actually is, nor what will happen when it presses a button.

> You are currently entrusting your family’s safety to a blind pilot—one who doesn’t know what he’s touching or what the consequences of his actions will be.

> **Are you truly okay with this?**

---

## 1. The Problem — It's acting without understanding.

The same Switch → ON command can lead to completely different results.

- Baby Mobile → Music and spinning (**Safe**)

- Space Heater → High heat and fire hazard (**Dangerous**)

Most smart home standards, like Matter, treat both as just a "Switch." **The system cannot tell them apart**.

## Unprepared Execution
The AI ​​always answers "Yes" to the question, "Can you do this?"  
This can lead to disasters such as the following:

- You asked it to spray air freshener, but the AI ​​turns on an electric heater covered in clothes.
- You tried to open the inner bedroom door, but the AI ​​opened the front door, allowing a stranger to enter.
- You asked it to water the yard, but the AI ​​fully opened the water valve in the laundry room, flooding the entire house.


We must move beyond simply asking:
"Can you do this task?"

And start asking:
**"Is this action ready to be executed?"**

---

### Traditional IoT systems rely on device types.

• This does not scale.  
• Every new device requires a new type.

So systems simplify everything into generic categories like “Switch.”  
**And from that moment, AI no longer knows what it is controlling.**

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

## 6. How This Can Be Implemented

This approach does not require new standards.

It can be implemented using existing fields such as:
• UserLabel  
• FixedLabel  

to encode:
• Intent (what this action means)  
• Safety (what must be protected)  
• Boundary (what must never be crossed)

**This allows systems to carry meaning without breaking existing architectures.**

---

## 🔗 Related Discussions (Hugging Face)

This work is part of a broader exploration of how AI should interact with the physical world:

### Core Concepts
- [**Making the Physical World Callable for AI**](https://discuss.huggingface.co/t/making-the-physical-world-callable-for-ai/172627)     
  Defines how physical actions are represented between devices and platforms so that AI can interpret them meaningfully.

- [**The 9-Question Protocol for Responsible AI Actions**](https://discuss.huggingface.co/t/the-9-question-protocol-for-responsible-ai-actions/173045)      
  Defines how actions are validated, including who is responsible for approval and under what conditions execution is allowed.

### Supporting Model
- [**Intent–State–Effect: A Minimal Interaction Model**](https://discuss.huggingface.co/t/ise-intent-state-effect-model-isolating-judgment-for-cost-optimization-and-explainable-safety/172853)      
  Provides a simplified structure for modeling actions, focusing on efficiency and reducing unnecessary execution cost.

### Extended Perspective
- [**An Interpretive Framework for AI Safety**](https://discuss.huggingface.co/t/stop-turning-buttons-into-switches/173264)      
  Explores responsibility, legal interpretation, and accountability across users, manufacturers, and platforms.

---

## 📦 Implementation

How physical actions are represented and handled between devices and platforms can be found in the repository below.

👉 https://github.com/anna-soft/Nemo-Anna

The approval process and permission model are defined in the [**The 9-Question Protocol for Responsible AI Actions**](https://discuss.huggingface.co/t/the-9-question-protocol-for-responsible-ai-actions/173045) document, where they are proposed as a JSON schema.

The adoption and final form of this schema should be determined through collaboration between regulators, users, and platforms.

## 🌐 Project Overview

👉 https://anna.software

This project defines **what actions are allowed, when they are allowed, and how they should behave**.

With just **9 structured questions**, a complete device behavior can be defined.

This is not a concept.  
**It is already implemented.**

AI does not need to guess anymore.

Scan a QR code on a Matter-enabled platform, and the device works immediately.

