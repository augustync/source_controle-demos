# Using GitHub Existing Repository 

### Forking a GitHub Repository
The first step is to fork the GitHub repository with which you’d like to work. For example, if you were interested in helping contribute content to the Open vSwitch web site, which is itself hosted as a GitHub repository, you would first fork it. Forking it is basically making a copy of the repository, but with a link back to the original.

Forking a repository is really straightforward:

1 Make sure you’re logged into GitHub with your account.
2 Find the GitHub repository with which you’d like to work.
3 Click the Fork button on the upper right-hand side of the repository’s page.

That’s it—you now have a copy of the original repository in your GitHub account.

### Making a Local Clone 
Determine the URL for the forked repository. 

```bash
git clone https://github.com/user_account/repo_u_need.git
```
Naturally, you’d replace the URL after git clone with the appropriate HTTPS clone URL for your forked project repository. (You have to clone your forked repository, not the original.)
When you clone the forked repository. Git will copy down the repository, both contents and commit history, to your system. Git will also add a Git remote called origin that points back to the forked repository in your GitHub account.


