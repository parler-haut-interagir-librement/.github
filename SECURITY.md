# Security policy

This policy applies to every repository of the Parler Haut, Interagir Librement (PHIL) organisation that does not carry its own `SECURITY.md`.

*Vous pouvez nous écrire en français ou en anglais.*

## Reporting a vulnerability

**Please do not open a public issue, discussion or pull request for a security problem.**

Report it privately through GitHub's private vulnerability reporting: in the repository concerned, open the
**Security** tab and choose **Report a vulnerability**. The report stays visible only to you and to the maintainers
until a fix is published.

If the code is not in a public repository yet, or if you cannot use GitHub, write to
[info@ph-il.ca](mailto:info@ph-il.ca) with “Security” in the subject.

Please include:

- the package and the version or commit affected;
- the PHP and Symfony versions;
- what an attacker can do, and the conditions it takes;
- the steps or a minimal proof of concept to reproduce it;
- a suggested fix, if you have one.

## What happens next

We are a small team; we aim to acknowledge a report within a week, to confirm or dismiss it, and then to agree with
you on a fix and a disclosure date. Once a fix is released, we publish a GitHub security advisory, request a CVE when
it is warranted, and credit you unless you prefer otherwise.

## Supported versions

PHIL packages are written in incubation and released one at a time. Today one package is released, `phil/enums` (published as `ph-il/enums`); the others are not released yet.

- **Package versions.** Before 1.0, only the latest release of a package receives security fixes. The policy for 1.0
  and later will be written here before the first 1.0 release.
- **PHP and Symfony.** Each package supports two versions of each: the **floor** it requires (today PHP 8.5 and
  Symfony 8.2 for new packages) and the **next** version, tested from its first release candidate (today PHP 8.6).
  The floor moves up when the next version reaches its first patch release for a Symfony minor (x.y.1), and its
  third for a Symfony major or a PHP version (x.0.3, x.y.3), always in a new version of our packages, never in an
  existing one. A released package states its own floor in its `composer.json`.

## Scope

This policy covers the code of the PHIL packages, kits and tools. Vulnerabilities in a dependency should also be
reported to its maintainers; tell us as well when our packages are affected.
