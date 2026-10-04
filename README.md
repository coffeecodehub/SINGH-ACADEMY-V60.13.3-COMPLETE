# Current update: Singh Academy V60.12.3

Read **V60.12.3-LOCAL-GUIDE.md** and **V60.12.3-QA-REPORT.md** first.
This focused change repairs test-only guest-page observation during logout /
Back / Refresh and streaming header duplication. It does not redesign the UI
or change application authentication, payment, certificate or database logic.
No tests are skipped; two genuinely visible headers still fail the check.

Local gate: `npm run verify:release`. Preserve .env and tested lockfiles.
No migration or seed. Keep Node 22.x or 24.x as already configured.

Historical guides below do not override the current release instructions.

---

# Singh Academy V60.12.1 — Node 22 / 24 release-tool compatibility

Start with **[V60.12.1-LOCAL-GUIDE.md](V60.12.1-LOCAL-GUIDE.md)** and
**[V60.12.1-QA-REPORT.md](V60.12.1-QA-REPORT.md)**.

This focused patch accepts stable Node **22.x or 24.x** for the existing local
release gate. **NVM is optional, not required.** An accepted runtime is not a
claim of a passing Next build, browser test, security audit or payment test.

From the project root:

```powershell
node -v
node -p "require('./package.json').version"
npm run check:runtime
npm run verify:release
```

Expected project version: `60.12.1`. Keep the current Hostinger Node **22**
selection; validate the same commit and reviewed lockfiles on its runtime before
handover. The CI workflow now includes separate Node 22 and 24 jobs; their
results still need to run in your repository.

No database migration, seed/reset, secret rotation, payment change, authentication
change, UI redesign or certificate redesign is introduced. Preserve private
`.env` files and existing tested lockfiles. Do not upload `node_modules` from a
Windows development computer to Hostinger; install from the lockfiles there.

The version check/report is independent of live-site acceptance. `verify:release`
still stops on the first failed install, preflight, build/test, audit, browser,
payment-config or SMTP-authentication check. Real sandbox transactions, webhook
DELIVERY and intended email INBOX receipt remain separate acceptance tests.

All earlier V60.x guides and QA reports are historical. The Node-22-only local
instruction in the older V60.12 guide is superseded by this patch; other original
application/security and acceptance requirements remain unchanged.
