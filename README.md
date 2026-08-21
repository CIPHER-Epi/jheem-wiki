# JHEEM Wiki

Canonical source for the cross-repository JHEEM knowledge base. The
[reader-facing site](https://cipher-epi.github.io/jheem-wiki/) provides the content
map and documentation boundary.

## Contributing

Commit-coupled documentation belongs in the repository it changes with. Durable
knowledge that spans repositories belongs here. Verify changeable claims against
the relevant source repositories and distinguish observed behavior, inference,
proposals, and adopted decisions.

When changing the wiki:

- Write for any reader, without machine- or person-specific instructions.
- Date-stamp substantive additions.
- Add new pages to the sidebar in `_quarto.yml`.
- Add superseding decisions rather than rewriting decision history.
- Preserve archived documents verbatim; put context in `archive/index.qmd`.
- Update `roadmap.qmd` when implementation changes the documented baseline.
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

GitHub Actions renders and deploys the site after changes land on `main`.
