# What is Git

### Fighting your tools

When I was a PhD student taking masters classes, we had a computer architecture project to build a simulation of a modern processor.  A seven stage pipeline with branch prediction and other optimizations.  I took the lead on this project, hashing out the architecture, dividing the bulk of the operations with my fellow architecture lab mate while giving the decoder to the computer vision teammate.

Aside from syncing up to talk about our design, we worked independently at our own computers, sometimes in a lab, sometimes at home.  We had all used git before, but barely.  And then, the resources online were few and mostly confusing garbage.  We pushed and pulled our code using git, but we'd run into conflicts if we'd edited the same file.  It was a nightmare.  We were already overworked because we were all PhD students in the midst of our quals, burdened by classes, homework, research, TA duty, and the general burden of being underpaid with no free time.  And we were teasing apart git conflicts by hand in our complicated system-c/c++ code.

We'd encounter conflicts when we pushed, when we pulled, when we did anything at all, it felt like.  We were awkward and uncomfortable with git.  We barely knew any commands, and we certainly didn't know how to fix our own problems.  It felt like our tool was working against us.  We started emailing each other files instead.

That came with its own problems.  One of the benefits of git is that it's easy to see what has changed.  That's effectively what a commit is -- a snapshot of the changes you're introducing.  But we barely felt like we were getting that benefit from this tool we didn't know how to use.  So we marched through our hacky approach to version control and submitted our project a month later.

Obviously the take away isn't that git is a pain and no one should use it.  Certainly there are valid complaints about git, for example the [inconsistency in its commands](http://stevelosh.com/blog/2013/04/git-koans/#the-hobgoblin).  (Also I'm not going to tackle comparing git to other modern version control systems.)  But, if you're not familiar with your tools, they'll feel like a burden, fighting you every step of the way.  You'll always have that nagging thought that you just want to get your work done & that your tool is getting in the way.

### Master of your tools

Then I got my first tech job.

Maybe the online resources for learning git had improved, or the cognitive burden of being overworked and poor was lifted, but I was actually getting used to it.  In fact, I started to go out of my way to learn git, trying to teach myself at least one new trick with every pull request I opened.

First, I had to go through [basic setup on github and other beginning steps](https://github.com/sllewely/notes/blob/master/git/total_beginner.md).

##### repos

My team had a remote repo on github.  I cloned it to my local desktop, pulling down all of the files on the master branch onto my local machine.

```git clone <repo address>```

We worked using forks, which meant I had another remote repo I named myFork which also lived on github.

```git remote add myFork <repo address of the fork>```

```git remote -v``` to view my added remote repos

##### pulling and pushing changes

We would pull changes from origin but push our branches to our forks, opening pull requests against the origin repo from our fork.

```git checkout master``` to go to my local master branch

```git pull origin master``` to get all changes from origin

```git checkout -b myFeatureBranch``` to start a new branch based off of master where I would do my work

```git push myFork myBranch``` to push my branch to my fork

```git push myFork myBranch:newBranchName``` to push my local myBranch changes to a remote branch named newBranchName which may or may not exist on the remote

```git push origin myFork :newBranchName``` to push nothing to newBranchName, deleting the branch

And so my code would cycle around in this triangle.

##### commits

This concept of distributed code in different states in different locations, propelled by diffs and commits, was confusing to my new team members who had been used to other version control systems like SVN.  Then I was the expert, teaching others and learning more myself.

```git add -A``` staging everything, about to be commited

OR ```git add <specific file>```

```git commit -m "<my message describing these changes>"```

##### diffs

Probably the most confusing concept for those new to git is that my local branches are just long commit histories, and that when you pull and push, you're just pulling the commits that you don't have and pushing the commits the target branch doesn't yet have.  You're not checking simply checking out whole files identical to the remote repo.  You pull commits from a target branch into your local branch, but your local branch may have changes or commits the target branch doesn't have.

```git log``` to see the commit history of your current branch

```git show <commit ref>``` to see changes that happened in the given commit

```git diff``` to see unstaged changes in your local branch

```git diff --name-only``` to see just the file names of changes

```git cherry-pick <commit ref>``` to checkout just a commit into your local branch



```git reset --hard``` to remove unstaged and staged changes locally to files git is tracking

```git clean -fd``` to remove untracked changes locally (but not ignored files)

##### remote branches

So what's going on?  How *can* I get exact copies of remote branches?  How do I know what's different in my local branches?

```git fetch origin``` gets references to all branches on the origin repo.  This is actually happening automatically every time you pull from a remote repo.  First you get the references to the branch, then you merge in commits.

```git show-refs``` to view all of those branch refs.

```git diff master..origin/master``` to see differences in files between your local master and the remote repo origin's master branch

```git checkout origin/master``` to checkout the remote version of a branch

```git fetch origin``` again of course to update all references to remote branches, getting references to any new commits other people may have pushed onto the remote origin

##### getting changes

##### resolving conflicts
