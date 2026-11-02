---
id: website.new.01
version: "1.1"
status: not-validated
validation_basis: "New-site starting point; not yet tested by the user."
site_mode: new
writes: design-review-only
---

# Prompt 01 — New website brief and visual Design Studio

**Status: NOT VALIDATED.** This is the new-site starting point, not the existing-site audit. Execute the instructions below; do not simply describe a plan.

## Mission and boundaries

Act as a senior web designer, UX strategist, and frontend prototyping engineer. Turn the business brief into a clear website proposal that I can inspect in a browser before approving a production build.

There is no established website baseline to redesign. Do not invent current-site screenshots, existing analytics, or observed usability problems. If this project replaces a live site, identify that and use the existing-site workflow unless the user explicitly approves a different scope.

Use the specified target repository, not the prompt-library repository. Follow repository instructions and preserve existing files and uncommitted work. Any starter code is a constraint or resource to inspect, not permission to overwrite it.

Inspect the real source code, architecture, routes, components, styles, configuration, and integrations that exist in that repository before proposing a stack or design. If it is empty, state that explicitly and work from the brief; do not invent existing code or a rendered website. Browser previews validate the proposed studio and complement source inspection. If the target repository is unavailable, request its location/access. All generated code and review assets belong in that target repository, never in this prompt library.

Create only an isolated, local-only `design-review/` studio or reuse an existing equivalent. No production application implementation, deployment, external account changes, purchases, or new Markdown reports during this phase.

## 1. Build an explicit brief

Read the user's instructions and any supplied business material, assets, product documentation, or starter code. Identify:

- Offer, target audience, problem solved, main benefit, and primary visitor action.
- Supported countries/languages, business tone, protected brand elements, and authentic proof.
- Initial launch pages, desired user journeys, required integrations, and non-goals.
- Available content, logos, images, product screenshots, and asset permissions.
- Known stack/hosting constraints and which capabilities genuinely exist.

Do not invent testimonials, statistics, prices, reviews, certifications, legal commitments, or product functionality. Treat missing claims as unresolved content needs. Draft neutral copy only where it can be written accurately from the brief.

Ask only essential questions that cannot be resolved from provided information. Otherwise proceed with clear, reversible assumptions displayed in the studio. Do not make the user fill out a long questionnaire before seeing useful work.

## 2. Define the proposed site

Design a purposeful sitemap, navigation, conversion paths, page roles, and section order. Put the value proposition and main action ahead of ornamental sections. Identify content needed to handle real visitor questions and objections.

If browsing is available, inspect three relevant reference or competitor sites and record source links plus concise observations. Do not copy their identity or claim research you did not perform.

Create a visual launch-scope board. Distinguish approved requirements, proposed features, missing business inputs, and later ideas. Use stable IDs such as `NEW-001` and clear acceptance criteria. P0 blocks a truthful, usable launch; P1 is essential to the main journey; P2 improves usability/quality; P3 is optional.

Propose the simplest suitable frontend approach that respects the user's constraints. Explain its fit and major limitations in the studio. A prototype stack is not automatically approval for a production architecture, paid service, or backend build.

## 3. Build three realistic design directions

Use stable IDs A, B, and C. Make them meaningfully different in layout, type, hierarchy, and presentation, while representing the same business and comparable page scope. Explain the advantages and tradeoffs and recommend one.

For each direction, create a complete responsive homepage and up to two other essential page templates. Show unmocked pages and states explicitly. Build runnable HTML/CSS or framework prototypes, not image-only mockups.

Use actual brand assets and truthful content. Clearly mark any missing production asset or provisional copy in the studio. Do not use fake product screenshots or made-up social proof to make the mockups look complete.

Specify exact typography and available fonts, colors, spacing, containers, breakpoints, image behavior, navigation, buttons, cards, forms, and relevant focus/loading/error/success states. Consider accessibility, responsive content length, reduced motion, and performance from the start.

Use isolated fixture data. Demo navigation and form states may work locally, but must not send messages, create accounts, trigger payments, or collect actual visitor data. A simulated submission must be labeled a demo, not a completed integration.

## 4. Deliver the visual studio

The studio must provide:

- A concise brief with known facts, assumptions, audience, offer, and primary action.
- The proposed sitemap, content structure, and launch scope.
- Switchable A/B/C prototypes, desktop/mobile views, and direct prototype URLs without studio controls.
- Rendered design-system examples and exact token/component references.
- A prioritized task board linking requirements and content gaps to mockups and acceptance criteria.
- A recommendation explaining what to approve and which dependencies remain unresolved.

Do not add a fake before/after view. Use alternatives and proposed journeys instead. Keep the studio interface lightweight and focus effort on the actual site designs.

Use real viewport rendering rather than scaling a desktop image to imitate mobile. Reference sizes are 1440 × 900 desktop, 390 × 844 mobile, and 768 × 1024 tablet; validate representative intermediate widths too.

Keep studio dependencies, configuration, and assets isolated from the production application. Do not modify root manifests or deployment settings simply to launch a prototype. Do not expose the studio publicly or add it to site navigation/sitemaps.

Inspect actual build/deployment rules; `.gitignore` alone does not prevent publication. If the default location is deployed, use a non-deployable location inside the target repository. If no safe location exists without production configuration changes, report the blocker before creating the studio; do not move it into the prompt library or outside the target repository.

## 5. Preserve the shared handoff

Create `design-review/design-manifest.json`, or adapt an existing equivalent, compatible with the shared implementation prompt. Include:

- Schema version and `siteMode: "new"`.
- Brief, assumptions, actual versus proposed capabilities, protected constraints, and content gaps.
- Proposed stack, launch scope, routes/templates, and integration requirements.
- Option IDs, recommendation, direct prototype URLs, source paths, tokens, assets, content, and responsive rules.
- Comparison viewport details and honest screenshot/test evidence.
- Requirement/task IDs, priorities, dependencies, coverage, and acceptance criteria.
- An initially unset approval record for option, prototype revision, page/state scope, production stack, and exceptions.
- A separate place for later implementation and verification results.

Use structured data to power the visual interface; do not create a report collection. Verify referenced paths. Do not store secrets or personal customer information.

The design must be implementable from its code and tokens, not reconstructed from an attractive picture or vague style notes. A recommendation or selected preview tab does not constitute user approval.

## 6. Verify and stop

Launch the studio, check every option on desktop and mobile, inspect representative tablet widths, verify assets/navigation, and run relevant studio checks. Capture real screenshots when possible. If browser access is missing, label visual verification not tested.

End with the exact launch command and working directory, a verified URL or clearly labeled expected URL, a concise A/B/C comparison, the recommended option, the principal launch dependencies, and the decision needed next.

**Stop after the visual proposal.** The user must approve the option, page scope, and production stack before [Prompt 02](../shared/02-implement-approved-design.md) is executed. This link identifies an instruction in the prompt library, not a file required in the target website. Do not create application functionality, commit, push, or deploy during this step.
