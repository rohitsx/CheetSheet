### (Visti this site to recall any advance topic)[https://learngitbranching.js.org/] or (visit this site to recall basic topics) [https://www.w3schools.com/git/default.asp?remote=github].

# Git starter

**git init:** Initialize the directory. Starts tracking the directory.

**git status (--short):** Provides the status of changes in the directory.

- Flag --short: Gives a concise output to the status.

## Staging enviroment

Staged files are files that are ready to be committed to the repository you are working on. As you work, add, edit, and remove files. Use the staging environment for commits.

**git add (--all/./\*/-A or fileName):** Adds files to the staging environment.

- Flag "--all/./\*/-A" used to select all flies from directory.
- Use "fileName" to add selected file to the staging.

**git commit (-a -m "commit message"):** Commits changes from the staging area to remote repo. Git considers each commit change point or "save point".

- Flag -a used when you want to stage and commint together **although it is not recomended**.
- Flag -m used to add commit message. when using -m flags always use double quotes to add message.

**git push (repo url)or(remote name) (brancName):** push you local files to remote repo.

**git remote add/set-url (remote name) (repo url):** create remote name and you can always use in the place of url.

- add cammand will add new remote name.
- set-url will set update the url.
- git remote list all the remote name.
- git remote remove (remote name).

**git log:** list all the commit history. use q to quite git log.

## Git pull

**git fetch remoteName/repoURL:**use to fetch changes made in remote repo (at githube).
tip: use "git status" after git fetch to see updates and then merge with your local repo to remote repo using git merge origin/master.

**git differ remoteName/localBranchName (e.g. main):** show changes differ between local repo and remote repo.

**git pull:** it is a combination of fetch and merge. It is used to pull all changes from a remote repository into the branch you are working on.

## Git push

**git push (remoteName branchName):** push the local file to remote directory (githube).

- remoteName and branchName is optional.

**git checkout branchName:** to change the branch

- **git checkout -b branchName** will create and swtich to new branch.

**git branch branchName:** to create a new branch

- **git branch -d branchName:** flag -d used to delete branch
- **git branch -a:** flag -a get you all the branch on remote repo
- note: when git pull will not fetch all branch

**git merge branchName:** to merge to the branch (you can also merge remote branch, so can update the local branch from remote branch)

**git rebase branchName:** Git rebase is used to integrate changes from one branch into another by moving or combining commits, creating a linear commit history.

difference between git merge and git rebase:

> Git merge combines changes from different branches by creating a new commit, while git rebase integrates changes by moving and reapplying commits to a new base, resulting in a linear commit history.

### Head

> "HEAD" points to the branch name and version you are currently on.

why head is importanct?

> use **git checkout comitId(or hash)** and you can go back to that version of commit and can creat new barnch, it's also called **head detached.**

note: when you create a new branch from **old commit** they are like temprory branch which will get deleted in future when started adding more commit to the current branch. watch this if you can't undersand "https://www.youtube.com/watch?v=HvDjbAa9ZsY&pp=ygUIZ2l0IGhlYWQ%3D"

### relative ref

> alternative way to get back old commit by entering the comand like **git checkout branchName^** this will get the head to the perent branch you can alway add more "^" to get back to the grand-parent branch or more future like this **"git checkout branchName^^"**. you can also include **"git checkout branchName head~number"** in the number secation assign number and you will go up to old commit.

**git branch -f main HEAD~number/branchId(or hash):** this command will change the postion of the branch by forcing it to go up.

how to reset old commit or get back to the old version?

> **git reset HEAD~number/branchId(or hash):** this reset the commit to the parent commit and the act like current comint never created.

**git revert HEAD/bracnhId(or hash):** this create a new commint by the parent branch but it will not remove the current branch like git reset does.
