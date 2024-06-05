# Node.js Application Deployment with Docker and MongoDB
This guide provides detailed instructions on Dockerizing your Node.js application, integrating it with a MongoDB container using Docker Compose, and connecting the application to a MongoDB Atlas database. Follow the steps below to easily deploy and scale your application.

### Prerequisites.

- Basic understanding of Docker, Docker Compose, and MongoDB.
- Docker and Docker Compose installed on your system.
- MongoDB Atlas account.

### Dockerfile Creation 
To begin, create a Dockerfile in the root directory of your Go-Flags application. This file will define the base image, dependencies, and commands needed to build and run the application.

### Steps:

### Create a Dockerfile in the root directory of the Go-Flags application.

- Define the base image, dependencies, and commands needed to build and run the application within the Dockerfile.
- Use multi-stage builds if required for optimization.
- Ensure all necessary environment variables and configurations are included.


### Docker Compose File Creation with MongoDB Specification:

 Create a Docker Compose file to orchestrate the deployment of both the Go-Flags application and MongoDB container. It simplifies the deployment process and ensures consistency across different environments.

### Steps:

1. Create a docker-compose.yml file in the project directory.
2. Specify services for both the Go-Flags application and MongoDB container.
3. Define environment variables, ports, volumes, and dependencies.
4. Mount a path for MongoDB for storage to persist data.
5.  Integrate the Dockerfile and docker-compose.yml to build and run both containers seamlessly.


Use the `docker-compose up` command to build and start the containers.

### MongoDB Atlas Setup

 Set up MongoDB Atlas to establish a connection for the application. It enables remote database access and management.

## **Steps:**

1. Go to MongoDB Atlas and create a cluster.
2. Set up necessary credentials including username, password, and IP address, or allow all connections.
3. Install the MongoDB Atlas latest driver on your system.

```jsx
npm install mongodb
```

1. Copy the connection string from MongoDB Atlas.

```jsx

api url = "mongodb+srv://${DB_USER}:${DB_PASS}@cluster0.hf2ex.mongodb.net/flagly_control"

/OR/

const { MongoClient, ServerApiVersion } = require('mongodb');
const uri = "mongodb+srv://${DB_USER}:${DB_PASS}@cluster0.hf2ex.mongodb.net/flagly_control";

// Create a MongoClient with a MongoClientOptions object to set the Stable API version
const client = new MongoClient(uri, {
  serverApi: {
    version: ServerApiVersion.v1,
    strict: true,
    deprecationErrors: true,
  }
});

async function run() {
  try {
    // Connect the client to the server	(optional starting in v4.7)
    await client.connect();
    // Send a ping to confirm a successful connection
    await client.db("admin").command({ ping: 1 });
    console.log("Pinged your deployment. You successfully connected to MongoDB!");
  } finally {
    // Ensures that the client will close when you finish/error
    await client.close();
  }
}
run().catch(console.dir);
";
```

Paste the connection string in the configuration file (e.g., app.js, config.js) at the specified connection line or use mongodb full connection string.

## Testing Connection.

 Rebuild the containers and test the connection between the application and MongoDB.

### Steps:

Rebuild the Docker containers to Test the application and ensure it connects to MongoDB successfully.

 `docker-compose up --build`.

### Conclusion:

By following these detailed steps, you can seamlessly Dockerize your Node.js application, integrate it with MongoDB Atlas, and ensure a successful connection between the application and the database. 





