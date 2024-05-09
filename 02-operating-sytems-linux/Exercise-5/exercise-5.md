


## Solution


```bash
#!/bin/bash

# Show the current user information
echo "The current user for this session is: $USER"

# Choice Selection for the user
while true; do
    echo "To sort the processes by MEMORY CONSUMPTION type 'm' or type 'c' to sort by CPU CONSUMPTION:"
    read selection
    if [ "$selection" = "m" ] || [ "$selection" = "c" ]; then
        break
    else
        echo "Invalid option! Enter 'm' or 'c' and try again."
    fi
done

# Ask for the number of processes to print
while true; do
    echo "Enter the number of processes to print:"
    read num_processes
    if [[ "$num_processes" =~ ^[0-9]+$ ]]; then
        break
    else
        echo "Invalid input! Enter a valid integer."
    fi
done

# List all processes for the current user

echo "Below are the running processes for $USER sorted by $(["$selection" = "m" ] && echo "memory" || echo "CPU") consumption:"
if [ "$selection" = "m" ]; then
    ps aux --sort -rss | grep $USER | head -n $num_processes
elif [ "$selection" = "c" ]; then
    ps aux --sort -%cpu | grep $USER | head -n $num_processes
fi

```