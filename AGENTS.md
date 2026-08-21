# jheem-wiki

This repository is the cross-repository knowledge base for the JHEEM ecosystem.
Canonical content is the Markdown and Quarto source; `_site/` is generated and
ignored.

## Before working

1. Read `README.md` for the documentation boundary and contribution conventions.
2. Read `ecosystem-map.qmd` and `decisions.qmd` before making cross-repository
   claims or proposals.
3. Read the relevant topic page and verify changeable details against the source
   repository rather than relying on the wiki alone.

## Documentation routing

- Put commit-coupled material—API documentation, runnable examples, vignettes,
  and single-repository build instructions—in the repository it changes with.
- Put durable cross-repository material—maps, flows, runbooks, practice baselines,
  and decisions—in this wiki.
- Keep session analysis, tentative strategy, and cross-session correspondence in
  ignored working notes such as `_reviews/`, not in the public wiki.

Public wiki prose must be audience-invariant: write normal senior-level
documentation, not instructions to an AI agent or narration of a particular
person's environment.

## Continuous capture

Treat every ecosystem task as a possible source of wiki knowledge. Before finishing
a task, assess whether the work:

- established or corrected a cross-repository fact;
- changed a documented workflow, baseline, or roadmap status;
- produced a reusable cross-repository runbook;
- adopted, reversed, or refined a recorded decision.

If so, update the appropriate page once the finding is evidence-backed and durable.
Do not force a wiki change when the result is local, tentative, or already belongs
in an owning repository. The goal is capture without reconstruction, not page-count
growth.

## Evidence and status

- Separate observed facts, inferences, proposals, and adopted decisions.
- Use commit-pinned references for implementation claims likely to drift.
- Quantify material scale or risk where possible; avoid unsupported severity
  adjectives and blame.
- Date-stamp substantive additions.
- Reserve “shipped” for work in its durable home, used through the supported path,
  and protected by an appropriate regression check.

## Repository conventions

- The decision log is append-only. Add a superseding entry instead of rewriting an
  earlier decision.
- Archived documents remain verbatim; add provenance or context only in
  `archive/index.qmd`.
- Add new pages to the sidebar in `_quarto.yml`.
- Update `roadmap.qmd` as implementation changes the documented state.
- Do not commit `_site/` or ignored working notes.
- Validate Quarto structure and links where practical; render the full site when
  the local toolchain permits it.

Keep this file and `CLAUDE.md` aligned when repository instructions change.
