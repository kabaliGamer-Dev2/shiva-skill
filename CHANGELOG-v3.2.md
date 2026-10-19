# SHIVA-SKILL v3.2 — Review and Changelog

**Baseline:** `S-Skill-v3.1.md` (36,859 bytes, 5,379 words, SHA256 `934961DC…AD7E`)  
**Result:** `S-Skill-v3.2.md` (49,136 bytes, 7,173 words, SHA256 `D68E253A…D1B8`)  
**Date:** 2026-10-19  
**Status:** Structural and tabletop validation complete. No task-level A/B evaluation. Not proven to reduce failures.

---

## Part 1 — What was weak

The v3.2 brief identified weaknesses from a separate Study Buddy planning evaluation. That evaluation was **not available in this repository and was not independently reproduced**. The items below are treated as requirements, not as verified findings.

| # | Weakness | Verdict against v3.1 |
|---|---|---|
| 1 | Claims about hosting, quotas, pricing, and model limits lacked source, date, and scope | Partial — §3.5, §9, §10 required honesty but no register |
| 2 | Components were evaluated separately; compatibility was not checked | Absent |
| 3 | RLS was described but not designed or tested | Thin — one line in §11 |
| 4 | Multi-provider AI and embedding compatibility were unspecified | Absent |
| 5 | Secret storage had no encryption or rotation lifecycle | Thin |
| 6 | Background work assumed to survive the request | Absent |
| 7 | RAG quality was not evaluated beyond output presence | Absent |
| 8 | Traceability lacked design/task columns and waiver rules | Partial — §7.4 |
| 9 | Readiness had no blocker table or partial-start rule | Partial — §7.2 |
| 10 | Phase exit criteria were implied, not recorded | Mostly present — §7.3, §7.6 |
| 11 | Deployment was not distinguished from a local build | Partial — stage 8 |
| 12 | Final reports omitted inspection, external claims, and next action | Mostly present — §9 |
| 13 | New rigor risked bloat and ceremony | Adequate — §2 modes, §4 |

## Part 2 — Weakness-to-section map

| Brief | Weakness | v3.2 location | Completion check |
|---|---|---|---|
| A | Pre-edit inspection | This changelog, Part 1; `VERIFICATION-CHECKLIST-v3.2.md` §1 | Inspection list present |
| B | External evidence | §9.1 register; §3.5 hook; §10 dedupe | Row with source, date, scope, status |
| C | Architecture compatibility | §11.1 | Each seam has evidence or a POC test |
| D | Database security | §11.2 | Policies for every resource; negative tests pass |
| E | AI provider and embeddings | §11.3 | Contract tests; dimension-mismatch test fails |
| F | Secrets lifecycle | §11.4 | Rotation/deletion tested or `NOT TESTED` |
| G | Durable jobs | §11.5 | Success, forced retry, duplicate submission |
| H | RAG evaluation | §11.6 | Dataset, baseline, comparison run |
| I | Traceability | §7.4 | Six-column matrix; waivers justified |
| J | Readiness | §7.2 | One of three outcomes; blocker table |
| K | Checkpoints | §7.3 phase contract; §7.6 failed-hypothesis record | Contract fields recorded per slice |
| L | Deployment | §11.7 | Deployed smoke test or recorded blocker |
| M | Reporting | §9 completion report fields | Inspection, claims, gaps, next action |
| N | Efficiency | §2 gate-depth matrix | Gate depth matches mode |
| O | Skill validation | §13.3 pointer; `VERIFICATION-CHECKLIST-v3.2.md` | Three scenarios + regression list |
| P | Deliverables | This file; checklist; README; template; guide | Files exist and agree |

## Part 3 — What changed

| Area | v3.2 change | Failure addressed |
|---|---|---|
| Metadata | Version 3.2; header states the new gates | Version drift |
| §2 | Added gate-depth-by-mode table | Ceremony on small work; skipped checks on large work |
| §3.5 | External claims point to §9.1 | Plausible assumptions presented as facts |
| §3.6 | Requirement statuses point to §7.4 | Parallel status vocabularies |
| §7.2 | Three outcomes; blocker table; partial-start rule; free-tier constraints; no unproven ping guarantee | Whole-project paralysis or premature start |
| §7.3 | Eight-field slice contract | Unrecorded exit criteria |
| §7.4 | Six-column matrix; eight statuses; waivers; negative tests | Traceability theater |
| §7.6 | Failed-hypothesis record; resume from last verified checkpoint | Repeated speculative fixes |
| §9 | §9.1 evidence register with four statuses; expanded report fields | Unsupported external claims; incomplete reports |
| §10 | Research rules deduplicated into §9.1 | Repeated instructions |
| §11 | New 11.1–11.7 gates; existing subsections renumbered 11.8–11.14, content preserved | Compatibility, isolation, provider, secret, job, evaluation, and deployment failures |
| §13.1 | Install command targets v3.2 | Stale install path |
| §13.3 | Points to the three-scenario revalidation | Skill changes untested |
| §13.5 | Rollback targets v3.1 | Wrong rollback version |
| §14 | Two checks merged; three added | Checklist did not cover seams, claims, deployment |

### Preserved deliberately

- Six non-negotiables, including "never fabricate" and "inspect before acting".
- ADHD communication contract and the five-item visible-list cap.
- Quick, Standard, and Project modes; Quick still skips documents, not verification.
- Handoff artifacts (§7.1), eight-stage lifecycle, integration matrix, plan drift.
- Root-cause-first debugging, emergency containment, retry limits, stop conditions.
- The five original completion statuses, now a subset of the eight matrix statuses.
- Minimal-change, preservation-of-user-work, dependency, destructive-action, and Git rules.
- Self-contained design: no external skill pack, MCP server, or repository is required.
- OpenCode v1/v2 schema table and activation canary.

### Changed on purpose

- `READY WITH ASSUMPTIONS` removed. Assumptions now belong in the evidence register; readiness answers whether work can start, not whether it is certain.
- `BLOCKED` as a project outcome replaced by `NOT READY`; `BLOCKED` remains a requirement and stage status.
- `PARTIALLY VERIFIED` and `NOT TESTED` are retained, so the brief's six-status list is extended rather than adopted verbatim.

### Not removed

No security, evidence, debugging, minimal-change, or communication rule was deleted. §10 lost two bullets because §9.1 now owns them.

## Part 4 — Gates added

| Gate | Input | Observable completion |
|---|---|---|
| 9.1 Evidence register | External claim | Row has source, date, scope, status |
| 11.1 Compatibility | Architecture | Every seam has evidence or a POC |
| 11.2 Database isolation | User-owned resource | Policies plus passing negative tests |
| 11.3 AI and embeddings | Provider, vector index | Contract tests; mismatch rejected |
| 11.4 Secrets lifecycle | Stored credential | Rotation and deletion tested or flagged |
| 11.5 Durable jobs | Asynchronous work | Retry and duplicate tests |
| 11.6 RAG evaluation | Retrieval or answers | Dataset and baseline recorded |
| 11.7 Deployment | Release claim | Deployed smoke test or blocker |

## Part 5 — Size and trade-offs

v3.2 adds 12,277 bytes and 1,794 words (+33.3%), using 16 bytes of the approved 49,152-byte ceiling.

The increase is concentrated in §11, where seven gates did not exist, and §9.1. Compression offset part of it: §10 was deduplicated, one §14 check was merged, and §11 prose is written as short rules rather than essays.

The trade-off: v3.2 is denser per line. The mitigation is the §2 gate matrix, which keeps Quick work free of the new artifacts. The risk is that a medium task reads as Project work; the "Standard may combine artifacts" rule remains.

## Part 6 — Validation status

| Check | Result |
|---|---|
| v3.1 and earlier files untouched | Yes — v3.1 hash unchanged |
| Frontmatter parses; version and name valid | Passed |
| Single file, 49,152-byte ceiling | Passed — 49,136 bytes |
| Section references resolve | Passed — 17 unique references |
| Table column consistency | Passed — 0 inconsistent blocks |
| Duplicate headings | None |
| Code fences balanced | Passed — 3 pairs |
| Duplicate-rule scan | Passed — no restated rule except pointers |
| Contradiction scan | Passed — table in `VERIFICATION-CHECKLIST-v3.2.md` §6 |
| Three tabletop scenarios | Passed — checklist §5 |
| Nine-behavior regression | Passed — checklist §7 |
| Fresh-session activation canary | Pending user-run; install verified |
| Task-level A/B evaluation | Not run |

## Part 7 — Install and rollback

```powershell
$skillDir = Join-Path $HOME ".config\opencode\skills\shiva-skill"
Copy-Item .\S-Skill-v3.2.md (Join-Path $skillDir "SKILL.md") -Force
```

Rollback: copy `S-Skill-v3.1.md` over `SKILL.md`, or remove the skill directory and the trigger line from `AGENTS.md`.

**Honest conclusion:** v3.2 closes the specified gaps with observable completion checks and passes structural, tabletop, and regression validation. It has not been shown, in a controlled comparison, to reduce implementation failures.
