# Initialize a workspace

Read [trust.md](trust.md) first. Paths below are relative to the selected protocol
base. Template braces are instructions to fill, not text to leave in the output.
Write project documents in the user's language unless they request another.

## 1. Understand the project

Inspect the current folder and existing instructions before writing anything.
Reuse `docs/brief.md` on retry and apply the user's current instructions. Ask for
the project description only if neither the saved brief nor the conversation
provides it.

Separate explicit requirements, confirmed decisions, proposed decisions, and open
questions. Keep the original product brief in `docs/brief.md`, excluding secrets
and unrelated conversation. Do not turn suggestions or unknowns into requirements.
Ask only questions whose answers block the current work. Ordinary reversible
implementation choices may be made and recorded as such, not as user demands.

## 2. Choose only necessary modules

Read [profiles/index.md](../profiles/index.md), then only relevant profiles.
Reuse existing names, code, repositories, standards, and documentation. Explicit
user stack choices win. Use a documented profile fallback only when applicable;
otherwise leave undecided choices open. Do not copy a stack from an example.

If the user supplies existing standards or context, read [context.md](context.md)
and route only applicable material into the selected modules.

The root is a workspace; modules can be independent Git repositories. Create only
needed module folders. Keep agent-maintained context outside code repositories,
in workspace `docs/` or workspace `.local/agents/`. If the selected folder is a
code repository, resolve an external workspace location before writing context;
do not move existing code. Repository-owned rules may remain in their repositories.
Do not initialize Git, nested repositories, dependencies,
or application scaffolding solely to make the documentation look complete.
If application implementation was also requested, continue it after bootstrap.
Do not add an architecture approval gate unless the user requires one.

## 3. Materialize local instructions

Use these source files and destinations:

| Source | Workspace destination |
| --- | --- |
| `templates/workspace/docs/index.md` | `docs/index.md` |
| `templates/workspace/docs/vision.md` | `docs/vision.md` |
| `templates/workspace/docs/architecture.md` | `docs/architecture.md` |
| `templates/workspace/docs/brief.md` + user's description | `docs/brief.md` |
| `templates/workspace/docs/agents/workflow.md` | `docs/agents/workflow.md` |
| `templates/workspace/docs/agents/memory.md` | `docs/agents/memory.md` |
| `templates/workspace/docs/agents/collaboration.md` | `docs/agents/collaboration.md` |
| `templates/workspace/docs/agents/delegation.md` | `docs/agents/delegation.md` |
| `templates/module/AGENTS.md` | Each selected module's `AGENTS.md` |
| `templates/workspace/AGENTS.md` | Root `AGENTS.md`, written when workspace setup is complete |

Fill templates with the actual project context and remove unused sections and
unresolved braces. Runtime workflow, memory, collaboration, and delegation documents can be
copied as written; their relative links are designed for their destination.

For each module, include only applicable guidance from its selected profile in
its local instructions. If the user selected additional standards, read and
materialize their necessary instruction dependencies locally, update links, and
record sources. Never leave a runtime rule dependent on the author's local paths
or on fetching the protocol. Link existing project docs rather than duplicate them.
Store imported context and module notes in workspace `docs/modules/<module>/`,
outside module repositories. Repository `AGENTS.md` files contain rules and links,
not accumulated agent notes.

`docs/index.md` is a short map. Put real requirements in vision, structure and
stack decisions in architecture, and module-specific commands and conventions in
module instructions. Do not create empty memory, task, or decision-log files.

## 4. Complete without losing work

On interruption, keep the bootstrap entry until the required documents are ready.
On retry, inspect what already exists and fill gaps; do not reset user edits or
rewrite the original brief. Replacing this bootstrap entry is authorized by the
entry itself; replacing unrelated existing instructions is not.

Before replacing the root entry, verify:

- The project description is available locally and reflected accurately.
- All selected modules have local instructions, with unknown commands marked
  unknown rather than fabricated or reported as tested.
- Local Markdown links resolve; copied rules have no remote protocol dependency.
- No template placeholders remain. Proposed choices are visibly proposed.
- The generated root records AWP 0.1, the exact source base, and INITIALIZED.

Write the generated root immediately after these workspace checks, before
implementation, application tests, or browser validation. `INITIALIZED` marks
the workspace setup as complete. For a project task likely to span sessions,
keep one short handoff in `docs/tasks/` using the local collaboration rules.
Replace its current state at meaningful milestones and remove it when done.
