# Claude Code Instructions for privatedeepsearch-melt

## MANDATORY: Read AGENTS.md First

Before ANY work in this repo: Read `AGENTS.md` for cross-agent compliance.
AGENTS.md is symlinked to CLAUDE.md — single source of truth across all repos and tools.

**Critical guardrails**:
- **Token cost**: Blocking wait ($0.20) vs polling loop ($20-40) = 100x savings
- **MCP vs Direct API**: <10 workflows use MCP, >10 use templates + urllib
- **Pre-commit hooks**: Automatically block anti-patterns (git-enforced)

---

## PROJECT GOAL

[1-2 sentence description of repo purpose]

---

## Execution Tasks

**For multi-phase overnight work, use the centralized orchestration pattern.**

### Quick Start

1. **Copy template:**
   ```bash
   cp ~/.cyrus/templates/execution_script_template.py scripts/<task_name>_execute.py
   ```

2. **Implement phases** as `OrchestrationScript` subclass

3. **Create Linear issue** from template:
   ```bash
   cat ~/.cyrus/templates/linear_execution_issue.md
   ```

4. **Validate before delegating:**
   ```bash
   python ~/.cyrus/scripts/validate_execution_issue.py ROM-XXX
   ```

5. **Delegate to jinyang** — execution happens automatically

### Resources

- **Template:** `~/.cyrus/templates/execution_script_template.py`
- **Docs:** `~/.cyrus/docs/EXECUTION_PATTERN.md`
- **Issue template:** `~/.cyrus/templates/linear_execution_issue.md`

**DON'T:** Create multiple Linear issues with `blockedBy` (doesn't auto-trigger)
**DO:** Single issue, single orchestration script, all phases sequential

---

## Project Structure

```
[Describe key directories and files]
```

---

## Development Workflow

### Testing
```bash
[test commands]
```

### Building
```bash
[build commands]
```

---

## Hard-Won Lessons

[Document institutional knowledge here as it accumulates]

---

*Last updated: 2026-02-06*

---

## Mandatory Plan-to-Linear Protocol

For non-trivial work, this sequence is required:

1. Create or update a plan file at `docs/plans/<slug>-<YYYY-MM-DD>.md`.
2. Break work into executable steps.
3. Create one Linear issue per executable step.
4. Link the plan path in each Linear issue.
5. Keep plan + Linear in sync as execution progresses.
6. Never ask the user to do manual Linear operations.

Linear outage fallback:
- If Linear is down/rate-limited, queue changes and continue execution:
  - `python3 scripts/linear_outbox_append.py ...`
  - `python3 scripts/linear_flush_outbox.py --backend auto`
