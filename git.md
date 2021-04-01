# Git

What I'm doing makes no sense (resets all changes, staged or not, but doesn't touch untracked files):

```bash
git checkout -f
```

## Stashing

```bash
git stash
git stash list
git stash apply
```

Include untracked changes in stash:

```bash
git stash -u
```

# Finding stuff

Repo commit history

```bash
git log --first-parent --oneline --reverse
```

Grep from history (`git-rev-list` lists commit objects)

```bash
git rev-list --all | xargs git grep EXPRESSION
```