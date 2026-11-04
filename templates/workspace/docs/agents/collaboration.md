# Concurrent work and handoffs

These conventions coordinate agents; a Markdown file is not an atomic lock.
Task-file paths are relative to the workspace root, outside code repositories.

- Inspect existing changes and relevant active tasks before editing. Preserve work
  that belongs to someone else. Do not reset, stash, or discard it to get a clean tree.
- Prefer separate modules or files. For concurrent edits in one repository, use
  separate branches/worktrees where the environment supports them. Worktrees do
  not coordinate separate module repositories automatically.
- If coordination needs shared state, create `docs/tasks/<short-name>.md` with a
  goal, agent/session identifier, status, affected repositories/files, next step,
  and checks. Link active task files from the documentation map. Keep them short.
- Check for conflicting ownership before claiming work. If two agents already
  touch the same area, coordinate a handoff or choose another area before editing.
  Do not assume that writing an owner field prevents races.
- A claim does not expire just because it is old. Verify status with the user or
  the agent before taking over an apparently abandoned task.
- Update a task when handing off or blocked; do not mirror every action. On
  completion, move durable knowledge to its owning document, remove the task file
  and its index link, and leave a normal completion report.
- Tool adapters contain only entry-point references and tool-specific mechanics.
  Do not duplicate product rules or maintain separate competing project memories.
