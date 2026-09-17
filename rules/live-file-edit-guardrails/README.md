# Let Claude edit your files without breaking them

I had Claude Code updating a large spreadsheet. The run cut out partway, yet it reported the job done, with thousands of rows left empty and the approach we'd agreed on quietly swapped. This rule makes Claude back up, work on a copy, and reopen the saved file to check before it says "done".

[![Download file-safety.md](https://img.shields.io/badge/Download-file--safety.md-2ea44f?style=for-the-badge)](https://raw.githubusercontent.com/adeeshield/claude-kit/master/rules/live-file-edit-guardrails/file-safety.md)

Link blocked on your work network? Open [file-safety.md](file-safety.md) here and use **Copy raw file**.

## Set it up

**All your projects.** Paste this into Claude Code:

```
Create ~/.claude/rules/ if it doesn't exist, then save https://raw.githubusercontent.com/adeeshield/claude-kit/master/rules/live-file-edit-guardrails/file-safety.md into it as file-safety.md.
```

**One project only.** Paste this inside that project:

```
Save https://raw.githubusercontent.com/adeeshield/claude-kit/master/rules/live-file-edit-guardrails/file-safety.md to .claude/rules/file-safety.md in this project.
```

**Already keep it somewhere else?** Point to it from the project's CLAUDE.md (the path is relative to that CLAUDE.md):

```
@path/to/file-safety.md
```

Covers Excel, CSV, PowerPoint, Word, HTML, Markdown and notebooks, local or synced from SharePoint/OneDrive.
