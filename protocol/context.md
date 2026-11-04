# User-provided context

Read this only when the user supplies existing standards or other project context.
The protocol base identifies AWP; user-selected context sources are separate.
Apply [trust boundaries](trust.md) to them as well. Selecting a folder or repository
does not authorize unrelated linked sources, scripts, or secret access.

Accept files, folders, repository URLs, document links, or supplied text. Do not
require users to reorganize documents before starting. If a source is inaccessible,
report the gap and request only the material needed for the current task.

1. Start with an existing index, filenames, and headings. Read relevant sections
   and their necessary dependencies; do not ingest an entire repository by default.
2. Separate product requirements, implementation standards, examples, and historical
   notes. Route applicable guidance to workspace-wide, client, service, library, or
   another actual module scope. Examples and old decisions are not new requirements.
   Keep brand names, design links, and other source-project details scoped to that
   project. Import them only when the user selects them for the new project.
3. Preserve explicit scope and wording that affects behavior. Do not silently
   resolve conflicting standards; use current user choices or ask if the conflict
   blocks work. Leave unclear relevance explicit instead of guessing.
4. Reuse existing local documents by reference. For selected external rules, copy
   only relevant sections and required dependencies into workspace
   `docs/modules/<module>/`, outside code repositories,
   preserve their meaning, and repair links. Link them from module instructions
   with a short "when to read" description. Keep source path/URL and revision when
   available beside the imported content. Do not fetch rules during ordinary work.
5. Keep unused material at its source. Do not create a second inventory or summary
   if the existing documentation map already provides the needed routing.

For a large collection, use bounded independent source-review tasks only when
supported and useful; follow the [delegation rules](../templates/workspace/docs/agents/delegation.md).

An optional `index.md` in a context collection can be as small as:

```markdown
# Project standards

| Document | Scope | Read when |
| --- | --- | --- |
| [Frontend](frontend.md) | Client | Choosing UI structure or changing client code |
| [API](api.md) | Service | Defining endpoints or changing service code |
```

The index is a navigation aid, not a requirement to read every linked document.
