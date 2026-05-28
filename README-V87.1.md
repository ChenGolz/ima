# V87.1 Security Blockers Fix

This patch addresses the v87 recheck report release blockers:

1. patient.html and boindex.html now actually guard `api` / `cloudUrl` query params before persisting them.
2. Manual private Apps Script URL setup is validated in index.html and boindex.html.
3. `securityMigrationReport` is admin-secret protected with Script Property `MIGRATION_ADMIN_SECRET`; by default it returns count only.
4. Key rotation uses backend `verifyAccessKey` and only succeeds when the board is already secured, the new key verifies, and the old key fails.
5. Legacy unsecured boards cannot rotate keys through the normal rotation path.
6. Import now whitelists expected board fields.

Deploy:
- Upload index.html, patient.html, boindex.html, sw.js, manifest.json to GitHub.
- Replace Code.gs in Apps Script.
- Deploy as New version.
