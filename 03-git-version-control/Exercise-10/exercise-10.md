## EXERCISE 10: Delete branches
Now that you are done, both feature and bugfix got deployed and you want to cleanup the old branches.

Delete both branches both locally and remotely

## Solution

 1. I  clicked on ``compare and pull request``
2. I inspected the change that was made and clicked ``create pull request``
3. I then Clicked on ``merge pull request``
4. Finally, I deleted the feature-exercise-3 branch
5. To update the changes on my local repo, i switcehd the branch to the main branch

```git
git checkout main
```

6. I pulled the changed to my local repo
```git
git pull
```