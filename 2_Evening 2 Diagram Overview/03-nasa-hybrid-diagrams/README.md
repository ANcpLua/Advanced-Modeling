# Class Group Exercise: Hybrid Diagrams @NASA

## Instructions

In real world projects very often elements from different diagram types are mixed. What diagram types were mixed in the
diagram below?

*(See `slides/` for the reference image)*

---

## Solution Analysis

Based on the NASA Systems Engineering Handbook example (Figure 5.3-2):

**1. Mixed Diagram Types:**

The diagram mixes:

* **Data Flow Diagram (DFD):** It shows the flow of data (arrows) between processes (ovals like "Planning",
  "Analysis").
* **Deployment / Block Diagram:** It divides the system into physical/logical partitions ("Ground System",
  "Flight System") using vertical swimlanes or boundaries.
* **Activity Diagram:** The flow of "Uplink Process" vs "Downlink Process" resembles a workflow.

**2. Why this is "Hybrid":**

Strict UML would separate the *location* (Deployment Diagram) from the *process flow* (Activity Diagram). This diagram
combines them to show **"Who does what and where"** in a single view. This is highly effective for systems engineering
where the physical location of a process (Earth vs. Space) is a critical constraint (latency, bandwidth).

**3. Key Elements:**

* **Swimlanes/Partitions:** External Systems | Ground System | Flight System | External Stimuli
* **Processes (Ovals):** Command Generation, Software Loads, Spacecraft Execution.
* **Flows (Arrows):** Data moving between processes.
