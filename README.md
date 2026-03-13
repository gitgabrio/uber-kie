uber-kie
========

PoC of aggregating the different kie repositories behind a single one.
The provided pom is meant to coordinate the build of each of them.
For this PoC, I have linked personal and outdated main branches of forked repository, to avoid any possible clash and interaction with official ones

git subtree
===========
Git subtree is a git feature that lets you nest one repository inside another as a sub-directory. It is one of several ways Git projects can manage project dependencies.

In a nutshell, linked repository remain to be independent, and can be managed as standalone git repositories.
But, at the same time, the subtree functionality include them inside the parent repository.
From that parent repository, is possible to pull the changes from the linked repositories.
It would be also possible to make modification in the parent repository and push them in the linked one, but it would be better to not use that feature to avoid issues for conflicts and similar on the linked repository.


Crash course guide:

1. include a remote repository as a subtree:

```bash
git subtree add --prefix {local directory being pulled into} {remote repo URL} {remote branch} --squash
```

2. pull changes from the subtree:
```bash
git subtree pull --prefix {local directory being pulled into} {remote repo URL} {remote branch} --squash
```

NOTES: 
git subtree commands can not be invoked with uncommited status of the repository.

Further readings:

1. [Introduction](https://www.atlassian.com/git/tutorials/git-subtree)
2. [Mastering Git subtrees](https://comprendre-git.com/en/commands/mastering-git-subtrees/)
3. [Git Subtree Basics](https://gist.github.com/SKempin/b7857a6ff6bddb05717cc17a44091202)
4. [Introducing the Space Git Subtree](https://blog.jetbrains.com/space/2023/11/21/space-git-subtree/)
5. [git-man git-subtree](https://manpages.debian.org/testing/git-man/git-subtree.1.en.html)




pom aggregator
==============
That PoC contains also a pom.xml so that all the linked repository are considered as maven submodules and could be built together by maven itself



