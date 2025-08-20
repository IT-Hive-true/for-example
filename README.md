# Installation:

1. You need to install the Docker desktop application.
    - For Windows: [Installation Guide for Windows](https://docs.docker.com/desktop/install/windows-install/)
    - For Mac: [Installation Guide for Mac](https://docs.docker.com/desktop/install/mac-install/)

2. Loading files and starting Docker containers.

2.1. To set up the system for the backend and quality control, execute the following commands (note that you need to choose the directory where you want to save the project before running the commands):

- For Windows:
  ```powershell
  git clone https://@github.com/Avoda-Zmanit-new/docker-config.git
  cd docker-config
  docker-compose up -d
  ```

- For Linux:
  ```bash
  git clone https://github.com/Avoda-Zmanit-new/docker-config.git && docker-compose up -d
  ```

2.2. Setting up the system for frontend development. Execute the following commands:

- For Windows:
  ```powershell
  git clone https://github.com/Avoda-Zmanit-new/docker-config.git --branch=frontend .
  cd docker-config
  docker-compose up -d
  ```

- For Linux:
  ```bash
  git clone https://github.com/Avoda-Zmanit-new/docker-config.git --branch=frontend . && docker-compose up -d
  ```

Note for section 2.2: For frontend developers, the port tracked is not from the container, but port 3000 of the local host.
  
The site is available at the link: http://localhost:8088/

# Running the site on a specific branch

To run the site on a specific branch, follow these steps:

1. Place the Dockerfile in the directory \sourcefiles\node\Dockerfile.
2. Add `--branch=branch_name` just before the "." in line 13.
3. In the directory containing docker-compose.yml, execute the following commands in the terminal:
    - Stop containers and deletes them: `docker-compose down`
    - Rebuild containers: `docker-compose build --no-cache`
    - Start containers: `docker-compose up -d`

# Applying new commits:

1. Navigate to the directory with the containers (where docker-compose.yml is located).
   For example: `cd D:\Projects\avodazmanit\docker-config`
2. Execute the command:
   ```bash
   docker-compose restart
   ```
    - If you want to update only the backend: `docker-compose restart php-fpm`
    - If you want to update only the frontend: `docker-compose restart node`
