# Project Standards

Capability-aware standards and reusable skills for designing reliable LLM projects, prompts, context systems, and controlled changes.

The project favors minimum-sufficient guidance: communicate the goal, necessary context, important constraints, authority, exact interfaces, and success conditions while allowing capable models or agents to infer non-load-bearing method. Allocate work to the least costly reliable mechanism supported by the actual environment, whether persistent instructions, task prompts, reference documents, skills, tools, validators, or direct inspection.

## Standards

- [Project Context and Capability Design Standard](standards/Project_Context_And_Capability_Design_Standard.md) governs project setup, context and capability allocation, persistent instructions, knowledge and prompt design, reusable capabilities, discovery, and environment-specific deployment.
- [Review and Change Ops Standard](standards/Review_And_Change_Ops_Standard.md) governs independent review, material findings, capability-fit evaluation, bounded changes, interface validation, and migrations.

Both standards are Active at version 2.0.0. Stable filenames identify their interfaces, and the metadata inside each file identifies its released version. Version 2.0.0 replaces the former numbered Document IDs and filenames with semantic identities; prior tags preserve the numbered interfaces.

The v2.0.0 bundle also adds an optional hybrid project/workflow/subject topology for complex repositories whose recurring operating domains cross projects and durable subject areas. The boundary must earn its cost; smaller repositories should retain simpler project-first layouts.

## Skills

The repository also provides three focused skill bundles:

- [Project Context Design](skills/project-context-design/SKILL.md) designs or revises project instructions, source architecture, capability allocation, reference documents, and split-or-merge decisions. It conditionally loads the project and capability standard for consequential or ambiguous architecture work, a maintained Codex repository-architecture reference when filesystem or Git structure materially affects Codex execution, and concrete topology examples only when a layout or comparison would help.
- [Prompt Design](skills/prompt-design/SKILL.md) creates or revises one-off prompts, reusable prompts, invocation wrappers, research prompts, and Deep Research prompts.
- [Review and Change](skills/review-and-change/SKILL.md) reviews project, prompt, knowledge, or capability systems and plans controlled patches, rewrites, migrations, or supersession. It includes the review and change standard as callable depth for structural or cross-artifact work.

The skills share canonical doctrine where appropriate while retaining distinct selection boundaries. Their bundled references are intended for selective loading, not routine use.

## Using the materials

Use the standards directly as project knowledge or design guidance when the host supports document context. In environments that support reusable skills, install or upload the complete directory for each desired skill so its metadata and conditional references remain together.

Choose only the capabilities the environment actually supports. A project can use the standards without installing the skills, and a focused task can use an individual skill without loading every standard.

## License

Released under the [MIT License](LICENSE).
