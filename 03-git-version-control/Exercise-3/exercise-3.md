## EXERCISE 3: Feature branch

Create a feature branch and change following:

Upgrade the logstash-logback-encoder version to 6.6

Add image to the index.html file (url:
https://www.careeraddict.com/uploads/article/58721/illustration-group-people-teammeeting.
jpg )

You are done with the changes. So:
Check your changes using “git diff” and
Commit them if everything is correct.

Note: There is a standard in your team to name commits with descriptive text.
Push your changes to your remote repository.

## Solution

I created a feature branch using the command

```git
git checkout -b feature-exercise-3

```

To edit the logstash-logback-encoder file, I navigated to ``git-project`` and edited the the build.gradle file using vim editor 

To edit the index.html file I navigated to the ``git-project/src/main/webapp`` folder and edited the file using the vim editor

I pushed the changed to github