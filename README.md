# Pacman App

## Build and push Docker Image

- Login into container registry

    ```docker
    docker login douretrogame.azurecr.io
    ```

- Build Docker image
  
    ```docker
    docker build -t pacman-app .
    ```

- Tag and Push

    ```docker
    docker tag pacman-app douretrogame.azurecr.io/pacman-app

    docker push douretrogame.azurecr.io/pacman-app
    ```

## Run in K8s Cluster

- Create namespace

    ```k8s
    kubectl create namespace pacman
    ```
- In k8s/db

    ```k8s
    kubectl -n pacman apply -f .
    ```

- In k8s/app

    ```k8s
    kubectl -n pacman apply -f .
    ```

- Get all in pacman ns

    ```
    kubectl -n pacman get all
    ```
