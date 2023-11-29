# Git starter

**git init:** Initialize the directory. Starts tracking this directory.

**git status <--short>:** Provides the status of changes in the directory.

- Flag --short: Gives a concise output to the status.

## Staging enviroment

Staged files are files that are ready to be committed to the repository you are working on. As you work, add, edit, and remove files. Use the staging environment for commits.

**git add <--all/./\*/-A> or <fileName>:** Adds files to the staging environment.

- Flag "--all/./\*/-A" used to select all flies from directory.
- Use "fileName" to add selected file to the staging.

**git commit <-a -m "commit message">:** Commits changes from the staging area to remote repo. Git considers each commit change point or "save point".

- Flag -a used when you want to stage and commint together although it is not recomended.
- Flag -m used to add commit message. when using -m flags always use double quotes to add message.

**git push <repo url> or <remote name>:** push you local files to remote repo.

**git remote <remote name> <repo url>:** create remote name and you can always use in the place of url.

- git remote list all the remote name.
- git remote remove <remote name>
