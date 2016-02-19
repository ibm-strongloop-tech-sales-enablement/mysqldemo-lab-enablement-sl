# Quick Demo Tutorial
This tutorial will teach you how to quick demonstrate StrongLoop focusing on Arc.
By the end of this tutorial you should be able to:

1. Create a StrongLoop Product
2. Use Composer to discover models from a MySQL database
3. Preview APIs using Explorer

*All demonstrations are presented using a Macintosh.*

Please direct any questions to: 
**Ken Nelson**
e: ken.nelson@us.ibm.com
p: (949) 444-6308
t: @KenAtIBM

Last updated: 2/1/2016

## Pre-requisites:
1. nodejs installed. For more information on installing node, please visit [www.nodejs.org]
2. StrongLoop installed. For more information on installing StrongLoop, please visit [www.strongloop.com]
3. A directory for creating projects. Recommended that you create a directory to store projects.

----
## Download and Run Option
If you want to just run this application, you can clone it and perform an npm install. Otherwise scroll down to the Script section to manually create.
* To do that, open a terminal and type:
```
git clone https://github/com/ibm-strongloop-tech-sales-enablement/mysqldemo-lab-enablement-sl
```

* Change directories to mysqldemo-lab-enalbement-sl
```
cd mysqldemo-lab-enablement-sl
```

* Install the required modules from npm
```
npm install
```

* Start the server
```
node .
```

* Open a browser and navigate to http://0.0.0.0:3000/explorer
----


# Script

## Create a StrongLoop Project
Create a project using the slc loopback command. This will create the initial project and install the necessary libraries from npm.
**Steps**
+ Open a terminal and navigate to your projects directory.
![Project Directory](images/2016-01-31_15-03-38.png)


+ Create a new StrongLoop project called MysqlDemo by entering slc loopback MysqlDemo at the command prompt. Note that if you forget to add the MysqlDemo at the command line you can always add it via the wizard.
```
slc loopback MysqlDemo
```

![Create Project](images/2016-01-31_15-25-17.png)

+ Accept the defaults by pressing enter or return. 
	+ What’s the name of your application? MysqlDemo
	+ Enter the name of the directory to contain the project: MysqlDemo
![Accept Defaults](images/2016-01-31_15-25-17.png)

+ This will create the project structure and install the base libraries needed run the application.
+ Change directories to the newly created directory - MysqlDemo and view the contents of the directory.
![Project Stucture](images/2016-01-31_16-48-43.png)
---- 

## Add the MySQL Connector
Add and save the Loopback MySQL Connector by installing from npm.

**Steps**
+ From the projects/MysqlDemo directory install the Loopback MySQL connector by typing 
```
npm install loopback-connector-mysql --save
```

![Install Loopback Connector for MySQL](images/2016-01-31_17-23-34.png)

The —-save will add the requirement for having the MySQL connector. Typing npm install in the project directory will ensure that the necessary files are downloaded and installed as well as any updates.

## Create a MySQL Connection
There are a few ways to add a connection to your project. The first option is to use StrongLoop Arc. Second option is to use the StrongLoop command line. The third option is to edit the server/datasources.json file directly.
For the purposes of this tutorial, use the StrongLoop Arc option to create a connection to the StrongLoop MySQL sample database.
**Steps**
+ Start StrongLoop Arc by typing the following on the command line:
```
slc arc
```

+ This will launch the StrongLoop Visual Suite called StrongLoop Arc. Login if necessary and the press the **Composer** button.
![StrongLoop Arc](images/2016-01-31_19-28-37.png)
+ This will launch the StrongLoop Composer tool. With the composer tool you can create models and datasources (connections to various data repositories).
+ To create a new datasource connection, press the **Add New Data Source** link on the left of the screen.
![Create Datasource](images/2016-01-31_19-32-30.png)
+ Enter the following:
	+ Name: Demo-MySQL
	+ Username: demo
	+ Password: L00pBack (That is L-zero-zero-pBack)
	+ Leave Url blank
	+ Host: demo.strongloop.com
	+ Port: 3306
	+ Database: demo
	+ Connector: MySQL
![Connection Parameters](images/2016-01-31_19-42-14.png)
+ Save the Datasource by pressing the **Save Datasource** Button.
![Save Datasource](images/2016-01-31_19-42-14-2.png)

+ Next, test the datasource to make sure you can successfully connect to it by pressing the **Test Connection** button
![Test Connection](images/2016-01-31_19-42-14-3.png)

+ If successful, you will see a **Success** message next the **Test Connection** button.
![Connection Test Success](images/2016-01-31_19-47-29.png)
---- 

## Discover Models
StrongLoop Composer has the ability discover models from relational databases with the click of a button.
**Steps**
+ Select the Demo-MySQL
+ Click the down arrow button. This will show a menu for the connection.
+ Select **discover models**. This will interrogate the database and open a dialog to listing the available tables to model.
![Discover Models](images/2016-01-31_20-07-38.png)

+ Select the Customer, Order, and Review table and press the **Next**button.
![Select Tables to Model](images/2016-01-31_20-10-00.png)

+ Next the dialog will display the attributes of each selected table. You can choose to un-select attributes if you like. Press the **Next**button.
![Model Attribures](images/2016-01-31_20-11-35.png)

+ This will create the models based on the tables and attributes selected.
![Orders Model](images/2016-01-31_20-14-43.png)
---- 

## Review the Models with StrongLoop API Explorer
StrongLoop provides a [Swagger] interface to the APIs that have been created. 

+ From StrongLoop Arc. To run from Arc, press the **App Controller** button in the upper right hand side of Arc (looks like a play button). This will open the App Controller. The application should be stopped at this time. Press the **Play** button.
![App Controller - Stopped](images/2016-02-01_15-12-01.png)

+ You should see the following to let you know that the API Explorer is available.
![App Controller](images/2016-02-01_15-15-31.png)

+ You can also look at your terminal and it should look similar to the following:
![Termanal](images/2016-02-01_15-15-51.png)

+ Once your loopback server application is running, you can press the the link localhost:3000 to view the status of the server.
![Follow Link](images/2016-02-01_21-27-57.png)

+ The server status should stated that it has been started with a timestamp and for how long the server has been running.
![Server Status](images/2016-02-01_21-38-21.png)

+ To view the explorer, launch your favorite browser and navigate to [http://0.0.0.0:3000/explorer].
![View in Explorer](images/2016-02-01_21-43-02.png)

+ (Option) An alternative to using StrongLoop Arc is to use the command line to start the server process without the Process Manager by opening a terminal and typing:
'' node .
![](images/2016-02-01_21-45-17.png)

+ This will start a StrongLoop process for your application. This is great for verifying the APIs.
++This does not start the Process Manager, it simply starts a process++
+ To view the explorer, launch your favorite browser and navigate to [http://0.0.0.0:3000/explorer].
![](iamges/2016-02-01_21-43-02.png)
---- 

## Review APIs
Play around with the available APIs. You will notice that there is a User Model that you did not create. This is a special model that is a descendent of PersistedModel and used for access management. This model will be used in future labs, you can ignore it for now.
+ Open the Customer model. Open the Get /Customer method. Press the **Try it out!** button.
![Try it out!](images/2016-02-01_21-53-08.png)
---- 

## Standard Project Structure
When creating a StrongLoop projects, a standard directory structure is created. The directories that are most important for creating APIs are:
`~/server`
`~/server/boot`
`~/common/models`


The sever directory contains all of your configuration scripts as well as a boot directory. The standard configuration files are;
+ component-config.json -Specifies LoopBack components to load. [See LoopBack Components for more information].
+ config.json - Application settings. [See config.json for more information].
+ datasources.json - Data source configuration file. [See datasources.json for more information].
+ middleware.json - Middleware definition file. Middleware refers to functions executed when HTTP requests are made to REST endpoints. Since LoopBack is based on Express, LoopBack middleware is the same as Express middleware.  However, LoopBack adds the concept of middleware phases, to clearly define the order in which middleware is called.  Using phases helps to avoid ordering issues that can occur with standard Express middleware. [See defining middleware for more information].
+ middleware.production.json - Middleware definition file with production configuration. [See preparing for deployment for more information].
+ model-config.json - Model configuration file.
+ server.js - Main application program file.

The boot directory contains scripts that are run as the server is started. There are two standard files in the boot directory as well as any custom scripts;
+ authentication.js - Enables authentication for the application by calling app.enableAuth().
+ root.js - Binds loopback.status() middleware at the root endpoint ("/") to provide basic status information.
+ <custom>.js - Scripts that you create. Custom scripts are executed in alphabetical order before authentication.js and root.js. 
The common directory will contain any custom scripts that are used by other scripts as well as the models directory. The common/models directory contains all model definition files. Each model will have both a JavaScript and JSON file. The JavaScript file contains all model processing logic and the JSON file contains all model structure information in JSON format.
![Scripts](images/2016-02-02_17-03-39.png)
---- 

## (Optional) Review the Datasources.json File
The datasources.json file shows all the connections that have been created either thru StrongLoop Arc or the StrongLoop command line. You can also manually add connections by editing this file.

Open the datasources.json file. It should contain the following:
```json
"db": {
	"name": "db",
	"connector": "memory"   
},
"SL-Mysql": {
	"host": "demo.strongloop.com",
	"port": 3306,
	"database": "demo",
	"password": "L00pBack",
	"name": "SL-Mysql",
	"user": "demo",
	"connector": "mysql"
}
```

---- 

## (Optional) Review the model files
When discovering the models, StrongLoop automatically created two files for each model. In the common/models directory you should see the following:
+ customer.js/customer.json
+ order.js/order.json
+ review.js/review.json
The first file is a JavaScript file. This is where you would program any remote methods or hooks as well as any business logic that might be needed for the model. This lab will not cover hooks or remote methods, later labs will.
![](iamges/2016-02-01_21-58-36.png)


The second file is a JSON file that describes the components of the model as well as any mappings. The JSON file also maintains information about model relationships, security, any validations, as well as any methods created. Those topics will be covered in subsequent labs.
![](images/2016-02-01_21-58-50.png)
---- 

## (Optional) Remove User Model
To remove the user model from the list of available APIs, open the model-config.json file. The model-config.json file configures LoopBack models, for example it binds models to data sources and specifies whether a model is exposed over REST.  The models referenced in this file must be either a built-in models or custom models defined by a JSON file in the common/models/ folder.

**Steps**
+ Locate the User model:
```json
"User": {
	"dataSource": "db"
},
```

+ Change to:

```
"User": {
	"dataSource": "db",
	"public": false
},
```

++Adding the public is false clause will remove the User model from the available APIs.++
+ Restart your server and tryout in explorer.
---- 

## (Optional) Remove Methods
To limit the available methods for a particular model, use the disableRemoteMethod method. Your existing Customer model in Explorer should look like:
![Existing Customer Model](images/2016-02-02_17-28-04.png)


**Steps**
+ Open the common/models/customer.js file. It should look similar to the following:
```javascript
  module.exports = function(Customer) {
  };
```

+ Add the following lines to the export block.
```javascript
  Customer.disableRemoteMethod('create', false);
  Customer.disableRemoteMethod('find', false);
  Customer.disableRemoteMethod('upsert', false);
  Customer.disableRemoteMethod('exists', true);
  Customer.disableRemoteMethod('findById', false);
  Customer.disableRemoteMethod('deleteById', false);
  Customer.disableRemoteMethod('createChangeStream', true);
  Customer.disableRemoteMethod('count', false);
  Customer.disableRemoteMethod('updateAll', true);
  Customer.disableRemoteMethod('findOne', false);
  Customer.disableRemoteMethod('updateAttributes', false);
```

+ Your code block should look like the following now:
```javascript
module.exports = function(Customer) {
  Customer.disableRemoteMethod('create', false);
  Customer.disableRemoteMethod('find', false);
  Customer.disableRemoteMethod('upsert', false);
  Customer.disableRemoteMethod('exists', true);
  Customer.disableRemoteMethod('findById', false);
  Customer.disableRemoteMethod('deleteById', false);
  Customer.disableRemoteMethod('createChangeStream', true);
  Customer.disableRemoteMethod('count', false);
  Customer.disableRemoteMethod('updateAll', true);
  Customer.disableRemoteMethod('findOne', false);
  Customer.disableRemoteMethod('updateAttributes', false);
};
```

+ This will disable the exists (HEAD), createChangeStream, and updateAll methods for the customer model.
+ Restart your server and look at the results.

Your new Customer model in Explorer should look like:
![New Customer API](images/2016-02-02_17-30-20.png)

---- 
## More information

[StrongLoop Documentation](https://docs.strongloop.com/display/SL/Installing+StrongLoop)
[StrongLoop Blog](https://strongloop.com/strongblog/)
[Signup for StrongLoop Newsletter](https://strongloop.com/newsletter-registration/)
[StrongLoop: Standard project structure](https://docs.strongloop.com/display/public/LB/Standard+project+structure)
[StrongLoop: Getting Started Tutorial - Part 1](https://docs.strongloop.com/display/public/LB/Getting+started+with+LoopBack)
[StrongLoop: Getting Started Tutorial - Part 2](https://docs.strongloop.com/display/public/LB/Getting+started+part+II)
[StrongLoop: Access Control Tutorial](https://docs.strongloop.com/display/public/LB/Tutorial%3A+access+control)
[StrongLoop: Creating Model Relations Tutorial](https://docs.strongloop.com/display/public/LB/Tutorial%3A+model+relations)
[StrongLoop: YouTube Videos](https://www.youtube.com/user/StrongLoopVideos)
