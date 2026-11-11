# Installation and compatibility

Project Tutor uses the open Agent Skills format: a skill directory containing `SKILL.md` plus optional supporting files. The teaching instructions are kept in one shared file; each AI coding assistant discovers and invokes skills through its own host integration.

## Recommended: install with GitHub CLI

The GitHub CLI provides `gh skill install`, which installs a skill into the selected agent's user or project skill directory.

First, check that your GitHub CLI version includes the skill command:

```bash
gh skill install --help
```

Run one command for the agent you use. These commands install the current default-branch version for your user account, making it available across projects:

### OpenAI Codex

```bash
gh skill install ldy12347/project-tutor project-tutor/SKILL.md --agent codex --scope user
```

Personal skill location: `~/.agents/skills/project-tutor/`

Invoke in Codex with:

```text
$project-tutor
```

### Claude Code

```bash
gh skill install ldy12347/project-tutor project-tutor/SKILL.md --agent claude-code --scope user
```

Personal skill location: `~/.claude/skills/project-tutor/`

Invoke in Claude Code with:

```text
/project-tutor
```

Claude Code skills follow the Agent Skills open standard. Claude Code also supports additional vendor-specific frontmatter and runtime features; Project Tutor intentionally uses only the shared core fields.

### Cursor

```bash
gh skill install ldy12347/project-tutor project-tutor/SKILL.md --agent cursor --scope user
```

Use Cursor's Agent chat and ask it to use Project Tutor. Skill discovery and invocation details can vary by Cursor version; confirm that the installed skill is visible to the Agent before starting a lesson.

### GitHub Copilot in VS Code

```bash
gh skill install ldy12347/project-tutor project-tutor/SKILL.md --agent github-copilot --scope user
```

Personal skill location: `~/.copilot/skills/project-tutor/`

In VS Code, open a new Chat session and select Project Tutor from the skills list or ask Copilot to use it. Agent Skills must be enabled in VS Code settings if the feature is not already enabled.

### Gemini CLI

```bash
gh skill install ldy12347/project-tutor project-tutor/SKILL.md --agent gemini-cli --scope user
```

Gemini CLI supports user skills under `~/.gemini/skills/` and the interoperable `~/.agents/skills/` alias. Check discovery with:

```text
/skills list
```

Then ask Gemini CLI to use Project Tutor for the current repository.

## Install for only one repository

Run the same command from inside the target repository, replacing `--scope user` with `--scope project`.

For example, for Codex:

```bash
gh skill install ldy12347/project-tutor project-tutor/SKILL.md --agent codex --scope project
```

Project-scope installation writes into the target repository's supported skill directory. Commit that skill directory if you want teammates to share it.

## Manual installation

If your GitHub CLI does not include `gh skill install`, clone the repository and copy the skill folder into the host's supported location.

```bash
git clone https://github.com/ldy12347/project-tutor.git
```

Copy the contents of the repository's `project-tutor/` directory (the one containing `SKILL.md`) into the destination folder:

| Host | Personal skill directory |
|---|---|
| Codex | `~/.agents/skills/project-tutor/` |
| Claude Code | `~/.claude/skills/project-tutor/` |
| GitHub Copilot in VS Code | `~/.copilot/skills/project-tutor/` |
| Gemini CLI | `~/.gemini/skills/project-tutor/` |

For Cursor, prefer the GitHub CLI installer with `--agent cursor` so it selects the destination supported by the installed version.

## Compatibility notes

- The portable core is `project-tutor/SKILL.md` and its referenced files. It uses the standard `name` and `description` frontmatter fields.
- `project-tutor/agents/openai.yaml` is optional Codex-specific UI metadata. Other hosts can ignore it.
- The skill's teaching workflow is instruction-based. It does not depend on Codex-only tools or APIs.
- A compatible host still needs repository access and file-reading tools for the AI to inspect the codebase. The skill cannot grant those permissions by itself.
- Skill discovery, explicit invocation syntax, and support for optional frontmatter vary by host and version. Installing a folder does not guarantee that every host will automatically select it.
- After installation, start a fresh session and verify that the skill is visible or invoke it explicitly before relying on it.

## Official references

- [Agent Skills specification](https://agentskills.io/specification)
- [Codex skills](https://developers.openai.com/codex/skills/)
- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [VS Code Agent Skills](https://code.visualstudio.com/docs/agent-customization/agent-skills)
- [Gemini CLI Agent Skills](https://geminicli.com/docs/cli/using-agent-skills/)
- [GitHub CLI: gh skill install](https://cli.github.com/manual/gh_skill_install)
- [Cursor documentation](https://docs.cursor.com/)
