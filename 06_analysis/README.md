# Analysis and Simulation

Use this directory for reproducible analysis work, such as calculations,
simulations, experiments, data processing, and reports. Keep inputs, methods,
results, and conclusions identifiable and traceable. A suggested layout is:

- `inputs/` - source data, models, configurations, and assumptions
- `methods/` - scripts, procedures, and analysis setup
- `results/` - retained results and selected exports
- `reports/` - reviewed summaries, visualizations, and conclusions
- `checks/` - benchmarks, validation, and independent review evidence

For each retained analysis, record the relevant source revision, tools and
versions, units, assumptions, method, data provenance, acceptance criteria,
and limitations. Include the configuration and procedures needed to reproduce
important results. Give result files stable names and link important claims
to verification records.

Keep text-based sources and small reviewable outputs in regular Git when
practical. The root `.gitattributes` includes optional Git LFS coverage for
common large binary design and data formats. Use it when appropriate and
check the remote host's storage and bandwidth limits. Distinguish retained
evidence from disposable scratch, and use narrow project-specific ignore
rules for scratch output.
