# Live file edit controls for Claude Code

Applies to files people work in: spreadsheets, CSVs, decks, documents and notebooks (.xlsx/.xlsm, .csv, .pptx, .docx, .ipynb and similar), plus any other file the user says is live or shared. Local or synced (OneDrive, SharePoint, Google Drive, Dropbox, iCloud). It applies however you edit the file: through the app, a script, or a library like openpyxl. A "live" file is the copy the user or their team actually works in.

It doesn't apply to files only you work with, like source code or config, unless the user says otherwise.

Steps marked **Windows** or **Mac** apply only on that system. Everything else applies everywhere.

## Before touching a file
- Confirm the exact location of the live file with the user (full path or URL) before the first edit. Never infer it from old scripts, earlier sessions, or a matching file name.
- Ask the user to close the file everywhere: desktop app, browser tab, web view. Wait for a clear "closed". Never assume.
- Then check it yourself:
  - **Windows:** look for running app processes (e.g. `EXCEL.EXE`) and `~$` lock files next to the file.
  - **Mac:** check whether the app is still running (e.g. `pgrep -l "Microsoft Excel"`) and run `lsof` on the file. Some apps don't keep the file open, so an empty `lsof` alone doesn't prove it's closed. Also look for `~$` lock files next to it.
  - If a lock file remains with the app closed, report it and ask before deleting.
- Back up first. Make a timestamped copy before the first edit. For a synced file, make the copy through the app or its web version, not by copying out of the sync folder, and confirm version history is available.

## Doing the work
- Build and verify on a copy first. Apply to the live file only after the copy passes, using the same steps.
- Never automate the user's open app session, and never touch other files open there.
  - **Windows:** automate in a separate, hidden app instance.
  - **Mac:** apps like Excel usually run as a single instance, so there's no separate hidden one. With the file closed, edit it with a file library (e.g. openpyxl, python-pptx, python-docx), or ask the user before scripting the app.
  - Using a library on either system: first check it keeps everything the file has (charts, pivots, macros, images, formatting). If it doesn't, stop and ask.
- Don't change the user's app settings (e.g. Excel's table auto-fill) without asking. Changes made by automation can persist in the user's own app, even from a hidden instance. If a change is needed, ask, restore the original value afterwards, and confirm it's restored.
- One writer at a time. Never have two processes or apps open the same file for editing.
- For a synced file, don't write through the local sync folder while it's syncing or open elsewhere, or sync can create conflict copies. Edit it through the app using the file's URL, or pause syncing, make the change, resume, and check that no conflict copy appeared.
- Don't change an agreed approach mid-build. If the data blocks the plan, stop and ask, stating what was found and the options.

## After
- Verify by reopening the saved file fresh: values, error cells and row counts for spreadsheets; slide or page counts and content for decks and documents. Don't trust the session that wrote it.
- If a run was interrupted (connection drop, timeout, app quit), inspect the file's real state before continuing. Never report an interrupted step as done.
- Close anything you opened and confirm nothing still holds the file (**Windows:** no leftover app processes or `~$` files; **Mac:** app quit and `lsof` shows nothing). Then tell the user it's safe to reopen.
- Report plainly what changed, what was verified, and what wasn't.
