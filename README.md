# Data Guardrails

Data Guardrails is a reusable Agent Skill for high-stakes data engineering and
research-data workflows.

It helps AI agents handle data transparently, preserve user control over
consequential decisions, reuse authoritative tools, validate outputs, and leave
an auditable handoff. It intentionally does not prescribe project-specific
algorithms, instruments, directory layouts, or processing stages.

[中文说明](README.zh.md)

## Core Principles

- Never silently alter, exclude, repair, substitute, or ignore data.
- Keep the user informed and in control of consequential decisions.
- Reuse authoritative project and domain implementations.
- Preserve source data, provenance, validation evidence, and limitations.
- Stop when required decisions are unresolved or products may be invalid.
- Separate data-producing operations from downstream interpretation.

## Structure

```text
data-guardrails/
├── SKILL.md
└── references/
    ├── audit-checklist.md
    └── decision-gates.md
```

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
<repository path or URL>
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

## Scope

Data Guardrails is suitable for:

- Data acquisition, selection, conversion, cleaning, calibration, and export
- Research and scientific data reduction
- Analysis-ready dataset production
- Multi-step data pipelines
- Workflows where silent fallback behavior could invalidate results

It is not a replacement for domain expertise, authoritative processing
software, project standards, or user approval.
