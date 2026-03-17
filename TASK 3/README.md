# Step 0 – Preparing prerequisites
![alt text](image.png)

# STEP 1 – BACKEND CONFIGURATION
Update ubuntu

sudo apt update
![alt text](image-1.png)
![alt text](image-4.png)

Upgrade ubuntu

sudo apt upgrade
![alt text](image-2.png)
![alt text](image-3.png)

Let’s get the location of Node.js software from Ubuntu repositories.

curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
![alt text](image-5.png)
![alt text](image-6.png)

Install Node.js on the server
Install Node.js with the command below
sudo apt-get install -y nodejs
![alt text](image-7.png)

Verify the node installation with the command below

node -v 

Verify the node installation with the command below

npm -v 
![alt text](image-8.png)

Application Code Setup
Create a new directory for your To-Do project:

mkdir Todo
![alt text](image-9.png)
![alt text](image-10.png)

## INSTALL EXPRESSJS
To use express, install it using npm:

npm install express

![alt text](image-11.png)

Now create a file index.js with the command below

ni index.js -ItemType File

![alt text](image-13.png)

Install the dotenv module

npm install dotenv

![alt text](image-12.png)

Open the index.js file with the command below

vim index.js
![alt text](image-14.png)

Now it is time to start our server to see if it works. Open your terminal in the same directory as your index.js file and type:

node index.js

![alt text](image-15.png)
![alt text](image-16.png)

Open up your browser and try to access your server’s Public IP or Public DNS name followed by port 5000:

http://<PublicIP-or-PublicDNS>:5000
![alt text](image-17.png)

Routes
There are three actions that our To-Do application needs to be able to do:
Create a new task
Display list of all tasks
Delete a completed task

For each task, we need to create routes that will define various endpoints that the To-do app will depend on. So let us create a folder routes

mkdir routes

Change directory to routes folder.

cd routes

Now, create a file api.js with the command below

touch api.js

Open the file with the command below

vim api.js

![alt text](image-18.png)

# MODELS
To create a Schema and a model, install mongoose which is a Node.js package that makes working with mongodb easier.
Change directory back Todo folder with cd .. and install Mongoose

npm install mongoose
![alt text](image-19.png)

Create a new folder models :

mkdir models

Change directory into the newly created ‘models’ folder with

cd models

Inside the models folder, create a file and name it todo.js

touch todo.js

![alt text](image-20.png)

Now we need to update our routes from the file api.js in ‘routes’ directory to make use of the new model.
In Routes directory, open api.js with vim api.js, delete the code inside with :%d command and paste there code below into it then save and exit

![alt text](image-21.png)

# MONGODB DATABASE
We need a database where we will store our data. For this we will make use of mLab. 

In the index.js file, we specified process.env to access environment variables, but we have not yet created this file. So we need to do that now.
Create a file in your Todo directory and name it .env.

![alt text](image-22.png)

Now we need to update the index.js to reflect the use of .env so that Node.js can connect to the database.
![alt text](image-23.png)

Start your server using the command:

node index.js
![alt text](image-24.png)
![alt text](<WhatsApp Image 2026-03-16 at 1.27.45 PM.jpeg>)

Testing Backend Code without Frontend using RESTful API
In this project, we will use Postman to test our API.

![alt text](image-26.png)

![alt text](image-27.png)

STEP 2 – FRONTEND CREATION
Since we are done with the functionality we want from our backend and API, it is time to create a user interface for a Web client (browser) to interact with the application via API. To start out with the frontend of the To-do app, we will use the create-react-app command to scaffold our app.

In the same root directory as your backend code, which is the Todo directory, run:

npx create-react-app client
![alt text](image-28.png)
![alt text](image-29.png)
![alt text](image-30.png)

This will create a new folder in your Todo directory called client, where you will add all the react code.

Running a React App

Before testing the react app, there are some dependencies that need to be installed.

Install concurrently. It is used to run more than one command simultaneously from the same terminal window.
npm install concurrently --save-dev

Install nodemon. It is used to run and monitor the server. If there is any change in the server code, nodemon will restart it automatically and load the new changes.
npm install nodemon --save-dev

In Todo folder open the package.json file. Change the highlighted part of the below screenshot and replace with the code below.
"scripts": {
"start": "node index.js",
"start-watch": "nodemon index.js",
"dev": "concurrently \"npm run start-watch\" \"cd client && npm start\""
},

![alt text](image-31.png)


Configure Proxy in package.json

Change directory to ‘client’

cd client

Open the package.json file

vi package.json

Add the key value pair in the package.json file "proxy": "http://localhost:5000".
![alt text](image-32.png)

The whole purpose of adding the proxy configuration in number 3 above is to make it possible to access the application directly from the browser by simply calling the server url like http://localhost:5000 rather than always including the entire path like http://localhost:5000/api/todos

Now, ensure you are inside the Todo directory, and simply do:
![alt text](image-33.png)

Your app should open and start running on localhost:3000

Important note: In order to be able to access the application from the Internet you have to open TCP port 3000 on EC2 by adding a new Security Group rule. You already know how to do it.

![alt text](image-34.png)


Creating your React Components
One of the advantages of react is that it makes use of components, which are reusable and also makes code modular. For our Todo app, there will be two stateful components and one stateless component.
From your Todo directory run
cd client

![alt text](image-35.png)

To make use of Axios, which is a Promise based HTTP client for the browser and node.js, you need to cd into your client from your terminal and run yarn add axios or npm install axios.
Move to the src folder
cd ..
Move to clients folder
cd ..
Install Axios
npm install axios

![alt text](image-36.png)

Go to ‘components’ directory

cd src/components

After that open your ListTodo.js

vi ListTodo.js

in the ListTodo.js copy and paste the following code
![alt text](image-37.png)

Then in your Todo.js file you write the following code
![alt text](image-38.png)

We need to make little adjustment to our react code. Delete the logo and adjust our App.js to look like this. Move to the src folder

cd ..

Make sure that you are in the src folder and run

vi App.js

Copy and paste the code below into it
![alt text](image-39.png)

Copy and paste the code below:
![alt text](image-40.png)

Go to the Todo directory

`cd ../..`
When you are in the Todo directory run:

`npm run dev`

![alt text](image-41.png)

![alt text](image-43.png)

Assuming no errors when saving all these files, our To-Do app should be ready and fully functional with the functionality discussed earlier: creating a task, deleting a task and viewing all your tasks.

![alt text](image-42.png)

Congratulations

In this Project 3, you have made a simple To-Do and deployed it to MERN stack. You wrote a frontend application using React.js that communicates with a backend application written using Expressjs. You also created a MongoDB backend for storing tasks in a database.