## Task: Node App with Log Directory

Extend the script to accept a parameter input log_directory: a directory where application will write logs.
The script will check whether the parameter value is a directory name that doesn’t exist and will create
the directory, if it does exist, it sets the env var LOG_DIR to the directory’s absolute path before running
the application, so the application can read the LOG_DIR environment variable and write its logs there.

Note:
- Check the app.log file in the provided LOG_DIR directory.
 - this is what the output of running the application must look like: 
 
 ![node-app-output.png](/02-operating-sytems-linux/Exercise-8/node-app-output.png)


 ## Solution

```bash




#!/bin/bash

# Check if Node.js and NPM are already installed
if ! command -v node &>/dev/null || ! command -v npm &>/dev/null; then
    echo "Node.js and/or NPM are not installed. Installing..."
    sudo apt-get update
    sudo apt-get install -y nodejs npm
fi

# Print Node.js and NPM versions
echo "Node.js version: $(node --version)"
echo "NPM version: $(npm --version)"

# Download the application
echo "Downloading the application..."
wget -qO- https://node-envvars-artifact.s3.eu-west-2.amazonaws.com/bootcamp-node-envvars-project-1.0.0.tgz | tar -xvzf -

# Set LOG_DIR environment variable
if [ -d "$LOG_DIRECTORY" ]; then
    echo "LOG_DIR already exists."
else
    mkdir -p "$LOG_DIRECTORY"
    echo "LOG_DIR has been created at: $1"
fi
export LOG_DIR="$(realpath "$LOG_DIRECTORY")"

# Set other environment variables
export APP_ENV=dev
export DB_USER=myuser
export DB_PWD=mysecret

# Install dependencies and start the application
echo "Installing dependencies..."
npm install

# Start the application in the background
echo "Starting the application..."
node server.js &

# Wait for a moment to ensure the application has started
sleep 5

# Check if the application is running
if pgrep -f "node server.js" &>/dev/null; then
    echo "Node.js application is running."
    echo "Checking app.log file in $LOG_DIR directory:"
    cat "$LOG_DIR/app.log" 2>/dev/null || echo "app.log file not found."
else
    echo "Failed to start Node.js application."
fi
