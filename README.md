# Voting App Deployment

This project sets up a simple voting application using Kubernetes and Minikube. The application consists of a voting frontend, a Redis instance, a PostgreSQL database, a worker application, and a result frontend.

## Prerequisites

- Minikube must be installed on your machine. You can follow the installation guide [here](https://minikube.sigs.k8s.io/docs/start/).

## Deployment Instructions

1. Create the deployments for each component:
    ```sh
    kubectl create -f voting-app-deploy.yaml
    kubectl create -f redis-deploy.yaml
    kubectl create -f postgres-deploy.yaml
    kubectl create -f worker-app-deploy.yaml
    kubectl create -f result-app-deploy.yaml
    ```

2. Access the services via Minikube:
    ```sh
    minikube service voting-service --url # for voting app URL to access via browser
    minikube service result-service --url # for result app URL to access via browser
    ```

3. Scale the voting frontend deployment:
    ```sh
    kubectl scale deployment voting-app-deploy --replicas=3 # to scale number of voting frontends to 3
    ```

## Description

- **Voting App**: The frontend where users can vote.
- **Redis**: Used as a queue for the votes.
- **PostgreSQL**: Stores the results of the votes.
- **Worker App**: Processes the votes from Redis and stores them in PostgreSQL.
- **Result App**: Displays the results of the voting.

This setup allows you to deploy and scale a simple voting application using Kubernetes and Minikube.