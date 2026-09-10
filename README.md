# Project Standards

Capability-aware standards and reusable skills for designing reliable LLM projects, prompts, context systems, and controlled changes.

The project favors minimum-sufficient guidance: communicate the goal, necessary context, important constraints, authority, exact interfaces, and success conditions while allowing capable models or agents to infer non-load-bearing method. Allocate work to the least costly reliable mechanism supported by the actual environment, whether persistent instructions, task prompts, reference documents, skills, tools, validators, or direct inspection.

## Standards

- [Project Context and Capability Design Standard](standards/0-01__Project_Context_And_Capability_Design_Standard.md) governs project setup, context and capability allocation, persistent instructions, knowledge and prompt design, reusable capabilities, discovery, and environment-specific deployment.
- [Review and Change Ops Standard](standards/0-02__Review_And_Change_Ops_Standard.md) governs independent review, material findings, capability-fit evaluation, bounded changes, interface validation, and migrations.

The Project Context and Capability Design Standard is Active at version 1.0.0; the Review and Change Ops Standard is Active at version 1.0.1. Stable filenames identify their interfaces, and the metadata inside each file identifies its released version.

The v1.1.2 bundle adds selectively loaded Codex repository topology examples for concrete layout and comparison requests. The examples remain subordinate calibration aids rather than required templates. It retains the v1.1.1 proportional review guidance and refined Codex architecture reference.

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
