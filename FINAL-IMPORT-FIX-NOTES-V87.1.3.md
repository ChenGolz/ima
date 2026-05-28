# Luach v87.1.3 Import Fix Notes

This build fixes the backup Import regression reported against the v87.1.2 hardened package.

## Fixed

- `sanitizeImportedBoardV871()` now preserves the current exported app data model, including:
  - `view`
  - `stage`
  - `livePing`
  - `person`
  - `medications`
  - `care`
  - `symptoms`
  - `monthly`
- Existing older/optional import keys remain supported.
- Runtime identifiers were bumped to `v87.1.3-full-release`.
- Service worker cache was bumped to `family-clock-v87-1-3-full-release`.

## Still a deployment gate for existing live backends

Run the protected `securityMigrationReport` endpoint and release broadly only when `missingSecurityCount` is `0`.
