# File safety rule

A Claude Code rule file for agents that edit files the user owns or shares — spreadsheets, docs, notebooks, and synced SharePoint/OneDrive files.

It sets the discipline around: closing files before editing, backing up first, working on a copy before touching the live file, one writer at a time, and verifying the result by reopening the saved file fresh instead of trusting the session that wrote it.

## Use it

Drop [`file-safety.md`](file-safety.md) into `~/.claude/rules/` (or your equivalent) so it loads for any session that touches user files.
