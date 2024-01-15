
# Docker Tutorial with DigitalOcean

This document provides a step-by-step guide on how to use Docker with DigitalOcean. You will learn how to set up a virtual machine (VM) on DigitalOcean with Docker installed, build and run a Docker container with a PHP-MySQL application, and configure the application to connect to a MySQL database.

## Prerequisites

- A DigitalOcean account
- Basic understanding of Docker, Git, and Linux commands

## Steps

### Step 1: Log in to DigitalOcean and Start a VM with Docker

1. Log in to your [DigitalOcean account](https://www.digitalocean.com/).
2. Start a VM on DigitalOcean that has Docker installed. Refer to the following guide: [How to Use the Docker 1-Click Install on DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-the-docker-1-click-install-on-digitalocean).

### Step 2: Clone the Source Code

1. On the DigitalOcean VM, clone the repository:
   ```
   git clone https://github.com/less-GAP/learning.git
   ```

### Step 3: Build the PHP-MySQL Image

1. Change directory to the `learning/php-mysql` folder:
   ```
   cd learning/php-mysql
   ```
2. Build the Docker image `php-mysql`:
   ```
   docker build -t php-mysql .
   ```

### Step 4: Run the PHP-MySQL Container

1. Run the container and map port 80:
   ```
   docker run -d -p 80:80 --name php-mysql php-mysql
   ```
2. Test the application by accessing the public IP of the DigitalOcean VM on port 80.

### Step 5: Run a MySQL Container

1. Run a MySQL container:
   ```
   docker run -d --name mysql -e MYSQL_ROOT_PASSWORD=secret -e MYSQL_DATABASE=mydatabase -p 3305:3306 mysql:5.7
   ```
2. Connect to the MySQL container using the public IP of the DigitalOcean VM on port 3305.

### Step 6: Update the PHP-MySQL Container to Connect to MySQL

1. Get the IP address of the MySQL container:
   ```
   docker inspect mysql | grep -i IPAddress
   ```
2. Update the PHP-MySQL container with the MySQL IP address:
   - Access the shell of the `php-mysql` container:
     ```
     docker exec -it php-mysql /bin/bash
     ```
   - Update the `$host` variable in the PHP configuration to the MySQL IP address.
