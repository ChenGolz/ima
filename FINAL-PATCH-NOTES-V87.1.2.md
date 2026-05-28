# Luach v87.1.2-full-release Final Patch Notes

Applied after QA report `luach-v87-1-2-full-release-qa-report(1).md`.

## Fixes

1. Saved private Drive folder IDs from older builds are no longer trusted silently.
   - `index.html`, `patient.html`, and `boindex.html` now require the trusted Drive marker.
   - Valid saved folder IDs without the marker prompt once before reuse.
   - Rejected or invalid saved folder IDs are cleared from localStorage.

2. Runtime/version/cache identifiers were aligned.
   - `Code.gs` and `apps-script/Code.gs`: `APP_VERSION = v87.1.2-full-release`.
   - `boindex.html` export metadata: `v87.1.2-full-release`.
   - `sw.js` cache name: `family-clock-v87-1-2-full-release`.

## Notes

Legacy unsecured boards are still a deployment migration gate by design. For existing production backends, run the protected `securityMigrationReport` and confirm `missingSecurityCount: 0` before broad release.
