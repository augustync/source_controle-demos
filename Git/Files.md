# Working with Files

### Editing and Tracked Files

To check what files are tracked in Git repository 
```bash
git ls-files
```
```bash
CONTRIBUTION.md
Jenkinsfile
LICENSE
README.md
_config.yml
docker-src/Dockerfile
docker-src/run.sh
me.txt
og-kafka-mm/.helmignore
og-kafka-mm/Chart.yaml
og-kafka-mm/templates/NOTES.txt
og-kafka-mm/templates/_helpers.tpl
og-kafka-mm/templates/deployment.yaml
og-kafka-mm/templates/jmx-configmap.yaml
og-kafka-mm/templates/mm-configmap.yaml
og-kafka-mm/templates/service.yaml
og-kafka-mm/values.yaml
scripts/common.sh
scripts/lint.sh
scripts/package.sh
```

to get file to tracked git repository we need too add it to git.
```bash
git add untracked.file
```

If we want to commit all files in which we made changes we should use 
```bash
git commit -am "commiting all files"
```

### Backing Out changes

First we will add some extra lines to one of the file to actually at the end back them out
```bash
❯  ll
total 72
drwxrwxr-x  15 nonus25  staff    480 11 Apr 18:12 .git
-rw-rw-r--   1 nonus25  staff    654 11 Apr 18:04 CONTRIBUTION.md
-rw-rw-r--   1 nonus25  staff     81 11 Apr 18:04 Jenkinsfile
-rw-rw-r--   1 nonus25  staff  11357 11 Apr 18:04 LICENSE
-rw-rw-r--   1 nonus25  staff   5153 11 Apr 18:04 README.md
-rw-rw-r--   1 nonus25  staff     26 11 Apr 18:04 _config.yml
drwxrwxr-x   4 nonus25  staff    128 11 Apr 18:04 docker-src
-rw-rw-r--   1 nonus25  staff     25 11 Apr 18:05 me.txt
drwxrwxr-x   6 nonus25  staff    192 11 Apr 18:04 og-kafka-mm
drwxrwxr-x   5 nonus25  staff    160 11 Apr 18:04 scripts
❯ echo "Adding extra line to see Backing out process" >> me.txt
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   me.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

```bash
❯ git commit -am "Added an extra line to the file"
[master 06be12d] Added an extra line to the file
 1 file changed, 1 insertion(+)

❯ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```

#### Removing the last commit
To remove the last commit from git, you can simply run 
```bash 
git reset --hard HEAD~
```
If you are removing multiple commits from the top, you can run 
```bash
git reset --hard HEAD~2 
```
to remove the last two commits. You can increase the number to remove even more commits.
If you want to "uncommit" the commits, but keep the changes around for reworking, remove the "--hard": 
```bash
git reset HEAD^ 
``` 
which will evict the commits from the branch and from the index, but leave the working tree around.
If you want to save the commits on a new branch name, then run 
```bash
git branch newbranchname 
```
before doing the 
```bash
git reset
```
Example:
```bash
❯ cat me.txt
Just adding example file
Adding extra line to see Backing out process
❯ git reset HEAD~
Unstaged changes after reset:
M	me.txt
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   me.txt

no changes added to commit (use "git add" and/or "git commit -a")

❯ git checkout -- me.txt
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
❯  cat me.txt
Just adding example file
```

And we backed out all changes from last commit.

### Removing the last commit
So once again we do 
```bash 
❯ echo "Adding extra line to see Backing out process" >> me.txt
❯ git commit -am "Added an extra line to the file"
[master 1cd42b5] Added an extra line to the file
 1 file changed, 1 insertion(+)
❯ git push
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 340 bytes | 340.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:augustync/og-helm-kafka-mm.git
   a93b85f..1cd42b5  master -> master
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
❯ cat me.txt
Just adding example file
Adding extra line to see Backing out process
```

And now when you refresh the page you will see the new line been added to the file.

### Removing the last push
Let's revert the last push we did to master.
```bash
❯ git reset --hard 1cd42b5
HEAD is now at 1cd42b5 Added an extra line to the file
❯ git reset --hard HEAD~
HEAD is now at a93b85f adding new file me.txt
❯ git push origin +a93b85f:master
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
Total 0 (delta 0), reused 0 (delta 0)
To github.com:augustync/og-helm-kafka-mm.git
 + 1cd42b5...a93b85f a93b85f -> master (forced update)
❯ cat me.txt
Just adding example file
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```


### Renaming and moving Files.

```bash
❯  git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
❯ ll
total 72
drwxrwxr-x  15 nonus25  staff    480 12 Apr 10:02 .git
-rw-rw-r--   1 nonus25  staff    654 11 Apr 18:04 CONTRIBUTION.md
-rw-rw-r--   1 nonus25  staff     81 11 Apr 18:04 Jenkinsfile
-rw-rw-r--   1 nonus25  staff  11357 11 Apr 18:04 LICENSE
-rw-rw-r--   1 nonus25  staff   5153 11 Apr 18:04 README.md
-rw-rw-r--   1 nonus25  staff     26 11 Apr 18:04 _config.yml
drwxrwxr-x   4 nonus25  staff    128 11 Apr 18:04 docker-src
-rw-rw-r--   1 nonus25  staff     25 11 Apr 19:52 me.txt
drwxrwxr-x   6 nonus25  staff    192 11 Apr 18:04 og-kafka-mm
drwxrwxr-x   5 nonus25  staff    160 11 Apr 18:04 scripts
```

Moving the file under Bash result in this state of Git
```bash
❯ mv -v me.txt my-nonus25.txt
me.txt -> my-nonus25.txt
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	deleted:    me.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	my-nonus25.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
```bash
❯ git add -A
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    me.txt -> my-nonus25.txt

❯ git commit -m "renaming file under bash"
[master dbaa2a1] renaming file under bash
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename me.txt => my-nonus25.txt (100%)
❯ git push
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 251 bytes | 251.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:augustync/og-helm-kafka-mm.git
   a93b85f..dbaa2a1  master -> master
```

Now lets rename the file once again via Git command
```bash
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
❯ ls -l
total 72
drwxrwxr-x  15 nonus25  staff    480 12 Apr 10:37 .git
-rw-rw-r--   1 nonus25  staff    654 11 Apr 18:04 CONTRIBUTION.md
-rw-rw-r--   1 nonus25  staff     81 11 Apr 18:04 Jenkinsfile
-rw-rw-r--   1 nonus25  staff  11357 11 Apr 18:04 LICENSE
-rw-rw-r--   1 nonus25  staff   5153 11 Apr 18:04 README.md
-rw-rw-r--   1 nonus25  staff     26 11 Apr 18:04 _config.yml
drwxrwxr-x   4 nonus25  staff    128 11 Apr 18:04 docker-src
-rw-rw-r--   1 nonus25  staff     25 11 Apr 19:52 my-nonus25.txt
drwxrwxr-x   6 nonus25  staff    192 11 Apr 18:04 og-kafka-mm
drwxrwxr-x   5 nonus25  staff    160 11 Apr 18:04 scripts
```

```bash
❯ git mv my-nonus25.txt me.txt
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	renamed:    my-nonus25.txt -> me.txt

❯ git commit -m "renaming file under git"
[master 2f2197e] renaming file under git
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename my-nonus25.txt => me.txt (100%)
❯ git push
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 242 bytes | 242.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:augustync/og-helm-kafka-mm.git
   dbaa2a1..2f2197e  master -> master
```

### Git History

To see Git History use log command and view options included by running one of the commands below
```bash
git log --help
git help log
```

To view history of commits lets run for now just 
```bash
git log

commit 2f2197ea3917d3e8144e846730f0a4676c61f936 (HEAD -> master, origin/master, origin/HEAD)
Author: Augustyn Chmiel <augustyn.chmiel@acoustic.com>
Date:   Sun Apr 12 10:39:02 2020 +0100

    renaming file under git

commit dbaa2a11baa44dc2c73efd88e1399a67b5d7bbcf
Author: Augustyn Chmiel <augustyn.chmiel@acoustic.com>
Date:   Sun Apr 12 10:35:19 2020 +0100

    renaming file under bash

commit a93b85f2b49049d3990edb56b2588d56cd824954
Author: Augustyn Chmiel <augustyn.chmiel@acoustic.com>
Date:   Sat Apr 11 18:11:43 2020 +0100

    adding new file me.txt

commit 2444d769be0213f1c66fbe0501b92a87aeaf6c3d
Author: paul-opsguru <paul@opsguru.io>
Date:   Mon Apr 29 10:47:23 2019 -0700

    Set theme jekyll-theme-cayman

commit ae54dcaf59b17f0902787d04e3c0860f8f264386
Author: ppodolny <paul.podolny@gmail.com>
Date:   Mon Apr 29 10:43:56 2019 -0700

    initial commit
```

Where on top we have last commit.
Now lets add few extra parameters to the log command 
```bash
git log --oneline --graph --decorate
* 2f2197e (HEAD -> master, origin/master, origin/HEAD) renaming file under git
* dbaa2a1 renaming file under bash
* a93b85f adding new file me.txt
* 2444d76 Set theme jekyll-theme-cayman
* ae54dca initial commit
```

Now lets see the histry of specific file, in this case we will need to use this command:
```bash
git log -- me.txt

commit 2f2197ea3917d3e8144e846730f0a4676c61f936 (HEAD -> master, origin/master, origin/HEAD)
Author: Augustyn Chmiel <augustyn.chmiel@acoustic.com>
Date:   Sun Apr 12 10:39:02 2020 +0100

    renaming file under git

commit dbaa2a11baa44dc2c73efd88e1399a67b5d7bbcf
Author: Augustyn Chmiel <augustyn.chmiel@acoustic.com>
Date:   Sun Apr 12 10:35:19 2020 +0100

    renaming file under bash

commit a93b85f2b49049d3990edb56b2588d56cd824954
Author: Augustyn Chmiel <augustyn.chmiel@acoustic.com>
Date:   Sat Apr 11 18:11:43 2020 +0100

    adding new file me.txt
```

Now, let see the change we did in the commit, for this case we will use git show command
```bash 
git show dbaa2a11baa44dc2c73efd88e1399a67b5d7bbcf

commit dbaa2a11baa44dc2c73efd88e1399a67b5d7bbcf
Author: Augustyn Chmiel <augustyn.chmiel@acoustic.com>
Date:   Sun Apr 12 10:35:19 2020 +0100

    renaming file under bash

diff --git a/me.txt b/my-nonus25.txt
similarity index 100%
rename from me.txt
rename to my-nonus25.txt
```
