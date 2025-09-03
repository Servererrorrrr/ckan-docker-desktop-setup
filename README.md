# ckan-docker-desktop-setup
Notes for setting up CKAN using Docker Desktop on Windows.
Since we are using Windows to set up the Ckan UI . We are goint to download the Docker Desktop for windows from the link mentioned below . 
**Link-1 :- [https://docs.docker.com/desktop/setup/install/windows-install/]** 

After installing the docker desktop . We would open any IDE of your choice . Here  I have used Visual Code Studio . 
Ater oppening the Visual Studio Code we are going top copy the ckan github repository from the link mentioned below.
**Link-2 :- [https://github.com/ckan/ckan]** 
After opening the Visvual Studio do the following steps. 
**Step-1 :- Click on File then click on New Window . Then in the Start menu click on clone from Git Repository and Paste the Link-2 over there** . 
**File ---> New Window ----> Start Menu ----> Clone on Clone from Git Repository ----> Paste the link-2 over there** . 
Wait for few minutes . All files and folders, yaml files and readme documents would be downloaded in your IDE 
After that I went to go the readme document to go thriough the necessary steps and requirements used for setting up the docker containers . 


**NOTE :-** After verfiying the ports, system and other requirements . I went to **.ENV.EXAMPLE FILE** and renamed it to **.ENV** . This is the most important step that we have to do in order to make the docker services up and running . 
These **.ENV** file contains the services and ports which are pointing it to the Docker-Compose-YML file . Which is basically required to run the docker containers for setting up the ckan services . 
After renaming the file . Run command **Docker --version.**   We will get the docker version it will also give you the indication that all the docker services are up and running well . 
**docker-compose up -d** ----> Run this command to set up the docker containers required for setting up the CKAN services .
This command will:
Start all the necessary services (Postgres, Solr, Redis, CKAN) in the background.
Pull Docker images and set up containers if not already present. 
To check that all the containers are running properly, use:

**docker-compose ps**
This will show the status of your containers (e.g., whether they are up or not).
Access CKAN Web Interface
Open your browser and go to **http://localhost:8443/**. 
You should see the CKAN homepage. 




**Create CKAN Admin User**
Access CKAN Container
To create a new admin user, you need to run commands inside the CKAN container. Use the following command to get a shell inside the CKAN container:

**docker-compose exec ckan bash**

Create Admin User
Inside the CKAN container, use the following CKAN CLI command to create an admin user:

**ckan -c /etc/ckan/production.ini sysadmin add admin email=admin@example.com name=admin password=YOUR_PASSWORD**


Replace YOUR_PASSWORD with a strong password and use your own email id . 

Exit CKAN Container
Exit the container by typing:

**exit**


Login to CKAN
Now, go to **https://localhost:8443/user/login** and log in using the admin credentials you just created
