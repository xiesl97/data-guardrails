# Audit Checklist

Select checks that are meaningful for the project's data model, domain, and downstream use. Do not apply irrelevant checks mechanically, and do not invent acceptance thresholds without authority.

## Governance

- Objective, data scope, deliverables, and output locations match the request.
- Consequential choices are approved by the user or governing standard.
- Deviations, fallbacks, and unresolved questions are explicit.
- No unapproved exclusions, repairs, substitutions, or transformations occurred.

## Inputs And Scope

- Required inputs exist and are the intended versions.
- Data access stayed within the allowed source and filesystem scope.
- Source integrity or identity is recorded where practical.
- Required metadata, schemas, coordinate systems, units, and time conventions are known.

## Processing

- Authoritative libraries and functions were used for domain-sensitive operations.
- Executed parameters and methods match the approved plan.
- Warnings, convergence states, return statuses, and exceptions were checked.
- Each consequential transformation has a traceable input and output.
- Source data remains unchanged unless in-place modification was approved.

## Products

- Expected products exist and are complete.
- Shapes, types, ordering, alignment, units, and identifiers are valid where applicable.
- Missing, invalid, duplicate, non-finite, or out-of-range values are reported according to project rules.
- Uncertainty, quality, exposure, weights, or analogous supporting quantities are preserved and validated where applicable.
- Intermediate products needed for audit and reproduction are retained.

## Reproducibility And Handoff

- Provenance records source identity, relevant versions, parameters, transformations, exclusions, and known limitations.
- Formal, exploratory, temporary, superseded, and invalid products are distinguishable.
- Another qualified person or agent can identify the current valid products and unresolved risks.
- The worklog or handoff record reflects the current state rather than an unfiltered chronological dump.

## Audit Report Minimum

An audit report should state:

1. What data was processed and what was deliberately not processed.
2. Which approved methods and parameters were executed.
3. Which checks passed, failed, or were not applicable.
4. Every warning, anomaly, deviation, fallback, and unresolved issue.
5. Whether the products are approved for downstream use, awaiting user review, or invalid.
