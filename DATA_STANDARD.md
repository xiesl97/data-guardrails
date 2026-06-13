# Data Processing Standard

This document is for the human project owner and downstream readers. It defines
the approved data-processing contract for the current project.

Its job is to make later writing, reporting, figure production, and result
interpretation possible without re-reading pipeline code.

## Purpose

- State what data was used, how it was processed, and what defaults are
  officially approved.
- Separate formal processing rules from AI execution notes.
- Provide a stable, human-readable reference for papers, reports, and reviews.

## Writing Rules

- Record approved methods and defaults, not passing experiments.
- Prefer explicit scope, parameters, and caveats over implementation detail.
- When a default changes, replace the old rule or mark it superseded.
- If a step is exploratory only, label it clearly as non-formal.

## Required Sections

### 1. Scope

- Project objective:
- Current scientific or analytical question:
- Covered data products:
- Out-of-scope data products:

### 2. Source Data

- Instrument or survey:
- Source files or file families:
- Time system:
- Detector or channel scope:
- Approved source-data location:

### 3. Data Selection And Cropping

- Time intervals:
- Detector selection:
- Energy selection:
- Quality flags or GTI policy:
- Inclusion and exclusion rules:
- Explicitly forbidden silent operations:

### 4. Authoritative Tools

- Preferred environments:
- Preferred project libraries:
- Domain-sensitive functions that must be reused:
- Tools or methods that are explicitly secondary or disfavored:

### 5. Transformations

- Barycentric or time correction:
- Binning rules:
- Background estimation:
- Detector combination rule:
- Net-signal definition:
- Derived products:

### 6. Formal Outputs

- Output directories:
- File naming:
- Required metadata:
- Which products are formal:
- Which products are exploratory only:

### 7. Validation And Approval

- Required checks:
- What counts as a passing audit:
- Known failure modes that require stop-and-report:
- Current approval boundary for downstream use:

### 8. Interpretation Limits

- What may be concluded safely:
- What must still be described as exploratory:
- What must not be claimed from current products:

### 9. Change Log

- Date:
- What changed:
- Why it changed:
- Which prior rule is now superseded:

## Minimal Example

### 1. Scope

- Objective: produce analysis-ready GBM burst-forest light curves for
  morphology and self-affine analysis.

### 2. Source Data

- Data: GBM TTE and matching poshist files.

### 3. Data Selection And Cropping

- Detectors: NaI `N6,N9` only; BGO excluded.
- Time interval: user-approved burst-forest interval only.
- Silent clipping, repair, interpolation, or detector substitution is not
  allowed.

### 4. Authoritative Tools

- Runtime: `gdt` environment.
- Preferred library: project `gbm` package.
- Existing `gbm` instrument-processing behavior must not be reimplemented.

### 5. Transformations

- Barycentric correction is applied to event times only.
- Fine-bin raw light curves are always rebinned from events, never resampled
  from coarse raw light curves.

### 6. Formal Outputs

- Formal products are saved separately from raw source data.

### 7. Validation And Approval

- Any detector mismatch, abnormal exposure, non-finite output, or suspicious
  background product triggers stop-and-report.

### 8. Interpretation Limits

- Exploratory diagnostics may guide future work but are not final scientific
  claims unless explicitly promoted here.
