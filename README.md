# Pacman App

- Create service principal

    ```bash
    az ad sp create-for-rbac --role="Owner" --scopes="/subscriptions/<subscription_id>"
    ```


## Build and push Docker Image

- Login into container registry

    ```docker
    docker login containerregistrypacman.azurecr.io
    ```

- Build Docker image
  
    ```docker
    docker build -t pacman-app .
    ```

- Tag and Push

    ```docker
    docker tag pacman-app containerregistrypacman.azurecr.io/pacman-app

    docker push containerregistrypacman.azurecr.io/pacman-app
    ```

## Conect to Kubernetes Cluster

- Run the following commands

    ```bash
    az account set --subscription <subscription_id>
    az aks get-credentials --resource-group <resource_group_name> --name <kubernetes_cluster_name>
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

## Run in Helm Chart

- Create namespace

    ```k8s
    kubectl create namespace pacman
    ```
- In helm/

    ```helm
    helm install retropacmanapp . -n pacman
    ```
