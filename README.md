# Mermaid Diagrams Skill for Claude Code

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that creates Mermaid diagrams using up-to-date syntax from the official Mermaid docs via Context7 MCP.

Supports flowcharts, sequence diagrams, class diagrams, state diagrams, ER diagrams, Gantt charts, pie charts, mindmaps, timelines, git graphs, quadrant charts, C4 architecture diagrams, sankey diagrams, XY charts, block diagrams, packet diagrams, kanban boards, requirement diagrams, user journey maps, and more.

## Installation

Clone this repo into your Claude Code skills directory:

```bash
git clone https://github.com/Liviofrol/mermaid-diagrams.git ~/.claude/skills/mermaid-diagrams
```

That's it. Claude Code automatically picks up skills from `~/.claude/skills/`.

## Prerequisites

This skill works best with a **Context7 MCP server** configured in Claude Code, which it uses to look up the latest Mermaid syntax. The skill still works without it, but Context7 enables querying official docs for newer or less common diagram types.

## Usage

In Claude Code, use the slash command:

```
/mermaid-diagrams [description]
```

Examples:

```
/mermaid-diagrams a flowchart showing user authentication
/mermaid-diagrams ER diagram for a blog with users, posts, and comments
/mermaid-diagrams kanban board with backlog, in progress, and done columns
/mermaid-diagrams sequence diagram of an OAuth2 authorization code flow
```

Or just ask Claude to create a Mermaid diagram in natural language — the skill triggers automatically when a diagram request is detected.

## How It Works

```mermaid
flowchart TD
    subgraph install["Installation"]
        A["git clone repo into<br/>~/.claude/skills/mermaid-diagrams"]
        A --> B["Claude Code auto-detects<br/>SKILL.md on startup"]
    end

    subgraph trigger["Trigger"]
        C["/mermaid-diagrams command"]
        D["Natural language request<br/>'create a diagram of...'"]
    end

    B --> C & D

    C & D --> E{"Identify<br/>diagram type"}

    E --> F{"Common type?"}

    F -->|"Yes: flowchart, sequence,<br/>class, ER, state, pie,<br/>Gantt, mindmap, timeline,<br/>git graph"| G["Use built-in<br/>syntax reference"]

    F -->|"No: architecture, kanban,<br/>sankey, XY, packet,<br/>requirement, ZenUML"| H["Query Context7 MCP<br/>/mermaid-js/mermaid"]

    H --> I["Get latest official<br/>Mermaid docs & syntax"]

    G & I --> J["Generate clean<br/>Mermaid code"]

    J --> K["Validate syntax:<br/>keywords, brackets,<br/>arrows, reserved words"]

    K --> L["Render diagram"]

    L --> M{{"20+ diagram types supported"}}

    classDef installStyle fill:#e8f5e9,stroke:#2e7d32,color:#1b5e20
    classDef triggerStyle fill:#e3f2fd,stroke:#1565c0,color:#0d47a1
    classDef decisionStyle fill:#fff8e1,stroke:#f9a825,color:#e65100
    classDef context7Style fill:#f3e5f5,stroke:#7b1fa2,color:#4a148c
    classDef outputStyle fill:#fce4ec,stroke:#c62828,color:#b71c1c

    class A,B installStyle
    class C,D triggerStyle
    class E,F decisionStyle
    class H,I context7Style
    class L,M outputStyle
```

## What's Included

- `SKILL.md` — The skill definition with full Mermaid syntax reference covering 20+ diagram types, styling/theming guidance, and instructions for using Context7 to look up latest syntax.

## Updating

Pull the latest changes:

```bash
git -C ~/.claude/skills/mermaid-diagrams pull
```

## Uninstalling

Remove the skill directory:

```bash
rm -rf ~/.claude/skills/mermaid-diagrams
```
