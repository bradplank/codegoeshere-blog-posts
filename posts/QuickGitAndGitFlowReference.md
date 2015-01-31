Quick Git and Git Flow Reference
================================

Git Commands
--------

List all branches (local and remote):
**git branch -a**

Clean remote branch list:
**git remote prune origin**

Annotated tag:
**git tag -a v1.7 -m 'version v1.7'**

Share tag:
**git push origin v1.7**

Delete local branch:
**git branch -d feature/branchName**

Delete remote branch:
**git push oriting --delete feature/branchName**

Checkout a remote tag with a local tracking branch:
**git checkout -b v2.2.0 v2.2.0**

References
-------

Git Commands - [Git Cheat Sheet PDF](https://training.github.com/kit/downloads/github-git-cheat-sheet.pdf)
Git Command Interactions - [Interactive Cheat Sheet](http://ndpsoftware.com/git-cheatsheet.html)

Git Flow Commands
------------

**git flow init [-d]**

This will then interactively prompt you with some questions on which branches you would like to use as development and production branches, and how you would like your prefixes be named. You may simply press Return on any of those questions to accept the (sane) default suggestions.

The -d flag will accept all defaults.

```
Which branch should be used for bringing forth production releases?
   - master
Branch name for production releases: [master]
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []
```

**git flow feature start &lt;name&gt;**

**git flow feature finish &lt;name&gt;**

```
TODO
```

**git flow release start &lt;tag-name&gt;**

**git flow release finish &lt;tag-name&gt;**

```
TODO
```

**git flow hotfix start &lt;tag-name&gt;**

**git flow hotfix finish &lt;tag-name&gt;**

```
TODO
```

References
-------
Git - [Git Documentation](http://git-scm.com/docs)
git-flow - [GitHub Repository](https://github.com/nvie/gitflow)
Vincent Driessen - [Successful Git Branching Model Blog Post](http://nvie.com/posts/a-successful-git-branching-model/)
