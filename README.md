# All I know about Cloud Native
# GKE - Google Kubernetes Engine
## Introduction
## High Level Overview
### Section Introduction
### Google Kubernetes Engine: A Google Managed Service
### Google Kubernetes Engine: Architecture
## GKE Deployment and Administration
### Section Introduction
### Hands-on: Creating our first GKE cluster
```sh
# 1. You can create a zonal cluster by using the gcloud CLI or the Google Cloud console.
# 2. We’ll use gcloud command using Google Cloud Shell
# 3. We’ll create a cluster with a custom boot disk to comply with the lab policies. If you specify a disk size higher than what’s specified in labs quick start page, the cluster creation command will throw up an error.
--disk-size=DISK_SIZE Size for node VM boot disks in GB. Defaults to 100GB.
DISK_SIZE should be less than 12 GB
--disk-type=DISK_TYPE Type of the node VM boot disk. For version 1.24.0+,
defaults to pd-balanced. DISK_TYPE must be: pd-standard
--num-nodes=NUM_NODES; default=3. NUM_NODES should be = 1
# Step 1: Install kubectl
gcloud components install kubectl
sudo apt-get install kubectl
# 1. You can create a zonal cluster by using the gcloud CLI or the Google Cloud
console.
# 2. We’ll use gcloud command using Google Cloud Shell
# 3. We’ll create a cluster with a custom boot disk to comply with the lab policies. If you specify a disk size higher than what’s specified in labs quick start page, thecluster creation command # will throw up an error.
# 5. Type the following command to create a cluster now
# gcloud container clusters create gke-deep-dive --num-nodes=1 --disk-type=pd-standard --disk-size=10
# Make sure of the name format: (?:[a-z](?:[-a-z0-9]{0,38}[a-z0-9])?)
```
#!/bin/bash

# FILEPATH: Untitled-1

# Step 1: Install Kubectl
sudo apt-get install kubectl
gcloud components install kubectl
sudo apt-get install kubectl

# 2. Verify that kubectl is installed
kubectl version

# Step 2: Verify installation of required plugins
# Before you begin, check whether the plugin is already installed:
gke-gcloud-auth-plugin --version
if [[ $? -ne 0 ]]; then
    gcloud components install gke-gcloud-auth-plugin
fi
gke-gcloud-auth-plugin --version

# Step 3: generate a kubeconfig context for a specific cluster and to use the
# plugin:
gcloud container clusters get-credentials CLUSTER_NAME --region=COMPUTE_REGION
# Replace the following:
# CLUSTER_NAME: the name of your cluster.
# COMPUTE_REGION: the Compute Engine region for your cluster. For
# zonal clusters, use --zone=COMPUTE_ZONE.
gcloud container clusters get-credentials gke-dp-dev --zone us-west1-a

# Step 4: Verify the configuration:
kubectl get namespaces

# Step 5: View Kubeconfig
kubectl config view

# Step 6: Install a test app:
kubectl run my-app --image gcr.io/cloud-marketplace/google/nginx1:latest --cluster <Cluster-Name>

# Step 7: Verify the app by listing pods:
kubectl get pods
```
```
### Prepare
## Networking for GKE clusters
## Managing Security Aspects
### Section Introduction - Plan, Deploy And Manage Workloads On GKE
## Plan, Deploy And Manage Workloads On GKE
## GKE Design Considerations
