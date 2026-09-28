# AIOps repository guidance

## Repository boundaries

This repository is the parent for `aiops-frontend/` and `aiops-backend/`, which
are separate Git submodules. Work in a child directory must follow its own
`AGENTS.md` and `.codex/` guidance. Future services should document their own
commands and conventions in their nearest `AGENTS.md`.

The frontend is a React and TypeScript Vite app. The backend is a Java 21 Spring
Boot service. The current browser routes use local prototype data; the backend
has users and messages CRUD APIs. Read the code and current documentation before
claiming that a proposed feature or integration exists.

## Working across services

- Identify the owning submodule for each change and inspect its guidance,
  manifest, relevant code, and Git status before editing.
- For a flow spanning services, agree on the HTTP and data contract before
  changing either side. Use the root `service-integration` skill for this work.
- Keep credentials and personal data out of browser bundles, logs, and examples.
  Do not infer authentication or assistant behavior from the existing CRUD APIs.
- Preserve unrelated changes in each submodule. Report changes and verification
  separately for each affected repository.
- A child commit does not update this parent's recorded submodule commit until
  the parent pointer is changed. Do not commit, push, or update pointers without
  explicit authorization.

## Commands

Run commands from the owning submodule directory:

| Area | Checks |
| --- | --- |
| Frontend | `npm test`, `npm run lint`, `npm run build` |
| Backend | `.\mvnw.cmd -Dtest=UserControllerTests test` for users API changes; `.\mvnw.cmd test` for the full suite |

Use the relevant child README for setup and runtime commands. The parent has no
combined build or test command.

## Project Codex extensions

Root-wide configuration lives in `.codex/`. Keep frontend-only and backend-only
agents and skills in their respective submodules. Add a root agent or skill only
for a distinct, recurring responsibility that crosses repository boundaries.
