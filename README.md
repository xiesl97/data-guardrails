# Data Guardrails

Data Guardrails is a reusable Agent Skill for high-stakes data engineering and
research-data workflows.

It helps AI agents handle data transparently, preserve user control over
consequential decisions, reuse authoritative tools, validate outputs, and leave
an auditable handoff. It intentionally does not prescribe project-specific
algorithms, instruments, directory layouts, or processing stages.

[简体中文](README.zh.md)

## Core Principles

- Never silently alter, exclude, repair, substitute, or ignore data.
- Keep the user informed and in control of consequential decisions.
- Reuse authoritative project and domain implementations.
- Preserve source data, provenance, validation evidence, and limitations.
- Stop when required decisions are unresolved or products may be invalid.
- Separate data-producing operations from downstream interpretation.
- Never use agent-internal labels such as `item1`, `phase3`, or `task_A` in scripts, products, or metadata; use physically meaningful, observation-relevant, or method-descriptive names instead.

## Structure

```text
data-guardrails/
├── AI_WORKLOG.md
├── DATA_STANDARD.md
├── SKILL.md
└── references/
    ├── audit-checklist.md
    └── decision-gates.md
```

- `AI_WORKLOG.md` is a reusable template for the AI-facing project worklog.
- `DATA_STANDARD.md` is a reusable template for the human-facing project data
  processing standard.
- `SKILL.md` contains the core instructions and activation description.
- `references/audit-checklist.md` provides a configurable audit checklist.
- `references/decision-gates.md` defines when an agent may proceed, must ask
  the user, or must halt.

The `references` directory is part of the portable skill. It contains supporting
guidance referenced by `SKILL.md`, not platform-specific configuration.

## Installation

Ask the AI agent you want to use to install this repository as a skill.

For example:

```text
Install this repository as a reusable skill for your agent environment:
https://github.com/xiesl97/data-guardrails
```

The agent should inspect its own skill format and capabilities before
installation. If it supports referenced resources, it should preserve the
`references` directory. If it only supports a standalone instruction file, it
should merge the necessary referenced guidance into the installed skill without
changing its meaning.

## Usage

Invoke the skill explicitly when performing consequential data work:

```text
Use $data-guardrails while building and validating this data pipeline.
```

An agent may also activate it automatically when its description matches the
task.

The skill complements project-specific processing standards. Project documents
should define the actual data sources, approved algorithms, parameters, quality
criteria, and output contracts. Data Guardrails governs how agents follow,
verify, document, and escalate those decisions.

When a project does not already provide equivalent documents, an agent using
this skill should create and maintain:

- `AI_WORKLOG.md` for AI-only operational handoff, current state, and durable
  execution constraints.
- `DATA_STANDARD.md` for the human-facing processing contract: approved data
  scope, transformations, defaults, outputs, validation, and interpretation
  limits.

These documents should live in the project workspace, not inside the installed
skill directory. When naming scripts or outputs, avoid agent-internal phase or
item labels; the only acceptable references are in planning documents or
explicit cross-references back to them.

## Scope

Data Guardrails is suitable for:

- Data acquisition, selection, conversion, cleaning, calibration, and export
- Research and scientific data reduction
- Analysis-ready dataset production
- Multi-step data pipelines
- Workflows where silent fallback behavior could invalidate results

It is not a replacement for domain expertise, authoritative processing
software, project standards, or user approval.
