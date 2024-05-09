## Task: Node App with Service user

You’ve been running the application with your user. But we need to adjust that and create own service user: myapp for the application to run. So extend the script to create the user and then run the application with the service user.

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
    echo "LOG_DIR has been created at: $LOG_DIRECTORY"
fi
export LOG_DIR="$(realpath "$LOG_DIRECTORY")"

# Create a new user to run the application
NEW_USER=myapp
if ! id "$NEW_USER" &>/dev/null; then
    echo "Creating new user: $NEW_USER"
    sudo useradd "$NEW_USER" -m
fi

# Set ownership of log directory to the new user
sudo chown "$NEW_USER:$NEW_USER" "$LOG_DIR"

# Set other environment variables
export APP_ENV=dev
export DB_USER=myuser
export DB_PWD=mysecret

# Install dependencies and start the application
echo "Installing dependencies..."
npm install

# Start the application as the new user in the background
echo "Starting the application..."
sudo -u "$NEW_USER" sh -c 'cd "$LOG_DIR"; node server.js &' 

# Wait for a moment to ensure the application has started
sleep 10

# Check if the application is running
if pgrep -fu "$NEW_USER" -f "node server.js" &>/dev/null; then
    echo "Node.js application is running."
    echo "Checking app.log file in $LOG_DIR directory:"
    sudo -u "$NEW_USER" cat "$LOG_DIR/app.log" 2>/dev/null || echo "app.log file not found."
else
    echo "Failed to start Node.js application."
fi

```
