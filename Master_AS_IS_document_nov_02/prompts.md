-----------Skill Generation Prompt--------------

Generate a Project-Specific AS-IS Design Document Generator Skill

You are acting as a **Senior Solution Architect, Business Analyst, Data Engineer, Technical Documentation Specialist, and Claude Code Skill Engineer**.

Your task is to create a final, reusable, project-specific Claude Code skill named:

`as-is-design-document-generator`

Use the existing `CLAUDE.md` and `Master_skill.md` as the authoritative instructions for this task. Analyze all relevant project evidence available inside the `input/` directory.

**Objective:** Preserve approximately 75% of the master instructions as reusable generic instructions and dynamically generate the remaining 25% as project-specific instructions based on the evidence discovered in `input/`.

**Workspace paths:**
- Workspace instructions: `./CLAUDE.md`
- Master skill: `./Master_skill.md`
- Project evidence: `./input/`
- Final skill: `./.claude/skills/as-is-design-document-generator/SKILL.md`

**Instructions:**

1. Read and follow `CLAUDE.md` first, particularly its Skill Creation Rules and Skill Creation Validation requirements.
2. Read the complete `Master_skill.md` and identify its generic and project-specific sections.
3. Analyze all relevant evidence recursively inside `./input/`.
4. Preserve the complete generic section from `Master_skill.md`, including all documentation, security, quality assurance, and validation instructions.
5. Generate the project-specific configuration using only evidence-supported information.
6. Append the newly generated project-specific configuration immediately after the generic section, replacing the existing project-specific example.
7. Perform the independent master-preservation, evidence-accuracy, completeness, and final-file validation defined in `CLAUDE.md`.
8. Correct identified issues before saving the final skill.

Do not modify `CLAUDE.md` or `Master_skill.md`.

**This is a SKILL CREATION TASK ONLY.**

- Do NOT generate the final AS-IS Word document.
- Do NOT create unnecessary intermediate skill files.
- Save the completed skill directly to `./.claude/skills/as-is-design-document-generator/SKILL.md`.
- Report the validation results and any unresolved evidence gaps.




------to generate design doc-------

Act as a Senior Solution Architect and generate the complete professional AS-IS / Current-State System Design Document.

Follow `CLAUDE.md` and the project-specific `as-is-design-document-generator` skill. Analyze all available project evidence and use Draw.io MCP for relevant diagrams.

Save the final deliverables in the configured output directory.