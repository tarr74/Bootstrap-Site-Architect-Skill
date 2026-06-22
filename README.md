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
Use the bootstrap-site-architect skill. Create an elegant, non-generic Bootstrap/PHP landing page. Use Bootstrap for structure and components, but put colors, typography, backgrounds, and visual details in home.css. If interactions are needed that Bootstrap does not already cover, put them in home.js. Do not modify the original Bootstrap files. Optimize SEO, performance, accessibility, and responsive behavior.
```

## Natural-language section example

```text
I want a section as wide as the whole site, with a two-column row: the first column should be 4/12 wide, with background #cfcfcf, text #ff9900, links #ff00ff, a dummy h1, and three paragraphs; the second column should be 8/12 wide, with background #000000, text #ffffff, and h1 and h2 color #667723. Generate Bootstrap HTML and external CSS.
```

Codex should produce Bootstrap markup plus a scoped CSS block/file, and should ask for clarification if color values or layout constraints are invalid.

## External frontend-design source

This package includes adapted principles from the community `frontend-design` skill in `vipulgupta2048/codex-skills`, but it remains self-contained and Bootstrap-first. For source notes, see:

```text
references/third-party-frontend-design-source.md
```
