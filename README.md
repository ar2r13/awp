# Agent Workspace Protocol

AWP is a workflow template for projects with one or more repositories. Put one
`AGENTS.md` in a new project folder, describe what you want to build, and let your
agent create the structure and concise project documentation.

It is a collection of linked Markdown instructions, with no installer, server,
or required integrations.

## Getting started

1. Copy [bootstrap/AGENTS.md](bootstrap/AGENTS.md) into your project folder as `AGENTS.md`.
2. If the protocol base is not configured, replace `REPLACE_WITH_PROTOCOL_BASE`
   with the protocol source URL supplied by its distributor. It should look like
   `https://raw.githubusercontent.com/OWNER/REPO/FULL_COMMIT_SHA`.
3. Open the folder in your coding agent and describe your project. If the agent
   does not load the file automatically, say: "Read AGENTS.md and initialize this
   workspace using my project description."

See [the notes application example](examples/notes.md) for a sample description
and the expected workspace structure.

## What happens

1. The agent reads the entry file and loads instructions from the configured source.
2. It identifies your goals, constraints, and required modules, asking only questions
   that block the current work.
3. It creates local documentation and module instructions using your requirements
   and stack choices. Unresolved choices remain explicit.
4. It checks local links and replaces the bootstrap entry with a project-specific
   `AGENTS.md`. Initialization does not repeat on subsequent tasks.
5. Future tasks use local rules. Reading AWP no longer requires network access.

The workspace includes the original brief, vision, architecture, a documentation
map, and working rules. Memory stores useful decisions and constraints rather
than chat history. Temporary task files are created only when needed.
Agent notes, code maps, decisions, and task files live at the workspace level,
outside code repositories. Repositories retain their own rules; module-specific
agent context belongs in workspace `docs/modules/<module>/`.

## Compatibility and sources

[AGENTS.md](https://agents.md/) is an open instruction format for coding agents.
Automatic loading depends on your tool, version, and settings. Explicitly asking
the agent to read the file provides a reliable entry point. If needed, the agent
can create a small tool-specific adapter that points to the shared instructions.

Review the protocol source before using it. Public GitHub history makes content
inspectable; it does not guarantee safety. The entry file and
[trust rules](protocol/trust.md) restrict instruction sources and actions. Actual
enforcement depends on your agent's tool permissions.

Use a source pinned to a full commit SHA. Existing workspaces keep their local
rules; updating them is an explicit task, with changes reviewed before adoption.

## Project conventions

Provide your frontend, backend, or other project standards with your description.
The protocol base points to AWP itself; your project standards are separate inputs.
You can supply files, folders, repository URLs, or document links. No special
format is required. An optional index with a document's scope and when to read it
helps the agent avoid loading unrelated material; see [context intake](protocol/context.md).
[Module profiles](profiles/index.md) guide structure. New browser apps default to
[TypeScript, Lit, and esbuild](profiles/client.md) unless project choices or
existing standards take precedence. The agent brings only selected standards
and their required instruction dependencies into your workspace.

For substantial independent research or context sorting, the agent may use
subagents when supported. Small tasks stay in one agent. Model and reasoning
preferences apply only where the tool exposes those controls; see
[delegation rules](templates/workspace/docs/agents/delegation.md).
