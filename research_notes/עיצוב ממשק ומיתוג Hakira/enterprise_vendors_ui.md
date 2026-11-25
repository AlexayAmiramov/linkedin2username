# Enterprise Cybersecurity Vendor UI Design and Visual Brand Identity (Palo Alto Networks, Fortinet, Check Point, CrowdStrike)

Research method note: this session could not fetch pages on paloaltonetworks.com, crowdstrike.com or checkpoint.com directly (the hosts are blocked by the session's network settings). Values from those sites below come from search-engine extracts of the official PDFs and docs, not from reading the full documents. github.com and raw.githubusercontent.com could be fetched, so the CrowdStrike token values were read directly from the source file. Research date: 2026-11-25.

## 1. Brand colors (hex) and how they are used in product UI

### Takeaway
All four brands are built on one saturated "signature" hue plus near-black, white and greys: Palo Alto orange #FA582D, Fortinet red #DA291C, Check Point "Brand Berry" #EE0C5D and CrowdStrike red (#EC0000 per third parties). Inside the products the signature hue is used sparingly or not at all. CrowdStrike's published UI tokens, for example, use teal or blue for primary buttons and keep red for critical severity.

### Cited Findings

**Palo Alto Networks**
- Official brand guidelines PDF dated July 2026 exists at paloaltonetworks.com/company/brand. A write-up of that edition names the main color "Cyber Orange" #FA582D, matched to Pantone 7417 C. The full PDF could not be fetched, so the color page was not read directly — [PAN Brand Guidelines July 2026 PDF](https://www.paloaltonetworks.com/content/dam/creative-assets/brand-assets/guidelines/Palo_Alto_Networks_Brand_Guidelines_July2026.pdf); [PAN brand page](https://www.paloaltonetworks.com/company/brand)
- Brandfetch lists #FA582D ("Outrageous Orange", RGB 250/88/45). Other listed colors are #006074 ("Orient", a deep teal), #8C8C8C (grey) and #FFCB06 ("Supernova" yellow); none of these is confirmed as an official secondary color — [Brandfetch PAN](https://brandfetch.com/paloaltonetworks.com); [Logotyp.us](https://logotyp.us/logo/paloalto/)
- Third-party sites disagree: #F04E23 (Dwglogo), #F04D1E / PMS 1665 C (BrandsColorCodes), and an outdated "Palo Alto Red" #ED1C24 with black #231F20. Treat these as legacy or unreliable — [Dwglogo](https://dwglogo.com/color-codes/palo-alto-networks/); [BrandsColorCodes](https://brandscolorcodes.com/palo-alto-networks-color-codes/); [DesignYourWay](https://www.designyourway.net/blog/palo-alto-networks-logo/)
- Brand questions go to brand@paloaltonetworks.com, per the brand page — [PAN brand page](https://www.paloaltonetworks.com/company/brand)

**Fortinet**
- Fortinet Brand Guidelines (2019 Q1, partner copy): "RED PMS 485C HEX DA291C C0 M95 Y100 K0". The same guidelines say to "reserve Fortinet Red for emphasizing key elements in your design" — [Fortinet Brand Guidelines 2019 (Exclusive Networks copy)](https://www.exclusive-networks.com/hk/wp-content/uploads/sites/4/2021/02/ASIA-VM-Fortinet-Brand-Guidelines.pdf); [Fabrik Brands](https://fabrikbrands.com/fortinet-logo-history-icon-meaning-and-evolution/)
- Unofficial conflicting values are #D72B2B and #CC3B29 — [Coloropedia](https://coloropedia.com/fortinet-colors-logo-codes/)
- Official logo variants are "RGB Black", "RGB Black Red", "Logomark RGB Black" and "Logomark RGB Red". The black wordmark with a red mark is the standard pairing — [icons.fortinet.com](https://icons.fortinet.com)

**Check Point**
- 2024 Brand Visual Identity Guidelines: the primary color is "Brand Berry" #EE0C5D (Pantone 1925 C, CMYK 0/100/47/0, RGB 238/12/93), with a screen variant "Brand Berry Click" #E40C5B. The primary "is often accompanied by Gravitas Grey and Clay" — [Check Point Brand Guidelines 2024](https://www.checkpoint.com/downloads/company/check-point-brand-guidelines-2024.pdf)
- Secondary and product colors are Gravitas Grey #41273C (a dark aubergine grey), Quantum orange #FF6700, CloudGuard #00B7FF and Harmony #C42DE8. The Clay hex was not in the extracted text — [Check Point Brand Guidelines 2024](https://www.checkpoint.com/downloads/company/check-point-brand-guidelines-2024.pdf)
- A February 2026 edition exists. It says secondary colors act as accents and should be limited "to approximately 10% to 20% coverage" — [Check Point Brand Guidelines 2026](https://www.checkpoint.com/downloads/company/check-point-brand-guidelines-2026.pdf?v=1.1)
- The 2022 rebrand blog describes the new logo as having "a modern design, and a vibrant color" while keeping a connection to the earlier pink brand — [Check Point blog 2022](https://blog.checkpoint.com/security/2022-a-new-strategy-for-the-new-year/)

**CrowdStrike**
- Official "CrowdStrike Brand ID 2025" PDF: "Our core colors — red, black, and white — are the signature colors of the CrowdStrike logo." White is given as #FFFFFF. The red hex was not visible in the extract — [CrowdStrike Brand ID 2025](https://www.crowdstrike.com/content/dam/crowdstrike/marketing/en-us/documents/pdfs/brand/CrowdStrike-Brand-ID-2025.pdf)
- Brandfetch and logo.dev give red #EC0000 (RGB 236/0/0). A brand-style page gives "CRWD Red" #EC0000, "CRWD Dark Red" #B52026, Black #000000, "CRWD Storm" #A7A9AC and "CRWD Cloud" #F8F8F8. One logo-history article says #FC0000 instead, which conflicts — [Brandfetch CrowdStrike](https://brandfetch.com/crowdstrike.com); [logo.dev](https://www.logo.dev/search/brands/crowdstrike.com); [DesignYourWay](https://www.designyourway.net/blog/crowdstrike-logo/)

**In-product use of brand color (CrowdStrike: hard data from its published tokens)**
- CrowdStrike's open-source `@crowdstrike/falcon-styles` tokens (used to theme Foundry apps inside the Falcon console) set the light-theme primary button to teal #0F687B (hover #128098, active #064F5F) and links to #064F5F. The dark-theme primary button is pale blue #C3D9FD, links are #C3D9FD, the focus ring is blue (#2A67ED light / #567FF9 dark), and the "primary" alert color is blue #2A67ED. Brand red appears in these tokens only as error, danger and critical (#E9181F light / #EF3E40 dark) — [falcon-styles tokens.json](https://raw.githubusercontent.com/CrowdStrike/falcon-styles/main/tokens.json); [falcon-styles repo](https://github.com/CrowdStrike/falcon-styles)

### Inferences
- The shared pattern is to put the brand hue in the logo and wordmark and keep it out of interactive controls. A loud brand color on every button would compete with red and orange severity signals. CrowdStrike's tokens show this directly, since their red is reserved for "critical". Palo Alto's orange and Fortinet's red sit right next to "high" and "critical" severity colors, so they would face the same problem. For Hakira, keep the brand accent away from the severity reds and oranges, or limit it to logo and marketing use.
- The 10–20% accent coverage rule (Check Point) and "reserve red for key elements" (Fortinet) are written-down versions of the restraint that makes these brands read as premium.
- Deep, desaturated companions (PAN #006074 teal, Check Point Gravitas Grey #41273C, CrowdStrike teal #0F687B for buttons) do the everyday interactive and structural work.

### Gaps
- I could not read the exact secondary palettes in the PAN July 2026 and CrowdStrike 2025 PDFs (host blocked). The PAN #006074 and #FFCB06 values come from Brandfetch only.
- The Check Point "Clay" hex and any Infinity/Check Point Portal UI accent tokens were not found.
- I found no published Fortinet brand guide newer than 2019.

## 2. Dark vs light theme: defaults, options and dark-surface handling

### Takeaway
All four offer both themes. Light is the documented default where a default is stated (CrowdStrike falcon-styles, Cortex XSOAR). Cortex XSIAM lets each user toggle, and its Command Center dashboard is dark-only. FortiOS has the widest theme system, including three dark themes and custom light/dark-based themes in 8.0. CrowdStrike's tokens use true black #000000 as the dark base, with lighter neutral layers stacked above it.

### Cited Findings
- **Cortex XSIAM:** light and dark mode are toggled per user. An older KB article puts the sun/moon icon above the username at the bottom-left of the console. The current XSIAM 3.x docs put the toggle in the user menu opened by clicking the username — [PAN KB: toggle dark/light in XSIAM](https://knowledgebase.paloaltonetworks.com/KCSArticleDetail?id=kA14u000000PRNoCAO&lang=en_US); [XSIAM 3.x Use the interface](https://docs-cortex.paloaltonetworks.com/r/Cortex-XSIAM/Cortex-XSIAM-3.x-Documentation/Use-the-interface)
- XSIAM Command Center dashboards are described as dark-only (from Scribd copies of older admin guides; unverified for current version) — [Scribd XSIAM docs](https://www.scribd.com/document/927170085/XSIAM-Documentation)
- **Cortex XSOAR 6.x:** the default theme for new users is light, and admins can change it with the `default.theme` server config key — [XSOAR 6.12 Set the default theme](https://cortex-docs.paloaltonetworks.com/xsoar-6-administrator-guide/6.12/onboard-cortex-xsoar/users-and-roles/set-the-default-theme-for-new-users)
- **FortiOS 7.x:** under System > Settings > View Settings, the themes are Jade, Neutrino, Mariner, Graphite, Melongene, Retro, Dark Matter, Onyx and Eclipse — [FortiGate 7.4.3 Changing the view settings](https://docs.fortinet.com/document/fortigate/7.4.3/administration-guide/316105/changing-the-view-settings). The dark themes are Dark Matter (purple), Onyx (green) and Eclipse (orange). Neutrino is dark blue and Mariner is blue, but these are not described as dark themes — [Fortinet Community tech tip](https://community.fortinet.com/t5/FortiGate/Technical-Tip-How-to-change-the-theme-color-of-the-FortiGate-GUI/ta-p/191472). FortiOS 7.0 added new themes — [FortiOS 7.0 new themes](https://docs.fortinet.com/document/fortigate/7.0.0/new-features/821052/new-themes-and-cli-console-enhancements)
- **FortiOS 8.0:** custom GUI themes and admin-level personalization. A custom theme starts from `base-theme` light or dark. It can also set a navigation-bar color (light/dark/gray), toggle border-radius on buttons and inputs, and attach banner messages by severity. Themes can be assigned to the system, admin profiles or individual admins — [FortiOS 8.0 Custom GUI themes](https://docs.fortinet.com/document/fortigate/8.0.0/new-features/643704/custom-gui-themes-and-admin-level-personalization); [FortiOS 8.0 CLI reference](https://docs.fortinet.com/document/fortigate/8.0.0/cli-reference/283802485)
- **Check Point:** Harmony Email & Collaboration added a per-administrator Dark mode for its dashboard (gradual rollout, roughly April 2026) — [Check Point blog: Dashboard Dark Mode Theme](https://blog.checkpoint.com/product-updates/dashboard-dark-mode-theme/). I found no evidence of a dark theme for the whole Infinity/Check Point Portal.
- **CrowdStrike Falcon:** the console stores a per-user theme preference. Foundry apps read it and set a `theme-dark` or `theme-light` class on the root, which updates live when the user switches — [CrowdStrike Foundry-JS demo guide](https://www.crowdstrike.com/tech-hub/ng-siem/getting-started-with-foundry-js-using-the-foundry-js-demo-app/); [foundry-js-blueprint-react](https://github.com/CrowdStrike/foundry-js-blueprint-react). In falcon-styles, "By default all styles are in light mode"; dark is enabled by adding `theme-dark`. That repo was archived on 2026-02-27 — [falcon-styles](https://github.com/CrowdStrike/falcon-styles)
- **CrowdStrike dark-surface layering (exact tokens):** background.default #000000, then light #161618, lighter #1D1C20 and lightest #2C2C30. Borders are #2C2C30 (light), #3B3A40 (medium) and #5D5B65 (bold). Text is primary #F7F7F8, secondary #B8B7BD and disabled #5D5B65. The neutrals have a faint cool/violet tint rather than flat grey. Light theme: background.default #DDDDDF, light #EFEEF2, lighter #F7F7F8, lightest #FFFFFF; text #161618 / #3B3A40 — [falcon-styles tokens.json](https://raw.githubusercontent.com/CrowdStrike/falcon-styles/main/tokens.json)
- CrowdStrike's Toucan design system exports three palettes from Figma: LIGHT, DARK and "MEZZANINE", the last apparently an intermediate theme — [tailwind-toucan-base](https://github.com/CrowdStrike/tailwind-toucan-base)

### Inferences
- Offering both themes, chosen per user, is standard for this category. SOC users (XSIAM, Falcon) lean dark, while admin and configuration tools (XSOAR default, FortiOS Jade) lean light. For SMB owners viewing Hakira occasionally, a light default with a dark option matches the documented defaults.
- CrowdStrike does use pure black, but only as the bottom layer. Cards and panels sit on #161618–#2C2C30, so the "not pure black" advice applies to the surfaces people actually read on. The steps between layers are small (roughly 5–8 L* steps), and borders carry most of the separation.
- In dark mode, accents become lighter and less saturated (primary button #C3D9FD, severity low #B7F2CA) instead of reusing the light-mode saturated values.

### Gaps
- Default theme for the current Falcon console, Prisma Cloud and Strata Cloud Manager: not confirmed by any source found.
- FortiOS default theme (commonly believed to be Jade): no source in this research states it.
- No dark-surface hex values were found for Palo Alto, Fortinet or Check Point. Any value would have to be estimated from screenshots, and I did not do that.

## 3. Typography

### Takeaway
The brand typefaces are commercial grotesques or customs: Check Point uses DIN Pro, Fortinet Helvetica Neue LT Pro (2019 guide), CrowdStrike Haas plus Tungsten (2022 guide), and Palo Alto reportedly H&Co Decimal (unconfirmed). Product UIs fall back to system stacks. CrowdStrike's UI tokens use the system stack (-apple-system, Segoe UI, Roboto, Helvetica, Arial).

### Cited Findings
- Check Point: "DIN Pro" is the preferred typeface for designed communications in the 2024 and 2026 guides. Arial is specified for PowerPoint and Word — [Check Point Brand Guidelines 2024](https://www.checkpoint.com/downloads/company/check-point-brand-guidelines-2024.pdf); [Check Point Brand Guidelines 2026](https://www.checkpoint.com/downloads/company/check-point-brand-guidelines-2026.pdf?v=1.1)
- Fortinet (2019 Q1): primary typeface Helvetica Neue LT Pro, with restricted distribution because of license cost. Arial is the fallback. The wordmark is a custom logotype — [Fortinet Brand Guidelines 2019 (SG copy)](https://www.exclusive-networks.com/sg/wp-content/uploads/sites/10/2021/02/ASIA-VM-Fortinet-Brand-Guidelines.pdf); [DesignYourWay Fortinet](https://www.designyourway.net/blog/fortinet-logo/)
- CrowdStrike 2022 Brand Guide: "Haas" is the primary font for headlines and body, and "Tungsten" (a condensed display face) is secondary for subheads and CTAs — [CrowdStrike 2022 Brand Guide](https://www.crowdstrike.com/wp-content/uploads/2022/11/2022-CS-Brand-Guide.pdf). A 2025 blog claims Sharp Sans instead; this conflicts with the 2022 guide and is low reliability — [Designbeep](https://designbeep.com/2025/11/30/crowdstrike-font/)
- CrowdStrike UI tokens: `system.font-family.sans-serif` begins "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif". The monospace stack is "Consolas, Menlo, Monaco, Courier, monospace" — [falcon-styles tokens.json](https://raw.githubusercontent.com/CrowdStrike/falcon-styles/main/tokens.json)
- Palo Alto Networks: a GDP Studio case study is said to describe a typographic system on Hoefler & Co.'s Decimal for information-dense screens. Brandfetch lists PAN's brand fonts only as "custom". This is not confirmed by the official guide — [GDP Studio: Palo Alto Networks](https://www.gdp.studio/work/palo-alto-networks); [Brandfetch PAN](https://brandfetch.com/paloaltonetworks.com)

### Inferences
- The premium feel comes from a single disciplined grotesque or neo-grotesque with a strict weight hierarchy, not from display fonts in the UI. Each vendor's brand face (DIN, Helvetica, Haas) is a neutral, engineered sans.
- For Hebrew RTL, Hakira needs a typeface family with matched Hebrew and Latin glyphs. None of these vendors gives a Hebrew precedent. The "system stack in product, brand face in marketing" split (CrowdStrike) is a viable model.
- A dedicated monospace stack for IDs, hashes, IPs and CVE numbers is part of the pattern (CrowdStrike tokens).

### Gaps
- Current PAN typeface per the July 2026 guide, and current CrowdStrike typeface per the 2025 Brand ID, could not be confirmed because those hosts were blocked.
- The fonts actually used inside the Cortex, Prisma, FortiOS and Infinity product UIs were not documented in any source found.

## 4. Layout patterns (navigation, widgets, KPIs, scores, tables, drawers)

### Takeaway
The dominant pattern is a collapsible left navigation rail with search, grouped by job ("Insights" vs "Configuration"). The home page is a "Command Center" of widget cards with KPI and health summaries. Scores are presented as ratings with categorized controls (Fortinet Security Rating). Incidents use severity-sorted tables that open into detail or timeline views.

### Cited Findings
- **Strata Cloud Manager** (June 2025 navigation redesign): related configuration workflows are grouped and a search box is added to the left menu. Monitor and Dashboards were merged into "Insights", and Manage and Workflows into "Configuration" — [SCM New Features June 2025](https://docs.paloaltonetworks.com/strata-cloud-manager/release-notes/new-features-strata-cloud-manager/new-features-in-june-2025); [LIVEcommunity navigation preview](https://live.paloaltonetworks.com/t5/strata-cloud-manager/preview-of-upcoming-navigation-changes-in-the-strata-cloud/td-p/1231240)
- **SCM Command Center:** an "interactive visual summary" used as the NetSec homepage for network health, security and efficiency, with multiple views starting from a Summary view. Command Center 2.0 added GenAI app visibility — [SCM Command Center docs](https://docs.paloaltonetworks.com/strata-cloud-manager/getting-started/command-center); [PAN blog 2024](https://www.paloaltonetworks.com/blog/2024/04/platform-power-with-strata-cloud-managers-command-center/); [Command Center 2.0 blog](https://www.paloaltonetworks.com/blog/network-security/one-view-faster-action-introducing-command-center-2-0/)
- A designer portfolio (self-reported) describes the 2024 Command Center project: an outside dashboard design partner, a weekly designer/engineer working group, and the page becoming the most-viewed in the platform — [justin-ux.com Command Center](https://www.justin-ux.com/work/command-center)
- **Strata Multitenant Cloud Manager:** the Summary/Insights page was rebuilt around roles and tasks rather than product tabs (July 2026) — [Strata Multitenant What's New](https://docs.paloaltonetworks.com/sase/prisma-sase-multitenant-platform/release-updates/whats-new)
- **SCM policy tables** (August 2025): timestamps on config entities, a Rule Type column, and new icons for rule and address types — [SCM UI enhancements Aug 2025](https://docs.paloaltonetworks.com/whats-new/new-features/august-2025/ui-enhacements-strata-cloud-manager)
- A practitioner review criticizes SCM for full-page refreshes that make users lose their place — [packetswitch.co.uk](https://www.packetswitch.co.uk/strata-cloud-manager-worth-the-hype/)
- **Cortex XDR/XSIAM:** an incident/case has a severity (Critical/High/Medium/Low) and a score, with an "assess case severity and score" workflow — [Cortex XDR 5.x Assess case severity and score](https://cortex-docs.paloaltonetworks.com/cortex-xdr-5.x/detect-investigate-and-respond-to-threats/investigate-and-respond-to-cases/analyze-and-resolve-cases/establish-case-context/assess-case-severity-and-score). An older guide describes an incident "lanes" timeline view with severity-colored activity nodes, and high/medium alerts split from low/informational "Insights" tabs — [Scribd Cortex XDR Admin](https://www.scribd.com/document/477275363/cortex-xdr-admin)
- **FortiOS 7.6 Security Rating:** a page with Security Controls and Vulnerabilities tabs. Controls are reorganized into categories, objects needing attention are highlighted with a "Security Rating Insights" tooltip, and checks run on demand after config changes — [FortiOS 7.6 GUI improvements to Security Rating](https://docs.fortinet.com/document/fortigate/7.6.0/new-features/96589/gui-improvements-to-security-rating); [FortiOS 7.6 Security ratings](https://docs.fortinet.com/document/fortigate/7.6.0/new-features/714314/security-ratings). Security Rating and Fabric topology were removed on 2 GB RAM models from 7.6.3 — [FortiOS 7.6.7 release notes](https://fortinetweb.s3.amazonaws.com/docs.fortinet.com/v2/attachments/7f08d223-5ac6-11f1-a33a-02356ffb40d9/fortios-v7.6.7-release-notes.pdf)
- **FortiOS dashboards:** widget-based, with a Security dashboard containing Compromised Hosts, Top Threats and Asset Vulnerabilities widgets — [FortiOS 7.6.0 Admin Guide (manuals.plus copy)](https://manuals.plus/m/846663c66bc2841ecb5f6f8cd7de12010bddba8317370be09809276929457357). FortiAnalyzer FortiView dashboards include a threat map — [FortiAnalyzer 7.6 FortiView dashboards](https://docs.fortinet.com/document/fortianalyzer/7.6.0/administration-guide/570191/viewing-fortiview-dashboards)
- **Check Point Portal** (formerly Infinity Portal): a March 2026 doc revision updated product names and grouping "to match new navigation". A menu button lists available services — [Check Point Portal MSSP Admin Guide](https://sc1.checkpoint.com/documents/Infinity_Portal/WebAdminGuides/EN/Infinity-Portal-MSSP-Admin-Guide/CP_Check_Point_Portal_MSSP_AdminGuide.pdf); [Check Point Unified Security Management Platform](https://www.checkpoint.com/infinity/portal/)
- **CrowdStrike Falcon** (G2/PeerSpot): reviewers call the dashboard clean and its navigation easy to follow, but say there is "information overload sometimes". The console "has grown a lot with all the new modules, so navigation is less intuitive", and custom dashboards are "cumbersome" to build — [G2 Falcon reviews](https://www.g2.com/products/crowdstrike-falcon-endpoint-protection-platform/reviews); [G2 pros and cons](https://www.g2.com/products/crowdstrike-falcon-endpoint-protection-platform/reviews?qs=pros-and-cons); [PeerSpot](https://www.peerspot.com/products/crowdstrike-falcon-reviews); [G2 Exposure Mgmt](https://www.g2.com/products/crowdstrike-falcon-exposure-management/reviews?qs=pros-and-cons)

### Inferences
- The most common complaint about these big consoles is module sprawl and navigation complexity. A small-business tool can stand out with a short, flat navigation (for example 5–7 items) and a single summary home.
- "Group navigation by user task" (SCM Insights/Configuration; Multitenant "roles and tasks rather than product tabs") is the current direction. For Hakira this could mean a structure like "Score / Findings / Fix / Reports".
- Fortinet's Security Rating (categorized controls plus a vulnerabilities tab plus insight tooltips on what to fix) is the closest analogue to an SMB assessment score page.
- For RTL, the left rail becomes a right rail. Icons that imply direction (chevrons, drawers sliding in) need mirroring.

### Gaps
- No primary source described exact grid sizes, card dimensions or drawer behavior for any of the four products. Screenshots were not accessible.
- No Prisma Cloud (now Cortex Cloud) UI redesign source was found.

## 5. Severity color conventions

### Takeaway
The only exact, published severity palette found is CrowdStrike's: critical red, high orange, medium amber, low green, info blue, with separate light and dark values. Cortex XDR (older guide) used red for high, yellow for medium, blue for low and grey for informational. FortiAnalyzer's threat map uses red for critical, yellow for high and white for low.

### Cited Findings
- **CrowdStrike** (`falcon-styles` tokens, exact):
  - Light: critical #E9181F (also alert.danger), high #DE5D29, medium #CF8F0F (also alert.warning), low #2D865A (also alert.success), info #2A67ED
  - Dark: critical #EF3E40, high #F6753D, medium #F3C238, low #B7F2CA, info #8CB0FD; alert.success #34D79E
  - Error text: #B11D13 (light) / #EF3E40 (dark)
  - Source: [falcon-styles tokens.json](https://raw.githubusercontent.com/CrowdStrike/falcon-styles/main/tokens.json)
- **Cortex XDR** (older Admin Guide): incident-lane nodes are colored high = red, medium = yellow, low = blue, informational = gray; no critical color was given. The API severity values are critical, high, medium, low and info — [Scribd Cortex XDR Admin](https://www.scribd.com/document/477275363/cortex-xdr-admin); [Cortex XDR IR integration](https://xsoar.pan.dev/docs/reference/integrations/cortex-xdr---ir)
- **FortiAnalyzer 7.6 FortiView threat map:** red line = critical, yellow line = high, and white = low in replay mode — [FortiAnalyzer 7.6 FortiView dashboards](https://docs.fortinet.com/document/fortianalyzer/7.6.0/administration-guide/570191/viewing-fortiview-dashboards)
- **FortiOS 8.0:** custom themes can attach banner messages by severity, but no color values were found — [FortiOS 8.0 Custom GUI themes](https://docs.fortinet.com/document/fortigate/8.0.0/new-features/643704/custom-gui-themes-and-admin-level-personalization)

### Inferences
- The conventions differ: CrowdStrike uses green for "low" while Cortex XDR used blue. Blue or grey for low/info avoids suggesting that a low finding is "safe" or good. That matters for an SMB assessment, where green usually means "passed". Hakira should keep green for "passed / no issue" and use a neutral or cool hue for low.
- In dark mode CrowdStrike lightens the severity colors rather than keeping them saturated, which helps contrast on #161618–#2C2C30 surfaces.

### Gaps
- No published severity hex values for Palo Alto (current XSIAM/Cortex Cloud), Fortinet FortiOS widgets or Check Point.

## 6. Polish details (spacing, density, iconography, data viz, restraint, micro-interactions) and published design systems

### Takeaway
The verifiable polish markers are CrowdStrike's 4px-based spacing scale and small radii (2–8px, with 16px max), muted neutrals with a slight tint, and brand color held back from controls. Of the four vendors, only CrowdStrike publishes design-system code: Toucan (Tailwind preset), falcon-styles and falcon-shoelace. Fortinet publishes an icon library. I found no public Palo Alto or Check Point UI design system.

### Cited Findings
- **CrowdStrike spacing tokens:** base 1rem. The scale is x0 0, x025 0.0625rem, x05 0.125rem, x1 0.25rem, x2 0.5rem, x3 0.75rem, x4 1rem, x5 1.25rem, x6 1.5rem, x8 2rem, x12 3rem and x16 4rem — effectively a 4px grid — [falcon-styles tokens.json](https://raw.githubusercontent.com/CrowdStrike/falcon-styles/main/tokens.json)
- **CrowdStrike radius tokens:** none 0, s 0.125rem (2px), m 0.25rem (4px), l 0.5rem (8px), xl 1rem (16px) — [falcon-styles tokens.json](https://raw.githubusercontent.com/CrowdStrike/falcon-styles/main/tokens.json)
- **CrowdStrike design system repos:**
  - Toucan: "A Tailwind preset that provides the base styles for CrowdStrike's Toucan design system". Palettes and shadows are exported from Figma into `themes.json` (Light, Dark, Mezzanine); tested only with Tailwind v2 — [tailwind-toucan-base](https://github.com/CrowdStrike/tailwind-toucan-base)
  - falcon-styles: CSS custom properties, independent of any component library; archived 2026-02-27 — [falcon-styles](https://github.com/CrowdStrike/falcon-styles)
  - falcon-shoelace: a Shoelace web-components theme — [falcon-shoelace](https://github.com/CrowdStrike/falcon-shoelace)
- **Security note:** `@crowdstrike/tailwind-toucan-base` versions 5.0.1 and 5.0.2 were flagged by Snyk as containing embedded malicious code (critical, 9.3) and were removed from npm. Do not install those versions as a reference — [Snyk advisory](https://security.snyk.io/vuln/SNYK-JS-CROWDSTRIKETAILWINDTOUCANBASE-12705369)
- **Fortinet:** an official icon and logo library is published at icons.fortinet.com — [icons.fortinet.com](https://icons.fortinet.com)
- **Fortinet FortiOS 8.0:** a configurable border-radius toggle for buttons and inputs and a configurable nav-bar tone. This shows corner radius and chrome tone treated as theme-level choices — [FortiOS 8.0 CLI reference](https://docs.fortinet.com/document/fortigate/8.0.0/cli-reference/283802485)
- **Palo Alto SCM:** new dedicated icons for rule and address types (August 2025) — [SCM UI enhancements Aug 2025](https://docs.paloaltonetworks.com/whats-new/new-features/august-2025/ui-enhacements-strata-cloud-manager)
- **Check Point:** accent colors limited to roughly 10–20% coverage (brand rule) — [Check Point Brand Guidelines 2026](https://www.checkpoint.com/downloads/company/check-point-brand-guidelines-2026.pdf?v=1.1)
- A search hit titled "Introducing the New Cortex Experience" (cortex.io) belongs to Cortex, an unrelated developer-portal company, not Palo Alto Cortex. Exclude it — [cortex.io](https://www.cortex.io/post/introducing-the-new-cortex-experience)

### Inferences
- A practical "enterprise polish" recipe from the verified data:
  - a 4px spacing grid
  - 4px default radius on controls and 8px on cards
  - tinted near-neutrals instead of pure grey
  - 3–4 surface levels per theme
  - one desaturated interactive color (teal or blue), separate from the brand hue and from the severity hues
  - a monospace face for technical identifiers
  - severity colors re-tuned per theme
- Restraint is the shared premium signal: brand hue in the logo, roughly 10–20% accent coverage, and color mostly reserved for meaning (severity, status).
- These are inferences from tokens and guidelines, not from observed micro-interactions. Hover and active button shades (teal 500/600/700) are the only interaction detail with data.

### Gaps
- No public design system or Figma community file was found for Palo Alto Networks (Cortex/Strata/Prisma), Fortinet (UI components) or Check Point.
- No sources on data-visualization palettes, chart styles or micro-interaction specs for any vendor.
- No designer case studies on Behance, Dribbble or Medium were found beyond the self-reported justin-ux.com Command Center piece.
- Screenshot-based approximations of surface colors for PAN, Fortinet and Check Point were not produced. The vendor sites could not be fetched, and no hex value was estimated.
