---
name: prompt-design
description: Create or revise one-off prompts, reusable prompts, invocation wrappers, research prompts, and Deep Research prompts. Do not use to perform the prompt's underlying task or redesign an entire project unless the request requires it.
---

# Prompt Design

Create the smallest task contract that reliably produces the user's intended outcome. Improve the prompt without taking over the underlying task unless the user asks for both.

## Determine what the prompt must carry

Inspect supplied artifacts and discoverable context before asking questions. Include only components that affect correctness or usefulness:

- task or question;
- desired outcome or decision use;
- context and inputs the target model cannot otherwise access;
- scope and exclusions;
- constraints or invariants;
- source, freshness, evidence, citation, or conflict posture;
- deliverable or exact output interface;
- approval, stop, or handoff boundary;
- examples when semantic guidance does not calibrate behavior reliably.

These are optional components, not a form to complete. Ordinary clear requests may need only a sentence.

## Preserve model autonomy and exactness

The author owns requirements; the model normally owns solution search. Prefer goals, relevant context, invariants, and acceptance criteria over narrated reasoning or routine steps.

Specify procedure when order changes the result, a stage consumes controlled prior output, approval or user input is required, validation gates continuation, state or permissions change, an action is irreversible, or a recurring workflow has a real handoff contract.

State positive intended behavior clearly. Add prohibitions for safety, privacy, authority, exact interfaces, or demonstrated failure boundaries. Preserve literal schemas, wrappers, filenames, field order, variables, and required headings exactly when a consumer depends on them. Keep source text, examples, and copy-ready output distinguishable from instructions.

## Ground the task

State source requirements only to the degree the task needs. Clarify authority, freshness, citations, uncertainty, and conflict handling when they can change the answer. Permit unknown or inaccessible information rather than fabricated closure.

For long inputs, label source blocks and keep the operative task, source precedence, critical constraints, and output interface easy to locate. Use extraction or staged processing only when context size or retrieval risk warrants it.

## Handle reusable and research prompts

For a reusable prompt, separate stable shared instructions from run-specific variables, sources, and choices. An invocation wrapper should bind one run to its task, inputs, source posture, target interface, and stopping point without repeating the full method.

Use a prompt pack only when multiple maintained prompts or variants recur. Consider a skill instead when a recognizable recurring goal needs focused workflow guidance, resources, templates, or scripts and the runtime can invoke it reliably.

A research prompt defines the evidence contract, not the researcher's internal search plan. Specify the objective, material scope, freshness, evidence posture, disconfirmation needs, deliverable, uncertainty handling, and stop boundary as needed. Avoid arbitrary source quotas, exhaustive sub-question catalogs, and prescribed search stages unless method is part of validity.

## Deliver and check

Return copy-ready prompt text separately from commentary. When useful, briefly state material assumptions or optional variants outside the prompt. Do not add fields, examples, workflows, or formatting merely for completeness.

Before finishing, check that the task and useful outcome are unambiguous, required context is available without hidden chat history, constraints are semantic where possible and exact where required, sources and literal interfaces cannot be confused, procedure represents a real dependency, reusable and run-specific content are separated, and the stopping boundary matches the user's authorization.
