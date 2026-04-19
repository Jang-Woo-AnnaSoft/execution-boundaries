# execution-boundaries
## "Natural language is how we express intent. This JSON is how intent is validated."


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

### So instead of asking what AI *can* do,  
### we need to define whether an action *should be allowed* before it runs.

## What this is

This repository proposes a minimal structure that determines whether an action is allowed before execution.

Instead of focusing on what AI **can** do,  
it defines what an action **means**, **when it is allowed**,  
and under **what conditions it must not run**.

## What this produces

This defines whether an action is allowed before execution.

```json
{
  "Label": "Cook Jjapagetti",
  "ExecutionEffect": {
    "Type": "Boil",
    "Target": "Stove"
  },
  "Boundaries": [
    { "Type": "NotStartIf", "Value": "no_water" },
    { "Type": "limit", "Value": "max-cook-5min" },
    { "Type": "warning", "Value": "fire-risk" }
  ],
  "Context": "SundayCooking",
  "EventTrigger": [
    { "Observation": "water_ready", "Expected": true },
    { "Observation": "stove_available", "Expected": true }
  ],
  "ResponsibilityLimit": {
    "MaxDurationSec": 300
  },
  "StartImpactConstraint": [
    {
      "Type": "NoConcurrentHeatSource",
      "Targets": ["Oven", "AirFryer"]
    }
  ]
}
```

You can cook Jjapagetti.

But it must not start if there is no water,  
it must not run for too long,  
it must consider fire risk,  
and it must not start if another heat source is already active.

This is the missing layer between intent and execution.

**You can describe device behavior in JSON — not code.**  
**This lets you define safe actions without rewriting firmware.**

---
    
We keep trying to make AI smarter.
But maybe that’s not the problem.

The real issue is what happens before action.

**Manufacturers** predefine the **meaning** of actions and **safety rules**.  
**AI** checks them **before** taking any action.  
**Users** set what is **allowed**.

**AI is not deciding. It’s following predefined rules.**

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

### Example: Rejected Execution

User: "Turn on the heater"

System: ❌ Execution Rejected

Reason:  
• This device may generate high heat.  
• Remote operation is restricted by the manufacturer.  
• The user's presence cannot be verified.

Suggestion:  
• Please confirm the situation locally before operating the device.

### Example: Clarification Required

User: "Open the door"

System: ⚠️ Clarification Required

Multiple doors are available (front door, bedroom door).  
Opening the wrong door may have security implications.  
Please specify which door you want to open.

---

## 4. Why This Is Important

When AI interacts with physical systems, lack of context directly leads to safety risks.

- ❌ Past: Was the execution correct?
- ✅ Present: Should the execution have happened at all?

### What This Actually Means

This is not just an IoT problem.

This applies to any system that can act in the physical world:  
• AI Agents  
• Robotics  
• Smart Home  
• Autonomous Systems  

 **Any system that can take action must be able to decide whether that action should be allowed.**
 
---

## 5. Who This Is For

- **End Users**: Understand why a device acted (or refused to act) and build trust in AI systems.
- **Developers**: Move beyond simple ON/OFF abstractions and define actions with intent and constraints.
- **Platforms & AI Safety Systems**: Introduce a veto layer that prevents unsafe execution and clarifies responsibility.

---

## 6. How This Can Be Implemented

**This approach does not require new standards.**

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

This work is part of a broader exploration of how AI should interact with the physical world.

> A highly capable new employee (LLM) joins the team.  
> They performed well elsewhere.  
> But the physical world is different.  
> Letting them act freely is risky.  
> So we give them a manual.

## 🧠 Core Principles (Human-Readable Form)

- **Know yourself**  
- **Ask if unsure**  
- **Stay in your lane**  
- **It’s by design**

---

## 📘 Mapping to the System

### 1. Core Concepts

**[Making the Physical World Callable for AI](https://discuss.huggingface.co/t/making-the-physical-world-callable-for-ai/172627)** → *Know yourself*  
→ What is the action?  
→ How is it defined?

**[The 9-Question Protocol for Responsible AI Actions](https://discuss.huggingface.co/t/the-9-question-protocol-for-responsible-ai-actions/173045)** → *Ask if unsure*  
→ When is execution allowed?  
→ Who approves it?

---

### 2. Supporting Model

**[Intent–State–Effect: A Minimal Interaction Model](https://discuss.huggingface.co/t/ise-intent-state-effect-model-isolating-judgment-for-cost-optimization-and-explainable-safety/172853)** → *Stay in your lane*  
→ Minimize unnecessary execution  
→ Keep actions bounded

---

### 3. Extended Perspective

**[Interpretive Framework for AI Safety](https://discuss.huggingface.co/t/stop-turning-buttons-into-switches/173264)** → *It’s by design*  
→ Responsibility and accountability  
→ Why these constraints exist

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



> ### AI should not act because it can.  
> ### It should act only when it understands.

