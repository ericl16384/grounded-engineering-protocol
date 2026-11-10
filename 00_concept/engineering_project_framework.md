# Grounded Engineering Protocol

## A reusable, evidence-linked workflow for mechanical and software projects

### Vision

Engineering projects often lose time and credibility not because the central
idea is weak, but because critical constraints, interfaces, assumptions, or
tests are discovered too late. Meanwhile, decisions and their rationale get
scattered across conversations, notes, code, and spreadsheets.

The Grounded Engineering Protocol (GEP) is a lightweight information workflow
for an engineer working with an AI agent. It aims to keep the current project
understandable while preserving the reasoning and evidence behind it. It is
designed for mechanical engineering, software development, and integrated
projects; the agent adapts its questions to the actual work rather than
assuming every project is a robot or a research paper.

The project has one central human-readable synthesis: the living whitepaper
(`01_whitepaper/main.tex` in this starter repository). It communicates the
current baseline, but it does not replace detailed records or test evidence.
Think of it as an engineering brief with traceable links, not as a magical
compiled truth. Other projects may choose Markdown or another format for this
central document.

## What goes where

Paths are relative to the project root.

| Record | Stores | Does not imply |
|---|---|---|
| `00_concept/` | Project framing and this reusable workflow | Approval of a particular design |
| `01_whitepaper/main.tex` | The readable current baseline and its open questions | That a claim is proven |
| `02_context_and_history/scratchpad.md` | Ideas, alternatives, and questions for exploration | A commitment or requirement |
| `02_context_and_history/scope_ledger.md` | Goals, deliverables, boundaries, and success criteria | That scope can never change |
| `02_context_and_history/adr_log.md` | Significant decisions, rationale, alternatives, and consequences | That an old decision remains correct forever |
| `03_grounding_data/system_budgets.json` | Quantified limits and allocations with units | That estimates are measured facts |
| `03_grounding_data/interface_matrix.csv` | Contracts between components, people, systems, and environments | That an interface has been tested |
| `03_grounding_data/bom_tracker.csv` | Physical parts and/or software components, sources, owners, and alternatives | That a component is available or production-ready |
| `04_verification/assumption_register.csv` | Unverified beliefs that could affect success | That a planned check has passed |
| `04_verification/v_and_v_matrix.csv` | How requirements and claims will be checked and what evidence resulted | That a test proves more than its conditions allow |
| `01_whitepaper/references.bib` | Cited publications, standards, specifications, and other sources | That a citation supports claims beyond what it states |

Use the records that fit the project. A small project may not need every table
or budget category. Add or split files only when doing so makes information
easier to maintain, review, or validate.

## The information flow

### 1. Explore

Capture rough ideas in the scratchpad. Encourage useful alternatives and
questions, but label speculative statements and note constraints still to
check. Do not silently promote brainstormed content into the baseline.

### 2. Define

Agree on the problem or opportunity, intended users or stakeholders, scope,
deliverables, success criteria, non-goals, and meaningful constraints in the
scope ledger. If these are unclear, say what remains to be decided.

### 3. Expose the hard parts

For each leading concept, ask what could make it fail, become unaffordable, or
miss its purpose. Choose checks that fit the discipline:

- **Mechanical:** loads, motion, materials, dimensions, tolerances, wear,
  safety, environment, assembly, fabrication, inspection, and maintenance.
- **Software:** requirements, architecture, data, dependencies, security,
  performance, failure handling, deployment, compatibility, maintainability,
  and testing.
- **Integrated systems:** mechanical/electrical/software boundaries, timing,
  data formats, installation, human operation, lifecycle, and fault behavior.
- **Any project:** cost, schedule, sourcing, compliance, usability, and
  stakeholder acceptance when relevant.

These are prompts, not a mandatory checklist. Apply the concerns that matter;
explicitly mark others out of scope when that is a deliberate choice.

### 4. Decide

Record consequential decisions in the ADR log: context, decision, alternatives,
trade-offs, consequences, status, and date. The user owns major scope and design
choices. The agent should identify scope drift and its cost, not quietly decide
to accept or reject it.

### 5. Verify

Give important assumptions stable IDs. For each high-impact assumption or
requirement, define a proportionate check, such as calculation, code test,
prototype, inspection, simulation, source review, or user evaluation. Record
the method, acceptance criteria, evidence location, result, conditions, and
limitations. Keep failures and inconclusive results visible.

### 6. Synthesize and maintain

Update the whitepaper when the baseline changes. Link claims to requirement,
decision, assumption, test, or source IDs as applicable. Update affected
supporting files at the same time. Mark the status of claims clearly (for
example proposed, analyzed, tested, or accepted), and avoid calling something
verified without sufficient evidence.

## Grounding rules

1. **Distinguish fact from estimate.** Identify whether a value is measured,
   calculated, sourced, inferred, proposed, or unknown. Include units,
   assumptions, and uncertainty where useful.
2. **Trace important claims.** Use stable IDs and citations to connect the
   whitepaper to the detailed records and evidence.
3. **Check interfaces, not just components.** Many failures occur where
   mechanical, electrical, software, organizational, or external systems meet.
4. **Test the riskiest uncertainty early.** Prefer the cheapest informative
   check that can change the decision, rather than polishing an untested design.
5. **Keep scope changes explicit.** Record the reason, impact, and any work
   removed or deferred when the project's goals change.
6. **Keep the system proportionate.** Do not create process overhead or empty
   fields that do not help this project.
7. **Preserve provenance and limitations.** A passing test supports only the
   tested article, configuration, environment, and acceptance criteria.

## Reusable agent instructions

The repository-level `AGENT_INSTRUCTIONS.md` is the operational prompt for the
agent. Copy or adapt it when starting another project. It should remain
domain-neutral; place project-specific requirements, standards, conventions,
and decisions in that project's own files.

At project kickoff, the agent should help fill the scope ledger and identify
the useful constraints, interfaces, assumptions, and verification records.
For routine work, it should read only the records relevant to the change,
update linked records when needed, and report uncertainties rather than
inventing details.

## Starter repository layout

```text
00_concept/
  initial_concept.md
  engineering_project_framework.md
01_whitepaper/
  main.tex
  references.bib
02_context_and_history/
  scope_ledger.md
  scope_ledger_example.md
  adr_log.md
  scratchpad.md
03_grounding_data/
  system_budgets.json
  system_budgets_example.json
  interface_matrix.csv
  bom_tracker.csv
04_verification/
  assumption_register.csv
  assumption_register_example.csv
  v_and_v_matrix.csv
AGENT_INSTRUCTIONS.md
information_architecture.md
```

## First use on a new project

1. Describe the problem, who it affects, and what success would look like.
2. Fill in the scope ledger collaboratively; keep unresolved choices visible.
3. Select only the budget categories and interface records that matter.
4. Identify the few assumptions with the largest impact and the fastest useful
   checks for them.
5. Compare solution options and record significant decisions.
6. Draft the central technical synthesis with links to its evidence.
7. Revisit scope, assumptions, and tests as implementation or new evidence
   changes the plan.

The intended outcome is not documentation for its own sake. It is a project
whose important unknowns are visible, whose decisions are explainable, and
whose claims can be checked.
