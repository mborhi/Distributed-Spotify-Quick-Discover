# Distributed Spotify Quick Discover

A web app allowing users to quickly discover and svae music from Spotify categories and genres. Documentation for API can be found on the [Spotify Quick Discover Microservices](https://www.postman.com/research-operator-51189562/workspace/spotify-quick-discover-microservices/overview) Postman workspace.

## Table of Contents

* [Quick Start](#quick-start)
    - [Kubernetes](#kubernetes)
    - [Docker](#docker)
* [Architecture](#architecture)
    - [Retrieval Service](#retrieval-service)
    - [Playback Service](#playback-service)
    - [Authentication Service](#authentication-service)
    - [API Gateway](#api-gateway)
* [Work Process](#work-process)
* [Updates](#updates)

---

# Quick Start

This section describes how to run this app locally on your machine, or how one might deploy this using a service provider.

## Kubernetes

To begin, make sure that you have installed kubectl on your machine or have enabled Kubernetes integration in Docker Desktop.
To verify that you have correctly installed and can use `kubectl`, enter the following inside your terminal: 

```
kubectl version --short
```

For instructions on how to set these up please refer to the [Kubenertes] installation documentation and the [Docker] documentation. 

We are now ready to run the application. The deploymenet and service yaml files can be find in the [k8s/ directory](./k8s/) inside the root of the project. To run these, `cd` into the root directory of the project and run:

```
kubectl apply -f k8s/
```

This command will apply all kubernetes yaml specification files and start the application. Make sure that all services and deployments are active by running:

```
kubectl get svc
```

and 

```
kubectl get deploy
```

Once all pods have been created and are running, you can access the app in your prefered browser by heading to: http://localhost:3000 .

To stop the application, run:

```
kubectl delete -f k8s/
```

You can verify that all services and deployments are no longer running by entering the commands, `kubectl get svc` and `kubectl get deploy` again.

## Docker

You may also run this application by using docker-compose.

To do this, first make sure you have docker command tools installed your machine. Verify this by entering the following command in your terminal:

```
docker --version
```

If you get an error, you can install it on the official [Docker page](https://www.docker.com/get-started/).

To orchestrate the required containers, first make sure that all the images have beein pulled from `mborhi/spotify-quick-discover-*`, or that all the images are accessible from the directory containing the docker-compose file.
Now, in the directory containing the `docker-compose.yaml`, you can run:

```
docker-compose up --build
```

You can now open http://localhost:3000 in your preferred browser to use the app.

To stop the containers, run:

```
docker-compose down
```

Alternatively, you can complete these steps using the [Docker Desktop](https://www.docker.com/products/docker-desktop/) app.

---

# Architecture

This sections describes the distrubuted architecture of this project.

The high level architecture can be visualized as such:

[image]


## Retrieval Service

## Playback Service

## Authentication Service

## API Gateway

---

# Work Process

I first began by creating a monolith version of this app.

...

The full documentation for my work process can be found in the [WorkProcess.md](./WorkProcess.md) file.

---


# Updates