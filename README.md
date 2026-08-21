# JHEEM Wiki

The JHEEM Wiki is the cross-repository knowledge base for the Joint HIV
Epidemiology and Economic Model ecosystem. It explains what the repositories do,
how data and artifacts move between them, and why important cross-cutting decisions
were made.

The canonical source is the Markdown and Quarto content in this repository. GitHub
Pages publishes the rendered site at
[cipher-epi.github.io/jheem-wiki](https://cipher-epi.github.io/jheem-wiki/).

## Documentation boundary

Use one routing rule:

- Knowledge that changes with a commit belongs in the repository changed by that
  commit: API reference, function documentation, runnable examples, vignettes, and
  single-repository build instructions.
- Knowledge that spans repositories or outlives individual commits belongs here:
  ecosystem maps, cross-repository data flows, runbooks, program direction,
  practice baselines, and decisions.

The wiki is not a scratchpad. Work across the ecosystem should continuously surface
possible wiki updates, but findings are promoted here only when they are supported
by evidence, useful beyond the immediate task, and stable enough to review. Session
notes, tentative strategy, and unverified observations remain working material until
they meet that threshold.

## Start here

- [`ecosystem-map.qmd`](ecosystem-map.qmd) maps the repositories and artifact flow.
- [`application-anatomy.qmd`](application-anatomy.qmd) describes the current
  application lifecycle.
- [`decisions.qmd`](decisions.qmd) records adopted direction and rationale.
- [`roadmap.qmd`](roadmap.qmd) tracks current sequencing and the practice baseline.
- [`program.qmd`](program.qmd) holds the longer-form working vision.

## Contributing

Before making cross-repository claims, consult the ecosystem map and decision log.
Verify claims against the relevant source repositories; use commit-pinned evidence
for details likely to change. Distinguish observed behavior, inference, proposals,
and adopted decisions.

When changing the wiki:

- Write for any reader, without machine- or person-specific instructions.
- Date-stamp substantive additions.
- Add new pages to the sidebar in `_quarto.yml`.
- Treat the decision log as append-only: record a new superseding decision rather
  than rewriting an earlier one.
- Preserve archived documents verbatim; put context in `archive/index.qmd`.
- Update roadmap status when implementation changes the documented baseline.
- Reserve “shipped” for work in its durable home, used through the supported path,
  and protected by an appropriate regression check.

## Local preview

[Install Quarto](https://quarto.org/docs/get-started/) and run:

```sh
quarto preview
```

To build the complete site into the ignored `_site/` directory:

```sh
quarto render
```

GitHub Actions renders and deploys the site after changes land on the default
branch.
