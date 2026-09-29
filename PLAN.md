# Project Plan

## 1. Current Process

Riverside Community Clinic currently manages website changes manually. The contractor edits website files directly on the live server on Thursday evenings, without a formal version-control process or automated checks. Previous versions are stored in manually named folders such as `site-old`, `site-old2`, and `site-old-FINAL`, which makes recovery uncertain. Approximately one change in four has to be reversed because something breaks. The process also depends heavily on the contractor because there is no documented operating procedure.

## 2. Current-State DevOps Lifecycle

| Lifecycle Stage | Current State | Evidence |
|---|---|---|
| Plan | Manual | Changes are made when required, mainly on Thursday evenings |
| Code | Manual | Contractor edits website files directly |
| Build | Absent | No automated build or verification process exists |
| Test | Absent | There is no automated verification before release |
| Release | Manual | Changes are uploaded directly to the live server |
| Deploy | Manual | Contractor performs the live deployment |
| Operate | Manual | Website operation depends heavily on the contractor |
| Monitor | Manual/Absent | Problems are noticed after changes cause issues |

The current process therefore contains mostly manual activities and several absent controls.

## 3. CALMS Assessment

### C — Culture

The current process has a strong dependency on one contractor. The scenario states that the contractor is the only person who knows how the system works. This creates a knowledge-sharing problem and makes the process difficult for another person to operate.

### A — Automation

Automation is very limited or absent. Website files are edited and uploaded manually, and there is no automated verification before changes reach the live website.

### L — Lean

The process contains unnecessary manual recovery work. When a change breaks the site, someone must identify which backup folder is the correct previous version and re-upload it.

### M — Measurement

There is no formal measurement of delivery performance. The clinic knows that roughly one change in four has to be reversed, but it does not have a structured delivery-metrics process.

### S — Sharing

Operational knowledge is concentrated with one contractor and the process is undocumented. This means knowledge is not effectively shared with the office coordinator or another potential operator.

### Weakest CALMS Element

The weakest element is **Automation** because the scenario describes direct manual editing, manual uploading and no automated verification. This directly contributes to the risk of incorrect opening hours and broken pages reaching the live website.

## 4. User Stories

### User Story 1 — Clinic Manager

**As a clinic manager, I want website changes to be checked before they are released so that incorrect or broken content is less likely to reach patients.**

Acceptance Criteria:

- A proposed content change must trigger an automated verification process.
- The verification must fail when the required opening-hours file is missing.
- A successful verification must be visible in the repository's Actions history.

### User Story 2 — Office Coordinator

**As an office coordinator, I want website content changes to be reviewed through a pull request so that another person can see what is changing before it is accepted.**

Acceptance Criteria:

- Content changes must be submitted through a branch and pull request.
- The pull request must show the automated verification result.
- The change must be merged only after the verification passes.

### User Story 3 — Patient

**As a patient, I want the published opening hours to be maintained through a controlled process so that I can rely on the information before visiting the clinic.**

Acceptance Criteria:

- The repository must contain a clearly identified opening-hours section.
- The automated check must verify that the opening-hours file exists and is not empty.
- Changes to opening hours must be traceable through repository history.

### User Story 4 — Future Operator

**As a second clinic staff member, I want the delivery process to be documented so that I can operate it without depending on the contractor.**

Acceptance Criteria:

- The repository must contain documentation describing the delivery process.
- The pipeline must be stored in the repository and explained in plain English.
- A documented failure and recovery example must be available.

## 5. Definition of Done

A website-content change is considered Done when:

1. The change is made on a short-lived branch.
2. The change is submitted through a pull request.
3. Automated verification passes.
4. The change has been reviewed before merging.
5. The change is merged into the main branch.
6. The repository history provides evidence of the change and verification result.
The lifecycle mapping is deliberately descriptive of the fictional current state rather than claiming that the clinic already has the new process.
