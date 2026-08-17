# Refactoring Status

**Created:** 2024-11-20
**Last Updated:** 2024-12-10
**Current Phase:** 1 (Mono-Repo Extraction)
**Week:** 1 of 8 - ✅ COMPLETE + VALIDATED
**Current Task:** Ready for Week 2-3 (jheem.specification extraction)

---

## Phase 1 Progress: Mono-Repo Extraction

### Week 1: Extract jheem.core ✅ COMPLETE

#### Completed
- [x] Created refactor branch: `refactor/extract-packages`
- [x] Set up `.refactoring/` tracking directory
- [x] Created STATUS.md tracker
- [x] Establish baseline metrics (79,977 LOC total)
- [x] Create packages/ directory
- [x] Extract jheem.core files (8 R files, 2 C++ files)
- [x] Create jheem.core DESCRIPTION with dependencies
- [x] Build jheem.core with Rcpp::compileAttributes()
- [x] Install jheem.core to R library ✅ SUCCESS
- [x] Update jheem2/DESCRIPTION to import jheem.core
- [x] Create R/jheem2-imports.R with @import declaration
- [x] Integrate with main jheem2 package
- [x] Remove original R/ONTOLOGY, R/HELPERS files from jheem2
- [x] Remove duplicate C++ files from jheem2/src
- [x] Fix C++ build artifacts issue (rm *.o, update .gitignore)
- [x] Fix package initialization issue (created .onLoad() hook)
- [x] Fix NAMESPACE export issue (exportPattern("."))
- [x] Verify jheem2 loads with devtools::load_all() ✅ SUCCESS
- [x] Commit extraction: `a811405`
- [x] Commit integration: `28ee31c`
- [x] Document issues and tech debt in ISSUES.md
- [x] Create SESSION_HANDOFF.md for continuity
- [x] Commit documentation: `179f2ac`

#### Metrics
- **Lines removed from jheem2:** 11,776
- **Files extracted:** 10 (8 R + 2 C++)
- **jheem.core size:** ~8,732 lines
- **jheem2 version:** 1.9.2 → 1.9.3
- **Total commits:** 3

#### Issues Resolved
1. ✅ C++ build artifacts corruption (stale .o files)
2. ✅ Top-level code execution during package load
3. ✅ NAMESPACE export pattern (functions not exported)

#### Tech Debt Acquired
- TD-1: Manual NAMESPACE export with exportPattern(".") [Low priority]
- TD-2: Redundant NULL.INTERVENTION initialization [Very Low priority]
- TD-3: ~~Existing tests not run~~ ✅ RESOLVED - validation script created
- TD-4: No formal testthat framework yet [Low priority - deferred until architecture stable]

#### Validation (2024-12-09, updated 2024-12-10) ✅ COMPLETE

Created `.refactoring/validate.R` - a repeatable validation checkpoint that:
- Loads jheem2 package
- Compiles EHE specification
- Loads real simset from jheem2_interactive
- Tests `sim$get()` for multiple outcomes
- Tests `ontology()` and jheem.core functions
- Creates engine and runs fresh simulation
- Compares fingerprint to baseline
- **Tests interventions** using CDCT spec/simset (added 2024-12-10)

**Fingerprint (baseline from dev):**
```
simset.incidence.2020.sum: 2559.33
simset.prevalence.2020.sum: 179901.4
simset.new.2020.sum: 1129.65
simset.pop.2020.sum: 23439308
fresh.sim.incidence.2020: 42
```

**Result:** ✅ Refactor branch matches dev branch exactly + interventions work

**Run after each extraction:** `Rscript .refactoring/validate.R`

#### Known Pre-existing Issues (NOT caused by extraction)
- Depression model specification broken (missing 'depression' dimension)

#### Next Steps
Proceed to **Week 2-3: Extract jheem.specification**

---

## Blockers
None - ready to proceed with Week 2-3

---

## Notes

### Session 2024-12-10 (Validation Overhaul)
- Investigated intervention testing after user pushback on minimal validation
- Initial attempts with CDCT spec failed - CDCT simset missing 'population' outcome
- Discovered root cause of "environment not subsettable" error:
  - S3 methods for `protected.numeric.vector` NOT registered in NAMESPACE
  - Works in interactive R, fails in Rscript (different method dispatch)
  - Shiny app workaround: exports all internal functions
- Switched to Ryan White workflow for validation:
  - More significant/recent work than EHE or CDCT
  - Full outcome coverage (has 'population')
  - Based on simplified patterns from jheem-container-minimal
- Final validation tests:
  - Package loading, spec loading, simset loading
  - Outcome retrieval (incidence, prevalence, new, population)
  - Ontology functions (jheem.core)
  - Engine creation and simulation
  - Null intervention and Ryan White intervention
- Documented S3 registration issue as TD-4 in ISSUES.md
- Pulled latest jheem-container-minimal with simplified intervention patterns

### Session 2024-12-09 (Validation)
- Returned after 3-week break
- Existing test scripts (R/production_tests/) are stale - not useful for validation
- Created validation approach using real simsets from jheem2_interactive repo
- Built `.refactoring/validate.R` - repeatable validation checkpoint
- Confirmed refactor branch produces identical results to dev branch
- Identified pre-existing issues (Depression model, some intervention workflows) - not caused by extraction
- Decision: Defer formal testthat framework until architecture stabilizes
- Ready to proceed with Week 2-3: jheem.specification extraction

### Session 2024-11-20 (Phase 1, Week 1)
- Decided on phased mono-repo → multi-repo approach
- Rationale: Mono-repo during active refactoring (easier), multi-repo after stable
- Started with jheem.core (zero dependencies, high value, low risk)
- Successfully extracted and integrated jheem.core
- Resolved 3 technical issues during integration
- Identified need for proper testthat framework (existing tests are scripts, may be outdated)
- Documentation: ISSUES.md, SESSION_HANDOFF.md created for continuity

### Key Decisions
- **Approach:** Mono-repo in Phase 1-2, split to multi-repo in Phase 3
- **First package:** jheem.core (ONTOLOGY + HELPERS + VERSIONS)
- **Branch strategy:** Long-lived refactor branch, merge to dev after Phase 1 complete

---

## Metrics Tracking

### Baseline (Start of Phase 1)
- Total lines of code: 62,942
- Number of modules: 11
- Circular dependencies: 11
- Max file size: 10,967 lines (SPECIFICATION_model_specification.R)
- Test framework: Manual scripts (no testthat yet)

### After Week 1
- jheem2 lines of code: ~51,200 (down from 62,942)
- Lines extracted to jheem.core: ~8,732
- Number of modules in jheem2: 10 (down from 11)
- Packages created: 1 (jheem.core)
- Test coverage: None (testthat not set up yet)

---

## Quick Commands

**Run validation (after each extraction):**
```bash
Rscript .refactoring/validate.R
```

**Check status:**
```bash
git status
git branch
```

**Build sub-package:**
```bash
cd packages/jheem.core
Rscript -e "devtools::document()"
Rscript -e "devtools::install()"
cd ../..
```

**Test integration:**
```bash
Rscript -e "devtools::load_all()"
```
