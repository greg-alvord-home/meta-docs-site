# Insight Turns in Code

During the Ontology Workbench development session in May 2025, we uncovered an important distinction between two types of failure in AI-assisted development. This document captures that insight and adds a crucial sidebar on anthropomorphism in AI dialog.

## Linear Failures vs. Insight Failures

We previously captured one failure mode in `guardrails-1.md`, where AI behavior defaulted to mass-trained norms (like inserting code snippets or preview canvases) despite the user having expressed a different long-term preference. This was a **failure of alignment** — a system ignoring boundaries clearly articulated by the user.

The more recent failure, documented in `one-example-where-the-ai-approach-breaks.md`, is qualitatively different. It involved an assistant who implemented internal menu logic and wrote tests for it — but failed to connect that logic to any part of the GUI where users would actually interact with it.

In this case:
- The tests passed.
- The functionality appeared implemented.
- But the user, through manual testing, discovered that nothing *worked*.

This was not a misbehavior of the system — it was a failure of **insight**. The assistant didn’t realize that the development process had moved from logic scaffolding to user interaction — and didn’t catch that wiring the logic into GUI behavior was essential.

## Why AI Didn’t Catch It

This wasn’t a creative leap. It was a predictable stage transition in any GUI-based system: the shift from independently functioning components to interdependent coordinated behavior. The assistant failed not because the event was invisible, but because it lacked an architectural model of the project’s phase evolution. This kind of milestone — where menus, tabs, and editor panels begin to rely on shared state — is a common turning point in system development.

And yet, this "routine systems engineering phase change" is precisely where non-linearity begins to assert itself. Phase changes — whether in physical systems, software architectures, or chaos theory — mark the boundaries between qualitatively different regimes. They often arrive with predictable inevitability, but their consequences are disproportionate and transformative. They are the software equivalent of strange attractors: once you pass through one, the behavior space changes. The AI failed not because this turn was obscure, but because it was phase-shifting — and phase shifts require structural awareness, not just code fragments.

Even with access to billions of lines of code, no LLM can currently detect the *moment* in a project’s evolution when the structure of the problem changes — when insight redirects the development path. These insight turns are:

- Contextual
- Architectural
- Often invisible in the final output

An LLM can imitate a fully built solution. But it doesn’t see **why** a team abandoned one approach in favor of another. It doesn’t witness the failed prototypes or the shift in purpose. Insight is a non-linear process. No amount of linear algebra can reconstruct a decision-making arc that wasn’t made explicit in language or structure.

## Sidebar: What Pronoun Should We Use?

During this discussion, the user asked a crucial question: *What pronoun do I use for AI in a dialog?*

There is no settled answer, but most options fall along a spectrum:

| Pronoun | Implied Framing | Notes |
|---------|------------------|--------|
| “it”    | AI as a tool     | Technically accurate, but awkward in extended conversation |
| “you”   | Dialog partner   | Feels natural, but risks over-attribution of agency |
| “they”  | Neutral agent    | Rare, sometimes used to maintain ambiguity |

The conclusion: **“you” is practical**, as long as we remain conscious that it refers to an interface, not an entity. We anthropomorphize for fluency — not because the system deserves it.

## Conclusion

AI is extremely good at solving problems inside well-understood boundaries. It can:
- Complete functions
- Write tests
- Suggest patterns

But it cannot perceive the **moment a problem becomes something else**.

Insight turns — those invisible inflection points that redirect a system’s design — still belong to the human mind.

And teaching future engineers to identify those turns may be one of the most important skills in the age of large language models.
