# Glossary

This is a reduced version of https://git-scm.com/docs/gitglossary if some of the points are unclear please comment here or mention it to Oliver or Leandro and then we will try to replace the explanation with something more understandable.

## Bare Repository

A bare repository is normally an appropriately named [directory](#directory) with a `.git` suffix that does not have a locally checked-out copy of any of the files under revision control. That is, all of the Git administrative and control files that would normally be present in the hidden `.git` sub-directory are directly present in the `repository.git` directory instead, and no other files are present and checked out. Usually publishers of public repositories make bare repositories available.

## Branch

A "branch" is an active line of development. The most recent [commit](#commit) on a branch is referred to as the tip of that branch. The tip of the branch is referenced by a branch [head](#head), which moves forward as additional development is done on the branch. A single Git [repository](#repository) can track an arbitrary number of branches, but your [working tree](#working-tree) is associated with just one of them (the "current" or "checked out" branch), and [HEAD](#HEAD) points to that branch.

## Cache

Obsolete for: [index](#index).

## Checkout

The action of updating all or part of the [working tree](#working-tree) with a [tree object](#tree-object) or [blob](#blob-object) from the [object database](#object_database), and updating the [index](#index) and [HEAD](#HEAD) if the whole working tree has been pointed at a new [branch](#branch).

## Clean

A [working tree](#working-tree) is clean, if it corresponds to the [revision](#revision) referenced by the current [head](#head). Also see "[dirty](#dirty)".

## Commit

As a noun: A single point in the Git history; the entire history of a project is represented as a set of interrelated commits. The word "commit" is often used by Git in the same places other revision control systems use the words "revision" or "version". Also used as a short hand for [commit object](#commit-object).

As a verb: The action of storing a new snapshot of the project’s state in the Git history, by creating a new commit representing the current state of the [index](#index) and advancing [HEAD](#HEAD) to point at the new commit.

## Commit object

An [object](#object) which contains the information about a particular [revision](#revision), such as [parents](#parent), committer, author, date and the [tree object](#tree-object) which corresponds to the top [directory](#directory) of the stored revision.

## Detached HEAD

Normally the [HEAD](#HEAD) stores the name of a [branch](#branch), and commands that operate on the history HEAD represents operate on the history leading to the tip of the branch the HEAD points at. However, Git also allows you to [check out](#checkout) an arbitrary [commit](#commit) that isn’t necessarily the tip of any particular branch. The HEAD in such a state is called "detached".

Note that commands that operate on the history of the current branch (e.g. `git commit` to build a new history on top of it) still work while the HEAD is detached. They update the HEAD to point at the tip of the updated history without affecting any branch. Commands that update or inquire information _about_ the current branch (e.g. `git branch --set-upstream-to` that sets what remote-tracking branch the current branch integrates with) obviously do not work, as there is no (real) current branch to ask about in this state.

## Directory

The list you get with "ls" :-)

## Dirty

A [working tree](#working_tree) is said to be "dirty" if it contains modifications which have not been [committed](#commit) to the current [branch](#branch).

## Evil merge

An evil merge is a [merge](#merge) that introduces changes that do not appear in any [parent](#parent).

## Fast-Forward

A fast-forward is a special type of [merge](#merge) where you have a [revision](#revision) and you are "merging" another [branch](#branch)'s changes that happen to be a descendant of what you have. In such a case, you do not make a new [merge](#merge) [commit](#commit) but instead just update to his revision. This will happen frequently on a [remote-tracking branch](#remote-tracking-branch) of a remote [repository](#repository).

## Fetch

Fetching a [branch](#branch) means to get the branch’s [head ref](#head-ref) from a remote [repository](#repository), to find out which objects are missing from the local [object database](#object-database), and to get them, too.

## File System

Linus Torvalds originally designed Git to be a user space file system, i.e. the infrastructure to hold files and directories. That ensured the efficiency and speed of Git.

## Gitfile

A plain file `.git` at the root of a working tree that points at the directory that is the real repository.

## Hash

In Git’s context, synonym for [object name](#object-name).

## head

A [named reference](#ref) to the [commit](#commit) at the tip of a [branch](#branch). Heads are stored in a file in `$GIT_DIR/refs/heads/` directory, except when using packed refs.

## HEAD

The current [branch](#branch). In more detail: Your [working tree](#working-tree) is normally derived from the state of the tree referred to by HEAD. HEAD is a reference to one of the [heads](#head) in your repository, except when using a [detached HEAD](#detached-HEAD), in which case it directly references an arbitrary commit.

## head ref

A synonym for [head](#head).

## Hook

During the normal execution of several Git commands, call-outs are made to optional scripts that allow a developer to add functionality or checking. Typically, the hooks allow for a command to be pre-verified and potentially aborted, and allow for a post-notification after the operation is done. The hook scripts are found in the `$GIT_DIR/hooks/` directory, and are enabled by simply removing the `.sample` suffix from the filename. In earlier versions of Git you had to make them executable.

## Index

A collection of files with stat information, whose contents are stored as objects. The index is a stored version of your [working tree](#working-tree). Truth be told, it can also contain a second, and even a third version of a working tree, which are used when [merging](#merge).

## Index entry

The information regarding a particular file, stored in the [index](#index). An index entry can be unmerged, if a [merge](#merge) was started, but not yet finished (i.e. if the index contains multiple versions of that file).

## Master

The default development [branch](#branch). Whenever you create a Git [repository](#repository), a branch named "master" is created, and becomes the active branch. In most cases, this contains the local development, though that is purely by convention and is not required.

## Merge

As a verb: To bring the contents of another [branch](#branch) (possibly from an external [repository](#repository)) into the current branch. In the case where the merged-in branch is from a different repository, this is done by first [fetching](#fetch) the remote branch and then merging the result into the current branch. This combination of fetch and merge operations is called a [pull](#pull). Merging is performed by an automatic process that identifies changes made since the branches diverged, and then applies all those changes together. In cases where changes conflict, manual intervention may be required to complete the merge.

As a noun: unless it is a [fast-forward](#fast-forward), a successful merge results in the creation of a new [commit](#commit) representing the result of the merge, and having as [parents](#parent) the tips of the merged [branches](#branch). This commit is referred to as a "merge commit", or sometimes just a "merge".

## Object

The unit of storage in Git. It is uniquely identified by the [SHA-1](https://en.wikipedia.org/wiki/SHA-1) of its contents. Consequently, an object can not be changed.

## Object database

Stores a set of "objects", and an individual [object](#object) is identified by its [object name](#object-name). The objects usually live in `$GIT_DIR/objects/`.

## Object identifier

Synonym for [object name](#object-name).

## Object name

The unique identifier of an [object](#object). The object name is usually represented by a 40 character hexadecimal string. Also colloquially called [SHA-1](https://en.wikipedia.org/wiki/SHA-1).

## Object type

One of the identifiers "[commit](#commit-object)", "[tree](#tree-object)", "[tag](#tag-object)" or "[blob](#blob-object)" describing the type of an [object](#object).

## Origin

The default upstream [repository](#repository). Most projects have at least one upstream project which they track. By default _origin_ is used for that purpose. New upstream updates will be fetched into [remote-tracking branches](#remote-tracking-branch) named origin/name-of-upstream-branch, which you can see using `git branch -r`.

## Glob

Git treats the pattern as a shell glob suitable for consumption by fnmatch(3) with the FNM_PATHNAME flag: wildcards in the pattern will not match a / in the pathname. For example, "Documentation/\*.html" matches "Documentation/git.html" but not "Documentation/ppc/ppc.html" or "tools/perf/Documentation/perf.html".

Two consecutive asterisks ("`**`") in patterns matched against full pathname may have special meaning:

- A leading "`**`" followed by a slash means match in all directories. For example, "`**/foo`" matches file or directory "`foo`" anywhere, the same as pattern "`foo`". "`**/foo/bar`" matches file or directory "`bar`" anywhere that is directly under directory "`foo`".

- A trailing "`/**`" matches everything inside. For example, "`abc/**`" matches all files inside directory "abc", relative to the location of the `.gitignore` file, with infinite depth.

- A slash followed by two consecutive asterisks then a slash matches zero or more directories. For example, "`a/**/b`" matches "`a/b`", "`a/x/b`", "`a/x/y/b`" and so on.

- Other consecutive asterisks are considered invalid.

  Glob magic is incompatible with literal magic.

## Exclude

After a path matches any non-exclude pathspec, it will be run through all exclude pathspecs (magic signature: `!` or its synonym `^`). If it matches, the path is ignored. When there is no non-exclude pathspec, the exclusion is applied to the result set as if invoked without any pathspec.

## Parent

A [commit object](#commit-object) contains a (possibly empty) list of the logical predecessor(s) in the line of development, i.e. its parents.

## Pull

Pulling a [branch](#branch) means to [fetch](#fetch) it and [merge](#merge) it.

## Push

Pushing a [branch](#branch) means to get the branch’s [head ref](#head-ref) from a remote [repository](#repository), find out if it is a direct ancestor to the branch’s local head ref, and in that case, putting all objects, which are [reachable](#reachable) from the local head ref, and which are missing from the remote repository, into the remote [object database](#object-database), and updating the remote head ref. If the remote [head](#head) is not an ancestor to the local head, the push fails.

## Rebase

To reapply a series of changes from a [branch](#branch) to a different base, and reset the [head](#head) of that branch to the result.

## Ref

A name that begins with `refs/` (e.g. `refs/heads/master`) that points to an [object name](#object-name) or another ref (the latter is called a [symbolic ref](#symref)). For convenience, a ref can sometimes be abbreviated when used as an argument to a Git command. Refs are stored in the [repository](#repository).

The ref namespace is hierarchical. Different subhierarchies are used for different purposes (e.g. the `refs/heads/` hierarchy is used to represent local branches).

There are a few special-purpose refs that do not begin with `refs/`. The most notable example is `HEAD`.

## Refspec

A "refspec" is used by [fetch](#fetch) and [push](#push) to describe the mapping between remote [ref](#ref) and local ref.

## Remote repository

A [repository](#repository) which is used to track the same project but resides somewhere else. To communicate with remotes, see [fetch](#fetch) or [push](#push).

## Remote-tracking branch

A [ref](#ref) that is used to follow changes from another [repository](#repository). It typically looks like _refs/remotes/foo/bar_ (indicating that it tracks a branch named _bar_ in a remote named _foo_), and matches the right-hand-side of a configured fetch [refspec](#refspec). A remote-tracking branch should not contain direct modifications or have local commits made to it.

## Repository

A collection of [refs](#ref) together with an [object database](#object-database) containing all objects which are [reachable](#reachable) from the refs, possibly accompanied by meta data from one or more [porcelains](#porcelain). A repository can share an object database with other repositories via [alternates mechanism](#alternate-object-database).

## Resolve

The action of fixing up manually what a failed automatic [merge](#merge) left behind.

## Revision

Synonym for [commit](#commit) (the noun).

## Rewind

To throw away part of the development, i.e. to assign the [head](#head) to an earlier [revision](#revision).

## SHA-1

"Secure Hash Algorithm 1"; a cryptographic hash function. In the context of Git used as a synonym for [object name](#object-name).

## Stash entry

An [object](#object) used to temporarily store the contents of a [dirty](#dirty) working directory and the index for future reuse.

## Submodule

A [repository](#repository) that holds the history of a separate project inside another repository (the latter of which is called [superproject](#superproject)).

## Superproject

A [repository](#repository) that references repositories of other projects in its working tree as [submodules](#submodule). The superproject knows about the names of (but does not hold copies of) commit objects of the contained submodules.

## Symref

Symbolic reference: instead of containing the [SHA-1](https://en.wikipedia.org/wiki/SHA-1) id itself, it is of the format _ref: refs/some/thing_ and when referenced, it recursively dereferences to this reference. _[HEAD](#HEAD)_ is a prime example of a symref. Symbolic references are manipulated with the [git-symbolic-ref\[1\]](/docs/git-symbolic-ref) command.

## Tag

A [ref](#ref) under `refs/tags/` namespace that points to an object of an arbitrary type (typically a tag points to either a [tag](#tag-object) or a [commit object](#commit-object)). In contrast to a [head](#head), a tag is not updated by the `commit` command. A Git tag has nothing to do with a Lisp tag (which would be called an [object type](#object-type) in Git’s context). A tag is most typically used to mark a particular point in the commit ancestry [chain](#chain).

## Tag object

An [object](#object) containing a [ref](#ref) pointing to another object, which can contain a message just like a [commit object](#commit-object). It can also contain a (PGP) signature, in which case it is called a "signed tag object".

## Topic branch

A regular Git [branch](#branch) that is used by a developer to identify a conceptual line of development. Since branches are very easy and inexpensive, it is often desirable to have several small branches that each contain very well defined concepts or small incremental yet related changes.

## Tree

Either a [working tree](#working-tree), or a [tree object](#tree-object) together with the dependent [blob](#blob-object) and tree objects (i.e. a stored representation of a working tree).

## Tree object

An [object](#object) containing a list of file names and modes along with refs to the associated blob and/or tree objects. A [tree](#tree) is equivalent to a [directory](#directory).

## Unmerged index

An [index](#index) which contains unmerged [index entries](#index-entry).

## Unreachable object

An [object](#object) which is not [reachable](#reachable) from a [branch](#branch), [tag](#tag), or any other reference.

## Upstream branch

The default [branch](#branch) that is merged into the branch in question (or the branch in question is rebased onto). It is configured via branch.<name>.remote and branch.<name>.merge. If the upstream branch of _A_ is _origin/B_ sometimes we say "_A_ is tracking _origin/B_".

## Working tree

The tree of actual checked out files. The working tree normally contains the contents of the [HEAD](#HEAD) commit’s tree, plus any local changes that you have made but not yet committed.
