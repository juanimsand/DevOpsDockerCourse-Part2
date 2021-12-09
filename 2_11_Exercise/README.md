# Description

This docker compose exercise use a node backend server project. The backend project uses nodemon as development tool. In index.js file the routing, a static db, some function for generate IDs and others elementals could be found.

# Project

You could found the backend project in: https://github.com/juanimsand/part3/tree/master/phonebookfullstack . We are going to need package.json, package-lock.json and index.js files.

# Docker

For generate an image and run a container, I created a Dockerfile and docker-compose.yml file.

## Dockerfile

Dockerfile uses node:14 image and copy the index.js, package.json and package-lock.json files into the image. Then the node package module is installed and also nodemon for run the application in development mode.

## docker-compose.yml

The docker-compose.yml file builds the Dockerfile, published the application port which is 3001 into 3001 host port, etcetera. But the more important thing is the command key which npm run dev, this command launches the application in development mode using nodemon.

# Testing the development mode

For test our application knowing what index.js file has it's a must.
Diving into it we could see the routes that are handled by the app, for example '/api/persons'. When a GET request is done a response with a JSON that has a phonebook list is returned, this list was define previously in the same index.js file.
Knowing that, we run our docker-compose file by executing docker-compose up.
So, if open our browser and go to http://localhost:3001/api/persons the JSON object with the phonebook list could be seen.
Now, that we know that it is working, we must test nodemon. We are going to change something in index.js file. For example, we could add a person to the list or change some phone number of a person that is already in that list. When we save the file, we could see that nodemon detects that and re runs the application. The result as a new phonebook list could be seen by refreshing our browser!