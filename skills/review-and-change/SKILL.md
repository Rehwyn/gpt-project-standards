---
name: review-and-change
description: Review project, prompt, knowledge, or capability systems; choose patch versus rewrite; draft exact changes; and plan migration or supersession. Do not use for first-pass creation without a review or change decision.
---

# Review and Change

Provide an independent, evidence-backed judgment and the smallest responsible change strategy. Do not affirm the author's preferred conclusion by default, invent findings to fill a count, or expand a review request into implementation without authorization.

## Callable standard depth

Handle ordinary review and bounded change work from this skill. Read only the relevant headings of [Review and Change Ops Standard](references/review-and-change-standard.md) when the task:

- involves a structural migration, supersession, rollback, or coordinated activation;
- spans several artifacts, owners, capability forms, or dependent interfaces;
- requires the exact change or review invocation patterns;
- claims behavioral improvement that needs matched validation design; or
- exposes material review, severity, or change-strategy ambiguity not resolved here.

The reference is a bundled snapshot of active standard `Review_And_Change_Ops_Standard` v2.0.0. Apply its relevant depth rather than summarizing it, and do not load it for routine review merely because it is available.

## Establish the review contract

Identify the decision the review must support, the governing requirements and exact interfaces, the actual runtime, and the breadth needed: local, whole artifact, cross-document, capability-system, or migration. Inspect current sources when authority, status, filenames, schemas, citations, or copy-ready wording matters.

Evaluate against evidence, risks, acceptance criteria, intended use, and environment—not style preference. State material uncertainty and unrun validation rather than inferring a pass.

Use severity when it helps action:

- **Must:** blocks readiness or breaks correctness, safety, authority, a required interface, migration continuity, capability availability, or the requested outcome.
- **Should:** materially affects reliability, clarity, maintenance, source or capability use, or coherence.
- **Nice:** optional polish without material correctness effect.

`No action` is a verdict or disposition for an acceptable tradeoff, false positive, or issue that does not warrant change; it is not a finding severity.

Group findings with one cause or fix and avoid false precision.

## Select checks by risk

Use only checks that can detect likely failures or support the decision. Consider readiness, exact interfaces, source authority and freshness, compression loss, runtime/capability fit, competing owners, trigger overlap, migration continuity, permissions, and adversarial or high-cost failures as relevant.

For ordinary local, reversible, and low-consequence work, direct inspection and cheap relevant checks may be sufficient. Escalate when consequence, uncertainty, irreversibility, external exposure, sensitive information, shared authority, dependent coupling, or exactness makes failure materially more costly.

For capability fit, distinguish:

- whether the host exposes the proposed mechanism;
- need recognition and source or skill selection;
- loading or invocation;
- freshness, authority, and correct application after retrieval;
- whether exactness belongs in a schema, validator, permission, test, or script;
- whether fallback behavior preserves essential outcomes.

Do not treat feature availability as evidence that the feature improves the design.

## Choose the change strategy

Patch when the owner model and surrounding structure are sound. Use a bounded rewrite when one coherent section or cluster has obsolete framing or duplication. Use a full rewrite when role, authority, deployment, or ownership changes, or local patches would preserve a misleading frame. Defer when a required source, decision, authorization, capability, or compatible target is missing.

Preserve stable interfaces during ordinary patches. During an explicit rebaseline, evaluate whether each interface still earns preservation and provide a crosswalk for justified changes.

Do not replace removed workflow narration with a shorter generic workflow unless sequence, state, approval, validation, or handoff is actually load-bearing. When a required fix belongs to an artifact outside the authorized target, keep the in-scope patch clean, name the dependent update, and leave readiness blocked or qualified until that owner is separately changed. Never invent missing interface details such as types, enums, requiredness, or additional-property behavior; preserve only supplied exact elements and identify the incomplete interface as a dependent blocker.

When exact text is requested, keep placement guidance outside the copy-ready block and provide:

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

Increase outer fence depth when nested content requires it.

## Protect migrations

For structural migration involving authority, interfaces, dependents, or generated state: inventory active sources and dependents; define the target owner model and crosswalk; classify material; draft without changing authority; validate content, interfaces, tooling, and representative use; prepare dependents without activation; and preserve an unchanged archive. Execute activation atomically or in controlled stages while keeping authority and compatible dependents explicit, then complete supersession, generated outputs, validation, and material recovery or residual-risk evidence. Ordinary bounded edits do not require migration artifacts merely because they change a file.

Keep historical reports and archives historically accurate. Do not leave old and new owners active together silently.

## Deliver and validate

Lead with a verdict: `Ready`, `Revise`, `Patch`, `Bounded rewrite`, `Full rewrite`, `Defer`, or `No action`. Report material findings with target, evidence, severity when useful, and recommended action. Include acceptable tradeoffs, change strategy, residual risks, and validation gaps only when they aid the decision.

Distinguish static contract checks from observed behavior. When behavioral improvement is claimed, compare matched tasks under recorded model, context, tools, invocation, and runtime conditions. Stop at findings, exact changes, or implementation according to the user's authorization.
