# Project Tutor

**Project Tutor** is an explain-first, evidence-grounded learning skill for understanding existing software projects in Codex.

It is designed for developers who want to understand a project's **business behavior and architecture** without having to read and decipher the source code themselves. The AI inspects the repository, traces real execution paths, and translates the implementation into clear explanations and practical examples.

**Current version: v0.2.1**

## What changed in v0.2.1

Version 0.2.1 fixes lesson continuity: after answering a comprehension check or a clarification question, the AI resumes the next planned teaching step instead of stopping. Users should not need to type "continue" after every small exchange.

See [CHANGELOG.md](CHANGELOG.md) for details.

## What changed in v0.2.0

Version 0.2.0 changes the teaching model from question-first to **AI explanation first, questions second**.

- Introduces the tutor and offers a learning-mode choice at the beginning.
- Provides three modes: Hybrid (recommended), Explanation, and Guided.
- Requires the AI to explain business context and technical terms before asking questions.
- Makes source-code inspection the AI's responsibility; users are not assigned code-reading homework.
- Treats "I don't know" or "I don't understand" as a signal to explain differently, not to ask harder questions.
- Measures progress by the user's understanding of business flows and architecture, not their ability to navigate source files.

See [CHANGELOG.md](CHANGELOG.md) for details.

## Learning modes

| Mode | How it works |
|---|---|
| **Hybrid (recommended)** | The AI explains first. Simple topics are explained directly; complex topics are broken into steps, followed by an optional understanding check. |
| **Explanation** | The AI leads with clear explanations and examples. No quizzes unless the user asks. |
| **Guided** | The AI explains the necessary context first, then helps the user connect ideas through one focused question at a time. No blind guessing. |

If the user does not want to choose, Hybrid is the default.

## What it helps you understand

1. **Business domain** — users, business objects, user journeys, rules, and state transitions.
2. **Architecture** — entry points, processes, module responsibilities, service boundaries, and communication paths.
3. **End-to-end flows** — how a real request or event travels through the system and produces an observable result.
4. **Data and state ownership** — where important data is created, maintained, persisted, and synchronized.
5. **Design decisions** — the requirements and constraints behind a design, plus its trade-offs.
6. **Relevant failure paths** — validation, timeout, retry, duplicate delivery, partial failure, and recovery where applicable.

## Install across AI coding tools

Project Tutor uses the open Agent Skills format. Its core teaching instructions are shared; each coding assistant uses its own skill discovery and invocation mechanism.

See **[Installation and compatibility](docs/INSTALLATION.md)** for installation commands for Codex, Claude Code, Cursor, GitHub Copilot in VS Code, and Gemini CLI.

Quick install with GitHub CLI (Codex example):

```bash
gh skill install ldy12347/project-tutor project-tutor/SKILL.md --agent codex --scope user
```

The GitHub CLI installer supports multiple AI coding agents and chooses the host-specific destination. If your installed GitHub CLI does not provide `gh skill install`, use the manual installation instructions in the compatibility guide.

## Use

Open the target repository in Codex and invoke:

```text
$project-tutor
```

On first launch, Project Tutor introduces itself and asks you to choose a learning mode. You can also specify one immediately:

```text
$project-tutor

Use Hybrid mode. Help me understand this project's business and architecture.
Start with a real user scenario. Explain the flow in plain Chinese.
I don't want to read source code; inspect it for me and show concise evidence.
```

Useful phrases during a session:

- `混合模式` — explain first, then optionally check understanding.
- `讲解模式` — explain without quizzes.
- `引导模式` — explain context, then guide reasoning.
- `继续` — continue the next explanation step.
- `直接解释` — skip the understanding check.
- `换个例子` — use another concrete example.
- `我没听懂` — stop questioning and explain more simply.
- `检查代码依据` — verify the explanation against the source.
- `总结本节` — summarize what has been learned.

## Repository structure

```text
project-tutor/
├── README.md
├── CHANGELOG.md
├── VERSION
└── project-tutor/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── learning-record-template.md
```

## Safety and evidence

- Read and explain; do not modify application source code, tests, configuration, dependencies, or Git metadata.
- Do not start services, run tests or migrations, install packages, or write to databases by default.
- Do not create learning records unless the user explicitly asks to save progress.
- Verify important claims against implementation and distinguish code facts, documented intent, inference, and unknowns.
- Source paths and line references are evidence for the explanation, not homework for the user.

## License

No license has been added yet. The repository is publicly viewable, but reuse and redistribution are not automatically granted. A license can be added in a future release.
