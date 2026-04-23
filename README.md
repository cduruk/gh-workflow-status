# gh-workflow-status

A GitHub CLI extension for viewing the status of a GitHub Actions workflow from the current repository.

The extension follows the same lightweight shell-script style as `davidxia/gh-merge-queue`: one executable script plus `jq` for formatting.

## Installation

Dependencies:

- [GitHub CLI](https://cli.github.com)
- [jq](https://jqlang.org/download/)

From this checkout:

```sh
gh extension install .
```

If this is later published as a repository named `gh-workflow-status`:

```sh
gh extension install OWNER/gh-workflow-status
```

## Usage

```sh
# Show a workflow from the current repository
gh workflow-status deploy.yml

# Refresh every 15 seconds
gh workflow-status --watch 15 deploy.yml

# Show job detail for the selected run
gh workflow-status --jobs deploy.yml

# Show a specific workflow by repo and file/name
gh workflow-status cli/cli build.yml

# Parse a GitHub workflow URL
gh workflow-status https://github.com/cli/cli/actions/workflows/build.yml
```

Useful options:

```sh
gh workflow-status deploy.yml --limit 10
gh workflow-status deploy.yml --branch main
gh workflow-status deploy.yml --status in_progress
gh workflow-status --run 24856112866
gh workflow-status deploy.yml --all-jobs --jobs-limit 100
```

Defaults can be changed with environment variables:

```sh
export GH_WORKFLOW_STATUS_REPO=OWNER/REPO
export GH_WORKFLOW_STATUS_WORKFLOW=deploy.yml
export GH_WORKFLOW_STATUS_LIMIT=5
export GH_WORKFLOW_STATUS_JOB_LIMIT=25
```

For private repositories, your `gh` auth token must have access to the repository and Actions runs.
