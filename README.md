# work-hub-backend

The API, the worker and the admin CLI of [work-hub](https://github.com/SrZafkiell/work-hub):
one place for your work and your personal projects, with tasks, meetings, notes and
calendars kept in separate workspaces.

> Status: planning. The plan, the decisions and the risk register live in
> [work-hub](https://github.com/SrZafkiell/work-hub/blob/main/docs/PLAN.md). The issues
> of this repository are created from that plan and tracked on one
> [project board](https://github.com/users/SrZafkiell/projects/2).

## What lives here

- The FastAPI application and its OpenAPI contract. Every client is generated from the
  contract, and a published contract is never broken within a major version.
- The PostgreSQL schema, its migrations and the row-level security policies that keep
  workspaces and accounts apart.
- Passkey sign-in, server-side sessions and `hubctl`, the admin CLI that creates
  accounts on the server. There is no sign-up endpoint.
- The worker: calendar sync, reminders and digests.

## What lives elsewhere

- The web app: [work-hub-frontend](https://github.com/SrZafkiell/work-hub-frontend).
- The server setup, the Compose files, the deploy agent, the release manifests and the
  end-to-end tests: [work-hub](https://github.com/SrZafkiell/work-hub).
- The desktop app, planned:
  [work-hub-desktop](https://github.com/SrZafkiell/work-hub-desktop).

## How it ships

CI builds, scans and signs one API image on `main` and publishes the contract with every
release. A release of the product is a signed manifest in `work-hub` that pins this image
together with a web image that passed the end-to-end tests with it. The server pulls and
verifies; no CI system holds a credential for it.

## License

Apache-2.0. See [LICENSE](LICENSE).
