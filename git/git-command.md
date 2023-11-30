### (Visti this site to recall any advanced topic) [https://learngitbranching.js.org/] or (visit this site to recall basic topics) 
 [https://www.w3schools.com/git/default.asp?remote=github].

# Git starter

**git init:** Initialize the directory. Starts tracking the directory.

**git status (--short):** Provides the status of changes in the directory.

- Flag --short: Gives a concise output to the status.

## Staging environment

Staged files are files that are ready to be committed to the repository you are working on. As you work, add, edit, and remove files. Use the staging environment for commits.

**git add (--all/./\*/-A or fileName):** Adds files to the staging environment.

- Flag "--all/./\*/-A" used to select all flies from a directory.
- Use "fileName" to add the selected file to the staging.

**git commit (-a -m "commit message"):** Commits changes from the staging area to remote repo. Git considers each commit change point or "save point".

- Flag -a used when you want to stage and commit together **although it is not recommended**.
- Flag -m used to add a commit message. when using -m flags always use double quotes to add a message.

**git push (repo url)or(remote name) (brancName):** push you local files to remote repo.

**git remote add/set-url (remote name) (repo url):** Create a remote name and you can always use it in place of URL.

- The add command will add a new remote name.
- set-url will update the URL.
- git remote list all the remote names.
- git remote remove (remote name).

**git log:** List all the commit history. use q to quit the git log.

## Git pull

**git fetch remoteName/repoURL:**use to fetch changes made in the remote repo (at GitHub).
tip: use "git status" after git fetch to see updates and then merge with your local repo to the remote repo using git merge origin/master.

**git differ remoteName/localBranchName (e.g. main):** show changes differ between local repo and remote repo.

**git pull:** It is a combination of fetch and merge. It is used to pull all changes from a remote repository into the branch you are working on.

## Git push

**git push (remoteName branchName):** Push the local file to the remote directory (GitHub).

- remoteName and branchName is optional.

**git checkout branchName:** to change the branch

- **git checkout -b branchName** will create and switch to the new branch.

**git branch branchName:** to create a new branch

- **git branch -d branchName:** flag -d used to delete the branch
- **git branch -a:** flag -a get you all the branches on the remote repo
- note: when git pull will not fetch all branch

**git merge branchName:** to merge to the branch (you can also merge the remote branch, so can update the local branch from the remote branch)

**git rebase branchName:** Git rebase is used to integrate changes from one branch into another by moving or combining commits, creating a linear commit history.

difference between git merge and git rebase:
> Git merge combines changes from different branches by creating a new commit, while Git rebase integrates changes by moving and reapplying commits to a new base, resulting in a linear commit history.


### Head
> "HEAD" points to the branch name and version you are currently on.


Why is important?
> Use **git checkout comitId(or hash)** and you can go back to that version of commit and create a new branch, it's also called **head detached.**
note: when you create a new branch from **old commit** they are like a temporary branch that will get deleted in the future when start adding more commit to the current branch. watch this if you can't understand "https://www.youtube.com/watch?v=HvDjbAa9ZsY&pp=ygUIZ2l0IGhlYWQ%3D"


### relative ref
> An alternative way to get back an old commit is by entering the command like **git checkout branchName^** this will get the head to the parent branch you can always add more "^" to get back to the grand-parent branch or more future like this **"git checkout branchName^^"**. you can also include **"git checkout branchName head~number"** in the number section assign a number and you will go up to the old commit.


**git branch -f main HEAD~number/branchId(or hash):** This command will change the position of the branch by forcing it to go up.

how to reset old commit or get back to the old version?

> **git reset HEAD~number/branchId(or hash):** this reset the commit to the parent commit and the act like current comint never created.

**git revert HEAD/bracnhId(or hash):** this create a new commint by the parent branch but it will not remove the current branch like git reset does.
