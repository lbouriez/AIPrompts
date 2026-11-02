---
id: website.existing.01
version: "1.1"
status: validated
validation_basis: "User-tested audit and visual-review workflow; consolidated revision not yet re-run end to end."
site_mode: existing
writes: design-review-only
---

# Prompt 01 — Existing website audit and visual Design Studio

**Status: VALIDATED — workflow.** This merges the original tested Prompt 1 and Prompt 1.5. The exact consolidated edition has not been re-run. Execute the instructions below; do not simply summarize them.

## Mission

Act as a senior product designer, UX strategist, and frontend prototyping engineer.

Analyze this **existing, working website** and turn the findings into a clear, runnable visual proposal. I want to see what is wrong, compare credible alternatives, and understand exactly what should change. I do not want more Markdown reports.

Perform discovery before designing. Keep the analysis deep, the explanations brief, and the output visual. Do not modify the production application or implement any option during this phase.

## Context and defaults

Use the target repository specified by the user, or the current application repository when unambiguous. Do not analyze the prompt library as the website. Follow repository instructions, including `AGENTS.md` or equivalent, and inspect Git status without overwriting unrelated changes.

Read the actual target source code and trace its architecture, routes, components, styles, and integrations. Browser rendering is complementary evidence, not a substitute for repository inspection. If the target or its source is unavailable, request the missing access rather than producing a website audit from screenshots alone. All generated code and review assets belong in the target repository, never in this prompt library.

Discover the business, audience, primary action, stack, routes, languages, branding, assets, integrations, and constraints from existing evidence. Use provided user context before asking questions. Label uncertain inferences; do not invent business facts. Ask only for essential information that cannot be discovered and would materially alter the design. Otherwise proceed with visible assumptions.

Default studio location: `design-review/` in the target repository. Reuse an existing equivalent rather than creating competing studios. Read old `docs/website-improvement/` reports when present, but treat them as evidence to verify—not unquestionable instructions. Do not require or recreate them.

## 1. Understand and inventory the real site

Inspect source, configuration, components, styles, content, assets, routing, rendering strategy, and available tests. Establish:

- What the business offers, to whom, and the primary conversion journey.
- Current public pages, distinct page templates, locales, navigation, and user states.
- Reusable components and design tokens; elements that define recognizable branding.
- Functional contracts to preserve: forms, authentication entry points, pricing, checkout, subscriptions, search, analytics events, consent, external links, and integrations where applicable.
- Current accessibility, responsiveness, performance, and SEO risks relevant to design.
- What is observed, inferred, unavailable, or explicitly out of scope.

Inventory all discoverable public routes, grouping large collections by template. Exclude authenticated/private areas from this redesign unless requested. Show the inventory and coverage in the studio; do not imply all pages have been inspected when only samples were reviewed.

When browser access is available, start the current site using its documented commands and inspect rendered pages. Distinguish the live site from a local revision when they differ. Do not submit production forms, change account data, or trigger payments while inspecting.

Record existing baseline test failures separately from any issues introduced by the studio.

## 2. Capture evidence and identify useful changes

Capture real current-site screenshots for the homepage and the highest-impact page templates. Use consistent reference viewports:

- Desktop: 1440 × 900 CSS pixels.
- Mobile: 390 × 844 CSS pixels.
- Tablet: 768 × 1024 CSS pixels for representative layout validation.

Record viewport, device pixel ratio, browser, locale, page state, and capture source. Prefer the same environment for later comparisons. Include full-page views and section crops where they clarify problems. Avoid exposing private data.

Evaluate first-screen clarity, information hierarchy, navigation, copy, CTAs, trust, forms, typography, spacing, imagery, component consistency, mobile interactions, and accessibility. Also flag design-related SEO and performance risks without turning this phase into a production optimization task.

If external browsing is available, review three relevant competitor or reference sites. Record the actual source and a short observation for each. Learn from effective patterns without copying branding, content, or layouts wholesale. If browsing or screenshots are unavailable, show that limitation; never fabricate research, screenshots, or metrics.

Create stable issue IDs such as `UI-001`. Each issue must have:

- Page/section and real screenshot or code reference.
- Observed problem, evidence confidence, and user impact.
- Specific proposed change and the mockup that demonstrates it.
- Priority, implementation complexity, dependency, and observable acceptance criterion.

Use priorities consistently: P0 blocks a critical journey; P1 causes major friction or misunderstanding; P2 improves meaningful consistency/usability; P3 is optional polish. Do not call a stylistic preference a P0.

Keep findings understandable. “On mobile, the menu covers the submit button” is useful. “Enhance digital experience” is not.

## 3. Create three distinct, high-fidelity directions

Use stable IDs **A**, **B**, and **C**. Adapt their character to the actual business rather than imposing a generic SaaS look:

- **A — Refined evolution:** retain recognizable branding while improving clarity and consistency.
- **B — Stronger visual identity:** a more distinctive composition and presentation without sacrificing usability.
- **C — Focused simplicity:** prioritize essential content, navigation, and the primary action.

They must differ in meaningful layout, hierarchy, typography, and storytelling—not merely color or border radius. Recommend one and explain the tradeoffs. Recommendation is not approval.

For each direction, build the complete responsive homepage and up to two additional high-impact page templates. On small sites, cover all main pages when practical. Keep comparison scope equivalent across alternatives. Show all unmocked routes explicitly; never quietly reduce an option to a hero-only sketch.

Include the navigation, hero, supporting content, real benefits, primary CTA, necessary forms or representative states, and footer. Use only sections that help this business. Do not force testimonials, pricing grids, FAQs, or “how it works” blocks where they add no value.

Use real logos, product screenshots, content, and permitted assets. Rewrite unclear copy while preserving factual meaning, actual prices, product capabilities, and supported languages. Do not invent testimonials, customers, ratings, claims, scarcity, certifications, or capabilities. Mark missing assets visibly in the studio and flag them as implementation dependencies rather than hiding fabricated replacements.

Define exact typography, font availability, colors, spacing, containers, breakpoints, borders, shadows, icons, image crop behavior, buttons, inputs, and interaction states. Include focus, hover, loading, disabled, error, and success states where relevant. Respect reduced motion and avoid decorative effects that compromise clarity or performance.

Build runnable frontend prototypes, not image-only mockups. Prefer the site's existing frontend technology when it can be used independently. Reuse pure presentational code/assets safely, but do not import modules that initialize production services, tracking, or authentication. Use isolated copies or adapters when needed.

Use safe local fixtures for interactions. Demo forms must not send real messages or collect real data. Do not connect prototypes to live payment, account, analytics, or customer services.

## 4. Build one understandable Design Studio

Create a lightweight, local-only studio in `design-review/`. Keep it outside the production build, deployment, routing, and search sitemap. Do not change root application dependencies, lockfiles, or configuration just to host it. Use isolated tooling where required; do not install global tools. Do not create new Markdown files.

Inspect actual build/deployment rules; `.gitignore` alone does not prevent publication. If the default location is deployed, use a non-deployable location inside the target repository. If no safe location exists without production configuration changes, report the blocker before creating the studio; do not move it into the prompt library or outside the target repository.

The studio should offer these views, using concise explanations rather than walls of text:

**Overview:** what the site does, its main user journey, five to ten important findings, current screenshots, scope, assumptions, and the recommended direction.

**Current versus proposed:** side-by-side views or an overlay, issue markers, short explanations, and links to the relevant prototype. Label current evidence and proposed designs clearly. Never simulate an unavailable “before” view.

**Options A/B/C:** switch between full responsive prototypes, page templates, and desktop/mobile views. Include direct links that open each prototype without studio navigation; these are the later screenshot targets. Device previews must render at the stated CSS viewport width, not just shrink a desktop screenshot.

**Design system:** real rendered examples of tokens, type scale, components, and interaction states for each option, with source references.

**Issues and implementation steps:** a filterable, prioritized board connecting issue → proposed visual change → task → acceptance criterion. Show affected routes/components, dependencies, complexity, and coverage gaps. Include relevant accessibility, SEO, and performance follow-up items without pretending they are fixed.

Keep the studio itself simple. Spend the effort on the website mockups and useful comparisons, not on building an elaborate dashboard platform.

## 5. Preserve an actionable, machine-readable handoff

Store concise structured data in `design-review/design-manifest.json`, or adapt an existing equivalent while preserving compatibility. Use it to power the studio, not as a hidden replacement for four reports.

Include, at minimum:

- Schema version and `siteMode: "existing"`.
- Verified project context, assumptions, protected behaviors, launch instructions, and coverage.
- Stable option IDs and the recommended option.
- Per-option prototype routes and production-route/template mappings.
- Exact component, style/token, asset, and content source paths.
- Responsive breakpoints, comparison viewports, screenshot references, and important states.
- Issue/task IDs, priorities, dependencies, proposed fixes, and acceptance criteria.
- An approval object initially unset: selected option, approved revision, approved routes/states, explicit exceptions, and approval status.
- A place for subsequent implementation/verification results without overwriting design references.

Use relative paths where practical, verify that references exist, and avoid secrets. Separate recommendations, user approval, and implementation results. Merely viewing or selecting an option tab is not approval to modify the application.

Make the approved design reusable. Its exact code, assets, tokens, content, and page mappings should let Step 2 reproduce it without guessing. Do not rely on a screenshot alone or on remembered chat context.

## 6. Verify before handing it over

Run the studio, inspect each option on desktop and mobile, and check representative tablet/intermediate widths. Confirm that fonts and assets load, menus work, preview routes open, content is not clipped, and the issue links point to actual mockups. Run applicable studio build/lint/type checks.

Confirm that production application files, dependency manifests, routing, and configuration remain unchanged. Ignore only generated studio caches through studio-local settings when needed; do not alter unrelated repository files.

If browser tooling is unavailable, still build the prototypes and expose exact launch instructions, but label screenshot comparisons and visual validation **not tested**. Never claim that a URL is running or a screenshot exists without verifying it.

## Output and stop condition

The deliverable is the runnable studio, its prototype code/assets, structured handoff, and honest evidence. No new Markdown audit, roadmap, or implementation reports.

End with a short response containing the launch command and working directory, the verified local URL or clearly labeled expected URL, a brief A/B/C comparison, the recommendation, the five highest-priority issues, and any coverage/tool limitations.

Tell me to review the visual options and approve an option plus scope before running Step 2. **Stop here. Do not implement any option, commit, push, deploy, or change external services.**
