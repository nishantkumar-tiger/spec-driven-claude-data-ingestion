---
name: as-is-design-document-generator
description: Generate evidence-based AS-IS design documents from project intake forms, reference documents, source files, technical artifacts, and operational evidence. Use when asked to analyze, document, or update the current state of a business process, application, data solution, or infrastructure.
---

# AS-IS Design Document Generator — Master Skill

> **Team usage:** This is the reusable master skill. The generic framework is intended to remain stable. The section marked **PROJECT-SPECIFIC CONFIGURATION — CUSTOMIZE THIS SECTION** must be reviewed and updated for each new project. Do not carry project-specific facts from one project into another.

## 1. Purpose and outcome

Create a clear, complete, evidence-based AS-IS design document describing how the selected business process, application, data solution, or infrastructure currently works.

The document must help business stakeholders, analysts, engineers, architects, operations teams, and modernization teams understand the current state. It must distinguish the existing implementation from proposed improvements or target-state ideas.

The normal deliverable is a Microsoft Word document (`.docx`), unless the project's `CLAUDE.md` specifies another format.

## 2. Configuration and project instructions

Before analysis:

1. Read CLAUDE.md if it exists.
2. Follow its project-specific instructions and configured paths.
3. If CLAUDE.md does not exist, use the following defaults:
   - Project inputs: ./input/
   - Output directory: ./output/
   - Output format: DOCX
4. Discover and analyse all relevant files inside the configured input directory.
5. Do not assume that files are separated into business, technical, reference, or inventory folders.
6. Use available reference documents as structural and quality references.
7. Do not assume that every project has a reference document.
8. Do not invent missing configuration values.

`CLAUDE.md` is the source of truth for file paths and run-specific settings. Do not hardcode local paths in this skill.

## 3. Discover and inventory the evidence

Inspect the configured input and reference locations. Discover files dynamically; do not assume that every project supplies the same file types or inventory.

Potential evidence includes:
- Intake forms, questionnaires, business requirements, and stakeholder notes
- Existing AS-IS documents, process documents, SOPs, and runbooks
- Architecture diagrams, design documents, interface specifications, and data dictionaries
- Source code, SQL, configuration files, scripts, API specifications, and package definitions
- Job schedules, orchestration configurations, logs, monitoring outputs, and incident records
- Spreadsheets, inventories, system lists, application catalogues, and environment details

Create an evidence inventory for the analysis. Classify each relevant item by type, purpose, version/date (if available), and the aspects of the process it can support.

If multiple versions exist, identify the likely current version using dates, version labels, or metadata. If version order cannot be established, flag it for confirmation.

Do not assume a file is relevant merely because it is present. Do not omit a relevant file merely because its extension or name is unfamiliar; inspect it where tools permit.

## 4. Evidence, traceability, and accuracy rules

These rules are mandatory:

- Separate confirmed facts, stakeholder-reported information, assumptions, inferences, conflicts, and open questions.
- Prefer implementation evidence (source code, configuration, scheduler definitions, package contents, logs) for technical behavior. Use intake forms and interviews for business intent, ownership, and reported operations.
- Treat an existing AS-IS document as a reference for structure and context, not automatic proof that all details remain current.
- Preserve exact system names, object names, schemas, paths, job names, API names, file formats, and identifiers as supplied. Do not silently rename or normalize them.
- Do not infer functionality from a filename, table name, or component name alone.
- Do not claim a component, interface, schedule, control, or dependency is active unless evidence supports that claim.
- Distinguish configured schedules from observed run times, source refresh frequency from process execution frequency, and process execution from downstream delivery.
- When sources disagree, document both versions, identify their sources, explain the impact, and mark the item **Conflict — confirmation required**. Do not silently choose one.
- Mark unavailable information as **Not provided**, **Not verified**, or **To be confirmed**. Never invent values to make a section look complete.
- Attribute important facts to their source file and, where practical, page, section, code object, or line range. Maintain an evidence register when useful.
- Do not reproduce personal, confidential, or security-sensitive information unnecessarily.

## 5. Understand the business and operational context

Establish, where evidence is available:
- Business purpose, objectives, users, stakeholders, and expected outcomes
- Process boundaries, scope, exclusions, triggers, inputs, and outputs
- Business owners, process owners, system owners, data owners, technical owners, and support teams
- Business rules, decisions, exceptions, approvals, and manual activities
- Service expectations, SLAs, cut-off times, calendars, and operational dependencies
- Downstream consumers and the business impact of delays, failures, or incorrect outputs

Explain domain terminology and expand acronyms on first use.

## 6. Reconstruct the current-state solution

Adapt the analysis to the actual project domain. Do not force every project into a data-engineering or application-centric model.

- **Data solution:** investigate sources, ingestion, staging, transformations, data quality, lineage, storage, outputs, and consumers.
- **Application:** investigate users, components, user journeys, business logic, APIs, integrations, persistence, authentication, deployment, and runtime dependencies.
- **Business process:** investigate activities, roles, decisions, approvals, hand-offs, exceptions, controls, and supporting systems.
- **Infrastructure:** investigate environments, compute, storage, networks, connectivity, identity, security boundaries, dependencies, monitoring, backup, and recovery.
- **Mixed solution:** combine the relevant views.

Trace the end-to-end process from its trigger or entry point through processing and controls to its outcome and consumers. Use technical artifacts to verify details. Where source code or configuration is available, inspect it rather than relying only on questionnaire descriptions.

## 7. Document structure

Use the reference document's structure when the project has an approved reference and it is appropriate. Otherwise, adapt this baseline. Include relevant detailed subsections, and explicitly mark material gaps.

1. **Document Control** — title, project/process, version, date, author/preparer, status, reviewers, approvals.
2. **Executive Summary** — purpose, scope, current-state overview, major components, key findings, critical gaps.
3. **Business Context and Scope** — objectives, process description, boundaries, stakeholders, owners, terminology.
4. **Current-State Overview and Architecture** — systems, components, platforms, environments, major interactions.
5. **Inputs, Sources, and Dependencies** — source inventory, origin, owner, purpose, refresh/availability, dependencies.
6. **End-to-End AS-IS Process Flow** — ordered steps from trigger to outcome, including branches, decisions, exceptions, hand-offs.
7. **Detailed Functional and Technical Design** — relevant business rules, logic, transformations, interfaces, components, configurations, processing behavior.
8. **Outputs and Consumers** — generated records, files, reports, services, destinations, recipients, delivery mechanisms.
9. **Scheduling and Orchestration** — triggers, schedules, dependencies, sequencing, run windows, retries, failure paths, where applicable.
10. **Data, Information, and Records Management** — entities, formats, quality, lineage, retention, ownership, where applicable.
11. **Security, Access, and Compliance** — identity, authentication, authorization, secrets handling, classification, privacy, compliance evidence.
12. **Monitoring, Support, and Operations** — logging, alerts, reconciliation, manual activities, support, incident handling, recovery, runbooks.
13. **Known Issues, Risks, and Constraints** — evidence-backed current-state limitations and impacts.
14. **Future Considerations / Modernization Drivers** — stakeholder-stated needs and possible improvements, clearly separated from the AS-IS.
15. **Assumptions, Conflicts, and Open Questions** — unresolved items, evidence gaps, owner (if known), impact.
16. **Appendices** — detailed inventories, glossary, evidence register, supplementary diagrams, supporting information.

Adapt section names and ordering to the reference document or project requirements when justified. Do not create irrelevant sections merely to match this baseline. Do not omit a relevant section because information is missing; state the gap.

## 8. Diagrams and visual representation

Create diagrams when they improve understanding and are supported by evidence. Select only relevant views, for example:
- Business/system context
- End-to-end process or workflow
- Application or component architecture
- Data flow or lineage
- Integration/interface view
- Infrastructure/deployment view
- Roles, approvals, and hand-offs

Diagram standards:
- Use verified components and relationships only.
- Preserve exact known names for systems, components, interfaces, data stores, jobs, and environments.
- Label uncertain or inferred relationships clearly; use a legend where needed.
- Do not invent missing servers, networks, APIs, data stores, protocols, or process steps.
- Ensure diagrams are legible in the final Word document and consistent with the written explanation.
- If a diagram cannot be generated reliably, include a clear textual flow or Mermaid source where supported.

Use tables for inventories, interfaces, schedules, roles, controls, risks, assumptions, and open questions. Split large inventories into logical tables.

## 9. Security and credential documentation — configurable

Identify security and authentication mechanisms actually used or required by the project. These may include passwords, service accounts, API keys, tokens, certificates, SSH keys, database credentials, SSO, or other mechanisms.

Follow the active project's security instructions in `CLAUDE.md` and the project-specific configuration below.

- Include credential or authentication fields only when applicable or explicitly required.
- When a project requires a password column/field, include that field in the document.
- Do not put plaintext passwords, API keys, tokens, private keys, or other reusable secrets in the generated document by default. Use an approved vault/secret reference or a placeholder such as `[REDACTED — retrieve from approved secrets vault]`.
- Do not invent vault names, secret identifiers, credential owners, usernames, rotation schedules, or security policies.
- If source material contains exposed secrets, do not reproduce them. Flag the exposure for handling under the organization's security process.
- Document authentication method, purpose, consuming component, ownership, storage reference, and rotation/expiry expectations only where known and permitted.
- If the organization has an explicitly approved exception requiring different treatment, follow its documented policy and access controls; do not independently decide to disclose a secret.

A project may require a password field even though another project does not. This is controlled by the project-specific configuration, not by a universal mandatory password requirement.

## 10. Writing and formatting standards

- Write in clear, professional language suitable for business and technical readers.
- Explain how the current process works, not how it should work.
- Be detailed enough for another team to understand the process without relying on undocumented knowledge.
- Avoid unsupported claims, vague statements, marketing language, and unnecessary repetition.
- Use consistent heading levels, numbering, terminology, tables, captions, and diagram titles.
- Use exact date/time formats and state the time zone.
- Explain acronyms on first use and include a glossary where useful.
- Distinguish current-state facts from assumptions, risks, recommendations, and target-state ideas.
- Use "Not provided", "To be confirmed", or "Not verified" for missing information rather than leaving critical fields blank.

## 11. Generate and validate the deliverable

Use the output directory, filename, and format specified in `CLAUDE.md`.

For a Word deliverable:
1. Generate a properly formatted `.docx` with a title page or document-control section as appropriate.
2. Use consistent styles for headings, body text, tables, captions, headers, and footers.
3. Insert diagrams at readable sizes and check that they are not clipped or distorted.
4. Use page breaks and table layout thoughtfully. Avoid splitting important table rows where possible.
5. Do not overwrite an approved or existing deliverable unless explicitly instructed. Create a versioned copy when appropriate.
6. Reopen or otherwise verify the generated file and check that it is readable and saved at the configured path.

### Mandatory Quality Assurance and Independent Validation

Before delivering any AS-IS document, perform an independent quality review of the complete generated document.

Do not assume that information is correct simply because it was extracted or generated successfully.

**1. Evidence Verification**
- Verify every important business and technical statement against the original input evidence.
- Maintain traceability to the source filename and relevant page, section, sheet, table, or code location.
- Verify exact system names, server names, table names, stored procedures, job names, schedules, paths, and identifiers.
- Do not introduce unsupported facts or silently resolve conflicting information.

**2. Cross-Document Validation**
- Compare information across all relevant source documents.
- Identify contradictory values, outdated information, missing details, and duplicate or inconsistent definitions.
- Give preference to authoritative and current implementation evidence for technical behavior.
- Record unresolved conflicts instead of choosing a value without evidence.

**3. Completeness Validation**
- Verify that all relevant source systems, processes, business rules, inputs, outputs, integrations, schedules, dependencies, and operational requirements have been considered.
- Ensure that important source inventory entries have not been omitted.
- Check that diagrams accurately represent the documented process.
- Confirm that future-state recommendations are not presented as current-state facts.

**4. Independent Second-Pass Review**

After generating the document, perform a separate review as a Senior Solution Architect and Technical Reviewer.

Re-examine the document against the original source evidence rather than relying on the generated document's own explanations.

Look specifically for:
- Unsupported statements
- Incorrect technical interpretations
- Missing components or dependencies
- Contradictory schedules or process descriptions
- Incorrect names and identifiers
- Inconsistent tables and diagrams
- Security and confidentiality issues
- Missing evidence references

Correct all issues that can be resolved from available evidence and repeat the validation.

**5. Validation Report**

Generate a validation report containing:
- Total source files analyzed
- Important facts verified
- Evidence coverage and traceability
- Missing or conflicting information
- Technical and business validation results
- Security validation results
- Issues corrected during review
- Remaining items requiring stakeholder confirmation

**6. Delivery Status**

Classify the final deliverable as one of the following:

- `READY FOR STAKEHOLDER REVIEW` — Required checks completed, with no unresolved critical issues.
- `REVIEW REQUIRED` — Material information gaps, conflicts, or unverified technical details remain.
- `VALIDATION FAILED` — Critical accuracy, completeness, or security checks failed.

Never describe an automatically generated document as approved, fully verified, or production-ready without the required human review and sign-off.

Do not hide unresolved issues to achieve a passing validation result.

---

# PROJECT-SPECIFIC CONFIGURATION — CUSTOMIZE THIS SECTION FOR EACH PROJECT

> **Team instruction:** This is the replaceable part of the master skill. Keep the generic sections above intact. Replace every bracketed placeholder for a new project. Remove requirements that do not apply. Never carry facts from a previous project into another project.

## A. Project identity

- Project name: `[ENTER PROJECT NAME]`
- Business/domain area: `[E.G. INSURANCE, BANKING, RETAIL, HEALTHCARE, INTERNAL OPERATIONS]`
- Process/application/solution: `[ENTER NAME]`
- Business purpose: `[DESCRIBE PURPOSE]`
- Document audience: `[BUSINESS / ENGINEERING / ARCHITECTURE / OPERATIONS / OTHER]`
- Document type: `AS-IS Design Document`
- Approved reference document: `[PATH OR NONE]`

## B. Scope and terminology

- In scope: `[PROCESSES, SYSTEMS, APPLICATIONS, TEAMS, CAPABILITIES]`
- Out of scope: `[EXCLUSIONS OR NOT PROVIDED]`
- Important business rules: `[LIST OR POINT TO EVIDENCE]`
- Important terminology/acronyms: `[LIST OR DERIVE FROM INPUTS AND CONFIRM]`
- Required project-specific sections: `[LIST OR USE GENERIC BASELINE AND REFERENCE]`

## C. Technology and evidence focus

- Expected technology/platforms: `[LIST OR DISCOVER FROM EVIDENCE]`
- Expected source/evidence types: `[LIST IF KNOWN; NOT EXHAUSTIVE]`
- Critical systems/components/interfaces to validate: `[LIST OR DISCOVER]`
- Project-specific inventories: `[E.G. APPLICATION, SOURCE TABLE, API, SERVER, JOB INVENTORY]`
- Project-specific diagrams: `[LIST OR SELECT BASED ON EVIDENCE]`
- Known discrepancies/items to investigate: `[LIST OR IDENTIFY DURING ANALYSIS]`

## D. Security and special documentation requirements

- Credential documentation: `[REQUIRED / IF APPLICABLE / NOT REQUIRED]`
- Password / Secret field: `[REQUIRED / IF APPLICABLE / NOT REQUIRED]`
- Required authentication details: `[LIST OR DOCUMENT ONLY WHAT IS APPLICABLE AND EVIDENCED]`
- Secret handling / approved reference method: `[ORGANIZATIONAL POLICY OR VAULT REFERENCE APPROACH]`
- Data classification / privacy / compliance requirements: `[LIST OR TO BE CONFIRMED]`
- Other special requirements: `[LIST OR NONE]`

**Security rule:** Even if a password field is required, do not put a live plaintext password in the document by default. Prefer an approved secret reference or redacted placeholder. Follow documented organizational policy for any approved exception.

## E. Project-specific validation and acceptance criteria

- Required sections/template: `[SPECIFY]`
- Required inventories/tables: `[SPECIFY]`
- Required diagrams: `[SPECIFY]`
- Required evidence traceability: `[SPECIFY]`
- Business/technical review owners: `[SPECIFY OR TO BE CONFIRMED]`
- Acceptance criteria: `[SPECIFY OR USE GENERIC QUALITY CHECKLIST]`

Before generating the AS-IS document, review all project-specific configuration sections (A–E). Mark unknown values as To be confirmed and never invent missing information.
