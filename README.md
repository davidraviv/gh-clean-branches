# Clean Branches
## Description
Github CLI extension

Safely delete local branches that have no remotes and no hanging changes.

The extension uses `git branch -d` to delete the local branches, hence it will not delete branches with un-pushed changes.

## Usage
Run it inside a git repo folder:
```bash
gh clean-branches
```

## Dependencies
The extension relays on:
- gh CLI 2.0
- zsh
- node.js

I may remove the last two dependencies, they are not really needed (pull requests are welcomed!). It helped me for fast developing it.

## Installation
```bash
gh extension install davidraviv/gh-clean-branches
```
