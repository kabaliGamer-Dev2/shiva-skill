# Shiva-Skill

A single-file engineering and delivery protocol for AI coding agents (OpenCode, Claude Code, Codex, and similar). It defines how the assistant plans, hands off, implements, debugs, verifies, communicates, and reports software work.

**Current version:** `S-Skill-v3.2.md` (v3.2, 2026-10-19)

**Previous versions:** `S-Skill-v3.1.md` (v3.1), `S-Skill-v3.md` (v3.0), `S-Skill-v2.md` (v2.0), and `S-Skill.md` (v1.0), kept for comparison and rollback.

## What v3.2 changes

- Adds an external evidence register (§9.1) with source, date, scope, and `VERIFIED` / `ASSUMED` / `UNVERIFIED` / `CONTRADICTED` status.
- Adds an architecture compatibility gate (§11.1) covering runtime, hosting limits, auth seams, API contracts, AI limits, vector dimensions, streaming, and deployment differences.
- Adds a database isolation gate (§11.2) for every user-owned resource, including child tables, vector functions, storage, and privileged clients, with negative tests.
- Adds AI provider and embedding contracts (§11.3), fallback prohibitions, dimension checks, and re-embedding rules.
- Adds a secrets and encryption lifecycle (§11.4), a durable background-processing gate (§11.5), RAG quality evaluation (§11.6), and deployment verification (§11.7).
- Strengthens readiness with three outcomes, a blocker table, and partial-start rules (§7.2); traceability gains design and task columns, eight statuses, and waiver rules (§7.4).
- Adds a gate-by-mode matrix (§2) so Quick work does not inherit Project-level ceremony.

v3.1's handoff contract, eight-stage lifecycle, integration matrix, checkpoints, debugging rules, evidence honesty, and ADHD communication contract are preserved. `READY WITH ASSUMPTIONS` is retired; assumptions live in the evidence register.

## Files

| File | Purpose |
|---|---|
| `S-Skill-v3.2.md` | Current self-contained protocol; also usable as `SKILL.md` |
| `OPENCODE-GUIDE.md` | Install, activate, configure, update, and troubleshoot in OpenCode |
| `HANDOFF-TEMPLATE.md` | Reusable ChatGPT → OpenCode artifact, evidence, readiness, and gate template |
| `VERIFICATION-CHECKLIST-v3.2.md` | Structural checks, regression checks, tabletop scenarios, limits, and pilot |
| `CHANGELOG-v3.2.md` | v3.1-to-v3.2 change record, weakness map, and preserved rules |
| `S-Skill-v3.1.md` | Previous version, preserved for rollback |
| `S-Skill-v3.md` | Older version, preserved for rollback |
| `S-Skill-v2.md` | Older version, preserved for rollback |
| `S-Skill.md` | Initial version, preserved for rollback |

The v3.1 documents `CHANGELOG-v3.1.md` and `VERIFICATION-CHECKLIST.md` remain as historical records.

## Recommended install: OpenCode skill on demand

The skill body loads only when needed, so it does not consume context every session.

```powershell
$skillDir = Join-Path $HOME ".config\opencode\skills\shiva-skill"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item .\S-Skill-v3.2.md (Join-Path $skillDir "SKILL.md") -Force
```

Append a trigger to the existing global `AGENTS.md`; do not overwrite it:

```powershell
$agents = Join-Path $HOME ".config\opencode\AGENTS.md"
Add-Content -Path $agents -Value '- For multi-step coding, planning, debugging, review, or handoff work, load the `shiva-skill` skill before acting.'
```

Start a new session. Mention `@shiva-skill` or let the task description load it. See `OPENCODE-GUIDE.md` for project installs, activation checks, permissions, and rollback.

For an always-loaded install, append the skill text to `AGENTS.md` and remove the YAML frontmatter. Do not replace an existing instruction file.

### Other agents

- Claude Code: `~/.claude/CLAUDE.md` or a project `CLAUDE.md`.
- Codex: `~/.codex/AGENTS.md` or project instructions.
- OpenCode: prefer the skill directory above; `AGENTS.md` is the always-loaded alternative.

## Size and context

v3.2 is 49,136 bytes and 7,173 words, 16 bytes under the approved 48 KiB (49,152-byte) ceiling. The on-demand skill avoids paying the full context cost every session. If installed in an always-loaded instruction file, check the host’s instruction limit; Codex’s default cap includes project instructions. The size ceiling rose from 36 KiB in v3.1 because seven domain gates were added; the §2 mode matrix keeps small tasks from paying for them.

## Sections

| # | Section |
|---|---|
| 1 | Scope and precedence |
| 2 | Mission, modes, and success criteria |
| 3 | Six non-negotiables |
| 4 | Communication contract (ADHD) |
| 5 | Reasoning method |
| 6 | Planning-first product intelligence |
| 7 | Handoff, readiness, and staged delivery |
| 8 | Debugging, retries, and stop conditions |
| 9 | Evidence, status, honesty, and completion |
| 10 | Reviews and research |
| 11 | Engineering, security, and failure modes |
| 12 | Tools, skills, memory, resources |
| 13 | OpenCode operating guide |
| 14 | Final quality gate |
| 15 | References |

## Validation status

v3.2 has been checked structurally: frontmatter, size ceiling, section references, table consistency, duplicate headings, duplicate rules, contradictions, nine preserved behaviors, and three tabletop scenarios. It has not been evaluated in a controlled task-level A/B run, so it is not claimed to be proven to reduce failures. See `VERIFICATION-CHECKLIST-v3.2.md` for the checks, limits, and pilot protocol.

## Version history

| Version | File | Date | Notes |
|---|---|---|---|
| 3.2 | `S-Skill-v3.2.md` | 2026-10-19 | Evidence register, compatibility, database isolation, AI embeddings, secrets, durable jobs, RAG evaluation, deployment verification |
| 3.1 | `S-Skill-v3.1.md` | 2026-10-19 | Handoff contract, readiness gate, staged delivery, checkpoints, integration testing, measurable completion, OpenCode guide |
| 3.0 | `S-Skill-v3.md` | 2026-10-19 | Planning-first product intelligence, traceability, outcome measurement |
| 2.0 | `S-Skill-v2.md` | 2026-10-19 | Merge with Strict Engineering Protocol; deduplicated; references verified |
| 1.0 | `S-Skill.md` | 2026-10-19 | Initial global personalization prompt |

## License

No license specified yet.
