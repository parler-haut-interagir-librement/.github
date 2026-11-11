# Contributing to PHIL

Thank you for wanting to help. This guide applies to every repository of the Parler Haut, Interagir Librement (PHIL) organisation that does not
carry its own `CONTRIBUTING.md`.

*Vous pouvez écrire vos tickets et vos discussions en français ou en anglais ; le code, la documentation et les
messages de commit sont en anglais.*

## Where things happen

- **Questions and ideas** go to [Discussions](https://github.com/orgs/parler-haut-interagir-librement/discussions).
- **Bugs and feature requests** go to an issue in the repository concerned, through its forms.
- **Security problems** never go to a public issue: see [SECURITY.md](SECURITY.md).
- **Packages are incubated privately** in the `phil-prerelease` monorepo until they are finished, then move to the
  public monorepo [`parler-haut-interagir-librement/phil`](https://github.com/parler-haut-interagir-librement/phil), from which each package is split into a
  read-only repository. Send pull requests to the monorepo, never to a split repository. Until a package is public,
  issues and discussions are the way to take part.
- **The UX kit repositories** ([ux-kit](https://github.com/parler-haut-interagir-librement/ux-kit), [ux-css](https://github.com/parler-haut-interagir-librement/ux-css), [ux-kit-shadcn](https://github.com/parler-haut-interagir-librement/ux-kit-shadcn)) take pull requests directly once their content is published.

For anything larger than a small fix, open an issue or a discussion first, so that we can agree on the shape before
you spend time on it.

## Your own code

The code of a PHIL package is its own; third-party code enters only as a declared Composer dependency.

- **No third-party code is copied** into a package — not a function, not a snippet, whatever its licence. Other
  projects may be studied for their ideas and their behaviour; the code you submit must be your own.
- **Data is different from code.** Reference data from open sources (for example CLDR) may be imported by a script,
  with its licence and attribution recorded next to it.
- **Check what your tools produce.** If an assistant or a generator suggested code, make sure it is not a copy of
  existing code before you submit it.

## Licence of contributions

There is **no contributor licence agreement** and **no sign-off** to add. By submitting a contribution, you confirm
that you wrote it and have the right to submit it, and you agree that it is published under the licence of the
package it belongs to — MIT for every PHIL package.

## Rules every package follows

- **A pure PHP library and its Symfony bundle.** The library has no framework dependency beyond the Symfony
  components it genuinely uses; the bundle wires it into Symfony. A new dependency needs agreement in the issue first.
- **Generic.** A package never names a particular website, company project or service of ours, not even in an
  example; site-specific behaviour belongs to the site, through the package's extension points.
- **Extension points** are tagged services and public interfaces, documented in `doc/extension-points.md`.
- **Accessibility:** keyboard and screen-reader use, visible focus, reduced motion, sufficient contrast, and no
  information carried by colour alone.
- **Internationalisation:** every user-facing string is translatable; formats, plurals and typography follow the
  locale; nothing assumes the languages of our own sites.
- **Privacy** (Loi 25, GDPR): no tracking, no third-party call without the site's explicit configuration, personal
  fields declared so that they can be exported and erased, and queued messages that carry identifiers rather than
  personal data.

## Setting up

```bash
composer install
vendor/bin/phil-dev init   # once, when a package is created
composer gates             # every quality gate, in CI order
```

The shared configurations, scripts and the package skeleton come from `phil/dev-tools`. Integration tests that need
MySQL, PostgreSQL or Gotenberg start them in Docker.

## Coding standards

- `declare(strict_types=1);` in every PHP file, strict comparisons everywhere.
- PHP-CS-Fixer with the `@Symfony` and `@Symfony:risky` rule sets.
- PHPStan at its maximum level with the strict rules, on every PHP version of the matrix.
- Rector with the sets of the installed PHP, Symfony, Doctrine and PHPUnit versions.
- Deptrac and Arkitect for the architecture: domain models are `final`, value objects `final readonly`, and domain
  code knows nothing of HTTP, Messenger, forms or the container.
- Dates are never compared with `==` or `===`; compare their instants.

## Tests

- `tests/Unit` runs without a kernel or a server; `tests/Integration` boots a kernel or talks to a real server;
  `tests/Functional` goes through HTTP.
- Deprecations, notices and warnings fail the run, on the floor PHP and Symfony **and** on the next ones (the next
  version enters the matrix at its first release candidate).
- Every package must also pass when installed on its own.
- **Mutation testing:** Infection must reach **100 %** of mutants killed and of covered mutants killed. A surviving
  mutant is a missing test, or code nothing can reach; an equivalent mutant is named in the package's manifest with
  its reason. The bar is never lowered.

## Documentation

- In English. Each package has a README (what it does, installation, a short example, a status table) and a
  complete `doc/` folder.
- Documentation describes the code as it is now: no history of how it was written. Change the documentation in the
  same pull request as the code.

## CHANGELOG

Each package keeps a `CHANGELOG.md` following [Keep a Changelog](https://keepachangelog.com), with the coming changes
under a `NEXT` heading.

- **Before a package's first public release**, the `NEXT` section has an `Added` list only: the package is described
  as it will ship.
- **After the first release**, use the usual sections: `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`,
  `Security`.

## Commit messages

- One logical change per commit.
- A title of about 50 characters, at most 72, in the imperative mood (“Add the weekly leagues”).
- A blank line, then a body that explains what changed and why, in short paragraphs or bullets.
- Reference the issue when there is one (`Closes #12`).

## Pull requests

Fill in the pull request template. A pull request is ready when `composer gates` passes, the mutation score is
100 %, the documentation and the CHANGELOG are updated, and the checklist is ticked. Reviews may ask for changes;
that is normal and never personal.

## Conduct

Everyone taking part follows the [code of conduct](CODE_OF_CONDUCT.md).
