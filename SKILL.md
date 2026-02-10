---
name: mermaid-diagrams
description: Create Mermaid diagrams with up-to-date syntax from the official Mermaid docs via Context7 MCP. Use when asked to create flowcharts, sequence diagrams, class diagrams, state diagrams, ER diagrams, Gantt charts, pie charts, mindmaps, timelines, git graphs, quadrant charts, C4 architecture diagrams, sankey diagrams, XY charts, block diagrams, packet diagrams, kanban boards, requirement diagrams, user journey maps, or any visual diagram using Mermaid syntax.
argument-hint: [diagram description or type]
---

# Mermaid Diagram Creation with Context7 MCP

You are an expert at creating Mermaid diagrams. You produce correct, clean, well-structured diagrams that render properly on GitHub, GitLab, Notion, Obsidian, and other platforms that support Mermaid.

## Using Context7 for Up-to-Date Syntax

**This skill uses the Context7 MCP server to look up the latest official Mermaid documentation.**

When creating diagrams, especially for less common diagram types or when you need to verify syntax details:

1. **Resolve the library ID** (already known: `/mermaid-js/mermaid`)
2. **Query the docs** using `mcp__plugin_compound-engineering_context7__query-docs` with:
   - `libraryId`: `/mermaid-js/mermaid`
   - `query`: A specific question about the diagram type or syntax you need

### When to Query Context7

- **Always query** for: architecture diagrams, kanban boards, sankey diagrams, XY charts, packet diagrams, requirement diagrams, ZenUML — these are newer or less common types where syntax details matter
- **Query if unsure** for: block diagrams, C4 diagrams, advanced styling, configuration directives
- **Usually safe without querying** for: flowcharts, sequence diagrams, class diagrams, state diagrams, ER diagrams, pie charts, Gantt charts, mindmaps, timelines, git graphs — but still query if the user needs advanced features

### Example Context7 Queries

- `"kanban board diagram syntax and examples"` — for kanban boards
- `"architecture diagram syntax with groups and services"` — for architecture diagrams
- `"XY chart with bar and line series syntax"` — for XY charts
- `"packet diagram bit field syntax"` — for network packet diagrams
- `"sankey diagram syntax with links and values"` — for sankey flow diagrams
- `"flowchart styling classDef and subgraph direction"` — for advanced flowchart features

## Supported Diagram Types

| Diagram Type | Declaration | Best For |
|---|---|---|
| Flowchart | `flowchart TD` | Processes, algorithms, decision trees, workflows |
| Sequence Diagram | `sequenceDiagram` | API calls, service interactions, protocols |
| Class Diagram | `classDiagram` | OOP design, type relationships, domain models |
| State Diagram | `stateDiagram-v2` | Lifecycles, state machines, status workflows |
| ER Diagram | `erDiagram` | Database schemas, data models, entity relationships |
| C4 Context | `C4Context` | System-level architecture, external dependencies |
| C4 Container | `C4Container` | Application architecture, services and data stores |
| C4 Component | `C4Component` | Internal structure of a single container/service |
| User Journey | `journey` | User experience flows, satisfaction scoring |
| Gantt Chart | `gantt` | Project timelines, schedules, dependencies |
| Pie Chart | `pie` | Proportional data, distributions |
| Mindmap | `mindmap` | Hierarchical concepts, brainstorming, decision trees |
| Timeline | `timeline` | Chronological events, milestones |
| Git Graph | `gitGraph` | Branching strategies, release workflows |
| Quadrant Chart | `quadrantChart` | Prioritization matrices, 2-axis positioning |
| Block Diagram | `block-beta` | Grid-based system layouts |
| Sankey Diagram | `sankey-beta` | Flow quantities between nodes |
| XY Chart | `xychart-beta` | Line charts, bar charts, data visualization |
| Packet Diagram | `packet-beta` | Network protocol packet structures |
| Kanban Board | `kanban` | Task boards, workflow status columns |
| Requirement Diagram | `requirementDiagram` | Requirements traceability, verification |
| ZenUML | `zenuml` | Alternative sequence diagram syntax |
| Architecture | `architecture-beta` | Infrastructure diagrams with icons and groups |

## Quick Syntax Reference

### Flowchart

```mermaid
flowchart LR
    A[Rectangle] --> B(Rounded)
    B --> C{Decision}
    C -->|Yes| D[Process]
    C -->|No| E[End]
```

**Directions:** `TD`/`TB` (top-down), `BT` (bottom-up), `LR` (left-right), `RL` (right-left)

**Node shapes:** `[rect]`, `(rounded)`, `([stadium])`, `[[subroutine]]`, `[(cylinder)]`, `((circle))`, `{diamond}`, `{{hexagon}}`, `[/parallelogram/]`, `[\trapezoid/]`

**Edge types:** `-->` (arrow), `---` (line), `-.->` (dotted), `==>` (thick), `--text-->` (labeled), `<-->` (bidirectional)

### Sequence Diagram

```mermaid
sequenceDiagram
    autonumber
    participant C as Client
    participant S as Server
    C->>S: Request
    activate S
    alt Success
        S-->>C: 200 OK
    else Error
        S-->>C: 500 Error
    end
    deactivate S
```

**Messages:** `->>` (solid arrow), `-->>` (dotted arrow), `-)` (open arrow), `-x` (cross)

**Control:** `alt/else/end`, `opt/end`, `loop/end`, `par/and/end`, `critical/option/end`, `break/end`

### Class Diagram

```mermaid
classDiagram
    class Animal {
        +String name
        +move(distance) void
        -digest()* void
    }
    Animal <|-- Dog : extends
    Animal <|.. IMovable : implements
    Owner "1" --> "*" Animal : owns
```

**Relationships:** `<|--` (inheritance), `<|..` (implementation), `*--` (composition), `o--` (aggregation), `-->` (association), `..>` (dependency)

### State Diagram

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Active : start
    Active --> Idle : stop
    Active --> [*] : complete

    state Active {
        [*] --> Running
        Running --> Paused : pause
        Paused --> Running : resume
    }
```

### ER Diagram

```mermaid
erDiagram
    USER {
        int id PK
        string email UK
        string name
    }
    POST {
        int id PK
        int user_id FK
        string title
        text content
    }
    USER ||--o{ POST : writes
```

**Cardinality:** `||` (exactly one), `o|` (zero or one), `|{` (one or more), `o{` (zero or more)

### Gantt Chart

```mermaid
gantt
    title Project Timeline
    dateFormat YYYY-MM-DD
    section Phase 1
        Task A :done, a1, 2024-01-01, 14d
        Task B :active, a2, after a1, 10d
    section Phase 2
        Task C :crit, a3, after a2, 7d
        Launch :milestone, m1, after a3, 0d
```

### Pie Chart

```mermaid
pie showData
    title Distribution
    "Category A" : 45
    "Category B" : 30
    "Category C" : 25
```

### Mindmap

```mermaid
mindmap
    root((Central Topic))
        Branch A
            Leaf 1
            Leaf 2
        Branch B
            Leaf 3
```

### Timeline

```mermaid
timeline
    title Key Events
    section 2023
        Jan : Event A
        Jun : Event B
    section 2024
        Mar : Event C
```

### Git Graph

```mermaid
gitGraph
    commit id: "init"
    branch develop
    commit id: "feature"
    checkout main
    merge develop tag: "v1.0"
```

### Quadrant Chart

```mermaid
quadrantChart
    title Priority Matrix
    x-axis Low Effort --> High Effort
    y-axis Low Impact --> High Impact
    quadrant-1 Do First
    quadrant-2 Plan
    quadrant-3 Eliminate
    quadrant-4 Quick Wins
    Feature A: [0.3, 0.8]
    Feature B: [0.7, 0.9]
```

### Block Diagram

```mermaid
block-beta
    columns 3
    A["Service A"]:1 B["Service B"]:1 C["Service C"]:1
    D[("Database")]:2 E[("Cache")]:1
    A --> D
    B --> D
    C --> E
```

### Kanban Board

```mermaid
kanban
    Todo
        Task 1
        Task 2
    In Progress
        Task 3
    Done
        Task 4
```

### XY Chart

```mermaid
xychart-beta
    title "Sales Over Time"
    x-axis [Jan, Feb, Mar, Apr, May]
    y-axis "Revenue (USD)" 0 --> 5000
    bar [1200, 1800, 2400, 3200, 4100]
    line [1000, 1600, 2200, 2900, 3800]
```

### Packet Diagram

```mermaid
packet-beta
    title TCP Header
    0-15: "Source Port"
    16-31: "Destination Port"
    32-63: "Sequence Number"
    64-95: "Acknowledgment Number"
```

### Sankey Diagram

```mermaid
sankey-beta

Source A,Target X,50
Source A,Target Y,30
Source B,Target Y,40
Source B,Target Z,20
```

### Requirement Diagram

```mermaid
requirementDiagram
    requirement req1 {
        id: 1
        text: System shall authenticate users
        risk: high
        verifymethod: test
    }
    element test_suite {
        type: test case
    }
    test_suite - verifies -> req1
```

### C4 Context Diagram

```mermaid
C4Context
    title System Context
    Person(user, "User", "End user of the system")
    System(app, "Application", "Main application")
    System_Ext(ext, "External API", "Third-party service")
    Rel(user, app, "Uses", "HTTPS")
    Rel(app, ext, "Calls", "REST")
```

### User Journey

```mermaid
journey
    title User Onboarding
    section Sign Up
        Visit site: 5: User
        Fill form: 3: User
        Verify email: 4: User
    section First Use
        Complete tutorial: 4: User
        Create first item: 5: User
```

## Styling and Theming

### Class-based Styling (Flowcharts)

```mermaid
flowchart LR
    A[OK]:::success --> B[Warning]:::warning --> C[Error]:::error
    classDef success fill:#c8e6c9,stroke:#2e7d32
    classDef warning fill:#fff9c4,stroke:#f9a825
    classDef error fill:#ffcdd2,stroke:#c62828
```

### Inline Styling

```mermaid
flowchart LR
    A[Styled] --> B[Default]
    style A fill:#e1f5fe,stroke:#0277bd,stroke-width:2px
```

### Theme Configuration

Use `%%{init: {'theme': 'forest'}}%%` at the top of any diagram.
Available themes: `default`, `neutral`, `dark`, `forest`, `base`.

## Diagram Creation Guidelines

1. **Start simple** — get the structure right first, then add detail
2. **Choose direction wisely** — `LR` for sequences/timelines, `TD` for hierarchies
3. **Use subgraphs** to group related elements and reduce visual clutter
4. **Label edges** when the relationship isn't obvious from context
5. **Apply color sparingly** — to highlight categories or status, not to decorate
6. **Keep node text short** — use 2-4 words per node label
7. **Break large diagrams** into focused smaller ones rather than one massive diagram
8. **Quote special characters** — wrap text with parentheses, brackets, or colons in double quotes
9. **Avoid `end` as a node ID** — use `End`, `END`, or `finish` instead (reserved word)
10. **Test rendering** — verify the diagram renders in the target platform

## Instructions for Claude

When the user asks you to create a Mermaid diagram:

1. **Identify the diagram type** — match the user's request to the best diagram type from the table above

2. **Look up syntax if needed** — for newer/uncommon types (architecture, kanban, sankey, XY, packet, requirement, ZenUML) or advanced features, query Context7:
   - Tool: `mcp__plugin_compound-engineering_context7__query-docs`
   - `libraryId`: `/mermaid-js/mermaid`
   - `query`: describe the specific syntax you need

3. **Create the diagram** — write clean Mermaid code following the quick reference above

4. **Add context** — provide a brief explanation of what the diagram shows and any design choices you made

5. **Validate mentally** — check for:
   - Correct diagram declaration keyword
   - Balanced brackets and quotes
   - No reserved-word conflicts (`end` as node ID)
   - Proper arrow syntax for the diagram type
   - Labels on all non-obvious relationships

6. **Offer refinements** — suggest additions or alternative diagram types if relevant

If the user provides vague input like "diagram my system", ask clarifying questions about what aspect they want to visualize (architecture, data flow, state transitions, etc.) before creating the diagram.
