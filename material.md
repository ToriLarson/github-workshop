# Intro to Git and GitHub 

<!-- Should probably ask how many people have used Git and GitHub --> <!-- Explain that this workshop is targeted for beginners and created in the context of Code For GSO's workflow -->

 ## What is Git

According to git-scm.com:

> Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

But what does that mean and what problem does Git solve?

Have you ever worked on a paper or a project where maybe after you finished your first draft and got some feedback and before you start working on the next draft you name the file something like `my_project_2018-09-25.txt`<br>
Then you start on the next draft and you repeat the process and name it like `my_project_2018-10-18.txt`<br>
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

You forked a repo!<br>
Forking is Git terminology for copying someone else's project. It provides a place for you to make your own changes and if you want you can later give your changes back to the original repo.<br>
When contributing to projects in a team (and especially in open source) this is the first step

## Step 1 - Clone your newly forked repo

Mac/Linux - Open terminal<br>
Windows - Open Git Bash Type the following

```bash
git clone git@github.com:/YOUR_GITHUB_USERNAME/git-workshop-site/
# Can copy the URL from GitHub page
cd git-workshop-site
ls
``` 

<!-- TODO: How to run site -->

 ### What the heck did I just do?

You cloned a repo!<br>
Cloning is when you make a copy of a Git project on your local machine.

### Wait, this is confusing! How is cloning different from forking?!

<!-- TODO: This is not good. Find analogy or better way to explain --> Cloning is different because you are downloading the project to your machine. With forking you are creating your own copy of the project remotly.<br>
If there is ever a project you just want to use and not contribute to, you'd often skip forking it and would just clone it.

## Branches

```bash
git checkout -b hello-world
git branches
```

- Branches

  - What is a branch
  - How does a branch differ from a fork
  - Feature branching (?)

- Make a commit

  - What is a commit
  - How often should I commit

- Revert the commit

- Make another commit

- Push to your repo

- Create PR

- .gitignore

- Markdown ???

- Give additonal resource

  - Online
  - `git --help`
  - `man git`
