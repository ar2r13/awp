# Service

Create a service module only when requirements need an API, backend, worker, or
background processing. Do not assume a runtime, database, queue, or provider.

In local module instructions, capture the chosen runtime, service boundaries,
contract location, and verified run/check commands when available. Document
configuration variable names without secret values once the implementation uses
them. Do not create integrations or infrastructure solely because of this profile.

The service owns its public contract; consumers link to it. Record storage,
authentication, and deployment decisions only when specified or actually chosen.
