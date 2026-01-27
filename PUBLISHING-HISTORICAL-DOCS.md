# Publishing Historical Documents (Meta-Docs → Posts → LinkedIn/Substack)

This document is the **operational checklist** for publishing historical documents from the Meta-Docs library into the 
public “Posts” stream and (optionally) generating LinkedIn/Substack cuts.

**Design intent**
- The Meta-Docs library remains **topic-organized** and stable.
- The Posts stream is **time-organized** and represents what I’ve chosen to “publish.”
- Publishing is a **projection** (copy and normalize), not a repo-wide reorganization.

---

## 0) Ground rules (to avoid tail-chasing)

1. **Do not move** files out of `docs/meta-docs/content/...`.
2. Publish **one document at a time**.
3. Do not bulk-rename or bulk-date historical items.
4. If a date is uncertain, choose a reasonable “publish date” and proceed.
5. If I feel myself looping or over-optimizing, stop and ship the simplest version.

---

## 1) Directory conventions

### Canonical library (unchanged)
- `docs/meta-docs/content/...` (topic-based)

### Publication stream (new)
- `docs/posts/YYYY/`
  - Example: `docs/posts/2025/2025-05-14-one-example-where-ai-breaks.md`

### Distribution artifacts (generated)
- `dist/`
  - `dist/linkedin.txt`
  - `dist/substack.md`

### Tools
- `tools/publish.py`

---

## 2) Promote one historical document to a published post

### Step A — Pick a source document
Choose one file under:
- `docs/meta-docs/content/...`

Example:
- `docs/meta-docs/content/AI-evaluations/ChatGPT/one-example-where-the-ai-approach-breaks.md`

### Step B — Copy (do not move) into the posts stream
Copy the file into:
- `docs/posts/2025/` (or the appropriate year)

### Step C — Rename using a date-based filename
Use:
- `YYYY-MM-DD-title-slug.md`

Examples:
- `2025-05-14-one-example-where-the-ai-approach-breaks.md`
- `2025-06-04-chatgpt-admits-to-silent-assumption-shifts.md`

**Note:** The file system modified timestamp is not trusted. The filename date is the “publish date” for the stream.

### Step D — Add YAML front matter (minimal)
At the very top of the copied post-file, add:

```yaml
---
title: "Human-readable title"
date: 2025-05-14
tags: [ai, evaluation]
summary: "One sentence that previews the point."
---
