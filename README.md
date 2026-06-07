# UiPath AI Skills

> Transform natural language into production-ready UiPath automations using Coding Agents, Agent Builder, deterministic workflow generation, and enterprise-grade validation.

<p align="center">
  <img src="assets/banner.png" alt="uipath-ai-skills" width="100%">
</p>

## Overview

UiPath AI Skills is an agent-powered automation development platform that enables coding agents such as Claude Code, Codex, Cursor, and Gemini CLI to create production-ready UiPath Studio projects from natural language requirements.

Instead of allowing large language models to generate fragile or invalid XAML directly, the platform combines AI reasoning with deterministic workflow generators, validation pipelines, framework scaffolding, and governance controls to ensure every generated automation can be opened, validated, and deployed within the UiPath ecosystem.

The result is a faster path from Process Definition Document (PDD) to enterprise-ready automation while maintaining the reliability, governance, and quality standards required for production environments.

---

# AgentHack Challenge Alignment

This project was built for UiPath AgentHack and demonstrates how Coding Agents and UiPath platform capabilities can work together to create, validate, and operationalize enterprise automations.

The solution extends coding agents with specialized UiPath automation skills that:

* Analyze business requirements and PDDs
* Generate complete UiPath projects
* Scaffold REFramework architectures
* Build workflows from structured specifications
* Validate generated artifacts
* Detect and prevent hallucinated UiPath activities
* Enforce development best practices
* Produce deployable automations for UiPath Automation Cloud

The project focuses on solving one of the biggest challenges in agentic automation development:

> Moving from AI-generated prototypes to production-ready enterprise automations.

---

# UiPath Components Used

## UiPath Agent Builder

Agent Builder serves as the AI orchestration layer for interpreting business requirements and coordinating automation generation workflows.

The platform leverages Agent Builder to create low-code AI agents capable of:

* Understanding automation requirements
* Generating automation plans
* Coordinating generation workflows
* Managing validation processes
* Interacting with automation tools

## UiPath Studio

UiPath Studio serves as the target runtime environment.

Generated automations include:

* Sequence Projects
* REFramework Dispatcher Projects
* REFramework Performer Projects
* Object Repository Assets
* Config-driven workflows
* Production-ready XAML

Every generated workflow is designed to open successfully in UiPath Studio without requiring manual reconstruction.

## UiPath API Workflows

API Workflows provide reusable enterprise tools that agents can invoke during automation creation and validation.

These workflows enable:

* Secure API integrations
* Enterprise system connectivity
* Controlled execution of automation services
* Standardized business operations
* Reusable automation capabilities

## UiPath Automation Cloud

Automation Cloud provides deployment, governance, monitoring, and execution capabilities for generated automations.

Generated projects are designed to be published and managed through the UiPath cloud ecosystem.

## UiPath Orchestrator

Orchestrator provides:

* Package management
* Asset management
* Queue management
* Process deployment
* Execution monitoring
* Enterprise governance

## UiPath Coding Agents

The solution is specifically designed for coding agents including:

* Claude Code
* Codex
* Cursor
* Gemini CLI

These agents use UiPath AI Skills to transform natural language requirements into deployable UiPath projects.

---

# Agent Type

## Coded Agents

The project uses coded agents to:

* Analyze Process Definition Documents
* Generate automation specifications
* Scaffold projects
* Create workflows
* Refactor existing automations
* Generate automation assets

Supported coding agents include Claude Code, Codex, Cursor, and Gemini CLI.

## Low-Code Agents

The project also utilizes UiPath Agent Builder to create and orchestrate low-code AI agents within the UiPath platform.

## Hybrid Agent Architecture

This solution combines both coded agents and low-code agents.

Coding agents provide reasoning, planning, and automation generation capabilities while UiPath Agent Builder provides orchestration, governance, and enterprise deployment capabilities.

This hybrid architecture allows organizations to benefit from advanced AI-assisted development while maintaining enterprise-grade control and governance.

---

# The Problem

Large Language Models are excellent at understanding business requirements but struggle to generate valid UiPath projects.

Common issues include:

* Invalid XAML
* Hallucinated activities
* Incorrect namespaces
* Broken selectors
* Missing framework components
* Studio compatibility issues
* Invalid package references

These problems often result in hours of manual repair before an automation can be executed.

---

# The Solution

UiPath AI Skills introduces a deterministic generation architecture.

Instead of generating XAML directly, AI agents generate structured specifications.

The platform then:

1. Validates requirements
2. Creates project scaffolding
3. Generates workflows using deterministic generators
4. Validates generated artifacts
5. Detects hallucination patterns
6. Applies framework wiring
7. Produces production-ready UiPath projects

This approach ensures reliability, consistency, and enterprise readiness.

---

# Key Features

* Natural language to UiPath automation
* REFramework generation
* Deterministic XAML generation
* Hallucination prevention
* Validation and auto-fix pipeline
* Object Repository generation
* Config-driven architecture
* Plugin-based extensibility
* Multi-agent support
* Enterprise governance support
* Studio compatibility validation
* Automation Cloud deployment readiness

## Supported Agents

* Claude Code
* OpenAI Codex
* Cursor
* Gemini CLI
* Future coding agent integrations

## Supported Automation Types

* Web Automation
* Desktop Automation
* Queue Processing
* Queue Dispatching
* API Integrations
* Email Automation
* Excel Automation
* PDF Processing
* Human-in-the-Loop Workflows
* Multi-System Enterprise Processes

## Quick start

> [!IMPORTANT]
> **Plugin Layout:** Plugins (like `uipath-tasks`) must be installed as sibling directories to `uipath-core`. The runtime loader scans sibling folders for extensions; moving them to a different nested structure will break discovery.

> [!NOTE]
> **PowerShell:** While the core generators are cross-platform, desktop selector generation via `inspect-ui-tree.ps1` requires PowerShell on a Windows environment.

Adding the skills to your environment is super simple:

<details open>
<summary><strong>Claude Code</strong></summary>

```
/plugin marketplace add marcelocruzrpa/uipath-ai-skills
/plugin install uipath-core@uipath-ai-skills
/plugin install uipath-tasks@uipath-ai-skills
```

Verify by asking Claude *"List my available skills"* — you should see both `uipath-core` and `uipath-tasks`.

</details>

<details>
<summary><strong>Codex CLI</strong></summary>

```bash
git clone https://github.com/Clean-earthw/uipath-ai-skills-submission.git
mkdir -p .codex/skills
cp -r uipath-ai-skills/uipath-core  .codex/skills/uipath-core
cp -r uipath-ai-skills/uipath-tasks .codex/skills/uipath-tasks
codex
```

Or install globally:

```bash
cp -r uipath-ai-skills/uipath-core  ~/.codex/skills/uipath-core
cp -r uipath-ai-skills/uipath-tasks ~/.codex/skills/uipath-tasks
```

If Codex truncates the skill, raise the instruction limit in `~/.codex/config.toml`:

```toml
project_doc_max_bytes = 131072  # 128 KB
```

</details>

<details>
<summary><strong>Manual install</strong></summary>

If you're using a different agent or vendoring the plugins into an existing project, clone and copy:

```bash
git clone https://github.com/Clean-earthw/uipath-ai-skills-submission.git

# Optional: install openpyxl for Config.xlsx management
pip install "openpyxl>=3.1.0"
```

No other dependencies required — all core scripts use Python stdlib.

Copy into a Claude Code project:

```bash
mkdir -p <your-project>/.claude/skills
cp -r uipath-ai-skills/uipath-core  <your-project>/.claude/skills/
cp -r uipath-ai-skills/uipath-tasks <your-project>/.claude/skills/
```

Copy into a Codex CLI project:

```bash
mkdir -p <your-project>/.codex/skills
cp -r uipath-ai-skills/uipath-core  <your-project>/.codex/skills/
cp -r uipath-ai-skills/uipath-tasks <your-project>/.codex/skills/
```

</details>

### Using the skill

1. **Start in plan mode when your agent supports it.** In Claude Code, toggle plan mode with Shift+Tab before sending your prompt — the agent reads your **PDD (Process Definition Document)**, drafts a plan, and waits for your approval before touching files. Review the plan, tweak it if needed, then approve and let it execute.
2. **Name the skill in your prompt** to be sure it loads — e.g. *"Use `uipath-core` to scaffold a REFramework dispatcher for this PDD..."*. The skill also auto-loads when your prompt mentions UiPath, but naming it explicitly is the surest path. For human-in-the-loop or Tasks workflows, name `uipath-tasks`.
3. **Three ways to use it:**
   - **Build a project from a PDD** — point the agent at a PDD file and (optionally) tell it the architecture (sequence, dispatcher, or performer). It scaffolds the project, generates the workflows, inspects target apps for selectors, and validates the output.
   - **Update an existing project** — point it at an existing UiPath project and ask for a bug fix, a new workflow, or a small change. It reads the project structure, generates only the deltas, and re-validates.
   - **Refactor a legacy project into REFramework** — point it at an existing project built with flat structure or bad practices and ask for a wholesale rewrite. It reads the workflows, proposes a proper decomposition (launch / init / process / action files, Config.xlsx, Object Repository), and migrates the logic into the new shape. *Not battle-tested as the other two modes*

