# clean-comment-lines

Clean comment line skill for coding agents.

Coding agents over-comment. They narrate their edits, restate the code,
explain their fixes inline, and leave commented-out code behind. This skill
sets one standard for comments, applies it whenever the agent writes or
edits code, and sweeps existing files on demand.

## Rules

A comment is written for three things only:

- a non-obvious why, in one line
- a section divider in long code
- a header on a file long or complex enough to need one

Everything else is deleted before the edit is finished:

- change narration ("switched X to Y because the old approach didn't work")
- comments that restate the code ("increment i")
- references to the conversation ("as requested")
- inline explanations of a fix
- commented-out code
- multi-sentence comments on ordinary lines

Existing comments are kept unless the code they describe changed, the file's
comment style and width are respected, and punctuation and divider formatting
are enforced. The full rule set is in
[SKILL.md](skills/clean-comment-lines/SKILL.md), with before and after
examples in [examples](skills/clean-comment-lines/examples).

## Use

Install it and it applies on its own, every time the agent writes or edits
code. Nothing to run.

The `/` command is optional, for old files or direct orders. In Claude Code:

```
/clean-comment-lines src/foo.ts       # sweep one file, comments only
/clean-comment-lines bar.ts fix this  # do the task, keep comments clean
/clean-comment-lines                  # sweep the files changed this session
```

Skills load only when the agent decides they apply. For guaranteed coverage
on every edit, copy the "Never write these" section of SKILL.md into your
CLAUDE.md or AGENTS.md.

## Install

Any agent the skills CLI supports (Claude Code, Codex, Cursor, OpenCode, and
70+ others):

```
npx skills add oynozan/clean-comment-lines
```

Claude Code, as a plugin:

```
/plugin marketplace add oynozan/clean-comment-lines
/plugin install clean-comment-lines
```

Or copy `skills/clean-comment-lines/` into your agent's skills directory,
for example `~/.claude/skills/` (all projects) or `.claude/skills/` (one
project).

## License

MIT