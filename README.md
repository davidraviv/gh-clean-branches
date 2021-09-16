# Clean Branches
## Description
Github CLI extension

Safely delete local branches that have no remotes and no hanging changes.

The extension uses `git branch -d` to delete the local branches, hence it will not delete branches with un-pushed changes.

## Installation
```bash
gh extension install davidraviv/gh-clean-branches
```

## Usage
Execute it inside a git repo folder:
```bash
gh clean-branches [--dry-run]
```
Use the `--dry-run` flag to see the list of branches to be deleted before actually deleting them.

## Script flow
- Fetches the repo
- Checkout the default branch (e.g `main`) and pull changes (needed if we want to delete the current branch)
- Lists all local branches
- Lists all remote branches
- Lists branches with missing upstream to be deleted
- Deletes branches with no upstream and no un-pushed changes _(Skipped on `--dry-run`)_
- Checkout the branch we started with unless it was deleted, then stays on the default branch

When using the `--dry-run` flag, deleting the branches is skipped. All the rest is always performed.
## Dependencies
The extension depends on:
- zsh
- git v2.22
- gh CLI v2.0
