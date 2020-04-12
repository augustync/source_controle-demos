# Basic Git Commands 

### Git configuration, clone and basic Git workflow
After git installation run those commands to setup your User and email address 
Afterwords make sure your config its configured as expected.
```
git config --global user.name "fname sname"
git config --global user.email "your@email.address"
git config --global --list
```

Copy the Repository to your local machine, from github repository locate the button "clone or download"
Use either SSH or HTTPS for coping the repository 

```
git clone git@github.com:augustync/source_controle-demos.git
```
or 
```
git clone https://github.com/augustync/source_controle-demos.git
```

Checking the git status and on which branch we are 
We use this command to check where we are between our local and remote area 
```
git status
```

Once you create new file, we need to add the file to git for this use this command
```
git add newfile.txt
```

After creating this file you can verify git status and see that there is new file in the staging area.
Ready to be commited, to commit the change type this command

```
git commit -m "Adding new start file to repo"
git push orghin master
```

And if all been done correctly we should see the new file in the Remote repository.


* [Basic Commands Listing](https://github.com/augustync/source_controle-demos/blob/master/Git/Basic_Commands_Listing.md)

