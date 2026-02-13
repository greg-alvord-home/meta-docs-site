# YAML-LD: A Call to Action for MISMO

*(Draft workspace — add your text anywhere below. I can edit, tighten, and structure once you’ve written a first pass.)*

---

## On the shoulders of giants

All of MISMO’s work stands on the shoulders of giants—most notably the W3C standards community. XML Schema (XSD) and XLink were essential precursors to the V3.x reference model and enabled rigor, interoperability, and long‑term governance.

For decades, a “simplicity” movement has pressed against that rigor. In practice, the cost of that simplicity has been high: repeated rework, continual renegotiation of meaning, and an overall loss of clarity.

I have written previously about the value of namespaces to the success of the model’s implementations. Claims that “namespaces are just strings” miss their core value: vocabulary isolation, identity, and governance. Yet pressure to adopt “more modern” formats continues.

The W3C has recognized this tension and produced a solution that preserves namespaces while remaining compatible with developer‑friendly formats.

## Working thesis

MISMO should not abandon namespaces for the short-term convenience and popularity of JSON. Instead, MISMO can adopt a JSON-compatible, W3C-aligned approach that preserves endemic namespaces and semantic identity: **YAML-LD** (Linked Data in YAML), based on JSON-LD semantics.

---

## Why this matters

- **Standards live in namespaces.** Namespaces preserve identity, scope, and governance.
- JSON and YAML became popular by being simple — but they deliberately omit namespaces.
- The long-term cost is predictable: ambiguity, incompatible interpretations, and repeated re-litigation of “what things mean.”

---

## What MISMO can do

- As with other W3C‑aligned standards, MISMO should lead through education and publication—embracing the simplicity of JSON/YAML **without abandoning** the rigor of namespaces via YAML‑LD.
- When JSON exchanges are requested, respond with YAML‑LD configurations that remain JSON‑compatible while preserving semantic identity.
- Publish a minimal, versioned `@context` for MISMO artifacts.
- Provide reference examples, validation guidance, and tooling support.


## Why JSON is unfit for data model standard publications

- JSON lacks a published **semantic** standard and instead operates on informal best practices and local tribal knowledge.
- JSON *does* have standards for syntax: objects, arrays, strings, numbers, booleans, and null.
- JSON has **no standards** for semantics, identity, namespaces, extensibility rules, governance, versioning, or how keys are to be interpreted.
- JSON is a **well‑standardized data container**, not a data model.
- As a result, JSON‑based standards frequently rely on breaking changes and version churn to manage meaning drift.

## Why YAML is a better candidate for standards

1. **Human authorship and review**
   - Comments matter in standards.
   - YAML supports comments; JSON does not.
   - This alone is a major reason many standards bodies prefer YAML for specifications and profiles.
2. **Document-centric standards**
   - YAML supports multi-document files.
   - YAML tolerates ordering where humans expect it.
   - JSON is intentionally hostile to document structure beyond data trees.
3. **Extensibility without breakage**
   - YAML allows gradual enrichment (anchors, aliases, annotations).
   - JSON extensions tend to be ad hoc and brittle.
4. **Standards-as-text, not just wire format**
   - Standards are read, debated, revised, and governed.
   - YAML is designed for that lifecycle.
   - JSON is designed for transmission.

## What YAML is missing as a candidate for standards

On its own, YAML:

1. Does **not** define identity
2. Does **not** define namespaces
3. Does **not** define meaning

## YAML‑LD is what makes YAML suitable for semantic standards

YAML‑LD adds what both JSON and YAML deliberately omit:

1. Namespaces
2. Identity
3. Governance
4. W3C‑defined semantics

Together, these allow YAML to serve as a human‑friendly **carrier** for formally defined meaning.


---

## Draft text

(Write here)

---

## Notes / references to weave in later

- W3C Community Group Report: YAML-LD (Linked Data in YAML) 
  - [https://www.w3.org/community/reports/json-ld/CG-FINAL-yaml-ld-20231206/?utm\_source=chatgpt.com#informative-references ](https://www.w3.org/community/reports/json-ld/CG-FINAL-yaml-ld-20231206/?utm_source=chatgpt.com#informative-references )
- Relationship to JSON-LD and RDF
- Why this avoids the “stringly-typed meaning” tax
- How this fits MISMO governance and interoperability goals

---

## Call to action

MISMO does not need to choose between modern developer tooling and semantic rigor. YAML‑LD offers a W3C‑aligned bridge that preserves namespaces, identity, and governance while remaining compatible with today’s JSON‑centric ecosystems.

The cost of abandoning namespaces is already well known. The opportunity now is to lead—by showing how simplicity and meaning can coexist.

