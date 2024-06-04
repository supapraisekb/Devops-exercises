## EXERCISE 9: Merge

- This time you want to merge your branch directly into master without merge request. 
- So:
merge your bugfix branch into master using git CLI (Hint: master branch must be up-to-date
before the merge)
- Being on the master branch now. Push your merge commit to remote repository

## Solution:

1. I switched to the main branch

```bash
git checkout main
```

2. I pulled the changes to the main branch

```bash
git pull
``` 

3. I switched to the bugfix branch, and merged all the changes from the remote repo

```bash
# switch to the bugfix branch
git checkout bugfix/spelling-error-in-java-app

# merge all the main changes from the main to the bugfix
git merge main

#switch back to the main branch branch
git checkout main

#push the changes to the remote remote repo

git add .
git commit -m "pushed the merged commits"
git push
```

switched back to
