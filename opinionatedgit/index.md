---
layout: post
author: Johan Abildskov
---

# Opinionated Git

## Should I rebase or merge

A very common question is _"Should I merge or should I rebase?"_.
Always do rebases. It makes your history look prettier.

For a more in-depth look at the difference between the two approaches
please read [merge vs. rebase](http://edwardthomson.com/blog/merge_vs_rebase.html) by [Edward Thomson](https://twitter.com/ethomson).

## Should I use submodules for dependencies

No, use a proper dependency management tool!

Also note that subtree and subrepo should be avoided.

## Monorepo or many-repos

If you find yourself building specific tooling in order to accommodate a huge
repository, you should split up your repository.

## How do I spell Git

Use Git for the tool, the community, the concept. use `git` for the cli tool.
Never user _GIT_, it is not an acronym!

## What is the recommended Git workflow

Do trunk based development - DORA says it is the best way to do.
Integrate often. Only long-lived branches should be maintenance branches.

Proactively deprecate maintenance branches that are no longer needed.

Have shortlived feature branches - they should not live longer than a day.

There is no such thing as hotfix branches. Especially when we are doing something urgent, 
we do not want to skip our pipeline and workflow. This is how production gets borked.

## Do not make commits on master

When you are making a change to your code base, isolate your development on
a separate branch. This allows for easier and safer experimentation.

It also allows you to easily switch context, should you feel the need to
investigate different versions of your code, or the pressure to switch context
because something is burning.

## Only fast-forward merge the master branch

If you do not have any automate the correct workflow for getting changes to the
master branch is:
1. `git checkout feature/branchname`
2. `git rebase master`
3. Test everything!
4. `git checkout master`
5. `git merge feature/branchname`

Isolate your work, preserve your master branches.

## Practice Continuous Integration

Automate your quality criteria. Protect your master branch as that perfect
truth it is.

## On commit messages

Commit messages are important, and there are some many great examples of bad commit messsages.

A commit message should concisely describe what is the consequence of applying a commit.

In real life you will also be using a task management system, a commit should be done in context of a task, and such the task should be referenced from the commit.

Take advantage of the fact that you have both a _subject_ and a _body_ to elaborate on your commit message. Put task references in the _body_.

I expect you to make small commits, so I don't want to see a novel in the commit message. It is probably better suited either in a changelog, the documentation or inline in the code.

Read [How to Write a Git Commit message](https://chris.beams.io/posts/git-commit/) by Chris Beams.
