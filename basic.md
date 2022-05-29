Git Workshop - Basics
======================


In this step, we will play with the basic git commands. We will start with an empty repository,
add files, stage and commit them.

Good luck

Before starting, there are some preparations had to be done. If this is not the first time you use git, just verify you don't miss anything

# Setup

## Install git
install git and verify that you can work with git using the command line.
Try to run `git --version` for example

<img width="396" alt="image" src="https://user-images.githubusercontent.com/100768144/170858869-348b116b-a3c3-4fc4-97f1-3bea8caf6709.png">

## Configure Email/Name
It is good practice to config your user name and email for git. It is more important when working in collaboration (using GitHub for example), but it is good to define this as you start.

To configure your user name and email, run the following command (just change the values before 😄)

If you think you already configured these values, you can first check
```bash
git config --get user.name
git config --get user.email
```
And then, you can set

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

## Configure Editor

Git sometimes uses the editor to prompt you for questions and editing. For this it used the default editor defined in your environemnt or fallbacks to `vi`.
You can set the default editor explcitly using the `core.editor` key, e.g.,

```
git config --global core.editor nano
```

# Create empty repp

We will start with empty folder

* Create a new folder, cd to this folder 

```bash
mkdir my-project
cd my-project
ls  # verify empty folder
```

* Initialize the repo

To initialize the repo, we use the command git init. It will create a `.git` folder under the current folder. 
This folder used to hold all the data about the repository: commits, commits tree, current commit and more.

```
git init
ls -a # use -a to show hidden files and verify you have .git folder
```

# Create the first commit

We first create new file. 
```
echo US > countries.txt
```

The command `git status` tells us about the status of the repository. 
```
% git status
```

<img width="820" alt="image" src="https://user-images.githubusercontent.com/100768144/170857613-fbb47150-2f16-4b4e-ab44-4a3941d98643.png">

As can see, we added new file. This file was not added to the repostiory yet, so it is listed under untracked files. 
Now we need to run `git add` to add this file to the repository, so it will be part of the version control

```
git add countries.txt
```
Now if we run the git status again, we see that this was staged and it will be committed in the next commit. 
<img width="576" alt="image" src="https://user-images.githubusercontent.com/100768144/170857664-f15e675a-675a-46ae-8606-622744ef65ff.png">

So let's create the first commit. When committing, we need to provide commit message. We can write `git commit` and then we will be prompted to commit message, or we can pass the comment as parameter `git commit -m "comment"`. So let's commit.
```
git commit -m "added countries file"
```
If we run git status again, we see that there is nothing to commit.

<img width="426" alt="image" src="https://user-images.githubusercontent.com/100768144/170857904-1f9391b1-9e90-459f-8669-3b1c187e5d76.png">


**Congrats! You just created your first commit**

# Create more commits

Let's continue the work. Let's add another two countries to the `countries.txt` file.

**Use >> in the commands below**

```bash
echo "Italy" >> countries.txt
echo "UK" >> countries.txt
```

Now if we run `git status` we get the following output

<img width="730" alt="image" src="https://user-images.githubusercontent.com/100768144/170858314-71847d36-5c8d-4bc2-8659-412d56be23ee.png">

We did a change if file, but we did not stage this change yet. So `git status` tells us that there are changes that are not staged yet.
If we want to stage these changes, we need to run `git add` and then we can commit.

But **before** staging and committing, let's use the `git diff` command. Let's run `git diff` with no arguments and see the output

```bash
git diff
```
<img width="501" alt="image" src="https://user-images.githubusercontent.com/100768144/170858415-e2983734-1f0f-4e30-a60e-bc652494fc90.png">

Let's understand what we see. When running `git diff` with no arguments, it show us the diff between the working tree (e.g. your folder) and the staged changes. 
That is, it shows you the changes you did which are not **staged**.

In this case, we see that we added two lines with Italy and UK - as expected.

Let's stage the change. Remember - to stage the changes, you need to run `git add`

```bash
git add countries.txt
```
Not the changes are staged. If you run `git diff` now (with no arguments) you will get empty output.

Let's now add new file. Let's call it `foods.txt` and create it with single food Pizza

```bash
echo Pizza > foods.txt
```

So what is our status now. We have one change that is staged (in `countries.txt`), and one new file that was created, but not added (staged) yet. 
This is exactly what `git status` will tell us.
```bash
git status
```
<img width="744" alt="image" src="https://user-images.githubusercontent.com/100768144/170858679-7ae95269-11c1-4a31-9e3c-764ab49391e6.png">


Now let's add the `foods.txt` and create out second! commit. We will not commit without the -m parameter, and we will be prompted to insert comment.

```bash
git add foods.txt
git commit
```
**Enter a comment when prompted and finalize the commit. Note the commit prompt will be done using your configured editor**

<img width="856" alt="image" src="https://user-images.githubusercontent.com/100768144/170858758-2a0243c5-5efe-429f-b2a5-492a5542f116.png">

# Create the third commit

We already created two commits. Now let's create the third one (again use **>>** and not >). 

```bash
echo "Falafel" >> foods.txt
echo "Israel" >> countries.txt
```

So we modified the two files, you can use `git diff` to see the actual changes and `git status` to see that they were not staged yet. 

<img width="769" alt="image" src="https://user-images.githubusercontent.com/100768144/170859321-b29dbdba-2a96-427d-8d9a-4803771b7229.png">

Now we need to stage the changes and commit them.

Since the pattern of editing -> staging -> committing is common, Git gives us a way to skip the git add and do both the staging and committing in single command.

So instead of running
```
git add countries.txt foods.txt
git commit -m "updated countries and foods"
```

We can run the following
```
git commit -am  "updated countries and foods"
```

This will work if you edit files, not if you add new ones.
Run either of the commands.

# History

Now we have 3 commits, we can now look at the history. The command to show us the history is `git log`. 

```bash
git log
```
<img width="674" alt="image" src="https://user-images.githubusercontent.com/100768144/170859483-82699b30-96a4-4a76-81c7-f56e4b5aad86.png">

What we see here?
You should see 3 entries, new to old (e.g your first changes are at the bottom). For each change, you see the commit id (40 chars), the author, the date and comment you entered.

If you want a less verbose format, you can run `git log --oneline`, this gives you the output in one line for each commit, and also short the commit id.

There are many ways to customize `git log`. Like all Git commands, you can run `git log --help` to get help or search google 😄. 

# Git diff

We already show that we can use `git diff` to see the changes you did and not staged (added) yet. You can also use `git diff` to show diffs for specific file between commits.

Let's run `git log --oneline`

<img width="567" alt="image" src="https://user-images.githubusercontent.com/100768144/170859916-3ef69726-e63c-4e11-9295-f347885a36b9.png">

So I have 3 commits in my history, from new to old they are: `ced8115` `cfd4ea1` `9b746af` (**If you have different commit ids, you should replace mine with yours)

If I want to see the diff in `countries.txt` between the first commit (the oldest) and the second commit, I can run the following:

```
git diff 9b746af cfd4ea1 -- countries.txt
```
I'll get the following output

<img width="619" alt="image" src="https://user-images.githubusercontent.com/100768144/170860016-7ef23628-b033-45e7-ac53-bbbfb9bbe299.png">

Which is what I did in the second commit for this file (we added Italy and UK).

* If you omit the path (e.g. countries.txt) you will get the diffs for all the files

## Get the recent diff

Many times you want to see the diffs in your recent commit. With the above output of log, I can run 

```bash
git diff ced8115 cfd4ea1
```

However, Git used a special pointer for the recent commit called HEAD. It also let you use HEAD^ to mark the one version before the HEAD, so to see
the diff from the last commit, you can run
```bash
git diff HEAD^ HEAD
```
Moreover, you can omit the last HEAD since this is the default when comparing commits. So you can just run
```
git diff HEAD^
```

<img width="525" alt="image" src="https://user-images.githubusercontent.com/100768144/170861105-73b4424c-48d0-4929-ab15-2c42979c031c.png">


Again, git diff has many options, you can read here https://git-scm.com/docs/git-diff or run `git diff --help` or google.














