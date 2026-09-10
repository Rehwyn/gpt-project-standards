# 0-02 — Review and Change Ops Standard
Document ID: 0-02__Review_And_Change_Ops_Standard
Status: Active
Version: 1.0.1
Last Updated: 2026-09-10
Purpose: Govern independent review, material findings, capability-fit evaluation, bounded changes, interface validation, and migrations.

## 1. Purpose and review contract

Use this standard when review or change work must support a decision such as:

- ready, revise, or defer;
- patch, bounded rewrite, or full rewrite;
- preserve, move, merge, retire, or supersede;
- accept or reject a capability allocation or migration;
- approve an interface, source-authority, or deployment change.

Review against the task, actual runtime, active owner sources, acceptance criteria, and exact interfaces. Use `0-01__Project_Context_And_Capability_Design_Standard` to design project/context systems, task and prompt contracts, reusable capabilities, and environment-specific deployment.

This is an agent-facing review and change-reasoning standard, not a substitute for project-local operational, security, legal, regulatory, contractual, or professional controls. Apply stricter requirements when they govern the actual work; do not import them into ordinary low-risk tasks when they do not apply.

An effective review:

- is independent of the author's preferred conclusion;
- evaluates evidence, requirements, risks, runtime conditions, and intended use;
- finds material defects without inventing issues to fill a count;
- distinguishes correctness and interface failures from style preferences;
- gives enough evidence to verify each material finding;
- recommends the smallest strategy that resolves the actual problem;
- states meaningful uncertainty, validation gaps, and acceptable tradeoffs;
- keeps breadth and output detail proportional to the decision.

The user may request a local, whole-artifact, cross-document, capability-system, or full-rebaseline review. Review only the breadth needed to support that decision. Deeper reasoning should improve selection and confidence, not automatically lengthen the report.

### 1.1 Review invocation pattern

```text
Task
Review [artifact or system] to decide [readiness or change decision].

Authority and evidence
- [Active owner source or acceptance criteria.]
- [Supporting source, runtime evidence, or observed behavior, only if needed.]

Scope and material risks
- [Local, whole artifact, cross-document, capability-system, or migration scope.]
- [Interfaces, sources, retrieval, runtime, migration, or failure modes that matter.]

Deliverable
- Verdict.
- Material findings with evidence and severity when useful.
- Smallest responsible change strategy.
- Acceptable tradeoffs, uncertainty, and residual risks when material.

Boundary
[Whether to stop at findings, draft exact changes, or apply authorized changes.]
```

Do not force a finding count. “No material issues found” is valid when supported.

This is a review-operation invocation interface, not a general prompt-design template. Use `0-01__Project_Context_And_Capability_Design_Standard` for general task and prompt contracts.

## 2. Severity and materiality

Use these classes when severity helps drive action:

| Severity | Meaning |
|---|---|
| Must | Blocks readiness or breaks correctness, safety, authority, a required interface, migration continuity, capability availability, or the requested outcome |
| Should | Materially affects reliability, clarity, maintenance, source or capability use, or coherence but does not block all use |
| Nice | Optional polish or convenience with no material effect on correctness |

`No action` is a verdict or disposition for an acceptable tradeoff, false positive, or issue that does not warrant change; it is not a finding severity.

Do not inflate polish into a blocker or hide structural failures as suggestions. Group findings that share one cause or fix. When classification is uncertain, explain why and avoid false precision.

## 3. Risk-selected review checks

Use the smallest set of checks that can detect likely failure and support the next action.

Increase review depth when consequence, uncertainty, irreversibility, external exposure, sensitive information, shared authority, dependent coupling, or exact interfaces make failure materially more costly. Ordinary local, reversible, and low-consequence work may need only direct inspection and cheap relevant checks.

| Risk or decision | Check |
|---|---|
| Readiness | Required content, completion criteria, blockers, and truthful status |
| Exact interface | Fields, schemas, headings, wrappers, filenames, commands, permissions, or validation contracts |
| Source and grounding | Authority, currentness, citations, unsupported claims, conflicts, and uncertainty |
| Compression or simplification | Duplicate obligations, persistent salience, unique-content loss, and relocation of callable or non-governing depth |
| Runtime and capability fit | Availability, allocation, discovery, retrieval, invocation, fallback, and enforcement |
| Cross-artifact coherence | Competing owners, duplicated doctrine, overlapping triggers, stale references, and shadow authority |
| Migration or supersession | Crosswalk, dependents, activation order, archive integrity, generated outputs, and rollback evidence |
| High-cost or adversarial risk | Misleading inputs, biased framing, permission boundaries, rare interface failures, and targeted probes |

Do not run every check because it exists. Domain-specific, regulated, or machine-validated work may need exact local checklists; keep them with the owning project or interface.

## 4. Capability-fit review

Test the design against the actual host rather than the capabilities of an ideal platform.

Check:

- model capability, available context, permissions, tools, apps, MCP servers, skills, plugins, memory, and retrieval semantics;
- whether each requirement belongs in persistent instructions, a task prompt, a reference, a skill, a plugin, a live tool, an enforceable control, state, direct inspection, or omission;
- need recognition, source or skill selection, loading or invocation, correct application, freshness, and authority after retrieval as distinct failure points;
- whether a skill has a recurring goal, distinctive trigger and exclusions, maintainable resources, acceptable version risk, and limited overlap;
- whether a plugin solves distribution, MCP, hook, UI, authentication, or lifecycle needs rather than merely packaging prose;
- whether live truth comes from an appropriate tool and whether authorization is clear;
- whether schemas, validators, permissions, tests, or scripts should own exactness or safety;
- whether fallback behavior preserves essential outcomes when a preferred capability is unavailable.

Do not treat the existence of a platform feature as evidence that it improves this task. Distinguish static contract plausibility from observed selection and execution behavior.

## 5. Patch, bounded rewrite, full rewrite, or defer

Patch when the surrounding structure and ownership remain sound and a bounded change resolves the issue.

Use a bounded rewrite when one section or coherent cluster has obsolete framing, duplicated obligations, or the wrong structure while the artifact's larger role remains valid.

Use a full rewrite when:

- the artifact's role, authority, capability form, or deployment model changes;
- its structure repeatedly causes drift, conflicts, missed selection, or unreliable use;
- local patches would preserve a misleading frame;
- consolidation or separation changes the owner model;
- rebuilding from a clean contract is safer than overlapping edits.

Defer when a required source, owner decision, user authorization, runtime capability, or compatible target is missing.

Preserve stable interfaces during ordinary patches. During an explicit rebaseline, evaluate whether each interface still earns preservation; migrate justified changes instead of retaining historical baggage solely because an old standard locked it.

## 6. Exact change interface

Placement guidance and exact replacement text are different artifacts. Keep commentary outside copy-ready text.

Use this pattern when a change must be applied mechanically:

```text
Target artifact: [path or document]
Target: [heading, interface, or exact location]
Change type: insert | replace | delete | move | rename

Placement guidance:
[Human-readable instructions.]

Exact text:
~~~text
[Only text intended to be applied.]
~~~

Dependent updates:
- [Reference, version, schema, test, or generated output affected.]
```

Increase outer fence depth when exact text contains fences. Validate the result against the target interface and every named dependent surface.

## 7. Migration and supersession sequence

Structural migrations involving authority, interfaces, dependents, or generated state have real sequence dependencies. Use this order unless the target system establishes a safer one. Ordinary bounded edits do not require migration artifacts merely because they change a file.

1. Inventory current active sources, interfaces, status, and known dependents.
2. Define the target owner model and old-to-new crosswalk.
3. Classify current material as keep, merge, move, localize, retire, pilot, or archive.
4. Draft the replacement without prematurely changing current authority.
5. Validate content, interfaces, references, tooling, and representative use.
6. Prepare dependent and generated-output updates without activating them.
7. Preserve an unchanged archival snapshot before changing active authority.
8. Execute the controlled transition atomically or in stages as appropriate. Keep active authority and compatible dependent state explicit throughout; do not allow old and new owners to compete silently. Complete activation, dependent updates, generated outputs, supersession, validation, and recovery or residual-risk evidence required by the task.

Preserve high-value identifiers when compatibility value exceeds structural cost. Retire low-value anchors, identifiers, or metadata through a crosswalk instead of carrying obsolete grammar indefinitely.

Historical reports and archives continue to describe the state they recorded. Do not rewrite them merely to make old identifiers appear current.

## 8. Static and behavioral validation

Validate in proportion to risk:

- documentation: headings, links, identifiers, status, authority, and required references;
- prompts and instructions: representative runs, exact output interfaces, source behavior, unnecessary obligations, and completion effort;
- knowledge and retrieval: need recognition, candidate selection, loading, freshness, authority, and correct use;
- skills: positive, negative, mixed, and overlapping triggers; resource loading; version/currentness; and fallback behavior;
- plugins, apps, MCP, and tools: availability, authentication, permissions, data/action contracts, errors, and degraded operation;
- architecture: persistent versus callable allocation, loaded working set, fragmentation, and ambiguous routing;
- tools and enforcement: narrow tests, dry runs, schemas, permissions, outputs, and generated artifacts;
- migrations: filename and DocID consistency, crosswalk completeness, stale references, export or build behavior, archive preservation, and rollback evidence.

Static checks show that a contract is coherent; they do not prove model behavior. Compare current and candidate guidance on matched representative tasks when behavioral improvement is claimed. Record the model, host, available context, tools, invocation method, and execution conditions. Check required outcomes and individual obligations separately from clarification, completion, and verification effort.

Treat unrun comparisons as validation gaps, not evidence of improvement. Report checks that could not be performed and what would resolve the gap.

## 9. Review output pattern and acceptance criteria

Use only sections that support the decision:

```text
Verdict
[Ready | Revise | Patch | Bounded rewrite | Full rewrite | Defer | No action]

Material findings
| Severity | Target | Finding | Evidence | Recommended action |
|---|---|---|---|---|

Acceptable tradeoffs or false positives
[Only when they prevent overcorrection.]

Change strategy
[Smallest responsible fix, migration, or next action.]

Material decisions and residual risks
[Non-obvious removals, moves, authority or capability changes, validation gaps, or uncertainty.]
```

The former “Reviewer Notice” behavior survives as the optional final section; its label is not mandatory.

Review or change work is complete when:

- the verdict answers the requested decision;
- findings are material, evidenced, and tied to an owner, runtime fact, or acceptance criterion;
- capability availability and retrieval behavior are observed or identified as assumptions;
- the change strategy matches the defect's true scope;
- exact interfaces and dependent surfaces are preserved or intentionally migrated;
- source authority and currentness are not inferred without support;
- migration order prevents old and new owners from competing silently;
- exact patch text is mechanically usable when requested;
- static and behavioral evidence are distinguished and validation limits remain visible;
- fallbacks are evaluated where capability availability varies;
- archives, reports, research, memory, and legacy sources remain historical or supporting rather than shadow authority.
