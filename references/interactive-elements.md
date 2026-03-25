# Interactive Elements Reference

Use this reference only for UI Mode of `system-design-interview-simulator`.

## Purpose

Define reusable UI behaviors for a realistic mock system design interview experience. Prioritize
flow clarity, interviewer realism, and clear candidate controls. Implement these behaviors in the
`ui/` directory across separate HTML, CSS, and JavaScript files.

## UI File Structure

- `ui/index.html`: session setup, interview panels, and debrief containers
- `ui/styles.css`: interactive states, controls, transcript bubbles, and mobile layout
- `ui/app.js`: event handling, interview state, command actions, and debrief rendering

## Required UI Sections

1. **Session Setup Panel**
   - Inputs: topic (`random` or custom), difficulty (`Junior`, `Mid`, `Senior`, `Staff`)
   - Start button to begin interview
2. **Interview Phase Tracker**
   - Phases: setup, problem, requirements, architecture, deep dives, debrief
   - Highlight active phase and completed phases
3. **Prompt and Response Area**
   - Show current interviewer prompt
   - Candidate response text area
   - Submit response action
4. **Command Bar**
   - Buttons: `hint`, `skip`, `feedback`, `restart`, `new problem`, `done`
   - Difficulty switcher available mid-session
5. **Transcript Panel**
   - Timestamped interviewer and candidate messages
   - Auto-scroll to newest message
6. **Debrief Renderer**
   - Structured scorecard exactly matching the skill's format

## Interaction Rules

- After each candidate response, generate one focused interviewer follow-up.
- Do not auto-provide solutions; `hint` returns one directional nudge only.
- `skip` advances to the next interview topic area while preserving transcript.
- `feedback` provides partial, section-specific feedback and resumes.
- `done` locks inputs and renders the final debrief.
- `restart` clears transcript and state.
- `new problem` keeps difficulty and starts a fresh prompt context.

## State Model (Suggested)

```javascript
const state = {
  topic: "random",
  difficulty: "Senior",
  phase: "setup",
  sectionIndex: 0,
  transcript: [],
  strengths: [],
  gaps: [],
  scores: {
    requirements: null,
    architecture: null,
    data: null,
    scalability: null,
    reliability: null,
    communication: null
  },
  isComplete: false
};
```

## Debrief Structure Requirement

Render this exact output shape in UI:

- `Interview Debrief — [Problem Name]`
- `Overall Signal: [Strong Hire / Hire / No Hire / Strong No Hire]`
- Table rows:
  - Requirements Clarification
  - System Architecture
  - Data Modeling & Storage
  - Scalability & Performance
  - Reliability & Fault Tolerance
  - Communication & Structure
- Sections:
  - What You Did Well
  - Areas to Improve
  - What a Strong Answer Would Have Included
  - Recommended Topics to Study

## Suggested Components

- **Phase chips:** compact labels for interview stage
- **Transcript bubbles:** interviewer vs candidate styling
- **Score badges:** 1-4 badges with color-coded severity
- **Prompt cards:** current question + follow-up prompt
- **Control pills:** command actions with clear affordance

## Error Handling and UX Guardrails

- If candidate submits empty response, request content instead of advancing.
- If user clicks `done` too early, still provide best-effort debrief based on available transcript.
- Prevent command spam by debouncing control actions for 200ms.
- Keep all behaviors deterministic and understandable; avoid hidden auto-resets.

## Mobile Behavior

- Stack prompt/response above transcript.
- Keep command bar sticky at bottom with horizontal scrolling for buttons.
- Ensure transcript remains readable and does not overlap controls.
