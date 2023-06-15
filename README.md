# Build & Deploy Node.js Application to Amazon EKS with Skaffold and GitHub Actions

![Diagram of workflow](skaffold-and-github-actions.png)

This repository contains source code for a basic Node.js application that can be be built and deployed to an Amazon EKS cluster. During the CI stage, the application is tested, built and pushed to Docker Hub repository. After that, a connection is established with the Amazon EKS cluster before the application is deployed using Skaffold.

## Prerequisites
* [Skaffold](https://skaffold-latest.firebaseapp.com/)
* [Node.js](https://nodejs.org/)
* [kubectl](https://kubernetes.io/docs/tasks/tools/)
* [Rancher Desktop](https://rancherdesktop.io/) (for local K8s development)
* [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli) (to create K8s cluster with IaC)

## Folder Structure

```
├── Dockerfile
├── README.md
├── manifests.yaml
├── node_modules
├── package-lock.json
├── package.json
├── skaffold.yaml
└── src
   ├── app.js
   ├── index.js
   └── test
```

## Local Development with Skaffold
To use Skaffold for local Kubernetes development and debugging on your application, ensure that you have Skaffold installed on your machine and a Kubernetes cluster with an established connection. For easy K8s development, you can make use of [Rancher Desktop](https://rancherdesktop.io/).

```
kubectl config current-context
skaffold init # run this if you don't have a Skaffold manifest file
skaffold dev # run this for continuous delivery to you K8s cluster 
```

## Create Amazon EKS Cluster with Terraform
You can create an Amazon EKS cluster in your AWS account using the source code available [here](https://github.com/LukeMwila/amazon-eks-cluster).
