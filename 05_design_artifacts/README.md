# Design Artifacts

Use this directory for design models and deliverables that benefit from
versioned, shared storage. This can include geometry, drawings, diagrams,
specifications, prototypes, or other project artifacts. Adapt the organization
to the project; for example, group by artifact type, component, or lifecycle.

Keep editable sources distinct from approved deliverables and derived
exports. Identify authoritative versions and revisions where needed. For
artifacts that require it, record units, coordinate systems, assumptions,
external references, authoring tool/version, and dependencies. Prefer
repository-relative references. Confirm that externally sourced material may
be stored and shared here.

The root `.gitattributes` includes optional Git LFS coverage for common large
binary design and data formats. Install Git LFS when working with those files
and check the remote host's storage and bandwidth limits. Add narrow,
project-specific ignore rules for disposable caches; do not ignore approved
sources or deliverables.
