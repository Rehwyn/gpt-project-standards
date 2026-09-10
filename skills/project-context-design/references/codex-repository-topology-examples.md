# Codex Repository Topology Examples

Artifact Type: `Maintained platform-specific example set`
Status: `Maintained`
Last Reviewed: `2026-09-10`
Source Posture: `Illustrates the active Project Context and Capability Design Standard and the maintained Codex Repository Architecture guide. These examples calibrate judgment; they are not templates, required anatomy, or a maturity ladder.`

## 1. Use these examples selectively

Consult this file only after the relevant Codex repository architecture guidance when a concrete tree, comparison between plausible layouts, or translation from abstract boundaries to files would materially help.

Start from the smallest example that fits. Remove any directory, instruction file, Skill, state artifact, handoff, schema, or tool that does not earn its place through authority, discovery, reuse, lifecycle, execution, or validation. Rename generic labels to match the domain. A novel, home-network reference, research collection, and software project should not be forced into identical vocabulary.

The trees show where information could live, not what Codex automatically loads. Launch location, instruction discovery, Skill selection, and explicit file inspection remain separate concerns.

## 2. Minimal single-project repository

Use a compact layout when one project has one authority model and only a few recurring work types.

```text
repo/
├── AGENTS.md                 # thin repository-wide contract
├── README.md                 # human orientation and commands
├── project/                  # primary manuscript, site, docs, or code
├── references/               # durable facts or exact supporting material
├── scripts/                  # only existing maintenance or validation tools
└── archive/                  # optional, clearly non-current material
```

Possible authority and loading choices:

- Keep universal goals, safeguards, source precedence, and completion posture in the root `AGENTS.md`.
- Keep substantive content and domain facts in `project/` or `references/`, not in persistent instructions.
- Add `.agents/skills/<workflow>/` only after a recognizable recurring workflow warrants reusable callable guidance.
- Add a nested `AGENTS.md` only when nearly every task intentionally launched in that subtree needs a persistent local delta.
- Omit `archive/`, scripts, or any other shown surface when the project does not need it.

This is often enough for a solo novel, personal website, home-network documentation set, or small application.

## 3. Modular project-first repository

Use project-first organization when several initiatives share doctrine or tooling but each project owns its brief, sources, state, and outputs.

```text
repo/
├── AGENTS.md
├── README.md
├── .agents/
│   └── skills/               # shared recurring workflows
├── shared/
│   ├── INDEX.md              # concise discovery aid when needed
│   ├── doctrine/             # shared active guidance or canon
│   └── templates/            # exact reusable interfaces
├── projects/
│   ├── atlas/
│   │   ├── README.md         # local purpose, owners, and source map
│   │   ├── AGENTS.md         # only if Atlas needs a persistent local delta
│   │   ├── brief.md
│   │   ├── sources/
│   │   ├── work/
│   │   ├── state.md          # current progress, not doctrine
│   │   ├── handoffs/         # only for real stage or agent boundaries
│   │   └── outputs/
│   └── borealis/
│       └── ...
├── tools/                    # justified repository-wide checks
└── archive/                  # marked historical material
```

The project is the main semantic and authority unit. Shared Skills own reusable workflow; they do not require every project to copy `brainstorm/`, `draft/`, or `review/` directories. Add stage directories or handoffs only when those states or transitions must remain visible and durable.

Do not add every surface at repository creation. A project can begin with `brief.md`, `sources/`, and `outputs/`, then acquire state, handoffs, local instructions, or validation only when actual work creates the need.

## 4. Lane-first exception

Prefer a lane-first boundary only when the lane has persistent differences stronger than ordinary workflow reuse—for example separate permissions, maintainers, tooling, retention, or an independently governed intake/output contract.

```text
repo/
├── AGENTS.md
├── projects/                 # project truth and accepted outputs
└── lanes/
    └── regulated-review/
        ├── AGENTS.md         # persistent lane-specific safeguards
        ├── intake/           # explicit accepted inputs
        ├── procedures/       # authoritative lane rules
        └── outputs/          # review artifacts returned to projects
```

If drafting, review, or research differs only by reusable method, keep project truth together and express the method as a Skill. Do not create top-level lanes merely to make procedures easy to find.

## 5. Launch location and instruction chain

Given:

```text
repo/
├── AGENTS.md
└── projects/
    └── atlas/
        ├── AGENTS.md
        └── site/
            └── AGENTS.md
```

Current Codex instruction discovery makes the intended launch location part of the design:

```text
Launch at repo/                  → global instructions + repo/AGENTS.md
Launch at projects/atlas/       → global + root + atlas instructions
Launch at projects/atlas/site/  → global + root + atlas + site instructions
```

A root-started run does not acquire a descendant instruction file merely because it later edits a file there, and changing directories mid-run should not be assumed to rebuild the chain. Put a local instruction file in the tree only when work is intentionally launched from that scope. An `AGENTS.override.md` replaces the ordinary instruction source at its directory level; use it only when replacement is intended. Recheck current Codex mechanics and the target surface before relying on any of these behaviors.

Worktrees provide isolated mutable checkouts for concurrent work. They do not change which source is authoritative, replace a project/state model, or make an ambiguous tree coherent.

## 6. Adaptation questions

Before proposing a tree, ask only the questions that change it:

- What is the semantic unit whose truth should remain locally answerable?
- Which rules must shape nearly every run, and which are conditional workflows or references?
- Which sources own doctrine, current state, exact interfaces, generated outputs, and history?
- Are nested launches actually used, making local instruction scope meaningful?
- Do permissions, lifecycle, tooling, or release boundaries justify modules, lanes, or separate repositories?
- Which displayed files and directories can be removed without reducing correctness, discovery, authority, or validation?

Return an adapted tree with the material choices explained. Never reproduce an example unchanged merely because it is available.
