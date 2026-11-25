# React implementation techniques for a premium Hakira dashboard (React 18 + TS + Vite + plain CSS, Hebrew RTL, light/dark)

Method note for the report writer: in this session most documentation sites (motion.dev, reactflow.dev, MDN, web.dev, caniuse, echarts.apache.org, radix-ui.com, react-spectrum.adobe.com) could not be reached, because the session's network policy blocked them. What I could reach:
(a) the **npm registry** (versions, licenses, publish dates and peer dependencies, as of 2026-11-25);
(b) the **published package tarballs**, which I downloaded and inspected. Type definitions, CSS and minified bundles were grepped and gzipped locally, so claims marked "verified in package" come straight from shipped code;
(c) the **`web-features` dataset v3.47.0**, the data behind Baseline / webstatus.dev, which I used for browser support;
(d) WebSearch result snippets.
Package-file citations point to the matching unpkg path so a reader can check them. Anything I could not check is flagged **[unverified]**.

### Version snapshot (npm registry, checked 2026-11-25)
| Package | Latest | License | Published | Notes |
|---|---|---|---|---|
| `motion` (and the alias `framer-motion`) | 14.14.0 | MIT | 2026-11-13 | peer `react ^18 \|\| ^19` |
| `@xyflow/react` | 13.0.3 | MIT | 2026-11-23 | peer `react >=18`; depends on `zustand ^5`, `@xyflow/system 1.0.0`, `react-compiler-runtime ^1` |
| `cytoscape` | 3.35.0 | MIT | 2026-11-10 | |
| `recharts` | 3.11.1 | MIT | 2026-11-23 | |
| `echarts` | 6.1.0 | Apache-2.0 | 2026-05-19 | `echarts-for-react` 3.1.0 (MIT) |
| `@visx/*` (e.g. `@visx/shape`, `@visx/gradient`, `@visx/text`) | 4.0.0 | MIT | 2026-06-11 | peer `react ^18 \|\| ^19` |
| `@nivo/core` | 0.99.0 | MIT | 2025-05-23 | |
| `@tremor/react` | 3.18.7 | Apache 2.0 | 2025-01-13 | no npm release since the Vercel acquisition |
| `d3` | 7.9.2 | ISC | 2026-11-03 | |
| `elkjs` | 0.12.1 | **EPL-2.0 OR GPL-3.0-or-later** | 2026-10-28 | |
| `@dagrejs/dagre` | 3.1.4 | MIT | 2026-11-24 | the old `dagre` package (0.8.5, 2019) is abandoned |
| `radix-ui` (unified) | 1.8.1 | MIT | 2026-10-12 | `@radix-ui/react-direction` 1.2.0 |
| `@radix-ui/themes` | 3.3.0 | MIT | 2026-01-31 | |
| `react-aria-components` | 1.22.1 | Apache-2.0 | 2026-10-09 | |
| `@ark-ui/react` | 5.40.1 | MIT | 2026-11-23 | |
| `@number-flow/react` | 0.6.2 | MIT | 2026-07-18 | peer `react ^18 \|\| ^19` |
Source: npm registry `https://registry.npmjs.org/<pkg>`, e.g. [motion](https://www.npmjs.com/package/motion), [@xyflow/react](https://www.npmjs.com/package/@xyflow/react), [recharts](https://www.npmjs.com/package/recharts), [elkjs](https://www.npmjs.com/package/elkjs).

---

## Animation: Motion vs CSS-only (transitions, @keyframes, View Transitions, scroll-driven, @starting-style)

### Takeaway
Use **CSS for most of the polish**: hover and focus states, the entrance of dialogs and popovers with `@starting-style`, staggered reveals, and stroke-dasharray drawing. In 2026 these are Baseline or close to it, and they cost 0 KB.
Add **Motion 14 (`motion/react`)** only where it adds something CSS can't do: layout/`layoutId` animations, `AnimatePresence` exit animations, and spring physics. Load it through `LazyMotion` + `m` + `domAnimation`, which is about 30 KB gzip instead of about 46 KB.
Hakira is on React 18, so neither React's `<ViewTransition>` nor Motion's `AnimateView` is available: both need React 19.3. The raw `document.startViewTransition()` API works with any React version.

### Cited Findings
- `motion` and `framer-motion` are both at 14.14.0 (MIT, published 2026-11-13), with peer `react ^18.0.0 || ^19.0.0`, so React 18 is supported — [npm: motion](https://www.npmjs.com/package/motion), [npm: framer-motion](https://www.npmjs.com/package/framer-motion)
- The upgrade guide says v13 and v14 have no breaking changes for JavaScript users. The v12 change was that `press`/`hover`/`inView` gesture start callbacks now receive the target element as their first argument — [Motion upgrade guide](https://motion.dev/docs/react-upgrade-guide) (via search snippet)
- The package exports these subpaths: `.`, `./m`, `./mini`, `./dom`, `./dom/mini`, `./client`, `./projection`, `./animate-view`, `./debug`, `./remix` (verified in package.json) — [unpkg framer-motion@14.14.0/package.json](https://unpkg.com/framer-motion@14.14.0/package.json)
- **Measured bundle sizes**: gzip -9 of the size-check bundles Motion ships in `dist/`, excluding React (verified in package) — [unpkg framer-motion@14.14.0/dist/](https://unpkg.com/framer-motion@14.14.0/dist/):
  - full `motion` component: 140 KB minified / **~45.6 KB gzip**
  - `m` + `LazyMotion` with `domAnimation`: **~30.3 KB gzip**
  - `m` + `domMax` (adds layout and drag): ~45.8 KB gzip
  - bare `m` with no features loaded: ~4.9 KB gzip
  - `animate()` (hybrid): ~25.2 KB gzip
  - WAAPI-only `animate` (from `motion/mini`): **~3.3 KB gzip**
  - `scroll()`: ~3.8 KB gzip
- The typings include `AnimatePresence`, `LayoutGroup`, `LazyMotion`, `MotionConfig`, `domAnimation`, `domMax`, `useAnimate`, `useInView`, `useScroll`, `useSpring`, `useTransform`, `useReducedMotion`, `stagger` and the `layoutId` prop (verified in `dist/index.d.ts`) — [unpkg framer-motion@14.14.0/dist/index.d.ts](https://unpkg.com/framer-motion@14.14.0/dist/index.d.ts)
- `MotionConfig` accepts `reducedMotion?: ReducedMotionConfig`, where `type ReducedMotionConfig = "always" | "never" | "user"` (verified in `motion-dom` typings) — [unpkg framer-motion dist/index.d.ts](https://unpkg.com/framer-motion@14.14.0/dist/index.d.ts)
- `AnimateView` (from `motion/react` `./animate-view`) animates enter, exit, share and update view transitions. Its docstring says it **"Requires React and React DOM 19.3 or later"** (verified in `dist/animate-view.d.ts`) — [unpkg framer-motion@14.14.0/dist/animate-view.d.ts](https://unpkg.com/framer-motion@14.14.0/dist/animate-view.d.ts)
- React's `<ViewTransition>` component became stable in **React 19.3 (9 Sept 2026)**. The react.dev reference page still labels it Canary, which conflicts with the blog post — [React 19.3 blog](https://react.dev/blog/2026/09/09/react-19-3); [ViewTransition reference](https://react.dev/reference/react/ViewTransition)
- Browser support from the Baseline data in [web-features 3.47.0](https://www.npmjs.com/package/web-features) (Baseline "low" = newly available in all core browsers; "high" = widely available):
  - `@starting-style`: Baseline low since 2024-08-06 (Chrome 117, Firefox 129, Safari 17.5). `transition-behavior: allow-discrete` is Baseline low since 2024-08-06.
  - **Same-document View Transitions** (`document.startViewTransition`): Baseline low since **2025-10-14** (Chrome 111, Firefox 144, Safari 18). `view-transition-class`: Baseline low since 2025-10-14.
  - Cross-document view transitions: **not Baseline** (Chrome 126, Safari 18.2; no Firefox).
  - **Scroll-driven animations** (`animation-timeline`, `view-timeline`, `animation-range`): Baseline low since **2026-10-27** (Chrome 115, Firefox 159, Safari 26).
  - `sibling-index()` / `sibling-count()`: Baseline low since **2026-08-18** (Chrome 138, Firefox 154, Safari 26.2). This allows pure-CSS stagger, e.g. `transition-delay: calc(sibling-index() * 40ms)`.
  - `linear()` easing (for spring-like curves in CSS): Baseline high (2026-06-11).
  - `@property` (registered custom properties, needed to animate gradient angles or CSS counters): Baseline low since 2024-07-09.
  - `interpolate-size` / `calc-size()` (animating to `height: auto`): Chrome-only, not Baseline.
  - `individual-transforms` (`translate`, `scale`, `rotate` properties): Baseline high.
- `@number-flow/react` 0.6.2 ("A component to transition and format numbers", peer `react ^18 || ^19`) has a `respectMotionPreference: boolean` option that checks a `matchMedia` reduced-motion query (verified in the `number-flow` dist) — [npm @number-flow/react](https://www.npmjs.com/package/@number-flow/react); [unpkg number-flow@0.6.2](https://unpkg.com/number-flow@0.6.2/)
- xyflow's stylesheet animates edges with `@keyframes dashdraw` and has **no `prefers-reduced-motion` rule**, so `animated: true` edges keep moving for users who asked for reduced motion unless you override this yourself (verified in `dist/style.css`) — [unpkg @xyflow/react@13.0.3/dist/style.css](https://unpkg.com/@xyflow/react@13.0.3/dist/style.css)

### Inferences
- **Recommended split for Hakira:**
  - CSS handles hover lift (`translate`/`box-shadow` on a pseudo-element), dialog and popover entrance (`@starting-style` + `transition-behavior: allow-discrete`), list stagger and SVG stroke drawing.
  - Motion (`LazyMotion features={domAnimation} strict` + `m.div`) handles `AnimatePresence` exit animations for findings or toasts, and spring count-ups via `useSpring` + `useTransform`.
  - Load `domMax` asynchronously, and only on screens that need `layout`/`layoutId` shared-element moves such as "card expands into details".
- **Staggered list reveal:**
  - Cross-browser method that works today: set a `--i` custom property inline (`style={{'--i': index}}`) with `animation-delay: calc(var(--i) * 40ms)`.
  - `sibling-index()` became Baseline only in Aug 2026. If it's used, keep the `--i` fallback for users on older Safari or Firefox.
  - In Motion: `variants` with `transition: { delayChildren: stagger(0.04) }` on the parent. **[unverified]** the exact current syntax, since the docs were unreachable; older docs used `staggerChildren: 0.04`.
- **Number count-up:**
  - Easiest option: `@number-flow/react`, which formats through `Intl.NumberFormat` and so supports `he-IL` locales, and respects reduced motion.
  - Alternative: a Motion `useSpring` value rendered through `useTransform(v => Math.round(v))`.
  - Pure CSS: an `@property --n { syntax: '<integer>' }` plus `counter-reset: n var(--n)`, animated with a transition. Because it relies on `@property`, it works in all modern browsers.
  - In every case, put the final value in the DOM (or in `aria-label`) so screen readers don't announce intermediate values.
  - Use `font-variant-numeric: tabular-nums` (Baseline high) to prevent jitter.
- **SVG path drawing:**
  - Set `pathLength="1"` on the `<path>`, then `stroke-dasharray: 1; stroke-dashoffset: 1` and animate `stroke-dashoffset` to 0. No `getTotalLength()` call is needed.
  - Motion's `pathLength` motion value does the same declaratively.
  - Direction: drawing follows the path's own direction, not the CSS direction. For RTL, author attack-path edges from the right-hand source to the left-hand target, or flip with `transform: scaleX(-1)` only on graphics with no text.
- **View transitions on React 18:**
  - Wrap state updates as `document.startViewTransition(() => flushSync(() => setState(...)))` and give the matching elements a `view-transition-name`.
  - Feature-detect it, and skip it under `prefers-reduced-motion`.
  - The React-native `<ViewTransition>` / Motion `AnimateView` path needs an upgrade to React 19.3+. That upgrade is worth considering, because both 13.x and 14.x of the libraries above accept React 19.
- **Scroll-driven animations** became Baseline only in Oct 2026, so treat them as progressive enhancement inside `@supports (animation-timeline: view())`.
- **RTL and Motion:**
  - Motion animates physical `x`/`translateX`. A slide-in "from the start side" therefore has to flip its sign in RTL (`x: dir === 'rtl' ? 24 : -24`).
  - Alternatively, use CSS `translate` with a `--dir` multiplier (`:root[dir=rtl]{--dir:-1}`).
  - Layout animations measure bounding boxes, so they are direction-agnostic. **[unverified]**: I found no Motion documentation on RTL.

### Gaps
- motion.dev docs were unreachable, so I couldn't confirm the current `stagger()`/`delayChildren` API or Motion's own published KB figures. The figures above come from Motion's bundled size-check files, not its docs.
- I couldn't fetch a changelog for Motion 13 or 14 beyond the search snippet saying "no breaking changes".

---

## Graph / attack-path visualization (React Flow, Cytoscape.js, visx, D3, ELK/dagre)

### Takeaway
For a 3–8 node attack path with custom React-rendered nodes, animated edges and keyboard access, **`@xyflow/react` (React Flow 13, MIT)** is the best fit. Nodes are real DOM/React components, so Hebrew text, CSS tokens, focus rings and RTL text work naturally. It also ships keyboard and ARIA support. Pair it with **`@dagrejs/dagre` (MIT)** for layout, or hard-code positions for so few nodes. Avoid ELK unless EPL/GPL is acceptable.
Cytoscape.js draws to canvas, which hurts accessibility and CSS theming. With 8 nodes, a **hand-rolled SVG with `d3-shape` paths or visx** is also viable and the lightest option.

### Cited Findings
- `@xyflow/react` 13.0.3 (MIT, 2026-11-23), peer `react >=18` — [npm @xyflow/react](https://www.npmjs.com/package/@xyflow/react). Version 12 was the release that moved to the `@xyflow/react` package name (July 2024) — [React Flow 12 announcement](https://reactflow.dev/whats-new/2024-07-09)
- Measured size: `dist/index.js` is **~50 KB gzip**, plus `zustand` and `@xyflow/system` as dependencies; `dist/style.css` is ~18 KB raw. The package also ships `base.css` and `xy-theme.css` (verified in package) — [unpkg @xyflow/react@13.0.3/dist/](https://unpkg.com/@xyflow/react@13.0.3/dist/)
- **v13 theming change (verified in source):**
  - Props expose `forceColorMode?: ColorMode`, documented as "Forces a color scheme on the flow container via class name… Page-level theming is typically done by setting `data-theme` on `<html>`."
  - The stylesheet uses `light-dark()` (26 occurrences), `color-scheme`, and selectors such as `[data-theme='dark'] .react-flow` and `.dark .react-flow`.
  - Theme variables such as `--xy-edge-stroke`, `--xy-edge-stroke-selected` and `--xy-edge-stroke-width` can be overridden.
  - Sources: [unpkg src/types/component-props.ts](https://unpkg.com/@xyflow/react@13.0.3/src/types/component-props.ts), [unpkg dist/style.css](https://unpkg.com/@xyflow/react@13.0.3/dist/style.css). This replaces v12's `colorMode` prop, which I could not find in v13's ReactFlow container.
- **Accessibility props present in v13 source:**
  - `nodesFocusable`, `edgesFocusable`, `disableKeyboardA11y`, `autoPanOnNodeFocus` and `ariaLabelConfig?: Partial<AriaLabelConfig>`. Per-element props include `ariaRole` and `domAttributes`.
  - There is an `A11yDescriptions` component and a live-region `ariaLiveMessage`.
  - Default strings include `'node.a11yDescription.default': 'Press enter or space to select a node. Press delete to remove it and escape to cancel.'`. These can all be replaced with Hebrew text through `ariaLabelConfig`.
  - Arrow keys move selected nodes.
  - Sources: [unpkg @xyflow/react@13.0.3/src](https://unpkg.com/@xyflow/react@13.0.3/src/); [unpkg @xyflow/system@1.0.0](https://unpkg.com/@xyflow/system@1.0.0/dist/)
- **No RTL/`dir` prop exists in React Flow 13.** "direction" in the source refers only to keyboard nudging, pan-on-scroll and resizer directions (verified by grep). Handle `Position.Left`/`Position.Right` values are physical — [unpkg src](https://unpkg.com/@xyflow/react@13.0.3/src/). If handles move after render, the docs advise `useUpdateNodeInternals` — [React Flow handles docs](https://reactflow.dev/learn/customization/handles). I found no issue specifically about RTL — [GitHub search via WebSearch](https://github.com/xyflow/xyflow/issues/805)
- `cytoscape` 3.35.0 (MIT): `cytoscape.min.js` measured at **~138 KB gzip** (verified in package) — [unpkg cytoscape@3.35.0/dist/](https://unpkg.com/cytoscape@3.35.0/dist/)
- `elkjs` 0.12.1 is licensed **"EPL-2.0 OR GPL-3.0-or-later"**. `@dagrejs/dagre` 3.1.4 is MIT and actively published (2026-11-24); the legacy `dagre` 0.8.5 dates from 2019 — [npm elkjs](https://www.npmjs.com/package/elkjs), [npm @dagrejs/dagre](https://www.npmjs.com/package/@dagrejs/dagre), [npm dagre](https://www.npmjs.com/package/dagre)
- `@visx/*` 4.0.0 (MIT, 2026-06-11) supports React 18 and 19 — [npm @visx/shape](https://www.npmjs.com/package/@visx/shape); `d3` 7.9.2 (ISC) — [npm d3](https://www.npmjs.com/package/d3)

### Inferences
- **Recommended stack:** `@xyflow/react` with custom node types, where each node is a themed card (asset icon, Hebrew label, severity chip). Use a custom edge (`BaseEdge` + `getSmoothStepPath`/`getBezierPath`) with an SVG `<animate>`, or a CSS-animated gradient dot travelling along the path.
  - Set `nodesDraggable={false}`, `panOnDrag={false}` and `zoomOnScroll={false}` so it reads as a diagram rather than an editor.
  - Use `fitView` and `proOptions={{ hideAttribution: true }}`. **[unverified]**: the attribution can be hidden under MIT, but the maintainers ask that it be kept unless you subscribe to React Flow Pro; check the current wording on reactflow.dev.
- **RTL for the graph:**
  - Compute the layout left-to-right, e.g. dagre with `rankdir: 'LR'`, then mirror x coordinates (`x' = width - x - nodeWidth`) and swap the source and target handle positions (`Position.Right` for the source becomes `Position.Left`). The attack then flows right-to-left, matching Hebrew reading order.
  - Alternatively, use `rankdir: 'RL'` directly in dagre. **[unverified]**: dagre's RL support is documented in the dagre wiki, which I could not fetch.
  - Keep `dir="rtl"` on node content so Hebrew labels render correctly. The canvas itself is absolutely positioned and unaffected.
- **Reduced motion for edges:** add `@media (prefers-reduced-motion: reduce) { .react-flow__edge.animated path { animation: none; } }`, because the library ships no such rule.
- **Accessibility:**
  - Translate `ariaLabelConfig` into Hebrew.
  - Give the flow container `aria-label`/`role="group"`, and supply an equivalent ordered textual list of the attack steps (`<ol>`) for screen readers, either visually hidden or as a "show as list" toggle. A spatial graph is rarely self-explanatory to AT users.
  - Cytoscape's canvas output would need that text alternative entirely, and canvas nodes cannot take CSS tokens or focus rings.
- **Lightest alternative:** for a fixed 3–8 node linear or branching path, a hand-built `<svg>` with HTML cards positioned via CSS grid plus SVG connectors (using `d3-shape` `linkHorizontal`, or the `@visx/shape` `LinkHorizontal`) costs a few KB and gives full control. React Flow becomes worthwhile when pan/zoom, minimap or larger graphs are expected.
- **ELK** gives the best layered layouts, but EPL-2.0/GPL may need legal review for a commercial SaaS. dagre is enough for fewer than 10 nodes.

### Gaps
- I couldn't read the React Flow 13 release notes or migration guide (GitHub API access was not enabled; reactflow.dev was blocked). The full v12→v13 breaking-change list is unknown beyond the `colorMode`→`forceColorMode` change I confirmed in source.
- I didn't measure the visx or d3-shape tree-shaken size for a link-only use.

---

## Charts (Recharts, visx, Apache ECharts, Nivo, Tremor): gauges, radial progress, sparklines, severity bars, RTL, CSS-variable theming

### Takeaway
- **Recharts 3 (MIT)** is the pragmatic choice for SVG charts:
  - SVG output, so `fill="var(--token)"` theming works.
  - An accessibility layer is on by default.
  - The animation setting `'auto'` respects reduced motion.
  - `RadialBar`/`Pie` can serve as gauges.
- **visx 4** is the choice for bespoke, design-led gauges and sparklines with full control.
- **ECharts 6** is the most feature-rich (gauge series, themes via `setTheme`), but it is large (~368 KB gzip full), renders to canvas by default, so CSS variables must be read via JS, and has no built-in RTL.
- **Tremor**'s npm package has been dormant since Jan 2025, and its newer copy-paste components are Tailwind-based, a poor fit for a plain-CSS codebase.
- None of these libraries has a true RTL mode: mirror axes manually.

### Cited Findings
- `recharts` 3.11.1 (MIT, 2026-11-23). Its CHANGELOG now points to GitHub Releases for newer notes — [npm recharts](https://www.npmjs.com/package/recharts); [unpkg recharts@3.11.1/CHANGELOG.md](https://unpkg.com/recharts@3.11.1/CHANGELOG.md)
- Recharts typings (verified in package) — [unpkg recharts@3.11.1/types/](https://unpkg.com/recharts@3.11.1/types/):
  - `accessibilityLayer?: boolean`, `@defaultValue true`
  - `isAnimationActive?: boolean | 'auto'`, `@defaultValue auto`, documented as "the animation will be disabled in SSR and will respect the user's prefers-reduced-motion system preference"
  - `XAxis`/`YAxis` support `reversed`, `orientation` and `mirror`
  - Tooltip has `reverseDirection`
  - Polar components available: `Pie`, `RadialBar`, `Radar`, `PolarAngleAxis`, `PolarRadiusAxis`, `PolarGrid`
- Recharts CHANGELOG history mentions "Add props reversed to XAxis and YAxis", "fix position of tooltip when direction is rtl", and keyboard navigation in pie charts (2.2.0) — [unpkg CHANGELOG.md](https://unpkg.com/recharts@3.11.1/CHANGELOG.md)
- Recharts UMD bundle (everything included) measured at ~181 KB gzip. A tree-shaken ESM import of a few charts will be smaller **[not measured]** — [unpkg recharts@3.11.1/umd/](https://unpkg.com/recharts@3.11.1/umd/)
- `echarts` 6.1.0 (Apache-2.0, 2026-05-19): `dist/echarts.min.js` measured at **~368 KB gzip**. The v6 typings include `setTheme(theme: object): void` on the chart instance, so the theme can switch at runtime (verified in package). `echarts-for-react` 3.1.0 is the React wrapper — [unpkg echarts@6.1.0](https://unpkg.com/echarts@6.1.0/types/dist/echarts.d.ts); [npm echarts-for-react](https://www.npmjs.com/package/echarts-for-react)
- **ECharts has no native RTL support.** A Wikimedia task links ECharts issue #16419. A comment on issue #19609 suggests approximating RTL through option tweaks and CSS — [Wikimedia Phabricator T375575](https://phabricator.wikimedia.org/T375575); [ECharts issue #19609 comment (mail archive)](https://www.mail-archive.com/commits@echarts.apache.org/msg73369.html). AG Charts (`enableRtl: true`) is an alternative with built-in RTL — [AG Charts RTL](https://ag-grid.com/charts/react/rtl.md)
- **Tremor:**
  - Vercel acquired Tremor on 22 Jan 2025, and all Tremor products became free and open source — [Vercel blog](https://vercel.com/blog/vercel-acquires-tremor).
  - Tremor Raw is "not a component library"; its components are copied as code, and Raw Blocks "use plain Tailwind CSS" — [Tremor docs](https://tremor.so/docs/getting-started/about); [Tremor changelog](https://tremor.so/changelog).
  - The last `@tremor/react` npm release was 3.18.7 on 2025-01-13 — [npm @tremor/react](https://www.npmjs.com/package/@tremor/react).
- `@nivo/core` 0.99.0, last published 2025-05-23 — [npm @nivo/core](https://www.npmjs.com/package/@nivo/core)
- `@visx/gradient`, `@visx/pattern` and `@visx/text` are at 4.0.0 with peer React 18/19 — [npm @visx/gradient](https://www.npmjs.com/package/@visx/gradient)

### Inferences
- **Gauge / security score:** the cleanest result comes from a **hand-built SVG arc**.
  - Use two `<circle>`s with `pathLength="100"`, `stroke-dasharray` set to the score, `stroke-linecap: round`, and a `conic-gradient` or `<linearGradient>` stroke.
  - Alternatively, `@visx/shape`'s `Arc`/`Pie` with `@visx/gradient`.
  - Either way it's about 1–3 KB, fully CSS-token-themed, and animates with a CSS `stroke-dashoffset` transition. Recharts `RadialBarChart` with `startAngle`/`endAngle` is the off-the-shelf alternative.
  - In RTL, a gauge should still fill clockwise from the start side. Decide deliberately, since Hebrew users read numbers LTR, and test with native readers.
- **Sparklines:**
  - Recharts `<LineChart>` / `<AreaChart>` with no axes, or a 20-line custom SVG using `d3-shape` `line()` + `curveMonotoneX`.
  - Time axes in RTL: put the newest point on the start (right) side via `<XAxis reversed>` and `<YAxis orientation="right">`. Many Hebrew dashboards keep time running left-to-right, though, so this is a product decision.
- **Severity distribution bars:**
  - These need no chart library. Use a flex row of segments with `flex-grow: var(--count)`, `border-radius` on the first and last child via logical properties (`border-start-start-radius`), and colours from tokens.
  - This mirrors automatically in RTL and is accessible as a list with text counts.
- **CSS-variable theming:**
  - SVG libraries (Recharts, visx, custom) accept `fill="var(--sev-critical)"` / `stroke="var(--chart-grid)"`, so light and dark themes switch without re-render.
  - Canvas libraries (ECharts default renderer, Cytoscape) need values resolved via `getComputedStyle(document.documentElement).getPropertyValue('--token')` and re-applied (`chart.setTheme(...)` / `setOption`) when the theme changes.
  - ECharts' SVG renderer (`renderer: 'svg'`) is an option. **[unverified]**: I could not confirm whether `var()` strings pass through.
- **Tooltips in RTL:** render custom tooltip content with `dir="rtl"` and use `Intl.NumberFormat('he-IL')`. Wrap numbers and English CVE IDs in `<bdi>`, or use `unicode-bidi: isolate`, to stop bidi reordering.
- **Recommendation:** Recharts for standard charts, plus custom SVG for the hero gauge, radial progress and severity bar. Avoid ECharts unless chart variety later exceeds what Recharts offers, because of its size, canvas output and lack of RTL. Avoid Tremor in a non-Tailwind codebase.

### Gaps
- I didn't measure the tree-shaken size of Recharts or `echarts/core` (modular import); it needs a local bundle analysis.
- I couldn't confirm whether Recharts 3 changed tooltip or legend RTL handling after 2.x (the CHANGELOG stops at 2.x and points to GitHub Releases, which were unreachable).
- Nivo's maintenance status beyond its last publish date (May 2025) is unknown.

---

## CSS techniques for depth in dark mode, with 2026 browser support

### Takeaway
Everything needed for a "premium dark" look is now Baseline high, meaning safe without fallbacks:
- `color-mix()` and `oklch()`/`oklab()`
- CSS masks
- `border-image`
- conic gradients
- container queries
- `:has()`
- nesting
- `light-dark()`

Relative color syntax (`oklch(from var(--brand) l c h / 0.5)`), `backdrop-filter` and `@property` are Baseline low, so they work in all current browsers but need fallbacks for older Safari and Firefox. `prefers-reduced-transparency` works only in Chromium.

### Cited Findings
All support data comes from [web-features 3.47.0](https://www.npmjs.com/package/web-features), the Baseline data behind webstatus.dev. Dates are when each feature reached Baseline "low" / "high".
- **Baseline high (widely available):**
  - `color-mix()`: low 2023-05-09, high 2025-11-09 (Chrome 111, Firefox 113, Safari 16.2)
  - `oklab`/`oklch`: high 2025-11-09 (Safari 15.4)
  - **CSS masks** (`mask-image`, `mask-composite`): high 2026-06-07 (Chrome 120, Firefox 53, Safari 15.4)
  - `border-image`: high since 2019
  - `conic-gradient`: high since 2023
  - SVG filters (`feTurbulence` etc.): high since 2018
  - `light-dark()`: high 2026-11-13 (Chrome 123, Firefox 120, Safari 17.5)
  - container queries: high 2025-08-14
  - `:has()`: high 2026-06-19
  - CSS nesting: high 2026-06-11
  - logical properties: high since 2024-03-20
  - `text-wrap: balance`: high 2026-11-13
  - `prefers-contrast`: high
  - `forced-colors`: high
  - `font-variant-numeric`: high
- **Baseline low (newly available):**
  - **relative color syntax**: 2024-09-16 (Chrome 125, Firefox 128, Safari 18)
  - **`backdrop-filter`**: 2024-09-16 (unprefixed in Safari 18; Chrome 76, Firefox 103)
  - `@property`: 2024-07-09 (Firefox 128)
  - `contrast-color()`: 2026-04-10 (Chrome 147, Firefox 146, Safari 26)
  - `content-visibility`: 2025-09-15
  - `popover`: 2025-01-27
  - `scrollbar-gutter`: 2024-12-11
  - `shape()`: 2026-02-24
- **Not Baseline:**
  - `prefers-reduced-transparency`: Chromium 119+ only
  - `corner-shape`: Chromium 139 only
  - `interpolate-size`/`calc-size()`: Chromium only
  - CSS `if()`: Chromium only
  - anchor positioning: Chrome 157 and Safari 27, no Firefox in the dataset
  - `text-box`: Chrome 133 and Safari 18.2
- `prefers-reduced-transparency` maps to OS settings such as macOS System Settings › Accessibility › Display › Reduce transparency — [MDN prefers-reduced-transparency](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-transparency); [Chrome blog](https://developer.chrome.com/blog/css-prefers-reduced-transparency)
- **Glass guidance:**
  - Contrast is the core accessibility risk of translucent, blurred surfaces.
  - Recommended practice: an opaque base background, translucent styles inside `@supports (backdrop-filter: blur(1px))`, and a near-opaque override with `backdrop-filter: none` under `prefers-reduced-transparency: reduce`.
  - Test contrast against the *most translucent* state.
  - Sources: [Axess Lab: Glassmorphism meets accessibility](https://axesslab.com/?p=5111); [NN/g Glassmorphism](https://www.nngroup.com/articles/glassmorphism/)
- React Flow 13's own stylesheet already relies on `light-dark()` + `color-scheme`, which shows the approach is mainstream (verified) — [unpkg @xyflow/react@13.0.3/dist/style.css](https://unpkg.com/@xyflow/react@13.0.3/dist/style.css)

### Inferences
The snippets below are standard techniques from prior knowledge. Their *support* is cited above; the snippets themselves were not re-fetched from MDN this session.
- **Layered surfaces via tokens:**
  - Define `--surface-0..4` in `oklch`, raising lightness (L) by about 0.03–0.04 per elevation level in dark mode, e.g. `oklch(0.17 0.02 265)` up to `oklch(0.29 0.02 265)`.
  - Derive tints with `color-mix(in oklch, var(--brand) 12%, var(--surface-2))`. OKLCH keeps perceived lightness uniform across hues, which makes severity colours (critical/high/medium/low) feel equally weighted.
  - Use `light-dark(lightValue, darkValue)` under `color-scheme: light dark`, or keep the existing `[data-theme=dark]` token override (it matches React Flow's selector).
- **Gradient borders**, three options:
  - (1) `border: 1px solid transparent; background: linear-gradient(var(--surface-2) 0 0) padding-box, linear-gradient(135deg, var(--brand), transparent 60%) border-box;`. Works with `border-radius`, which `border-image` does not.
  - (2) A `::before` with `padding: 1px`, a gradient background, and `mask: linear-gradient(#000 0 0) content-box exclude, linear-gradient(#000 0 0)` (or `-webkit-mask-composite: xor`). This allows a rotating `conic-gradient` with `@property --angle` for an animated "scanning" border.
  - (3) `border-image` only for square corners.
  - RTL: rewrite gradient angles to logical intent. There is no logical gradient direction, so mirror the angle under `:dir(rtl)`, e.g. `135deg` becomes `225deg`.
- **Inner highlight:** `box-shadow: inset 0 1px 0 0 color-mix(in oklch, white 8%, transparent), 0 1px 2px oklch(0 0 0 / .4), 0 8px 24px -8px oklch(0 0 0 / .5);`. A top-edge 1px highlight plus layered soft shadows gives a "lit from above" look. In dark mode, rely more on lighter surfaces and the highlight than on shadows.
- **Subtle radial glow:** `background: radial-gradient(120% 80% at 50% -20%, color-mix(in oklch, var(--brand) 18%, transparent), transparent 60%), var(--surface-1);` on hero or score cards. Positions are physical; use `at 100% 0` vs `at 0 0` per direction if asymmetric.
- **Noise texture:**
  - Inline SVG data URI: `<filter id='n'><feTurbulence type='fractalNoise' baseFrequency='.8' numOctaves='3' stitchTiles='stitch'/></filter><rect width='100%' height='100%' filter='url(#n)' opacity='.05'/>`. Apply as `background-image` on a `::after` with `pointer-events: none; mix-blend-mode: overlay`.
  - Keep opacity at 3–6% to avoid banding while keeping text crisp.
  - Pre-rendering to a small PNG tile avoids per-paint filter cost.
- **backdrop-filter:** limit it to sticky headers, command palette and modals, not every card, because each blurred layer costs GPU work on scroll. Keep an opaque fallback, and add `-webkit-backdrop-filter` for Safari before 18.
- **Severity text on tinted backgrounds:** `contrast-color()` is only Baseline low since 2026-04, so precompute accessible text colours per token rather than relying on it.

### Gaps
- I couldn't fetch MDN or web.dev articles for code-level verification of the mask-composite and feTurbulence snippets. They are well-established techniques, but the report should present them as recipes to test.
- I have no measured GPU or paint-cost data for `backdrop-filter` on low-end devices.

---

## Accessibility and performance (reduced motion, contrast with gradients/glass, layout shift, GPU-friendly properties)

### Takeaway
- Gate all non-essential motion behind `prefers-reduced-motion` (Baseline high), and wire that one preference through CSS, Motion (`<MotionConfig reducedMotion="user">`), Recharts (`isAnimationActive="auto"`, the default), NumberFlow (`respectMotionPreference`) and React Flow edges (manual CSS override needed).
- Animate only `transform`/`translate`/`scale`/`opacity`/`filter`.
- Reserve space for charts and graphs to avoid CLS.
- Check contrast on the worst-case translucent state.

### Cited Findings
- `prefers-reduced-motion`: Baseline high since 2022-07-15. `prefers-contrast` and `forced-colors` are Baseline high. `prefers-reduced-transparency` is Chromium-only — [web-features 3.47.0](https://www.npmjs.com/package/web-features)
- Motion `MotionConfig.reducedMotion` takes `"always" | "never" | "user"` (verified) — [unpkg framer-motion@14.14.0](https://unpkg.com/framer-motion@14.14.0/dist/index.d.ts)
- Recharts `isAnimationActive` defaults to `'auto'`, which respects `prefers-reduced-motion`. `accessibilityLayer` defaults to `true` (verified) — [unpkg recharts@3.11.1/types](https://unpkg.com/recharts@3.11.1/types/)
- React Flow's CSS has no reduced-motion rule for animated edges (verified) — [unpkg @xyflow/react@13.0.3/dist/style.css](https://unpkg.com/@xyflow/react@13.0.3/dist/style.css)
- Translucent and blurred surfaces frequently fail contrast against busy backgrounds. Provide fallbacks and test the lowest-alpha state — [Axess Lab](https://axesslab.com/?p=5111); [NN/g](https://www.nngroup.com/articles/glassmorphism/)
- `content-visibility` became Baseline low on 2025-09-15, which helps long findings lists offscreen. Individual transform properties are Baseline high — [web-features 3.47.0](https://www.npmjs.com/package/web-features)

### Inferences
- **WCAG targets** (well-known criteria, not re-fetched; see [WCAG 2.2](https://www.w3.org/TR/WCAG22/)):
  - 1.4.3 text contrast: 4.5:1 normal, 3:1 large
  - 1.4.11 non-text contrast: 3:1 for chart marks, focus rings, gauge tracks and severity segments against their surface
  - 2.2.2 Pause, Stop, Hide: auto-playing motion longer than 5 s (a perpetually animated attack-path edge, a looping "scan" border) needs a way to stop it, or should stop on its own
  - 2.3.3 Animation from Interactions (AAA): honour reduced motion
- **Do not rely on colour alone for severity:** add a text label or icon, which matters even more with gradients.
- **One global rule plus per-library wiring:** `@media (prefers-reduced-motion: reduce){ *,*::before,*::after{ animation-duration:.01ms!important; animation-iteration-count:1!important; transition-duration:.01ms!important; scroll-behavior:auto!important } }`, plus the library hooks listed above. Under reduced motion, prefer cross-fades over removing all feedback.
- **CLS:**
  - Give every chart, gauge and flow container explicit `block-size`/`aspect-ratio`. React Flow and ResponsiveContainer measure their parent, so a zero-height parent collapses.
  - Use skeletons with the same box size.
  - Use `font-variant-numeric: tabular-nums` for counters.
  - Load the Hebrew webfont with `font-display: swap` plus `size-adjust`/`ascent-override` metric overrides. **[unverified]**: no specific Hebrew-font data was gathered.
- **GPU-friendly:**
  - Animate `transform`, `opacity` and `clip-path` (usually composited). Animating `stroke-dashoffset` triggers paint, not layout, which is fine for small SVGs.
  - Avoid animating `box-shadow`, `filter: blur()` on large areas, `width`/`height`, `top`/`left`. For hover elevation, fade the opacity of a pre-rendered shadow on a pseudo-element.
  - Use `will-change` sparingly and only while animating.
- **Performance budget:**
  - Motion via LazyMotion + `domAnimation`: ~30 KB gzip
  - React Flow: ~50 KB gzip plus zustand
  - Recharts: tree-shaken, size unmeasured
  - Lazy-load the attack-path view and charts with `React.lazy` + Vite code-splitting so the first dashboard paint isn't blocked.

### Gaps
- I didn't fetch web.dev's CLS/INP guidance or MDN's compositing guidance this session. The GPU property list is standard practice from prior knowledge.
- I have no data on screen-reader behaviour with React Flow's Hebrew `ariaLabelConfig` overrides (needs manual testing with NVDA/VoiceOver in Hebrew).

---

## Component libraries that can be themed to a custom brand (Radix Primitives / Radix Themes, Ark UI, React Aria) and RTL

### Takeaway
For a custom-branded, plain-CSS codebase, use **unstyled primitives**: `radix-ui` (unified package, MIT), `react-aria-components` (Apache-2.0) or `@ark-ui/react` (MIT). Styling them with Hakira's own tokens is what keeps the result from looking generic.
All three support RTL through a provider plus `dir="rtl"` on `<html>`:
- Radix: `Direction.Provider dir="rtl"`
- React Aria: `I18nProvider locale="he-IL"`, which flips arrow-key navigation and localises dates and numbers
- Ark UI: a `LocaleProvider` (present in the package)

React Aria has the deepest i18n (Hebrew calendars and date fields, bidi-aware number formatting). Radix Themes is a pre-styled system, harder to make distinctive.

### Cited Findings
- `radix-ui` 1.8.1 (MIT, 2026-10-12) re-exports the Direction utility as `export { reactDirection as Direction }` from `@radix-ui/react-direction` 1.2.0 (verified in `dist/index.d.ts`) — [unpkg radix-ui@1.8.1/dist/index.d.ts](https://unpkg.com/radix-ui@1.8.1/dist/index.d.ts); [npm radix-ui](https://www.npmjs.com/package/radix-ui)
- Radix docs: wrap the app in `Direction.Provider` so primitives (popovers, sliders and so on) follow reading direction. The provider is separate from the HTML `dir` attribute, which the app must still set — [Radix Direction Provider docs](https://www.radix-ui.com/docs/primitives/utilities/direction-provider); [shadcn RTL (Vite)](https://ui.shadcn.com/docs/rtl/vite)
- `@radix-ui/themes` 3.3.0 (MIT) was last published 2026-01-31, the previous release being 3.2.1 (Feb 2025). The release cadence is slow — [npm @radix-ui/themes](https://www.npmjs.com/package/@radix-ui/themes)
- React Aria: `I18nProvider` sets the locale for descendants, and `useLocale()` returns `{ locale, direction }`. Set `lang`/`dir` on the root element. React Aria flips arrow-key navigation automatically in RTL, but visual mirroring is the app's job because it ships no styles. Prefer CSS logical properties — [React Aria Internationalization](https://react-spectrum.adobe.com/react-aria/internationalization.html); [I18nProvider](https://react-aria.adobe.com/I18nProvider); [React Aria blog on RTL date/time](https://react-aria.adobe.com/blog/rtl-date-time)
- `react-aria-components` 1.22.1 (Apache-2.0, 2026-10-09) — [npm](https://www.npmjs.com/package/react-aria-components)
- `@ark-ui/react` 5.40.1 (MIT, 2026-11-23) ships a `providers/` directory containing `environment`, `locale` and `interaction` providers (verified in package) — [unpkg @ark-ui/react@5.40.1/dist/providers/](https://unpkg.com/@ark-ui/react@5.40.1/dist/providers/)
- Base UI also documents a direction provider, noting that the `dir="rtl"` attribute must be added by application code — [Base UI direction provider](https://base-ui.com/react/utils/direction-provider.md)

### Inferences
- **Recommended:** Radix Primitives (`radix-ui`) for dialog, popover, tooltip, tabs, dropdown, toggle-group and scroll-area. It is lightweight and widely used, and its `data-state` attributes pair well with CSS `@starting-style` / keyframe enter and exit animations.
  - Use React Aria Components instead if Hakira needs strong date pickers or ranges (Hebrew calendar) or grid/table keyboard models. Its `data-entering`/`data-exiting` render props also support CSS animations.
  - Avoid mixing two primitive libraries for the same widget type.
- **RTL wiring:**
  - Set `<html lang="he" dir="rtl">`, wrap the app in `<Direction.Provider dir="rtl">` (Radix) and/or `<I18nProvider locale="he-IL">` (React Aria), and keep the two values in sync from one source.
  - Write all component CSS with logical properties: `margin-inline-start`, `inset-inline-end`, `padding-inline`, `border-start-start-radius`, `text-align: start`.
  - Use the `:dir(rtl)` pseudo-class (**[unverified]** Baseline status; I didn't query it) or `[dir=rtl]` for the rare physical overrides: directional icons (chevrons, arrows), gradient angles, Motion `x` offsets, React Flow handle positions.
- **Avoiding a generic look:** the primitives are unstyled, so distinctiveness comes from the token layer (oklch surfaces, gradient borders, glow and noise), motion choreography and data-viz styling, not from the component library. Radix Themes is the opposite trade-off: fast, but recognisably "Radix" unless heavily overridden, and its release cadence is slow.

### Gaps
- I couldn't reach the Radix Themes docs to confirm whether `<Theme>` has its own `dir` handling.
- I didn't verify the Ark UI `LocaleProvider` prop names (`locale="he-IL"`) against its docs; only the provider's presence in the package is confirmed.
- I didn't query the Baseline status of `:dir()`.
