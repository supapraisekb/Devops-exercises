## EXERCISE 7: Revert commit

Still on the bugfix branch:
-  You also noticed a spelling mistake in the index.html file, so you want to fix
that in the same branch.
- Fix the spelling mistake and commit the fix
- You also want to update the image.
- So also change the image url (src) in a separate commit.
- You are done with the changes:
- Push both commits to the remote repository.
- Your team members tell you the previous image was the correct one, so you want to undo it. But since you already pushed to remote, you must revert the change.
Revert the last commit and push your changes to remote repository


## Solution:

I achived this soultion using the command

```bash
git revert < Commit Hash >
```