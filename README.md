# GitHub Auto Update Pre-Commit Action

This GitHub Action automatically updates the pre-commit hooks in your repository to ensure they are always up-to-date. It is particularly useful for maintaining consistency and avoiding outdated hooks across your development team.

## Features

- Automatically updates pre-commit hooks to the latest versions.
- Creates a pull request with the updated hook versions.
- Easy to integrate into your CI/CD pipeline.

## Usage

To use this action in your repository, add the following to your workflow YAML file:

```yaml
name: Update Pre-Commit Hooks

on:
  workflow_dispatch:
  schedule:
    - cron: '0 0 * * 0' # Runs weekly on Sunday at midnight

jobs:
  update-precommit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Run Auto Update Pre-Commit Action
        uses: LeonLuttenberger/gh-auto-update-precommit@v1.0.0
        with:
          base-branch: "main" # Optional: Specify the base branch for the pull request
```

## Inputs

### `base-branch`

- **Description**: The base branch for the pull request.
- **Default**: `main`

## Outputs

This action does not produce any outputs.

## Setup

1. Ensure you have a `.pre-commit-config.yaml` file in the root of your repository.
2. Add this action to your GitHub workflows as shown in the usage section.
3. Ensure the GitHub token used by the workflow has write permissions.
4. Commit and push the workflow file to your repository.

## License

This project is licensed under the [MIT License](LICENSE).
