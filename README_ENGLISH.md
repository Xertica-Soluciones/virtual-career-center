![image](https://github.com/user-attachments/assets/a1a596ee-eade-4774-837e-bd46552af9c4)
# Kubernetes (K8s) 

[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/569/badge)](https://bestpractices.coreinfrastructure.org/projects/569) [![Go Report Card](https://goreportcard.com/badge/github.com/kubernetes/kubernetes)](https://goreportcard.com/report/github.com/kubernetes/kubernetes)

<img src="https://github.com/kubernetes/kubernetes/raw/master/logo/logo.png" width="100">

----
# Overview

It is a cloud-based platform that uses Generative AI, Machine Learning and Natural Language Processing algorithms to improve student employability through:
▷ Automatic CV generation
▷ Job-to-candidate and candidate-to-job matching
▷ Generating strategic insights into the local job market

# Support Description

Thank you for reaching out to Xertica Virtual Career Center support on Google Cloud Marketplace. We are here to help you with any questions or issues you may have.

In order for us to best respond to your request, please include the following information in your email:
 ```bash
 vcc-suporte@xertica.com
 ```

Google Cloud Project ID: The project ID of the project where you are using [Your Product Name].
Problem Description: Please provide details about the issue you are experiencing, including the steps you took and the results you obtained. If possible, include screenshots or error logs.
Contact Information: Your name, email address, and phone number so that we can contact you if necessary.
We aim to respond to your request as quickly as possible. Response times may vary depending on the complexity of the issue and the volume of requests.

# Support URL
```bash
https://www.xertica.ai/en/contact
```
# Application Deployment on Kubernetes

This repository contains the files needed to deploy the application to Kubernetes. Follow the steps below to apply all the deployment files.

To obtain the installation files, contact support.

## File Structure

- `k8s/deployment.yaml`: Deployment do frontend.
- `k8s/service.yaml`: Service to expose the frontend.

## Cluster Creation

```bash
gcloud container clusters create-auto [CLUSTER_NAME] \
    --region [REGIÃO] \
    --project [ID_DO_PROJETO]
```

## Connect to Cluster

If you are not already authenticated, sign in to your Google Cloud account:

```bash
gcloud auth login
```

Make sure you are using the correct Google Cloud project:

```bash
gcloud config set project [PROJECT_ID]
```

Use the below command to get the cluster credentials and configure them in `kubectl`:

```bash
gcloud container clusters get-credentials [CLUSTER_NAME] \
    --region [REGION] \
    --project [PROJECT_ID]
```

To verify that the connection was established correctly, run:

```bash
kubectl get nodes
```

## How to Apply Deployment Files

To apply all deployment files, run the commands below:

```bash
kubectl create namespace vcc
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```
----

# Kubernetes uninstallation process

![image](https://github.com/user-attachments/assets/7b08a6f3-ca09-41a3-8522-6c0e4b6acd5a)

To uninstall or remove resources created in Kubernetes via CLI, you need to delete the deployments, services, and other resources that were applied during installation.

Below is a step-by-step guide to uninstalling the application:

## Connect to Cluster

First, make sure you are connected to the Kubernetes cluster where the resources are deployed. If you are already connected (as described in the installation process), you can skip this step.

Otherwise, follow the steps to authenticate and connect to the cluster:

```bash
gcloud auth login
gcloud config set project [PROJECT_ID]
gcloud container clusters get-credentials [CLUSTER_NAME] \
    --region [REGION] \
    --project [PROJECT_ID]
```

## Delete Deployment and Service Resources

Run the commands below to delete the deployments and services you applied previously:

```bash
kubectl delete -f k8s/deployment.yaml -n [NAME_SPACE_NAME]
kubectl delete -f k8s/service.yaml -n [NAME_SPACE_NAME]
```

These commands delete the deployments and services specified in the YAML files.

## Delete Namespace (Optional)

If the namespace was created exclusively for this application and you want to remove it, you can delete the entire namespace. This will remove all resources within it:

```bash
kubectl delete namespace [NAME_SPACE_NAME]
```

**Attention**: Deleting a namespace will remove all resources (deployments, services, pods, etc.) that are within it. Use this command with caution..

## Verify Deletion

After deleting the resources, you can check if everything was removed correctly:

```bash
kubectl get all -n [NAME_SPACE_NAME]
```
