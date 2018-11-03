# Help I'm a total beginner with git

You have files you've been working on on your computer.

Give your local machine permission to push and pull using your github account
[Github's guide on how to create a new ssh key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
Also follow the instructions for adding the ssh key to your github account.

Create a new git repo inside of your local folder
```git init```

Create a remote repo on github where you will push your repo to
Add it as a remote
```git remote add origin <replace here with the repo address.git found on the repo page>```

Add a .gitignore file into your local repo to stop tracking the temp or misc files.  You can google for "gitignore unity" or whatever you're working in.

Make your first commit!
Your files are all pending.
To add all files:
```git add -A```
Your files are now in staging.
To commit (make a snapshot)
```git commit -m "my description of the changes I made in this commit"```

Now push to your remote repo on github
```git push origin master```



