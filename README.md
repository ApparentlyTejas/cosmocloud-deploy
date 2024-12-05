# cosmocloud-deploy
Cosmocloud Helm Chart

This repository contains a Helm chart to deploy a simple application stack on Kubernetes. The stack includes a frontend service, a backend service, and a Redis database. The chart is designed to be simple, modular, and easy to use.

Installation

Follow these steps to install and test the Helm chart:

Prerequisites
Kubernetes cluster (e.g., Minikube, K3s, or any managed Kubernetes service).
kubectl installed and configured to connect to your cluster.
Helm installed (version 3.0 or higher).

File Structure

Here’s a quick summary of the files in this repository:

Chart.yaml
The main Helm chart configuration file. It defines metadata like the chart name (cosmocloud-deploy) and version.

values.yaml
The default values for the chart. This file contains configuration for:

Backend (image, environment variables, ports)
Frontend (image, environment variables, ports)
Redis (image, ports)
You can modify this file to customize the deployment.

templates/
This folder contains all the Kubernetes manifests rendered by Helm:

backend-deployment.yaml: Deploys the backend service as a Deployment.
backend-service.yaml: Exposes the backend as a ClusterIP service.
frontend-deployment.yaml: Deploys the frontend service as a Deployment.
frontend-service.yaml: Exposes the frontend as a NodePort service.
redis-deployment.yaml: Deploys the Redis database as a Deployment.
redis-service.yaml: Exposes the Redis database as a ClusterIP service.
README.md
This file. Provides installation instructions and an overview of the project.

How It Works

Backend:
Pulls the image shreybatra/sample-backend.
Connects to Redis using the environment variable REDIS_URI.
Exposed internally via the backend-svc service.
Frontend:
Pulls the image shreybatra/sample-frontend.
Communicates with the backend using the environment variable BACKEND_URL.
Exposed externally via the frontend-svc service (NodePort).
Redis:
Pulls the official redis image.
Used by the backend to store data.
Exposed internally via the redis-svc service.
