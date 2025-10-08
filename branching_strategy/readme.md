# Branching Strategy: Hybrid GitFlow

## Branches
- main — always deployable; tagged releases only.
- develop — integration branch for the next release.
- feature/<ticket-or-epic>-<short-name> — short-lived branches off develop.
- release/<version> — stabilize for a few days (string-freeze, docs, version bump); merge back to main and develop.
- hotfix/<version> — urgent fix from main; merge back to main and develop.

## Rules & protections
- Protect main and develop: require PR + 1–2 reviews, passing CI, and up-to-date with base.
- Only release/* and hotfix/* PRs can merge to main.
- Disallow force-push on protected branches.
- Require conventional commits (or enforce via PR title): feat:, fix:, docs:, chore:, refactor:, perf:, test:.

## Versioning & tags
- SemVer tags on main: vX.Y.Z.
- Create a GitHub Release from the tag with changelog notes (auto-generated from conventional commits).

## PR workflow
1.	Branch from develop: feature/123-estimates-endpoint.
2.	Open PR to develop; CI runs (lint, tests, type checks, build).
3.	Squash-merge with a clean message (keeps history tidy).
4.	When features are ready, cut release/1.3.0 from develop; only fixes & docs allowed.
5.	Merge release/* → main (tag v1.3.0 automatically), then back-merge to develop.

## Hotfixes
-	Branch hotfix/1.3.1 from main, fix, PR to main, tag on merge, then back-merge to develop.

# Data considerations (ESTER-specific)
- Keep code and heavy data separate:
  - Use a data repo for large datasets
	-	Never commit derived outputs; publish them via the pipeline to Dataverse/ZENODO and reference DOIs.
	-	If you must version small seed data: data/seed/ tracked normally; larger → LFS.

## Naming conventions
-	Features: feature/456-hierarchical-model-priors
-	Fixes: fix/789-ci-cache-miss
-	Release: release/1.4.0
-	Hotfix: hotfix/1.4.1

## CI/CD checks (gatekeepers)
-	Lint & format
-	Unit tests with coverage threshold (e.g., ≥80%).
-	Type checking
- Build static assets (if dashboard).
-	Security (Dependabot + pip/audit or npm audit).

## Changelog
-	Auto-generate from commit messages on release
