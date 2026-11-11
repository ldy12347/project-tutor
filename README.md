# Project Tutor

**Project Tutor** is an explain-first, visual-first, evidence-grounded learning skill for understanding existing software projects across compatible AI coding assistants.

It is designed for developers who want to understand a project's **business behavior and architecture** without having to read and decipher the source code themselves. The AI inspects the repository, traces real execution paths, and translates the implementation into simple diagrams and concise explanations.

**Current version: v0.4.0**

## What changed in v0.4.0

Version 0.4.0 combines three improvements based on real learning feedback:

- **Visual-first explanations:** use compact flowcharts, component maps, data-flow diagrams, and state diagrams for topics that benefit from visualization. Keep supporting text short.
- **Continuous teaching:** move automatically through connected knowledge points within a chapter; do not stop after a correct answer or clarification.
- **Learning roadmap and chapter handoff:** maintain a project-specific 3–5 chapter roadmap for broad learning goals. At the end of a chapter, summarize progress, recommend the next chapter, and explicitly ask whether to continue.

See [CHANGELOG.md](CHANGELOG.md) for details.

## Learning modes

| Mode | How it works |
|---|---|
| **Hybrid (recommended)** | The AI explains first. Simple topics are explained directly; complex topics use diagrams and short explanations, followed by an optional understanding check. |
| **Explanation** | The AI leads with visual explanations and examples. No quizzes unless the user asks. |
| **Guided** | The AI explains the necessary context first, then helps the user connect ideas through one focused question at a time. No blind guessing. |

If the user does not want to choose, Hybrid is the default. Visual-first is the default presentation style for flows, architecture, and state changes; it is not an additional learning mode.

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

Open the target repository in your AI coding assistant and invoke Project Tutor using that host's skill mechanism. For example, in Codex:

```text
$project-tutor
```

On first launch, Project Tutor introduces itself, asks you to choose a learning mode, inspects the repository, and proposes a project-specific learning roadmap. It then starts the first chapter.

Useful phrases during a session:

- `混合模式` — explain first, then optionally check understanding.
- `讲解模式` — explain without quizzes.
- `引导模式` — explain context, then guide reasoning.
- `图解模式` — prioritize diagrams for flows, architecture, and state changes.
- `文字模式` — use concise prose and tables.
- `只看主流程` — show only the main path.
- `展开这个节点` — explain one selected part of a diagram.
- `继续` — continue within the current chapter, or start the next chapter after agreeing.
- `直接解释` — skip the understanding check.
- `换个例子` — use another concrete example.
- `我没听懂` — stop questioning and explain more simply.
- `检查代码依据` — verify the explanation against the source.
- `总结本节` — summarize the chapter and recommend the next one.

## Repository structure

```text
project-tutor/
├── README.md
├── CHANGELOG.md
├── VERSION
├── docs/
│   └── INSTALLATION.md
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
- Keep diagrams grounded in the actual implementation. Do not invent components or relationships to make a diagram look complete.

## License

No license has been added yet. The repository is publicly viewable, but reuse and redistribution are not automatically granted.
