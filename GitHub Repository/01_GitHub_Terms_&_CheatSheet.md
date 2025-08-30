# GitHub Dictionary

| Term | Description |
|------|-------------|
| Branch | A separate line of development in Git. Each branch can have its own commits. |
| Commit | A snapshot of changes in your repository. Each commit has a unique hash. |
| Diff | Shows differences between commits or between commit and working directory. |
| Fetch | Get updates from a remote repository without merging them into your branch. |
| File | A single unit of data stored on disk. |
| HEAD | Pointer to the current branch and commit you are working on. |
| Main / Master | The primary branch in a Git repository. Modern repos often use `main`. |
| Merge | Combine changes from one branch into another. |
| Pull | Fetch and merge changes from remote to your current branch. |
| Pull Request | A request to merge changes from one branch to another in a remote repository. |
| Push | Send local commits to a remote repository. |
| Remote | A version of your repository hosted on a server (like GitHub). |
| Reset | Move the HEAD pointer to a specific commit; can optionally discard changes. |
| Revert | Create a new commit that undoes a previous commit. |
| Stage / Staging Area | An intermediate step between making changes to the files and committing those changes to the repository's history. It allows to selectively choose which modifications one want to include in your next commit, giving fine-grained control over the project's version history. |
| Tracking Branch | A local branch linked to a remote branch for push/pull operations. |
| Upstream | Remote branch that the local branch tracks for push/pull. |



<br>
<br>

# GitHub Cheat Sheet

## Branch Commands

| Command | Description |
| ----------- | ----------- |
| `git branch` | List local branches and show the current branch (`*`).  |
| `git branch -v` | Lists all branches in the repository and provides additional information about each branch (local). |
| `git branch -r` | List remote branches. |
| `git branch <branch-name>` | Create branch. |
| `git branch -b <branch-name>` | Create branch and switch to it. |
| `git branch -d <branch>` | Delete a local branch if merged (when no more commits). |
| `git branch -D <branch>` | Force delete a local branch. |
| `git checkout <branch>` | Switch to another branch. |

## Remote Commands

| Command | Description |
|---------|-------------|
| `git remote -v` | Show configured remotes and their URLs. |
| `git remote add origin <url>` | Add a new remote called `origin`. |
| `git remote set-url origin <url>` | Change the URL of an existing remote. |
| `git fetch --all` | Fetch all remote branches without merging. |
| `git fetch --all --prune` | Fetch all branches and remove stale references. |
| `git push origin <branch>` | Push local commits to the remote branch. |
| `git push origin --delete <branch>` | Delete a branch in the remote repo. |

## Commits and Changes

| Command | Description |
|---------|-------------|
| `git log` | Show full commit history. |
| `git log --oneline` | Show summarized commit history. |
| `git log origin/main..HEAD --oneline` | Show commits not yet pushed to remote. |
| `git log HEAD..origin/main --oneline` | Show commits in remote not in local. |
| `git show <hash>` | Show a specific commit with changes. |
| `git diff <hash1> <hash2>` | Show differences between commits. |
| `git diff <hash>` | Show changes vs working directory. |
| `git revert <hash>` | Create a new commit that undoes a previous commit. |
| `git reset <hash>` | Move HEAD to a previous commit; keep changes in working directory. |
| `git reset --hard <hash>` | Move HEAD and overwrite local changes. |

## Files and Folders

| Command | Description |
|---------|-------------|
| `git rm <file>` | Stage a file deletion for commit. |
| `git rm -r <folder>` | Stage folder deletion recursively. |
| `git add -u` | Stage all tracked changes (including deletions). |
| `git commit -m "message"` | Commit staged changes. |
| `git status` | Show current repository status. |
| `git reset --hard HEAD` | Restore all files to last commit. |
| `git fetch origin && git reset --hard origin/main` | Sync local branch with remote, discarding local changes. |

<br>
<br>

# GitHub Quick Workflow

1. Delete files/folders ->`rm` (Linux) or `git rm` (Git).  
2. Stage changes ->`git add <path>` or `git add -u`.  
    - ❌ Undo staged file: `git restore --staged <file>` 
3. Commit changes ->`git commit -m "message"`.  
    - ❌ Wrong commit message (last commit only): `git commit --amend -m "new message"`  
    - ❌ Wrong commit entirely:  
        - Keep changes (unstage): `git reset --soft HEAD~1`  
        - Discard changes (dangerous): `git reset --hard HEAD~1`  
4. Push to remote ->`git push origin <branch>`.  
    - ❌ Undo last push (if safe):  
        - Rewrite history and force push: `git push origin <branch> --force`  
        ⚠️ Use only if no one else depends on that branch.  
5. Sync with remote
    - Update info: `git fetch`  
    - Reset local to match remote: `git reset --hard origin/<branch>`  
6. View commits ->`git log`, `git show`, `git diff`.  
