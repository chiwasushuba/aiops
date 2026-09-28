---
name: service-integration
description: Plan, implement, or review a user flow or contract spanning multiple AIOps submodules or services. Use for frontend and backend integration, shared data behavior, and cross-service verification.
---

# AIOps service integration

Start in the parent repository. Identify every affected submodule and read its
`AGENTS.md`, current Git status, relevant manifest, and existing Codex guidance.
Use the frontend's `frontend-api-contract` skill for browser request details and
the backend's `aiops-backend-api` skill for HTTP implementation details when
those boundaries are involved. Do not copy their instructions into the parent.

Trace one user-visible flow from UI state through the request to the backend
controller, service, persistence, and response. Record the actual method, path,
request and response fields, status codes, validation, and failure behavior.
Separate implemented behavior from proposed features. The current users and
messages APIs are CRUD contracts; they do not establish login or generated chat.

Agree on the smallest compatible contract before editing either service. Assign
each change to its owning submodule and keep types, field names, and error states
consistent. For personal data, check identity and authorization assumptions,
browser exposure, and whether a model suggestion is merely proposed or saved.
Do not present prototype records as persisted data.

Verify the affected backend tests and frontend tests, lint, and build according
to the changed surfaces. Exercise one success path and the relevant failure path
for the integration. Report each submodule's changed files and checks separately,
including any contract gap or check blocked by the environment. Inspect the
parent and child Git status separately: a dirty child working tree is different
from a changed parent submodule pointer. Updating the recorded pointer requires
an authorized commit in the child and then the parent.
