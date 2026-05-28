# Luach v87.1.2 Final Cleanup Notes

This package is based on `luach-v87.1.2-final-release-fixed` and applies the final static-QA cleanup items from the follow-up report.

## Changes

- Removed the duplicate/unreachable `doGet(action=health)` branch in `Code.gs` and `apps-script/Code.gs`.
- Updated `getSecurityRow_()` to return `createdAt` and `updatedAt`, so strict access-key rotation can preserve the original security-row creation timestamp.
- Kept the existing v87.1.2 security fixes intact:
  - trusted saved API URL migration;
  - trusted saved Drive folder migration;
  - strict access-key rotation;
  - admin-protected security migration report;
  - disabled public owner-audio-folder mutation;
  - fixed import/export;
  - full package assets included;
  - aligned runtime/cache/export version identifiers.

## Verification

Static check result: 54 passed, 3 warnings, 0 failed.

Remaining warnings are deployment/maintenance items only:

1. Existing live backends with old unsecured boards still need migration or explicit acceptance. Run the protected `securityMigrationReport` and require `missingSecurityCount: 0` before broad rollout on existing production Sheets.
2. Frontend duplicate function overrides remain in `patient.html` and `boindex.html`; they are not syntax blockers, but should be consolidated before long-term maintenance.
