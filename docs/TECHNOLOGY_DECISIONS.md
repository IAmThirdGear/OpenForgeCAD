# Technology Decision Records

This file tracks decisions and hypotheses. A candidate is not considered selected until it has been tested and a decision is recorded.

## TDR-001: Reuse a proven geometry kernel

**Status:** Proposed direction.

**Question:** Should the project implement its own exact solid-modeling kernel?

**Current direction:** No, not for the initial project. Evaluate Open CASCADE Technology and other established options before considering custom kernel work.

**Reasoning:** Exact solid modeling, topology, Boolean operations, and file interoperability are substantial engineering problems. Reuse can let the project focus on application workflows and integration.

**Validation needed:** licensing, supported platforms, STEP behavior, API quality, performance, packaging, and maintenance.

## TDR-002: GPU rendering is a first-class requirement

**Status:** Proposed direction.

**Current direction:** Prototype Vulkan rendering on the intended Linux/AMD setup.

**Reasoning:** The viewport is central to CAD usability, and a modern explicit graphics API provides control over rendering and resource management.

**Validation needed:** development complexity, driver behavior, UI integration, picking/selection, text rendering, and performance benchmarks.

## TDR-003: GPU compute is workload-specific

**Status:** Proposed direction.

**Current direction:** Keep the compute backend modular. Evaluate Vulkan compute and AMD-supported compute frameworks against specific tasks.

**Reasoning:** Rendering acceleration does not imply exact geometric operations will benefit from GPU compute. Each workload needs measurement.

**Validation needed:** supported hardware/software combinations, portability, numerical correctness, VRAM use, and speedups against CPU baselines.

## TDR-004: AI is optional and plugin-based

**Status:** Proposed direction.

**Current direction:** Put AI integrations behind a plugin/provider interface. Keep the core CAD application functional without AI.

**Reasoning:** This avoids lock-in to a model, inference runtime, or provider and enables community extensions.

**Validation needed:** stable command API, model context limits, structured output reliability, permissions, document transactions, and GPU memory contention.

## TDR-005: Prefer open, interoperable formats

**Status:** Proposed direction.

**Current direction:** Prioritize suitable exchange formats such as STEP for solid geometry and STL/3MF for mesh/printing workflows.

**Reasoning:** Users should be able to move designs between tools.

**Validation needed:** preservation of units, metadata, assemblies, color, and other relevant properties for each format.
