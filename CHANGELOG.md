# Changelog

## [0.2.1] — 2026-11-11

### Fixed
- Added an explicit continuous teaching loop so an active lesson advances after the user answers a comprehension check.
- Clarification questions are answered directly, then the AI resumes from the next not-yet-explained concept.
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
