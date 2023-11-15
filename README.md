# workflows

This repository contains reusable workflows and actions for the Manytask organization.

## Reusable Workflows

The `.github/workflows` directory contains GitHub Actions workflows that can be reused across multiple repositories. These workflows are designed to automate common tasks and improve efficiency.

Currently, we have the following reusable workflows:

- `reusable-validate-pr.yml`: This workflow checks the pull request title for compliance with the [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/) format and PR labels.
- `reusable-update-changelog-version.yml`: This workflow updates the `CHANGELOG.md` and `VERSION` files upon release.

Please note that these workflows contain `on: workflow_call:` jobs, which means they won't be executed automatically. 
To use a workflow from this directory, you need to call it from another workflow in your repository:
```yaml
jobs:
  call-workflow-passing-data:
    uses: manytask/workflows/.github/workflows/reusable-workflow.yml@main
    with:
      config-path: .github/labeler.yml
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
    permissions:
      contents: read
```

## Action Configs

The `.github` directory contains GitHub Actions configurations that can be **reused** in multiple repositories.

- `release-drafter.yml` - config for [release-drafter](https://github.com/release-drafter/release-drafter) GitHub Action.

    You need to create `.github/release-drafter.yml` file in your repository to use this config.
    ```yaml
    _extends: manytask/workflows:.github/release-drafter.yml
    ```
