# Browser client UI and style

Read for Lit rendering, components, CSS, or interaction. Match existing files and
the project's design system. Apply these defaults where no local convention exists.

- Keep shell layout, global layers, and typography in `src/style.css`; place
  shared tokens and primitives in `src/styles/`. Colocate feature CSS with its
  owner. Extract a shared primitive only when its contract is reused.
- Prefer light DOM for pages and app UI that participates in the global cascade.
  Reuse the existing helper. Use shadow DOM for isolation or an explicit slot/part
  contract. Share styles across that boundary through inheritance, custom
  properties, or explicit stylesheets; global selectors do not cross it.
- Use the actual CSS pipeline. Load light-DOM CSS through the global entry or
  an explicit route loader. A lazy JS import alone does not guarantee CSS is
  applied. Use `with { type: 'css' }` for constructable sheets only when the target
  browsers or the build handle it; esbuild's ordinary CSS loader is different.
- Prefer low-specificity scoped selectors and composable kebab-case traits,
  such as `button solid`; avoid new BEM namespaces. Use `@scope` where supported
  or scope under the owned element. Use `@custom-selector` for named, reusable
  selector groups and `:is()` or `:where()` for one-off groups. The default build
  compiles custom selectors to standard CSS.
- Default layer order: `reset, element, component.base, component.modifier,
  layout, modifier`. Put primitives in `component.base`, not bare `component`:
  direct rules in a layer outrank its sublayers for normal declarations.
- Reuse semantic tokens and the spacing scale. Use `rem` for design sizes and
  `px` for intentionally fixed borders or thresholds. Let typography and color
  inherit; vary primitives through custom properties. Group declarations by
  purpose and nest media queries under their owner where appropriate.
- TypeScript: tabs, same-line braces, single quotes, usually no semicolons;
  `render ()` for definitions, `render()` for calls, `value : string` for types.
  Prefer concise precise names. Comments explain intent and quirks. Do not reformat
  unrelated code.
- Lit templates: unquoted simple static attributes where valid, single quotes
  for multi-word values, small expressions and bindings close to their element.
  Compute multi-step values outside the template. Use Lit bindings for dynamic
  content rather than inserting raw HTML.
- Prefer native controls. Preserve accessible names, keyboard and focus behavior,
  contrast, zoom, and non-color status cues. Respect reduced motion. Check the
  changed interaction instead of running a general UI checklist on every edit.
