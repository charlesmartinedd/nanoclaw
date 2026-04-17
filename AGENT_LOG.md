### $stamp — Codex (GPT)
**Task**: Debug and permanently fix NanoClaw OAuth token expiry on VPS.
**Changes**:
- Centralized Anthropic auth injection in `src/container-runner.ts` so containers can read `CLAUDE_CODE_OAUTH_TOKEN` / `ANTHROPIC_AUTH_TOKEN` / `ANTHROPIC_API_KEY` from NanoClaw `.env`.
- Added safe `chown` handling for IPC input directory creation to prevent test/runtime failures.
- Added `src/container-runner.test.ts` coverage for centralized OAuth env injection.
- Rebuilt NanoClaw, ran test/typecheck validation, and restored current fleet auth via fresh session credential sync from local machine.
- Confirmed long-lived auth still needs one-time `claude setup-token` browser approval; short-lived `.credentials.json` access tokens are not valid for the centralized env path.

**Commit**: `refactor: centralize nanoclaw auth token injection`
**Status**: ✅ Pushed

---
### 2026-04-17 00:25:59 — Codex (GPT)
**Task**: Debug and permanently fix NanoClaw OAuth token expiry on VPS.
**Changes**:
- Centralized Anthropic auth injection in `src/container-runner.ts` so containers can read `CLAUDE_CODE_OAUTH_TOKEN` / `ANTHROPIC_AUTH_TOKEN` / `ANTHROPIC_API_KEY` from NanoClaw `.env`.
- Added safe `chown` handling for IPC input directory creation to prevent test/runtime failures.
- Added `src/container-runner.test.ts` coverage for centralized OAuth env injection.
- Rebuilt NanoClaw, ran test/typecheck validation, and restored current fleet auth via fresh session credential sync from the local machine.
- Confirmed long-lived auth still needs one-time `claude setup-token` browser approval; short-lived `.credentials.json` access tokens are not valid for the centralized env path.

**Commit**: `refactor: centralize nanoclaw auth token injection`
**Status**: ✅ Pushed

---
