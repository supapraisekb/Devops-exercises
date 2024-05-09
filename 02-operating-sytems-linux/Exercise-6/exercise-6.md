

## Task Bash Script - Start Node App

Write a bash script with following logic:

### Install NodeJS and NPM and print out which versions were installed

Download an artifact file from the URL: https://node-envvars-artifact.s3.eu-west-
2.amazonaws.com/bootcamp-node-envvars-project-1.0.0.tgz . 
Hint: use curl or wget
Unzip the downloaded file

Set the following needed environment variables: 
APP_ENV=dev, 
DB_USER=myuser,
DB_PWD=mysecret

### Change into the unzipped package directory

Run the NodeJS application by executing the following commands: 
npm install and node
server.js

### Notes:
Make sure to run the application in background so that it doesn’t block the terminal session
where you execute the shell script
If any of the variables is not set, the node app will print error message that env vars is not
set and exit
It will give you a warning about LOG_DIR variable not set. You can ignore it for now.

## Solution

```bash
#!/bin/bash

# Install Node.js and NPM
echo "Installing Node.js and NPM..."
sudo apt-get update
sudo apt-get install -y nodejs npm

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

echo "Node.js application is running in the background."


```