# Sample service using the shared release repo

This repo demonstrates the consumer-side contract for the centralized release pipeline.

- `ci.yml` runs on PRs and pushes to `main`.
- `release.yml` invokes the shared release workflow in the organization release-actions repo.
- The release pipeline computes the next semantic version from conventional commit titles and promotes through `dev`, `rc`, and production approval.

## Example release call

```yaml
uses: tseste/release-actions/.github/workflows/release-orchestrator.yml@main
with:
  service_name: sample-service
  pr_title: feat: add customer profile API
  manager_team: release-managers
```

The shared repo enforces the tag-based lifecycle and the production approval checkpoint.
