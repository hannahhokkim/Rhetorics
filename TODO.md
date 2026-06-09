# TODO.md

## Rules for Codex

- Complete only the first unchecked task.
- Do not start later tasks.
- Keep changes small and reviewable.
- Run relevant checks after each change.
- Mark a task complete only if the requested checks pass or if the task is purely an audit.
- If blocked, add a `BLOCKED:` note under the task and stop.
- Do not rewrite manuscript prose unless the task explicitly asks for writing.
- Do not change substantive analyses without explaining why.
- All paper-facing numbers should come from the cleaned-data workflow.

## Task queue

### Repo cleanup and workflow stabilization

- [x] Audit old analysis files before moving them.
  - Completed: both files were found to be superseded and not depended on by active notebooks.
  - Archived candidates:
    - `archive/old_analysis/InitialPlotsRhetorics_260325.Rmd`
    - `archive/old_analysis/Rhetorics_analyses.Rmd`
  - Search the full repo for references to these filenames.
  - Check whether either file contains analysis logic, outputs, objects, or figures not reproduced in:
    - `Cleaning.qmd`
    - `CleanedData_Analyses.qmd`
    - `FergusonFigures.qmd`
    - `ExploreQualAndMissing.qmd`
  - Do not move or delete anything yet.
  - Output a recommendation: keep, archive, or delete.

- [x] Archive old analysis files if the audit shows they are superseded.
  - Completed: archived in `archive/old_analysis/`.
  - Moved:
    - `archive/old_analysis/InitialPlotsRhetorics_260325.Rmd`
    - `archive/old_analysis/Rhetorics_analyses.Rmd`
  - Added `archive/old_analysis/README.md`.
  - Active supporting notebooks retained in `Code/`:
    - `FergusonFigures.qmd`
    - `ExploreQualAndMissing.qmd`

- [ ] Audit `Cleaning.qmd` for fragile or suspicious code.
  - Pay special attention to any `skip=,` or malformed import arguments.
  - Confirm what raw input files are required.
  - Confirm that the script creates `Data/responses_final_complete_clean.rds`.
  - Do not change substantive cleaning decisions yet unless the issue is clearly a syntax/fragility bug.
  - Report any cleaning decisions that need human confirmation.

- [ ] Confirm that `Data/responses_final_complete_clean.rds` is reproducibly created.
  - Run or execute the cleaning workflow if possible.
  - Confirm the output file exists.
  - Report dimensions, duplicate `ResponseId` count, missing `field_first` count, and missing methodological orientation count.
  - If Quarto is unavailable, execute the R code chunks directly where feasible and report the limitation.

### Main analysis verification

- [ ] Execute or render `CleanedData_Analyses.qmd`.
  - If Quarto is available, render it.
  - If Quarto is not available, execute the R code chunks directly.
  - Save or update a plain-text/markdown output summary if the notebook already uses one.
  - Report warnings separately from errors.

- [ ] Verify sample characteristics from the cleaned data.
  - Report:
    - analytic N
    - duplicate `ResponseId` count
    - field counts
    - methodological orientation counts
    - years-of-research n, mean, SD, median, range
  - Confirm that field summaries exclude missing `field_first`.

- [ ] Verify scale reliability.
  - Report alpha or omega values currently used in the notebook.
  - Confirm values for:
    - Positivism
    - Inclusivity
    - Neutrality
  - Flag whether Neutrality should be excluded from confirmatory models.

- [ ] Verify H1: epistemological beliefs by field.
  - Report field-level means for Positivism, Inclusivity, and Neutrality.
  - Report model/test outputs used for field differences.
  - Flag which numbers are manuscript-ready.

- [ ] Verify H2: epistemological beliefs by methodological orientation.
  - Compare quantitative and qualitative researchers.
  - Report means and model/test outputs for Positivism, Inclusivity, and Neutrality.
  - Explicitly report missing methodological orientation.

- [ ] Verify perceived qualitative composition analyses.
  - Identify the relevant variable(s).
  - Report correlations or models currently used.
  - Decide whether this belongs in the main paper or supplement.

- [ ] Verify open science attitude models.
  - Outcomes:
    - data sharing attitude
    - preregistration attitude
    - open access attitude
    - replication attitude
  - Confirm whether adding Positivism and Inclusivity improves fit beyond field and methodological orientation.
  - Report model comparison results.

- [ ] Verify open science behavior models.
  - Outcomes:
    - data sharing behavior
    - preregistration behavior
    - open access behavior
    - replication behavior
  - Confirm which behavior models are significant after correction.
  - Report model comparison results.

- [ ] Verify Micah’s granular behavior analyses.
  - Identify which analyses are confirmatory, exploratory, or descriptive.
  - Decide whether they belong in the main text, supplement, or should be removed from the paper workflow.

### Figures and optional analyses

- [ ] Audit `FergusonFigures.qmd`.
  - Identify which figures it creates.
  - Check whether it repeats cleaning or analysis logic that should instead come from `Data/responses_final_complete_clean.rds`.
  - Recommend one of:
    - keep separate as figure notebook
    - fold into `CleanedData_Analyses.qmd`
    - replace with a dedicated `Figures.qmd`

- [ ] Audit `ExploreQualAndMissing.qmd`.
  - Identify analyses it contains.
  - Decide whether these analyses are needed for:
    - main paper
    - supplement
    - internal checking only
  - Do not delete the file unless explicitly asked.

### Manuscript comparison

- [ ] Create a manuscript-number checklist.
  - Make a file called `manuscript_number_checklist.md`.
  - Include all key numbers from `CleanedData_Analyses.qmd` that must be checked against the manuscript:
    - analytic N
    - field counts
    - method counts
    - years of research
    - reliability values
    - field means
    - method means
    - model comparison results
    - attitude results
    - behavior results
  - Mark old known mismatch:
    - old manuscript N = 1446
    - cleaned data N = 1220, pending verification

- [ ] Compare current manuscript results against cleaned analysis outputs.
  - Use the manuscript file if present in the repo.
  - If no manuscript file is present, stop and ask for the manuscript.
  - Identify every mismatch between manuscript claims and cleaned-data outputs.
  - Do not rewrite the manuscript yet.
  - Output a table:
    - manuscript location
    - old value
    - cleaned-data value
    - source analysis section
    - recommended action

### Documentation

- [ ] Create or update `README.md`.
  - Explain the canonical workflow:
    1. run `Cleaning.qmd`
    2. run `CleanedData_Analyses.qmd`
  - Explain optional files:
    - `FergusonFigures.qmd`
    - `ExploreQualAndMissing.qmd`
  - Explain archived files if applicable.
  - Include required data inputs if known.
  - Include how to reproduce key outputs.

- [ ] Create a final analysis status report.
  - Make `analysis_status.md`.
  - Include:
    - canonical dataset
    - canonical notebooks
    - verified sample numbers
    - verified reliability values
    - verified main model results
    - unresolved issues
    - manuscript sections needing update
