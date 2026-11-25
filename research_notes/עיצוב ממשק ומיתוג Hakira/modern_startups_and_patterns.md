# Modern Design-Led Security Startups and UI Patterns (input for Hakira GUI)

Research note (compiled 2026-11-25). Method limitation: in this session, direct page fetches (WebFetch) were blocked for every external host tried (wiz.io, world.hey.com, cdn.jsdelivr.net). All findings below come from search-engine result summaries of the cited pages, not from full-page reads. I could not inspect any screenshots. No hex code here comes from sampling a screenshot; every hex is from the cited (mostly third-party) listing and is labeled with its source and reliability.

## 1. Brand colors (hex where published or reliably documented) and in-product use

### Takeaway
None of the six companies has an official public hex palette that turned up in search. Wiz's brand is documented qualitatively: a "vibrant blue" plus a pink accent, chosen deliberately against the red/black fear palette used across the security industry. SentinelOne is purple, with third-party values clustering around #6B0AEA/#6100FF. Snyk's third-party listings conflict.

### Cited Findings
**Wiz**
- Wiz's own blog post "The Magic of Branding: Creating an Optimistic Identity for a Security Product" says the vibrant blue brand color stands for trust, loyalty and wisdom, and the pink accent stands for energy, playfulness and optimism. The post says the brand uses figurative, "magical" imagery and that its illustrations add a "whimsical yet smart" element. — [Wiz blog](https://www.wiz.io/blog/the-magic-of-branding)
- The same post sets Wiz against an industry that leans on fear and intimidation, and builds the brand around "the power of optimism and positivity." — [Wiz blog](https://www.wiz.io/blog/the-magic-of-branding)
- Roy Katz, Wiz's Director of Brand, told Globes that cybersecurity companies typically use scare tactics in red and black. He chose to drop that palette and "inject lots of pink," describing the contrast with confident blue as a sudden femininity, softness and playfulness. Globes credits this branding as a factor in Wiz's $32B exit. — [Globes](https://www.globes.co.il/news/article.aspx?did=1001517931)
- Secondary summaries describe the identity as deep blue for trust and technology, vivid pink accents, and illustrations "inspired by magic and storytelling rather than technical schematics." — [Inshi](https://inshi.pro/blog/wiz-effect/). Another calls it "cartoonish imagery, with bright blues and pinks." — [Foundation Inc.](https://foundationinc.co/lab/wiz)
- Hex search: no authoritative Wiz hex code turned up. Results for "Wiz" on Brandfetch-type sites belonged to unrelated companies (for example Wiz Expert, and the Washington Wizards at #002B5C). — [Brandfetch wiz-expert](https://brandfetch.com/wiz-expert.com); [brandcolorcode](https://www.brandcolorcode.com/washington-wizards)
- A "Wiz Design System" portfolio page found in search belongs to Wiz Robotics, an unrelated company. Do not use it. — [roxyshi.com](https://roxyshi.com/projects/wiz%20design%20system/)

**SentinelOne (Singularity / Purple AI)**
- Most-cited primary purple: #6B0AEA (rgb 107,10,234), listed by Brandfetch with #0B0C1B (near-black navy) and #FFFFFF. — [Brandfetch](https://brandfetch.com/sentinelone.com); [worldvectorlogo](https://worldvectorlogo.com/logo/sentinelone-logo)
- Conflicting third-party values: #6100FF (alternate Brandfetch listing); a gradient from #4500B6 to #6100FF ([logotyp.us](https://logotyp.us/logo/sentinelone/)); #4B00C6 ([logo.dev](https://www.logo.dev/search/brands/sentinelone.com)); #5800E7 and #4C00C8 ([zonalogo](https://zonalogo.com/sentinelone-logo-png-svg)). All are unofficial.
- AKQA's rebrand case study says SentinelOne kept "a refined colour palette and icon system in SentinelOne's standout hue of purple." — [AKQA](https://www.akqa.com/work/sentinelone/evolving-cybersecurity/). A LinkedIn post on the 2024 rebrand ("Always Evolving, Infinitely Intelligent") confirms the brand stayed purple. — [LinkedIn](https://www.linkedin.com/posts/blandinedelaporte-cybersecurity-manager_sentinelone-always-evolving-infinitely-intelligent-activity-7166580062174068737-y8D_)
- SentinelOne's marketing describes the Purple AI interface as dark, with a sidebar, a "+ New Notebook" button, "Threat Hunting" and "Support Questions" panels, an input prompt, warning text, and result counts next to charts and text summaries. — [SentinelOne Purple LP](https://www.sentinelone.com/lp/purple/); [SentinelOne platform/purple](https://www.sentinelone.com/platform/purple/)

**Snyk**
- No official hex palette was found, and the third-party listings conflict:
  - Brandfetch (snyk.com): #E73448, #F5484E, #21214C ("Port Gore" navy).
  - Brandfetch (snyk.io): #145DEB, #F6F4FA, #01011E. — [Brandfetch snyk.com](https://brandfetch.com/snyk.com); [Brandfetch snyk.io](https://brandfetch.com/snyk.io)
  - colors.gallery: #4C4A73 ("Snyk Purple"), #8B79FF ("Snyk Lavender"). — [colors.gallery](https://colors.gallery/snyk)
  - logo.dev: #4404B2, #3C3364, #9C00CE. — [logo.dev](https://www.logo.dev/search/brands/snyk.io)
  - An unofficial "brand guidelines" interpretation gives #4B45A9, #1C1A33, #E0565B, #3B82C4, #F7F6FB and states that no official hex is published. — [Made Good Designs](https://madegooddesigns.com/snyk-brand-guidelines/)
- Brandfetch listing ages range from 108 to 1,651 days, so some values probably predate Snyk's current (purple-leaning) identity. — [Brandfetch](https://brandfetch.com/snyk.io)

**Cyera**
- After its $300M Series C, Cyera's brand was refreshed by agency Shaped By, which describes an "abstract visual language" built to keep technical credibility. The new brand and website launched at Cyera's DataSec conference. The case study frames the work as evolving the brand through a $3B-to-$9B valuation story. — [Shaped By](https://shaped-by.com/work/cyera-brand-identity/)
- Studio Poink also has a Cyera DSPM project page (product or motion work; details not retrievable). — [Studio Poink](https://studiopoink.com/work/dspm/)
- No hex values were found.

**Guardz, Coro**
- No brand hex values were found in this session.

### Inferences
- Wiz shows that a security brand can win by refusing the industry default (red/black, hooded hackers, fear) in favor of optimism, warmth and illustration. That fits a product for non-technical small-business owners, who need to feel able to fix things rather than scared.
- Purple is now strongly tied to SentinelOne and Snyk in security, and to "AI" generally (see section 5). For Hakira, a purple primary would read as derivative on both counts.
- In-product, these brands appear to keep the strong brand hue for identity and accents, and keep severity colors separate. This is an inference; I could not view screenshots to confirm how hues are split.

### Gaps
- No official brand or press-kit hex for Wiz, Cyera, Snyk, Guardz or Coro. Sampling logos or site CSS would be needed and was not possible here (fetch was blocked).
- How brand color is used inside the Wiz, Cyera and Snyk consoles (light versus dark default, accent usage) could not be verified without screenshots.

## 2. How Wiz and others visualize attack paths and security graphs, and present risk, severity, findings tables and detail panels

### Takeaway
Wiz treats the graph as the data model and analysis engine, with the visual layer on top. Users meet it mainly as a prioritized list of "Issues" (toxic combinations), each with an attack-path or "View in graph" drill-down. Wiz explicitly aims for graph visuals "anyone can understand." Cyera's dashboard pairs a risk-trend chart with issues counted by severity, posture scores per framework, and actions shown as labeled buttons.

### Cited Findings
- Wiz describes the Security Graph as "not just a visualization layer, but the database, the normalizing data model, and the analysis layer." — [Wiz blog: Anatomy of a Toxic Combination](https://wiz.io/blog/the-anatomy-of-a-toxic-combination-of-risk)
- A toxic combination pairs a resource with a high likelihood of compromise with a significant business impact if it is compromised. Wiz calls these "a critical Wiz Issue." — [Wiz blog](https://wiz.io/blog/the-anatomy-of-a-toxic-combination-of-risk)
- Wiz's product messaging promises "simple and intuitive graph visualization that anyone can understand without cloud or AI security expertise," and "a single list of prioritized issues of toxic combinations… that have a high probability of being exploited." — [Wiz (G2 landing page)](https://www.wiz.io/br-pm-wiz-b)
- Runtime signals feed into the graph so Wiz can "map the complete path from the internet to your most sensitive data in a single view." — [Wiz blog: runtime signals](https://wiz.io/blog/runtime-signals-in-security-graph)
- Google Cloud's architecture guide describes Wiz building a node-and-edge graph of assets and their interconnections, flagging the most toxic combinations as Wiz Issues, which then trigger alerts and remediation workflows. — [Google Cloud Architecture Center](https://docs.cloud.google.com/architecture/partners/id-prioritize-security-risks-with-wiz)
- An informal third-party description of how Wiz is structured (treat with caution):
  - A Control is a graph query plus a severity, and an Issue opens when the query matches nodes and edges.
  - Issue details link to "Attack Path" or "View in graph."
  - The left navigation has a "Security Graph" entry, offering a visual explorer or WQL (a query language).
  — [techclick blog](https://ai.techclick.in/blog_wiz_security_graph)
- Wiz Academy's framing: attack path analysis traces how an attacker can chain exposures (for example, internet exposure, then a vulnerability, then excessive permissions, then sensitive data). — [Wiz Academy](https://www.wiz.io/academy/detection-and-response/attack-path-analysis)
- Comparable pattern from Google Cloud Security Command Center: its Risk Engine generates an attack-path visualization from a toxic combination to "high-value resources," and also identifies chokepoints. — [Google Cloud SCC docs](https://docs.cloud.google.com/security-command-center/docs/toxic-combinations-overview?authuser=6)
- Cyera's DSPM page describes its dashboard screens (vendor marketing, figures illustrative):
  - A downward risk-trend graph and "2.7K open issues by severity."
  - Datastore scanning progress bars with completion percentages and sensitivity labels.
  - Actions shown as icons plus labels: "Create Jira Ticket," "Apply Sensitivity Label," "Disable Public Access."
  - Compliance posture scores for NIST, PCI DSS, GDPR and HIPAA.
  — [Cyera DSPM](https://www.cyera.com/platform/dspm)
- Cyera users disagree on the UI: one PeerSpot reviewer calls the dashboard user-friendly, while another says the UI "requires a more appealing design." — [PeerSpot](https://www.peerspot.com/products/cyera-reviews)
- Orca Security shows an alert's attack path from initial access to final objective, tagged with MITRE ATT&CK techniques that can be used as filters. — [Orca](https://orca.security/resources/blog/mitre-attck-framework/)

### Inferences
- The pattern to borrow is "list first, graph on demand": a ranked list of combined risks, each opening a detail view with the path drawn left to right (right to left for Hebrew), running from entry point (internet or public exposure) to impact (data, money, account).
- For Hakira's small-business audience, the "graph" can be a linear chain of 3 to 6 steps rather than a free-form network. Wiz's own stated goal ("anyone can understand") supports simplifying.
- Severity sits on the Issue (combination), not only on individual findings. Hakira should score the story or path, then show contributing findings beneath it.

### Gaps
- Exact Wiz graph visual grammar could not be verified: node iconography, edge styling, severity chip colors, light or dark theme, detail-drawer layout. That needs Wiz docs (behind login) or screenshots.
- No Wiz design-team blog posts about the graph UI turned up.
- Snyk's findings-table and priority-score UI was not covered in the results.

## 3. How SMB tools (Guardz, Coro) simplify security for non-technical owners

### Takeaway
Guardz leads with a single posture score shown as a red-to-green gauge against a visible threshold (for example "Your Business 71" against an insurance line at 80). It groups risk into plain categories (devices, emails and so on), surfaces "3 critical issues" in a summary widget, and offers one-click remediation with multiple options. Coro wins reviews on consolidation into "one dashboard" and fast setup. Both, however, sell mostly through MSPs, so their "plain language" is partly aimed at the MSP explaining to the owner.

### Cited Findings
- Guardz shows a "real-time cybersecurity posture score that reflects the cyber risk and remediation progress." — [Guardz business owners page](https://guardz.com/business-owners/)
- The insurance-linked view is a bar gauge running red to green, with the business score (71) marked against a dashed "Insurance Threshold" line at 80. — [Guardz](https://guardz.com/business-owners/)
- The business-owner dashboard groups status into six categories (Digital Presence, Compromised Data, Cloud Apps, Web Browsing, Devices, Emails) and "highlights 3 critical cyber issues in a summary widget to ensure peace of mind." — [Guardz](https://guardz.com/business-owners/)
- The homepage hero shows "Security Score of 81" next to a notification "6 User Leaked Credentials." — [Guardz home-v2](https://guardz.com/home-v2/)
- Onboarding claims "Activate in Less Than 5 Mins… Onboard your clients in just 3 clicks," with connection through Microsoft 365 or Google Workspace (vendor claim). — [Guardz](https://guardz.com/); [Guardz support: getting started](https://support.guardz.com/en/articles/8006282-msp-getting-started-with-guardz)
- Remediation: the system "will offer multiple remediation options, allowing you to choose the one most suitable." Bulk fixes cover "up to 200 issues at once," run asynchronously. — [Guardz support: issues handling](https://support.guardz.com/en/articles/8078220-issues-handling); [Guardz support: automatic remediation](https://support.guardz.com/en/articles/10234744-automatic-remediation)
- Reviewers praise "clear instructions and steps" in remediation options ([Capterra](https://www.capterra.com/p/10011525/Guardz//reviews/)) and say the platform helps "communicate outcomes to SMB owners in plain language" ([G2](https://www.g2.com/products/guardz/reviews)). A small-business president on G2 asked for more tailored training and onboarding support. — [G2](https://www.g2.com/products/guardz/reviews)
- Guardz is positioned as a platform "Built for MSPs to Secure & Insure Small to Medium-Sized Businesses," managed from a central dashboard. — [CSO Online](https://www.csoonline.com/article/3686534/guardz-debuts-with-cybersecurity-as-a-service-for-small-businesses.html)
- Coro reviewers praise ease of use and "multiple cybersecurity functions in one dashboard," one saying it "consolidated our platforms down into one manageable place." Setup is easy, and users "quickly… identify vulnerabilities in their email accounts and devices." — [G2 Coro](https://www.g2.com/products/coro-cybersecurity/reviews)
- Coro cons: a "learning curve for desired level of granularity" ([Software Advice](https://www.softwareadvice.com/network-security/coronet-profile/)); requests for better malware reporting and dashboard detail ([G2 pros/cons](https://www.g2.com/products/coro-cybersecurity/reviews?qs=pros-and-cons)); a 3/5 Gartner reviewer found setup smooth but security and reporting disappointing ([Gartner](https://www.gartner.com/reviews/product/coro?marketSeoName=data-loss-prevention)). Ratings: G2 4.7/5 (231 reviews), Capterra 4.6. — [G2](https://www.g2.com/products/coro-cybersecurity/reviews); [Capterra](https://www.capterra.com/p/182368/Coronet/reviews/)

### Inferences
- Patterns worth adopting for Hakira:
  - One headline score with a meaningful reference line, such as "the level insurers expect" or "the average for businesses like yours." A score without a benchmark means little to an owner.
  - Six or fewer plain-language categories.
  - A "top 3 things to fix" widget.
  - Fix options presented as choices (do it yourself, forward to your IT person, and so on).
- A red-to-green gauge is not colorblind-safe on its own (section 6). Pair it with the number, a text label and position.
- Hakira sells direct to owners, unlike MSP-mediated Guardz and Coro. That raises the bar for in-product plain language and onboarding, because no MSP stands in between to translate.

### Gaps
- No Guardz or Coro empty-state designs, onboarding screen sequences or microcopy examples could be retrieved. Screenshots and help-center pages would need fetching, which was blocked.
- No Coro brand or UI color details.

## 4. Storytelling and narrative UI for step-by-step sequences (timelines, steppers, kill chains, MITRE layouts)

### Takeaway
Established patterns:
- ATT&CK matrix: tactics as columns (phases in order), techniques as rows.
- Kill-chain-ordered attack graphs: the progression must read in phase order.
- Two distinct views: an untimed graph and a timestamped activity timeline.
- Step-chain builders where each step carries tactic, technique, severity, evidence and timestamp.
- AI "notebook" summaries with suggested follow-ups (Purple AI).

### Cited Findings
- In MITRE ATT&CK, tactics form columns and techniques form rows, so tactics read as the phases of a multi-step attack. A kill-chain attack-graph diagram "must show the attacker's progression through phases in their proper order," with each technique tied to its allowed phases. — [arXiv 2206.10272](https://arxiv.org/html/2206.10272.pdf)
- The kill chain shows lifecycle only, while attack graphs lack a standardized action set. Combining the two is the recommended approach. — [arXiv 2206.10272](https://arxiv.org/pdf/2206.10272)
- Cambridge Intelligence demo design:
  - Techniques become graph nodes, colored by ATT&CK matrix column (tactic).
  - An animated transition moves from the graph view back into the matrix layout, so analysts can relate the graph to a familiar frame.
  - A phase's duration is overlaid on a timeline above the traffic visualization.
  — [Cambridge Intelligence](https://cambridge-intelligence.com/visualize-a-cyber-attack-with-the-mitre-attack-framework/)
- An open-source STIX tool separates an untimed "attack graph," which shows techniques in matrix context, from an "activity thread graph," which uses timestamps to produce a timeline. — [GitHub yukh1402](https://github.com/yukh1402/cti-stix-diamond-activity-attack-graph)
- Cyver Core "Attack Chains" lets pentesters assemble steps, evidence and goals into a chain. Each step has tactics, techniques, severity and timestamps, and the chain exports as a summary table for reports. — [Cyver](https://core.cyver.io/feature-highlight-attack-chains/)
- Purple AI turns natural-language questions into PowerQueries, offers one-click "quick start" hunts, summarizes results "intelligently," and suggests follow-on queries in natural language. Investigations are kept in "saved, shared, and editable notebooks," which can be exported and turned into auto-generated emails. — [SentinelOne resources](https://www.sentinelone.com/resources/general/sentinelones-purple-ai-natural-language-queries-quickstarts-and-notebooks); [SentinelOne blog](https://www.sentinelone.com/tw/blog/purple-ai-empowering-cybersecurity-analysts-with-ai-driven-threat-hunting-analysis-response/). SentinelOne's figure of "80% faster" hunting comes from a vendor survey of early adopters.

### Inferences
- Hakira's "attacker's story" maps naturally onto a vertical stepper or timeline, ordered by phase, with these elements per step:
  - A plain-language heading ("The attacker finds your old WordPress login page").
  - The verified evidence behind it (finding, source, date), shown as a chip or expandable block, following the Cyver "step + evidence" model.
  - A severity marker.
  - A "fix this to break the chain" link into the prioritized fix list.
- Showing which fix "breaks" the chain earliest gives owners a clear reason for the priority order. This is an inference drawn from the chokepoint concept in [Google SCC](https://docs.cloud.google.com/security-command-center/docs/toxic-combinations-overview?authuser=6).
- For RTL, a vertical stepper avoids the left-to-right versus right-to-left arrow ambiguity of horizontal graphs. If a horizontal path is used, mirror it to flow right to left.
- Purple AI's "summary plus suggested follow-up questions" pattern suits an AI narrative: lead with a short summary, then let the reader drill in.

### Gaps
- No usability studies on stepper-style attack timelines for non-experts were found.
- No consumer- or SMB-grade "attack story" UIs were found for direct comparison.

## 5. What makes dashboards look generic or "AI-made" (2025-2026) versus premium

### Takeaway
Practitioners agree on the tells of the "AI-made" look:
- A purple-to-blue gradient (named the single most recognizable tell).
- Inter, shadcn/ui components, Lucide icons and Tailwind defaults all at once.
- A centered hero over three equal cards.
- `rounded-2xl` cards, soft shadows and gradient buttons.
- Placeholder content ("John Doe," "Acme").

Premium in 2026 means "quiet chrome, high density":
- Near-monochrome surfaces with one accent, where color carries meaning.
- Shrinking borders and shadows.
- Deliberate typography, including monospace or tabular numerals for data.
- Progressive disclosure.

These sources are practitioner blogs and opinion, not research.

### Cited Findings
- The purple-to-blue gradient is called the single most recognizable AI tell. Other tells: a centered hero, three equal cards, "John Doe" and "Acme" placeholders, and "rounded-2xl cards, soft shadows, gradient buttons." — [DEV: AI purple problem](https://dev.to/jaainil/ai-purple-problem-make-your-ui-unmistakable-3ono); [DEV: fix the AI-generated look](https://dev.to/alanwest/how-to-fix-the-ai-generated-look-in-your-frontend-1ahh); [Kosta Canatselis, "Spot the slop"](https://world.hey.com/kostac/spot-the-slop-a-ui-designer-s-guide-to-fixing-ai-defaults-4c448c9c)
- Lovable, v0 and Claude Code "all ship with the same defaults: Inter for type, ShadCN for components, Lucide for icons, Tailwind for spacing." The layout is common because it "appears in every shadcn/ui example, every Tailwind UI screenshot, every Vercel template." — [DEV](https://dev.to/alanwest/how-to-fix-the-ai-generated-look-in-your-frontend-1ahh); [Medium, Rythmux](https://medium.com/@Rythmuxdesigner/why-your-ai-generated-ui-looks-like-everyone-elses-and-how-to-break-the-pattern-7a3bf6b070be)
- The proposed explanation is that models reproduce the training-data median: "the mean of web UI is Tailwind defaults plus a violet gradient." — [DEV](https://dev.to/jaainil/ai-purple-problem-make-your-ui-unmistakable-3ono); [UX Collective: "AI design isn't ugly, it's fluent"](https://uxdesign.cc/ai-design-isnt-ugly-it-s-fluent-and-that-s-the-problem-131b2f4eb78c?gi=720330de0898)
- Suggested fixes:
  - Change the font first, called the "single highest-leverage move."
  - Define design tokens so generated UI stays within constraints.
  - Reserve gradients for one element per page.
  — [Kosta Canatselis](https://world.hey.com/kostac/spot-the-slop-a-ui-designer-s-guide-to-fixing-ai-defaults-4c448c9c); [DEV](https://dev.to/jaainil/ai-purple-problem-make-your-ui-unmistakable-3ono)
- Counterpoint: indigo itself is "not inherently" bad, since it is "versatile, accessible, and familiar." The gradient treatment may matter more than the hue. — [DEV](https://dev.to/jaainil/ai-purple-problem-make-your-ui-unmistakable-3ono); [UX Collective "Purple"](https://uxdesign.cc/purple-6a6d1786f6c1)
- Community "anti-slop" ban lists and detection guides exist, along with tools such as Uiverse Design ("de-slop your AI generated websites"). — [GitHub ux-skill wiki: detect AI slop](https://github.com/Laith0003/ux-skill/wiki/How-to-detect-AI-slop-in-your-design); [Anti AI slop ban list](https://github.com/Laith0003/ux-skill/wiki/Anti-AI-slop-ban-list); [Product Hunt Uiverse](https://www.producthunt.com/p/uiverse-io/uiverse-design)
- Built In argues that "AI makes bad design look good enough," producing a fluent but undifferentiated sameness. — [Built In](https://builtin.com/articles/ai-design-slop-era)
- Premium trend, "quiet chrome, high density":
  - Vercel uses a monochrome system where "color = meaning."
  - "Borders, shadows, and decoration keep shrinking; information density rises."
  - Linear shows "radical restraint — near-monochrome surfaces, one accent color."
  — [AdminLTE: SaaS dashboard examples 2026](https://adminlte.io/blog/saas-dashboard-design-examples/)
- In B2B, too much whitespace "makes [a professional tool] feel inefficient." The recommended approach is three to five top-level KPIs, with granular data behind "View Details" or slide-out drawers. — [Desisle](https://www.desisle.com/resources/saas-dashboard-design-guidelines); [Tenscope](https://www.tenscope.com/ui-ux-guide/saas-dashboard-design-inspiration)
- Typography advice:
  - Pair a humanist sans for UI with monospace for data and numbers, but avoid careless mixing, which makes dashboards "feel visually unstable."
  - Headline metrics at 48px or more, primary data at 14px or more.
  — [Lollypop, July 2026](https://lollypop.design/blog/2026/july/enterprise-saas-typography-rules/); [Pixelean](https://pixelean.com/blog/20-saas-dashboard-design-examples-that-actually-work-2026/)
- Trust-sensitive products (for example banking) lean toward calm, while analytics and developer tools lean toward density. — [Muzli 2026](https://muz.li/blog/best-dashboard-design-examples-inspirations-for-2026/)

### Inferences
Concrete implications for Hakira:
- **Brand hue:** avoid a purple or violet primary with a purple-to-blue gradient. It is both the "AI" tell and SentinelOne's and Snyk's territory.
- **Typeface:** do not ship Inter, Lucide and shadcn defaults unmodified. A Hebrew-first product has a natural differentiation lever here: a distinctive, well-crafted Hebrew typeface replaces Inter.
- **Color system:** near-neutral surfaces, one brand accent, and severity colors used only for meaning.
- **Illustration:** custom illustration in the Wiz mold (optimistic, story-like) suits the "attacker's story" concept better than stock "hacker" imagery or emoji icons.
- **Real content:** use real, specific data (actual domain names, actual finding dates) instead of placeholder metrics. This is both "premium" and a trust signal for "verified public findings."
- **Density:** with a small-business audience, follow the "calm, trust-sensitive" end of the spectrum. Show fewer KPIs, keep the narrative prominent, and put detail in drawers, rather than copying Wiz-level analyst density.

### Gaps
- The Kosta Canatselis article and the pixelslop pattern catalog could not be fetched in full, so specific values (radii, exact font recommendations) are missing.
- No Nielsen Norman Group or Smashing Magazine articles specifically on "AI-looking" UI turned up in these searches.

## 6. Accessible (colorblind-safe) severity color scales for security products

### Takeaway
The consensus:
- Do not rely on red-versus-green alone; WCAG 1.4.1 (Use of Color) applies.
- Step severities by lightness as well as hue.
- Always add a redundant cue: text label, icon shape, or position or pattern.
- Base palettes on Okabe-Ito/Wong (categorical), blue/orange (ordered), or Viridis/Cividis (continuous).
- Test under protanopia and deuteranopia simulation, on dark backgrounds too.

### Cited Findings
- A real security dashboard fix: the original severity scale "was unusable with red/green colour blindness (~8% of men)." It was replaced with hues that stay distinct under simulated deuteranopia and protanopia, and the separation check was turned into an automated test. — [GitHub PR wyvern #47](https://github.com/photodoc1960/wyvern/pull/47)
- Don't rely on color alone (WCAG 1.4.1). Example of a redundant cue: an orange border around the text for "medium," and a red background with white text for "high." Icons, labels and patterns serve as additional cues. — [ADA Compliance Pros](https://www.adacompliancepros.com/blog/color-blindness-accessibility); [Medium, Courtney Jordan](https://medium.com/@courtneyjordan/designing-color-blind-accessible-dashboards-ba3e0084be82)
- "Lightness (luminance) survives every type of color blindness," so a severity ramp should step in lightness as well as hue. — [thisdevtool](https://thisdevtool.com/blog/color-blind-safe-palettes-developers)
- Okabe-Ito/Wong is the most-cited categorical default. Blue/orange pairs are recommended for ordered data, and Viridis/Cividis for continuous data. — [rgblind 2026](https://rgblind.com/blog/color-blindness-friendly-chart-colors); [ColorContrast.org](https://www.colorcontrast.org/color-blind-colors/)
- Tools exist that check palettes with CIEDE2000 distance constraints, Viénot/Brettel simulation and WCAG contrast. — [Toolsana](https://toolsana.com/tools/colorblind-safe-palette-generator/)
- GitLab moved its vulnerability-severity icon colors to design tokens and has revised its severity colors for the project security status area. These are examples of a large security product formalizing severity color as tokens. — [GitLab issue 515423](https://gitlab.com/gitlab-org/gitlab/-/issues/515423); [GitLab issue 199126](https://gitlab.com/gitlab-org/gitlab/issues/199126)

### Inferences
- Recommended approach for Hakira:
  - Severity is a separate token set from the brand palette.
  - Each level gets a distinct lightness step, a distinct icon shape (for example octagon for critical, triangle for high, circle for medium, square or dot for low), and a Hebrew text label (קריטי / גבוה / בינוני / נמוך).
  - The scale runs from dark, saturated red-magenta (critical) through orange and amber to a desaturated blue or gray (low), so the ends never depend on red versus green.
  - "Fixed" or "safe" uses blue or teal with a checkmark, not pure green alone.
- Okabe-Ito reference values for building or validating the scale: #E69F00 orange, #56B4E9 sky blue, #009E73 bluish green, #F0E442 yellow, #0072B2 blue, #D55E00 vermillion, #CC79A7 reddish purple, #000000 black. These are the widely published Okabe & Ito (2002) values; they come from my own knowledge, not from a page retrieved in this session, so verify before use. Okabe-Ito vermillion #D55E00 plus orange #E69F00 plus blue #0072B2 forms a plausible critical/high/low core, with a dark tone for critical.
- Guardz's red-to-green gauge (section 3) should not be copied as is. Use a single-hue or blue-to-orange ramp with the numeric score and a reference marker.

### Gaps
- No authoritative industry standard severity palette (for example from CVSS/FIRST, NN/g or a major vendor's public design system) was retrieved with hex values.
- The exact hex values from the wyvern PR and from GitLab's new severity tokens could not be fetched.
