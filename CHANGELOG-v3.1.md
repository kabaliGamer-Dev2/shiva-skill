# SHIVA-SKILL v3.1 — Review and Changelog

**Baseline:** `S-Skill-v3.md` (v3.0, 31,023 bytes, 4,555 words)  
**Result:** `S-Skill-v3.1.md` (36,859 bytes, 5,379 words)  
**Date:** 2026-10-19  
**Status:** Design review, documentation verification, and tabletop validation only. Not empirically proven to reduce failures.

---

## Part 1 — Ranked review of v3

The ranking is by expected impact on preventable implementation failures, not by document length.

### P1 — Major gaps

**1. No planning-to-implementation handoff contract.**  
v3 §7 starts from an approved idea but never defines what the implementation agent must receive. A ChatGPT plan can contain stale paths, versions, commands, or data assumptions. OpenCode has no required artifact to compare against the repository, so it can start coding on a plan that no longer matches reality.

**2. No readiness gate or staged exit criteria.**  
v3 §7 says to work in small steps and verify, but it does not define when implementation may start, what each stage must produce, or when dependent work is blocked. A failed build or missing service can be treated as an interruption rather than a gate failure.

**3. Requirement traceability and completion are not measurable.**  
v3 §3.6 defines useful statuses, but §9 ends with a prose definition of “done.” There is no required matrix linking requirement → acceptance test → evidence → status. A file can be generated, a server can start, and the work can still be reported as complete without proving the requirement.

**4. Integration and regression testing are under-specified.**  
v3 §7.F lists verification categories but not the boundaries that commonly fail: UI↔API, auth/authz, API contract, database migrations, environment/external services, retries, and critical journeys. Individually working components can be reported as a working product.

**5. Debugging rules are absolute and do not cover containment.**  
v3 §8 correctly forbids symptom fixes, but it has no exception for an active outage, data loss, or security exposure. It also says “two attempts per identical failure mode” without defining a failure mode or explaining how to resume root-cause work after emergency containment.

### P2 — Meaningful gaps

**6. Planning lacks explicit decision discipline.**  
v3 §6 has a strong product brief, but it does not require separating mandatory from optional scope, naming expensive-to-reverse decisions, or defining data and interface boundaries before implementation. Those omissions cause late redesign.

**7. No verified OpenCode operating guide.**  
v3 mentions skills but does not explain installation paths, skill discovery, activation, project overrides, permission schemas, or how to prove the instructions were loaded. A file existing on disk is not evidence that the model received it.

**8. Duplication and an unmeasurable final gate.**  
v3’s canonical workflow overlaps the reasoning method and product brief. The final quality gate is a long checklist without statuses or traceability. The document is usable, but the duplicated process increases reading cost without adding a decision rule.

---

## Part 2 — What changed in v3.1

The revision is targeted. v3’s spine, voice, and core prohibitions remain.

| Area | v3.1 change | Failure addressed |
|---|---|---|
| §1 Scope | Preserved precedence; clarified that OpenCode combines `AGENTS.md` files without resolving conflicts; removed duplicated product-scope paragraph | Silent blending of conflicting instructions |
| §2 Modes | Added Quick, Standard, and Project selector with proportionate ceremony | Heavyweight process on small work; missing rigor on large work |
| §3 Non-negotiables | Preserved all six; tightened inspection, planning, preservation, evidence, and status rules | Fabrication, unverified claims, destructive edits |
| §4 Communication | Preserved ADHD contract; removed low-value repetition and time-estimate rule | Cognitive load without losing safety or clarity |
| §5 Reasoning | Preserved phases; condensed evaluation and tutorial guidance | Bloated reasoning without a decision |
| §6 Planning | Added mandatory vs optional scope, expensive-to-reverse decisions, data/interface boundaries, and unresolved-decision approval; merged duplicate approval section | Late redesign and approval after implementation |
| §7 Delivery | Replaced the generic workflow with a handoff artifact contract, readiness gate, eight-stage lifecycle with exit gates, traceability matrix, integration matrix, checkpoints, and plan-drift protocol | Stale plans, premature coding, lost work, false completion, broken integration |
| §8 Debugging | Preserved root-cause law; added emergency containment, clarified retry budget and stop conditions | Outage delay, blind retries, symptom patching |
| §9 Evidence | Added a completion report with requirement IDs, checks, evidence, status, and notes | “Implemented” reported as “verified” |
| §10 Reviews | Preserved review standard and research rules; compressed priority definitions | Generic reviews and unsupported claims |
| §11 Engineering | Preserved security rules; added dependency/supply-chain and data/migration checks | Typosquatting, unsafe migrations, data loss |
| §12 Tools | Preserved capability honesty, skills, tools, subagents, plan mode, context; trimmed duplicated resource advice | Claimed capabilities and context waste |
| §13 OpenCode | New verified operating guide: install, activation, project overrides, v1/v2 schema table, ChatGPT→OpenCode bootstrap | Instructions present but not loaded; v1/v2 config corruption |
| §14 Gate | Replaced 19 loose questions with 14 evidence-oriented checks | Checklist theater |
| §15 References | Kept source links and the “reference is not installation” warning | Mistaking documentation for capability |

### Removed or merged

- Merged v3 §6.4 “approve before major implementation” into §6.3/§7.2 to avoid a second approval process.
- Removed the repeated “match depth” paragraph and shortened tutorial guidance where §2 and §5 already covered it.
- Removed the standalone traceability table row in §7.4 in favor of the required columns and update rules.
- Did not remove any security, evidence, debugging, or minimal-change rule.

### Preserved deliberately

- ADHD communication contract.
- Six non-negotiables.
- Evidence honesty and the five completion statuses.
- Root-cause-first debugging and retry limits.
- Minimal changes, preservation of user work, and security.
- Small-task proportionality and the ban on unnecessary dependencies, abstractions, documents, and agents.
- Self-contained design: no external skill pack or MCP server is required.

### Size and trade-offs

v3.1 adds about 824 words and 5.8 KB. The increase is concentrated in §7 and §13, where v3 had no operational procedure. Duplication was cut elsewhere. The file is 36,859 bytes (5 bytes under 36 KiB) and 5,379 words; in decimal units it is 36.9 KB.

The trade-off is deliberate: more structure for substantial work, while Quick mode explicitly skips handoff documents. The risk is ceremony on medium tasks; the Standard-mode “one short spec may combine artifacts” rule is the mitigation.

---

## Part 3 — Validation status

| Check | Result |
|---|---|
| v3 preserved for rollback | Yes, `S-Skill-v3.md` untouched |
| Frontmatter parses; name/description valid | Yes |
| 15 numbered sections plus operating loop/final principle | Yes |
| All `§` references resolve | Yes |
| Markdown table columns consistent | Yes |
| External reference URLs return HTTP 200 on 2026-10-19 | Yes |
| OpenCode paths and schemas checked against official v2 docs | Yes |
| Representative scenarios walked through | Yes, tabletop only |
| OpenCode activation canary | Passed, 2 runs (explicit mention and `AGENTS.md` trigger) |
| Full task-level behavioral evaluation | Not run |
| A/B comparison against v3 | Not run |

**Honest conclusion:** v3.1 is structurally complete, addresses the identified gaps, and passed two activation canaries in OpenCode v2.0.32. It is not proven to reduce failures. The verification checklist records the limits and defines a pilot protocol for a later measured comparison.
