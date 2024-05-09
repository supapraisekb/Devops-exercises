
## Question:

Write a bash script using Vim editor that checks all the processes running for the current user (USER
env var) and prints out the processes in console. Hint: use ps aux command and grep for the user



## Solution:

On the console time Vi Current-user-process.sh


```bash
#!/bin/bash

# Show the current user information
echo "The current user for this session is: $USER"

# list all processes for the current user
echo "Below are the running processes for $USER:"
ps aux | grep $USER


``` 