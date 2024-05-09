

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

export NODE_VERSION=$(node -v)
export NPM_VERSION=$(npm -v)
export APP_ENV=dev
export DB_USER=myuser
export DB_PWD=mysecret
# First we want to download and install nodejs from official repo

curl -O https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh

# Install the script above and source the shell
bash install.sh

source ~/.bashrc

# Install the node package manager NVM
nvm install 20

echo "You have installed this version of NodeJS: $NODE_VERSION"
echo "You have also installed this version of NPM: $NPM_VERSION"

# Download and extract the Bootcamp NodeJS App
wget https://node-envvars-artifact.s3.eu-west-2.amazonaws.com/bootcamp-node-envvars-project-1.0.0.tgz

tar -xvzf bootcamp-node-envvars-project-1.0.0.tgz

#Change to application folder

cd package/
#Install NPM dependencies
npm install

#Run NODEJS App
node server.js &

```