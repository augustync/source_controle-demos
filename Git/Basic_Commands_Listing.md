# Git Quick Start Commands
### Command Listing, Part 1
```bash
pwd
mkdir projects
cd projects
pwd
```

### Command Listing, Part 2
```bash
git version
git config --global user.name "Name Surname"
git config --global user.email "email@address.com"
git config --global --list
git clone github-https-url # paste in your GitHub HTTPS clone URL
ls
cd github-demo
ls
git status
echo "Test Git Quick Start demo" >> start.txt
ls
cat start.txt
git status
git add start.txt
git status
git commit -m "Adding start text file"
git status
git push origin master
```

# Mac OS X: TextMate 2

### Command Listing

```bash
git config --global --list # before
git config --global core.editor "mate -w"
git config --global --list # after
mate .gitconfig # compare with snip below
```

```bash
~/.gitconfig File (snip)
[core]
editor = mate -w
```
