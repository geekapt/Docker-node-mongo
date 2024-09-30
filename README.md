## This demo app in Node and mongo demonstrates a simple user profile application, using Docker:

Its utilizing: index.html with pure JavaScript and CSS styles, Node.js backend using the Express framework, MongoDB for data storage. All components are containerized using Docker.


### To start the application:

> Step 1: Create a Docker network (optional). 
- docker network create mongo-network
> Step 2: Start MongoDB.
- docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo
> Step 3: Start Mongo Express.
- docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express

``` Note: Creating a Docker network is optional. You can run both containers on the default network by omitting the --net flag in the docker run commands. ```

> Step 4: Access Mongo Express in your browser.
- Navigate to: http://localhost:8081
> Step 5: In Mongo Express, create a database named user-account and a collection called users.

> Step 6: Start your Node.js application locally. Navigate to the app directory:
- npm install
- node server.js
> Step 7: Access your Node.js application UI in your browser.
- Navigate to: http://localhost:3000
### Using Docker Compose
To start the application:
> Step 1: Start MongoDB and Mongo Express.

docker-compose -f docker-compose.yaml up 
You can access Mongo Express at http://localhost:8080.
> Step 2: In the Mongo Express UI, create a new database called my-db.
	
> Step 3: In the Mongo Express UI, create a new collection named users within the my-db database.

> Step 4: Start the Node.js server.
- npm install
- node server.js
> Step 5: Access the Node.js application in your browser.

Navigate to: http://localhost:3000

### To build a Docker image from the application:
docker build -t my-app:1.0 .
The dot (.) at the end of the command indicates the location of the Dockerfile.



