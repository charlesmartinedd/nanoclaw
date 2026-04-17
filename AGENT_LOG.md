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
### 2026-04-17 00:41:25 — Codex (GPT)
**Task**: Complete NanoClaw permanent auth cutover with a long-lived Claude token.
**Changes**:
- Completed `claude setup-token` on the VPS and installed the resulting 1-year `CLAUDE_CODE_OAUTH_TOKEN` into `/root/nanoclaw/.env`.
- Fixed `src/container-runner.ts` so first-party Claude OAuth uses only `CLAUDE_CODE_OAUTH_TOKEN` and no longer misroutes through `ANTHROPIC_AUTH_TOKEN`.
- Verified direct container auth succeeds with the long-lived token and still succeeds when `/home/node/.claude/.credentials.json` contains deliberately invalid credentials.
- Restarted `nanoclaw.service` on the permanent token path.

**Commit**: `fix: finalize long-lived nanoclaw oauth path`
**Status**: ✅ Pushed

---
