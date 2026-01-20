# One Example Where the AI Approach Breaks

In May 2025, during development of the Ontology Workbench project, a critical disconnect emerged between automated testing and expected functionality. This is a concrete illustration of how current-generation AI tooling, while powerful, still fails to internalize intent or track non-linear shifts in system scope.

## Background

The Ontology Workbench application includes a dual-panel GUI. The user requested that menu items such as `Validate XML`, `Validate Schema`, and `Validate TTL` should be:

- Present in the application menus.
- Enabled or disabled dynamically based on the file type currently loaded in each panel.

Additionally, the user explicitly asked whether such menu functionality could be tested, noting from experience in C# QA work that GUI behavior usually requires special tooling.

## What Happened

The assistant responded affirmatively and proceeded to:

- Add the requested QAction items to the menus.
- Implement an `update_validation_menu_items()` method that enabled or disabled them based on file extensions.
- Write unit tests confirming that the method correctly toggled the action states.

**However, the assistant failed to connect this logic to real GUI behavior.**

There was no integration between the file-opening mechanisms or tab management and the enabling of the validators. The unit tests passed — but the user, through manual testing, discovered that the menu items never became enabled in practice.

## Root Causes

1. **Lack of Insight Recognition**:
   The assistant did not detect the system’s transition from logic-layer development to UI-layer behavior testing.

2. **Tooling Assumption Blind Spot**:
   The assistant did not recommend `pytest-qt` or any GUI integration tool, despite the question clearly implying a shift toward full behavior testing.

3. **AI’s Linear Strength, Human’s Non-Linear Context Awareness**:
   The assistant performed symbolically correct operations but did not track the goal’s non-linear trajectory.

## Why It Matters

The assistant generated tests that “passed” but gave a false sense of completeness.
A human engineer correctly anticipated the blind spot — even without remembering the name of the GUI testing library — and manually discovered the flaw before deployment.

This is a classic example of what can happen when you trust AI-generated scaffolding without enforcing your own architectural and intent-based oversight.

## Conclusion

This moment is not a failure of AI as a tool — it’s a validation of the role of human insight. It illustrates why software engineers, especially those guiding the next generation, must be deliberate about:

- Drawing the boundary between **unit testing** and **integration testing**.
- Recognizing when an AI has stopped following the purpose behind a feature.
- Embedding critical questions like, "Is the behavior observable by the user?" into every test design.

**AI is not ready to take your job. But it is ready to amplify your judgment — if you use it wisely.**
