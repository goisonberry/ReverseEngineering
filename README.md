# ReverseEngineering

## Below is a document that outlines the files in the provided homework:

### Config Folder:

In the config folder, we have a config.json file, within this file we have the configuration for three different databases called “passport_demo”, “database_test”, and “database_production”, which act different purposes in the development, test, and production of the application.
Also in the config folder, is the passport.js file which uses the passport authentication middleware for node.js in order to provide authentication for user log-in. This starts by setting up the passport.use call to specify the user will be inputting an email. The email is looked up using sequelize “findOne”. If there isn’t an email that matches, an error will be thrown. This file is linked with the models folder (var db = require("../models")), and references the valid password custom method called validPassword that is called to verify a password matches the password in the database.
The last file in the config folder is within a middleware sub folder and is called isAthenticated.js, which is a middleware that simply restricts the routes a user can access if they are not logged in. If the user is not logged in, it will redirect them to the login page.

### Models Folder:

The next folder is the model folder, which has an index.js file and a user.js file. The index.js file uses the models that are in the model folder (in this case, user).
The user model (in user.js) sets up the sequelize table for the email and password for the user.
A user will be an object compiled of an email that is a string, unique, and is a valid email as well as a password, which is also a string. There is a custom model for validating passwords which we saw linked in the passport.js file.
Lastly, there is a “addHook” function, which is an automatic method that is run. This one is run before a user is created, and will automatically hash their password.
Hashing the password refers to scrambling the password through a random algorithm. This is done for security purposes and so a user’s password isn’t stored directly.

### Public Folder:

The public folder includes everything needed for the front end of this application. There are three different HTML files for the login, members, and signup pages (login.html, members.html, and signup.html). These files refer to the CSS and JS files. The js folder includes three different js files (login.js, members.js, and signup.js) which is the script needed for these HTML files.
The style.css file in the stylesheets folder simply has a top margin for the forms.

### Routes Folder:

The routes folder includes two files, api-routes.js and html-routes.js.
The api routes include the POST and GET routes that allow for a user to be signed up and their information stored in the database.
The html routes render the html pages. The GET requests are needed so that different things will happen if the user already has an account (sent to member page) or doesn’t have an account (sent to sign up page).

### Package.json

Includes that information for the development of this project called “1-Passport-Example”. The required dependencies for this project are:
Bcryptjs - uses an API to get random numbers for the hashing of passwords
Express
Express-session
Mysql2
Passport - authentication middleware
Passport-local
Sequelize

### Server.js

This file is used to set up the server on port 8080. There is also code that configures the middleware that is needed for the authentication. There are also links to the html-routes.js and api-routes.js files. This server is connected using sequelize.
After creating the “passport_demo:” database and running npm install in your command line, you can run this application.
You are then sent to the /members page with a greeting with the username that is currently logged in.
You can log-out to be sent back to the sign-up form. But if you already have an account, you can select “login” and get to the /members page that way.
