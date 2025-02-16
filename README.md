
# Web Application CI/CD Pipeline with Docker, Jenkins, Vagrant, and Ansible

## Project Overview
This project demonstrates a simple Continuous Integration/Continuous Deployment (CI/CD) pipeline using Jenkins, Docker, Vagrant, and Ansible to deploy a Python web application. The pipeline pulls code from a GitHub repository, builds a Docker image, pushes it to Docker Hub, and then uses Ansible to configure two Vagrant machines for deployment.

## Requirements

- **GitHub** - For storing the Python web application.
- **Docker** - To containerize the application.
- **Vagrant** - To create and manage virtual machines for deployment.
- **Jenkins** - To automate the CI/CD pipeline.
- **Ansible** - To configure and manage the deployment on Vagrant machines.

### Prerequisites
- Install [Git](https://git-scm.com/)
- Install [Docker](https://docs.docker.com/get-docker/)
- Install [Vagrant](https://www.vagrantup.com/)
- Install [Jenkins](https://www.jenkins.io/download/)
- Install [Ansible](https://www.ansible.com/)
- A **GitHub account** with a private repository for the code.
- **Docker Hub account** for pushing images.

## Steps to Setup

### 1. Clone the GitHub Repository

Clone the repository that contains the Python code for the web application to your local machine.


### 2. Dockerfile for Containerization

In the root directory of your project, create a **Dockerfile** that will containerize your Python web application. Here's a sample Dockerfile for a Python Flask application:



### 3. Vagrant Configuration

Create **two Vagrant machines** with low specs 

### 4. Jenkins Pipeline Configuration

Set up a **Jenkins pipeline** that does the following:

1. **Pulls code** from a private GitHub repository using your credentials (token).
2. **Builds the Docker image** for the Python web application.
3. **Pushes the image** to Docker Hub.
4. **Runs an Ansible playbook** to install Docker on the target VMs, pull the image from Docker Hub, and run the Docker container.


### 5. Ansible Playbook for Deployment

Create an Ansible playbook to install Docker on the target VMs and deploy the Docker container. 

### 6. Running the Application

- **Step 1**: First, ensure that Vagrant machines are up and running:
  ```bash
  vagrant up
  ```

- **Step 2**: Trigger the Jenkins pipeline by pushing the code to the repository. The Jenkins pipeline will:
  - Clone the repository.
  - Build and push the Docker image.
  - Use Ansible to configure the VMs and deploy the container.

### 7. Verification

Once the pipeline completes successfully, you should be able to access the Python web application by visiting the IP address of the Vagrant machines at port `5000` (e.g., `http://<vagrant_ip>:5000`).

---

## Summary of Project Flow

1. **Jenkins** triggers on push to GitHub, builds the Docker image.
2. The Docker image is pushed to **Docker Hub**.
3. **Ansible** installs Docker on Vagrant machines and runs the container.
4. **Email notification** of the build status is sent.

---

## Conclusion

This project demonstrates a simple but effective way to automate deployment of a web application using a CI/CD pipeline with Jenkins, Docker, Vagrant, and Ansible. It covers the entire process from code pushing to deployment across multiple machines.



Results :

![Screenshot 2025-02-14 215405](https://github.com/user-attachments/assets/7fecbccc-2192-4a91-bb69-0c7fbcd38ec4)
![Screenshot 2025-02-14 215435](https://github.com/user-attachments/assets/6d1013ea-126d-4c68-9f26-6c1be4202475)

Emails Sent: 
![image](https://github.com/user-attachments/assets/b85dea12-bab2-4e2f-a828-1e0356ed9aa5)



