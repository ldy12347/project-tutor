# Changelog

## [0.4.2] — 2026-11-11

### Changed
- Set Mermaid as the default first-choice format for visual explanations of business flows, branches, architecture relationships, data flows, sequences, and state transitions.
- Defined ASCII diagrams as the compatibility fallback when the current Agent client is known not to render Mermaid or the user reports that Mermaid is displayed as raw source.
- Reserved generated images for complex spatial layouts that cannot be explained clearly with Mermaid or ASCII.
- Added conservative Mermaid syntax guidance to improve compatibility across renderers and avoid renderer-specific features.
- Clarified that Mermaid source belongs in a fenced Mermaid block for rendering, not in an ordinary code explanation.
- Updated README and Codex UI metadata to describe the Mermaid-first strategy.


## [0.4.1] — 2026-11-11

### Fixed
- Removed the repeated permission prompt at chapter boundaries. Starting a learning plan authorizes the tutor to proceed through its planned chapters.
- Required the tutor to announce the next chapter and continue automatically instead of asking "要继续学习下一节吗？".
- Added explicit pause/stop phrases and clarified that the roadmap is paused only when the user asks, the goal is complete, or essential scope information is missing.
- Clarified that completing a chapter is a progress marker, not a reason to stop the lesson.


## [0.4.0] — 2026-11-11

### Added
- Added visual-first teaching for business flows, architecture, module relationships, data flow, and state transitions.
- Added diagram selection guidance: flowcharts, branch diagrams, component maps/swimlanes, data-flow diagrams, and state diagrams.
- Added compact diagram rules: one main diagram at a time, Chinese labels, 3–5 short supporting points, and progressive expansion.
- Added project-specific learning roadmaps, normally 3–5 chapters for broad learning goals.
- Added explicit chapter states: 未开始, 进行中, and 已完成.
- Added chapter-completion handoff: summarize the current chapter, recommend the next chapter, explain why it follows, and ask whether to continue.

### Fixed
- Prevented a completed knowledge point or chapter from being mistaken for completion of the whole project-learning goal.
- Clarified that connected knowledge points should advance automatically within the current chapter.
- Required the tutor to distinguish knowledge-point completion, chapter completion, and overall roadmap completion when asked "学完了吗？".
- Required a clear continue/pause decision at a genuine chapter boundary instead of a vague optional offer.

### Changed
- Updated the learning-record template to track roadmap chapters and their progress.
- Updated the README and Codex UI metadata to describe visual-first and roadmap-based teaching.

## [0.3.0] — 2026-11-11

### Added
- Added cross-platform installation and compatibility documentation for Codex, Claude Code, Cursor, GitHub Copilot in VS Code, and Gemini CLI.
- Added GitHub CLI installation commands using the exact nested skill path in this repository.
- Documented user-scope and project-scope installation, host-specific invocation, and post-install verification.
- Clarified the boundary between the portable Agent Skills core and optional Codex-specific UI metadata.
- Documented that skill compatibility does not itself grant repository access or file-reading tools.

## [0.2.1] — 2026-11-11

### Fixed
- Added an explicit continuous teaching loop so an active lesson advances after the user answers a comprehension check.
- Clarification questions are answered directly, then the AI resumes the next not-yet-explained concept.
- Prevented a correct answer or a simple confirmation from being treated as the end of the lesson.
- Removed the expectation that users must repeatedly type "继续" after each teaching point.
- Defined clear stopping conditions: explicit pause/finish, completed learning goal, required user scope decision, or a change of task.

## [0.2.0] — 2026-11-11

### Changed
- Reframed the teaching approach from question-first to AI explanation first, questions second.
- Added an opening introduction and an explicit three-mode selection: Hybrid, Explanation, and Guided.
- Made Hybrid the recommended default.
- Clarified that repository inspection and source-code tracing are the AI's responsibility; users are not expected to read source files.
- Reordered learning around concrete business scenarios, end-to-end flows, component responsibilities, data/state ownership, design decisions, and relevant failure paths.
- Added strict question-quality checks: questions must be answerable from context already explained.
- Changed the response to "I don't know" or "I don't understand": stop the quiz and explain again with simpler language or examples.
- Updated progress levels to measure business and architecture understanding rather than source-code navigation.
- Updated the learning-record template to capture the selected mode, explanations, business flows, and evidence checked by the AI.

## [0.1.0] — 2026-11-11

### Added
- Initial Codex skill structure.
- Hybrid teaching rules and repository evidence standards.
- Learning-record template.
- Initial README and installation instructions.
