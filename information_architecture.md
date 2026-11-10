# Project Information Architecture

This document defines the purpose and organization of the project files. Paths
are relative to the repository root.

## `00_concept/` — Concept and framing

Early-stage project ideas and guidance.

| Path | Purpose |
|---|---|
| `00_concept/initial_concept.md` | Initial project concept |
| `00_concept/agent_ghostwriting_framework.md` | Framework for AI-assisted ghostwriting |

## `01_whitepaper/` — Canonical engineering synthesis

The whitepaper documents the current engineering baseline.

| Path | Purpose |
|---|---|
| `01_whitepaper/main.tex` | Main LaTeX whitepaper source |
| `01_whitepaper/sections/` | Modular LaTeX sections, such as kinematics, control, and hardware |
| `01_whitepaper/references.bib` | Literature and datasheet citations |

## `02_context_and_history/` — Scope and decision history

Records project direction, decisions, and unverified ideas over time.

| Path | Purpose |
|---|---|
| `02_context_and_history/scope_ledger.md` | Project focus, north-star goals, and non-goals |
| `02_context_and_history/adr_log.md` | Architecture Decision Records explaining decisions and pivots |
| `02_context_and_history/scratchpad.md` | Brainstorming and raw ideas before verification |
| `02_context_and_history/scope_ledger_example.md` | Example scope ledger |

## `03_grounding_data/` — Machine-readable engineering constraints

Stores quantitative budgets and subsystem interface and procurement data.

| Path | Purpose |
|---|---|
| `03_grounding_data/system_budgets.json` | Hard mass, power, compute, cost, and latency budgets |
| `03_grounding_data/interface_matrix.csv` | Subsystems, protocols, voltages, baud rates, and connectors |
| `03_grounding_data/bom_tracker.csv` | Bill of materials, lead times, and fallback parts |
| `03_grounding_data/system_budgets_example.json` | Example system budgets |

## `04_verification/` — Assumptions and testing

Tracks risks and the evidence needed to validate engineering claims.

| Path | Purpose |
|---|---|
| `04_verification/assumption_register.csv` | Unverified assumptions and their severity |
| `04_verification/v_and_v_matrix.csv` | Verification and validation tests linked to whitepaper claims |
| `04_verification/assumption_register_example.csv` | Example assumption register |
