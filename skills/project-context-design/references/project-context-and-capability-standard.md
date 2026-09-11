# Project Context and Capability Design Standard
Document ID: Project_Context_And_Capability_Design_Standard
Status: Active
Version: 2.0.0
Last Updated: 2026-09-11
Purpose: Govern project setup, context and capability allocation, persistent instructions, knowledge and prompt design, reusable capabilities, discovery, and environment-specific deployment.

## 1. Purpose and use

Use this standard when deciding how an LLM or agent should receive the context, capability, control, or continuity needed to perform work reliably. It governs:

- project and repository instructions;
- knowledge and reference sources;
- one-off, reusable, research, and Deep Research prompts;
- skills and their supporting resources or scripts;
- plugins, apps, MCP servers, and other tools;
- schemas, validators, permissions, tests, and other enforceable controls;
- memory, state, direct inspection, and source discovery;
- split, merge, loading, and deployment decisions across runtimes.

Use `Review_And_Change_Ops_Standard` for independent evaluation, severity, patch/rewrite decisions, exact changes, validation, migrations, and supersession.

This standard defines allocation judgment, not a mandatory project anatomy. A small project may need only concise instructions and a few sources. A capable agent environment may use skills, tools, and validators. Neither is inherently more mature.

Ordinary conversational requests do not need formal prompt structure when the task, context, and expected answer are already clear.

## 2. Governing model: outcome, runtime, and minimum-sufficient support

Start with the outcome and acceptance conditions. Inspect the actual runtime. Then select the least costly mechanism that supplies or enforces what reliable work requires with acceptable omission, discovery, authority, maintenance, and enforcement risk.

Use the smallest high-signal contract that supplies necessary information and keeps must-not-miss requirements salient. Guidance may deserve persistent placement even when a model could infer it if omission would materially increase risk. Conversely, do not persist information merely because it is useful somewhere.

| Mechanism | Use when | Avoid when |
|---|---|---|
| Persistent project or repository instructions | A goal, invariant, authority rule, discovery cue, or completion posture must shape ordinary work | It is task-specific, volatile, large, or reliably discoverable when needed |
| Run-specific prompt | One task needs a particular outcome, input, constraint, source posture, interface, or checkpoint | The same stable workflow is repeatedly reconstructed |
| Knowledge or reference source | Durable facts, definitions, evidence, examples, or exact reference depth must be available | The information is live state better obtained from its owning system |
| Skill | A recognizable recurring goal benefits from focused instructions, resources, templates, or scripts | Native capability is sufficient, the trigger is indistinct, or use is too rare to maintain |
| Plugin | Users need a discoverable, installable bundle of stable skills and possibly MCP, hooks, or UI | A local skill suffices and no shared integration or distribution need exists |
| MCP server, app, or tool | Work requires live information, authenticated access, controlled action, or a typed operation | Static context safely supplies the needed truth |
| Schema, validator, permission, test, or script | Exact structure, deterministic transformation, validation, or safety should not depend on prose adherence | The requirement is irreducible judgment |
| Memory or state artifact | Current decisions, progress, or handoff state must persist across sessions | The content is governing doctrine or cheaply recoverable from authoritative state |
| Direct inspection | Current truth is cheap, reliable, and authorized to discover | Discovery is costly, opaque, ambiguous, or permission-limited |
| Omission | A capable model can infer the method and maintained context adds no material value | Missing information would change correctness, authority, source choice, or safety |

These mechanisms can complement one another. A skill may use a reference and script; a project instruction may name a tool; a schema may enforce a prompt's output. Give each requirement one primary owner and add only the supporting surfaces that improve execution.

Different forms of specificity still have distinct jobs:

- goals and principles own generalizable judgment;
- invariants own boundaries that must hold across solution paths;
- factual context belongs in an authoritative source with the right currentness;
- exact interfaces belong in schemas, templates, or typed contracts;
- procedures own sequence, state, approval, validation, handoff, or irreversible action;
- examples solve measured calibration problems;
- evidence and history support provenance, comparison, or recovery;
- enforceable controls own guarantees that should not rely on model obedience.

## 3. Runtime and capability assessment

Before choosing a design, determine what the actual host supports:

- model capability and relevant limitations;
- persistent instruction surfaces and their scope;
- retrieval, file-selection, and callable-context behavior;
- available skills, plugins, apps, MCP servers, tools, and direct filesystem or source access;
- permissions, authentication, approval, and irreversible-action boundaries;
- schemas, validators, tests, sandboxes, or lifecycle controls;
- memory and state persistence;
- volatility and currentness of required information.

Do not recommend a capability merely because another platform exposes it. State important availability assumptions and define a degradation path when absence would change the design. Common degradations include replacing a skill with an explicit task prompt, replacing live access with a dated reference plus an as-of warning, or moving a must-not-miss invariant into persistent instructions.

Discovery is an engineering property, not a model compliment. Omit discoverable information only when the runtime permits cheap, reliable, authorized discovery and failure to discover it has an acceptable consequence.

## 4. Persistent project contract

Project or repository instructions are the primary persistent contract for ordinary work. Keep them focused on information that deserves routine salience:

- project purpose and optimization target;
- non-obvious project-wide facts or terminology;
- invariants, authorization and safety boundaries, and irreversible-action safeguards;
- source precedence where conflicts could change execution;
- artifact or completion posture that applies broadly;
- concise semantic cues for additional sources or capabilities;
- exact validation commands or local conventions that are expensive to rediscover;
- a fallback for unclear source status, ownership, precedence, or selection.

Avoid task-specific procedures, volatile fact catalogs, large templates, example banks, migration history, or exhaustive inventories. Supporting sources are warranted by conditionality, size, exactness, reuse, volatility, independent authority, maintenance cadence, or a distinct loading boundary.

### 4.1 Compact project-instruction pattern

Use only the sections the project needs:

```text
# Project Instructions

Purpose
[What the project is for and what strong work optimizes for.]

Persistent context
[Non-obvious facts or terminology needed across many tasks.]

Invariants and boundaries
- [Project-wide requirement or safeguard.]

Source guide
- `[Source or capability]`: [what it supplies and when to use it].
- Consult `[Project Map]` only when status, ownership, precedence, or selection is unclear.

Completion and validation
- [Persistent artifact posture, validation command, or definition of done.]
```

This is an aid, not a required anatomy. A shorter complete contract is preferable.

## 5. Knowledge and reference design

Knowledge and reference sources hold durable factual, definitional, evidentiary, example, or interface depth. They may be authoritative, supporting, or historical. Their role and status matter more than their upload location.

### 5.1 Source flow, authority, and status

For ordinary work, route directly from persistent instructions or the task to the relevant source. Use a Project Map when source choice, authority, status, or migration is ambiguous.

`persistent contract or task → task-relevant source`

`persistent contract or task → Project Map → task-relevant source`

Apply these authority rules:

- explicit user and higher-priority platform instructions govern within their authority;
- active project instructions and active owner sources govern project work;
- exact templates, schemas, permissions, and tool contracts govern their defined surfaces;
- drafts, proposals, reports, research, examples, logs, superseded sources, and archives inform unless promoted;
- more specific active guidance may narrow broader guidance;
- unresolved material conflicts must be surfaced rather than silently normalized.

When exact wording, current state, citations, source order, legal or policy facts, schemas, status, or copy-ready text matters, inspect or refresh the owning source. Availability, memory, attachment, upload order, or prior loading does not establish current authority.

Consult research, reports, logs, examples, or archives when evidence, history, comparison, or recovery is part of the task. Their availability does not make them active authority.

### 5.2 Project Maps, routers, and source relationships

A Project Map is an optional maintenance and ambiguity-resolution surface. It may identify active, draft, superseded, and planned sources; concise purposes and owners; precedence notes; migration state; complex relationships; and unresolved overlaps or transition risks. It should not duplicate full doctrine or become a mandatory runtime hop.

A dedicated router must earn its existence through substantial branches, gates, state, precedence, or independently maintained dispatch logic. A trigger-phrase inventory is not a substitute for semantic selection.

Existing numbered maps, router/crosswalk sets, doctrine/operations manuals, or similar layouts may remain when their boundaries still improve execution or maintenance. Do not reproduce them for symmetry.

Reference another source in task-facing guidance only when it owns required information, changes authority, supplies necessary depth, prevents harmful duplication, or resolves material ambiguity. Put broader inventories and architecture graphs in a map or migration record.

### 5.3 Artifact boundary

Use LLM-facing structure when an artifact will be stored, retrieved, cited, transformed, patched, or reused as guidance. Use human genre conventions for emails, reports, proposals, slide copy, narrative summaries, and ordinary answers. For mixed-use artifacts, optimize for the human audience and add only the machine-use surfaces required for reliable reuse.

### 5.4 Structure

Use descriptive headings and the form that matches the information: prose for explanation and judgment, bullets for separable constraints, numbered steps for real sequence, tables for comparisons or field alignment, schemas for exact interfaces, and delimiters when roles could blur.

One concise opening orientation may help a long source. Do not create repeated summaries or shadow specifications. State principles before edge cases. Enumerate exact fields, options, states, boundaries, steps, or checks; otherwise prefer a semantic rule.

### 5.5 Metadata

Metadata is conditional. Every field must help a model, maintainer, tool, or auditor make a real decision.

Active shared standards in this repository use H1 title, `Document ID`, `Status`, `Version`, `Last Updated`, `Owner / Maintainer`, and `Purpose`. Other artifacts may need less. Add dates, provenance, ownership, lifecycle, or versions only when currentness, authority, auditability, or tooling uses them.

Do not add keyword taxonomies, dependency graphs, loading classes, integrity labels, collaborator lists, or related-document catalogs without a demonstrated use.

### 5.6 Headings, anchors, and cross-references

Descriptive headings are the default reference surface. Add explicit anchors only for demonstrated external, patch, or machine-interface use. When a rebaseline changes referenced headings, provide a crosswalk or redirect rather than distorting the new structure.

Cross-reference an owning file and heading clearly. Avoid positional references and thematic related lists. A task-facing reference should change execution, authority, or necessary depth.

### 5.7 Examples and templates

Examples calibrate judgment; templates define reusable literal structure. Start with semantic guidance. Add examples for an observed ambiguity, label them illustrative when confusion is plausible, keep larger sets callable or local, and vary examples when one would imply a false universal pattern. Keep exact templates copy-safe, with stable required fields and obvious placeholders.

## 6. Task and prompt contracts

A task prompt binds one run to its outcome, available context, constraints, sources, interface, and stopping point. It is one capability form within the project system, not a separate architecture.

### 6.1 Prompt contract

Use the smallest relevant combination of:

| Component | Include when |
|---|---|
| Task or question | The requested work is not already unambiguous |
| Outcome or acceptance criteria | Plausible outputs differ materially in usefulness or correctness |
| Context or inputs | The model needs facts, artifacts, terminology, or prior decisions it cannot access or infer |
| Scope | Adjacent work could absorb effort or change the deliverable |
| Constraints or invariants | A boundary must hold across valid solution paths |
| Source posture | Evidence, freshness, citations, or conflict handling matter |
| Output interface | Structure, schema, filename, headings, field order, or artifact type matters |
| Stop or checkpoint | The model might overproduce, act irreversibly, or cross an approval boundary |
| Example | Semantic guidance alone does not reliably calibrate behavior or shape |

These are contract components, not mandatory fields.

### 6.2 Specificity and model autonomy

Human authors own requirements; capable models own solution search unless the path is part of correctness. Prefer goals, invariants, context, and acceptance criteria over narrated reasoning.

Specify procedure when a stage consumes controlled prior output, order changes results, approval is required, validation gates continuation, state or permissions change, an action is irreversible, or a recurring workflow has a real handoff contract. State each obligation once and merge overlapping clauses.

### 6.3 Structure and boundaries

Use ordinary prose for short prompts, headings or labels for visible sections, fenced blocks for literal material, semantic tags when paired boundaries help, and tables for concise priority or field mapping. Syntax helps distinguish roles; it does not create authority.

For long context, label source blocks; keep the operative question, source precedence, critical constraints, and output interface easy to locate; and use extraction or chunking when a monolithic pass creates retrieval risk. Treat placement heuristics as model- and task-sensitive.

### 6.4 Constraints, interfaces, and examples

State positive intended behavior clearly. Add prohibitions for safety, privacy, authority, exact interfaces, or demonstrated failure boundaries. Use exact fields, wrappers, filenames, and ordering when a consumer or validator requires them. Keep required schemas separate from illustrative examples.

### 6.5 Sources, grounding, and uncertainty

State sources, freshness, citation, and precedence only to the degree the task requires. Permit unknown, conflicting, inaccessible, or unverified findings rather than fabricated closure. Citations must identify sources actually consulted. Do not add research machinery to transformation or action tasks already grounded in supplied material.

### 6.6 Reusable prompts and prompt packs

A reusable prompt is warranted when stable structure reduces drift in variables, sources, interfaces, approvals, or completion boundaries. Separate shared instruction from run-specific inputs and choices. An invocation wrapper binds one run to its task, inputs, source posture, target interface, and stopping point without restating the full method.

Use a prompt pack when multiple maintained prompts or variants recur. Its index needs only enough information to choose and run the correct prompt: name, use, required inputs, governing source when needed, output, and status. Use a skill instead when a recognizable recurring goal needs focused workflow guidance, bundled resources, templates, or scripts and the runtime can select or invoke it reliably. Do not turn every reusable prompt into a skill.

### 6.7 Multi-stage and agentic work

Choose the smallest execution shape that preserves correctness and control: one bounded request, a visible plan, staged work with checkpoints, or a maintained workflow. Define completion, authorized actions, and user decisions. A clarification blocks only dependent work; a correction preserves still-valid goals and constraints unless the objective changes.

Tool contracts, permissions, schemas, tests, and environment controls should own guarantees that cannot safely depend on prompt adherence.

### 6.8 General task/prompt pattern

Use only the labels needed:

```text
Task
[What to do.]

Outcome
[What success must enable or contain.]

Context and inputs
[Relevant material the model cannot otherwise access.]

Constraints
- [Invariant, boundary, source rule, or exact requirement.]

Deliverable
[Artifact, sections, schema, or output posture.]

Stop or checkpoint
[Only when continuation, approval, or action must be bounded.]
```

## 7. Research and Deep Research prompts

Research prompts define an evidence contract, not the researcher's internal search plan. Include the smallest relevant combination of objective, scope, freshness, evidence expectations, material distinctions or disconfirmation, deliverable, uncertainty posture, and stop boundary.

Allow the agent to choose queries, source sequence, decomposition, and synthesis unless method is required for validity. Avoid arbitrary source counts, vendor quotas, exhaustive sub-question lists, and prescribed search stages.

### 7.1 Deep Research pattern

```text
Objective
[Question to answer and decision or artifact it supports.]

Scope
- Include: [material boundaries].
- Exclude: [adjacent work that should not absorb effort].
- As of: [date or freshness expectation, when relevant].

Evidence posture
- Prefer: [primary, official, peer-reviewed, or other required sources].
- Treat cautiously or exclude: [source classes, if material].
- Cite load-bearing claims and report meaningful conflicts or uncertainty.
- Seek evidence that could disconfirm the leading hypothesis when relevant.

Deliverable
[Required synthesis, comparison, recommendation, or artifact.]

Stop boundary
[Where the research ends and what later action is not authorized.]
```

## 8. Skills

A skill is focused, callable support for a recognizable recurring goal. Create one when its instructions, resources, templates, or scripts materially improve repeated outcomes without deserving persistent attention.

A skill should have:

- a distinctive positive trigger and useful exclusions;
- enough metadata for selection without loading the full body;
- a focused operational contract after invocation;
- progressive disclosure of references or resources;
- scripts only for deterministic, repeated, or validation-heavy work;
- clear currentness and version ownership;
- positive, negative, mixed, and overlap validation before broad deployment.

Prefer explicit invocation when missing the skill would be costly and implicit selection is not sufficiently reliable. Avoid overlapping micro-skills whose triggers compete. Split a skill only when tasks have independent selection, resources, maintenance, or validation needs.

Skills operationalize doctrine; they do not silently become the only owner of must-not-miss project requirements. Keep those requirements persistent or explicitly invoke the skill.

## 9. Plugins, apps, MCP, and tools

A plugin distributes a stable bundle that may include skills, MCP connectivity, lifecycle hooks, or UI. Create one for demonstrated sharing, installation, integration, authentication, lifecycle, or interface needs—not merely to package unvalidated prose.

Use MCP servers, apps, or tools for live information, authenticated access, controlled actions, or typed operations. Keep these concerns distinct:

- a skill tells the agent how to perform a workflow;
- a live tool supplies data or action capability;
- permissions and approvals determine authority;
- a plugin packages and distributes supported components.

Do not copy volatile platform manifests or schemas into general doctrine. Consult the current platform interface when implementing them, and provide a fallback when availability varies.

## 10. Enforcement, memory, and inspection

Use schemas, validators, permissions, sandboxes, tests, scripts, and approval mechanisms when correctness or safety can be enforced mechanically. Retain a concise invariant explaining the intended boundary, but do not treat prose repetition as enforcement.

Use memory or state artifacts for current decisions, progress, assignments, and handoff state. Do not use memory as the sole owner of governing doctrine, exact interfaces, or facts that should be refreshed from an authoritative system.

Use direct inspection for current truth when it is authorized, cheap, reliable, and discoverable. Persist the result only when reuse, auditability, volatility management, or a future loading boundary warrants it.

Procedures remain appropriate when order, state, approval, validation, handoff, or irreversible action is part of correctness. Specify required sequence and gates precisely enough to execute. Routine inspect-think-draft-review narration is normally inferable.

## 11. Retrieval, fragmentation, and split/merge judgment

Evaluate the whole retrieval path rather than only whether context exists:

1. Can the agent recognize that additional capability or context is needed?
2. Can it select the correct candidate without harmful overlap?
3. Will the runtime load or expose the candidate reliably?
4. Is the content current, authoritative, and applicable after retrieval?
5. What is the consequence if any step fails?

Create or split a source or capability when independent authority, task-specific use, cadence, exact interface, stable workflow, size, evidence status, resources, or validation benefits exceed selection and maintenance costs.

Merge or avoid a separate artifact when candidates are normally used together, duplicate doctrine or routing, require coupled updates, have indistinct triggers, or increase retrieval cost without improving correctness. Do not split merely to create conceptual symmetry or layers named core, reference, and appendix.

Use a router only when semantic descriptions cannot reliably resolve substantial branching, state, precedence, or dispatch logic. For high-consequence omission, strengthen persistent discovery cues, require explicit invocation, or move the requirement to a more reliable owner.

## 12. Environment profiles

| Environment | Default posture | Material caution |
|---|---|---|
| Ordinary ChatGPT chat | Use a clear task contract and attach or name required sources | Do not assume project history, callable skills, or persistent files |
| ChatGPT Project | Keep project instructions thin; store coherent domain sources; explicitly name must-use material | Uploaded availability does not guarantee correct retrieval on every task |
| Existing custom GPT | Put core specialist behavior in instructions and use knowledge for reference depth | Knowledge retrieval and project integration may differ from ordinary project behavior |
| Codex repository | Keep `AGENTS.md` repository-specific; use focused skills, inspection, tools, and validators | Avoid accumulating general doctrine or overlapping skill triggers in persistent context |
| Managed Work or plugin environment | Use validated skills for workflow and plugins for warranted distribution/integration | Permissions, app availability, data access, and administration vary |
| API or custom agent harness | Design retrieval, state, tools, schemas, and permissions explicitly | Do not treat prose as enforcement or assume autonomous need recognition |

Adapt these profiles to observed host behavior. If a preferred mechanism is unavailable, preserve the outcome and invariants using the smallest reliable fallback.

## 13. Acceptance criteria

A project context or capability design is ready when:

- the actual runtime, permissions, retrieval behavior, and available capabilities were not assumed incorrectly;
- each persistent obligation earns routine salience and each callable or supporting surface earns selection and maintenance cost;
- must-not-miss requirements have discovery or invocation reliability proportional to omission consequence;
- project instructions, task prompts, sources, skills, tools, controls, and state have distinct primary roles;
- authority, status, freshness, and precedence are clear where conflict could matter;
- exact interfaces and required sequences remain explicit and enforceable where practical;
- prompts communicate the smallest complete task contract without prescribing inferable method;
- examples, research, reports, memory, and archives do not become shadow authority;
- split/merge decisions reduce rather than reproduce fragmentation;
- degradation paths preserve essential outcomes when capabilities are unavailable;
- representative use has not revealed a material failure that a smaller reliable change could prevent;
- existing compatibility surfaces are preserved or intentionally mapped for migration.

Keep the affected artifact Draft when unresolved runtime, authority, source, interface, or migration decisions prevent these conditions.
