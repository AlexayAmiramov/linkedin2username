# Claude Code / Agent Skills for premium, non-generic web UI (as of 2026-11-25)

Research method note: this session's network allowed raw.githubusercontent.com, code.claude.com and claude.com, but blocked the GitHub REST API (so **no star counts could be verified**), snyk.io, claudemarketplaces.com, arxiv.org and Medium/UX Planet full text. Primary-source facts below come from the repos' own README/SKILL.md/LICENSE files fetched raw from GitHub and from Anthropic's docs and blog. Facts from search snippets only are labeled "(search snippet, unverified)".

## 1. Official Anthropic frontend/UI design skills: what exists and what they instruct

### Takeaway
Anthropic ships one dedicated UI-design skill, `frontend-design` (Apache 2.0). The same SKILL.md lives in `anthropics/skills` and as a plugin in the official `claude-plugins-official` marketplace. Today's version is a ~9.4 KB "design lead" brief. It tells Claude to ground choices in the subject, write a token plan first, check that plan against a list of named "AI-generated" tells, then build with restraint and critique its own screenshots. Anthropic also publishes `web-artifacts-builder`, which uses React, Tailwind and shadcn/ui.

### Cited Findings
**Where it lives / packaging**
- `frontend-design` SKILL.md is at `skills/frontend-design/SKILL.md` in anthropics/skills. Its frontmatter description reads: "Guidance for distinctive, intentional visual design when building new UI or reshaping an existing one. Helps with aesthetic direction, typography, and making choices that don't read as templated defaults." The license is in LICENSE.txt, which is Apache License 2.0. — [anthropics/skills SKILL.md](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md)
- The same skill is packaged as a plugin in `anthropics/claude-plugins-official` at `plugins/frontend-design`. Its plugin.json gives version 1.1.1, author Anthropic. The SKILL.md there is byte-identical to the anthropics/skills copy (9,390 bytes, compared with `cmp`). The marketplace entry says: "Create distinctive, production-grade frontend interfaces with high design quality. Generates creative, polished code that avoids generic AI aesthetics." — [claude-plugins-official marketplace.json](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json); [plugin.json](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/frontend-design/.claude-plugin/plugin.json)
- `anthropics/claude-code/plugins` is now only a pointer. The README says "Anthropic's plugins are developed in claude-plugins-official". The `claude-code-plugins` marketplace in that repo is deprecated according to the docs. — [claude-code plugins README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md); [Anthropic's marketplaces doc](https://code.claude.com/docs/en/plugins/anthropic-marketplaces.md)
- The anthropics/skills README includes this disclaimer: "These skills are provided for demonstration and educational purposes only." — [anthropics/skills README](https://github.com/anthropics/skills)

**What the current SKILL.md instructs (primary source, paraphrased closely)**
- Persona: "the design lead at a design studio known for giving every client a distinct visual identity". The client "has already rejected proposals that felt cliché or templated". Claude should "take aesthetic risk if justified." — [SKILL.md](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md)
- Grounding: identify the subject, audience and primary job, and confirm them with the client. The text says "a dashboard for financial analysts" will look very different from a toy for kids. Use real content throughout. — same
- Hero: open with "the most characteristic thing in the subject's world". The text warns that "a big number with a small label, supporting stats, and a gradient accent is the default treatment". — same
- Typography: one or two families, chosen deliberately and not the defaults. Use a type scale per *The Elements of Typographic Style*. Keep lines under 80 characters. It bans common tells: accenting a single word in a headline, all-caps labels, and unnecessary labels above content. — same
- Structure: structural devices like numbered markers (01/02/03) are allowed only if the content really is a sequence. — same
- Motion: use non-user-triggered motion sparingly, and prefer "a single orchestrated moment". Per-section fade-and-slide-ups and hover effects on every card "read as AI-generated". Motion that responds to user actions is welcome. — same
- Calibration list of five "AI-generated design" clusters:
  1. Cream #F4F1EA with a serif and a terracotta accent near #D97757, which it calls "Anthropic's own Claude-interaction accent".
  2. Near-black with an acid-green or vermilion accent.
  3. A broadsheet layout with hairline rules.
  4. "The SaaS-card kit": identical rounded cards, one radius everywhere, rgba(0,0,0,.1) shadows, gradient washes.
  5. Template chrome: tracked ALL-CAPS eyebrows, 'A · B · C' meta strings, spaced em dashes, #0B0B0B/#111 near-blacks, monospace data labels, '→' on buttons.

  The skill adds that "the brief's own words always win". — same
- Process:
  - Two passes. First, a token plan: 4–6 named hex colors, typefaces and their roles, a layout concept with ASCII wireframes and alignment, and principles.
  - Review the plan against the brief and revise anything generic, saying what changed. Only then write code.
  - It warns about CSS specificity conflicts. — same
- Restraint and quality floor:
  - "Spend your boldness in one place."
  - The floor: responsive to mobile, visible keyboard focus, reduced motion respected, accessible, harmonious palettes.
  - Self-critique with screenshots ("a picture is worth 1000 tokens"). Chanel's advice: "remove one accessory". — same
- UX writing: write from the user's view, use active voice, and make CTAs specific ("Save changes," not "Submit"). Keep names consistent ("Publish" leads to "Published"). Errors should be specific and not apologize. Empty states should invite action. Use sentence case. — same

**Original version / blog rationale (Nov 12, 2025)**
- Anthropic's post "Improving frontend design through Skills" (Nov 12, 2025) names the problem "distributional convergence". Unguided LLM landing pages "almost always conform to Inter fonts, purple gradients on white backgrounds, and minimal animations." — [Claude blog](https://claude.com/blog/improving-frontend-design-through-skills)
- The post publishes a "~400 token" `<frontend_aesthetics>` prompt covering four areas:
  - Typography: avoid Inter, Roboto, Arial and system fonts.
  - Color and theme: use CSS variables; "dominant colors with sharp accents"; take inspiration from IDE themes and cultural aesthetics.
  - Motion: CSS-only for HTML, the Motion library for React, "one well-orchestrated page load with staggered reveals".
  - Backgrounds: layered gradients and patterns.

  It ends with a warning that Claude still converges on choices like Space Grotesk. — same
- A sample typography prompt in the post says "Never use: Inter, Roboto, Open Sans, Lato". It suggests fonts such as JetBrains Mono, Space Grotesk, Playfair Display, IBM Plex, Bricolage Grotesque and Newsreader, extreme weight contrasts (100/200 vs 800/900), and "size jumps of 3x+". — same
- The same post introduces `web-artifacts-builder`. It uses scripts to scaffold a React repo with Tailwind CSS and shadcn/ui, then bundles everything with Parcel into a single HTML file. — same

### Inferences
- The current SKILL.md has moved past the 2025 blog prompt. The blog's own examples (Space Grotesk, JetBrains Mono, staggered page-load reveals, dark themes with sharp accents) now look like the "tells" that the new version lists as defaults to avoid. The current skill favors restraint, grounding in the subject, and a plan-then-critique process over "bold fonts and gradients."
- For a data-heavy React dashboard, the parts that matter most are the "financial analysts dashboard" grounding, the warning against the "SaaS-card kit", the quality floor, and the UX-writing rules. The skill has no dashboard- or chart-specific rules.

### Gaps
- I could not list the full `anthropics/skills/skills/` directory, because the GitHub API was blocked. Other design-adjacent Anthropic skills (e.g. theme-factory, canvas-design, brand-guidelines) are therefore not verified here. Only `frontend-design` and `web-artifacts-builder` (via the blog) are confirmed.
- Star count and install count for anthropics/skills could not be verified. A search snippet cited "277K+ installs as of early 2026" for frontend-design, which is **unverified**.

## 2. Leading community skills/plugins for UI design, design systems, dashboards, data viz and accessibility

### Takeaway
Four community projects come up repeatedly in 2026 roundups, and each was verified from its own repo:
- **Impeccable** (pbakaus, Apache 2.0, forked from Anthropic's frontend-design): steering commands, critique and audit, and a deterministic 62-rule "slop detector" with a hook.
- **UI UX Pro Max** (nextlevelbuilder, MIT): a searchable design-intelligence database run by Python scripts, with explicit dashboard and chart guidance.
- **Taste Skill** (Leonxlnx, MIT): an opinionated kit for company websites, with Node scripts and headless-Chrome checks.
- **Vercel's `web-design-guidelines`** (vercel-labs/agent-skills): a 100+ rule UI audit.

Star counts could not be verified in this session.

### Cited Findings
**Impeccable — github.com/pbakaus/impeccable**
- Tagline: "The design vocabulary for your coding agent. Steer with `polish` and `bolder`, review with `critique` and `audit`, and catch AI slop before it ships." License: Apache 2.0. The README says it "started from Anthropic's frontend-design skill." — [Impeccable README](https://github.com/pbakaus/impeccable)
- What it adds:
  - Steering commands: `bolder`, `quieter`, `distill`, `colorize`, `typeset` and others.
  - `critique`, which scores against usability heuristics.
  - `audit`, which checks accessibility, performance, theming and responsiveness, with findings ranked P0–P3.
  - A "slop detector" with "62 deterministic rules … No LLM, no API key". It also has a design hook that "scans every UI file your agent edits". — same
- The README names the slop it targets: "Inter for everything. Purple-to-blue gradients. Cards nested in cards, gray text on colored backgrounds, a rounded-square icon tile above every heading." — same
- CLI: `npx impeccable detect src/`, `detect https://…` (uses the installed Chrome), and `--sarif` / `--github` output for CI. For TSX/JSX it applies pattern rules only. Contrast and tiny-text checks need a rendered URL. — same
- Evidence offered: a side-by-side README image with the same model ("Fable 5.1") and the same brief, without vs with Impeccable, plus a "Neo Mirai case study". — same
- The README says it is "strongest on interfaces that already exist: point it at a page or a component and iterate." — same
- Supports Claude Code, Cursor, Codex CLI, Copilot, Gemini CLI and many more. — same

**UI UX Pro Max — github.com/nextlevelbuilder/ui-ux-pro-max-skill**
- Described as "An AI skill that provides design intelligence for building professional UI/UX across multiple platforms and frameworks." License: MIT (Copyright 2024 Next Level Builder). — [UUPM README](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill); [LICENSE](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill/blob/main/LICENSE)
- Content claimed in the README:
  - 80 searchable UI styles (51 active)
  - 194 color palettes
  - 74 font pairings
  - **25 chart types "for dashboards and analytics"**
  - 141 UX guidelines
  - 194 industry reasoning rules, with anti-patterns (e.g. "AI purple/pink gradients" for banking)
  - official systems such as Fluent 2 and Shopify Polaris
  - RTL support flags
  - a pre-delivery checklist (e.g. prefers-reduced-motion) — same
- Mechanism: Python 3 scripts. For example, `python3 .claude/skills/ui-ux-pro-max/scripts/search.py "fintech dashboard" --design-system --tokens css` outputs a design system as `:root` CSS variables or W3C DTCG tokens. `--persist` writes a Master file plus per-page overrides such as `dashboard.md`. The README says the scripts are "standard library only — the scripts install nothing and make no network calls." — same
- Evidence offered: an ops-dashboard before/after hosted at skill-fixture-before.theroost.dev and ui-ux-pro-max-after.theroost.dev (not visited). — same
- Known issue: Marketplace installs before v2.5.1 failed with "Zip file contains a symbolic link". — same

**Taste Skill — github.com/Leonxlnx/taste-skill**
- The README describes it as "an Agent Skill that makes coding agents build professional company websites at the figma.com and x.ai level instead of assembling a generic landing page" (version `tasteskill 2.5.1`). License: MIT (Copyright 2026 Leonxlnx). — [Taste Skill README](https://github.com/Leonxlnx/taste-skill); [LICENSE](https://github.com/Leonxlnx/taste-skill/blob/main/LICENSE)
- Mechanism:
  - Node 22+ scripts. `start.mjs` assigns a palette and a Google Fonts pairing by page kind.
  - A starter HTML/CSS system ("one section per screen at desktop").
  - A vetted photo library.
  - Shaders only on software, tech and gaming pages.
  - `consistency.mjs`, `perf.mjs` and `shoot.mjs` render the page in headless Chrome at 1440/1024/768/390 px and print PASS/WARN/FAIL.
  - A "finish gate" that also acts as a **Stop hook**. — same
- Scope: built for **company websites and landing pages**, not app dashboards. Older variants (`high-end-visual-design`, `minimalist-ui`, `industrial-brutalist-ui`, etc.) moved to `Leonxlnx/taste-skill-classics`. — same
- Commercial signals: GitHub sponsors and a Kimi API referral ("10% bonus API credits"). The README includes a disclaimer about crypto tokens that impersonate the project. — same

**Vercel — github.com/vercel-labs/agent-skills**
- `web-design-guidelines` "Audits your code for 100+ rules covering accessibility, performance, and UX". Categories: accessibility, focus states, forms, animation (prefers-reduced-motion), typography (tabular-nums), images, performance (virtualization), URL state, dark mode, touch, i18n (Intl.NumberFormat). — [vercel-labs/agent-skills README](https://github.com/vercel-labs/agent-skills)
- `react-best-practices`: "40+ rules across 8 categories", covering waterfalls, bundle size, and re-render optimization. — same
- The repo is also behind the `npx skills` installer CLI used by other skills. — [Taste Skill README](https://github.com/Leonxlnx/taste-skill)

**Other relevant entries in the official marketplace (claude-plugins-official; 317 plugins in marketplace.json)**
- `playwright` (Microsoft): browser automation and screenshots, useful for the screenshot self-critique loop that frontend-design asks for. Also `chrome-devtools-mcp`, `figma` (design tokens and components from Figma files), `superdesign` (design on the Superdesign canvas), and `playground`. — [marketplace.json](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json)

**Roundups and popularity (secondary, mostly vendor blogs)**
- 2026 roundups that rank design skills: Snyk ("top Claude skills for UI/UX engineers"), Composio ("10 best design skills"), daisyUI ("best design skill 2026"), Superdesign, Firecrawl, designrevision, and claudemarketplaces.com ("Most-installed Claude Code Design & UI/UX skills (November 2026)"). — [Snyk](https://snyk.io/articles/top-claude-skills-ui-ux-engineers/); [Composio](https://composio.dev/blog/top-design-skills); [daisyUI](https://daisyui.com/claude-code/best-design-skill-2026/); [claudemarketplaces](https://claudemarketplaces.com/best/skills/design-ui) (all search snippets only; full pages blocked)
- Search-snippet consensus: Anthropic's frontend-design is the default pick. UI UX Pro Max, Taste Skill, Vercel Web Design Guidelines and Impeccable are the common alternatives. (Search snippet, unverified.) Many of these lists come from vendors with commercial interests (daisyUI, Superdesign, Composio).

### Inferences
- For a **premium React dashboard**, the strongest stack is:
  - Anthropic `frontend-design` for direction (official, small, Apache 2.0, no scripts).
  - UI UX Pro Max or Claude's own dataviz guidance for chart and palette choices. UUPM is the only verified community skill with explicit dashboard and chart content.
  - Impeccable or Vercel `web-design-guidelines` as an audit pass.
  - Playwright for screenshots.
- Taste Skill fits the marketing site better than the dashboard.
- Impeccable descends from Anthropic's skill. Its main value is review and detection on existing code, which suits iterating on a dashboard.

### Gaps
- **Star counts, fork counts and recent commit activity could not be verified for any repo.** The GitHub API and shields.io were blocked. Check them on github.com before deciding.
- I found no verified dedicated community skill for dashboards or data viz (e.g. Recharts/visx/Tremor-specific) or for motion. "awesome-claude-skills" lists (e.g. travisvn/awesome-claude-skills, ComposioHQ/awesome-claude-skills) are mentioned in roundups but were not verified in this session.
- I did not inspect the actual SKILL.md text of Impeccable, UUPM or Taste Skill, only their READMEs.

## 3. How to install skills in Claude Code (exact commands)

### Takeaway
There are three ways to install: (a) plugin marketplaces via `/plugin` or `claude plugin install <plugin>@<marketplace>`, (b) copying a folder with `SKILL.md` into `~/.claude/skills/<name>/` (personal) or `.claude/skills/<name>/` (project, commit it so teammates get it), or (c) vendor CLIs (`npx skills add …`, `npx impeccable install`, `uipro init`). The official marketplace is added automatically.

### Cited Findings
**Skill locations (official docs)**
- Personal: `~/.claude/skills/<skill-name>/SKILL.md` applies to "All your projects on this machine, but not Cowork or cloud sessions".
- Project: `.claude/skills/<skill-name>/SKILL.md` applies to "Sessions in this repository … Commit it so your team gets it too".
- There are also Enterprise (managed settings dir), Nested (`<subdir>/.claude/skills`) and `--add-dir` locations.
- Precedence: enterprise > personal > project. — [Claude Code skills docs](https://code.claude.com/docs/en/skills.md)
- Claude Code watches skill directories and picks up changes mid-session. The folder name becomes the `/command`. Don't name a skill folder `synced`. — same
- Cloud sessions don't read `~/.claude/skills/`. For cloud use, commit the skill to the repo's `.claude/skills/` or enable it on claude.ai. — same

**Plugin marketplace commands**
- Official marketplace (`claude-plugins-official`): "Claude Code adds it the first time you start an interactive terminal session". Install Anthropic's design plugin with `/plugin install frontend-design@claude-plugins-official` in a session, or `claude plugin install frontend-design@claude-plugins-official` in the shell. The general pattern comes from the docs: `/plugin install commit-commands@claude-plugins-official` and `claude plugin install <plugin>@claude-plugins-official`. — [Install plugins doc](https://code.claude.com/docs/en/plugins/install.md); [Anthropic's marketplaces](https://code.claude.com/docs/en/plugins/anthropic-marketplaces.md)
- In a session, `/plugin install` opens a details pane where you choose a scope: user ("every project on this machine"), project ("all collaborators on this repository"), or local ("you, in this repo only"). Verify with `claude plugin list`. — [Install plugins doc](https://code.claude.com/docs/en/plugins/install.md)
- anthropics/skills as a marketplace: `/plugin marketplace add anthropics/skills`, then `/plugin install example-skills@anthropic-agent-skills` (frontend-design is part of example-skills). — [anthropics/skills README](https://github.com/anthropics/skills)
- UI UX Pro Max: `/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill`, then `/plugin install ui-ux-pro-max@ui-ux-pro-max-skill`. Alternatives: `npx ui-ux-pro-max-cli init --ai claude` (add `--global` for `~/.claude/skills/`), or `gh skill install nextlevelbuilder/ui-ux-pro-max-skill .claude/skills/ui-ux-pro-max`. The README warns that the old `uipro-cli` npm package is stale. — [UUPM README](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
- Taste Skill: `npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"`, or `/plugin marketplace add Leonxlnx/taste-skill`, then `/plugin install taste-skill@taste-skill`. Requires Node 22+ and Chrome/Edge/Chromium. — [Taste Skill README](https://github.com/Leonxlnx/taste-skill)
- Impeccable: `npx impeccable install` from the project root (detects tools and offers the design hook), then `/impeccable init`. Or `/plugin marketplace add pbakaus/impeccable` and install from `/plugin`. The README notes "A manual copy skips the design hook and subagents." — [Impeccable README](https://github.com/pbakaus/impeccable)
- Search snippets also cite `npx -y skills add anthropics/skills --skill frontend-design --agent claude-code` for the skills.sh CLI (unverified syntax; the skills.sh badge appears in the anthropics/skills README). — [anthropics/skills README](https://github.com/anthropics/skills)
- Manual copy, from the docs example: `mkdir -p ~/.claude/skills/<name>` and save the file as `~/.claude/skills/<name>/SKILL.md`. — [Claude Code skills docs](https://code.claude.com/docs/en/skills.md)

### Inferences
- For a founder's team, the most reproducible option is project-scope install, or committing a reviewed copy of the skill folder into the repo's `.claude/skills/`, so the version is pinned and code-reviewed. Plugin auto-update can change files after review (see §4).

### Gaps
- I did not test the `npx skills add` CLI or confirm its flags directly.

## 4. Security risks of third-party skills and recommended review practices

### Takeaway
Plugins "can execute arbitrary code on your machine with your user privileges." Hooks, monitors and MCP/LSP servers run **outside** Claude Code's sandbox and permission rules. Skill text enters Claude's context as instructions, which is a prompt-injection vector. Academic scans of public skill registries found a meaningful rate of vulnerable or malicious skills. Anthropic's advice is to install only from trusted sources and to read every bundled file, especially scripts, hooks, `.mcp.json`, `bin/`, and any network calls. Several of the shortlisted design skills ship scripts or hooks.

### Cited Findings
**Anthropic primary guidance**
- "A Claude Code plugin you install can execute arbitrary code on your machine with your user privileges." — [Plugin security and trust](https://code.claude.com/docs/en/plugins/security.md)
- What a plugin can carry: hooks (shell commands at lifecycle points), monitors (background shell commands), mods (JavaScript), MCP/LSP servers, a `bin/` directory added to PATH, and skills, commands and agents that "enter Claude's context as instructions". — same
- "Claude Code runs hooks, monitors, MCP servers, LSP servers, and the processes a mod starts outside the sandbox". Permission rules cover only Claude's tool calls. — same
- Auto-update: "Claude Code updates that plugin in the background, so the files you reviewed can change on disk." — same
- Recommended review steps:
  1. `claude plugin marketplace list` to check the source.
  2. Read the `/plugin` details pane ("Will install" list).
  3. Read `hooks/hooks.json`, `.mcp.json` and every file in `bin/`.
  4. Run `claude --plugin-dir <dir> plugin details <name>` for a "Component inventory".
  5. Uninstall with `claude plugin uninstall <plugin> --scope …`. Cached files stay in `~/.claude/plugins/cache/` for 14 days. — same
- Marketplace tiers: official names (e.g. `claude-plugins-official`, `anthropic-agent-skills`) are accepted only from `github.com/anthropics/`. The community tier is `claude-community`, which pins entries to commit SHAs. Everything else is third-party. The install warning states that Anthropic "cannot verify that they will work as intended or that they won't change." — same
- Organizations can allowlist or blocklist marketplace sources, force-enable plugins, and restrict hooks to managed ones through managed settings. — same
- Anthropic engineering blog: "malicious skills may introduce vulnerabilities in the environment where they're used or direct Claude to exfiltrate data and take unintended actions. We recommend installing skills only from trusted sources." When a source is less trusted, "thoroughly audit it", "paying particular attention to code dependencies and bundled resources like images or scripts" and to "instructions or code within the skill that instruct Claude to connect to potentially untrusted external network sources." — [Equipping agents for the real world with Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

**Risk surface of the shortlisted design skills (from their own READMEs)**
- Impeccable: "**Hooks run outside model approval.** In Claude Code, installed command hooks run even when you deny the model's own commands, so the first edit can download the engine." It runs a "self-contained engine binary" that "downloads once into `~/.impeccable/bin/`". **Telemetry:** "When a new design starts, the skill fetches a set of visual directions from the impeccable.style catalog. Turning telemetry off doesn't stop that request". Live mode can run the `codex` or `claude` CLI. — [Impeccable README](https://github.com/pbakaus/impeccable)
- Taste Skill: Node scripts, a Stop hook ("The finish gate (also a Stop hook)"), and headless Chrome. The README says "none installs anything" and that it "uses no API keys". — [Taste Skill README](https://github.com/Leonxlnx/taste-skill)
- UI UX Pro Max: Python scripts that are, per the README, "standard library only — the scripts install nothing and make no network calls". The README also recommends installation through a global npm CLI (`ui-ux-pro-max-cli`), which is a supply-chain dependency. — [UUPM README](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
- Anthropic frontend-design: a single SKILL.md plus LICENSE, with no scripts or hooks in the skill folder (based on the files fetched; the folder listing was not verified via the API). — [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/frontend-design)

**Ecosystem studies (search snippets of arXiv papers; full text blocked; treat numbers as unverified)**
- arXiv 2601.10338: collected 42,447 skills from two marketplaces and analyzed 31,132. It reports a 14-pattern vulnerability taxonomy (prompt injection, data exfiltration, privilege escalation, supply chain) and that ~26.1% contained at least one vulnerability. — [arXiv 2601.10338](https://arxiv.org/abs/2601.10338)
- arXiv 2602.06547: verified 98,380 community-registry skills and confirmed 157 as malicious (632 vulnerabilities). 93.6% were removed within 30 days of disclosure. It notes that installed skills get full local user privileges with minimal isolation. — [arXiv 2602.06547](https://arxiv.org/abs/2602.06547)
- arXiv 2605.28588: reports that all confirmed malicious skills had malicious code patterns and 91% also used prompt injection. — [arXiv 2605.28588](https://arxiv.org/pdf/2605.28588)
- Counterpoint, arXiv 2603.16572 (238,180 skills): marketplace scanners flag up to 46.8% of skills as malicious, a figure the paper treats as a false-positive problem. — [arXiv 2603.16572](https://arxiv.org/abs/2603.16572)
- A Snyk article on UI/UX skills was cited in roundups for finding prompt injection in a large share of analyzed skills. The exact figure was not verified because snyk.io was blocked. — [Snyk](https://snyk.io/articles/top-claude-skills-ui-ux-engineers/)

### Inferences
- Practical checklist for the founder:
  1. Prefer `claude-plugins-official` or anthropics/* first.
  2. For community skills, clone the repo and read SKILL.md, every script, `hooks/hooks.json` and `.mcp.json`, and look for network calls and `curl | sh` patterns.
  3. Pin a commit by vendoring the folder into `.claude/skills/` instead of relying on auto-update.
  4. Accept hooks only after reading them.
  5. Run in a sandbox or devcontainer the first time.
  6. Re-review on update.
- Of the shortlist, Anthropic's skill has the smallest attack surface (text only). UUPM is next (stdlib Python, no network calls claimed). Taste Skill runs local Node and headless Chrome plus a Stop hook. Impeccable has the largest surface: a downloaded binary, hooks outside approval, and an outbound catalog fetch.

### Gaps
- I did not audit the actual code of any community skill. The "no network calls" and "installs nothing" claims are the authors' own and were not verified.

## 5. Evidence that these skills measurably improve UI output

### Takeaway
The evidence is qualitative. It consists of vendor before/after screenshots (Anthropic, Impeccable, UUPM) and a few subjective blogger comparisons whose verdicts conflict. I found no controlled, quantitative benchmark of UI quality.

### Cited Findings
- Anthropic shows before/after pairs for three cases: a SaaS landing page, a blog, and an **admin dashboard**. The dashboard went from "standard UI components with minimal visual hierarchy" to "bold typography, cohesive dark theme, and purposeful motion". The post claims the skill "dramatically improves frontend output". These are qualitative screenshots with no metrics. — [Claude blog](https://claude.com/blog/improving-frontend-design-through-skills)
- Impeccable's README shows a same-model, same-brief comparison (a guesthouse landing page). Without the skill: "cream page, thin serif, italic accent, pill buttons". With it: a page built around one picture. — [Impeccable README](https://github.com/pbakaus/impeccable)
- UUPM's README links to a live before/after of an ops dashboard. — [UUPM README](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
- UX Planet, "I Tested 3 Claude Code Skills for Web Design" (member-only; search snippets only): rated UI/UX Pro Max 4/5 and Taste Skill 4.5/5. It said Frontend Design's output "required sufficient refinement and didn't feel particularly polished". Taste Skill "consumed nearly 30% of my daily usage quota (almost twice as much as UI/UX Pro Max and three times as much as Frontend Design)." — [UX Planet](https://uxplanet.org/i-tested-3-claude-code-skills-for-web-design-which-one-is-best-521137220dc1) (unverified snippet)
- A second UX Planet test (home-cleaning landing page) found that UUPM "produces good design but works slower than frontend-design and consumes more tokens". It also reports frontend-design taking about half the time and tokens of UUPM. — [UX Planet](https://uxplanet.org/ive-tested-3-popular-claude-code-skills-for-web-design-24b7866e05a7) (unverified snippet)
- Claude Code supports plugin evals that compare against a no-plugin baseline with `claude plugin eval`. A team could use this to measure a skill on its own briefs. — [docs index](https://code.claude.com/docs/llms.txt) (page title: "Test plugins with evals")

### Inferences
- The two comparisons disagree on frontend-design. One ranks it lowest on polish, while others call it the default pick and note it is the cheapest in time and tokens. The skill was rewritten after the 2025 posts (see §1), so older comparisons may not reflect today's version.
- The best evidence for a founder is a quick A/B on their own dashboard brief: same prompt with no skill vs with each skill, compared on screenshots and token use.

### Gaps
- I found no quantitative, blinded or multi-rater benchmark of UI quality with vs without skills.
- I could not read the full UX Planet, Snyk, Composio or daisyUI articles because they were paywalled or blocked, so their methodology is unknown.
