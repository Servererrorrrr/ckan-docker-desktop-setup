Setting up CKAN using Docker Desktop on Windows

This guide provides a step-by-step process to set up CKAN (Comprehensive Knowledge Archive Network) using Docker Desktop on a Windows environment.

1. Install Docker Desktop for Windows

Download Docker Desktop from the official link:
**[https://docs.docker.com/desktop/setup/install/windows-install/]**

Follow the installation instructions.

After installation, verify that Docker is running by executing:

**docker --version**


This command should display the installed Docker version, confirming that Docker services are up and running.

2. Set Up IDE (Visual Studio Code Recommended)

Open Visual Studio Code (or any IDE of your choice).

Clone the official CKAN GitHub repository:
**[https://github.com/ckan/ckan]**

Go to: File → New Window

In the Start menu, select Clone from Git Repository

Paste the GitHub link provided above

Wait for a few minutes until all files (folders, YAML files, README, etc.) are downloaded into your workspace.

3. Configure Environment Variables

Inside the cloned repository, locate the file named:

**.env.example**


**Rename it to:**

**.env**


**Important**: This file defines environment variables such as ports, services, and configurations required for Docker to properly set up CKAN.

4. Start Docker Containers

Open a terminal in the project directory.

Run the following command to build and start the required containers in the background:

**docker-compose up -d**


This will:

Pull necessary Docker images (if not already present)

Start all CKAN services (Postgres, Solr, Redis, CKAN)

Verify that the containers are running:

docker-compose ps


This displays the status of each container (e.g., Up or Exited).

5. Access the CKAN Web Interface

Once the services are running, open your browser.

Navigate to:
👉 http://localhost:8443/

You should now see the CKAN homepage.

6. Create CKAN Admin User

To manage CKAN, you need an admin account.

Step 6.1 – Access the CKAN Container

Run the following command to open a shell inside the CKAN container:

docker-compose exec ckan bash

Step 6.2 – Create an Admin User

Inside the container, run:

ckan -c /etc/ckan/production.ini sysadmin add admin email=admin@example.com name=admin password=YOUR_PASSWORD


Replace YOUR_PASSWORD with a strong password of your choice.

Update admin@example.com with your own email ID.

Step 6.3 – Exit the Container

After creating the user, type:

exit

7. Log In to CKAN

Open your browser and visit:
👉 https://localhost:8443/user/login

Enter the admin username and password you created in Step 6.

You should now be logged into CKAN as the system administrator.

✅ Summary

By following these steps, you have:

Installed Docker Desktop on Windows

Cloned the CKAN GitHub repository

Configured the .env file

Started CKAN services using Docker Compose

Accessed the CKAN web interface

Created and logged in as an admin user
