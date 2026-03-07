# Improvement Plan: 06-643 Scientific Software Engineering with AI Coding Agents

Compiled from three independent reviews:
1. **CS Educator** — clarity, pedagogy, exercise quality, timing
2. **Instructional Designer** — objectives alignment, assessment, accessibility
3. **Domain Expert** — technical accuracy, industry relevance, best practices

---

## HIGH PRIORITY — Fix Before Course Launch

### H1. Virtual environments never taught
- **Source:** Domain Expert, Instructional Designer
- **Problem:** Students learn `pip install -e .` but never learn `python -m venv`, activation, or why isolation matters. This is a critical gap.
- **Fix:** Add a section to L04 (Python Packaging) teaching virtual environment creation and management. Mention `uv venv` as a modern alternative.
- **Files:** `sse/04-python-packaging/04-python-packaging.ipynb`

### H2. `git filter-branch` is deprecated
- **Source:** CS Educator, Domain Expert
- **Problem:** L02 recommends `git filter-branch` for removing sensitive data. It's deprecated in favor of `git filter-repo`.
- **Fix:** Replace with `git filter-repo` (or BFG Repo-Cleaner) and note installation via pip.
- **Files:** `sse/02-git-version-control/02-git-version-control.ipynb`

### H3. Pre-commit hook versions are 2+ years old
- **Source:** Domain Expert
- **Problem:** `.pre-commit-config.yaml` examples pin Black 23.12.0, Ruff v0.1.8, pre-commit-hooks v4.5.0.
- **Fix:** Update to current versions, or add a note telling students to check for latest versions and use `pre-commit autoupdate`.
- **Files:** `sse/06-code-quality/06-code-quality.ipynb`

### H4. Module 06 "Next Steps" references wrong module
- **Source:** CS Educator
- **Problem:** Cell says "next module covers Python classes and OOP" but Module 07 is Debugging.
- **Fix:** Change to "In the next module, we'll learn debugging and profiling with AI assistance."
- **Files:** `sse/06-code-quality/06-code-quality.ipynb`

### H5. No rubrics for any graded component
- **Source:** Instructional Designer
- **Problem:** Students know deliverables but not evaluation criteria. The project is 50% of the grade with no rubric.
- **Fix:** Add rubrics for: (a) each assignment (technical/reflection split), (b) participation journal (3-level scale with examples), (c) project (criteria and weights for each deliverable). Add a model journal entry showing expected depth.
- **Files:** `sse/syllabus.ipynb`, `sse/assignments/participation.ipynb`, `sse/assignments/index.md`

### H6. Course title inconsistency
- **Source:** Instructional Designer
- **Problem:** Syllabus says "Creating Scientific Software" but assignments say "Scientific Software Engineering."
- **Fix:** Pick one and use it everywhere. (README.org uses "Scientific Software Engineering".)
- **Files:** `sse/syllabus.ipynb` (and any other mismatches)

### H7. Prerequisites not stated
- **Source:** Instructional Designer
- **Problem:** Course assumes Python proficiency but never states it.
- **Fix:** Add to syllabus: "Prerequisites: Comfortable writing Python functions, using pip, and working in a text editor."
- **Files:** `sse/syllabus.ipynb`

---

## MEDIUM PRIORITY — Improve Before or During Course

### M1. L00 duplicate Summary and timing concerns
- **Source:** CS Educator, Domain Expert
- **Problem:** Duplicate summary cells (already partially fixed — verify). L00 is too dense for one 75-min session.
- **Fix:** Verify duplicates are removed. Consider splitting L00 content across the two Week 1 slots (L00a: tools + plan-execute + pacing; L00b: context engineering + prompting + evaluation).
- **Files:** `sse/00-ai-assisted-development/00-ai-assisted-development.ipynb`

### M2. L06 learning objectives mention Flake8/Pylint but content only teaches Ruff
- **Source:** CS Educator, Domain Expert
- **Problem:** Objectives say "Apply linters (Flake8, Pylint)" but body only covers Ruff.
- **Fix:** Change objectives to "Apply linters (Ruff) for quality checks" and note Flake8/Pylint as legacy tools Ruff replaces.
- **Files:** `sse/06-code-quality/06-code-quality.ipynb`

### M3. Ruff formatter not mentioned; Black may be unnecessary
- **Source:** Domain Expert
- **Problem:** Course teaches Black + Ruff separately. Ruff now includes `ruff format` which is Black-compatible.
- **Fix:** Consider simplifying to Ruff for both linting and formatting. Reduces tool count and aligns with the "use Ruff" message.
- **Files:** `sse/06-code-quality/06-code-quality.ipynb`

### M4. No `uv` coverage anywhere
- **Source:** Domain Expert
- **Problem:** `uv` is a major Python tool in 2026 (from Astral, same as Ruff) but is never taught.
- **Fix:** Add a section or sidebar to L04 introducing `uv` as a faster alternative to pip/venv. Mention `uv pip install`, `uv venv`, `uv run`.
- **Files:** `sse/04-python-packaging/04-python-packaging.ipynb`

### M5. h-index function inconsistency across modules
- **Source:** CS Educator, Domain Expert
- **Problem:** `calculate_h_index` appears in L05 (correct, with `enumerate(..., 1)`) and L07 (intentionally buggy, `enumerate(...)` starting at 0). No cross-reference between them. L05 version may also have a subtle `break` issue.
- **Fix:** (a) Verify L05 version is fully correct. (b) Add a note in L07 Exercise 2: "You saw a correct version of this in Module 05 — this one has a subtle difference." (c) Add a test case that catches the break issue if it exists.
- **Files:** `sse/05-testing-with-ai/05-testing-with-ai.ipynb`, `sse/07-debugging/07-debugging.ipynb`

### M6. PyPI publishing should use Trusted Publishers
- **Source:** Domain Expert
- **Problem:** L09 uses `twine upload` with stored secrets. Modern best practice is PyPI Trusted Publishers (OIDC) or `pypa/gh-action-pypi-publish`.
- **Fix:** Update publishing workflow example to use the official GitHub Action.
- **Files:** `sse/09-github-actions/09-github-actions.ipynb`

### M7. Week 6 timing problem (L10+L11 taught same week as project due)
- **Source:** Instructional Designer
- **Problem:** Documentation (L10) and agent configuration (L11) are taught the same week the final project is due. Students can't apply these skills in their project.
- **Fix:** Options: (a) Swap weeks 5 and 6 so L10/L11 come before L08/L09. (b) Move project deadline to end of Week 7. (c) Accept that L10/L11 are applied only in the presentation, not the submission.
- **Files:** `sse/syllabus.ipynb`

### M8. MCP server example may have issues
- **Source:** CS Educator, Domain Expert
- **Problem:** Imports `Tool, TextContent` but never uses them. No `pip install` instruction for the `mcp` package. API may have changed by course delivery.
- **Fix:** Remove unused imports. Add installation instruction. Note that students should check current MCP SDK docs.
- **Files:** `sse/11-advanced-mcp/11-advanced-mcp.ipynb`

### M9. A4 is overloaded
- **Source:** Instructional Designer
- **Problem:** A4 covers ruff, pre-commit, debugging with AI, type hints, and mypy — feels like four mini-assignments.
- **Fix:** Consider moving type hints/mypy (Part 3) to A3 (where students are already structuring their package) or making it optional.
- **Files:** `sse/assignments/a4-debugging-quality.ipynb`, possibly `sse/assignments/a3-testing-quality.ipynb`

### M10. SQLAlchemy example uses deprecated API
- **Source:** Domain Expert
- **Problem:** Databases optional module uses `declarative_base()` (SQLAlchemy 1.x pattern). SQLAlchemy 2.0+ uses `DeclarativeBase`.
- **Fix:** Update to modern SQLAlchemy 2.0 pattern.
- **Files:** `sse/optional/databases/databases.ipynb`

---

## LOW PRIORITY — Nice to Have

### L1. Unnumbered final exercises inconsistent across lectures
- **Source:** CS Educator
- **Problem:** Several lectures have an unnumbered exercise after the Summary section. Students won't know if it's required.
- **Fix:** Either number them and move before Summary, or label as "Optional" or "Take-Home."
- **Files:** L01, L04, L05, L06, L08, L10

### L2. L07 exercise times exceed class period
- **Source:** CS Educator
- **Problem:** Exercise times sum to ~65 minutes, leaving no time for content.
- **Fix:** Mark Exercise 5 as optional/take-home or reduce scope.
- **Files:** `sse/07-debugging/07-debugging.ipynb`

### L3. Participation journal lacks model entry and rubric
- **Source:** Instructional Designer
- **Problem:** Students don't know what "thoughtful reflection" looks like vs. surface-level.
- **Fix:** Add one model entry (Week 1 example) and a 3-level rubric (surface/adequate/insightful).
- **Files:** `sse/assignments/participation.ipynb`

### L4. "Hallucinate" used before defined in L00
- **Source:** CS Educator
- **Problem:** Term appears in cell-2 without definition.
- **Fix:** Add parenthetical: "hallucinate (confidently generate incorrect information)"
- **Files:** `sse/00-ai-assisted-development/00-ai-assisted-development.ipynb`

### L5. OpenAlex `/concepts` endpoint deprecated
- **Source:** Domain Expert
- **Problem:** L03 lists `/concepts` endpoint. OpenAlex has deprecated it in favor of `/topics`.
- **Fix:** Replace `/concepts` with `/topics`.
- **Files:** `sse/03-working-with-apis/03-working-with-apis.ipynb`

### L6. Context Engineering Reminders missing from L04, L09
- **Source:** CS Educator
- **Problem:** Reminders appear in L03, L05, L07, L08, L10, L11 but not L04 (packaging) or L09 (CI/CD) where they'd be useful.
- **Fix:** Add brief reminders before the first exercise in L04 and L09.
- **Files:** `sse/04-python-packaging/04-python-packaging.ipynb`, `sse/09-github-actions/09-github-actions.ipynb`

### L7. No branch protection rules in L08
- **Source:** Domain Expert
- **Problem:** Collaboration module doesn't mention requiring reviews or CI before merge.
- **Fix:** Add a brief section on configuring branch protection rules in GitHub.
- **Files:** `sse/08-github-collaboration/08-github-collaboration.ipynb`

### L8. Pricing and context window numbers will become stale
- **Source:** Domain Expert
- **Problem:** Specific prices and token counts will change.
- **Fix:** Add "as of early 2026" qualifiers or link to pricing pages.
- **Files:** `sse/00-ai-assisted-development/00-ai-assisted-development.ipynb`

### L9. MANIFEST.in tip is outdated
- **Source:** Domain Expert
- **Problem:** Tips section suggests writing MANIFEST.in. Modern pyproject.toml handles this.
- **Fix:** Replace with `[tool.setuptools.package-data]` guidance.
- **Files:** `sse/04-python-packaging/04-python-packaging.ipynb`

### L10. No mention of Docker/containers
- **Source:** Domain Expert
- **Problem:** Containers are increasingly important for reproducible science and deployment.
- **Fix:** Consider adding a brief optional module, or a sidebar in L09 (CI/CD runs in containers).
- **Files:** Could be a new optional module or added to existing content.

### L11. Accommodations section incomplete
- **Source:** Instructional Designer
- **Problem:** Says "contact the Office of Disability Resources" with no URL or contact info. Office hours are "TBD."
- **Fix:** Add CMU Disability Resources URL and fill in office hours before course launch.
- **Files:** `sse/syllabus.ipynb`

### L12. Participation scope unclear
- **Source:** Instructional Designer
- **Problem:** Is the journal the entirety of the 20% participation grade, or does attendance count too?
- **Fix:** State explicitly whether participation = journal only, or journal + attendance.
- **Files:** `sse/syllabus.ipynb`, `sse/assignments/participation.ipynb`

### L13. Ethics should arguably be required, not optional
- **Source:** Instructional Designer
- **Problem:** Given the course's heavy use of AI-generated code, copyright/licensing implications are important for all students.
- **Fix:** Consider making the ethics lecture required (perhaps Week 6 instead of one of L10/L11), or integrate key points into L00.
- **Files:** `sse/syllabus.ipynb`, `sse/_toc.yml`

---

## Implementation Order

**Phase 1 — Critical fixes (before any teaching):**
H1-H7, M1 (duplicates)

**Phase 2 — Technical accuracy:**
H2, H3, M2, M3, M5, M6, M8, M10

**Phase 3 — Assessment and rubrics:**
H5, L3, M9

**Phase 4 — Content improvements:**
M4, M7, L1, L2, L4-L9

**Phase 5 — Nice-to-have:**
L10-L13
