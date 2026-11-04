# {{PROJECT_NAME}}

Status: INITIALIZED
Protocol: AWP 0.1
Protocol source: {{EXACT_PROTOCOL_BASE}}

{{ONE_SENTENCE_PROJECT_PURPOSE}}

Read the target module's `AGENTS.md` before changing it. Use the
[documentation map](docs/index.md) when you need to find project context, and the
[working rules](docs/agents/workflow.md) for guidance relevant to the task.

{{MODULE_LINKS_WITH_ONE_LINE_RESPONSIBILITIES}}

Use confirmed requirements; keep proposals and unknowns explicit. Follow existing
style and make focused changes. Preserve other agents' and the user's work.
Keep durable knowledge in its owning document, not in a session log.
Agent-maintained context belongs at the workspace level, outside code repositories.
Keep module notes in workspace `docs/modules/<module>/`, not inside the module.

Use the local rules for this initialized workspace. Refresh protocol rules only
on request. For a resumed task, check any relevant active handoff and verify
progress against the current files before continuing.
