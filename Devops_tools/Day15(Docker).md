# Day 15: Docker

## 1. Introduction to Docker

### What is Docker?
**Docker** is an open-source platform that automates the deployment, scaling, and management of applications using containerization. Containers package an application and its dependencies into a single, portable unit that can run consistently across different environments.

### Key Concepts:
- **Containers**: Lightweight, standalone, and executable packages that include everything needed to run an application.
- **Images**: Read-only templates used to create containers. Images include the application code, libraries, and dependencies.
- **Dockerfile**: A script containing a series of instructions for building a Docker image.
- **Docker Hub**: A cloud-based registry for sharing Docker images.

---

## 2. Installing Docker

### A. Installing Docker on Your Machine
1. **For Windows and Mac**:
   - Download Docker Desktop from the [Docker website](https://www.docker.com/products/docker-desktop).
   - Follow the installation instructions for your operating system.

2. **For Linux**:
   - Install Docker using package management tools. For example, on Ubuntu:
     ```bash
     sudo apt update
     sudo apt install docker.io
     ```

3. **Verify Installation**:
   - Check the Docker version to ensure it is installed correctly:
     ```bash
     docker --version
     ```

---

## 3. Working with Docker

### A. Docker Images
1. **Pull an Image**:
   - Download an image from Docker Hub:
     ```bash
     docker pull ubuntu
     ```

2. **List Images**:
   - View all available images on your system:
     ```bash
     docker images
     ```

### B. Docker Containers
1. **Run a Container**:
   - Start a new container from an image:
     ```bash
     docker run -it ubuntu
     ```
   - This command starts an interactive terminal session in an Ubuntu container.

2. **List Running Containers**:
   - View active containers:
     ```bash
     docker ps
     ```

3. **Stop and Remove Containers**:
   - Stop a running container:
     ```bash
     docker stop container-id
     ```
   - Remove a stopped container:
     ```bash
     docker rm container-id
     ```

### C. Dockerfile
1. **Create a Dockerfile**:
   - Write a Dockerfile with instructions to build an image. Example Dockerfile:
     ```dockerfile
     # Use an official Ubuntu runtime as a parent image
     FROM ubuntu:latest

     # Set the working directory in the container
     WORKDIR /app

     # Copy the local files to the container
     COPY . /app

     # Install any needed packages
     RUN apt-get update && apt-get install -y python3

     # Run a command to verify the setup
     CMD ["python3", "--version"]
     ```

2. **Build an Image**:
   - Build an image from the Dockerfile:
     ```bash
     docker build -t my-python-app .
     ```

### D. Docker Hub
1. **Login to Docker Hub**:
   - Authenticate with Docker Hub:
     ```bash
     docker login
     ```

2. **Push an Image**:
   - Push a local image to Docker Hub:
     ```bash
     docker tag my-python-app username/my-python-app
     docker push username/my-python-app
     ```

3. **Pull an Image**:
   - Download an image from Docker Hub:
     ```bash
     docker pull username/my-python-app
     ```

---

## 4. Best Practices for Docker

### A. Image Management
- **Keep Images Small**: Use minimal base images and avoid installing unnecessary packages.
- **Use Multi-Stage Builds**: Optimize image size and build efficiency with multi-stage Dockerfiles.

### B. Container Security
- **Run as Non-Root**: Avoid running containers as the root user for better security.
- **Regular Updates**: Regularly update images to incorporate security patches and updates.

### C. Docker Networking
- **Network Modes**: Understand different networking options like bridge, host, and overlay.
- **Service Discovery**: Use Docker's built-in service discovery for inter-container communication.

---

## Summary
Today, we explored **Docker**, including how to install Docker, work with images and containers, and use Dockerfiles to build custom images. Docker simplifies application deployment by using containers to ensure consistency across different environments.

**Key Takeaways:**
- **Containers** and **Images** are central to Docker's functionality.
- Use **Dockerfile** to automate image creation and **Docker Hub** for sharing images.
- Follow **best practices** for image management, security, and networking.

---

### Next Session
In the next session, we will cover **Docker Hub** to understand how to manage and share Docker images in a centralized repository.

---

**Thank you!**
