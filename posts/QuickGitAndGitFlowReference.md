Quick Git and Git Flow Reference
================================

Git Commands
--------

TODO

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
git-flow - https://github.com/nvie/gitflow
Vincent Driessen - http://nvie.com/posts/a-successful-git-branching-model/
