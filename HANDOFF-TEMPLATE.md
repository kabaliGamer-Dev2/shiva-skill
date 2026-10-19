# Project Handoff Template

**ChatGPT planning → OpenCode implementation**

Use this for Standard and Project work. Quick work skips the files and uses the same questions inline.

Rules:

- Fill only the sections the project needs. Delete the rest; an empty section is not evidence.
- Keep one source of truth per decision. Link to another artifact instead of copying it.
- Use stable requirement IDs. Never renumber them to make a report look complete.
- Mark unknowns as `UNKNOWN`, assumptions as `HYPOTHESIS`, and blockers as `BLOCKED`.
- Record environment variables by name only. Never put secrets in a handoff.
- Put the artifacts in the repository (for example `docs/handoff/`) so OpenCode can inspect them.

---

## 0. Handoff cover

| Field | Value |
|---|---|
| Project | |
| Version / date | |
| Owner | |
| Mode | Standard / Project |
| Repository / branch | |
| Current stage | Discovery / Specification / Readiness / Foundation / Slices / Integration / Hardening / Release |
| Status | `DRAFT` / `READY` / `READY WITH BLOCKERS` / `NOT READY` |
| Last known good | commit / tag / branch |
| Approver | |

**One-sentence outcome:**

**Explicit non-goals:**

---

## 1. PRD.md

### Problem and evidence

- Who is hurt:
- How they are hurt:
- Evidence (observed behavior, support data, user statement, or `UNKNOWN`):
- Why now:

### Users and jobs

| User / role | Job to be done | Success looks like |
|---|---|---|
| | | |

### Requirements

| ID | Requirement | Mandatory or optional | Acceptance test / probe | Status |
|---|---|---|---|---|
| R-01 | | Mandatory | | `NOT TESTED` |
| R-02 | | Optional | | `NOT TESTED` |

### Non-goals

- 

### Journeys

**Primary journey:**

1. 
2. 
3. 

**Failure / recovery journey:**

1. 
2. 
3. 

### Success metrics

| Metric | Baseline | Target | How measured |
|---|---|---|---|
| | | | |

### Constraints

- Technical:
- Operational:
- Legal / privacy:
- Budget / free-tier limits:
- Hardware:
- Deadline:

### Risks and assumptions

| Item | Type | Impact | Cheap test / fallback | Blocking? |
|---|---|---|---|---|
| | Risk / Assumption | | | Yes / No |

### Open decisions

| Decision | Options | Recommendation | Owner | Blocking? |
|---|---|---|---|---|
| | | | | Yes / No |

---

## 2. ARCHITECTURE.md

### System context

- What the system does:
- External actors and services:
- Trust boundaries:

### Components and boundaries

| Component | Responsibility | Owns | Depends on | Interface |
|---|---|---|---|---|
| | | | | |

### Data flow

1. 
2. 
3. 

### Stack and versions

| Layer | Choice | Version / constraint | Why |
|---|---|---|---|
| Runtime | | | |
| Framework | | | |
| Database | | | |
| Auth | | | |
| Hosting | | | |

### Data model and interfaces

- Entities / tables:
- Key invariants:
- API or event contracts:
- Migration strategy:

### Security and privacy

- Authentication:
- Authorization:
- Secrets handling:
- Sensitive data:
- Input validation:
- Abuse cases:

### Failure modes and recovery

| Failure | Detection | Recovery / degraded mode | User-visible behavior |
|---|---|---|---|
| | | | |

### Expensive-to-reverse decisions

| Decision | Why expensive | Alternatives | Revisit trigger |
|---|---|---|---|
| | | | |

### Deployment and environments

- Environments:
- Configuration:
- Health checks:
- Rollback:

---

## 3. IMPLEMENTATION_PLAN.md

### Milestones

| Milestone | Outcome | Target | Exit gate |
|---|---|---|---|
| M1 | | | |
| M2 | | | |

### Vertical slices

Plan small end-to-end slices, not layer-by-layer generation.

| Slice | User-visible outcome | Files / modules | Depends on | Acceptance IDs | Verification | Rollback | Status |
|---|---|---|---|---|---|---|---|
| S1 | | | | R-01 | | | `NOT TESTED` |
| S2 | | | | R-02 | | | `NOT TESTED` |

### Slice contract

Before starting a slice, record these eight fields. Do not enter the next slice until they are satisfied.

1. Objective and scope.
2. Dependencies.
3. Files, modules, or interfaces expected to change.
4. Required tests, including one negative test for critical behavior.
5. Expected evidence.
6. Exit criteria.
7. Rollback or recovery.
8. Conditions that stop progression.

### Stage gates

| Stage | Entry | Output | Exit gate | Status |
|---|---|---|---|---|
| Discovery | Request | Scope note | Problem, users, constraints, risk understood | |
| Specification | Scope note | PRD + acceptance IDs | Criteria testable; non-goals explicit | |
| Readiness | Specification | Gate report | One of three outcomes; blockers and assumptions listed | |
| Foundation | Readiness | Runnable skeleton | Build, test, health checks pass | |
| Slices | Foundation | End-to-end capabilities | Slice acceptance and regression checks pass | |
| Integration | Slices | Integrated system | Integration matrix passes | |
| Hardening | Integration | Hardened build | No critical issue; limits recorded | |
| Release | Hardening | Release report | Mandatory criteria verified or waived | |

### Dependencies and environment

- Runtime:
- Package manager:
- Required services:
- Environment variable names:
- Test data:
- External API limits:

### Plan drift log

| Date | Trigger | Conflict | Proposed change | Artifacts updated | Re-approved? |
|---|---|---|---|---|---|
| | | | | | Yes / No |

---

## 4. ACCEPTANCE_CRITERIA.md

### Status definitions

- `NOT STARTED` — no work yet.
- `IN PROGRESS` — work has begun, no result yet.
- `BLOCKED` — verification or implementation cannot proceed.
- `FAILED` — the check ran and failed.
- `NOT TESTED` — no appropriate check ran.
- `PARTIALLY VERIFIED` — some criteria passed; others remain open.
- `VERIFIED` — the check ran and passed, with reproducible evidence.
- `WAIVED` — accepted without verification, with authorizer, reason, and residual risk.

### Traceability matrix

| Requirement ID | Design decision | Implementation task | Test / probe | Evidence | Status |
|---|---|---|---|---|---|
| R-01 | | | | | `NOT TESTED` |

Rules:

- Every mandatory requirement has an ID, a test, and a status.
- Every critical feature has a positive test and a negative test.
- An orphan requirement is a gap. A test with no requirement is allowed for regression or security, but label it.
- A waiver records who authorized it, why, and what risk remains. It cannot waive a mandatory security or safety failure.
- Update after each slice, not at the end. The final report uses the same IDs and statuses.

### Integration checks

| Boundary | Check | Result | Evidence |
|---|---|---|---|
| UI → API | Request/response shape, validation, loading, empty, error | | |
| Auth / authorization | Sign-in/out, expiry, roles, forbidden access | | |
| API contract | Schema, status codes, versioning, pagination, idempotency | | |
| Database / migrations | Clean apply, rollback, constraints, existing data | | |
| Environment / services | Required variables, unavailable service, timeout, rate limit | | |
| Failure / recovery | Retry, duplicate submit, partial failure, offline | | |
| Critical journey | Happy path plus one failure/recovery path | | |

A skipped boundary is `NOT TESTED`, not “probably fine.”

---

## 5. README.md or setup documentation

### Prerequisites

- Runtime and exact version:
- Package manager:
- Required services:
- Accounts or access:

### Install

```text
# exact commands
```

### Environment variables

| Name | Required? | Purpose | Where set |
|---|---|---|---|
| | | | |

Never include values, tokens, or passwords.

### Run

```text
# exact command
```

### Build and test

```text
# build
# test
# lint / typecheck
```

### Deployment

- Target:
- Command or pipeline:
- Health check:
- Rollback:

### Troubleshooting

| Symptom | Likely cause | Check | Fix |
|---|---|---|---|
| | | | |

Mark any command you have not run as `UNVERIFIED`.

---

## 6. Conditional artifacts

Add only when the change touches the boundary.

### API contract

| Method | Path | Auth | Request | Response | Errors | Idempotent? |
|---|---|---|---|---|---|---|
| | | | | | | |

Include versioning, pagination, rate limits, and validation rules.

### Database schema and migrations

| Table / type | Columns / fields | Constraints | Indexes |
|---|---|---|---|
| | | | |

- Migration order:
- Backup / snapshot:
- Rollback:
- Existing-data behavior:

### Security and threat model

| Asset | Actor | Trust boundary | Threat | Control | Verification |
|---|---|---|---|---|---|
| | | | | | |

Include secrets, permissions, abuse cases, and logging. Do not include real secrets.

### UI specification

| Screen / state | Purpose | Content | Actions | Loading / empty / error |
|---|---|---|---|---|
| | | | | |

Include responsive behavior, keyboard access, focus, labels, and contrast.

### Deployment and rollback plan

- Environments:
- Configuration differences:
- Environment variable names (never values):
- Migration step and order:
- Auth and redirect URLs:
- CORS, cookies, and allowed origins:
- Worker or serverless execution limits:
- Background jobs and schedules:
- Health check:
- Smoke test:
- Logging and error reporting:
- Backup and restore:
- Rollback trigger:
- Rollback command:
- Post-deploy verification:

A local build is not a deployment. Record the deployed URL and the smoke-test result, or mark release verification `NOT TESTED` / `BLOCKED`.

### RAG evaluation dataset

Fill only when retrieval or generated answers are part of the product.

| Case ID | Type | Input | Expected behavior | Retrieved? | Citation correct? | Result |
|---|---|---|---|---|---|---|
| Q-01 | Supported answer | | Answers from the source | | | |
| Q-02 | No answer in material | | Refuses or states uncertainty | | | |
| Q-03 | Multi-passage | | Combines passages | | | |
| Q-04 | Misleading document | | Does not follow the distractor | | | |
| Q-05 | Conflicting sources | | Reports the conflict | | | |
| Q-06 | Prompt injection in file | | Ignores embedded instructions | | | |
| Q-07 | Empty or malformed file | | Clear failure, no fabricated answer | | | |

Record a baseline before setting a threshold. Re-run after changes to chunking, embeddings, prompts, or models.

---

## 7. Readiness gate report

| Check | Evidence | Status | Blocking? |
|---|---|---|---|
| Outcome, users, non-goals, acceptance IDs | | | |
| Repository fit: paths, stack, versions, scripts | | | |
| Toolchain verified: runtime, package manager, install, build, test, lint | | | |
| Environment variables and services identified (no secrets) | | | |
| External claims have evidence-register rows | | | |
| Component compatibility checked | | | |
| Data, auth, authorization, API, migration, deployment constraints | | | |
| Verification and rollback defined | | | |
| Top uncertainties have a fallback | | | |

**Decision (choose one):** `READY` / `READY WITH BLOCKERS` / `NOT READY`

Assumptions belong in the evidence register; they are not a readiness state.

### Blockers

| Blocker | Why it matters | Affected phase | Required evidence or decision | Owner/action | Release impact |
|---|---|---|---|---|---|
| | | | | | |

Isolated tasks may proceed under `READY WITH BLOCKERS`. A blocker that prevents safe implementation or verification makes the project `NOT READY`.

### Evidence register

| Claim | Source | Date checked | Applies to | Status | Impact if wrong | Next action |
|---|---|---|---|---|---|---|
| | | | | `UNVERIFIED` | | |

Statuses: `VERIFIED`, `ASSUMED`, `UNVERIFIED`, `CONTRADICTED`. Prefer official sources; record the URL and date. Scope each row to the exact plan, region, model, or version.

### Domain gates

| Gate | Required when | Completion |
|---|---|---|
| Architecture compatibility | Multi-component or hosted system | Every seam has evidence or a proof of concept |
| Database isolation | User-owned data | Policies and negative tests pass |
| AI provider and embeddings | Models or vectors are used | Contract tests; mismatched dimensions rejected |
| Secrets lifecycle | Credentials are stored | Rotation and deletion tested or flagged |
| Durable jobs | Work outlives a request | Retry and duplicate-submission tests |
| RAG evaluation | Retrieval or generated answers | Dataset and baseline recorded |
| Deployment | Any production claim | Deployed smoke test or recorded blocker |

Mark a gate `N/A` with one reason; never leave it blank.

---

## 8. Checkpoint and resume record

| Field | Value |
|---|---|
| Date / time | |
| Stage / slice | |
| Goal | |
| Completed | |
| Pending | |
| Blocked | |
| Failed | |
| Unverified | |
| Last known good | commit / tag / branch |
| Exact commands | |
| Next action | |

On resume: read this record and `git status` first. Restate the state in one line.

---

## 9. OpenCode bootstrap prompt

```text
Read AGENTS.md and the handoff artifacts. Do not edit files yet.

1. Restate the outcome, non-goals, and mandatory acceptance criteria.
2. Compare the plan with the repository: paths, stack, versions, scripts, environment variables, data/auth, and deployment.
3. Run the §7.2 readiness gate. List blocking and non-blocking gaps with evidence.
4. Propose the first vertical slice, the files it touches, and how it will be verified.

Stop and wait for approval.
```

---

## 10. Completion report

| ID | Requirement | Check run | Evidence | Status | Notes |
|---|---|---|---|---|---|
| R-01 | | | | `NOT TESTED` | |

Completion rules:

- All mandatory requirements `VERIFIED` means complete.
- Any mandatory `FAILED`, `BLOCKED`, or `NOT TESTED` means not complete; state the gap and next action.
- `PARTIALLY VERIFIED` requires explicit residual scope and a recorded waiver.
- Deferred items are listed separately and are not complete.
- Name the command for tests and the target for build.
- Report what remains unverified even when the main result is positive.

---

## 11. Planner prompt for ChatGPT

Use this before exporting the artifacts:

```text
Act as a product and engineering planner. Do not invent repository facts.

From the information I provide:
1. State the problem, users, evidence, and explicit non-goals.
2. Separate mandatory requirements from optional features. Give each mandatory requirement an ID.
3. Identify expensive-to-reverse decisions, data/interface boundaries, and assumptions that could invalidate the plan.
4. Check feasibility against time, budget, free-tier limits, hardware, dependencies, and available services.
5. Define acceptance criteria and the cheapest verification method for each mandatory requirement.
6. List realistic failure modes, detection, recovery, and degraded behavior.
7. List unresolved decisions and risks. Mark blocking versus non-blocking.
8. Produce PRD.md, ARCHITECTURE.md, IMPLEMENTATION_PLAN.md, ACCEPTANCE_CRITERIA.md, and setup notes. Add API, database, security, UI, or deployment artifacts only if relevant.
9. Mark every unknown as UNKNOWN. Do not fill gaps with plausible-sounding details.

End with: READY, READY WITH BLOCKERS, or NOT READY. List assumptions in the evidence register, not as a state.
```
