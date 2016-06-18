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
git commit -m
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

origin is a reference to our github repository (remote reference), master refers to the master branch of a repository
```
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```
