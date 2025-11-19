# Applied Practice: ATM Context Diagram

## Instructions

Create a context diagram for an ATM system. Identify all external entities and data flows.

---

## Solution

### Context Diagram (Mermaid)

```mermaid
flowchart TD
    %% System
    System(ATM System)

    %% External Entities
    Customer((Customer))
    BankSystem[Bank Backend System]
    ServiceTech((Service Technician))
    SecuritySystem[Security/Alarm System]

    %% Data Flows - Customer
    Customer -- "Insert Card<br/>Enter PIN, Amount" --> System
    System -- "Cash, Receipt<br/>Screen Prompts" --> Customer

    %% Data Flows - Bank Backend
    System -- "Transaction Request<br/>PIN Verification" --> BankSystem
    BankSystem -- "Authorization<br/>Account Balance" --> System

    %% Data Flows - Service Tech
    ServiceTech -- "Maintenance Key<br/>Diagnostics Request" --> System
    System -- "Error Logs<br/>Cash Level Status" --> ServiceTech

    %% Data Flows - Security
    System -- "Tamper Alert<br/>Camera Feed" --> SecuritySystem

    style System fill:#4A90E2,stroke:#2E5C8A,stroke-width:3px,color:#fff
    style Customer fill:#28a745,stroke:#1e7e34,stroke-width:2px,color:#fff
    style BankSystem fill:#ffc107,stroke:#d39e00,stroke-width:2px,color:#000
    style ServiceTech fill:#28a745,stroke:#1e7e34,stroke-width:2px,color:#fff
    style SecuritySystem fill:#ffc107,stroke:#d39e00,stroke-width:2px,color:#000
```

**Analysis:**

* **System:** The ATM itself.
* **Actors:** Customer, Bank Backend (External System), Service Technician, Security System.
* **Flows:** Financial transaction data, authentication data, physical items (cash/card), and operational status data.
