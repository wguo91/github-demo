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

origin is a reference to our github repository (remote reference, the name "origin" is a convention), master refers to the master branch of a repository
```
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

Always pull before you push for best practice (below is a local master push to remote master push)
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

-A will recursively add changes and update files that have been renamed, moved, or deleted outside git(git add -A is equivalent to git add . followed by git add -u)
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

Compare arbitrary commit to last commit, HEAD refers to last commit in current branch
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


