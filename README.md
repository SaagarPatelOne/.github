# SaagarPatelOne organization defaults

This repository stores the default community health files and issue and pull request templates for repositories in the `SaagarPatelOne` organization.

These defaults are designed for a solo-maintained project set:

- concise contribution guidance
- high-signal issue and pull request intake
- private-first security reporting guidance
- low maintenance overhead

Individual repositories can override these defaults when they need something more specific.

## Template starter set

The organization currently keeps a small template set:

- `repo-template` for generic repositories
- `service-template` for apps, APIs, and services
- `library-template` for reusable packages and shared modules
- `infra-template` for infrastructure and operations repositories

The intent is to keep the catalog small and practical while relying on org-wide rules, Actions policy, and code security defaults for the shared guard rails.

## Operating manual

See [REPO_ONBOARDING.md](REPO_ONBOARDING.md) for the default path for:

- choosing the right starter template
- creating a new repository with `bootstrap-gh-repo`
- hardening an existing repository with `harden-gh-repo`
- understanding which protections come from the organization and which are still reconciled per repository

## Verify changes

Run from this repository's root. Python 3 with `venv`, Git and network access
for the initial tool/hook download are required. Keep the tooling environment
outside the repository:

```bash
python3 -m venv ../org-defaults-venv
../org-defaults-venv/bin/python -m pip install pre-commit
# Focused documentation check; replace README.md with the changed tracked files.
../org-defaults-venv/bin/pre-commit run --files README.md --show-diff-on-failure
# Same hygiene command as .github/workflows/ci.yml, across tracked files.
../org-defaults-venv/bin/pre-commit run --all-files --show-diff-on-failure
```

Some hooks fix whitespace or line endings: review their diff and rerun until
they pass. For a local history scan, install the CI version of Gitleaks (8.24.2)
and run `gitleaks git --redact --no-banner .`; keep findings redacted. The
required hosted checks are defined in [CI](.github/workflows/ci.yml) and
[Secret Scan](.github/workflows/secret-scan.yml). This repository has no app
server, package build, typecheck or separate test suite.

For issue/PR template changes, check the rendered intake form on the proposed PR
and confirm the required fields and guidance still make sense.
