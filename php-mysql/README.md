## Setting Up the Environment

To set up and run this application, follow these steps:

1. **Prerequisites**:
   - Make sure Docker and Git are installed on your system.

2. **Clone the Repository**:
   - Use Git to clone this repository to your local machine:
     ```bash
     git clone [Repository URL]
     ```

3. **Build the Docker Image**:
   - Navigate to the directory containing the cloned repository.
   - Build the Docker image using the following command:
     ```bash
     docker build -t php-mysql .
     ```

4. **Run the Container**:
   - After the build completes, run the container:
     ```bash
     docker run -d --name php-mysql php-mysql
     ```

5. **Push the image to Docker Hub Registry**:
   - Login to Docker Hub:
     ```bash
     docker login registry.docker.com
     ```
   - Push the image:
     ```bash
     docker push registry.docker.com/baoblack9/docker-php:demo
     ```

   - This will start the application and map port 80 of the container to port 80 on your host machine.

Now, the PHP application should be running and accessible via `http://localhost` on your web browser.