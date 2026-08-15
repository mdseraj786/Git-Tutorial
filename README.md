1. `git init` -> Powers your folder to be managed by git, and initialises a new empty repository. It also creates a .git folder that has all the relevant logic to manage versions of your project.

2. `Working Area` ->  There can be a bunch of files that are not currently handled by git. It means that changes done or to be done in those files are not managed by git yet. A file which is in Working area is considered to be not in staging area. When we do `git status` and wee see abunch if `untracked files` then these are actually called to be in the working area.

3. `Staging area` -> What all files are going to be part of the next version that we will create. This staging area is the place where git knows waht changes will be done from the last version to the next version.


4. `Repositoryy Area` -> This area actually contains the details of all you previous registered version. And the files in this area, git already managed them and knows their version history.

5. `git add <file>` -> moves file from working area to stagin area

6. `git rm cached <file>` -> moves file back from staging area to working area.

7. `commit` -> Commit is a perticular version of the project. It captures a snapshot of the project's staged changes and creates a version out of it. 

8. `git commit` -> registers staging changes to a commit
8. `git commit --amend` -> aappend commit to last commit not create another commit, but commit id will changes due to hashing because date are changes that why

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


Merge conflicts can occure if multiple people try to make change to the same file, and then collaborate.

---
### Stash 
- it is a locker that store the content so that it will not be the part of the next commit.
- it follows LIFO to maintain the stash
- a peace of code that you want to store somewhere but you don't want to be the part of the next commit.
- add file into staging area and hit the command `git stash` all the staging are content goes into stash.

- If you want to back the content use `git stash apply` it gives back latest stash, but I you want to back some specific stash then use `git stash apply stash@(1)`.
- `git stash show stash@{0}` -> if you want to see the date store in the stash

- there can be multiple stashes are created 
- stashes are not going to create for the untracked file, they will only created for changes happened in tracked file(staging area). (in staging area or changes in staging are content)
- `git stash list ` -> show the list of the stashes
- everytime you create a stash it create new version of stash changes, 
if you want to apply a perticular version then you mentioned which version you want to apply
-  if you are try to apply 2 stash version that are going to change a single line, untill and unless you commited it won't even apply, or if it commited it gives merge conflict

- `git stash --include-untracked` -> untracked file also be the part of stash
- `git stash --include-untracked -- <filename> ` -> for the specific file

- `git stash --all` -> for all the file
- `git stash pop` -> work like apply but also remove/drop the last stash

- `git stash drop` -> drop/remove last stash
- `git stash drop stash@{2}`

- `git stash clear` -> drop all the stash

- `git stash save "saving code.cpp"`  -> giving meaningful name to stash
- `git stash save "saving new_file.cpp" --include-untracked` -> uses for untracked file 

- `Note: `latest stash is stash@{0}

---

### Branch
- Everyone called branch is a parallel timeline that you preparing another branch. - for understanding and visualizing this is good
- but in technical they are just - pointer to a commit

- `git checkout -b <name>` -> create ne branch, it is just a new commit on that same commit and latter adding child commit makes it branch


- <b> Head </b>  - it tells you that what branch you are working on and what's the current commit is. ---   head moves when you change the branch or commit new changes 

<b> first commit </b>  <-- second commit <--- (main branch)  <---  head 

- after creating the new branch feature_branch create on second commit and then head point to the feature_branch

 
first <-- second <-- main branch <br>
 &emsp;&emsp;&emsp;&emsp;&emsp;   ^ <br>
  &emsp;&emsp;&emsp;&emsp;&emsp;               |
  <br>
   &emsp;&emsp;&emsp;&emsp;&emsp;             feature_branch <---head 

   - if you commit on feature_branch third commit point to sencond commit and feature_branch or head move to the third commit

- git checkout --<filename>  --- it is going to override the staged area content to working are -- it means we are going to loose the working area content 

- `git checkout <commit_id> --<filename>` 

- `git checkout <commit_id> `      =>  Moves HEAD to a specific commit. This puts you in a detached HEAD state — it’s safe, but you’re no longer on a branch.

- git switch -    -> Jumps back to the previous branch you were on, effectively undoing that checkout.

- git checkout -- new_file.txt --- > it is actually override the file in local area which is present in staging area ----- loose the working area content


- git branch -f <branch> <commit_d>   -> if you move your branch to latest commit, you can loose you commit reference(dangling point) its called dangling commit

- Note: if you are using checkout to particular commit, means you are moving your head you are still safe, just use `git switch -`  to revert back. Even if you making some changes your branch pointer still referring that commit, but when you move to the other commit this reference lost -- it is called dangling commit

#### git clean

- git clean -f -> clean untracked file
- git clean --dry-run   -> tell us which file deleted by clean if you do but not deleted
- git clean -d --dry-run  -> tell use which folder deleted by if you clean 
- git clean -d   => clean the untrack folder
- git clean -d -f  --- > clean untrack file as well as directory/folder


#### git log

   - ``git reflog`` --- log history
   git log --graph  -> visual branch view
- `git log --all --decorate --oneline --graph` -> see the graph like structure

- `git log --since="yesterday"  or -- since="10 minute ago"` etc use for loggin
- `git log --grep=2nd`   -> use regex to match the commit message
- `git log --since=10.minutes`
- `git log <commitId>^1 ` ->  ^n -- it gives your nth parent
- `git log <commitId>~1  ->   ~n -- it gives you nth ancestory
#### Tag
- tag is also a pointer, it points a perticular commit, you can store come metadata in tag

- `diff bt branch and tag` -> branch chanes after new commit but tag doesn't 

- `git tag -a v1 -m "tag 1"`  -> create tag
- `git show v1` -> show tag details
- `git push --tags origin main` -> push your tags on github
- `git show-ref --tags`  -> show all of the tags

---
### Open-source contribution
Learn = open-source contribute
- find open-source code - facebook, google, google summer code listed companies

fork -> new copy of the whole project that you are going to create on your GitHub account

`git clone <link> ` -> copy the repository
create new branch - feature name ----- changes and then push in your branch ---- after that go to GitHub and compare and pull -- pull request

git pull git push 


upstream and downstream in git 
upstream is from where you clone the repository, and downstream is any project that integrates your work with other work,

--- 





#### git reset
- `git checkout <commit>` - goes head to the perticular commit, and It can still recover via `git switch <branch>`, if the branch still pointed to that commit.
- it only moves your head pointer.

- `git checkout <commit_id>` => head moves to commit , branch <main> does not move, you enter detached Head state, working directory matches that commit

- `git checkout main`  => to go back main branch

- git reset has three mode - 1. soft  2. mixed  3.hard

- `git reset --soft HEAD~ ` => move both branch or head to particular commit , changes stay in staged ,  last commit wala file staged me aa jata hai or jab 

- `git reset ORIG_HEAD  =>  brings commit back but changes become unstaged
Note:- we can only back if we are not reset twice 
-  ORIG_HEAD points to the last commit that you commited just before the last reset 

- `git reset --mixed <commit id>`   => (default), branch pointer and head pointer moves, changes are unstaged but kept last commit unstaged me chala jata hai , and working directory still same
- git reset ORIG_HEAD brings commit back but changes become unstaged

- `git reset --hard <commit id>`    => branch and head pointer move, working directory is reset, data is lost,  (dangerous if commits aren't pushed)
- Modified tracked files → deleted,  Staged tracked files → deleted, Untracked files → untouched
- when use reset ORIG_HEAD untracked remain same, in staged new file added deleted, and modified file make its previous state
 
- `git reset ORIG_HEAD`  => back to original - ORIG_HEAD is a bookmark, not magic undo
It moves pointers, It does NOT commit, It does NOT restore staging automatically


- checkout  = move HEAD only (safe visit)
- reset     = move branch + HEAD (rewrite history)

- soft      = undo commit → staged
- mixed     = undo commit → unstaged
- hard      = undo commit → erased (tracked only)

- ORIG_HEAD = previous HEAD pointer (no magic restore)


- `git reflog`  => get all of the commit that you made, this command manages the information recorded in reflog = it expires in 90 days(default)

#### git revert
- `git revert <commit>`   => make new commit with the opposite changes of the last commit
if you revert one commit it will automatically done, and if you revert more than one commit it will merge by manually done

#### git merge
- `git merge`  =>  extracted the branch but master is not move forward then you will git merge there are something called as  fast forward strategy --- in this just move the pointer low to high commit branch, other wise if the both branch conflict we need to merge commit need to happened  

- if there are merge conflict you manually conflict if it is not, It will created merge commit automatically.