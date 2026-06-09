# AGENTS.md

## Project

This is the rhetoric/open science epistemology project.

The paper examines how epistemological beliefs vary across social science fields and methodological orientations, and how those beliefs relate to open science attitudes and behaviors.

The current canonical analysis should use the cleaned data workflow, not older scratch notebooks.

## Canonical workflow

The main reproducible workflow is:

1. `Cleaning.qmd`
2. `CleanedData_Analyses.qmd`

The cleaned analytic dataset is:

- `Data/responses_final_complete_clean.rds`

Other notebooks may be useful but should not be treated as canonical unless explicitly checked:

- `FergusonFigures.qmd`: figure-specific workflow, possibly optional.
- `ExploreQualAndMissing.qmd`: qualitative and missingness analyses, possibly optional.
- `archive/old_analysis/InitialPlotsRhetorics_260325.Rmd`: old/superseded analysis retained for history.
- `archive/old_analysis/Rhetorics_analyses.Rmd`: old/superseded or scratch analysis retained for history.

## Working rules

- Do one task at a time.
- Do not start the next unchecked task unless explicitly asked.
- Do not make broad refactors.
- Do not rewrite the scientific argument unless explicitly asked.
- Do not change substantive analyses without explaining the reason.
- Prefer simple readable R code.
- Prefer base R, tidyverse, dplyr, ggplot2, and common statistical packages already used in the repo.
- Avoid unnecessary custom functions.
- Avoid clever abstractions.
- Preserve existing variable names unless there is a clear reason to change them.
- Any manuscript number must come from the cleaned-data workflow.
- If a result differs from an older manuscript number, flag it clearly.
- If a task is blocked, write a `BLOCKED:` note explaining why and stop.

## Statistical/reporting rules

- Treat `Data/responses_final_complete_clean.rds` as the canonical analytic dataset unless the current task is about cleaning.
- Do not use old N = 1446 numbers unless explicitly comparing against the old draft.
- Current cleaned analytic sample appears to be N = 1220, but always verify from the data before reporting.
- Field-based summaries should exclude missing `field_first` unless the task is specifically about missingness.
- Confirmatory models should use Positivism and Inclusivity unless explicitly asked otherwise.
- Neutrality has lower reliability and should be treated cautiously.
- Distinguish attitudes from behaviors.
- Distinguish field effects from methodological orientation effects.
- When reporting model outputs, include enough information to trace the result back to the code.

## File hygiene

- Before deleting or archiving files, check whether they are referenced elsewhere.
- Prefer archiving over deleting unless explicitly asked to delete.
- Suggested archive location: `archive/old_analysis/`
- If moving old files, add a README explaining why they were moved.
- After moving files, run a repo-wide search to confirm active files do not refer to old paths.

## Output expectations

After each task, report:

1. What changed.
2. Which files changed.
3. What checks were run.
4. Any warnings or failures.
5. Any manuscript-relevant numbers that changed.
6. The git diff summary.

Do not claim a notebook renders unless it actually renders.
If Quarto is not installed, say so and execute the R code chunks if possible.
