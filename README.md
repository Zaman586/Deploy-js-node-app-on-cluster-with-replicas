# Deploy-js-node-app-on-cluster-with-replicas
# Deploy Node.js Application on Kubernetes

This repository contains Kubernetes manifests to deploy a simple Node.js application that responds with "Hello from Node.js!" on port 3000. The deployment consists of a `Deployment`, `ReplicaSet`, and a `Service` for exposing the app.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Manifests](#manifests)
- [Steps to Deploy](#steps-to-deploy)
  - [1. Create Namespace](#1-create-namespace)
  - [2. Apply the Deployment](#2-apply-the-deployment)
  - [3. Apply the ReplicaSet](#3-apply-the-replicaset)
  - [4. Expose the Application](#4-expose-the-application)
- [Accessing the Application](#accessing-the-application)
- [Clean Up](#clean-up)

## Prerequisites

Make sure you have the following installed:
- A running Kubernetes cluster
- `kubectl` configured to interact with the cluster

## Manifests

This repository contains the following Kubernetes manifests:
1. `deployment.yml` - Defines the deployment for the Node.js app.
2. `replicaset.yaml` - Creates a ReplicaSet to ensure 4 replicas of the app.
3. `service.yaml` - Exposes the application via a NodePort service on port 3000.

## Steps to Deploy

### 1. Create Namespace

First, create the namespace `groups-node` where the application will be deployed:

```bash
kubectl create namespace zaman
2. Apply the Deployment
2. Apply the Deployment

Use the deployment.yml file to create the Node.js deployment:

bash

kubectl apply -f deployment.yml

This will create 4 replicas of the Node.js app in the groups-node namespace.
3. Apply the ReplicaSet

You can create a ReplicaSet to manage the Node.js application replicas. Apply the replicaset.yaml:

bash

kubectl apply -f replicaset.yaml

The ReplicaSet ensures that 4 replicas of the app are always running.
4. Expose the Application

To access the app externally, apply the service.yaml to expose the Node.js app through a NodePort service:

bash

kubectl apply -f service.yaml

This will expose the Node.js app on port 30010 on your cluster's nodes.
Accessing the Application

Once the service is up, you can access the Node.js application using the external IP of any of your cluster nodes and the assigned NodePort.

For example, open a browser or use curl:

bash

curl http://<node-ip>:30010

You should see the message:

csharp

Hello from Node.js!

Clean Up

To remove the Node.js deployment, ReplicaSet, and Service, run the following commands:

bash

kubectl delete -f service.yaml
kubectl delete -f replicaset.yaml
kubectl delete -f deployment.yml

Notes

    The application uses Node.js v14.
    The service is exposed via NodePort on port 30010. Ensure your firewall settings allow traffic to this port.


