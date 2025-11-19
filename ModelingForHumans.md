# The Advanced Modeling Field Guide

> **For Humans:** A practical companion to the Advanced Modeling course.

## 1. Introduction: Grammar vs. Method

Most modeling courses teach **Grammar**: "This is a class," "This is an arrow," "This is a stick figure."
This course teaches **Method**:

* **When** to use which diagram?
* **In what order** should diagrams be created?
* **How** do they relate to each other?
* **Why** are we modeling this specific aspect?

### The Golden Rule

> "A model is a visual, abstract, and formal representation of a system."

If your model doesn't communicate, validate, or automate, it's just a drawing.

---

## 2. Competency: Structure Modeling (Static)

*Modeling the parts that persist, independent of time.*

### Key Diagrams

1. **Context Diagram:** The absolute first step. Defines the "System Boundary". Who is outside? What crosses the border?
2. **Class Diagram:** The backbone of code generation. Defines data, logic containers, and relationships.
3. **Component Diagram:** The "Lego blocks" of your system. Defines interfaces and dependencies.
4. **C4 Model (Container/Component):** (See Section 4)

### Best Practice: "The Map is Not the Territory"

Don't model every single class. Model the *architecturally significant* ones.

* **Bad:** Modeling 50 DTOs that are just getters/setters.
* **Good:** Modeling the complex relationship between `OrderStrategy`, `DiscountCalculator`, and `PaymentProvider`.

---

## 3. Competency: Behavior Modeling (Dynamic)

*Modeling how things change over time.*

### Key Diagrams

1. **Sequence Diagram:** The "Debugger" view. Shows method calls and message passing. Critical for distributed systems.
2. **Activity Diagram:** The "Flowchart" view. Shows algorithms, business processes, and parallel processing.
3. **State Machine:** The "Lifecycle" view. Shows valid states and transitions. Critical for business entities.

### The "T-Shape" of State Machines

* **A-States (Application):** Business logic states (e.g., Order Placed, Paid, Shipped). Technology agnostic.
* **T-States (Technical):** Infrastructure states (e.g., Connection Open, Retry, Timeout, Buffer Full).

---

## 4. Alternative Methods: The C4 Model

*Recommended for Software Architecture Documentation.*

The **C4 model** (by Simon Brown) is an abstraction-first approach to architecture, avoiding the complexity of UML.

### The 4 Levels

1. **Context:** System + Users + External Systems. (Equivalent to UML Context Diagram).
2. **Containers:** Applications, Data Stores, Microservices. (e.g., "Mobile App", "API Application", "Oracle DB").
3. **Components:** Structural building blocks within a container. (e.g., "Sign In Controller", "Security Component").
4. **Code:** UML class diagrams (details).

### Why use C4?

* **Audience-Centric:** Context is for non-tech stakeholders. Containers for ops/devs. Components for developers.
* **Zoom-In Approach:** Allows you to start simple and drill down only where necessary.

---

## 5. Modeling Methods & Process

*The "Secret Sauce" of this course.*

### The "Structure-First" Method

1. **Context:** Define scope.
2. **Structure:** Define the nouns (Classes/Components).
3. **Behavior:** Validate the structure by running scenarios (Use Cases) through it using Sequence Diagrams.
    * *Check:* If Object A calls Object B in the Sequence Diagram, is there a relationship in the Class Diagram?

### The "Behavior-First" Method (BDD style)

1. **Use Cases:** Define what users want.
2. **Behavior:** Draw the flow (Activity/Sequence) to realize the use case.
3. **Structure:** Derive the necessary classes/components to support that flow.

### Integration with Code & Testing

* **Model-Based Testing (MBT):**
  * Use **State Machines** to generate test paths (cover all transitions).
  * Use **Sequence Diagrams** to generate integration test assertions.
* **Code Generation:**
  * **Class Diagrams** -> Database Schema (SQL) + Class Skeletons (Java/C#).
  * **State Machines** -> State Pattern implementation.

---

## 6. Quality Assessment

*How do you know if a model is good?*

### The Checklist

1. **Syntactic Quality:** Does it follow the rules? (e.g., No arrows connecting two actors in a Use Case diagram).
2. **Semantic Quality:** Does it mean the right thing? (e.g., Does the "Ship" action result in the "Shipped" state?).
3. **Pragmatic Quality:** Is it useful?
    * **Abstraction Level:** Is it too detailed for the manager? Too vague for the dev?
    * **Aesthetics:** Is the layout readable? (Minimal crossing lines).
    * **Purpose:** Does it answer a specific question?

### Anti-Patterns to Avoid

* **Spiderweb:** Too many relationships. High coupling.
* **God Class:** One class connected to everything.
* **Black Hole:** A state/activity you can enter but never leave.
* **Miracle:** A state/activity you can leave but never enter.

---

## 7. Exercises & Applied Practice

*Put theory into practice with these hands-on scenarios.*

### Evening 1: Foundations

* **[Kloc Digital Watch](1_Evening%201%20The%20Importance%20of%20Modeling/00-applied-practice-scenarios/01-kloc-digital-watch/)**:
  Find errors in a spec using State Machines.
* **[Logistics Robotics](1_Evening%201%20The%20Importance%20of%20Modeling/00-applied-practice-scenarios/02-logistics-robotics-quality-check/)**:
  Automated graph analysis for deadlocks.

### Evening 2: Diagram Overview

* **[Visual Explanation](2_Evening%202%20Diagram%20Overview/01-home-exercise-explaining-visually/)**:
  Communicate a complex system without text.
* **[Sliding Door](2_Evening%202%20Diagram%20Overview/02-class-practice-sliding-door/)**:
  Model a safety-critical controller.
* **[NASA Hybrid](2_Evening%202%20Diagram%20Overview/03-nasa-hybrid-diagrams/)**:
  Analyze a complex real-world engineering diagram.
* **[ATM Context](2_Evening%202%20Diagram%20Overview/00-applied-practice-scenarios/02-atm-context-diagram/)**:
  Define system boundaries (DFD Level 0).
* **[Insurance Policy](2_Evening%202%20Diagram%20Overview/00-applied-practice-scenarios/03-insurance-policy-lifecycle/)**:
  Model business object states (A-States).
* **[AI Generation Prep](2_Evening%202%20Diagram%20Overview/00-applied-practice-scenarios/04-ai-generation-prep/)**:
  Create a rigorous model for code generation.
* **[Smart Home Hybrid](2_Evening%202%20Diagram%20Overview/00-applied-practice-scenarios/05-smart-home-hybrid/)**:
  Combine structure and behavior.
* **[Class Diagram Check](2_Evening%202%20Diagram%20Overview/00-applied-practice-scenarios/06-class-diagram-self-check/)**:
  Test your knowledge of UML syntax.
