---
id: website.shared.03
version: "2.1"
status: not-validated
validation_basis: "Standalone, visual-first revision; not yet tested by the user."
site_mode: existing-or-explicitly-new
standalone: true
requires_previous_steps: false
default_mode: review
writes: review-workspace-by-default-application-only-after-approval
---

# Prompt 03 — Mobile polish, accessibility, and performance

**Status: NOT VALIDATED.** Produce a visual issues board with concrete proposals, then implement selected fixes only after approval.

## Standalone operation and execution mode

**Run this prompt directly on the current website. Prompts 1, 1.5, 2, and all other phases are optional—not prerequisites.** Do not run them, regenerate design alternatives, or require their reports, approvals, manifests, or results.

Inspect the target application repository and rendered site. Follow repository instructions, inspect Git status, and preserve unrelated work. Discover the stack, routes, assets, existing tests, and start/build commands from the project. Do not mistake the prompt library for the application. A website built or modified manually is a valid starting point.

Read the real source code: trace the architecture, route definitions, components, styles/tokens, content, configuration, and integrations responsible for each finding. Browser rendering complements source inspection; it does not replace it. If the target repository or its source is unavailable, request the missing location/access rather than substituting a screenshot-only audit. Application changes and all review code/assets belong in the target repository, never in the prompt library.

Treat the current implementation as the accepted **visual starting point**, not evidence that it is correct. Preserve its brand and layout intent while identifying genuine defects. Older mockups and reports are optional background; do not restore an older option or report deviations from it as defects unless the user explicitly asks for that comparison. Without a required reference, historical design-fidelity checks are **not applicable**, not blockers. Capture fresh evidence for this run.

Execution modes:

- **`review` — default:** inspect, test, and build a visual issues board with proposed solutions. Create isolated mockups and review/evidence files only. Do not modify application source, production configuration, existing tests, or existing design references. Stop for approval.
- **`implement-approved`:** after the user approves issue IDs or an explicit bounded scope, resolve that approval to stable issue IDs and their specific proposal revisions before editing. Recheck the current code, implement only those fixes, and verify them. Use this same prompt; Prompt 2 is not needed. Do not infer approval from a severity label, a recommendation, or a browser selection alone.
- **`verify`:** rerun the selected checks and update evidence without changing application source. Do not silently fix failures.

If an implementation request has no identifiable approved scope, complete the visual review and expose the decision needed rather than applying all recommendations. Instructions about fixes below apply only in `implement-approved` mode. Missing previous phases never block the review; missing credentials, tools, source, or essential test evidence must still be disclosed.

Do not deploy, commit, push, perform live transactions, change external accounts, weaken security/consent, or install unnecessary dependencies. Run potentially stateful tests only against safe, authorized test environments. Redact secrets and personal data from evidence. Keep existing approved prototypes immutable.

## One visual review workspace, not Markdown reports

Reuse an existing quality-review workspace or add a separate review area to a usable `design-review/` studio without changing its design options. If neither exists, create an isolated **`website-review/`** workspace. No earlier studio is required. Any of Prompts 3, 4, or 5 must be able to initialize it; later runs reuse it and preserve other categories' findings.

Keep it outside production routes, bundles, public assets, sitemaps, and deployment artifacts. Check the actual build/deployment rules; `.gitignore` alone is not deployment protection. If the default location is deployed, use a non-deployable location inside the target repository. If no safe location exists without production configuration changes, report the blocker before creating the workspace; do not move it into the prompt library or outside the target repository.

Use a lightweight local HTML/CSS/JavaScript interface or the existing isolated preview stack. Prefer a small working interface over building a new reporting application. Do not add a backend, accounts, analytics, or a new production dependency. The board itself must be responsive and keyboard-accessible.

Suggested structure, adaptable to the existing workspace:

```text
<review-root>/
├── index.html           # Or the existing preview app
├── review-data.json     # Shared runs, issues, proposals, decisions, checks
├── evidence/            # Sanitized screenshots and tool results
└── mockups/             # Isolated, runnable proposed changes
```

A structured data file powers the interface; it is not another report the user must read. No generated Markdown audits, plans, summaries, changelogs, or README files. Put launch instructions and concise conclusions in the final response and the board.

## Mobile, accessibility, and performance scope

Act as a mobile UX engineer, accessibility reviewer, and web performance engineer. The goal is targeted quality improvements, not a new visual direction. Use `MOB-`, `A11Y-`, and `PERF-` issue prefixes unless the existing board already has an ID convention. Reuse an existing issue ID when the same problem has already been recorded.

### 1. Establish the baseline

Inventory important public page templates, locales, and conversion journeys. Include expanded navigation, forms and validation errors, loading/empty states, dialogs, long text, and applicable authenticated flows using safe test data. Sample repetitive templates and show what was and was not covered.

Capture current screenshots and test conditions before any fixes. Distinguish existing defects from regressions introduced during this run. No old baseline is required: without one, assess current quality and do not invent historical regression claims.

### 2. Responsive behavior and mobile usability

Inspect representative widths of 320, 375, 390, 430, 768, 1024, 1440, and 1920 CSS pixels as appropriate, plus widths around real breakpoints. Test portrait/landscape, zoom/text enlargement, and relevant long translated text. Use real browser rendering where available.

Find overflow, clipping, broken grids, unreadable text, awkward wrapping, inaccessible controls, layout shifts, and unnecessarily dense mobile content. Review menus, headers/footers, sticky actions, images, forms, tables, dropdowns, and dialogs. Verify reachable actions with an on-screen keyboard or consent banner, safe areas, scroll locking, and tap versus hover behavior where testing tools permit.

Show targeted mockups for proposed visual changes: for example, the actual overflowing card beside its corrected mobile layout, or a modal with proposed keyboard-safe positioning. Keep current branding and interaction intent. Broad aesthetic changes require a separate decision, not a mobile-polish pretext.

### 3. Accessibility

Target WCAG 2.2 Level AA and check current W3C guidance when executing. Combine automated testing with manual keyboard, focus, labeling, landmark/heading, contrast, zoom/reflow, and reduced-motion checks. Review form instructions, error announcements, dialog focus/return, skip navigation, menus, and status feedback. State actual screen-reader coverage; an automated scan alone does not establish conformance.

Evaluate target-size requirements and their exceptions accurately; distinguish an ergonomic preference for larger controls from a conformance minimum. Prefer native semantics. Do not add redundant ARIA, remove focus visibility, hide useful content from assistive technology, or substitute an accessibility overlay for repairs.

For visible changes such as contrast, focus rings, labels, and touch targets, show current/proposed states. For nonvisual changes such as accessible names or live-region behavior, show the user interaction, expected assistive output, focused markup change, and verification procedure—not a cosmetic mockup pretending to prove accessibility.

### 4. Performance measurement

Use an optimized production build for meaningful lab comparisons. Record tool/version, route, browser, viewport, CPU/network conditions, cache state, environment, and run count. Compare like with like; do not compare a cold dev build with a warm production build. Where practical, show the median and variability from three comparable runs.

Keep lab results and real-user field data separate. Read authorized field measurements when available. Lighthouse scores and lab Total Blocking Time do not establish field INP or a real-user Core Web Vitals pass. Missing field data is `unavailable`, not a fabricated result. Verify current Core Web Vitals definitions and thresholds against official guidance at execution time.

Investigate measured bottlenecks: hero/LCP resource loading, long tasks and interaction handlers, image dimensions and payloads, layout instability, JavaScript/CSS, font loading, hydration, caching, rendering, and required third-party scripts. Show clear technical cards with the actual resource or trace, the proposed change, and the measurement needed to prove an improvement.

In review mode, display only measured current results; after-values remain `not measured`. A benchmark of an isolated demo must not be presented as an improved production-site result. Do not promise a Lighthouse score or remove necessary content to chase one.

### 5. Fix strategy and cross-browser verification

Propose responsive media, explicit dimensions, appropriate hero loading priority, below-the-fold lazy loading, code splitting, font improvements, cheaper rendering, and cache changes only where evidence supports them. Do not lazy-load the main LCP image by default, preload everything, remove needed integrations, or introduce a framework migration or broad dependency upgrade.

Hosting/CDN changes are external actions requiring separate authorization. Preserve validation/submission behavior, security, analytics, and consent. After approved fixes, compare the current application with the baseline and approved **issue mockups**, not an assumed old Option B design.

Use available Chromium, Firefox, and WebKit coverage. Distinguish browser automation, mobile emulation, and physical-device testing. Recheck navigation, forms, sticky elements, dialogs, fonts, images, keyboard/touch behavior, and critical journeys. Do not mark unavailable coverage passed.

### Mobile/performance board views

Alongside the shared issues board, provide a compact viewport/browser coverage grid and a measurements view. Separate responsive, accessibility, and performance findings; link each metric or failed check to the relevant issue and evidence. Label proposed benefits versus verified changes.

In review mode, finish with **review ready** or **review ready with named coverage gaps**. After approved fixes, summarize verified improvements and remaining risks. There is no requirement to run SEO next, and this review alone is not a full release certification.

## Visual deliverable: show the problem and the proposed solution

Build the review as an actionable visual issues list, **not a long report pasted into HTML**. Start with the highest-priority problems and the next decision. Use concise cards, thumbnails, filters, and expandable details. Use real data, not decorative scores or invented example issues.

### Overview and issue cards

Show review scope, environment/revision and timestamp, blocker counts, top priorities, coverage gaps, and what to do next. Support filtering by priority, page, category, and status. Provide stable issue links and IDs. Preserve IDs across reruns; merge duplicate root causes instead of inflating counts. Cross-reference an existing issue discovered by another prompt rather than creating a conflicting duplicate.

Each issue must include:

- **Location and evidence:** affected page/state/viewport and relevant source component or file; a screenshot, rendered-output excerpt, reproducible steps, or real measurement.
- **Problem and impact:** a specific title, a plain-English explanation, and who is affected. Distinguish observed defects, code-inferred risks, hypotheses, and optional preferences.
- **Proposed fix:** the exact change, affected files/components, expected benefit, complexity, dependencies, and risk. Do not invent measured gains.
- **Acceptance check:** an observable pass condition and how to verify it.
- **Decision and verification:** proposal state, explicit user approval, implementation state, and actual verification result, kept separate and tied to the proposal revision.

Priorities: **P0** critical broken journey/exposure/release blocker; **P1** major user-facing or technical defect; **P2** useful nonblocking improvement; **P3** optional polish. Do not classify aesthetic preference as a critical defect.

### Visual or interaction issues: current versus proposed

Show an actual current screenshot beside an isolated, high-fidelity mockup of the **specific fix**. Label them **CURRENT — observed**, **PROPOSED — not implemented**, and, after an approved fix, **IMPLEMENTED — verified / not yet verified**. Include complete-page context plus focused crops when useful.

Use the site's real assets, copy, tokens, and components. Match route, content, locale, viewport, and interaction state. Use desktop/mobile views when affected. Prefer runnable HTML/CSS/component prototypes over generated illustrations; make menu, form, focus, and error-state proposals interactive when that is necessary to judge the fix. Reuse a representative component mockup for shared issues and list all affected pages.

Do not merely display a screenshot with a text description of a visual suggestion. Show the actual proposed appearance. Do not create new A/B/C redesign directions or alter the live application to produce a mockup. A working prototype is not a production fix, and a screenshot is not proof of keyboard or assistive-technology behavior.

### Technical or nonvisual issues: explanation and proof

Do not invent visual mockups for changes with no visible effect. Instead show **Current behavior → Why it matters → Proposed change → How we will verify it**. Use an expandable focused code/config diff, real response/header excerpt, request-flow diagram, metric comparison, or test trace—whichever makes the issue understandable.

Keep the plain-English explanation visible; put logs and implementation detail behind an expander. Explain expected behavior rather than promising a speed, ranking, conversion, or accessibility outcome. Suggested patches remain proposals until approved. Unmeasured after-values display **not measured**, never optimistic invented numbers.

### Evidence, approval, and coverage

Store and display independent status fields for each issue, not a single lifecycle label:

- `proposalStatus`: `draft`, `proposed`, or `deferred`.
- `approvalStatus`: `not-requested`, `pending`, `approved`, or `rejected`, with the explicit user decision, approved proposal revision, and scope.
- `implementationStatus`: `not-started`, `in-progress`, or `implemented`.
- `verificationStatus`: `not-tested`, `passed`, `failed`, `blocked`, or `not-applicable`, with per-check evidence and the tested code revision.

Preserve compatible existing fields when reusing a board; add the missing distinctions without discarding earlier findings. Passing a check does not approve or implement a proposal. Implementation does not imply verification, and an older approval does not cover a materially changed proposal. Show baseline, proposal, implementation, and verification separately.

Keep small structured records of issue IDs, source prompt, routes, evidence, proposal/mockup paths, acceptance checks, explicit approvals, timestamps, and tested revision. Mark old evidence stale after relevant code changes. If screenshots or browser tools are unavailable, still build the board and feasible runnable proposals, label code-based findings and unrendered mockups honestly, and never fabricate observed screenshots or successful tests.

Allow selecting issues and copying an implementation instruction, for example: `Run this same prompt in implement-approved mode for <selected issue IDs> only.` Keep the selected work within this prompt's scope; identify cross-scope items separately. Browser selection is a review aid, not an automatic authorization or code-execution mechanism. If selection is local-only, say so and export or copy the chosen IDs rather than claiming a saved approval.

## Implement and verify approved issues without Prompt 2

When the user returns with explicit issue IDs or a bounded scope, continue from the board and actual code. Verify the approved proposals are still applicable; flag material changes to their scope or design before proceeding. Keep the baseline and proposal immutable, implement only the approved fixes in the application, and preserve integrations and unrelated work.

For visual fixes, match the approved local mockup, reuse its code/tokens where practical, and compare the actual implementation at the same viewport and state. Do not change a reference to hide a mismatch. For technical fixes, run the stated acceptance checks and display the actual before/after evidence. Also run relevant build, lint, type, functional, accessibility, and regression checks.

Update the **same board** with changed files, implementation evidence, actual verification results, residual differences, and blocked checks. `Implemented` does not mean `verified`; a passing build alone is insufficient. Do not create Markdown implementation reports or a second dashboard.

## Final response and stop condition

Keep the response short: the actual workspace path, launch command, and browser URL; the most important findings or fixes; checks that could not run; and the next concrete decision. Verify the preview when tools permit. Do not say a local server is running unless it is; otherwise label the URL as available after the launch command.

In `review` mode, stop after the working visual board, proposals, and evidence are ready. State that application code was not changed and show how to approve the selected issue IDs. In `implement-approved` mode, stop after approved fixes and verification; in `verify` mode, stop after the updated results. Never deploy or automatically run the next numbered prompt. Keep this prompt marked **NOT VALIDATED** until the user reviews its actual results.

## Primary references

Verify current guidance and installed tool behavior when executing:

- [Core Web Vitals](https://web.dev/articles/vitals)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [Target size: minimum](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum)
