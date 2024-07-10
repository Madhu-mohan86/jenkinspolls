# Setting Up Jenkins Pipeline for Simple React App

This repository demonstrates setting up a Jenkins pipeline for that builds the Docker image of a basic react application.

## Prerequisites

- Docker installed on your Jenkins server or machine: [Install Docker](https://docs.docker.com/get-docker/)
- Jenkins installed and running: [Install Jenkins](https://www.jenkins.io/download/)

## Steps to Set Up

### 1. Install Jenkins Plugins

Ensure the following plugins are installed in Jenkins:

- Docker Plugin: Allows Jenkins to use Docker to run builds.
- Pipeline Plugin: Provides support for Pipeline as Code.

### 2. Configure Jenkins

1. **Start Jenkins**:
   - Follow installation instructions to start Jenkins.
   - Access Jenkins at `http://localhost:8080` (or configured port).

2. **Set up Docker Hub Credentials** (if applicable):
   - Go to Jenkins > Credentials.
   - Add Docker Hub username and password as secret text credentials.

### 3. Create Jenkins Pipeline

1. **Create a New Pipeline Project**:
   - Click on "New Item" on Jenkins dashboard.
   - Enter a name (e.g., `my-react-app-pipeline`) and select "Pipeline" as project type.

2. **Configure Pipeline from SCM**:
   - Under "Pipeline" section, choose "Pipeline script from SCM".
   - Select your SCM (e.g., Git) and enter repository URL (`https://github.com/your-username/my-react-app`).

3. **Save and Run Pipeline**:
   - Save your pipeline configuration.
   - Click "Build Now" to run the pipeline manually for the first time.

### 4. Monitor and Customize Pipeline

- Jenkins will execute the steps defined in `Jenkinsfile` (located in your repository).
- Customize `Jenkinsfile` to define build, test, and deployment stages specific to your React application.
