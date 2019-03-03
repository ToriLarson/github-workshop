# Intro to Git and GitHub

<!--  When using Git correctly it gives you the confidence to break stuff -->

## What is Git

According to git-scm.com:

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

But what does that mean and what problem does Git solve?

Have you ever worked on a paper or a project where maybe after you finished your first draft and got some feedback and before you start working on the next draft you name the file something like `my_project_2018-09-25.txt`
Then you start on the next draft and you repeat the process and name it like `my_project_2018-10-18.txt`
And so on and so forth and eventually you end up with a directory that looks like this:

```bash
project
├── my_project_2018-09-25.txt
├── my_project_2018-10-18.txt
├── my_project_final.txt
├── my_project_final_final.txt
└── my_project_final_final_THIS_ONE.txt
```

Now imagine you and a team were working on this project and you were saving files like this and each person was making their own changes and sharing the files back and forth.

**Git provides a way to track incremental changes and share those changes with others.**

In our example what would happen if two people made changes to the same file at the same time? They would have to manually figure out what to keep and what to get rid of. Git can do this automatically and when it can't it provides a convient interface for doing it yourself.

## What is GitHub

Now what is GitHub and how it different from Git.

According to GitHub's website:

> GitHub is a development platform inspired by the way you work. From open source to business, you can host and review code, manage projects, and build software alongside 31 million developers.

But what does that even mean?

Basically GitHub is a cloud based Git server. It provides a place for developers to `push` and store their Git projects and it makes it easier for multiple people to work on the same project.

This is all still a little confusing and highlevel so lets get started on a project and hopefully that will clarify things.

<!-- TODO: Get a real URL -->

## Step 0 - Fork the Repo

- Go to this url: [SOME_URL]
- Click the `Fork` button in the upper right corner <!-- TODO: Screenshot? -->

### What's did I just do?

You forked a repo!  
Forking is Git terminology for copying someone else's project. It provides a place for you to make your own changes and if you want you can later give your changes back to the original repo.  
When contributing to projects in a team (and especially in open source) this is the first step

## Step 1 - Clone your newly forked repo

Mac/Linux - Open terminal  
Windows - Open Git Bash Type the following

```bash
git clone git@github.com:/YOUR_GITHUB_USERNAME/git-workshop-site/
# Can copy the URL from GitHub page
cd git-workshop-site
ls
```

<!-- TODO: How to run site -->

### What the heck did I just do?

You cloned a repo!
Cloning is when you make a copy of a Git project on your local machine.

### Wait, this is confusing! How is cloning different from forking?!

<!-- TODO: This is not good. Find analogy or better way to explain -->

Cloning is different because you are downloading the project to your machine. With forking you are creating your own copy of the project remotly.

If there is ever a project you just want to use and not contribute to, you'd often skip forking it and would just clone it.

## Branches

Alright, so you have the project on your machine and it's time for you to make some changes to it

Let's assume your team wants you to _change something on the website_. Using Git, how do we go about this?  
Side note: there are many ways to do this with Git, but we are making the assumption that your are working on a team. And for that assumption, this is a common workflow you would see.

```bash
git checkout -b my-contribution
git branch # Shows you a list of all your local branches. Press `q` to exit
```

### You created a new branch but what does that mean?

A branch is just code that _branches_ from the another development branch.  
A lot people use braching for something called "feature branching". This means you create a new branch for each logical group of changes.  
For example your working on a website and your boss asks you to add the navbar.  
You might then create a branch called `add-navbar`. This would allow you to create and push as many changes as you want without affecting the main development branch.

### Branches and Forks and Repos. Oh My!

We've covered several terms so far and they all sound kind of similair. So lets take a moment to recap and clarify things

- Repo (repository) -> This is your project
- Fork -> Creating a repo by copying another repo
- Branches -> Groups of logical code changes (Or, groups of commits)

Maybe an analogy would make things clearer:  
A repo is a tree.  
When you fork someone's repo, you make an identical copy of their tree and plant it in your front yard.  
The branches on the tree represent your Git branches. These branches stem from the trunk (typically called the `master` branch) and in Git - unlike a real tree - these branches will rejoin the `master` or another branch

<!-- These branches - Just like real branches - can also be removed or added -->

Is that any clearer?

<!--
Switching branches Deleting branches Creating a branch without checking out
Where do I want to talk about this? Before making commits, or after?
-->

## Commits

First, lets make a change to our `index.html` file. Open the `index.html` file in your favorite editor. Look at the comment around line 54 and replace it with today's date

Great, now from the command line type `git status`. You should see something like the following:

```bash
On branch my-contribution
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```

### Notice the suggestions

Git is very good about providing help with what it thinks you're trying to do.  
In this case Git is telling us how to stage the file or delete our changes

Let's go remove this change

```bash
git checkout -- index.html
git status
```

You should see something like the following:

```bash
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
(use "git push" to publish your local commits)

nothing to commit, working tree clean
```

## Let's make another change

Around line 78 change the project URL to your github url

Then run

```bash
git add index.html
git status
```

You should see something like this:

```bash
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
```

When you run `git add` you stage your change. this means you are ready to commit the file to the repo. Run the following:

```bash
git commit -m "Add my repo url"
```

### What did that do?

You just made your first commit! Commits are how you save your changes to a project.

Type `git log` to show a list of commits in the current branch. Press `q` to exit.

## Let's revert this commit

So you made your first commit and that's great. But let's pretend your boss or project manager comes to you and says they no longer want your change. How do you go back to a previous commit?

```bash
git log --pretty=oneline
# Copy the second commit's hash
git revert HASH
# This will launch some form of editor. If you are in Vi or Vim type :wq to exit.
# If you are in nano type Ctrl+X then type y
git log
```

## Let's make one more commit, and this time we are going to leave it

```bash
# Checkout a new branch
git checkout -b add-github-username
```

Go to line 103 or so and add your Github username and a link to your profile with the listed template

```html
<li>
  <a href="https://github.com/YOUR_USER_NAME">YOUR_USER_NAME</a>
</li>
```

<!-- TODO: at some point checkout master -->

```bash
git add index.html
git commit -m "Add GitHub username"
```

So you added your username and commited the change. Now it's time to share your change with the world (me).

```bash
git checkout master
git merge add-github-username
git push origin master
```

### What did this do?

You moved back to your master branch and merged you changes with it. Then you pushed your changes to GitHub.

## Go to GitHub

Go to your repository on GitHub and look at the index.html file. You will see your changes.

## Make A Pull Request

<!-- TODO: Screenshots -->

From your repository page, Click the `Pull requests` tab and click the green `New pull request` button

Write a title and body

Submit your Pull Requests

<!-- /TODO: -->

## What next?

So, you just submitted your first Pull Request, that's awesome! A pull request is how you share your changes with others. Now it's up to the project maintainer (in this case me) to reivew, aprove, or reject your pull request.

Once your PR is approved it's changes will automatically get merged and in this case the website will update.

## Congrats You've Finished the Workshop!!!!

## Additional Help

- `man git`
- `git --help`
- Attlassian
- Git SCM

### .gitignore

### Markdown

<!--

- Review PR

- .gitignore

- Markdown ???

- Give additonal resource

  - Online
  - `git --help`
  - `man git`
  - https://www.atlassian.com/git/tutorials/undoing-changes -->
