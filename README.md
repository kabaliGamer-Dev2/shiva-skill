# Shiva-Skill

A single-file global AI personalization prompt for AI coding agents (Claude Code, OpenCode, Codex, and similar). It defines how the assistant reasons, frames products, communicates, investigates, debugs, engineers, and verifies work in every conversation.

**Current version:** `S-Skill-v3.md` (v3.0, 2026-10-19)
**Previous versions:** `S-Skill-v2.md` (v2.0) and `S-Skill.md` (v1.0), kept for comparison and rollback.

## What v3 changes

- Adds planning-first product intelligence: challenge the idea, define the product, evaluate independently, approve before major implementation, trace requirements, and measure outcomes.
- Adds a one-screen product brief: problem and audience, requirements and acceptance tests, non-goals, journeys, success metrics, constraints, assumptions and risks, alternatives, and feasibility.
- Adds three proof standards: a polished PRD is not proof of feasibility; a successful build is not proof of product correctness; a plausible AI-generated review is not proof that its findings are true.
- Integrates the product gates into the existing workflow instead of adding a second process.
- Adds requirement traceability: requirement → acceptance test → verification evidence.
- Adds outcome measurement against a baseline before and after implementation.
- Keeps v2's strict engineering, evidence, debugging, security, and ADHD communication rules.
- Preserves the self-contained design: no external skill pack, MCP server, or repository is required.

## v3 sections

| # | Section |
|---|---------|
| 1 | Scope and precedence |
| 2 | Mission and success criteria |
| 3 | Six non-negotiables |
| 4 | Communication contract (ADHD) |
| 5 | Reasoning method |
| 6 | Planning-first product intelligence |
| 7 | Canonical workflow |
| 8 | Debugging, retries, and stop conditions |
| 9 | Evidence, status, and honesty |
| 10 | Reviews and research |
| 11 | Engineering, security, and failure modes |
| 12 | Tools, skills, memory, resources |
| 13 | Final quality gate |
| 14 | References |

## Usage

1. Copy `S-Skill-v3.md` into your agent's global instructions location, or paste it as a system prompt.
   - Claude Code: `~/.claude/CLAUDE.md`
   - OpenCode: `~/.config/opencode/AGENTS.md`
   - Codex: `~/.codex/AGENTS.md`
2. Start a new conversation. The rules apply automatically; no activation phrase is needed.
3. To disable ADHD formatting, say `normal mode` or `stop ADHD mode`.

Project-specific instructions (`AGENTS.md`, `CLAUDE.md`, `CONTRIBUTING.md`) take precedence over this file for work in that project. Platform and safety instructions take precedence over both.

**Size note:** v3 is about 30 KB. Codex's default 32 KiB instruction cap includes project instructions; if you install it as project instructions alongside a large `AGENTS.md`, raise `project_doc_max_bytes` or keep it as a global instruction file.

## Version history

| Version | File | Date | Notes |
|---------|------|------|-------|
| 3.0 | `S-Skill-v3.md` | 2026-10-19 | Adds planning-first product intelligence, traceability, and outcome measurement |
| 2.0 | `S-Skill-v2.md` | 2026-10-19 | Merge with Strict Engineering Protocol; deduplicated; references verified |
| 1.0 | `S-Skill.md` | 2026-10-19 | Initial global personalization prompt |

## Previous versions

`S-Skill-v2.md` and `S-Skill.md` remain in the repository for comparison and rollback. Their section tables were removed from this README to keep it focused on the current version.

## License

No license specified yet.
