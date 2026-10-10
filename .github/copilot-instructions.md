# Copilot instructions

## Project shape

This is a standalone browser quiz implemented entirely in `index.html`. The file contains:

- The document structure for three UI states: start, quiz, and results.
- All styling in the `<style>` block, including responsive layout, light/dark theme tokens, animations, and reduced-motion handling.
- All behavior in the `<script>` block, including the question data, state transitions, answer evaluation, score tracking, feedback, and result messaging.

There is no server, package manager, build step, runtime dependency, or separate source directory. Keep the app runnable by opening `index.html` directly as a `file://` URL.

## Commands and validation

No build, test, or lint commands are defined because the repository has no dependency or tool configuration. For manual validation, open the file directly:

```text
file:///Users/neelalohithrkashyap/Downloads/space_quiz/index.html
```

Exercise the full browser flow: start the quiz, activate answers with keyboard focus and Enter/Space, verify correct and incorrect feedback plus score changes, complete all 10 questions, confirm the emoji results screen, and use “Play again” to reset the quiz.

To check a single behavior manually, use the integrated browser’s page inspection/evaluation tools against the relevant DOM elements (`#start-button`, `#choices button`, `#feedback`, `#score`, `#result-screen`, and `#restart-button`).

## Implementation conventions

- Keep the project single-file and dependency-free unless the user explicitly changes that constraint.
- Add or edit quiz content in the `questions` array. Each entry must keep the `{ question, choices, answer }` shape, with `answer` as the zero-based index of the correct choice.
- Preserve the existing state flow: `showScreen()` controls visibility, `renderQuestion()` resets the current question UI, `selectAnswer()` locks input and schedules progression, and `showResults()` maps the final score to a result message.
- Use the existing CSS custom properties for colors and surfaces so light mode, dark mode, and feedback states remain consistent. Theme overrides belong in `@media (prefers-color-scheme: dark)`.
- Preserve native `<button>` controls and their visible `:focus-visible` styles. New interactive controls should remain keyboard accessible without custom focus or click handling.
- Keep feedback state classes (`correct`, `wrong`, `good`, `bad`, `shake`) aligned between the JavaScript and CSS; feedback is intentionally shown briefly before advancing.
- Respect `prefers-reduced-motion` when adding animations or transitions.
- Keep the narrow centered-column layout and responsive sizing patterns (`min()`, `clamp()`, and flexible padding) when changing the UI.
