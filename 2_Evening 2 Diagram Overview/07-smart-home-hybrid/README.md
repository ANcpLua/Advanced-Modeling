# Exercise 5: Hybrid Diagram

## Instructions

Create a communication diagram (structure + behavior) for a simple interaction.

**Scenario:** Smart Home - "Turn On Living Room Lights"

**Hybrid Aspect:** We combine the structural view (links between objects) with behavior (numbered messages) and add a
"Frequency Heatmap" annotation to indicate traffic load on specific links.

---

## Solution

### Communication Diagram with Heatmap (PlantUML)

![Smart Home Communication Diagram](smart-home-communication.svg)

**Source**: [smart-home-communication.puml](smart-home-communication.puml)

**Explanation:**

* **Structure:** Shows that the Bulb does not talk to Alexa directly; it goes through the Hub and Cloud.
* **Behavior:** The numbered messages (1-9) show the sequence of execution.
* **Hybrid Info:** The notes indicate the "Heatmap" or load on the connections, which is useful for identifying
  bottlenecks (e.g., the Cloud connection is critical).
