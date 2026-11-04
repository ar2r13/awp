# Bounded delegation

Use subagents when supported for substantial independent research, document
classification, or implementation in separate areas. Handle small lookups and
edits directly. Parallelism is useful only when it justifies the additional context
and coordination; it does not guarantee fewer tokens.

- Give each subagent a bounded question, relevant sources, allowed edit scope,
  and a concise expected result with evidence links and unresolved questions.
  Avoid full chat history when a focused handoff suffices and the tool allows it.
- Do not duplicate the delegated investigation in the parent. Read the returned
  findings and verify consequential claims at their source. Do not collect raw
  document dumps or create nested delegation unless the task requires it.
- Respect user-selected models and effort. Otherwise use a configured lightweight
  model for straightforward extraction or classification, where selection is
  supported. Use supported low effort for simple work, medium for bounded
  implementation, and high for ambiguous reasoning or complex review. Increase
  effort when task difficulty or failed checks justify it, not for every task.
- Check the actual tool interface before requesting model, effort, or context
  inheritance settings. These instructions express preferences, not controls.
  If overrides are unavailable, use the inherited/configured settings or keep the
  task in the parent; never claim that a cheaper model was selected without evidence.
- Do not change the parent session's configuration or create provider-specific
  agent configuration just to satisfy this policy. Such setup is a separate task.
- Read [collaboration.md](collaboration.md) before concurrent edits in shared areas.

Use the tools' documented defaults when no suitable override is available. Model
names, effort levels, inheritance behavior, and billing vary between tools.
