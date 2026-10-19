# OpenCode Installation and Activation Guide

**For:** SHIVA-SKILL v3.2  
**Verified against:** OpenCode v2.0.32 locally and the official OpenCode v2 documentation on 2026-10-19.  
**Re-check before relying on this for a different version:** <https://opencode.ai/v2/docs/skills>, <https://opencode.ai/v2/docs/instructions>, <https://opencode.ai/v2/docs/config>.

This guide installs the skill on demand. The skill body is not loaded into every session; only its name and description are advertised until the model or the user loads it.

---

## 1. Recommended install: global skill on demand

### Step 1 — Copy the skill into the global skill directory

Run from the repository root in PowerShell:

```powershell
$skillDir = Join-Path $HOME ".config\opencode\skills\shiva-skill"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item .\S-Skill-v3.2.md (Join-Path $skillDir "SKILL.md") -Force
```

The directory name is the skill ID (`shiva-skill`). The file must be named exactly `SKILL.md`.

### Step 2 — Append a short trigger to the global `AGENTS.md`

Inspect the existing file first. Then append; do not overwrite it.

```powershell
$agents = Join-Path $HOME ".config\opencode\AGENTS.md"
Get-Content $agents -Tail 20
Add-Content -Path $agents -Value '- For multi-step coding, planning, debugging, review, or handoff work, load the `shiva-skill` skill before acting.'
```

If `AGENTS.md` does not exist, `Add-Content` creates it. If it already contains a similar rule, do not add a duplicate.

### Step 3 — Start a new session

OpenCode discovers `~/.config/opencode/skills/shiva-skill/SKILL.md`, advertises its description, and loads the body when the task matches or when you mention `@shiva-skill`.

The global `AGENTS.md` trigger costs one line of context per session. The full skill costs context only when loaded.

---

## 2. Project-scoped install

Use this when the workflow belongs to one repository and should be shared with the team.

```powershell
$skillDir = Join-Path (Get-Location) ".opencode\skills\shiva-skill"
New-Item -ItemType Directory -Force $skillDir | Out-Null
Copy-Item .\S-Skill-v3.2.md (Join-Path $skillDir "SKILL.md") -Force
```

Then add a project `AGENTS.md` trigger, or commit a short instruction in the repository's existing `AGENTS.md`:

```markdown
- For multi-step coding, planning, debugging, review, or handoff work, load `@shiva-skill` before acting.
```

A project skill overrides a global skill with the same ID. Do not keep two different copies unless you intend the override.

OpenCode also discovers compatibility paths such as `.claude/skills`, `.agents/skills`, `~/.claude/skills`, and `~/.agents/skills`. Prefer one source of truth.

---

## 3. Activation check

A file on disk is not proof that the model received its instructions. Start a fresh session and use a behavioral canary:

```text
Without editing files, answer from the loaded shiva-skill:
1. Name the six non-negotiables.
2. Which mode applies to a multi-file feature in one service?
3. What is the first stage of the lifecycle and its exit gate?
4. Which section defines the completion statuses?
```

Expected answers:

1. Never fabricate; inspect before acting; plan before substantial implementation; preserve existing work; evidence before conclusions; never fake completion.
2. Standard.
3. Discovery; the exit gate is a shared understanding of the problem, users, constraints, and risk.
4. §3.6, used by the completion report in §9.

If the model cannot answer, do not assume the skill is active. Check the items below.

In the tested version, `opencode debug config` shows configuration sources, not the loaded `AGENTS.md` or skill text. No verified CLI command prints the loaded body. The canary is the practical check.

A project-scoped canary passed twice in OpenCode v2.0.32 on 2026-10-19, using `opencode/deepseek-v4.1-flash-free`: once with `@shiva-skill` and once through the project `AGENTS.md` trigger. That verifies discovery and loading for this setup; it does not prove consistent compliance under task pressure.

### If the skill is not discovered

| Check | Action |
|---|---|
| File name | Must be exactly `SKILL.md` |
| Directory | Must be `.../skills/shiva-skill/SKILL.md`; ID is the directory name |
| Description | Must be present; skills without a description are not advertised |
| Permission | The selected agent's `skill` permission must allow or ask for `shiva-skill` |
| Duplicate ID | A later source may override it; search global and project skill paths |
| Autoinvoke | `metadata.opencode/autoinvoke: false` hides it from the model-facing list |
| Session | Start a new session after installing or replacing the file |
| Mention | Try `@shiva-skill` to load it explicitly |

### If the skill loads but is ignored

- The request may not match the description closely enough; mention `@shiva-skill`.
- A higher-precedence `AGENTS.md` may conflict. OpenCode combines instruction files and does not resolve conflicts; state the precedence order from §1.
- A project override may be loading an older copy.
- Ask the model to quote the section number and rule it is applying. That exposes whether it has the body.

---

## 4. Configuration and permissions

### v2 versus v1

Do not mix schemas.

| Area | v1 | v2 |
|---|---|---|
| Permission key | `permission` object | `permissions` array |
| Agent key | `agent` | `agents` |
| Shell action | `bash` | `shell` |
| Subagent action | `task` | `subagent` |

### v2 example

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "permissions": [
    { "action": "skill", "resource": "shiva-skill", "effect": "allow" },
    { "action": "shell", "resource": "*", "effect": "ask" },
    { "action": "shell", "resource": "git push *", "effect": "deny" }
  ]
}
```

Rules are evaluated in order and the last matching rule wins, so put broad rules before specific exceptions.

### v1 example

```jsonc
{
  "permission": {
    "skill": {
      "shiva-skill": "allow"
    },
    "bash": "ask"
  }
}
```

### Config locations

- Global: `~/.config/opencode/opencode.json` or `opencode.jsonc`
- Project: `opencode.json` / `opencode.jsonc`, or `.opencode/opencode.json` / `.opencode/opencode.jsonc`
- Global instructions: `~/.config/opencode/AGENTS.md`
- Project instructions: `<repo>/AGENTS.md`

The skill grants no tools or permissions by itself. The harness and OpenCode permission rules still apply.

---

## 5. ChatGPT planning → OpenCode implementation

1. In ChatGPT, produce the artifacts in `HANDOFF-TEMPLATE.md`: `PRD.md`, `ARCHITECTURE.md`, `IMPLEMENTATION_PLAN.md`, `ACCEPTANCE_CRITERIA.md`, and setup docs. Add API, database, security, UI, or deployment artifacts only when the project needs them.
2. Put the artifacts in the repository. Do not use a chat transcript as the plan.
3. Start a fresh OpenCode session. Send the bootstrap prompt below.
4. Require a readiness report. Fix blocking gaps before approving code.
5. Implement one vertical slice. Update acceptance evidence and write a checkpoint.
6. Repeat through integration, hardening, and release verification. Report with the §9 completion table.

### Bootstrap prompt

```text
Read AGENTS.md and the handoff artifacts. Do not edit files yet.

1. Restate the outcome, non-goals, and mandatory acceptance criteria.
2. Compare the plan with the repository: paths, stack, versions, scripts, environment variables, data/auth, and deployment.
3. Run the §7.2 readiness gate. List blocking and non-blocking gaps with evidence.
4. Propose the first vertical slice, the files it touches, and how it will be verified.

Stop and wait for approval.
```

### If the plan and repository disagree

Use §7.7:

1. Stop the affected work.
2. State the conflict with evidence.
3. Propose the smallest change that preserves intent.
4. Update the affected artifact.
5. Re-approve if scope, architecture, security, data, or cost changes.

Do not silently “fix” the plan after implementation.

---

## 6. Updating and rollback

### Update

```powershell
Copy-Item .\S-Skill-v3.2.md (Join-Path $HOME ".config\opencode\skills\shiva-skill\SKILL.md") -Force
```

Start a new session. Skills can be cached by the running process.

### Rollback

1. Restore the previous file, or copy `S-Skill-v3.1.md` over `SKILL.md`.
2. Remove the trigger line from `AGENTS.md` if you no longer want it.
3. Start a new session.

For a project install, revert the repository changes instead of editing global files.

---

## 7. Security notes

- Skills can direct tool use. Inspect any third-party skill before installing it.
- Do not put secrets, tokens, or personal data in handoff artifacts.
- The skill instructs the model to protect credentials, but the permission system is the enforcement layer.
- A skill is not a sandbox. Keep shell, edit, and push permissions explicit.
- A reference URL in a document is not an installed capability.

---

## 8. Known limitations

- OpenCode v2 documentation changes; re-check paths and schemas for your version.
- Local verification used OpenCode v2.0.32 on Windows.
- No verified CLI prints the loaded instruction body; the canary is behavioral evidence, not cryptographic proof.
- Installation commands are documented, not executed automatically by this repository.
- The skill’s effectiveness is not empirically proven; see `VERIFICATION-CHECKLIST.md`.
