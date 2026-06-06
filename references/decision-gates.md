# Decision Gates

Use these gates whenever an action may affect data meaning, membership, quality, provenance, or downstream validity.

## Proceed

Proceed without another approval only when all of the following hold:

- The action is explicitly requested or already authorized by the governing project standard.
- The method and parameters are unambiguous.
- An authoritative implementation is available when domain-sensitive behavior is involved.
- Inputs and prerequisites pass the checks required for this boundary.
- The action stays within the permitted data, filesystem, and overwrite scope.
- The outcome and provenance can be verified.

## Pause For User Decision

Pause before execution when any of the following holds:

- Multiple scientifically or operationally meaningful methods are plausible.
- A threshold, selection rule, fallback, exclusion, repair, or approximation is not approved.
- The proposed action may remove information or change which records reach downstream analysis.
- A project instruction is missing, ambiguous, or inconsistent with another authority.
- Continuing requires changing an approved plan, tool, parameter, data source, or output contract.
- An overwrite, destructive edit, or migration has not been explicitly authorized.

Present the observation, options, consequences, and recommended choice without taking the decision away from the user.

## Halt As Invalid

Halt the current path when any of the following holds:

- A required input or authoritative implementation is unavailable.
- Data or metadata is inconsistent in a way that undermines interpretation.
- A required transformation, validation, or export fails.
- The output is partial, corrupt, misaligned, non-reproducible, or outside allowed scope.
- Continuing would require concealing or bypassing a failure.

Preserve evidence and intermediate products that help diagnose the issue. Do not quietly produce a reduced or substituted result.

## Consequential Versus Presentational Changes

A change is consequential when it can alter data values, membership, uncertainty, semantics, provenance, or downstream conclusions. It requires prior authorization from the user or governing standard.

A presentational change affects only how an already-defined product is displayed. It may proceed when it preserves the underlying product and does not imply unsupported meaning. Record it when it materially affects interpretation.
