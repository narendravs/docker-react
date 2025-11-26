# Dockerized React App with GitHub Actions CI/CD

A boilerplate project for creating a React application, containerizing it with Docker, and setting up a Continuous Integration and Continuous Deployment (CI/CD) pipeline using GitHub Actions.

## Table of Contents

- [Project Architecture](#project-architecture)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [Installation](#installation)
  - [Running Locally](#running-locally)
- [Docker Setup](#docker-setup)
  - [Building the Docker Image](#building-the-docker-image)
  - [Running with Docker](#running-with-docker)
- [CI/CD with GitHub Actions](#cicd-with-github-actions)
  - [Workflow](#workflow)
  - [Secrets](#secrets)
- [Available Scripts](#available-scripts)
- [Folder Structure](#folder-structure)
- [Contributing](#contributing)
- [License](#license)

## Project Architecture

This project uses a standard React application structure created with `create-react-app`. The application is then containerized using Docker. We use a multi-stage `Dockerfile` to create an optimized, production-ready image.

The CI/CD pipeline is configured with GitHub Actions. The workflow is triggered on every push to the `main` branch. It performs the following steps:

1.  **Checkout Code**: Checks out the repository code.
2.  **Set up Docker Buildx**: Sets up the Docker builder instance.
3.  **Log in to Docker Hub**: Authenticates with Docker Hub to push the image.
4.  **Build and Push**: Builds the Docker image and pushes it to Docker Hub.
5.  **(Optional) Deploy**: A deployment step can be added to deploy the image to a cloud provider (e.g., AWS, Azure, Heroku).

## Features

- **React**: A simple dummy React application.
- **Docker**: Containerized application for consistent development and production environments.
- **Multi-stage Docker build**: Creates a lightweight production image using Nginx.
- **GitHub Actions**: Automated CI/CD pipeline for building and pushing the Docker image.

## Prerequisites

Make sure you have the following installed on your local machine:

- Node.js (v14.x or later)
- npm or Yarn
- Docker

## Getting Started

### Installation

1.  **Clone the repository:**

    ```sh
    git clone https://github.com/<YOUR_USERNAME>/<YOUR_REPOSITORY>.git
    cd <YOUR_REPOSITORY>
    ```

2.  **Install dependencies:**
    ```sh
    npm install
    ```

### Running Locally

To start the development server, run:

```sh
npm start
```

The application will be available at `http://localhost:3000`.

## Docker Setup

The project includes a `Dockerfile` for building a production image and a `docker-compose.yml` for easier local container management.

### Building the Docker Image

To build the Docker image, run the following command from the project root:

```sh
docker build -t <your-dockerhub-username>/docker-react .
```

### Running with Docker

To run the application inside a Docker container:

```sh
docker run -p 8080:80 <your-dockerhub-username>/docker-react
```

The application will be available at `http://localhost:8080`.

## CI/CD with GitHub Actions

### Workflow

The CI/CD workflow is defined in `.github/workflows/main.yml`. It automates the process of building the Docker image and pushing it to a container registry (like Docker Hub) whenever changes are pushed to the `main` branch.

### Secrets

To allow GitHub Actions to push to your Docker Hub repository, you need to add the following secrets to your GitHub repository settings (`Settings > Secrets and variables > Actions`):

- `DOCKERHUB_USERNAME`: Your Docker Hub username.
- `DOCKERHUB_TOKEN`: Your Docker Hub access token.

## Available Scripts

- `npm start`: Runs the app in development mode.
- `npm test`: Runs the test suite.
- `npm run build`: Builds the app for production.

## Folder Structure

```
.
├── .github/workflows/   # GitHub Actions CI/CD configuration
├── public/              # Public assets
├── src/                 # React application source code
├── .dockerignore        # Files to ignore in Docker context
├── .gitignore           # Files to ignore for Git
├── Dockerfile           # Docker configuration for building the image
├── package.json         # Project dependencies and scripts
└── README.md            # This file
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1.  Fork the repository.
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.
