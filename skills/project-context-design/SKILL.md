---
name: project-context-design
description: Design or revise project instructions, context and source architecture, capability allocation, knowledge or reference documents, and split or merge decisions. Do not use for ordinary prompt drafting without an architecture consequence or for independent review-only work.
---

# Project Context Design

Design the smallest reliable project system for the actual runtime. Begin with the work the project must support, the consequences of missing context or capability, and the user's existing constraints. Do not assume that a richer architecture is better.

## Callable reference depth

Handle ordinary work from this skill. Load additional depth only when the task requires it.

### General standard reference

Read only the relevant headings of [Project Context and Capability Design Standard](references/project-context-and-capability-standard.md) when the task:

- is a consequential whole-project or cross-environment architecture decision;
- crosses several context or capability forms and their ownership is unclear;
- requires deeper retrieval, fragmentation, environment-profile, or split/merge judgment;
- depends on an exact pattern or acceptance criterion not reproduced here; or
- exposes material ambiguity that this skill does not resolve.

This reference is a bundled snapshot of active standard `0-01` v1.0.0. Apply its relevant depth rather than summarizing it, and do not load it merely because it is available.

### Codex repository reference

Read the relevant sections of [Codex Repository Architecture](references/codex-repository-architecture.md) only when:

- the target environment is Codex;
- filesystem or Git repository structure materially affects execution; and
- the task involves repository topology, working-directory scope, `AGENTS.md` placement, repository Skills, authoritative-source routing, state and handoffs, worktrees, agent-heavy workflows, or repository validation.

Do not load this reference for general ChatGPT Project design, ordinary prompt drafting, routine code changes, or Codex tasks whose repository structure is not part of the decision.

For consequential Codex architecture work, also consult the general standard reference when authority, capability allocation, split/merge judgment, or cross-environment behavior is material.

Route within the Codex reference by need:

- discovery, configuration, instruction scope, or repository Skills: sections 2 and 6;
- repository topology, project-first or lane-first organization, splits, or worktrees: sections 3 and 5;
- authority, state, or handoffs: sections 4 and 7;
- enforcement, failure analysis, or release validation: sections 8 through 10.

### Codex topology examples

After reading the relevant Codex repository guidance, read [Codex Repository Topology Examples](references/codex-repository-topology-examples.md) only when the user requests a concrete tree or layout, plausible repository topologies need comparison, or abstract guidance is insufficient for an actionable design. Adapt the smallest relevant example to the actual domain and remove unwarranted surfaces. Do not load the examples alone, treat them as templates, or use them for ordinary architecture advice that does not need a concrete layout.

## Establish the operating context

Inspect available project files, instructions, tools, permissions, retrieval behavior, memory or state, and exact interfaces when they are accessible. Ask only for material facts that cannot be discovered.

Identify:

- project purpose and success conditions;
- must-not-miss invariants, authority, and safety boundaries;
- durable facts versus volatile or live state;
- recurring versus one-off work;
- required interfaces, validators, approvals, and handoffs;
- runtime capabilities and credible fallbacks.

Do not recommend skills, plugins, apps, MCP, memory, or repository mechanisms that the target environment does not support. When availability is uncertain, state the assumption and provide a simpler fallback.

## Allocate context and capability

Choose the least costly reliable owner for each requirement:

- persistent instructions for broadly applicable goals, invariants, authority, discovery cues, and completion posture;
- task prompts for run-specific outcomes, inputs, constraints, sources, interfaces, and checkpoints;
- knowledge or reference sources for durable factual, evidentiary, example, or interface depth;
- skills for recognizable recurring workflows needing focused instructions, resources, templates, or scripts;
- plugins for warranted distribution or integration of stable skills and optional tools, hooks, or UI;
- apps, MCP servers, or tools for live data, authenticated access, controlled actions, or typed operations;
- schemas, validators, permissions, tests, or scripts for enforceable guarantees;
- memory or state artifacts for current decisions, progress, and handoff continuity;
- direct inspection for cheap, reliable, authorized current truth;
- omission for method a capable agent can infer without material risk.

Persist information when it must remain salient, even if it is technically inferable. Omit discoverable information only when discovery is cheap and reliable enough for the consequence of missing it.

## Design the project contract and sources

Keep project instructions thin: purpose, non-obvious durable context, invariants, authority, concise source or capability cues, and broadly applicable validation. Exclude task-specific procedure, large templates, volatile catalogs, example banks, and migration history.

Prefer direct semantic discovery from project instructions or the task to the relevant source. Use a Project Map only when source status, ownership, precedence, migration, or selection is genuinely ambiguous. Add a dedicated router only for material branching, state, gates, or dispatch logic.

Create or split a source when independent authority, loading, update cadence, exactness, reusable workflow, size, or evidence status justifies the boundary. Merge or avoid a source when it is normally loaded with another, duplicates doctrine, has an indistinct trigger, or creates coupled maintenance without improving correctness.

Use descriptive headings and conditional metadata. Preserve exact schemas and templates; label examples as illustrative when needed. Keep active authority distinct from drafts, research, reports, logs, and archives.

## Deliver an actionable design

Match the output to the request. For a substantial design, normally provide:

- the recommended architecture and why it fits the runtime;
- copy-ready project instructions when requested;
- each supporting source or capability, its owner, and when it is used;
- direct discovery and ambiguity fallback;
- exact interfaces, validation, and enforcement owners;
- unavailable-capability fallbacks;
- material split, merge, migration, or compatibility consequences.

Do not create files, deploy skills, install plugins, connect tools, or reorganize external projects unless the user authorized those actions. Distinguish a proposal from an applied change.

## Check the result

Confirm that every persistent element earns routine salience, every callable element has a recognizable selection boundary, live truth comes from an appropriate source, exactness is enforceable where practical, and the design still works when optional capabilities are absent. Remove structure that performs no meaningful correctness, discovery, authority, safety, maintenance, reuse, or validation job.
