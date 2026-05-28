# Luach v87.1.4 JSONP runtime fix

This build fixes the live browser error:

`Uncaught ReferenceError: luach_cb_... is not defined`

Cause: Google Apps Script JSONP responses can arrive after the previous short browser timeout, especially on cold starts. The old cleanup deleted the callback, so the late script response threw a ReferenceError and the page showed a cloud update failure.

Changes:

- `patient.html` and `boindex.html`: cloud `load` JSONP timeout increased from 8.5 seconds to 45 seconds.
- `patient.html` and `boindex.html`: JSONP cleanup keeps expired callbacks as no-op functions for five minutes before deletion.
- `Code.gs` and `apps-script/Code.gs`: JSONP output is guarded so a missing callback does not throw.
- Runtime version: `v87.1.4-jsonp-runtimefix`.
- Service worker cache: `family-clock-v87-1-4-jsonp-runtimefix`.

Important deployment step: deploy the included `Code.gs` as a new Apps Script version, then upload the updated frontend files and hard-refresh the browser/PWA.
