# The PR Butler — Challenge Brief

## 1. The Mission

Create a **PR Butler Skill** — a structured `SKILL.md` file that instructs an AI agent to automate the complete checklist developers run before opening a pull request. **Any IDE** with agent support works (VS Code, Cursor, IntelliJ, Windsurf, etc.).

Your Skill orchestrates **6 steps**, turning the deliberately flawed scaffold into ship-ready code:

| Step | What the Agent Does |
|------|-------------------|
| 1. Translation Fix | Detect 12 missing French keys in `fr.json`, generate translations |
| 2. Code Cleanup | Format code consistently, fix lint violations, fix code style |
| 3. Test Automation | Generate tests for uncovered functions, push coverage above 80% |
| 4. Documentation | Add docstrings, update README, generate CHANGELOG + PR_REQUEST.md |
| 5. Quality Gates | Enforce thresholds — fail if coverage < 80%, lint errors remain, or tests fail |
| 6. PR Preparation | Generate conventional commit message, finalize all deliverables |

---

## 2. What's Broken (On Purpose)

The scaffold at `scaffold/website/` has these deliberate issues for your Skill to fix:

| Category | Issue | Details |
|----------|-------|---------|
| **Translations** | 12 of 14 French keys missing | `src/translations/fr.json` has 2 entries vs 14 in `en.json` |
| **Code Quality** | Bad formatting | `handleSubmit()` in `main.ts` — no indentation |
| **Test Coverage** | ~30% covered | 6 functions untested: `toggleTask`, `deleteTask`, `setFilter`, `render`, `saveToStorage`, `loadFromStorage` |
| **Documentation** | No docstrings | 9 public functions undocumented: `addTask`, `toggleTask`, `deleteTask`, `setFilter`, `render`, `init`, `setupEventListeners`, `handleSubmit`, `switchLanguage` |
| **Documentation** | README is bare | Missing Features, Testing, and Contributing sections |

---

## 3. Creating Your SKILL.md

For **VS Code / GitHub Copilot**, place it at:

```
.github/skills/<skill-name>/SKILL.md
```

A starter template is at `.github/skills/pr-butler/SKILL.md` — it has the structure and a locked Report Card step at the end. For other IDEs, refer to your IDE's agent skill documentation.

### Required Structure

Your SKILL.md needs **YAML frontmatter** (name + description) and these **4 sections:**

| Section | What to Include |
|---------|----------------|
| **Overview** | What the Skill does, when to invoke it |
| **Instructions** | Step-by-step workflow for all 6 steps — specific files, commands, outputs |
| **Examples** | At least 2 scenarios with expected output |
| **Success Criteria** | Checklist the agent uses to confirm everything passed |

> **Important:** The starter template includes a final step (Report Card) that **must not be modified**. It's a self-grading mechanism for tracking your progress.

---

## 4. Step Details

### Step 1: Translation Detection & Fix
- Compare keys in `src/translations/en.json` vs `src/translations/fr.json`
- Generate missing French translations using context from the English values
- Update `fr.json` — validate all 14 keys are present

### Step 2: Code Cleanup
- Format all source files consistently (Prettier or equivalent)
- Fix auto-fixable lint violations
- Fix the `handleSubmit` function formatting in `main.ts`

### Step 3: Test Automation
- Run existing tests: `npm run test`
- Generate test cases for: `toggleTask`, `deleteTask`, `setFilter`, `render`, `saveToStorage`, `loadFromStorage`
- Re-run to confirm all pass
- Achieve >80% coverage: `npm run test:coverage`

### Step 4: Documentation Updates

| Document | What to Do |
|----------|-----------|
| **Source docstrings** | JSDoc/TSDoc on all 9 undocumented public functions in `src/` |
| **`scaffold/website/README.md`** | Add Features, Testing, and Contributing sections |
| **`CHANGELOG.md`** | Summarize all fixes made by the Skill |
| **`PR_REQUEST.md`** | Conventional PR description with title, summary, checklist, coverage report |

### Step 5: Quality Gates
- Coverage ≥ 80% — fail if below
- Zero critical lint errors
- All tests pass
- If any gate fails: report the failure and stop

### Step 6: PR Preparation
- Generate a conventional commit message from the changes
- Finalize `PR_REQUEST.md` with all quality metrics
- Confirm all Step 4 deliverables are complete

---

## 5. Deliverables Checklist

Your submission must include **all** of the following:

- [ ] **`SKILL.md`** — complete with YAML frontmatter + all 4 sections
- [ ] **Updated `fr.json`** — all 14 French translation keys
- [ ] **Updated source files** — lint-clean, properly formatted
- [ ] **Test files** — new or updated, achieving >80% coverage
- [ ] **Source docstrings** — JSDoc/TSDoc on all 9 public functions
- [ ] **Updated `scaffold/website/README.md`** — Features, Testing, Contributing sections
- [ ] **`CHANGELOG.md`** — summarizing all changes
- [ ] **`PR_REQUEST.md`** — conventional PR description with summary, checklist, coverage

---

## 6. Grading

Your submission is evaluated by an AI grading agent:

| Dimension | Focus |
|-----------|-------|
| **Translation Automation** | Detects all missing keys, generates accurate French, updates `fr.json` correctly |
| **Code Quality Automation** | Formats consistently, fixes lint violations, improves code style |
| **Test Automation** | Meaningful test cases, >80% coverage, all tests pass |
| **Documentation Automation** | Docstrings on all functions, README updated, CHANGELOG and PR_REQUEST.md generated |
| **Quality Gates** | Steps in correct order, gates enforced, clear pass/fail reporting |
| **Orchestration & Reliability** | Instructions are clear, workflow is repeatable, errors handled gracefully |

### Sparks

- **8 ✦** for a passing submission
- Bonus sparks for going above and beyond

---

## 7. Submission

1. **Fork** this repository
2. Create your SKILL.md (see [Section 3](#3-creating-your-skillmd))
3. Run your Skill against the scaffold to verify it works
4. **Commit frequently** — we review your progression
5. Submit your **fork URL** via the AI Hub Portal
6. In the notes field, **paste the full contents of your SKILL.md** — ensures evaluation even if repo access is restricted
