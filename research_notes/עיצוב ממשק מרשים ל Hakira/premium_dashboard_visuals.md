# What Makes Security and SaaS Dashboards Look Premium in 2025-2026 (for Hakira, Ink & Lime, RTL)

Research method note: Web search worked, but WebFetch was blocked in this session for linear.app, wiz.io, nngroup.com, en.globes.co.il and docs.cloud.google.com (DNS not allowed). Facts below therefore come from search-result summaries of those pages, not full-page reads. Claims are attributed to the page named in the result. Anything not stated by a source is in "Inferences" and is my own design reasoning. No vendor hex codes are given unless a source stated them, and unofficial ones are flagged.

## 1. Which products are praised for visual design, and which elements create the premium feel?

### Takeaway
The best-documented "premium" references are Linear (perceptual LCH color system, layered surfaces, a dimmed sidebar so content stands out, Inter Display headings), Vercel Geist (high-contrast, accessible semantic colors, tokenized "materials" for radii, fills, strokes and shadows) and Wiz (a deliberately optimistic, magical brand with illustration that "talks about risk without inducing panic"). Security vendors (CrowdStrike, Palo Alto, SentinelOne, Vanta, Drata, Aikido) are praised mostly for clarity and unification, not documented visual specifics. Their public design detail is thin.

### Cited Findings
**Linear**
- Linear rebuilt theme generation in the LCH color space instead of HSL. This makes it possible "to generate more consistently good-looking themes, regardless of which base colors are used", and in the refresh they started using it for the main light and dark themes, not only custom themes. LCH was kept because it tracks human perception and handles surface elevation levels such as backgrounds, panels and dialogs. — [Linear: How we redesigned the Linear UI](https://linear.app/now/how-we-redesigned-the-linear-ui)
- Linear built an internal theme editor with controls for the hue, chroma and lightness of individual design tokens. — [Linear: Behind the latest design refresh](https://linear.app/blog/behind-the-latest-design-refresh)
- Linear uses Inter Display for headings and regular Inter for the rest of the text. — [Linear: How we redesigned the Linear UI](https://linear.app/blog/how-we-redesigned-the-linear-ui)
- A companion post describes softer borders and subtler visual separation in the updated dark interface. — [Linear: A design reset](https://linear.app/blog/a-design-reset)
- Linear's March 2026 UI refresh changelog says the navigation sidebars are "slightly dimmer, allowing the main content area to stand out". — [Linear changelog 2026-03-12 UI refresh](https://linear.app/changelog/2026-03-12-ui-refresh)
- A 2026 third-party analysis frames the Linear look as tokens plus density plus keyboard-first UX. Not opened, so the title only. — [BuildMVPFast: The Linear Aesthetic, Decoded](https://www.buildmvpfast.com/blog/linear-aesthetic-tokens-density-keyboard-first-ux-2026)

**Vercel Geist**
- Geist calls its colors "a high contrast, accessible color system". All semantic colors, including the bright variants, meet a minimum 4.5:1 contrast ratio, and the docs show the ratio measured against #FBFBFA. A "materials" section defines presets for radii, fills, strokes and shadows. — [Vercel Geist Design System](https://vercel.com/geist)
- Unofficial community write-ups describe Vercel's style as near-black #171717 on near-white #fafafa, with blue (#0070f3) reserved for links and focus, plus a hero-scale multi-color mesh gradient. These values are NOT official tokens. — [shadcn.io Vercel-inspired design](https://www.shadcn.io/design/vercel); [oh-my-opencode Vercel reference](https://cdn.jsdelivr.net/npm/oh-my-opencode@4.18.2/dist/skills/frontend/references/design/vercel.md)

**Wiz**
- Wiz's blog says the idea behind the brand "was not to reflect a traditional cloud security brand, but to provide an exciting, innovative, magical, and special experience". — [Wiz: The Magic of Branding](https://www.wiz.io/blog/the-magic-of-branding)
- Wiz brand chief Roy Katz: thanks to the illustration style, "he can talk about risk without inducing panic and simplify a lot of complexities". — [Globes: How branding helped drive Wiz's $32 billion exit](https://en.globes.co.il/en/article-how-branding-helped-drive-wizs-32-billion-exit-1001517931)
- A brand audit lists Wiz's recurring assets: a 4-pointed teal spark, a cloud device, a node-graph UI, the verbal anchor "build and run", and a crystal-ball illustration tied to a playful "wizard" streak. — [STFO brand audit: Wiz](https://www.stfo.io/research/audits/wiz/)

**Security platforms (feature and UX claims, little visual detail)**
- CrowdStrike unveiled a persona-aware, "AI-powered" Falcon console at Fal.Con 2025 that turns natural-language requests into dashboards tailored to each user, from analysts to CISOs, and brings hybrid and multi-cloud assets into one view. It began in public preview for Falcon Cloud Security and Exposure Management. — [CrowdStrike: New User Experience Transforms Interaction with the Falcon Platform](https://www.crowdstrike.com/en-us/blog/crowdstrike-transforms-falcon-ux-charlotte-ai); [CrowdStrike Fall 2025 release](https://www.crowdstrike.com/en-us/blog/crowdstrike-fall-2025-release-defines-agentic-soc-secures-ai-era)
- Cortex XSIAM 3.0 (April 2025) introduced a "Cloud & SOC Command Center", a single UI for unified enterprise and cloud visibility. — [Palo Alto: Introducing XSIAM 3.0](https://www.paloaltonetworks.com/blog/2025/04/introducing-cortex-xsiam-3-dot-0/)
- Palo Alto's July 2025 UX piece recommends a "breadth-first" approach: users see a high-level view before drilling down. — [Palo Alto: Security by Design — UX and AI](https://www.paloaltonetworks.com/blog/2025/07/security-by-design-ux-ai-modern-cybersecurity/)
- Purple AI pages describe it delivering an investigation verdict. No visual specifics were found. — [SentinelOne Purple AI](https://www.sentinelone.com/platform/purple/)
- Aikido reviewers call the interface "super clean and easy to use", with "top-level critical security issues front and center". They say it is usable by team members "not deeply specialized in security" and that it auto-prioritizes issues and estimates fix times. These are user reviews, not design evaluations. — [G2: Aikido Security reviews](https://g2.com/products/aikido-security/reviews)
- G2 reviewers say Vanta makes compliance status easy to track without overload. Drata's dashboard shows overall control and requirement readiness, and a reviewer calls it clear for technical and non-technical stakeholders. Vanta lets customers brand their Trust Center with header images and typography. — [G2: Vanta vs Drata](https://www.g2.com/compare/vanta-vs-drata); [Vanta Trust Center](https://www.vanta.com/products/trust-center)

### Inferences
- The "premium" common denominator is a systematic token layer, not decoration. That means perceptual color (LCH/OKLCH), a few elevation steps, softened borders, a quiet chrome (sidebar) so content wins, and a display face for headings. For Hakira: generate the ink-and-lime ramps in OKLCH and dim the sidebar a step below the canvas. Use a display cut, or heavier weight, of the Hebrew typeface for the score and the headings.
- Wiz shows that a security brand can be optimistic and magical and still be trusted. That fits Hakira's small-business audience better than SOC-style "threat red" aesthetics.
- Aikido's praise (critical issues "front and center", fix-time estimates, usable by non-specialists) is the closest analogue to Hakira's audience. An "estimated fix time" chip per finding is a cheap, high-value detail.

### Gaps
- I could not open screenshots or design posts for Wiz's product UI, Orca, Snyk, Raycast or Charlotte AI, so there is no verified visual detail (colors, layout) for them.
- I found no 2025 design write-up from Vercel about its dashboard redesign.

## 2. Attack-path and security-graph visualization: how leaders draw it and make it readable

### Takeaway
Leading tools converge on a graph of assets, identities and vulnerabilities. They highlight "toxic combinations" and "choke points" (nodes where paths converge), attach a severity score to each path, pair the graph with a plain-language explanation and timeline, and deprioritize non-viable paths. The most explicit visual rule found is Google SCC's: a yellow border for nodes that contribute to a toxic combination and a red border for chokepoints.

### Cited Findings
- Wiz describes attack path analysis as mapping routes an attacker could take to critical assets. A graph model visualizes the relationships between resources, permissions and vulnerabilities, and findings include automatic root-cause and "blast radius" analysis. — [Wiz Academy: Attack path analysis](https://www.wiz.io/academy/detection-and-response/attack-path-analysis)
- Wiz layers runtime signals into the Security Graph to expose hidden attack paths. Because it uses a single graph database for all clouds, it can find cross-account and cross-cloud paths. — [Wiz: Uncovering Hidden Attack Paths Using Runtime Signals](https://www.wiz.io/fr-fr/authors/omri-shoham); [Wiz Security Graph](https://www.wiz.io/fr-fr/lp/wiz-security-graph)
- In Orca, each attack-path alert includes a graph visualization of the path, a short explanation and a timeline of events. Each path gets a numeric severity score and is prioritized by it. — [Orca Attack Path Analysis (PDF, May 2025)](https://orca.security/wp-content/uploads/2025/05/Orca-Attack-Path-Analysis-Digital.pdf); [Orca glossary](https://orca.security/glossary/attack-path-analysis/)
- XM Cyber's attack graph highlights choke points where multiple paths converge on critical assets and deprioritizes non-viable paths. — [XM Cyber attack graph analysis](https://xmcyber.com/platform/attack-graph-analysis/)
- Google Security Command Center gives nodes that contribute to a toxic combination a yellow border and chokepoints a red border. — [Google Cloud: Toxic combinations and chokepoints overview](https://docs.cloud.google.com/security-command-center/docs/toxic-combinations-overview)
- Microsoft Defender's attack path view shows multiple paths and "choke points, nodes that create bottlenecks in the graph or map where attack paths converge", and groups choke-point nodes. — [Microsoft Learn: Attack paths overview](https://learn.microsoft.com/security-exposure-management/work-attack-paths-overview)
- Rapid7 says attack-path visualizations aimed at non-technical stakeholders should be easy to read and should communicate impact. — [Rapid7: Toxic combinations with attack path analysis](https://www.rapid7.com/blog/post/2023/06/27/uncover-and-remediate-toxic-combinations-with-attack-path-analysis/)

### Inferences
- Hakira's "attack story" maps onto these patterns. The "break point" is equivalent to a choke point: the one node where fixing breaks the chain. Give it its own treatment, such as a lime ring or halo, with the rest of the path dimmed when it is focused, so the brand accent equals "the fix". Keep a warning hue, not lime, for the toxic or risky nodes so lime keeps meaning "safe, act here".
- For non-experts, a linear, left-to-right (in RTL, right-to-left) storyboard of 3-6 steps is more readable than a free force-directed graph. Each step is a card with an icon, a one-line plain-Hebrew sentence and a "verified" evidence chip. The edges between steps are labeled verbs ("exposed to", "allows", "leads to"). This follows Orca's graph + explanation + timeline triad.
- Motion that fits: draw the path edge by edge (stroke-dashoffset) once on first view. Then "cut" the edge at the break point when the user hovers or selects the fix, with a short snap and the downstream nodes fading to a neutral or safe state. The meaning: fixing this one item stops the whole story. Respect `prefers-reduced-motion` by showing the final state.
- Focus states: hover or select a node to highlight its incoming and outgoing edges, dim the others to about 30-40% opacity, and open a side panel with the evidence. In RTL, put the panel on the left (the inline-end side).
- Add a small blast-radius summary at the end node ("what the attacker reaches", for example customer data or email), borrowing Wiz's framing.

### Gaps
- I found no verified descriptions of Wiz's or Orca's exact node and edge styling, icon set, animation or zoom/pan behavior. The only explicit color rules found are Google SCC's yellow and red borders.

## 3. Hero moments: score reveals, gauges, "scan in progress", onboarding, empty states

### Takeaway
There is little published critique of score reveals specifically. The strongest evidence is behavioral: the "labor illusion" research shows that visibly showing the real work a system is doing raises perceived value, and that opaque waiting can hurt. Animated score rings with count-up are a common pattern, and good implementations respect reduced motion.

### Cited Findings
- Buell & Norton, "The Labor Illusion" (Management Science, 2011): when websites signal effort, people can prefer longer waits to instant results, even when the results are identical. Across five experiments, the effect is partly attributed to reciprocity. — [INFORMS: The Labor Illusion](https://pubsonline.informs.org/doi/references/10.1287/mnsc.1110.1376)
- Secondary write-ups report that the visible effort has to match the real processing, and that in a "blind progress bar" condition perceived value dropped over time. A HubSpot article cites an 8.1% value uplift, which I could not verify against the paper. — [HubSpot: Why AI shows it's working](https://blog.hubspot.com/marketing/why-ai-shows-loadtime); [Harvard Berkman Klein: Why progress bars can make you feel better](https://cyber.harvard.edu/story/2019-12/why-progress-bars-can-make-you-feel-better)
- One open-source score-ring component draws a 0-100 arc and counts up on mount with easing. Under `prefers-reduced-motion` it shows the final value instantly. — [21st.dev Score Ring](https://21st.dev/@forgedstep/components/score-ring)
- Risk and credit-score gauge animations commonly pair an arc fill or needle with a color transition and highlight improvements. These are marketing and demo assets, not usability evidence. — [DEV: Fraud risk gauge SVG needle GSAP](https://dev.to/vlad12k/fraud-risk-gauge-svg-needle-gsap-2c85); [LottieFiles credit score pack](https://lottiefiles.com/marketplace/credit-score-animation-pack_333219)
- Palo Alto's "breadth-first" principle (overview first, then drill down) supports a single dominant hero metric at the top. — [Palo Alto: Security by Design](https://www.paloaltonetworks.com/blog/2025/07/security-by-design-ux-ai-modern-cybersecurity/)

### Inferences
- Scan in progress is Hakira's biggest wow opportunity, backed by the labor illusion. Show a live, truthful checklist of what is being checked (domain, email records, exposed services, leaked credentials and so on). Each line ticks to "checked" with a verified, failed or clean state, findings "drop" into a counter as they are verified, and a thin lime progress line runs along the top. Never fake steps.
- Score reveal: count up over about 0.8-1.2 s with an ease-out curve. Draw the ring at the same time, then settle with a subtle single pulse of the ring, with no looping glow. Immediately show the delta vs the last scan and a one-sentence "what this means" line. Skip the animation on repeat visits, and play it only on first reveal after a new scan.
- Empty and clean states: "No exposure found in X" should feel like a reward, for example a small branded illustration plus lime accent, not a grey void. Empty findings before the first scan should be a call-to-action with a preview of what the scan will check.

### Gaps
- I found no UX research or authoritative critique on whether count-up reveals read as premium or gimmicky. Durations above are inferred from the general motion guidance in section 5.
- I could not verify onboarding flows of Wiz, Vanta or Aikido.

## 4. Depth and layering in dark UIs: elevation, gradients, inner highlights, glow, grain, glass

### Takeaway
Elevation in dark UI comes from lighter surfaces, not shadows, and never from pure black. Linear explicitly uses its LCH system to step elevation levels. Grain works at very low opacity (about 0.03-0.08) and needs dark-specific tuning. Inner top highlights (`inset 0 1px 0`) are the standard subtle "edge light". Glass is risky for legibility and should be limited to overlays.

### Cited Findings
- Material dark theme: higher elevation means a lighter surface, made by placing a semi-transparent white overlay over the surface. It suggests #121212 as the base dark surface, and calls for at least 15.8:1 contrast between 100%-white body text and the surface. This is Material 2, older guidance. — [Material Design 2: Dark theme](https://m2.material.io/design/color/dark-theme)
- Shadows are hard to see in dark mode, so practitioners use lighter shades of the background for elevation. Avoid pure #000000 for backgrounds. Use lighter, desaturated accents because saturated colors "vibrate" on dark surfaces. — [Toptal: Dark UI design](https://www.toptal.com/designers/ui/dark-ui-design); [LogRocket: Dark mode UI best practices](https://blog.logrocket.com/ux-design/dark-mode-ui-design-best-practices-and-examples/)
- Linear uses LCH partly because it handles surface elevation levels (background, panels, dialogs). — [Linear: How we redesigned the Linear UI](https://linear.app/now/how-we-redesigned-the-linear-ui)
- Grain: one guide recommends 0.03-0.08 opacity for most UIs and about 0.05 for dark UIs with light grain, and says the `screen` blend lightens, which suits dark UIs. — [Empire UI: Grain & Noise Texture in CSS](https://empire-ui.com/blog/grain-texture-css)
- CodeFronts warns that grain that looks refined on light surfaces looks like "a dirty screen" on dark ones. It recommends two grain weights, `soft-light` instead of `overlay`, and a mask that keeps noise out of the deepest shadows. It also says grain weight should climb with elevation. — [CodeFronts: Dark Mode Noise Without Muddy Shadows](https://codefronts.com/design-styles/css-grain-texture/dark-mode-noise-without-muddy-shadows/)
- A tactile-card example adds an inset top highlight via `box-shadow: inset 0 1px 0 ...`. The common implementation is an SVG `feTurbulence` data URI on a `::before`/`::after` pseudo-element with `mix-blend-mode` and `pointer-events: none`. — [CodeFronts: Tactile card surface with subtle noise](https://codefronts.com/design-styles/css-grain-texture/tactile-card-surface-with-subtle-noise/); [webdevpuneet: Noise grain background](https://webdevpuneet.com/ui-snippets/noise-background/)
- Glass: the core problem is text contrast on blurred, semi-transparent surfaces. NN/g says glassmorphism helps hierarchy but, if overused or without solid visual-design grounding, causes accessibility and usability problems. Ramotion advises applying it only to cards, overlays and priority elements, and keeping solid surfaces where readability matters. — [NN/g: Glassmorphism](https://www.nngroup.com/articles/glassmorphism/); [Axess Lab: Glassmorphism meets accessibility](https://axesslab.com/?p=5111); [Ramotion: What is glassmorphism](https://www.ramotion.com/blog/what-is-glassmorphism/)
- Apple's WWDC 2025 "Liquid Glass" drew public criticism from designers on aesthetics and accessibility. — [UX Collective: Liquid Glass isn't a design failure](https://uxdesign.cc/liquid-glass-isnt-a-design-failure-it-is-apple-s-most-tactile-digital-future-yet-091abade02b3)

### Inferences (Ink & Lime recipe; values to tune, not sourced)
- Canvas: Hakira ink #16211D is already a non-black, slightly green-tinted dark, which fits the "avoid pure black" guidance. Build 3-4 surface steps by raising OKLCH lightness in small increments while keeping the ink hue: canvas, then card, then raised or popover, then modal. Sidebar one step darker or dimmer than canvas, in the Linear 2026 style.
- Cards: 1px border at low-alpha white (hairline), plus `inset 0 1px 0` with a slightly brighter low-alpha white for a top "edge light". No drop shadow in dark mode. In light mode use soft, tinted ink shadows instead.
- Glow: reserve lime glow for exactly one thing per screen, for example the score ring's progress cap or the break-point node. Use a soft, low-alpha radial behind it, not neon text-shadow. Lime #B4F06C is light and saturated, so on dark backgrounds use it for fills, strokes and large numerals. Avoid long lime body text, which risks the "vibration" the sources describe. In the light theme, lime on white likely fails contrast for text, so use ink text on lime fills or a darker lime step.
- Subtle gradients: a very faint radial lime-to-transparent "aura" behind the hero score, or a top-of-page vertical gradient from a slightly lighter ink, gives depth without template-y mesh gradients.
- Grain: an optional ~0.03-0.05 grain on hero surfaces only (score card, scan screen), never on tables.
- Glass: only for sticky headers or command palette overlays, with a high-opacity tint (mostly solid). Never behind findings text.

### Gaps
- I found no authoritative source stating exact elevation lightness steps for 2025 products (Linear's internal values are not published in the results).

## 5. Motion and micro-interactions: premium vs gimmicky; durations and easings

### Takeaway
Sources cluster on 100-300 ms for micro-interactions and 100-500 ms overall, with ease-out for entering elements. Premium motion is short, purposeful, explains state changes (path draws, score settles, items stagger in once), and respects reduced motion. Gimmicky motion loops, delays content or animates everything.

### Cited Findings
- NN/g: most UI animations should fall in roughly 100-500 ms depending on complexity and distance travelled. Larger changes such as a modal can use about 200-300 ms. Ease-in and ease-in-out can feel unresponsive for some transitions, which points to ease-out for entrances. — [NN/g: Executing UX Animations: Duration](https://nngroup.com/articles/animation-duration)
- Toyota's design system: 100 ms for icon transforms and micro-interactions, 200 ms for hover states and small toggles. Colorado's digital guidelines: micro-interactions can be as short as 100 ms. A third-party motion reference suggests 90-150 ms for hover and press. — [Toyota Europe DX playbook: Animations](https://dx-playbook.toyota-europe.com/cds/foundations/animations/); [Colorado Digital Guidelines: Motion](https://dcs.colorado.gov/ids/digital-guidelines/design-tokens/motion-interaction); [Refero motion reference](https://raw.githubusercontent.com/referodesign/refero_skill/f78b4eccf112d7a179b92afeafdd7e8684560ac2/references/motion.md)
- Material: acceleration and deceleration should be smooth so movement doesn't look mechanical. — [Material Design: Duration & easing](https://m1.material.io/motion/duration-easing.html)
- Score animations should fall back to the final value instantly under `prefers-reduced-motion`. — [21st.dev Score Ring](https://21st.dev/@forgedstep/components/score-ring)

### Inferences
- Suggested Hakira motion tokens (inferred from the above): `fast` 120 ms (hover, press), `base` 200 ms (toggles, tabs, tooltips), `slow` 300 ms (panels, modals), `hero` 800-1200 ms (score count-up and ring draw, attack-path draw, once only). Use ease-out cubic-bezier curves for entrances and slightly faster exits.
- Stagger reveals of findings cards at about 30-50 ms per item, capped at the first ~8 items so long lists don't feel slow.
- Number count-ups only for the hero score and the "findings verified" counter, not for every KPI.
- In RTL, directional motion (slide-ins, path drawing, progress) must flow right-to-left. Mirror any x-axis translate values.

### Gaps
- I found no published motion specs (durations or curves) from Linear, Vercel, Wiz or Raycast in the accessible results.

## 6. Data visualization richness: sparklines, heatmaps, radial, timelines, severity bars, RTL

### Takeaway
Security buyers value a breadth-first overview with drill-down, a score per path or asset, and timelines tied to findings. For Hebrew RTL there is no settled chart-mirroring standard. Mirror the layout, axes labels and annotations, and review time axes and bar direction case by case.

### Cited Findings
- Breadth-first: users start from a high-level view before drilling into specific areas. — [Palo Alto: Security by Design](https://www.paloaltonetworks.com/blog/2025/07/security-by-design-ux-ai-modern-cybersecurity/)
- Orca pairs each attack path with a timeline of events and a numeric severity score. — [Orca Attack Path Analysis PDF](https://orca.security/wp-content/uploads/2025/05/Orca-Attack-Path-Analysis-Digital.pdf)
- A 2025 endpoint-security redesign case study names the "lack of at-a-glance information" as a top user frustration. — [Contra: Endpoint Protector V2 redesign](https://contra.com/p/YbUvmPbW-endpoint-protector-v2-a-uxui-redesign-case-study)
- An IEEE VIS 2024 paper says there are RTL web guidelines but no similar standard for visualization design. A 2026 study of Arabic-speaking practitioners and tools finds fragmented, inconsistent RTL support. — [IEEE VIS 2024: Design Patterns in RTL Visualizations](https://nc.ieeevis.org/year/2024/program/paper_v-short-1078.html); [KCL 2026 VIS RTL interviews (PDF)](https://kclpure.kcl.ac.uk/ws/files/383439862/2026_VIS_RTL_Interviews_tools_revised_-2.pdf)
- Wikimedia Codex flags charts as a category to mirror with caution, since mirroring can affect data interpretation. A Wikimedia discussion notes the x-axis is not consistent in Hebrew and Arabic practice. — [Wikimedia Codex: Bidirectionality](https://doc.wikimedia.org/codex/latest/style-guide/bidirectionality.html); [Wikimedia Phabricator T396690](https://phabricator.wikimedia.org/T396690)
- Datawrapper flips the y-axis, annotations and range highlights under an RTL locale, but some built-in orientations (for example bar direction) aren't customizable. AG Charts has an RTL option for chart direction, separate from UI localization. — [Datawrapper: Right-to-left visualizations](https://www.datawrapper.de/blog/right-to-left-visualizations); [AG Charts RTL](https://ag-grid.com/charts/javascript/rtl.md)

### Inferences
- Meaningful viz set for Hakira: (1) hero score ring with a sparkline of the score over past scans; (2) a severity distribution as one stacked horizontal bar (critical, high, medium, low) instead of a pie; (3) a "surface" heat-strip or grid by category (email, website, credentials, network, devices) that doubles as navigation; (4) a scan timeline (first seen, verified, fixed). Avoid world maps and 3D charts. They add "SOC spectacle" without meaning for a small business.
- Severity colors must be distinct from the brand lime. Lime should mean "fixed or safe or action", so the critical-to-low ramp should be a separate warm scale, with the scale checked for contrast in both themes.
- RTL: mirror the layout and the start position of bars and progress (fill from the right). Decide one convention for time axes and keep it consistent across the product, then validate it with Hebrew-speaking users.

### Gaps
- I found no verified examples of how Wiz, Vanta or Drata style their specific charts (colors, chart types).

## 7. Illustration and iconography that make security approachable

### Takeaway
Wiz is the clearest documented case: an in-house, optimistic, "magical" brand with a recurring spark motif, a node-graph motif and playful wizard-themed illustration. Its explicit goal is to discuss risk without panic and to simplify complexity.

### Cited Findings
- Wiz's goal was an "exciting, innovative, magical, and special experience" rather than a traditional security brand. — [Wiz: The Magic of Branding](https://www.wiz.io/blog/the-magic-of-branding)
- Illustration lets Wiz "talk about risk without inducing panic and simplify a lot of complexities" (Roy Katz). — [Globes](https://en.globes.co.il/en/article-how-branding-helped-drive-wizs-32-billion-exit-1001517931)
- Recurring motifs: a 4-pointed teal spark, a cloud device, a node-graph UI and a crystal-ball or wizard streak. — [STFO: Wiz brand audit](https://www.stfo.io/research/audits/wiz/)
- Vercel's Geist ships its own icon set as part of the system, which shows that a consistent custom icon family is part of the premium feel. — [Vercel Geist Icons](https://vercel.com/geist/icons)

### Inferences
- Hakira could own one simple motif, for example a "break point" mark (a link in a chain snapping, or a lime notch), and reuse it in the logo, the attack-story break node, empty states and the scan loader. That mirrors how Wiz reuses its spark.
- Use a single-weight line icon family with lime as the only accent. Give each asset type in attack stories a consistent icon (domain, inbox, server, user, laptop, cloud).
- Illustrations for small businesses should depict their world (a shop, an inbox, a laptop) in a flat or abstract style using ink and lime plus one neutral. Avoid hooded hackers, padlocks and Matrix code, which induce the "panic" Wiz avoids.

### Gaps
- I found no verified information about the illustrators or agencies behind Wiz, Vanta or others, or about isometric illustration trends specifically in 2025 security products.

## 8. Pitfalls: what makes "wow" UIs feel generic or hurt trust and accessibility

### Takeaway
The documented risks are low contrast (especially glass and blur), saturated colors vibrating on dark surfaces, fake or opaque progress, overused effects, and inconsistent RTL charts. The EU Accessibility Act (enforceable from 28 June 2025) raises the stakes for WCAG 2.1 AA.

### Cited Findings
- Glass and blur reduce text contrast. They are a problem for users with visual and cognitive impairments when overused. — [NN/g: Glassmorphism](https://www.nngroup.com/articles/glassmorphism/); [Axess Lab](https://axesslab.com/?p=5111)
- The EU Accessibility Act is enforceable from 28 June 2025 and requires WCAG 2.1 AA for digital services. This was reported by a secondary source, and its other statistics are unverified. — [WeCanDevelopIt research report](https://www.wecandevelopit.com/news/accessibility-in-the-age-of-glassmorphic-ui-research-report-and-evidence-base)
- Saturated accents vibrate on dark backgrounds. Pure black should be avoided. Shadows don't read in dark mode. — [Toptal: Dark UI design](https://www.toptal.com/designers/ui/dark-ui-design); [Material 2 Dark theme](https://m2.material.io/design/color/dark-theme)
- Grain done wrong on dark surfaces looks like "a dirty screen". — [CodeFronts](https://codefronts.com/design-styles/css-grain-texture/dark-mode-noise-without-muddy-shadows/)
- Visible effort must reflect real processing. Opaque, blind progress lowers perceived value over time. — [HubSpot on the labor illusion](https://blog.hubspot.com/marketing/why-ai-shows-loadtime); [INFORMS: The Labor Illusion](https://pubsonline.informs.org/doi/references/10.1287/mnsc.1110.1376)
- RTL chart support is inconsistent across tools, and mirroring charts can change interpretation. — [Wikimedia Codex](https://doc.wikimedia.org/codex/latest/style-guide/bidirectionality.html); [IEEE VIS 2024](https://nc.ieeevis.org/year/2024/program/paper_v-short-1078.html)
- Even Apple's 2025 Liquid Glass drew designer backlash on legibility. — [UX Collective](https://uxdesign.cc/liquid-glass-isnt-a-design-failure-it-is-apple-s-most-tactile-digital-future-yet-091abade02b3)

### Inferences
- Generic-template tells to avoid: purple-blue mesh-gradient heroes, neon glows on every card, glass everywhere, a 3D globe with attack arcs, donut charts for everything, and identical KPI-tile rows with fake sparklines. Hakira's differentiation should come from its unique content, the attack story and the break point, rendered with craft.
- Trust killers for a security product: animations that delay the score, fake "scanning" steps, unexplained numbers (a score without "why" and "what to do"), and lime used for both "danger" and "safe".
- Accessibility checklist: 4.5:1 for text in both themes, as Geist does for all semantic colors ([Vercel Geist](https://vercel.com/geist)); never encode severity by color alone (add a label or icon); reduced-motion fallbacks; focus-visible rings (lime works well as a focus ring on ink); RTL-correct keyboard order.

### Gaps
- No quantitative study was found that links "wow" visuals to trust or conversion in security SaaS specifically.
