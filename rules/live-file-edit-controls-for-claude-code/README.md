# Let Claude edit your files without breaking them

For three sessions, Claude Code edited my own copy of a spreadsheet, sure it was my team's file: an old script pointed there, and both had similar names. Another run cut out halfway, still reported "done", and left thousands of rows empty. Nothing in my setup told it to check which file was real, back up first, or reopen the file before saying "done".

So I wrote those controls down: confirm which file is the real one, close it everywhere, back up, work on a copy, leave app settings alone, one writer at a time, stop and ask if the plan breaks, and verify the saved file fresh. This is how I built control over what Claude does when it touches a live file. Works on Windows and Mac.

It's slower and uses more tokens. Most times, caution is the right cost: broken files cost more.

## Why a rules file

I didn't want to paste these steps into every project. A file in `~/.claude/rules/` fixes that:

- **Works in every session.** It loads no matter which project you open.
- **Keeps project instructions short.** Your CLAUDE.md files stay about the project, not repeated safety steps.
- **Still pluggable.** You can pull the same file into one project's instructions with `@path`.
- **One file to maintain.** Change a step once, every project gets it.

*Example:* you use Claude Code on a campaign tracker, a sales notebook, and a monthly deck. Without a rules file, the same safety steps sit in three CLAUDE.md files, and a tweak means three edits. With this file in `~/.claude/rules/`, you edit it once and all three pick it up next session.

*Tip:* keep your own stories and team-specific notes in a second file in the same folder, like `my-incidents.md`. Claude reads both, and you can update this file without losing them.

### How the rules folder works

Claude Code reads every `.md` file in `~/.claude/rules/` at the start of each session, alongside your CLAUDE.md. Subfolders count too. A project can have its own `.claude/rules/` for rules that only apply there. No setup or frontmatter needed.

## Get the file

[![Get the file: live-file-edit-controls-for-claude-code.md](https://img.shields.io/badge/Get_the_file-live--file--edit--controls--for--claude--code.md-D97757?style=for-the-badge)](https://raw.githubusercontent.com/adeeshield/claude-kit/master/rules/live-file-edit-controls-for-claude-code/live-file-edit-controls-for-claude-code.md)

Opens the plain text. Save it with Ctrl+S (Windows) or Cmd+S (Mac).

Link blocked on your network? Open [the file](live-file-edit-controls-for-claude-code.md) here, click **Copy raw file**, then paste it into Claude Code with:

```
Save this as live-file-edit-controls-for-claude-code.md in ~/.claude/rules/, creating the folder if it doesn't exist.
```

## Set it up

**Recommended: all your sessions.** Paste into Claude Code:

```
Check whether ~/.claude/rules/ exists and create it if it doesn't. Then save https://raw.githubusercontent.com/adeeshield/claude-kit/master/rules/live-file-edit-controls-for-claude-code/live-file-edit-controls-for-claude-code.md into it as live-file-edit-controls-for-claude-code.md, and confirm the file is there.
```

### Other ways

**One project only.** Paste inside that project:

```
Create .claude/rules/ in this project if it doesn't exist, then save https://raw.githubusercontent.com/adeeshield/claude-kit/master/rules/live-file-edit-controls-for-claude-code/live-file-edit-controls-for-claude-code.md into it as live-file-edit-controls-for-claude-code.md.
```

**Keep the file somewhere else.** Add this line to a project's CLAUDE.md (or `~/.claude/CLAUDE.md`). The path is relative to that CLAUDE.md:

```
@path/to/live-file-edit-controls-for-claude-code.md
```

Already in `~/.claude/rules/`? No need for the `@path` line; it loads on its own.
