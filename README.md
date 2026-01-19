1. `git init` -> Powers your folder to be managed by git, and initialises a new empty repository. It also creates a .git folder that has all the relevant logic to manage versions of your project.

2. `Working Area` ->  There can be a bunch of files that are not currently handled by git. It means that changes done or to be done in those files are not managed by git yet. A file which is in Working area is considered to be not in staging area. When we do `git status` and wee see abunch if `untracked files` then these are actually called to be in the working area.

3. `Staging area` -> What all files are going to be part of the next version that we will create. This staging area is the place where git knows waht changes will be done from the last version to the next version.


4. `Repositoryy Area` -> This area actually contains the details of all you previous registered version. And the files in this area, git already managed them and knows their version history.

5. `git add <file>` -> moves file from working area to stagin area

6. `git rm cached <file>` -> moves file back from staging area to working area.

7. `commit` -> Commit is a perticular version of the project. It captures a snapshot of the project's staged changes and creates a version out of it. 

8. `git commit` -> registers staging changes to a commit

9. `git log` -> list downs all the commits of the repository. If you want to log prompt press `q`

10. `git restore <file>` -> It removes all files changes from the staging area to be committed. This can be useful, if we did some dirty piece of code and now no more want it. Instead of deleting every change line by line, we can restore it or you can say restore last clean version of the file.

11. `git restore --staged <file>` -> it removes file from changes from staging area to working area. This only words if changes are in your staging area.

12. `Difference between git rm and git remove`
ans: If you want to the whole file back to the untracked state, then we do git rm, otherwise if we just want the changes to be moved in working area or staging area then we use git restore.

13. `git diff commit1 commit2` -> gives the difference of all the file changes between two commits

14. `git commit -m "your commit message>"` -> If we want to avoid opening a text editor like vim/namo to add commit message we use this command.

15. `git remote` -> list down all the remote connection name

16. Remote connection -> It helps you to link two git repositories for uploading and downloading changes from each other 

17. `git remote add <name of remote> <link of the remote>` -> This command helps us to add a new link to the remote repo and give a name to it.

18. `git remote rm <name of remote>` -> this command deletes a remote connection

19. `git remote rename <oldname> <newname>` -> this command renames the remote connection

Note: The name of the remote connections is always used to establish communication between the repos

20. `git add <file1> <file2> <file3>` : this command will add multiple file changes together in the staging area

21. `git add . ` : this command will add all the files from working area to staging area 

22. `git pull <remote name> <branch name>` : downloads latest changes from the branch of the mentioned remote in your local repo.

    
### Recommended practice to do
 - make changes
 - git add <file>
 - git commit 
 - git pull
 - git push 
