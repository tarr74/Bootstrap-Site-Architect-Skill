[README.md](https://github.com/user-attachments/files/29217246/README.md)
# Bootstrap Site Architect Skill v8

A Codex skill for designing, creating, refactoring, visually reviewing, SEO/performance-auditing, and editing text/content in Bootstrap 5.3 HTML/PHP pages, landing pages, and templates.

This v8 package combines five layers:

1. **Bootstrap-first implementation**: real Bootstrap 5.3 HTML/PHP/CSS/JS, not generic mockups.
2. **Full modular Bootstrap docs**: the user-provided Bootstrap 5.3 offline docs, split by menu topic under `references/bootstrap-docs-full/`.
3. **Integrated frontend-design layer**: art-direction guidance adapted from the community `frontend-design` approach, but constrained to Bootstrap-based sites.
4. **Strict custom CSS/JS policy**: Bootstrap source files are never changed; all non-standard visual decisions go into custom CSS loaded after Bootstrap, and all non-Bootstrap behavior goes into external custom JS loaded separately.
5. **Safe JavaScript behavior layer**: custom interactions are implemented with vanilla JS in external files and only when Bootstrap does not already provide the behavior.

The Bootstrap `About` section is intentionally omitted from the full docs.

## Efficiency model

Codex should not read the full documentation library by default. It should read:

1. `SKILL.md`;
2. one operational reference when needed;
3. one to three targeted Bootstrap docs from `references/bootstrap-docs-full/` when Bootstrap-specific uncertainty exists;
4. the frontend-design layer only for substantial visual design work.

Key routers:

```text
references/bootstrap-doc-router.md
references/frontend-design-interop.md
references/frontend-design-bootstrap-layer.md
references/bootstrap-custom-css-policy.md
references/bootstrap-custom-js-policy.md
```

## Hard rule about Bootstrap files

Do not edit Bootstrap original CSS or JS files. Do not patch `bootstrap.css`, `bootstrap.min.css`, `bootstrap.bundle.js`, `bootstrap.bundle.min.js`, CDN Bootstrap files, vendor copies, or `node_modules/bootstrap/`.

Custom style belongs in a separate file loaded after Bootstrap, for example:

```html
<link rel="stylesheet" href="/assets/vendor/bootstrap/css/bootstrap.min.css">
<link rel="stylesheet" href="/assets/css/custom.css">
<link rel="stylesheet" href="/assets/css/home.css">
```

Custom JavaScript belongs in a separate script file loaded after Bootstrap when it depends on Bootstrap behavior, for example:

```html
<script src="/assets/vendor/bootstrap/js/bootstrap.bundle.min.js" defer></script>
<script src="/assets/js/site.js" defer></script>
```

## Example prompt

```text
Usa la skill bootstrap-site-architect. Crea una landing Bootstrap/PHP elegante e non generica. Usa Bootstrap per struttura e componenti, ma metti colori, tipografia, background e dettagli visuali in home.css. Se servono interazioni non coperte da Bootstrap, mettile in home.js. Non modificare i file originali di Bootstrap. Ottimizza SEO, performance, accessibilità e responsive.
```

## Natural-language section example

```text
Voglio una section larga come tutto il sito con una riga a due colonne: la prima larga 4/12, background #cfcfcf, testo #ff9900, link #ff00ff, dummy h1 e tre paragrafi; la seconda larga 8/12, background #000000, testo #ffffff, h1 e h2 #667723. Genera HTML Bootstrap e CSS esterno.
```

Codex should produce Bootstrap markup plus a scoped CSS block/file, and should ask for clarification if color values or layout constraints are invalid.

## External frontend-design source

This package includes adapted principles from the community `frontend-design` skill in `vipulgupta2048/codex-skills`, but it remains self-contained and Bootstrap-first. For source notes, see:

```text
references/third-party-frontend-design-source.md
```
