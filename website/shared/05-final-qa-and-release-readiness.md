---
id: website.shared.05
version: "2.1"
status: not-validated
validation_basis: "Standalone, visual-first revision; not yet tested by the user."
site_mode: existing-or-explicitly-new
standalone: true
requires_previous_steps: false
default_mode: review
writes: review-workspace-by-default-application-only-after-approval
---

# Prompt 05 — Independent QA and release readiness

**Status: NOT VALIDATED.** Test the current website and present a visual defect board, proposed fixes, and an evidence-based release recommendation.

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

## Independent QA and release-readiness scope

Act as an independent frontend QA engineer and release reviewer. Audit the current website even if none of the other prompts ran. Use `QA-` IDs for new findings, but link to existing `MOB-`, `A11Y-`, `PERF-`, or `SEO-` issues when they describe the same defect. Previous summaries and screenshots are leads to investigate, not proof of current correctness.

### 1. Establish current scope and expectations

Identify in-scope pages/templates, user journeys, states, locales, integrations, and environments from the actual application and explicit user requirements. Use existing tests and documentation as context, but investigate contradictions rather than assuming either is correct. Record uncertain expected behavior and the decision needed.

Capture the current revision, working-tree state, and baseline evidence. No earlier audit, implementation report, or prototype is required. If historical behavior is unknown, report **current defect/risk**, not a proven regression. Compare earlier evidence only when relevant and label it stale after code changes.

Create a compact coverage matrix with route/state, environment, expected behavior, observed behavior, evidence, and check status. Prioritize critical journeys and changed/high-risk areas. Do not claim exhaustive testing from sampling.

### 2. Functional checks

Test relevant navigation, deep links, refresh behavior, expected redirects, nonexistent pages, forms and validation, authentication, search/filtering, locale switching, menus/dialogs, pricing links, and loading/error/empty states.

Exercise checkout, subscriptions, contact delivery, account updates, or similar state-changing operations only in authorized test environments or safe mocks. Avoid live charges, messages, customer records, and polluted production analytics. Clearly state which integration boundaries were mocked or not exercised end to end. A fixture returning success is not evidence that a real integration works.

Check existing analytics wiring and consent behavior, error handling, duplicate submission protection, and whether prototype data or fake success screens replaced working logic. Capture reproducible steps and actual failure traces.

For visible error-handling or interaction fixes, show a small runnable proposed state/flow using the current interface. For a server response or routing defect with no visual change, show the request/response sequence and proposed correction instead.

### 3. Visual quality and responsive behavior

Inspect the actual interface for clipping, overflow, broken layouts, inconsistent components, unreadable typography, missing assets, focus problems, obscured controls, long translations, and unusable menus/dialogs. Review whole pages and important states, not only the hero. Use desktop 1440 × 900, mobile 390 × 844, tablet 768 × 1024, and relevant edge/breakpoint widths as useful starting points—not a claim of exhaustive device coverage.

The current site is the visual baseline unless the user explicitly requires fidelity to a particular prototype. An older Option B may be useful background, but its existence alone does not authorize restoring it or undoing manual changes. With no required prototype, mark historical design-fidelity checks **not applicable** and still inspect real usability and visual defects.

For an explicitly required reference or an approved issue mockup, compare matching route, content, locale, state, fonts, browser, viewport, and device pixel ratio. Show material differences. Never edit a reference to conceal a mismatch or mark an unapproved exception accepted.

Show targeted current/proposed mockups for visual defects, not an unsolicited redesign. Distinguish automated browser coverage, emulated devices, and physical-device testing.

### 4. Accessibility and performance checks

Run available automated checks plus manual keyboard, focus, labeling, contrast, reflow/zoom, landmarks, error announcements, and reduced-motion checks. State screen-reader coverage honestly; automated results alone do not prove WCAG conformance. Use current official guidance for applicable requirements.

Measure representative pages in an optimized build under recorded, repeatable conditions. Reuse a prior measurement only if its conditions are comparable; otherwise establish a fresh baseline. Keep lab and field results separate and show unavailable real-user data honestly. Never claim a real-user Core Web Vitals pass from a Lighthouse score.

Review loading, interaction, and layout-stability risks, especially around images, fonts, scripts, consent, and content changes. A new site's lack of field data is a monitoring limitation, not automatically a release blocker. Missing evidence for an essential usable journey is more serious.

### 5. Technical SEO and environment checks

Check intended indexability, private/staging protections, real status codes, titles/descriptions, canonical rules, sitemap/robots behavior, internal links, structured data, and localization where applicable. Verify that review workspaces, screenshots, test data, and private assets do not enter production builds or sitemaps.

Catch staging noindex settings accidentally carried into production configuration. Keep local technical readiness separate from actual indexing/ranking. Record external Search Console, hosting, or post-launch checks as owner actions rather than claiming they ran locally. Do not require Prompt 4 to perform these checks.

### 6. Code, tests, and production build

Inspect available commands before running them; avoid scripts with destructive or live side effects. Run relevant build, type, lint, unit, integration, and end-to-end checks. Where possible, serve/test the actual production artifact locally or in a safe test environment, not just the dev server.

Inspect console/network errors, missing environment configuration, hydration issues, broken imports/assets, duplicate tracking, unnecessary dependencies, and accidental secret/debug exposure. Do not copy credentials or personal data into the board. Review accidental inclusion of demo fixtures, rejected designs, or review-only dependencies.

Separate existing failures from new regressions without dismissing existing production risks. Do not disable or weaken failing checks, hide broken routes, or refactor unrelated code to obtain a clean result. This is scoped QA, not a penetration test or security certification.

### 7. Proposed fixes, verification, and release decision

In default `review` mode, surface issues, actionable proposals, and the release recommendation for the **current** site; do not secretly fix defects first. High priority is not automatic implementation approval. Escalate critical findings immediately and visibly.

In `implement-approved` mode, fix only the approved issues, rerun their acceptance checks and affected journeys, and update the same board. If a fix materially changes approved behavior, design, infrastructure, or scope, expose that decision instead of expanding the task. Reassess the release recommendation using the resulting code and current evidence.

Use one evidence-based recommendation for the stated scope/environment:

- **GO:** essential journeys and checks passed; no blocking defect or unresolved required approval remains. State residual noncritical limitations.
- **CONDITIONAL GO:** no critical blocker is known, but explicit nonblocking conditions or pre-release owner actions remain. Do not hide unknown essential functionality behind this label.
- **NO-GO:** a critical/release-blocking defect, unresolved material approval conflict, or insufficient evidence for an essential journey prevents release.

Skipping prior prompts or lacking old mockups is **not** a reason for NO-GO. Missing genuine release requirements or verification may be. Separate diagnostic coverage limits from actual failed checks.

### QA board views

Show a clear release-status banner with its reasons, the prioritized issues, a journey/page/browser coverage matrix, and expandable test evidence. Link failed checks to proposed fixes and mockups. Counts and status must come from recorded results, not a decorative readiness percentage.

Provide a short owner-action checklist: tested revision, environment checks, smoke-test routes, monitoring, applicable approved redirects, and a rollback approach grounded in the real project. Mark post-launch checks unperformed and deployment separately authorized. Do not invent infrastructure commands.

In the final response, lead with the current GO / CONDITIONAL GO / NO-GO recommendation and scope, followed by the board location, main blockers or fixes, untested essentials, and the next decision. This prompt can run alone; running it after other changes is useful for checking their combined result, not a prerequisite.

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

Use current official guidance where relevant:

- [Playwright visual comparisons](https://playwright.dev/docs/test-snapshots)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [Core Web Vitals](https://web.dev/articles/vitals)
- [Google Search Essentials](https://developers.google.com/search/docs/essentials)
