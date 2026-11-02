# CLAUDE.md

# AI-Assisted AS-IS / Current-State System Documentation

## 1. Project Purpose

This workspace supports two related workflows:

1. **Skill Creation:** Generate a project-specific Claude Code skill using `Master_skill.md` and the available project evidence.
2. **AS-IS Documentation:** Use the generated skill to produce an accurate, evidence-based AS-IS / Current-State System Design Document.

This file defines the permanent operating rules for both workflows.

`Master_skill.md` defines the reusable instructions for AS-IS document generation. The generated `SKILL.md` combines those generic instructions with project-specific configuration.

All instructions must remain generic. Project-specific facts belong in the input evidence and generated skill, not in this file.

---

## 2. Workspace Structure

Use the following default structure:

```text
AS_IS_migration/
├── CLAUDE.md
├── Master_skill.md
├── input/
├── output/
└── .claude/
    └── skills/
        └── as-is-design-document-generator/
            └── SKILL.md
```

Default locations:

- Master template: `./Master_skill.md`
- Project evidence: `./input/`
- Customized skill: `./.claude/skills/as-is-design-document-generator/SKILL.md`
- Final deliverables: `./output/`

If a valid project-level configuration specifies different paths, follow that configuration.

Do not assume that every project contains the same types of evidence.

---

## 3. Operating Modes

Determine which workflow the user requests.

### Mode A — Skill Creation

Use this mode when asked to create, customize, regenerate, or update the AS-IS generator skill.

Required inputs:

- `Master_skill.md`
- Available project evidence in `./input/`

Output:

- `./.claude/skills/as-is-design-document-generator/SKILL.md`

Do not generate the actual AS-IS Word document during this workflow.

### Mode B — AS-IS Document Generation

Use this mode when asked to generate or update an AS-IS design document.

Required instructions:

- This `CLAUDE.md`
- The generated project-specific `SKILL.md`
- Any additional design specifications referenced by the skill, if available

Use all relevant evidence available in the configured input location.

Output:

- Design Document.docx
- Relevant editable diagrams
- STTM.xlsx when applicable
- Work and QA artifacts

Do not regenerate the customized skill unless explicitly requested.

---

## 4. Genericity and Separation of Responsibilities

Keep responsibilities separate:

| Artifact | Responsibility |
|---|---|
| CLAUDE.md | Workspace rules, workflow selection, skill creation, validation and tool usage |
| Master_skill.md | Reusable AS-IS documentation instructions |
| SKILL.md | Generic master instructions combined with project-specific configuration |
| Project evidence | Source of project-specific facts |
| Output | Generated documentation and supporting artifacts |

Never hardcode project names, customers, business domains, technologies, servers, databases, owners, or other project-specific details in this file.

Do not duplicate detailed instructions already maintained in the master template or customized skill.

---

## 5. Skill Creation Rules

When generating or updating the project-specific skill:

1. Treat `Master_skill.md` as the authoritative master template.
2. Read the complete master template before generating the skill.
3. Inspect all relevant files recursively inside `./input/`.
4. Preserve the complete generic master section without omitting or weakening its instructions.
5. Generate the project-specific configuration using evidence from the current project.
6. Replace the existing project-specific placeholder or example completely.
7. Append the new project-specific configuration immediately after the generic master section.
8. Do not retain outdated facts from another project.
9. Do not invent missing information or silently resolve conflicting evidence.
10. Protect credentials, passwords, tokens, keys, and sensitive information.
11. Preserve valid Claude Code skill frontmatter and structure.
12. Save the final skill directly to the configured skill path.

Do not modify `Master_skill.md` unless explicitly requested.

Do not create unnecessary intermediate skill files.

### 5.1 Skill Creation Validation

Before saving the final `SKILL.md`, perform an independent validation.

**Master preservation:**
- Verify that all generic sections from `Master_skill.md` are preserved.
- Confirm that all recently added QA and security instructions are retained.
- Confirm that the old project-specific example has been replaced.

**Evidence accuracy:**
- Verify important project facts against the original evidence.
- Check exact system names, servers, databases, tables, procedures, jobs, schedules, technologies, paths, and ownership.
- Distinguish confirmed, inferred, unknown, conflicting, and TBC information.
- Do not invent missing facts or expand abbreviations without evidence.

**Completeness:**
- Check that important business processes, technical components, integrations, dependencies, inputs, outputs, and operational requirements are represented.
- Preserve important exceptions and limitations.
- Separate current-state facts from future-state recommendations.

**Final review:**
- Compare the generated skill against both the master and original evidence.
- Correct all identifiable errors.
- Verify frontmatter, section order, project-specific configuration, and final save location.

If evidence is incomplete or contradictory, preserve the uncertainty in the generated skill.

Report validation results and unresolved gaps after completion.

---

## 6. Evidence Handling Rules

Evidence may include:

- Word, PDF, Excel, and PowerPoint documents
- Existing design documents
- Architecture diagrams and screenshots
- Meeting notes and transcripts
- Walkthrough videos
- SQL and database definitions
- Source code and scripts
- JSON, YAML, XML, and configuration files
- API specifications
- Infrastructure and deployment definitions
- Job definitions, logs, and operational records

Inspect the available evidence dynamically.

Do not assume every file type or artifact will exist.

For every important statement:

- Identify its supporting evidence.
- Preserve the source filename and relevant locator where practical.
- Distinguish direct evidence from technical interpretation.
- Identify contradictions and unresolved questions.
- Do not claim that a source was inspected if it was not.

For Word documents, inspect embedded review comments and reply threads when present. Treat comments as evidence and distinguish resolved facts from unresolved discussions.

Never reproduce actual credentials, tokens, passwords, keys, or real sensitive personal values.

---

## 7. Source-of-Truth and Accuracy

Use the following general evidence priority:

1. Direct technical implementation and configuration
2. Authoritative technical documentation
3. Explicit system-owner or SME information
4. Structured walkthrough notes
5. Walkthrough and video evidence
6. Architecture diagrams
7. Meeting and workshop notes
8. General project documentation
9. AI inference

Adjust this hierarchy when the project defines a different authoritative source.

Code demonstrates implementation logic but does not necessarily prove that the code is deployed or executed in production.

When sources conflict:

- Preserve both pieces of evidence.
- Identify the conflict.
- Determine which source appears more authoritative.
- Mark the issue as CONFLICTING.
- Record an open question where necessary.

Never prioritize document completeness over factual accuracy.

---

## 8. Draw.io MCP and Diagram Generation

Use **Draw.io MCP** for architecture and process diagram generation when it is available.

Prefer native, editable `.drawio` files rather than static images.

Generate diagrams based on the documented current-state understanding.

Depending on the evidence, relevant diagrams may include:

- System Context
- Current-State Architecture
- Business or Technical Process Flow
- Data Flow
- API and Integration Flow
- Data Processing Flow
- Security and PII Flow
- Deployment and Infrastructure View

### Diagram requirements

- Represent the actual current state.
- Use evidence-backed components only.
- Maintain consistent names across the model, diagrams, and document.
- Show correct relationships and data direction.
- Use pinned connector entry/exit points and orthogonal routing where supported.
- Avoid overlapping shapes, clipped labels, tangled connectors, and unreadable text.
- Split complex diagrams rather than overcrowding them.
- Keep diagrams editable.

Save native diagrams under:

`./output/diagrams/`

### Diagram validation

Creating a `.drawio` file is not sufficient.

Render and visually inspect every generated diagram before delivery.

Check layout, alignment, connector routing, labels, readability, page fit, and consistency with the document.

Export appropriate PNG or SVG versions for embedding in the Word document.

If Draw.io MCP is unavailable, report the limitation. Do not claim that Draw.io diagrams were generated.

---

## 9. Output Management

Use the configured output directory.

Default structure:

```text
output/
├── Design Document.docx
├── STTM.xlsx
├── diagrams/
├── work/
└── qa/
    └── qa_report.md
```

Generate STTM.xlsx when transformation code or sufficient source-to-target mapping evidence is provided and the applicable skill instructions require it.

Keep working artifacts separate from final deliverables.

Do not overwrite existing deliverables without checking whether the user intends an update or a new version.

---

## 10. Quality Assurance and Delivery

For actual AS-IS document generation, follow the mandatory QA requirements in `Master_skill.md` as preserved in the customized skill.

At minimum, validate:

- Evidence accuracy and traceability
- Completeness of important system components and flows
- Technical identifiers and schedules
- Consistency between the document and diagrams
- Current-state versus future-state separation
- Security and sensitive information handling
- Open questions, conflicts, assumptions, and unknowns
- Diagram rendering and visual quality
- Final Word document rendering and readability

Save the QA report under:

`./output/qa/qa_report.md`

Use one of these delivery statuses:

- READY FOR STAKEHOLDER REVIEW
- REVIEW REQUIRED
- VALIDATION FAILED

Never claim formal approval or production readiness without the required human sign-off.

---

## 11. Final Operating Principle

Follow this sequence:

**For skill creation:**

```text
Master Template
      +
Project Evidence
      ↓
Generic Instruction Preservation
      ↓
Project-Specific Configuration
      ↓
Independent Validation
      ↓
Final SKILL.md
```

**For AS-IS documentation:**

```text
CLAUDE.md + Customized SKILL.md
                +
          Project Evidence
                ↓
        Evidence Analysis
                ↓
       Current-State Model
                ↓
         Documentation
                ↓
       Draw.io Diagrams
                ↓
        Technical QA
                ↓
          Visual QA
                ↓
         Final Deliverables
```

The primary objective is always an accurate, traceable, technically detailed representation of the system as it currently exists.

When evidence is incomplete, document the uncertainty. Never invent an answer to make the document appear complete.