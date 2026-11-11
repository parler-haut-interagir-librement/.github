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
- **The tooling** every package is checked with: `phil/dev-tools` and the project skeletons.

[ph-il.ca](https://ph-il.ca) presents the platform and will become the catalogue of the modules: one page per
package, generated from its README and its documentation, in English and in French.

The game and gamification packages — dice, generators, points, badges, quests and the rest — live next door, in
[Tilttek](https://github.com/TiltTek).

## Why

Shops, conventions, clubs, publishers and online communities keep needing the same bricks: a catalogue and a cash
register, a calendar, a forum, a newsletter, a privacy policy that is actually applied. We would rather write each
brick once, carefully, in the open, than glue the same parts together on every site. And we would rather tell you
plainly how far along each brick is: **today, 28 packages are released; the others are being written or planned,
and they follow by small daily groups.**

## Principles

- **Written from scratch.** No third-party code is copied into a PHIL package. Other projects are studied for ideas,
  never pasted.
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
| [ux-kit](https://github.com/parler-haut-interagir-librement/ux-kit) | The PHIL UX kit: the same recipes as the Toolkit's Shadcn kit — names, props, Twig blocks, Stimulus controllers — with HTML and CSS written from scratch and styled with phil-ux. `php bin/console ux:install <recipe> --kit=github.com/parler-haut-interagir-librement/ux-kit` | 🧪 incubation, ~10% |
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
  and the skeleton of a new package. Published under the MIT licence:
  [dev-tools](https://github.com/parler-haut-interagir-librement/dev-tools).
- **Project skeletons** — [MicroSymfony](https://github.com/parler-haut-interagir-librement/MicroSymfony) (based on
  `strangebuzz/MicroSymfony`) and [WebSymfony](https://github.com/parler-haut-interagir-librement/WebSymfony).

## The packages

✅ **released** · 🧪 **written, in incubation** (approximate completion) · 🗓️ **planned**

**339 packages:** 28 released, 127 in incubation, 184 planned. Percentages are estimates from our
latest status report (8 November 2026). The released packages are developed in the public monorepo
[`phil`](https://github.com/parler-haut-interagir-librement/phil), each split into its own read-only repository and
published on Packagist; `phil/enums` continues [`ph-il/enums`](https://packagist.org/packages/ph-il/enums). **The
showcase continues by small daily groups** of two to four packages, dependencies first.
`phil/identity-provider-*` stands for one package per sign-in provider.

<details>
<summary><b>Data &amp; infrastructure</b> — ✅ 12 · 🧪 20 · 🗓️ 9</summary>

- [`phil/enums`](https://github.com/parler-haut-interagir-librement/enums) · ✅ released ([Packagist](https://packagist.org/packages/phil/enums)) — Traits and attributes to list, compare, describe and group PHP enums (formerly `ph-il/enums`)
- [`phil/enums-bundle`](https://github.com/parler-haut-interagir-librement/enums-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/enums-bundle)) — Enums in Symfony forms, translations, Twig, validation, Doctrine and API contracts
- [`phil/resource`](https://github.com/parler-haut-interagir-librement/resource) · ✅ released ([Packagist](https://packagist.org/packages/phil/resource)) — Point at any record by its kind and identifier, such as `page:42`
- [`phil/ddd-bundle`](https://github.com/parler-haut-interagir-librement/ddd-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/ddd-bundle)) — Shared domain types: identifiers, domain events, errors, command and query buses
- [`phil/slug`](https://github.com/parler-haut-interagir-librement/slug) · ✅ released ([Packagist](https://packagist.org/packages/phil/slug)) — URL slugs from titles and names, as a type that accepts nothing else
- [`phil/slug-bundle`](https://github.com/parler-haut-interagir-librement/slug-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/slug-bundle)) — Named sluggers declared in configuration, autowired and usable in Twig
- [`phil/recurrence`](https://github.com/parler-haut-interagir-librement/recurrence) · ✅ released ([Packagist](https://packagist.org/packages/phil/recurrence)) — Repeating dates from RFC 5545 rules: read, check, write, list occurrences
- [`phil/recurrence-bundle`](https://github.com/parler-haut-interagir-librement/recurrence-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/recurrence-bundle)) — A form for repeating events, a column for the rule, and the rule in words
- [`phil/standard-webhooks`](https://github.com/parler-haut-interagir-librement/standard-webhooks) · ✅ released ([Packagist](https://packagist.org/packages/phil/standard-webhooks)) — Sign and verify webhooks to the Standard Webhooks specification
- [`phil/standard-webhooks-bundle`](https://github.com/parler-haut-interagir-librement/standard-webhooks-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/standard-webhooks-bundle)) — Verified webhook deliveries as controller arguments, and signed webhooks sent
- [`phil/circuit-breaker`](https://github.com/parler-haut-interagir-librement/circuit-breaker) · ✅ released ([Packagist](https://packagist.org/packages/phil/circuit-breaker)) — One circuit breaker for HTTP clients and feature flags
- [`phil/circuit-breaker-bundle`](https://github.com/parler-haut-interagir-librement/circuit-breaker-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/circuit-breaker-bundle)) — One circuit breaker wired into Symfony HTTP clients and feature flags
- `phil/doctrine-behaviours` · 🧪 55% — Opt-in timestamps, blame, soft delete and trees for Doctrine entities
- `phil/doctrine-behaviours-bundle` · 🧪 60% — Entity behaviours switched on by configuration in Symfony
- `phil/url` · 🧪 95% — Web addresses as normalised values, their kind detected: Mastodon, YouTube, a website
- `phil/url-bundle` · 🧪 95% — Link fields that detect their kind, a constraint, a column type and Twig filters
- `phil/references-bundle` · 🧪 95% — Know where each resource is used, and refuse to delete one still needed
- `phil/trash-bundle` · 🧪 95% — A trash for deleted resources: restore them, or purge them after a set time
- `phil/almanac` · 🧪 85% — Easter, Moon phases, seasons and dates in words, for any year
- `phil/almanac-bundle` · 🧪 90% — Holidays and computed dates in configuration, editable, shown in Twig
- `phil/scheduled-transitions-bundle` · 🧪 95% — Publish and unpublish on a schedule, with nobody online
- `phil/tenancy-bundle` · 🧪 65% — Which tenant an account acts in, switched instantly and enforced in every query
- `phil/feature-flags-bundle` · 🧪 90% — Turn features off without a deploy, run A/B tests, stop calling a failing service
- `phil/usage-meter` · 🧪 90% — Measure what each subject used and refuse an action past its quota
- `phil/http-cache-tags-bundle` · 🧪 95% — Cache whole pages in Varnish or a CDN, purge exactly what an edit changed
- `phil/api-contract` · 🧪 70% — Problem details, deprecation signals and idempotency keys for HTTP APIs
- `phil/api-contract-bundle` · 🧪 90% — Problem details, replayed idempotent requests and deprecation notices in Symfony
- `phil/usage-meter-bundle` · 🧪 93% — Usage meters stored with DBAL, rate limiters and purge commands
- `phil/encrypted-fields` · 🧪 92% — Doctrine columns encrypted with libsodium, blind indexes, key rotation
- `phil/encrypted-fields-bundle` · 🧪 85% — Encrypted fields configured in Symfony, keys in Symfony secrets or a KMS
- `phil/rate-limit-bundle` · 🧪 92% — Rate limits declared by attribute on routes, forms and APIs
- `phil/api-keys-bundle` · 🧪 88% — Personal access tokens for a public API: scopes, expiry, revocation, quotas
- `phil/idempotency` · 🗓️ planned — Idempotency keys for APIs, Messenger, payment webhooks and double form posts
- `phil/console-bundle` · 🗓️ planned — Console guards per environment and timestamped output
- `phil/spreadsheet` · 🗓️ planned — Read and write XLSX, ODS and CSV
- `phil/import-wizard` · 🗓️ planned — Guided file import, column by column
- `phil/json-canvas` · 🗓️ planned — Read and write the open JSON Canvas format
- `phil/open-data` · 🗓️ planned — Publish a site's open data
- `phil/number-words` · 🗓️ planned — Numbers written in words, in every language
- `phil/natural-dates` · 🗓️ planned — Dates typed in words ("next Thursday 7 pm") understood in each language
- `phil/timezone-display` · 🗓️ planned — Times shown in the visitor's time zone

</details>

<details>
<summary><b>Content &amp; text</b> — ✅ 6 · 🧪 15 · 🗓️ 20</summary>

- [`phil/ujo`](https://github.com/parler-haut-interagir-librement/ujo) · ✅ released ([Packagist](https://packagist.org/packages/phil/ujo)) — UJO (Universal JSON Output) documents read strictly, checked block by block, rendered as safe HTML
- [`phil/ujo-bundle`](https://github.com/parler-haut-interagir-librement/ujo-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/ujo-bundle)) — UJO (Universal JSON Output) documents in Doctrine, forms and Twig
- [`phil/text-diff`](https://github.com/parler-haut-interagir-librement/text-diff) · ✅ released ([Packagist](https://packagist.org/packages/phil/text-diff)) — What changed between two texts, word by word, paragraph by paragraph or block by block
- [`phil/highlight`](https://github.com/parler-haut-interagir-librement/highlight) · ✅ released ([Packagist](https://packagist.org/packages/phil/highlight)) — Code in 24 languages coloured on the server, as plain HTML any stylesheet can theme
- [`phil/css-sanitizer`](https://github.com/parler-haut-interagir-librement/css-sanitizer) · ✅ released ([Packagist](https://packagist.org/packages/phil/css-sanitizer)) — Let people style their pages without their CSS running code, loading what it should not, or leaving its frame
- [`phil/highlight-bundle`](https://github.com/parler-haut-interagir-librement/highlight-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/highlight-bundle)) — Highlighting wired into UJO (Universal JSON Output) rendering and Twig, with a theme
- `phil/content-bundle` · 🧪 88% — Pages and articles stored by locale, stage and version, published from draft to live
- `phil/markup` · 🧪 87% — Markdown, BBCode, MediaWiki, DokuWiki, Creole, HTML or plain text turned into safe HTML
- `phil/markup-bundle` · 🧪 93% — Markup formats rendered safely in Twig and converted to UJO (Universal JSON Output), as Symfony services
- `phil/block-editor-bundle` · 🧪 90% — A block editor for Symfony forms in Stimulus, writing UJO (Universal JSON Output) checked on the server
- `phil/edit-lock-bundle` · 🧪 94% — One writer per block: edit leases, presence and saves pushed through Mercure
- `phil/comments-bundle` · 🧪 83% — Comments and suggested changes anchored to passages, following the text as it changes
- `phil/taxonomy-bundle` · 🧪 95% — Tags and a translated category tree for any resource, with form types
- `phil/svg-sanitizer` · 🧪 94% — Purify SVG: allow-list of elements and attributes, no script, no external reference
- `phil/latex-mathml` · 🧪 80% — LaTeX formulas turned into the MathML that browsers draw, on the server
- `phil/svg-chart` · 🧪 90% — Charts drawn as SVG on the server, from the configuration a chart editor already writes
- `phil/svg-blocks` · 🧪 90% — Formulas, diagrams, charts and QR codes of block documents drawn once, on the server
- `phil/svg-blocks-bundle` · 🧪 85% — Block drawings made on save in Symfony, with Mermaid in a container
- `phil/text-diff-bundle` · 🧪 90% — Text comparison in Twig and Stimulus
- `phil/content-warnings` · 🧪 95% — Content warnings for games, books, articles and events, with a translated base list
- `phil/content-warnings-bundle` · 🧪 90% — Content warnings in forms, pages and filters
- `phil/wiki-bundle` · 🗓️ planned — A collaborative wiki: pages, compared revisions, `[[links]]`, block locks
- `phil/faq-bundle` · 🗓️ planned — Frequently asked questions by section, searchable, with structured data
- `phil/glossary-bundle` · 🗓️ planned — A glossary whose terms are linked automatically in texts
- `phil/timeline-bundle` · 🗓️ planned — Timelines of dated content
- `phil/series-bundle` · 🗓️ planned — Content series
- `phil/footnotes-sidenotes` · 🗓️ planned — Footnotes and side notes
- `phil/citations` · 🗓️ planned — Citations and bibliographies in common styles
- `phil/credits` · 🗓️ planned — The credits page of a work: contributors, roles, order
- `phil/math` · 🗓️ planned — Mathematical formulas rendered in MathML
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

</details>

<details>
<summary><b>Languages, translation &amp; typography</b> — ✅ 2 · 🧪 2 · 🗓️ 2</summary>

- [`phil/typography`](https://github.com/parler-haut-interagir-librement/typography) · ✅ released ([Packagist](https://packagist.org/packages/phil/typography)) — Real quotes, dashes, French spaces and soft hyphens in your HTML, in every language
- [`phil/typography-bundle`](https://github.com/parler-haut-interagir-librement/typography-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/typography-bundle)) — Typography everywhere a Symfony application prints text
- `phil/translation-bundle` · 🧪 83% — A translation screen: segments that survive edits, a memory and a checking glossary
- `phil/translation-memory` · 🧪 87% — Segment-by-segment translation that reuses past work and keeps terms consistent
- `phil/machine-translation` · 🗓️ planned — Machine-suggested translations, always reviewed
- `phil/translation-ui` · 🗓️ planned — The screen for translating a site's content and messages

</details>

<details>
<summary><b>Media, documents &amp; print</b> — ✅ 1 · 🧪 13 · 🗓️ 11</summary>

- [`phil/qr-code`](https://github.com/parler-haut-interagir-librement/qr-code) · ✅ released ([Packagist](https://packagist.org/packages/phil/qr-code)) — QR codes written from scratch, Reed-Solomon included, in SVG and PNG
- `phil/media-bundle` · 🧪 80% — Uploaded files and images, described, versioned and served at signed URLs
- `phil/document-import` · 🧪 73% — Word-processing documents, Markdown and HTML turned into UJO (Universal JSON Output), with a report of what did not fit
- `phil/epub` · 🧪 85% — EPUB 3 books from your HTML, valid for EPUBCheck and readable by assistive technologies
- `phil/fonts` · 🧪 95% — What a font file says about itself — names, weight, embedding licence — and its `@font-face`
- `phil/paged-media` · 🧪 68% — PDF documents from PHP, with real fonts and paged HTML/CSS engines
- `phil/paged-media-bundle` · 🧪 90% — PDFs in Symfony, from a native writer or Gotenberg, through one service, now or through Messenger
- `phil/print-preflight` · 🧪 82% — Catch what a printer would refuse before the file reaches it
- `phil/document-import-bundle` · 🧪 90% — Document import wired into the media library
- `phil/fonts-bundle` · 🧪 95% — Fonts configured for PDF and media
- `phil/epub-bundle` · 🧪 95% — EPUB generation in Symfony
- `phil/print-preflight-bundle` · 🧪 90% — Preflight wired into PDF generation
- `phil/print-compositor` · 🧪 90% — Garment mock-ups and print files, one layer per ink
- `phil/qr-code-bundle` · 🧪 88% — QR codes in Twig, routes and typed contents (URL, vCard, Wi-Fi, iCalendar)
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

</details>

<details>
<summary><b>Search, SEO &amp; the open web</b> — 🧪 10 · 🗓️ 11</summary>

- `phil/search-bundle` · 🧪 70% — Full-text search over your own resources, kept up to date at each Doctrine flush
- `phil/search-loupe` · 🧪 90% — Typo-tolerant search in SQLite files, with no server to run
- `phil/sitemap` · 🧪 95% — Sitemap XML built from checked pages, cut to the protocol's limits
- `phil/sitemap-bundle` · 🧪 96% — `/sitemap.xml` from route options, URL providers and an event
- `phil/social-cards` · 🧪 88% — Open Graph tags and generated share images
- `phil/social-cards-bundle` · 🧪 87% — Share metadata and generated cards in Symfony, with a preview of incoming links
- `phil/structured-data` · 🧪 92% — A page's schema.org graph assembled from JSON-LD pieces
- `phil/structured-data-bundle` · 🧪 88% — A page's schema.org graph in Symfony, with a command that checks it
- `phil/redirects-bundle` · 🧪 90% — Managed 301 redirects, 404 tracking, old domains
- `phil/well-known-bundle` · 🧪 90% — `/.well-known/` endpoints: security.txt, change-password, WebFinger, nodeinfo
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

</details>

<details>
<summary><b>Identity, access &amp; security</b> — ✅ 3 · 🧪 7 · 🗓️ 10</summary>

- [`phil/bot-detection-bundle`](https://github.com/parler-haut-interagir-librement/bot-detection-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/bot-detection-bundle)) — Tell a robot from a human in the browser, without a CAPTCHA
- [`phil/spam-protection`](https://github.com/parler-haut-interagir-librement/spam-protection) · ✅ released ([Packagist](https://packagist.org/packages/phil/spam-protection)) — Spot spam in a form submission without a CAPTCHA, in plain PHP
- [`phil/spam-protection-bundle`](https://github.com/parler-haut-interagir-librement/spam-protection-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/spam-protection-bundle)) — Keep spam out of Symfony forms without a CAPTCHA, a third party or an identifier
- `phil/user-secrets-bundle` · 🧪 80% — Keys people lend your application, sealed and theirs alone
- `phil/passwords` · 🧪 90% — A strength meter written from scratch, k-anonymous breach checks, generation
- `phil/csp-bundle` · 🧪 92% — Content Security Policy with nonces and reports
- `phil/route-access-check` · 🧪 90% — Fail CI when a route has no access rule
- `phil/route-access-check-bundle` · 🧪 90% — The route access check as a Symfony command, with a baseline and a strict mode
- `phil/upload-scan` · 🧪 92% — Antivirus scanning of uploads behind a port
- `phil/upload-scan-bundle` · 🧪 88% — Upload scanning in Symfony: a file constraint, quarantine and rescans
- `phil/identity-provider-bundle` · 🗓️ planned — An OpenID Connect provider written from scratch: passkeys, passwords, TOTP, step-up
- `phil/identity-provider-*` · 🗓️ planned — One package per federated sign-in provider, from Google to Bluesky
- `phil/identity-client-bundle` · 🗓️ planned — Connect a Symfony site to an OpenID provider, on Symfony 8.2's `oidc_login`
- `phil/organizations-bundle` · 🗓️ planned — Organisations, roles and invitations
- `phil/access-bundle` · 🗓️ planned — Access rights per site
- `phil/webauthn-step-up` · 🗓️ planned — Confirm a sensitive action with a passkey
- `phil/fraud-signals` · 🗓️ planned — Fraud signals on orders and sign-ups
- `phil/trust-levels` · 🗓️ planned — Trust levels that open rights with activity
- `phil/verification-marks` · 🗓️ planned — Verified-account marks
- `phil/invitations` · 🗓️ planned — Member invitations, with limits

</details>

<details>
<summary><b>Privacy, accessibility &amp; compliance</b> — 🧪 5 · 🗓️ 7</summary>

- `phil/privacy-bundle` · 🧪 62% — Declare personal fields, redact logs, answer access and erasure requests (Loi 25, GDPR)
- `phil/analytics-bundle` · 🧪 85% — Visits counted in daily aggregates, never tied to a person
- `phil/audit-bundle` · 🧪 60% — An append-only, tamper-evident audit trail that still lets you erase personal information
- `phil/ip-anonymizer` · 🧪 95% — Truncate, salt-hash and generalise IP addresses
- `phil/accessibility-check` · 🧪 90% — Accessibility checks at publication: alt texts, heading order, contrast
- `phil/legal-notices` · 🗓️ planned — A site's legal notices and privacy policy
- `phil/terms-bundle` · 🗓️ planned — Versioned terms of use and their acceptance
- `phil/accessibility-statement` · 🗓️ planned — A site's accessibility statement
- `phil/accessibility-info` · 🗓️ planned — Accessibility information for a venue or event
- `phil/easy-read` · 🗓️ planned — Easy-read versions of content, and their checks
- `phil/age-gate` · 🗓️ planned — Declarative age checks for content or listings
- `phil/heatmaps` · 🗓️ planned — Aggregated heatmaps, with no identifier

</details>

<details>
<summary><b>Community</b> — 🧪 3 · 🗓️ 32</summary>

- `phil/poll-bundle` · 🧪 85% — The voting engine: single, multiple or ranked choice
- `phil/poll` · 🧪 90% — A voting engine: ballots checked against their poll's rules, counted into standings
- `phil/listings` · 🧪 90% — The listings core: criteria, expiry, replies, moderation
- `phil/forum-bundle` · 🗓️ planned — Forums by section, with chat, reporting and per-section moderation
- `phil/moderation-bundle` · 🗓️ planned — One report queue for forums, comments, reactions, listings and messages
- `phil/reactions-bundle` · 🗓️ planned — Reactions to content, one per member, list chosen per site
- `phil/mentions-bundle` · 🗓️ planned — @mentions in texts, and their notifications
- `phil/follow-bundle` · 🗓️ planned — Follow content, threads, listings or members
- `phil/conversation-bundle` · 🗓️ planned — Private messages one-to-one or in groups, encrypted at rest
- `phil/groups-bundle` · 🗓️ planned — Member groups
- `phil/profiles-bundle` · 🗓️ planned — A member's public page: what they show, and to whom
- `phil/reviews-bundle` · 🗓️ planned — Moderated reviews and ratings of products, games or places
- `phil/survey-bundle` · 🗓️ planned — Questionnaires with sections and conditional logic
- `phil/ideas-bundle` · 🗓️ planned — An idea box with statuses and votes
- `phil/qa-bundle` · 🗓️ planned — Questions and answers, the best one accepted
- `phil/code-of-conduct` · 🗓️ planned — A code of conduct, its acceptance and its reports
- `phil/onboarding-bundle` · 🗓️ planned — Welcoming new members: steps, guided tour, checklist
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

</details>

<details>
<summary><b>Learning &amp; credentials</b> — 🧪 3 · 🗓️ 2</summary>

- `phil/open-badges` · 🧪 90% — Issue, sign, verify, bake and revoke Open Badges 3.0 credentials
- `phil/open-badges-bundle` · 🧪 85% — Issuer profile, public key and verification page for Open Badges
- `phil/certificates-bundle` · 🧪 85% — Verifiable certificates: criteria, PDF with QR code, public registry
- `phil/courses-bundle` · 🗓️ planned — Online courses: modules, lessons, progress
- `phil/mentoring-bundle` · 🗓️ planned — Mentoring: matching, sessions, follow-up

</details>

<details>
<summary><b>Notifications, mail &amp; messaging</b> — 🧪 5 · 🗓️ 10</summary>

- `phil/instant-messenger` · 🧪 95% — Messaging handles per service: WhatsApp, Telegram, Signal, Matrix and more
- `phil/instant-messenger-bundle` · 🧪 95% — A messaging handle field, a constraint and Twig filters
- `phil/notifications-bundle` · 🧪 80% — Toasts, a notification centre, email digests, Web Push, Discord or Slack
- `phil/bounce-parser` · 🧪 90% — Parse DSN and ARF bounces and auto-replies
- `phil/email-address` · 🧪 85% — Email address validation
- `phil/newsletter-bundle` · 🗓️ planned — Newsletters: lists, double opt-in, templates, sending through Symfony Mailer
- `phil/newsletter-archive` · 🗓️ planned — The public archive of sent newsletters
- `phil/email-automation` · 🗓️ planned — Newsletter sequences and triggers, never on an open
- `phil/email-templates-bundle` · 🗓️ planned — Email templates shared between several sites, with conditional blocks
- `phil/email-preview` · 🗓️ planned — Preview email templates
- `phil/mail-auth-check` · 🗓️ planned — Test a sending domain's SPF, DKIM and DMARC
- `phil/inbound-mail-bundle` · 🗓️ planned — Inbound mail, parsed and routed
- `phil/sms-bundle` · 🗓️ planned — Send and receive SMS on Symfony Notifier
- `phil/audience-segments` · 🗓️ planned — Audience segments defined by rules, for newsletters and notifications
- `phil/live-chat` · 🗓️ planned — Live chat with a visitor

</details>

<details>
<summary><b>Events, calendar &amp; booking</b> — 🧪 5 · 🗓️ 19</summary>

- `phil/calendar-bundle` · 🧪 61% — Events, repeating or not, as a month, week, day, list or posters
- `phil/reservation` · 🧪 90% — The booking core: resources, slots, rules, conflicts and reminders
- `phil/reservation-bundle` · 🧪 85% — Bookings in Symfony: resources, slots, conflicts and reminders
- `phil/checkin-bundle` · 🧪 85% — The shared check-in core: ticket or registration read, attendance noted
- `phil/checkin` · 🧪 92% — A code read at a door, decided at once, recorded once, online or offline
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

</details>

<details>
<summary><b>Commerce</b> — ✅ 2 · 🧪 12 · 🗓️ 20</summary>

- [`phil/money`](https://github.com/parler-haut-interagir-librement/money) · ✅ released ([Packagist](https://packagist.org/packages/phil/money)) — Amounts of money as exact integers in a known currency, with no float anywhere
- [`phil/money-bundle`](https://github.com/parler-haut-interagir-librement/money-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/money-bundle)) — Money in Symfony forms, validation, Twig and Doctrine, without floats
- `phil/tax` · 🧪 95% — Several taxes on one sale, itemised to the cent
- `phil/commerce-bundle` · 🧪 87% — Orders, prices, taxes, payments and receipts for a Symfony store, with modules on top
- `phil/commerce-catalog-bundle` · 🧪 55% — Products, price books and promotions
- `phil/commerce-logistics-bundle` · 🧪 77% — Stock per location, reservations, parcels and delivery methods per zone
- `phil/commerce-pos-bundle` · 🧪 80% — A cash register for counter sales: tills, shifts, cash counts, layaways, offline sales
- `phil/commerce-returns-bundle` · 🧪 82% — Returns from authorisation to refund, store credit or exchange, line by line
- `phil/commerce-stored-value-bundle` · 🧪 85% — Digital gift cards and store credit, spent as payments of an order
- `phil/commerce-subscription-bundle` · 🧪 80% — Recurring offers in tiers: trials, renewal, dunning and unlocked features
- `phil/commerce-syndication-bundle` · 🧪 85% — Resell another shop's products, orders forwarded to the supplier who ships
- `phil/commerce-wholesale-bundle` · 🧪 90% — Customer groups with their own prices and minimums, sales on credit with net terms
- `phil/commerce-product-template` · 🧪 90% — Product templates that generate combinations, SKUs, mock-ups and production sheets
- `phil/commerce-product-template-bundle` · 🧪 75% — Product templates in the catalogue and the administration
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
- `phil/licensing-bundle` · 🗓️ planned — Licences for a work or a digital product
- `phil/contracts-bundle` · 🗓️ planned — Contracts generated, sent and tracked
- `phil/crm-lite` · 🗓️ planned — A customer book and the history of exchanges

</details>

<details>
<summary><b>Places, contacts &amp; directories</b> — ✅ 2 · 🧪 10 · 🗓️ 4</summary>

- [`phil/phone`](https://github.com/parler-haut-interagir-librement/phone) · ✅ released ([Packagist](https://packagist.org/packages/phil/phone)) — Phone numbers read as typed, checked against their country's plan, and formatted
- [`phil/phone-bundle`](https://github.com/parler-haut-interagir-librement/phone-bundle) · ✅ released ([Packagist](https://packagist.org/packages/phil/phone-bundle)) — A phone field, a constraint, a column type and Twig filters
- `phil/address` · 🧪 95% — Postal addresses checked and written the way each country writes them
- `phil/address-bundle` · 🧪 95% — An address form whose fields follow the chosen country
- `phil/contact` · 🧪 85% — Contact cards for people and organisations, as vCard or JSON-LD
- `phil/contact-bundle` · 🧪 95% — A contact card form, a JSON column and vCard downloads
- `phil/contact-form-bundle` · 🧪 95% — A "write to us" page, protected from spam without a CAPTCHA
- `phil/geo` · 🧪 95% — Coordinates, distances and bounding boxes as values, geocoding through the provider you pick
- `phil/geo-bundle` · 🧪 95% — Stored coordinates, distances in Twig, geocoders and nearest-first lists
- `phil/opening-hours` · 🧪 95% — A place's opening hours, and whether it is open right now
- `phil/opening-hours-bundle` · 🧪 95% — An opening-hours form, a JSON column and localised hours in Twig
- `phil/directory-bundle` · 🧪 90% — A directory of listings that members write and administrators publish
- `phil/map-bundle` · 🗓️ planned — Leaflet maps in Stimulus, on tracking-free tiles
- `phil/contact-sync` · 🗓️ planned — Contact synchronisation over CardDAV
- `phil/portfolio-bundle` · 🗓️ planned — A portfolio, one listing per project
- `phil/library-bundle` · 🗓️ planned — A game or book library: catalogue, loans, returns

</details>

<details>
<summary><b>Operations &amp; administration</b> — 🧪 9 · 🗓️ 13</summary>

- `phil/migration` · 🧪 90% — Release notes and news that Doctrine migrations send to chat
- `phil/migration-bundle` · 🧪 90% — Each migration run announced once on your chat channels
- `phil/backup-bundle` · 🧪 93% — Backups and guarded restores: database, media, encryption, rotation
- `phil/backup` · 🧪 96% — Back up a database and its media, encrypted and rotated, and prove they restore
- `phil/monitoring-bundle` · 🧪 90% — Health checks, maintenance mode, uptime, cron and queue health
- `phil/error-tracking` · 🧪 88% — Self-hosted error tracking, written from scratch
- `phil/error-tracking-bundle` · 🧪 82% — Error tracking in Symfony: groups, regressions by release, alerts through a queue
- `phil/reporting-bundle` · 🧪 90% — Dashboards in Twig components, accessible charts, scheduled reports
- `phil/settings-bundle` · 🧪 88% — Settings that users change themselves
- `phil/sites-console-bundle` · 🗓️ planned — Run several sites: versions, health, shared configuration, admin accounts
- `phil/status-page-bundle` · 🗓️ planned — A service status page
- `phil/performance-budget` · 🗓️ planned — A performance budget checked in CI
- `phil/broken-flow-alerts` · 🗓️ planned — Alerts when a user journey stops completing
- `phil/bulk-actions` · 🗓️ planned — Bulk actions in an administration
- `phil/admin-notes` · 🗓️ planned — Internal admin notes on a record
- `phil/config-ui` · 🗓️ planned — Site configuration edited in the administration
- `phil/sandbox-preview` · 🗓️ planned — Preview a change in a sandbox before it goes live
- `phil/duplicate-detector` · 🗓️ planned — Detect and merge duplicate records
- `phil/dependency-report` · 🗓️ planned — A package's or site's dependencies and their licences
- `phil/secrets-rotation` · 🗓️ planned — Rotate an application's secrets
- `phil/helpdesk-bundle` · 🗓️ planned — A help desk: requests, queues, canned replies
- `phil/automations` · 🗓️ planned — No-code automations triggered by site events

</details>

<details>
<summary><b>Integrations &amp; AI</b> — 🧪 1 · 🗓️ 6</summary>

- `phil/ai-bundle` · 🧪 70% — Language-model tasks that propose and never impose, counted to the token, forgetful of every word
- `phil/mcp-bundle` · 🗓️ planned — An MCP server on Symfony AI, within the user's rights, audited
- `phil/discord-community` · 🗓️ planned — Link a community to its Discord server: roles, events, announcements
- `phil/discord-interactions-bundle` · 🗓️ planned — Ed25519-signed Discord interactions: commands, deferred replies
- `phil/slack-interactions-bundle` · 🗓️ planned — Signed Slack commands and interactions
- `phil/notion` · 🗓️ planned — Read and write Notion databases, text converted to UJO (Universal JSON Output)
- `phil/logseq` · 🗓️ planned — Read and write a Logseq graph

</details>

<details>
<summary><b>UX &amp; interface</b> — 🧪 7 · 🗓️ 8</summary>

- `phil/ux-bundle` · 🧪 36% — PHIL UX components, being rewritten as a kit for the Symfony UX Toolkit and the phil-ux CSS
- `phil/ux-css` · 🧪 52% — phil-ux, the CSS framework: OKLCH tokens, light and dark themes, classless elements, layout utilities
- `phil/ux-kit` · 🧪 22% — The PHIL UX kit for the Symfony UX Toolkit: Logo, AnimatedHeadline, Illustration and the ComingSoon block so far
- `phil/ux-kit-shadcn` · 🧪 31% — Tailwind versions, in the Shadcn style, of the recipes PHIL UX adds
- `phil/forms-bundle` · 🧪 90% — Forms defined in the database, entries kept only as long as needed
- `phil/menu-bundle` · 🧪 95% — Navigation menus and breadcrumbs, with the current page marked
- `phil/forms-autosave` · 🧪 90% — Form input saved as you go
- `phil/data-table-bundle` · 🗓️ planned — Live Component tables: sorting, filters, inline editing, stacked on mobile
- `phil/forms-signature` · 🗓️ planned — A handwritten or electronic signature field
- `phil/pwa-bundle` · 🗓️ planned — Installable, offline-readable sites: manifest, service worker, full screen
- `phil/theme-builder` · 🗓️ planned — Build a theme from PHIL UX tokens
- `phil/page-builder` · 🗓️ planned — Pages composed of blocks, without code
- `phil/landing-pages` · 🗓️ planned — Landing pages composed in the administration
- `phil/menu-builder-ui` · 🗓️ planned — Edit menus with the mouse
- `phil/announcement-bar` · 🗓️ planned — A site announcement bar

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
- **L'outillage** qui vérifie chaque paquet : `phil/dev-tools` et les squelettes de projet.

[ph-il.ca](https://ph-il.ca) présente la plateforme et deviendra le catalogue des modules : une page par paquet,
générée de son README et de sa documentation, en anglais et en français.

Les paquets de jeu et de ludification — dés, générateurs, points, badges, quêtes et le reste — vivent à côté, chez
[Tilttek](https://github.com/TiltTek).

### Pourquoi

Boutiques, conventions, clubs, éditeurs et communautés en ligne ont sans cesse besoin des mêmes briques : un
catalogue et une caisse, un calendrier, un forum, une infolettre, une politique de confidentialité vraiment
appliquée. Nous préférons écrire chaque brique une fois, avec soin et à découvert, plutôt que recoller les mêmes
morceaux sur chaque site. Et nous préférons vous dire franchement où en est chacune : **aujourd'hui, 28 paquets
sont publiés ; les autres sont en écriture ou prévus, et suivent par petits groupes quotidiens.**

### Principes

- **Écrit de zéro.** Aucun code tiers n'est copié dans un paquet PHIL. D'autres projets sont étudiés pour leurs
  idées, jamais recopiés.
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
| [ux-kit](https://github.com/parler-haut-interagir-librement/ux-kit) | Le kit PHIL UX : les mêmes recettes que le kit Shadcn du Toolkit — noms, props, blocs Twig, contrôleurs Stimulus — avec un HTML et un CSS écrits de zéro, habillés par phil-ux. `php bin/console ux:install <recette> --kit=github.com/parler-haut-interagir-librement/ux-kit` | 🧪 incubation, ~10 % |
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
  la matrice des versions de PHP et de Symfony ; et le squelette d'un nouveau paquet. Publié sous licence MIT :
  [dev-tools](https://github.com/parler-haut-interagir-librement/dev-tools).
- **Les squelettes de projet** — [MicroSymfony](https://github.com/parler-haut-interagir-librement/MicroSymfony)
  (issu de `strangebuzz/MicroSymfony`) et [WebSymfony](https://github.com/parler-haut-interagir-librement/WebSymfony).

### Les paquets

✅ **publié** · 🧪 **écrit, en incubation** (avancement approximatif) · 🗓️ **prévu**

**339 paquets :** 28 publiés, 127 en incubation, 184 prévus. Les pourcentages sont des estimations
tirées de notre dernier rapport d'avancement (8 novembre 2026). Les paquets publiés sont développés dans le monodépôt
public [`phil`](https://github.com/parler-haut-interagir-librement/phil), scindés chacun dans son propre dépôt en
lecture seule et publiés sur Packagist ; `phil/enums` poursuit
[`ph-il/enums`](https://packagist.org/packages/ph-il/enums). **La vitrine se poursuit par petits groupes
quotidiens** de deux à quatre paquets, les dépendances d'abord.
`phil/identity-provider-*` désigne un paquet par fournisseur de connexion.

<details>
<summary><b>Données et infrastructure</b> — ✅ 12 · 🧪 20 · 🗓️ 9</summary>

- [`phil/enums`](https://github.com/parler-haut-interagir-librement/enums) · ✅ publié ([Packagist](https://packagist.org/packages/phil/enums)) — Traits et attributs pour lister, comparer, décrire et regrouper les enums PHP (anciennement `ph-il/enums`)
- [`phil/enums-bundle`](https://github.com/parler-haut-interagir-librement/enums-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/enums-bundle)) — Les enums dans les formulaires, traductions, Twig, la validation, Doctrine et les contrats d'API de Symfony
- [`phil/resource`](https://github.com/parler-haut-interagir-librement/resource) · ✅ publié ([Packagist](https://packagist.org/packages/phil/resource)) — Désigner n'importe quel enregistrement par sa sorte et son identifiant, comme `page:42`
- [`phil/ddd-bundle`](https://github.com/parler-haut-interagir-librement/ddd-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ddd-bundle)) — Types de domaine communs : identifiants, événements, erreurs, bus de commandes et de requêtes
- [`phil/slug`](https://github.com/parler-haut-interagir-librement/slug) · ✅ publié ([Packagist](https://packagist.org/packages/phil/slug)) — Des slugs d'URL tirés des titres et des noms, en type qui n'accepte rien d'autre
- [`phil/slug-bundle`](https://github.com/parler-haut-interagir-librement/slug-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/slug-bundle)) — Des générateurs de slugs nommés en configuration, injectés et utilisables dans Twig
- [`phil/recurrence`](https://github.com/parler-haut-interagir-librement/recurrence) · ✅ publié ([Packagist](https://packagist.org/packages/phil/recurrence)) — Des dates répétées par les règles RFC 5545 : lire, vérifier, écrire, énumérer les occurrences
- [`phil/recurrence-bundle`](https://github.com/parler-haut-interagir-librement/recurrence-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/recurrence-bundle)) — Un formulaire d'événements répétés, une colonne pour la règle, et la règle en toutes lettres
- [`phil/standard-webhooks`](https://github.com/parler-haut-interagir-librement/standard-webhooks) · ✅ publié ([Packagist](https://packagist.org/packages/phil/standard-webhooks)) — Signer et vérifier des webhooks selon la spécification Standard Webhooks
- [`phil/standard-webhooks-bundle`](https://github.com/parler-haut-interagir-librement/standard-webhooks-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/standard-webhooks-bundle)) — Les livraisons de webhooks vérifiées en arguments de contrôleur, et l'envoi de webhooks signés
- [`phil/circuit-breaker`](https://github.com/parler-haut-interagir-librement/circuit-breaker) · ✅ publié ([Packagist](https://packagist.org/packages/phil/circuit-breaker)) — Un seul disjoncteur pour les clients HTTP et les drapeaux de fonctions
- [`phil/circuit-breaker-bundle`](https://github.com/parler-haut-interagir-librement/circuit-breaker-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/circuit-breaker-bundle)) — Le disjoncteur branché dans les clients HTTP et les drapeaux de fonctions de Symfony
- `phil/doctrine-behaviours` · 🧪 55 % — Horodatage, auteur, suppression douce et arbres pour les entités Doctrine, chacun sur option
- `phil/doctrine-behaviours-bundle` · 🧪 60 % — Les comportements d'entité activés par configuration dans Symfony
- `phil/url` · 🧪 95 % — Des adresses Web en valeurs normalisées, leur sorte détectée : Mastodon, YouTube, un site
- `phil/url-bundle` · 🧪 95 % — Des champs de lien qui détectent leur sorte, une contrainte, un type de colonne et des filtres Twig
- `phil/references-bundle` · 🧪 95 % — Savoir où chaque ressource est employée, et refuser d'effacer celle qui sert encore
- `phil/trash-bundle` · 🧪 95 % — Une corbeille pour les ressources effacées : les restaurer, ou les purger après un délai
- `phil/almanac` · 🧪 85 % — Pâques, phases de la Lune, saisons et dates en toutes lettres, pour toute année
- `phil/almanac-bundle` · 🧪 90 % — Fériés et dates calculées en configuration, modifiables, montrés dans Twig
- `phil/scheduled-transitions-bundle` · 🧪 95 % — Publier et retirer à heure fixe, sans personne en ligne
- `phil/tenancy-bundle` · 🧪 65 % — Le locataire où agit un compte, changé à l'instant et appliqué à chaque requête
- `phil/feature-flags-bundle` · 🧪 90 % — Couper une fonction sans déploiement, mener un test A/B, cesser d'appeler un service en panne
- `phil/usage-meter` · 🧪 90 % — Mesurer ce que chacun a consommé et refuser une action au-delà de son quota
- `phil/http-cache-tags-bundle` · 🧪 95 % — Mettre des pages entières en cache Varnish ou CDN, purger exactement ce qu'une modification change
- `phil/api-contract` · 🧪 70 % — Détails de problème, signaux de dépréciation et clés d'idempotence pour les API HTTP
- `phil/api-contract-bundle` · 🧪 90 % — Détails de problème, requêtes idempotentes rejouées et avis de dépréciation dans Symfony
- `phil/usage-meter-bundle` · 🧪 93 % — Compteurs d'usage stockés par DBAL, limiteurs de débit et commandes de purge
- `phil/encrypted-fields` · 🧪 92 % — Colonnes Doctrine chiffrées par libsodium, index aveugles, rotation des clés
- `phil/encrypted-fields-bundle` · 🧪 85 % — Les champs chiffrés configurés dans Symfony, clés dans les secrets ou un KMS
- `phil/rate-limit-bundle` · 🧪 92 % — Limites de débit déclarées par attribut sur les routes, formulaires et API
- `phil/api-keys-bundle` · 🧪 88 % — Jetons d'accès personnels pour une API publique : portées, expiration, révocation, quotas
- `phil/idempotency` · 🗓️ prévu — Clés d'idempotence pour les API, Messenger, les webhooks de paiement et les doubles envois
- `phil/console-bundle` · 🗓️ prévu — Garde-fous de console par environnement et sortie horodatée
- `phil/spreadsheet` · 🗓️ prévu — Lire et écrire XLSX, ODS et CSV
- `phil/import-wizard` · 🗓️ prévu — L'import guidé d'un fichier, colonne par colonne
- `phil/json-canvas` · 🗓️ prévu — Lire et écrire le format ouvert JSON Canvas
- `phil/open-data` · 🗓️ prévu — Publier les données ouvertes d'un site
- `phil/number-words` · 🗓️ prévu — Les nombres en toutes lettres, dans toutes les langues
- `phil/natural-dates` · 🗓️ prévu — Une date écrite en mots (« jeudi prochain 19 h ») comprise dans chaque langue
- `phil/timezone-display` · 🗓️ prévu — Une heure affichée dans le fuseau du visiteur

</details>

<details>
<summary><b>Contenu et texte</b> — ✅ 6 · 🧪 15 · 🗓️ 20</summary>

- [`phil/ujo`](https://github.com/parler-haut-interagir-librement/ujo) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ujo)) — Des documents UJO (Universal JSON Output) lus strictement, vérifiés bloc par bloc, rendus en HTML sûr
- [`phil/ujo-bundle`](https://github.com/parler-haut-interagir-librement/ujo-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/ujo-bundle)) — Les documents UJO (Universal JSON Output) dans Doctrine, les formulaires et Twig
- [`phil/text-diff`](https://github.com/parler-haut-interagir-librement/text-diff) · ✅ publié ([Packagist](https://packagist.org/packages/phil/text-diff)) — Ce qui a changé entre deux textes, mot à mot, paragraphe par paragraphe ou bloc par bloc
- [`phil/highlight`](https://github.com/parler-haut-interagir-librement/highlight) · ✅ publié ([Packagist](https://packagist.org/packages/phil/highlight)) — Du code en 24 langages coloré au serveur, en HTML simple que toute feuille de style habille
- [`phil/css-sanitizer`](https://github.com/parler-haut-interagir-librement/css-sanitizer) · ✅ publié ([Packagist](https://packagist.org/packages/phil/css-sanitizer)) — Laisser les gens habiller leurs pages sans que leur CSS exécute du code, charge ce qu'il ne doit pas ou sorte de son cadre
- [`phil/highlight-bundle`](https://github.com/parler-haut-interagir-librement/highlight-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/highlight-bundle)) — La coloration branchée dans le rendu UJO (Universal JSON Output) et dans Twig, avec un thème
- `phil/content-bundle` · 🧪 88 % — Pages et articles gardés par langue, étape et version, publiés du brouillon à la mise en ligne
- `phil/markup` · 🧪 87 % — Markdown, BBCode, MediaWiki, DokuWiki, Creole, HTML ou texte brut rendus en HTML sûr
- `phil/markup-bundle` · 🧪 93 % — Les formats de balisage rendus sans danger dans Twig et convertis en UJO (Universal JSON Output), en services Symfony
- `phil/block-editor-bundle` · 🧪 90 % — Un éditeur par blocs pour les formulaires Symfony, en Stimulus, qui écrit de l'UJO (Universal JSON Output) vérifié au serveur
- `phil/edit-lock-bundle` · 🧪 94 % — Un seul rédacteur par bloc : baux d'édition, présence et enregistrements poussés par Mercure
- `phil/comments-bundle` · 🧪 83 % — Commentaires et suggestions ancrés à des passages, qui suivent le texte quand il change
- `phil/taxonomy-bundle` · 🧪 95 % — Étiquettes et arbre de catégories traduit pour toute ressource, avec leurs types de formulaire
- `phil/svg-sanitizer` · 🧪 94 % — Purifier le SVG : liste blanche d'éléments et d'attributs, ni script ni référence externe
- `phil/latex-mathml` · 🧪 80 % — Des formules LaTeX converties, au serveur, en MathML que les navigateurs dessinent
- `phil/svg-chart` · 🧪 90 % — Des graphiques dessinés en SVG au serveur, d'après la configuration qu'écrit déjà un éditeur de graphiques
- `phil/svg-blocks` · 🧪 90 % — Les formules, schémas, graphiques et codes QR des documents par blocs, dessinés une fois au serveur
- `phil/svg-blocks-bundle` · 🧪 85 % — Les dessins des blocs faits à l'enregistrement dans Symfony, Mermaid dans un conteneur
- `phil/text-diff-bundle` · 🧪 90 % — La comparaison de textes dans Twig et Stimulus
- `phil/content-warnings` · 🧪 95 % — Avertissements de contenu pour jeux, livres, articles et événements, sur une liste de base traduite
- `phil/content-warnings-bundle` · 🧪 90 % — Les avertissements de contenu dans les formulaires, les pages et les filtres
- `phil/wiki-bundle` · 🗓️ prévu — Un wiki collaboratif : pages, révisions comparées, liens `[[ ]]`, verrous par bloc
- `phil/faq-bundle` · 🗓️ prévu — Les questions fréquentes par section, cherchables, en données structurées
- `phil/glossary-bundle` · 🗓️ prévu — Un glossaire dont les termes se lient seuls dans les textes
- `phil/timeline-bundle` · 🗓️ prévu — Des lignes du temps de contenus datés
- `phil/series-bundle` · 🗓️ prévu — Les séries de contenus
- `phil/footnotes-sidenotes` · 🗓️ prévu — Notes de bas de page et notes en marge
- `phil/citations` · 🗓️ prévu — Citations et bibliographie dans les styles courants
- `phil/credits` · 🗓️ prévu — La page des crédits d'une œuvre : contributeurs, rôles, ordre
- `phil/math` · 🗓️ prévu — Formules mathématiques rendues en MathML
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

</details>

<details>
<summary><b>Langues, traduction et typographie</b> — ✅ 2 · 🧪 2 · 🗓️ 2</summary>

- [`phil/typography`](https://github.com/parler-haut-interagir-librement/typography) · ✅ publié ([Packagist](https://packagist.org/packages/phil/typography)) — Vrais guillemets, tirets, espaces françaises et césure dans votre HTML, dans toutes les langues
- [`phil/typography-bundle`](https://github.com/parler-haut-interagir-librement/typography-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/typography-bundle)) — La typographie partout où une application Symfony écrit du texte
- `phil/translation-bundle` · 🧪 83 % — Un écran de traduction : segments qui survivent aux modifications, mémoire et glossaire qui vérifie
- `phil/translation-memory` · 🧪 87 % — Traduction par segments qui réutilise l'acquis et garde les termes constants
- `phil/machine-translation` · 🗓️ prévu — Des traductions proposées par la machine, toujours relues
- `phil/translation-ui` · 🗓️ prévu — L'interface de traduction des contenus et des messages d'un site

</details>

<details>
<summary><b>Médias, documents et impression</b> — ✅ 1 · 🧪 13 · 🗓️ 11</summary>

- [`phil/qr-code`](https://github.com/parler-haut-interagir-librement/qr-code) · ✅ publié ([Packagist](https://packagist.org/packages/phil/qr-code)) — Des codes QR écrits de zéro, Reed-Solomon compris, en SVG et PNG
- `phil/media-bundle` · 🧪 80 % — Fichiers et images téléversés, décrits, versionnés et servis à des URL signées
- `phil/document-import` · 🧪 73 % — Documents de traitement de texte, Markdown et HTML convertis en UJO (Universal JSON Output), avec le relevé de ce qui n'a pas passé
- `phil/epub` · 🧪 85 % — Des livres EPUB 3 tirés de votre HTML, valides pour EPUBCheck et lisibles par les aides techniques
- `phil/fonts` · 🧪 95 % — Ce qu'un fichier de police dit de lui-même — noms, graisse, licence d'intégration — et sa règle `@font-face`
- `phil/paged-media` · 🧪 68 % — Des PDF depuis PHP, avec de vraies polices et des moteurs HTML/CSS paginés
- `phil/paged-media-bundle` · 🧪 90 % — Les PDF dans Symfony, par un écrivain natif ou Gotenberg, par un seul service, tout de suite ou par Messenger
- `phil/print-preflight` · 🧪 82 % — Repérer ce qu'un imprimeur refuserait avant que le fichier lui parvienne
- `phil/document-import-bundle` · 🧪 90 % — L'import de documents branché dans la médiathèque
- `phil/fonts-bundle` · 🧪 95 % — Les polices configurées pour le PDF et les médias
- `phil/epub-bundle` · 🧪 95 % — La génération d'EPUB dans Symfony
- `phil/print-preflight-bundle` · 🧪 90 % — Le contrôle prépresse branché dans la génération de PDF
- `phil/print-compositor` · 🧪 90 % — Maquettes de vêtements et fichiers d'impression, une couche par encre
- `phil/qr-code-bundle` · 🧪 88 % — Les codes QR dans Twig, les routes et les contenus typés (URL, vCard, Wi-Fi, iCalendar)
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

</details>

<details>
<summary><b>Recherche, référencement et Web ouvert</b> — 🧪 10 · 🗓️ 11</summary>

- `phil/search-bundle` · 🧪 70 % — La recherche plein texte dans vos ressources, tenue à jour à chaque flush de Doctrine
- `phil/search-loupe` · 🧪 90 % — Une recherche tolérante aux fautes dans des fichiers SQLite, sans serveur
- `phil/sitemap` · 🧪 95 % — Des plans de site XML bâtis de pages vérifiées, coupés aux limites du protocole
- `phil/sitemap-bundle` · 🧪 96 % — `/sitemap.xml` tiré des options de route, de fournisseurs d'URL et d'un événement
- `phil/social-cards` · 🧪 88 % — Balises Open Graph et images de partage générées
- `phil/social-cards-bundle` · 🧪 87 % — Les métadonnées de partage et les cartes générées dans Symfony, avec l'aperçu des liens entrants
- `phil/structured-data` · 🧪 92 % — Le graphe schema.org d'une page, assemblé de morceaux JSON-LD
- `phil/structured-data-bundle` · 🧪 88 % — Le graphe schema.org d'une page dans Symfony, avec une commande qui le vérifie
- `phil/redirects-bundle` · 🧪 90 % — Redirections 301 gérées, suivi des 404, anciens domaines
- `phil/well-known-bundle` · 🧪 90 % — Les adresses `/.well-known/` : security.txt, change-password, WebFinger, nodeinfo
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

</details>

<details>
<summary><b>Identité, accès et sécurité</b> — ✅ 3 · 🧪 7 · 🗓️ 10</summary>

- [`phil/bot-detection-bundle`](https://github.com/parler-haut-interagir-librement/bot-detection-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/bot-detection-bundle)) — Distinguer un robot d'un humain dans le navigateur, sans CAPTCHA
- [`phil/spam-protection`](https://github.com/parler-haut-interagir-librement/spam-protection) · ✅ publié ([Packagist](https://packagist.org/packages/phil/spam-protection)) — Repérer le pourriel d'un formulaire sans CAPTCHA, en PHP simple
- [`phil/spam-protection-bundle`](https://github.com/parler-haut-interagir-librement/spam-protection-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/spam-protection-bundle)) — Garder le pourriel hors des formulaires Symfony sans CAPTCHA, ni tiers, ni identifiant
- `phil/user-secrets-bundle` · 🧪 80 % — Les clés que les gens prêtent à votre application, scellées et à eux seuls
- `phil/passwords` · 🧪 90 % — Une jauge de robustesse écrite de zéro, vérification des fuites par k-anonymat, génération
- `phil/csp-bundle` · 🧪 92 % — La politique de sécurité du contenu, ses nonces et ses rapports
- `phil/route-access-check` · 🧪 90 % — Faire échouer la CI quand une route n'a pas de règle d'accès
- `phil/route-access-check-bundle` · 🧪 90 % — Le contrôle d'accès des routes en commande Symfony, avec baseline et mode strict
- `phil/upload-scan` · 🧪 92 % — L'antivirus des téléversements derrière un port
- `phil/upload-scan-bundle` · 🧪 88 % — L'analyse des téléversements dans Symfony : contrainte de fichier, quarantaine et nouvelles analyses
- `phil/identity-provider-bundle` · 🗓️ prévu — Un fournisseur OpenID Connect écrit de zéro : passkeys, mots de passe, TOTP, step-up
- `phil/identity-provider-*` · 🗓️ prévu — Un paquet par fournisseur de connexion fédérée, de Google à Bluesky
- `phil/identity-client-bundle` · 🗓️ prévu — Brancher un site Symfony à un fournisseur OpenID, sur `oidc_login` de Symfony 8.2
- `phil/organizations-bundle` · 🗓️ prévu — Organisations, rôles et invitations
- `phil/access-bundle` · 🗓️ prévu — Les droits d'accès par site
- `phil/webauthn-step-up` · 🗓️ prévu — Confirmer une action sensible par une clé d'accès
- `phil/fraud-signals` · 🗓️ prévu — Les signaux de fraude d'une commande ou d'une inscription
- `phil/trust-levels` · 🗓️ prévu — Des niveaux de confiance qui ouvrent des droits avec l'activité
- `phil/verification-marks` · 🗓️ prévu — La marque d'un compte vérifié
- `phil/invitations` · 🗓️ prévu — L'invitation d'une personne par un membre, avec ses limites

</details>

<details>
<summary><b>Vie privée, accessibilité et conformité</b> — 🧪 5 · 🗓️ 7</summary>

- `phil/privacy-bundle` · 🧪 62 % — Déclarer les champs personnels, caviarder les journaux, répondre aux demandes d'accès et d'effacement (Loi 25, RGPD)
- `phil/analytics-bundle` · 🧪 85 % — Les visites comptées en agrégats quotidiens, jamais liées à une personne
- `phil/audit-bundle` · 🧪 60 % — Un journal d'audit en ajout seul, qui montre toute altération et permet quand même d'effacer les renseignements personnels
- `phil/ip-anonymizer` · 🧪 95 % — Tronquer, hacher avec sel et généraliser les adresses IP
- `phil/accessibility-check` · 🧪 90 % — Le contrôle d'accessibilité à la publication : textes de remplacement, ordre des titres, contraste
- `phil/legal-notices` · 🗓️ prévu — Les mentions légales et la politique de confidentialité d'un site
- `phil/terms-bundle` · 🗓️ prévu — Des conditions d'utilisation versionnées et leur acceptation
- `phil/accessibility-statement` · 🗓️ prévu — La déclaration d'accessibilité d'un site
- `phil/accessibility-info` · 🗓️ prévu — Les renseignements d'accessibilité d'un lieu ou d'un événement
- `phil/easy-read` · 🗓️ prévu — La version en langage simplifié d'un contenu, et sa vérification
- `phil/age-gate` · 🗓️ prévu — La vérification d'âge déclarative d'un contenu ou d'une annonce
- `phil/heatmaps` · 🗓️ prévu — Des cartes de chaleur agrégées, sans identifiant

</details>

<details>
<summary><b>Communauté</b> — 🧪 3 · 🗓️ 32</summary>

- `phil/poll-bundle` · 🧪 85 % — Le moteur de vote : choix unique, multiple ou classé
- `phil/poll` · 🧪 90 % — Un moteur de vote : des bulletins vérifiés selon les règles de leur scrutin, comptés en classements
- `phil/listings` · 🧪 90 % — Le noyau des annonces : critères, expiration, réponses, modération
- `phil/forum-bundle` · 🗓️ prévu — Des forums par section, leur clavardage, le signalement et la modération par section
- `phil/moderation-bundle` · 🗓️ prévu — Une seule file de signalements pour forums, commentaires, réactions, annonces et messages
- `phil/reactions-bundle` · 🗓️ prévu — Les réactions à un contenu, une par membre, liste choisie par site
- `phil/mentions-bundle` · 🗓️ prévu — Les @mentions dans un texte, et leur notification
- `phil/follow-bundle` · 🗓️ prévu — Suivre un contenu, un fil, une fiche ou un membre
- `phil/conversation-bundle` · 🗓️ prévu — Les messages privés à deux ou en groupe, chiffrés au repos
- `phil/groups-bundle` · 🗓️ prévu — Des groupes de membres
- `phil/profiles-bundle` · 🗓️ prévu — La page publique d'un membre : ce qu'il y montre, et à qui
- `phil/reviews-bundle` · 🗓️ prévu — Avis et notes modérés sur un produit, un jeu ou un lieu
- `phil/survey-bundle` · 🗓️ prévu — Des questionnaires à sections et à logique conditionnelle
- `phil/ideas-bundle` · 🗓️ prévu — Une boîte à idées avec statuts et votes
- `phil/qa-bundle` · 🗓️ prévu — Des questions et leurs réponses, la meilleure acceptée
- `phil/code-of-conduct` · 🗓️ prévu — Un code de conduite, son acceptation et ses signalements
- `phil/onboarding-bundle` · 🗓️ prévu — L'accueil d'un nouveau membre : étapes, visite guidée, liste à cocher
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

</details>

<details>
<summary><b>Apprentissage et attestations</b> — 🧪 3 · 🗓️ 2</summary>

- `phil/open-badges` · 🧪 90 % — Émettre, signer, vérifier, cuire et révoquer des justificatifs Open Badges 3.0
- `phil/open-badges-bundle` · 🧪 85 % — Profil de l'émetteur, clé publique et page de vérification des Open Badges
- `phil/certificates-bundle` · 🧪 85 % — Des certificats vérifiables : critères, PDF à code QR, registre public
- `phil/courses-bundle` · 🗓️ prévu — Des cours en ligne : modules, leçons, progression
- `phil/mentoring-bundle` · 🗓️ prévu — Le mentorat : jumelage, séances, suivi

</details>

<details>
<summary><b>Notifications, courriel et messagerie</b> — 🧪 5 · 🗓️ 10</summary>

- `phil/instant-messenger` · 🧪 95 % — Les identifiants de messagerie par service : WhatsApp, Telegram, Signal, Matrix et d'autres
- `phil/instant-messenger-bundle` · 🧪 95 % — Un champ d'identifiant de messagerie, une contrainte et des filtres Twig
- `phil/notifications-bundle` · 🧪 80 % — Toasts, centre de notifications, résumés par courriel, Web Push, Discord ou Slack
- `phil/bounce-parser` · 🧪 90 % — Lire les rebonds DSN et ARF et les réponses automatiques
- `phil/email-address` · 🧪 85 % — La validation des adresses de courriel
- `phil/newsletter-bundle` · 🗓️ prévu — L'infolettre : listes, double inscription, gabarits, envoi par Symfony Mailer
- `phil/newsletter-archive` · 🗓️ prévu — L'archive publique des infolettres envoyées
- `phil/email-automation` · 🗓️ prévu — Séquences et déclencheurs d'infolettre, jamais sur une ouverture
- `phil/email-templates-bundle` · 🗓️ prévu — Des gabarits de courriel partagés entre plusieurs sites, à blocs conditionnels
- `phil/email-preview` · 🗓️ prévu — L'aperçu des gabarits de courriel
- `phil/mail-auth-check` · 🗓️ prévu — Tester SPF, DKIM et DMARC d'un domaine d'envoi
- `phil/inbound-mail-bundle` · 🗓️ prévu — Le courrier entrant, analysé et routé
- `phil/sms-bundle` · 🗓️ prévu — Envoyer et recevoir des SMS sur Symfony Notifier
- `phil/audience-segments` · 🗓️ prévu — Des segments d'audience définis par des règles, pour l'infolettre et les notifications
- `phil/live-chat` · 🗓️ prévu — Le clavardage en direct avec un visiteur

</details>

<details>
<summary><b>Événements, calendrier et réservation</b> — 🧪 5 · 🗓️ 19</summary>

- `phil/calendar-bundle` · 🧪 61 % — Des événements, répétés ou non, en mois, semaine, jour, liste ou affiches
- `phil/reservation` · 🧪 90 % — Le noyau de réservation : ressources, créneaux, règles, conflits et rappels
- `phil/reservation-bundle` · 🧪 85 % — Les réservations dans Symfony : ressources, plages, conflits et rappels
- `phil/checkin-bundle` · 🧪 85 % — Le noyau d'accueil commun : billet ou inscription lus, présence notée
- `phil/checkin` · 🧪 92 % — Un code lu à une porte, décidé aussitôt, noté une fois, en ligne ou hors ligne
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

</details>

<details>
<summary><b>Commerce</b> — ✅ 2 · 🧪 12 · 🗓️ 20</summary>

- [`phil/money`](https://github.com/parler-haut-interagir-librement/money) · ✅ publié ([Packagist](https://packagist.org/packages/phil/money)) — Des montants en entiers exacts dans une devise connue, sans aucun nombre flottant
- [`phil/money-bundle`](https://github.com/parler-haut-interagir-librement/money-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/money-bundle)) — L'argent dans les formulaires, la validation, Twig et Doctrine de Symfony, sans flottants
- `phil/tax` · 🧪 95 % — Plusieurs taxes sur une vente, détaillées au cent
- `phil/commerce-bundle` · 🧪 87 % — Commandes, prix, taxes, paiements et reçus pour une boutique Symfony, avec des modules par-dessus
- `phil/commerce-catalog-bundle` · 🧪 55 % — Produits, listes de prix et promotions
- `phil/commerce-logistics-bundle` · 🧪 77 % — Stock par emplacement, réservations, colis et modes de livraison par zone
- `phil/commerce-pos-bundle` · 🧪 80 % — Une caisse pour la vente au comptoir : tiroirs, quarts, comptes de caisse, mises de côté, ventes hors ligne
- `phil/commerce-returns-bundle` · 🧪 82 % — Les retours, de l'autorisation au remboursement, au crédit ou à l'échange, ligne par ligne
- `phil/commerce-stored-value-bundle` · 🧪 85 % — Cartes-cadeaux numériques et crédit en boutique, dépensés comme paiements d'une commande
- `phil/commerce-subscription-bundle` · 🧪 80 % — Offres récurrentes par paliers : essais, renouvellement, relances et fonctions débloquées
- `phil/commerce-syndication-bundle` · 🧪 85 % — Revendre les produits d'une autre boutique, commandes transmises au fournisseur qui expédie
- `phil/commerce-wholesale-bundle` · 🧪 90 % — Groupes de clients à prix et minimums propres, ventes à crédit à terme net
- `phil/commerce-product-template` · 🧪 90 % — Des gabarits de produit qui génèrent combinaisons, SKU, maquettes et bons de production
- `phil/commerce-product-template-bundle` · 🧪 75 % — Les gabarits de produit dans le catalogue et l'administration
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
- `phil/licensing-bundle` · 🗓️ prévu — Les licences d'une œuvre ou d'un produit numérique
- `phil/contracts-bundle` · 🗓️ prévu — Des contrats générés, envoyés et suivis
- `phil/crm-lite` · 🗓️ prévu — Un carnet de clients et l'historique des échanges

</details>

<details>
<summary><b>Lieux, contacts et répertoires</b> — ✅ 2 · 🧪 10 · 🗓️ 4</summary>

- [`phil/phone`](https://github.com/parler-haut-interagir-librement/phone) · ✅ publié ([Packagist](https://packagist.org/packages/phil/phone)) — Des numéros de téléphone lus comme on les tape, vérifiés selon le plan de leur pays, et formatés
- [`phil/phone-bundle`](https://github.com/parler-haut-interagir-librement/phone-bundle) · ✅ publié ([Packagist](https://packagist.org/packages/phil/phone-bundle)) — Un champ de téléphone, une contrainte, un type de colonne et des filtres Twig
- `phil/address` · 🧪 95 % — Des adresses postales vérifiées et écrites comme chaque pays les écrit
- `phil/address-bundle` · 🧪 95 % — Un formulaire d'adresse dont les champs suivent le pays choisi
- `phil/contact` · 🧪 85 % — Fiches de contact de personnes et d'organisations, en vCard ou JSON-LD
- `phil/contact-bundle` · 🧪 95 % — Un formulaire de fiche de contact, une colonne JSON et le téléchargement en vCard
- `phil/contact-form-bundle` · 🧪 95 % — Une page « écrivez-nous », protégée du pourriel sans CAPTCHA
- `phil/geo` · 🧪 95 % — Coordonnées, distances et boîtes englobantes en valeurs, géocodage par le fournisseur choisi
- `phil/geo-bundle` · 🧪 95 % — Coordonnées gardées, distances dans Twig, géocodeurs et listes du plus proche au plus loin
- `phil/opening-hours` · 🧪 95 % — Les heures d'ouverture d'un lieu, et s'il est ouvert en ce moment
- `phil/opening-hours-bundle` · 🧪 95 % — Un formulaire d'heures d'ouverture, une colonne JSON et les heures localisées dans Twig
- `phil/directory-bundle` · 🧪 90 % — Un répertoire de fiches que les membres écrivent et l'administration publie
- `phil/map-bundle` · 🗓️ prévu — Des cartes Leaflet en Stimulus, sur des tuiles sans pistage
- `phil/contact-sync` · 🗓️ prévu — La synchronisation des contacts par CardDAV
- `phil/portfolio-bundle` · 🗓️ prévu — Un portfolio, une fiche par projet
- `phil/library-bundle` · 🗓️ prévu — Une ludothèque ou une bibliothèque : catalogue, prêts, retours

</details>

<details>
<summary><b>Exploitation et administration</b> — 🧪 9 · 🗓️ 13</summary>

- `phil/migration` · 🧪 90 % — Notes de version et nouvelles que les migrations Doctrine envoient au clavardage
- `phil/migration-bundle` · 🧪 90 % — Chaque passage des migrations annoncé une fois sur vos canaux de clavardage
- `phil/backup-bundle` · 🧪 93 % — Sauvegarde et restauration protégée : base, médias, chiffrement, rotation
- `phil/backup` · 🧪 96 % — Sauvegarder une base et ses médias, chiffrés et en rotation, et prouver qu'ils se restaurent
- `phil/monitoring-bundle` · 🧪 90 % — Points de santé, mode maintenance, disponibilité, tâches planifiées et files
- `phil/error-tracking` · 🧪 88 % — Le suivi des erreurs chez soi, écrit de zéro
- `phil/error-tracking-bundle` · 🧪 82 % — Le suivi des erreurs dans Symfony : groupes, régressions par version, alertes par une file
- `phil/reporting-bundle` · 🧪 90 % — Tableaux de bord en composants Twig, graphiques accessibles, rapports planifiés
- `phil/settings-bundle` · 🧪 88 % — Les réglages qu'un usager modifie lui-même
- `phil/sites-console-bundle` · 🗓️ prévu — Gérer plusieurs sites : versions, santé, configuration commune, comptes d'administration
- `phil/status-page-bundle` · 🗓️ prévu — La page d'état des services
- `phil/performance-budget` · 🗓️ prévu — Un budget de performance vérifié en CI
- `phil/broken-flow-alerts` · 🗓️ prévu — L'alerte quand un parcours cesse d'aboutir
- `phil/bulk-actions` · 🗓️ prévu — Les actions en lot dans une administration
- `phil/admin-notes` · 🗓️ prévu — Les notes internes de l'administration sur une fiche
- `phil/config-ui` · 🗓️ prévu — La configuration d'un site éditée dans l'administration
- `phil/sandbox-preview` · 🗓️ prévu — Voir un changement dans un bac à sable avant sa mise en ligne
- `phil/duplicate-detector` · 🗓️ prévu — Détecter et fusionner les fiches en double
- `phil/dependency-report` · 🗓️ prévu — Les dépendances d'un paquet ou d'un site et leurs licences
- `phil/secrets-rotation` · 🗓️ prévu — La rotation des secrets d'une application
- `phil/helpdesk-bundle` · 🗓️ prévu — Un service d'assistance : demandes, files, réponses types
- `phil/automations` · 🗓️ prévu — Des automatisations sans code déclenchées par les événements du site

</details>

<details>
<summary><b>Intégrations et IA</b> — 🧪 1 · 🗓️ 6</summary>

- `phil/ai-bundle` · 🧪 70 % — Des tâches de modèle de langue qui proposent sans imposer, comptées au jeton, sans rien retenir
- `phil/mcp-bundle` · 🗓️ prévu — Un serveur MCP sur Symfony AI, dans les droits de l'usager, audité
- `phil/discord-community` · 🗓️ prévu — Lier une communauté à son serveur Discord : rôles, événements, annonces
- `phil/discord-interactions-bundle` · 🗓️ prévu — Les interactions Discord signées Ed25519 : commandes, réponses différées
- `phil/slack-interactions-bundle` · 🗓️ prévu — Les commandes et interactions Slack signées
- `phil/notion` · 🗓️ prévu — Lire et écrire une base Notion, le texte converti en UJO (Universal JSON Output)
- `phil/logseq` · 🗓️ prévu — Lire et écrire un graphe Logseq

</details>

<details>
<summary><b>UX et interface</b> — 🧪 7 · 🗓️ 8</summary>

- `phil/ux-bundle` · 🧪 36 % — Les composants PHIL UX, en réécriture en kit pour le Toolkit de Symfony UX et en CSS phil-ux
- `phil/ux-css` · 🧪 52 % — phil-ux, le cadre CSS : jetons OKLCH, thèmes clair et sombre, éléments sans classe, utilitaires de mise en page
- `phil/ux-kit` · 🧪 22 % — Le kit PHIL UX pour le Toolkit de Symfony UX : Logo, AnimatedHeadline, Illustration et le bloc ComingSoon pour l'instant
- `phil/ux-kit-shadcn` · 🧪 31 % — Les versions Tailwind, à la façon de Shadcn, des recettes que PHIL UX ajoute
- `phil/forms-bundle` · 🧪 90 % — Des formulaires définis en base, leurs réponses gardées le temps nécessaire seulement
- `phil/menu-bundle` · 🧪 95 % — Menus de navigation et fil d'Ariane, avec la page courante marquée
- `phil/forms-autosave` · 🧪 90 % — La saisie d'un formulaire gardée en cours de route
- `phil/data-table-bundle` · 🗓️ prévu — Des tableaux en Live Component : tri, filtres, édition en ligne, empilés sur mobile
- `phil/forms-signature` · 🗓️ prévu — Un champ de signature manuscrite ou électronique
- `phil/pwa-bundle` · 🗓️ prévu — Des sites installables et lisibles hors ligne : manifeste, service worker, plein écran
- `phil/theme-builder` · 🗓️ prévu — Composer un thème à partir des jetons PHIL UX
- `phil/page-builder` · 🗓️ prévu — Des pages composées de blocs, sans code
- `phil/landing-pages` · 🗓️ prévu — Des pages d'atterrissage composées par l'administration
- `phil/menu-builder-ui` · 🗓️ prévu — L'édition des menus à la souris
- `phil/announcement-bar` · 🗓️ prévu — Le bandeau d'annonce d'un site

</details>


### Participer

- 💬 Questions et idées : [Discussions](https://github.com/orgs/parler-haut-interagir-librement/discussions)
- 🐛 Bogues et demandes de fonctions : un ticket dans le dépôt concerné
- 🤝 [Contribuer](https://github.com/parler-haut-interagir-librement/.github/blob/main/CONTRIBUTING.md) ·
  [Code de conduite](https://github.com/parler-haut-interagir-librement/.github/blob/main/CODE_OF_CONDUCT.md) ·
  [Sécurité](https://github.com/parler-haut-interagir-librement/.github/blob/main/SECURITY.md) ·
  [Soutien](https://github.com/parler-haut-interagir-librement/.github/blob/main/SUPPORT.md)
- ✉️ [info@ph-il.ca](mailto:info@ph-il.ca) · 🌐 [ph-il.ca](https://ph-il.ca)
