# Exercise: Insurance Policy Lifecycle

## Instructions

Model the lifecycle of an "Insurance Policy" based on the real-world example shown in class.

**Key Concept:**
This example demonstrates **A-States (Application/Business States)**. The transitions are triggered by high-level
Use Cases (e.g., "Create Application", "Accept Option"), ensuring consistency between the Use Case Model and the
State Machine.

**States to Model:**

* **In Progress:** Application created, data being entered.
* **Calculated:** Risk/Premium calculated, options available.
* **Change Option Pending:** Waiting for user to select a new option.
* **Active:** Policy is live and valid.
* **Canceled:** Policy terminated.
* **Rejected:** Application denied.

---

## Solution

### Insurance Policy State Machine

```mermaid
stateDiagram-v2
    [*] --> InProgress: Create Application

    InProgress --> Canceled: Cancel Policy
    InProgress --> Calculated: Calculate Policy
    InProgress --> Rejected: Reject Policy

    Calculated --> InProgress: Any Use Case<br/>changing policy
    Calculated --> Canceled: Cancel Policy
    Calculated --> Active: Release Policy
    Calculated --> ChangeOption: Offer Option

    ChangeOption --> Calculated: Accept Option
    ChangeOption --> Rejected: Reject Option (Implicit)

    Active --> Canceled: Expiry / Cancel

    Canceled --> InProgress: Reset Policy

    Rejected --> [*]
    Canceled --> [*]

    note right of InProgress
        Application created,
        data being entered
    end note

    note right of Calculated
        Risk/Premium calculated,
        options available
    end note

    note right of Active
        Policy is live
        and valid
    end note

    note left of Canceled
        TERMINAL STATE
        (with recovery option)
        Can loop back to InProgress
        via "Reset Policy"
    end note

    note right of Rejected
        TERMINAL STATE
        (permanent)
        No recovery path,
        policy permanently denied
    end note
```

**PlantUML Source**: [insurance-policy-state.puml](insurance-policy-state.puml)
