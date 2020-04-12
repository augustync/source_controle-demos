# Aliases and History

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

### Git Aliases

In this section we will show how to create aliases to long Git command
So lets create alias for viwing the History with some short alias, instead of typing each time long commands.
```bash
git log --all --graph --decorate --oneline
```
For this we need to edit gitconfig to set the alias on user level

```bash
❯ git config --global alias.hist "log --all --graph --decorate --oneline"
❯ git hist

* 2f2197e (HEAD -> master, origin/master, origin/HEAD) renaming file under git
* dbaa2a1 renaming file under bash
* a93b85f adding new file me.txt
* 2444d76 Set theme jekyll-theme-cayman
* ae54dca initial commit
```

And now we are able to view the history with short command.
Now lets see where the alias its stored in case we need to modify if.

```bash
❯ cat ~/.gitconfig
[filter "lfs"]
        clean = git-lfs clean -- %f
        smudge = git-lfs smudge -- %f
        process = git-lfs filter-process
        required = true
[user]
        name = Augustyn Chmiel
        email = augustyn.chmiel@acoustic.com
[core]
        editor = /usr/local/bin/vim
[alias]
        hist = log --all --graph --decorate --oneline
```
So by editing this file we are able to add or modify new aliases.
