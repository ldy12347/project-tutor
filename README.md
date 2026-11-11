# Project Tutor

**Project Tutor** is a hybrid, evidence-grounded learning skill for understanding existing software projects in Codex.

It helps developers build an independent mental model of both the **business behavior** and the **system architecture**—not just memorize file names or receive a large, unexplained architecture dump.

## Teaching approach

- **Simple questions:** explain the relevant concept or code fact directly.
- **Complex topics:** use guided, Socratic questions—one focused question at a time.
- **Progressive hints:** move from conceptual hints to code pointers, partial explanations, and finally a full explanation when needed.
- **Evidence first:** ground important conclusions in actual implementation, tests, and project documents. Distinguish observed facts, documented intent, inference, and unknowns.
- **Read-only by default:** learning should not change the project.

## What it helps you understand

1. **Business domain** — actors, business objects, user journeys, rules, and state transitions.
2. **Architecture** — entry points, processes, module responsibilities, service boundaries, and communication paths.
3. **End-to-end flows** — trace one real request or event through the code to its observable result.
4. **Data and state ownership** — identify who creates, reads, writes, persists, and synchronizes each important state.
5. **Design decisions** — reason from requirements and constraints to design choices and trade-offs.
6. **Failure paths** — inspect relevant validation, timeout, retry, duplicate-delivery, and partial-failure behavior.

The workflow adapts to the user's learning goal; it does not force every topic into every session.

## Install for Codex

Clone this repository:

```bash
git clone https://github.com/ldy12347/project-tutor.git
cd project-tutor
```

Install the skill for your user:

```bash
mkdir -p ~/.agents/skills
cp -R project-tutor ~/.agents/skills/
```

The installed skill directory should be:

```text
~/.agents/skills/project-tutor/
```

To install it for only one repository, copy the `project-tutor` directory into that repository's `.agents/skills/` directory instead.

If Codex does not show the skill immediately, restart Codex and check the skills picker.

## Use

Open the target repository in Codex and invoke:

```text
$project-tutor
```

A useful starting prompt:

> Help me understand this repository's business and architecture. Start with the core business scenario. Explain simple questions directly; for complex flows, module boundaries, state ownership, and design trade-offs, guide me with one question at a time. Inspect the repository read-only and support important conclusions with code evidence. Do not produce a full architecture summary upfront.

You can also say:

- **开始学习** — inspect the project and establish a learning starting point.
- **继续** — continue with one next question or step.
- **直接解释** — switch to a direct explanation.
- **提示** — provide the next progressive hint.

## Repository structure

```text
project-tutor/
├── README.md
└── project-tutor/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── learning-record-template.md
```

## Safety defaults

- Read and explain; do not modify application source code, tests, configuration, dependencies, or Git metadata.
- Do not start services, run tests or migrations, install packages, or write to databases by default.
- Do not create learning records unless the user explicitly asks to save or resume progress.
- Do not invent runtime behavior or design rationale. Clearly mark evidence gaps and inferences.

## License

No license has been added yet. Until a license is selected, the repository is publicly viewable but reuse and redistribution are not automatically granted.
