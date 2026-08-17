# jheem-wiki

Cross-repo knowledge base for the JHEEM ecosystem. Canonical content is the markdown/qmd in this repo; a Quarto site renders from it (`quarto render`; output in `_site/`, gitignored).

Ground rules:

- **Boundary rule:** only cross-repo knowledge lives here (map, runbooks, decisions, roadmap). Single-repo detail belongs in that repo's own docs/CLAUDE.md.
- **Decision log is append-only.** Reversals get a new superseding entry, never an edit.
- **Archive is verbatim.** Historical docs keep their original text; context goes in `archive/index.qmd`.
- Date-stamp substantive additions. Update `roadmap.qmd` status tables as work lands.
- Sidebar navigation is defined in `_quarto.yml` — new pages must be added there.

Start by reading `ecosystem-map.qmd` and `decisions.qmd` before making cross-repo claims.
