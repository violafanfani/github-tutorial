
1. Install git on computer
2. Configure git
`git config --global user.name "First Last"`
`git config --global user.email "first.last@example.com"`

3. Check config
````
git config --list
````

# git

### Create new repo

Go to folder of interest
`cd myfolder`

Create a new folder that is gonna be the repository for the code (and 
data) and navigate into the folder
`mkdir new-git-project`
`cd new-git-project`

Check what's in the folder: `ls .`

Initialize repo (starts git history)
`git init`

### Track files

Now start adding and changing things in the repo
`nano readme.txt` or `touch readme.txt`

Check what's in the folder and check what's tracked by git
`ls` and `git status`

Add another file
` touch mydoc.md`


Add files to tracking

`git add readme.txt`

What happened (git status)?

```
⚡ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   readme.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	mydoc.md

```


Q: *Add and then untrack one file (mydoc)*

Usually you'll try to add all files and track all changes
`git add .`

Now we need to create a snapshot of the files in the repo. The **commit** 
is a recorded version in the git history, a snapshot of the repo, that is 
key for following and reverting things in the repo

`git commit -m 'created repo and added basic readme files'`


```
⚡ git commit -m 'created repo and added basic readme files'
[main (root-commit) b4cd57b] created repo and added basic readme files
 2 files changed, 1 insertion(+)
 create mode 100644 mydoc.md
 create mode 100644 readme.txt
```


You'll see that now the working tree is clean

Use `git log` to check the history of the repo


## Making changes to the repo

Change something within the docs file
`nano mydocs.md`

Check status and add+commit changes

```
git add .
git commit -m 'started writing down documentation file'
```

New git log


Q: *Change mydoc again and track them*

How do I revert it?

Check commit number from git log

`git checkout 9d929d1df3323f22b97e17cf5852fdad88b8ce4d --f mydoc.md`

`cat mydoc.md` to check the version of the file now

Add and commit.

## Github

Create repo on github and push our repo to remote

```
git remote add origin git@github.com:violafanfani/github-tutorial.git
git branch -M main
git push -u origin main
```


## Branches


Create new branch and move there

`git checkout -b first-branch`

Create, add and track newdoc.md

```
commit ee3b8c147aadf9fe4b354458bd744d928974ea1a (HEAD -> first-branch)
Author: violafanfani <viol.fanfani@gmail.com>
Date:   Thu Jan 9 17:45:10 2025 -0500

    new doc in first branch

commit e9318a18e1e2bb5d071a1f51f6fd9423a1e0a96e (origin/main, main)
Author: violafanfani <viol.fanfani@gmail.com>
Date:   Thu Jan 9 17:38:53 2025 -0500

    reverted mydoc

commit 535ddfc7d46e3bc1752e45805a19174257ef7e6a
Author: violafanfani <viol.fanfani@gmail.com>
Date:   Thu Jan 9 17:37:27 2025 -0500

    third commit

commit 9d929d1df3323f22b97e17cf5852fdad88b8ce4d
Author: violafanfani <viol.fanfani@gmail.com>
Date:   Thu Jan 9 17:34:43 2025 -0500

    started writing down documentation file

commit b4cd57b5f3e17ef00dc119007a9b5017ae017a29
Author: violafanfani <viol.fanfani@gmail.com>
Date:   Thu Jan 9 17:32:08 2025 -0500

    created repo and added basic readme files
```


Add branch to remote

`git push --set-upstream origin first-branch`


Now we merge, go into the branch you want to merge to, for instance, to 
put the new stuff from first-branch into the main branch (first-branch 
->main)

`git checkout main`
`git merge first-branch`

And as usual `git push`

Q: *What happened remotely?*



