## Docker Compose Setup for Mage-AI, PostgreSQL, PgAdmin,Grafana, and Jupyter

This README will guide you through the step-by-step processof running the Docker Compose setup for the Mage-AI, PostgreSQL, PgAdmin,Grafana, and Jupyter services. The instructions will explain how to configurebindings, PostgreSQL credentials, and other required edits.

**Requirements**

Before you start, ensure you have the following installed:

*   **Docker**: The Docker platform must be installed on your system.
    

*   **Docker Compose**: Docker Compose should be installed as well.
    

You can verify the installation by running the followingcommands in your terminal:
```bash
docker --version
```
```bash
docker-compose --version
```
### Step 1: Clone or Download the Project Files
-------------------------------------------

First, ensure you have the docker-compose.yml file ready on your machine. You can create this file manually or download it from the repository.

### Step 2: Set Up Bind Volumes
---------------------------

#### Explanation of Bind Volumes:

In this Docker Compose setup, **bind mounts** are used to map directories on your local machine to directories inside the containers. This allows changes to files in the local directory to be reflected inside the container and vice versa.

```bash
volumes:
  - type: bind
    source: C:\Users\user\Documents\COMESA
    target: /home/src/default_repo/rap
```
In this example:

*   **source** is the path to a local directory on your machine (C:\\Users\\user\\Documents\\COMESA).
    
*   **target** is the path inside the container (/home/src/default\_repo/rap).
    

### Edit the Bind Source Directory:

The source path points to the directory where your local files are stored. You must ensure this path exists on your machine before running the containers. If you are using a different directory, replace C:\\Users\\user\\Documents\\COMESA with your preferred path.

#### Example:

If your directory is C:\\Projects\\MageAI, update the volumes section as follows:
```bash
environment:
  POSTGRES_DB: grafana_db
  POSTGRES_USER: postgres
  POSTGRES_PASSWORD: postgres
```
*   **POSTGRES\_DB**: The name of the database to create when the PostgreSQL container is initialized (default is grafana\_db).
    
*   **POSTGRES\_USER**: The username for PostgreSQL (default is postgres).
    
*   **POSTGRES\_PASSWORD**: The password for the PostgreSQL user (default is postgres).

#### Edit PostgreSQL Credentials:

If you want to change the database name, username, or password, simply modify the values in the docker-compose.yml file.

#### Example:

To use a different database name, username, and password, update as follows:
```bash
environment:
  POSTGRES_DB: my_database
  POSTGRES_USER: my_user
  POSTGRES_PASSWORD: my_password
```
Make sure to keep track of these credentials, as you will need them later when configuring the PgAdmin and Grafana services.

### Step 4: Running the Docker Compose Setup
--------------------------------------------

Once you’ve configured the bindings and PostgreSQL credentials, it’s time to start the Docker Compose setup.

1.  Open a terminal or command prompt.
    
2.  Navigate to the directory where your docker-compose.yml file is located.
    
3.  Run the following command to start the services:

```bash
docker-compose up -d
```

The -d flag runs the containers in detached mode, meaning they will run in the background.

####Verifying the Services:
You can check if the containers are running by using:
```bash
docker ps
```

This command will show you the status of the running containers.

### Step 5: Accessing the Services
------------------------------

Once the containers are running, you can access the services using the following ports:

*   **Mage-AI**: Open your browser and navigate to http://localhost:6789.
    
*   **PgAdmin**: Navigate to http://localhost:5000 to access the PgAdmin interface. Log in using the email admin@admin.com and the password pgadmin (or whatever you configured in the docker-compose.yml file).
    
*   **Grafana**: Navigate to http://localhost:3001 to access the Grafana interface. You can log in using the default Grafana credentials (admin for both username and password).
    
*   **Jupyter Notebook**: Navigate to http://localhost:8888 to access Jupyter Notebook. Since the token is set to an empty string, you won’t need a token to access the notebooks.

### Conclusion

You have successfully set up and configured Docker Compose for the Mage-AI, PostgreSQL, PgAdmin, Grafana, and Jupyter services. Be sure to adjust the bind source directories and PostgreSQL credentials to match your local setup. Enjoy working with your containers!

