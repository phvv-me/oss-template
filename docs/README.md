# Docs design base

`stylesheets/base.css` is the canonical brand layer shared by every package
in `packages/`. It is the single source of truth for the docs look.

The styling is mkdocs-material's built-in components plus Open Props design
tokens. Open Props is pulled build-free over the wire with a CSS `@import`,
so there is no build step and nothing is vendored except the one CSS file.

## How packages use it

Each package vendors a copy of `base.css` into its own
`docs/stylesheets/base.css` and pairs it with a tiny `brand.css` that sets
only three hook variables for its accent color.

```css
:root {
  --brand-primary: #d97706;       /* primary header, light scheme */
  --brand-primary-dark: #b45309;  /* primary header, dark scheme  */
  --brand-accent: #0d9488;        /* links, focus, active state    */
}
```

The package `mkdocs.yml` loads them in order.

```yaml
extra_css:
  - stylesheets/base.css
  - stylesheets/brand.css
```

`base.css` maps those hooks and Open Props tokens onto Material's own CSS
variables, so a package only ever picks a color. To change the shared look,
edit this file and copy it out to each package.
