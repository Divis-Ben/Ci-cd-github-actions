# CI/CD Pipeline with Docker and GitHub Actions

A simple CI/CD project that demonstrates how to containerize a web application with Docker and automatically build and test it using GitHub Actions.

## Project Overview

This project uses Nginx to serve a simple HTML application inside a Docker container.

GitHub Actions is used to automate the CI/CD process whenever code is pushed to the `main` branch or a pull request is opened against `main`.

## Technologies Used

- Linux
- Docker
- Nginx
- Git
- GitHub
- GitHub Actions
- HTML
- Bash
- cURL

## Project Structure

```text
ci-cd-github-actions/
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── app/
│   └── index.html
│
├── Dockerfile
└── README.md



DOCKERFILE

The application uses the lightweight nginx:alpine image.

FROM nginx:alpine

COPY app/index.html /usr/share/nginx/html/index.html

EXPOSE 80

The Dockerfile:

1. Uses Nginx Alpine as the base image.
2. Copies the application's index.html into the Nginx web directory.
3. Exposes port 80.


CI/CD PIPELINE

The GitHub Actions workflow is triggered by:

Pushes to the main branch
Pull requests targeting the main branch


PIPELINE STEPS

Code Push / Pull Request
          ↓
    Checkout Code
          ↓
   Build Docker Image
          ↓
   Run Docker Container
          ↓
   Verify Container
          ↓
   Test Application
          ↓
       Pipeline
       Pass/Fail


GITHUB ACTIONS WORKFLOW

The pipeline performs the following operations:

1. Checkout code using actions/checkout@v4
2. Build Docker image
3. Run Docker container
4. Verify the container
5. Test the application using cURL

The application is mapped from container port 80 to host port 8081.

RUN THE PROJECT LOCALLY

1. Clone the repository

git clone https://github.com/Divis-Ben/Ci-cd-github-actions.git
cd Ci-cd-github-actions

2. Build the Docker image

docker build -t my-cicd-app .

3. Run the container

docker run -d --name my-cicd-container -p 8081:80 my-cicd-app

4. Verify the container

docker ps --filter name=my-cicd-container

5. Test the application

Open:

http://localhost:8081

Or test using:

curl --fail http://localhost:8081


CI/CD AUTOMATION

The purpose of this project is to demonstrate how GitHub Actions can automatically validate a Dockerized application after code changes.

This helps catch application or container startup problems before the code is considered ready.

WHAT I LEARNED

Through this project, I practiced:

Creating a Dockerfile
Building Docker images
Running Docker containers
Port mapping
Using Nginx to serve a web application
Writing GitHub Actions workflows
Automating application testing
Using cURL for application testing
Troubleshooting CI/CD pipeline failures
Working with Git and GitHub

FUTURE IMPROVEMENTS

Possible improvements include:

Push Docker images to Docker Hub
Add additional automated tests
Add Docker image versioning
Add a deployment stage
Deploy the application to a cloud platform
Add environment variables and GitHub Secrets
Add monitoring and logging
Author

DIVIS-BEN

Cloud & DevOps Engineer in Training
