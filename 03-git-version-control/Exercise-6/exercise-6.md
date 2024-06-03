## EXERCISE 6: Fix merge conflict
Your are on the bugfix branch. You notice the logger library version is old, so:
Update it to version 6.2 (Change the same location in bugfix branch)
Some time went by since you opened your bugfix branch, so you want the up-to-date master state to
avoid major conflicts.
Merge the master branch in your bugfix branch - fix the merge conflict!


## Solution

1. To generate the merge conflict, I ultered the same lines in the  build.gradle file on the bugfix branch but on the github GUI and locally

2. Commit error generated when i tried to push to the remote repo 

![Commit error due to conflict](/assets/commit-error-from-conflict.JPG)

3. to resolve this, I did a git rebase pull

```bash
git pull -r 

```

![git merge conflic](/assets/Merge-conflict.JPG)

4. I resolved the confilct in the editor and pushed the chaged to the remote repo


