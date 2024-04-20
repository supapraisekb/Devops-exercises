Write a bash script using Vim editor that installs the latest java version and checks whether java was installed successfully by executing a java -version command. Checks if it was successful and prints a success message, if not prints a failure message.

**SOLUTION**

Below is the code for the script to perform this task:

```
 #!/bin/bash/

   # Install java application                                                                         
 sudo apt update
   sudo apt install openjdk-11-jre-headless
  
   # Check if Java was installed successfully
  
  java -version >/dev/null 2>&1
  if [ $? -eq 0 ]; then
 
 echo "Java installed on this device!"
   else
      echo "Java installation unsuccessful."
      fi
```
