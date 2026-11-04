# Example project

Sample user description:

> I want a personal notes application with a browser client and a separate API.
> No registration or synchronization for now. Use TypeScript for the client;
> leave the framework choice open for now. Use Deno for the API. Prepare only the
> workspace first; do not write application code. The client and API will
> eventually be separate Git repositories.

Expected minimal structure after bootstrap:

```text
AGENTS.md                 # INITIALIZED; protocol source recorded
docs/
  index.md                # documentation map, not a duplicate summary
  brief.md                # original description above
  vision.md               # notes; no invented registration or synchronization
  architecture.md         # client + api; framework choice remains open
  agents/
    workflow.md
    memory.md
    collaboration.md
    delegation.md
client/
  AGENTS.md               # TypeScript; commands not configured yet
api/
  AGENTS.md               # Deno; commands not configured yet
```

Module names are examples, not a required convention. Bootstrap does not create
`.git`, application code, dependencies, empty task files, or adapters for every
possible agent. The unresolved framework choice does not block documentation.
Architecture records the future repositories as not yet created.

A subsequent request to "add notes search" uses local rules and proceeds with
that task. It does not download the protocol or initialize the workspace again.
