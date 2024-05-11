## Question:
Extend the previous script to ask for a user input for sorting the processes output either by memory or CPU consumption, and print the sorted list.

## Soultion

```bash
#!/bin/bash

# Show the current user information

echo "The current user for this session is: $USER"

# Choice Selection for the user

echo "To sort the processes by MEMORY CONSUMPTION type 'm' or type 'c' to sort by CPU CONSUMPTION:"

read selection

#list all processes for the current user
echo "Below are the running processes for $USER sorted by $(["$selection" = "m" ] $$ echo "memory" || echo "CPU") consumption:"
if [ "$selection" = "m" ]; then
        ps aux --sort -rss | grep $USER
elif [ "$selection" = "c" ]; then
        ps aux --sort -%cpu | grep $USER
else
        echo "Invalid option! enter 'm' or 'c' and try again."

fi

```
