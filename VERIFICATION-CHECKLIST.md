# SHIVA-SKILL v3.1 — Verification Checklist

**Date:** 2026-10-19  
**Baseline:** `S-Skill-v3.md` (31,023 bytes, 4,555 words)  
**Candidate:** `S-Skill-v3.1.md` (36,859 bytes, 5,379 words)  
**Local OpenCode:** v2.0.32  
**Status:** Structural, documentation, tabletop validation, and two OpenCode activation canaries complete. No full task-level behavioral evaluation or A/B comparison has been run.

---

## 1. What was verified

| Check | Method | Result |
|---|---|---|
| Frontmatter parses | PyYAML 6.0.3 | Pass |
| Skill name is valid | Regex `^[a-z0-9]+(-[a-z0-9]+)*$` | Pass |
| Description present and within limit | Length check | Pass (280 characters) |
| Metadata values are strings | Type check | Pass |
| 15 numbered sections | Heading scan | Pass |
| All `§` references resolve | Reference-to-heading comparison | Pass |
| Markdown tables have consistent columns | Table block scan | Pass |
| No `TODO`, `TBD`, `lorem`, or `placeholder` | Text search | Pass |
| External references return HTTP 200 | HEAD requests on 2026-10-19 | Pass (7/7) |
| v3 rollback copy untouched | File inspection | Pass |
| Companion deliverables exist | File inspection | Pass |
| OpenCode activation canary | `opencode run` in a temporary project, 2 runs | Pass |

### Size result

- 36,859 bytes, 5 bytes under the 36 KiB target.
- 5,379 words, close to the ~5,400 target.
- Compared with v3: +824 words (+18.1%) and +5,836 bytes.
- The increase is concentrated in the new handoff/readiness/lifecycle/OpenCode material. Duplication was removed elsewhere.

---

## 2. Brief coverage

| Requirement | Where it is addressed | Result |
|---|---|---|
| P1 handoff artifact contract | §7.1; `HANDOFF-TEMPLATE.md` | Pass |
| P1 requirements traceability | §7.4 and §9 completion table | Pass |
| P1 readiness gate | §7.2; `READY` / `READY WITH ASSUMPTIONS` / `BLOCKED` | Pass |
| P1 staged implementation with exit gates | §7.3, eight stages | Pass |
| P1 checkpoint and recovery | §7.6; resume record in template | Pass |
| P1 integration and regression testing | §7.5 boundary matrix | Pass |
| P2 OpenCode operating guide | §13; `OPENCODE-GUIDE.md` | Pass |
| P2 planning and implementation coordination | §6.1, §6.3, §7.7 | Pass |
| P2 debugging emergency and retry clarity | §8 emergency containment, retry policy, stop signals | Pass |
| P2 measurable completion | §9 statuses, table, completion rules | Pass |
| Preserve ADHD communication | §4 | Pass |
| Preserve evidence honesty | §3.1, §3.5, §3.6, §9 | Pass |
| Preserve minimal changes and user work | §3.2, §3.4, §7.6 | Pass |
| Preserve security | §11, §13.5 | Pass |
| Preserve root-cause debugging | §8 iron law and four phases | Pass |
| Preserve resource awareness | §12 resources | Pass |
| Preserve truthful reporting | §3.6, §9, §14 | Pass |
| Keep small tasks lightweight | §2 Quick mode; §7.1 scaled artifacts | Pass |
| Avoid unnecessary documents/agents/dependencies/tests | §2, §3.4, §7.1, §12 | Pass |
| Do not promise 100% success | §9 and this checklist | Pass |

### Minor compression note

v3’s standalone TDD bullet was not retained verbatim. The failing-test discipline remains in §8 phase 4, and v3.1 adds “Use TDD where practical” in §11. This is a compression, not a removed capability.

---

## 3. Section-by-section comparison

| v3 section | v3.1 section | Change | Result |
|---|---|---|---|
| Operating loop | Operating loop | Compressed to five steps | Preserved |
| 1 Scope | 1 Scope | Removed duplicated product-scope paragraph; clarified OpenCode `AGENTS.md` merging | Improved |
| 2 Mission | 2 Mission, modes | Added Quick/Standard/Project selector; compressed depth guidance | Improved |
| 3 Six non-negotiables | 3 Six non-negotiables | Preserved; tightened inspection and completion wording | Preserved |
| 4 Communication | 4 Communication | Preserved ADHD rules; removed low-value repetition | Preserved |
| 5 Reasoning | 5 Reasoning | Preserved phases; merged delivery into validation; condensed | Preserved |
| 6 Product intelligence | 6 Planning-first product intelligence | Added mandatory/optional scope, expensive-to-reverse decisions, data/interface boundaries; merged approval into evaluation | Improved |
| 7 Canonical workflow | 7 Handoff, readiness, staged delivery | Replaced with artifact contract, gate, eight stages, traceability, integration, checkpoints, drift | Improved |
| 8 Debugging | 8 Debugging | Added emergency containment; clarified retry and stop rules | Improved |
| 9 Evidence | 9 Evidence, status, completion | Added completion report and status rules | Improved |
| 10 Reviews/research | 10 Reviews/research | Preserved; compressed priority definitions | Preserved |
| 11 Engineering/security | 11 Engineering/security/failure modes | Added dependency/supply-chain and data/migration checks; retained security | Improved |
| 12 Tools/skills/resources | 12 Tools/skills/resources | Preserved; trimmed duplicate resource advice | Preserved |
| 13 Final gate | 14 Final gate | Reduced to 14 evidence-oriented checks | Improved |
| 14 References | 15 References | Kept; links checked | Preserved |
| Final principle | Final principle | Compressed | Preserved |
| — | 13 OpenCode guide | New; verified against official v2 docs | Added |

No v3 section is missing. The canonical workflow was replaced rather than duplicated. The numbering changed because §13 is new and the final gate moved to §14.

---

## 4. OpenCode claim verification

Sources checked on 2026-10-19:

- <https://opencode.ai/v2/docs/skills>
- <https://opencode.ai/v2/docs/instructions>
- <https://opencode.ai/v2/docs/config>
- <https://opencode.ai/v2/docs/permissions>
- <https://opencode.ai/docs/agents> (v1)
- <https://opencode.ai/docs/skills> (v1)

| Claim | Evidence | Result |
|---|---|---|
| Global skills path is `~/.config/opencode/skills` | v2 skills docs | Verified |
| Project skills path is `.opencode/skills` | v2 skills docs | Verified |
| The file must be named `SKILL.md` | v2 skills docs | Verified |
| The directory/path supplies the skill ID | v2 skills docs | Verified |
| A description is needed for model discovery | v2 skills docs | Verified |
| `@skill-id` loads a skill explicitly | v2 skills docs | Verified |
| Project skills override global skills with the same ID | v2 skills docs precedence table | Verified |
| `AGENTS.md` files are combined, not conflict-resolved | v2 instructions docs | Verified |
| OpenCode v2 does not use `CLAUDE.md` as a fallback | v2 instructions docs callout | Verified |
| Config `instructions` load after `AGENTS.md` | v2 instructions docs ordering | Verified |
| v2 uses `permissions` array, `agents`, `shell`, `subagent` | v2 permissions/config docs | Verified |
| v1 uses `permission` object, `agent`, `bash`, `task` | v1 agents/config docs | Verified |
| Skill permissions use the `skill` action and ID | v2 skills/permissions docs | Verified |
| `opencode debug config` shows sources, not loaded text | Local check; docs do not expose a loaded-body printer | Verified as a limitation |
| `metadata.opencode/autoinvoke: false` hides a skill from the model list | v2 skills docs | Verified |
| Compatibility paths include `.claude/skills` and `.agents/skills` | v2 skills docs | Verified |
| Project skill is discovered and loaded | Canary run 1, explicit `@shiva-skill` | Verified |
| `AGENTS.md` trigger loads the skill without `@` | Canary run 2 | Verified |
| Global skill path install | Documentation only | Documented, not executed |

The guide does not claim that a file on disk proves loading. It uses a behavioral canary.

### Activation canary (executed)

Environment: OpenCode v2.0.32 on Windows; temporary project with `.opencode/skills/shiva-skill/SKILL.md` and an `AGENTS.md` trigger; model `opencode/deepseek-v4.1-flash-free`.

**Run 1 — explicit mention:**

```powershell
opencode run --standalone --auto --model opencode/deepseek-v4.1-flash-free "Load @shiva-skill. ..."
```

Observed: the tool line `Skill "shiva-skill"` appeared; the model returned the six non-negotiables, `Standard` mode, the Discovery stage and its exit gate, and §3.6 as the status section.

**Run 2 — AGENTS trigger, no explicit `@` mention:**

```powershell
opencode run --standalone --auto --model opencode/deepseek-v4.1-flash-free "Do not edit files. Follow the project AGENTS.md. ..."
```

Observed: the tool line `Skill "shiva-skill"` appeared; the model returned the six rules and identified §3.6/§9 for completion statuses.

**Result:** pass for project-scoped discovery, explicit loading, and the `AGENTS.md` trigger. Limits: one model, one prompt per run, and a canary response — not a task-level compliance evaluation. The global install path was documentation-verified, not executed.

---

## 5. Scenario tabletop

These are rule-tracing walkthroughs, not executions. “Pass” means the skill gives a clear decision path with evidence and a stop condition.

| Scenario | Expected path | Result | Gap / note |
|---|---|---|---|
| Small one-file bug fix | Quick mode; inspect; smallest change; targeted check; no handoff files | Pass | Completion table optional for Quick |
| Multi-file feature in one service | Standard; one short spec; readiness; vertical slices; integration; completion report | Pass | Project still needs full artifacts |
| ChatGPT plan handed to OpenCode | Export artifacts; fresh session; readiness gate; compare paths/stack/versions; plan drift | Pass | Requires the user to export artifacts, not chat scrollback |
| Missing environment variables | §7.2 identifies names; missing required value blocks; no secrets requested; fallback if non-blocking | Pass | Skill cannot discover a secret the user withholds |
| Conflicting requirements | §1 precedence; §6.3 contradictions; §7.7 drift; §8 stop and ask | Pass | User must resolve product-level conflict |
| Failed build | Foundation exit gate fails; §8 root cause; §7.6 checkpoint; `FAILED`; no dependent work | Pass | Build command must exist in repo/toolchain |
| Incompatible API contract | Conditional API artifact; §7.5 contract checks; §7.7 change; re-approve if scope changes | Pass | External API may be undiscoverable without credentials |
| Database permission error | §7.2 environment constraint; §7.5 migration check; §8 classify permissions; §11 data safety | Pass | Actual DB access depends on user environment |
| Broken integration | §7.5 boundary matrix; instrument boundary; `NOT TESTED` for skipped checks; checkpoint | Pass | No substitute for running the integration |
| Regression after a change | §3.4 preserve; §7.5 critical journeys; §7.6 last-known-good; §8 diagnosis; §9 status | Pass | Regression suite must exist or be built |
| Production outage / data-loss risk | §8 emergency containment; smallest reversible action; record; label `CONTAINED, NOT FIXED`; resume root cause | Pass | Emergency action still needs authorization |
| Plan drift after new evidence | §7.7 stop, state conflict, smallest change, update artifacts, re-approve if material | Pass | User availability may delay blocking changes |
| Context loss / resumed session | §7.6 resume record + `git status`; restate state; preserve user work | Pass | Record must have been written |

### Scenario conclusion

The rules cover the required failure cases. The tabletop found no dead end, but it cannot prove that a model will follow the rules under pressure. That requires the pilot below.

---

## 6. Contradiction and duplication scan

| Potential issue | Finding |
|---|---|
| “No fix without root cause” vs emergency containment | §8 explicitly limits containment to active outage, data loss, security exposure, or user-blocking production failure; root-cause work must resume |
| “Two attempts per identical failure” vs “three failed fixes” | Different counters: identical retries vs distinct attempted fixes. The first limits repetition; the second triggers architectural reassessment |
| Quick mode vs required artifacts | Quick explicitly skips handoff files; Standard may combine artifacts; Project uses the full set |
| “Do not enter next stage” vs “small tasks may collapse stages” | Collapsing stages is allowed; skipping verification is not |
| Project skill vs global skill | Project source has higher precedence; the guide says use one source of truth |
| v3/v2/v1 config schemas | Explicitly separated in a table; “do not mix schemas” |
| OpenCode combines `AGENTS.md` vs precedence | §1 states the conflict and the higher rule; it does not silently blend |

No unresolved contradiction was found in the document.

---

## 7. Honest limitations

1. **Limited behavioral evaluation.** Two activation canaries ran; no task-level evaluation was run against representative tasks.
2. **No A/B comparison.** v3 and v3.1 were not run on the same tasks, repository, model, and tools.
3. **Tabletop is not proof.** The scenarios check that a rule exists and is reachable, not that a model applies it correctly.
4. **OpenCode docs change.** Paths and schemas were verified for v2.0.32 on 2026-10-19; re-check for another version.
5. **No loaded-text CLI.** The canary is behavioral evidence, not a cryptographic guarantee that the full body was received.
6. **No global installation performed.** Project-scoped loading was tested in a temporary directory; the global path was documentation-verified, not executed.
7. **Instruction length is not free.** v3.1 is ~6 KB larger than v3; always-loaded installation costs more context than on-demand skill loading.

The honest claim is: **v3.1 is structurally complete, passed two activation canaries, and is designed to detect and recover from the identified failure modes earlier. It is not proven to reduce failures.**

---

## 8. Optional pilot: v3 vs v3.1

Run only if a measured claim is needed. Keep the same repository state, model, tools, time limit, and task prompts for both versions.

### Suggested tasks

1. Small bug fix with a reproduction test.
2. Multi-file feature with a hidden acceptance criterion.
3. ChatGPT plan with one stale path and one outdated version.
4. Missing environment variable or unavailable service.
5. API contract mismatch between frontend and backend.
6. Regression after a change.

### Metrics

| Metric | Definition |
|---|---|
| First-pass verification | Acceptance criteria verified without a repair cycle |
| Preventable failures | Failures caused by skipped inspection, stale assumptions, or missing integration |
| False completion | Claimed complete with a mandatory criterion `FAILED`, `BLOCKED`, or `NOT TESTED` |
| Recovery quality | Correct containment, root cause, and resume record after a failure |
| Token / tool cost | Total tokens and tool calls per completed task |
| Time to verified outcome | Wall-clock time to evidence-backed completion |
| Unrelated changes | Files changed outside the task scope |

### Pilot rules

- Pre-register the tasks and scoring.
- Use the same model and tool permissions for both arms.
- Randomize order to reduce learning effects.
- Score from artifacts, not from the model’s self-report.
- Report all runs, including failures and abandoned runs.
- With a small sample, report descriptive results only; do not claim statistical significance.

Until this is run, no failure-reduction claim is supported.

---

## 9. Release checklist

- [x] `S-Skill-v3.1.md` exists and is self-contained.
- [x] Frontmatter parses and the skill can be copied to `SKILL.md`.
- [x] v3, v2, and v1 remain available for rollback.
- [x] Changelog and ranked review exist.
- [x] OpenCode guide exists and cites verified docs.
- [x] Handoff template exists.
- [x] Verification checklist exists.
- [x] README describes v3.1 and does not overclaim.
- [x] OpenCode activation canary passed (project-scoped, 2 runs).
- [ ] Empirical pilot completed (not done; optional).
- [ ] A/B failure-reduction claim approved by evidence (not done; do not claim).

**Verdict:** Ready for design review and controlled use. Activation is verified for the tested project setup; failure reduction is not proven.
