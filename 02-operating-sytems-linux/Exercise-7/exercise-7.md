## Task Node App Check Status

Extend the script to check after running the application that the application has successfully started and
prints out the application’s running process and the port where it’s listening.

## Solution:

In this script, we want to first check if Node JS and NPM are already installed beofre proceeding to launch the app if already installed or, if not installed, it will install node and NPM.

```bash
#!/bin/bash

# Function to check if Node.js and NPM are installed
check_installation() {
    if command -v node &>/dev/null && command -v npm &>/dev/null; then
        return 0  # Node.js and NPM are installed
    else
        return 1  # Node.js and NPM are not installed
    fi
}

# Check if Node.js and NPM are already installed
if check_installation; then
    echo "Node.js and NPM are already installed on this machine."
else
    echo "Installing Node.js and NPM..."
    sudo apt-get update
    sudo apt-get install -y nodejs npm
fi

# Print installed Node.js and NPM versions
echo "Node.js version:"
node --version
echo "NPM version:"
npm --version

# Download artifact file
echo "Downloading artifact file..."
curl -O https://node-envvars-artifact.s3.eu-west-2.amazonaws.com/bootcamp-node-envvars-project-1.0.0.tgz

# Unzip downloaded file
echo "Unzipping downloaded file..."
tar -zxvf bootcamp-node-envvars-project-1.0.0.tgz

# Set environment variables
export APP_ENV=dev
export DB_USER=myuser
export DB_PWD=mysecret

# Change into the unzipped package directory
cd bootcamp-node-envvars-project-1.0.0

# Run the Node.js application
echo "Running Node.js application..."
npm install
node server.js &

# Check if the application has started successfully

sleep 10 # Wait for a few seconds for the application to start
node_pid=$(pgrep -f "node server.js")
if [ -n "$node_pid" ]; then
    echo "Node.js application has started successfully."
    echo "Node.js process ID: $node_pid"
    echo "Listening on port:"
    netstat -tuln | grep "$node_pid/node"
else
    echo "Failed to start Node.js application."
fi




```