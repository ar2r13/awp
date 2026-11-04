# Browser client architecture

Read for startup, routing, controllers, build, or browser compatibility. These
are defaults for a new browser app. Existing code and project requirements win.

| Area | Suggested location and owner |
| --- | --- |
| Boot | `src/index.html` for the shell; `src/index.ts` for compatibility setup and app import |
| Composition | `src/app.ts` wires the shell, router, guards, and route table |
| Routing | `src/controllers/router.ts` when routing outgrows the composition root |
| Screens and UI | `src/pages/` for route targets; `src/components/` for reusable UI |
| Domain and IO | `src/controllers/` for state, transport, and persistence; `src/lib/` for small generic helpers |
| Build and compatibility | `scripts/` for esbuild; `src/polyfills/index.ts` for required shims |

- Use Lit as the rendering layer. Prefer browser APIs before adding dependencies;
  avoid adding a second UI framework, router, or global store to this stack.
- For an SPA, use one route table with Navigation API and `URLPattern`. Load
  `@virtualstate/navigation/polyfill` and `urlpattern-polyfill` on demand when
  their APIs are missing, before starting the router. Intercept eligible same-origin
  navigations, handle the initial URL, and keep real links usable. Lazy-load pages and await only their
  needed domain data. Keep guards in routing; the API enforces authorization.
- Share domain state through exported controller instances. Use
  `@lit-labs/signals` for shared reactive state and `SignalWatcher` for components
  that read it. Use the package's `signal()` or the existing `Signal.State` pattern;
  do not assume Signals are a native browser API. Pages own temporary UI state.
  Generic components take properties and emit events; domain-aware ones may read
  controllers. Controllers do not import pages or components.
- Give async work an owner. Cancel superseded operations or ignore stale results
  when requests overlap. Add retries, rollback, or error distinctions only when
  behavior needs them. Keep durable caches with their owning controller: IndexedDB
  for structured data, `localStorage` for small preferences. Keep sensitive data
  out of caches and logs unless explicitly needed and protected.
- Use a small esbuild ESM build with code splitting for lazy routes. Determine
  the actual scripts, output directory, and stylesheet pipeline from the project.
  For new clients, configure PostCSS with `postcss-custom-selectors` and
  `{ preserve: false }` in the default build. Apply it to CSS that reaches the
  browser, including copied stylesheets and constructable sheets if used. Keep
  alias definitions and their consumers in the same CSS processing context.
  Edit source, not generated output. Client build variables are public.
- Set target browsers first. Verify required APIs and CSS against those targets;
  prefer stable features and targeted, feature-detected shims over speculative
  APIs or a second compatibility architecture. Optional motion should degrade
  to an immediate update. Check embedded WebViews separately if supported.
- For installable or offline apps, add a manifest and service worker as needed.
  Define cache lifetime and offline behavior; do not cache authenticated responses
  indiscriminately. Do not scaffold PWA assets for every browser UI.
