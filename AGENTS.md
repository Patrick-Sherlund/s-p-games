No code comments (ABSOLUTE): Never add comments to code—no //, /* */, JSDoc/TSDoc, TODOs, or commented-out code—under any circumstance unless the user explicitly requests it.

File hygiene: Delete files that become truly obsolete due to your change. Do not delete files to “fix” lint/type errors—stop and ask the user first.

Coordinate before undoing others: Don’t revert/delete work you didn’t author. If unsure about in-flight work, stop and coordinate.

No destructive git ops: Never run git reset --hard, git restore/checkout to older commits, or rm as a “fix” unless the user explicitly instructs it in this chat.

No reverting others’ files: Never use git restore (or similar) to revert files you didn’t author.

Observe the folder / file architecture for the project, ensure that you always follow that consistently for all feature work.

No amend: Never amend commits unless explicitly approved in writing.

Rebase without editors: Use GIT_EDITOR=: and GIT_SEQUENCE_EDITOR=: (or --no-edit) to avoid interactive editors.

Cloudflare-first backend discipline: Any backend/server feature must be implemented in a way that is actually compatible with Cloudflare Workers and the project’s Cloudflare deployment model; do not introduce server patterns, libraries, filesystem assumptions, long-lived in-memory assumptions, or Node-only APIs that are incompatible with Workers unless the user explicitly requests that architectural change.

Authoritative backend behavior: For any multiplayer, timer-based, room-based, or synchronized feature, keep the backend authoritative for room state, timing, phase/state transitions, and validation; do not push authoritative game logic into the client unless the user explicitly asks for a client-authoritative design.

Shared type discipline: When the project has shared models/types for frontend and backend communication, update them first-class and keep them as the source of truth rather than duplicating slightly different ad hoc shapes across files.

Realtime correctness over shortcuts: For realtime or room-based flows, prefer correctness, synchronization, reconnect safety, and race-condition resistance over “quick demo” shortcuts.

No placeholder integrations: Do not leave fake stubbed backend flows, fake realtime wiring, fake upload flows, or fake success paths in place of the real feature unless the user explicitly asks for a stub/prototype.

Cloudflare configuration discipline: When backend changes require Cloudflare bindings, environment variables, routes, durable state/storage choices, or wrangler configuration changes, update the appropriate config files consistently and keep code aligned with those bindings/configurations.

No secret leakage: Never hardcode API keys, secrets, tokens, Cloudflare credentials, or environment-specific private values in source code, config committed to the repo, client bundles, tests, or examples.

Frontend/backend boundary discipline: Keep browser-only code out of the Worker/backend side, and keep server-only secrets/authority out of the client side; do not blur those boundaries.

Mobile-first product discipline: For user-facing feature work in this project, preserve a mobile-first experience and ensure frontend decisions support responsive handheld use rather than only desktop layouts.

Polish from the start: Do not treat UI quality, interaction quality, or responsiveness as optional follow-up work; implement features in a way that is already coherent, polished, and aligned with the intended product feel.

Runnability matters: Any feature work must leave the project in a runnable state for local development and in a deployable state for the project’s Cloudflare deployment path; do not make changes that conceptually “should work” while leaving the repo misconfigured or broken.