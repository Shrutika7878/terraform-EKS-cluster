# Amazon EKS Cluster with Managed Node Group using Terraform

## Overview

This project provisions an Amazon EKS (Elastic Kubernetes Service) cluster and a managed node group using Terraform.

The infrastructure includes:

* Amazon EKS Cluster
* EKS Control Plane IAM Role
* EKS Worker Node IAM Role
* Required IAM Policy Attachments
* Managed Node Group
* Default VPC and Subnets Integration

## Architecture

Terraform provisions:

1. IAM Role for EKS Cluster
2. Amazon EKS Cluster
3. IAM Role for Worker Nodes
4. Worker Node Policy Attachments
5. EKS Managed Node Group

## Prerequisites

* AWS Account
* AWS CLI configured
* Terraform installed
* Appropriate IAM permissions
* Existing Default VPC in the selected region

## Technologies Used

* Terraform
* AWS EKS
* AWS IAM
* AWS VPC
* Kubernetes

## Configuration

Provider Configuration:

```hcl
provider "aws" {
  region = "eu-north-1"
}
```

Node Group Configuration:

```hcl
instance_types = ["t3.micro"]

scaling_config {
  desired_size = 2
  min_size     = 1
  max_size     = 3
}
```

## Deployment Steps

Initialize Terraform:

```bash
terraform init
```

Validate Configuration:

```bash
terraform validate
```

Review Execution Plan:

```bash
terraform plan
```

Create Infrastructure:

```bash
terraform apply
```

## Configure kubectl

Update kubeconfig:

```bash
aws eks update-kubeconfig \
  --region eu-north-1 \
  --name cluster
```

Verify Cluster:

```bash
kubectl get nodes
```

## Resources Created

### IAM Roles

* eks-cluster-example
* eks-node-group-example

### EKS Resources

* EKS Cluster: cluster
* Node Group: worker-nodes

## Cleanup

Destroy all resources:

```bash
terraform destroy
```

## Learning Outcomes

This project demonstrates:

* Infrastructure as Code (IaC)
* Amazon EKS Deployment
* IAM Role Management
* Managed Node Groups
* Terraform Resource Dependencies
* Kubernetes Infrastructure Provisioning
