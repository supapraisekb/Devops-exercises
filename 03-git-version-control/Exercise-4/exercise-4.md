## EXERCISE 4 - Bugfix branch
You find out there is a bug in your project, so you need to fix it using a new bugfix branch:
- Create a new bugfix branch
- Fix the spelling error in Application.java file
- You are done with the changes. So:
- Check your changes using “git diff” and
- Commit them if everything is correct.
- Push your changes to your remote repository.

## Solution
1. I created a the new bugfix branch using:

```bash
git checkout -b bugfix/spelling-error-in-java-app
```

2. I fixed the error in the file Application.java file 

3. After adding and committing the change, I pushed the application to GitHub using the command:

```bash
git push --set-upstream origin bugfix/spelling-error-in-java-app
```
