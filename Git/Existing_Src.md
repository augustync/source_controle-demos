# Existing Source

We will need to create quick striucture of the project and then we will add it to Git and remove it.

```bash
mkdir -p new_project/files/{a,b}
touch new_project/README.md new_project/files/a/a.txt new_project/files/b/b.txt new_project/files/here.md
cd new_project
ls -l 
ls -l files
```

And we should see this structure
```bash
❯ ls -l
total 0
-rw-rw-r--  1 nonus25  staff    0 11 Apr 15:12 README.md
drwxrwxr-x  5 nonus25  staff  160 11 Apr 15:12 files
❯ ls -l files
total 0
drwxrwxr-x  3 nonus25  staff  96 11 Apr 15:12 a
drwxrwxr-x  3 nonus25  staff  96 11 Apr 15:12 b
-rw-rw-r--  1 nonus25  staff   0 11 Apr 15:12 here.md
```

View the Git status 
```bash
❯  git status
fatal: not a git repository (or any of the parent directories): .git
❯ ls -la
total 0
drwxrwxr-x   4 nonus25  staff   128 11 Apr 15:12 .
drwxr-xr-x+ 77 nonus25  staff  2464 11 Apr 15:17 ..
-rw-rw-r--   1 nonus25  staff     0 11 Apr 15:12 README.md
drwxrwxr-x   5 nonus25  staff   160 11 Apr 15:12 files
```

Now we can initialize the Git there
```bash
❯ git init
Initialized empty Git repository in /Users/nonus25/new_project/.git/
git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md
	files/

nothing added to commit but untracked files present (use "git add" to track)
```

To add all files to staging area we do 
```bash 
❯ git add .
❯ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   README.md
	new file:   files/a/a.txt
	new file:   files/b/b.txt
	new file:   files/here.md
```

files can be now commited. at once
```bash
❯ git commit -m "adding all in one commit"
[master (root-commit) adfc807] adding all in one commit
 4 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
 create mode 100644 files/a/a.txt
 create mode 100644 files/b/b.txt
 create mode 100644 files/here.md
```

Removing the Repo from Git only ...
```bash
❯ ls -la
total 0
drwxrwxr-x   5 nonus25  staff   160 11 Apr 15:18 .
drwxr-xr-x+ 77 nonus25  staff  2464 11 Apr 15:21 ..
drwxrwxr-x  12 nonus25  staff   384 11 Apr 15:20 .git
-rw-rw-r--   1 nonus25  staff     0 11 Apr 15:12 README.md
drwxrwxr-x   5 nonus25  staff   160 11 Apr 15:12 files
```
We have there .git directory which we have to remove it ... to remove the project from git.
```bash
❯  git status
On branch master
nothing to commit, working tree clean

❯ rm -rfv .git
.git/config
.git/objects/ad/fc80795f1b48f757e4238e4082739ea5660c56
.git/objects/ad
.git/objects/ec/5e386905ff2d36e291086a1207f2585aaa8920
.git/objects/ec
.git/objects/pack
.git/objects/28/712d44629e349bf1327994f051d58c0fac524b
.git/objects/28
.git/objects/info
.git/objects/65/a457425a679cbe9adf0d2741785d3ceabb44a7
.git/objects/65
.git/objects/e6/9de29bb2d1d6434b8b29ae775ad8c2e48c5391
.git/objects/e6
.git/objects/7f/f3dcc883007ca144c58738457cc487cc067056
.git/objects/7f
.git/objects
.git/HEAD
.git/info/exclude
.git/info
.git/logs/HEAD
.git/logs/refs/heads/master
.git/logs/refs/heads
.git/logs/refs
.git/logs
.git/description
.git/hooks/commit-msg.sample
.git/hooks/pre-rebase.sample
.git/hooks/pre-commit.sample
.git/hooks/applypatch-msg.sample
.git/hooks/fsmonitor-watchman.sample
.git/hooks/pre-receive.sample
.git/hooks/prepare-commit-msg.sample
.git/hooks/post-update.sample
.git/hooks/pre-merge-commit.sample
.git/hooks/pre-applypatch.sample
.git/hooks/pre-push.sample
.git/hooks/update.sample
.git/hooks
.git/refs/heads/master
.git/refs/heads
.git/refs/tags
.git/refs
.git/index
.git/COMMIT_EDITMSG
.git

❯ git status
fatal: not a git repository (or any of the parent directories): .git
❯ ls -la
total 0
drwxrwxr-x   4 nonus25  staff   128 11 Apr 15:23 .
drwxr-xr-x+ 77 nonus25  staff  2464 11 Apr 15:24 ..
-rw-rw-r--   1 nonus25  staff     0 11 Apr 15:12 README.md
drwxrwxr-x   5 nonus25  staff   160 11 Apr 15:12 files
```

And as we can see project been removed from Git Repository.

