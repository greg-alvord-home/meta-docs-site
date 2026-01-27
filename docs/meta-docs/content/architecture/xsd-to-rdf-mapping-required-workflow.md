# XSD → RDF Mapping: Required Workflow and Tooling (OTK / OWB)

## Context
This is **not scope creep**. It is a surfaced requirement discovered through real use:

> Given an XSD, it is *not safe* to assume it is directly mappable to RDF/OWL without loss or distortion.

XSD design choices (ordering, Russian Doll vs global elements, identity constraints, mixed content, substitution groups, etc.) can actively **block or bias** a faithful RDF mapping. Therefore, a disciplined workflow is required.

This document defines that workflow and the supporting responsibilities of **OTK** (tooling) and **OWB** (workflow/orchestration).

---

## Core Principle
**RDF mapping must be validated against real instance data, not just schema intent.**

An XSD is an *operational constraint system*. RDF is a *semantic model*. Bridging them requires a normalization step grounded in observed XML usage.

---

## Required Workflow (Normative)

### Step 1 — Require Representative XML Instances
**Input:**
- Supplied XSD
- A *collection* of XML documents claimed to be valid against that XSD

**Rationale:**
- XSDs routinely contain constructs that are unused, misused, or misunderstood
- RDF mapping must reflect *actual data patterns*, not theoretical allowances

**OTK responsibility:**
- Accept multiple XML instances as a set
- Treat the set as part of the formal input, not optional metadata

---

### Step 2 — Validate XML Set Against Original XSD
**Goal:** Establish a baseline of truth.

**Actions:**
- Validate each XML instance against the supplied XSD
- Record:
  - validation success/failure
  - ordering dependencies
  - constraint violations
  - optional branches actually exercised

**Outcomes:**
- Confirmation that the instance set is coherent
- Evidence of which schema features are *operationally relevant*

**OTK responsibility:**
- Batch validation
- Deterministic reporting (machine-readable)

**OWB responsibility:**
- Surface results to the user
- Gate subsequent steps on successful baseline validation (or explicit override)

---

### Step 3 — Recast XSD into an RDF-Mappable Form
**This is the critical normalization step.**

The recast XSD is *not* a replacement for the original; it is a **mapping artifact**.

#### Typical Transformations (Non-Exhaustive)
- Eliminate ordering sensitivity (`xs:sequence` → `xs:choice` where safe)
- Replace Russian Doll constructs with named global elements/types
- Remove identity constraints (`xs:key`, `xs:keyref`, `xs:unique`)
- Replace `xs:ID/IDREF` with unconstrained lexical types
- Normalize substitution groups and abstract heads
- Isolate operational constraints into optional include/import schemas

**Key rule:**
> The recast schema must preserve *structural meaning* while removing *operational enforcement* that has no RDF analogue.

**OTK responsibility:**
- Provide transformation utilities (rule-driven, explainable)
- Track provenance: original construct → transformed construct

**OWB responsibility:**
- Present the recast schema as a **derived view**, not an overwrite
- Make transformations visible and reviewable

---

### Step 4 — Revalidate XML Set Against Recast XSD
**Purpose:** Ensure semantic equivalence for the observed data.

**Actions:**
- Validate the same XML instances against the recast schema
- Identify:
  - instances that fail
  - schema features that were implicitly relied upon

**Interpretation:**
- Failures here are *informative*, not errors
- They reveal hidden dependencies that must be addressed explicitly

**OTK responsibility:**
- Comparative validation reporting (original vs recast)

**OWB responsibility:**
- Guide the user through resolution options
- Support iterative refinement

---

## Resulting Artifacts

After successful completion, OWB should have:

1. Original XSD (as supplied)
2. Validated XML instance set
3. Recast, RDF-mappable XSD
4. Validation report (original vs recast)
5. RDF/OWL model derived from the recast schema

This establishes a **defensible semantic pipeline**.

---

## Why This Belongs in Scope

- This workflow is **required to produce correct RDF**, not an enhancement
- It prevents silent semantic corruption
- It formalizes practices you already arrived at empirically (e.g., MISMO)
- It creates a reusable, standards-agnostic capability

In short:
> **If OWB claims to map XSD → RDF, it must control the schema-to-data relationship.**

That control requires exactly the steps outlined above.

---

## Boundary Conditions (Explicitly Out of Scope)
- Business-rule enforcement
- Runtime data validation beyond supplied instance sets
- Automatic inference of domain semantics without user review

---

## Summary
This is not scope creep. It is the **minimum responsible scope** required to make XSD-to-RDF mapping technically honest, repeatable, and explainable.

OTK provides the instruments.
OWB provides the workflow.
Together, they prevent category errors between operational schemas and semantic models.

