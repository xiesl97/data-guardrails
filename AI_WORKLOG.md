# AI Worklog

This document is for AI collaborators only. It is the operational handoff
record for the current project or workspace.

Keep it short, current, and decision-oriented. Remove or compress exploratory
history once it no longer affects future work.

## Purpose

- Give the next AI enough context to continue work safely.
- Record durable decisions, approved defaults, formal products, and current
  limitations.
- Make high-risk processing assumptions explicit.

## How To Use

- Read this file before non-trivial work.
- Update it after meaningful work that changes project state, approved methods,
  formal outputs, or known limitations.
- Prefer editing existing bullets over appending endless history.

## What Belongs Here

- Workspace root, current target files, and active analysis interval.
- Approved instruments, detectors, energy bands, bin sizes, or study scope.
- Authoritative tool/library choices.
- Output locations for formal products.
- Validation or audit status that affects whether downstream work may proceed.
- Current blockers, limitations, caveats, and unresolved questions.

## What Does Not Belong Here

- Long narrative reasoning that no longer affects future actions.
- General project background for human readers.
- Full methods writeups, derivations, or report-style explanations.
- Large tables, plots, or raw logs.

## Required Sections

### Workspace And Rules

- Root path:
- Current target files:
- Large source-data location:
- Temporary-artifact policy:
- High-risk boundaries:
- Authoritative project standard:
- Preferred environments:
- Preferred libraries and forbidden reinventions:

### Current State

- Current active interval or sample:
- Current approved detector or instrument subset:
- Current formal products:
- Latest meaningful decision:

### Validation Status

- What has been audited:
- What passed:
- What remains exploratory:
- What must not be overstated in downstream writing:

### Open Questions

- Item:

## Update Style

- Use dated bullets.
- Keep each bullet factual and compact.
- Distinguish facts, approvals, and unresolved issues.
- Mark superseded defaults clearly rather than leaving contradictory bullets.

## Example Entry Shape

- `2026-06-13, AgentName:` Updated detector selection to `N6,N9` only. Formal
  extraction now uses `gbm.data.primitives.EventList` with barycentered `TDB`
  times. Existing quicklooks are still valid; prior `N6,N7,N9` exploratory
  products should not be reused.
