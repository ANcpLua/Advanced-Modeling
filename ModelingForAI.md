# SOFTWARE MODELING KNOWLEDGE BASE

## AI-Optimized Semantic Model v1.1

```yaml
metadata:
  ontology_version: 1.1
  domain: Software Modeling
  purpose: Machine-readable knowledge base for AI systems
  encoding: Semantic markup with explicit relationships
  last_updated: 2025-11-19
  focus: Code Generation, Model-Based Testing, Architecture Validation
```

---

## ENTITY_TYPES

```yaml
entity_types:
  - MODELING_METHOD: Process or workflow for creating models
  - DIAGRAM_TYPE: Category of visual model
  - NOTATION_ELEMENT: Symbol or shape with defined meaning
  - METAMODEL: Rules defining valid models
  - GENERATION_TARGET: Artifact generable from model (Code, Test, Doc)
  - VALIDATION_RULE: Automated check for quality
  - QUALITY_CRITERION: Evaluation standard
```

---

## MODELING_METHODS

### METHOD[id=STRUCTURE_DRIVEN]

```yaml
type: MODELING_METHOD
name: Structure-Driven Design
steps:
  1: Define System Boundary (Context Diagram)
  2: Define Domain Entities (Class Diagram)
  3: Define Component Interfaces (Component Diagram)
  4: Validate with Scenarios (Sequence Diagram)
validation_rule: >
  FOR_EACH message IN Sequence_Diagram:
    ASSERT connection_exists_in(Class_Diagram, message.sender, message.receiver)
```

### METHOD[id=BEHAVIOR_DRIVEN]

```yaml
type: MODELING_METHOD
name: Behavior-Driven Design (BDD)
steps:
  1: Capture User Intent (Use Case Diagram)
  2: Define Workflows (Activity Diagram)
  3: derive System Requirements (Component/Class Diagram)
validation_rule: >
  FOR_EACH activity IN Activity_Diagram:
    ASSERT component_exists_to_perform(activity)
```

---

## GENERATION_TARGETS (AI-Specific)

### TARGET[id=MODEL_BASED_TESTING]

```yaml
type: GENERATION_TARGET
source: STATE_MACHINE_DIAGRAM
output: Test Suite (JUnit/NUnit)
strategy: Path Coverage
algorithm: |
  graph = build_graph(state_machine)
  paths = find_all_paths(start_node, end_node)
  
  FOR path IN paths:
    test_case = create_test()
    current_state = start_node
    
    FOR transition IN path:
      test_case.add_step(
        action: transition.trigger,
        assert: transition.target_state
      )
    
    suite.add(test_case)
```

### TARGET[id=INTEGRATION_TESTS]

```yaml
type: GENERATION_TARGET
source: SEQUENCE_DIAGRAM
output: Integration Test Mocks
algorithm: |
  participants = get_participants(sequence_diagram)
  messages = get_messages(sequence_diagram)
  
  FOR message IN messages:
    IF message.receiver IS_EXTERNAL_SYSTEM:
      generate_mock(message.receiver)
      expect_call(message.receiver, message.name, message.params)
      return_value(message.return_type)
```

### TARGET[id=ARCHITECTURE_DOCUMENTATION]

```yaml
type: GENERATION_TARGET
source: HYBRID_MODEL (C4 + UML)
output: Markdown Documentation (arc42)
mapping:
  Context_Diagram: "arc42 Section 3: Context and Scope"
  Component_Diagram: "arc42 Section 5: Building Block View"
  Sequence_Diagram: "arc42 Section 6: Runtime View"
  Deployment_Diagram: "arc42 Section 7: Deployment View"
```

---

## DIAGRAM_TYPES_ONTOLOGY

### DIAGRAM_TYPE[id=C4_CONTEXT]

```yaml
type: DIAGRAM_TYPE
name: C4 System Context Diagram
purpose: High-level scope and external dependencies
elements:
  - Person (User)
  - Software System (The Project)
  - External System (Dependency)
relationships:
  - Uses
  - Delivers
quality_checks:
  - "CHECK: Focus is on people and systems, not technologies"
  - "CHECK: Description provided for every element"
```

### DIAGRAM_TYPE[id=C4_CONTAINER]

```yaml
type: DIAGRAM_TYPE
name: C4 Container Diagram
purpose: High-level technical architecture (Deployable units)
elements:
  - Container (Web App, Mobile App, Database, API)
  - Boundary (System Boundary)
relationships:
  - HTTPS/JSON
  - SQL/TCP
quality_checks:
  - "CHECK: Technology choices listed (e.g., 'Java/Spring', 'React')"
  - "CHECK: Data flow direction explicit"
```

---

## QUALITY_CRITERIA (Formal)

### CRITERION[id=SYNTACTIC_CORRECTNESS]

```yaml
type: QUALITY_CRITERION
definition: Adherence to metamodel grammar
checks:
  - "No loose ends in flows"
  - "Unique IDs for elements"
  - "Valid relationship types for element pairs"
```

### CRITERION[id=SEMANTIC_CONSISTENCY]

```yaml
type: QUALITY_CRITERION
definition: Logical soundness across views
checks:
  - "Structure-Behavior Bridge: Messages match Links"
  - "State Machine Completeness: All states reachable"
  - "Interface Compliance: Components implement provided interfaces"
```

---

## END_OF_KNOWLEDGE_BASE
