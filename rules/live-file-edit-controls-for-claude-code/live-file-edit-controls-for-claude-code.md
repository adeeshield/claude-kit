# File safety — working on the user's files

Covers any file the user owns or shares: .xlsx/.xlsm, .csv, .pptx, .docx, .html, .md, .ipynb, and others. It covers both local files and synced SharePoint/OneDrive files. A "live" file is the copy the user or team actually works in.

## Before touching a file
- Ask the user to close the file everywhere: desktop app, browser tab, SharePoint web view. Wait for a clear "closed". Never assume.
- Then check it yourself. Look for running Office processes holding the file, and for `~$` lock files next to it. If a lock file remains with the app closed, report it and ask before deleting.
- Back up first. Make a timestamped copy before the first edit. For a SharePoint/OneDrive file, save a snapshot copy through the app, not by copying the sync folder.

## Doing the work
- Build and verify on a copy first. Apply to the live file only after the copy passes, using the same steps.
- Automate in a separate, hidden app instance. Never attach to the user's open session, and never touch other files open there.
- One writer at a time. Never have two processes or apps open the same file for editing.
- Edit cloud files through their URL in the app, not through the local sync folder, so sync doesn't produce conflict copies.
- Don't change an agreed approach mid-build. If the data blocks the plan, stop and ask, stating what was found and the options.

## After
- Verify by reopening the saved file fresh: values, error cells, row counts. Don't trust the session that wrote it.
- If a run was interrupted (connection drop, timeout, app quit), inspect the file's real state before continuing. Never report an interrupted step as done.
- Close and quit the app instance, confirm nothing still holds the file, then tell the user it's safe to reopen.
- Report plainly what changed, what was verified, and what wasn't.
