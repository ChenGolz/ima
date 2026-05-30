# v87.1.19 Incognito accessKey read fix

Fixes the fresh-browser / Incognito link issue where generated links contained `accessKey=` but the frontend readers only checked `key`, `token`, and `boardKey`.

Changed in `index.html`, `boindex.html`, and `patient.html`:

- `accessKeyFromUrlOrStorage()` now reads `accessKey` from the query string.
- `accessKeyFromUrlOrStorageV52()` now reads `accessKey` from the query string and scoped storage.
- Hash compatibility remains for older `#key=` links.

This means a fresh Incognito browser can finally use links like:

`patient.html?board=...&accessKey=...`

without falling back to the default panel.
