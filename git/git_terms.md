What is git?
> A stupid content tracker. Git is fundamentally a content-addressable filesystem with a VCS user interface written on top of it.

What does a content-addressable filesystem mean? 
> This means that at the core of Git is a simple key-value data store i.e you can insert any kind of content into a Git repository, for which Git will hand you back a unique key which you can use later to reterive that content.

What is `.git` repository?
 > Is a hidden directory where Git contains all information required for version control.
`.git` is initilaized by `git init`. `.git` contains all the inforamtion required for version control.
`.git` contains:
- 4 files:
    - `HEAD` - this file points to the branch you currently have checked out
    - `config` - project-specific configuration options
    - `decription` - file used only by GitWeb
    - `index` - staging area
- 4 sub-directiories:
    - `objects/` - all `objects` i.e stores all the content for your database (object database)
    - `refs/` - pointers to `commit` objects in that data(`branches`, `tags`, `remotes`, and more)
    - `info/` - keeps a global `exclude` file for ignored patterns that you don't want to track in a `.gitignore` file
    - `hooks` - contains client or server-side hook scripts
- 3 objects:
    - `blob` - files
    - `tree` - directories
    - `commit` - reference to a `tree`, parent `commit`
- 2 objects sub-directiories:
    - `.git/objects/pack` - 
    - `.git/objects/info` -

How does Git store content? 
> As a single file per piece of content, named with the `SHA-1` checksum of the content and its header.The subdir is named with first two characters of the `SHA-1` and the filname is the remaining 38 characters.
All content is stored as `tree` or `blob` objects, `trees` corresponding to UNIX directories entries and `blobs` corresponding more or less to `inodes` or file contents.

What are plumbing commands?
> Low level commands that were designed to be chanined UNIX-style or called from scripts.
```python
git help git
git help -av
```
What are porcelain commands? 

User friendly commands.

What is a branch? 
> A `branch` is a simple pointer or reference to the head of a line of work.

What is a working tree? 

What is a working directory? 

What is worktree?

What is a repository? 

What is a local repository?

What is a remote repository?

What is a bare repository?

What is a blob object?
> Blob means a sequence of bytes.
> A Git blob (binary large object) is the object type used to store the contents of each file in a repository.

What is the index?

What is a tag object?

`tag` object is fourth object type in Git. A `tag` object is very much like `commit` object - it contains a tagger, a date, a message and a pointer.
The main difference is that `tag` object generally points to a `commit` rather than a `tree`. Its like a `branch` reference, but it never moves - it always points to the same `commit` but gives it a friendlier name.

What are the two types of `tag`? 

- `annotated` - more complex, git creates a `tag` object and then writes a `reference` to point to it rather than directly to the `commit` (created by using `git tag -a <>`
- `lightweight` - a `reference` that never moves.

What is master?

What is main?

What is HEAD?

`HEAD` file is a symbolic `reference` to the `branch` you're currently on.

What is head?

What is a named reference?

What is a `commit` object?

It specifies the top-level `tree` for the snapshot of the project a that point, the parent `commits` if any, the author/committer information, a blank line and then the `commit` message. Each `commit` ojbect points to snapshot `tree`.

What is heads(refs/heads/main)?

What is head (named reference)?

What is a head ref?

What is checkout?

What is commit-ish?

What is tree-ish?

What is detached HEAD?

What is a directory?

What is clean working tree?

What is dirty working tree?

What is merge?

What is object?

What is origin?

What is pull?

What is push?

What is rebase?

What is refs or references?

A simple name for a file in which `SHA-1` value is stored so that you don't have to use `SHA-1` value.These are stored under `.git/refs` directory

What is reflog?

What is refspec?

What is remote-tracking branch?

What is tree?

What is a tree object?

Solves the problem of storing the filename and also allows you to store a group of files together.
A single `tree` object contains one or more entries, each of which is a the `SHA-1` hash or a `blob` or `subtree` with its associated mode, type and filename.

What does `git cat-file` command do?

Command to inspect Git objects.

What does `git cat-file -p master^{tree}` command do?

`master^{tree}` syntax specifies the `tree` object that is pointed to by the last commit on your `master` branch.

How does Git create a `tree` object?

Git creates a `tree` by taking the state of your staging area or `index` and writing a series of `tree` objects from it.
So, to create a `tree` object you first have to set up an index by staging some files.

What are the only 3 file modesi valide for files(`blobs`) in Git? 

- `100644` - normal file
- `100755` - executable file
- `120000` - symbolic link

What does `git write-tree` command do?

To write the staging area out to a `tree` object.

What does `git write-tree` command do?

To read `trees` into your staging area.

What happens when you run `git add` and `git commit` ?

When you run these commands:
    - Git stores `blobs` for the files that have changed
    - Git updates index
    - Git writes out `trees` 
    - Git writes `commit` objects that reference the top-level `trees` and the `commits` that came immediately befor them.

What are the three main Git objects?

- the `blob`
- the `tree`
- the `commit`

How does the object storage work?

- A header is stored with every object you commit to your Git object database.

How to see the history of your repository reachable from a `commit` say `1a41aa`?

Run `git log 1a41aa`

What happens when you run `git branch <branch>` ? 

Git runs `update-ref` command to add the `SHA-1` of the last `commit` of the `branch` you're on into whatever new `reference` you want to create.

How does Git know the `SHA-1` of the last `commit` when you run `git branch <branch>` ? 

`HEAD` file.
`HEAD` file is a symbolic `reference` to the `branch` you're currenlty on.
A symboic reference, unlike a normal reference, it contains a pointer to another `reference`

What is a `detached HEAD` ? 

In cases ehre the `HEAD` file may contain the `SHA-1` value of a git `object`. This happens when you `checkout` a `tag`, `commit`, or a `remote branch` which puts your repository in a `detached HEAD` state.

What happens when you run `git commit`?

Git create the `commit` object, specifying the parent of the that `commit` object to be whatever `SHA-1` value the `reference` in `HEAD` points to.

How to read the value of your `HEAD` ?

Run `git symboic-ref HEAD`

What are the 3 types of `references` ? 
Run command `git show-ref`
- `refs/heads`
- `refs/tags`
- `refs/remotes`

What is a `remote` reference?

If you add a `remote` and push to it, Git stores the value you last pushed to that `remote` for each `branch` in `refs/remotes`directory.For instance, you can add a `remote` called `origin` and push your `main` branch to it.

How do `remote` references differ from `branches`(`refs/heads references`) ?

`remote` references are considered read-only. You can `git checkout` to one but git won't symbolically reference `HEAD` to one, so you will never update it with a `commit` command.
Git manages them as bookmarks to the last know state of where those `branches` were on those servers.

What is a loose object?

The initial format in which Git saves objects on disk.

What are dangling object? 

The `blob` objects that aren't pointed to by a `commit`.

What is a packfile(`.pack`) ?

Git packs several `loose` objects into a single binary file called `packfile` in oder to save space and be more efficient.
git does this automatically or you could use `git gc`
The `packfile` is a single file containing the contents of all the objects that were removed from your filesystem.

What is a `.idx` file?

The index is a file that contains offsets into the packfile so you can quickly seek to a specific object.

How does git pack objects?

Git looks for files that are named and sized similarly, and stores just the deltas from one version of the file to the next.
Run `git verify-pack` to look into a packfile
Check out that the second version of the file is the one that is stored intact, whereas the original version is stored as a delta - this is becausse you're most likely to need faster access to the most recent version of the file.
