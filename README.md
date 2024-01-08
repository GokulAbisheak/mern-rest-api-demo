# MERN Backend - REST API Demo

Table of Contents
 1. [Environment Setup](#environment)
 2. [Folder Structure](#folder)
 3. [Initializing Backend Server](#server)
 4. [Good Practices](#practices)
 5. [Database Connection](#database)
 6. [CRUD Implementation](#crud)
 7. [API Testing](#testing)

<div id="environment">

 ## Environment Setup 
 There are few things that are essential to develop a MERN backend. They are,
 1. Node Environment 
 2. Integrated Development Environment
 3. Package Manager

**Node Environment**
In order to run the MERN backend we need to install node.js from https://nodejs.org/en

It is ideal to download LTS (Long-Term Support) version. 

Verify your installation by entering the following in the command prompt.

    node --version
<br/>

**Integrated Development Environment**
Integrated Development Environment aka IDE will be our workspace in which we develop our backend application.

There are many IDEs to choose from but I would recommend using VS Code.

Download VS Code from - https://code.visualstudio.com/
<br/>

**Package Manager**
By default the Node Package Manager (npm) will be available, If you want you can also use Yarn packager manager by installing yarn.

    npm install -g yarn

</div>
<br/>
<div id="folder">

## Folder Structure

![image](https://github.com/GokulAbisheak/mern-rest-api-demo/assets/116421744/8ad9e73a-f7dd-42ad-8a90-d3527b6e74e4)

Let me give a brief idea about the folder structure here,
* configs - This folder will contain all the configuration files (Example - Database Configuration).
* controllers - This folder will hold files which contains business logic.
* middleware - This folder will hold files which acts as a intermediate for client and server. (Example - Authentication and Validation Files)
* models - This folder will contain all the schema objects.
* routes - This folder will have files with routes defined to access the controller.
* utils - This folder will contain all the utilities. (Example - Logger)
</div>
<br/>
<div id="server">

## Initializing Backend Server

First we need to initialize our node app for that use the following command,

    #if you are using npm
    npm init -y

	#if you are using yarn
    yarn init -y

This will create a `package.json` file.

After that, add the following inside the `package.json` file.

    "scripts": {
	    "start" : "node index.js"
    }

The start command can be used to run the index.js file.

    #if you are using npm
    npm start
    
    #if you are using yarn
    yarn start

I'll be using ES6, therefore I'm add the following code to `package.json`

    "type" : "module"

After these steps, it should look like this, <br/>
![image](https://github.com/GokulAbisheak/mern-rest-api-demo/assets/116421744/00b251a4-e3c0-42d8-b488-92a63a3aedee) 

We need `express` package to run our server and we are going to use `cors` to restrict cross-origin requests. Enter the following command to install the packages.

    #if you are using npm
    npm install express cors
	
	#if you are using yarn
	yarn add express cors

Next we have to add the following code inside the `index.js` file in the root.

```
import  express  from  'express';
import  cors  from  'cors';

const  PORT  =  8080;

const  app  =  express();

app.use(cors());
app.use(express.json());

app.listen(PORT, () => {
	console.log(`Server has started and running on PORT ${PORT}`);
	console.log(`Server is running in Local Environment - http://localhost:${PORT}`);
});

app.get('/', (req, res) => {
	res.json('Server is running!')
});
```
Now run the application by entering the following command,

    #if you are using npm
    npm start
    
	#if you are using yarn
	yarn start

After running the application, you will be able to see the following output,
![image](https://github.com/GokulAbisheak/mern-rest-api-demo/assets/116421744/a3e97dba-eba2-47aa-8d44-72b7e96fa47c)

If you open the URL `http://localhost:8080` in the web browser, you will be able to see the following output.
![image](https://github.com/GokulAbisheak/mern-rest-api-demo/assets/116421744/f50d451b-cab4-4d1f-bf72-eb32d871f9b8)
</div>
