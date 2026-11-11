<div align="center">

# PHIL

### Proclaim Honestly, Interact Liberally
*Parler Haut, Interagir Librement*

[![phil/enums on Packagist](https://img.shields.io/packagist/v/phil/enums?label=phil%2Fenums&logo=packagist&logoColor=white)](https://packagist.org/packages/phil/enums)
[![Licence: MIT](https://img.shields.io/badge/licence-MIT-blue)](https://opensource.org/license/mit)
[![PHP 8.5+](https://img.shields.io/badge/PHP-8.5%2B-777BB4?logo=php&logoColor=white)](https://www.php.net)
[![Symfony 8.2+](https://img.shields.io/badge/Symfony-8.2%2B-000000?logo=symfony&logoColor=white)](https://symfony.com)
[![ph-il.ca](https://img.shields.io/website?url=https%3A%2F%2Fph-il.ca&label=ph-il.ca)](https://ph-il.ca)

**[English](#what-phil-is)** · **[Français](#version-française)**

</div>

---

## What PHIL is

**phil-ip** (*Internet Platform*), also called **phil-pc** (*Collaborative Platform*), is a platform for building
collaborative websites, online and in person. We built it first for the websites of Le Gnome Archiviste — a game
shop and creator from Québec — and we publish its modules as open source, so that you can use them too and add your
own grain of salt.

PHIL is three things:

- **The `phil/*` libraries and Symfony bundles** — content and text, commerce, events, community, privacy,
  media and print, and the plumbing in between. The full list, with the state of each package, is
  [below](#the-packages).
- **PHIL UX** (`phil-ux`), the design system: a kit for the Symfony UX Toolkit and a CSS framework. Its site will be
  [ux.ph-il.ca](https://ux.ph-il.ca).
- **The tooling** every package is checked with: `phil/dev-tools` and the project templates.

[ph-il.ca](https://ph-il.ca) presents the platform and will become the catalogue of the modules: one page per
package, generated from its README and its documentation, in English and in French.

The game and gamification packages — dice, generators, points, badges, quests and the rest — live next door, in
[Tilttek](https://github.com/TiltTek).

## Why

Shops, conventions, clubs, publishers and online communities keep needing the same bricks: a catalogue and a cash
register, a calendar, a forum, a newsletter, a privacy policy that is actually applied. We would rather write each
brick once, carefully, in the open, than glue the same parts together on every site. And we would rather tell you
plainly how far along each brick is: **today, 85 packages are released; the others are being written or planned,
and they follow by small daily groups.**

## Principles

- **Original code.** Third-party code enters a PHIL package only as a declared Composer dependency. Other projects
  are studied for their ideas.
- **MIT, all of it.** Every package carries its own licence file.
- **A modern floor:** PHP 8.5+ and Symfony 8.2+.
- **The next versions, early.** The next PHP and the next Symfony enter our test matrix at their first release
  candidate (today: PHP 8.6). Our constraints let you install them before we require them; a deprecation on the next
  PHP fails the build. The floor moves up when the next version reaches its third patch release (x.y.3) — always in
  a new version of our packages, never in an existing one.
- **Strict quality gates.** PHPStan at its maximum level with strict rules, on every PHP of the matrix;
  PHP-CS-Fixer with the Symfony rules and `declare(strict_types=1)` everywhere; Rector; Deptrac and Arkitect for the
  architecture; PHPUnit failing on any deprecation, notice or warning; and every package installed and tested on its
  own.
- **A 100 % mutation score.** Infection must kill every mutant. A surviving mutant is a missing test, or code that
  nothing can reach; the bar is never lowered, and a package does not leave incubation below it.
- **Accessible by default.** Keyboard and screen-reader use, visible focus, reduced motion, sufficient contrast, and
  never information carried by colour alone.
- **Every language, not only ours.** Data comes from CLDR and other open references; addresses, phone numbers,
  plural rules and typography follow each country and language. Nothing is limited to the languages of our own sites.
- **Privacy by design.** Built for Québec's Loi 25 and the GDPR: no tracking, no third-party trackers, analytics in
  aggregates only, IP addresses anonymised, personal fields declared so that they can be exported and erased, and
  queued messages that carry identifiers, never personal data.
- **Extensible on purpose.** Documented extension points (tagged services and public interfaces), so that add-ons
  plug in without patches; they are declared stable from 1.0.
- **Documented in English.** Each package has a README and a full `doc/` folder.

## How the packages are organised

- **A pure PHP library and its Symfony bundle.** `phil/money` works in any PHP project; `phil/money-bundle` wires it
  into forms, validation, Twig and Doctrine. Some packages exist only as a bundle. Libraries rely on the existing
  Symfony components rather than reinventing them.
- **Incubation.** New packages are written in a private monorepo, `phil-prerelease`, the permanent incubator, where
  changes that span several packages are made and tested together.
- **Release.** A finished package moves to the public monorepo
  [`parler-haut-interagir-librement/phil`](https://github.com/parler-haut-interagir-librement/phil), where it is
  developed from then on, and from which each package is split into its own read-only repository and published on
  [Packagist](https://packagist.org).
- **Versions.** Semantic versioning; each package keeps a [Keep a Changelog](https://keepachangelog.com) file.

## PHIL UX

PHIL UX goes through the [Symfony UX Toolkit](https://ux.symfony.com/toolkit): no custom installer, just
`ux:install`.

| Repository | What it holds | State |
|---|---|---|
| [ux-kit](https://github.com/parler-haut-interagir-librement/ux-kit) | The PHIL UX kit: the same recipes as the Toolkit's Shadcn kit — names, props, Twig blocks, Stimulus controllers — with their own HTML and CSS, styled with phil-ux. `php bin/console ux:install <recipe> --kit=github.com/parler-haut-interagir-librement/ux-kit` | 🧪 incubation, ~10% |
| [ux-css](https://github.com/parler-haut-interagir-librement/ux-css) | phil-ux, the CSS framework: real, mostly classless CSS with `--phil-*` tokens, light and dark, and `isX`/`hasX` state classes; for AssetMapper (Composer) and npm | 🧪 incubation, ~30% |
| [ux-kit-shadcn](https://github.com/parler-haut-interagir-librement/ux-kit-shadcn) | Tailwind versions, in the Shadcn style, of the recipes PHIL UX adds | 🧪 incubation, ~25% |

Available so far, in the incubator:

- **Logo** — a logo with its WebP source and alternative text, linked home when given an `href`, one per theme and
  language.
- **AnimatedHeadline** — a headline whose words take turns, in a Stimulus controller; under `prefers-reduced-motion`,
  nothing moves.
- **Illustration** — a figure showing one picture chosen on the server among candidates, at random or by seed.
- **ComingSoon**, a block — a "coming soon" page built from the three recipes above.
- **Layout utilities** in phil-ux — `isStack`, `isCluster`, `isCenter`, `isNarrow`, `isSplit`, `isCover`, `isBleed` and
  their kin, with gaps read from the tokens.
- **Themes** in phil-ux — light and dark, from an OKLCH palette whose pairs are checked against a contrast rule.

The Shadcn kit's components come next, starting with the ones our bundles need.

Because the recipes share the Shadcn kit's names and props, every PHIL bundle renders with PHIL UX **or** with the
Shadcn kit: keep Tailwind if you like it.

## Tooling

- **`phil/dev-tools`** — the shared configurations of PHP-CS-Fixer, PHPStan, Rector, Deptrac, Arkitect, Infection,
  PHPUnit and PHPBench; the Composer scripts that run them; documentation checks; real MySQL, PostgreSQL and
  Gotenberg servers in Docker for integration tests; replayable HTTP recordings; the PHP and Symfony version matrix;
  and the scaffolding of a new package. Published under the MIT licence:
  [dev-tools](https://github.com/parler-haut-interagir-librement/dev-tools).
- **Project templates** — [MicroSymfony](https://github.com/parler-haut-interagir-librement/MicroSymfony) (based on
  `strangebuzz/MicroSymfony`) and [WebSymfony](https://github.com/parler-haut-interagir-librement/WebSymfony).

## The packages

✅ **released** · 🧪 **written, in incubation** (approximate completion) · 🗓️ **planned**

**418 packages:** 85 released, 90 in incubation, 243 planned. Percentages are estimates from our
latest status report (11 November 2026). The released packages are developed in the public monorepo
[`phil`](https://github.com/parler-haut-interagir-librement/phil), each split into its own read-only repository and
published on Packagist; `phil/enums` continues [`ph-il/enums`](https://packagist.org/packages/ph-il/enums). **The
showcase continues by small daily groups** of two to four packages, dependencies first.

<details>
<summary><b>Data &amp; infrastructure</b> — ✅ 19 · 🧪 16 · 🗓️ 16</summary>

- [`phil/enums`](https://github.com/parler-haut-interagir-librement/enums) · ✅ released ([Packagist](https://packagist.org/packages/phil/enums)) — Traits and attributes to list, compare, describe and group PHP enums (formerly `ph-il/enums`)
- [`phil/enums-bundle`](https://github.com/parler-haut-interagir-librement/enums-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/enums-bundle)) — Enums in Symfony forms, translations, Twig, validation, Doctrine and API contracts
- [`phil/resource`](https://github.com/parler-haut-interagir-librement/resource) · ✅ released ([Packagist](https://packagist.org/packages/phil/resource)) — Point at any record by its kind and identifier, such as `page:42`
- [`phil/ddd-bundle`](https://github.com/parler-haut-interagir-librement/ddd-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/ddd-bundle)) — Shared domain types: identifiers, domain events, errors, command and query buses
- [`phil/slug`](https://github.com/parler-haut-interagir-librement/slug) · ✅ released ([Packagist](https://packagist.org/packages/phil/slug)) — URL slugs from titles and names, as a type that accepts nothing else
- [`phil/slug-bundle`](https://github.com/parler-haut-interagir-librement/slug-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/slug-bundle)) — Named sluggers declared in configuration, autowired and usable in Twig
- [`phil/url`](https://github.com/parler-haut-interagir-librement/url) · ✅ released ([Packagist](https://packagist.org/packages/phil/url)) — Web addresses as normalised values, their kind detected: Mastodon, YouTube, a website
- [`phil/url-bundle`](https://github.com/parler-haut-interagir-librement/url-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/url-bundle)) — Link fields that detect their kind, a constraint, a column type and Twig filters
- [`phil/references-bundle`](https://github.com/parler-haut-interagir-librement/references-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/references-bundle)) — Know where each resource is used, and refuse to delete one still needed
- [`phil/trash-bundle`](https://github.com/parler-haut-interagir-librement/trash-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/trash-bundle)) — A trash for deleted resources: restore them, or purge them after a set time
- [`phil/recurrence`](https://github.com/parler-haut-interagir-librement/recurrence) · ✅ released ([Packagist](https://packagist.org/packages/phil/recurrence)) — Repeating dates from RFC 5545 rules: read, check, write, list occurrences
- [`phil/recurrence-bundle`](https://github.com/parler-haut-interagir-librement/recurrence-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/recurrence-bundle)) — A form for repeating events, a column for the rule, and the rule in words
- [`phil/feature-flags-bundle`](https://github.com/parler-haut-interagir-librement/feature-flags-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/feature-flags-bundle)) — Turn features off without a deploy, run A/B tests, stop calling a failing service
- [`phil/http-cache-tags-bundle`](https://github.com/parler-haut-interagir-librement/http-cache-tags-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/http-cache-tags-bundle)) — Cache whole pages in Varnish or a CDN, purge exactly what an edit changed
- [`phil/standard-webhooks`](https://github.com/parler-haut-interagir-librement/standard-webhooks) · ✅ released ([Packagist](https://packagist.org/packages/phil/standard-webhooks)) — Sign and verify webhooks to the Standard Webhooks specification
- [`phil/standard-webhooks-bundle`](https://github.com/parler-haut-interagir-librement/standard-webhooks-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/standard-webhooks-bundle)) — Verified webhook deliveries as controller arguments, and signed webhooks sent
- [`phil/circuit-breaker`](https://github.com/parler-haut-interagir-librement/circuit-breaker) · ✅ released ([Packagist](https://packagist.org/packages/phil/circuit-breaker)) — One circuit breaker for HTTP clients and feature flags
- [`phil/circuit-breaker-bundle`](https://github.com/parler-haut-interagir-librement/circuit-breaker-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/circuit-breaker-bundle)) — One circuit breaker wired into Symfony HTTP clients and feature flags
- [`phil/console-bundle`](https://github.com/parler-haut-interagir-librement/console-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/console-bundle)) — Console guards per environment and timestamped output
- `phil/doctrine-behaviours` · 🧪 95% — Opt-in timestamps, blame, soft delete and trees for Doctrine entities
- `phil/doctrine-behaviours-bundle` · 🧪 93% — Entity behaviours switched on by configuration in Symfony
- `phil/almanac` · 🧪 85% — Easter, Moon phases, seasons and dates in words, for any year
- `phil/almanac-bundle` · 🧪 90% — Holidays and computed dates in configuration, editable, shown in Twig
- `phil/scheduled-transitions-bundle` · 🧪 96% — Publish and unpublish on a schedule, with nobody online
- `phil/tenancy-bundle` · 🧪 72% — Which tenant an account acts in, switched instantly and enforced in every query
- `phil/usage-meter` · 🧪 90% — Measure what each subject used and refuse an action past its quota
- `phil/api-contract` · 🧪 72% — Problem details, deprecation signals and idempotency keys for HTTP APIs
- `phil/api-contract-bundle` · 🧪 93% — Problem details, replayed idempotent requests and deprecation notices in Symfony
- `phil/usage-meter-bundle` · 🧪 93% — Usage meters stored with DBAL, rate limiters and purge commands
- `phil/idempotency` · 🧪 92% — Idempotency keys for APIs, Messenger, payment webhooks and double form posts
- `phil/encrypted-fields` · 🧪 93% — Doctrine columns encrypted with libsodium, blind indexes, key rotation
- `phil/encrypted-fields-bundle` · 🧪 86% — Encrypted fields configured in Symfony, keys in Symfony secrets or a KMS
- `phil/rate-limit-bundle` · 🧪 97% — Rate limits declared by attribute on routes, forms and APIs
- `phil/api-keys-bundle` · 🧪 88% — Personal access tokens for a public API: scopes, expiry, revocation, quotas
- `phil/rate-limit` · 🧪 95% — The production guard of Symfony rate limits: the build fails on a limiter that counts per server
- `phil/spreadsheet` · 🗓️ planned — Read and write XLSX, ODS and CSV
- `phil/import-wizard` · 🗓️ planned — Guided file import, column by column
- `phil/json-canvas` · 🗓️ planned — Read and write the open JSON Canvas format
- `phil/open-data` · 🗓️ planned — Publish a site's open data
- `phil/number-words` · 🗓️ planned — Numbers written in words, in every language
- `phil/natural-dates` · 🗓️ planned — Dates typed in words ("next Thursday 7 pm") understood in each language
- `phil/timezone-display` · 🗓️ planned — Times shown in the visitor's time zone
- `phil/safe-http` · 🗓️ planned — A protected HTTP client for packages that read other sites: SSRF protection, size and time limits
- `phil/rules` · 🗓️ planned — Fixed, composable conditions evaluated without code, read by prices, promotions and access
- `phil/rules-bundle` · 🗓️ planned — Named rules in Symfony, their conditions as tagged services
- `phil/measurement` · 🗓️ planned — Units of measure and their conversion, per sales channel
- `phil/measurement-bundle` · 🗓️ planned — Measures in Symfony forms, Doctrine and Twig
- `phil/custom-fields` · 🗓️ planned — Custom fields: types, field sets applied by category, protected and formula fields
- `phil/custom-fields-bundle` · 🗓️ planned — Custom fields in Symfony: generated forms and list filters
- `phil/field-layout` · 🗓️ planned — Declared layout of edit forms: tabs, widths, visibility conditions
- `phil/field-layout-bundle` · 🗓️ planned — Field layouts rendered by a Symfony form theme

</details>

<details>
<summary><b>Content &amp; text</b> — ✅ 17 · 🧪 5 · 🗓️ 28</summary>

- [`phil/ujo`](https://github.com/parler-haut-interagir-librement/ujo) · ✅ released ([Packagist](https://packagist.org/packages/phil/ujo)) — UJO (Universal JSON Output) documents read strictly, checked block by block, rendered as safe HTML
- [`phil/ujo-bundle`](https://github.com/parler-haut-interagir-librement/ujo-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/ujo-bundle)) — UJO (Universal JSON Output) documents in Doctrine, forms and Twig
- [`phil/markup`](https://github.com/parler-haut-interagir-librement/markup) · ✅ released ([Packagist](https://packagist.org/packages/phil/markup)) — Markdown, BBCode, MediaWiki, DokuWiki, Creole, HTML or plain text turned into safe HTML
- [`phil/markup-bundle`](https://github.com/parler-haut-interagir-librement/markup-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/markup-bundle)) — Markup formats rendered safely in Twig and converted to UJO (Universal JSON Output), as Symfony services
- [`phil/block-editor-bundle`](https://github.com/parler-haut-interagir-librement/block-editor-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/block-editor-bundle)) — A block editor for Symfony forms in Stimulus, writing UJO (Universal JSON Output) checked on the server
- [`phil/edit-lock-bundle`](https://github.com/parler-haut-interagir-librement/edit-lock-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/edit-lock-bundle)) — One writer per block: edit leases, presence and saves pushed through Mercure
- [`phil/text-diff`](https://github.com/parler-haut-interagir-librement/text-diff) · ✅ released ([Packagist](https://packagist.org/packages/phil/text-diff)) — What changed between two texts, word by word, paragraph by paragraph or block by block
- [`phil/highlight`](https://github.com/parler-haut-interagir-librement/highlight) · ✅ released ([Packagist](https://packagist.org/packages/phil/highlight)) — Code in 24 languages coloured on the server, as plain HTML any stylesheet can theme
- [`phil/css-sanitizer`](https://github.com/parler-haut-interagir-librement/css-sanitizer) · ✅ released ([Packagist](https://packagist.org/packages/phil/css-sanitizer)) — Let people style their pages without their CSS running code, loading what it should not, or leaving its frame
- [`phil/taxonomy-bundle`](https://github.com/parler-haut-interagir-librement/taxonomy-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/taxonomy-bundle)) — Tags and a translated category tree for any resource, with form types
- [`phil/svg-sanitizer`](https://github.com/parler-haut-interagir-librement/svg-sanitizer) · ✅ released ([Packagist](https://packagist.org/packages/phil/svg-sanitizer)) — Purify SVG: allow-list of elements and attributes, no script, no external reference
- [`phil/svg-chart`](https://github.com/parler-haut-interagir-librement/svg-chart) · ✅ released ([Packagist](https://packagist.org/packages/phil/svg-chart)) — Charts drawn as SVG on the server, from the configuration a chart editor already writes
- [`phil/text-diff-bundle`](https://github.com/parler-haut-interagir-librement/text-diff-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/text-diff-bundle)) — Text comparison in Twig and Stimulus
- [`phil/highlight-bundle`](https://github.com/parler-haut-interagir-librement/highlight-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/highlight-bundle)) — Highlighting wired into UJO (Universal JSON Output) rendering and Twig, with a theme
- [`phil/footnotes-sidenotes`](https://github.com/parler-haut-interagir-librement/footnotes-sidenotes) · ✅ released ([Packagist](https://packagist.org/packages/phil/footnotes-sidenotes)) — Footnotes and side notes
- [`phil/content-warnings`](https://github.com/parler-haut-interagir-librement/content-warnings) · ✅ released ([Packagist](https://packagist.org/packages/phil/content-warnings)) — Content warnings for games, books, articles and events, with a translated base list
- [`phil/content-warnings-bundle`](https://github.com/parler-haut-interagir-librement/content-warnings-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/content-warnings-bundle)) — Content warnings in forms, pages and filters
- `phil/content-bundle` · 🧪 88% — Pages and articles stored by locale, stage and version, published from draft to live
- `phil/comments-bundle` · 🧪 85% — Comments and suggested changes anchored to passages, following the text as it changes
- `phil/latex-mathml` · 🧪 80% — LaTeX formulas turned into the MathML that browsers draw, on the server
- `phil/svg-blocks` · 🧪 90% — Formulas, diagrams, charts and QR codes of block documents drawn once, on the server
- `phil/svg-blocks-bundle` · 🧪 85% — Block drawings made on save in Symfony, with Mermaid in a container
- `phil/wiki-bundle` · 🗓️ planned — A collaborative wiki: pages, compared revisions, `[[links]]`, block locks
- `phil/faq-bundle` · 🗓️ planned — Frequently asked questions by section, searchable, with structured data
- `phil/glossary-bundle` · 🗓️ planned — A glossary whose terms are linked automatically in texts
- `phil/timeline-bundle` · 🗓️ planned — Timelines of dated content
- `phil/series-bundle` · 🗓️ planned — Content series
- `phil/citations` · 🗓️ planned — Citations and bibliographies in common styles
- `phil/credits` · 🗓️ planned — The credits page of a work: contributors, roles, order
- `phil/content-templates` · 🗓️ planned — Templates for new content
- `phil/content-queries` · 🗓️ planned — Content lists defined by a query in the administration
- `phil/curated-lists` · 🗓️ planned — Hand-picked, annotated lists of content
- `phil/related-content` · 🗓️ planned — Related content and related products
- `phil/content-expiry` · 🗓️ planned — Content that shows its age or expires on a date
- `phil/content-transfer` · 🗓️ planned — Move content from one site to another with its media and links
- `phil/editorial-calendar` · 🗓️ planned — The editorial calendar of publications
- `phil/page-protection` · 🗓️ planned — Pages locked against editing or reserved to roles
- `phil/reading-progress` · 🗓️ planned — Reading progress through long content
- `phil/dictionary` · 🗓️ planned — A dictionary and thesaurus behind a port
- `phil/release-notes` · 🗓️ planned — Announced release notes
- `phil/publishing` · 🗓️ planned — The PagePublished event and its contract, for the content lifecycle
- `phil/story-graph` · 🗓️ planned — A branching story graph for branching lessons and gamebooks
- `phil/content-access` · 🗓️ planned — Content access by entitlement: public, members, tiers, early access, fixed or sliding periods
- `phil/content-access-bundle` · 🗓️ planned — Content access in Symfony: voters, Twig checks and rule administration
- `phil/content-archive` · 🗓️ planned — A portable content archive: faithful UJO (Universal JSON Output), readable Markdown, media
- `phil/share-links` · 🗓️ planned — Named private links to unpublished content, with visit counts and revocation
- `phil/share-links-bundle` · 🗓️ planned — Share links in Symfony: routes, sandboxed preview, revocation
- `phil/suggested-edits` · 🗓️ planned — Suggested edits to a message or to a whole piece of content
- `phil/live-preview-bundle` · 🗓️ planned — Live preview on several targets and device sizes, morphed in place by Turbo
- `phil/form-logic` · 🗓️ planned — Conditional form logic evaluated the same way in PHP and Stimulus, the server as judge

</details>

<details>
<summary><b>Languages, translation &amp; typography</b> — ✅ 2 · 🧪 3 · 🗓️ 2</summary>

- [`phil/typography`](https://github.com/parler-haut-interagir-librement/typography) · ✅ released ([Packagist](https://packagist.org/packages/phil/typography)) — Real quotes, dashes, French spaces and soft hyphens in your HTML, in every language
- [`phil/typography-bundle`](https://github.com/parler-haut-interagir-librement/typography-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/typography-bundle)) — Typography everywhere a Symfony application prints text
- `phil/translation-bundle` · 🧪 83% — A translation screen: segments that survive edits, a memory and a checking glossary
- `phil/translation-memory` · 🧪 87% — Segment-by-segment translation that reuses past work and keeps terms consistent
- `phil/locale-dimensions` · 🧪 95% — Locales, versions and declared fallback chains, as plain value objects
- `phil/machine-translation` · 🗓️ planned — Machine-suggested translations, always reviewed
- `phil/translation-ui` · 🗓️ planned — The screen for translating a site's content and messages

</details>

<details>
<summary><b>Media, documents &amp; print</b> — ✅ 5 · 🧪 11 · 🗓️ 18</summary>

- [`phil/fonts`](https://github.com/parler-haut-interagir-librement/fonts) · ✅ released ([Packagist](https://packagist.org/packages/phil/fonts)) — What a font file says about itself — names, weight, embedding licence — and its `@font-face`
- [`phil/print-preflight`](https://github.com/parler-haut-interagir-librement/print-preflight) · ✅ released ([Packagist](https://packagist.org/packages/phil/print-preflight)) — Catch what a printer would refuse before the file reaches it
- [`phil/print-compositor`](https://github.com/parler-haut-interagir-librement/print-compositor) · ✅ released ([Packagist](https://packagist.org/packages/phil/print-compositor)) — Garment mock-ups and print files, one layer per ink
- [`phil/qr-code`](https://github.com/parler-haut-interagir-librement/qr-code) · ✅ released ([Packagist](https://packagist.org/packages/phil/qr-code)) — QR codes in plain PHP, Reed-Solomon included, in SVG and PNG
- [`phil/qr-code-bundle`](https://github.com/parler-haut-interagir-librement/qr-code-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/qr-code-bundle)) — QR codes in Twig, routes and typed contents (URL, vCard, Wi-Fi, iCalendar)
- `phil/media-bundle` · 🧪 90% — Uploaded files and images, described, versioned and served at signed URLs
- `phil/document-import` · 🧪 73% — Word-processing documents, Markdown and HTML turned into UJO (Universal JSON Output), with a report of what did not fit
- `phil/epub` · 🧪 85% — EPUB 3 books from your HTML, valid for EPUBCheck and readable by assistive technologies
- `phil/paged-media` · 🧪 70% — PDF documents from PHP, with real fonts and paged HTML/CSS engines
- `phil/paged-media-bundle` · 🧪 94% — PDFs in Symfony, from a native writer or Gotenberg, through one service, now or through Messenger
- `phil/document-import-bundle` · 🧪 90% — Document import wired into the media library
- `phil/fonts-bundle` · 🧪 95% — Fonts configured for PDF and media
- `phil/epub-bundle` · 🧪 95% — EPUB generation in Symfony
- `phil/print-preflight-bundle` · 🧪 90% — Preflight wired into PDF generation
- `phil/paged-media-weasyprint` · 🧪 92% — The WeasyPrint engine for paged media: HTML and CSS laid out as PDF, offline
- `phil/creation-disclosure` · 🧪 90% — How a work was made, declared part by part in the IPTC Digital Source Type vocabulary
- `phil/gallery-bundle` · 🗓️ planned — Photo galleries by album and by event
- `phil/video-bundle` · 🗓️ planned — Hosted or linked videos, subtitles and chapters
- `phil/podcast-bundle` · 🗓️ planned — Podcasts: episodes, Podcasting 2.0 feeds, chapters, transcripts
- `phil/live-stream-bundle` · 🗓️ planned — Live streams announced, embedded and archived
- `phil/transcription` · 🗓️ planned — Audio and video transcription behind a port
- `phil/image-editor` · 🗓️ planned — An image editor: crop, rotate, filters, annotations
- `phil/avatar` · 🗓️ planned — Generated avatars
- `phil/document-preview` · 🗓️ planned — Document previews
- `phil/pdf-watermark` · 🗓️ planned — Personalised watermarks on sold PDFs
- `phil/braille-export` · 🗓️ planned — Contracted or uncontracted braille export of a document
- `phil/demo-videos` · 🗓️ planned — Demo videos of a product or package
- `phil/audio` · 🗓️ planned — Audio: optional transcoding, waveform, clips and an accessible player that works without JavaScript
- `phil/audio-bundle` · 🗓️ planned — Audio in Symfony: player component, uploads and transcoding jobs
- `phil/music-bundle` · 🗓️ planned — An artist's or band's music: albums, tracks, sales and listening without purchase
- `phil/timed-text` · 🗓️ planned — Timed text read and written: WebVTT, SRT, chapters and Podcasting 2.0 transcripts
- `phil/braille-export-liblouis` · 🗓️ planned — The braille export adapter that calls liblouis
- `phil/slides` · 🗓️ planned — Slides read from a UJO document, with presenter mode, notes, timer and PDF export
- `phil/diagram` · 🗓️ planned — Diagrams written as text and rendered as SVG on the server, with a text description

</details>

<details>
<summary><b>Search, SEO &amp; the open web</b> — ✅ 5 · 🧪 5 · 🗓️ 14</summary>

- [`phil/sitemap`](https://github.com/parler-haut-interagir-librement/sitemap) · ✅ released ([Packagist](https://packagist.org/packages/phil/sitemap)) — Sitemap XML built from checked pages, cut to the protocol's limits
- [`phil/sitemap-bundle`](https://github.com/parler-haut-interagir-librement/sitemap-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/sitemap-bundle)) — `/sitemap.xml` from route options, URL providers and an event
- [`phil/structured-data`](https://github.com/parler-haut-interagir-librement/structured-data) · ✅ released ([Packagist](https://packagist.org/packages/phil/structured-data)) — A page's schema.org graph assembled from JSON-LD pieces
- [`phil/redirects-bundle`](https://github.com/parler-haut-interagir-librement/redirects-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/redirects-bundle)) — Managed 301 redirects, 404 tracking, old domains
- [`phil/well-known-bundle`](https://github.com/parler-haut-interagir-librement/well-known-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/well-known-bundle)) — `/.well-known/` endpoints: security.txt, change-password, WebFinger, nodeinfo
- `phil/search-bundle` · 🧪 70% — Full-text search over your own resources, kept up to date at each Doctrine flush
- `phil/search-loupe` · 🧪 90% — Typo-tolerant search in SQLite files, with no server to run
- `phil/social-cards` · 🧪 89% — Open Graph tags and generated share images
- `phil/social-cards-bundle` · 🧪 90% — Share metadata and generated cards in Symfony, with a preview of incoming links
- `phil/structured-data-bundle` · 🧪 95% — A page's schema.org graph in Symfony, with a command that checks it
- `phil/search-synonyms` · 🗓️ planned — Search synonyms managed in the administration
- `phil/feed-bundle` · 🗓️ planned — RSS, Atom and JSON Feed of any content
- `phil/indexnow` · 🗓️ planned — Notify search engines through IndexNow
- `phil/seo-check` · 🗓️ planned — SEO checks at publication: title, description, links, structured data
- `phil/link-checker` · 🗓️ planned — Find and report dead links
- `phil/short-link-bundle` · 🗓️ planned — Short links on a dedicated domain, visits counted without tracking
- `phil/activitypub-bundle` · 🗓️ planned — Full ActivityPub federation for members (opt-in) and groups
- `phil/webmention-bundle` · 🗓️ planned — Send and receive Webmentions
- `phil/oembed-bundle` · 🗓️ planned — An oEmbed provider for your pages
- `phil/embed-bundle` · 🗓️ planned — Embeddable features for other sites: token, theme, `frame-ancestors`
- `phil/sitemap-visual` · 🗓️ planned — A visual site map for visitors
- `phil/search-console` · 🗓️ planned — Google Search Console data, read for any site
- `phil/search-console-bundle` · 🗓️ planned — Search Console in Symfony: credentials, scheduled fetches, dashboard widgets
- `phil/feed-import` · 🗓️ planned — RSS and Atom feeds imported as content

</details>

<details>
<summary><b>Identity, access &amp; security</b> — ✅ 7 · 🧪 4 · 🗓️ 13</summary>

- [`phil/bot-detection-bundle`](https://github.com/parler-haut-interagir-librement/bot-detection-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/bot-detection-bundle)) — Tell a robot from a human in the browser, without a CAPTCHA
- [`phil/spam-protection`](https://github.com/parler-haut-interagir-librement/spam-protection) · ✅ released ([Packagist](https://packagist.org/packages/phil/spam-protection)) — Spot spam in a form submission without a CAPTCHA, in plain PHP
- [`phil/spam-protection-bundle`](https://github.com/parler-haut-interagir-librement/spam-protection-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/spam-protection-bundle)) — Keep spam out of Symfony forms without a CAPTCHA, a third party or an identifier
- [`phil/passwords`](https://github.com/parler-haut-interagir-librement/passwords) · ✅ released ([Packagist](https://packagist.org/packages/phil/passwords)) — A strength meter with its own dictionaries, k-anonymous breach checks, generation
- [`phil/route-access-check`](https://github.com/parler-haut-interagir-librement/route-access-check) · ✅ released ([Packagist](https://packagist.org/packages/phil/route-access-check)) — Fail CI when a route has no access rule
- [`phil/route-access-check-bundle`](https://github.com/parler-haut-interagir-librement/route-access-check-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/route-access-check-bundle)) — The route access check as a Symfony command, with a baseline and a strict mode
- [`phil/upload-scan`](https://github.com/parler-haut-interagir-librement/upload-scan) · ✅ released ([Packagist](https://packagist.org/packages/phil/upload-scan)) — Antivirus scanning of uploads behind a port
- `phil/user-secrets-bundle` · 🧪 80% — Keys people lend your application, sealed and theirs alone
- `phil/identity-client-bundle` · 🧪 85% — Connect a Symfony site to an OpenID provider, on Symfony 8.2's `oidc_login`
- `phil/browser-security-bundle` · 🧪 97% — The protections a Symfony application asks of the browser: CSP with nonces, HSTS, signed cookies
- `phil/upload-scan-bundle` · 🧪 88% — Upload scanning in Symfony: a file constraint, quarantine and rescans
- `phil/identity-provider-bundle` · 🗓️ planned — An OpenID Connect provider for Symfony: passkeys, passwords, TOTP, step-up
- `phil/identity-provider-google` · 🗓️ planned — Google sign-in for the identity provider, the first federated sign-in package
- `phil/organizations-bundle` · 🗓️ planned — Organisations, roles and invitations
- `phil/access-bundle` · 🗓️ planned — Access rights per site
- `phil/webauthn-step-up` · 🗓️ planned — Confirm a sensitive action with a passkey
- `phil/fraud-signals` · 🗓️ planned — Fraud signals on orders and sign-ups
- `phil/trust-levels` · 🗓️ planned — Trust levels that open rights with activity
- `phil/verification-marks` · 🗓️ planned — Verified-account marks
- `phil/invitations` · 🗓️ planned — Member invitations, with limits
- `phil/resource-permissions` · 🗓️ planned — Per-resource permissions inherited down a tree, the most specific one winning
- `phil/access-codes` · 🗓️ planned — Single-use codes in named batches, with a redemption page and codes stored hashed
- `phil/access-links` · 🗓️ planned — Invitations by personal link: token, validity, reminders, editable reply
- `phil/delegated-accounts` · 🗓️ planned — A parent manages the accounts of their minor children, with age checks

</details>

<details>
<summary><b>Privacy, accessibility &amp; compliance</b> — 🧪 11 · 🗓️ 6</summary>

- `phil/privacy-bundle` · 🧪 95% — Declare personal fields, redact logs, answer access and erasure requests (Loi 25, GDPR)
- `phil/analytics-bundle` · 🧪 95% — Visits counted in daily aggregates, never tied to a person
- `phil/audit-bundle` · 🧪 60% — An append-only, tamper-evident audit trail that still lets you erase personal information
- `phil/ip-anonymizer` · 🧪 97% — Truncate, salt-hash and generalise IP addresses
- `phil/legal-notices` · 🧪 96% — A site's legal notices and privacy policy
- `phil/terms-bundle` · 🧪 94% — Versioned terms of use and their acceptance
- `phil/accessibility-check` · 🧪 94% — Accessibility checks at publication: alt texts, heading order, contrast
- `phil/accessibility-statement` · 🧪 96% — A site's accessibility statement
- `phil/accessibility-statement-bundle` · 🧪 89% — A versioned accessibility statement page in English and French, with a footer link
- `phil/legal-notices-bundle` · 🧪 90% — Legal notice and privacy policy pages, per locale, with every version at its own address
- `phil/indexing-consent` · 🧪 93% — A public record's reach decided by the person it is about: listed, unindexed or unlisted
- `phil/accessibility-info` · 🗓️ planned — Accessibility information for a venue or event
- `phil/easy-read` · 🗓️ planned — Easy-read versions of content, and their checks
- `phil/age-gate` · 🗓️ planned — Declarative age checks for content or listings
- `phil/heatmaps` · 🗓️ planned — Aggregated heatmaps, with no identifier
- `phil/guardian-consent` · 🗓️ planned — Age brackets and parental consent for minors under 14, as Quebec privacy law requires
- `phil/account-lifecycle` · 🗓️ planned — Inactive accounts warned, deactivated, then deleted or anonymized

</details>

<details>
<summary><b>Community</b> — ✅ 2 · 🧪 4 · 🗓️ 41</summary>

- [`phil/poll`](https://github.com/parler-haut-interagir-librement/poll) · ✅ released ([Packagist](https://packagist.org/packages/phil/poll)) — A voting engine: ballots checked against their poll's rules, counted into standings
- [`phil/listings`](https://github.com/parler-haut-interagir-librement/listings) · ✅ released ([Packagist](https://packagist.org/packages/phil/listings)) — The listings core: criteria, expiry, replies, moderation
- `phil/reactions-bundle` · 🧪 86% — Reactions to content, one per member, list chosen per site
- `phil/mentions-bundle` · 🧪 88% — @mentions in texts, and their notifications
- `phil/poll-bundle` · 🧪 85% — The voting engine: single, multiple or ranked choice
- `phil/onboarding-bundle` · 🧪 90% — Welcoming new members: steps, guided tour, checklist
- `phil/forum-bundle` · 🗓️ planned — Forums by section, with chat, reporting and per-section moderation
- `phil/moderation-bundle` · 🗓️ planned — One report queue for forums, comments, reactions, listings and messages
- `phil/follow-bundle` · 🗓️ planned — Follow content, threads, listings or members
- `phil/conversation-bundle` · 🗓️ planned — Private messages one-to-one or in groups, encrypted at rest
- `phil/groups-bundle` · 🗓️ planned — Member groups
- `phil/profiles-bundle` · 🗓️ planned — A member's public page: what they show, and to whom
- `phil/reviews-bundle` · 🗓️ planned — Moderated reviews and ratings of products, games or places
- `phil/survey-bundle` · 🗓️ planned — Questionnaires with sections and conditional logic
- `phil/ideas-bundle` · 🗓️ planned — An idea box with statuses and votes
- `phil/qa-bundle` · 🗓️ planned — Questions and answers, the best one accepted
- `phil/code-of-conduct` · 🗓️ planned — A code of conduct, its acceptance and its reports
- `phil/bookmarks-bundle` · 🗓️ planned — Members' bookmarks, sorted into lists
- `phil/user-lists` · 🗓️ planned — Lists of members kept by a member
- `phil/classifieds-bundle` · 🗓️ planned — Classified ads between members, without payment
- `phil/job-board-bundle` · 🗓️ planned — A community's job and contract offers
- `phil/matchmaking-bundle` · 🗓️ planned — Find partners: criteria, approximate place or online, safety first
- `phil/tasks-bundle` · 🗓️ planned — Team tasks and kanban boards
- `phil/roadmap-bundle` · 🗓️ planned — A public roadmap and its votes
- `phil/collab-whiteboard` · 🗓️ planned — A shared real-time whiteboard
- `phil/mind-map` · 🗓️ planned — A shared mind map
- `phil/family-tree` · 🗓️ planned — A family tree
- `phil/secret-santa` · 🗓️ planned — Gift exchanges drawn at random
- `phil/expense-split` · 🗓️ planned — Split a group's expenses
- `phil/ownership-transfer` · 🗓️ planned — Transfer ownership of content or a group to another member
- `phil/membership-bundle` · 🗓️ planned — Membership of an organisation: dues, member card, renewal
- `phil/assembly-bundle` · 🗓️ planned — General assemblies: notice, proposals, votes, minutes
- `phil/budget-transparency` · 🗓️ planned — An organisation's budget published and explained
- `phil/sponsors-bundle` · 🗓️ planned — Sponsors and their tiers
- `phil/press-kit-bundle` · 🗓️ planned — A press kit: logos, photos, biographies, releases
- `phil/spaces` · 🗓️ planned — A registry of the modules a group or an organization switches on
- `phil/ranking` · 🗓️ planned — Popular, active, controversial and best-of sorts, shared by forum, ideas and Q&A
- `phil/reputation` · 🗓️ planned — Reputation from peer votes, with a daily cap and no downvotes
- `phil/community-notes` · 🗓️ planned — Community notes published by an explainable cross-agreement rule
- `phil/user-blocks` · 🗓️ planned — Ignore or mute a member, group, domain or keywords
- `phil/watched-words` · 🗓️ planned — Watched words that block, hold, flag, replace or tag
- `phil/incident-mode` · 🗓️ planned — A standalone incident mode: presets, mandatory duration, automatic lifting
- `phil/elections-bundle` · 🗓️ planned — Moderator elections by single transferable vote
- `phil/watch-party` · 🗓️ planned — Listen or watch together in sync, with a moderated chat
- `phil/milestones` · 🗓️ planned — Milestones on a counter and a production threshold for an item
- `phil/milestones-bundle` · 🗓️ planned — Milestones in Symfony: counters tied to site events, progress in Twig
- `phil/habits` · 🗓️ planned — A habit tracker with streaks and a smoothed strength score

</details>

<details>
<summary><b>Learning &amp; credentials</b> — ✅ 1 · 🧪 2 · 🗓️ 8</summary>

- [`phil/open-badges`](https://github.com/parler-haut-interagir-librement/open-badges) · ✅ released ([Packagist](https://packagist.org/packages/phil/open-badges)) — Issue, sign, verify, bake and revoke Open Badges 3.0 credentials
- `phil/open-badges-bundle` · 🧪 85% — Issuer profile, public key and verification page for Open Badges
- `phil/certificates-bundle` · 🧪 85% — Verifiable certificates: criteria, PDF with QR code, public registry
- `phil/courses-bundle` · 🗓️ planned — Online courses: modules, lessons, progress
- `phil/mentoring-bundle` · 🗓️ planned — Mentoring: matching, sessions, follow-up
- `phil/assessment` · 🗓️ planned — Assessment: question types, certainty-based marking, a versioned question bank
- `phil/assessment-bundle` · 🗓️ planned — Assessment in Symfony: quiz screens, attempts and question bank administration
- `phil/competencies` · 🗓️ planned — Competency frameworks, learning plans and Open Badges alignments
- `phil/peer-review` · 🗓️ planned — Peer assessment in phases, with a double grade and optional grader calibration
- `phil/proposal-review` · 🗓️ planned — One jury review engine for calls, courses and contests, with pairwise voting
- `phil/spaced-repetition` · 🗓️ planned — Generic spaced repetition: the FSRS algorithm, cards and reviews

</details>

<details>
<summary><b>Notifications, mail &amp; messaging</b> — ✅ 3 · 🧪 2 · 🗓️ 11</summary>

- [`phil/instant-messenger`](https://github.com/parler-haut-interagir-librement/instant-messenger) · ✅ released ([Packagist](https://packagist.org/packages/phil/instant-messenger)) — Messaging handles per service: WhatsApp, Telegram, Signal, Matrix and more
- [`phil/instant-messenger-bundle`](https://github.com/parler-haut-interagir-librement/instant-messenger-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/instant-messenger-bundle)) — A messaging handle field, a constraint and Twig filters
- [`phil/bounce-parser`](https://github.com/parler-haut-interagir-librement/bounce-parser) · ✅ released ([Packagist](https://packagist.org/packages/phil/bounce-parser)) — Parse DSN and ARF bounces and auto-replies
- `phil/notifications-bundle` · 🧪 81% — Toasts, a notification centre, email digests, Web Push, Discord or Slack
- `phil/email-address` · 🧪 92% — Email address validation
- `phil/newsletter-bundle` · 🗓️ planned — Newsletters: lists, double opt-in, templates, sending through Symfony Mailer
- `phil/newsletter-archive` · 🗓️ planned — The public archive of sent newsletters
- `phil/email-templates-bundle` · 🗓️ planned — Email templates shared between several sites, with conditional blocks
- `phil/email-preview` · 🗓️ planned — Preview email templates
- `phil/mail-auth-check` · 🗓️ planned — Test a sending domain's SPF, DKIM and DMARC
- `phil/inbound-mail-bundle` · 🗓️ planned — Inbound mail, parsed and routed
- `phil/sms-bundle` · 🗓️ planned — Send and receive SMS on Symfony Notifier
- `phil/audience-segments` · 🗓️ planned — Audience segments defined by rules, for newsletters and notifications
- `phil/live-chat` · 🗓️ planned — Live chat with a visitor
- `phil/mime-reader` · 🗓️ planned — MIME email reading, shared by bounce parsing and inbound mail
- `phil/email-address-bundle` · 🗓️ planned — Email addresses in Symfony: a constraint, bounce rules and IMAP reading

</details>

<details>
<summary><b>Events, calendar &amp; booking</b> — ✅ 2 · 🧪 3 · 🗓️ 30</summary>

- [`phil/reservation`](https://github.com/parler-haut-interagir-librement/reservation) · ✅ released ([Packagist](https://packagist.org/packages/phil/reservation)) — The booking core: resources, slots, rules, conflicts and reminders
- [`phil/checkin`](https://github.com/parler-haut-interagir-librement/checkin) · ✅ released ([Packagist](https://packagist.org/packages/phil/checkin)) — A code read at a door, decided at once, recorded once, online or offline
- `phil/calendar-bundle` · 🧪 61% — Events, repeating or not, as a month, week, day, list or posters
- `phil/reservation-bundle` · 🧪 85% — Bookings in Symfony: resources, slots, conflicts and reminders
- `phil/checkin-bundle` · 🧪 85% — The shared check-in core: ticket or registration read, attendance noted
- `phil/convention-bundle` · 🗓️ planned — A convention programme: tables, seats, sign-ups, venues and rooms
- `phil/booking-bundle` · 🗓️ planned — Appointment booking on the reservation core
- `phil/scheduling-poll-bundle` · 🗓️ planned — Availability polls, answered by link without an account
- `phil/shared-timer-bundle` · 🗓️ planned — Shared timers over Mercure, chained, with a remote control
- `phil/qr-attendance` · 🗓️ planned — Attendance read from QR codes
- `phil/waitlist-bundle` · 🗓️ planned — Waiting lists and released places
- `phil/workshops-bundle` · 🗓️ planned — Workshops: sessions, places, sign-ups
- `phil/carpool-bundle` · 🗓️ planned — Carpooling to an event
- `phil/lodging-bundle` · 🗓️ planned — Event lodging: rooms, beds, assignments
- `phil/meal-planning` · 🗓️ planned — Event meals: menus, allergies, quantities
- `phil/equipment-rental` · 🗓️ planned — Equipment rental on the reservation core
- `phil/event-weather` · 🗓️ planned — Forecast weather for an outdoor event
- `phil/participant-safety-info` · 🗓️ planned — Participants' safety information, encrypted, read by organisers only
- `phil/press-accreditation` · 🗓️ planned — Media accreditation for an event
- `phil/lost-and-found` · 🗓️ planned — An event's lost and found
- `phil/schedule-app` · 🗓️ planned — An event programme as an installable offline app with a personal schedule
- `phil/digital-signage` · 🗓️ planned — Digital signage: schedules and announcements on screens
- `phil/virtual-queue` · 🗓️ planned — A virtual queue for a booth or an activity
- `phil/qr-menu` · 🗓️ planned — A menu read from a QR code
- `phil/calendar-sync` · 🗓️ planned — External calendars synced: busy times blocked from ICS and CalDAV
- `phil/calendar-activitypub` · 🗓️ planned — Calendar events federated through ActivityPub
- `phil/availability` · 🗓️ planned — Absences with handover, date exceptions and holidays imported from ICS
- `phil/reservation-teams` · 🗓️ planned — Collective reservations: weighted round robin, groups and reassignment
- `phil/call-for-papers-bundle` · 🗓️ planned — A call for proposals: deadlines by session type, co-presenters, review cycle
- `phil/speakers-bundle` · 🗓️ planned — Speakers with no account required, their profile reused from event to event
- `phil/shifts` · 🗓️ planned — Volunteer shifts, three assignment modes, a swap board and a reserve
- `phil/shifts-bundle` · 🗓️ planned — Volunteer shifts in Symfony: sign-up, swap board, coordination screens
- `phil/signup-rounds` · 🗓️ planned — Sign-up groups with capacities, and ranked choices processed in rounds
- `phil/assignment` · 🗓️ planned — Assignment by ranked preferences: ranked-choice rounds, then global optimization
- `phil/stockroom` · 🗓️ planned — A props stockroom: containers, items, movements and packing lists

</details>

<details>
<summary><b>Commerce</b> — ✅ 4 · 🧪 11 · 🗓️ 27</summary>

- [`phil/money`](https://github.com/parler-haut-interagir-librement/money) · ✅ released ([Packagist](https://packagist.org/packages/phil/money)) — Amounts of money as exact integers in a known currency, with no float anywhere
- [`phil/money-bundle`](https://github.com/parler-haut-interagir-librement/money-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/money-bundle)) — Money in Symfony forms, validation, Twig and Doctrine, without floats
- [`phil/tax`](https://github.com/parler-haut-interagir-librement/tax) · ✅ released ([Packagist](https://packagist.org/packages/phil/tax)) — Several taxes on one sale, itemised to the cent
- [`phil/commerce-product-template`](https://github.com/parler-haut-interagir-librement/commerce-product-template) · ✅ released ([Packagist](https://packagist.org/packages/phil/commerce-product-template)) — Product templates that generate combinations, SKUs, mock-ups and production sheets
- `phil/commerce-bundle` · 🧪 90% — Orders, prices, taxes, payments and receipts for a Symfony store, with modules on top
- `phil/commerce-catalog-bundle` · 🧪 55% — Products, price books and promotions
- `phil/commerce-logistics-bundle` · 🧪 84% — Stock per location, reservations, parcels and delivery methods per zone
- `phil/commerce-pos-bundle` · 🧪 80% — A cash register for counter sales: tills, shifts, cash counts, layaways, offline sales
- `phil/commerce-returns-bundle` · 🧪 82% — Returns from authorisation to refund, store credit or exchange, line by line
- `phil/commerce-stored-value-bundle` · 🧪 92% — Digital gift cards and store credit, spent as payments of an order
- `phil/commerce-subscription-bundle` · 🧪 93% — Recurring offers in tiers: trials, renewal, dunning and unlocked features
- `phil/commerce-syndication-bundle` · 🧪 85% — Resell another shop's products, orders forwarded to the supplier who ships
- `phil/commerce-wholesale-bundle` · 🧪 94% — Customer groups with their own prices and minimums, sales on credit with net terms
- `phil/commerce-product-template-bundle` · 🧪 75% — Product templates in the catalogue and the administration
- `phil/licensing-bundle` · 🧪 96% — Licences for a work or a digital product
- `phil/coupons-bundle` · 🗓️ planned — Promo codes usable without the catalogue: donations, tickets, memberships
- `phil/donations-bundle` · 🗓️ planned — One-off or monthly donations
- `phil/digital-downloads` · 🗓️ planned — Sell and deliver digital files
- `phil/product-bundles` · 🗓️ planned — Products sold together
- `phil/preorders-bundle` · 🗓️ planned — Pre-orders, charged at release
- `phil/receipt-email` · 🗓️ planned — Payment receipts and donation tax receipts by email
- `phil/invoicing-bundle` · 🗓️ planned — Invoices and their payments
- `phil/accounting-export` · 🗓️ planned — Export sales and payments to accounting
- `phil/affiliates-bundle` · 🗓️ planned — Affiliate links, commissions and payouts
- `phil/abandoned-cart` · 🗓️ planned — Abandoned-cart reminders, with the customer's consent
- `phil/inventory-alerts` · 🗓️ planned — Low-stock and back-in-stock alerts
- `phil/local-pickup` · 🗓️ planned — Pick up an order in store or at a convention booth
- `phil/trade-in-bundle` · 🗓️ planned — Trade in used items for credit
- `phil/auctions` · 🗓️ planned — Auctions: bids, reserve price, closing, payment
- `phil/product-feeds` · 🗓️ planned — Catalogue feeds for comparison sites and marketplaces
- `phil/shoppable-images` · 🗓️ planned — Images whose objects link to their product
- `phil/currency-display` · 🗓️ planned — Prices shown in the visitor's currency
- `phil/contracts-bundle` · 🗓️ planned — Contracts generated, sent and tracked
- `phil/crm-lite` · 🗓️ planned — A customer book and the history of exchanges
- `phil/commerce-promotions-bundle` · 🗓️ planned — Automatic promotions: buy X get Y, free shipping, usage limits
- `phil/commerce-payment-plans-bundle` · 🗓️ planned — Payment plans with a grace period; nothing ships before the last payment
- `phil/commerce-quick-order-bundle` · 🗓️ planned — Quick ordering by SKU or barcode, pasted lines, reorders and shared lists
- `phil/commerce-embed` · 🗓️ planned — A buy button and widget to embed in another page
- `phil/barcode` · 🗓️ planned — EAN, UPC, ISBN, Code 128 and GS1 barcodes
- `phil/barcode-bundle` · 🗓️ planned — Barcodes in Symfony: Twig rendering, validation, scanner input
- `phil/benefit-deliverables` · 🗓️ planned — Benefits owed to each member as a per-period checklist
- `phil/external-entitlements` · 🗓️ planned — Dated entitlements granted by external support platforms

</details>

<details>
<summary><b>Places, contacts &amp; directories</b> — ✅ 9 · 🧪 3 · 🗓️ 4</summary>

- [`phil/address`](https://github.com/parler-haut-interagir-librement/address) · ✅ released ([Packagist](https://packagist.org/packages/phil/address)) — Postal addresses checked and written the way each country writes them
- [`phil/address-bundle`](https://github.com/parler-haut-interagir-librement/address-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/address-bundle)) — An address form whose fields follow the chosen country
- [`phil/phone`](https://github.com/parler-haut-interagir-librement/phone) · ✅ released ([Packagist](https://packagist.org/packages/phil/phone)) — Phone numbers read as typed, checked against their country's plan, and formatted
- [`phil/phone-bundle`](https://github.com/parler-haut-interagir-librement/phone-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/phone-bundle)) — A phone field, a constraint, a column type and Twig filters
- [`phil/contact-form-bundle`](https://github.com/parler-haut-interagir-librement/contact-form-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/contact-form-bundle)) — A "write to us" page, protected from spam without a CAPTCHA
- [`phil/geo`](https://github.com/parler-haut-interagir-librement/geo) · ✅ released ([Packagist](https://packagist.org/packages/phil/geo)) — Coordinates, distances and bounding boxes as values, geocoding through the provider you pick
- [`phil/geo-bundle`](https://github.com/parler-haut-interagir-librement/geo-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/geo-bundle)) — Stored coordinates, distances in Twig, geocoders and nearest-first lists
- [`phil/opening-hours`](https://github.com/parler-haut-interagir-librement/opening-hours) · ✅ released ([Packagist](https://packagist.org/packages/phil/opening-hours)) — A place's opening hours, and whether it is open right now
- [`phil/opening-hours-bundle`](https://github.com/parler-haut-interagir-librement/opening-hours-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/opening-hours-bundle)) — An opening-hours form, a JSON column and localised hours in Twig
- `phil/contact` · 🧪 85% — Contact cards for people and organisations, as vCard or JSON-LD
- `phil/contact-bundle` · 🧪 95% — A contact card form, a JSON column and vCard downloads
- `phil/directory-bundle` · 🧪 92% — A directory of listings that members write and administrators publish
- `phil/map-bundle` · 🗓️ planned — Leaflet maps in Stimulus, on tracking-free tiles
- `phil/contact-sync` · 🗓️ planned — Contact synchronisation over CardDAV
- `phil/portfolio-bundle` · 🗓️ planned — A portfolio, one listing per project
- `phil/library-bundle` · 🗓️ planned — A game or book library: catalogue, loans, returns

</details>

<details>
<summary><b>Operations &amp; administration</b> — ✅ 6 · 🧪 4 · 🗓️ 11</summary>

- [`phil/migration`](https://github.com/parler-haut-interagir-librement/migration) · ✅ released ([Packagist](https://packagist.org/packages/phil/migration)) — Release notes and news that Doctrine migrations send to chat
- [`phil/migration-bundle`](https://github.com/parler-haut-interagir-librement/migration-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/migration-bundle)) — Each migration run announced once on your chat channels
- [`phil/backup-bundle`](https://github.com/parler-haut-interagir-librement/backup-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/backup-bundle)) — Backups and guarded restores: database, media, encryption, rotation
- [`phil/backup`](https://github.com/parler-haut-interagir-librement/backup) · ✅ released ([Packagist](https://packagist.org/packages/phil/backup)) — Back up a database and its media, encrypted and rotated, and prove they restore
- [`phil/monitoring-bundle`](https://github.com/parler-haut-interagir-librement/monitoring-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/monitoring-bundle)) — Health checks, maintenance mode, uptime, cron and queue health
- [`phil/reporting-bundle`](https://github.com/parler-haut-interagir-librement/reporting-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/reporting-bundle)) — Dashboards in Twig components, accessible charts, scheduled reports
- `phil/error-tracking` · 🧪 88% — Self-hosted error tracking, personal data scrubbed before anything is written
- `phil/error-tracking-bundle` · 🧪 89% — Error tracking in Symfony: groups, regressions by release, alerts through a queue
- `phil/broken-flow-alerts` · 🧪 90% — Alerts when a user journey stops completing
- `phil/settings-bundle` · 🧪 88% — Settings that users change themselves
- `phil/sites-console-bundle` · 🗓️ planned — Run several sites: versions, health, shared configuration, admin accounts
- `phil/status-page-bundle` · 🗓️ planned — A service status page
- `phil/bulk-actions` · 🗓️ planned — Bulk actions in an administration
- `phil/admin-notes` · 🗓️ planned — Internal admin notes on a record
- `phil/duplicate-detector` · 🗓️ planned — Detect and merge duplicate records
- `phil/dependency-report` · 🗓️ planned — A package's or site's dependencies and their licences
- `phil/secrets-rotation` · 🗓️ planned — Rotate an application's secrets
- `phil/helpdesk-bundle` · 🗓️ planned — A help desk: requests, queues, canned replies
- `phil/automations` · 🗓️ planned — No-code automations triggered by site events
- `phil/data-table-export` · 🗓️ planned — Rows exported as CSV, then XLSX
- `phil/expenses-bundle` · 🗓️ planned — Expense claims: displayed policy, nobody approves their own, private receipts

</details>

<details>
<summary><b>Integrations &amp; AI</b> — 🧪 1 · 🗓️ 6</summary>

- `phil/ai-bundle` · 🧪 70% — Language-model tasks that propose and never impose, counted to the token, forgetful of every word
- `phil/mcp-bundle` · 🗓️ planned — An MCP server on Symfony AI, within the user's rights, audited
- `phil/slack-interactions-bundle` · 🗓️ planned — Signed Slack commands and interactions
- `phil/notion` · 🗓️ planned — Read and write Notion databases, text converted to UJO (Universal JSON Output)
- `phil/logseq` · 🗓️ planned — Read and write a Logseq graph
- `phil/chat-community` · 🗓️ planned — Link a community to a chat service: linked roles, mirrored events, announcements
- `phil/chat-interactions-bundle` · 🗓️ planned — Signed chat-service interactions: Ed25519 checks, commands, deferred replies

</details>

<details>
<summary><b>UX &amp; interface</b> — ✅ 3 · 🧪 5 · 🗓️ 8</summary>

- [`phil/ux-css`](https://github.com/parler-haut-interagir-librement/ux-css) · ✅ released ([Packagist](https://packagist.org/packages/phil/ux-css)) — phil-ux, the CSS framework: OKLCH tokens, light and dark themes, classless elements, layout utilities
- [`phil/ux-kit`](https://github.com/parler-haut-interagir-librement/ux-kit) · ✅ released ([Packagist](https://packagist.org/packages/phil/ux-kit)) — The PHIL UX kit for the Symfony UX Toolkit: the recipes of the Shadcn kit and its own, styled with phil-ux
- [`phil/menu-bundle`](https://github.com/parler-haut-interagir-librement/menu-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/menu-bundle)) — Navigation menus and breadcrumbs, with the current page marked
- `phil/ux-bundle` · 🧪 37% — PHIL UX components, being rewritten as a kit for the Symfony UX Toolkit and the phil-ux CSS
- `phil/ux-kit-shadcn` · 🧪 88% — Tailwind versions, in the Shadcn style, of the recipes PHIL UX adds
- `phil/forms-bundle` · 🧪 90% — Forms defined in the database, entries kept only as long as needed
- `phil/data-table-bundle` · 🧪 88% — Live Component tables: sorting, filters, inline editing, stacked on mobile
- `phil/forms-autosave` · 🧪 90% — Form input saved as you go
- `phil/forms-signature` · 🗓️ planned — A handwritten or electronic signature field
- `phil/pwa-bundle` · 🗓️ planned — Installable, offline-readable sites: manifest, service worker, full screen
- `phil/theme-builder` · 🗓️ planned — Build a theme from PHIL UX tokens
- `phil/page-builder` · 🗓️ planned — Pages composed of blocks, without code
- `phil/landing-pages` · 🗓️ planned — Landing pages composed in the administration
- `phil/menu-builder-ui` · 🗓️ planned — Edit menus with the mouse
- `phil/announcement-bar` · 🗓️ planned — A site announcement bar
- `phil/ux-translate` · 🗓️ planned — The browser's Translator API in Stimulus and Twig, on demand, never sent to a service

</details>


## Get involved

- 💬 Questions and ideas: [Discussions](https://github.com/orgs/parler-haut-interagir-librement/discussions)
- 🐛 Bugs and feature requests: an issue in the repository concerned
- 🤝 [Contributing](https://github.com/parler-haut-interagir-librement/.github/blob/main/CONTRIBUTING.md) ·
  [Code of conduct](https://github.com/parler-haut-interagir-librement/.github/blob/main/CODE_OF_CONDUCT.md) ·
  [Security](https://github.com/parler-haut-interagir-librement/.github/blob/main/SECURITY.md) ·
  [Support](https://github.com/parler-haut-interagir-librement/.github/blob/main/SUPPORT.md)
- ✉️ [info@ph-il.ca](mailto:info@ph-il.ca) · 🌐 [ph-il.ca](https://ph-il.ca)

---

## Version française

**PHIL** — *Parler Haut, Interagir Librement* (*Proclaim Honestly, Interact Liberally*)

### Ce qu'est PHIL

**phil-ip** (*Internet Platform*), aussi appelée **phil-pc** (*Collaborative Platform*), est une plateforme pour bâtir
des sites collaboratifs, sur Internet et en présentiel. Nous l'avons d'abord créée pour les sites du Gnome
Archiviste — boutique et créateur de jeux du Québec — et nous publions ses modules en code ouvert, pour que vous en
profitiez aussi et y ajoutiez votre grain de sel.

PHIL, c'est trois choses :

- **Les librairies et les bundles Symfony `phil/*`** — contenu et texte, commerce, événements, communauté, vie
  privée, médias et impression, et la plomberie entre les deux. La liste complète, avec l'état de chaque paquet, est
  [plus bas](#les-paquets).
- **PHIL UX** (`phil-ux`), le système de design : un kit pour le Toolkit de Symfony UX et un cadre CSS. Son site sera
  [ux.ph-il.ca](https://ux.ph-il.ca).
- **L'outillage** qui vérifie chaque paquet : `phil/dev-tools` et les gabarits de projet.

[ph-il.ca](https://ph-il.ca) présente la plateforme et deviendra le catalogue des modules : une page par paquet,
générée de son README et de sa documentation, en anglais et en français.

Les paquets de jeu et de ludification — dés, générateurs, points, badges, quêtes et le reste — vivent à côté, chez
[Tilttek](https://github.com/TiltTek).

### Pourquoi

Boutiques, conventions, clubs, éditeurs et communautés en ligne ont sans cesse besoin des mêmes briques : un
catalogue et une caisse, un calendrier, un forum, une infolettre, une politique de confidentialité vraiment
appliquée. Nous préférons écrire chaque brique une fois, avec soin et à découvert, plutôt que recoller les mêmes
morceaux sur chaque site. Et nous préférons vous dire franchement où en est chacune : **aujourd'hui, 85 paquets
sont publiés ; les autres sont en écriture ou prévus, et suivent par petits groupes quotidiens.**

### Principes

- **Du code original.** Le code tiers n'entre dans un paquet PHIL que comme dépendance Composer déclarée. D'autres
  projets sont étudiés pour leurs idées.
- **MIT, en entier.** Chaque paquet porte son propre fichier de licence.
- **Un plancher moderne :** PHP 8.5+ et Symfony 8.2+.
- **Les versions suivantes, tôt.** Le PHP et le Symfony suivants entrent dans notre matrice de tests dès leur
  première version candidate (aujourd'hui : PHP 8.6). Nos contraintes vous laissent les installer avant que nous les
  exigions ; une dépréciation du PHP suivant fait échouer les tests. Le plancher monte quand la version suivante
  atteint sa troisième version corrective (x.y.3) — toujours dans une nouvelle version de nos paquets, jamais dans une
  version existante.
- **Des barrières de qualité strictes.** PHPStan au niveau maximal avec les règles strictes, sur chaque PHP de la
  matrice ; PHP-CS-Fixer aux règles de Symfony et `declare(strict_types=1)` partout ; Rector ; Deptrac et Arkitect
  pour l'architecture ; PHPUnit qui échoue à la moindre dépréciation, notice ou avertissement ; et chaque paquet
  installé et testé seul.
- **Un score de mutation de 100 %.** Infection doit tuer chaque mutant. Un mutant qui survit est un test manquant, ou
  du code que rien n'atteint ; la barre ne baisse jamais, et un paquet ne sort pas d'incubation en dessous.
- **Accessible d'office.** Clavier et lecteur d'écran, focus visible, mouvement réduit, contraste suffisant, et jamais
  une information portée par la seule couleur.
- **Toutes les langues, pas seulement les nôtres.** Les données viennent du CLDR et d'autres références ouvertes ;
  adresses, numéros de téléphone, règles du pluriel et typographie suivent chaque pays et chaque langue. Rien n'est
  limité aux langues de nos propres sites.
- **La vie privée dès la conception.** Pensé pour la Loi 25 du Québec et le RGPD : aucun pistage, aucun traceur tiers,
  une analytique en agrégats seulement, des adresses IP anonymisées, des champs personnels déclarés pour être exportés
  et effacés, et des messages en file qui portent des identifiants, jamais de données personnelles.
- **Extensible à dessein.** Des points d'extension documentés (services tagués et interfaces publiques), pour que les
  add-ons se branchent sans correctif ; ils sont déclarés stables à partir de 1.0.
- **Documenté en anglais.** Chaque paquet a son README et un dossier `doc/` complet.

### L'organisation des paquets

- **Une librairie PHP pure et son bundle Symfony.** `phil/money` marche dans tout projet PHP ; `phil/money-bundle` le
  branche dans les formulaires, la validation, Twig et Doctrine. Certains paquets n'existent qu'en bundle. Les
  librairies s'appuient sur les composants Symfony existants plutôt que de les réinventer.
- **L'incubation.** Les nouveaux paquets s'écrivent dans un monodépôt privé, `phil-prerelease`, l'incubateur
  permanent, où un changement qui touche plusieurs paquets se fait et se teste d'un coup.
- **La sortie.** Un paquet fini passe au monodépôt public
  [`parler-haut-interagir-librement/phil`](https://github.com/parler-haut-interagir-librement/phil), où il est
  développé ensuite, et d'où chaque paquet est scindé dans son propre dépôt en lecture seule et publié sur
  [Packagist](https://packagist.org).
- **Les versions.** Versionnage sémantique ; chaque paquet tient un fichier [Keep a Changelog](https://keepachangelog.com).

### PHIL UX

PHIL UX passe par le [Toolkit de Symfony UX](https://ux.symfony.com/toolkit) : pas d'installateur maison, seulement
`ux:install`.

| Dépôt | Ce qu'il contient | État |
|---|---|---|
| [ux-kit](https://github.com/parler-haut-interagir-librement/ux-kit) | Le kit PHIL UX : les mêmes recettes que le kit Shadcn du Toolkit — noms, props, blocs Twig, contrôleurs Stimulus — avec leur propre HTML et leur propre CSS, habillés par phil-ux. `php bin/console ux:install <recette> --kit=github.com/parler-haut-interagir-librement/ux-kit` | 🧪 incubation, ~10 % |
| [ux-css](https://github.com/parler-haut-interagir-librement/ux-css) | phil-ux, le cadre CSS : du vrai CSS, presque sans classe, aux jetons `--phil-*`, clair et sombre, avec les classes d'état `isX`/`hasX` ; pour AssetMapper (Composer) et npm | 🧪 incubation, ~30 % |
| [ux-kit-shadcn](https://github.com/parler-haut-interagir-librement/ux-kit-shadcn) | Les versions Tailwind, à la façon de Shadcn, des recettes que PHIL UX ajoute | 🧪 incubation, ~25 % |

Déjà disponibles, dans l'incubateur :

- **Logo** — un logo avec sa source WebP et son texte de remplacement, lié à l'accueil s'il a un `href`, un par thème
  et par langue.
- **AnimatedHeadline** — un titre dont les mots se relaient, par un contrôleur Stimulus ; sous
  `prefers-reduced-motion`, rien ne bouge.
- **Illustration** — une figure qui montre une image choisie au serveur parmi des candidates, au hasard ou par graine.
- **ComingSoon**, un bloc — une page « bientôt » bâtie des trois recettes ci-dessus.
- **Les utilitaires de mise en page** de phil-ux — `isStack`, `isCluster`, `isCenter`, `isNarrow`, `isSplit`, `isCover`,
  `isBleed` et leurs semblables, aux écarts tirés des jetons.
- **Les thèmes** de phil-ux — clair et sombre, sur une palette OKLCH dont les paires sont vérifiées par une règle de
  contraste.

Les composants du kit Shadcn suivent, à commencer par ceux dont nos bundles ont besoin.

Comme les recettes reprennent les noms et les props du kit Shadcn, chaque bundle PHIL se rend avec PHIL UX **ou** avec
le kit Shadcn : gardez Tailwind si vous l'aimez.

### L'outillage

- **`phil/dev-tools`** — les configurations partagées de PHP-CS-Fixer, PHPStan, Rector, Deptrac, Arkitect, Infection,
  PHPUnit et PHPBench ; les scripts Composer qui les lancent ; les vérifications de la documentation ; de vrais
  serveurs MySQL, PostgreSQL et Gotenberg en Docker pour les tests d'intégration ; des enregistrements HTTP rejouables ;
  la matrice des versions de PHP et de Symfony ; et la base d'un nouveau paquet. Publié sous licence MIT :
  [dev-tools](https://github.com/parler-haut-interagir-librement/dev-tools).
- **Les gabarits de projet** — [MicroSymfony](https://github.com/parler-haut-interagir-librement/MicroSymfony)
  (issu de `strangebuzz/MicroSymfony`) et [WebSymfony](https://github.com/parler-haut-interagir-librement/WebSymfony).

### Les paquets

✅ **publié** · 🧪 **écrit, en incubation** (avancement approximatif) · 🗓️ **prévu**

**418 paquets :** 85 publiés, 90 en incubation, 243 prévus. Les pourcentages sont des estimations
tirées de notre dernier rapport d'avancement (11 novembre 2026). Les paquets publiés sont développés dans le monodépôt
public [`phil`](https://github.com/parler-haut-interagir-librement/phil), scindés chacun dans son propre dépôt en
lecture seule et publiés sur Packagist ; `phil/enums` poursuit
[`ph-il/enums`](https://packagist.org/packages/ph-il/enums). **La vitrine se poursuit par petits groupes
quotidiens** de deux à quatre paquets, les dépendances d'abord.

<details>
<summary><b>Données et infrastructure</b> — ✅ 19 · 🧪 16 · 🗓️ 16</summary>

- [`phil/enums`](https://github.com/parler-haut-interagir-librement/enums) · ✅ publié ([Packagist](https://packagist.org/packages/phil/enums)) — Traits et attributs pour lister, comparer, décrire et regrouper les enums PHP (anciennement `ph-il/enums`)
- [`phil/enums-bundle`](https://github.com/parler-haut-interagir-librement/enums-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/enums-bundle)) — Les enums dans les formulaires, traductions, Twig, la validation, Doctrine et les contrats d'API de Symfony
- [`phil/resource`](https://github.com/parler-haut-interagir-librement/resource) · ✅ publié ([Packagist](https://packagist.org/packages/phil/resource)) — Désigner n'importe quel enregistrement par sa sorte et son identifiant, comme `page:42`
- [`phil/ddd-bundle`](https://github.com/parler-haut-interagir-librement/ddd-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ddd-bundle)) — Types de domaine communs : identifiants, événements, erreurs, bus de commandes et de requêtes
- [`phil/slug`](https://github.com/parler-haut-interagir-librement/slug) · ✅ publié ([Packagist](https://packagist.org/packages/phil/slug)) — Des slugs d'URL tirés des titres et des noms, en type qui n'accepte rien d'autre
- [`phil/slug-bundle`](https://github.com/parler-haut-interagir-librement/slug-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/slug-bundle)) — Des générateurs de slugs nommés en configuration, injectés et utilisables dans Twig
- [`phil/url`](https://github.com/parler-haut-interagir-librement/url) · ✅ publié ([Packagist](https://packagist.org/packages/phil/url)) — Des adresses Web en valeurs normalisées, leur sorte détectée : Mastodon, YouTube, un site
- [`phil/url-bundle`](https://github.com/parler-haut-interagir-librement/url-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/url-bundle)) — Des champs de lien qui détectent leur sorte, une contrainte, un type de colonne et des filtres Twig
- [`phil/references-bundle`](https://github.com/parler-haut-interagir-librement/references-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/references-bundle)) — Savoir où chaque ressource est employée, et refuser d'effacer celle qui sert encore
- [`phil/trash-bundle`](https://github.com/parler-haut-interagir-librement/trash-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/trash-bundle)) — Une corbeille pour les ressources effacées : les restaurer, ou les purger après un délai
- [`phil/recurrence`](https://github.com/parler-haut-interagir-librement/recurrence) · ✅ publié ([Packagist](https://packagist.org/packages/phil/recurrence)) — Des dates répétées par les règles RFC 5545 : lire, vérifier, écrire, énumérer les occurrences
- [`phil/recurrence-bundle`](https://github.com/parler-haut-interagir-librement/recurrence-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/recurrence-bundle)) — Un formulaire d'événements répétés, une colonne pour la règle, et la règle en toutes lettres
- [`phil/feature-flags-bundle`](https://github.com/parler-haut-interagir-librement/feature-flags-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/feature-flags-bundle)) — Couper une fonction sans déploiement, mener un test A/B, cesser d'appeler un service en panne
- [`phil/http-cache-tags-bundle`](https://github.com/parler-haut-interagir-librement/http-cache-tags-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/http-cache-tags-bundle)) — Mettre des pages entières en cache Varnish ou CDN, purger exactement ce qu'une modification change
- [`phil/standard-webhooks`](https://github.com/parler-haut-interagir-librement/standard-webhooks) · ✅ publié ([Packagist](https://packagist.org/packages/phil/standard-webhooks)) — Signer et vérifier des webhooks selon la spécification Standard Webhooks
- [`phil/standard-webhooks-bundle`](https://github.com/parler-haut-interagir-librement/standard-webhooks-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/standard-webhooks-bundle)) — Les livraisons de webhooks vérifiées en arguments de contrôleur, et l'envoi de webhooks signés
- [`phil/circuit-breaker`](https://github.com/parler-haut-interagir-librement/circuit-breaker) · ✅ publié ([Packagist](https://packagist.org/packages/phil/circuit-breaker)) — Un seul disjoncteur pour les clients HTTP et les drapeaux de fonctions
- [`phil/circuit-breaker-bundle`](https://github.com/parler-haut-interagir-librement/circuit-breaker-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/circuit-breaker-bundle)) — Le disjoncteur branché dans les clients HTTP et les drapeaux de fonctions de Symfony
- [`phil/console-bundle`](https://github.com/parler-haut-interagir-librement/console-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/console-bundle)) — Garde-fous de console par environnement et sortie horodatée
- `phil/doctrine-behaviours` · 🧪 95 % — Horodatage, auteur, suppression douce et arbres pour les entités Doctrine, chacun sur option
- `phil/doctrine-behaviours-bundle` · 🧪 93 % — Les comportements d'entité activés par configuration dans Symfony
- `phil/almanac` · 🧪 85 % — Pâques, phases de la Lune, saisons et dates en toutes lettres, pour toute année
- `phil/almanac-bundle` · 🧪 90 % — Fériés et dates calculées en configuration, modifiables, montrés dans Twig
- `phil/scheduled-transitions-bundle` · 🧪 96 % — Publier et retirer à heure fixe, sans personne en ligne
- `phil/tenancy-bundle` · 🧪 72 % — Le locataire où agit un compte, changé à l'instant et appliqué à chaque requête
- `phil/usage-meter` · 🧪 90 % — Mesurer ce que chacun a consommé et refuser une action au-delà de son quota
- `phil/api-contract` · 🧪 72 % — Détails de problème, signaux de dépréciation et clés d'idempotence pour les API HTTP
- `phil/api-contract-bundle` · 🧪 93 % — Détails de problème, requêtes idempotentes rejouées et avis de dépréciation dans Symfony
- `phil/usage-meter-bundle` · 🧪 93 % — Compteurs d'usage stockés par DBAL, limiteurs de débit et commandes de purge
- `phil/idempotency` · 🧪 92 % — Clés d'idempotence pour les API, Messenger, les webhooks de paiement et les doubles envois
- `phil/encrypted-fields` · 🧪 93 % — Colonnes Doctrine chiffrées par libsodium, index aveugles, rotation des clés
- `phil/encrypted-fields-bundle` · 🧪 86 % — Les champs chiffrés configurés dans Symfony, clés dans les secrets ou un KMS
- `phil/rate-limit-bundle` · 🧪 97 % — Limites de débit déclarées par attribut sur les routes, formulaires et API
- `phil/api-keys-bundle` · 🧪 88 % — Jetons d'accès personnels pour une API publique : portées, expiration, révocation, quotas
- `phil/rate-limit` · 🧪 95 % — La garde de production des limites de débit de Symfony : la construction échoue si un limiteur compte par serveur
- `phil/spreadsheet` · 🗓️ prévu — Lire et écrire XLSX, ODS et CSV
- `phil/import-wizard` · 🗓️ prévu — L'import guidé d'un fichier, colonne par colonne
- `phil/json-canvas` · 🗓️ prévu — Lire et écrire le format ouvert JSON Canvas
- `phil/open-data` · 🗓️ prévu — Publier les données ouvertes d'un site
- `phil/number-words` · 🗓️ prévu — Les nombres en toutes lettres, dans toutes les langues
- `phil/natural-dates` · 🗓️ prévu — Une date écrite en mots (« jeudi prochain 19 h ») comprise dans chaque langue
- `phil/timezone-display` · 🗓️ prévu — Une heure affichée dans le fuseau du visiteur
- `phil/safe-http` · 🗓️ prévu — Un client HTTP protégé pour les paquets qui lisent d'autres sites : protection contre le SSRF, limites de taille et de durée
- `phil/rules` · 🗓️ prévu — Des conditions fixes et composables évaluées sans code, lues par les prix, les promotions et l'accès
- `phil/rules-bundle` · 🗓️ prévu — Des règles nommées dans Symfony, leurs conditions en services étiquetés
- `phil/measurement` · 🗓️ prévu — Les unités de mesure et leur conversion, par canal de vente
- `phil/measurement-bundle` · 🗓️ prévu — Les mesures dans les formulaires, Doctrine et Twig de Symfony
- `phil/custom-fields` · 🗓️ prévu — Les champs personnalisés : types, trousses appliquées par catégorie, champs protégés et à formule
- `phil/custom-fields-bundle` · 🗓️ prévu — Les champs personnalisés dans Symfony : formulaires générés et filtres de listes
- `phil/field-layout` · 🗓️ prévu — La disposition déclarée des formulaires d'édition : onglets, largeurs, conditions de visibilité
- `phil/field-layout-bundle` · 🗓️ prévu — Les dispositions de champs rendues par un thème de formulaire Symfony

</details>

<details>
<summary><b>Contenu et texte</b> — ✅ 17 · 🧪 5 · 🗓️ 28</summary>

- [`phil/ujo`](https://github.com/parler-haut-interagir-librement/ujo) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ujo)) — Des documents UJO (Universal JSON Output) lus strictement, vérifiés bloc par bloc, rendus en HTML sûr
- [`phil/ujo-bundle`](https://github.com/parler-haut-interagir-librement/ujo-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ujo-bundle)) — Les documents UJO (Universal JSON Output) dans Doctrine, les formulaires et Twig
- [`phil/markup`](https://github.com/parler-haut-interagir-librement/markup) · ✅ publié ([Packagist](https://packagist.org/packages/phil/markup)) — Markdown, BBCode, MediaWiki, DokuWiki, Creole, HTML ou texte brut rendus en HTML sûr
- [`phil/markup-bundle`](https://github.com/parler-haut-interagir-librement/markup-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/markup-bundle)) — Les formats de balisage rendus sans danger dans Twig et convertis en UJO (Universal JSON Output), en services Symfony
- [`phil/block-editor-bundle`](https://github.com/parler-haut-interagir-librement/block-editor-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/block-editor-bundle)) — Un éditeur par blocs pour les formulaires Symfony, en Stimulus, qui écrit de l'UJO (Universal JSON Output) vérifié au serveur
- [`phil/edit-lock-bundle`](https://github.com/parler-haut-interagir-librement/edit-lock-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/edit-lock-bundle)) — Un seul rédacteur par bloc : baux d'édition, présence et enregistrements poussés par Mercure
- [`phil/text-diff`](https://github.com/parler-haut-interagir-librement/text-diff) · ✅ publié ([Packagist](https://packagist.org/packages/phil/text-diff)) — Ce qui a changé entre deux textes, mot à mot, paragraphe par paragraphe ou bloc par bloc
- [`phil/highlight`](https://github.com/parler-haut-interagir-librement/highlight) · ✅ publié ([Packagist](https://packagist.org/packages/phil/highlight)) — Du code en 24 langages coloré au serveur, en HTML simple que toute feuille de style habille
- [`phil/css-sanitizer`](https://github.com/parler-haut-interagir-librement/css-sanitizer) · ✅ publié ([Packagist](https://packagist.org/packages/phil/css-sanitizer)) — Laisser les gens habiller leurs pages sans que leur CSS exécute du code, charge ce qu'il ne doit pas ou sorte de son cadre
- [`phil/taxonomy-bundle`](https://github.com/parler-haut-interagir-librement/taxonomy-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/taxonomy-bundle)) — Étiquettes et arbre de catégories traduit pour toute ressource, avec leurs types de formulaire
- [`phil/svg-sanitizer`](https://github.com/parler-haut-interagir-librement/svg-sanitizer) · ✅ publié ([Packagist](https://packagist.org/packages/phil/svg-sanitizer)) — Purifier le SVG : liste blanche d'éléments et d'attributs, ni script ni référence externe
- [`phil/svg-chart`](https://github.com/parler-haut-interagir-librement/svg-chart) · ✅ publié ([Packagist](https://packagist.org/packages/phil/svg-chart)) — Des graphiques dessinés en SVG au serveur, d'après la configuration qu'écrit déjà un éditeur de graphiques
- [`phil/text-diff-bundle`](https://github.com/parler-haut-interagir-librement/text-diff-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/text-diff-bundle)) — La comparaison de textes dans Twig et Stimulus
- [`phil/highlight-bundle`](https://github.com/parler-haut-interagir-librement/highlight-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/highlight-bundle)) — La coloration branchée dans le rendu UJO (Universal JSON Output) et dans Twig, avec un thème
- [`phil/footnotes-sidenotes`](https://github.com/parler-haut-interagir-librement/footnotes-sidenotes) · ✅ publié ([Packagist](https://packagist.org/packages/phil/footnotes-sidenotes)) — Notes de bas de page et notes en marge
- [`phil/content-warnings`](https://github.com/parler-haut-interagir-librement/content-warnings) · ✅ publié ([Packagist](https://packagist.org/packages/phil/content-warnings)) — Avertissements de contenu pour jeux, livres, articles et événements, sur une liste de base traduite
- [`phil/content-warnings-bundle`](https://github.com/parler-haut-interagir-librement/content-warnings-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/content-warnings-bundle)) — Les avertissements de contenu dans les formulaires, les pages et les filtres
- `phil/content-bundle` · 🧪 88 % — Pages et articles gardés par langue, étape et version, publiés du brouillon à la mise en ligne
- `phil/comments-bundle` · 🧪 85 % — Commentaires et suggestions ancrés à des passages, qui suivent le texte quand il change
- `phil/latex-mathml` · 🧪 80 % — Des formules LaTeX converties, au serveur, en MathML que les navigateurs dessinent
- `phil/svg-blocks` · 🧪 90 % — Les formules, schémas, graphiques et codes QR des documents par blocs, dessinés une fois au serveur
- `phil/svg-blocks-bundle` · 🧪 85 % — Les dessins des blocs faits à l'enregistrement dans Symfony, Mermaid dans un conteneur
- `phil/wiki-bundle` · 🗓️ prévu — Un wiki collaboratif : pages, révisions comparées, liens `[[ ]]`, verrous par bloc
- `phil/faq-bundle` · 🗓️ prévu — Les questions fréquentes par section, cherchables, en données structurées
- `phil/glossary-bundle` · 🗓️ prévu — Un glossaire dont les termes se lient seuls dans les textes
- `phil/timeline-bundle` · 🗓️ prévu — Des lignes du temps de contenus datés
- `phil/series-bundle` · 🗓️ prévu — Les séries de contenus
- `phil/citations` · 🗓️ prévu — Citations et bibliographie dans les styles courants
- `phil/credits` · 🗓️ prévu — La page des crédits d'une œuvre : contributeurs, rôles, ordre
- `phil/content-templates` · 🗓️ prévu — Les gabarits d'un nouveau contenu
- `phil/content-queries` · 🗓️ prévu — Des listes de contenus définies par une requête dans l'administration
- `phil/curated-lists` · 🗓️ prévu — Des listes de contenus choisies et commentées
- `phil/related-content` · 🗓️ prévu — Les contenus voisins et les produits voisins
- `phil/content-expiry` · 🗓️ prévu — Un contenu qui signale son âge ou expire à une date
- `phil/content-transfer` · 🗓️ prévu — Transférer un contenu d'un site à l'autre avec ses médias et ses liens
- `phil/editorial-calendar` · 🗓️ prévu — Le calendrier éditorial des publications
- `phil/page-protection` · 🗓️ prévu — Des pages verrouillées ou réservées à des rôles
- `phil/reading-progress` · 🗓️ prévu — La progression de lecture d'un long contenu
- `phil/dictionary` · 🗓️ prévu — Un dictionnaire et un thésaurus derrière un port
- `phil/release-notes` · 🗓️ prévu — Les notes de version annoncées
- `phil/publishing` · 🗓️ prévu — L'événement PagePublished et son contrat, pour le cycle de vie du contenu
- `phil/story-graph` · 🗓️ prévu — Un graphe narratif à embranchements pour les leçons à embranchements et les livres-jeux
- `phil/content-access` · 🗓️ prévu — L'accès au contenu par droits : public, membres, paliers, accès anticipé, durées fixes ou glissantes
- `phil/content-access-bundle` · 🗓️ prévu — L'accès au contenu dans Symfony : voters, vérifications Twig et administration des règles
- `phil/content-archive` · 🗓️ prévu — Une archive de contenu portable : UJO (Universal JSON Output) fidèle, Markdown lisible, médias
- `phil/share-links` · 🗓️ prévu — Des liens privés nommés vers du contenu non publié, avec compteur de visites et révocation
- `phil/share-links-bundle` · 🗓️ prévu — Les liens de partage dans Symfony : routes, aperçu en bac à sable, révocation
- `phil/suggested-edits` · 🗓️ prévu — Des modifications suggérées à un message ou à tout un contenu
- `phil/live-preview-bundle` · 🗓️ prévu — L'aperçu en direct sur plusieurs cibles et tailles d'appareil, remplacé sur place par Turbo
- `phil/form-logic` · 🗓️ prévu — La logique conditionnelle des formulaires, évaluée de la même façon en PHP et en Stimulus, le serveur faisant foi

</details>

<details>
<summary><b>Langues, traduction et typographie</b> — ✅ 2 · 🧪 3 · 🗓️ 2</summary>

- [`phil/typography`](https://github.com/parler-haut-interagir-librement/typography) · ✅ publié ([Packagist](https://packagist.org/packages/phil/typography)) — Vrais guillemets, tirets, espaces françaises et césure dans votre HTML, dans toutes les langues
- [`phil/typography-bundle`](https://github.com/parler-haut-interagir-librement/typography-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/typography-bundle)) — La typographie partout où une application Symfony écrit du texte
- `phil/translation-bundle` · 🧪 83 % — Un écran de traduction : segments qui survivent aux modifications, mémoire et glossaire qui vérifie
- `phil/translation-memory` · 🧪 87 % — Traduction par segments qui réutilise l'acquis et garde les termes constants
- `phil/locale-dimensions` · 🧪 95 % — Les locales, les versions et les chaînes de repli déclarées, en simples objets-valeurs
- `phil/machine-translation` · 🗓️ prévu — Des traductions proposées par la machine, toujours relues
- `phil/translation-ui` · 🗓️ prévu — L'interface de traduction des contenus et des messages d'un site

</details>

<details>
<summary><b>Médias, documents et impression</b> — ✅ 5 · 🧪 11 · 🗓️ 18</summary>

- [`phil/fonts`](https://github.com/parler-haut-interagir-librement/fonts) · ✅ publié ([Packagist](https://packagist.org/packages/phil/fonts)) — Ce qu'un fichier de police dit de lui-même — noms, graisse, licence d'intégration — et sa règle `@font-face`
- [`phil/print-preflight`](https://github.com/parler-haut-interagir-librement/print-preflight) · ✅ publié ([Packagist](https://packagist.org/packages/phil/print-preflight)) — Repérer ce qu'un imprimeur refuserait avant que le fichier lui parvienne
- [`phil/print-compositor`](https://github.com/parler-haut-interagir-librement/print-compositor) · ✅ publié ([Packagist](https://packagist.org/packages/phil/print-compositor)) — Maquettes de vêtements et fichiers d'impression, une couche par encre
- [`phil/qr-code`](https://github.com/parler-haut-interagir-librement/qr-code) · ✅ publié ([Packagist](https://packagist.org/packages/phil/qr-code)) — Des codes QR en PHP pur, Reed-Solomon compris, en SVG et PNG
- [`phil/qr-code-bundle`](https://github.com/parler-haut-interagir-librement/qr-code-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/qr-code-bundle)) — Les codes QR dans Twig, les routes et les contenus typés (URL, vCard, Wi-Fi, iCalendar)
- `phil/media-bundle` · 🧪 90 % — Fichiers et images téléversés, décrits, versionnés et servis à des URL signées
- `phil/document-import` · 🧪 73 % — Documents de traitement de texte, Markdown et HTML convertis en UJO (Universal JSON Output), avec le relevé de ce qui n'a pas passé
- `phil/epub` · 🧪 85 % — Des livres EPUB 3 tirés de votre HTML, valides pour EPUBCheck et lisibles par les aides techniques
- `phil/paged-media` · 🧪 70 % — Des PDF depuis PHP, avec de vraies polices et des moteurs HTML/CSS paginés
- `phil/paged-media-bundle` · 🧪 94 % — Les PDF dans Symfony, par un écrivain natif ou Gotenberg, par un seul service, tout de suite ou par Messenger
- `phil/document-import-bundle` · 🧪 90 % — L'import de documents branché dans la médiathèque
- `phil/fonts-bundle` · 🧪 95 % — Les polices configurées pour le PDF et les médias
- `phil/epub-bundle` · 🧪 95 % — La génération d'EPUB dans Symfony
- `phil/print-preflight-bundle` · 🧪 90 % — Le contrôle prépresse branché dans la génération de PDF
- `phil/paged-media-weasyprint` · 🧪 92 % — Le moteur WeasyPrint des médias paginés : HTML et CSS mis en page en PDF, sans réseau
- `phil/creation-disclosure` · 🧪 90 % — La façon dont une œuvre a été faite, déclarée partie par partie dans le vocabulaire Digital Source Type de l'IPTC
- `phil/gallery-bundle` · 🗓️ prévu — Des galeries de photos par album et par événement
- `phil/video-bundle` · 🗓️ prévu — Des vidéos hébergées ou liées, sous-titres et chapitres
- `phil/podcast-bundle` · 🗓️ prévu — Un balado : épisodes, flux Podcasting 2.0, chapitres, transcriptions
- `phil/live-stream-bundle` · 🗓️ prévu — La diffusion en direct annoncée, intégrée et archivée
- `phil/transcription` · 🗓️ prévu — La transcription d'un audio ou d'une vidéo derrière un port
- `phil/image-editor` · 🗓️ prévu — Un éditeur d'image : recadrage, rotation, filtres, annotations
- `phil/avatar` · 🗓️ prévu — Des avatars générés
- `phil/document-preview` · 🗓️ prévu — L'aperçu d'un document
- `phil/pdf-watermark` · 🗓️ prévu — Le filigrane personnalisé d'un PDF vendu
- `phil/braille-export` · 🗓️ prévu — L'export en braille abrégé ou intégral d'un document
- `phil/demo-videos` · 🗓️ prévu — Les vidéos de démonstration d'un produit ou d'un paquet
- `phil/audio` · 🗓️ prévu — L'audio : transcodage facultatif, forme d'onde, extraits et lecteur accessible qui fonctionne sans JavaScript
- `phil/audio-bundle` · 🗓️ prévu — L'audio dans Symfony : composant de lecteur, téléversements et tâches de transcodage
- `phil/music-bundle` · 🗓️ prévu — La musique d'un artiste ou d'un groupe : albums, pistes, ventes et écoute sans achat
- `phil/timed-text` · 🗓️ prévu — Le texte minuté lu et écrit : WebVTT, SRT, chapitres et transcriptions Podcasting 2.0
- `phil/braille-export-liblouis` · 🗓️ prévu — L'adaptateur de l'export braille qui appelle liblouis
- `phil/slides` · 🗓️ prévu — Des diapositives lues dans un document UJO, avec mode présentateur, notes, minuterie et export PDF
- `phil/diagram` · 🗓️ prévu — Des diagrammes écrits en texte et rendus en SVG au serveur, avec une description textuelle

</details>

<details>
<summary><b>Recherche, référencement et Web ouvert</b> — ✅ 5 · 🧪 5 · 🗓️ 14</summary>

- [`phil/sitemap`](https://github.com/parler-haut-interagir-librement/sitemap) · ✅ publié ([Packagist](https://packagist.org/packages/phil/sitemap)) — Des plans de site XML bâtis de pages vérifiées, coupés aux limites du protocole
- [`phil/sitemap-bundle`](https://github.com/parler-haut-interagir-librement/sitemap-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/sitemap-bundle)) — `/sitemap.xml` tiré des options de route, de fournisseurs d'URL et d'un événement
- [`phil/structured-data`](https://github.com/parler-haut-interagir-librement/structured-data) · ✅ publié ([Packagist](https://packagist.org/packages/phil/structured-data)) — Le graphe schema.org d'une page, assemblé de morceaux JSON-LD
- [`phil/redirects-bundle`](https://github.com/parler-haut-interagir-librement/redirects-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/redirects-bundle)) — Redirections 301 gérées, suivi des 404, anciens domaines
- [`phil/well-known-bundle`](https://github.com/parler-haut-interagir-librement/well-known-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/well-known-bundle)) — Les adresses `/.well-known/` : security.txt, change-password, WebFinger, nodeinfo
- `phil/search-bundle` · 🧪 70 % — La recherche plein texte dans vos ressources, tenue à jour à chaque flush de Doctrine
- `phil/search-loupe` · 🧪 90 % — Une recherche tolérante aux fautes dans des fichiers SQLite, sans serveur
- `phil/social-cards` · 🧪 89 % — Balises Open Graph et images de partage générées
- `phil/social-cards-bundle` · 🧪 90 % — Les métadonnées de partage et les cartes générées dans Symfony, avec l'aperçu des liens entrants
- `phil/structured-data-bundle` · 🧪 95 % — Le graphe schema.org d'une page dans Symfony, avec une commande qui le vérifie
- `phil/search-synonyms` · 🗓️ prévu — Les synonymes de la recherche, gérés par l'administration
- `phil/feed-bundle` · 🗓️ prévu — Flux RSS, Atom et JSON Feed de tout contenu
- `phil/indexnow` · 🗓️ prévu — Prévenir les moteurs de recherche par IndexNow
- `phil/seo-check` · 🗓️ prévu — Le contrôle de référencement à la publication : titre, description, liens, données structurées
- `phil/link-checker` · 🗓️ prévu — Trouver et signaler les liens morts
- `phil/short-link-bundle` · 🗓️ prévu — Des liens courts sur un domaine dédié, visites comptées sans pistage
- `phil/activitypub-bundle` · 🗓️ prévu — La fédération ActivityPub complète pour les membres (sur option) et les groupes
- `phil/webmention-bundle` · 🗓️ prévu — Envoyer et recevoir des Webmention
- `phil/oembed-bundle` · 🗓️ prévu — Un fournisseur oEmbed pour vos pages
- `phil/embed-bundle` · 🗓️ prévu — Des fonctions intégrables ailleurs : jeton, thème, `frame-ancestors`
- `phil/sitemap-visual` · 🗓️ prévu — Le plan du site dessiné pour les visiteurs
- `phil/search-console` · 🗓️ prévu — Les données de Google Search Console, lues pour tout site
- `phil/search-console-bundle` · 🗓️ prévu — Search Console dans Symfony : identifiants, récupérations planifiées, widgets de tableau de bord
- `phil/feed-import` · 🗓️ prévu — Des fils RSS et Atom importés comme contenu

</details>

<details>
<summary><b>Identité, accès et sécurité</b> — ✅ 7 · 🧪 4 · 🗓️ 13</summary>

- [`phil/bot-detection-bundle`](https://github.com/parler-haut-interagir-librement/bot-detection-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/bot-detection-bundle)) — Distinguer un robot d'un humain dans le navigateur, sans CAPTCHA
- [`phil/spam-protection`](https://github.com/parler-haut-interagir-librement/spam-protection) · ✅ publié ([Packagist](https://packagist.org/packages/phil/spam-protection)) — Repérer le pourriel d'un formulaire sans CAPTCHA, en PHP simple
- [`phil/spam-protection-bundle`](https://github.com/parler-haut-interagir-librement/spam-protection-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/spam-protection-bundle)) — Garder le pourriel hors des formulaires Symfony sans CAPTCHA, ni tiers, ni identifiant
- [`phil/passwords`](https://github.com/parler-haut-interagir-librement/passwords) · ✅ publié ([Packagist](https://packagist.org/packages/phil/passwords)) — Une jauge de robustesse avec ses propres dictionnaires, vérification des fuites par k-anonymat, génération
- [`phil/route-access-check`](https://github.com/parler-haut-interagir-librement/route-access-check) · ✅ publié ([Packagist](https://packagist.org/packages/phil/route-access-check)) — Faire échouer la CI quand une route n'a pas de règle d'accès
- [`phil/route-access-check-bundle`](https://github.com/parler-haut-interagir-librement/route-access-check-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/route-access-check-bundle)) — Le contrôle d'accès des routes en commande Symfony, avec baseline et mode strict
- [`phil/upload-scan`](https://github.com/parler-haut-interagir-librement/upload-scan) · ✅ publié ([Packagist](https://packagist.org/packages/phil/upload-scan)) — L'antivirus des téléversements derrière un port
- `phil/user-secrets-bundle` · 🧪 80 % — Les clés que les gens prêtent à votre application, scellées et à eux seuls
- `phil/identity-client-bundle` · 🧪 85 % — Brancher un site Symfony à un fournisseur OpenID, sur `oidc_login` de Symfony 8.2
- `phil/browser-security-bundle` · 🧪 97 % — Les protections qu'une application Symfony demande au navigateur : CSP avec nonces, HSTS, témoins signés
- `phil/upload-scan-bundle` · 🧪 88 % — L'analyse des téléversements dans Symfony : contrainte de fichier, quarantaine et nouvelles analyses
- `phil/identity-provider-bundle` · 🗓️ prévu — Un fournisseur OpenID Connect pour Symfony : passkeys, mots de passe, TOTP, step-up
- `phil/identity-provider-google` · 🗓️ prévu — La connexion Google du fournisseur d'identité, premier paquet de connexion fédérée
- `phil/organizations-bundle` · 🗓️ prévu — Organisations, rôles et invitations
- `phil/access-bundle` · 🗓️ prévu — Les droits d'accès par site
- `phil/webauthn-step-up` · 🗓️ prévu — Confirmer une action sensible par une clé d'accès
- `phil/fraud-signals` · 🗓️ prévu — Les signaux de fraude d'une commande ou d'une inscription
- `phil/trust-levels` · 🗓️ prévu — Des niveaux de confiance qui ouvrent des droits avec l'activité
- `phil/verification-marks` · 🗓️ prévu — La marque d'un compte vérifié
- `phil/invitations` · 🗓️ prévu — L'invitation d'une personne par un membre, avec ses limites
- `phil/resource-permissions` · 🗓️ prévu — Des permissions par ressource héritées le long d'un arbre, la plus précise l'emportant
- `phil/access-codes` · 🗓️ prévu — Des codes à usage unique par lots nommés, avec page d'échange et codes stockés sous forme d'empreinte
- `phil/access-links` · 🗓️ prévu — Les invitations par lien personnel : jeton, validité, rappels, réponse modifiable
- `phil/delegated-accounts` · 🗓️ prévu — Un parent gère les comptes de ses enfants mineurs, avec des vérifications d'âge

</details>

<details>
<summary><b>Vie privée, accessibilité et conformité</b> — 🧪 11 · 🗓️ 6</summary>

- `phil/privacy-bundle` · 🧪 95 % — Déclarer les champs personnels, caviarder les journaux, répondre aux demandes d'accès et d'effacement (Loi 25, RGPD)
- `phil/analytics-bundle` · 🧪 95 % — Les visites comptées en agrégats quotidiens, jamais liées à une personne
- `phil/audit-bundle` · 🧪 60 % — Un journal d'audit en ajout seul, qui montre toute altération et permet quand même d'effacer les renseignements personnels
- `phil/ip-anonymizer` · 🧪 97 % — Tronquer, hacher avec sel et généraliser les adresses IP
- `phil/legal-notices` · 🧪 96 % — Les mentions légales et la politique de confidentialité d'un site
- `phil/terms-bundle` · 🧪 94 % — Des conditions d'utilisation versionnées et leur acceptation
- `phil/accessibility-check` · 🧪 94 % — Le contrôle d'accessibilité à la publication : textes de remplacement, ordre des titres, contraste
- `phil/accessibility-statement` · 🧪 96 % — La déclaration d'accessibilité d'un site
- `phil/accessibility-statement-bundle` · 🧪 89 % — La page de déclaration d'accessibilité versionnée, en anglais et en français, avec un lien de pied de page
- `phil/legal-notices-bundle` · 🧪 90 % — Les pages d'avis légal et de politique de confidentialité, par langue, chaque version à sa propre adresse
- `phil/indexing-consent` · 🧪 93 % — La portée d'une fiche publique décidée par la personne qu'elle concerne : listée, non indexée ou non listée
- `phil/accessibility-info` · 🗓️ prévu — Les renseignements d'accessibilité d'un lieu ou d'un événement
- `phil/easy-read` · 🗓️ prévu — La version en langage simplifié d'un contenu, et sa vérification
- `phil/age-gate` · 🗓️ prévu — La vérification d'âge déclarative d'un contenu ou d'une annonce
- `phil/heatmaps` · 🗓️ prévu — Des cartes de chaleur agrégées, sans identifiant
- `phil/guardian-consent` · 🗓️ prévu — Tranches d'âge et consentement parental des mineurs de moins de 14 ans, comme l'exige la loi québécoise
- `phil/account-lifecycle` · 🗓️ prévu — Les comptes inactifs avertis, désactivés, puis supprimés ou anonymisés

</details>

<details>
<summary><b>Communauté</b> — ✅ 2 · 🧪 4 · 🗓️ 41</summary>

- [`phil/poll`](https://github.com/parler-haut-interagir-librement/poll) · ✅ publié ([Packagist](https://packagist.org/packages/phil/poll)) — Un moteur de vote : des bulletins vérifiés selon les règles de leur scrutin, comptés en classements
- [`phil/listings`](https://github.com/parler-haut-interagir-librement/listings) · ✅ publié ([Packagist](https://packagist.org/packages/phil/listings)) — Le noyau des annonces : critères, expiration, réponses, modération
- `phil/reactions-bundle` · 🧪 86 % — Les réactions à un contenu, une par membre, liste choisie par site
- `phil/mentions-bundle` · 🧪 88 % — Les @mentions dans un texte, et leur notification
- `phil/poll-bundle` · 🧪 85 % — Le moteur de vote : choix unique, multiple ou classé
- `phil/onboarding-bundle` · 🧪 90 % — L'accueil d'un nouveau membre : étapes, visite guidée, liste à cocher
- `phil/forum-bundle` · 🗓️ prévu — Des forums par section, leur clavardage, le signalement et la modération par section
- `phil/moderation-bundle` · 🗓️ prévu — Une seule file de signalements pour forums, commentaires, réactions, annonces et messages
- `phil/follow-bundle` · 🗓️ prévu — Suivre un contenu, un fil, une fiche ou un membre
- `phil/conversation-bundle` · 🗓️ prévu — Les messages privés à deux ou en groupe, chiffrés au repos
- `phil/groups-bundle` · 🗓️ prévu — Des groupes de membres
- `phil/profiles-bundle` · 🗓️ prévu — La page publique d'un membre : ce qu'il y montre, et à qui
- `phil/reviews-bundle` · 🗓️ prévu — Avis et notes modérés sur un produit, un jeu ou un lieu
- `phil/survey-bundle` · 🗓️ prévu — Des questionnaires à sections et à logique conditionnelle
- `phil/ideas-bundle` · 🗓️ prévu — Une boîte à idées avec statuts et votes
- `phil/qa-bundle` · 🗓️ prévu — Des questions et leurs réponses, la meilleure acceptée
- `phil/code-of-conduct` · 🗓️ prévu — Un code de conduite, son acceptation et ses signalements
- `phil/bookmarks-bundle` · 🗓️ prévu — Les signets d'un membre, rangés en listes
- `phil/user-lists` · 🗓️ prévu — Les listes de membres qu'un membre tient
- `phil/classifieds-bundle` · 🗓️ prévu — Des petites annonces entre membres, sans paiement
- `phil/job-board-bundle` · 🗓️ prévu — Les offres d'emploi et de contrat d'une communauté
- `phil/matchmaking-bundle` · 🗓️ prévu — Trouver des partenaires : critères, lieu approximatif ou en ligne, sécurité d'abord
- `phil/tasks-bundle` · 🗓️ prévu — Des tâches et des tableaux kanban d'équipe
- `phil/roadmap-bundle` · 🗓️ prévu — Une feuille de route publique et ses votes
- `phil/collab-whiteboard` · 🗓️ prévu — Un tableau blanc partagé en temps réel
- `phil/mind-map` · 🗓️ prévu — Une carte mentale partagée
- `phil/family-tree` · 🗓️ prévu — Un arbre généalogique
- `phil/secret-santa` · 🗓️ prévu — L'échange de cadeaux tiré au sort
- `phil/expense-split` · 🗓️ prévu — Le partage des dépenses d'un groupe
- `phil/ownership-transfer` · 🗓️ prévu — Transférer la propriété d'un contenu ou d'un groupe à un autre membre
- `phil/membership-bundle` · 🗓️ prévu — L'adhésion à une organisation : cotisation, carte de membre, renouvellement
- `phil/assembly-bundle` · 🗓️ prévu — Les assemblées : convocation, propositions, votes, procès-verbal
- `phil/budget-transparency` · 🗓️ prévu — Le budget d'une organisation publié et expliqué
- `phil/sponsors-bundle` · 🗓️ prévu — Les commanditaires et leurs niveaux
- `phil/press-kit-bundle` · 🗓️ prévu — Une trousse de presse : logos, photos, biographies, communiqués
- `phil/spaces` · 🗓️ prévu — Un registre des modules qu'active un groupe ou une organisation
- `phil/ranking` · 🗓️ prévu — Les tris populaire, actif, controversé et meilleur, partagés par le forum, les idées et les questions
- `phil/reputation` · 🗓️ prévu — La réputation issue des votes des pairs, avec un plafond quotidien et sans vote négatif
- `phil/community-notes` · 🗓️ prévu — Des notes communautaires publiées selon une règle d'accord croisé explicable
- `phil/user-blocks` · 🗓️ prévu — Ignorer ou mettre en sourdine un membre, un groupe, un domaine ou des mots-clés
- `phil/watched-words` · 🗓️ prévu — Des mots surveillés qui bloquent, retiennent, signalent, remplacent ou étiquettent
- `phil/incident-mode` · 🗓️ prévu — Un mode d'incident autonome : préréglages, durée obligatoire, levée automatique
- `phil/elections-bundle` · 🗓️ prévu — Les élections de modérateurs par vote unique transférable
- `phil/watch-party` · 🗓️ prévu — Écouter ou regarder ensemble, synchronisés, avec un clavardage modéré
- `phil/milestones` · 🗓️ prévu — Des jalons sur un compteur et le seuil de production d'un article
- `phil/milestones-bundle` · 🗓️ prévu — Les jalons dans Symfony : compteurs reliés aux événements du site, progression dans Twig
- `phil/habits` · 🗓️ prévu — Un suivi d'habitudes avec séries et score de force lissé

</details>

<details>
<summary><b>Apprentissage et attestations</b> — ✅ 1 · 🧪 2 · 🗓️ 8</summary>

- [`phil/open-badges`](https://github.com/parler-haut-interagir-librement/open-badges) · ✅ publié ([Packagist](https://packagist.org/packages/phil/open-badges)) — Émettre, signer, vérifier, cuire et révoquer des justificatifs Open Badges 3.0
- `phil/open-badges-bundle` · 🧪 85 % — Profil de l'émetteur, clé publique et page de vérification des Open Badges
- `phil/certificates-bundle` · 🧪 85 % — Des certificats vérifiables : critères, PDF à code QR, registre public
- `phil/courses-bundle` · 🗓️ prévu — Des cours en ligne : modules, leçons, progression
- `phil/mentoring-bundle` · 🗓️ prévu — Le mentorat : jumelage, séances, suivi
- `phil/assessment` · 🗓️ prévu — L'évaluation : types de questions, notation selon la certitude, banque de questions versionnée
- `phil/assessment-bundle` · 🗓️ prévu — L'évaluation dans Symfony : écrans de questionnaire, tentatives et administration de la banque de questions
- `phil/competencies` · 🗓️ prévu — Référentiels de compétences, plans d'apprentissage et alignements Open Badges
- `phil/peer-review` · 🗓️ prévu — L'évaluation par les pairs en phases, avec une double note et un étalonnage facultatif des correcteurs
- `phil/proposal-review` · 🗓️ prévu — Un seul moteur d'évaluation par jury pour appels, cours et concours, avec vote par paires
- `phil/spaced-repetition` · 🗓️ prévu — La répétition espacée générique : l'algorithme FSRS, les cartes et les révisions

</details>

<details>
<summary><b>Notifications, courriel et messagerie</b> — ✅ 3 · 🧪 2 · 🗓️ 11</summary>

- [`phil/instant-messenger`](https://github.com/parler-haut-interagir-librement/instant-messenger) · ✅ publié ([Packagist](https://packagist.org/packages/phil/instant-messenger)) — Les identifiants de messagerie par service : WhatsApp, Telegram, Signal, Matrix et d'autres
- [`phil/instant-messenger-bundle`](https://github.com/parler-haut-interagir-librement/instant-messenger-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/instant-messenger-bundle)) — Un champ d'identifiant de messagerie, une contrainte et des filtres Twig
- [`phil/bounce-parser`](https://github.com/parler-haut-interagir-librement/bounce-parser) · ✅ publié ([Packagist](https://packagist.org/packages/phil/bounce-parser)) — Lire les rebonds DSN et ARF et les réponses automatiques
- `phil/notifications-bundle` · 🧪 81 % — Toasts, centre de notifications, résumés par courriel, Web Push, Discord ou Slack
- `phil/email-address` · 🧪 92 % — La validation des adresses de courriel
- `phil/newsletter-bundle` · 🗓️ prévu — L'infolettre : listes, double inscription, gabarits, envoi par Symfony Mailer
- `phil/newsletter-archive` · 🗓️ prévu — L'archive publique des infolettres envoyées
- `phil/email-templates-bundle` · 🗓️ prévu — Des gabarits de courriel partagés entre plusieurs sites, à blocs conditionnels
- `phil/email-preview` · 🗓️ prévu — L'aperçu des gabarits de courriel
- `phil/mail-auth-check` · 🗓️ prévu — Tester SPF, DKIM et DMARC d'un domaine d'envoi
- `phil/inbound-mail-bundle` · 🗓️ prévu — Le courrier entrant, analysé et routé
- `phil/sms-bundle` · 🗓️ prévu — Envoyer et recevoir des SMS sur Symfony Notifier
- `phil/audience-segments` · 🗓️ prévu — Des segments d'audience définis par des règles, pour l'infolettre et les notifications
- `phil/live-chat` · 🗓️ prévu — Le clavardage en direct avec un visiteur
- `phil/mime-reader` · 🗓️ prévu — La lecture des courriels MIME, partagée par l'analyse des rebonds et le courriel entrant
- `phil/email-address-bundle` · 🗓️ prévu — Les adresses courriel dans Symfony : une contrainte, des règles de rebond et la lecture IMAP

</details>

<details>
<summary><b>Événements, calendrier et réservation</b> — ✅ 2 · 🧪 3 · 🗓️ 30</summary>

- [`phil/reservation`](https://github.com/parler-haut-interagir-librement/reservation) · ✅ publié ([Packagist](https://packagist.org/packages/phil/reservation)) — Le noyau de réservation : ressources, créneaux, règles, conflits et rappels
- [`phil/checkin`](https://github.com/parler-haut-interagir-librement/checkin) · ✅ publié ([Packagist](https://packagist.org/packages/phil/checkin)) — Un code lu à une porte, décidé aussitôt, noté une fois, en ligne ou hors ligne
- `phil/calendar-bundle` · 🧪 61 % — Des événements, répétés ou non, en mois, semaine, jour, liste ou affiches
- `phil/reservation-bundle` · 🧪 85 % — Les réservations dans Symfony : ressources, plages, conflits et rappels
- `phil/checkin-bundle` · 🧪 85 % — Le noyau d'accueil commun : billet ou inscription lus, présence notée
- `phil/convention-bundle` · 🗓️ prévu — Le programme d'une convention : tables, places, inscriptions, lieux et salles
- `phil/booking-bundle` · 🗓️ prévu — La prise de rendez-vous sur le noyau de réservation
- `phil/scheduling-poll-bundle` · 🗓️ prévu — Le sondage de disponibilités, répondu par lien sans compte
- `phil/shared-timer-bundle` · 🗓️ prévu — Une minuterie partagée par Mercure, enchaînée, avec télécommande
- `phil/qr-attendance` · 🗓️ prévu — La présence lue au code QR
- `phil/waitlist-bundle` · 🗓️ prévu — Les listes d'attente et la libération des places
- `phil/workshops-bundle` · 🗓️ prévu — Des ateliers : sessions, places, inscriptions
- `phil/carpool-bundle` · 🗓️ prévu — Le covoiturage vers un événement
- `phil/lodging-bundle` · 🗓️ prévu — L'hébergement d'un événement : chambres, lits, attributions
- `phil/meal-planning` · 🗓️ prévu — Les repas d'un événement : menus, allergies, quantités
- `phil/equipment-rental` · 🗓️ prévu — La location de matériel sur le noyau de réservation
- `phil/event-weather` · 🗓️ prévu — La météo prévue d'un événement en plein air
- `phil/participant-safety-info` · 🗓️ prévu — Les renseignements de sécurité des participants, chiffrés, lus par les seuls responsables
- `phil/press-accreditation` · 🗓️ prévu — L'accréditation des médias à un événement
- `phil/lost-and-found` · 🗓️ prévu — Les objets perdus et trouvés d'un événement
- `phil/schedule-app` · 🗓️ prévu — Le programme d'un événement en application installable hors ligne, avec horaire personnel
- `phil/digital-signage` · 🗓️ prévu — L'affichage dynamique : horaire et annonces sur des écrans
- `phil/virtual-queue` · 🗓️ prévu — La file d'attente virtuelle d'un kiosque ou d'une activité
- `phil/qr-menu` · 🗓️ prévu — Un menu consultable par code QR
- `phil/calendar-sync` · 🗓️ prévu — La synchronisation des calendriers externes : plages occupées bloquées depuis ICS et CalDAV
- `phil/calendar-activitypub` · 🗓️ prévu — Les événements du calendrier fédérés par ActivityPub
- `phil/availability` · 🗓️ prévu — Les absences avec transfert, les exceptions de dates et les fériés importés d'ICS
- `phil/reservation-teams` · 🗓️ prévu — Les réservations collectives : tourniquet pondéré, groupes et réaffectation
- `phil/call-for-papers-bundle` · 🗓️ prévu — Un appel de propositions : échéances par type de séance, coprésentateurs, cycle d'évaluation
- `phil/speakers-bundle` · 🗓️ prévu — Les présentateurs sans compte requis, leur profil réutilisé d'un événement à l'autre
- `phil/shifts` · 🗓️ prévu — Les quarts de bénévolat, trois modes d'affectation, un tableau d'échanges et une réserve
- `phil/shifts-bundle` · 🗓️ prévu — Les quarts de bénévolat dans Symfony : inscription, tableau d'échanges, écrans de coordination
- `phil/signup-rounds` · 🗓️ prévu — Des groupes d'inscription avec capacités, et des choix classés traités par tours
- `phil/assignment` · 🗓️ prévu — L'affectation par préférences classées : tours de choix classés, puis optimisation globale
- `phil/stockroom` · 🗓️ prévu — Une réserve d'accessoires : contenants, articles, mouvements et listes de chargement

</details>

<details>
<summary><b>Commerce</b> — ✅ 4 · 🧪 11 · 🗓️ 27</summary>

- [`phil/money`](https://github.com/parler-haut-interagir-librement/money) · ✅ publié ([Packagist](https://packagist.org/packages/phil/money)) — Des montants en entiers exacts dans une devise connue, sans aucun nombre flottant
- [`phil/money-bundle`](https://github.com/parler-haut-interagir-librement/money-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/money-bundle)) — L'argent dans les formulaires, la validation, Twig et Doctrine de Symfony, sans flottants
- [`phil/tax`](https://github.com/parler-haut-interagir-librement/tax) · ✅ publié ([Packagist](https://packagist.org/packages/phil/tax)) — Plusieurs taxes sur une vente, détaillées au cent
- [`phil/commerce-product-template`](https://github.com/parler-haut-interagir-librement/commerce-product-template) · ✅ publié ([Packagist](https://packagist.org/packages/phil/commerce-product-template)) — Des gabarits de produit qui génèrent combinaisons, SKU, maquettes et bons de production
- `phil/commerce-bundle` · 🧪 90 % — Commandes, prix, taxes, paiements et reçus pour une boutique Symfony, avec des modules par-dessus
- `phil/commerce-catalog-bundle` · 🧪 55 % — Produits, listes de prix et promotions
- `phil/commerce-logistics-bundle` · 🧪 84 % — Stock par emplacement, réservations, colis et modes de livraison par zone
- `phil/commerce-pos-bundle` · 🧪 80 % — Une caisse pour la vente au comptoir : tiroirs, quarts, comptes de caisse, mises de côté, ventes hors ligne
- `phil/commerce-returns-bundle` · 🧪 82 % — Les retours, de l'autorisation au remboursement, au crédit ou à l'échange, ligne par ligne
- `phil/commerce-stored-value-bundle` · 🧪 92 % — Cartes-cadeaux numériques et crédit en boutique, dépensés comme paiements d'une commande
- `phil/commerce-subscription-bundle` · 🧪 93 % — Offres récurrentes par paliers : essais, renouvellement, relances et fonctions débloquées
- `phil/commerce-syndication-bundle` · 🧪 85 % — Revendre les produits d'une autre boutique, commandes transmises au fournisseur qui expédie
- `phil/commerce-wholesale-bundle` · 🧪 94 % — Groupes de clients à prix et minimums propres, ventes à crédit à terme net
- `phil/commerce-product-template-bundle` · 🧪 75 % — Les gabarits de produit dans le catalogue et l'administration
- `phil/licensing-bundle` · 🧪 96 % — Les licences d'une œuvre ou d'un produit numérique
- `phil/coupons-bundle` · 🗓️ prévu — Des codes promotionnels utilisables sans le catalogue : dons, billets, adhésions
- `phil/donations-bundle` · 🗓️ prévu — Les dons ponctuels ou mensuels
- `phil/digital-downloads` · 🗓️ prévu — Vendre et livrer des fichiers numériques
- `phil/product-bundles` · 🗓️ prévu — Les ensembles de produits vendus ensemble
- `phil/preorders-bundle` · 🗓️ prévu — Les précommandes, facturées à la sortie
- `phil/receipt-email` · 🗓️ prévu — Le reçu d'un paiement et le reçu fiscal d'un don par courriel
- `phil/invoicing-bundle` · 🗓️ prévu — Des factures et leurs paiements
- `phil/accounting-export` · 🗓️ prévu — L'export des ventes et paiements vers la comptabilité
- `phil/affiliates-bundle` · 🗓️ prévu — L'affiliation : liens, commissions, versements
- `phil/abandoned-cart` · 🗓️ prévu — La relance d'un panier abandonné, avec le consentement du client
- `phil/inventory-alerts` · 🗓️ prévu — Les alertes de stock bas et de retour en stock
- `phil/local-pickup` · 🗓️ prévu — Le ramassage d'une commande en magasin ou au kiosque d'une convention
- `phil/trade-in-bundle` · 🗓️ prévu — La reprise d'articles usagés contre un crédit
- `phil/auctions` · 🗓️ prévu — Les enchères : mises, prix de réserve, fin, paiement
- `phil/product-feeds` · 🗓️ prévu — Le catalogue en flux pour les comparateurs et places de marché
- `phil/shoppable-images` · 🗓️ prévu — Une image dont chaque objet mène à sa fiche produit
- `phil/currency-display` · 🗓️ prévu — Un prix affiché dans la devise du visiteur
- `phil/contracts-bundle` · 🗓️ prévu — Des contrats générés, envoyés et suivis
- `phil/crm-lite` · 🗓️ prévu — Un carnet de clients et l'historique des échanges
- `phil/commerce-promotions-bundle` · 🗓️ prévu — Les promotions automatiques : achetez X obtenez Y, livraison gratuite, limites d'usage
- `phil/commerce-payment-plans-bundle` · 🗓️ prévu — Les paiements échelonnés avec délai de grâce ; rien n'est expédié avant le dernier paiement
- `phil/commerce-quick-order-bundle` · 🗓️ prévu — La commande rapide par UGS ou code-barres, lignes collées, nouvelles commandes et listes partagées
- `phil/commerce-embed` · 🗓️ prévu — Un bouton d'achat et un widget à intégrer dans une autre page
- `phil/barcode` · 🗓️ prévu — Les codes-barres EAN, UPC, ISBN, Code 128 et GS1
- `phil/barcode-bundle` · 🗓️ prévu — Les codes-barres dans Symfony : rendu Twig, validation, saisie par lecteur
- `phil/benefit-deliverables` · 🗓️ prévu — Les avantages dus à chaque membre, en liste de contrôle par période
- `phil/external-entitlements` · 🗓️ prévu — Des droits datés accordés par des plateformes externes de soutien

</details>

<details>
<summary><b>Lieux, contacts et répertoires</b> — ✅ 9 · 🧪 3 · 🗓️ 4</summary>

- [`phil/address`](https://github.com/parler-haut-interagir-librement/address) · ✅ publié ([Packagist](https://packagist.org/packages/phil/address)) — Des adresses postales vérifiées et écrites comme chaque pays les écrit
- [`phil/address-bundle`](https://github.com/parler-haut-interagir-librement/address-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/address-bundle)) — Un formulaire d'adresse dont les champs suivent le pays choisi
- [`phil/phone`](https://github.com/parler-haut-interagir-librement/phone) · ✅ publié ([Packagist](https://packagist.org/packages/phil/phone)) — Des numéros de téléphone lus comme on les tape, vérifiés selon le plan de leur pays, et formatés
- [`phil/phone-bundle`](https://github.com/parler-haut-interagir-librement/phone-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/phone-bundle)) — Un champ de téléphone, une contrainte, un type de colonne et des filtres Twig
- [`phil/contact-form-bundle`](https://github.com/parler-haut-interagir-librement/contact-form-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/contact-form-bundle)) — Une page « écrivez-nous », protégée du pourriel sans CAPTCHA
- [`phil/geo`](https://github.com/parler-haut-interagir-librement/geo) · ✅ publié ([Packagist](https://packagist.org/packages/phil/geo)) — Coordonnées, distances et boîtes englobantes en valeurs, géocodage par le fournisseur choisi
- [`phil/geo-bundle`](https://github.com/parler-haut-interagir-librement/geo-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/geo-bundle)) — Coordonnées gardées, distances dans Twig, géocodeurs et listes du plus proche au plus loin
- [`phil/opening-hours`](https://github.com/parler-haut-interagir-librement/opening-hours) · ✅ publié ([Packagist](https://packagist.org/packages/phil/opening-hours)) — Les heures d'ouverture d'un lieu, et s'il est ouvert en ce moment
- [`phil/opening-hours-bundle`](https://github.com/parler-haut-interagir-librement/opening-hours-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/opening-hours-bundle)) — Un formulaire d'heures d'ouverture, une colonne JSON et les heures localisées dans Twig
- `phil/contact` · 🧪 85 % — Fiches de contact de personnes et d'organisations, en vCard ou JSON-LD
- `phil/contact-bundle` · 🧪 95 % — Un formulaire de fiche de contact, une colonne JSON et le téléchargement en vCard
- `phil/directory-bundle` · 🧪 92 % — Un répertoire de fiches que les membres écrivent et l'administration publie
- `phil/map-bundle` · 🗓️ prévu — Des cartes Leaflet en Stimulus, sur des tuiles sans pistage
- `phil/contact-sync` · 🗓️ prévu — La synchronisation des contacts par CardDAV
- `phil/portfolio-bundle` · 🗓️ prévu — Un portfolio, une fiche par projet
- `phil/library-bundle` · 🗓️ prévu — Une ludothèque ou une bibliothèque : catalogue, prêts, retours

</details>

<details>
<summary><b>Exploitation et administration</b> — ✅ 6 · 🧪 4 · 🗓️ 11</summary>

- [`phil/migration`](https://github.com/parler-haut-interagir-librement/migration) · ✅ publié ([Packagist](https://packagist.org/packages/phil/migration)) — Notes de version et nouvelles que les migrations Doctrine envoient au clavardage
- [`phil/migration-bundle`](https://github.com/parler-haut-interagir-librement/migration-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/migration-bundle)) — Chaque passage des migrations annoncé une fois sur vos canaux de clavardage
- [`phil/backup-bundle`](https://github.com/parler-haut-interagir-librement/backup-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/backup-bundle)) — Sauvegarde et restauration protégée : base, médias, chiffrement, rotation
- [`phil/backup`](https://github.com/parler-haut-interagir-librement/backup) · ✅ publié ([Packagist](https://packagist.org/packages/phil/backup)) — Sauvegarder une base et ses médias, chiffrés et en rotation, et prouver qu'ils se restaurent
- [`phil/monitoring-bundle`](https://github.com/parler-haut-interagir-librement/monitoring-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/monitoring-bundle)) — Points de santé, mode maintenance, disponibilité, tâches planifiées et files
- [`phil/reporting-bundle`](https://github.com/parler-haut-interagir-librement/reporting-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/reporting-bundle)) — Tableaux de bord en composants Twig, graphiques accessibles, rapports planifiés
- `phil/error-tracking` · 🧪 88 % — Le suivi des erreurs chez soi, données personnelles retirées avant toute écriture
- `phil/error-tracking-bundle` · 🧪 89 % — Le suivi des erreurs dans Symfony : groupes, régressions par version, alertes par une file
- `phil/broken-flow-alerts` · 🧪 90 % — L'alerte quand un parcours cesse d'aboutir
- `phil/settings-bundle` · 🧪 88 % — Les réglages qu'un usager modifie lui-même
- `phil/sites-console-bundle` · 🗓️ prévu — Gérer plusieurs sites : versions, santé, configuration commune, comptes d'administration
- `phil/status-page-bundle` · 🗓️ prévu — La page d'état des services
- `phil/bulk-actions` · 🗓️ prévu — Les actions en lot dans une administration
- `phil/admin-notes` · 🗓️ prévu — Les notes internes de l'administration sur une fiche
- `phil/duplicate-detector` · 🗓️ prévu — Détecter et fusionner les fiches en double
- `phil/dependency-report` · 🗓️ prévu — Les dépendances d'un paquet ou d'un site et leurs licences
- `phil/secrets-rotation` · 🗓️ prévu — La rotation des secrets d'une application
- `phil/helpdesk-bundle` · 🗓️ prévu — Un service d'assistance : demandes, files, réponses types
- `phil/automations` · 🗓️ prévu — Des automatisations sans code déclenchées par les événements du site
- `phil/data-table-export` · 🗓️ prévu — Des lignes exportées en CSV, puis en XLSX
- `phil/expenses-bundle` · 🗓️ prévu — Les notes de frais : politique affichée, personne n'approuve la sienne, reçus privés

</details>

<details>
<summary><b>Intégrations et IA</b> — 🧪 1 · 🗓️ 6</summary>

- `phil/ai-bundle` · 🧪 70 % — Des tâches de modèle de langue qui proposent sans imposer, comptées au jeton, sans rien retenir
- `phil/mcp-bundle` · 🗓️ prévu — Un serveur MCP sur Symfony AI, dans les droits de l'usager, audité
- `phil/slack-interactions-bundle` · 🗓️ prévu — Les commandes et interactions Slack signées
- `phil/notion` · 🗓️ prévu — Lire et écrire une base Notion, le texte converti en UJO (Universal JSON Output)
- `phil/logseq` · 🗓️ prévu — Lire et écrire un graphe Logseq
- `phil/chat-community` · 🗓️ prévu — Relier une communauté à un service de clavardage : rôles liés, événements reproduits, annonces
- `phil/chat-interactions-bundle` · 🗓️ prévu — Les interactions signées d'un service de clavardage : signatures Ed25519, commandes, réponses différées

</details>

<details>
<summary><b>UX et interface</b> — ✅ 3 · 🧪 5 · 🗓️ 8</summary>

- [`phil/ux-css`](https://github.com/parler-haut-interagir-librement/ux-css) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ux-css)) — phil-ux, le cadre CSS : jetons OKLCH, thèmes clair et sombre, éléments sans classe, utilitaires de mise en page
- [`phil/ux-kit`](https://github.com/parler-haut-interagir-librement/ux-kit) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ux-kit)) — Le kit PHIL UX pour le Toolkit de Symfony UX : les recettes du kit Shadcn et les siennes, habillées par phil-ux
- [`phil/menu-bundle`](https://github.com/parler-haut-interagir-librement/menu-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/menu-bundle)) — Menus de navigation et fil d'Ariane, avec la page courante marquée
- `phil/ux-bundle` · 🧪 37 % — Les composants PHIL UX, en réécriture en kit pour le Toolkit de Symfony UX et en CSS phil-ux
- `phil/ux-kit-shadcn` · 🧪 88 % — Les versions Tailwind, à la façon de Shadcn, des recettes que PHIL UX ajoute
- `phil/forms-bundle` · 🧪 90 % — Des formulaires définis en base, leurs réponses gardées le temps nécessaire seulement
- `phil/data-table-bundle` · 🧪 88 % — Des tableaux en Live Component : tri, filtres, édition en ligne, empilés sur mobile
- `phil/forms-autosave` · 🧪 90 % — La saisie d'un formulaire gardée en cours de route
- `phil/forms-signature` · 🗓️ prévu — Un champ de signature manuscrite ou électronique
- `phil/pwa-bundle` · 🗓️ prévu — Des sites installables et lisibles hors ligne : manifeste, service worker, plein écran
- `phil/theme-builder` · 🗓️ prévu — Composer un thème à partir des jetons PHIL UX
- `phil/page-builder` · 🗓️ prévu — Des pages composées de blocs, sans code
- `phil/landing-pages` · 🗓️ prévu — Des pages d'atterrissage composées par l'administration
- `phil/menu-builder-ui` · 🗓️ prévu — L'édition des menus à la souris
- `phil/announcement-bar` · 🗓️ prévu — Le bandeau d'annonce d'un site
- `phil/ux-translate` · 🗓️ prévu — L'API Translator du navigateur en Stimulus et en Twig, à la demande, jamais envoyée à un service

</details>


### Participer

- 💬 Questions et idées : [Discussions](https://github.com/orgs/parler-haut-interagir-librement/discussions)
- 🐛 Bogues et demandes de fonctions : un ticket dans le dépôt concerné
- 🤝 [Contribuer](https://github.com/parler-haut-interagir-librement/.github/blob/main/CONTRIBUTING.md) ·
  [Code de conduite](https://github.com/parler-haut-interagir-librement/.github/blob/main/CODE_OF_CONDUCT.md) ·
  [Sécurité](https://github.com/parler-haut-interagir-librement/.github/blob/main/SECURITY.md) ·
  [Soutien](https://github.com/parler-haut-interagir-librement/.github/blob/main/SUPPORT.md)
- ✉️ [info@ph-il.ca](mailto:info@ph-il.ca) · 🌐 [ph-il.ca](https://ph-il.ca)
