# Distributed Spotify Quick Discover

A web app allowing users to quickly discover and svae music from Spotify categories and genres.

## Table of Contents

* [Quick Start](#quick-start)
    - [Kubernetes](#kubernetes)
    - [Docker](#docker)
* [Architecture](#architecture)
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

