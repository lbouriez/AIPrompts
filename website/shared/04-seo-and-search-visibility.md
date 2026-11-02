---
id: website.shared.04
version: "2.1"
status: not-validated
validation_basis: "Standalone, visual-first revision; not yet tested by the user."
site_mode: existing-or-explicitly-new
standalone: true
requires_previous_steps: false
default_mode: review
writes: review-workspace-by-default-application-only-after-approval
---

# Prompt 04 — SEO and search visibility

**Status: NOT VALIDATED.** Produce a visual SEO issues board with page previews and clear technical proposals; implement only approved changes.

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

## SEO and search-visibility scope

Act as a technical SEO engineer and content strategist. Work from the current website, not an assumed redesign. Use `SEO-` issue IDs unless the existing board has a convention. Consult current official search-engine and framework guidance; attach source links and observation dates to policy-sensitive findings. Missing browsing or account access limits verification, not the ability to produce a useful review.

### 1. Inventory the real search surface

Identify the actual offer, audience, markets/languages, conversion goals, public routes/templates, rendering strategy, content sources, metadata, analytics/consent, and deployment environments. For an explicitly new site, assess launch readiness without inventing traffic, rankings, indexed URLs, or conversions.

Create a filterable route view: page purpose, locale, status, intended indexability, title/description, canonical, sitemap membership, internal-link coverage, and actual evidence. Distinguish public indexable pages, intentional non-indexable utilities, private/authenticated areas, staging, and local review workspaces. Do not assume every reachable route belongs in search.

Use authorized Search Console or analytics data when available. A file or script in the repository does not prove account verification, sitemap submission, tracking delivery, or actual indexing.

### 2. Technical SEO

Inspect actual HTTP responses and initial/rendered HTML where tools permit. Review status codes, broken links, redirects, soft 404s, robots.txt, meta/HTTP robots directives, canonical rules, query parameters, HTTPS/host consistency, sitemaps, orphaned pages, navigation, and relevant pagination.

Check unique and accurate titles/descriptions, meaningful headings and landmarks, descriptive links, suitable image alternatives, and social-sharing metadata. Show exact affected routes and the rule/component responsible; do not return a generic SEO checklist.

Explain nonvisual issues with focused current/proposed evidence: for example, a response/status trace for a soft 404, a canonical diff for duplicate routing, or a short crawler-flow diagram for a conflicting indexing rule. Do not mock a redesigned page when the fix is a header or metadata change.

Crawling, indexing, and security are separate. robots.txt is not access control; a blocked crawler may not see a page's noindex instruction. Keep private content protected by authentication/authorization. Verify staging safeguards without accidentally making production non-indexable. Review workspaces and evidence must remain outside public builds and sitemaps.

Do not redirect all missing routes to the homepage, canonicalize unrelated pages together, or change URLs merely to add keywords. Indexability changes with uncertain business intent, domain/URL migrations, redirects, deletions, and bulk consolidation require explicit approval, mapping, impact assessment, and rollback considerations.

### 3. Rendering and internationalization

Check how meaningful content, links, and metadata reach crawlers. Do not label all client-rendered pages unindexable without evidence. Prefer framework-compatible corrections; SSR/SSG migrations and route redesigns are separate decisions, not automatic SEO tweaks.

For actual localized pages, review language declarations, genuine translations, locale URLs, reciprocal hreflang where appropriate, canonical consistency, fallback intent, and accessible language navigation. Do not canonicalize all valid translations to one language, mark untranslated content localized, or generate regional doorway pages.

### 4. Search intent, visible content, and previews

Research real relevant queries and competing pages where tools permit. Separate observed results and authorized analytics from hypotheses. Never invent search volumes, difficulty, ranking positions, competitor traffic, testimonials, or business claims.

Map important pages to audience questions, intent/topic clusters, proposed titles/descriptions, main headings, content gaps, internal links, and conversion actions. Avoid near-duplicate pages competing for the same purpose. Keep the current brand voice and page composition; do not insert keywords at the expense of meaning.

For visible copy, headings, link placement, or a genuinely useful FAQ section, show a targeted in-context desktop/mobile mockup using the current layout—not just replacement text in a table. Do not silently replace the hero, add large sections, or publish new pages.

For metadata, provide current/proposed search-snippet and social-card previews where useful. Label them **illustrative previews, not live search results or guaranteed rendering**. Search engines and platforms may choose different text/images; do not imply placement, indexing, rich-result eligibility, or ranking from the preview.

Propose only worthwhile content opportunities: missing product/use-case pages, fair comparisons, clear answers, or a small prioritized editorial list where relevant. Each card should state the audience question, business relevance, required original input, internal-link plan, and desired action. Avoid padding the board with a fixed article quota or mass-produced content.

### 5. Structured data and AI-assisted search

Inspect existing markup first. Select Schema.org types appropriate to real entities and visible page content. Do not fabricate ratings, reviews, offers, prices, authors, locations, or capabilities; avoid conflicting duplicate entities.

Show proposed JSON-LD in a compact technical diff with a plain-English explanation. Distinguish valid schema, engine-specific eligibility, and an actual displayed search feature. Verify current rules and run available syntax/schema/rich-result checks; do not claim that a proposed patch has passed validation of the live page.

For AI-assisted search, favor clear entity information, useful direct answers, crawlable public content, genuine expertise, and appropriate source/author details. Use current primary guidance rather than promises of AI citations or special ranking tricks. Do not present optional files such as `llms.txt` as established search requirements without reliable evidence for the specific claim. Respect existing crawler, privacy, and consent policies; do not automatically allow every bot.

### 6. Measurement, ownership, and approved implementation

Review consent-aware analytics, conversion-event wiring, Search Console access, sitemap readiness, and monitoring. Show external setup as owner-action cards with the exact action and required access. Do not add duplicate tracking or claim account-side work was completed by editing application code.

In `implement-approved` mode, apply only approved corrections and copy changes; keep proposals requiring separate migration, publication, or external-account approval pending. Recheck visible copy changes on mobile and relevant locales. Validate route responses, metadata, canonical/indexability logic, sitemap content, structured data, internal links, nonexistent-page behavior, and affected language relationships. Run relevant build and regression checks.

Keep **technically ready for indexing**, **actually indexed**, and **measured organic improvement** separate. Never promise rankings, traffic, rich results, or AI citations. You may recommend final QA, but no other prompt is required to finish this review.

### SEO board views

Add the route-health view, current/proposed snippet and content previews, technical correction cards, and a compact opportunities/owner-actions view to the shared board. Use `not checked` or `unknown intent` where appropriate rather than treating every route as a pass/fail. Show policy sources and tool coverage in expandable details.

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

Verify current guidance at execution time:

- [Google Search Essentials](https://developers.google.com/search/docs/essentials)
- [SEO Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)
- [Controlling indexing with noindex](https://developers.google.com/search/docs/crawling-indexing/block-indexing)
- [Structured data guidelines](https://developers.google.com/search/docs/appearance/structured-data/sd-policies)
- [Localized versions](https://developers.google.com/search/docs/specialty/international/localized-versions)
- [AI features and your website](https://developers.google.com/search/docs/appearance/ai-features)
