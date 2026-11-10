# Project Information Architecture

This repository is a reusable starting point for mechanical engineering,
software development, and integrated engineering projects. Paths are relative
to the repository root. Keep the structure lightweight: add discipline-specific
records only when the project needs them.

## `00_concept/` — Project framing

Capture the idea, user or stakeholder need, and the reusable method before
committing to a specific solution.

| Path | Purpose |
|---|---|
| `00_concept/initial_concept.md` | Purpose and principles of the reusable project framework |
| `00_concept/engineering_project_framework.md` | How the AI-assisted workflow organizes and promotes information |

## `01_whitepaper/` — Current technical synthesis

The living whitepaper is the readable overview of the current baseline: what
the project is, what is being built, why choices were made, what supports the
claims, and what remains unresolved. It may be a design dossier, engineering
report, or research paper depending on the project.

| Path | Purpose |
|---|---|
| `01_whitepaper/main.tex` | Main LaTeX technical synthesis and claim-status macros |
| `01_whitepaper/sections/` | Optional modular sections, created when useful |
| `01_whitepaper/references.bib` | Literature, standards, specifications, and other citations |

## `02_context_and_history/` — Intent and decisions

Keep evolving intent and rationale visible without confusing brainstorming
with the current baseline.

| Path | Purpose |
|---|---|
| `02_context_and_history/scope_ledger.md` | Goals, stakeholders, deliverables, success criteria, and non-goals |
| `02_context_and_history/adr_log.md` | Significant decisions, alternatives, consequences, and status |
| `02_context_and_history/scratchpad.md` | Unfiltered ideas and questions not yet adopted |
| `02_context_and_history/scope_ledger_example.md` | Example scope ledger |

## `03_grounding_data/` — Constraints and interfaces

Store structured values that need consistent review or comparison. Use only
the categories relevant to the project and document units and definitions.

| Path | Purpose |
|---|---|
| `03_grounding_data/system_budgets.json` | Project limits and allocations, such as dimensions, load, power, latency, memory, cost, or schedule |
| `03_grounding_data/interface_matrix.csv` | Mechanical, electrical, software, data, operational, and external interfaces |
| `03_grounding_data/bom_tracker.csv` | Physical parts, software components, services, sourcing, ownership, and alternatives as applicable |
| `03_grounding_data/system_budgets_example.json` | Illustrative, domain-neutral budget example |

## `04_verification/` — Risk and evidence

Track uncertainty and how each important requirement or claim will be checked.

| Path | Purpose |
|---|---|
| `04_verification/assumption_register.csv` | Unverified assumptions, consequences, and planned checks |
| `04_verification/v_and_v_matrix.csv` | Verification and validation activities with acceptance criteria and evidence |
| `04_verification/assumption_register_example.csv` | Illustrative mechanical/software assumption examples |

## Information flow

1. Capture possibilities in the scratchpad without implying approval.
2. Clarify the need, scope, deliverables, constraints, and success criteria in
   the scope ledger.
3. Evaluate candidate approaches; record important assumptions and interfaces.
4. Record consequential choices and trade-offs in the ADR log.
5. Test, analyze, inspect, or research claims; retain results and limitations in
   the verification records.
6. Synthesize the current baseline and link claims to their supporting records
   in the whitepaper.
7. Revisit linked records whenever evidence or scope changes.

The whitepaper is the central narrative, not the sole source of truth. Detailed
tables and evidence remain in their appropriate records; the whitepaper points
to them rather than copying mutable details unnecessarily. An item is not
verified merely because it appears in the whitepaper or a test was attempted.
