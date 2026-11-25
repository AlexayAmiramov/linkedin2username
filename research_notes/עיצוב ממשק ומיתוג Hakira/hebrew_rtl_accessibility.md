# Hebrew / RTL Typography, RTL Dashboard UI and Accessibility for "Hakira" (dark-themed Hebrew-first security SaaS)

Research date: 2026-11-25. Method note: in this research session only web search and raw.githubusercontent.com (the google/fonts repository) could be fetched directly. fonts.google.com, w3.org, material.io, gov.il, kolzchut.org.il, alefalefalef.co.il, fontef and webaim.org were blocked by the network sandbox. Font facts (weights, axes, subsets, licenses, designers) therefore come from Google Fonts' own METADATA.pb files on GitHub, which is the source data behind fonts.google.com. Other claims come from search-result summaries of the cited pages and should be spot-checked before publication. No prices were guessed. The only price below is quoted from a MyFonts listing.

## 1. Which Hebrew web fonts are best for modern product UIs (free vs. commercial)?

### Takeaway
For a Hebrew-first product UI, the strongest free candidates are **Heebo** (variable font, weights 100-900, Hebrew drawn by Oded Ezer, Latin from Roboto), **Assistant** (variable font, weights 200-800, Latin from Adobe's family), **IBM Plex Sans Hebrew** (7 static weights, part of a full superfamily that includes IBM Plex Mono) and **Noto Sans Hebrew** (variable weight 100-900 and width 62.5-100). All of them are SIL OFL 1.1 and on Google Fonts, so they can be embedded in a commercial SaaS with no fee. **Rubik** has a rounded, friendlier personality and supports Hebrew, Latin and Arabic. Alef, Secular One and Varela Round are too limited in weights for a dense dashboard: they work only for headings or branding, or not at all. Commercial Israeli fonts (AlefAlefAlef's Ploni and Almoni, Fontef's Simpler) need separate web and app licenses bought from the foundry. I could not verify their current terms or prices in this session.

### Cited Findings
**Free / Google Fonts candidates. Facts come from each font's Google Fonts METADATA.pb.**
- **Heebo**: designer Oded Ezer. OFL. Variable `wght` axis 100-900 (normal style only, no italic). Subsets hebrew, latin, latin-ext, math, symbols. Added to Google Fonts on 2016-06-20. — [google/fonts heebo METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/heebo/METADATA.pb)
- Heebo "extends Christian Robertson's Roboto Latin to Hebrew. The Hebrew was drawn by Oded Ezer." A November 2023 update fixed some Hebrew bugs. — [Fontsource: Heebo](https://fontsource.org/fonts/heebo/about); [GitHub OdedEzer/heebo](https://github.com/OdedEzer/heebo)
- **Assistant**: designers "Adobe Systems Inc., Ben Nathan". OFL. Variable `wght` 200-800, no italic. Subsets hebrew, latin, latin-ext. Described as "a Hebrew and Latin type family, with a contemporary sans serif Hebrew design", with 6 upright styles from ExtraLight to Black. — [google/fonts assistant METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/assistant/METADATA.pb); [Google Fonts: Assistant about](https://fonts.google.com/specimen/Assistant/about)
- **Rubik**: designers "Hubert and Fischer, Meir Sadan, Cyreal, Daniel Grumer, Omaima Dajani". OFL. Variable `wght` 300-900, with roman and italic styles. Subsets include hebrew, latin, arabic and cyrillic. "Sans serif font family with slightly rounded corners… Meir Sadan redesigned the Hebrew component in 2015." — [google/fonts rubik METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/rubik/METADATA.pb); [Rubik DESCRIPTION](https://raw.githubusercontent.com/google/fonts/main/ofl/rubik/DESCRIPTION.en_us.html)
- The Rubik effect variants (Glitch, Wet Paint, Moonrocks and others) are single-style display fonts, suitable for headlines only. — [Awesome Hebrew Fonts](https://github.com/danielrosehill/Awesome-Hebrew-Fonts)
- **IBM Plex Sans Hebrew**: designers Mike Abbink and Bold Monday. OFL. 7 static upright weights (100, 200, 300, 400, 500, 600, 700), no italic. Subsets hebrew, latin, latin-ext, cyrillic-ext. Added 2021-06-18. — [google/fonts ibmplexsanshebrew METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/ibmplexsanshebrew/METADATA.pb)
- **Noto Sans Hebrew**: designer Google. OFL. Variable `wght` 100-900 and `wdth` 62.5-100. Subsets hebrew, latin, latin-ext, cyrillic-ext, greek-ext. — [google/fonts notosanshebrew METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/notosanshebrew/METADATA.pb)
- **Open Sans** (the Google Fonts version includes Hebrew): designer Steve Matteson. OFL. Variable `wght` 300-800 and `wdth` 75-100, roman and italic. The hebrew subset is included. — [google/fonts opensans METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/opensans/METADATA.pb). A separate "OpenSansHebrew" project exists on GitHub (gsshab). — [Awesome Hebrew Fonts](https://github.com/danielrosehill/Awesome-Hebrew-Fonts)
- **Alef**: designers Hagilda and Mushon Zer-Aviv. OFL. Only 2 weights (400, 700). Subsets hebrew and latin. — [google/fonts alef METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/alef/METADATA.pb). The Font Squirrel copy is under SIL OFL 1.1 with the reserved font name "Alef". — [Font Squirrel: Alef](https://www.fontsquirrel.com/fonts/alef). Hagilda's own Alef site says the terms are "subject to The Attribution Share-Alike license by Creative Commons", which conflicts with the OFL listings. The Google Fonts metadata says OFL. — [alef.hagilda.com](https://alef.hagilda.com/)
- **Secular One**: designer Michal Sahar. OFL. **A single weight (400)**. — [google/fonts secularone METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/secularone/METADATA.pb)
- **Varela Round**: designer Joe Prince. OFL. **A single weight (400)**. Subsets include hebrew. — [google/fonts varelaround METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/varelaround/METADATA.pb)
- Other Hebrew-capable OFL families on Google Fonts:
  - **Fredoka**: Hebrew by Hafontia. `wght` 300-700, `wdth` 75-125. — [METADATA](https://raw.githubusercontent.com/google/fonts/main/ofl/fredoka/METADATA.pb)
  - **Miriam Libre**: `wght` 400-700. — [METADATA](https://raw.githubusercontent.com/google/fonts/main/ofl/miriamlibre/METADATA.pb)
  - **Playpen Sans Hebrew**: handwriting style, `wght` 100-800. — [METADATA](https://raw.githubusercontent.com/google/fonts/main/ofl/playpensanshebrew/METADATA.pb)
  - **Google Sans**: OFL. Includes a hebrew subset. `wght` 400-700, plus `opsz` and `GRAD` axes. — [METADATA](https://raw.githubusercontent.com/google/fonts/main/ofl/googlesans/METADATA.pb)
- A curated list classes Open Sans, Google Sans and Arimo as "daily driver" Hebrew fonts for body copy, UI and documents. It classes Heebo as "stylistic" and Alef and Secular One as "easy to read". The same list notes that most Hebrew fonts are OFL or Apache 2.0. — [Awesome Hebrew Fonts](https://github.com/danielrosehill/Awesome-Hebrew-Fonts)
- **Wix Madefor** (Wix's corporate font, by Dalton Maag, OFL): the Google Fonts version lists **no hebrew subset**, only cyrillic, latin, latin-ext and vietnamese. — [google/fonts wixmadefortext METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/wixmadefortext/METADATA.pb); [GitHub wix-incubator/wixmadefor](https://github.com/wix-incubator/wixmadefor)

**Commercial Israeli foundries**
- **AlefAlefAlef: Almoni.** The foundry sells separate licenses:
  - Webfont License: "embed the font as live text on an internet website". Agencies "may not share a single webfont license across multiple websites".
  - Application License: "embed the font in an application or computer software… up to 50k installations".
  - Desktop license.
  — [Fonts.com: Almoni licenses](https://www.fonts.com/font/alefalefalef/almoni/licenses); [AlefAlefAlef FAQ](https://alefalefalef.co.il/en/resources/faq/)
- **AlefAlefAlef: Ploni.** A MyFonts listing shows "Complete family of 8 fonts: $4,500.00 USD", with a separate webfont license option. That price is as shown on MyFonts at search time, so re-verify it. — [MyFonts: Ploni](https://www.myfonts.com/collections/ploni-font-alefalefalef/). A third-party site claims Ploni is OFL, and another calls it "demo font free for personal use only". Both conflict with the foundry's commercial listing. Treat the foundry's terms as authoritative. — [itsbaba: Ploni](https://www.itsbaba.com/hebrew-fonts/ploni)
- **Fontef (Simpler)** and **Hagilda's commercial catalogue**: searches in English and Hebrew returned no foundry pages or license terms. Hagilda's best-known free font is Alef (see above). Note that Ploni and Almoni are AlefAlefAlef fonts, not Hagilda fonts.

**Use by well-known Israeli tech products**
- No cited finding is available: searches for the Hebrew fonts used by monday.com, Wix's Hebrew UI or Israeli bank apps returned no reliable source. See Gaps.

### Inferences
- **Recommended primary UI font: Heebo.** It has the full 100-900 variable weight range in one file, which suits dense tables and numbers. Its Latin is Roboto-derived, so English technical terms such as "DMARC", "SPF" and "Cloudflare" inside Hebrew sentences match the Hebrew stroke weight. It is widely familiar to Israeli users. **Strong alternative: IBM Plex Sans Hebrew**, which gives a more "technical/security" voice. Its biggest advantage is a family-consistent monospace (IBM Plex Mono) for evidence and code. **Noto Sans Hebrew** is a good choice if a width axis is needed for compact tables.
- **Assistant** caps at 800 and has no Hebrew-relevant italic, which is fine for a dashboard. Its Latin comes from an Adobe family (per the designer credit), so its Latin pairing is also good.
- **Avoid Alef, Secular One and Varela Round** for app body text: each has only 1-2 weights. Secular One could be a brand or heading accent.
- If a commercial font such as Almoni, Ploni or Simpler is chosen for brand distinctiveness, budget for **both** a web license and possibly an app license (for a desktop or mobile wrapper). Confirm per-domain and pageview terms with the foundry. AlefAlefAlef licenses are per website.
- All OFL fonts can be self-hosted (for example via Fontsource), which avoids third-party requests to Google. That may matter for a privacy-sensitive security product.

### Gaps
- I could not verify current Fontef "Simpler" license terms, weights or price.
- I could not verify the complete AlefAlefAlef price list or current web-license tiers (pageview caps). The foundry site was blocked.
- I found no source on fonts actually used by monday.com (Hebrew), Wix Hebrew UI, Bank Hapoalim, Leumi, Discount or the Bit app.
- Numeral style: none of the fetched sources documents tabular-figure (`tnum`) support for Heebo, Assistant or Plex Sans Hebrew. Test `font-variant-numeric: tabular-nums` in the browser before relying on it.
- The Google Fonts metadata does not say whether Rubik's italic style includes Hebrew glyphs.

## 2. Latin / monospace pairing for code, domains and technical evidence in an RTL layout

### Takeaway
**IBM Plex Mono** (if the UI uses IBM Plex Sans Hebrew) or **JetBrains Mono** (if the UI uses Heebo) are the best OFL choices. Neither contains Hebrew glyphs. If Hebrew can appear inside code or log blocks, use **Cascadia Code**, which is now on Google Fonts with a Hebrew subset, or set a Hebrew font as the fallback in the monospace stack. Always render code, domains, IPs, hashes and JSON in an LTR-isolated container.

### Cited Findings
- **IBM Plex Mono**: OFL. 7 weights (100-700), roman and italic. Subsets latin, latin-ext, cyrillic, vietnamese, symbols2. **No hebrew subset.** — [google/fonts ibmplexmono METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/ibmplexmono/METADATA.pb)
- **JetBrains Mono**: OFL. Variable `wght` 100-800, roman and italic. Subsets latin, cyrillic, greek, vietnamese. **No hebrew subset.** — [google/fonts jetbrainsmono METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/jetbrainsmono/METADATA.pb). A separate community "JetBrains Mono Hebrew" project is listed on GitHub. — [Awesome Hebrew Fonts](https://github.com/danielrosehill/Awesome-Hebrew-Fonts)
- **Cascadia Code** (Microsoft): OFL. Variable `wght` 200-700, roman and italic. **Includes a hebrew subset**, with Hebrew by Liron Lavi Turkenich, plus arabic. Added to Google Fonts on 2025-03-18. — [google/fonts cascadiacode METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/cascadiacode/METADATA.pb)
- **Noto Sans Mono**: OFL. `wght` 100-900, `wdth` 62.5-100. No hebrew subset. — [METADATA](https://raw.githubusercontent.com/google/fonts/main/ofl/notosansmono/METADATA.pb)
- IBM Plex Sans Hebrew and IBM Plex Mono come from the same designers (Mike Abbink and Bold Monday), so they form one superfamily. — [Plex Sans Hebrew METADATA](https://raw.githubusercontent.com/google/fonts/main/ofl/ibmplexsanshebrew/METADATA.pb); [Plex Mono METADATA](https://raw.githubusercontent.com/google/fonts/main/ofl/ibmplexmono/METADATA.pb); [Wikipedia: IBM Plex](https://en.wikipedia.org/wiki/IBM_Plex)

### Inferences
- Suggested stacks:
  - With Heebo: `--font-ui: "Heebo", "Noto Sans Hebrew", system-ui, sans-serif; --font-mono: "JetBrains Mono", "Cascadia Code", ui-monospace, monospace;`
  - All-Plex: `--font-ui: "IBM Plex Sans Hebrew"; --font-mono: "IBM Plex Mono", "Cascadia Code", ui-monospace, monospace;`
  - In both stacks, Cascadia Code is the fallback that catches Hebrew characters inside mono blocks.
- Mono text should be set about 0.9-0.95em relative to Hebrew body text. Latin monospace x-heights generally look large next to Hebrew. This is a design judgment: test visually.
- Code, evidence blocks, DNS records and HTTP headers should carry `dir="ltr"` and `text-align: left`, even inside an RTL page (see section 3).

### Gaps
- I found no published Israeli-designer comparison of Hebrew + mono pairings.

## 3. RTL UI best practices: mirroring, icons, charts/timelines, bidi handling, numbers, CSS logical properties

### Takeaway
Mirror the layout: navigation sits on the right, "back" arrows point right, and progress through a flow runs right to left. **Do not mirror** clocks, circular refresh/sync icons, media-playback controls, non-directional objects or logos. Keep time-series chart X-axes and numbers LTR. Isolate every piece of user or technical data (domains, emails, IPs, JSON, file paths) with `<bdi>`, `dir="auto"` or `dir="ltr"`. Build all spacing with CSS logical properties so one stylesheet serves both directions.

### Cited Findings
**Mirroring and icons**
- Material Design (M2 and M3): "the linear representation of time is mirrored in RTL, the circular direction of time is not". Clock icons and circular refresh or progress indicators with clockwise arrows should not be mirrored. Media playback buttons and the media progress indicator "reflect the direction of the media" and are not mirrored. M3 says that in Hebrew, timelines and media controls should retain LTR directionality. Non-directional objects such as a keyboard or camera are not mirrored. — [Material 2: Bidirectionality](https://m2.material.io/design/usability/bidirectionality.html); [Material 3: Bidirectionality & RTL](https://m3.material.io/foundations/layout/bidirectionality-rtl); [Material 1](https://m1.material.io/usability/bidirectionality.html)
- Material Icons documentation covers RTL icon handling. — [Google Fonts: Material Icons Guide](https://developers.google.com/fonts/docs/material_icons)

**Charts and timelines**
- An RTL guide lists numbers, dates and time-axis charts among elements that should **not** be mirrored for Hebrew and Arabic. — [Vitra: RTL Layouts](https://www.vitra.ai/general/rtl-layout-localization)
- An academic study of RTL visualizations (Arabic content) found that for numerical and time-series data, the most common pattern (58%) keeps the Y-axis on the left with an LTR X-axis, and 33% mirror both axes. The authors note that designers take "inconsistent cues" from RTL guidelines. — [Alebri et al. 2024, Design Patterns in RTL Visualizations (PDF)](https://rakotondravony.com/assets/pdf/alebri2024design.pdf)
- ApexCharts keeps its SVG LTR inside RTL pages, and its datetime axis runs LTR in all languages. — [ApexCharts: Localize a dashboard](https://apexcharts.com/recipes/ship-one-locale-across-a-dashboard/). AG Charts has an explicit RTL mode for text, legend and controls. — [AG Charts: RTL Layout](https://www.ag-grid.com/charts/javascript/rtl/)
- Counterexample: a Hebrew expense app reversed X-axes so that time flows right to left. — [GitHub PR Omeriko90/home-expenses #28](https://github.com/Omeriko90/home-expenses/pull/28)

**Bidi markup**
- W3C i18n guidance: wrap a phrase of unpredictable direction in `<bdi>`, or add `dir="auto"` to a tightly wrapping element. A `bdi` element with no `dir` attribute behaves as if it had `dir="auto"`. U+2068 FIRST STRONG ISOLATE … U+2069 is the plain-text equivalent. — [W3C: Inline markup and bidirectional text in HTML](https://www.w3.org/International/articles/inline-bidi-markup/); [UAX #9 Unicode Bidi Algorithm](http://www.unicode.org/reports/tr9/)
- WHATWG HTML rendering: `input[dir=auto]` of type search, tel, url or email, plus `textarea[dir=auto]` and `pre[dir=auto]`, get `unicode-bidi: plaintext` by default. `bdi` and `output` get `unicode-bidi: isolate` by default. — [HTML Standard: Rendering](https://html.spec.whatwg.org/multipage/rendering.html); [MDN: unicode-bidi](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/unicode-bidi)
- The W3C "Additional Requirements for Bidi in HTML & CSS" note is old, and its proposed `ubi` attribute was not adopted. — [W3C TR html-bidi](https://www.w3.org/TR/html-bidi/)

**CSS logical properties**
- `margin-inline-start` corresponds to `margin-left` in LTR and flips automatically in RTL. `inset-inline-start` and `inset-inline-end` replace `left` and `right`. — [MDN: Margins, borders, padding](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties/Margins_borders_padding); [MDN: Floating and positioning](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_logical_properties_and_values/Floating_and_positioning)
- A single `margin-inline-end` rule replaces separate `html[dir="rtl"]` overrides. — [Ahmad Shadeed: CSS Logical Properties](https://ishadeed.com/article/css-logical-properties/); [web.dev: Logical properties](https://web.dev/learn/css/logical-properties); [web.dev: flow-relative shorthands](https://web.dev/articles/logical-property-shorthands)

### Inferences
These are implementation recommendations synthesized from the findings above.
- Set `<html lang="he" dir="rtl">` once. Never set direction with CSS `direction` alone: direction is document semantics.
- **Technical tokens** (domains, emails, IPs, URLs, hashes, CVE IDs, ports, DNS TXT records): render as `<bdi dir="ltr" class="mono">example.co.il</bdi>` or `<span dir="ltr">`. An explicit `ltr` is safer than `auto` for IPs like `192.168.1.1` and for strings that start with digits or punctuation, because `auto` decides direction from the first strong character. Strings with no strong characters fall back to the parent direction. This is an inference: I found no source specific to IPs.
- **User-provided strings that may be either language** (company names, page titles, email subjects): use `<bdi>` with no `dir` attribute, which behaves as `dir="auto"`. Use `dir="auto"` on inputs and textareas where users type free text. Inputs of type email and url should use `dir="ltr"`.
- **JSON, log and evidence blocks**: `<pre dir="ltr"><code>` with `text-align: left`, and keep the block's own scrollbars LTR.
- **Numbers and percentages**: Hebrew uses Western digits (0-9), and digits run LTR inside RTL text via the bidi algorithm. Use `Intl.NumberFormat('he-IL')` for grouping and percent formatting, and `Intl.DateTimeFormat('he-IL')` for dates. Wrap compound values like "12/45" or "-3%" in `<bdi>` so the sign or slash doesn't jump. Use `font-variant-numeric: tabular-nums` in tables.
- **Mirror**: sidebar (right side), breadcrumbs, back/next chevrons, progress steppers, table column order (first column on the right), toggle switch "on" direction, drawer slide direction, toast position.
- **Don't mirror**: logos, clocks/history icons, refresh/sync, play/pause, checkmarks, search magnifier (a debated case: verify per icon set), external-link icon (debated), charts' time axis, code, phone numbers, and brand marks of third parties (Google, Microsoft).
- Use CSS logical properties everywhere (`padding-inline`, `margin-inline-start`, `inset-inline-end`, `border-inline-start`, `text-align: start`). For directional icons, use `:dir(rtl) .icon-directional { transform: scaleX(-1); }` or the icon library's RTL flag.
- For a security timeline (events over time), keep the chronological axis LTR in charts, consistent with the majority practice and the library defaults. A vertical event list (newest on top) avoids the problem entirely.

### Gaps
- I found no authoritative source on how monday.com (Hebrew UI), Wix Hebrew, or Israeli banking apps (Hapoalim, Leumi, Discount, Bit) mirror charts, icons or tables. The searches returned nothing primary.
- I found no source for checkmark or search-icon mirroring rules (Material's checkmark rule could not be fetched).

## 4. How Israeli SaaS products handle Hebrew dashboards

### Takeaway
I found no reliable primary or secondary source documenting monday.com's, Wix's or Israeli banks' Hebrew dashboard conventions (fonts, chart direction, bidi handling). This remains a gap to fill by hands-on review of those products.

### Cited Findings
- Search for monday.com Hebrew UI and Israeli designer practice returned only generic RTL guidance and library documentation. — [AG Charts RTL](https://www.ag-grid.com/charts/javascript/rtl/); [Vitra RTL](https://www.vitra.ai/general/rtl-layout-localization)
- Wix's own brand font, Wix Madefor, is not distributed with Hebrew on Google Fonts, so its Hebrew UI must use another font or a private build. — [google/fonts wixmadefortext METADATA.pb](https://raw.githubusercontent.com/google/fonts/main/ofl/wixmadefortext/METADATA.pb)

### Inferences
- A practical substitute for missing documentation: take screenshots of monday.com (Hebrew), Wix dashboard (Hebrew), the Bit app and the Hapoalim or Leumi apps. Inspect their computed `font-family` in DevTools to record the actual Hebrew fonts, chart directions and number formatting.

### Gaps
- No verified facts on fonts or patterns used by monday.com, Wix Hebrew, or Israeli bank apps.

## 5. Accessibility: WCAG 2.2 AA contrast on dark backgrounds, colorblind-safe severity, Israeli regulation

### Takeaway
The minimums are 4.5:1 for normal text, 3:1 for large text, and 3:1 for meaningful UI component boundaries, icons, focus indicators and chart marks against adjacent colors. These apply to the dark theme independently. Color must never be the sole carrier of severity. Legally, Israeli commercial websites and apps that serve the public must meet **IS (ת"י) 5568 at level AA**, which adopts WCAG 2.0 with Israeli deviations (some vendors say 2.1). The obligation comes from the Equal Rights for Persons with Disabilities (Service Accessibility Adjustments) Regulations 2013, Regulation 35. An accessibility statement is required, and exemptions exist for small turnover. Designing to WCAG 2.2 AA exceeds the legal floor.

### Cited Findings
**WCAG contrast**
- SC 1.4.3 Contrast (Minimum), AA: 4.5:1 for normal text and 3:1 for large text. SC 1.4.11 Non-text Contrast, AA: input borders, focus rings, icons and chart marks that carry meaning must have at least 3:1 against adjacent colors. There is no separate dark-mode rule: each theme must pass on its own background. — [WebAIM: Contrast and Color Accessibility](https://webaim.org/articles/contrast/); [a11yflow WCAG 2.2 contrast guide](https://www.a11yflow.dev/blog/color-contrast-wcag-developer-guide); [Dev.to: Dark mode accessibility](https://dev.to/giriprasad_patil_c2719c67/dark-mode-accessibility-why-a-theme-toggle-doesnt-satisfy-wcag-contrast-21ni)
- Example: gray `#6B7280` passes on white (4.83:1) but fails on `#121212` (3.87:1). Re-derive dark-theme colors rather than inverting the light palette. — [Dev.to: Dark mode accessibility](https://dev.to/giriprasad_patil_c2719c67/dark-mode-accessibility-why-a-theme-toggle-doesnt-satisfy-wcag-contrast-21ni). My own computation agrees: 3.88:1.
- WCAG 2.2 focus criteria:
  - SC 2.4.13 Focus Appearance is **AAA**. It requires 3:1 between the focused and unfocused states of the indicator pixels, and it does not replace 1.4.11.
  - SC 2.4.11 Focus Not Obscured (Minimum) is AA.
  - Some blogs mislabel Focus Appearance as 2.4.11 AA.
  — [Vispero: New Success Criteria in WCAG 2.2](https://vispero.com/resources/new-success-criteria-in-wcag22/); [w3c/wcag issue #1490](https://github.com/w3c/wcag/issues/1490)
- Pure white on pure black (21:1) "can cause eye strain". WCAG sets a floor, not a target, so avoiding pure black is a readability recommendation, not a WCAG requirement. — [colorpickerweb WCAG 2.2 explained](https://www.colorpickerweb.com/wcag-2-2-color-contrast/); [rgblind WCAG contrast](https://rgblind.com/blog/wcag-color-contrast-requirements)

**Color-blind-safe severity**
- SC 1.4.1 Use of Color (Level A): color must not be "the only visual means of conveying information". Supplement it with shape or text. — [W3C Understanding SC 1.4.1 (WCAG 2.2)](https://w3.org/WAI/WCAG22/Understanding/use-of-color.html)
- The Okabe-Ito palette is "the most widely cited colorblind-safe palette": `#E69F00` orange, `#56B4E9` sky blue, `#009E73` bluish green, `#F0E442` yellow, `#0072B2` blue, `#D55E00` vermillion, `#CC79A7` reddish purple. It works best for about 8 categories. — [AudioEye: colorblind-friendly palettes](https://www.audioeye.com/post/colorblind-friendly-palettes/)
- The EU Data Visualisation Guide advises against red/green traffic-light coding for safe/dangerous. Datawrapper warns that some colors are hard to distinguish when used as thin lines. — [data.europa.eu: accessible colour palettes](https://data.europa.eu/apps/data-visualisation-guide/accessible-colour-palettes); [Datawrapper: colorblindness part 2](https://www.datawrapper.de/blog/colorblindness-part2)
- GitLab's design system documents a data-viz color system with accessibility constraints. — [GitLab design: data visualization color](https://design.gitlab.com/data-visualization/color)

**Israeli regulation**
- The governing instrument is the Equal Rights for Persons with Disabilities (Service Accessibility Adjustments) Regulations 2013 (תקנות שוויון זכויות לאנשים עם מוגבלות (התאמות נגישות לשירות), תשע"ג-2013). Regulation 35 makes accessibility mandatory for "all websites and applications which provide service and/or information to the public", including businesses. — [JST Law: digital accessibility obligations](https://www.jstlaw.co.il/en/the-equal-rights-for-persons-with-disabilities-law-digital-accessibility-obligations/); [Schwebel Law: Website and App Accessibility in Israel](https://schwebel-law.com/en/writing/website-accessibility-law-israel)
- The binding standard is IS 5568 Part 1 (September 2023 edition), level AA. It "adopts the WCAG 2.0 guidelines with national deviations". — [gov.il: SI 5568-2 September 2023 PDF](https://www.gov.il/BlobFolder/legalinfo/israeli_accessibility_standards_pdf/he/sitedocs_si-5568-2-september-2023.pdf); [SII standard page](https://www.sii.org.il/he/lobby/standardization/standard-page?id=6753); [W3C WAI policies: Israel](https://www.w3.org/wai/policies/israel). **Conflict:** vendor pages state that IS 5568 adopts WCAG 2.1. — [EqualWeb: IS 5568](https://www.equalweb.com/platform/standards/is-5568.html); [ea-coding: IS 5568 — WCAG 2.1 AA](https://ea-coding.com/en/services/web-accessibility/)
- Timeline: existing websites had to be accessible by 25 Oct 2016 (some sources say October 2017 for private sites). New sites must be accessible from launch. — [Open University presentation (PDF)](https://www.openu.ac.il/Lists/MediaServer_Documents/מייטלגרייבר.pdf); [aisrael: All web sites to be accessible by October 2017](https://aisrael.org/en/all-web-sites-to-be-accessible-in-israel-by-october-2017/)
- Accessibility statement: Regulation 35ה (35E) requires a published accessibility statement. Regulation 35ו (35F) gathers the exemptions. An exempt provider must offer alternative accessibility and declare the exemption and the alternatives in its accessibility statement. — [Schwebel Law](https://schwebel-law.com/en/writing/website-accessibility-law-israel); [user-a FAQ on laws](https://user-a.co.il/faq_laws)
- Small-business exemption:
  - A service provider whose average turnover is ≤ ₪1,000,000 is exempt for a website or application **that began operating before the regulations took effect**, provided its contact details are published. The exemption is valid for three years and renewable.
  - Per gov.il as summarized, a business below ₪1M annual turnover generally need not apply to the Commission for this exemption.
  - A secondary source claims a full exemption at ≤ ₪100,000 average turnover. This is unverified.
  — [user-a FAQ on laws](https://user-a.co.il/faq_laws); [aisrael: website accessibility guide (Hebrew)](https://aisrael.org/%D7%9E%D7%99%D7%93%D7%A2-%D7%9C%D7%9E%D7%A0%D7%92%D7%99%D7%A9/%D7%9E%D7%93%D7%A8%D7%99%D7%9B%D7%99-%D7%A0%D7%92%D7%99%D7%A9%D7%95%D7%AA/%D7%94%D7%9E%D7%93%D7%A8%D7%99%D7%9A-%D7%9C%D7%94%D7%A0%D7%92%D7%A9%D7%AA-%D7%90%D7%AA%D7%A8-%D7%90%D7%99%D7%A0%D7%98%D7%A8%D7%A0%D7%98-3/)
- A website or app owner is not responsible for the accessibility of content "produced and/or prepared by a third party". — [HG.org: Revision of the regulations](https://www.hg.org/legal-articles/revision-of-the-regulations-requiring-websites-and-applications-to-be-accessible-for-people-with-disabilities-in-israel-45630)
- Exposure: an inaccessible site exposes its owner to lawsuits under the Equal Rights law, "in some cases, no proof of damage is required". — [sgo.co.il: Website Accessibility in Israel 2026](https://sgo.co.il/en/blog/website-accessibility-israel-2026/). A figure of ₪50,000 statutory damages appears in one source but was **not confirmed** by others. — [disabilityworld.org](https://www.disabilityworld.org/regulations/il/)
- A periodic accessibility survey is required under Regulation 28 and IS 5568. — [Open University: accessibility testing (PDF)](https://www.openu.ac.il/Lists/MediaServer_Documents/אילנה%20בניש%20-%20בדיקות%20נגישות.pdf)

### Inferences
**Computed contrast ratios for a proposed Hakira dark palette.** I calculated these myself with the WCAG 2.x relative-luminance formula. They are not taken from a source.

| Foreground | on bg `#0F141A` | on surface `#161D26` | on raised `#1E2733` | Use |
|---|---|---|---|---|
| text `#E6EAF0` (off-white, not #FFF) | 15.32 | 14.05 | 12.48 | primary text |
| muted `#A3ADBB` | 8.15 | 7.47 | 6.64 | secondary text |
| subtle `#7D8796` | 5.09 | 4.67 | 4.15 (fails 4.5 for small text) | captions, but not on raised |
| `#6B7280` (Tailwind gray-500) | 3.83 (fail) | 3.51 (fail) | 3.12 (fail) | don't use for text |
| border `#4B5768` | 2.52 | 2.31 | 2.05 | decorative dividers only (fails 3:1) |
| critical `#FF6B5E` | 6.62 | 6.07 | 5.40 | severity: critical |
| high `#FF9F43` | 9.07 | 8.31 | 7.39 | severity: high |
| medium `#F2C94C` | 11.66 | 10.69 | 9.50 | severity: medium |
| low `#5DADE2` | 7.52 | 6.90 | 6.13 | severity: low/info |
| ok `#3DD6A3` | 9.99 | 9.17 | 8.14 | passed/secure |
| focus ring `#7CC4FF` | 9.86 | 9.05 | 8.04 | focus indicator |
| Okabe-Ito vermillion `#D55E00` | 4.78 | 4.39 | 3.90 | too dark for small text on dark surfaces |
| Okabe-Ito blue `#0072B2` | 3.57 | 3.27 | 2.91 | avoid as text on dark |

- Background: use a near-black blue-gray such as `#0F141A` instead of `#000`, and off-white text such as `#E6EAF0` instead of `#FFF`. This keeps contrast around 15:1, well above AA, while avoiding halation.
- Input borders and toggles that are the **only** visual boundary of a control need at least 3:1 against the background. A gray in the `#5C6878`-plus range passes on `#0F141A`; verify it with a checker. Purely decorative dividers are exempt.
- Severity should combine **color + icon shape + Hebrew text label**, for example critical = octagon + "קריטי", high = triangle + "גבוה", medium = diamond + "בינוני", low = circle + "נמוך". This satisfies SC 1.4.1. The proposed red-orange, orange, yellow and blue ramp avoids relying on red vs. green alone.
- Legal positioning: a commercial B2B SaaS serving the Israeli public is very likely in scope of Regulation 35. The ₪1M exemption, as described, applies to sites that existed before the regulations, so a new product launching in 2026 should plan for full IS 5568 AA compliance. It should publish a Hebrew accessibility statement (הצהרת נגישות) naming an accessibility coordinator and contact details. Designing to WCAG 2.2 AA covers both the 2.0 and 2.1 interpretations of IS 5568.
- Provide an accessible alternative channel (phone or email) and document it in the statement.

### Gaps
- I could not confirm whether IS 5568 Part 1 (2023) references WCAG 2.0 or 2.1. The official SII and gov.il pages could not be fetched, and sources conflict.
- I could not confirm the statutory-damages amount for accessibility claims, or the ₪100k turnover full-exemption claim.
- I found no authoritative guidance on how responsibility is split between a SaaS vendor and its business customers (for example, customer-uploaded content), beyond the third-party-content carve-out.
- The kolzchut.org.il and gov.il Commission pages were blocked, so details of how to file the accessibility statement and the coordinator requirements were not verified.
