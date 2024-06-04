## EXERCISE 8: Reset commit

- You found 1 last thing you think must be fixed. Bruno just moved to DevOps team, so Bruno’s role must
be fixed.
- Update the text accordingly
- Commit that fix locally (don’t push to remote)
- However after talking to a colleague, you find out it has already been fixed in another branch. So you
want to undo your local commit.

**Since commit is only locally, you can reset the commit*


## Solution:

To Achieve this assignment, I undid the commit locally by using the command

```bash
git resert --hard HEAD~1
``