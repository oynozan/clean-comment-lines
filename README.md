# clean-comment-lines

Clean comment line skill for coding agents.

Stops Claude Code from writing change-narration comments ("switched X to Y
because the old approach didn't work"). Comments describe the code as it is
now. History stays in git.

Comments are allowed for three things only: a non-obvious *why*, section
dividers in long code, and a header on a long file. Anything else is deleted
before the edit is finished.

## Install

As a plugin:

```
/plugin marketplace add oynozan/clean-comment-lines
/plugin install clean-comment-lines@clean-comment-lines
```

Or copy `skills/clean-comment-lines/` into `~/.claude/skills/` (all projects)
or `.claude/skills/` (one project).

## Use

The skill loads on its own when Claude writes or edits code. To clean up a
file that already has the problem:

```
/clean-comment-lines src/foo.ts
```

Skills load only when Claude decides they apply. For guaranteed coverage on
every edit, copy the "Never write these" section of `SKILL.md` into your
`CLAUDE.md`.

## License

MIT
