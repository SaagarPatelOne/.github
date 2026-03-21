# Integrations Policy

The `SaagarPatelOne` organization defaults to first-party GitHub capabilities before adding third-party integrations.

## Default baseline

- GitHub Actions for automation
- Dependabot for dependency maintenance
- GitHub code security configuration
- Secret scanning and push protection
- Private vulnerability reporting

## Third-party GitHub Apps

Third-party GitHub Apps should only be installed when there is a clear operational need.

Requirements:

- GitHub App only, not long-lived personal access token bots
- least-privilege repo and org scopes
- owner approval before installation
- a short written record of why the installation exists and what access it needs

## Review standard

Before installing an app, review:

- which repositories it needs
- whether it needs org-wide access or selected repositories only
- what webhooks, write permissions, or secrets it requires
- whether GitHub-native features already solve the same problem
