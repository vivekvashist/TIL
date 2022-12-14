**What is git?**

> git is just a fancy key value store. The keys are SHA-1 hash of the contents of the objects and the values are content
> 
> A stupid content tracker. Git is fundamentally a content-addressable filesystem with a VCS user interface written on top of it.Git is a Distributed Version Control System(DVCS).Git is not a delta-based version control, Git thinks of its data more like a series of snapshots of a miniature filesystem.
> 
> Git thinks about its data more like a `stream of snapshots`
> 
> Git basically takes a picture of what all your files look like at that moment and stores a `reference` to that snapshot.To be efficient, if files have not changed, Git doesn't store the file again, just a link to the previous identical file it has already stored.
> 
> Nearly every opteration in Git is local.
> 
> Everything in git is checksumed before it is stored and then referred to by that checksum.This means, it is impossible to change the contents of any file/directory without Git knowing about it.You can't lose information in transit or get file corruption without Git being able to detect it.The mechanism that Git uses for this checksumming is called SHA-1 hash.This hash is calculated based on the contents of a file or directory structure in Git.
> 
> Git stores everything in its database not by file name but by the hash value of its contents.
> 
> Nearly all git actions only add data to git database.It is hard to get the system to do anything that is not undoable or to make it erase data in anyway. Once you `commit` a snapshot into Git it is very difficutlt to lose, especially if you regularly push your database to another repository.

**What are the 3 main states that files can reside in Git?**

> 1.`modified` - means you have changed the file but have not committed it to your database yet.If it was changed since it was checked out but has not been staged, it is modified.
> 
> 2.`staged` - means you have maked a modified file in its current version to go into your next commit snapshot. If it has been modified and was added to the staging area it is staged.
> 
> 3.`committed` - means that the data is safely stored in your local database. If a particular version of a file is in the Git directory, it is considered committed.

**What are the 3 main sections of a Git project?**

>1. `working tree` - is a single checkout of one version of the project.These files are pulled out of the compressed database in the Git directory and placed on disk for you to use and modify.
>
>2. `staging area` - is a file,(technical name is `index`) contained in your Git directory, that stores information about what will go into your next commit.
>
>3. `Git directory` - is where Git stores the metadata and object database for your project.This is what gets copied when you `clone` a repository from another computer.

**What is the basic git workflow?**

>1. You modifiy files in your `working tree`
>
>2. You selectively stage just those changes you want to be part of your next commit, which adds only those changes to the staging area.
>
>3. You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently in your Git repository.

**What are the 3 places where `git config` variables can be stored?**

>1.`[path]/etc/gitconfig` file - contains values applied to every user on the system and all their repositories.`git config --system`
>
>2. `~/.gitconfig` or `~/.config/git/config` file - personal git values to you, the user.`git config --global` (affects all of the repositories you work with on your system.
>
>3. `config` file - inside the Git directory this is specific to that single repository. `git config --local`

**What is the command to view all config settings and where they are coming from?**

> `git config --list --show-origin`

**How do you query Git as to the origin for a value to tell you which configuration file had the final say in setting that value?**

> `git cofnig --show-origin rerer.autoUpdate`

**What is a DVCS?**

> clients fully mirror the repository including its full history. Every clone is really a full backup of all the data. 

**What is a patch?**

> Differences between files.

**What does a content-addressable filesystem mean?**

> This means that at the core of Git is a simple key-value data store i.e you can insert any kind of content into a Git repository, for which Git will hand you back a unique key which you can use later to reterive that content. Method of storing information so that it may be retrieved based on its content.

**What is `.git` repository?**

 > Is a hidden directory where Git contains all information required for version control. `.git` is initilaized by `git init`. `.git` contains all the inforamtion required for version control. `.git` contains:
>
> - 4 files:
>
> - 1.`HEAD` - this file points to the branch you currently have checked out
>
> - 2.`config` - project-specific configuration options
>
> - 3.`decription` - file used only by GitWeb
>
> - 4.`index` - staging area
>
> - 4 sub-directiories:
>
> - 1.`objects/` - all `objects` i.e stores all the content for your database (object database)
>
> - 2.`refs/` - pointers to `commit` objects in that data(`branches`, `tags`, `remotes`, and more)
>
> - 3.`info/` - keeps a global `exclude` file for ignored patterns that you don't want to track in a `.gitignore` file
>
> - 4.`hooks` - contains client or server-side hook scripts
>
> - 3 objects:
>   - `blob` - files
>   - `tree` - directories
>   - `commit` - reference to a `tree`, parent `commit`
>
> - 2 objects sub-directiories:
>  - `.git/objects/pack`
>  - `.git/objects/info`

**How does Git store content?**

> As a single file per piece of content, named with the `SHA-1` checksum of the content and its header.The subdir is named with first two characters of the `SHA-1` and the filname is the remaining 38 characters.
>  
> All content is stored as `tree` or `blob` objects, `trees` corresponding to UNIX directories entries and `blobs` corresponding more or less to `inodes` or file contents.

**What are plumbing commands?**

> Low level commands that were designed to be chanined in UNIX-style or called from scripts.
```python
git help git
git help -av
```
**What are porcelain commands?**

> User friendly Git commands.

**What is a branch?**

> A `branch` is a simple pointer or reference to the head of a line of work.
> 
> Branches are pointer to commits

**What is a working tree?**

> Equivalent to `working directory`

**What is a working directory?**

> Think of working directory as a `sandbox`, where you can try changes out before committing them to your staging area(index) and then to history. Working directory (also commonnly referred to as working tree).The other two trees `index` and `HEAD` store their content in an efficient but inconvenient manner inside `.git` folder. The working directory unpacks them into actual files, which makes it much easier to edit them.

**What is worktree?**

**What is a repository?**

**What is a local repository?**

**What is a remote repository?**

**What is a bare repository?**

**What is a blob object?**

> Blob means a sequence of bytes. A Git blob (binary large object) is the object type used to store the contents of each file in a repository.
> a blob contains file contents

**What is the index?**

> `index` is your proposed next commit.This is also refered to as staging area as this is what git looks at when you run `git commit`
> 
> Git polulates this index with a list of all file contents that were last checked out into your working directory and what they looked like when they were orginally checked out.When you replace some of those files with new versions of them, and `git commit` converts that into the tree for new commit.
> 
`git ls-files -s` shows what your index currently looks like.The index is not technically a tree structure - its implementd as a flattened manifest but for our purposes its close enough.

**What is a tag object?**

> `tag` object is fourth object type in Git. A `tag` object is very much like `commit` object - it contains a tagger, a date, a message and a pointer. The main difference is that `tag` object generally points to a `commit` rather than a `tree`. Its like a `branch` reference, but it never moves - it always points to the same `commit` but gives it a friendlier name.

**What are the two types of `tag`?**

> - `annotated` - more complex, git creates a `tag` object and then writes a `reference` to point to it rather than directly to the `commit` (created by using `git tag -a <>` `lightweight` - a `reference` that never moves.

**What is master?**

**What is main?**

**What is HEAD?**

> `HEAD` file is a symbolic `reference` to the `branch` you're currently on. `HEAD` is a pointer to the current branch reference,which is in turn a pointer to the last commit made on that branch.That means `HEAD` will be the parent of the next commit that is created.
> Think of `HEAD` as the snapshot of your last commit on that branch.

**What is head?**

**What is a named reference?**

**What is a `commit` object?**

> It specifies the top-level `tree` for the snapshot of the project a that point, the parent `commits` if any, the author/committer information, a blank line and then the `commit` message. Each `commit` ojbect points to snapshot `tree`.
> commits are NOT diffs!

**What is heads(refs/heads/main)?**

**What is head (named reference)?**

**What is a head ref?**

**What is checkout?**

> When you checkout a branch, it changes `HEAD` to point to the new branch ref, populates your `index` with the snapshot of that `commit`,then copies the contents of the `index` into your `working directory`.

**What is commitish?**

> Short form for commit hashes.

**What is treeish?**

> Short form for tree hashes.

**What is detached HEAD?**

**What is a directory?**

**What is clean working tree?**

**What is dirty working tree?**

**What is merge?**

**What is object?**

**What is origin?**

**What is pull?**

**What is push?**

**What is rebase?**

**What is refs or references?**

> A simple name for a file in which `SHA-1` value is stored so that you don't have to use `SHA-1` value.These are stored under `.git/refs` directory

**What is reflog?**

> `reflog` is a local command

**What is refspec?**

**What is remote-tracking branch?**

**What is tree?**

> Think of Git being a content manager of three different trees. Trees here means collection of files not specifically the data structure.

**What are the three trees (not tree object/data structure) git manages and manipulates?**

> `HEAD` - last commit snapshot, next parent
>
> `index` - proposed next commit snapshot
>
> `working directory` - sandbox

**What is a tree object?**

> Solves the problem of storing the filename and also allows you to store a group of files together. A single `tree` object contains one or more entries, each of which is a the `SHA-1` hash or a `blob` or `subtree` with its associated mode, type and filename.
> 
> A tree contains folder contents, contains names of files and folders inside
> 
> contains blobs (files) and trees(folders)
> 
> includes file mode (unix file permissions)

**What does `git cat-file` command do?**

> Command to inspect Git objects.

**What does `git cat-file -p master^{tree}` command do?**

> `master^{tree}` syntax specifies the `tree` object that is pointed to by the last commit on your `master` branch.

**How does Git create a `tree` object?**

> Git creates a `tree` by taking the state of your staging area or `index` and writing a series of `tree` objects from it. So, to create a `tree` object you first have to set up an index by staging some files.

**What are the only 3 file modes valide for files(`blobs`) in Git?**

> - `100644` - normal file
>
> - `100755` - executable file
>
> - `120000` - symbolic link

**What does `git write-tree` command do?**

> To write the staging area out to a `tree` object.

**What does `git write-tree` command do?**

To read `trees` into your staging area.

**What happens when you run `git add` and `git commit` ?**

> `git add` - is used to begin tracking new files , to stage files, marking merge-conflicted files as resolved
>
> `git add` - think `add precisely this content to the next commit` rather then `add this file to the project`
>
> git stages file at it is when you run `git add` i.e a file can be listed as both staged and unstaged
>
> if you modify a file after you run `git add` you will have to run `git add` again to stage the latest version of the file
>
When you run these commands:
>    - Git stores `blobs` for the files that have changed
>    - Git updates index
>    - Git writes out `trees` 
>    - Git writes `commit` objects that reference the top-level `trees` and the `commits` that came immediately befor them.

**How does the object storage work?**

> A header is stored with every object you commit to your Git object database.

**How to see the history of your repository reachable from a `commit` say `1a41aa`?**

> Run `git log 1a41aa`

**What happens when you run `git branch <branch>` ?**

>Git runs `update-ref` command to add the `SHA-1` of the last `commit` of the `branch` you're on into whatever new `reference` you want to create.

**How does Git know the `SHA-1` of the last `commit` when you run `git branch <branch>` ?**

> `HEAD` file.
>
> `HEAD` file is a symbolic `reference` to the `branch` you're currenlty on.
>
> A symboic reference, unlike a normal reference, it contains a pointer to another `reference`

**What is a `detached HEAD` ?**

> In cases where the `HEAD` file may contain the `SHA-1` value of a git `object`. This happens when you `checkout` a `tag`, `commit`, or a `remote branch` which puts your repository in a `detached HEAD` state.

**What happens when you run `git commit`?**

> Git creates the `commit` object, specifying the parent of the that `commit` object to be whatever `SHA-1` value the `reference` in `HEAD` points to.

**How to read the value of your `HEAD` ?**

> Run `git symboic-ref HEAD`

**What are the 3 types of `references` ?**

> Run command `git show-ref`
> - `refs/heads`
>
> - `refs/tags`
>
> - `refs/remotes`

**What is a `remote` reference?**

> If you add a `remote` and push to it, Git stores the value you last pushed to that `remote` for each `branch` in `refs/remotes`directory.For instance, you can add a `remote` called `origin` and push your `main` branch to it.

**How do `remote` references differ from `branches`(`refs/heads references`) ?**

> `remote` references are considered read-only. You can `git checkout` to one but git won't symbolically reference `HEAD` to one, so you will never update it with a `commit` command. Git manages them as bookmarks to the last know state of where those `branches` were on those servers.

**What is a loose object?**

> The initial format in which Git saves objects on disk.

**What are dangling object?**

> The `blob` objects that aren't pointed to by a `commit`.

**What is an orphan or dangling commit?**

> A `commit` that is not reachable by a `branch`

**What is a packfile(`.pack`) ?**

> Git packs several `loose` objects into a single binary file called `packfile` in order to save space and be more efficient. git does this automatically or you could use `git gc` The `packfile` is a single file containing the contents of all the objects that were removed from your filesystem.

**What is a `.idx` file?**

> The index is a file that contains offsets into the packfile so you can quickly seek to a specific object.

**How does git pack objects?**

> Git looks for files that are named and sized similarly, and stores just the deltas from one version of the file to the next.
>
> Run `git verify-pack` to look into a packfile
>
> Check out that the second version of the file is the one that is stored intact, whereas the original version is stored as a delta - this is becausse you're most likely to need faster access to the most recent version of the file.

**What is `origin main` vs `origin/main`?**

**What is `origin master` vs `origin/master`?**

**What is a SHA-1 hash?**

> Individual fingerprint for the content.

**What is fast-forward merge?**
>

**What is non fast-forward merge?**

**What is master?**

> `master` is the state of master branch on local repository

**What is main?**

> `main` is a local branch

**What is origin/master?**

> `origin/master` is the state of master branch on the remote repository

**What is origin/main?**

> is a remote trakcing branch(which is a local copy of the branch named `main` on the remote `origin`
>
> `origin/main` branch is local.

**What is origin/HEAD?**

> `origin/HEAD` is the default branch for the remote named `origin`

**What is origin?**

> `origin` is a remote

**How do you obtain a Git repository on your local machine?**

> 1. Take a local project directory that is not under VC, and turn it into Git repository
> 
> 2. Clone an existing Git repository from elsewhere

**What happens when you run `git clone <url>`?**

> Git receives a full copy of nearly all data that the server has, every version of every file for the history of the project is pulled down by default and checks out a `working copy` of the latest version.
> 
> When you clone a repository, all of the your files will be tracked and unmodified because Git just checked them out and you haven't edited anything

**What is a hunk?**

> When comparing two files, diff finds sequences of lines common to both files, interspersed with groups of differing lines called hunks
>
> Each hunk shows one area where the files differ. 
>
> more details -  http://www.gnu.org/software/diffutils/manual/html_node/Hunks.html

**What are untracked files?**

> Files that are in you directory that but have not been added to `.git` repository to be tracked

**What are the three modes of Git reset command?**

> `--hard`
>
> `--mixed` (default)
>
> `--soft`

**What is Git revert?**

**What is Git reset?**

**What is `filter-branch`?**

**When to use ~ vs ^?**

> Use `~` most of the time - to go back a number of generations, usually what you want. Tilde `~` is almost linear in appearence and wants to go backward in a straight line.
>
> Use `^` on merge commits - because they have two or more(immediate) parents. Caret `^` suggests an interesting segment of a tree or a fork in the road

**What are the two states that a file can be in a `working directory`?**

> `tracked` - (are the files that git knows about) tracked files are files that were in the last snapshot, as well as newly staged files, any newly staged files they can be unmodified, modified or staged.
>
> `untracked` - any files that were not in your last snapshot and are not in your staging area. When you clone as you edit files git sees them as modified because you've changed them since your last commit.
>
> Untracked means Git sees a file you didn't have in the previous snapshot(commit), and which hasn't yet been staged,git won't start including it in your commit snapshot until you explicitly tell it to do so.

**What does `working tree clean` mean's when you run `git clone` on a freshly cloned project?**

> This means you have a clean working directory, none of your tracked files are modified.And there are no untacked files

**How can you tell that the file is staged?**

> `git status` command `Changed to be committed` shows the file is not tracked and staged to be committed.

**In `git status` what does `Changes not staged for commit` mean?**

> If a file appears under `Change not staged for commit` section means that is tracked and has been modified in the working directory but not yet staged.

**what does `git status -s` mean?**

> `git status -s` is more simplified version of `git status` command
>
> `git status -s` has to two columns, LHS is status of staging area and RHS is the status of working tree
>
> `??` - new files that aren't tracked - untracked
>
> `A ` - `Added` - new files that have been added to staging area or added to index
> 
> `M ` - modifiled and stagd

**What questions does `git diff` answer?**

> What have you changed but not yet staged?
>
> What have you staged that you are about to commit?
>
> `git status` show the files listing 
>
> `git diff` - shows the exact lines added and removed - the patch as it were.
>
> `git diff` - compares whats is in your working directory with whats in your staging area
>
> `git diff --staged` - compares your staged changes to your last commit
>
> `git diff` - by itself doesn't show all changes made since your last commit - only changes that are still unstaged.If you have staged all your changes `git diff` will give you no output.
>
> `git diff --cached` - `--staged` and `--cached` are synonyms i.e what have you staged so far

**What does a commit record?**

> A commit records the snapshot you setup in your staging area.Every time you perform a commit you're recording a snapshot of your project that you can rever to or compare to later.

**How can you remove a file from Git?**

> To remove a file from Git, you have to remove it from your tracked files(more accurately, remove it from your staging area) and then commit.
> 
> `git rm` command does that and alro removes the file from your working directory so that you don't see it as untracked file next time around.
> 
> If you simply remove the file from your working directory, it shows up under the "Changes not staged for commit"(that is unstaged) area of `git status` output.

**How can you keep a file in your working tree but remove it from your staging area?**

> To keep a file on your hard drive but not have Git track it anymore, this is particularly useful if you forgot to add something to your `.gitignore` and accidentally staged it, like a large log file.To do this use `git rm --cached FILENAME`
> 
> You can pass files, directories and file-glob patterns to `git rm` 

**How do you move files in Git?**

> Git doesn't explicitly track file movement.If you rename a file in git, no metadata is stored in git that tells it you renamed the file.
> 
> To rename a file in git `git mv file_from file_to`
> 
> this is equivilant to running `git rm file` and then `git add file`

**How can you show the difference (the patch output) introduced in each commit?**

> run `git log -p 1`
> 
> run `git log --stat` - to see summary/abbreviated stats for each commit
> 
> run `git log --pretty=oneline` - useful at looking at lots of commits other options are `short`, `full`, `fuller`
> 
> run `git log --pretty=format:"%h -%an, %ar : %s"` - allows you to specify your own log output format, useful when you're generating output for machine parsing
> 
> run `git log --graph` - nice ASCII graph showing your branch and merge history
> 
> run `git log --since=2.weeks` - time limiting options such as `--since` and `--until`
> 
> run `git log -S function_name` - git's "pickaxe" which takes a string and shows only those commits that changed the number of occurrences of that string.
> 
> run `git log -- [path/to/file]` - filter as a path to limit the log output to commits that introduced a change to those files
> 
> run `git log --no-merges` - merge commits aren't very informattive depending your workflow

**What does a commit object contain?**

> A root tree
> A lis tof parent commits
> A commit message
> An author name, email, time
> An committer name, email, time

**How does working directory, staging, committed related?**

> [WORKING DIRECTORY] --[git add]--> [STAGING AREA] --[git commit]--> [REPOSITORY]

**How do you undo if you commit too early or forge tto add some files or mess up your commit message?**

> use `git commit --amend` - this command takes your staging area an uses it for the commit.
> 
```python
git commit -m 'initial commit'
git add forgotten_file
git commit --amend
```
> with this you end up with a single commit - the second commit replaces the results of the first
>
> only amend commits that are still local and have not been pushed somewhere.
>
> amending last commit is not fixing it as in replacing it entirely with a new improved commit that pushes the old commit out of the way and puts a new commit in its place.Effectively as if previous never happend and it wont show up in your repository history.

**how to unmodify a modified file with `git restore`?**

> run `git restore --staged <file>
> 
> Note: `git restore` is a dangerous command any local changes you made to that file are gone. Git replaces the file with the last staged or committed version
