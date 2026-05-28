# Luach v87.1.2 — Final Optional Hardening Notes

This build starts from `luach-v87.1.2-final-release-cleaned` and applies one additional low/medium hardening item from the final QA report.

## Changes

- `doGet(action=templateSetupInfo)` now requires `MIGRATION_ADMIN_SECRET` before returning spreadsheet metadata or a `/copy` URL.
- The backoffice template setup button now prompts for `MIGRATION_ADMIN_SECRET` and sends it only for that request.
- `Code.gs` and `apps-script/Code.gs` remain byte-identical.

## Still intentionally unchanged

- Legacy unsecured boards are still supported for backward compatibility. For existing production Sheets, run the protected `securityMigrationReport` and release only when `missingSecurityCount` is `0`.
- Duplicate frontend patch-layer functions remain as a maintenance cleanup item; the active runtime behavior is still determined by the final declarations.
