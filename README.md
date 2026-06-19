# Clean Branches
## Description
Github CLI extension

Safely delete local branches that have no remotes and no hanging changes.

The extension uses `git branch -d` to delete the local branches, hence it will not delete branches with un-pushed changes
unless using `--force` flag.

The extension supports single or multiple upstream.
## Installation
```bash
gh extension install davidraviv/gh-clean-branches
```

## Usage
Execute it inside a git repo folder:
```bash
gh clean-branches [--dry-run] [--force] [--verbose] [--worktrees]
```
### Options

- `--dry-run` See the list of branches and worktrees to be deleted before actually deleting them.
- `--force` Uses `git branch -D` forcing a branch to be deleted regardless if upstream branches have local changes. Also force-removes worktrees that have uncommitted changes. Use carefully!
- `--verbose` Print all log statements.
- `--worktrees` Also remove local worktrees whose remote branch has been deleted, then delete their local branch. Worktrees in detached HEAD state (no branch) are removed as well. Without this flag, worktree cleanup is skipped and existing behaviour is unchanged.

## Script flow
- Fetches the repo
- Checkout the default branch (e.g `main`) and pull changes (needed if we want to delete the current branch)
- Lists all remote branches _(only with `--verbose` flag)_
- Lists all local branches _(only with `--verbose` flag)_
- _(With `--worktrees`)_ Lists orphaned worktrees (remote branch gone or detached HEAD) and removes them
- Lists branches with missing upstream to be deleted
- Deletes branches with no upstream and no un-pushed changes _(Skipped on `--dry-run`)_
- Checkout the branch we started with unless it was deleted, then stays on the default branch

## Dependencies
The extension depends on:
- zsh
- git v2.22
- gh CLI v2.0
