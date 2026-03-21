# Repository onboarding

This organization is designed so new repositories start from a small template set and inherit shared guard rails from the organization.

## Choose a starter

- `repo-template`: generic starting point when the repo type is still unclear
- `service-template`: apps, APIs, background workers, and other deployable services
- `library-template`: reusable packages, SDKs, and shared modules
- `infra-template`: infrastructure, platform, automation, and operations repositories

## Default path for a new repository

Use the local bootstrap helper when possible.

```bash
unset GITHUB_TOKEN
bootstrap-gh-repo my-new-repo --template SaagarPatelOne/service-template
```

Useful examples:

```bash
unset GITHUB_TOKEN
bootstrap-gh-repo my-app --template SaagarPatelOne/service-template --description "Application or API"
bootstrap-gh-repo my-library --template SaagarPatelOne/library-template --description "Reusable package"
bootstrap-gh-repo my-infra --template SaagarPatelOne/infra-template --private --description "Infrastructure and operations"
bootstrap-gh-repo my-scratch-repo --template SaagarPatelOne/repo-template
```

What this does:

1. Creates the repository from the selected template
2. Runs the repo hardening fallback
3. Verifies org ruleset coverage and repo security settings

## Path for an existing repository

If a repository already exists and needs to be brought back to the org baseline:

```bash
unset GITHUB_TOKEN
harden-gh-repo SaagarPatelOne/my-existing-repo
```

Use this when a repo:

- was created outside the template flow
- predates the current baseline
- looks like it may have drifted from the shared org posture

## What the organization already enforces

The organization is the primary source of truth for shared guard rails.

- default branch rules are enforced by the org ruleset
- GitHub Actions are restricted at the org level
- the GitHub-recommended code security configuration is the default for new repos
- org-wide community health defaults come from the public `.github` repository

## What the repo hardener still reconciles

Some settings still benefit from an explicit repo pass, especially for brand-new generic repositories.

- repo-level security feature enablement
- vulnerability alerts
- final verification that the active org ruleset applies to the repo

## Recommended habit

For new work:

1. choose the smallest matching template
2. create the repo with `bootstrap-gh-repo`
3. confirm `CI` and `Secret Scan` pass on the first push

For older repos:

1. run `harden-gh-repo`
2. verify the repo shows the `Default branch baseline` ruleset
3. check that secret scanning and Dependabot security updates are enabled

## Current intentional exceptions

- org-wide 2FA enforcement is deferred for now
- `members_can_invite_outside_collaborators` is intentionally left as-is
