# Copilot Agent Skills Examples

This directory contains example Agent Skills that show how to teach GitHub Copilot specialized, reusable capabilities.

## What are Agent Skills?

A skill is a **directory** containing a `SKILL.md` file (plus any optional scripts or resources). Copilot reads each skill's `name` and `description`, and loads the full instructions only when the skill is relevant to what you asked.

Agent Skills follow an [open standard](https://agentskills.io) and work across GitHub Copilot in VS Code, GitHub Copilot CLI, and the Copilot cloud agent.

## Directory Layout

Project skills live in `.github/skills/`, with one subdirectory per skill:

```
.github/skills/
├── api-docs/
│   └── SKILL.md
├── pr-review/
│   └── SKILL.md
└── write-tests/
    └── SKILL.md
```

> [!IMPORTANT]
> The file must be named exactly `SKILL.md`. Names such as `my-skill.SKILL.md` are not discovered.

Copilot also recognises `.claude/skills/` and `.agents/skills/` for project skills, and `~/.copilot/skills/` for personal skills that apply across all your repositories.

## Available Example Skills

### 1. `write-tests/`
Guides Copilot to write comprehensive unit tests, covering:
- AAA pattern (Arrange, Act, Assert)
- Descriptive test naming conventions
- Mocking external dependencies
- Happy paths and edge cases

### 2. `pr-review/`
Guides Copilot to review pull requests against consistent criteria:
- Code quality and readability
- Test coverage verification
- Security considerations
- Documentation requirements
- Performance and scalability

### 3. `api-docs/`
Guides Copilot to generate API documentation:
- JSDoc format for functions
- REST endpoint documentation
- Request/response examples
- Error case documentation

## How to Use These Skills

1. **Open this repository** in VS Code with GitHub Copilot, or in GitHub Copilot CLI — project skills are discovered automatically.
2. **Ask a related question**, for example "add unit tests for this module". Copilot matches your request against each skill's `description` and loads the matching skill.
3. **Invoke one explicitly** if you prefer, for example "use the write-tests skill for this file".
4. **Customize** — copy a skill directory and edit it to match your team's conventions.

## Creating Your Own Skill

1. Create a directory under `.github/skills/` named after your skill, using lowercase and hyphens.
2. Inside it, create a `SKILL.md` file with YAML frontmatter:

   ```yaml
   ---
   name: your-skill-name
   description: What this skill does and when Copilot should use it.
   ---
   ```

3. Write the instructions in the Markdown body below the frontmatter.
4. Optionally add scripts or reference files to the same directory and refer to them from `SKILL.md`. Use the `allowed-tools` frontmatter field to pre-approve the tools the skill needs.

> [!TIP]
> The `description` is the only signal Copilot uses to decide whether a skill is relevant, so state both **what** the skill does and **when** to use it. There is no `applyTo` field for skills — glob-based targeting belongs to [custom instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions) (`.instructions.md`).

## Skills vs Custom Instructions

| | Agent Skills | Custom Instructions |
|---|---|---|
| **Purpose** | Teach specialized capabilities and workflows | Define coding standards and guidelines |
| **Loaded** | On demand, when relevant | Always, or via `applyTo` glob patterns |
| **Content** | Instructions, scripts, examples, resources | Instructions only |
| **Location** | `.github/skills/<name>/SKILL.md` | `.github/copilot-instructions.md` |

## Best Practices

- **Be specific** — provide concrete examples and clear guidelines
- **Keep focused** — each skill should address one task or workflow
- **Write a strong description** — it determines when the skill is selected
- **Use examples** — show Copilot exactly what patterns you expect
- **Version control** — check skills into your repository so the whole team benefits

## Learn More

Complete **Path 2: Build with Copilot Agents** to learn more about Agent Skills and other advanced Copilot features:
- [Workshop Home](../../index.html)
- [Build with Copilot Agents](../../github-copilot-workshop/pro-features.html)

## Resources

- [Adding agent skills for GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-skills)
- [Use Agent Skills in VS Code](https://code.visualstudio.com/docs/agent-customization/agent-skills)
- [Copilot customization cheat sheet](https://docs.github.com/en/copilot/reference/customization-cheat-sheet)
- [Add repository custom instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
