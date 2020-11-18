# NodeGoat Workshop

This codebase is used to conduct a workshop on GitHub Actions and GitHub Code Scanning.

## NodeGoat

Being lightweight, fast, and scalable, Node.js is becoming a widely adopted platform for developing web applications. This project provides an environment to learn how OWASP Top 10 security risks apply to web applications developed using Node.js and how to effectively address them.

## Getting Started

OWASP Top 10 for Node.js web applications:

### Know it!

[Tutorial Guide](http://nodegoat.herokuapp.com/tutorial) explaining how each of the OWASP Top 10 vulnerabilities can manifest in Node.js web apps and how to prevent it.

### Do it!

[A Vulnerable Node.js App for Ninjas](http://nodegoat.herokuapp.com/) to exploit, toast, and fix. You may like to [set up your own copy](#how-to-set-up-your-copy-of-nodegoat) of the app to fix and test vulnerabilities. Hint: Look for comments in the source code.

#### Default user accounts

The database comes pre-populated with these user accounts created as part of the seed data -

- Admin Account - u:admin p:Admin_123
- User Accounts (u:user1 p:User1_123), (u:user2 p:User2_123)
- New users can also be added using the sign-up page.

## How to Set Up Your Copy of NodeGoat

### OPTION 1 - Run NodeGoat in Codespaces

The repo includes a `.devcontainer/` directory with Codespaces configuration artifacts that can be used to open the repository and launch the application directly from within the web browser. The Codespace also includes a MongoDB instance.

1. Navigate to [https://github.com/octodemo/NodeGoat-Workshop](https://github.com/octodemo/NodeGoat-Workshop)

2. Click on the green "Code" drop-down button

3. Select "Open with Codespaces".

4. Either select an existing Codespace or click "New codespace" to launch the repository within a Codespace

5. Open the Visual Studio Code Integrated Terminal

6. Install node packages (only if `node_modules/` is missing):

   ```sh
   npm install
   ```

7. Populate MongoDB with the seed data required for the app:

   ```sh
   npm run db:seed
   ```

8. Start the server:

   ```sh
   npm start
   ```

### OPTION 2 - Run NodeGoat on your machine

1. Install [Node.js](http://nodejs.org/) - NodeGoat requires Node v8 or above

2. Clone the github repository:

   ```sh
   git clone https://github.com/OWASP/NodeGoat.git
   ```

3. Go to the directory:

   ```sh
   cd NodeGoat
   ```

4. Install node packages:

   ```sh
   npm install
   ```

5. Set up MongoDB. You can either install MongoDB locally or create a remote instance:

   - Using local MongoDB:

     1. Install [MongoDB Community Server](https://docs.mongodb.com/manual/administration/install-community/)
     2. Start [mongod](http://docs.mongodb.org/manual/reference/program/mongod/#bin.mongod)

   - Using remote MongoDB instance:

     1. [Deploy a MongoDB Atlas free tier cluster](https://docs.atlas.mongodb.com/tutorial/deploy-free-tier-cluster/) (M0 Sandbox)
     2. [Enable network access](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) to the cluster from your current IP address
     3. [Add a database user](https://docs.atlas.mongodb.com/tutorial/create-mongodb-user-for-cluster/) to the cluster
     4. Set the `MONGODB_URI` environment variable to the connection string of your cluster, which can be viewed in the cluster's
        [connect dialog](https://docs.atlas.mongodb.com/tutorial/connect-to-your-cluster/#connect-to-your-atlas-cluster). Select "Connect your application",
        set the driver to "Node.js" and the version to "2.2.12 or later". This will give a connection string in the form:

        ```sh
        mongodb://<username>:<password>@<cluster>/<dbname>?ssl=true&replicaSet=<rsname>&authSource=admin&retryWrites=true&w=majority
        ```

        The `<username>` and `<password>` fields need filling in with the details of the database user added earlier. The `<dbname>` field sets the name of the
        database nodegoat will use in the cluster (eg "nodegoat"). The other fields will already be filled in with the correct details for your cluster.

6. Populate MongoDB with the seed data required for the app:

   ```sh
   npm run db:seed
   ```

   By default this will use the "development" configuration, but the desired config can be passed as an argument if required.

7. Start the server. You can run the server using node or nodemon:

   - Start the server with node. This starts the NodeGoat application at [http://localhost:4000/](http://localhost:4000/):

     ```sh
     npm start
     ```

   - Start the server with nodemon, which will automatically restart the application when you make any changes. This starts the NodeGoat application at [http://localhost:5000/](http://localhost:5000/):

     ```sh
     npm run dev
     ```

#### Customizing the Default Application Configuration

By default the application will be hosted on port 4000 and will connect to a MongoDB instance at localhost:27017. To change this set the environment variables `PORT` and `MONGODB_URI`.

Other settings can be changed by updating the [config file](https://github.com/OWASP/NodeGoat/blob/master/config/env/all.js).

### OPTION 3 - Run NodeGoat on Docker

The repo includes the Dockerfile and docker-compose.yml necessary to set up the app and db instance, then connect them together.

1. Install [docker](https://docs.docker.com/installation/) and [docker compose](https://docs.docker.com/compose/install/)

2. Clone the github repository:

   ```sh
   git clone https://github.com/OWASP/NodeGoat.git
   ```

3. Go to the directory:

   ```sh
   cd NodeGoat
   ```

4. Build the images:

   ```sh
   docker-compose build
   ```

5. Run the app, this starts the NodeGoat application at http://localhost:4000/:

   ```sh
   docker-compose up
   ```

## Contributors

Here are the amazing [contributors](https://github.com/OWASP/NodeGoat/graphs/contributors) to the NodeGoat project.

## Supports

- Thanks to JetBrains for providing licenses to fantastic [WebStorm IDE](https://www.jetbrains.com/webstorm/) to build this project.

## License

Code licensed under the [Apache License v2.0.](http://www.apache.org/licenses/LICENSE-2.0)
