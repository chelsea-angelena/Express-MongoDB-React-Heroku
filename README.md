# Set-up for React, Express, MongoDB, Heroku App

Basic boilerplate set-up for React, Express and MongoBD to deploy to heroku. Start script in package JSON tell heroku to build the clint folder after deploying the React App.

## Installing / Getting started

To install the project:

Clone or fork from github, then run npm i in both the root folder and the client folder. This will install all of the dependencies.

These are the required dependencies for the root folder package json:

  "dependencies": {
    "cors": "^2.8.5",
    "express": "^4.17.1",
    "mongoose": "^5.11.13"
  },
  "devDependencies": {
    "dotenv": "^8.2.0",
    "morgan": "^1.10.0",
    "nodemon": "^2.0.7"
  }

If you are using the yarn package manager be sure to delete the package-lock.json (not the package.json, just the lockfile) and run yarn install in both the root and client folder.

The client folder includes the proxy url in the package.json. Be sure to update that if you change your Expresss server port number. The following dependencies will be installed in the client folder:


	"proxy": "http://localhost:5000",
	"dependencies": {
		"@testing-library/jest-dom": "^5.11.9",
		"@testing-library/react": "^11.2.3",
		"@testing-library/user-event": "^12.6.2",
		"axios": "^0.21.1",
		"history": "^5.0.0",
		"node-sass": "^4.14.1",
		"react": "^17.0.1",
		"react-dom": "^17.0.1",
		"react-router-dom": "^5.2.0",
		"react-scripts": "4.0.1",
		"web-vitals": "^0.2.4"
	},


### Initial Configuration
Requirements: Node v12 or later, npm v6 or later.

Update the root folder package-json to include the following:

"main": "server.js",
	"engines": {
		"node": "14.x",
		"npm": "6.x"
	},
  "scripts": {
		"test": "echo \"Error: no test specified\" && exit 1",
		"start": "node server.js",
		"heroku-postbuild": "cd client && npm install && npm run build"
  },

***Please note: Before trying to run the project locally you must set up a MongoDB database as well as a .env file with the following:

MONGO_DB_PASS: (password that you have set in your mongo DB cluster)
MONGO_DB_USER: (the database username)
MONGO_DB_DATABASE: (the name of the default database your app will be using)

The npm package 'dotenv' will be installed when you run npm or yarn install, and the db configuration file is set up to require this dependency if NODE_ENV !== 'production'. Please follow the instructions below to set up your environment variables for deploying to heroku.


## Developing

Once you have installed all of the dependencies, set up your database, and added the dotenv file, run 'nodemon server.js' from the root folder, and then 'cd client' and 'npm run start' or 'yarn start'.

Nodemon will have been installed as a Dev dependency. If you have nodemon installed globally you can remove this from the package.json.

Alternatively you can install and configure the npm package 'concurrently' to start the project with a single command.

#### Deploying

This section is not required for running the project in a dev environment, just for deploying to heroku.

Open a new terminal window from the root folder of your project, then run "heroku login" (assuming the heroku CLI is installed). You will be asked to hit any key to log in and will be redirected to the heroku homepage. Once you are logged in return to the terminal window and then type: "heroku create (enter project name or leave blank for auto-generated name)". Heroku will automatically create your new project. From here you will need to configure your production env vars (see the note below). The .env file is only for development and should not be used in production. Make sure it is included in your .git ignore file.

Once your env/config variables are all set up and everything is running smoothly in your dev environment, from the root folder run: "git add -A", or, "git add ." , then,   "git commit -m plus your commit message" and finally: "git push heroku main:master". Alternatively you can configure your heroku git repository to use the "git push heroku main" command. Please see the heroku docs.

Setting up Heroku Env Vars:

The project will not deploy unless you configure the same environment variables in your heroku app as you have set up in your .env file. You can do this either from the heroku project dashboard, or, using the heroku CLI. The variables you need to configure are:

to set up with herok-cli:

run: heroku congif:set (variable_name): (variable_value)

to check the environment variables run heroku config:get

to change from master to main branch:
If you first create your remote with Githb you will already be on the main branch.

If you first push to heroku you will be on the master branch.

Just run:
git checkout -b main
git checkout -D master
git push heroku main


MONGO_DB_PASS: (password that you have set in your mongo DB cluster)
MONGO_DB_USER: (the database username)
MONGO_DB_DATABASE: (the name of the default database your app will be using)

**note: these have the same names as the dev environment variables, but they should have different values so that you are not using the same database for both production and dev environments

## Features

Minimal code/set up reuired to connect to a mongo DB cluster and run a react app on the front-end, deploying to heroku.

## Links

- Repository:

- Bugs:

## Licensing
The code in this project is licensed under "ISC" license.

### Thanks!!
Thank you for reading this and for checking out my app! Comments, concerns and questions are always welcome.

chelsea.angelena@gmail.com





