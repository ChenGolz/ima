# Luach v87.1 Final Security Blocker Fix Summary

Applied after QA recheck on 2026-05-28.

## Fixed

1. `patient.html` and `boindex.html`
   - Removed raw `params.get("api")` usage from `cloudConfigFromUrl()`.
   - Route URL-supplied `api` / `cloudUrl` through `privateApiFromUrl()` approval and validation.
   - Added `sanitizeCloudConfigV871()` and call it when loading saved cloud config, when merging URL config, and after known-board recovery.
   - Invalid persisted `CLOUD_CONFIG_KEY.appsScriptUrl` values are replaced with `OWNER_APPS_SCRIPT_URL` or cleared.

2. `Code.gs` and `apps-script/Code.gs`
   - `doPost({ action: "rotateAccessKey" })` now calls `strictRotateAccessKeyV871_()`.
   - Legacy `rotateBoardAccessKey_()` is retained only as a compatibility wrapper and no longer auto-registers unsecured boards.

3. `boindex.html`
   - `importJson()` now uses `deepMerge(DEFAULT, value)` instead of undefined `DEFAULT_DATA`.

## Static checks run

- `manifest.json` parses as valid JSON.
- `sw.js` passes `node --check`.
- Extracted inline JavaScript from `index.html`, `patient.html`, and `boindex.html` passes `node --check`.
- `Code.gs` passes JavaScript syntax check after copying to `.js`.
- `Code.gs` and `apps-script/Code.gs` are byte-identical.
- Static release-blocker scans pass for API URL approval, saved cloud-config sanitization, strict backend rotation, and import fix.

## Not run

Live Google Apps Script, Google Sheets/Drive, and browser-device tests were not run in this offline sandbox.
