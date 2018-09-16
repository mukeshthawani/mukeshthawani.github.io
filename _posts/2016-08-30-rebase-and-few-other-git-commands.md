---
layout: post
title: Rebase and few other git commands
excerpt: "This post is for listing some useful git commands other than what we commonly use."
modified: 2016-08-15
tags: [git, VCS]
comments: true
---

*Updated on 2018-09-16*

There are some git commands which we may not use daily, but they are useful in a lot of cases. In this post, I will list some of that git commands with their description.

So here starts the list:

### To edit the HEAD commit (i.e last commit) you can use:

 `git commit --amend.`

1. For changing message of last commit - just use `git commit --amend` then change your message in editor and save.

2. To change your files of last commit - change your files then `git add` then `git commit -amend` to update last commit files or add new one in that commit.

We can do the same using rebase also which I will explain later in this article.

Warning: You should not perform this steps if you have already pushed your last commit, it will create issues for other. 🔥


There are many different use cases of modifying commits:

### Squashing many commits into one single commit

This is useful when you are working on a feature and you want to merge multiple commits into one. Normally when implementing a feature we divide the process into small parts and, once it gets completed we create a new commit for that. You should create a different branch for a particular feature and do this inside that.

Now to squash the multiple commits into one single commit, we will use `rebase`.

Rebasing rewrites the history of the project by creating new commits. So, if you use rebase and push this branch to remote, it will create an issue for others because their history is different. You should use it on your local branches without creating a dirty state for others.

Here we want to squash commits into one so we need to see which ones to squash, for that there is something called Interactive Rebasing.

`git rebase -i <branch>`

So let's say you want to squash last 3 commits so you will use:
 `git rebase -i HEAD~3`
Here the number is 3 because we want to rewrite the last three commits. Then you will see the interactive rebasing tool with first three commit messages and a few other options. Here to combine the last two commits into first one change option of last two commits which is pick to squash.

Use `git rebase -i --root`
to modify all the history even the root commit.

### Update commit message

If you want to update the message of your last commit, we will use interactive rebasing which we did in our last step. There is one more way to do it using `git commit --amend -m "your new message"` which we already saw earlier but using rebasing is better as there you have option to edit more commits.

So use:
`git rebase -i HEAD~1`
then the same editor will open, change the option to `reword` and save the file. After that editor will open again now change the message and save the file.

Now your commit is updated with new message.

**Always remember to play locally i.e create a new branch for every feature because here if you apply rebase or other commands(where history can change), you don't have to worry about history as your master branch is clean. Also it will save others because they won't see their history getting affected. One more benefit of this is that if somebody updates remote branch with new commits then you can pull it from master and then rebase it into branch you are working on (if you need that commits that are changed in upstream) this way it won't create a new merge commit like it does when you use merge not rebase.**


### To revert back x commits

Use:

`git checkout COMMIT .`

Where COMMIT is the commit hash.
`.` at the end is used to apply changes to the whole tree.

To undo this:

`git reset --hard; `


### To add only specific lines

`git add -p`

it will interactively let you add, skip, or split diff hunks.

### To see the changes after adding

`git diff --staged`

Normally we just use `git diff` but that only works before staging.

### To see the commit differences between git branches

`git log master..branch-X`

This will show you the list of commits that branch-X has but master doesn't.

### To checkout only the specific lines

`git checkout -p`

### To see the changes in a commit

`git show COMMIT`

The COMMIT parameter is a commit-ish.

### To undo git add

`git reset`

Your changes will be unstaged and ready for you to re-add as you want. It is useful when you want to unstage multiple files but you want to keep that changes.

### Merge Git branches without using checkouts

As long as you're doing a fast-forward merge, then you can simply use

`git fetch <remote> <sourceBranch>:<destinationBranch>`

Use `git checkout [revision] .Examples:`

Merge local branch foo into local branch master,
without having to checkout master first.
Here `.` means to use the local repository as the "remote":

`git fetch . foo:master`

😎 💻
