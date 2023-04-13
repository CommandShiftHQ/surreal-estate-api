# Surreal Estate API

A simple Real Estate Marketplace API to showcase how to build post and fetch data with React.

## Run locally

- To run locally, clone this repo and install all dependencies `npm i`
- Create a `.env` file in the project root.
- Paste a MongoDb connection string in there, you can create an instance on Mlab/Atlas for free.
- E.g: `DATABASE_CONN=mongodb://username:password@ds117960.mlab.com:17960/surreal-estate`

## Deploy using Render & MongoDB Atlas

You can deploy this API on Render and use MongoDB Atlas to store data. You will need to create an account on both services but you can use the free tiers on both so you won’t need any payment or credit card information.

### MongoDB Atlas

1. First create a [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register) Account
2. At the end of the sign-up process, you will be prompted to create an organization and a project.
   - Organizations allow you to group and define users and teams, and grant them access to the different projects.
   - Projects allow you to define and organize resources such as database clusters, triggers, and data lakes. A common way to use projects is to define each environment as a project
3. Set the Project title as `Surreal Estate`
4. Once you have an Atlas account and have created an organization and a project, you’ll be able to create a database cluster.
5. Select `Create New Cluster`. Choose `AWS` as provider and change the Cluster Name to `Surreal Estate API`. Once you've done this select `Create Cluster`
6. Your new cluster should be showing under `Deployment` > `Database`.

In order to access your MongoDB Atlas cluster, you’ll need to enable network access for your network or IP address and create a database user for connecting to the cluster. After that, you can generate a connection string for your application or script.

Follow this [tutorial article](https://www.mongodb.com/basics/mongodb-atlas-tutorial) to create a user and generate a connection string. Make sure you select `Allow Access from anywhere` and save your connection string as we will need it when deploying to render.

Note that the connection string generated does not include the actual cluster user login. You will need to replace the `<username>` and `<password>` with your actual username and password. It should look something like:

```bash
mongodb+srv://<admin>:<password>@<project-name>.mongodb.net/test
```

### Render

1. Create an [Account](https://dashboard.render.com/) on Render and check the details used to configure Mongo DB match the ones recommended in [Renders Documentation](https://render.com/docs/connect-to-mongodb-atlas)
2. Once signed in, select `New` and choose `Web Service`
3. Here you can copy the link of the repo you are deploying into `Public Git repository` and select continue

```
https://github.com/tsv-stacks/surreal-estate-api/tree/master
```

4. Add a name for your web service and choose the free instance type
5. Select the `Advanced` Options menu and select `Add Environment Variable`
   - Set the key as `DATABASE_CONN`
   - Set the value as your MongoDB connection string
6. Scroll down and select `Create Web Service`

## Run in container

- You can run a pre-configured version of the app and the required database with docker-compose. You can read how to install docker-compose [here](https://docs.docker.com/compose/install/)
- Once docker-comopse is installed, you can start the app and database by running `docker-compose up` from the root of this project
- Alternately, you can run the app in detached mode by running `docker-compose up -d` from the root of this project
- You will not see any output from the containers in detached mode. You can check their logs with `docker-compose logs SERVICE_NAME`
- You can stop the containers with `docker-compose stop` in the root of this project
- You can start them again with `docker-compose start`
- You can tear down all the containers with `docker-compose down`, or `Ctrl + c` in the terminal window, if not running in detached mode
