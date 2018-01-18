---
layout: post
author: Johan Abildskov
---

# Opinionated Git

## Should I rebase or merge?

A very common question is _"Should I merge or should I rebase?"_.
Always do rebases. It makes your history look prettier.

For a more in-depth look at the difference between the two approaches
please read [merge vs. rebase](http://edwardthomson.com/blog/merge_vs_rebase.html) by [Edward Thomson](https://twitter.com/ethomson).

## Should I use submodules for dependencies?

No, use a proper dependency management tool!

## Monorepo or many-repos

If you find yourself building specific tooling in order to accommodate a huge
repository, you should split up your repository.

## How do I spell Git?

Use Git for the tool, the community, the concept. use `git` for the cli tool.
Never user _GIT_, it is not an acronym?

## What is the recommended Git workflow

Do trunk based development - DORA says it is the best way to do.
Integrate often. Only long-lived branches should be maintenance branches.

Proactively deprecate maintenance branches that are no longer needed.

Have shortlived feature branches - they should not live longer than a day.

## Do not make commits on master

Isolate your changes to feature branches. Always assume you will be working on
more than one thing at a time. Feature branches allows for easier switching of
concepts

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
