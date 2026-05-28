# V84 - Scaling, Security, and Clone Template Sharing

## What changed

- Apps Script CacheService wrapper for board loads to reduce Spreadsheet reads.
- LockService wrapper for saves to reduce concurrent write collisions.
- Cache invalidation after saves.
- Helper for clearing stale chunk rows before rewriting chunks when supported by the current function names.
- More robust POST payload parsing.
- Service Worker bypasses HTTP Range requests, improving audio/music playback on Safari/iOS.
- JSONP script cleanup hardening to prevent DOM bloat on tablets.
- Patient screen refreshes immediately after tablet wake/visibility return.
- XSS hardening: strips inline event handlers and javascript: URLs from newly inserted DOM.
- Backoffice includes Clone My Template instructions for friends/families to create a fully private independent copy.

## Recommended sharing path

For friends or other families, the safest path is:
1. Clean a Google Sheet template so it contains no personal data or private Drive IDs.
2. Share the clean template as "Anyone with the link can view".
3. Change the sheet URL ending from `/edit#gid=0` to `/copy`.
4. Send that `/copy` link.
5. Each friend clicks Make a copy.
6. They deploy their copied Apps Script as:
   - Execute as: Me
   - Who has access: Anyone
7. They use their own Web App URL in the frontend.

This gives complete data separation because their Sheet, Apps Script, and Drive all belong to their Google account.
