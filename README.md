README

Basic Git commands:
```
git config --global --list
git config --global user.name "Wilson Guo"
git config --global user.email "wguo91@gmail.com"
git init
git init project-name
git clone https://github.com/wguo91/github-demo.git
git status
git add
git add .
git commit
git commit -m "message here"
git pull origin master 
git push origin master
```

Set global editor to Atom
```
git config --global core.editor "atom --wait"
```

Confirm global editor is set to atom
```
git config --global -e
```

Sample commit message (root-commit means this is the FIRST commit of the repository)
```
[master (root-commit) 5e93393] Adding new file with hipster ipsum I can use multiple line commit messages
```

origin is a reference to our github repository (remote reference, the name "origin" is a convention), master refers to the master branch of a repository, always pull before you push for best practice
```
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

Below is a local master push to remote master push result (hence the two masters)
```
To https://github.com/wguo91/starter-web.git
   4beb7f0..2a259e0  master -> master
```

Add all modified tracked files (excluding newly added files) and commit with inline message:
```
git commit -am "message here"
```

List all tracked files:
```
git ls-files
```

Unstage files and revert to previous state:
```
git reset HEAD your-file-here.txt
git checkout -- your-file-here.txt
```

Rename and move (if you do not preface command with git, git will interpret rename as removing the old file and adding a newly renamed file), if we want to undo a rename, simply rename the file back to its original name
```
git mv your-file-name.txt your-new-file-name.txt
```

Removing files and recovering removed files from staging (half-completion not available, make sure you type out the entire name)
```
git rm file.txt
git reset HEAD file.txt
git checkout -- file.txt
```

-A will recursively add changes and update files that have been renamed, moved, or deleted outside git (git add -A is equivalent to git add . followed by git add -u)
```
git add -A
```

Renaming in OSX Finder will result in a .DS_Store (operating system file), so we need to add the correct files individually and then tell git we renamed the file using the -u flag 
```
git add -u
```

Other helpful options, including commit histories (git log displays in reverse chronological order), abbreviated SHA1 identifiers, displaying commits in a decorated graph, displaying a range of commits, displaying commits from a certain time period, displaying commits involving a certain file, displaying commits that follow the renames of a certain file, displaying diff information for a certain commit
```
git help log
git log
git log --abbrev-commit
git log --oneline --graph --decorate
git log 43287f1...ae502fd
git log --since="3 days ago"
git log -- file.txt
git log --follow -- level1/level2/level2.txt
git show a3ed055e83ae868bf534c6592ff2da1ab9333c01
```

Logs display SHA1 identifier (can typically be shortened), author, and date
```
commit 43287f1cf7fa85e422e3134ee7bdf29ce39878f3
Author: Wilson Guo <wguo91@gmail.com>
Date:   Sat Jun 18 00:07:09 2016 -0700
```

Create your own git command
```
git config --global alias.hist "log --all --graph --decorate --oneline"
```

Add a .gitignore file to ignore unwanted files and folders (pattern examples below)
```
specific: myfile.ext
file pattern: *.ext
folder: my-folder/
```

Set P4Merge as the designated diff and merge tool and disable prompts for both
```
git config --global diff.tool p4merge
git config --global difftool.p4merge.path /Applications/p4merge.app/Contents/MacOS/p4merge
git config --global difftool.prompt false
git config --global merge.tool p4merge
git config --global mergetool.p4merge /Applications/p4merge.app/Contents/MacOS/p4merge
git config --global mergetool.prompt false
```

Compare differences between working directory and staging area
```
git diff
git difftool
```

Compare differences between working directory and git repository (last commit)
```
git diff HEAD
git difftool HEAD
```

Compare differences between staging area and git repository (last commit) 
```
git diff --staged HEAD
git difftool --staged HEAD
```

Limit diff to only one file
```
git diff -- file.txt
git difftool -- file.txt
```

Compare arbitrary commit to last commit, HEAD is a ref (reference) to the currently checked out commit of the current branch
```
git log --oneline
git diff e9ac0a0 HEAD 
git diff e9ac0a0 a3ed055 
```

Compare HEAD and the one commit before HEAD
```
git diff HEAD HEAD^
git difftool HEAD HEAD^
```

Compare master branch on local repository and the master branch on git repository
```
git diff master origin/master
git difftool master origin/master
```

List local branches 
```
git branch
```

List local and remote branches 
```
git branch -a
```

Create branch and switch to the new branch, remember that branches are simply pointers 
```
git branch mynewbranch
git checkout mynewbranch
```

Rename branch and delete branch (cannot delete branch you are currently on)
```
git branch -m mynewbranch newbranch
git branch -d newbranch
```

b parameter will create the branch before checking it out (the branch did not exist previously)
```
git checkout -b title-change
```

Switch back to master after changes to your feature branch, then merge the changes from feature (fast-forward branch merge), note that no changes were done on the master branch previously; we can delete the feature branch once the change has been merged
```
git merge title-change
```

Non fast-forward branch merge, so we use --no-ff to disable the fast-forward capability to preserve the fact that we branched off
```
git merge --no-ff
```

Merge with message parameter (automatic merge)
```
git merge simple-change -m "merging changes from simple-change"
```

Invoke p4merge to resolve the conficts (we can do this manually if desired)
```
git mergetool
```

Remove untracked files (first one tells user what git clean -f will do)
``` 
git clean -n
git clean -f 
```

Rebasing (on feature branch) is another method to merge two branches together, this involves replaying features that were committed on one branch and replaying them on top of another; use it to incorporate master branch changes into your current feature branch to prevent merging headaches later on
```
git rebase master 
```

Rebase options (add your changes first)
```
When you have resolved this problem, run "git rebase --continue". 
If you prefer to skip this patch, run "git rebase --skip" instead. 
To check out the original branch and stop rebasing, run "git rebase --abort".
```

Fetch is a non-destructive command that updates the references between the remote and the local repositories
```
git fetch origin master
```

Pull with rebase (in case you need to grab whatever changes that were made on the remote master branch)
```
git pull --rebase origin master
```



