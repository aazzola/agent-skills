# agent-skills

A small collection of reusable behavioral instructions for AI coding agents — packaged today as [Claude Code / Claude Cowork skills](https://docs.claude.com/en/docs/claude-code/skills) (a `SKILL.md` Claude loads automatically when a task matches), but the instructions themselves name no vendor and read fine pasted into another assistant's system prompt or custom instructions.

## Skills

- **[reassess-approach](skills/reassess-approach/SKILL.md)** — prompts Claude to periodically ask "is this still the best approach?" during technical work, and to speak up with a concrete, evidence-grounded alternative when one would materially help, without turning every suggestion into a permission request or a research project.

## Installing a skill

Copy the skill's folder into your skills directory:

```bash
git clone https://github.com/<your-username>/agent-skills.git
cp -r agent-skills/skills/reassess-approach ~/.claude/skills/reassess-approach
```

Claude Code and Claude Cowork pick up skills under `~/.claude/skills/` automatically — no restart needed for most clients. See the [skills documentation](https://docs.claude.com/en/docs/claude-code/skills) for project-scoped and plugin-based installation instead.

## Contributing

Each skill lives in its own folder under `skills/` with a single `SKILL.md` (YAML frontmatter with `name` and `description`, then the instructions as Markdown). Keep skills narrow and evidence-grounded rather than broad and aspirational — a skill should change what Claude *does*, not just restate good intentions.

## License

MIT — see [LICENSE](LICENSE).
