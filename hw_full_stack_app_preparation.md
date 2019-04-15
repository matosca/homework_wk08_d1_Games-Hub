# Homework: Full Stack Games Hub App

### Learning Objectives

- Understand the relationship between client, server and database
- Be able to navigate a codebase that you haven't written

## Brief

Your boss has asked to you look over the codebase of a full-stack JavaScript application. The front-end is written in JavaScript using no frameworks, the back-end uses an Express server and a MongoDB database. Your task is to make yourself familiar with the codebase.

The application includes a README.md with instructions on running the application.

![Overview of the tech stack and tooling with commands](images/tech_stack_with_commands.png)

*Overview of the tech stack and tooling with commands*

## MVP

### Task

Draw a diagram showing the dataflow through the application starting with a form submission, ending with the re-rendering of the page. This will involve a multi-direction data-flow with the client posting data to the server and the server sending data back to the client with the response. Detail the client, server and database in the diagram and include the names of the files involved in the process.

### Questions

1. What is responsible for defining the routes of the `games` resource?
Helper file - create_router.js which is triggered by the server.js file and at the same time triggers the db games_hub in the seeds.js file.
2. What are the the responsibilities of server.js?
Server.js is responsible for running and triggering the db games_hub and also for making the routes helper file work.
3. What are the responsibilities of the `gamesRouter`?
GamesRouter is responsible for creating the router/routes addresses  and connecting to the database in order to get and post the data.
4. What process does the the client (front-end) use to communicate with the server?
The client-side requires of a request_helper.js file which manages the request to the url and so it fetch the url and gets a promise that is then used to publish the games data. As we can see in games.js there are three function (getData, postGame and deleteGame) that make request to server.
5. What optional second argument does the `fetch` method take? And what is it used for in this application? Hint: See [Using Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) on the MDN docs
Fetch takes as argument an url and optionally an init object that allows you to control a number of different settings. In request_helper.js, the code written for method post has a fetch funciton that takes an init object which handle the post method of data.
6. Which of the games API routes does the front-end application consume (i.e. make requests to)?
The front-end application make request to server of get(games) in getData function, post(game) in postGame function and delete(gameid) in deleteGame.
7. What are we using the [MongoDB Driver](http://mongodb.github.io/node-mongodb-native/) for?
We are using MongoDB in order to get data from a database, for data persistance.
## Extension

Why do we need to use [`ObjectId`](https://mongodb.github.io/node-mongodb-native/api-bson-generated/objectid.html) from the MongoDB driver?
The ObjectId is required in the create_router.js file as a kind of constractor of new db objects when new data is inputted and submitted in the app. ObjectId is used in the different routers when finding one document in the db, when updating one document or field in a document in the db, and also when deleting one document from the db. It allows us for a fast and unique way of identifying and accesing data in the db.
