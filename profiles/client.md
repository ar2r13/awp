# Client

Create a client module only when the product needs one. Preserve existing code,
frontend standards, and design systems.

For a new browser app, default to TypeScript, Lit custom elements, and esbuild
with ESM output. Skip this fallback if existing conventions, supplied frontend
standards, or explicit stack choices conflict, or if the user defers selection.
Do not apply it to native clients or migrate existing code to it.

When selected, copy these references to workspace `docs/modules/<module>/` and
link them from the module's instructions with their read conditions:

- [Architecture](client/architecture.md): boot, build, routing, state, or browser support.
- [UI and style](client/style.md): components, templates, CSS, or interaction.

Record the stack as an AWP fallback, not a user requirement. Copy the references
without pulling both into every task. Keep entry points and commands in the module
instructions limited to paths and scripts that actually exist.

In local module instructions, capture the chosen stack, entry points, applicable
UI standards, and verified development/build/check commands when available.
Link detailed frontend documentation rather than duplicating it in `AGENTS.md`.

Keep API contracts with the module that owns them and link from the client.
Treat loading, empty, and error states as implementation concerns when relevant
to the requested screen; do not invent screens or features during bootstrap.
