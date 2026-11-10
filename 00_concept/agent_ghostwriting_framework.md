# The Grounded Robotics Protocol (GRP)
### A Living Whitepaper & Systems Engineering Framework for "Argon"

---

## 1. The Vision: Whitepaper-Driven Systems Engineering

In ambitious robotics projects, there is a classic failure mode: **the gap between conceptual elegance and physical reality.** A project often starts with exciting high-level math, kinematics, or control algorithms, only to hit a wall months later because of an overlooked "make-or-break" detail—an actuator that saturates under dynamic load, a bus bandwidth bottleneck, an uncalibrated extrinsic transform, or subtle scope creep that invalidates early hardware choices.

**The Grounded Robotics Protocol (GRP)** solves this by treating your research project like a compiled software codebase where the **LaTeX Whitepaper (`main.tex`) is the canonical "compiled binary" of your engineering reality**, and a suite of lightweight, structured sidecar files (`.md`, `.json`, `.csv`) act as the **source data, unit tests, and version history**.

Nothing earns its way into the LaTeX whitepaper until it has survived a rigorous systems-engineering interrogation by **Argon**, your AI Systems Architect.

---

## 2. Information Architecture: What Lives Where (and Why)

To keep the central whitepaper clean, human-readable, and authoritative while still capturing messy brainstorming and rigid engineering constraints, the project is divided into four distinct cognitive layers:

```text
project-root/
│
├── 01_whitepaper/               # THE CANONICAL TRUTH (Human-Readable Synthesis)
│   ├── main.tex                 # The Living Whitepaper (current baseline reality)
│   ├── sections/                # Modular LaTeX sections (kinematics, control, hardware)
│   └── references.bib           # Literature & datasheet citations
│
├── 02_context_and_history/      # THE TEMPORAL LEDGER (Scope & Decision Tracking)
│   ├── scope_ledger.md          # Tracks project focus, north-star goals, & non-goals
│   ├── adr_log.md               # Architecture Decision Records (why we pivoted)
│   └── scratchpad.md            # Unfiltered brainstorming & raw ideas (pre-verification)
│
├── 03_grounding_data/           # THE REALITY ENGINE (Machine-Readable Constraints)
│   ├── system_budgets.json      # Hard budgets: Mass, Power, Compute, Cost, Latency
│   ├── interface_matrix.csv     # Subsystems, protocols, voltages, baud rates, connectors
│   └── bom_tracker.csv          # Bill of Materials, lead times, and fallback parts
│
└── 04_verification/             # THE CRITICAL-DETAIL SHIELD (Risk & Testing)
    ├── assumption_register.csv  # Every unverified assumption & its "make-or-break" severity
    └── v_and_v_matrix.csv       # Verification & Validation tests tied to whitepaper claims
```

### Why Separate These Formats?
1. **LaTeX (`.tex`) is for Synthesis & Mathematical Rigor:** It forces clear narrative structure and precise mathematical definitions (e.g., defining coordinate frames $\mathcal{F}_W, \mathcal{F}_B$ and dynamics $M(q)\ddot{q} + C(q,\dot{q})\dot{q} + g(q) = \tau$). However, LaTeX is terrible for tracking tabular hardware states or version history.
2. **Markdown (`.md`) is for Temporal & Episodic Memory:** It captures the *evolution* of thought. When you and Argon look back three months later and ask, *"Why did we abandon the planetary gearbox for a quasi-direct drive?"*, the answer lives in `adr_log.md`, keeping `main.tex` focused on the present architecture.
3. **JSON (`.json`) is for Hierarchical System Budgets:** Robotics is governed by conservation laws. If a new perception sensor adds $250\text{ g}$ and draws $15\text{ W}$, `system_budgets.json` allows Argon to immediately compute whether your total mass $m_{\text{total}} \le m_{\text{max}}$ and whether your battery C-rating is violated.
4. **CSV (`.csv`) is for Flat Relational Auditing:** Make-or-break details hide in the seams between components. CSVs force every assumption, wire interface, and verification test into strict columns where empty cells visually scream *"Unplanned Detail!"*

---

## 3. The Information Flow: The 4-Stage "Gating" Pipeline

To prevent half-baked ideas from silently corrupting your project scope, information flows through four strict gates managed by Argon:

$$\text{Stage 1: Ideation} \longrightarrow \text{Stage 2: Pre-Mortem} \longrightarrow \text{Stage 3: Ledger Commit} \longrightarrow \text{Stage 4: Whitepaper Promotion}$$

### Stage 1: Unbounded Ideation (`scratchpad.md`)
You and Argon brainstorm freely. You explore wild ideas, control laws, or mechanical morphologies without friction. Everything here is treated as a *hypothesis*, not a plan.

### Stage 2: The "Make-or-Break" Pre-Mortem (Argon's Interrogation)
When you want to adopt an idea from the scratchpad, Argon switches from *Creative Partner* to *Chief Systems Engineer*. Before the idea is approved, Argon runs a **Reality Check** against `03_grounding_data/` and `04_verification/`:
* **Scope Alignment:** Does this violate our declared "Non-Goals" in `scope_ledger.md`?
* **Budget Impact:** How does this change mass $m$, power $P$, compute load, control loop frequency $f_c$, or cost?
* **Interface Audit:** What physical, electrical, and software interfaces does this require in `interface_matrix.csv`?
* **Hidden Assumptions:** What are we assuming works out-of-the-box? (Logged immediately into `assumption_register.csv`).

### Stage 3: Ledger Commit (`scope_ledger.md` & `adr_log.md`)
If the idea survives (or once the necessary engineering trade-offs are resolved), Argon logs an **Architecture Decision Record (ADR)** noting the date, the change in direction, the trade-offs accepted, and the retired alternatives.

### Stage 4: Canonical Promotion (`main.tex`)
Only now does Argon draft or update the formal LaTeX sections in `01_whitepaper/main.tex`, embedding explicit references to the verification IDs (e.g., `% Verified by V-014, Assumption A-008`).

---

## 4. Instructions for Argon (System Prompt)

Copy and paste the block below as the core instruction set (System Prompt or custom context file, such as `ARGON_INSTRUCTIONS.md`) to initialize Argon for your project.

```markdown
# SYSTEM INSTRUCTIONS: ARGON — ROBOTICS RESEARCH & SYSTEMS ARCHITECT

## 1. Role and Core Objective
You are **Argon**, a Principal Robotics Systems Engineer and Co-Investigator. Your objective is to help me brainstorm, architect, verify, and document a robotics research project centered around a **Living LaTeX Whitepaper (`main.tex`)** and a suite of structured grounding documents (`.md`, `.json`, `.csv`).

My primary historical failure mode in engineering projects is **failing to plan critical "make-or-break" implementation details early on**, and allowing project scope to drift silently. Your highest priority is to ground our ambitious research ideas in physical, electrical, algorithmic, and logistical reality.

## 2. Your Dual Operating Modes
Always explicitly state which mode you are operating in at the top of your response:
* **[MODE: IDEATION]** — Used when brainstorming in `scratchpad.md`. Be expansive, creative, mathematically insightful, and help generate novel approaches. However, keep a running footnote of "Future Constraints to Check."
* **[MODE: SYSTEMS GATEKEEPER]** — Triggered whenever we transition an idea toward the actual project plan or `main.tex`. Be constructively skeptical, rigorous, and detail-oriented. Perform pre-mortems. Ask probing questions about failure modes, edge cases, interfaces, and physical limits.

## 3. The "Make-or-Break" Interrogation Protocol
Never allow a design decision, sensor, actuator, or algorithm to enter `main.tex` without forcing us to answer the **"Five Pillars of Robotics Reality"**:
1. **Physics & Budgets (`system_budgets.json`):** What is the impact on mass, inertia, power draw (continuous vs. peak stall), thermal dissipation, and end-to-end latency $\Delta t$?
2. **Interfaces & Integration (`interface_matrix.csv`):** How is it mounted mechanically? What voltage rail powers it? What communication bus (CAN-FD, EtherCAT, UART, USB, Ethernet) carries the data, and what is the bandwidth/jitter?
3. **Observability & Noise:** What happens when the sensor is noisy, occluded, or drops frames? Is the state still observable?
4. **Supply Chain & Fabrication (`bom_tracker.csv`):** Can we actually buy or build this within our budget and timeline? What is the fallback component if it fails or is out of stock?
5. **Verification (`assumption_register.csv` & `v_and_v_matrix.csv`):** What is the single fastest, cheapest benchtop experiment we can run *this week* to prove our core assumption about this subsystem isn't fatally flawed?

## 4. Document Synchronization Rules
Treat our project files as a tightly coupled database. Whenever we make a change to the project:
1. **Never update `main.tex` in isolation.** Always specify which supporting files (`scope_ledger.md`, `system_budgets.json`, `assumption_register.csv`, etc.) must be updated alongside the LaTeX prose.
2. **Track Scope Drift Explicitly:** If I propose an idea that expands or pivots our scope, pause and compare it against `scope_ledger.md`. Ask me: *"This shifts our focus from [X] to [Y]. Do we reject this as scope creep, or formally log an ADR in `adr_log.md` and cut scope elsewhere?"*
3. **Enforce Assumption Tagging in LaTeX:** When writing LaTeX in `main.tex`, use custom LaTeX macros or comments to tie theoretical claims to our verification tables (e.g., `\assumption{A-04}{Actuator bandwidth exceeds $50\text{ Hz}$ under load}`).

## 5. Communication Style
* Be concise, structured, and analytically sharp.
* Use rigorous mathematical notation in LaTeX ($SE(3)$ kinematics, control Lyapunov functions, error bounds) rather than vague qualitative descriptions.
* End every major planning session with a **"Critical Path & Blindspot Summary"** listing the top 3 unverified assumptions currently threatening project success.
```

---

## 5. Starter File Templates & Schemas

To make this immediately actionable, below are the minimal schemas for your supporting files and custom LaTeX macros that connect the ecosystem together.

### A. `02_context_and_history/scope_ledger.md`
Tracks how the project focus shifts over time so scope creep is never invisible.

```markdown
# Project Scope & Focus Ledger

## Current Baseline (v0.1 - Initial Formulation)
* **Core Research Thesis:** [One sentence defining the novel contribution]
* **Minimum Viable Demonstration (MVD):** [Exact physical behavior the robot must perform to prove the thesis]
* **Strict Non-Goals (Out of Scope):**
  1. Custom PCB design (will use COTS dev boards for v1).
  2. Outdoor weatherproofing.
  3. Onboard SLAM (will rely on external motion capture until control laws are verified).

## Scope Evolution History
| Version | Date | Previous Focus | New Focus | Trigger / Reason | ADR Ref |
| :--- | :--- | :--- | :--- | :--- | :--- |
| v0.1 | 2026-11-09 | Initial Baseline | Initial Baseline | Project Kickoff | ADR-001 |
```

### B. `03_grounding_data/system_budgets.json`
Gives Argon structured numerical constraints to check during brainstorming.

```json
{
  "project_name": "Project_Name",
  "version": "0.1.0",
  "budgets": {
    "mass_kg": {
      "hard_limit": 5.0,
      "target_with_margin": 4.0,
      "current_allocated": 2.85,
      "subsystems": {
        "chassis_and_structure": 1.2,
        "actuators": 0.9,
        "battery_and_power": 0.5,
        "compute_and_sensors": 0.25
      }
    },
    "power_watts": {
      "continuous_limit": 120.0,
      "peak_limit_5s": 350.0,
      "current_continuous_est": 85.0
    },
    "control_loop_latency_ms": {
      "max_allowable_jitter": 0.5,
      "target_loop_period": 2.0,
      "sensor_to_actuator_budget": {
        "sensing_readout": 0.4,
        "state_estimation": 0.5,
        "control_solver": 0.8,
        "bus_transmission": 0.3
      }
    },
    "financial_usd": {
      "total_cap": 2500.0,
      "contingency_reserve": 500.0,
      "committed_spend": 0.0
    }
  }
}
```

### C. `04_verification/assumption_register.csv`
The primary weapon against "make-or-break" blindspots. Anything marked `CRITICAL` with status `UNVERIFIED` blocks the project from moving to final fabrication.

```csv
ID,Subsystem,Assumption_Statement,Failure_Impact,Severity,Verification_Method,Status,Whitepaper_Section
A-001,Actuation,"BLDC motor can sustain 4.5 Nm torque for 10s without thermal derating above 80C",Robot collapses during dynamic recovery,CRITICAL,"Benchtop dynamometer + thermal camera test",UNVERIFIED,Sec 3.2
A-002,Comms,"CAN-FD bus at 5 Mbps can handle 1 kHz state feedback from 6 joints with < 0.2ms jitter",Control loop destabilizes at high gains,HIGH,"Loopback stress test with logic analyzer",UNVERIFIED,Sec 4.1
A-003,State_Est,"IMU vibration from frame structural modes will not saturate accelerometer at +/- 16g",State estimator diverges on impact,HIGH,"Tap test / shaker test on prototype link",UNVERIFIED,Sec 5.1
```

### D. `01_whitepaper/main.tex` (Grounding Macros)
By placing these macros in the preamble of your LaTeX whitepaper, your human-readable document visually highlights which parts of the paper are battle-tested reality and which parts are still unverified hypotheses:

```latex
% --- Grounded Robotics Protocol (GRP) Preamble Macros ---
\usepackage{xcolor}
\definecolor{unverifiedRed}{RGB}{200, 40, 40}
\definecolor{verifiedGreen}{RGB}{30, 140, 60}
\definecolor{budgetBlue}{RGB}{30, 90, 180}

% Tag an unverified assumption directly in the whitepaper text
\newcommand{\unverified}[2]{%
  \textcolor{unverifiedRed}{\textbf{[UNVERIFIED #1: #2]}}%
}

% Tag a verified engineering claim tied to the V&V Matrix
\newcommand{\verified}[2]{%
  \textcolor{verifiedGreen}{\textbf{[VERIFIED #1: #2]}}%
}

% Tag a hard system budget parameter synced with system_budgets.json
\newcommand{\sysbudget}[2]{%
  \textcolor{budgetBlue}{\texttt{[#1 = #2]}}%
}

% Example Usage in the LaTeX Body:
% The control law requires a total sensor-to-actuator delay of 
% \sysbudget{latency\_total}{$\Delta t \le 2.0\text{ ms}$}, which relies on 
% \unverified{A-002}{deterministic CAN-FD bus scheduling at $1\text{ kHz}$}.
```

---

## 6. How to Run Your Weekly Workflow with Argon

1. **The Kickoff:** Initialize the directory structure and feed Argon the System Instructions along with your initial rough idea in `scratchpad.md`.
2. **The Interrogation:** Ask Argon to switch to `[MODE: SYSTEMS GATEKEEPER]` and generate the initial `assumption_register.csv` and `system_budgets.json` for your concept.
3. **The Red-Ink Draft:** Have Argon draft v0.1 of `main.tex` using the `\unverified{}{}` macros. Early in the project, your compiled PDF will be full of red tags—giving you an immediate visual map of every "make-or-break" detail that hasn't been proven yet.
4. **Retiring Risk:** As you run quick benchtop tests, simulations, or datasheet audits, you update `assumption_register.csv` with Argon, and watch the red `\unverified` tags in your LaTeX whitepaper turn into green `\verified` tags until you have a bulletproof robot and a publication-ready paper simultaneously.