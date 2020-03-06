---
layout: post
title:      "React Redux Portfolio Project"
date:       2020-01-07 18:01:47 -0500
permalink:  react_redux_portfolio_project
---


My goal for this project was to expand upon my [previous Rails Project](https://github.com/terryblue99/my-watch-collection-v-001) by utilizing a React Redux frontend and a Rails API backend. 

It is an application named 'My Watch Collection' that allows a watch collector (like myself) to catalogue, update, and view their watch collection.

**REQUIREMENTS**
 
1.  The code should be written in ES6 as much as possible
2.  Use the create-react-app generator to start the project
3.  The app should have one HTML page to render the react-redux application
4.  There should be 2 container components
5.  There should be 5 stateless components
6.  There should be 3 routes
7.  The Application must make use of react-router and proper RESTful routing
8.  Use Redux middleware to respond to and modify state change
9.  Make use of async actions to send data to and receive data from a server
10.  The Rails API should handle the data persistence. Use fetch() within actions to GET and POST data from the API - do not use jQuery methods
11.  The client-side application should handle the display of data with minimal data manipulation
12.  The application should have some minimal styling: like react-bootstrap, but additional CSS may be included
      
I used Github branches to code and test my application as I developed it and merged those with the master branch when successfully tested.

I encountered a major problem when testing the completed app.  It turned out that SQLite3, the default Rails DB, was being locked occasionally when async operations were executing.  This occurred when a watch or user and related watch records were being deleted and caused the process to fail, leaving behind orphaned watch attachments.  To solve this problem I converted to the MYSQL DB which did not produce the same problem. I had also upgraded from Rails 5 to Rails 6 which made the conversion so much easier. Rails 6 introduces the "[rails db:system:change](https://youtu.be/FlY82Eiyx3o)" command to make this easier, using all the built-in generators for database.yml and more.

**HELPERS**

[Visual Studio Code (VS Code)](https://code.visualstudio.com/docs/introvideos/basics)

[Google](https://www.google.com/)

[Scrimba](https://scrimba.com/)

[Flowchart](https://imgur.com/eCEjcaZ)

[Video Walk Through](https://youtu.be/_GNLVTxxW-Y)

[MYSQL version of the app](https://github.com/terryblue99/my-watch-collection-v-003)

[SQLite3 version of the app](https://github.com/terryblue99/my-watch-collection-v-002)











