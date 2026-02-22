
# 🤖 AI-Powered SDLC Workflow

> A multi-agent system built on Claude Code that automates the entire Software Development Lifecycle — from requirements gathering to parallel swarm-based development — using prompt-engineered markdown templates and intelligent agent orchestration.

---

## 📖 Overview

The **AI-Powered SDLC Workflow** is an open-source framework that uses specialized AI agents at every phase of software development. The system is built around a set of **prompt-engineered markdown templates** that serve as structured instructions for Claude to generate artifact content — and a set of **Claude Code agents** that read these templates, ask contextual questions to keep humans in the loop, and produce real, usable outputs.

The workflow progresses through three major phases:

1. **Requirements Phase** — The `req-agent` gathers context through questions and fills structured requirement artifacts
2. **Design Phase** — The `des-agent` produces architecture, API contracts, and technical design artifacts
3. **Development Phase** — A swarm of three agents (`code-agent`, `review-agent`, `test-agent`) work in parallel via tmux to complete user stories, triggerable via a single slash command: `/develop [story-number]`

---

## 🏗️ How It Works

### Step 1 — Prompt-Engineered Markdown Templates

Before any agent runs, a set of markdown template files is prepared for each SDLC phase. These templates were designed using ChatGPT with a structured prompt engineering format:

```
<!--
ROLE        You are a Senior Product Manager...
TASK        Analyze the raw input and synthesize...
CONSTRAINTS - Use only the information provided...
INPUT       00_raw_input.md
OUTPUT      A Markdown document containing...
-->
```

These templates act as **instructions embedded inside the artifact files themselves** — Claude reads them and knows exactly what content to generate, in what format, and with what constraints.

All templates are stored in a GitHub repository, cloned locally, and opened in VS Code:

```
project-repo/
├── requirements/
│   ├── 00_raw_input.md
│   ├── 01_problem_statement.md
│   ├── 02_goals.md
│   ├── 03_scope.md
│   ├── 04_prd.md
│   ├── 05_user_stories_epics.md
│   ├── 06_acceptance_criteria.md
│   ├── 07_requirement_templates.md
│   ├── 08_stakeholder_summary.md
│   ├── 09_implementation_details.md
│   ├── 10_technical_specs.md
│   ├── 11_technical_dependencies.md
│   ├── 12_edge_cases.md
│   └── 13_test_scenarios.md
├── design/
│   ├── HLD/
│   │   ├── architecture_overview.md
│   │   ├── system_components.md
│   │   ├── data_flow.md
│   │   ├── tech_stack_decisions.md
│   │   └── non_functional_design.md
│   ├── LLD/
│   │   ├── component_design.md
│   │   ├── api_contracts.md
│   │   ├── database_schema.md
│   │   ├── sequence_flows.md
│   │   └── error_handling.md
│   └── UI_UX/
│       ├── design_variations.md
│       └── design_to_code_suggestions.md
├── SWARM_CONTEXT.md
└── CLAUDE.md
```

---

### Step 2 — Requirement Agent

**Trigger:** Type `run req-agent` in Claude Code

The requirement agent keeps the **human in the loop** by first asking a series of contextual questions about the product being built. Once it has enough context, it iterates through every file in the `requirements/` folder and fills in the content for each artifact.

**Example questions asked by req-agent:**

- What type of tool is this?
- Who is the target user?
- Where does the data come from?
- How should users interact with the results?
- Does the app need authentication?

**Output:** All requirement markdown files populated with structured, product-ready content — problem statements, user stories, epics, acceptance criteria, stakeholder summaries, and more.

---

### Step 3 — Design Agent

**Trigger:** Type `run des-agent` in Claude Code

With the requirement artifacts now populated, the design agent reads them, asks clarifying questions about technical preferences and constraints, and fills in all files in the `design/` folder.

**Output:** Complete technical design documentation including:

- High-Level Design (architecture overview, data flow, tech stack decisions)
- Low-Level Design (component design, API contracts, database schema, sequence flows)
- UI/UX design variations and design-to-code suggestions

---

### Step 4 — JIRA Agent

**Trigger:** Type `run jira-agent` in Claude Code

The JIRA agent asks claryfiying questions to better understand the team velocity and reads the populated requirement artifacts — particularly user stories, epics, and acceptance criteria — and uses the **Atlassian MCP connection** to create issues directly in your JIRA project.

**Output:**

- Epics with detailed descriptions
- User stories with acceptance criteria and priority
- Subtasks mapped to stories
- A sprint blueprint showing recommended execution order

> **Prerequisite:** Claude Code must be connected to your JIRA project via the Atlassian MCP. See [Setup](#-setup) below.

---

### Step 5 — Swarm Execution (Development Phase)

The development phase uses a **multi-agent swarm** running in parallel via tmux. Three agents — `code-agent`, `review-agent`, and `test-agent` — work simultaneously on a single user story, communicating with each other and reporting to a team lead (you).

#### The SWARM_CONTEXT.md File

Before swarm execution, a `SWARM_CONTEXT.md` file was created to serve as the **shared instruction set** for all three agents. It defines each agent's responsibilities, their communication protocol, and the exact workflow for completing a user story.

To start a swarm session manually, open a new Claude Code instance in tmux, attach `SWARM_CONTEXT.md` as context, and ask Claude to create an agent team with the three agents. Claude will then spawn them in split panes for full parallel visibility:

```


________________________________________________
|                                              |
|                  TEAM LEAD                   |
|                (orchestrator)                |
┌──────────────────────┬──────────────────────┐|
│     code-agent       │    review-agent       │
│                      │                       │
│  Generating code...  │  Reviewing spec...    │
│                      │                       │
├──────────────────────┴──────────────────────┤
│                  test-agent                  │
│                                              │
│  Running pytest + playwright test suite...   │
└─────────────────────────────────────────────┘
```

#### Agent Responsibilities

| Agent            | Role                                                                                                        |
| ---------------- | ----------------------------------------------------------------------------------------------------------- |
| **code-agent**   | Generates production code for the user story based on design artifacts                                      |
| **review-agent** | Reviews code for spec compliance, logic correctness, and security issues                                    |
| **test-agent**   | Writes and runs unit, integration, navigation, UI/UX, API, and user journey tests via pytest and Playwright |

#### Communication Flow

```
code-agent writes code
       │
       ▼
review-agent reviews
       │
       ├── issues found? → reports to code-agent → code-agent fixes → review-agent re-reviews
       │
       ▼ (approved)
test-agent runs full test suite
       │
       ├── tests fail? → reports to code-agent → fixes → test-agent re-runs
       │
       ▼ (all tests pass)
team lead (you) approves writing code to project directory
       │
       ▼
Story complete ✅
```

> **Human Approval Gate:** No code is written to the project directory without explicit approval from the team lead. Every file write is requested and only proceeds on your confirmation.

---

### Step 6 — The `/develop` Skill

After validating the swarm execution workflow, the entire process was generalized into a **Claude Code custom skill** called `develop`.

**Trigger:** `/develop [user-story-number]`

This single slash command replaces the need to manually open a tmux session, attach `SWARM_CONTEXT.md`, and prompt Claude to create the agent team. The skill handles all of that automatically — it reads the SWARM_CONTEXT file, spawns the three agents in tmux, and begins parallel swarm execution for the specified user story.

```bash
# Example — kick off development for user story 4
/develop [4], [US-04], [User Story 4]
```

---

## 🚀 Setup

### Prerequisites

- [Claude Code](https://docs.anthropic.com) installed and authenticated with your Anthropic API key
- [VS Code](https://code.visualstudio.com/) with integrated terminal
- [tmux](https://github.com/tmux/tmux/wiki) installed on your machine
- [JIRA account](https://www.atlassian.com/software/jira) + API token
- [Atlassian MCP](https://www.atlassian.com/) configured and connected to Claude Code

### Installation

```bash
# Clone the repository
git clone https://github.com/divi2227/SDLC_FinalTemplate.git
cd SDLC_FinalTemplate

# Open in VS Code
code .
```

### JIRA MCP Configuration

Connect Claude Code to your JIRA project by configuring the Atlassian MCP with your credentials:

```json
{
  "jira": {
    "baseUrl": "https://your-domain.atlassian.net",
    "email": "your_email@example.com",
    "apiToken": "your_jira_api_token",
    "projectKey": "YOUR_PROJECT_KEY"
  }
}
```

---

## 🧑‍💻 Usage Summary

| Phase        | Command                   | Output                                                    |
| ------------ | ------------------------- | --------------------------------------------------------- |
| Requirements | `run req-agent`           | Populated requirement artifact `.md` files                |
| Design       | `run des-agent`           | Populated design artifact `.md` files                     |
| JIRA         | `run jira-agent`          | Epics, stories & sprint blueprint created in JIRA         |
| Development  | `/develop [story-number]` | Code, tests & review completed via parallel swarm in tmux |

---

## 🙏 Acknowledgements

- [Anthropic](https://anthropic.com) for Claude Code and the Claude API
- [Atlassian](https://atlassian.com) for the JIRA MCP integration
- [OpenAI / ChatGPT](https://openai.com) for helping design the prompt-engineered markdown templates
