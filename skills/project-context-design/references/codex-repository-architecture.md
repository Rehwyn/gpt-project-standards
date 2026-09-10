# Codex Repository Architecture

Artifact Type: `Maintained platform-specific application guide`
Status: `Maintained`
Last Reviewed: `2026-09-10`
Source Posture: `Applies the active Project Context and Capability Design Standard to source-controlled Codex work. The standard owns general doctrine. Current official OpenAI documentation owns Codex platform mechanics. This guide does not apply to ordinary ChatGPT Project design or generic codebase organization.`

## 1. Use and when repository architecture matters

Use this guide when the target runtime is Codex and filesystem or Git structure materially affects instruction scope, source discovery, authority, workflow transitions, concurrent execution, or validation.

Do not use it merely because work happens in a repository. Ordinary code organization should follow the codebase's domain and build needs. Ordinary ChatGPT Project design does not inherit Codex's Git-root, current-working-directory, worktree, or repository-skill behavior.

The governing objective is:

> Design the shortest reliable path from task to applicable instructions, authoritative sources, current state, and a valid output.

Repository size alone does not determine architecture. Split, scope, or add routing when semantic cohesion, authority, loading, ownership, lifecycle, permissions, or observed retrieval behavior warrants the boundary.

## 2. Verify the actual Codex environment

Before recommending a structure, inspect what the current host and repository actually expose:

- Git or other project-root markers and the intended launch directory;
- root and nested instruction files;
- repository, user, admin, and system skills visible to the host;
- trusted project configuration, rules, hooks, tools, validators, and permissions;
- current source, state, handoff, generated-output, and archive conventions;
- worktree or parallel-task behavior relevant to the requested workflow.

Do not infer platform behavior from another agent product. Recheck time-sensitive mechanics against current official OpenAI documentation before implementing configuration, relying on a limit, or designing around discovery behavior.

As verified on 2026-09-10:

- Codex constructs an instruction chain once per run, starting with Codex-home guidance and then walking from the project root toward the current working directory. At each directory it selects at most one non-empty instruction source, preferring `AGENTS.override.md`, then `AGENTS.md`, then configured fallback filenames. More local guidance appears later and can override broader guidance. The combined project-instruction limit is controlled by `project_doc_max_bytes` and defaults to 32 KiB. See [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md).
- Skills use progressive disclosure: name and description are exposed for selection, while the full `SKILL.md` loads after explicit or implicit invocation. Codex scans repository `.agents/skills` locations from the current working directory up to the repository root. Same-named skills are not merged. See [Build skills](https://learn.chatgpt.com/docs/build-skills).
- Trusted project `.codex/config.toml` files layer from the project root toward the current working directory, with nearer values winning. Some user-level settings cannot be overridden by project configuration. See [Advanced Configuration](https://learn.chatgpt.com/docs/config-file/config-advanced).
- Codex worktrees provide independent checkouts for parallel chats while sharing repository history. They isolate mutable work; they do not repair ambiguous information architecture. See [Worktrees](https://learn.chatgpt.com/docs/environments/git-worktrees).

These are platform facts, not permanent doctrine. Preserve the architectural outcome if the exact mechanisms change.

Evidence boundary: the linked mechanics above were checked against official documentation on the review date. They are documented behavior, not evidence that this draft's routing improves runtime outcomes. Launch-location effects, source selection, and behavior under parallel execution remain pilot questions until observed and recorded.

## 3. Design four topologies separately

Do not use one directory tree as an implicit answer to four different questions.

| Topology | Question | Design concern |
|---|---|---|
| Repository | What belongs in one Git history and working universe? | Coupling, ownership, permissions, lifecycle, atomic change, and shared artifacts |
| Context | What is automatically present, conditionally loaded, or inspected on demand? | Salience, discovery, selection, context cost, and omission risk |
| Authority | Which source governs when several artifacts discuss the same subject? | Ownership, status, precedence, exact interfaces, and stale material |
| Workflow | How does accepted work move between activities or agents? | State, decisions, handoffs, approvals, outputs, and validation gates |

A monorepo is a repository-boundary choice, not a complete context strategy. A worktree is execution isolation, not a work-stream or authority model. A folder is not an instruction scope merely because Codex can place an `AGENTS.md` there.

## 4. Allocate repository information by role

Give each durable requirement one primary owner and use other surfaces only to route, execute, validate, or present it.

| Information | Primary surface | Boundary |
|---|---|---|
| Universal repository purpose, invariants, authority, and completion posture | Root `AGENTS.md` | Keep thin and routinely applicable |
| Persistent behavior genuinely shared by tasks launched in one subtree | Nested `AGENTS.md` | State the local delta; do not duplicate the root |
| Conditional reusable workflow | Skill | Use a distinctive trigger and load detailed references only when relevant |
| Substantive doctrine, canon, evidence, specification, or reference depth | Indexed ordinary file | Keep inspectable, status-marked, and independently maintained |
| Current decisions, progress, assignments, or known issues | State artifact | Do not let volatile state become doctrine |
| Accepted transition between stages | Handoff artifact | Name authoritative inputs, accepted decisions, unresolved items, exclusions, and acceptance criteria |
| Deterministic structure or safety boundary | Schema, validator, permission, test, rule, hook, or script | Do not rely only on prose when the host can enforce it |
| Generated presentation or delivery surface | Reproducible derivative | Edit the maintained source and regenerate |
| Retired or superseded material | Marked archive | Preserve history without competing with current authority |

An index routes by topic, purpose, status, and use condition. It should not restate the indexed doctrine. A handoff narrows rich upstream exploration into the accepted subset downstream work may rely upon. A state file records where work stands; it does not silently revise the brief or owner source.

## 5. Choose repository boundaries deliberately

### Modular monorepo

Prefer one modular repository when projects or work streams share substantial doctrine, state, artifacts, tooling, and history; when transitions are frequent; or when atomic cross-area changes matter. Use semantically coherent subtrees, thin persistent instructions, conditional Skills, indexed sources, and explicit handoffs to prevent the shared repository from becoming a shared ambiguity surface.

### Project-first organization

Prefer project-first subtrees when brainstorming, drafting, review, implementation, or publication stages share one project's truth. Keep its brief, sources, state, decisions, handoffs, outputs, and archive close enough that “what is true for this project?” has a local answer. Centralize reusable stage procedures as Skills instead of copying them into every project.

### Lane-first organization

Prefer lane-first organization when the lane has genuinely distinct ownership, permissions, tooling, retention, or persistent operating rules and receives narrow, explicit inputs from projects. Do not use lane-first layout merely to make procedures easy to find; a Skill can provide reusable procedure without fragmenting project truth.

### Executable modules or workspaces

Use package, module, or workspace machinery when a unit has meaningful executable independence, such as its own dependencies, build or test commands, deployment target, or enforceable interface. Do not introduce that machinery merely to mirror workflow phases, reduce an assumed context window, or make a document-heavy repository appear modular; semantically coherent directories are sufficient when the units do not need independent execution contracts.

### Polyrepo or shared-core hybrid

Split repositories when the boundary is independently justified by permissions, security, ownership, release cadence, retention, tooling environment, or weak coupling. Do not split solely to reduce instruction context or file count. A shared-core model needs a versioned distribution or materialization contract; a reference to important doctrine in another inaccessible repository is not reliable context.

### Worktrees

Use worktrees when concurrent tasks need isolated mutable checkouts of the same Git repository. Give each task a separate branch or detached worktree state as the host requires. Continue to define authority, source selection, workflow stage, and handoff contracts inside the repository; cloning a confused structure does not clarify it.

## 6. Place instructions and Skills by selection need

Keep the root `AGENTS.md` limited to information that should shape nearly every repository task:

- repository purpose and optimization target;
- project-wide invariants and authorization boundaries;
- authoritative-source rules and ambiguity fallback;
- concise routing cues;
- a small set of broadly applicable validation or completion requirements.

Create a nested instruction file only when nearly every task intentionally launched in that subtree needs persistent behavior that differs from the parent. Because an override replaces the ordinary instruction file at its directory level, use `AGENTS.override.md` only when replacement is intentional.

Use a repository Skill when a recognizable task type needs conditional procedure, references, assets, or scripts. Keep must-not-miss repository invariants in persistent instructions or enforceable controls; successful Skill discovery should not be the sole safety mechanism for a requirement that cannot be missed.

Treat launch location as part of the design because current instruction and repository-skill discovery are path-sensitive. Verify the actual chain with a fresh Codex run in the intended working directory. Do not assume that changing directories inside an existing run rebuilds startup context.

Opening or editing a descendant file from a root-launched run does not activate that descendant's `AGENTS.md`. When local instructions materially affect correctness, start a fresh run in the intended working directory and verify the effective instruction chain on the Codex surface being used.

## 7. Make workflow transitions explicit

Use an explicit handoff when a downstream stage must consume a controlled subset of upstream work, rejected alternatives must remain excluded, or acceptance changes authority.

A useful handoff identifies:

```markdown
# [Source stage] to [target stage] handoff

Status: `[Draft | Accepted | Superseded]`
Project: `[project identifier]`

## Accepted outcome
[What the downstream stage may treat as selected.]

## Authoritative inputs
- `[exact path]`

## Decisions already made
- [Decision downstream work should preserve.]

## Deliberately unresolved
- [Question the downstream stage may decide.]

## Excluded material
- [Rejected or non-authoritative input that must not leak forward.]

## Acceptance criteria
- [Required downstream result or validation gate.]
```

This is an adaptable pattern, not a mandatory schema. Promote it to a schema or validator only when repeated workflows depend on exact fields or automated checks.

## 8. Enforce what should not drift

Use repository tooling when a rule can be checked deterministically and the consequence of drift justifies maintenance. Candidate checks include:

- referenced authoritative paths exist;
- accepted handoffs contain required fields and do not unintentionally point into archives or rejected material;
- canonical identifiers are unique;
- generated derivatives match their maintained sources;
- indexes do not point to missing or superseded owners;
- current pointers resolve and active-owner declarations remain unique;
- status values are valid, archived or superseded references are marked, and required provenance is present;
- forbidden dependency directions are absent;
- public packages contain only allowlisted and sanitized files.

Keep tools read-only or check-only by default unless their write contract is explicit. Validate the current source and interface rather than making the tool infer authority from filenames or age.

## 9. Failure patterns

Avoid:

- a giant root `AGENTS.md` containing doctrine, examples, procedures, inventories, and volatile state;
- an instruction file in every directory without a persistent semantic difference;
- duplicated doctrine under each project or workflow lane;
- indexes that summarize enough content to become shadow owners;
- unmarked archives or sequences such as `final`, `final2`, and `final-revised` competing for authority;
- one undifferentiated notes file combining requirements, decisions, transient status, and handoffs;
- repository splits justified only by token assumptions;
- treating worktrees, branches, tasks, agents, and workflow stages as interchangeable boundaries;
- prose-only enforcement for exact interfaces or high-cost invariants;
- assuming that available Skills, files, or tools will always be selected correctly.

## 10. Validate the architecture

Before activation:

1. Verify the project root, intended launch directories, active instruction chain, visible Skills, and trusted configuration.
2. Test representative positive, negative, mixed, and overlapping tasks rather than only checking file presence.
3. Confirm correct source selection when current, draft, superseded, informal, and archived material coexist.
4. Compare direct discovery with any proposed map or router; keep the extra layer only when it improves a material ambiguity.
5. Test handoffs against unstructured upstream material when transition precision is important.
6. Test concurrent work in isolated checkouts when worktree use is part of the design.
7. Run link, schema, validator, generated-output, privacy, and release checks owned by the repository.
8. Record current platform facts, inference, observed behavior, and unrun scenarios separately.

Do not claim that a structure improves behavior from static plausibility alone. If a smaller architecture passes the same representative tasks, prefer it.
