Git Workshop - Remote
=========================

In this step, we will practice everything we learned so far.

We will clone this repository, create a branch, make changes and commit them, push them to a remote branch, create a pull request, ask someone to review, and merge the changes into the main branch.

## Cloning the repo

1. Go to the repo page (https://github.com/swimmio/git-workshop-1) and find clone url (use the HTTPS link).

2. Go to your terminal and run the clone command:

```
git clone https://github.com/swimmio/git-workshop-1.git
```

3. Change directory to the `git-workshop-1` directory that was just created.

4. Check out your remote url by running:

```
git remote -v
```

## Create a branch

1. Create a new branch, choose a name of your choice:

```
git checkout -b <my-branch>
```

## Make Local Changes

1. Open the repository folder in an IDE or Text Editor of your choice.

2. Open the `CONTRIBUTORS.md` file and add your name to the end of the list of names.

3. Please do not make changes to the exercise files :)

4. Commit your changes:

```
git commit -m "add <my-name> into contributores list"
```

## Push Your Changes To Remote

1. First, let's make sure we have the recent changes from the remote repository into our local repository:

```
git pull
```

2. Push your branch with the changes:

```
git push
```

3. Git will notify you that your local branch doesn't exist in the remote repository, so let's define it and push:

```
git push --set-upstream origin <my-branch>
```

4. Go to the repo on GitHub again, change the branch to your branch you just pushed, make sure you see your changes.

## Create a Pull Request

1. While viewing your changes compared to the `main` branch, click on the Create Pull Request button.

2. Add some info about the change you just did in the Pull Request description.

3. Ask for a friend to review your changes by assigning them as a reviewer (ask for their GitHub username).

4. Review someone else's Pull Request if you are asked to review. Approve the Pull Request to they will be able to merge it to `main`.

5. After your Pull Request is approved, click on the Merge Pull Request button.

6. Go back to the repo page, click on the CONTRIBUTORS.md file in the `main` branch, notice your name is in the list of names.

# Thats it!

## Further subjects you can explore (OPTIONAL)
- Forks
- Git Fetch
