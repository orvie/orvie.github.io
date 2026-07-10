---
layout: page
title: Git Notes
---

## Remote config for github two different accounts different sshkey

```conf
Host github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/github-orvie

Host github-orvie1011
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_ed25519
```

```bash
# Set origin using alias
# Note: here im using organizations <org-name>/<repo-name>.git
git remote set-url origin git@github-orvie1011:orvie1011/<repo-name>.git
```

## Useful Log Views

```bash
# Compact one-line log
git log --oneline

# Graph view across branches
git log --oneline --graph --all --decorate

# Log with diff stats
git log --stat

# Log for a specific file
git log --follow -- path/to/file

# Search commit messages
git log --grep="fix login"

# Search for a code change (who introduced this string)
git log -S"functionName" --oneline
```

## Basic Rebase

Replays your branch's commits on top of another branch instead of merging.

```bash
git checkout feature-branch
git rebase main
```

If conflicts occur:

```bash
# fix the conflicted files, then
git add <file>
git rebase --continue

# or bail out entirely
git rebase --abort
```

## Interactive Rebase (squash, reorder, reword)

```bash
# Rebase the last 5 commits interactively
git rebase -i HEAD~5
```

This opens an editor listing commits oldest-first:

```
pick a1b2c3d Add login form
pick d4e5f6g Fix typo
pick h7i8j9k Add validation
pick k1l2m3n Fix validation bug
pick n4o5p6q Update tests
```

Common actions (replace `pick` with):

- `squash` (or `s`) — combine this commit into the previous one, keep both messages to edit
- `fixup` (or `f`) — combine into the previous one, discard this commit's message
- `reword` (or `r`) — keep the commit, edit its message
- `drop` (or `d`) — remove the commit entirely
- reorder lines to change commit order

Example — squash the last 4 commits into the first:

```
pick a1b2c3d Add login form
squash d4e5f6g Fix typo
squash h7i8j9k Add validation
squash k1l2m3n Fix validation bug
squash n4o5p6q Update tests
```

Save and close, then edit the combined commit message on the next screen.

## Quick Squash Shortcuts

```bash
# Squash all commits on this branch since it diverged from main
git rebase -i main

# Amend the most recent commit (message and/or staged changes)
git commit --amend

# Amend without changing the commit message
git commit --amend --no-edit
```

## Rewriting History Safely

```bash
# After rebasing a branch you've already pushed, force-push safely
# (fails if the remote has commits you don't have locally)
git push --force-with-lease
```

## Recovering from a Bad Rebase

```bash
# Reflog shows every place HEAD has pointed, including pre-rebase
git reflog

# Reset back to a commit shown in the reflog
git reset --hard HEAD@{2}
```

## Troubleshooting

- **Conflicts on every commit during rebase**: Consider `git rebase -i` with `squash` first to reduce the number of replayed commits, or rebase onto a closer common ancestor
- **Pushed a rebased branch and remote rejects it**: Use `git push --force-with-lease` instead of a plain force push
- **Lost commits after a rebase**: `git reflog` almost always has them; find the commit before the rebase and `git reset --hard` to it
