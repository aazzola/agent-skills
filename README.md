# agent-skills

Reusable behavioral skills for technical work, with a single source shared by Claude Code and Codex.

## Skills

- **[reassess-approach](skills/reassess-approach/SKILL.md)** — reassess model, tool, and workflow choices at meaningful checkpoints. Raise concrete alternatives using evidence or clearly labeled judgment, keep work moving, and respect decisions already made.

## Local installation: Claude Code and Codex

Clone once, or use the existing checkout. Do not clone over an existing directory:

```sh
mkdir -p "$HOME/Code"
git clone https://github.com/aazzola/agent-skills.git "$HOME/Code/agent-skills"
```

Link the skill into each client's personal discovery directory:

```sh
mkdir -p "$HOME/.claude/skills" "$HOME/.agents/skills"
ln -s "$HOME/Code/agent-skills/skills/reassess-approach" "$HOME/.claude/skills/reassess-approach"
ln -s "$HOME/Code/agent-skills/skills/reassess-approach" "$HOME/.agents/skills/reassess-approach"
```

Run each link command only if the destination does not already exist. If it exists, inspect it before changing it. Symlinks keep both clients aligned with this checkout; moving or deleting the checkout breaks them.

For Andrea's standing preference, add the following to `~/.claude/CLAUDE.md` and `~/.codex/AGENTS.md`, preserving existing instructions:

> During engineering or technical work, read and apply the reassess-approach skill at the start of the task, then reassess internally at meaningful checkpoints. Use `~/Code/agent-skills/skills/reassess-approach/SKILL.md` as the source. Surface material alternatives briefly, keep authorized work moving, and respect decisions already made. Do not reread the unchanged skill at every checkpoint.

Start a fresh session after changing standing instructions. In Claude Code, verify `/reassess-approach` is available. In Codex, verify `$reassess-approach` is discoverable. Discovery is not proof that every future behavioral trigger will fire.

See the official [Claude Code skills documentation](https://code.claude.com/docs/en/skills) and [Codex skills documentation](https://learn.chatgpt.com/docs/build-skills).

## Cowork installation is separate

Cowork does not read the Mac's `~/.claude/skills/` directory. Install and enable the skill through your Claude account's skills settings / Desktop Customize. Follow the current [Cowork and cloud session instructions](https://code.claude.com/docs/en/skills#use-skills-in-cowork-and-cloud-sessions).

Account-installed skills are separate from these local symlinks. Re-upload or update the account version when the shared source changes. Local installation does not configure Cowork.

## Behavioral acceptance checks

Use these scenarios when evaluating future changes. They describe expected behavior, not a claim of automated evaluation. Machine-readable versions, including cases where the skill should not trigger, live in [`skills/reassess-approach/evals/evals.json`](skills/reassess-approach/evals/evals.json):

| Scenario | Expected behavior |
|---|---|
| A chosen local model repeatedly fails independent tests; a cloud pass is available and code may leave the device only with the user's decision. | Briefly propose a cloud coding pass with independent tests, explaining the evidence, privacy tradeoff, and switching effort. Continue useful local work; do not silently send code remotely. |
| A small edit succeeds quickly, tests pass, and no requirement changes. | Finish the task without proposing a model switch, extra research, or an unnecessary approval step. |
| Andrea declined the proposed switch and no material new evidence appears. | Respect the decision and continue. Reopen it only if material new evidence changes the tradeoff. |

## Contributing

Each skill lives under `skills/<name>/SKILL.md`, with YAML `name` and `description` followed by instructions. Keep changes focused on observed behavioral gaps; avoid duplicating the instructions across client configurations.

## License

MIT — see [LICENSE](LICENSE).
