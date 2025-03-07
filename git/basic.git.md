# Git – Basic Guide for Beginners

**offical documentation : [git-scm.com](https://git-scm.com/)**

### 🎉 What is Git?

Git is a Distributed Version Control System (DVCS) that tracks changes in source code over time, enables efficient team collaboration, and allows reverting to previous versions when needed.

### 🎉What is Git’s Snapshot Mechanism?

Instead of saving entire files every time a change occurs, Git only stores snapshots of the data. If a file remains unchanged, Git simply links to the previous version instead of duplicating its content.

### 🎉 Key Concepts in Git

🔹 Source Folder, Workspace, Indexing, Staging, Commit
Term Meaning

- Source Folder The directory containing the project's source code
- Workspace The working area where you modify files
- Indexing The process of adding files to Git’s tracking system
- Staging Files that have been added to the staging area (git add) before committing
- Commit Saves changes to Git history

🔹 Relationship Between Folder States & Tree Objects

- When committing, Git saves the directory’s state as a tree object, organizing data in a tree structure.
- Each file in the directory corresponds to a blob object, which contains the file content without metadata.

🔹 What is HEAD?

- HEAD is a pointer to the latest commit on the current branch.
- When switching branches (git checkout branch_name), HEAD updates accordingly.

### 🎉 .gitignore – Ignore Unnecessary Files

- A .gitignore file instructs Git to ignore specified files (e.g., config files, build folders, dependencies).
- If you accidentally add a file before ignoring it:

```sh
git rm --cached file_name # Remove the file from the index but keep it locally
echo "file_name" >> .gitignore
```

## 🎉Basic Git Operations

🔥 Add files to staging

```sh
git add file_name
```

🔥 Work with a remote repository

```sh
git remote add origin <repository_url> # Connect to a remote repo
git fetch # Fetch latest data without merging
git pull # Fetch and merge changes into the current branch
git push # Push local changes to remote
```

🔥 Commit changes to Git history

```sh
git commit -m "Commit description"
```

🔥 Work with branches

```sh
git branch branch_name # Create a new branch
git checkout branch_name # Switch to another branch
git merge branch_name # Merge a branch into the current branch
```

### 🎉 Reset & Stash – Managing Local Changes

🔥 Reset to a previous state

```sh
git reset --soft HEAD~1 # Reset commit but keep changes
git reset --mixed HEAD~1 # Reset commit & index, keep changes in workspace
git reset --hard HEAD~1 # Remove all changes
```

🔥 Temporarily save changes with stash

```sh
git stash # Save changes to stash
git stash pop # Restore changes from stash
```

### 🎉 Merge & Rebase – Merging Branches

🔥 Merge: Fast-Forward (FF) vs Non-Fast-Forward (Non-FF)

- Fast-Forward (FF): Moves HEAD directly to the feature branch if no new commits exist in the main branch.
- Non-FF: If the main branch has new commits, Git creates a merge commit.

```sh
  git merge --no-ff feature_branch # Merge with a merge commit
```

🔥 Squash Merge – Keep main branch history clean

Always use --no-ff and squash commits before merging into main.

```sh
git merge --squash feature_branch
git commit -m "Squashed all commits into one"
```

🔥 Rebase – When to Use It?

Reorder, group, or edit commits (Interactive Rebase)

```sh
git rebase -i HEAD~3 # Modify recent commits
Edit the last commit
```

```sh
git commit --amend # Modify the last commit
```

🎉 Cherry Pick – Selectively Apply Commits

If you need to take a specific commit from another branch:

```sh
git cherry-pick commit_hash
```

#### 🎉 Additional Tips

✅ Learn Git Conventions but Keep It Simple
Follow commit message conventions:

- **feat:** (new feature)
- **fix:** (bug fix)
- **refactor:** (code restructuring)
- **chore:** (minor changes, not affecting main code)

✅ Use Git Desktop Applications

Tools like GitHub Desktop and Sourcetree simplify Git workflows for beginners.

download: **[github desktop](https://desktop.github.com/download/)**
