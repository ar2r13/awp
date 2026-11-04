# Keep useful context

Save a fact when it will change a future agent's action and is costly to rediscover:
a confirmed decision and its reason, a non-obvious constraint, a verified command,
or a reproducible pitfall. Record evidence or a code/document link where useful.

- All paths below are relative to the workspace root, outside code repositories.
  Store requirements in vision, boundaries in architecture, and module findings,
  code maps, commands, and pitfalls in `docs/modules/<module>/` as needed. Existing
  repository rules remain authoritative; do not use them as agent notebooks.
- For a substantial decision, create a short `docs/decisions/<topic>.md` only when
  the tradeoff needs its own explanation; add a link to the documentation map.
- Store one fact in one place. Correct or remove stale facts instead of appending
  contradictory notes. Recheck facts likely to have changed before relying on them.
- Do not save chat transcripts, routine edits, raw tool output, secrets, or an
  automatic changelog. Do not create a memory file after every task.
- Keep temporary handoffs in task files, not permanent project instructions.
  Remove a completed task file after transferring any durable facts to their owner.
- If tool-specific local notes are useful, use workspace `.local/agents/<tool>.md`,
  outside code repositories; do not create the folder otherwise.
  Shared rules must not depend on private notes or a tool's built-in memory.

A useful entry explains the fact, why it matters, and where to verify it in a few
lines. A second agent should be able to use it without reading the previous chat.
