# GitHub Copilot Instructions for space-quiz

## Architecture & Project Structure

- **Self-Contained Web App**: Entire application runs from a single zero-dependency file (`index.html`) containing embedded HTML, CSS, and Vanilla JavaScript.
- **Runtime Environment**: Client-side only. Requires no build toolchain, package manager (`npm`/`yarn`), bundling pipeline, or web server.
- **Layout & Sizing**: Narrow, centered card design (`max-width: 480px`) with standard body typography (14–16px sans-serif).
- **Theming**: System theme responsive via CSS custom properties and `@media (prefers-color-scheme: dark)`.

## Running & Testing

- **Local Preview**: Open `index.html` directly in a browser or browser canvas (`file:///Users/justinyoo/dev/gh/space-quiz/index.html`).
- **Interactive Verification**:
  - Test questions via mouse clicks or keyboard hotkeys (`1-4`, `A-D`, `ArrowUp`/`ArrowDown`).
  - Verify accessibility and visual feedback (correct green pulse, incorrect red shake animation).
  - Verify restart flow via button click or `Enter`/`Space`/`R` on the results view.

## Key Conventions & Constraints

- **Zero External Dependencies**: Keep everything in pure Vanilla HTML5, CSS3, and ES6+ JavaScript. Do not introduce CDN scripts, NPM packages, or CSS frameworks.
- **Question Schema**: Maintain questions inside the `questions` array adhering to the structure:
  ```javascript
  {
    category: "Category Name",
    question: "Question prompt text",
    options: ["Option A", "Option B", "Option C", "Option D"],
    answer: 0 // 0-based index of correct option
  }
  ```
- **State & Transition Timing**: Selection transitions use an answering lock (`isAnsweringLocked = true`) with a 1250ms timeout before advancing to allow feedback animations to complete. Keep state resets aligned in `restartQuiz()`.
- **Mission Control Theme**: The header HUD (`div.title-row`) contains flight telemetry indicators (`SYS NOMINAL`, status beacon, live point counter). Ensure accessibility labels (`aria-live`, `aria-label`) remain intact when adjusting header components.
