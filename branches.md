Git Workshop - Branches
=========================

In this step, we will play with the branches and merging. We will continue working with the repository we used until now.

We will create branches, make commits and merge the branches.

# Creating a branch

## Create and Checkout 
We want to create another txt file with a new list - colors. When creating a branch we will try to give it a name that gives ideas of the changes this branch includes.
By checking out the branch we move the `HEAD` to point on the last commit of the branch (on creation it is the same commit as the last one in the `master` branch)

```
git checkout -b colors-list
git status
```

NOTE: `git checkout -b <branchname>` is a shortcut for `git branch <branchname>` followed by a `git checkout <branchname>`.

Notice that the git status command reports that you are on the `colors-list` branch.

## Make changes on the branch
1. We first create new file. 

```
echo "blue" > colors.txt
```

2. Commit the file

3. Look at `git log`
You should see that the HEAD is point on the new commit and the branch name.
You can also see in the log that we are 1 commit ahead master.

4. Make 2 more commits
- Add another color to `colors.txt` 
- Add another food to `food.txt`

## Switching between branches

We can use the command `git checkout <branch-name>` to switch between branches.
You can see what branches you currently have with the command `git branch`

1. Switch back to the master branch

```
git checkout master
```

2. Look at the files you have in the repo - the state is before the changes you made in the `color-list` branch.

3. Run `git log` 
`HEAD` is now pointing to the last commit that was maid in the `master` branch. 

4. You can also see the `diff` between the main and the `color-list` branch

```
git diff color-list
```

5. Make another change to the `countries.txt` file and **commit** it to the master branch.

NOTE: If you would have made changed to `food.txt` it is possible you would have conflicts when trying to merge the branches - both branches made new changes to the file and during the merge you will need to choose what should stay. 

# Merging branches

## Merge from `master` into `color-list`
During development with a team the default branch - master or main - will be updated during the time you working on a side branch.
So once in a while we should pull the new changes made and merge them to the side-branch to keep the branch updated and ahead.

1. Checkout the `color-list` branch

```
git checkout colors-list
```
2. Take a look at the file `countries.txt` - The change you made on the `master` branch should not be there.

3. Run `git log` and see the history of the branch before the merge.

4. Merge the branch `master` into the branch `color-list`

```
git merge master
```

5. Take a look at the file `countries.txt` not - The change you made on the `master` branch now also exist in this branch.

6. Run `git log` and see the history of the branch after the merge.

## Merge from `color-list` into `master`

Now that the `color-list` is updated with the recent changes from `master` we now want to merge our changes to the `master` branch.

1. Checkout the `master` branch
2. Run `git log` and see the history of the branch before the merge.
3. Merge the branch `color-list` into the branch `master`

```
git merge color-list
```
4. See the repo content - now you should have `colors.txt` in the master branch.
5.  Run `git log` and see the history of the branch after the merge.


# Thats it!

I hope this exercise helped you understand how we switch and merge between branches.
It will make sense even more when working remotely with the `pull` command that is used to merge new changes from the remote branch to the local branch.
And also the Pull Request which we creating a request that the remote main branch to merge the changes from a side branch.

## Further subjects you should explore
- How to resolve merge conflict
- `git merge` vs `git rebase`
- Squash
