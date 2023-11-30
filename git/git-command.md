# Git Basics Cheat Sheet

## Resources for Learning Git:
- [Learn Git Branching](https://learngitbranching.js.org/)
- [W3Schools Git Tutorial](https://www.w3schools.com/git/default.asp?remote=github)

## Git Commands:

### Initialize and Status:
- `git init`: Initialize the directory. Starts tracking the directory.
- `git status (--short)`: Provides the status of changes in the directory.
  - Flag `--short`: Gives a concise output to the status.

### Staging Environment:
Staged files are ready to be committed to the repository.

- `git add (--all/./\*/-A or fileName)`: Adds files to the staging environment.
  - Flag "--all/./\*/-A": Selects all files from a directory.
  - Use "fileName" to add a specific file to the staging.

- `git commit (-a -m "commit message")`: Commits changes from the staging area to the remote repo.
  - Flag `-a`: Stages and commits together (not recommended).
  - Flag `-m`: Adds a commit message. Always use double quotes.

### Remote Operations:
- `git push (repo url)or(remote name) (branchName)`: Push local files to remote repo.
- `git remote add/set-url (remote name) (repo url)`: Create a remote name and update its URL.
  - `git remote`: List all remote names.
  - `git remote remove (remote name)`: Remove a remote name.

### Viewing and Fetching:
- `git log`: List all commit history. Use `q` to quit the git log.
- `git fetch remoteName/repoURL`: Fetch changes made in the remote repo (at GitHub).
  - Tip: Use `git status` after `git fetch` to see updates. Merge with your local repo using `git merge origin/master`.

- `git diff remoteName/localBranchName (e.g., main)`: Show changes between local and remote repo.

- `git pull`: Combination of fetch and merge. Pulls all changes from a remote repository into the current branch.

### Branching and Merging:
- `git branch branchName`: Create a new branch.
  - `git branch -d branchName`: Delete the branch.
  - `git branch -a`: List all branches (local and remote).

- `git checkout branchName`: Switch to a branch.
  - `git checkout -b branchName`: Create and switch to a new branch.

- `git merge branchName`: Merge changes from one branch into another.
- `git rebase branchName`: Integrate changes from one branch into another by moving or combining commits.

### Head and Reset:
- "HEAD" points to the current branch and version.

- `git branch -f main HEAD~number/branchId(or hash)`: Change the position of the branch.

- How to reset or revert:
  - `git reset HEAD~number/branchId(or hash)`: Reset the commit to the parent commit.
  - `git revert HEAD/branchId(or hash)`: Create a new commit by the parent branch without removing the current branch.
