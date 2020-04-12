# Basic Git Workflow (add, commit, pull & push) on Forked repository

### Cloning the Forked repository to your local repo

```bash
git clone git@github.com:augustync/og-helm-kafka-mm.git
```

### Now we will preforming operations on our local and remote copy of the repository
```bash
❯ ls -l
total 64
drwxrwxr-x  12 nonus25  staff    384 11 Apr 18:04 .git
-rw-rw-r--   1 nonus25  staff    654 11 Apr 18:04 CONTRIBUTION.md
-rw-rw-r--   1 nonus25  staff     81 11 Apr 18:04 Jenkinsfile
-rw-rw-r--   1 nonus25  staff  11357 11 Apr 18:04 LICENSE
-rw-rw-r--   1 nonus25  staff   5153 11 Apr 18:04 README.md
-rw-rw-r--   1 nonus25  staff     26 11 Apr 18:04 _config.yml
drwxrwxr-x   4 nonus25  staff    128 11 Apr 18:04 docker-src
drwxrwxr-x   6 nonus25  staff    192 11 Apr 18:04 og-kafka-mm
drwxrwxr-x   5 nonus25  staff    160 11 Apr 18:04 scripts
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

### Doing the add, commit, pull and push commands 
```bash
❯ echo "Just adding example file" > me.txt
```
```bash
❯ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	me.txt

nothing added to commit but untracked files present (use "git add" to track)
```
```bash
❯ git add me.txt
❯ git pull origin master
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
From github.com:augustync/og-helm-kafka-mm
 * branch            master     -> FETCH_HEAD
Already up to date.

❯ git commit -m "adding new file me.txt"
[master a93b85f] adding new file me.txt
 1 file changed, 1 insertion(+)
 create mode 100644 me.txt

❯ git push
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 312 bytes | 312.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:augustync/og-helm-kafka-mm.git
   2444d76..a93b85f  master -> master

❯ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```

Now when you refresh the repository in your browser you should see the new file.

