# flvx Fork Update Notes

## Overview
- Target fork: `iKeilo/flvx`
- Upstream source: `Sagit-chu/flvx`
- Comparison date: 2026-05-20
- Upstream default branch: `main`
- Fork default branch: `main`

## Cross-Comparison Result
- `iKeilo/flvx:main` is behind `Sagit-chu/flvx:main` by `178` commits.
- GitHub compare status: `ahead` from the upstream compare API perspective for `Sagit-chu/flvx` over `iKeilo/flvx`.
- The upstream has broad updates across backend, frontend, docs, compose files, and workflow files.

## High-Level Upstream Changes Observed
- Backend updates under `go-backend/`, including upgrade logic, monitoring, storage, and HTTP handlers.
- Frontend updates under `vite-frontend/`, including version-channel logic and node page UI.
- Compose and install script updates such as `docker-compose-v4.yml`, `docker-compose-v6.yml`, and install helpers.
- Documentation growth under `docs/` with multiple design/spec/plan documents.

## Custom Changes Prepared In This Working Copy
These changes are applied in the local synced working tree `flvx-src/` and are intended to be carried into the fork.

### 1. Stable channel release recognition refinement
Files:
- `go-backend/internal/http/handler/upgrade.go`
- `go-backend/internal/http/handler/upgrade_release_channel_test.go`
- `vite-frontend/src/utils/version-update.ts`
- `vite-frontend/src/pages/config.tsx`

Behavior after adjustment:
- `stable` accepts plain numeric releases such as `3.0.0`
- `stable` accepts RC-tagged releases such as `3.0.0-rc6`
- `stable` does **not** accept `alpha` or `beta`
- `dev` continues to catch non-stable special tags

### 2. Node tile layout improvement in tiled mode
Files:
- `vite-frontend/src/pages/node.tsx`

UI changes:
- Moved the online/offline indicator below the node name
- Placed the online/offline indicator above the IP block
- Expanded the visible area for node names
- Limited the node name to two lines so it stays inside each tile card

## Files Currently Changed Relative To The Upstream Snapshot Used For Editing
- `go-backend/internal/http/handler/upgrade.go`
- `go-backend/internal/http/handler/upgrade_release_channel_test.go`
- `vite-frontend/src/utils/version-update.ts`
- `vite-frontend/src/pages/config.tsx`
- `vite-frontend/src/pages/node.tsx`

## Deployment Notes Already Applied On The Live Server
Server-side runtime changes were already tested on the running deployment:
- Patched `flux-panel-backend` binary to support `stable => rc`
- Rebuilt and replaced `vite-frontend` container to include the tiled node-card layout fix

These deployment-side actions are not yet pushed to `iKeilo/flvx` from the current environment.

## Recommended Fork Sync Strategy
1. Sync `iKeilo/flvx` with upstream `Sagit-chu/flvx:main`.
2. Re-apply or cherry-pick the custom changes listed above.
3. Commit with a message similar to:
   - `sync upstream and refine stable rc handling`
   - `adjust tiled node card status and title layout`
4. Push to `iKeilo/flvx:main` or open a PR branch first.

## Blocking Issue For Direct Upload From This Environment
The current environment does not have a writable GitHub auth path configured:
- no usable `git` binary was found locally in this workspace flow
- no GitHub token or authenticated CLI session is available here
- the working copy was prepared from source files, not from an authenticated git clone

## Source Links
- Upstream repository: https://github.com/Sagit-chu/flvx
- Fork repository: https://github.com/iKeilo/flvx
- Upstream releases: https://github.com/Sagit-chu/flvx/releases
