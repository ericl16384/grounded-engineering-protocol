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
