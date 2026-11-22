# optical-alignment-skill

An agent skill for optical icon alignment: center icons by weight and size, not by bounding box.

## Install

```bash
npx skills add TheoSlater/optical-alignment-skill
```

Or install just this skill:

```bash
npx skills add TheoSlater/optical-alignment-skill --skill optical-icon-alignment
```

## Skills

| Skill | What it does |
| --- | --- |
| [`optical-icon-alignment`](skills/optical-icon-alignment/SKILL.md) | Nudges icons to optical center in small px steps and reports each offset |

## Compatibility

Follows the [Agent Skills specification](https://agentskills.io). Installs to `.agents/skills/` (read by Codex, Cursor, and others), with a symlink for Claude Code at `.claude/skills/`.

## Version

MIT licensed (see [LICENSE](LICENSE)).

`0.1.1` (set in `metadata.version` in each `SKILL.md`; releases are tagged `vX.Y.Z`).
