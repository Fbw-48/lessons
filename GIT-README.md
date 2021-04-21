## Basic Git commands

Here is a list of some basic Git commands to get you going with Git.
1. Git slides  
   [Slides ](https://github.com/hnsreeny/git/)

1. Official Documentation  
   [Git scm Doc](https://git-scm.com/doc)

1. Git Glossary  
   [Git Glossary](./git/glossary.md)

1. Github Training videos  
   [Github on Youtube](https://www.youtube.com/watch?v=noZnOSpcjYY&list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-&index=1)

1. Intro videos  
   [Git SCM Videos](https://git-scm.com/videos)

1. A cheat sheet for the most common git commands:  
   [Git Cheat Sheet](./git/git-cheatsheet-EN-grey.pdf)

### git setting

#### SSh Key

[Github](https://help.github.com/en/enterprise/2.15/user/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

#### New repo

```
echo "# YOUR-REPO-NAME" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:YOUR-ACCOUNT/YOUR-REPO.git
git push -u origin master

```

#### upstream

If you have cloned repository from someone and it would update often and you want to get those updates from time to time, then instead of editing origin it would be best to add a new remote:

```
$ git remote rename origin upstream
$ git remote add origin https://github.com/YOUR-ACCOUNT/YOUR_REPO
# or
git remote add origin git@github.com:YOUR-ACCOUNT/YOUR-REPO.git
```

Then whenever you want to check if there is changes from upstream, you can do:

```
$ git fetch upstream
```

However if you want to pull from the original repo you will use:

```
$ git pull upstream master
```

##### Tell Git who you are

Configure the author name and email address to be used with your commits. 
Note that Git strips some characters (for example trailing periods) from user.name.

```
git config --global user.name "Your Name" 
git config --global user.email yourmail@example.com
```

##### Create a new local repository 	  	

```
git init
```

###### Check out a repository 

Create a working copy of a local repository: 	
```
git clone /path/to/repository
```

For a remote server, use: 	
```
git clone username@host:/path/to/repository
```

###### Add files

Add one or more files to staging (index): 	

```
git add <filename>
git add *
```

##### Commit

Commit changes to head (but not yet to the remote repository): 	
```
git commit -m "Commit message"
```

Commit any files you've added with git add, and also commit any files you've changed since then: 	
```
git commit -a
```

##### Push

Send changes to the master branch of your remote repository: 	
```
git push origin master
```

##### Status
List the files you've changed and those you still need to add or commit: 	

```
git status
```

##### Connect to a remote repository
If you haven't connected your local repository to a remote server, add the server to be able to push to it:
```
git remote add origin <server>
```

List all currently configured remote repositories:
```
git remote -v
```

##### Branches

Create a new branch and switch to it: 	

```
git checkout -b <branchname>
```

Switch from one branch to another: 	
```
git checkout <branchname>
```

List all the branches in your repo, and also tell you what branch you're currently in: 	
```
git branch
```

Delete the feature branch: 	
```
git branch -d <branchname>
```

Push the branch to your remote repository, so others can use it: 	
```
git push origin <branchname>
```

Push all branches to your remote repository: 	
```
git push --all origin
```

Delete a branch on your remote repository: 	
```
git push origin :<branchname>
```

##### Update from the remote repository

Fetch and merge changes on the remote server to your working directory:

```
git pull
```

To merge a different branch into your active branch: 	
```
git merge <branchname>
```

View all the merge conflicts:
View the conflicts against the base file:
Preview changes, before merging:

```
git diff
git diff --base <filename>
git diff <sourcebranch> <targetbranch>
```

After you have manually resolved any conflicts, you mark the changed file: 	
```
git add <filename>
```


##### Tags

You can use tagging to mark a significant changeset, such as a release: 	
```
git tag 1.0.0 <commitID>
```

CommitId is the leading characters of the changeset ID, up to 10, but must be unique. Get the ID using: 	
```
git log
```

Push all tags to remote repository: 	
```
git push --tags origin
```

##### Undo local changes

If you mess up, you can replace the changes in your working tree with the last content in head:

Changes already added to the index, as well as new files, will be kept.
	
```
git checkout -- <filename>
```

Instead, to drop all your local changes and commits, fetch the latest history from the server and point your local master branch at it, do this: 	
```
git fetch origin
git reset --hard origin/master
```

##### Search
Search the working directory for foo():
```
git grep "foo()"
```

##### Fix the last commit message with "commit --amend"
You just typo’d the last commit message, you did git commit -m "Fxies bug #42" but before git push you realized that really should say “Fixed commit message”.

```
git commit --amend -m "Fixed commit message"
```

What’s happening: git commit --amend will update and replace the most recent commit with a new commit that combines any staged changes with the contents of the previous commit. With nothing currently staged, this just rewrites the previous commit message.


##### git revert - Undo a “public” change
You just ran git push, sending your changes to GitHub, now you realize there’s a problem with one of those commits. You’d like to undo that commit.

```
git revert <SHA>
```

What’s happening: git revert will create a new commit that’s the opposite (or inverse) of the given SHA. If the old commit is “matter”, the new commit is “anti-matter”—anything removed in the old commit will be added in the new commit and anything added in the old commit will be removed in the new commit.

This is Git’s safest, most basic “undo” scenario, because it doesn’t alter history—so you can now git push the new “inverse” commit to undo your mistaken commit.

##### git reset - Reset “local” changes

You’ve made some commits locally (not yet pushed), but everything is terrible, you want to undo the last three commits—like they never happened.

```
git reset --hard <last good SHA>
```

What’s happening: git reset rewinds your repository’s history all the way back to the specified SHA. It’s as if those commits never happened. By default, git reset preserves the working directory. The commits are gone, but the contents are still on disk. This is the safest option, but often, you’ll want to “undo” the commits and the changes in one move—that’s what --hard does.


##### Stashing your work

The git stash command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy.

```
git stash "Some description"
git stash list
```


##### Re-applying your stashed changes

You can reapply previously stashed changes with git stash pop:

```
$ git stash pop 
```

Popping your stash removes the changes from your stash and reapplies them to your working copy.

Alternatively, you can reapply the changes to your working copy and keep them in your stash with git stash apply:

```
$ git stash apply
```

This is useful if you want to apply the same stashed changes to multiple branches. 



#### More Git Resources

* [The official Git site](https://git-scm.com/)
* [Git from the inside out](https://codewords.recurse.com/issues/two/git-from-the-inside-out)
* [Pro Git (Book)](https://git-scm.com/book/en/v2)
* [Common Git commands](http://guides.beanstalkapp.com/version-control/common-git-commands.html)

#### Other Resources

* [Basic writing and formatting syntax](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
* [What is Markdown? (Wikipedia)](https://en.wikipedia.org/wiki/Markdown)
* [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
