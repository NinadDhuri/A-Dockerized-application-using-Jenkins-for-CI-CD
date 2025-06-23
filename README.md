# Dockerized Node.js Application with Jenkins CI/CD

This repository contains a simple Node.js application packaged with Docker and a Jenkins pipeline for automated builds and deployments.

## Features

- **Node.js Express server** located in `index.js`.
- **Dockerfile** for building a container image.
- **Jenkinsfile** describing a pipeline that builds and runs the Docker image.
- **.dockerignore** file to keep the image slim by excluding unnecessary files.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (for local development)
- [Docker](https://www.docker.com/) for containerization
- [Jenkins](https://www.jenkins.io/) if you want to run the pipeline

### Running Locally

1. Install dependencies:
   ```bash
   npm install
   ```
2. Start the application:
   ```bash
   npm start
   ```
   The app will be available on `http://localhost:3000`.

### Configuration

You can override the default port by setting the `PORT` environment variable:

```bash
PORT=8080 npm start
```

### Building the Docker Image

```bash
docker build -t node-app .
```

### Running the Docker Container

```bash
docker run -d -p 3000:3000 --name node-container node-app
```

### Jenkins Pipeline

The included `Jenkinsfile` contains stages that check out the code, build the Docker image, and run the container. You can create a pipeline job in Jenkins and point it to this repository to automate these steps.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

