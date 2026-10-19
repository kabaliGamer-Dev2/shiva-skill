# SHIVA-SKILL v3.2 — Verification Checklist

**Source:** `S-Skill-v3.2.md` (49,136 bytes, 7,173 words)  
**Baseline:** `S-Skill-v3.1.md` (36,859 bytes, SHA256 `934961DC…AD7E`)  
**Date:** 2026-10-19  
**Method:** structural scripts, grep-based regression checks, and tabletop scenarios. No task-level behavioral run.

---

## 1. What was inspected

| Item | Evidence |
|---|---|
| v3.1 full source | 597 lines; 15 sections; SHA256 recorded |
| Repository tree and git state | Four prior versions; v3.1 files untracked; README modified before this work |
| `CHANGELOG-v3.1.md` | Full read; merge/dedupe history |
| `VERIFICATION-CHECKLIST.md` §6–7 | Contradiction scan and limitations |
| `README.md` | Full read; version, size, install, validation claims |
| `HANDOFF-TEMPLATE.md` | Readiness, status, and matrix sections |
| `OPENCODE-GUIDE.md` | Version references and rollback |
| Global `AGENTS.md`, `opencode.json` | Trigger present; no `skill` permission deny |
| Study Buddy evaluation | **Not available — not inspected** |

## 2. Structural checks

| Check | Command or method | Result |
|---|---|---|
| Frontmatter | First and eighth lines are `---`; `name`, `description`, `metadata.version` present | PASSED |
| Version | `version: "3.2"` | PASSED |
| Size ceiling | `(Get-Item).Length` ≤ 49,152 | PASSED — 49,136 (16 bytes spare) |
| Word count | Whitespace split | 7,173 words |
| Section references | Extract `§N[.M]`; compare with headings | PASSED — 17 unique refs, 0 unresolved |
| Table consistency | Pipe count per contiguous table block | PASSED — 0 inconsistent blocks |
| Duplicate headings | Group headings by text | PASSED — none |
| Code fences | Count lines starting with three backticks | PASSED — 6 lines, 3 pairs |
| Stale vocabulary | Search `READY WITH ASSUMPTIONS`, old status pointer | PASSED — none |
| Stale install path | Search `S-Skill-v3.1.md` | PASSED — rollback reference only |
| Earlier versions untouched | SHA256 of `S-Skill-v3.1.md` | PASSED — matches pre-work hash |

## 3. Coverage of the brief

The weakness-to-section map is in `CHANGELOG-v3.2.md` Part 2. Every brief item A–P has a destination and a completion check. Items recorded as partially covered:

- **A** inspection: completed for this repository; the Study Buddy plan was unavailable.
- **O** validation: three scenarios are tabletop, not model runs.
- **P** deliverables: produced except a controlled outcome experiment.

## 4. Regression checks — nine v3.1 behaviors

| # | Behavior | Probe | Result |
|---|---|---|---|
| R1 | Six non-negotiables | §3.1–§3.6 headings present | PASSED |
| R2 | ADHD contract | §4 and five-item cap present | PASSED |
| R3 | Mode proportionality | Quick, Standard, Project; "Quick never skips security" | PASSED |
| R4 | Handoff artifacts | §7.1; PRD and acceptance files named | PASSED |
| R5 | Eight-stage lifecycle | Stage 1 and stage 8 rows present | PASSED |
| R6 | Root-cause debugging | Iron law, containment, retry wording | PASSED |
| R7 | Completion statuses | `VERIFIED`, `FAILED`, `NOT TESTED`, `PARTIALLY VERIFIED` | PASSED |
| R8 | OpenCode guide | Install, schema table, activation check | PASSED |
| R9 | Plan drift and user work | §7.7; "Never overwrite user changes" | PASSED |

## 5. Tabletop scenarios

### Scenario 1 — RAG application, auth, vector search, free-tier hosting

| Requirement | v3.2 path | Reached |
|---|---|---|
| Host limits and free-tier facts | §7.2 evidence rows; §11.1 items 1–2, 10 | Yes |
| Serverless async does not survive the response | §11.1 last paragraph → §11.5 | Yes |
| Embedding model and dimension compatibility | §11.1 vector paragraph; §11.3 RAG paragraph | Yes |
| Child tables, chunks, citations, storage | §11.2 resource list and negative tests | Yes |
| Privileged server client | §11.2 third paragraph | Yes |
| Provider fallback and privacy | §11.3 fallback paragraph | Yes |
| Ingestion job recovery | §11.5 completion checks | Yes |
| RAG quality and document injection | §11.6 dataset | Yes |
| Deployment proof | §11.7 | Yes |
| Requirement evidence | §7.4 six-column matrix | Yes |

**Result:** every brief requirement is reachable. Residual: no numeric accuracy threshold is prescribed, by design.

### Scenario 2 — small frontend-only project

- Mode is Quick. §2 matrix skips database, AI, secrets, jobs, RAG, and deployment artifacts.
- Only claims that affect cost, security, or feasibility need an evidence row.
- No handoff documents; §7.2 is checked inline.

**Result:** adds at most one table row and one compatibility check. No Project-level ceremony.

### Scenario 3 — intermittent failure

- §8 is unchanged: reproduce, instrument, hypothesize, change one variable, respect retry limits.
- §7.6 now records the failed hypothesis and its evidence and resumes from the last verified checkpoint.
- §9 requires reporting what was not tested.

**Result:** no conflict with the iron law; one extra record field.

## 6. Contradiction and duplication scan

| Potential conflict | Finding |
|---|---|
| `NOT READY` vs `BLOCKED` | Different scopes: project readiness versus stage or requirement status. Stated in §7.2 and §7.4 |
| Three readiness states vs eight matrix statuses | Different objects; cross-references only |
| Quick "Skip" vs "Quick never skips security" | Skip means no artifact; the rule still applies. Stated under the §2 table |
| Evidence register vs research rules | §10 now points to §9.1 instead of repeating it |
| 36 KiB target vs 49,152-byte ceiling | README updated; the old target is historical |
| "Queue not required" vs "durable job" | A durable job may be a database-backed state machine, not a queue |
| §11.1 completion "READY WITH BLOCKERS" vs §7.2 | Same vocabulary, same meaning |
| New gates vs Quick mode | §2 matrix is the single proportionality rule |

No unresolved contradiction found.

## 7. Duplicate-rule scan

Searched for repeated normative statements: "proportionate", "never invent", "do not assume", "official source". The only repetitions are deliberate cross-references from §3.5, §7.2, and §10 to §9.1. No rule is stated twice with different obligations.

## 8. Installation and activation evidence

| Step | Evidence | Status |
|---|---|---|
| Previous installed version | `SKILL.md` SHA256 `934961DC…AD7E`, 36,859 bytes (v3.1) | OBSERVED |
| Copy to skill directory | `Copy-Item S-Skill-v3.2.md → %USERPROFILE%\.config\opencode\skills\shiva-skill\SKILL.md` | RAN |
| Hash match source/installed | Both `D68E253A52B299FBA1583E1F94DA81764C83E211CBC30653DFA7A2A2B763D1B8` | VERIFIED |
| Size match | Both 49,136 bytes | VERIFIED |
| Skill discovery and load | `skill` tool returned the body titled `SHIVA-SKILL v3.2`, including §9.1 and §11.1–11.7 | VERIFIED |
| Fresh-session canary | Requires a newly started session by the user | NOT TESTED |

The load above proves the installed file is discoverable and parsed as a skill. It does not prove a new session applies every rule; that is the pending canary.

Rollback: copy `S-Skill-v3.1.md` over `SKILL.md` (hash `934961DC…AD7E`), then start a new session.

## 9. Honest limitations

1. **Tabletop is not behavioral proof.** Scenarios show the rule exists and is reachable; they do not show a model applies it.
2. **No A/B run.** v3.1 and v3.2 were not compared on identical tasks.
3. **Size headroom is 16 bytes.** Any future addition requires compressing an existing passage first.
4. **Provider and hosting facts were not re-verified.** v3.2 deliberately contains no quota, price, or model claim, so no external claim is asserted.
5. **Activation is not yet canaried in a fresh session** at the time this file was written.
6. **Small sample.** The next experiment cannot establish statistical significance at the proposed size.
7. **Line endings.** The repository has `core.autocrlf=true` and no `.gitattributes`. A CRLF checkout would make the file about 49,873 bytes, above the approved ceiling; the ceiling is met as stored (LF). Add `*.md text eol=lf` or treat the limit as LF-normalized before committing.

## 10. Recommended next experiment

**Question:** does v3.2 reduce unsupported claims and false completion without increasing cost?

| Element | Design |
|---|---|
| Arms | v3.1 vs v3.2, same model, tools, repository state, and time limit |
| Tasks | (1) RAG plan with auth and free-tier hosting; (2) small frontend; (3) intermittent bug |
| Pre-registration | Freeze prompts, tasks, and scoring before the first run |
| Scoring | From artifacts, not self-report |
| Metrics | Unsupported external claims; missing gate coverage; false completion; first-pass verification; total tokens |
| Sample | 3 tasks × 2 arms as a pilot; repeat to at least 6 per arm before any comparative claim |
| Reporting | All runs, including failures; descriptive statistics only |

Until that runs, the honest claim is: **v3.2 is structurally validated and closes the specified gaps; it is not proven to improve outcomes.**

## 11. Release checklist

- [x] Source inspected before editing
- [x] v3.1 and earlier preserved byte-identical
- [x] Size within approved ceiling
- [x] References, tables, and fences valid
- [x] Regression checks passed
- [x] Three scenarios walked through
- [x] Installed and hash-verified
- [x] Skill body loaded through the `skill` tool as v3.2
- [ ] Fresh-session canary run by the user
- [ ] Commit or push (not requested)
