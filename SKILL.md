---
name: data-guardrails
description: Guardrails for high-stakes or research data work where silent transformations, undocumented assumptions, or unapproved decisions could invalidate downstream results. Use when acquiring, selecting, converting, cleaning, calibrating, combining, reducing, or exporting data; building data pipelines; or producing analysis-ready datasets. Enforces user governance, provenance, established-tool reuse, explicit decision gates, validation, and auditable handoffs without prescribing project-specific algorithms.
---

# Data Guardrails

Treat data engineering as part of the result, not as invisible preparation. Preserve the user's knowledge of and authority over every decision that can change which data exists, what it means, or how downstream results should be interpreted.

## Establish The Governing Contract

Before changing data, identify:

1. The requested objective and deliverables.
2. The authoritative project instructions, schemas, domain documentation, and approved tools.
3. The source data, allowed scope, output location, and overwrite policy.
4. Which choices the user has already made and which remain unresolved.
5. The validation evidence required before downstream use.

Follow explicit user and project decisions. Do not turn a choice that was appropriate in another project into a universal rule. If instructions conflict, are ambiguous, or omit a consequential choice, stop at the decision boundary and ask.

## Preserve User Governance

The user must retain meaningful knowledge and control over data-affecting decisions.

- Never silently select, exclude, filter, clip, repair, interpolate, impute, smooth, normalize, reweight, merge, relabel, deduplicate, substitute, or otherwise alter data.
- Never silently ignore warnings, failed records, missing inputs, invalid values, partial outputs, or validation failures.
- Never invent domain meaning, calibration behavior, quality criteria, or acceptance thresholds.
- State proposed consequential transformations before executing them unless the user or governing standard has already approved them.
- When an unapproved decision is required, preserve the current state, explain the options and consequences, and wait for the user.

Do not treat logging an unapproved choice after the fact as consent.

## Hard Rule — No Agent-Internal Phase Labels In Products

Never use agent-internal labels such as `item1`, `item2`, `phase3`, `stage7`, `task_A`, or similar numbering in script filenames, output directory names, output filenames, variable names, metadata `item`/`stage` fields, or any scientific product.

These labels exist only in:

- agent-human conversation,
- planning documents such as `PLAN.md`, `HANDOFF`, or the worklog,
- explicit cross-references back to those plans.

Scripts and products must use names that are physically meaningful, observation-relevant, or method-descriptive. The only exception is when a genuine scientific convention already uses numbered phases; agent-internal numbering is never the exception.

## Use Authoritative Implementations

Reuse the project's trusted libraries, domain tools, schemas, and established pipeline functions for domain-sensitive operations.

- Inspect available APIs and local project patterns before implementing processing logic.
- Do not reimplement established domain behavior merely because a custom version appears simple.
- If the authoritative implementation cannot handle the input, report the gap. Do not silently replace it with an approximation or a different method.
- Custom code may orchestrate approved functions, validate products, preserve metadata, and visualize returned data.
- Clearly identify any custom transformation that affects data semantics and obtain approval before relying on it.

## Protect Sources And Provenance

- Treat source data as immutable unless the user explicitly requests an in-place change.
- Write derived products separately and make their relationship to sources traceable.
- Avoid destructive overwrites. Require explicit approval or a project-approved overwrite mechanism.
- Record enough provenance to reproduce each formal product: source identity, relevant versions, parameters, transformations, exclusions, timestamps or run identity, and known limitations.
- Distinguish observed facts, validation results, assumptions, and interpretations.

## Create And Maintain Project Companion Documents

When a project does not already define equivalent files, create and maintain two
workspace documents alongside the actual project work:

- `AI_WORKLOG.md`: for AI collaborators only. Keep it short, current, and
  operational. Record durable decisions, current approved scope, formal
  products, validation status, limitations, and unresolved questions.
- `DATA_STANDARD.md`: for the user and downstream human readers. Record the
  approved processing contract: source data, selection rules, authoritative
  tools, transformations, defaults, outputs, validation requirements, and
  interpretation limits.

Do not merge these two audiences into one document by default. The AI worklog
is for execution handoff; the data standard is for stable human reference.
Update both when meaningful changes affect their audience.

## Validate At Meaningful Boundaries

Validate inputs before processing, intermediate products after consequential transformations, and final products before handoff.

- Choose checks from the governing schema, domain rules, and intended downstream use.
- Surface all failed checks and suspicious observations; do not convert them into silent repairs.
- Confirm that outputs are complete, aligned, correctly typed and shaped, and traceable to inputs where applicable.
- Verify that the executed method and parameters match the approved plan.
- Scale independent checks, audit products, and approval gates with the transformation's risk and irreversibility.

Use [references/audit-checklist.md](references/audit-checklist.md) to assemble a project-appropriate audit. It is a menu, not a claim that every check applies universally.

## Stop At Decision Gates

Stop before proceeding when the next action would require an unapproved consequential decision, when trustworthy processing is unavailable, or when evidence indicates the products may be invalid.

Use [references/decision-gates.md](references/decision-gates.md) to decide whether to proceed, pause for user approval, or halt because the current path is invalid.

When stopping, report:

- What was attempted and what remains untouched.
- The precise observation or missing decision.
- Why it matters to data meaning or downstream validity.
- The available options and their tradeoffs.
- The smallest user decision needed to continue.

## Separate Processing From Interpretation

Keep data-producing steps distinguishable from downstream analysis and presentation.

- Downstream analysis must consume identifiable, validated data products.
- Visualization may reveal and audit data, but must not silently change the underlying product.
- Iterating on plots must not rerun or alter data processing unless that rerun is deliberate and reported.
- Retain intermediate products when they are necessary to audit or reproduce a result.

Use staged review or an explicit audit-before-analysis gate when the user, project standard, or risk level calls for it. Do not impose a fixed number of phases on every project.

## Maintain A Durable Handoff

Leave the workspace understandable to another qualified agent or person.

- Ensure `AI_WORKLOG.md` and `DATA_STANDARD.md` exist when the project calls for
  them or when equivalent documents are absent.
- Update the project's chosen worklog or handoff record with durable decisions, current formal products, validation status, limitations, and unresolved questions.
- Update the project's human-facing standard when approved processing scope,
  defaults, formal outputs, or interpretation limits change.
- Keep exploratory history only when it affects interpretation or future decisions.
- Mark superseded or invalid products clearly so they are not reused accidentally.
- Keep temporary artifacts and large source data in locations permitted by the project's workspace policy.

## Completion Standard

Do not call data work complete merely because a script ran. Completion requires:

- The requested product exists in the approved location.
- Consequential transformations were approved and recorded.
- Required validation passed, or failures are explicitly reported.
- Provenance and limitations are sufficient for downstream users.
- No unresolved issue is being hidden by fallback behavior or omission.
